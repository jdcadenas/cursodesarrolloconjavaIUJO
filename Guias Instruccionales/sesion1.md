

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
### **Sesión 1: Fundamentos de Java y Estructuras Básicas**

#### **Contenidos de esta sesión:**
1. Origen y filosofía de Java.
2. La plataforma Java: JDK, JRE y la Máquina Virtual (JVM).
3. Instalación y configuración del entorno (VS Code + JDK).
4. Sintaxis y estructura de un programa (Clase y método main).
5. Variables, constantes y tipos de datos primitivos.
6. Operadores aritméticos básicos.

---

#### **1.1 ¿Por qué aprender Java?**
Java es una plataforma tecnológica fundamental que impulsa más de **3,000 millones de dispositivos móviles Android** y sistemas críticos en empresas como **Netflix, Spotify, Amazon y la NASA**. Su principal ventaja es la filosofía **"Write Once, Run Anywhere"** (Escríbelo una vez, ejecútalo en cualquier lugar), lo que garantiza que un programa escrito en Windows funcione idénticamente en Linux o Mac.

#### **1.2 La Máquina Virtual de Java (JVM) y el Bytecode**
A diferencia de otros lenguajes, Java no se traduce directamente a lenguaje de máquina, sino a un código intermedio llamado **Bytecode** (archivos .class).
*   **Bytecode:** Código universal generado tras la compilación.
*   **JVM:** Es el motor encargado de traducir ese bytecode al lenguaje específico de cada sistema operativo, permitiendo la portabilidad total.

#### **1.3 Instalación y Preparación**
Para programar necesitamos:
1.  **JDK (Java Development Kit):** El kit de herramientas que contiene el compilador.
2.  **Visual Studio Code:** Con el plugin *"Extension Pack for Java"* para escribir el código de forma eficiente.

#### **1.4 Estructura básica de un programa**
En Java, **todo el código debe vivir dentro de una Clase**. El punto de entrada es siempre el método `main`.
*   **Sentencias:** Deben terminar siempre con **punto y coma**.
*   **Bloques:** Se delimitan con **llaves { }**.

#### **1.5 Variables y Tipos de Datos**
Una variable es un espacio de memoria etiquetado para guardar datos.
**Tipos Primitivos Comunes:**
*   `int`: Números enteros (ej: `edad = 25;`).
*   `double`: Números reales con decimales (ej: `precio = 10.50;`).
*   `boolean`: Valores lógicos (`true` o `false`).
*   `char`: Un solo carácter en comillas simples (ej: `inicial = 'J';`).

**Tipo Objeto Especial:**
*   `String`: Se usa para cadenas de texto entre comillas dobles (ej: `"Hola IUJO"`).

---

#### **1.6 Operadores Aritméticos**
Java utiliza símbolos estándar para realizar cálculos matemáticos:
*   `+` Suma y concatenación de textos.
*   `-` Resta.
*   `*` Multiplicación.
*   `/` División (si los operandos son `int`, el resultado es entero).
*   `%` **Módulo:** Calcula el resto de una división entera.

---

### **Ejercicios Prácticos de la Sesión 1 **

A continuación, se presentan los códigos íntegros para que los estudiantes puedan copiarlos, probarlos y analizarlos.

#### **Ejercicio 1.1: Mi primer "Hola Mundo"**
**Objetivo:** Validar que el entorno está correctamente configurado y entender la estructura `main`.

```java
// Nombre del archivo: HolaMundo.java
public class HolaMundo {
    public static void main(String[] args) {
        // Impresión en consola
        System.out.println("¡Hola, bienvenido al curso de Java en el IUJO!");
        System.out.println("Nombre del estudiante: [Tu Nombre Aquí]");
        System.out.println("Expectativa: Aprender a desarrollar aplicaciones robustas.");
    }
}
```

#### **Ejercicio 1.2: Cálculo del Área de un Círculo**
**Objetivo:** Aplicar el uso de variables tipo `double` y operadores aritméticos.

```java
// Nombre del archivo: AreaCirculo.java
public class AreaCirculo {
    public static void main(String[] args) {
        // Declaración de variables
        double radio = 5.0;
        double pi = 3.14159;
        
        // Operación aritmética: Area = PI * r * r
        double area = pi * radio * radio;
        
        // Concatenación de resultados
        System.out.println("El radio del círculo es: " + radio);
        System.out.println("El área calculada es: " + area);
    }
}
```

#### **Ejercicio 1.3: Conversor de Temperatura (Celsius a Fahrenheit)**
**Objetivo:** Manejar fórmulas matemáticas y asegurar precisión con decimales.

```java
// Nombre del archivo: ConversorTemperatura.java
public class ConversorTemperatura {
    public static void main(String[] args) {
        // Variable de entrada
        double celsius = 25.0;
        
        // Fórmula: F = (C * 9/5) + 32
        double fahrenheit = (celsius * 9 / 5) + 32;
        
        System.out.println("Temperatura en Celsius: " + celsius + "°C");
        System.out.println("Equivalente en Fahrenheit: " + fahrenheit + "°F");
    }
}
```

---

#### **Resumen de Buenas Prácticas (Sesión 1)**
1.  **Nomenclatura CamelCase:** Las clases inician con Mayúscula (`HolaMundo`). Las variables con minúscula (`miEdad`).
2.  **Identación:** Mantener el código alineado dentro de las llaves para que sea legible.
3.  **Comentarios:** Usar `//` para explicar líneas lógicas complejas.
4.  **Consistencia:** El nombre del archivo debe ser **exactamente igual** al nombre de la clase pública.

***
