## Definición

Utilizado para crear objetos complejos de manera controlada. En lugar de crear el objeto de una sola vez, el patrón **Builder** permite construirlo paso a paso. (No es recomendable heredar, puesto que estarías creando subclases que posiblemente no uses todos sus propiedades posteriormente).

El patrón **Builder** separa la construcción de un objeto complejo de su representación final. Esto permite crear distintos tipos y configuraciones de objetos usando el mismo proceso de construcción.

Es especialmente útil cuando el objeto:

- Tiene muchas opciones o configuraciones que pueden no ser necesarias en cada instancia.
- Se construye de manera compleja, como cuando necesita un orden específico para crearse correctamente.
## Esquema y estructura

Builder crea los componentes y solo los llama cuando los necesita. En lugar de hacer una clase casa y hacer subclases: casa con piscina. Porque no siempre se va a utilizar.

Un objeto se compone de 5 partes, las cuales no se pueden repetir.

1. **Producto (Product)**: El objeto complejo que se crea a partir de los pasos realizados por el Builder. Es el resultado final.
2. **Builder**: Es una interfaz o clase abstracta que define los pasos necesarios para crear el objeto.
3. **Specific Builder**: Crea las partes del objeto complejo. El specific builder se le dice: CasaDeLujo. Implementa la interfaz `Builder` y proporciona una implementación específica para cada paso de construcción.
4. **Director**: Este actor construye el objeto complejo con la interfaz del constructor. Acciona los parámetros. Esta clase (opcional) controla el proceso de construcción. Llama a los métodos del Builder en un orden específico para crear el objeto. El cliente puede usarlo para construir el objeto de una manera particular sin preocuparse de los detalles.
5. **Cliente**: El cliente que utiliza el director para obtener el producto final.


![[Pasted image 20241105092819.png]]
## Se basa

- Separación de responsabilidades - Separa el código.
- Construcción paso a paso - Construir de manera incremental.
- Flexibilidad
- Encapsulación

## Ejemplo


```C#
// Producto
public class Casa
{
    public string Tamaño { get; private set; }
    public int NúmeroDeHabitaciones { get; private set; }
    public bool TienePiscina { get; private set; } = false; // Predeterminado a false
    public bool TieneGaraje { get; private set; } = false; // Predeterminado a false
    public string Estilo { get; private set; }

    public Casa(string tamaño, int númeroDeHabitaciones, string estilo)
    {
        Tamaño = tamaño;
        NúmeroDeHabitaciones = númeroDeHabitaciones;
        Estilo = estilo;
    }

    public void SetTienePiscina(bool tienePiscina)
    {
        TienePiscina = tienePiscina;
    }

    public void SetTieneGaraje(bool tieneGaraje)
    {
        TieneGaraje = tieneGaraje;
    }

    public override string ToString()
    {
        return $"Casa: {Tamaño}, Habitaciones: {NúmeroDeHabitaciones}, Estilo: {Estilo}, Tiene Piscina: {TienePiscina}, Tiene Garaje: {TieneGaraje}";
    }
}

// Builder
public interface ICasaBuilder
{
    void SetTamaño(string tamaño);
    void SetNúmeroDeHabitaciones(int númeroDeHabitaciones);
    void SetEstilo(string estilo);
    void SetTienePiscina(bool tienePiscina);
    void SetTieneGaraje(bool tieneGaraje);
    Casa Build();
}

// Specific Builder
public class CasaBuilder : ICasaBuilder
{
    private string _tamaño;
    private int _númeroDeHabitaciones;
    private string _estilo;
    private bool _tienePiscina = false; // Predeterminado a false
    private bool _tieneGaraje = false; // Predeterminado a false

    public void SetTamaño(string tamaño)
    {
        _tamaño = tamaño;
    }

    public void SetNúmeroDeHabitaciones(int númeroDeHabitaciones)
    {
        _númeroDeHabitaciones = númeroDeHabitaciones;
    }

    public void SetEstilo(string estilo)
    {
        _estilo = estilo;
    }

    public void SetTienePiscina(bool tienePiscina)
    {
        _tienePiscina = tienePiscina;
    }

    public void SetTieneGaraje(bool tieneGaraje)
    {
        _tieneGaraje = tieneGaraje;
    }

    public Casa Build()
    {
        Casa casa = new Casa(_tamaño, _númeroDeHabitaciones, _estilo);
        casa.SetTienePiscina(_tienePiscina);
        casa.SetTieneGaraje(_tieneGaraje);
        return casa;
    }
}


// Director
public class CasaDirector
{
    private readonly ICasaBuilder _casaBuilder;

    public CasaDirector(ICasaBuilder casaBuilder)
    {
        _casaBuilder = casaBuilder;
    }

    public void ConstruirCasaDeLujo()
    {
        _casaBuilder.SetTamaño("Grande");
        _casaBuilder.SetNúmeroDeHabitaciones(5);
        _casaBuilder.SetEstilo("Lujo");
        _casaBuilder.SetTienePiscina(true);
        _casaBuilder.SetTieneGaraje(true);
    }

    public void ConstruirCasaSimple()
    {
        _casaBuilder.SetTamaño("Pequeña");
        _casaBuilder.SetNúmeroDeHabitaciones(2);
        _casaBuilder.SetEstilo("Simple");
        // No configuramos piscina ni garaje
    }
}

// Cliente
public class Program
{
    public static void Main(string[] args)
    {
        ICasaBuilder builder = new CasaBuilder();
        CasaDirector director = new CasaDirector(builder);

        // Construir una casa de lujo
        director.ConstruirCasaDeLujo();
        Casa casaDeLujo = builder.Build();
        Console.WriteLine(casaDeLujo);

        // Construir una casa simple
        builder = new CasaBuilder(); // Crear un nuevo builder para una nueva casa
        director = new CasaDirector(builder);
        director.ConstruirCasaSimple();
        Casa casaSimple = builder.Build();
        Console.WriteLine(casaSimple);
    }
}

```


