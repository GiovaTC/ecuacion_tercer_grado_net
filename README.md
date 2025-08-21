# Programa en C# para resolver ecuaciones cúbicas

Este programa de consola en C# resuelve una ecuación de tercer grado de la forma:

ax³ + bx² + cx + d = 0

Utiliza el método de Cardano para calcular raíces reales y muestra los resultados por consola.

## Código

```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Ecuación cúbica: ax^3 + bx^2 + cx + d = 0");
        
        Console.Write("Ingresa el valor de a: ");
        double a = double.Parse(Console.ReadLine());

        Console.Write("Ingresa el valor de b: ");
        double b = double.Parse(Console.ReadLine());

        Console.Write("Ingresa el valor de c: ");
        double c = double.Parse(Console.ReadLine());

        Console.Write("Ingresa el valor de d: ");
        double d = double.Parse(Console.ReadLine());

        if (a == 0)
        {
            Console.WriteLine("No es una ecuación cúbica. El coeficiente 'a' no puede ser 0.");
            return;
        }

        double p = (3 * a * c - b * b) / (3 * a * a);
        double q = (2 * b * b * b - 9 * a * b * c + 27 * a * a * d) / (27 * a * a * a);

        double discriminante = (q * q / 4) + (p * p * p / 27);

        Console.WriteLine($"\nDiscriminante: {discriminante}");

        double shift = b / (3 * a);

        if (discriminante > 0)
        {
            Console.WriteLine("Una raíz real y dos complejas.");

            double sqrtDiscriminant = Math.Sqrt(discriminante);
            double u = Math.Cbrt(-q / 2 + sqrtDiscriminant);
            double v = Math.Cbrt(-q / 2 - sqrtDiscriminant);

            double x1 = u + v - shift;

            Console.WriteLine($"Raíz real: x = {x1}");
        }
        else if (discriminante == 0)
        {
            Console.WriteLine("Todas las raíces reales. Al menos dos son iguales.");

            double u = Math.Cbrt(-q / 2);
            double x1 = 2 * u - shift;
            double x2 = -u - shift;

            Console.WriteLine($"x1 = {x1}");
            Console.WriteLine($"x2 = x3 = {x2}");
        }
        else
        {
            Console.WriteLine("Tres raíces reales distintas.");

            double r = Math.Sqrt(-p * p * p / 27);
            double phi = Math.Acos(-q / (2 * Math.Sqrt(-p * p * p / 27)));

            double m = 2 * Math.Sqrt(-p / 3);

            double x1 = m * Math.Cos(phi / 3) - shift;
            double x2 = m * Math.Cos((phi + 2 * Math.PI) / 3) - shift;
            double x3 = m * Math.Cos((phi + 4 * Math.PI) / 3) - shift;

            Console.WriteLine($"x1 = {x1}");
            Console.WriteLine($"x2 = {x2}");
            Console.WriteLine($"x3 = {x3}");
        }

        Console.WriteLine("\nPresiona una tecla para salir...");
        Console.ReadKey();
    }
}
Ejemplo
Para la ecuación:

x³ - 6x² + 11x - 6 = 0
Ingresa:
a = 1
b = -6
c = 11
d = -6
Resultado esperado:

x1 = 1
x2 = 2
x3 = 3
Requisitos
Visual Studio 2022

.NET 6.0 o superior

Cómo usarlo
Crear un proyecto de consola en Visual Studio.

Pegar el código anterior en Program.cs.

Ejecutar el programa (Ctrl + F5).

