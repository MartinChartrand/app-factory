# 🏭 App Factory — Martin & Sébastien

Repo central pour le pipeline d'idéation, d'évaluation et de développement de micro-applications iOS.

## Comment ça marche

| Étape | Où | Qui |
|---|---|---|
| **Idée brute** | Slack `#idées` → GitHub Discussion | Sébastien / Martin |
| **Évaluation** | GitHub Discussion (grille dans `/docs`) | Les deux |
| **BRD** | GitHub Issue (template structuré) | Les deux |
| **Développement** | Repo dédié par app | Martin |
| **Testing** | TestFlight | Sébastien |
| **Release** | App Store | Martin |

## Structure du repo

```
app-factory/
├── .github/
│   └── ISSUE_TEMPLATE/        # Templates d'Issues (idée, feature, bug)
├── docs/
│   ├── BRD-TEMPLATE.md        # Business Requirements Document template
│   ├── EVALUATION-GRID.md     # Grille d'évaluation des idées
│   ├── SETUP-GUIDE.md         # Config GitHub Projects + Slack
│   └── APP-LAUNCH-CHECKLIST.md # Checklist pré-lancement App Store
├── apps/
│   └── [nom-app]/             # Dossier par app (liens, notes, assets)
└── README.md
```

## Rôles

**Sébastien** — Idéation, validation de concept, testing utilisateur, feedback UX, perspectives marché
**Martin** — Architecture technique, développement SwiftUI/SwiftData, App Store, infrastructure

## Liens rapides

- [📋 Project Board](../../projects) — Pipeline des apps
- [💬 Discussions](../../discussions) — Brainstorm et évaluations
- [📖 Template BRD](docs/BRD-TEMPLATE.md)
- [⚖️ Grille d'évaluation](docs/EVALUATION-GRID.md)

## Stack technique commun

- **UI**: SwiftUI
- **Data**: SwiftData + CloudKit Sync
- **Minimum**: iOS 17+
- **Modèle**: Freemium / micro-apps ciblées
- **Dev**: Xcode + Claude (Max / agent)
- **CI/CD**: Xcode Cloud (éventuellement)

## Convention de nommage des repos

Chaque app qui passe en développement obtient son propre repo :
`nomapp-ios` (ex: `creditcopilot-ios`, `clearpath-ios`)

Ce repo-ci reste le hub d'idéation et de documentation commune.
