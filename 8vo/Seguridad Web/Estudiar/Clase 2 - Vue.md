# ¿Qué es una SPA?

Una SPA (Single Page Application) es una aplicación web que carga una única página HTML y actualiza dinámicamente su contenido. Esto permite que el usuario interactúe con la aplicación sin necesidad de recargar la página.

Las SPAs son una buena opción para: Desarrollar sitios web pequeños, Proyectos que están iniciándose, Startups recién creadas, Desarrollar landing pages. 

Las ventajas de las SPAs son: Son rápidas, Ofrecen una experiencia de usuario fluida y controlada, Son escalables, El código es reutilizable, Permiten desarrollar todo el código pensando en la lógica de negocio. 

Para implementar una SPA, se carga el contenido HTML, CSS y JavaScript por completo al abrir la web. Luego, se actualiza el contenido del cuerpo de la página a través de API de JavaScript.

# Función de una Single Page Application

Su función es mejorar la experiencia del usuario al permitir que las páginas se actualicen dinámicamente sin necesidad de recargar el navegador.
- El contenido HTML, CSS y JavaScript se cargan por completo al abrir la página. 
- La página no se recarga al cambiar de dirección o modificar la URL. 
- Los datos se cargan en segundo plano y se insertan de forma automática en el DOM de la página. 
- El servidor envía los datos puros, sin mezclarlos con HTML u otro lenguaje.

# Diferencias entre Pagina Web, landing page y un sitio que integra más funcionalidades

**Sitio web** 
- Su función es generar confianza en la empresa.
- El contenido es el mismo para todos los visitantes.

**Landing page**
- Su función es captar el contacto de clientes potenciales. 
- Se centra en un único llamado a la acción (CTA). 
- Se utiliza en campañas de marketing, como anuncios o embudos de correo electrónico. 

**SPA**
- Es un tipo de sitio web que se ejecuta en una sola página. 
- Tiene varias vistas, que son los distintos apartados de la web. 
- El contenido HTML, CSS y JavaScript se cargan por completo al abrir la web. 
- Al pasar de una sección a otra, solo se carga el contenido nuevo de forma dinámica.

# API (Application Program Interface)

# Librería vs Framework

### Librerías
- Son archivos escritos en un lenguaje de programación que proporcionan funcionalidades específicas. 
- Ayudan a evitar la duplicidad de código y a reducir el tiempo de desarrollo. 
- Son conjuntos de herramientas que se usan cuando se necesita.
### Frameworks
- Proporcionan un marco de trabajo para desarrollar aplicaciones. 
- Ofrecen un conjunto de herramientas, estándares y plantillas para el desarrollo rápido de aplicaciones. 
- Controlan la llamada a las bibliotecas para el código. 
- Brindan reglas y pautas para escribir código y estructurar archivos y carpetas.
# ¿Qué es VUE?
Vue es una librería. (Según la doc es un framework, segun el profe es una libreria)

## Componente - SFC **(Single-File Components)**

**Un componente es SFC:** Single File Component y se compone de 3 cosas en VUE:
- Estructura a nivel de código (HMTL)
- Estructura a nivel de typescript (TYPESCRIPT)
- Estilos a nivel de (CSS)

>[!NOTA]
>Vue Single-File Components (a.k.a. `*.vue` files, abbreviated as **SFC**) is a special file format that allows us to encapsulate the **template**, **logic**, and **styling** of a Vue component in a single file. 

#### Here's an example SFC:

```ts
<script setup> 
import { ref } from 'vue' 
const greeting = ref('Hello World!') 
</script> 

<template> 
	  <p class="greeting">{{ greeting }}</p> 
</template> 

<style> 
	.greeting { 
		color: red; 
		font-weight: bold; 
		} 
</style>
```

# Librerias para el funcionamiento de VUE
## Pinia - Manejador de estados

### ¿Qué es un manejador de estados?
Las aplicaciones tienen un estado, este estado es la representación de la información y las modificaciones hechas a la misma, mientras la app se ejecuta. En general, el tema de manejar un estado para nuestra aplicación, está estrechamente relacionado con aplicaciones interactivas, donde precisamente la interacción del usuario modifica el estado de nuestra aplicación.

Consideremos por ejemplo, el reproductor de vídeos de CódigoFacilito. Inicialmente, su estado es "detenido", cuando das clic en el botón Play, su estado pasa a "reproduciendo".

Lo interesante del manejo del estado de una aplicación, es que por lo general, la modificación de una parte del estado, desencadena otras modificaciones. Si volvemos a considerar el ejemplo, podemos notar que si el estado del reproductor pasa a "reproduciendo", aparece un modal oscuro alrededor del reproductor que podríamos decir paso del estado "oculto" al estado "mostrar", por su parte se modifican otros valores como el contador del tiempo reproducido, la barra de progreso del vídeo, etc.

Todo esto que cambia, mientras el usuario usa o interactúa con nuestra app, es el estado de nuestra aplicación, que inicia de una forma, pero conforme la interacción sucede va cambiando.

#### Pinia
Pinia es una biblioteca de gestión de estado para Vue.js. Se utiliza para compartir estado entre componentes o páginas de una aplicación.

#### Redux
Asi como Redux en react, la cual es una library de javascript para la gestión de estados globales predecibles y mantenibles.

- Realiza actualizaciones de estado en respuesta a acciones 
- Modifica el estado a través de objetos llamados acciones, en lugar de hacerlo directamente 
- El estado es inmutable, por lo que no se puede modificar directamente 
- Los reducers son funciones que definen cómo debe cambiar el estado de la aplicación

## Options API VS Composition API
### Options API
La modalidad **Options API** nos permite trabajar mediante **opciones** en un objeto de Vue. La información está separada por nombre de estructuras, de modo que la curva de aprendizaje es muy sencilla y agradable, y resulta muy apropiado para usuarios que comienzan a trabajar con frameworks:

```ts
export default {
  name: "ComponentName",
  props: { ... },     // Props
  data() { ... },     // Data variables
  computed: { ... },  // Computed props
  methods: { ... },   // Functions
  mounted() { ... }   // Mounted hook (lifecycle)
}
```

### Composition API (El más nuevo)

Por otro lado, la **Composition API**, en lugar de separar la información en opciones, utiliza un método especial (_hook_) llamado `setup()` donde podremos escribir nuestro código Javascript de inicialización del componente. Dicho hook devolverá un `object` con los elementos que queramos utilizar en el resto del componente (_como por ejemplo, en el `<template>`_).

La forma de trabajar con esta **Composition API** es más cercana a Javascript nativo (_y puede que un poco más complejo si no se tienen bases sólidas de Javascript_), pero es mucho más práctica para reutilizar datos y crear aplicaciones grandes y fáciles de mantener.

Por esta razón, puede ser una buena aproximación para usuarios avanzados que ya han trabajado previamente con Vue y quieren optar por utilizar una forma más avanzada de gestionar los componentes de su aplicación Vue. La sintaxis de dicha **API** es la siguiente:

```ts
export default {
  name: "ComponentName",
  props: { ... },     // Props
  setup() {
    // Init logic, lifecycle hooks, etc...
    return {
      // Data, methods, computed, etc...
    }
  }
}

```

## Vue Router: Manejo de Rutas y Redirección

Vue Router es el paquete oficial de Vue para manejar el enrutamiento en aplicaciones de una sola página (SPA). Permite definir las rutas de la aplicación y manejar la navegación entre ellas, lo que se traduce en una experiencia fluida sin recargas de página.

Para el manejo de rutas y redirección

# Dos formas de crear una Aplicación de VUE

Hay dos formas de crear una app de VUE, desde CLI y desde CDN
## Creating a Vue Application - CLI

**Nota:** El proyecto creado es de página única

```shell
npm create vue@latest
```

**Maneja un DOM virtual:** El **DOM (Document Object Model)** real es la representación de la estructura de un documento HTML en el navegador.
**Scaffolding:** es un término utilizado en el desarrollo de aplicaciones que se refiere a la creación automática de una estructura básica o inicial de un proyecto o componente. Es como un "andamiaje"

Para que sirve cada opción:
```shell

✔ Project name: … <your-project-name> # nombre del proyecto
✔ Add TypeScript? … No / Yes # agregar TypeScript al proyecto
	✔ Add JSX Support? … No / Yes # una extensión de la sintaxis de JavaScript que permite escribir código HTML dentro de JavaScript
✔ Add Vue Router for Single Page Application development? … No / Yes #
✔ Add Pinia for state management? … No / Yes # manejador de estados
✔ Add Vitest for Unit testing? … No / Yes #
✔ Add an End-to-End Testing Solution? … No / Cypress / Nightwatch / Playwright 
✔ Add ESLint for code quality? … No / Yes # tema de calidad de codigo
✔ Add Prettier for code formatting? … No / Yes # para el formateo de código
✔ Add Vue DevTools 7 extension for debugging? (experimental) … No / Yes #
Scaffolding project in ./<your-project-name>... Done.
```

**ESLint** es una herramienta de análisis de código estático para identificar patrones problemáticos que se encuentran en el código JavaScript. 

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

## Creating a Vue Application - Using Vue from CDN

### CDN (Content Delivery Network) - Red de entrega de contenido
Se referire a red de entrega de contenido (Content Delivery Network)
Una red de entrega de contenido es una red de servidores que distribuyen contenido web a los usuarios. Las CDN aceleran la carga de páginas web y mejoran la calidad del contenido.

- Las CDN almacenan en caché el contenido en servidores cercanos a los usuarios. 
- Las CDN reducen la distancia entre el contenido y el usuario. 
- Las CDN mejoran la calidad del contenido entregado. 
- Las CDN ayudan a los minoristas a suministrar contenido de comercio electrónico rápidamente. 
- Las CDN mejoran la seguridad del contenido.

### Using the Global Build

- El CDN se añade en el index.html
- El index.html es la plantilla en donde se cargan los componentes
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

- **createApp:** Se utiliza para inicializar o crear una nueva aplicación de Vue. Permite configurar la lógica principal de la aplicación, como los métodos, datos y componentes que se utilizarán.
- **ref:** Es una API de Reactividad proporcionada por Vue 3. Permite crear valores reactivos que son accesibles y actualizables en el DOM. Los cambios en las propiedades definidas con `ref` se reflejan automáticamente en la interfaz de usuario.
- **setup:** Es una función que se ejecuta al inicializar el componente. Es el lugar recomendado para declarar valores reactivos, funciones y lógica de los componentes en Vue 3. Se utiliza principalmente con Composition API para mejorar la reutilización del código y el manejo de estados.
- **mount:** identificar en donde va a inyectar la aplicación, hace referencia con el id. Se crea un div y se le asigna un id para decirle en donde va a inyectar la aplicación. - Asocia (monta) la aplicación Vue al elemento del DOM que tiene un ID específico (en este caso, `#app`). Una vez montada, Vue toma el control de ese elemento y renderiza el contenido dinámicamente.****

# Empaquetador de código:

Cuando hablamos de **empaquetadores de código** como **Webpack** y **Vite**, nos referimos a herramientas que permiten agrupar (empaquetar) todos los archivos y recursos de un proyecto (JavaScript, CSS, imágenes, etc.) en un único archivo (o varios) para su distribución en producción. Ambas herramientas tienen el objetivo de optimizar el proceso de construcción de proyectos web, pero tienen diferencias notables en cómo funcionan y cómo se utilizan.

- **webpack:** es uno de los empaquetadores más populares y flexibles para aplicaciones web modernas. Se utiliza para agrupar módulos de JavaScript, CSS, imágenes, y otros archivos en un conjunto optimizado que se puede ejecutar en el navegador.
- **Vite:** es un empaquetador moderno y de alto rendimiento creado por el mismo autor de Vue.js. Está diseñado para ser más rápido y sencillo que Webpack, aprovechando tecnologías más recientes como **ES Modules** y el servidor de desarrollo basado en **esbuild**.

# Estructura de vue
### Carpetas:
```
|- node_modules/ # Dependencias instaladas por npm (automático) 
|- public/ # Archivos estáticos públicos 
|- src/ # Código fuente principal 
| |- assets/ # Recursos estáticos (imágenes, estilos, etc.) 
| |- components/ # Componentes reutilizables de la UI 
| |- router/ # Configuración de rutas 
| |- stores/ # Gestor de estado global 
| |- views/ # Vistas principales (mapeadas a rutas) 
| |- App.vue # Componente raíz de Vue 
| |- main.ts # Punto de entrada del código fuente (inicia la app)
|- index.html # Punto de entrada principal (estructura HTML básica)
|- package.json # Configuración del proyecto y dependencias 
|- tsconfig.json # Configuración de TypeScript (si se usa)
|- vite.config.ts # Configuración del build con Vite

```

### Etiquetas:
Cuando un usuario navega por una ruta en la aplicación, Vue Router renderiza el componente asociado a esa ruta dentro del `<router-view>`. Este componente actúa como el lugar donde se inserta el contenido dinámico, basado en la ruta actual.

`router-link` es un componente de Vue que actúa como un **enlace** para navegar entre rutas. Es un reemplazo de los elementos `<a>` tradicionales, pero con el propósito de realizar **navegación interna** sin recargar la página (lo que hace que sea más rápido y fluido, propio de las SPAs).

# ¿Por qué no guardar imagenes en public?

Los buckets son un **contenedor de objetos**, es decir, un espacio de almacenamiento de objetos digitales, como archivos de texto, imágenes o vídeos, entre otros. Su uso depende que tan escalabre quieres que sea tu app

### ¿Por qué usar buckets?
- **No es Escalable**:  
    Cuando guardas imágenes directamente en `public`, el servidor que hospeda tu aplicación carga con la responsabilidad de almacenar y servir esos archivos. Esto genera problemas si el número de archivos crece mucho, ya que el servidor puede quedarse sin espacio o volverse lento.
    
- **Riesgos de Seguridad**:  
    Al almacenar archivos directamente en una carpeta pública, existe el riesgo de que un atacante acceda a archivos sensibles, ya que el acceso a esa carpeta es directo desde el navegador.
    
- **Dificultad en Mantenimiento**:
    - Si necesitas hacer un backup o mover los archivos a otro servidor, el proceso puede ser complicado.
    - Es más difícil controlar y administrar versiones o eliminar archivos no usados.
    
- **Problemas en Aplicaciones Distribuidas**:  
    En una arquitectura distribuida con varios servidores (o instancias), no todos comparten la misma carpeta `public`. Esto puede generar inconsistencias si un servidor tiene ciertos archivos y otro no.

### ✅ Ventajas de Usar Buckets (Como AWS S3):

1. **Escalabilidad Automática**:  
    Los buckets están diseñados para almacenar grandes cantidades de archivos sin preocuparte por el espacio. Además, permiten el acceso a miles de usuarios simultáneamente.
    
2. **Entrega de Archivos Más Rápida**:  
    Los servicios como AWS S3 están integrados con **CDNs (Content Delivery Networks)**, que replican tus archivos en servidores globales para que los usuarios los descarguen más rápido.
    
3. **Mejor Seguridad**:  
    Puedes configurar permisos granulares (por ejemplo, que ciertos archivos solo sean accesibles a usuarios autenticados) y aplicar medidas como cifrado.
    
4. **Integración y Automatización**:
    - Puedes automatizar la carga y eliminación de archivos.
    - Puedes manejar versiones o archivos temporales de manera más eficiente.
    
5. **Independencia del Servidor**:  
    Los archivos no están atados a tu aplicación ni a tu infraestructura. Esto significa que puedes hacer despliegues o migrar servidores sin preocuparte por mover grandes cantidades de datos.

---
# Resumen de lo visto en clase
- que es una spa
- diferencias entre sitio, landing page y un sitio que integra más funcionalidades
- funcion de single page
- que es sfc
- que son los componentes
- cuales son algunas librerias para las funcionalidades de vue, como lo de manejador de estados global, vue router para el manejo de rutas y redirección
- como poder crear una aplicacion vue de dos formas: desde cdn o cli
- empaquetador: webpack y vite

