# Cron Schedule Documenter with Jules AI

Workflow de GitHub Actions que usa **Jules AI** para mejorar automáticamente los comentarios en tu archivo `cron_job.yaml`.

## 🚀 Configuración Inicial

### 1. Crear cuenta y API key en Jules

1. Ve a [Jules Google Developers](https://developers.google.com/jules/api)
2. Autentica con tu cuenta de Google
3. Ve a **Settings** en la app de Jules
4. Crea un nuevo **API key** (máximo 3 por cuenta)
5. Copia el API key

### 2. Agregar el API key a GitHub Secrets

1. Ve a tu repositorio → **Settings** → **Secrets and variables** → **Actions**
2. Click en **New repository secret**
3. Name: `JULES_API_KEY`
4. Value: Pega tu API key de Jules
5. Click **Add secret**

### 3. Ejecutar el workflow

1. Ve a **Actions** → **Improve Cron Schedules with Jules**
2. Click en **Run workflow**
3. Jules analizará tu `cron_job.yaml` y mejorará los comentarios
4. Se creará un PR automáticamente con los cambios

## 📋 Cómo Funciona

1. **Disparas el workflow** manualmente
2. **Jules recibe el prompt** con instrucciones
3. **Jules analiza** el archivo `cron_job.yaml`
4. **Jules genera mejoras** en los comentarios
5. **Se crea un PR** automáticamente con los cambios mejorados

## 📁 Estructura del Proyecto

```
.
├── .github/workflows/
│   ├── document-cron-schedules.yml     # Workflow con Jules
│   └── cron_trigger_deploy.yml         # Ejemplo de cron
├── cron_job.yaml                       # Tu configuración de schedules
└── README.md
```

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

- **Nunca** commitees API keys al repositorio
- Almacena claves en GitHub Repository Secrets
- Usa `${{ secrets.JULES_API_KEY }}` en workflows
- Las API keys expuestas públicamente serán deshabilitadas automáticamente por Google

## 📚 Referencias

- [Jules API Documentation](https://developers.google.com/jules/api)
- [Jules Authentication](https://jules.google/docs/api/reference/authentication/)
- [GitHub Actions Workflow Syntax](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [Cron Expression Reference](https://crontab.guru/)

## 📄 Licencia

MIT
