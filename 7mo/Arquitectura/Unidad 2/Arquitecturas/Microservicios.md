## Definición
Un microservicio es un estilo arquitectónico que se utiliza para desarrollar aplicaciones como una colección de servicios pequeños, independientes y autónomos. Cada microservicio se centra en una funcionalidad específica de la aplicación y se comunica con otros microservicios a través de interfaces bien definidas, generalmente utilizando APIs. Esto permite una mayor escalabilidad, flexibilidad y facilidad de mantenimiento, ya que los equipos pueden trabajar en diferentes microservicios de manera independiente.

## En que se basa
- **Descomposición de la aplicación**: La arquitectura de microservicios divide una aplicación monolítica en componentes más pequeños y manejables. Cada microservicio es responsable de una única funcionalidad o un conjunto de funcionalidades relacionadas.
- **Desarrollo independiente**: Cada microservicio puede ser desarrollado, implementado y escalado de manera independiente. Esto permite que diferentes equipos trabajen simultáneamente en distintas partes de la aplicación sin interferir entre sí.
- **Escalabilidad**: Los microservicios pueden escalar de manera independiente, lo que significa que se pueden aumentar los recursos solo para aquellos servicios que lo necesitan, optimizando así el uso de recursos.
- **Tecnología heterogénea**: Cada microservicio puede ser desarrollado utilizando diferentes tecnologías, lenguajes de programación o bases de datos, lo que permite a los equipos elegir la mejor herramienta para cada tarea.
- **Resiliencia**: Si un microservicio falla, el resto de la aplicación puede continuar funcionando, lo que mejora la resiliencia y la disponibilidad general del sistema.

## Esquema
- **Microservicios**: Cada bloque representa un microservicio que realiza una función específica.
- **API Gateway**: Un punto de entrada para todas las solicitudes que se dirigen a los microservicios, actuando como intermediario para enrutar las peticiones.
- **Cliente/Front**: El cliente que interactúa con la aplicación, que puede ser una aplicación web, móvil, etc.

## Estructura
![[Pasted image 20241105114414.png]]

## Ejemplos
- **E-commerce**: En una aplicación de comercio electrónico, diferentes microservicios pueden manejar distintas funciones como el catálogo de productos, el procesamiento de pagos, la gestión de usuarios y la gestión de pedidos. Cada uno de estos microservicios puede ser desarrollado y escalado de forma independiente.
- **Aplicaciones bancarias**: Una aplicación bancaria podría tener microservicios dedicados a la gestión de cuentas, transacciones, reportes y notificaciones. Cada microservicio puede estar escrito en diferentes lenguajes o usar distintas bases de datos según las necesidades.
- **Servicios de streaming**: En un servicio de streaming de video, podrían existir microservicios para el manejo de usuarios, el almacenamiento y distribución de videos, y la analítica del uso. Esto permite a los desarrolladores actualizar y escalar diferentes partes de la plataforma de manera independiente.
- **Aplicaciones SaaS**: Las aplicaciones Software as a Service (SaaS) a menudo utilizan una arquitectura de microservicios para ofrecer funcionalidades modulares a sus usuarios, permitiendo personalización y escalabilidad.
- **Redes sociales**: En una aplicación de red social, diferentes microservicios pueden manejar la gestión de perfiles, publicaciones, comentarios y notificaciones, permitiendo un desarrollo ágil y eficiente.