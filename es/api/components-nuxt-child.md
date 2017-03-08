---
title: "API: El Componente <nuxt-child>"
description: Muestra la página actual
---

# El Componente &lt;nuxt-child&gt;

> Este componente es usado para mostrar los componentes hijos en una [ruta anidada](/guide/routing#nested-routes).

Ejemplo:

```bash
-| pages/
---| parent/
------| child.vue
---| parent.vue
```

Este árbol de archivos generará estas rutas:
```js
[
  {
    path: '/parent',
    component: '~pages/parent.vue',
    name: 'parent',
    children: [
      {
        path: 'child',
        component: '~pages/parent/child.vue',
        name: 'parent-child'
      }
    ]
  }
]
```

Para mostrar el componente `child.vue`, debo insertar `<nuxt-child/>` dentro de `pages/parent.vue`:

```html
<template>
  <div>
    <h1>Yo soy la vista padre</h1>
    <nuxt-child/>
  </div>
</template>
```

Para ver un ejemplo, revisa el [ejemplo de rutas anidadas](/examples/nested-routes).
