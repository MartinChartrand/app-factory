# App Factory — Guide rapide (Martin)

Tout se passe dans #pipeline. Une thread par idee.

---

## Ton role

Tu es le cote technique et operations. Sebastien est le cote business et utilisateur.
Tu evalues la faisabilite, tu build, tu ship.

---

## Le pipeline complet

```
IDEE → EVAL → GO/KILL → VALIDATION → PRD → ARCHITECTURE → CLAUDE.md → DEV → BETA → SHIP
```

Les 4 etapes entre GO et DEV utilisent les templates dans app-factory/templates/.

---

## Ce que tu fais a chaque etape

### [IDEE] — Nouvelle idee (toi ou Seb)

Poste dans #pipeline :
```
[IDEE] NomApp — description courte
```

### [EVAL] — Evaluation conjointe

Partage le lien vers la grille d'evaluation dans la thread.
Vous scorez chacun. Moyenne des deux.

Ton focus pour le scoring :
- Faisabilite technique (APIs Apple, frameworks requis)
- Effort estime vs valeur potentielle
- Complexite de la maintenance long terme
- Risques App Store Review

Poste le verdict dans la thread : [GO], [HOLD], ou [KILL]

### [GO] → Pipeline de dev

C'est ici que les templates rentrent en jeu :

```
1. Copier templates/ dans apps/[nomapp]/
2. Remplir 01-validation.md   (30-45 min)
   → Si KILL, poster [KILL] dans la thread, arreter
3. Remplir 02-prd-ios.md      (45-60 min)
4. Remplir 03-architecture.md (30-45 min)
5. Remplir 04-CLAUDE-TEMPLATE (15-20 min)
6. Creer le repo [nomapp]-ios sur GitHub
7. Copier CLAUDE.md + PRD + Architecture dans le repo
8. Poster [DEV] dans la thread
```

### [DEV] — Build

Suivre le template 05-build-ship.md :
- Setup repo et Xcode
- Decoupage en phases (B1 a B8)
- Boucle Plan → Code → Verify par phase
- Commits atomiques

Updates dans la thread au besoin (pas obligatoire a chaque commit).

### [BETA] — TestFlight

Poster dans la thread :
```
[BETA] — TestFlight dispo, lien : [url]
A tester : [scenarios principaux]
```

Integrer le feedback de Seb. Minimum 2 cycles beta.

### [SHIP] — Soumission

Suivre la checklist App Store (template 05, Phase E).
Poster dans la thread :
```
[SHIP] — Soumis a Apple
```

Puis quand approuve :
```
[SHIP] — Live sur l'App Store : [lien]
```

---

## Les labels

```
[IDEE]  — Nouvelle idee soumise
[EVAL]  — En cours d'evaluation
[GO]    — Approuve, pipeline de dev demarre
[HOLD]  — Bonne idee, pas maintenant
[KILL]  — Pas viable, archiver
[DEV]   — En developpement
[BETA]  — TestFlight pret
[SHIP]  — Soumis / live sur l'App Store
```

---

## Checklist mentale par idee

```
[ ] Idee postee dans #pipeline avec [IDEE]
[ ] Grille remplie par les deux
[ ] Verdict poste dans la thread
[ ] Si GO : templates 01-04 remplis dans apps/[nomapp]/
[ ] Repo [nomapp]-ios cree
[ ] CLAUDE.md + docs copies dans le repo
[ ] [DEV] poste
[ ] MVP code et teste
[ ] [BETA] poste avec lien TestFlight
[ ] Feedback Seb integre (min 2 cycles)
[ ] [SHIP] poste
[ ] Retrospective remplie (template 05)
```

---

## Liens rapides

- Repo : github.com/MartinChartrand/app-factory
- Templates : app-factory/templates/
- Grille : app-factory/docs/EVALUATION-GRID.md
- BRD template : app-factory/docs/BRD-TEMPLATE.md
