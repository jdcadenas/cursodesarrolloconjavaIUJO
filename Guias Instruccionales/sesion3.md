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
**Fechas:** Sábados de 12pm a 4pm - 2026 <br>

### **Sesión 3: Fundamentos de Programación Orientada a Objetos (POO)**

#### **Contenidos de esta sesión:**
1. Concepto de Clase (molde) y Objeto (instancia).
2. Atributos (estado) y Métodos (comportamiento).
3. Constructores y el uso de la palabra reservada `this`.
4. Encapsulamiento: Modificadores de acceso (`private` vs. `public`).
5. Métodos Accesores: Getters y Setters.
6. Gestión de memoria: Referencias y el *Garbage Collector*.

---

#### **3.1 El Concepto de Clase y Objeto**
La POO no se basa en acciones aisladas, sino en los elementos de un sistema y cómo interactúan. 
*   **Clase:** Es el "plano de construcción" (*blueprint*) o molde que describe cómo será un conjunto de objetos.
*   **Objeto:** Es la **instancia física** en memoria creada a partir de ese plano. 
*   **Analogía:** Un plano arquitectónico es la **clase**; la casa real donde puedes vivir es el **objeto**.

La programación orientada a objetos no se basa en acciones secuenciales, sino en los elementos de un sistema, sus atributos y cómo interactúan entre ellos. En Java, la unidad fundamental de este paradigma es la **Clase**.

Imagina un `Carro`. Sus atributos son el color y el modelo; sus acciones (métodos) son acelerar y frenar.
*   **Analogía Técnica:** Así como se pueden construir muchas casas a partir de un solo plano, se pueden crear múltiples objetos a partir de una única clase. No se puede "cocinar" en la cocina de un plano, pero sí en la cocina de una casa real (el objeto).

**Ejemplo de Modelado Base: La Clase Círculo**
```java
public class Circulo {
    // Atributos: Definen el estado del objeto
    int x;      // Coordenada horizontal
    int y;      // Coordenada vertical
    int radio;  // Dimensión del círculo
}
```
Para usar esta clase, se debe declarar una variable y asignar un nuevo objeto mediante el operador `new`, el cual reserva espacio en memoria.
`Circulo miCirculo = new Circulo();`.

---

#### **3.2 Atributos y Métodos**
*   **Atributos:** Almacenan la información o el "estado" del objeto (ej. color, modelo, precio). Pueden ser tipos primitivos (`int`, `double`) o referencias a otros objetos.

**Práctica de Atributos: Clase Vehículo**
Para un sistema de alquiler, un vehículo requiere identificar su matrícula, marca, modelo, tarifa y disponibilidad.
```java
public class Vehiculo {
    String matricula; // Referencia a objeto String
    String marca;
    double tarifa;    // Tipo primitivo para precisión decimal
    boolean disponible; // Estado lógico
}
```
*   **Nota Teórica:** Los nombres de atributos deben ser sustantivos representativos y seguir la nomenclatura *lowerCamelCase*.

---

*   **Métodos:** Son las acciones que el objeto puede realizar (ej. acelerar, frenar, calcular). 

#### **3.3 Constructores y la referencia `this`**
El **Constructor** es un método especial que se ejecuta automáticamente al crear el objeto (`new`) para inicializar sus atributos.
1. Debe tener el mismo nombre que la clase y no devuelve ningún valor.
2. No devuelve ningún valor (ni siquiera `void`).
3. Si no se define uno, Java crea un "constructor por defecto" sin parámetros.

*   **Uso de `this`:** Se utiliza para diferenciar el atributo de la clase de un parámetro que tenga el mismo nombre.

**Ejemplo de Implementación con `this`:**
El uso de `this.atributo` permite diferenciar el atributo de la clase de un parámetro con el mismo nombre.
```java
public Vehiculo(String matricula, String marca, double tarifa) {
    this.matricula = matricula;
    this.marca = marca;
    this.tarifa = tarifa;
    this.disponible = false; // Estado inicial por defecto
}
```

---

#### **3.4 Encapsulamiento: El Escudo Protector**
Es un "campo de fuerza" que evita que los datos sean manipulados de forma inapropiada.
*   **Private:** El atributo solo es accesible dentro de su propia clase.
*   **Public:** Accesible desde cualquier parte del proyecto.
*   **Regla de oro:** Declarar atributos como `private` y permitir el acceso mediante métodos `public` (Getters y Setters) para validar los datos antes de asignarlos.

**Práctica de Métodos Accesores (Getters y Setters):**
Se recomienda que los atributos sean `private` y se acceda a ellos mediante métodos públicos.
```java
// Método 'get' para obtener el valor
public double getTarifa() {
    return this.tarifa;
}

// Método 'set' para modificarlo con validación
public void setTarifa(double nuevaTarifa) {
    if (nuevaTarifa > 0) {
        this.tarifa = nuevaTarifa;
    }
}
```
===

### **Ejemplos Técnicos de la Sesión 3 **

#### **Ejemplo 3.1: Modelado Base y Encapsulamiento (Clase Vehículo)**
**Objetivo:** Implementar una clase con atributos privados, constructor y métodos de validación.

```java
public class Vehiculo {
    // 1. Atributos Privados (Encapsulamiento)
    private String marca;
    private String modelo;
    private double velocidad;

    // 2. Constructor
    public Vehiculo(String marca, String modelo) {
        this.marca = marca;
        this.modelo = modelo;
        this.velocidad = 0; // Inicia detenido
    }

    // 3. Métodos con lógica de negocio (Validación)
    public void setVelocidad(double nuevaVelocidad) {
        // Ejemplo de "Escudo Protector": No permite velocidades negativas ni absurdas
        if (nuevaVelocidad >= 0 && nuevaVelocidad <= 120) {
            this.velocidad = nuevaVelocidad;
        } else {
            System.out.println("Error: Velocidad fuera de los límites físicos permitidos.");
        }
    }

    public double getVelocidad() {
        return this.velocidad;
    }

    public void mostrarInfo() {
        System.out.println("Vehículo: " + marca + " " + modelo + " | Velocidad: " + velocidad + " km/h");
    }
}
```

#### **Ejemplo 3.2: Implementación en el Main**
```java
public class PruebaVehiculo {
    public static void main(String[] args) {
        // Instanciación del objeto
        Vehiculo miAuto = new Vehiculo("Toyota", "Corolla");
        
        miAuto.setVelocidad(80); // Asignación correcta
        miAuto.mostrarInfo();
        
        miAuto.setVelocidad(500); // Intento de asignar valor inválido
        miAuto.mostrarInfo(); // Mantiene los 80 km/h por la validación
    }
}
```

---

### **Ejercicios Prácticos de la Sesión 3**

#### **Ejercicio 3.1: El Libro Digital**
**Objetivo:** Crear una clase con múltiples atributos y métodos de resumen.
Diseña una clase `Libro` con atributos privados `titulo`, `autor` y `numPaginas`. 
1. Implementa un constructor que reciba los tres parámetros.
2. Crea un método `mostrarResumen()` que imprima: "El libro [titulo] de [autor] tiene [numPaginas] páginas".
3. En el `main`, instancia dos libros distintos y llama al método.

Solucion:

```java
// Clase Libro
public class Libro {
    private String titulo;
    private String autor;
    private int numPaginas;

    public Libro(String titulo, String autor, int numPaginas) {
        this.titulo = titulo;
        this.autor = autor;
        this.numPaginas = numPaginas;
    }

    public void mostrarResumen() {
        System.out.println("El libro '" + titulo + "' de " + autor + " tiene " + numPaginas + " páginas.");
    }

    public static void main(String[] args) {
        Libro libro1 = new Libro("Java para Todos", "José Cadenas", 350);
        Libro libro2 = new Libro("POO Avanzada", "IUJO Press", 200);
        
        libro1.mostrarResumen();
        libro2.mostrarResumen();
    }
}
```

#### **Ejercicio 3.2: Sistema Bancario Seguro**
**Objetivo:** Aplicar lógica de seguridad en el manejo de saldos.
Crea una clase `CuentaBancaria` con un atributo privado `saldo`. 
1. Implementa un constructor que inicie el saldo en 100.0.
2. Crea el método `depositar(double cantidad)`.
3. Crea el método `retirar(double cantidad)` que solo permita la operación si el saldo es suficiente; de lo contrario, muestra un error.

Solución:

```java
public class CuentaBancaria {
    private double saldo;

    public CuentaBancaria() {
        this.saldo = 100.0; // Saldo inicial por defecto
    }

    public void depositar(double cantidad) {
        if (cantidad > 0) {
            saldo += cantidad;
            System.out.println("Depósito exitoso. Nuevo saldo: B/. " + saldo);
        }
    }

    public void retirar(double cantidad) {
        if (cantidad <= saldo) {
            saldo -= cantidad;
            System.out.println("Retiro exitoso. Saldo restante: B/. " + saldo);
        } else {
            System.out.println("Error: Saldo insuficiente para retirar B/. " + cantidad);
        }
    }

    public static void main(String[] args) {
        CuentaBancaria miCuenta = new CuentaBancaria();
        miCuenta.depositar(50);
        miCuenta.retirar(200); // Debería mostrar error
        miCuenta.retirar(40);  // Debería ser exitoso
    }
}
```

---

### Ejemplos práctico:

### 1. El Sistema de Seguridad Bancaria (Validación de saldo)
Este es el ejemplo clásico para entender por qué el acceso directo es peligroso. Si el atributo `saldo` fuera público, cualquier parte del programa podría ponerlo en cero sin permiso.

*   **Concepto:** Controlar que el retiro no exceda el dinero disponible.
*   **Código Sugerido:**
```java
public class CuentaBancaria {
    private double saldo; // Atributo privado: nadie lo ve desde fuera

    public CuentaBancaria(double saldoInicial) {
        this.saldo = saldoInicial;
    }

    // Getter para consultar el saldo de forma segura
    public double getSaldo() {
        return this.saldo;
    }

    // Setter con lógica de negocio: evita saldos negativos
    public void retirar(double cantidad) {
        if (cantidad > 0 && cantidad <= saldo) {
            this.saldo -= cantidad;
        } else {
            System.out.println("Operación no válida: fondos insuficientes.");
        }
    }
}
```

---

### Prácticas propuestas:

### 3. El Termómetro Digital (Rangos de seguridad)

*   **Concepto:** Un atributo `celsius` que solo acepte valores entre -100 y 100 para evitar errores de sensores dañados.
*   **Implementación:** El método `setCelsius(double t)` debe incluir un bloque `if` que valide el rango antes de asignar el valor al atributo privado.

### 4. Datos de "Solo Lectura" (Atributos sin Setters)
No todos los datos deben ser modificables. El ID de un estudiante o el título de un libro no deberían cambiar una vez creados.

*   **Concepto:** Crear atributos que tengan `Getter` pero **no** `Setter`.
*   **Ejemplo:** En una clase `Libro`, el atributo `titulo` es privado y solo tiene un `getTitulo()`. Esto garantiza que, una vez instanciado el objeto, el nombre del libro permanezca íntegro durante toda la ejecución del programa.

### 5. La "Caja Negra" (Ocultamiento de complejidad)
El encapsulamiento también sirve para ocultar cómo se hace un cálculo interno, mostrando solo el resultado.

*   **Ejemplo de la Clase Rectángulo:** El usuario solo necesita usar `setAncho` y `setAlto`. La variable `area` no necesita un setter, ya que se calcula internamente mediante un método que multiplica ambos atributos privados.

**Reto Final de la Sesión:**
Crea una clase `Empleado` con atributos `nombre`, `salario` y `cargo`. Incluye un constructor para inicializar los datos y un método `aumentarSalario(double porcentaje)`.

#### **Resumen de Buenas Prácticas Profesionales (Sesión 3)**
1.  **Privacidad por defecto:** Declara siempre tus atributos como `private`.
2.  **Apertura selectiva:** Crea Getters y Setters solo para los datos que realmente necesiten ser consultados o modificados.
3.  **Identidad Única:** No uses Setters para datos que no deben cambiar, como el ID de un estudiante o el título de un libro una vez creado.
4.  **Uso de `this`:** Utilízalo siempre en constructores y setters para evitar ambigüedades con los nombres de variables.

***
