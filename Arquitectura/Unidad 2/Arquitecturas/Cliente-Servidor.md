## En que se basa
- **Comunicación en red**: El modelo cliente-servidor se basa en la interconexión de múltiples dispositivos a través de una red, donde los clientes solicitan recursos y servicios de un servidor.
- **Relación cliente-servidor**: Este modelo establece una clara distinción entre los roles de los clientes, que inician solicitudes, y los servidores, que responden a esas solicitudes y proporcionan servicios o recursos.

## Definición
El modelo cliente-servidor es un paradigma de arquitectura de red en el que las tareas y responsabilidades se dividen entre los proveedores de recursos o servicios, llamados servidores, y los solicitantes de esos recursos, conocidos como clientes. En este modelo, los clientes envían solicitudes al servidor, que las procesa y devuelve los resultados. Este enfoque permite una gestión eficiente de recursos, escalabilidad y facilidad de mantenimiento.

## Esquema
- **Cliente**: Es el dispositivo o aplicación que realiza solicitudes de servicios o recursos. Los clientes pueden ser navegadores web, aplicaciones móviles, programas de correo electrónico, etc.
- **Servidor**: Es el sistema que recibe las solicitudes del cliente, procesa esos pedidos y envía las respuestas correspondientes. Los servidores pueden ser servidores web, servidores de bases de datos, servidores de archivos, etc.
- **Protocolos de comunicación**: Son las reglas que definen cómo se transmiten los datos entre el cliente y el servidor. Algunos ejemplos son:
    - **HTTP** (Hypertext Transfer Protocol): Utilizado para la transferencia de páginas web.
    - **SMTP** (Simple Mail Transfer Protocol): Utilizado para el envío de correos electrónicos.
    - **POP3** (Post Office Protocol 3): Utilizado para la recuperación de correos electrónicos.

## Estructura
- **Cliente**: Interfaz que permite al usuario enviar solicitudes al servidor. Puede estar en una computadora, dispositivo móvil, etc.
- **Servidor**: Programa o sistema que recibe solicitudes del cliente y devuelve respuestas. Puede incluir bases de datos y lógica de negocio.
- **Protocolo de comunicación**: Conjunto de reglas que define la comunicación entre cliente y servidor.
- **Red**: Infraestructura que permite la comunicación entre clientes y servidores. Puede ser local (LAN) o global (Internet).

![[Pasted image 20241105111032.png]]

## Ejemplos
- **Una aplicación web**: Un navegador web (cliente) solicita una página web a un servidor web, que procesa la solicitud y devuelve la página HTML al navegador.
    
- **Correo electrónico**: Un cliente de correo electrónico (como Outlook) envía un mensaje a un servidor SMTP, que se encarga de entregarlo al servidor de correo del destinatario.
    
- **Base de datos**: Una aplicación (cliente) envía consultas SQL a un servidor de bases de datos, que procesa la consulta y devuelve los resultados.
    
- **Servicios en la nube**: Aplicaciones como Google Drive o Dropbox utilizan un modelo cliente-servidor donde los clientes acceden a servicios y almacenamiento ofrecidos por servidores en la nube.
    
- **Videojuegos en línea**: Los jugadores (clientes) se conectan a un servidor de juego, que maneja las interacciones y el estado del juego, enviando actualizaciones a cada cliente.