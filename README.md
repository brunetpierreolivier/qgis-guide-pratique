# qgis-guide-pratique# QGIS — Guide pratique de production SIG (Playbook)

Objectif : fournir un guide **pas à pas** (débutant-friendly) pour produire une donnée SIG propre dans QGIS : import, CRS, reprojection, contrôle qualité, export “livraison”.

## Public visé
- Débutant SIG / opérateur SIG
- Data / GeoData : besoin de procédures reproductibles

## Contenu du repo
- `playbook/` : 5 procédures QGIS pas à pas
- `checklists/` : checklists avant livraison + contrôle qualité
- `conventions/` : conventions de nommage (couches, fichiers, exports)
- `assets/images/` : captures écran utilisées dans le guide
- `glossaire/` : dictionnaire carto / notions SIG
- `DEVLOG.md` : journal de travail (1 bloc par session)


## Comment utiliser ce guide
1. Suivre les pages dans l’ordre :
   - 01 Installation
   - 02 Importer des données
   - 03 Reprojection (CRS)
   - 04 Contrôle géométrie
   - 05 Export / livraison
2. Reproduire les manipulations dans QGIS avec un petit dataset OpenData.

## Pré-requis
- QGIS (version 3.x, idéalement une version LTR)
- Un dataset vecteur (GeoPackage/GeoJSON/Shapefile)
- Savoir créer un dossier de travail sur Windows

## Licence
MIT
