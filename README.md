# Workflows templates

Ce dépôt contient une collection de workflows GitHub Actions réutilisables destinés à standardiser les processus CI/CD au sein du projet.

## Utilisation

Chaque template est conçu pour être appelé (`workflow_call`) depuis d'autres dépôts.

### Templates disponibles

#### Image Builder

Fichier : [.github/workflows/image-builder.yml](.github/workflows/image-builder.yml)

Ce workflow gère :
- La configuration de Docker Buildx
- L'authentification au registre de conteneurs (ghcr.io)
- L'extraction des métadonnées
- La construction et la publication de l'image Docker

### Exemple d'appel

```yaml
jobs:
  docker-build:
    uses: ERP-CNAM/workflows-templates/.github/workflows/image-builder.yml@main
    with:
      image-name: erp-cnam-back
      context: .
```

Pour plus de détails sur les paramètres (`inputs`), ouvrez le fichier du template.

Les `inputs` sont overridables par chaque groupe si il le souhaite, dans la mesure où par exemple le fichier Dockerfile n'est pas à la racine du projet, mais dans un sous-dossier docker, modifier l'input `context`.

Sur ce, enjoy !