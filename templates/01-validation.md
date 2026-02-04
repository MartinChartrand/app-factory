# 01 — Validation rapide

> **Durée estimée :** 30–45 minutes
> **Quand :** Après qu'une idée passe le Go/No-Go sur la grille d'évaluation
> **But :** Confirmer que ça vaut la peine d'investir du temps de dev

---

## Identité de l'app

- **Nom de travail :** [NomApp]
- **Tagline (une phrase) :** [Ce que l'app fait pour qui]
- **Date de validation :** [YYYY-MM-DD]
- **Évaluateurs :** Martin / Sébastien

---

## 1. Analyse de la compétition App Store

Chercher directement dans l'App Store (pas Google — les résultats web et iOS sont différents).

| App concurrente | Prix / Modèle | Note ⭐ | # Avis | Forces | Faiblesses |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |
| | | | | | |

**Mots-clés recherchés dans l'App Store :**
- [ ] [mot-clé 1]
- [ ] [mot-clé 2]
- [ ] [mot-clé 3]

**Constat compétition :**
- [ ] 🟢 Peu de compétition directe — opportunité claire
- [ ] 🟡 Compétition présente mais faiblesses exploitables
- [ ] 🔴 Marché saturé — différenciation difficile

**Notre angle de différenciation :**
> [En quoi notre approche est différente / meilleure]

---

## 2. Faisabilité technique Apple

### Frameworks requis

| Framework | Usage | Maîtrise actuelle | Risque |
|---|---|---|---|
| SwiftUI | UI | ✅ Connu | Faible |
| SwiftData | Persistance | ✅ Connu | Faible |
| CloudKit | Sync | ✅ Connu | Faible |
| [Autre] | [Usage] | [?] | [?] |

### APIs & Capabilities

- [ ] Nécessite des APIs Apple non-standard? Lesquelles?
- [ ] Entitlements spéciaux requis? (HealthKit, Push, In-App Purchase, etc.)
- [ ] Données sensibles? (santé, finances, localisation)
- [ ] Accès réseau requis au-delà de CloudKit?
- [ ] Compatible avec iOS [version minimum ciblée]?
- [ ] Widgets pertinents? (WidgetKit)
- [ ] Watch/iPad pertinent pour le MVP?

### Risques techniques identifiés

| Risque | Impact | Mitigation |
|---|---|---|
| | | |
| | | |

**Verdict faisabilité :**
- [ ] 🟢 100% dans notre stack — aucun inconnu
- [ ] 🟡 1-2 éléments nouveaux mais documentés
- [ ] 🔴 Dépendances majeures non maîtrisées

---

## 3. Dimensionnement du marché

> Pour une micro-app iOS, on cherche pas un TAM de 1B$. On cherche un créneau viable.

**Public cible :** [Qui exactement]
**Taille estimée du segment :** [ordre de grandeur]
**Fréquence d'utilisation prévue :** quotidien / hebdomadaire / ponctuel
**Rétention :** Qu'est-ce qui ramène l'utilisateur?

### Signaux de demande

- [ ] Recherches Reddit / forums montrant le besoin
- [ ] Avis négatifs sur apps concurrentes pointant vers notre angle
- [ ] Tendance identifiable (réglementaire, sociale, technologique)
- [ ] Expérience personnelle directe du problème

---

## 4. Modèle de monétisation

| Modèle | Applicable? | Revenu estimé / utilisateur |
|---|---|---|
| Gratuit (portfolio / vitrine) | | |
| Freemium (core gratuit + premium) | | |
| Payant upfront | | |
| Abonnement | | |
| Tips / Pourboires | | |

**Modèle retenu :** [choix]
**Prix envisagé :** [montant]
**Justification :** [pourquoi ce modèle pour cette app]

---

## 5. Effort estimé

| Phase | Durée estimée |
|---|---|
| PRD + Architecture | [X] jours |
| MVP dev | [X] semaines |
| TestFlight beta | [X] semaines |
| Polish + soumission | [X] jours |
| **Total idée → App Store** | **[X] semaines** |

---

## Décision finale

| Critère | Score |
|---|---|
| Compétition | 🟢 🟡 🔴 |
| Faisabilité technique | 🟢 🟡 🔴 |
| Marché / demande | 🟢 🟡 🔴 |
| Monétisation claire | 🟢 🟡 🔴 |
| Effort raisonnable | 🟢 🟡 🔴 |

**Verdict :**
- [ ] ✅ **GO** — Passer au PRD (template 02)
- [ ] ⏸️ **HOLD** — Idée intéressante mais pas maintenant
- [ ] ❌ **KILL** — Pas viable, archiver

**Notes de décision :**
> [Pourquoi on y va ou non, contexte important à garder]
