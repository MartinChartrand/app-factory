# 03 — Architecture Swift : [NomApp]

> **Durée estimée :** 30–45 minutes
> **Quand :** Après le PRD (template 02)
> **But :** Définir comment builder le MVP — structure du code, modèles, patterns

---

## Vue d'ensemble technique

| Composant | Choix | Justification |
|---|---|---|
| **UI** | SwiftUI | Standard Apple, déclaratif |
| **Persistance** | SwiftData | Natif, intégré SwiftUI |
| **Sync** | CloudKit (via SwiftData) | Zero-config pour sync iCloud |
| **Navigation** | NavigationStack / TabView | Pattern standard iOS |
| **Réseau** | [URLSession / aucun] | [justification] |
| **Analytics** | [aucun / TelemetryDeck / custom] | [justification] |
| **Minimum iOS** | 18.0 | SwiftData + dernières APIs |
| **Xcode** | 26.x | Claude Agent intégré |

---

## Structure du projet

```
[NomApp]/
├── [NomApp]App.swift              # Entry point, @main
├── Models/
│   ├── [Entité1].swift            # @Model SwiftData
│   ├── [Entité2].swift            # @Model SwiftData
│   └── Enums/
│       └── [Enum].swift           # Types partagés
├── Views/
│   ├── ContentView.swift          # Root view (TabView ou NavigationStack)
│   ├── [Feature1]/
│   │   ├── [Feature1]View.swift   # Vue principale
│   │   └── [SubView].swift        # Sous-composants
│   ├── [Feature2]/
│   │   ├── [Feature2]View.swift
│   │   └── [SubView].swift
│   ├── Components/                # Composants réutilisables
│   │   ├── [Component].swift
│   │   └── [Component].swift
│   └── Settings/
│       └── SettingsView.swift
├── ViewModels/                    # Si complexité le justifie
│   └── [ViewModel].swift
├── Services/
│   ├── [Service].swift            # Logique métier isolée
│   └── NotificationService.swift  # Si notifications locales
├── Extensions/
│   ├── Date+Extensions.swift
│   └── [Type]+Extensions.swift
├── Resources/
│   ├── Assets.xcassets
│   ├── Localizable.xcstrings      # FR + EN
│   └── [NomApp].entitlements
├── Widgets/                       # Si widget dans le MVP
│   └── [NomApp]Widget.swift
└── Preview Content/
    └── PreviewSampleData.swift    # Données de preview
```

### Conventions de nommage

- **Fichiers :** PascalCase, suffixe par type (`ListView`, `DetailView`, `ItemModel`)
- **Variables :** camelCase
- **Constantes :** camelCase ou UPPER_SNAKE pour globales
- **Pas de Coordinator pattern** — NavigationStack natif
- **Pas de packages externes** sauf justification forte

---

## Modèles SwiftData

### [Entité1]

```swift
@Model
final class [Entité1] {
    var id: UUID
    // Champs principaux
    var [champ1]: [Type]
    var [champ2]: [Type]
    var [champ3]: [Type]

    // Métadonnées
    var createdAt: Date
    var updatedAt: Date

    // Relations
    @Relationship(deleteRule: .[rule])
    var [relation]: [Type]?

    init([params]) {
        self.id = UUID()
        // ...
        self.createdAt = .now
        self.updatedAt = .now
    }
}
```

### [Entité2]

```swift
@Model
final class [Entité2] {
    // [même pattern]
}
```

### Schéma de migration

- **V1 (MVP) :** Schéma initial, pas de migration nécessaire
- **V1.1+ :** Utiliser `VersionedSchema` + `SchemaMigrationPlan`

---

## Navigation

### Pattern principal

```
[NomApp]App
└── ContentView
    ├── TabView (si multi-section)
    │   ├── Tab 1: NavigationStack
    │   │   ├── [List]View
    │   │   └── → [Detail]View
    │   ├── Tab 2: NavigationStack
    │   │   └── [Feature]View
    │   └── Tab 3: NavigationStack (Settings)
    │       └── SettingsView
    │
    └── NavigationStack (si single-flow)
        ├── [Main]View
        └── → [Detail]View
```

### Deep linking (si applicable)

- [ ] Pas nécessaire pour le MVP
- [ ] Widget → vue spécifique
- [ ] Notification → vue spécifique

---

## CloudKit Sync

### Stratégie

- [ ] **Automatic** — SwiftData + CloudKit container automatique
- [ ] **Custom** — CKRecord manipulation directe (rare pour MVP)

### Configuration requise

```
Entitlements:
  - com.apple.developer.icloud-container-identifiers
  - com.apple.developer.icloud-services (CloudKit)

Container: iCloud.com.martinchartrand.[nomapp]
```

### Considérations sync

- **Conflit resolution :** Last-write-wins (défaut SwiftData/CloudKit)
- **Offline-first :** Oui — SwiftData persist localement, sync quand réseau disponible
- **Données initiales :** Seed data dans `init()` du ModelContainer si nécessaire
- **Latence sync :** Accepter 1-5 secondes de délai entre devices

---

## Widgets (si applicable)

- [ ] Pas de widget dans le MVP
- [ ] Widget prévu :

| Widget | Taille(s) | Données affichées | Refresh |
|---|---|---|---|
| [nom] | small / medium | [quoi] | Timeline: toutes les [X] heures |

### App Group

```
group.com.martinchartrand.[nomapp]
```

Requis pour partager des données entre l'app principale et le widget.

---

## Localisation

### Stratégie

- **Fichier :** `Localizable.xcstrings` (format Xcode 15+)
- **Langues MVP :** Français (base), English
- **Approche :** `String(localized:)` pour toutes les chaînes visibles
- **Pluralisation :** Utiliser les règles de pluralisation intégrées

### Convention de clés

```
"[ecran].[element].[description]"
Exemples:
  "dashboard.title" = "Tableau de bord"
  "settings.sync.toggle" = "Synchronisation iCloud"
  "item.delete.confirm" = "Supprimer cet élément?"
```

---

## Gestion d'erreurs

### Pattern

```swift
enum [NomApp]Error: LocalizedError {
    case [cas1]
    case [cas2]

    var errorDescription: String? {
        switch self {
        case .[cas1]: String(localized: "error.[cas1]")
        case .[cas2]: String(localized: "error.[cas2]")
        }
    }
}
```

### Stratégie UX pour les erreurs

- **Erreurs réseau :** Banner non-bloquant, retry automatique
- **Erreurs de données :** Alert avec action corrective
- **Erreurs critiques :** Fallback gracieux, jamais de crash

---

## Performance

### Cibles

| Métrique | Cible | Comment mesurer |
|---|---|---|
| Launch time | < 1s | Instruments |
| Scroll FPS | 60fps constant | Instruments |
| Mémoire | < 100MB usage normal | Instruments |
| Taille app | < 30MB | Xcode archive |

### Patterns à appliquer

- `@Query` avec `SortDescriptor` et `#Predicate` (jamais fetch all + filter)
- `LazyVStack` pour les listes longues
- Images optimisées dans Assets catalog
- Pas de `@State` inutile sur les vues parentes

---

## Testing MVP

### Approche pragmatique

| Type | Couverture MVP | Outil |
|---|---|---|
| **Preview** | Toutes les vues | Xcode Previews + sample data |
| **Manual QA** | Happy path complet | Simulator + device physique |
| **Crash monitoring** | 100% post-launch | Xcode Organizer |
| **Unit tests** | Modèles + logique métier critique | XCTest |
| **UI tests** | Happy path seulement | XCUITest (minimal) |

> Règle : pour un MVP micro-app, des previews solides + du testing manuel rigoureux > une suite de tests à 90% de couverture qui retarde le ship de 2 semaines.

---

## Dépendances externes

> **Philosophie : zéro dépendance externe pour le MVP sauf nécessité absolue.**

| Package | Usage | Justification | Risque |
|---|---|---|---|
| [aucun idéalement] | | | |

Si un package est nécessaire, vérifier :
- [ ] Maintenance active (commit < 3 mois)
- [ ] Compatible avec la version iOS ciblée
- [ ] License permissive (MIT, Apache 2.0)
- [ ] Pas de sous-dépendances lourdes

---

## Prochaine étape

✅ Architecture définie → Passer au **template 04 (CLAUDE.md)**
