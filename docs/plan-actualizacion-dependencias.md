# Plan de Actualización de Dependencias

## Objetivo
Actualizar el proyecto de Nuxt 3.13.2 a Nuxt 4.0.3 y todas las dependencias asociadas según `docs/package.destino.json`.

## Cambios Principales

### 1. Actualización de Nuxt Framework
- **Actual**: `nuxt@^3.13.2`
- **Destino**: `nuxt@^4.0.3`
- **Impacto**: Migración mayor que requiere revisión de breaking changes

### 2. Nuevas DevDependencies

#### ESLint y Herramientas de Desarrollo
```json
"@nuxt/eslint": "^1.8.0",
"@types/node": "^24.2.1",
"@typescript-eslint/eslint-plugin": "^8.39.0",
"@typescript-eslint/parser": "^8.39.0",
"eslint": "^9.33.0",
"eslint-config-prettier": "^10.1.8",
"eslint-plugin-prettier": "^5.5.4",
"eslint-plugin-unused-imports": "^4.1.4",
"eslint-plugin-vue": "^10.4.0"
```

#### Remover
```json
"@nuxtjs/i18n": "^8.5.4" (movido a dependencies)
"@rollup/plugin-alias": "^5.1.0"
"prettier-plugin-tailwindcss": "^0.6.6"
"vue-tsc": "^2.0.29"
```

### 3. Nuevas Dependencies

#### Módulos Nuxt Oficiales
```json
"@nuxt/icon": "^1.15.0",
"@nuxtjs/color-mode": "^3.5.2",
"@nuxtjs/tailwindcss": "^6.14.0",
"@vueuse/nuxt": "^13.6.0"
```

#### I18n Actualizado
```json
"@nuxtjs/i18n": "^10.0.4" (from ^8.5.4)
```

### 4. Actualizaciones de Versiones

#### Dependencies Actualizadas
- `@bhplugin/vue3-datatable`: ^1.0.3 → ^1.1.4
- `@fullcalendar/*`: ^6.1.15 → ^6.1.19
- `@vuelidate/core`: ^2.0.0 → ^2.0.3
- `@vuelidate/validators`: ^2.0.0 → ^2.0.4
- `apexcharts`: ^3.53.0 → ^3.54.1
- `easymde`: ^2.18.0 → ^2.20.0
- `file-upload-with-preview`: ^4.2.0 → ^4.3.0
- `highlight.js`: ^11.10.0 → ^11.11.1
- `maska`: ^3.0.0 → ^3.2.0
- `quill`: ^2.0.2 → ^2.0.3
- `sweetalert2`: ^11.14.0 → ^11.22.4
- `swiper`: ^11.1.14 → ^11.2.10
- `vue3-apexcharts`: ^1.6.0 → ^1.8.0

#### DevDependencies Actualizadas
- `@iconify-json/material-symbols`: ^1.2.31 (nueva)
- `prettier`: ^3.3.3 → ^3.6.2

### 5. Nuevos Scripts
```json
"sync": "cp CLAUDE.md .github/copilot-instructions.md",
"lint": "eslint .",
"format": "prettier --write . | grep -v 'unchanged'",
"validate": "npm run format && npm run lint && npm run build"
```

## Plan de Ejecución

### Fase 1: Preparación
1. **Backup del proyecto actual**
2. **Crear rama feature/nuxt4-upgrade**
3. **Documentar configuración actual**

### Fase 2: Actualización Core
1. **Actualizar Nuxt a v4**
   - Revisar [Nuxt 4 Migration Guide](https://nuxt.com/docs/getting-started/upgrade#nuxt-4)
   - Actualizar configuración `nuxt.config.ts`
   - Verificar compatibilidad de módulos

### Fase 3: Configuración de ESLint
1. **Instalar dependencias ESLint**
2. **Crear configuración `.eslintrc.js` o `eslint.config.js`**
3. **Configurar Prettier con ESLint**
4. **Añadir scripts de linting**

### Fase 4: Módulos Nuxt
1. **Instalar nuevos módulos oficiales**
   - `@nuxt/icon`
   - `@nuxtjs/color-mode`
   - `@nuxtjs/tailwindcss`
   - `@vueuse/nuxt`
2. **Actualizar configuración de módulos**

### Fase 5: Actualización de Dependencias
1. **Actualizar @nuxtjs/i18n a v10**
   - Revisar breaking changes
   - Actualizar configuración
2. **Actualizar resto de dependencias**
3. **Resolver conflictos de tipos**

### Fase 6: Testing y Verificación
1. **Ejecutar `npm run validate`**
2. **Probar funcionalidades críticas**
3. **Verificar build de producción**
4. **Testing completo de la aplicación**

## Riesgos y Consideraciones

### Breaking Changes Potenciales
- **Nuxt 4**: Cambios en el sistema de módulos y configuración
- **@nuxtjs/i18n v10**: Posibles cambios en la API
- **ESLint v9**: Nuevas reglas y configuración

### Dependencias a Vigilar
- `@nuxt/types`: Puede ser incompatible con Nuxt 4
- Módulos personalizados que dependan de APIs internas

## Comandos de Migración

```bash
# 1. Backup y rama
git checkout -b feature/nuxt4-upgrade

# 2. Actualizar package.json
cp docs/package.destino.json package.json

# 3. Limpiar node_modules
rm -rf node_modules package-lock.json

# 4. Instalar dependencias
npm install

# 5. Verificar
npm run validate
```

## Post-Migración

### Configuraciones Requeridas
1. **ESLint**: Crear configuración base
2. **Prettier**: Verificar integración
3. **Nuxt Config**: Actualizar para v4
4. **Tailwind**: Verificar nueva integración
5. **I18n**: Actualizar configuración

### Documentación
1. Actualizar README con nuevos scripts
2. Documentar cambios de configuración
3. Crear guía de desarrollo actualizada

---

**Estimación de tiempo**: 2-3 días
**Prioridad**: Alta
**Responsable**: Desarrollador principal