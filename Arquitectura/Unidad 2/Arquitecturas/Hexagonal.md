## Definición
La arquitectura hexagonal, también conocida como "Arquitectura de puertos y adaptadores", es un patrón de diseño que se centra en la separación de la lógica de negocio de los detalles de implementación, como la interfaz de usuario, las bases de datos y otros servicios externos. Su objetivo es facilitar el desarrollo, las pruebas y el mantenimiento de aplicaciones al permitir que la lógica de negocio se comunique a través de puertos definidos y se adapte a diferentes interfaces y tecnologías sin que la lógica misma se vea afectada.

## En que se basa
- **Separación de preocupaciones**: Al igual que la Onion Architecture, la arquitectura hexagonal promueve la separación de la lógica de negocio y los detalles técnicos, lo que mejora la mantenibilidad del código.
- **Adaptadores y puertos**: Se basa en la idea de que la lógica de negocio se comunica a través de puertos (interfaces) y utiliza adaptadores (implementaciones concretas) para interactuar con el mundo exterior.
- **Flexibilidad**: Permite cambiar la interfaz de usuario, la base de datos o cualquier otro sistema externo sin afectar la lógica de negocio.
- **Pruebas aisladas**: La separación de la lógica de negocio de la infraestructura facilita la realización de pruebas unitarias y de integración, ya que se puede probar la lógica en aislamiento.

## Esquema
- **Interfaz de Usuario**: Puede ser una aplicación web, móvil o cualquier tipo de frontend que interactúe con la lógica de negocio.
- **Adaptador**: Conecta la interfaz de usuario con la lógica de negocio a través de los puertos.
- **Puerto**: Define las interfaces que la lógica de negocio expone para que los adaptadores se comuniquen con ella.
- **Lógica de Negocio**: Contiene las reglas y el comportamiento del sistema.
- **Base de Datos y otros sistemas externos**: Conectados a través de adaptadores que implementan la lógica necesaria para interactuar con ellos.

## Estructura
- **Puertos**: Interfaces que definen las operaciones que la lógica de negocio ofrece. Pueden ser puertos de entrada (interacciones desde el exterior hacia la lógica de negocio) y puertos de salida (interacciones desde la lógica de negocio hacia el exterior).
- **Adaptadores**: Implementaciones concretas de los puertos que permiten que la lógica de negocio se comunique con el mundo exterior. Por ejemplo, un adaptador de un controlador de API REST que llama a la lógica de negocio.
- **Lógica de negocio**: Contiene las entidades del dominio y las reglas de negocio. Esta parte es independiente de los detalles de implementación.
- **Infraestructura**: Aquí se encuentran los detalles técnicos, como la base de datos, servicios de mensajería, APIs externas, etc. Se accede a través de los puertos y adaptadores.

## Ejemplos
- **Aplicaciones de comercio electrónico**: En una aplicación de e-commerce, la lógica de negocio podría incluir operaciones como crear pedidos y gestionar productos. Los adaptadores podrían incluir un API REST para interactuar con la aplicación web y un adaptador para la base de datos que almacena los productos y pedidos.
- **Sistemas de gestión de contenido**: La lógica para crear, leer, actualizar y eliminar contenido estaría en la parte central de la aplicación. Se podría tener un adaptador de API que permita a los frontends consumir estos servicios, y otro adaptador para conectarse a un sistema de almacenamiento de archivos.
- **Aplicaciones bancarias**: En una aplicación de banca en línea, la lógica de negocio podría incluir operaciones como transferencias y gestión de cuentas. Los puertos y adaptadores permitirían que la aplicación se conectara a diferentes interfaces de usuario y sistemas de pago.
- **Servicios de chat**: La lógica de negocio podría incluir la gestión de mensajes y usuarios. Adaptadores para la API REST y para la base de datos permitirían una comunicación fluida entre la interfaz de usuario y la lógica del chat.
- **Aplicaciones de IoT**: En un sistema de gestión de dispositivos IoT, la lógica de negocio podría controlar el comportamiento de los dispositivos. Los adaptadores permitirían la comunicación con interfaces de usuario y el acceso a bases de datos para almacenar el estado de los dispositivos.