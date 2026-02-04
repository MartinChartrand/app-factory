# Checklist pré-lancement App Store

À compléter pour chaque app avant soumission à Apple.

---

## Identité de l'app

- [ ] Nom final confirmé
- [ ] Bundle ID créé dans Apple Developer Portal
- [ ] Icône d'app (1024x1024, pas de transparence, pas de coins arrondis)
- [ ] Catégorie App Store choisie (primaire + secondaire)

## App Store Connect

- [ ] Screenshots iPhone (6.7" et 6.1" minimum)
- [ ] Screenshots iPad (si Universal)
- [ ] Description courte (30 caractères max — subtitle)
- [ ] Description longue (4000 caractères max)
- [ ] Mots-clés (100 caractères max, séparés par virgules)
- [ ] URL de support (peut être une page GitHub)
- [ ] URL politique de confidentialité (obligatoire)
- [ ] App Privacy questionnaire rempli (App Store Connect)

## Qualité

- [ ] Testé sur TestFlight par Sébastien
- [ ] Feedback intégré et issues fermées
- [ ] Aucun crash reproductible
- [ ] Testé sur au moins 2 tailles d'écran
- [ ] Mode sombre vérifié
- [ ] Dynamic Type vérifié (accessibilité)
- [ ] VoiceOver testé (minimum fonctionnel)
- [ ] Performance acceptable (pas de lag, pas de memory leaks évidents)

## Technique

- [ ] Scheme réglé sur Release (pas Debug)
- [ ] Clés API / secrets pas hardcodés
- [ ] Analytics / crash reporting en place (si applicable)
- [ ] CloudKit container en production (pas development)
- [ ] Version et build number incrémentés

## Monétisation

- [ ] In-App Purchases configurés dans App Store Connect (si applicable)
- [ ] Paywall testé en sandbox
- [ ] Restore Purchases fonctionnel
- [ ] Prix vérifié dans toutes les régions ciblées

## Légal

- [ ] Politique de confidentialité publiée
- [ ] Conditions d'utilisation (si abonnement)
- [ ] EULA custom (si nécessaire, sinon Apple standard)
- [ ] Pas de contenu sous copyright non autorisé

## Post-lancement

- [ ] Vérifier le statut de review quotidiennement
- [ ] Préparer réponse aux premiers avis
- [ ] Monitorer crash reports dans Xcode / App Store Connect
- [ ] Planifier la v1.1 basée sur le feedback réel
