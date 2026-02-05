# Livraison SIG — Contours administratifs (100m) + Région réparée

## Contenu
Cette livraison fournit un GeoPackage contenant des couches administratives (généralisation 100m) et un export cartographique PDF.

### Fichiers
- `livraison.gpkg` : GeoPackage contenant les couches listées ci-dessous
- `carte_livraison.pdf` : mise en page QGIS “Carte des Régions Réparée” (aperçu/portfolio)

### Couches (dans `livraison.gpkg`)
- `communes` : limites communales (généralisation 100m)
- `departements` : limites départementales (généralisation 100m)
- `epci` : limites EPCI (généralisation 100m)
- `regions_fix` : limites régionales (généralisation 100m) **réparées** (géométries valides)

> Note : la carte PDF utilise ces couches (cf. légende : `livraison — regions_fix`, `livraison — epci`, `livraison — departements`, `livraison — communes`).

## CRS (Système de coordonnées)
- Couches : EPSG:4326 (WGS84) 

## Source des données
- Contours administratifs (généralisation 100m) : data.gouv.fr  
  (couches : communes / départements / EPCI / régions)

## Contrôle qualité & corrections
- Vérification de validité géométrique réalisée dans QGIS (“Vérifier la validité”).
- La couche `regions_fix` a été corrigée via l’outil de réparation (“Réparer/Corriger les géométries”) :
  - objectif : supprimer les erreurs de type auto-intersection
  - résultat : couche finale avec **0 géométrie invalide** (selon l’outil de vérification)

## Notes / limites
- Les contours “100m” sont des géométries généralisées (allégées) : adaptées à l’affichage cartographique et aux webmaps, moins adaptées aux analyses fines à grande échelle.
- Si un autre CRS est nécessaire (ex. EPSG:2154 pour mesures en métropole), reprojeter une couche filtrée “métropole” plutôt que l’ensemble France+Outre-mer.
