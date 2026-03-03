# Docker Terragrunt Deploy

Imágenes Docker optimizadas para despliegues de infraestructura con Terragrunt, Terraform y Task.

## Imágenes disponibles

### Node.js

#### `node-20`
- **Base:** Node.js 20 Alpine
- **Herramientas incluidas:**
  - Terraform 1.9.5
  - Terragrunt 0.67.4
  - Task (go-task)
  - AWS CLI
  - Git, bash, jq, openssh-client

#### `node-22-pnpm`
- **Base:** Node.js 22 Alpine
- **Herramientas incluidas:**
  - Terraform 1.9.5
  - Terragrunt 0.67.4
  - Task (go-task)
  - pnpm 9.7.0
  - AWS CLI
  - Git, bash, jq, openssh-client

#### `node-24-pnpm`
- **Base:** Node.js 24 Alpine
- **Herramientas incluidas:**
  - Terraform 1.9.5
  - Terragrunt 0.67.4
  - Task (go-task)
  - pnpm 9.7.0
  - AWS CLI
  - Git, bash, jq, openssh-client

### Python

#### `python-3.12`
- **Base:** Python 3.12 Alpine
- **Herramientas incluidas:**
  - Terraform 1.9.5
  - Terragrunt 0.67.4
  - Task (go-task)
  - AWS CLI
  - Git, bash, jq, openssh-client

## Uso

### En GitHub Actions

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    container:
      image: karibu/terragrunt-deploy:node-24-pnpm
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Deploy infrastructure
        run: |
          cd infrastructure
          terragrunt run-all apply --terragrunt-non-interactive
```

### En GitLab CI

```yaml
deploy:
  image: karibu/terragrunt-deploy:node-24-pnpm
  script:
    - cd infrastructure
    - terragrunt run-all apply --terragrunt-non-interactive
```

### Localmente con Docker

```bash
docker run -it --rm \
  -v $(pwd):/home/node/infra \
  -v ~/.aws:/home/node/.aws:ro \
  karibu/terragrunt-deploy:node-24-pnpm \
  bash
```

## Docker Hub

Las imágenes están disponibles en: [Docker Hub - karibu/terragrunt-deploy](https://hub.docker.com/r/karibu/terragrunt-deploy)

## Licencia

Este proyecto está disponible bajo licencia MIT.
