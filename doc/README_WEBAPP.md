# MJSL Webapp - Carte interactive OSM et donnees geolocalisees

Cette application sert a explorer la Matrice de Justice Spatiale Littorale hors de QGIS. Elle charge les couches MJSL deja creees, interroge OpenStreetMap via Overpass, importe tes releves geolocalises et exporte un GeoJSON reutilisable dans QGIS.

## Ouvrir l'application

Methode conseillee sur Windows :

1. Va dans le dossier `mjsl_qgis`.
2. Double-clique sur `ouvrir_webapp_mjsl.bat`.
3. Une fenetre PowerShell s'ouvre et lance un serveur local.
4. Le navigateur s'ouvre sur `http://localhost:8765/webapp/index.html`.
5. Garde la fenetre PowerShell ouverte pendant l'utilisation.

Si tu ouvres directement `webapp/index.html`, la carte peut s'afficher, mais le chargement automatique des GeoJSON peut etre bloque par le navigateur. Dans ce cas, utilise le bouton `Importer GeoJSON / CSV`.

## Ce que tu peux faire

- Afficher les couches MJSL existantes.
- Lancer une requete OSM pour charger des indices : bancs, toilettes, fontaines, escaliers, arrets de bus, traversees, restaurants, cafes, belvederes.
- Importer tes propres fichiers `GeoJSON`, `JSON` ou `CSV`.
- Filtrer par dimension : physique, sensorielle, cognitive, economique, sociale, democratique.
- Filtrer par classe : `excluant`, `faible`, `acceptable`, `capacitant`.
- Filtrer par categorie d'exclusion : fragmentation, rupture metropolitaine, privatisation/invisibilisation.
- Cliquer sur un objet pour lire ses attributs et son diagnostic.
- Exporter les objets visibles en `mjsl_export_interactif.geojson`.

## Format CSV accepte

Pour importer un CSV, il faut au minimum deux colonnes de coordonnees :

- `lat` et `lon`, ou
- `latitude` et `longitude`, ou
- `coord_y` et `coord_x`.

Exemple :

```csv
fiche_id,lat,lon,secteur,d1_physique,d2_sensoriel,d3_cognitif,d4_economique,d5_social,d6_democratique,note_obs
F001,43.2864,5.3528,Vallon des Auffes,0,1,1,0,1,0,Escaliers et surcharge sensorielle.
```

## Comment utiliser OSM correctement

OSM fournit des indices, pas une preuve definitive. Un banc absent d'OSM peut exister sur place, et un objet present dans OSM peut etre mal positionne ou obsolete.

Utilise OSM pour reperer :

- les escaliers et ruptures physiques ;
- les bancs et ressources de repos ;
- les toilettes et fontaines ;
- les arrets de bus et points de transport ;
- les restaurants/cafes comme indices de confort marchand ;
- les belvederes et points de vue.

Chaque indice important doit ensuite etre verifie par photo, mesure ou observation.

## Export vers QGIS

1. Regle les filtres dans la webapp.
2. Clique sur `Exporter GeoJSON enrichi`.
3. Ouvre QGIS.
4. Glisse le fichier `mjsl_export_interactif.geojson` dans QGIS.
5. Utilise `classe_mjsl` ou `_mjsl_class` pour la symbologie.

## Limite importante

La webapp sert a explorer et croiser les donnees. Pour les planches finales du TPFE, QGIS reste meilleur pour la mise en page, les echelles, les legendes academiques et les exports haute resolution.
