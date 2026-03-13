<div style="display: flex; justify-content: space-between; align-items: center;">
  <div><br>
    <h2>Guía Instruccional</h2><br>
  </div>
  <div>
    <img src="LOGO_UPP_IUJO.png" alt="Logo IUJO" width="150">
  </div>
</div>

### **Introducción al Desarrollo con Java y POO**

**Unidad Pedagógica Productiva "Jesús Obrero"** <br> 
**Facilitador:** José Daniel Cadenas Lucero <br>
**Fechas:** [Sábados de 12pm a 4pm] - 2026 <br>

### **Sesión 2: Estructuras de Control y Modularidad**

#### **Contenidos de esta sesión:**
1. Lógica de selección: `if`, `else if`, `else` y el operador ternario.
2. Selección múltiple: Estructura `switch` y el uso de `break`.
3. Interactividad: Uso de la clase `Scanner` para entrada de datos.
4. Bucles e iteración: `while`, `do-while` y `for`.
5. Modularidad: Creación de métodos, parámetros y valores de retorno.

---

#### **2.1 Estructuras de Selección (Toma de Decisiones)**
En Java, las estructuras de control permiten romper la ejecución secuencial para tomar rutas lógicas basadas en condiciones booleanas (`true` o `false`).
*   **if-else:** Es el bloque fundamental. Si la condición es verdadera, ejecuta un código; de lo contrario, salta al bloque `else`.
*   **Operador Ternario:** Una forma compacta de escribir un `if-else` simple: `(condición) ? valor_si_cierto : valor_si_falso;`.

**Ejemplo de Selección Múltiple (`if-else-if`):**
```java
int calificacion = 85;
if (calificacion >= 90) {
    System.out.println("Excelente");
} else if (calificacion >= 75) {
    System.out.println("Bueno"); // Se ejecuta este bloque
} else {
    System.out.println("Necesita mejorar");
}
```

---

#### **2.2 Estructura switch: Selección por Valor**
Se utiliza cuando tenemos una sola variable que comparar contra múltiples valores constantes. Es vital usar la sentencia **break** para evitar el efecto de "caída" (*fall-through*), donde se ejecutarían todos los casos siguientes.

#### **2.3 Interactividad con Scanner**
Para que nuestros programas sean prácticos, deben recibir datos del usuario. Usamos la clase `java.util.Scanner`:
1.  **Importar:** `import java.util.Scanner;`.
2.  **Instanciar:** `Scanner teclado = new Scanner(System.in);`.
3.  **Leer:** `.nextInt()` para enteros, `.nextDouble()` para decimales o `.nextLine()` para texto.

#### **2.4 Estructuras de Repetición (Bucles)**
Permiten automatizar tareas repetitivas sin duplicar líneas de código:

| Estructura | Uso Ideal | Características |
| :--- | :--- | :--- |
| **`while`** | Cuando no sabemos cuántas veces repetiremos algo. | Comprueba la condición **antes** de entrar al bucle. |
| **`do-while`** | Cuando el código debe ejecutarse **al menos una vez**. | Comprueba la condición **al final**. |
| **`for`** | Cuando conocemos el número exacto de iteraciones. | Incluye inicialización, condición y actualización en una línea. |
| **`for-each`** | Para recorrer arreglos o colecciones. | No usa contadores, accede directamente al elemento. |

**Código de Ejemplo (Bucle con Centinela):**
```java
Scanner sc = new Scanner(System.in);
int numero;
do {
    System.out.print("Introduce un número (negativo para salir): ");
    numero = sc.nextInt();
} while (numero >= 0); // Se repite hasta que el usuario sea negativo.
```

---

#### **2.5 Modularidad: Métodos (Funciones)**
Un método es un bloque de código que realiza una tarea específica y puede ser reutilizado. Se compone de:
*   **Firma del Método:** Se compone de un modificador (ej. `public static`), un tipo de retorno (`void` si no devuelve nada, o un tipo como `int`), el nombre y los parámetros.
*   **Parámetros vs. Argumentos:** Los parámetros son las variables definidas en la cabecera del método; los argumentos son los valores reales que le enviamos al llamarlo.
*   **Retorno (`return`):** Envía un resultado de vuelta al lugar donde se llamó la función y finaliza su ejecución.

**Ejemplo de Método con Parámetros y Retorno:**
```java
// Definición del método
public static double calcularIVA(double precio) {
    return precio * 0.16; // Devuelve el cálculo
}

// Invocación en el main
double impuesto = calcularIVA(100.0);
System.out.println("El IVA es: " + impuesto);
```

---

### **Ejercicios Prácticos de la Sesión 2 **

#### **Ejercicio 2.1: Menú de Cajero Automático (switch)**
**Objetivo:** Implementar una interfaz de menú funcional usando `switch` y `Scanner`.

```java
import java.util.Scanner;

public class MenuCajero {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        System.out.println("--- BIENVENIDO AL CAJERO IUJO ---");
        System.out.println("1. Consultar Saldo");
        System.out.println("2. Retirar Efectivo");
        System.out.println("3. Salir");
        System.out.print("Seleccione una opción: ");
        
        int opcion = teclado.nextInt();
        
        switch (opcion) {
            case 1:
                System.out.println("Su saldo actual es de B/. 1,550.00");
                break;
            case 2:
                System.out.println("Procesando retiro...");
                break;
            case 3:
                System.out.println("Gracias por usar nuestros servicios.");
                break;
            default:
                System.out.println("Opción no válida.");
        }
    }
}
```

#### **Ejercicio 2.2: Validador de Notas (Integración if-else)**
**Objetivo:** Calcular promedios y validar estados académicos con lógica condicional.

```java
import java.util.Scanner;

public class ValidadorNotas {
    public static void main(String[] args) {
        Scanner entrada = new Scanner(System.in);
        
        System.out.print("Ingrese Nota 1: ");
        double n1 = entrada.nextDouble();
        System.out.print("Ingrese Nota 2: ");
        double n2 = entrada.nextDouble();
        System.out.print("Ingrese Nota 3: ");
        double n3 = entrada.nextDouble();
        
        double promedio = (n1 + n2 + n3) / 3;
        System.out.println("Promedio final: " + promedio);
        
        if (promedio >= 14) {
            System.out.println("Estado: APROBADO");
        } else {
            System.out.println("Estado: REPROBADO");
        }
    }
}
```

#### **Ejercicio 2.3: Generador de Tablas (for)**
**Objetivo:** Utilizar el bucle `for` para procesar secuencias numéricas.

```java
import java.util.Scanner;

public class TablaMultiplicar {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("¿Qué tabla desea ver?: ");
        int tabla = sc.nextInt();
        
        System.out.println("Tabla del " + tabla + ":");
        for (int i = 1; i <= 10; i++) {
            System.out.println(tabla + " x " + i + " = " + (tabla * i));
        }
    }
}
```

#### **Ejercicio 2.4: Calculadora Modular (Métodos)**
**Objetivo:** Separar la lógica en métodos independientes para promover la reutilización.

```java
public class CalculadoraModular {
    public static void main(String[] args) {
        double a = 10.5, b = 5.0;
        
        // Llamada a los métodos
        System.out.println("Suma: " + sumar(a, b));
        System.out.println("Resta: " + restar(a, b));
        System.out.println("Multiplicación: " + multiplicar(a, b));
    }
    
    // Definición de métodos
    public static double sumar(double n1, double n2) {
        return n1 + n2;
    }
    
    public static double restar(double n1, double n2) {
        return n1 - n2;
    }
    
    public static double multiplicar(double n1, double n2) {
        return n1 * n2;
    }
}
```

---

#### **Resumen de Buenas Prácticas Profesionales (Sesión 2)**
1.  **Nomenclatura de Métodos:** Deben iniciar con un verbo en minúscula (ej. `calcularPromedio`, `enviarCorreo`).
2.  **Seguridad en Bucles:** En un ciclo `while`, asegúrate siempre de que la variable de condición se actualice para evitar **bucles infinitos**.
3.  **Uso de Llaves:** Aunque Java permite omitir llaves en `if` de una sola línea, se recomienda usarlas siempre para mejorar la legibilidad y evitar errores futuros.
4.  **Validación de Entradas:** Siempre verifica que el usuario ingrese datos lógicos antes de procesar cálculos.

***
