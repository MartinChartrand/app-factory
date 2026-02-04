# Workflow — App Factory

> Version 1.0 — Fevrier 2026
> Martin Chartrand & Sebastien Doyon

---

## Vue d'ensemble

App Factory est un pipeline pour transformer des idees en micro-applications iOS
publiees sur l'App Store.

Deux roles :
- **Sebastien** — Ideation, evaluation marche, testing utilisateur, feedback
- **Martin** — Evaluation technique, developpement, App Store, operations

Un seul outil de communication : **Slack (#pipeline)**
Un seul repo de documentation : **GitHub (app-factory)**

---

## Le pipeline

```
[IDEE] → [EVAL] → [GO] → [DEV] → [BETA] → [SHIP]
                     |
                   [HOLD] ou [KILL]
```

Chaque idee vit dans une thread Slack dediee.
Chaque changement de statut est poste avec son label dans la thread.

---

## Etape par etape

### 1. [IDEE] — Quelqu'un a une idee

**Qui :** Martin ou Sebastien
**Ou :** Message dans #pipeline
**Format :**
```
[IDEE] NomApp — le probleme que ca resout en une phrase
```
**Duree :** 2 minutes

Tout le monde peut poster une idee a tout moment.
La discussion commence dans la thread de ce message.

---

### 2. [EVAL] — On evalue ensemble

**Qui :** Les deux
**Ou :** Thread de l'idee dans #pipeline
**Outil :** Grille d'evaluation (bookmarks du channel ou docs/EVALUATION-GRID.md)
**Duree :** 15-20 minutes chacun

Chacun score l'idee sur 100 points. On fait la moyenne.

| Score moyen | Decision |
|---|---|
| 70 et plus | Probablement [GO] |
| 50 a 69 | Discussion. [GO] si conviction forte, sinon [HOLD] |
| Moins de 50 | [KILL] |

**Sebastien evalue :**
- Le probleme est reel et frequent
- Le marche existe
- Les gens paieraient
- Les concurrents sont faibles ou absents

**Martin evalue :**
- Faisable avec le stack actuel (SwiftUI/SwiftData/CloudKit)
- Effort raisonnable pour un MVP
- Pas de risque App Store Review
- Maintenable a long terme

**Poster le verdict dans la thread :**
```
[GO] — Score moyen : 76. On y va.
[HOLD] — Score moyen : 62. Bonne idee, on garde pour plus tard.
[KILL] — Score moyen : 41. Pas viable.
```

---

### 3. [GO] → Pipeline technique (Martin seulement)

**Qui :** Martin
**Ou :** Repo app-factory, dossier apps/[nomapp]/
**Duree :** 2-3 heures pour les templates 01-04

Etapes :

```
a) Creer le dossier apps/[nomapp]/ dans app-factory
b) Copier les 5 templates depuis templates/
c) Remplir 01-validation.md
   → Si le verdict est KILL, poster [KILL] dans la thread et arreter
d) Remplir 02-prd-ios.md
e) Remplir 03-architecture.md
f) Remplir 04-CLAUDE-TEMPLATE.md
g) Creer le repo GitHub : [nomapp]-ios
h) Copier dans le repo de l'app :
   - CLAUDE.md (depuis le template 04 rempli)
   - docs/PRD-[NomApp]-MVP.md (depuis template 02)
   - docs/Architecture-[NomApp].md (depuis template 03)
i) Poster [DEV] dans la thread Slack
```

**Important :** Le template 01-validation est un deuxieme filtre.
Meme apres un [GO] a l'etape 2, la validation technique peut reveler
que l'idee est pas viable. C'est normal et c'est le but.

---

### 4. [DEV] — Martin build le MVP

**Qui :** Martin
**Ou :** Repo [nomapp]-ios, Xcode avec Claude Agent
**Reference :** Template 05-build-ship.md
**Duree :** 1-4 semaines selon complexite

Cycle par phase :
```
PLAN → CODE → VERIFY → COMMIT
```

Martin poste des updates dans la thread Slack au besoin.
Pas obligatoire a chaque commit — juste les milestones importants.

---

### 5. [BETA] — Sebastien teste

**Qui :** Martin prepare, Sebastien teste
**Ou :** TestFlight + thread Slack
**Duree :** 1-2 semaines (minimum 2 cycles)

Martin poste dans la thread :
```
[BETA] — TestFlight dispo
Lien : [url TestFlight]
A tester : [scenarios principaux]
```

Sebastien installe via TestFlight et teste pendant quelques jours.

**Feedback attendu de Sebastien :**
1. C'est clair ce que l'app fait des le premier ecran?
2. Le flow principal est intuitif?
3. Quelque chose de frustrant ou confus?
4. Ca vaut le prix demande?
5. Tu l'utiliserais vraiment?

Sebastien poste son feedback dans la thread. Direct et honnete.

Martin integre le feedback, pousse une nouvelle build.
Minimum 2 cycles avant soumission.

---

### 6. [SHIP] — Soumission App Store

**Qui :** Martin
**Ou :** App Store Connect
**Reference :** Template 05-build-ship.md, Phase E

Martin poste dans la thread :
```
[SHIP] — Soumis a Apple
```

Quand approuve :
```
[SHIP] — Live sur l'App Store : [lien]
```

Si rejete, Martin poste le motif et la correction prevue dans la thread.

---

### 7. Post-launch

**Qui :** Les deux
**Duree :** 30 jours d'observation

- Martin monitore les crash reports et les metriques
- Sebastien monitore les avis App Store
- Decision conjointe : continuer (v1.1), pivoter, ou archiver
- Martin remplit la retrospective (template 05)

---

## Structure des fichiers

```
app-factory/
├── docs/
│   ├── BRD-TEMPLATE.md            # Template business requirements
│   ├── EVALUATION-GRID.md         # Grille de scoring
│   ├── WORKFLOW-GUIDE.md          # Ce document
│   ├── SLACK-OPTIMIZATION.md      # Config Slack
│   ├── QUICK-REF-SEBASTIEN.md     # Reference rapide Seb
│   ├── QUICK-REF-MARTIN.md        # Reference rapide Martin
│   ├── SETUP-GUIDE.md             # Guide initial
│   └── APP-LAUNCH-CHECKLIST.md    # Checklist pre-launch
├── templates/                     # Templates de dev (01 a 05)
│   ├── README.md
│   ├── 01-validation.md
│   ├── 02-prd-ios.md
│   ├── 03-architecture.md
│   ├── 04-CLAUDE-TEMPLATE.md
│   └── 05-build-ship.md
├── apps/                          # Un dossier par app
│   └── [nomapp]/                  # Templates remplis pour cette app
└── README.md
```

---

## Slack

### Channels

| Channel | Usage |
|---|---|
| **#pipeline** | Tout le workflow. Une thread par idee. |
| **#general** | Casual, off-topic, liens. |

### Labels

```
[IDEE]  — Nouvelle idee
[EVAL]  — En evaluation
[GO]    — Approuve
[HOLD]  — Reporte
[KILL]  — Abandonne
[DEV]   — En developpement
[BETA]  — En test (TestFlight)
[SHIP]  — Soumis ou live
```

### Regle d'or

Une thread par idee. Tout dans la thread.
Les labels dans la thread, pas dans des channels separes.
