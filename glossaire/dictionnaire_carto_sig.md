# Dictionnaire carto / Glossaire SIG (QGIS)

Objectif : expliquer clairement les notions SIG utilisées dans le guide.

---

## 1) Notions de base (à connaître absolument)

### Carte
Représentation visuelle d’un territoire (couches + style + légende + échelle + titre). Dans QGIS, une carte peut être vue dans le canevas et exportée via une mise en page.

### Couche (Layer)
En SIG, une **couche** est un ensemble d’objets géographiques (points, lignes, polygones) + leurs attributs.  
Exemple : couche `communes` (polygones), couche `routes` (lignes).

### Entité (Feature)
Un objet individuel dans une couche.  
Exemple : “la commune de Toulouse” = 1 entité dans la couche `communes`.

### Géométrie
La forme d’une entité : point, ligne, polygone.  
C’est la partie “spatiale” de l’entité.

### Attributs
Les informations descriptives associées à une entité (table d’attributs).  
Exemple : `nom`, `code_insee`, `population`.

### Champ (Field)
Une colonne de la table d’attributs.  
Exemple : champ `code`, champ `nom`.

### Valeur
Le contenu d’un champ pour une entité donnée.  
Exemple : pour une entité “Toulouse”, valeur du champ `nom` = “Toulouse”.

### Identifiant (ID)
Un champ qui permet d’identifier une entité de manière stable.
- **Identifiant unique** : 1 valeur = 1 entité (ex : code INSEE commune).
- Important pour jointures, contrôles qualité, éviter les doublons.

### Table d’attributs
Table “type Excel” qui contient les attributs.  
Dans QGIS : clic droit couche → Ouvrir la table d’attributs.

### Jointure (Join)
Action d’associer une table (ex : CSV) à une couche via un champ commun (ex : code INSEE).  
But : enrichir la couche avec de nouvelles colonnes.

### Sélection
Choisir un sous-ensemble d’entités (par clic, rectangle, requête…).  
Utile pour filtrer, exporter, analyser.

### Filtre
Afficher uniquement certaines entités (sans les supprimer).  
Ex : afficher uniquement les communes d’un département.

---

## 2) CRS / Projection / Coordonnées (le cœur du SIG)

### Coordonnées
Nombres qui décrivent une position. Leur signification dépend du CRS.
- En degrés : longitude / latitude (ex : EPSG:4326)
- En mètres : coordonnées projetées (ex : EPSG:2154)

### CRS (Coordinate Reference System)
Système qui définit comment interpréter les coordonnées :
- le datum (repère terrestre),
- la projection,
- l’unité (degrés, mètres),
- parfois l’axe (ordre lat/lon…).

Exemples :
- EPSG:4326 = WGS84 (lon/lat en degrés)
- EPSG:3857 = Web Mercator (mètres “web”, affichage)
- EPSG:2154 = Lambert-93 (mètres, France, mesures fiables)

### Projection cartographique
Transformation mathématique pour passer de la Terre (sphère/ellipsoïde) vers une carte 2D.  
Toute projection déforme quelque chose (surfaces, distances, angles). On choisit selon l’usage.

### Datum
Modèle de la Terre utilisé par le CRS (ex : WGS84, ETRS89).  
Deux données peuvent avoir la même projection mais un datum différent.

### Reprojection
Changer réellement le CRS d’une couche (les coordonnées sont recalculées).  
Dans QGIS : Export → “Enregistrer les entités sous…” + CRS cible.

### Reprojection “à la volée”
QGIS affiche des couches de CRS différents ensemble en recalculant l’affichage, sans modifier les fichiers.

### Pourquoi c’est important ?
- Mesurer surface/distance exige un CRS en mètres adapté.
- Un mauvais CRS peut afficher ta couche au mauvais endroit.

---

## 3) Échelle / Résolution / Généralisation

### Échelle (ex : 1:25 000)
Rapport entre distance sur la carte et distance réelle.
- Grande échelle = beaucoup de détails (1:5 000)
- Petite échelle = vue large, moins de détails (1:1 000 000)

### Résolution (raster)
Taille d’un pixel au sol (ex : 10 m/pixel). Plus petit = plus détaillé.

### Généralisation
Simplification géométrique pour alléger et adapter à une petite échelle.
Ex : communes simplifiées “100m” pour webmaps.

---

## 4) Formats de données (les plus utilisés)

### Vecteur (Vector)
Objets discrets : points, lignes, polygones.
Formats courants :
- **GPKG (GeoPackage)** : recommandé (1 fichier, robuste, moderne)
- **GeoJSON** : pratique web, mais parfois lourd et limité
- **SHP (Shapefile)** : ancien, plusieurs fichiers, limitations (noms courts, encodage…)

### Raster
Grille de pixels (images géoréférencées) : MNT, orthophotos, imagerie.
Formats courants :
- **GeoTIFF (.tif)** : standard SIG
- **COG (Cloud Optimized GeoTIFF)** : GeoTIFF optimisé web/cloud

### CSV (table)
Table sans géométrie (ex : statistiques INSEE).  
Peut devenir couche de points si colonnes X/Y (lon/lat).

### Tuiles (Tiles)
Découpage pour web :
- **XYZ / TMS** : fonds de carte web
- **MBTiles** : base de tuiles dans un fichier

---

## 5) Acronymes SIG fréquents

- **SIG / GIS** : Système d’Information Géographique
- **CRS** : Coordinate Reference System
- **EPSG** : codes standard de CRS (ex : EPSG:2154)
- **WMS** : Web Map Service (images de cartes)
- **WFS** : Web Feature Service (objets vecteur)
- **WMTS** : Web Map Tile Service (tuiles)
- **XYZ** : tuiles web (format URL)
- **OSM** : OpenStreetMap (données libres)
- **MNT / DEM** : Modèle Numérique de Terrain (altitude)
- **MNS / DSM** : Modèle Numérique de Surface (inclut bâtiments/arbres)
- **BD** : Base de Données (ex : PostGIS)
- **QA/QC** : Quality Assurance / Quality Control
- **ETRS89** : datum Europe (proche WGS84 mais différent)
- **UTM** : projection par zones (EPSG:326xx / 327xx)

---

## 6) Projections courantes et quand les utiliser

### EPSG:4326 — WGS84 (degrés)
- Usage : GPS, web, échange standard, stockage simple
- Limite : mesures (surface/distance) peu fiables directement

### EPSG:3857 — Web Mercator
- Usage : affichage web (fonds de carte), compatibilité tuiles
- Limite : déforme fortement les surfaces, pas pour mesurer

### EPSG:2154 — Lambert-93 (France, mètres)
- Usage : analyses en France, mesures surface/distance, production
- Recommandé pour la plupart des projets France métropolitaine

### UTM (EPSG:326xx / 327xx)
- Usage : mesures locales, zones spécifiques (xx dépend de la zone)
- Très utile hors France métropolitaine selon région

### EPSG:3035 — ETRS89 / LAEA Europe
- Usage : analyses à l’échelle Europe (surfaces comparables)

---

## 7) Sources OpenData SIG (exemples utiles)

### France
- **data.gouv.fr** : portail open data national (beaucoup de couches)
- **IGN** : référentiels, orthos, altimétrie (selon licences)
- **INSEE** : statistiques + codes (souvent tables à joindre)
- **Opendatas locales** : régions, départements, métropoles, communes

### Monde
- **OpenStreetMap (OSM)** : routes, POI, bâtiments (via QuickOSM, Geofabrik…)
- **Natural Earth** : données mondiales simples (petites échelles)

---

## 8) Logiciels SIG (libres et autres)

### Libres / gratuits
- **QGIS** : référence libre (carto, analyses, mise en page)
- **GRASS GIS** : analyses raster/terrain avancées
- **GDAL/OGR** : conversion / reprojection / traitements “en ligne de commande”
- **PostGIS** : extension SIG de PostgreSQL (base de données spatiale)

### Propriétaires (courants)
- **ArcGIS Pro / ArcMap** : suite ESRI (très utilisée en institutions/entreprises)

---

## 9) Notions cartographiques utiles (mise en page)

### Légende
Explique les symboles utilisés.

### Symbologie (Style)
Façon d’afficher une couche (couleurs, épaisseurs, règles).

### Étiquettes (Labels)
Afficher un champ (ex : nom) sur la carte.

### Mise en page (Layout)
Composer la carte : titre, légende, échelle, nord, sources, encart, export PDF/PNG.

### Métadonnées
Description : source, date, CRS, méthode, licence, contact.

---

## 10) Erreurs fréquentes (à repérer vite)

- Couche au mauvais endroit : CRS mal défini
- Mesures absurdes : CRS en degrés au lieu de mètres
- Couche très lourde : géométrie trop détaillée (utiliser une version généralisée)
- Export “Shapefile” qui casse les accents : préférer GeoPackage
