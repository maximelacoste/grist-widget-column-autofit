# Ajuster les colonnes - widget Grist

*[English below](#english)*

Widget personnalisé Grist qui ajuste la largeur des colonnes d'une vue tableau à leur contenu, à la manière du double-clic sur une bordure de colonne dans un tableur.

Grist ne propose pas cette fonction nativement (voir les demandes sur le [forum Grist Creators](https://community.getgrist.com/t/auto-adjust-column-width/13424)).

## Fonctionnement

1. Choisissez une vue tableau du document, sur n'importe quelle page, ou une table en données brutes.
2. Le widget mesure le contenu de chaque colonne tel que Grist l'affiche : nombres selon leur format et la locale du document, dates et dates-heures selon leur format et leur fuseau, références par leur colonne d'affichage, choix sous forme de puces, texte multiligne d'après sa ligne la plus longue.
3. Un aperçu compare pour chaque colonne la largeur actuelle (trait) et la largeur proposée (barre, hachurée si elle atteint le maximum). Décochez les colonnes à laisser telles quelles.
4. **Appliquer** écrit les largeurs en une seule action. **Revenir aux largeurs précédentes** annule la dernière écriture, **Largeur par défaut** rétablit la largeur standard de la vue.

Réglages : largeur minimale et maximale, calcul d'après la valeur la plus longue ou d'après 95 % des valeurs (pour ignorer quelques valeurs exceptionnellement longues), prise en compte ou non des en-têtes. Les réglages et la vue choisie sont mémorisés dans les options du widget.

## Installation

1. **Ajouter un widget › Personnalisé › URL personnalisée**, avec l'adresse où le fichier `widget_column_autofit.html` est hébergé.
2. Dans le panneau de droite, onglet Widget : **Accès complet**.

Conseil : réduisez le widget (menu du widget › **Réduire le widget**). Il reste disponible dans la barre du haut de la page et s'ouvre par-dessus la page le temps de l'ajustement.

L'utilisateur doit avoir le droit de modifier la structure du document ; sinon l'écriture est refusée avec un message explicite.

## Confidentialité et sécurité

- Aucune requête réseau : les données sont lues et les largeurs calculées dans le navigateur. La politique de sécurité du contenu (CSP) interdit toute connexion sortante.
- La seule ressource externe est l'API des widgets, chargée depuis l'instance Grist elle-même (`grist.numerique.gouv.fr`). Pour une autre instance, modifiez le domaine dans la balise `<script>` **et** dans la CSP.
- Aucune donnée n'est insérée dans la page sous forme de HTML (pas d'`innerHTML`).
- L'accès complet est nécessaire parce que la largeur des colonnes est une métadonnée du document (`_grist_Views_section_field.width`), écrite via `applyUserActions`.

## Limites

- L'ajustement n'est pas dynamique : relancez-le après une modification importante des données.
- La mesure est une estimation à la police de Grist ; un écart de quelques pixels est possible.
- Les colonnes de pièces jointes ne sont pas modifiées.

## Licence

Voir le fichier [LICENSE](LICENSE).

---

## English

Grist custom widget that auto-fits the column widths of a table view to their content, like double-clicking a column border in a spreadsheet. Grist has no native equivalent.

**How it works:** pick any table view (any page, or raw data). The widget measures each column's content as Grist renders it (number and date formats, reference display columns, choice chips, longest line of multi-line text), shows a preview of current vs. proposed widths, and writes the checked ones in a single action. Settings: min/max width, longest value or 95th percentile, include headers or not.

**Install:** add a custom widget with the URL of `widget_column_autofit.html`, set access to **Full document access**. Collapsing the widget keeps the page tidy. Users need permission to edit the document structure.

**Privacy:** no network calls; everything runs in the browser. The only external resource is the widget API, loaded from the Grist instance itself — change the domain in both the `<script>` tag and the CSP for another instance.

**Limits:** not dynamic (rerun after major data changes); widths are estimates; attachment columns are left unchanged.
