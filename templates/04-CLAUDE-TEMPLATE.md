# 04 — Template CLAUDE.md : [NomApp]

> **Durée estimée :** 15–20 minutes (remplir les sections spécifiques à l'app)
> **Quand :** Après l'architecture (template 03)
> **But :** Fichier d'instructions pour Claude Agent dans Xcode — copier dans le repo de l'app

---

> ⚠️ **Ce fichier est un TEMPLATE.** Une fois rempli, le sauvegarder comme `CLAUDE.md` à la racine du repo de l'app.

---

```markdown
# CLAUDE.md — [NomApp]

## Identité du projet

- **App :** [NomApp]
- **Bundle ID :** com.martinchartrand.[nomapp]
- **Développeur :** Martin Chartrand
- **Stack :** SwiftUI + SwiftData + CloudKit
- **iOS minimum :** 18.0
- **Xcode :** 26.x
- **Langue du code :** Anglais (noms de variables, commentaires inline)
- **Langue du contenu :** Bilingue FR/EN (Localizable.xcstrings)

---

## Contexte

[2-3 phrases décrivant ce que l'app fait, pour qui, et pourquoi elle existe.
Copier la section "Le problème" + "La solution" du PRD.]

---

## Documents de référence

Avant de coder une feature, consulter dans l'ordre :
1. `docs/PRD-[NomApp]-MVP.md` — Ce qu'on build
2. `docs/Architecture-[NomApp].md` — Comment c'est structuré
3. Ce fichier — Les règles du jeu

---

## Règles absolues

### Tu DOIS toujours :
- Utiliser SwiftUI natif — pas de UIKit wrappers sauf cas extrême documenté
- Utiliser SwiftData pour la persistance — pas de Core Data, pas de SQLite direct
- Utiliser `String(localized:)` pour TOUT texte visible par l'utilisateur
- Utiliser SF Symbols pour les icônes — pas d'images custom sauf assets spécifiques
- Supporter Dark Mode via couleurs sémantiques Apple
- Supporter Dynamic Type — jamais de taille de police hardcodée
- Garder les vues petites — extraire les sous-composants à >40 lignes
- Utiliser `@Query` avec `#Predicate` pour filtrer — jamais fetch all + filter en mémoire
- Commenter le "pourquoi", pas le "quoi"

### Tu ne DOIS JAMAIS :
- Ajouter un package Swift externe sans demander d'abord
- Créer un Coordinator ou Router pattern — utiliser NavigationStack natif
- Utiliser `@ObservableObject` / `@Published` — on est en `@Observable` (iOS 17+)
- Hardcoder des strings visibles — tout passe par la localisation
- Utiliser `print()` pour le debug — utiliser `os.Logger`
- Créer des God Views — une vue = une responsabilité
- Forcer des `try!` ou `as!` — gérer les erreurs proprement
- Ignorer les previews — chaque vue a un `#Preview` fonctionnel

---

## Architecture

### Structure des fichiers

[Copier la structure du template 03-architecture.md une fois remplie]

### Patterns utilisés

- **MVVM léger** : `@Observable` ViewModels seulement quand la logique dépasse 10 lignes dans la vue
- **Repository pattern** : NON — SwiftData + `@Query` directement dans les vues pour le MVP
- **Dependency injection** : Via `.environment()` et `.modelContainer()`
- **Error handling** : `Result` type ou `throws` avec do-catch dans les ViewModels

### Navigation

[Copier le diagramme de navigation du template 03]

---

## Modèles de données

[Copier les @Model du template 03 une fois finalisés]

---

## Conventions de code

### Nommage

```
Vues :          [Nom]View.swift          (DashboardView, ItemDetailView)
Modèles :       [Nom].swift              (Transaction, Category)
ViewModels :    [Nom]ViewModel.swift     (DashboardViewModel)
Extensions :    [Type]+[Sujet].swift     (Date+Formatting.swift)
Services :      [Nom]Service.swift       (NotificationService)
Enums :         [Nom].swift              (AppError, SortOption)
```

### Structure d'une vue type

```swift
struct [Nom]View: View {
    // 1. Environment & Query
    @Environment(\.modelContext) private var context
    @Query private var items: [Item]

    // 2. State
    @State private var isShowingSheet = false

    // 3. Body
    var body: some View {
        // ...
    }

    // 4. Sous-vues extraites (private)
    private var headerSection: some View {
        // ...
    }

    // 5. Méthodes (private)
    private func deleteItem(_ item: Item) {
        // ...
    }
}

// 6. Preview
#Preview {
    [Nom]View()
        .modelContainer(PreviewSampleData.container)
}
```

---

## CloudKit

- **Container :** `iCloud.com.martinchartrand.[nomapp]`
- **Sync :** Automatique via SwiftData
- **Conflits :** Last-write-wins (défaut)
- **App Group :** `group.com.martinchartrand.[nomapp]` (si widget)

---

## Localisation

- **Format :** `Localizable.xcstrings`
- **Langues :** FR (base) + EN
- **Convention de clés :** `[ecran].[element].[description]`
- **Règle :** Jamais de string littérale dans les vues

---

## Pièges connus

> Choses qui m'ont fait perdre du temps sur des projets précédents :

1. **SwiftData + CloudKit :** Les propriétés optionnelles dans `@Model` sont obligatoires pour CloudKit sync. Toujours utiliser des valeurs par défaut ou des optionnels.
2. **@Query dans les sous-vues :** Attention aux re-renders. Préférer passer les données en paramètre plutôt que re-query dans chaque sous-vue.
3. **NavigationStack path :** Toujours utiliser un `NavigationPath` typé pour éviter les bugs de navigation programmatique.
4. **Preview crashes :** Toujours fournir un `ModelContainer` dans les previews. Utiliser `PreviewSampleData.container`.
5. **Widgets + SwiftData :** Le widget ne peut pas utiliser directement le même ModelContainer. Passer par App Group + UserDefaults ou un store séparé.
6. **Entitlements oubliés :** iCloud, Push Notifications, App Groups — vérifier que tout est activé dans Signing & Capabilities.
7. [Ajouter les pièges spécifiques à cette app au fil du développement]

---

## Contexte spécifique à cette app

[Section à enrichir pendant le développement — noter ici les décisions prises, les compromis, les choses que Claude doit savoir pour rester cohérent]

---

## Commandes utiles

```bash
# Build & run
Cmd+R

# Previews
Cmd+Option+Enter

# Clean build folder (quand ça fait des siennes)
Cmd+Shift+K

# Simulateur: reset données
Device → Erase All Content and Settings
```
```

---

## Prochaine étape

✅ CLAUDE.md créé et copié dans le repo de l'app → Passer au **template 05 (Build & Ship)**
