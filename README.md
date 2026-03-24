# Jules AI Agent - Cron Scheduler Documenter

Workflow de GitHub Actions que usa [Jules AI Agent](https://github.com/google-labs-code/jules-action) para mejorar y comentar automáticamente los schedules de cron en tu archivo `cron_job.yaml`.

## 🚀 Quick Start

### 1. Configurar Jules API Key

Agrega tu clave de Jules a los secretos de GitHub:
```bash
Settings → Secrets and variables → Actions → New repository secret
Name: JULES_API_KEY
```

### 2. Ejecutar el workflow

Ve a **Actions** → **Improve Cron Schedules with Jules** → **Run workflow**

Jules analizará y mejorará automáticamente los comentarios en tu archivo `cron_job.yaml`.

## 📋 Cómo Funciona

1. **Disparas el workflow** manualmente desde GitHub Actions
2. **Jules analiza** el archivo `cron_job.yaml`
3. **Jules genera mejoras** en los comentarios de los schedules
4. **Jules crea un PR** con los cambios

## 📁 Estructura del Proyecto

```
.
├── .github/workflows/
│   ├── document-cron-schedules.yml     # Workflow principal de Jules
│   ├── cron_trigger_deploy.yml         # Ejemplo de workflow con cron
│   └── jules-ai-agent.yml              # Template base de Jules
├── cron_job.yaml                       # Tu archivo de configuración de cron
└── README.md
```

## 🔄 Workflows Disponibles

### improve-cron-schedules.yml
**Disparador:** Manual (`workflow_dispatch`)

```bash
gh workflow run document-cron-schedules.yml
```

Jules mejorará los comentarios en `cron_job.yaml`:
- Mantiene las conversiones de zona horaria
- Agrega descripción de qué se dispara
- Hace los comentarios más descriptivos y claros

### cron_trigger_deploy.yml (Ejemplo)
Este es un workflow de ejemplo que dispara deployments en horarios específicos.

## 💡 Ejemplo de Mejoras

**Antes:**
```yaml
schedule:
  - cron: "0 13 * * 1-5" # 13 UTC - 7 AM MX, 10 AM CLT
  - cron: "0 15 * * 1-5" # 15 UTC - 9 AM MX, 12 PM CLT
```

**Después (mejorado por Jules):**
```yaml
schedule:
  - cron: "0 13 * * 1-5"  # Weekdays 1 PM UTC (7 AM MX, 10 AM CLT) - Check for manifests
  - cron: "0 15 * * 1-5"  # Weekdays 3 PM UTC (9 AM MX, 12 PM CLT) - Check for manifests
```

## 🔐 Seguridad

- **Nunca** commitees claves API al repositorio
- Almacena claves en GitHub Repository Secrets
- Usa `${{ secrets.JULES_API_KEY }}` en workflows

## 📚 Referencias

- [Jules Invoke Action](https://github.com/google-labs-code/jules-action)
- [GitHub Actions Workflow Syntax](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [Cron Expression Reference](https://crontab.guru/)

## 📄 Licencia

MIT
