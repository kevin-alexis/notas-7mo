# Seguridad en el desarrollo de aplicaciones


# Sitio web vs Aplicación

- Un sitio es estático, es un conjunto de páginas web. Se basa más de un spa. Esta más enfocado a informar.
- Una aplicación, es una implementación de una solución, tiene funcionalidad.

# CRM (Customer Relationship Management)
Gestión de Relaciones con Clientes, es un conjunto de estrategias, tecnologías y prácticas que ayudan a las empresas a administrar y analizar sus interacciones con los clientes.

- Wordpress (gestión, administración y configuración de un sitio)

Los datos son oro
Los desarrolladores se encargan de modificar, manipular, presentar y a veces de ... estos datos

---

# ¿Por qué es importante el desarrollo seguro?

El desarrollo seguro es importante porque ayuda a proteger los datos de los usuarios, la reputación de las organizaciones y a cumplir con normativas.

### Impacto de las vulnerabilidades comunes
- XSS (CROSS-SITE SCRIPTING)
	- **Impacto:**
	- Permite a un atacante inyectar scripts maliciosos en páginas web legítimas.
	- Puede robar cookies de sesión, credenciales de usuario o realizar acciones en nombre de la víctima.
	- Facilita ataques de phishing y redirecciones maliciosas.
	- **Ejemplo:**
	- Un formulario de comentarios que permite la inserción de `<script>alert('Hacked!');</script>` y ejecuta el código en el navegador de otros usuarios.
	
- SQL INJECTION
	- **Impacto:**
	- Permite a un atacante manipular consultas SQL para acceder, modificar o eliminar datos en la base de datos.
	- Puede exponer información sensible como contraseñas, datos de tarjetas de crédito, etc.
	- En casos extremos, permite tomar control total del servidor de la base de datos.
	🔹 **Ejemplo:**
	- Un campo de inicio de sesión vulnerable donde se ingresa:
	    `' OR '1'='1`
	    lo que da acceso sin autenticación.
	    
- CSRF
	- **Impacto:**
	- Engaña a un usuario autenticado para ejecutar acciones no deseadas en una aplicación en la que está registrado.
	- Puede modificar información, transferir dinero o cambiar contraseñas sin que el usuario lo note.
	🔹 **Ejemplo:**
	- Un atacante envía un enlace a una víctima autenticada que, al hacer clic, cambia su dirección de correo sin su consentimiento.
	
- Fuerza bruta
	- **Impacto:**
	- Un atacante intenta adivinar contraseñas probando combinaciones hasta encontrar la correcta.
	- Puede llevar al acceso no autorizado a cuentas de usuario o sistemas críticos.
	- En combinación con credenciales filtradas, facilita el acceso indebido a múltiples cuentas.
	🔹 **Ejemplo:**
	- Un atacante usa herramientas como Hydra o John the Ripper para intentar miles de combinaciones de contraseñas en un portal de inicio de sesión.
	
- Clickjacking 
	- **Impacto:**
	- Engaña a los usuarios para que hagan clic en elementos ocultos de una página web, como botones o enlaces peligrosos.
	- Puede provocar la activación de funciones maliciosas sin el consentimiento del usuario.
	- Se usa para robar credenciales, activar cámaras/micrófonos o realizar acciones en sitios autenticados.
	🔹 **Ejemplo:**
	- Un atacante inserta un iframe invisible sobre un botón legítimo, haciendo que el usuario haga clic en "Comprar" en lugar de "Cerrar".

- Phishing
	- **Impacto:**
	- Los atacantes envían correos electrónicos o mensajes fraudulentos que imitan fuentes legítimas.
	- Engañan a los usuarios para que ingresen credenciales o descarguen malware.
	- Se usa para obtener acceso a información personal, bancaria o corporativa.
	🔹 **Ejemplo:**
	- Un correo falso de "soporte técnico" que redirige a una página de inicio de sesión idéntica a la real para robar credenciales.

- DDoS 
	- **Impacto:**
	- Los atacantes envían grandes volúmenes de tráfico a un servidor, saturándolo hasta dejarlo inoperativo.
	- Puede afectar la disponibilidad de servicios críticos, provocando pérdidas económicas.
	- Se usa como parte de ataques de extorsión o sabotaje.
	🔹 **Ejemplo:**
	- Una botnet (red de dispositivos comprometidos) lanza millones de solicitudes simultáneas contra un sitio web para colapsarlo


### Riesgos de no priorizar la seguridad
- Perdida de datos sensibles.
- Vulnerabilidades como XSS, Inyección SQL, CSRF.
- Impacto en reputación de la organización.
- Indisponibilidad de nuestra aplicación - 404
- game over a la aplicación

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

**Se dedicada a:**
- Proporcionar recomendaciones sobre seguridad de software.
- Ofrece capacitación e información gratuita sobre seguridad de aplicaciones.
- Establecer estándares para la seguridad de aplicaciones.

https://owasp.org

# ¿Qué debemos proteger?

- Entradas del usuario
	- Formularios , parámetros URL, APIs
- Datos sensibles
	- Contraseñas, tokens, información personal
- Variables de Entorno
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
const sqlinjection = /['"\\;]/;
const isValidUsername = (username) => !sqlInjection.test(username);
console.log(isValidUsername("admin")); // VERDADERO
console.log(isValidUsername("admin' OR '1'='1")); // FALSO
console.log(isValidUsername("admin; DROP TABLE users")); //FALSO
```


# Prevención desde el diseño

**Principios básicos**
- Principio del mínimo privilegio (PoLP - Principle of Least Privilege): identificar cuales son el mínimo privilegio que hay que darle a las librerías, que no pida acceso a todo y dárselo sin más.
- Separación de datos sensibles del código: No subir los tokens harcodeados, entre otros datos sensibles, uso de .env.
- Validar entradas y salidas: una salida puede ser perturbada por una entrada.

**Control de dependencias:**
El control de dependencias es un aspecto esencial en el desarrollo de software, ya que permite gestionar las bibliotecas o paquetes de terceros que se utilizan en una aplicación. Utilizar herramientas que auditán y controlan estas dependencias ayuda a garantizar la seguridad y estabilidad del proyecto.

Usa herramientas como 
- npm audit: auditar nuestra app para ver si existen problemas críticos en ella
	 - **`npm audit`** es una herramienta de npm que permite analizar las dependencias de un proyecto Node.js en busca de vulnerabilidades de seguridad conocidas.
	 - Funciona comprobando las dependencias contra una base de datos de vulnerabilidades públicas y te informa sobre cualquier problema potencial.
- yarn audit: 
	- **`yarn audit`** es similar a `npm audit`, pero se utiliza cuando tu proyecto está gestionado con **Yarn** en lugar de npm.
	- Realiza un análisis similar de las dependencias de tu proyecto, pero lo hace con la base de datos de seguridad de Yarn.

### Ejemplo

# ¿Cómo evitarlo?

- Revisar si la librería o paquete esta en constante mantenimiento. no instalar cualquier librería.
	- Antes de integrar cualquier librería o paquete en tu proyecto, verifica si el mantenimiento de la librería está activo y si tiene una comunidad activa detrás. Esto incluye revisar el número de **commits recientes**, **issues** abiertas y la frecuencia con que se **actualizan** las versiones.
- Hacer revisiones constantes con el comando `npm audit` para el package.json
	- **`npm audit`** es una herramienta útil para realizar auditorías de seguridad en las dependencias de tu proyecto. Ejecutar este comando regularmente (al menos en cada ciclo de desarrollo importante) es una excelente práctica para detectar vulnerabilidades de seguridad conocidas en las bibliotecas de tu proyecto.
	- **`npm audit fix`** permite corregir automáticamente muchas de estas vulnerabilidades, lo cual facilita mantener las dependencias actualizadas.
- Instalar dependaBot en los repositorios github
	- **DependaBot** es una herramienta automatizada de GitHub que te ayuda a mantener las dependencias de tu proyecto actualizadas. Monitorea las versiones de las dependencias y crea **pull requests** automáticamente cuando una nueva versión segura de una librería esté disponible.
	- Configurar **DependaBot** en tus repositorios ayuda a asegurar que las actualizaciones de seguridad se apliquen rápidamente sin tener que hacerlo manualmente.
### Importancia de la modularidad y la separación de responsabilidades.

La **modularidad** y la **separación de responsabilidades** son principios clave en el desarrollo de software que mejoran la calidad y la mantenibilidad del código a largo plazo. A continuación, te explico por qué son tan importantes:

- **Facilita el Mantenimiento:**
    - Un sistema modular divide el código en **módulos independientes**, lo que facilita la localización y solución de problemas. Si algo falla en una parte específica del sistema, puedes trabajar en esa área sin afectar el resto de la aplicación.
    - Si un módulo necesita ser actualizado o reemplazado, puedes hacerlo sin necesidad de reescribir toda la aplicación.
    - 
- **Escalabilidad:**
    - A medida que una aplicación crece, los sistemas modulares permiten **escalar fácilmente** añadiendo nuevos módulos o características sin romper la estructura existente.
    - La separación de responsabilidades permite que los desarrolladores trabajen en diferentes partes del código simultáneamente sin interferir con el trabajo de otros.
    
- **Reusabilidad:**
    - Los módulos bien diseñados pueden ser **reutilizados** en otros proyectos o en diferentes partes de la misma aplicación, lo que ahorra tiempo y esfuerzo.
    - Al separar las responsabilidades, cada módulo se enfoca en una única tarea, lo que facilita la reutilización de código en distintos contextos.
    
- **Facilita las Pruebas:**
    - La modularidad hace que las **pruebas unitarias** sean más fáciles de implementar. Cada módulo puede probarse por separado de manera aislada.
    - La separación de responsabilidades permite realizar pruebas específicas para cada componente sin preocuparse por las interacciones con otros módulos.
    
- **Mejora la Colaboración:**
    - En equipos grandes, la modularidad facilita el trabajo colaborativo, ya que cada miembro del equipo puede ser responsable de desarrollar y mantener diferentes módulos sin depender directamente de los demás.
    - Esto también ayuda a reducir el **conflicto de código** cuando múltiples personas están trabajando en paralelo en distintas áreas del proyecto.
    
- **Reduce la Complejidad:**
    - Al dividir un sistema complejo en módulos con responsabilidades claras, puedes abordar problemas complejos de una manera más estructurada y controlada.
    - Cada módulo tiene una interfaz bien definida, lo que facilita entender su comportamiento sin tener que conocer todos los detalles internos.

### XSS atraves de v-HTML
Si un componente permite insertar HTML directamente (por ejemplo, mediante una propiedad `v-html` en Vue), esto puede dejar abierta la puerta a ataques como **Cross-Site Scripting (XSS)**, donde un atacante puede insertar JavaScript malicioso dentro de los datos que otros usuarios verán.

Esto deja abierto a que cualquier socio añada HTML con JS y pueda agregar mas funcionalidades, pero además permite que otros puedan agregar código y atacarnos. hay que ver si es útil desde la prevención del diseño o sanitizar aquella entrada.

>[!aviso]
>La representación dinámica de código HTML arbitrario en su sitio web puede ser muy peligrosa, ya que puede derivar fácilmente en [ataques XSS](https://en.wikipedia.org/wiki/Cross-site_scripting) . Utilícelo únicamente `v-html`en contenido confiable y **nunca** en contenido proporcionado por el usuario.

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
| Clickjacking  | X-Frame-Options: DENY, Content Security Policy (CSP).   |
| Inyección SQL | Uso de consultas preparadas, validación de entradas.    |
| Fuerza Bruta  | Implementar bloqueos tras múltiples intentos fallidos.  |
El encabezado **`X-Frame-Options`** es una medida de seguridad que evita que una página web sea embebida dentro de un **frame** o **iframe** en otro sitio web. Esto ayuda a prevenir ciertos tipos de ataques, como el **Clickjacking**.

El **Clickjacking** es un ataque donde un atacante engaña a un usuario para que haga clic en algo diferente a lo que piensa que está haciendo. Esto podría hacer que el usuario realice acciones no deseadas en otro sitio web. Usar `X-Frame-Options: DENY` ayuda a mitigar este tipo de ataque, asegurando que tu página no pueda ser incrustada en un frame de otro dominio, lo que hace que el ataque sea mucho más difícil de ejecutar.

**Content Security Policy (CSP)** es una medida de seguridad que ayuda a detectar y mitigar ciertos tipos de ataques, como **Cross-Site Scripting (XSS)** y **ataques de inyección de datos**. CSP permite a los desarrolladores especificar qué fuentes de contenido (scripts, imágenes, estilos, etc.) pueden ser cargadas en una página web.

CSP se implementa a través del encabezado HTTP `Content-Security-Policy`, y se puede personalizar para permitir solo ciertos recursos, restringir el uso de JavaScript no confiable o limitar las ubicaciones de donde se pueden cargar archivos.

### Balanceador de carga
**Definición:** Un **balanceador de carga** es un componente de infraestructura (hardware o software) cuyo objetivo principal es distribuir de manera equitativa las solicitudes o cargas de trabajo entre múltiples servidores o recursos en una red. El propósito de esto es mejorar el rendimiento, aumentar la disponibilidad, garantizar la confiabilidad y optimizar el uso de recursos.

# Desarrollo seguro paso a paso
**Validar entradas del usuario**
- Nunca confíes en el usuario.
- ¿Dónde Aplicarlo?
	- **Formularios web:** Siempre valida las entradas que el usuario proporciona en formularios, ya sea en el cliente (JavaScript) o en el servidor (backend).
	- **URLs y parámetros de consulta:** Cuando pases datos a través de URLs (como en parámetros de consulta), asegúrate de codificar los valores para evitar problemas de inyección de código.
	- **Base de datos:** Al recibir datos del usuario, valida que estos sean adecuados antes de insertarlos en la base de datos para prevenir inyecciones SQL.
	- **Archivos:** Si un usuario sube archivos, valida que el tipo y tamaño sean correctos para evitar el envío de archivos maliciosos.
- `encodeURIComponent` es una función de JavaScript que se utiliza para **codificar** un componente de una URI (Uniform Resource Identifier), como una cadena de consulta o un fragmento de URL, de forma que pueda ser transmitido de manera segura a través de la web.
	- **Propósito:** El propósito principal de `encodeURIComponent` es asegurarse de que los caracteres especiales, que podrían interferir con la estructura de una URL (como `&`, `=`, `?`, `#`, y otros), se codifiquen correctamente en su representación de URL. Esto es crucial cuando los datos que se están transmitiendo forman parte de una URL, como en parámetros de consulta, y queremos evitar problemas con la interpretación de esos caracteres.
	- **Cómo funciona:** La función convierte los caracteres no seguros en sus equivalentes en formato de **escape de URL** (por ejemplo, un espacio se convierte en `%20`, y un `&` en `%26`). Esto garantiza que los parámetros no interfieran con la estructura de la URL.
- Ejemplo:

```ts
// Evita inyección de codigo en URL
const userId = req.query.id;
const safeUserId = encodeURIComponent(userId)
```

**Protege datos sensibles**
- Encriptación y hashing con bcrypt.
	- **Encriptación:** La encriptación es el proceso de convertir datos legibles en un formato que solo pueda ser leído por aquellos que tengan una clave de desencriptación. La encriptación se usa cuando se necesita que los datos puedan ser restaurados a su formato original, como en el caso de archivos o mensajes.
	- **Hashing:** El hashing es el proceso de transformar una entrada (como una contraseña) en un valor de longitud fija que no se puede revertir para obtener el valor original. A diferencia de la encriptación, el hashing no tiene una clave de desencriptación, lo que hace que sea adecuado para almacenar contraseñas.

- ¿Dónde Aplicarlo?
	- **Contraseñas de usuario:** Nunca almacenes contraseñas como texto plano. Siempre hashea las contraseñas antes de almacenarlas.
	- **Tokens y claves secretas:** Usa encriptación para proteger tokens o claves secretas en tránsito y en reposo.
	- **Datos sensibles en bases de datos:** Si almacenas información sensible, como números de tarjetas de crédito, usa encriptación para proteger estos datos.
	
- Ejemplo:
```ts
// 
const bcrypt = require('bcrypt');
const hassPassword = await bcrypt.hash('MiContraseñaSegura', 10);
```

El `10` es el **número de rondas de salting** que `bcrypt` usa para generar el hash. Cuanto mayor es este número, más seguro será el hash, pero también tomará más tiempo para generarlo.

**Configuración de políticas de CORS (Evitar CSRF):**
- ¿Qué es CORS?
	- **CORS (Cross-Origin Resource Sharing)** es un mecanismo de seguridad implementado en los navegadores que restringe las solicitudes HTTP realizadas desde un dominio diferente al del servidor de origen. Su objetivo es prevenir ataques de tipo **Cross-Site Request Forgery (CSRF)** y asegurar que solo orígenes autorizados puedan acceder a los recursos de un servidor.
	- Cuando un cliente (como una aplicación en Angular, React o una API) intenta hacer una solicitud a un dominio distinto del que cargó originalmente la página web, el navegador verifica si el servidor permite dicha comunicación a través de los **headers de CORS**.
- ¿Dónde Aplicarlo?
	- CORS debe configurarse en el **servidor** para definir qué orígenes pueden acceder a los recursos y qué métodos están permitidos. Se debe aplicar en **APIs y servidores web** cuando:
		- La aplicación cliente (frontend) está en un dominio diferente al backend.  
		- Se manejan **peticiones AJAX o fetch** desde JavaScript.  
		- Se accede a una API REST desde una aplicación de terceros.
```ts
// Configuración de politicas de CORS (Evitar CSRF)
const cors = require('cors')
app.use(cors({ origin: 'https://tusitioseguro.com'}));
```

**Gestión de dependencias**
- ¿Dónde Aplicarlo?
	- Debe aplicarse en cualquier proyecto de desarrollo de software que dependa de bibliotecas externas.
	**Aplicaciones web y backend** (ASP.NET, Node.js, Python, Java, etc.).  
	**Aplicaciones frontend** (Angular, React, Vue, etc.).  
	**Bases de datos** (ORMs como Entity Framework, Sequelize, TypeORM).  
	**Automatización y scripts** (Python con `pip`, Bash con `brew`, etc.).  
	**DevOps y CI/CD** (Docker, Kubernetes, Terraform).
- Usar dependabot o npm audit fix
```bash
npm audit fix
```

# JWT (JSON Web Token)

**ACCES_TOKEN:**
Token de corta duración de autenticación de un inicio de sesión exitoso. Contiene al usuario y sus permisos, usando para acceder a recursos protegidos, validez corta para reducir el riesgo de acceso no autorizado.

**REFRESH_TOKEN:**
Token de mayor duración emitido durante la autenticación. Se utiliza para obtener un nuevo ACCESS_TOKEN sin volver a iniciar sesión. Esto representa una mejora a la seguridad al evitar que los usuarios ingresen repetidamente sus credenciales.

El refresh_token no es una capa de seguridad, es una capa de usabilidad, para que cuando el acces token se acabe, refresca el token sin volver a logearse.

Huella digital: permite guardar información extra para confirma que eres tú, con tu versión de tu navegador, tu computadora, tu versión de navegador, tu ip.

Se usan del lado del usuario


# Malas prácticas en el desarrollo de software 
(API_KEY’s en commits) .....


# Configuración de políticas de seguridad (CORS, IP’s, Roles, Permisos)

En el desarrollo de software, es fundamental establecer políticas de seguridad para proteger APIs y aplicaciones contra accesos no autorizados, ataques CSRF, y otros riesgos.

## **1. Configuración de CORS (Cross-Origin Resource Sharing)**

CORS controla qué orígenes pueden acceder a los recursos de un servidor.

🔴 **Problema:**  
Si CORS está mal configurado, cualquier sitio puede hacer solicitudes a tu API, exponiendo datos sensibles.

✅ **Solución:**

- Restringir orígenes específicos en el servidor.

## **2. Restricción de Acceso por IP (Whitelisting)**

Permitir solo ciertas IPs puede ayudar a limitar el acceso no autorizado.

✅ **Solución:**

- **Filtrar IPs en el middleware del servidor.**

## **3. Gestión de Roles y Permisos**

Los roles y permisos controlan qué acciones puede realizar cada usuario en la aplicación.

✅ **Solución:**

- Asignar **roles** como `admin`, `editor`, `user`.
- Controlar accesos en middleware según el rol.

## **4. Implementación de Seguridad con Headers HTTP**

Configurar los encabezados HTTP puede prevenir ataques comunes.

✅ **Solución:**

- Usar **helmet** para reforzar la seguridad en Express.js.

# Pruebas de seguridad durante el desarollo

**Automatización con herramientas:**
- **ESLint Plugin Security (análisis estático):** herramienta popular para análisis estático de código. Puedes integrar el plugin **eslint-plugin-security** para identificar vulnerabilidades comunes como inyecciones de código y prácticas inseguras en JavaScript.
- **OWASP ZAP (análisis dinámico):** una de las herramientas más completas para realizar **análisis dinámicos** de seguridad (DAST). Permite hacer pruebas automáticas de vulnerabilidades como **inyección SQL**, **XSS** y **CSRF**, entre otras.
- **Snvk (revisión de dependencias):** herramienta que ayuda a revisar las **dependencias de proyectos** para detectar vulnerabilidades conocidas. Es crucial mantener actualizadas las dependencias y asegurarse de que no estén utilizando versiones vulnerables de librerías.

## **1. Análisis Estático (Static Analysis)**

### **¿Qué es?**

El **análisis estático** implica revisar el **código fuente** o los **archivos del proyecto** sin ejecutarlo. En este enfoque, el análisis se realiza antes de que el software sea compilado o ejecutado, por lo que se enfoca en el código y la estructura del mismo.
### **¿Qué busca?**

- Detecta **vulnerabilidades de codificación**, como malas prácticas o patrones inseguros, antes de que el código se ejecute.
- Identifica posibles **errores de seguridad** en el código que podrían dar lugar a problemas más tarde.
- Es útil para revisar código de manera temprana durante el proceso de desarrollo.


## **2. Análisis Dinámico (Dynamic Analysis)**

### **¿Qué es?**

El **análisis dinámico** implica ejecutar el software en un entorno controlado (como un servidor o máquina de prueba) para observar cómo se comporta mientras está en funcionamiento. Este tipo de análisis se realiza **mientras el software está en ejecución**.
### **¿Qué busca?**

- Detecta **vulnerabilidades que solo aparecen durante la ejecución**, como **inyecciones SQL**, **Cross-Site Scripting (XSS)**, **Cross-Site Request Forgery (CSRF)**, entre otras.
- Puede identificar **errores de configuración**, problemas con la **autenticación** o **sesiones inseguras** que solo son evidentes cuando el software está interactuando con el entorno o el usuario.
- Es útil para probar las interacciones del software con otros sistemas y servicios.

**Pruebas unitarias:**
- Asegúrate de probar validaciones de seguridad.
