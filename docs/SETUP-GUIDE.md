# Guide de configuration — GitHub Projects + Slack

## 1. Activer GitHub Discussions

Déjà fait par le script de setup! Les catégories configurées :

| Catégorie | Description | Format |
|---|---|---|
| 💡 Idées | Nouvelles idées d'apps | Open-ended |
| 🔬 Recherche | Analyse de marché, compétition | Open-ended |
| 📣 Annonces | Décisions, lancements, milestones | Announcement |
| 💬 Général | Tout le reste | Open-ended |

## 2. GitHub Projects

Aussi créé par le script! Le board "App Pipeline" contient ces colonnes :

```
💡 Idées → 🔍 Évaluation → 📋 BRD → 🛠️ En dev → 🧪 Testing → 🚀 Shipped → ❌ Archivé
```

## 3. Intégration Slack

### Créer le workspace Slack

1. Créer un workspace gratuit (ou utiliser un existant)
2. Créer les channels :

| Channel | Usage |
|---|---|
| `#idées` | Brainstorm informel, idées brutes |
| `#dev` | Updates de développement, questions techniques |
| `#testing` | Feedback de Sébastien sur TestFlight |
| `#général` | Tout le reste |

### Installer l'app GitHub dans Slack

1. Dans Slack → Apps → chercher **GitHub**
2. Installer l'app
3. Dans le channel `#dev`, taper :
   ```
   /github subscribe MartinChartrand/app-factory issues pulls discussions comments
   ```
4. Dans `#idées`, taper :
   ```
   /github subscribe MartinChartrand/app-factory discussions
   ```

### Commandes Slack utiles

| Commande | Ce que ça fait |
|---|---|
| `/github subscribe owner/repo` | Abonner le channel aux notifications |
| `/github unsubscribe owner/repo` | Désabonner |
| `/github close owner/repo#123` | Fermer une Issue depuis Slack |
| `/github open owner/repo` | Ouvrir le repo dans le browser |

### Créer une Issue depuis un message Slack

1. Hover sur un message dans Slack
2. Cliquer les trois points (⋯) → More message shortcuts
3. Choisir **Create an issue**
4. Sélectionner le repo, ajouter un titre, soumettre

## 4. Inviter Sébastien

1. **GitHub** : Repo → Settings → Collaborators → Add people → son email
2. **Slack** : Workspace → Invite people → son email

## 5. Workflow quotidien

```
SÉBASTIEN                          MARTIN
    │                                  │
    ├─ Idée dans Slack #idées          │
    │                                  ├─ Voit la notification
    │                                  ├─ Crée Issue depuis Slack
    │                                  │   (ou GitHub Discussion)
    ├─ Score l'idée (grille)           ├─ Score l'idée (grille)
    │                                  │
    │         ── Go/No-Go ──           │
    │                                  │
    │                                  ├─ Remplit BRD technique
    ├─ Remplit BRD business            │
    │                                  ├─ Crée repo [app]-ios
    │                                  ├─ Code le MVP
    ├─ Teste sur TestFlight            │
    ├─ Feedback dans #testing          │
    │                                  ├─ Itère
    │                                  ├─ Soumet à l'App Store
    │                                  │
    │         ── 🚀 SHIPPED ──         │
```
