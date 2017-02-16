---
title: Comandos
description: Nuxt.js viene con un conjunto de comandos útiles con propósito en desarrollo y producción.
---

> Nuxt.js viene con un conjunto de comandos útiles con propósito en desarrollo y producción.

## Lista de Comandos

| Comando | Descripción |
|---------|-------------|
| nuxt | Lanza un servidor de desarrollo [localhost:3000](http://localhost:3000) con 'hot-reloading'. |
| nuxt build | Construye tu aplicación con webpack y minifica JS & CSS (para producción). |
| nuxt start | Empieza el servidor en modo producción (Después de correr `nuxt build`). |
| nuxt generate | Construye la aplicación y genera cada ruta como un archivo HTML (usado para hosting estático). |

Debes poner estos comandos en `package.json`:

```json
"scripts": {
  "dev": "nuxt",
  "build": "nuxt build",
  "start": "nuxt start",
  "generate": "nuxt generate"
}
```

Luego, puedes lanzar tus comandos vía `npm run <command>` (ejemplo: `npm run dev`).

## Entorno de Desarrollo

Para lanzar Nuxt en modo de desarrollo con el 'hot reloading':

```bash
nuxt
// o
npm run dev
```

## Implementación de Producción

Nuxt.js te deja elegir entre 2 modos para desplegar tu aplicación: 'Server Rendered' o 'Static Generated'.

### Implementación del servidor renderizado

Para desplegar, en lugar de correr nuxt, quizás quieras construir con anticipación. Por lo tanto, construir e iniciar son comandos separados:

```bash
nuxt build
nuxt start
```

El `package.json` se recomienda como a continuación:
```json
{
  "name": "my-app",
  "dependencies": {
    "nuxt": "latest"
  },
  "scripts": {
    "dev": "nuxt",
    "build": "nuxt build",
    "start": "nuxt start"
  }
}
```

Nota: recomendamos poner `.nuxt` en `.npmignore` o `.gitignore`.

### Implementación de Estática Generada

Nuxt.js te da la posibilidad de alojar tu aplicación web en cualquier hosting estático.

Para generar nuestra aplicación web en archivos estáticos:

```bash
npm run generate
```

Eso creará una carpeta `dist` con todo incluido listo para ser desplegado en un hosting estático.

Si tienes un proyecto con [rutas dinámicas](/guide/routing#dynamic-routes), visita [generar configuración](/api/configuration-generate) para decirle a nuxt.js cómo generar estas rutas dinámicas.

<div class="Alert">Cuando estes generando tu aplicación web con `nuxt generate`, [el contexto](/api#context) dada a [data()](/guide/async-data#the-data-method) y [fetch()](/guide/vuex-store#the-fetch-method) no tendrá `req` y`res`.</div>
