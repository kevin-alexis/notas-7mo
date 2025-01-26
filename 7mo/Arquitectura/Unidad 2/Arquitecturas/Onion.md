## Definición
La Onion Architecture (Arquitectura en Cebolla) es un patrón de diseño de software que busca resolver los problemas de dependencia y facilitar el desarrollo de aplicaciones escalables y mantenibles. Se basa en la separación de preocupaciones mediante capas concéntricas que delimitan la lógica de negocio del resto del sistema. En este enfoque, las dependencias apuntan hacia el interior, lo que significa que las capas externas no pueden depender de las internas.

## Notas
- Esta pensada para lenguajes de programación orientados a objetos..
- Ideal para aplicaciones complejas.
- Las capas se comunican a través de interfaces.
## En que se basa
- **Separación de preocupaciones**: Cada capa de la aplicación tiene responsabilidades claramente definidas, lo que mejora la organización y la mantenibilidad del código.
- **Independencia de la infraestructura**: La lógica de negocio no está acoplada a la tecnología específica (como bases de datos o frameworks), lo que permite que la aplicación sea más flexible y fácil de probar.
- **Pruebas unitarias**: Al tener la lógica de negocio aislada, es más fácil realizar pruebas unitarias sin la necesidad de depender de la infraestructura o de otras capas.
- **Inversión de dependencias**: La lógica de negocio no debe depender de los detalles, sino que los detalles deben depender de la lógica de negocio, lo que favorece una arquitectura más robusta.

## Esquema
- **Interfaces**: Capa más externa que se encarga de recibir las solicitudes y devolver las respuestas, como controladores o APIs.
- **Aplicación**: Contiene la lógica de aplicación y orquesta las operaciones entre la capa de dominio y la infraestructura.
- **Dominio**: La capa más interna que contiene la lógica de negocio, las entidades y las reglas del dominio.
- **Infraestructura**: Capa que interactúa con bases de datos, servicios externos, y cualquier otro detalle técnico.

## Estructura
- **Capa de dominio**: Aquí se encuentran las entidades del negocio y la lógica que define el comportamiento del sistema. Esta capa es independiente de cualquier tecnología específica.
- **Capa de aplicación**: Contiene servicios que manejan la lógica de aplicación, orquestan el flujo de datos y comunican la capa de dominio con la capa de presentación o infraestructura.
- **Capa de interfaces**: Esta capa se encarga de recibir y enviar datos a través de controladores, APIs, y cualquier otro medio de interacción con el usuario o sistemas externos.
- **Capa de infraestructura**: Provee implementaciones concretas para la capa de dominio y de aplicación. Aquí se encuentran los repositorios, acceso a bases de datos, y servicios externos.

## Ejemplos
- **Aplicaciones de gestión empresarial**: En un sistema de gestión empresarial, la capa de dominio puede incluir entidades como `Empleado`, `Departamento` y `Proyecto`, mientras que la capa de infraestructura puede implementar el acceso a bases de datos y servicios de terceros.
    
- **E-commerce**: En una aplicación de comercio electrónico, la capa de dominio podría incluir entidades como `Producto`, `Orden` y `Cliente`, y las capas externas manejarían la interfaz de usuario y las integraciones de pago.
    
- **Sistemas de facturación**: La lógica para calcular impuestos y gestionar clientes estaría en la capa de dominio, mientras que la comunicación con servicios de facturación y almacenamiento de datos se manejaría en la capa de infraestructura.
    
- **Aplicaciones de redes sociales**: La lógica de usuario, publicaciones y comentarios puede estar en la capa de dominio, mientras que la infraestructura maneja la persistencia de datos y la integración con otras APIs (como APIs de terceros para imágenes o autenticación).
    
- **Plataformas de streaming**: En este tipo de aplicaciones, la lógica de negocio (como la gestión de usuarios y contenido) residiría en la capa de dominio, mientras que la capa de infraestructura gestionaría la conexión a bases de datos y servicios de contenido.

## Ventajas y Desventajas

**Ventajas**
- Facilidad de mantenerse
- Independencia de tecnologias
- Pruebas más fáciles

**Desventajas**
- Curva de aprendizaje difícil
- Sobrecarga para proyectos pequeños

## Estructura 
Las dependencias solo van de afuera hacia adentro
- **Núcleo**
- **Capa externa**

La capa externa no esta atada al núcleo

## Núcleo
- Modelo de dominio
	- Entidades
- Servicios de dominio
	- Interfaces
	- DTO
- Servicios de aplicación
	- Lógica de negocio

## Capa Externa
- Pruebas
- Interfaz gráfica
- Infraestructura
	- Bases de datos
	- Sistemas de archivos
	- Servicios web
- Dispositivos

Permite conectarse a diferentes bases de datos

### En Capas Layer (Adyacente)
Puedes saltarte capas

### En Capas Onion
No puedes saltarte capas

