---
title: "API: El Componente <nuxt-link>"
description: Enlaza las páginas entre ellas con nuxt-link.
---

# El Component &lt;nuxt-link&gt;

> Este componente es usado para enlazar los componentes página entre ellos.

En este momento, `<nuxt-link>` es los mismo que [`<router-link>`](https://router.vuejs.org/en/api/router-link.html), así que te recomendamos que revises cómo usarlo en la [documentación de vue-router](https://router.vuejs.org/en/api/router-link.html).

Ejemplo (`pages/index.vue`):

```html
<template>
  <div>
    <h1>Página principal</h1>
    <nuxt-link to="/about">About</nuxt-link>
  </div>
</template>
```

En el futuro, vamos a añadir características al componente nuxt-link, como "pre-fetching" en segundo plano para mejorar la capacidad de respuesta de las aplicaciones nuxt.js.
