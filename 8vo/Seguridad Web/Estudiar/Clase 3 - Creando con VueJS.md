
Vue si es una librería, o al menos solía serlo. 

Nacio como una libreria para JS, sin embargo con el curso del tiempo y actualizaciones, en Vue 2 
se transformo en framework.

Framework: Proporciona diferentes herramientas para el desarrollo, es un marco de trabajo.

El framework de Vue es Nux.

# Objetivos

## Introducción
**¿Qué es vue?**
Un marco de trabajo que engloba muchas herramientas para el desarrollo

**¿Librería o framework?**
Framework

**Componentes**
Sirve para no repetir código, crear una parte de código que podamos utilizar en diferentes lugares de forma modular. 

- **¿Para que utilizar componentes?**
- Para no repetir código
- Para facilitar la legilibilidad del código
- Para facilitar el mantenimiento

**Reactividad**
Cuando una parte del DOM reacciona con las interacciones del usuario.
En JS para cambiar algo se requiere hacer un selector de clases, id, etc. para poder cambiarlo, que en un proyecto mas grande se vuelve excesivo crear funciones y constantes que manden a llamar esas partes. la reactividad permite crear un DOM, saber que hay en el DOM y poder actualizarlo.

**SFC (Single FIle Component)**
Es un componente el cual se compone de 3 cosas
- La estructura HTML
- La lógica con JS
- Los estilos con CSS

Todo se encapsula en cada componente
La propiedad scope hace que no hereden sus estilos

un componente si o si debe tener la etiqueta `<template></template>`
Script opcional y CSS no es requerido
Vite lo compila

```ts

```

**Composition API vs Options API**
A - Application
P - Programming
I - Interface

Options API (Code design by options)
Options es más desorganizado, ya que su codigo se diseña en opciones

| Estructura |
| ---------- |
| Lógica     |
| CSS        |
| Lógica     |
| Estructura |
| CSS        |
| Lógica     |
**Ciclo de vida:**
(Antes de que se cree el componente)
BeforeCreated -> Created ->BeforeMount -> Initial Render -> Mounted -> Updated -> BeforeMount ->UnMounted
- esta amarrado a la idea en que debemos seguri su ciclo de vida.
updated es un ciclo que esta detectando cambios del componente

- Composition API (Code design by features)
Composition es más organizado ya que su codigo se diseña en funciones

**Ciclo de vida:**
En este se manda a llamar el que queramos en el momento en que queramos
- BeforeCreated
- onBeforeMount()
- onUpdated()
- onUnmounted()
- OnMounted()
- onErrorCaptured()
- onDeactivated()
- onBeforeUpdated()
- onActivated()
- onServerPrefetch

| **Hook**         | **Cuándo se ejecuta**                                              | **¿Para qué se usa?**                                         |
| ---------------- | ------------------------------------------------------------------ | ------------------------------------------------------------- |
| beforeCreate     | Antes de que el componente sea creado.                             | Configurar opciones antes de que los datos estén disponibles. |
| onBeforeMount    | Antes de que el componente sea montado en el DOM.                  | Ajustes previos a la visualización.                           |
| onUpdated        | Después de que el componente haya sido actualizado.                | Realizar acciones después de cambios en los datos.            |
| onUnmounted      | Cuando el componente es desmontado.                                | Limpiar recursos como listeners o timers.                     |
| onMounted        | Después de que el componente ha sido montado en el DOM.            | Inicializar recursos dependientes del DOM.                    |
| onErrorCaptured  | Cuando ocurre un error en el componente o sus hijos.               | Capturar errores globalmente.                                 |
| onDeactivated    | Cuando el componente es desactivado (en <keep-alive>).             | Gestionar recursos cuando el componente es desactivado.       |
| onBeforeUpdated  | Justo antes de que el componente se actualice.                     | Realizar acciones antes de la actualización.                  |
| onActivated      | Cuando un componente previamente desactivado es activado de nuevo. | Inicializar recursos al volver a activar el componente.       |
| onServerPrefetch | Solo en renderizado en el servidor, antes de la renderización.     | Cargar datos antes de la renderización en el servidor.        |


| Estructura |
| ---------- |
| Lógica     |
| CSS        |

ejemplos:
**options API**

```ts
<script>
export default{
	data(){
		return{
			message: 'Hello World!'
		}
	}
}
</script>

<template>
	<h1>{{ message }}</h1>
</template>
```

**composition API** 
Se cambio a hooks y se mando a llamar ref.
Ref para el manejo de variables con reactividad

para usarlo seria message.value

las `{{ }}` accede al valor, por eso no dice message.value
- `ref` para datos primitivos
- `reactive` para datos estructurados
**Vue** utiliza un DOM virtual
```ts
<script setup>
import { ref } from 'vue'

const message = ref('Hello World');
</script>

<template>
	<h1>{{ message }}</h1>
</template>
```

**Componentes**
- Bloque de código reutilizable
- 

**Reactividad**
- Actualización automática
- Datos dinámicos
- Eficiencia
- Componentes (La reactividad funciona por medio de los componentes)
- Interaccions

**Reactividad:** Permite que Vue detecte cambios en los datos y actualice automáticamente la interfaz de usuario, Útil para crear aplicaciones dinámicas sin actualizar manualmente el DOM
## Desbaratando Vue
¿De qué se compone?


## Ventajas
¿Realmente es útil para mi?
## Implementación
¿Cómo lo uso?



