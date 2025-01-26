## Definición
El patrón **Factory Method** es un patrón de diseño creacional que proporciona una interfaz para crear objetos en una superclase, permitiendo que las subclases alteren el tipo de objetos que se crearán. Esto permite que las subclases decidan qué instancias deben crearse sin modificar el código cliente, facilitando la extensión y personalización de clases en un programa.

En otras palabras, en lugar de instanciar objetos de una clase directamente, el patrón delega la creación a un método (o fábrica), que será implementado por cada subclase. Así, cada subclase puede producir un tipo específico de objeto cuando se llama al método.

## Esquema

- **Producto**: Define la interfaz común para los objetos que serán creados.
- **Producto Concreto**: Implementa la interfaz del producto, es decir, cada clase concreta representa un tipo de producto.
- **Creador**: Declara el método `factoryMethod` que devuelve objetos del tipo `Producto`. Este método es abstracto en el creador, por lo que las subclases deben implementarlo.
- **Creador Concreto**: Extiende al Creador y sobrescribe el método `factoryMethod` para retornar instancias de `ProductoConcreto`.
## Estructura

![[Pasted image 20241105094219.png]]
## En que se basa

- Separación de responsabilidades
- Encapsulación de la creación
- Delega la creación de objetos a subclases concretas

## Ejemplos
```java
interface Notificacion {
    void enviar(String mensaje);
}

class NotificacionEmail implements Notificacion {
    public void enviar(String mensaje) {
        System.out.println("Enviando email: " + mensaje);
    }
}

class NotificacionSMS implements Notificacion {
    public void enviar(String mensaje) {
        System.out.println("Enviando SMS: " + mensaje);
    }
}

abstract class NotificacionFactory {
    public abstract Notificacion crearNotificacion();
}

class EmailNotificacionFactory extends NotificacionFactory {
    public Notificacion crearNotificacion() {
        return new NotificacionEmail();
    }
}

class SMSNotificacionFactory extends NotificacionFactory {
    public Notificacion crearNotificacion() {
        return new NotificacionSMS();
    }
}

```

>[!Factory Method vs Factory Abstract]
>**Factory Method**
>La clase principal no se entera de que saber fue el helado
>
>**Factory Abstract**
>La clase principal si se entera de que saber fue el helado y puede ser alterada


- **Factory Method**: La clase principal no sabe o no le importa qué tipo específico recibe. Solo necesita un único tipo de producto y llama a un método para obtenerlo.
- **Abstract Factory**: La clase principal sabe que puede obtener distintos productos de una familia, y puede elegir cuál usar de entre varios métodos para cada tipo de producto dentro de la familia.

### 1. Factory Method

En el **Factory Method**, el cliente **conoce el tipo específico de producto** que necesita y **llama a un método de fábrica que genera ese producto específico**. Aquí:

- **La fábrica produce un solo tipo de producto** (o una familia muy estrecha de productos).
- **El cliente conoce qué producto espera** y solo llama al método para obtenerlo.

Por ejemplo, si el cliente necesita crear solo "Documentos", podría llamar a `createDocument()` en una fábrica de documentos, y esta devolvería un objeto específico como `WordDocument` o `PDFDocument` según la fábrica concreta que esté usando.

### 2. Abstract Factory

En el **Abstract Factory**, el cliente **trabaja con una familia de productos** relacionados, pero **sin conocer los detalles de cada uno**. En lugar de un único método para crear un producto, la fábrica abstracta tiene **múltiples métodos para crear cada uno de los productos en esa familia**.

- **La fábrica puede crear diferentes tipos de productos** (por ejemplo, `createTextNotification()` y `createImageNotification()`), todos relacionados, pero sin que el cliente sepa qué implementaciones concretas está usando.
- **El cliente no necesita conocer los productos específicos**, solo trabaja con interfaces o abstracciones.