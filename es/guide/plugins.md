---
título: Plugins
descripción: Nuxt.js te permite definir los plugins js que serán corridos antes de instanciar la aplicación vue.js de origen, puede ser para usar tu propia librería o módulos externos.
---

> Nuxt.js te permite definir los 'plugins js' que serán corridos antes de instanciar la aplicación vue.js de origen, puede ser para usar tu propia librería o módulos externos.

<div class="Alert">Es importante saber que en cualquier Vue [Ciclo de vida de la instancia](https://vuejs.org/v2/guide/instance.html#Lifecycle-Diagram), solo `beforeCreate` y `created` son llamados **desde el lado del cliente y del servidor**. Todos los otros 'hooks' son llamados solo del lado del cliente.</div>

## Paquetes Externos

Querremos usar paquetes externos/módulos en nuestra aplicación, un gran ejemplo es [axios](https://github.com/mzabriskie/axios) para hacer solicitudes HTTP para el cliente y servidor.

Lo instalamos vía NPM:

```bash
npm install --save axios
```

Luego, lo podemos usar directamente en nuestra páginas:

```html
<template>
  <h1>{{ title }}</h1>
</template>

<script>
import axios from 'axios'

export default {
  async data ({ params }) {
    let { data } = await axios.get(`https://my-api/posts/${params.id}`)
    return { title: data.title }
  }
}
</script>
```

Pero hay **un problema acá**, si importamos 'axios' en otra página, será incluido de nuevo para el conjunto de páginas. Queremos incluir `axios` osolo una vez en nuestra aplicación, para esto, usamos la llave `build.vendor` en nuestro `nuxt.config.js`:

```js
module.exports = {
  build: {
    vendor: ['axios']
  }
}
```

Luego, puedo importar `axios` donde sea sin tener que preocuparme por hacer un conjunto más grande!

## Plugins Vue

Si queremos usar [notificaciones-vue](https://github.com/se-panfilov/vue-notifications) para mostrar notificaciones en nuestra aplicación, tenemos que preparar el plugin antes de lanzar el app.

Archivo `plugins/vue-notifications.js`:
```js
import Vue from 'vue'
import VueNotifications from 'vue-notifications'

Vue.use(VueNotifications)
```

Luego, agregamos el archivo dentro de la llave `plugins` en `nuxt.config.js`:
```js
module.exports = {
  plugins: ['~plugins/vue-notifications']
}
```

Para aprender más acerca de la llave de configuración 'plugins', revisa [plugins api](/api/configuration-plugins).

Aunque de verdad, `vue-notifications` será incluido en el paquete del app, pero como es una librería, queremos incluirlo en el paquete de proveedores para tener un mejor caché. 

Podemos actualizar nuestro `nuxt.config.js` tpara agregar `vue-notifications` en el paquete de proveedores:
```js
module.exports = {
  build: {
    vendor: ['vue-notifications']
  },
  plugins: ['~plugins/vue-notifications']
}
```

## Solo Lado del Cliente

Algunos plugins pueden funcionar **solo para el navegador**, puedes usar la variable `process.BROWSER_BUILD` para ver si el plugin correrá desde el lado del cliente.

Ejemplo:
```js
import Vue from 'vue'
import VueNotifications from 'vue-notifications'

if (process.BROWSER_BUILD) {
  Vue.use(VueNotifications)
}
```

En caso necesites algunas librerías solo para el servidor, puedes usar la variable `process.SERVER_BUILD` con valor `true` cuando el 'webpack' este creando el archivo `server.bundle.js`.
