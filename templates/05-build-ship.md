# 05 — Build & Ship : [NomApp]

> **Durée estimée :** Variable (1-4 semaines selon la complexité)
> **Quand :** Après CLAUDE.md (template 04) placé dans le repo de l'app
> **But :** Exécuter le build de façon structurée, tester, et shipper sur l'App Store

---

## Phase A : Setup du repo

### Checklist de démarrage

- [ ] Repo créé : `[nomapp]-ios` sur GitHub
- [ ] `.gitignore` Swift/Xcode en place
- [ ] Projet Xcode initialisé avec le bon Bundle ID
- [ ] `CLAUDE.md` copié à la racine du repo (depuis template 04)
- [ ] `docs/PRD-[NomApp]-MVP.md` copié dans le repo (depuis template 02)
- [ ] `docs/Architecture-[NomApp].md` copié dans le repo (depuis template 03)
- [ ] Entitlements configurés (iCloud, App Groups, etc.)
- [ ] CloudKit container créé dans le Developer Portal
- [ ] Signing & Capabilities vérifiés

---

## Phase B : Plan d'implémentation

> Avant de coder quoi que ce soit, découper le MVP en phases séquentielles.

### Découpage en phases

| Phase | Quoi | Dépend de | Estimé |
|---|---|---|---|
| **B1** — Modèles | @Model SwiftData + PreviewSampleData | Rien | [X] jours |
| **B2** — Navigation | Structure TabView/NavigationStack | B1 | [X] jours |
| **B3** — Vues principales | Écrans du happy path | B1 + B2 | [X] jours |
| **B4** — Logique métier | Calculs, règles, services | B1 | [X] jours |
| **B5** — CloudKit sync | Activer sync + tester multi-device | B1-B4 | [X] jours |
| **B6** — Localisation | FR + EN complet | B3 | [X] jours |
| **B7** — Widget | Si applicable | B1 + B4 | [X] jours |
| **B8** — Polish | Animations, edge cases, empty states | Tout | [X] jours |

### Prompt de démarrage pour Claude Agent

> Coller ce prompt dans Xcode Claude Agent au début de chaque session :

```
Lis CLAUDE.md, puis docs/PRD-[NomApp]-MVP.md et docs/Architecture-[NomApp].md.
Résume les 3 points clés de chaque document pour confirmer ta compréhension.
Ensuite, on attaque la phase [BX] : [description].
Propose un plan d'implémentation avant de coder.
```

---

## Phase C : Boucle de développement

> Répéter pour chaque phase (B1 à B8).

### Cycle Plan → Code → Verify

```
┌─────────────────────────────────────────┐
│                                         │
│   1. PLAN                               │
│   Claude propose l'implémentation       │
│   Tu valides ou ajustes                 │
│                                         │
│   2. CODE                               │
│   Claude implémente                     │
│   Commits atomiques par feature         │
│                                         │
│   3. VERIFY                             │
│   ✅ Build compile sans warning          │
│   ✅ Previews fonctionnent               │
│   ✅ Happy path fonctionne sur Simulator │
│   ✅ Dark Mode vérifié                   │
│   ✅ Dynamic Type vérifié                │
│   ❌ Si échec → retour à 1. PLAN        │
│                                         │
│   4. COMMIT                             │
│   Message format: "feat: [description]" │
│   Push sur main                         │
│                                         │
└─────────────────────────────────────────┘
```

### Convention de commits

```
feat:     Nouvelle fonctionnalité
fix:      Correction de bug
refactor: Refactoring sans changement fonctionnel
style:    Changement visuel/UI
docs:     Documentation
chore:    Config, build, dépendances
```

### Checkpoints réguliers

Après chaque phase complétée :

- [ ] Tout compile sans warnings
- [ ] Toutes les previews affichent correctement
- [ ] Test manuel du happy path sur Simulator
- [ ] Test Dark Mode
- [ ] Test sur device physique (au moins 1x par phase)
- [ ] Git push

---

## Phase D : TestFlight Beta

### Préparation

- [ ] Version 1.0.0 (build 1) dans Xcode
- [ ] App icon finalisée (1024x1024)
- [ ] Launch screen configuré
- [ ] Archive : Product → Archive
- [ ] Upload vers App Store Connect
- [ ] Groupe de test interne créé

### Testeurs

| Nom | Rôle | Focus de testing |
|---|---|---|
| Martin | Dev | Edge cases, performance, crash |
| Sébastien | Utilisateur | UX, clarté, utilité, flow |
| [Autre] | [Rôle] | [Focus] |

### Feedback template pour Sébastien

> Envoyer ce template à Sébastien avec le lien TestFlight :

```
TestFlight: [NomApp] v1.0.0

À tester :
1. [Scénario principal]
2. [Scénario secondaire]
3. Navigation générale

Feedback recherché :
- C'est clair ce que l'app fait dès le premier écran?
- Le flow principal est intuitif?
- Quelque chose de frustrant ou confus?
- Ça vaut le prix de [X]$?
- Tu l'utiliserais vraiment?
```

### Cycles de beta

| Cycle | Build | Focus | Feedback | Statut |
|---|---|---|---|---|
| Beta 1 | 1 | Happy path, premières impressions | | ⬜ |
| Beta 2 | 2 | Fixes du cycle 1 + edge cases | | ⬜ |
| Beta 3 | 3 | Polish final | | ⬜ |

> **Règle :** Minimum 2 cycles de beta avant soumission. Maximum 4 (sinon c'est du scope creep).

---

## Phase E : Soumission App Store

### Pré-soumission

#### Métadonnées App Store Connect

- [ ] **Nom de l'app** (max 30 caractères) : [nom]
- [ ] **Sous-titre** (max 30 caractères) : [sous-titre]
- [ ] **Catégorie principale** : [catégorie]
- [ ] **Catégorie secondaire** : [catégorie]
- [ ] **URL de confidentialité** : [URL]
- [ ] **URL de support** : [URL]

#### Description

- [ ] **Description FR** (max 4000 caractères) — rédigée
- [ ] **Description EN** (max 4000 caractères) — rédigée
- [ ] **Keywords FR** (max 100 caractères, séparés par virgule)
- [ ] **Keywords EN** (max 100 caractères, séparés par virgule)
- [ ] **What's New** : "Version initiale de [NomApp]."

#### Visuels

- [ ] **Screenshots iPhone 6.9"** (iPhone 16 Pro Max) — min 3, max 10
- [ ] **Screenshots iPhone 6.7"** (si différent)
- [ ] **Screenshots iPad** (si applicable)
- [ ] **App Preview vidéo** (optionnel, max 30 secondes)

#### Review

- [ ] **Notes for Review** : explication claire si l'app nécessite un compte ou du contenu spécifique
- [ ] **Demo account** : si login requis, fournir des credentials de test
- [ ] **App Review contact** : email + téléphone

#### Vérifications finales

- [ ] Privacy Nutrition Labels remplis et exacts
- [ ] Pas de fonctionnalité utilisant des APIs privées
- [ ] Pas de mention de plateformes concurrentes dans la description
- [ ] Prix / In-App Purchases configurés dans App Store Connect
- [ ] Disponibilité géographique confirmée (Canada + tous pays, ou sélection)
- [ ] Rating age configuré (questionnaire Apple)
- [ ] Build uploadé et processing terminé

### Soumission

- [ ] Soumettre pour Review
- [ ] **Date de soumission :** [YYYY-MM-DD]
- [ ] **Statut :** Waiting for Review → In Review → Approved / Rejected

### Si rejeté

| Motif de rejet | Action corrective | Statut |
|---|---|---|
| [motif] | [correction] | ⬜ |

---

## Phase F : Post-launch

### Jour 1-7

- [ ] Vérifier les crash reports dans Xcode Organizer
- [ ] Monitorer les premiers avis
- [ ] Répondre aux avis (surtout les négatifs constructifs)
- [ ] Partager le lien sur les réseaux si pertinent

### Jour 7-30

- [ ] Analyser les métriques (template 02 — Métriques de succès)
- [ ] Recueillir le feedback de Sébastien sur l'usage réel
- [ ] Prioriser le backlog v1.1 basé sur les données

### Décision post-MVP

- [ ] 🚀 **Continuer** — Métriques positives, feedback bon → planifier v1.1
- [ ] 🔄 **Pivoter** — L'app a du potentiel mais pas dans cette direction
- [ ] 🗄️ **Archiver** — Pas de traction, pas de demande → passer à la prochaine idée

---

## Retrospective

> À remplir après le ship. Nourrit les futurs projets.

**Ce qui a bien marché :**
- [point 1]
- [point 2]

**Ce qui a été plus difficile que prévu :**
- [point 1]
- [point 2]

**Temps réel vs estimé :**
| Phase | Estimé | Réel | Écart |
|---|---|---|---|
| Setup → Code | | | |
| Code → TestFlight | | | |
| TestFlight → App Store | | | |
| **Total** | | | |

**Leçons pour le prochain projet :**
> [insights concrets à appliquer]
