# MJSL QGIS - Outil de diagnostic du littoral marseillais

Ce dossier transforme la Matrice de Justice Spatiale Littorale en outil QGIS. Il est pense pour un TPFE d'architecture : tu peux l'utiliser comme support de diagnostic, de cartographie et de passage vers le projet.

## Contenu du dossier

- `templates/grille_scoring_mjsl.csv` : grille complete des six dimensions et des criteres notes de `0` a `3`.
- `templates/schema_couches_qgis.csv` : structure des couches QGIS et des champs attributaires.
- `templates/fiche_releve_terrain_mjsl.csv` : fiche terrain au format tableur.
- `templates/test_pilote_vallon_malmousque.csv` : test pilote pour le Vallon des Auffes / Malmousque.
- `templates/expressions_qgis_mjsl.md` : formules a coller dans la calculatrice de champs QGIS.
- `data/*.geojson` : couches QGIS de depart avec quelques objets pilotes a verifier.
- `docs/fiche_releve_terrain_mjsl.md` : fiche terrain lisible et imprimable.
- `docs/test_pilote_vallon_malmousque.md` : protocole de test pilote.
- `docs/cartes_synthese_mjsl.md` : methode pour construire les cartes finales.

## Demarrage dans QGIS

1. Ouvrir QGIS.
2. Glisser-deposer les fichiers `.geojson` du dossier `data`.
3. Verifier que le projet est en `EPSG:4326` ou reprojeter ensuite en Lambert 93 si besoin pour les mesures.
4. Ajouter un fond OpenStreetMap depuis le panneau Navigateur de QGIS.
5. Pour chaque couche, ouvrir la table attributaire et verifier les champs.
6. Utiliser la calculatrice de champs avec les expressions de `templates/expressions_qgis_mjsl.md`.

## Methode de travail conseillee

Commencer par le troncon pilote `Vallon des Auffes - Malmousque`. Ne cherche pas tout de suite a couvrir tout le littoral.

1. Redecoupe le parcours en petits segments de 25 a 50 m.
2. Remplis une fiche terrain par segment.
3. Note les six dimensions avec l'echelle `0-3`.
4. Ajoute les points de rupture, seuils et amenites.
5. Calcule le score global.
6. Regarde si le diagnostic confirme ou nuance ton hypothese.

## Echelle de score

- `0` : excluant.
- `1` : faible.
- `2` : acceptable.
- `3` : capacitant.

Le score global n'est pas une verite mathematique. C'est un outil de lecture critique. Il sert a comparer les troncons et a justifier les choix de projet.

## Principe important

La MJSL n'est pas une simple carte PMR. Elle croise la continuite physique, les ambiances, la cognition, les couts, la legitimite sociale et la participation. Un lieu peut donc etre techniquement praticable mais rester injuste s'il est bruyant, privatisant, socialement filtrant ou impossible a atteindre depuis le reste de la ville.

## Sorties attendues pour le TPFE

- Une carte globale de justice spatiale littorale.
- Six cartes analytiques par dimension.
- Trois cartes de categories d'exclusion.
- Un zoom pilote sur le Vallon des Auffes / Malmousque.
- Une planche projectuelle montrant ou et comment intervenir.
