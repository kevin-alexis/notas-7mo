# 1. Introducción al Desarrollo Seguro
### Importancia del desarrollo seguro.
### Impacto de las vulnerabilidades comunes (XSS, SQL Injection, etc.).
### Riesgos derivados de la falta de seguridad en aplicaciones.

# 2. Requisitos de Seguridad
### Identificación de elementos críticos a proteger: entradas del usuario, datos sensibles, variables de entorno,etc.
### Identificación de vectores y/o puntos de ataque.
### Buenas prácticas iniciales (políticas de contraseñas, estándares y arquitectura).

# 3. Diseño Seguro
### Principios de seguridad en el diseño (principio del mínimo privilegio – PoLP).
### Separación de datos sensibles del código.
### Control y revisión de dependencias.
### Importancia de la modularidad y la separación de responsabilidades.

# 4. Desarrollo Seguro
### Validación para la sanitización de entradas y salidas.
### Protección de datos sensibles mediante encriptación y hashing (ejemplo bcrypt) y donde aplicarlo.
### Uso adecuado de tokens: ACCESS_TOKEN (de corta y/o larga duración) y REFRESH_TOKEN.
### Malas practicas en el desarrollo de software (API_KEY’s en commits)
### Configuración de políticas de seguridad (CORS, IP’s, Roles, Permisos)

# 5. Gestión de Dependencias
### Uso de herramientas para la gestión de dependencias npm audit, yarn audit y automatización.
### Importancia de mantener las dependencias actualizadas y en mantenimiento activo.

# 6. Pruebas de Seguridad
### Implementación de pruebas análisis de seguridad como software.
### Revisión y auditoría constante del código (mantenimiento post-deploy).

# 7. Ataques Comunes y sus Contramedidas
### Descripción y mitigación de ataques como XSS, SQL Injection, DDoS, Clickjacking y fuerza bruta.
### Medidas de protección específicas: firewalls, consultas preparadas, bloqueo tras múltiples intentos, etc.


# 8. Buenas Prácticas en Seguridad
### “Nunca confíes en el usuario”: validación y sanitización de datos.
### Importancia de la separación entre datos sensibles y lógica de negocio.
### Revisión continua y actualización de dependencias y librerías.
### “Si sirve no lo toques...al menos que te paguen demasiado bien ”