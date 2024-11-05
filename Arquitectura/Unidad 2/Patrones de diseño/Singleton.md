Instancia - Objeto

Clase con única instancia
Cliente hace una petición. retorna una única instancia.


SOLID

## ¿En qué se basa?

- Restricción de instancias - Solo puede crear una única instancia 
- Acceso controlado - Método estático o global.
- Control del ciclo de vida - La única instancia se crea en el momento que es necesario
- Uso global - Como es global, las otras clases pueden usarla sin crear múltiples instancias innecesarias.

## Definición
El patrón Singleton es un patrón de diseño que asegura que una clase tenga una única instancia y proporciona un punto de acceso global a esa instancia. Esto es útil en situaciones donde se necesita controlar el acceso a un recurso compartido, como una conexión a base de datos o una configuración de aplicación.

## Estructura
![[Pasted image 20241016220050.png]]
- **Singleton**: La clase que contiene la instancia única.
- **instancia**: Variable privada que almacena la única instancia.
- **getInstance()**: Método estático que devuelve la instancia. Si la instancia no existe, la crea.
- **metodoEjemplo()**: Un método de la clase que puede ser utilizado por otras clases.

>[!IMPORTANT]
>Solo aplicarlo cuando se requiere

## Ejemplo:

```TS
class Singleton {
    private static instancia: Singleton;

    // Constructor privado para evitar instanciación externa
    private constructor() { }

    // Método para obtener la única instancia
    public static getInstance(): Singleton {
        if (!this.instancia) {
            this.instancia = new Singleton();
        }
        return this.instancia;
    }

    // Un método de ejemplo
    public metodoEjemplo(): void {
        console.log("Método del Singleton ejecutado");
    }
}

// Uso del Singleton
const instancia1 = Singleton.getInstance();
const instancia2 = Singleton.getInstance();

instancia1.metodoEjemplo(); // Imprime: Método del Singleton ejecutado

console.log(instancia1 === instancia2); // Imprime: true (ambas variables apuntan a la misma instancia)

```

### En este ejemplo:

- El constructor de la clase `Singleton` es privado, lo que impide que otras clases puedan crear instancias de ella directamente.
- El método estático `getInstance()` proporciona acceso a la instancia única, creando una nueva solo si no existe.
- Las variables `instancia1` y `instancia2` apuntan a la misma instancia del `Singleton`, lo que confirma que solo hay una instancia activa en la aplicación.