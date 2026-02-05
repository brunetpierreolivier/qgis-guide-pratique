# Checklist — Contrôle qualité (QGIS)

## Géométrie
- [ ] La couche a une géométrie (pas de géométries nulles)
- [ ] Pas d’erreurs évidentes (self-intersections, anneaux cassés)
- [ ] Vérification faite via **Traitements → Vérifier la validité** (ou équivalent)
- [ ] Si corrections : outil **Corriger les géométries** (Fix geometries) et export d’une couche corrigée

## CRS / Projection
- [ ] CRS de la couche connu (Propriétés → Information)
- [ ] CRS du projet cohérent avec l’objectif (mesures → projection métrique)
- [ ] Reprojection/export faits si nécessaire (Save Features As…)

## Attributs
- [ ] Champ identifiant unique (code/id) présent si attendu
- [ ] Pas de doublons sur l’identifiant (vérif simple via table + tri / outils)
- [ ] Champs indispensables présents (nom, code, etc.)
- [ ] Valeurs vides critiques identifiées

## Sortie
- [ ] Export final en GeoPackage (format propre et robuste)
- [ ] Nom de couche clair (pas “export” / “couche1”)
