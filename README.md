# Cron Schedule Documenter

Workflow de GitHub Actions que automáticamente mejora y documenta los schedules de cron en tu archivo `cron_job.yaml`.

## 🚀 Quick Start

### Ejecutar el workflow

Ve a **Actions** → **Improve Cron Schedules** → **Run workflow**

El workflow analizará y mejorará automáticamente los comentarios en tu archivo `cron_job.yaml`.

## 📋 Cómo Funciona

1. **Disparas el workflow** manualmente desde GitHub Actions
2. **Script Python** mejora los comentarios en `cron_job.yaml`
3. **Crea un PR** automáticamente con los cambios

## 📁 Estructura del Proyecto

```
.
├── .github/workflows/
│   ├── document-cron-schedules.yml     # Workflow principal
│   └── cron_trigger_deploy.yml         # Ejemplo de workflow con cron
├── cron_job.yaml                       # Tu archivo de configuración de cron
└── README.md
```

## 🔄 Workflow: document-cron-schedules.yml

**Disparador:** Manual (`workflow_dispatch`)

```bash
gh workflow run document-cron-schedules.yml
```

El workflow:
1. Ejecuta un script Python que mejora los comentarios
2. Crea un Pull Request con los cambios
3. Preserva la estructura YAML original

## 💡 Ejemplo de Mejoras

**Antes:**
```yaml
schedule:
  - cron: "0 13 * * 1-5" # 13 UTC - 7 AM MX, 10 AM CLT
  - cron: "0 15 * * 1-5" # 15 UTC - 9 AM MX, 12 PM CLT
```

**Después (mejorado):**
```yaml
schedule:
  - cron: "0 13 * * 1-5"  # Weekdays 1 PM UTC (7 AM MX, 10 AM CLT) - Check for manifests
  - cron: "0 15 * * 1-5"  # Weekdays 3 PM UTC (9 AM MX, 12 PM CLT) - Check for manifests
```

## 📚 Referencias

- [GitHub Actions Workflow Syntax](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [Cron Expression Reference](https://crontab.guru/)

## 📄 Licencia

MIT
