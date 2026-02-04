# 🔧 Pipeline de développement iOS

> Ces templates structurent le cycle de vie d'une micro-app iOS, de la validation à l'App Store.
> Ils s'intègrent au workflow existant de l'App Factory.

## Où ça s'insère dans le workflow global

```
App Factory — Workflow complet
══════════════════════════════════════════════════════════

  IDÉATION (existant)              DÉVELOPPEMENT (nouveau)
  ─────────────────────            ──────────────────────────

  💡 Idée (Slack/Discussion)
      │
      ▼
  ⚖️  Grille d'évaluation
      │
      ▼
  📋 BRD (Issue GitHub)
      │
      ▼
  ✅ Go / No-Go
      │
      ╠══════════════════════════════════════════════╗
      ║                                              ║
      ▼                                              ▼
  01-validation.md ──► Confirmer la viabilité    (si KILL → archiver)
      │
      ▼
  02-prd-ios.md ────► Définir le QUOI
      │
      ▼
  03-architecture.md ► Définir le COMMENT
      │
      ▼
  04-CLAUDE-TEMPLATE ► Configurer l'agent AI
      │
      ▼
  05-build-ship.md ─► Exécuter, tester, shipper
      │
      ▼
  🚀 App Store
      │
      ▼
  📊 Post-launch → Décision : continuer / pivoter / archiver
```

## Utilisation

### Pour chaque nouvelle app :

1. **Copier** le dossier `templates/` dans un nouveau dossier `apps/[nomapp]/`
2. **Remplir** les templates dans l'ordre (01 → 05)
3. **Créer** le repo `[nomapp]-ios` quand on arrive au template 05
4. **Copier** le CLAUDE.md rempli + le PRD + l'Architecture dans le repo de l'app
5. **Builder** en suivant le template 05

### Astuce : un template à la fois

Ne pas remplir les 5 templates d'un coup. Chaque template a un checkpoint Go/No-Go.
Si la validation (01) dit KILL, on arrête là. Pas besoin de faire un PRD pour rien.

## Les templates

| # | Fichier | Quoi | Durée |
|---|---|---|---|
| 01 | [validation.md](01-validation.md) | Compétition, faisabilité, marché | 30-45 min |
| 02 | [prd-ios.md](02-prd-ios.md) | Quoi builder, pour qui, MVP scope | 45-60 min |
| 03 | [architecture.md](03-architecture.md) | Structure code, modèles, patterns | 30-45 min |
| 04 | [CLAUDE-TEMPLATE.md](04-CLAUDE-TEMPLATE.md) | Instructions pour Claude Agent Xcode | 15-20 min |
| 05 | [build-ship.md](05-build-ship.md) | Exécution, TestFlight, App Store | 1-4 semaines |

**Total pré-dev (templates 01-04) : ~2-3 heures**
C'est un investissement qui sauve des jours de refactoring.

## Ce que CreditCopilot m'a appris

Ces templates sont basés sur l'expérience concrète de CreditCopilot et des autres apps.
Les "pièges connus" dans le template 04 viennent de vraies pertes de temps.
Le découpage en phases (template 05) évite le pattern "tout coder d'un coup et debugger pendant 2 semaines".
