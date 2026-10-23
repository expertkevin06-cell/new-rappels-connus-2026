# DTC Diag Pro — PWA diagnostic OBD

21 000 fiches DTC • pannes connues par marque/modèle/motorisation/puissance • campagnes de rappels 2017-2026 • mode admin • accès tiers • mise à jour à distance.

## Identifiants
- Admin : `admin` / `Kevin83600` (modifiable dans Administration → Sécurité)
- Tiers démo : `TIERS-DEMO-2026` (autres codes créés par l'admin)

## Déploiement GitHub (propre)
1. Créer/vider le dépôt, puis uploader TOUS les fichiers de ce projet à la racine.
2. Générer les icônes si absentes : ouvrir `tools/generate-icons.html` → bouton → placer les 3 PNG dans `assets/icons/`.
3. Settings → Pages → Source : Deploy from a branch → `main` / `(root)` → Save.
4. Site : `https://<user>.github.io/<repo>/` (vérifier `/manifest.json` et une icône PNG).
5. PWABuilder : coller l'URL → Package For Stores → Android → Package ID (ex. `com.kevin.dtcdiag`) → Generate → APK/AAB + assetlinks à mettre dans `.well-known/`.

## Mise à jour des données (admin uniquement)
Administration → 📦 Mise à jour APK :
- soit télécharger `update-pack.json` + `update.json` et les committer (`data/` et racine),
- soit publication directe via jeton GitHub (scope `repo`).
Tous les utilisateurs (tiers compris) appliquent le pack automatiquement au lancement.

## Structure
- `js/data.js` : moteur 21 000 fiches + catalogue véhicules 2017-2026
- `js/recalls.js` : campagnes de rappels (réelles + générées + personnalisées)
- `js/updater.js` : canal de mise à jour
- `js/app.js` : interface (recherche, codes, véhicules, rappels, admin)

## Notes
- HTTPS obligatoire (Pages OK). Le service worker est « réseau d'abord » : les déploiements sont visibles immédiatement.
- `update.json` et `data/` ne sont jamais mis en cache.
