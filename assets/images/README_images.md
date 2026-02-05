# README — Suivi des images (WebP) pour le guide QGIS

Objectif : suivre le playbook étape par étape, en produisant une capture légère (WebP) pour chaque action clé.

---

## Règles (à appliquer partout)
- Format final : **.webp** dans `assets/images/`
- Sources (optionnel) : PNG dans `assets/images/_src/` (non versionné si ignoré)
- Nommage : `NN_description.webp`  
  - `01_...` pour la page 01, `02_...` pour la page 02, etc.
- Insertion dans les pages `playbook/*.md` : image **sous l’étape** avec un chemin relatif :
  - `![Texte](../assets/images/01_exemple.webp)`

---

## Conversion WebP (commande modèle)
Depuis la racine du repo :

```powershell
magick "assets/images/_src/01_exemple.png" -resize 1400x -quality 80 "assets/images/01_exemple.webp"
