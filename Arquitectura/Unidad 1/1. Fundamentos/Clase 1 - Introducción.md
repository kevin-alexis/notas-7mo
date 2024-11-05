# **Fundamentos de arquitectura de software**

### Porcentajes:

 - 50% Practicas y Tareas
 - 40% Examen
 - 10% Asistencia

La arquitectura, referida al software, es un concepto que surge ya en los años 60 y se refiere a una planificación basada en modelos, patrones y abstracciones teóricas, a la hora de realizar una pieza de software de cierta complejidad y como paso previo a cualquier implementación. De esta forma se dispone de una guía teórica detallada que nos permite entender cómo van a encajar cada una de las piezas de nuestro producto o servicio

### **Importancia de la arquitectura de software**

La arquitectura nos permite planificar nuestro desarrollo y elegir el mejor conjunto de herramientas para llevar a cabo nuestros proyectos, es por tanto un paso critico antes de pasar a programar ya que determinará en gran medida el ritmo del desarrollo e incluso factores económicos y humanos durante el proceso

### **Coste**

¿Cuánto estamos dispuestos a invertir en el desarrollo y mantenimiento de nuestro sistema? Como hemos visto hay ciertos patrones más complejos, que requieren más infraestructura y cuyo desarrollo puede ser más irregular, por tanto, hemos de saber cuánto estamos dispuestos a invertir primero en el desarrollo de nuestra aplicación
### **Tiempo de desarrollo**

Igualmente, y muy relacionado con lo anterior, debemos de preguntarnos cuanto tiempo disponemos para desarrollar el producto, y cómo de cerca se encontraría la fecha de entrega o de salida al mercado

### **Número de usuarios**

Sin duda uno de los ítems críticos a la hora de desarrollar el producto es preguntarnos que tipo de producto es y cuantos usuarios soporta

- ¿Funciona a través de web?
- ¿Es stand-alone?
- ¿Debe de soportar cargas elevadas de diseño?

Estas preguntas pueden declinarnos a elegir patrones más o menos distribuidos, pasando, por ejemplo, de uno menos distribuido como el de capas al más distribuido o broker

>[!Info] En el sector de la informática, un programa **stand alone** es aquel que puede funcionar de manera independiente sin necesidad de estar conectado a internet o depender de otros programas o servidores para su correcto y completo funcionamiento.
### **Nivel de aislamiento**

Otro factor importante a tener en cuenta es si nuestro producto funciona de forma aislada al resto de productos del usuario o si debe de integrarse o permitir integraciones de terceros. Algunas arquitecturas, como la de capas, son más cerradas y podrían dificultar estas integraciones si lo escogemos sobre otras

## **Características de la arquitectura**

Cualquier arquitectura exitosa depende de qué tan bien definamos las Características de la Arquitectura. Hay muchos atributos de calidad del sistema que podemos discutir, las siguientes características de la arquitectura constituyen una base sólida para que la arquitectura de software moderna desarrolle un producto exitoso

![[Pasted image 20240912094022.png]]
### **1. Comprensibilidad**

La arquitectura de software no solo debe ser efectiva, sino también fácil de entender para los equipos de desarrollo y las partes interesadas. Un nuevo desarrollador debería poder comprenderla con una breve introducción
*Consideraciones:* Entender las necesidades de los equipos y conocer sus fortalezas y debilidades
### **2. Facilidad de uso y Aprendizaje**

La usabilidad depende de factores como los usuarios objetivos y la facilidad de uso. Las características del producto deben ser claras y fáciles de aprender. La decisión de adoptar nuevas tecnologías debe considerar lo rápido que los desarrolladores pueden aprenderlas
*Consideraciones:* Identificar usuarios, garantizar accesibilidad y visibilidad de características, investigar tecnologías nuevas
### **3. Asegurabilidad**

Las aplicaciones expuestas a la web enfrentan riesgos de ciberataques. Se deben implementar mecanismos de autenticación, autorización, auditoría y cifrado de datos
*Consideraciones:* Autenticación, uso de protocolos seguros, protección contra ataques DDoS e inyecciones SQL, y auditoría de actividades
### **4. Confiabilidad y disponibilidad**

La confiabilidad implica que el sistema funciones bajo condiciones predefinidas. La disponibilidad se mide en porcentaje (99.9% = 8 horas 45 minutos de inactividad al año)
*Consideraciones:* Planes de recuperación, notificaciones de fallos y tiempos de inactividad aceptables

>[!Info] Calculadora de disponibilidad: https://uptime.is/99.9

### **5. Interoperabilidad**

Las aplicaciones deben comunicarse con sistemas externos o heredados.  La interoperabilidad se facilita con interfaces bien diseñadas, pero los sistemas heredados pueden presentar dificultades
*Consideraciones:* Formatos de datos, versiones de API, compatibilidad retroactiva 
### **6. Comprobabilidad**

Un 30-40% del costo de software se destina a pruebas. Es esencial diseñar la arquitectura para que los componentes sean probables. Esto incluye la capacidad de reproducir entornos de prueba y detectar problemas rápidamente
*Consideraciones:* Requisitos de negocio consistentes, entornos similares para pruebas, captura de resultados de pruebas
### **7. Escalabilidad**

A medida que crecen los usuarios, la aplicación debe poder escalar sin perder rendimiento. Existen dos tipos de escalado: vertical (más hardware) y horizontal (más servidores)
*Consideraciones:* Número de usuarios, datos generados, operaciones de CPU/memoria, funciones de larga duración

### **8. Rendimiento**

El rendimiento se mide en términos de velocidad, precisión, y capacidad para manejar solicitudes. Esto depende de la escalabilidad y otros factores de diseño
*Consideraciones:* Escalado horizontal, balanceo de carga, procesamiento en paralelo, soluciones de caché
### **9. Agilidad**

La arquitectura debe ser lo suficientemente ágil para adaptarse rápidamente a los cambios y demandas del mercado. Se recomienda anticipar lo justo y necesario para evitar complejidades excesivas
*Consideraciones:* Desarrollo "justo a tiempo", enfoque continuo en las características del cliente, análisis del backlog y deuda técnica
### **10. Observabilidad**

La observabilidad implica monitorear el estado de los servicios distribuidos en infraestructuras modernas. Involucra la gestión de registros y la recolección de datos para entender qué sucede y actuar rápidamente
*Consideraciones:* Gestión centralizada de logs, visualización en dashboards, y notificaciones para acciones rápidas
### **11. Tolerancia a Fallos**

Las aplicaciones deben continuar operando, aunque sea a un nivel reducido, en caso de fallos. Se deben prever fallos de diseño y en tiempo de ejecución, y tomar medidas para recuperarse
*Consideraciones:* Detección de fallos, acciones de recuperación y prevención