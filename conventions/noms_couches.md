# Conventions de nommage (couches, fichiers, exports)

## Objectif
Rendre les livraisons lisibles : un non-tech doit comprendre “ce que c’est” sans ouvrir la couche.

## Règles simples

### Noms de fichiers
- minuscules + underscores
- pas d’accents, pas d’espaces
- pas de “final_final”

Exemples :
- `donnees_admin.gpkg`
- `livraison_2026-01-29.gpkg`

### Noms de couches (dans le GeoPackage)
- nom court + explicite
- exemples :
  - `communes`
  - `departements`
  - `regions`
  - `epci`

### Champs (si tu crées/renommes)
- `code` : identifiant (si applicable)
- `nom` : nom lisible
- éviter : `field1`, `var2`

### Dossier de livraison recommandé
- `livraison/`
  - `livraison.gpkg`
  - `projet.qgz` (si utile)
  - `README_livraison.md`
