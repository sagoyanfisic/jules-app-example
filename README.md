# Cron Schedule Documenter with Jules AI

Workflow de GitHub Actions que usa **Jules AI** para mejorar automáticamente los comentarios en tu archivo `cron_job.yaml`.

## 🚀 Configuración Inicial

### 1. Configurar Jules en tu cuenta

1. Ve a [jules.google](https://jules.google)
2. Autentica con tu cuenta de Google
3. Acepta los términos de privacidad
4. Conecta tu cuenta de GitHub (OAuth)
5. Selecciona los repositorios que Jules puede acceder (este repositorio)

### 2. Obtener API Key

1. En [jules.google](https://jules.google), ve a **Settings**
2. Crea un nuevo **API Key** (máximo 3 por cuenta)
3. Copia el API key

### 3. Agregar API Key a GitHub Secrets

1. Ve a tu repositorio → **Settings** → **Secrets and variables** → **Actions**
2. Click en **New repository secret**
3. Name: `JULES_API_KEY`
4. Value: Pega tu API key de Jules
5. Click **Add secret**

### 4. Ejecutar el workflow

1. Ve a **Actions** → **Improve Cron Schedules with Jules**
2. Click en **Run workflow**
3. Jules analizará tu `cron_job.yaml` y mejorará los comentarios
4. Se creará un PR automáticamente con los cambios

## 📋 Cómo Funciona

1. **Disparas el workflow** manualmente desde GitHub Actions
2. **El workflow envía un prompt a Jules** con instrucciones claras
3. **Jules analiza** el archivo `cron_job.yaml` en tu repositorio
4. **Jules crea mejoras** en los comentarios de los schedules
5. **Se genera un PR** automáticamente con los cambios

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

## 🔒 Seguridad

- **Nunca** commitees API keys al repositorio
- Almacena claves en GitHub Repository Secrets
- Usa `${{ secrets.JULES_API_KEY }}` en workflows
- Jules accede solo a los repositorios que autorizaste
- Las API keys comprometidas serán deshabilitadas automáticamente

## 📚 Documentación Oficial

- [Jules Documentation](https://jules.google/docs/)
- [Jules Guides](https://jules.google/docs/guides/)
- [Jules Tools (CLI)](https://jules.google/docs/guides/tools/)
- [Jules REST API Reference](https://jules.google/docs/rest-api/)

## 📄 Licencia

MIT
