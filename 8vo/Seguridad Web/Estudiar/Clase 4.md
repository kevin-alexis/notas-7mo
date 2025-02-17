
composable: como un componente pero de lógica, para reutilizar código.
data: campos o valores que no cambiaran segun la interacción de los usuarios.
service: servicio para hacer una petición a un servicio o api.
interfaces: forma de estandarizar los datos para saber que respuesta o que valores estamos esperando.
router: para las rutas de las vistas
stores: para manejar el estado global de la aplicación
utils: pequeños scripts para la lógica, se podria decir que algo como composable


Los parametros de una url: para definir cierta información y podamos compartirla.

----
Props o propiedades: aquellos atributos que podemos esperar recibir o definir en un componente.
`<slot />`: renderiza el html que se le envia al componente a traves de template, lo metes entre las dos etiquetas

se puede hacer diferentes tipos de slot. se le puede poner title, para que el padre le diga al hijo donde renderizarlo
`<slot title="image" />`
`<slot title="description" />`

`:disabled="disabled"` los : es para que sepa que es variable lo que se le envia

ref - variable reactivo

los inputs y las diferentes etiquetas que requieren un valor van a requerir la etiqueta v-model, el cual hace un vindeo, el vindeo se hace con los dos puntos :

vindear es crear una conexión entre la reactividad y lo estatico(creo)

tiene atributos y eventos
atributos: al detectar una entrada realice una accion (como un input al entrar)
eventos: al detectar un evento realice una accion (como un boton on click)



**Datos computados**: representaciones simbólicas que un ordenador puede procesar y mostrar como información que lo hace cuando cambia el valor reactivo

**onMounted:** cuando se monta el componente, ejecuta las funciones dentro de onMounted


vue y los componentes no pueden comunicarse de forma horizontal.

con emits y providers se puede comunicar de diferente niveles padre e hijo
- **`emit`**:
    - Es útil para la **comunicación de hijo a padre**.
    - Funciona mediante eventos.
    - El padre escucha el evento y maneja los datos o acciones.
    
- **`provide/inject`**:
    - Se usa para compartir datos entre **componentes no directamente relacionados**.
    - Ideal para compartir datos entre varios niveles de la jerarquía de componentes.
    - El componente proveedor (`provide`) pone a disposición los datos, y el componente receptor (`inject`) los recibe.


el store permite compartir datos donde la información va hacia cada componente