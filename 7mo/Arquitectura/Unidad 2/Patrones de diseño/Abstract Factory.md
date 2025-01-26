## Definición

**Abstract Factory** es un patrón de diseño creacional que permite crear **familias de objetos relacionados o dependientes** sin especificar sus clases concretas. Esto significa que la clase principal (o cliente) puede usar diferentes "fábricas abstractas" para crear un conjunto de objetos que comparten un tema común (por ejemplo, helados de diferentes sabores o estilos).

Este patrón se usa cuando una aplicación debe crear grupos de objetos relacionados, y se quiere cambiar el grupo completo de productos creado sin modificar el código cliente.

## En que se basa
Abstract Factory se basa en una **interfaz de fábrica abstracta** que define métodos para crear cada tipo de objeto en la familia. Cada "fábrica concreta" (implementación de la fábrica abstracta) representa una variante específica de los productos y proporciona una implementación concreta de cómo crear cada uno.

Por ejemplo, podríamos tener una fábrica abstracta `HeladeriaFactory` que declare métodos para crear `HeladoDeChocolate`, `HeladoDeVainilla`, etc. Luego, dos fábricas concretas —una para helados veganos y otra para helados tradicionales de leche— implementarían esta interfaz, y cada una retornaría versiones específicas (veganas o de leche) de cada helado.

## Esquema
- **AbstractFactory**: Interfaz para crear diferentes tipos de objetos relacionados.
- **ConcreteFactory**: Implementa la interfaz `AbstractFactory` y crea una variante específica de cada producto.
- **AbstractProduct**: Interfaz para un tipo específico de producto dentro de la familia.
- **ConcreteProduct**: Implementa `AbstractProduct` y define un producto específico de una variante.
- **Cliente (Client)**: Usa la fábrica abstracta para obtener los productos necesarios sin saber cuáles son sus implementaciones concretas.

## Estructura
![[Pasted image 20241105105320.png]]

## Ejemplos

```java
// Abstract Factory para notificaciones
interface NotificationFactory {
    Notification createTextNotification();
    Notification createImageNotification();
}

// Concrete Factory para Email
class EmailNotificationFactory implements NotificationFactory {
    public Notification createTextNotification() {
        return new EmailTextNotification();
    }

    public Notification createImageNotification() {
        return new EmailImageNotification();
    }
}

// Concrete Factory para SMS
class SMSNotificationFactory implements NotificationFactory {
    public Notification createTextNotification() {
        return new SMSTextNotification();
    }

    public Notification createImageNotification() {
        return new SMSImageNotification();
    }
}

// Concrete Factory para Push Notifications
class PushNotificationFactory implements NotificationFactory {
    public Notification createTextNotification() {
        return new PushTextNotification();
    }

    public Notification createImageNotification() {
        return new PushImageNotification();
    }
}

// Abstract Product para Notificaciones
interface Notification {
    void send(String message);
}

// Implementación de Notificación de Texto en Email
class EmailTextNotification implements Notification {
    public void send(String message) {
        System.out.println("Enviando Email de Texto: " + message);
    }
}

// Implementación de Notificación de Imagen en Email
class EmailImageNotification implements Notification {
    public void send(String message) {
        System.out.println("Enviando Email con Imagen: " + message);
    }
}

// Implementación de Notificación de Texto en SMS
class SMSTextNotification implements Notification {
    public void send(String message) {
        System.out.println("Enviando SMS de Texto: " + message);
    }
}

// Implementación de Notificación de Imagen en SMS
class SMSImageNotification implements Notification {
    public void send(String message) {
        System.out.println("Enviando SMS con Imagen: " + message);
    }
}

// Implementación de Notificación de Texto en Push
class PushTextNotification implements Notification {
    public void send(String message) {
        System.out.println("Enviando Push de Texto: " + message);
    }
}

// Implementación de Notificación de Imagen en Push
class PushImageNotification implements Notification {
    public void send(String message) {
        System.out.println("Enviando Push con Imagen: " + message);
    }

// Cliente que usa la Abstract Factory para enviar notificaciones
class NotificationService {
    private Notification textNotification;
    private Notification imageNotification;

    public NotificationService(NotificationFactory factory) {
        this.textNotification = factory.createTextNotification();
        this.imageNotification = factory.createImageNotification();
    }

    public void sendTextNotification(String message) {
        textNotification.send(message);
    }

    public void sendImageNotification(String message) {
        imageNotification.send(message);
    }
}

```
