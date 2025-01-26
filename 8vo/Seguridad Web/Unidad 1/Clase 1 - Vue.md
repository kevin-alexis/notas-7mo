# ¿Qué es una SPA?


# Diferencias entre sitio, landing page y un sitio que integra más funcionalidades


# Función de single page

# ¿Qué es VUE?
Vue es una libreria

Componente: se compone de 3 cosas en vue
Un componente es SFC: Single File Component y se compone de:
- Estructura a nivel de codigo (HMTL)
- Estructura a nivel de typescript (TYPESCRIPT)
- Estilos a nivel de (CSS)

>[!NOTA]
>Vue Single-File Components (a.k.a. `*.vue` files, abbreviated as **SFC**) is a special file format that allows us to encapsulate the template, logic, **and** styling of a Vue component in a single file. Here's an example SFC:

```ts
<script setup> import { ref } from 'vue' const greeting = ref('Hello World!') </script> <template> <p class="greeting">{{ greeting }}</p> </template> <style> .greeting { color: red; font-weight: bold; } </style>
```


## Creating a Vue Application

El proyecto creado es de página unica

```shell
npm create vue@latest
```


Maneja un DOM virtual
scaffold
Scaffolding

Para que sirve cada opción:
```shell

✔ Project name: … <your-project-name> # nombre del proyecto
✔ Add TypeScript? … No / Yes #
✔ Add JSX Support? … No / Yes # 
✔ Add Vue Router for Single Page Application development? … No / Yes #
✔ Add Pinia for state management? … No / Yes # manejador de estados
✔ Add Vitest for Unit testing? … No / Yes #
✔ Add an End-to-End Testing Solution? … No / Cypress / Nightwatch / Playwright 
✔ Add ESLint for code quality? … No / Yes # tema de calidad de codigo
✔ Add Prettier for code formatting? … No / Yes # para el formateo de código
✔ Add Vue DevTools 7 extension for debugging? (experimental) … No / Yes #
Scaffolding project in ./<your-project-name>... Done.
```

Mi ejemplo:
```bash
 Unidad 1  npm create vue@latest
Need to install the following packages:
create-vue@3.14.0
Ok to proceed? (y) y


> npx
> create-vue


Vue.js - The Progressive JavaScript Framework

√ Project name: ... vue-project
√ Add TypeScript? ... Yes
√ Add JSX Support? ... Yes
√ Add Vue Router for Single Page Application development? ... Yes
√ Add Pinia for state management? ... Yes
√ Add Vitest for Unit Testing? ... No 
√ Add an End-to-End Testing Solution? » No
√ Add ESLint for code quality? » Yes
√ Add Prettier for code formatting? ... Yes

Scaffolding project in D:\Archivos\Documentos OneDrive\OneDrive - UNIVERSIDAD TECNOLOGICA DE CANCUN\8vo Cuatrimestre\Seguridad en la web\Unidad 1\vue-project...

Done. Now run:

  cd vue-project
  npm install
  npm run format
  npm run dev

```

# Pinia

Manejador de estados

asi como redux en react


# Composition API VS Options API
You should now have your first Vue project running! Note that the example components in the generated project are written using the [Composition API](https://vuejs.org/guide/introduction.html#composition-api) and `<script setup>`, rather than the [Options API](https://vuejs.org/guide/introduction.html#options-api). Here are some additional tips:


# CDN


## Using Vue from CDN

El CDN se añade en el index.html

El index.html es la plantilla en donde se cargan los componentes



### Using the Global Build

```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>

<div id="app">{{ message }}</div>

<script>
  const { createApp, ref } = Vue

  createApp({
    setup() {
      const message = ref('Hello vue!')
      return {
        message
      }
    }
  }).mount('#app')
</script>
```

- **createApp:** para crear o inicializar la app
- **ref:**
- **setup:** 
- **mount:** identificar en donde va a inyectar la aplicación, hace referencia con el id

Se crea un div y se le asigna un id para decirle en donde va a inyectar la aplicación

Empaquetador de código:

- webpack


- que es una spa
- diferencias entre sitio, landing page y un sitio que integra más funcionalidades
- funcion de single page
- que es sfc
- que son los componentes
- cuales son algunas librerias para las funcionalidades de vue, como lo de manejador de estados global, vue router para el manejo de rutas y redirección
- como poder crear una aplicacion vue de dos formas: desde cdn o cli
- empaquetador: webpack y vite


# Estructura de vue

por que no guardar imagenes en public: 
S3 - Buckets
Los buckets es un lugar de almacenamiento. Depende que tan escalabre quieres que sea



carpetas:

- stores: gestor de estado global


routerview: historia de rutas, ... permite saber la estructura del sitio o el mapa del sitio. Asi como angular cuando creas la carpeta de rutas en las carpetas con los componentes
routerLink: 
