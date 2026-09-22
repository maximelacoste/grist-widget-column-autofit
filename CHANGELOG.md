# Changelog

Toutes les évolutions notables de ce widget sont consignées ici.
Format : [Keep a Changelog](https://keepachangelog.com/fr/1.1.0/) — versionnement : [SemVer](https://semver.org/lang/fr/).

## [Non publié]

## [1.0.0] — 2026-09-22

### Ajouté
- Choix de la vue à ajuster parmi toutes les vues tableau du document, groupées par page, et les tables en données brutes.
- Mesure du contenu tel que Grist l'affiche : nombres (format et locale du document), dates et dates-heures (format et fuseau), références (colonne d'affichage), puces Choice / ChoiceList / RefList, texte multiligne, erreurs.
- Réglages : largeur minimale et maximale, calcul d'après la valeur la plus longue ou 95 % des valeurs, prise en compte des en-têtes.
- Aperçu par colonne (largeur actuelle et proposée, signalement des largeurs plafonnées) avec sélection des colonnes à modifier.
- Écriture groupée des largeurs (`BulkUpdateRecord` sur `_grist_Views_section_field`), retour aux largeurs précédentes, retour à la largeur par défaut.
- Mémorisation des réglages et de la vue choisie dans les options du widget.
- Messages explicites en cas d'accès insuffisant ou d'écriture refusée.

### Sécurité
- Aucune requête réseau ; CSP restrictive (`connect-src 'none'`), API des widgets chargée depuis l'instance Grist.
- Aucun `innerHTML` : tout contenu issu du document passe par `textContent`.

[Non publié]: https://github.com/maximelacoste/grist-widget-column-autofit/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/maximelacoste/grist-widget-column-autofit/releases/tag/v1.0.0
