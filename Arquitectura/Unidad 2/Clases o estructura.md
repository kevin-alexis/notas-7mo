### Singleton
- **Singleton**: La clase que contiene la instancia única.
- **instancia**: Variable privada que almacena la única instancia.
- **getInstance()**: Método estático que devuelve la instancia. Si la instancia no existe, la crea.
- **metodoEjemplo()**: Un método de la clase que puede ser utilizado por otras clases.

### Factory Method
- **Producto**: Define la interfaz común para los objetos que serán creados.
- **Producto Concreto**: Implementa la interfaz del producto, es decir, cada clase concreta representa un tipo de producto.
- **Creador**: Declara el método `factoryMethod` que devuelve objetos del tipo `Producto`. Este método es abstracto en el creador, por lo que las subclases deben implementarlo.
- **Creador Concreto**: Extiende al Creador y sobrescribe el método `factoryMethod` para retornar instancias de `ProductoConcreto`.

### Abstract Factory
- **AbstractFactory**: Interfaz para crear diferentes tipos de objetos relacionados.
- **ConcreteFactory**: Implementa la interfaz `AbstractFactory` y crea una variante específica de cada producto.
- **AbstractProduct**: Interfaz para un tipo específico de producto dentro de la familia.
- **ConcreteProduct**: Implementa `AbstractProduct` y define un producto específico de una variante.
- **Cliente (Client)**: Usa la fábrica abstracta para obtener los productos necesarios sin saber cuáles son sus implementaciones concretas.

### Builder
- **Producto (Product)**: El objeto complejo que se crea a partir de los pasos realizados por el Builder. Es el resultado final.
2. **Builder**: Es una interfaz o clase abstracta que define los pasos necesarios para crear el objeto.
3. **Specific Builder**: Crea las partes del objeto complejo. El specific builder se le dice: CasaDeLujo. Implementa la interfaz `Builder` y proporciona una implementación específica para cada paso de construcción.
4. **Director**: Este actor construye el objeto complejo con la interfaz del constructor. Acciona los parámetros. Esta clase (opcional) controla el proceso de construcción. Llama a los métodos del Builder en un orden específico para crear el objeto. El cliente puede usarlo para construir el objeto de una manera particular sin preocuparse de los detalles.
5. **Cliente**: El cliente que utiliza el director para obtener el producto final.

### Cliente-Servidor
- **Cliente**: Es el dispositivo o aplicación que realiza solicitudes de servicios o recursos. Los clientes pueden ser navegadores web, aplicaciones móviles, programas de correo electrónico, etc.
- **Servidor**: Es el sistema que recibe las solicitudes del cliente, procesa esos pedidos y envía las respuestas correspondientes. Los servidores pueden ser servidores web, servidores de bases de datos, servidores de archivos, etc.
- **Protocolos de comunicación**: Son las reglas que definen cómo se transmiten los datos entre el cliente y el servidor. Algunos ejemplos son:
    - **HTTP** (Hypertext Transfer Protocol): Utilizado para la transferencia de páginas web.
    - **SMTP** (Simple Mail Transfer Protocol): Utilizado para el envío de correos electrónicos.
    - **POP3** (Post Office Protocol 3): Utilizado para la recuperación de correos electrónicos.

### Peer to peer
- **Nodos**: Son los participantes de la red, que pueden ser dispositivos como computadoras, smartphones, etc.
- **Conexiones**: Establecen la comunicación entre los nodos. Pueden ser conexiones directas o a través de otros nodos.
- **Protocolo de comunicación**: Define cómo los nodos se comunican y comparten datos entre ellos.
- **Sistema de identificación**: Permite a los nodos identificarse unos a otros, facilitando la conexión y el intercambio de datos.

### Microservicio
- **Microservicios**: Cada bloque representa un microservicio que realiza una función específica.
- **API Gateway**: Un punto de entrada para todas las solicitudes que se dirigen a los microservicios, actuando como intermediario para enrutar las peticiones.
- **Cliente/Front**: El cliente que interactúa con la aplicación, que puede ser una aplicación web, móvil, etc.

### Hexagonal
- **Puertos**: Interfaces que definen las operaciones que la lógica de negocio ofrece. Pueden ser puertos de entrada (interacciones desde el exterior hacia la lógica de negocio) y puertos de salida (interacciones desde la lógica de negocio hacia el exterior).
- **Adaptadores**: Implementaciones concretas de los puertos que permiten que la lógica de negocio se comunique con el mundo exterior. Por ejemplo, un adaptador de un controlador de API REST que llama a la lógica de negocio.
- **Lógica de negocio**: Contiene las entidades del dominio y las reglas de negocio. Esta parte es independiente de los detalles de implementación.
- **Infraestructura**: Aquí se encuentran los detalles técnicos, como la base de datos, servicios de mensajería, APIs externas, etc. Se accede a través de los puertos y adaptadores.

### Onion
- **Interfaces**: Capa más externa que se encarga de recibir las solicitudes y devolver las respuestas, como controladores o APIs.
- **Aplicación**: Contiene la lógica de aplicación y orquesta las operaciones entre la capa de dominio y la infraestructura.
- **Dominio**: La capa más interna que contiene la lógica de negocio, las entidades y las reglas del dominio.
- **Infraestructura**: Capa que interactúa con bases de datos, servicios externos, y cualquier otro detalle técnico.

#### Estructura 
Las dependencias solo van de afuera hacia adentro
- **Núcleo**
- **Capa externa**

La capa externa no esta atada al núcleo

#### Núcleo
- Modelo de dominio
	- Entidades
- Servicios de dominio
	- Interfaces
	- DTO
- Servicios de aplicación
	- Lógica de negocio

#### Capa Externa
- Pruebas
- Interfaz gráfica
- Infraestructura
	- Bases de datos
	- Sistemas de archivos
	- Servicios web
- Dispositivos
