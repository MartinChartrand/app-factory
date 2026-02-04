# App Factory — Guide rapide (Sebastien)

Tout se passe dans #pipeline. Une thread par idee.

---

## Ton role

Tu es le cote business et utilisateur. Martin est le cote technique.
Tu trouves les idees, tu evalues le marche, tu testes les apps, tu donnes du feedback.

---

## Le pipeline en 30 secondes

```
IDEE → EVAL → GO/KILL → DEV → BETA → SHIP
```

Chaque etape a un label. Quand le statut change, on le poste dans la thread.

---

## Ce que tu fais a chaque etape

### [IDEE] — Tu as une idee

Poste dans #pipeline :
```
[IDEE] NomApp — description courte du probleme que ca resout
```
C'est tout. Martin va voir et repondre dans la thread.

### [EVAL] — On evalue ensemble

Martin va partager la grille d'evaluation (lien dans les bookmarks).
Vous scorez chacun sur 100 points. Moyenne des deux scores.

- 70+ : probablement [GO]
- 50-69 : [HOLD] ou discussion
- Moins de 50 : [KILL]

Ton focus pour le scoring :
- Le probleme est-il reel? Les gens en souffrent?
- Les apps existantes sont-elles bonnes ou nulles?
- Est-ce que TU utiliserais cette app?
- Le modele de prix est-il realiste?

### [GO] — On y va

Martin prend le relai technique. Toi tu attends le [BETA].
Tu peux suivre les updates dans la thread si ca t'interesse.

### [BETA] — Tu testes

Martin va poster un lien TestFlight dans la thread.
Installe l'app via TestFlight et teste pendant quelques jours.

Ton feedback doit couvrir :
1. C'est clair ce que l'app fait des le premier ecran?
2. Le flow principal est intuitif?
3. Quelque chose de frustrant ou confus?
4. Ca vaut le prix demande?
5. Tu l'utiliserais vraiment au quotidien?

Poste ton feedback dans la thread. Sois honnete et direct.

### [SHIP] — C'est live

Martin soumet a Apple. Tu peux aider avec :
- Relecture de la description App Store
- Idees de screenshots
- Partage dans ton reseau si pertinent

---

## Les labels

```
[IDEE]  — Nouvelle idee soumise
[EVAL]  — En cours d'evaluation
[GO]    — Approuve, on build
[HOLD]  — Bonne idee, pas maintenant
[KILL]  — Pas viable
[DEV]   — Martin code
[BETA]  — TestFlight pret, teste!
[SHIP]  — Soumis / live sur l'App Store
```

---

## Liens utiles

- Repo : github.com/MartinChartrand/app-factory
- Grille d'evaluation : dans les bookmarks du channel
- TestFlight : Martin t'enverra les liens dans les threads

---

## En resume

1. Tu as une idee → poste [IDEE] dans #pipeline
2. On evalue ensemble → grille de scoring
3. Si [GO] → Martin build, tu attends [BETA]
4. Tu testes → feedback honnete dans la thread
5. On ship
