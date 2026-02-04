# Optimisation Slack — Apps-iOS

> Instructions pour restructurer le workspace Slack.
> A faire une seule fois, maintenant.

---

## 1. Restructurer les channels

### Garder (2 channels)

**#pipeline** (renommer #all-apps-ios)
- Tout le workflow : idees, evaluations, dev updates, testing, shipping
- Une thread par idee/app
- C'est LE channel de travail

**#general** (renommer #general)
- Casual, off-topic, liens interessants, jasette

### Supprimer (3 channels)

- #idees → fusionne dans #pipeline
- #dev → fusionne dans #pipeline
- #testing → fusionne dans #pipeline

**Pourquoi :** Avec 2 personnes, 5 channels fragmente les conversations.
Tout doit etre au meme endroit avec des threads pour organiser.

### Comment faire

```
1. Aller dans #all-apps-ios → Settings (gear) → Edit channel
   → Renommer en "pipeline"
   → Description : "Workflow complet : idees, evaluation, dev, testing, shipping"

2. Aller dans #general → verifier que la description est claire
   → Description : "Discussions generales, liens, off-topic"

3. Archiver les channels inutiles :
   #idees → Settings → Archive channel
   #dev → Settings → Archive channel
   #testing → Settings → Archive channel
```

---

## 2. Configurer les bookmarks du channel #pipeline

En haut du channel #pipeline, ajouter des bookmarks :

```
Cliquer "Add bookmark" en haut du channel, ajouter :

1. "Repo App Factory"
   URL : https://github.com/MartinChartrand/app-factory

2. "Templates dev"
   URL : https://github.com/MartinChartrand/app-factory/tree/main/templates

3. "Grille evaluation"
   URL : https://github.com/MartinChartrand/app-factory/blob/main/docs/EVALUATION-GRID.md
```

---

## 3. Creer le Canvas "Comment ca marche"

Dans #pipeline :
1. Cliquer "Add canvas" en haut du channel (a cote de "Messages")
2. Titre : "Comment ca marche"
3. Coller le contenu du fichier QUICK-REF-SEBASTIEN.md
4. Ce canvas sera toujours visible et accessible en un clic

---

## 4. Configurer GitHub dans #pipeline

Si pas deja fait :
```
/github subscribe MartinChartrand/app-factory issues discussions comments
```

Ceci enverra automatiquement dans #pipeline :
- Les nouvelles Issues
- Les nouvelles Discussions
- Les commentaires

---

## 5. Convention de threads dans #pipeline

### Nouvelle idee :

```
Martin ou Seb poste dans #pipeline :

[IDEE] NomApp — description en une ligne

Tout le reste de la discussion sur cette idee
se fait dans la THREAD de ce message.
```

### Quand le statut change, Seb ou Martin repond dans la thread :

```
[EVAL] — En evaluation, scores a venir
[GO] — Approuve, Martin commence le dev
[HOLD] — Bonne idee, pas maintenant
[KILL] — Pas viable, on arrete
[DEV] — En developpement
[BETA] — TestFlight disponible, lien : [url]
[SHIP] — Soumis a l'App Store
```

### Exemples concrets :

```
Martin : [IDEE] BudgetBuddy — app de suivi de budget pour couples
  └── Seb : J'aime ca, le probleme est reel. Mon score : 78/100
  └── Martin : Mon score : 72/100. Moyenne 75. [GO]
  └── Martin : [DEV] — MVP en cours, 2 semaines estimees
  └── Martin : [BETA] — TestFlight : [lien]
  └── Seb : Teste. Le onboarding est confus, le reste est bon.
  └── Martin : Fix pousse, nouvelle build dispo.
  └── Martin : [SHIP] — Soumis a Apple.
```

---

## 6. Note sur le trial Pro

Le workspace est en trial Pro (30 jours). Apres :
- Slack Free garde les 90 derniers jours de messages
- Limite de 10 integrations (GitHub en prend 1)
- Les Canvas restent accessibles
- Les bookmarks restent

C'est suffisant pour 2 personnes. Pas besoin de payer.

---

## Checklist

- [ ] #all-apps-ios renomme en #pipeline
- [ ] #idees archive
- [ ] #dev archive
- [ ] #testing archive
- [ ] Bookmarks ajoutes dans #pipeline
- [ ] Canvas "Comment ca marche" cree dans #pipeline
- [ ] GitHub subscribe configure dans #pipeline
- [ ] Premiere idee postee avec le format [IDEE]
