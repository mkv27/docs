---
título: Estructura del Directorio
descripción: La estructura predeterminada de la aplicación Nuxt.js tiene el propósito de proveer un gran punto de partida para aplicaciones pequeñas y grandes.
---

> La estructura predeterminada de la aplicación Nuxt.js tiene el propósito de proveer un gran punto de partida para aplicaciones pequeñas y grandes. Por supuesto, tú eres libre de organizar tu aplicación como te guste.

## Directorios

### Directorio de Assets

El directorio de `assets` contiene tus 'assets' sin compilar como LESS, SASS o JavaScript.

[Más documentación acerca de la integración de Assets](/guide/assets)

### El Directorio de los Componentes

El directorio de los `components` contienen tus componentes de Vue.js. Nuxt.js no sobrecarga el método de datos en estos componentes.

### El Directorio de Layouts

El directorio de `layouts` contiene los 'Layouts' de tu Aplicación.

_Este directorio no puede ser renombrado._

[Más documentación acerca de la integración de Layouts](/guide/views#layouts)

### El Directorio Middleware

_Pronto_

### El Directorio de Páginas

El directorio de `pages` contiene las Vistas y Rutas de tu Aplicación. El framework lee todos los archivos `.vue` dentro de este directorio y crea el enrutador de tu aplicación.

_Este directorio no puede ser renombrado._

[Más documentación acerca de la integración de Pages](/guide/views)

### El Directorio de Plugins

El directorio de `plugins` contiene los plugin de Javascript que quieres correr antes de instanciar la aplicación origen de vue.js.

[Más documentación acerca de la integración de Plugins](/guide/plugins)

### El Directorio de Estática

El directorio de `static` contiene tus archivos estáticos. Cada archivo dentro de este directorio está asignada a /.

**Ejemplo:** /static/robots.txt está asignado como /robots.txt

_Este directorio no puede ser renombrado._

[Más documentación acerca de la integración de Static](/guide/assets#static)

### El Directorio de Tiendas

El directorio de `store` contiene tus archivos [Vuex Store](http://vuex.vuejs.org). La opción de Vuex Store es implementada en el framework de Nuxt.js. Creando un archivo `index.js` en este directorio activa automáticamente la opción en el framework.

_Este directorio no puede ser renombrado._

[Más documentación acerca de la integración de Store](/guide/vuex-store)

### El Archivo nuxt.config.js

El archivo `nuxt.config.js` contiene tu configuración personalizada de Nuxt.js.

_Este archivo no puede ser renombrado._

[Más documentación acerca de la integración de nuxt.config.js](/guide/configuration)

### El Archivo package.json

El archivo `package.json` contiene las dependencias y 'scripts' de tu Aplicación.

_Este archivo no puede ser renombrado._

## Alias

| Alias | Directorio |
|-----|------|
| ~ | / |
| ~assets | /assets |
| ~components | /components |
| ~pages | /pages |
| ~plugins | /plugins |
| ~static | /static |

Alias que enlazan a archivos:

| Alias | Uso | Descripción |
|-------|------|--------------|
| ~store | `const store = require('~store')` | Import the `vuex` store instance. |
| ~router | `const store = require('~router')`| Import the `vue-router` instance. |
