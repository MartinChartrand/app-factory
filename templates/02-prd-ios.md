# 02 — PRD iOS : [NomApp]

> **Durée estimée :** 45–60 minutes
> **Quand :** Après validation (template 01 = GO)
> **But :** Définir exactement quoi builder pour le MVP — ni plus, ni moins

---

## Identification

| Champ | Valeur |
|---|---|
| **Nom de l'app** | [NomApp] |
| **Bundle ID** | com.martinchartrand.[nomapp] |
| **Catégorie App Store** | [Catégorie principale] / [Catégorie secondaire] |
| **Version MVP** | 1.0.0 |
| **iOS minimum** | 18.0 |
| **Devices MVP** | iPhone uniquement / iPhone + iPad / + Watch |
| **Langues MVP** | 🇫🇷 Français, 🇬🇧 English |
| **Date de validation** | [YYYY-MM-DD] |

---

## Le problème

> [2-3 phrases max. Quel problème concret l'utilisateur a, et pourquoi les solutions actuelles sont insuffisantes.]

## La solution

> [2-3 phrases max. Comment notre app résout ce problème, et ce qui la rend unique.]

---

## Persona utilisateur

**Nom :** [Persona]
**Âge :** [tranche]
**Contexte :** [situation de vie pertinente]
**Frustration principale :** [ce qui fait mal]
**Objectif :** [ce qu'il/elle veut accomplir]
**Comportement mobile :** [comment il/elle utilise son iPhone]

---

## Fonctionnalités MVP

> Règle d'or : si c'est pas essentiel pour que l'app soit utile dès le jour 1, c'est pas dans le MVP.

### Must Have (P0) — Le MVP ne ship pas sans ça

| # | Fonctionnalité | Description courte | Critère de succès |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

### Should Have (P1) — V1.1, rapidement après le launch

| # | Fonctionnalité | Description courte |
|---|---|---|
| 1 | | |
| 2 | | |

### Nice to Have (P2) — Backlog futur

| # | Fonctionnalité | Description courte |
|---|---|---|
| 1 | | |
| 2 | | |

### Explicitement hors scope MVP

> Important : lister ce qu'on fait PAS pour éviter le scope creep.

- ❌ [Feature exclue et pourquoi]
- ❌ [Feature exclue et pourquoi]

---

## Parcours utilisateur principal (Happy Path)

```
Lancement app
    → [Étape 1 : Onboarding / premier écran]
    → [Étape 2 : Action principale]
    → [Étape 3 : Résultat / feedback]
    → [Étape 4 : Boucle de rétention]
```

**Premier lancement (FTUE) :**
> [Comment l'utilisateur comprend l'app en 30 secondes sans tutoriel]

**Usage récurrent :**
> [Pourquoi et quand l'utilisateur revient]

---

## Design & UX

### Principes Apple HIG à respecter

- [ ] Navigation standard iOS (NavigationStack / TabView)
- [ ] SF Symbols pour les icônes
- [ ] Dynamic Type supporté
- [ ] Dark Mode supporté
- [ ] Couleurs sémantiques Apple (pas de hardcoded colors)
- [ ] Accessibilité VoiceOver de base
- [ ] Animations natives SwiftUI (pas de custom excessif)

### Structure de navigation MVP

```
[TabView / NavigationStack]
├── Tab 1 : [Nom] — [Rôle principal]
├── Tab 2 : [Nom] — [Rôle]
├── Tab 3 : [Nom] — [Rôle]
└── Settings (si nécessaire)
```

### Palette de couleurs

| Rôle | Light | Dark | Notes |
|---|---|---|---|
| Accent | [couleur] | [couleur] | Action principale |
| Background | system | system | Couleurs sémantiques |
| Texte | primary | primary | Couleurs sémantiques |

---

## Données & Sync

### Modèle de données principal

| Entité | Champs clés | Persistance |
|---|---|---|
| [Entité 1] | [champs] | SwiftData |
| [Entité 2] | [champs] | SwiftData |

### Stratégie de synchronisation

- [ ] Local seulement (pas de sync)
- [ ] CloudKit sync (même utilisateur, multi-devices)
- [ ] Partage CloudKit (entre utilisateurs)

### Données sensibles

- [ ] Aucune donnée sensible
- [ ] Données financières → encryption locale
- [ ] Données de santé → HealthKit + encryption
- [ ] Autre : [préciser]

---

## Monétisation MVP

**Modèle :** [Gratuit / Freemium / Payant / Abonnement]

### Si Freemium :

| Gratuit | Premium |
|---|---|
| [features gratuites] | [features payantes] |

**Prix :** [montant]
**StoreKit 2 :** [type de produit — consumable, non-consumable, subscription]

---

## Conformité App Store

### App Store Review Guidelines — Points d'attention

- [ ] **4.2** — Design minimum : l'app apporte une valeur réelle
- [ ] **4.3** — Pas de spam/clone : différenciation claire
- [ ] **5.1.1** — Collecte de données : Privacy Nutrition Label exacte
- [ ] **5.1.2** — Utilisation des données conforme à la description
- [ ] **3.1.1** — In-App Purchase pour contenu digital (si applicable)
- [ ] **2.1** — Performance : pas de crash, pas de bug bloquant

### Privacy Nutrition Label

| Type de donnée | Collecté? | Lié à l'identité? | Usage |
|---|---|---|---|
| [type] | Oui/Non | Oui/Non | [fonctionnalité] |

### App Privacy Policy

- [ ] URL de la politique de confidentialité : [URL]
- [ ] Hébergée sur [site perso / GitHub Pages]

---

## Métriques de succès MVP

> Comment on sait si le MVP est un succès?

| Métrique | Cible 30 jours | Comment mesurer |
|---|---|---|
| Downloads | [X] | App Store Connect |
| Rétention J7 | [X]% | App Store Connect |
| Crash-free rate | >99% | Xcode Organizer |
| Note moyenne | ≥4.0 | App Store |
| [Métrique spécifique] | [cible] | [méthode] |

---

## Prochaine étape

✅ PRD complété → Passer au **template 03 (Architecture Swift)**
