# Seguridad en el desarrollo de aplicaciones


# Sitio web vs Aplicación

- Un sitio es estático. Se basa más de un spa. Esta más enfocado a informar.
- Una aplicación, una implementación de una solución, tiene funcionalidad

# CRM

- Wordpress (gestión, administración y configuración de un sitio)

Los datos son oro

Nosotros nos encargamos de modificar, manipular, presentar y a veces de ... estos datos

---

# ¿Por qué es importante el desarrollo seguro?

### Riesgos de no priorizar la seguridad
- Perdida de datos sensibles.
- Vulnerabilidades como XSS, Inyección SQL, CSRF.
- Impacto en reputación de la organización.
- Indisponibilidad de nuestra aplicación - 404

game over a la aplicación

# Problema 
El 90% de las aplicaciones tienen vulnerabilidades críticas según la OWASP (Open Web Application Security Project)

https://haveibeenpwned.com

- El 90% porque ninguna aplicación esta exenta a fallar. 
	- **Lo que lo ocasiona:**
		- Aplicaciones legacy
		- Actualizaciones de librerías,
		- No se le da mantenimiento a la aplicación
		- Ahorro en el desarrollo

# ¿Con que se come un OWASP o que es un OWASP

OWASP (Open Web Application Security Project) Organización sin fines de lucro que trabaja para mejorar la seguridad del software.

Se basa en crear estándares.

**Dedicada a:**
- Proporcionar recomendaciones sobre seguridad de software.
- Ofrece capacitación e información gratuita sobre seguridad de aplicaciones.
- Establecer estándares para la seguridad de aplicaciones.

https://owasp.org

# ¿Qué debemos proteger?

- Entradas del usuario
	- Formularios , parámteros URL, APIs
- Datos sensibles
	- Contraseñas, tokens, informacion personal
- Buenas prácticas iniciales:
	- Definir políticas claras de contraseñas
	- Identificar diferentes puntos de ataque

# Ejemplo

```ts
// protección de política de contraseñas ejemplo:
const passwordPolicy = /^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$/;
const isValidpassword = (password) => passwordPolicy.test(password)
console.log(isValidpassword("Clave123")); // verdadero
```

```ts
// Protección de inyección de SQL ejemplo login de usuario:
const sqlinjection = /['"\\:]/;
const isValidUsername = (username) => !sqlInjection.test(username);
console.log(isValidUsername("admin")); // VERDADERO
console.log(isValidUsername("admin' OR '1'='1")); // FALSO
console.log(isValidUsername("admin; DROP TABLE users")); //FALSO
```


# Prevención desde el diseño

**Principios básicos**
- Principio del mínimo privilegio (PoLP): identificar cuales son el minimo privilegio que hay que darle a las librerias, que no pida acceso a todo y darselo sin más.
- Separación de datos sensibles del código: No subir los tokens harcodeados, entre otros datos sensibles, uso de .env.
- Validar entradas y salidas: una salida puede ser perturbada por una entrada.

**Control de dependencias:**
Usa herramientas como 
- npm audit: auditear nuestra app para ver si existen problemas criticos en ella
- yarn audit: 

---
==Revisar esto==
En vue hay un componente b que es una etiqueta que nos permite insertar mas html

esto deja abierto a que cualquier socio añada html con js y pueda agregar mas funcionalidades, pero ademas permite que otros puedan agregar codigo y atacarnos. hay que ver si es util desde la prevencion desde el diseño o sanitizar aquella entrada.

---
### Ejemplo

# ¿Cómo evitarlo?

- Revisar sin la librería o paquete esta en constante mantenimiento. no instalar cualquier librería.
- Hacer revisiones constantes con el comando `npm audit` para el package.json
- Instalar dependaBot en los repositorios github

# ¿Qué es XSS?

Principalmente encontrado en las aplicaciones web, permite a los atacantes inyectar scripts maliciosos en contenido donde se permite la entrada a los usuarios.
Puede provocar riesgosos daños al sitio como robo de cookies, tokens de sesión, robo de información sensible, reestructuración del sitio web o redirigir a sitios maliciosos.

# Otros ataques famosos
- **Fuerza bruta:** Decifrar un dato del lado del cliente.
- **Clickjacking:** un sitio web tapado de algo que puede ser, pero no es. Ej. cuando vas a descargar algo y sale un boton de descargar y no es el real de descargar.
- **Phishing:**
- **DDoS:** Usa fuerza bruta para realizar la denegación de servicio
- **SQL Injection:**

### ¿Cómo mitigarlo?

| Ataque        | Medidas de protección                                   |
| ------------- | ------------------------------------------------------- |
| DDOS          | Firewall de aplicaciones, limitación de ancho de banda. |
| Clickjacking  | C-Frame-Options: DENY, Content Security Policy (CSP).   |
| Inyección SQL | Uso de consultas preparadas, validación de entradas.    |
| Fuerza Bruta  | Implementar bloqueos tras múltiples intentos fallidos.  |

### Balanceador de carga
**Definición:**


# Desarrollo seguro paso a paso
**Validar entradas del usuario**
- Nunca confíes en el usuario.
- Ejemplo:

```ts
// Evita inyección de codigo en URL
const userId = req.query.id;
const safeUserId = encodeURIComponent(userId)
```

**Protege datos sensibles**
- Encriptación y hashing con bcrypt.
- Ejemplo:
```ts
// 
const bcrypt = require('bcrypt');
const hassPassword = await bcrypt.hash('MiContraseñaSegura', 10);
```

**Configuración de políticas de CORS (Evitar CSRF):**
```ts
// Configuración de politicas de CORS (Evitar CSRF)
const cors = require('cors)
app.use(cors({ origin: 'https://tusitioseguro.com'}));
```

**Gestión de dependencias**
Usar dependabot o npm audit fix
```bash
npm audit fix
```

# JWT (JSON Web Token)

**ACCES_TOKEN:**
Token de corta duración de autenticación de un inicio de sesión exitoso. Contiene al usuario y sus permisos, usando para acceder a recursos protegidos, validez corta para reducir el riesgo de acceso no autorizado.

**REFRESH_TOKEN:**
Token de mayor duración emitido durante la autenticación. Se utiliza para obtener un nuevo ACCESS_TOKEN sin volver a iniciar sesión. Esto representa una mejora a la seguridad al evitar que los usuarios ingresen repetidamente sus credenciales.

El refresh_token no es una capa de seguridad, es una capa de usabilidad, para que cuando el acces token se acabe, refresca el token sin volver a logearse.

Huella digital: permite guardar información extra para confirma que eres tú, con tu versión de tu navegador, tu computadora, tu version de navegador, tu ip.

Se usan del lado del usuario


# Pruebas de seguridad durante el desaroolo

**Automatización con herramientas:**
- ESLint Plugin Security (análisis estático).
- OWASP ZAP (análisis dinámico).
- Snvk (revisión de dependencias).

**Pruebas unitarias:**
- Asegúrate de probar validaciones de seguridad.
