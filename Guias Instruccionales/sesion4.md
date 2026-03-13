<div style="display: flex; justify-content: space-between; align-items: center;">
  <div><br>
    <h2>Guía Instruccional</h2><br>
  </div>
  <div>
    <img src="LOGO_UPP_IUJO.png" alt="Logo IUJO" width="150">
  </div>
</div>

### **Introducción al Desarrollo con Java y POO**

### **Sesión 4: Herencia, Abstracción e Interfaces**

#### **Contenidos de esta sesión:**
1. Herencia: Creación de superclases y subclases (Relación "Es-Un").
2. Navegación jerárquica: Uso de `super` y `this`.
3. Abstracción: Definición de plantillas con clases y métodos abstractos.
4. Interfaces: El contrato del sistema y la implementación múltiple.
5. Miembros de Clase: Atributos y métodos estáticos (`static`).

---

#### **4.1 Herencia: Especialización de Clases**
La herencia permite que una clase (subclase) adquiera automáticamente los atributos y métodos de otra (superclase).
*   **Relación "Es-Un":** Se usa cuando una categoría es una versión especializada de otra (ej. un Gerente **es un** Empleado).
*   **Reutilización:** Evita duplicar código al heredar comportamientos comunes y solo programar lo que hace única a la subclase.

**Ejemplo Técnico (Jerarquía de Vehículos):**
```java
public class Vehiculo {
    protected String matricula; // Protected permite acceso a las subclases
    public void arrancar() { System.out.println("Vehículo en marcha"); }
}

public class Coche extends Vehiculo { // 'extends' establece la herencia
    private int puertas;
    public void tocarBocina() { System.out.println("Beep beep"); }
}
```

---

#### **4.2 Referencias: `this` vs. `super`**
Para manejar la jerarquía, Java provee palabras reservadas específicas:
*   **`this`:** Se refiere al objeto actual de la clase donde se encuentra.
*   **`super`:** Se usa para invocar el constructor de la clase padre o acceder a sus métodos. En un constructor, `super()` debe ser siempre la primera instrucción.

**Uso en Constructores:**
```java
public Coche(String matricula, int puertas) {
    super(matricula); // Llama al constructor del padre
    this.puertas = puertas; // Referencia al atributo propio
}
```

---


#### **4.3 Clases y Métodos Abstractos**
A veces necesitamos definir una "plantilla" que no tenga sentido instanciar por sí misma.
*   **Clase Abstracta:** Una clase que no puede crear objetos con `new`. Sirve solo para ser heredada.
*   **Método Abstracto:** Una acción que declaramos sin cuerpo (sin código) para **obligar** a las subclases a darle una implementación real.

#### **4.4 Interfaces: Contratos de Comportamiento**
Una interfaz define **qué** debe hacer una clase, pero no **cómo**.
*   **Poder de Java:** A diferencia de las clases, una misma clase puede implementar **múltiples interfaces**, superando la limitación de la herencia simple.

#### **4.5 Miembros Estáticos (`static`)**
Los elementos marcados como `static` pertenecen a la **clase** y no a los objetos individuales. Se pueden usar sin necesidad de crear una instancia (ej. `Math.sqrt()`).

---

### **Ejemplos Técnicos de la Sesión 4 **

#### **Ejemplo 4.1: Jerarquía de Empleados (Herencia)**
**Objetivo:** Mostrar cómo una subclase hereda y extiende el comportamiento de su padre.

```java
// Superclase
public class Empleado {
    protected String nombre;
    protected double salario;

    public Empleado(String nombre, double salario) {
        this.nombre = nombre;
        this.salario = salario;
    }

    public void mostrarDatos() {
        System.out.println("Empleado: " + nombre + " | Salario: B/. " + salario);
    }
}

// Subclase
public class Gerente extends Empleado {
    private String departamento;

    public Gerente(String nombre, double salario, String departamento) {
        super(nombre, salario); // Llama al constructor del padre
        this.departamento = departamento;
    }

    @Override
    public void mostrarDatos() {
        super.mostrarDatos(); // Usa la lógica del padre
        System.out.println("Cargo: Gerente de " + departamento);
    }
}
```

#### **Ejemplo 4.2: Figuras Geométricas (Abstracción)**
**Objetivo:** Implementar métodos abstractos que cada figura calcula de forma distinta.

```java
public abstract class Figura {
    public abstract double calcularArea(); // Obliga a las hijas a implementarlo
}

public class Rectangulo extends Figura {
    private double base, altura;

    public Rectangulo(double base, double altura) {
        this.base = base;
        this.altura = altura;
    }

    @Override
    public double calcularArea() {
        return base * altura;
    }
}
```

---

### **Ejercicios Prácticos de la Sesión 4**

#### **Ejercicio 4.1: Sistema de Dispositivos (Interfaces)**
**Objetivo:** Crear un contrato que dispositivos de distintas marcas deben cumplir.

```java
// Definición del Contrato
interface Conectable {
    void encender();
    void apagar();
}

// Implementación en una SmartTV
public class SmartTV implements Conectable {
    @Override
    public void encender() {
        System.out.println("SmartTV: Mostrando logo de bienvenida y conectando a WiFi...");
    }

    @Override
    public void apagar() {
        System.out.println("SmartTV: Guardando estado y apagando pantalla.");
    }
}

// Prueba en el Main
public class PruebaInterface {
    public static void main(String[] args) {
        Conectable miTV = new SmartTV();
        miTV.encender();
        miTV.apagar();
    }
}
```

#### **Ejercicio 4.2: El Contador de Instancias (Static)**
**Objetivo:** Usar un atributo estático para contar cuántos objetos se han creado de una clase.

```java
public class Estudiante {
    public static int contador = 0; // Pertenece a la clase
    private String nombre;

    public Estudiante(String nombre) {
        this.nombre = nombre;
        contador++; // Se incrementa con cada nuevo objeto
    }

    public static void main(String[] args) {
        new Estudiante("Ana");
        new Estudiante("Luis");
        new Estudiante("Pedro");
        System.out.println("Total estudiantes registrados: " + Estudiante.contador);
    }
}
```

---

#### **Resumen de Buenas Prácticas Profesionales (Sesión 4)**
1.  **Anotación `@Override`:** Úsala siempre al sobrescribir métodos para que el compilador valide que la firma es correcta.
2.  **Uso de `final`:** Si no quieres que una clase sea heredada o un método sea modificado, márcalos como `final`.
3.  **Constantes:** Las variables `static final` deben escribirse siempre en **MAYÚSCULAS** (ej. `PI_VALOR`).
4.  **Visibilidad `protected`:** Úsalo solo cuando necesites que las subclases vean el atributo; de lo contrario, prefiere `private` para mantener el encapsulamiento.
5.  **Responsabilidad Única:** No satures una interfaz; es mejor tener varias interfaces pequeñas y específicas que una gigante.

***
