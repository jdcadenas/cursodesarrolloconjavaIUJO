<div style="display: flex; justify-content: space-between; align-items: center;">
  <div><br>
    <h2>Guía Instruccional</h2><br>
  </div>
  <div>
    <img src="LOGO_UPP_IUJO.png" alt="Logo IUJO" width="150">
  </div>
</div>

### **Introducción al Desarrollo con Java y POO**

### **Sesión 6: Manejo de Errores y Proyecto Final Integrador**

#### **Contenidos de esta sesión:**
1. Robustez del Sistema: Manejo de excepciones con `try-catch`.
2. Repaso Integral: Desde la sintaxis hasta la abstracción.
3. Diseño de la Aplicación "Agenda Personal".
4. Implementación del CRUD (Crear, Leer, Actualizar, Borrar).
5. Validación de datos y lógicas de búsqueda avanzada.

---

#### **6.1 Robustez: Manejo de Excepciones**
Un programa profesional no debe cerrarse inesperadamente si el usuario comete un error (como ingresar letras donde se pide un número).
*   **Bloque `try`:** Contiene el código "peligroso" que podría fallar.
*   **Bloque `catch`:** Captura el error (excepción) y permite al programador decidir cómo reaccionar sin detener el sistema.

#### **6.2 Repaso Integral: Java en Resumen**
Antes de iniciar la codificación final, revisamos los pilares que permiten construir software profesional:
*   **Sintaxis y Tipos de Datos:** Manejo de variables y constantes.
*   **Estructuras de Control:** Toma de decisiones con `if` y `switch`, y automatización con bucles `for` y `while`.
*   **Modularidad:** Uso de funciones y métodos para reutilizar lógica.
*   **POO:** Modelado de la realidad mediante clases, objetos, herencia y encapsulamiento.
*   **Abstracción:** Definición de contratos mediante interfaces.
*   **Colecciones:** Gestión dinámica de datos con `ArrayList` y `HashMap`.
*   **Robustez:** Manejo de errores con bloques `try-catch`.
*  
---

#### **6.2 Proyecto Final: Aplicación "Agenda Personal"**
El objetivo es construir una herramienta de consola que gestione contactos utilizando una arquitectura de objetos y colecciones dinámicas. La estructura se divide en tres capas:
1.  **Modelo de Datos:** La clase `Contacto`. Entidad que representa la información individual.
2.  **Lógica de Negocio:** La clase `Agenda` que gestiona el `ArrayList`.
3.  **Interfaz de Usuario:** El menú interactivo basado en `Scanner` y `switch`.

---

### **Implementación Técnica Paso a Paso **

#### **Paso 1: La Entidad (Clase Contacto)**
**Objetivo:** Aplicar encapsulamiento y métodos accesores para la información individual.

```java
public class Contacto {
    private String nombre;
    private String telefono;
    private String correo;

    public Contacto(String nombre, String telefono, String correo) {
        this.nombre = nombre;
        this.telefono = telefono;
        this.correo = correo;
    }

    // Getters y Setters (Encapsulamiento)
    public String getNombre() { return nombre; }
    public void setNombre(String nombre) { this.nombre = nombre; }
    public String getTelefono() { return telefono; }
    public void setTelefono(String telefono) { this.telefono = telefono; }
    public String getCorreo() { return correo; }

    @Override
    public String toString() {
        return "Nombre: " + nombre + " | Tel: " + telefono + " | Email: " + correo;
    }
}
```

#### **Paso 2: El Gestor (Clase Agenda)**
**Objetivo:** Implementar las operaciones CRUD utilizando un `ArrayList`.

```java
import java.util.ArrayList;

public class Agenda {
    private ArrayList<Contacto> listaContactos;

    public Agenda() {
        this.listaContactos = new ArrayList<>();
    }

    // CREATE: Añadir
    public void añadirContacto(Contacto c) {
        listaContactos.add(c);
        System.out.println("¡Contacto guardado con éxito!");
    }

    // READ: Listar todos
    public void listarContactos() {
        if (listaContactos.isEmpty()) {
            System.out.println("La agenda está vacía.");
        } else {
            for (Contacto c : listaContactos) {
                System.out.println(c);
            }
        }
    }

    // UPDATE: Editar por nombre
    public void editarTelefono(String nombre, String nuevoTel) {
        for (Contacto c : listaContactos) {
            if (c.getNombre().equalsIgnoreCase(nombre)) {
                c.setTelefono(nuevoTel);
                System.out.println("Teléfono actualizado.");
                return;
            }
        }
        System.out.println("Contacto no encontrado.");
    }

    // DELETE: Eliminar
    public void eliminarContacto(String nombre) {
        listaContactos.removeIf(c -> c.getNombre().equalsIgnoreCase(nombre));
        System.out.println("Proceso de eliminación finalizado.");
    }
}
```

#### **Paso 3: La Interfaz y Manejo de Errores (Clase Main)**
**Objetivo:** Crear un menú seguro que no falle ante entradas inválidas.

```java
import java.util.Scanner;
import java.util.InputMismatchException;

public class AppAgenda {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Agenda miAgenda = new Agenda();
        int opcion = 0;

        do {
            try {
                System.out.println("\n--- AGENDA IUJO BARQUISIMETO ---");
                System.out.println("1. Agregar Contacto\n2. Mostrar Todos\n3. Eliminar\n4. Salir");
                System.out.print("Seleccione: ");
                opcion = sc.nextInt(); // Riesgo de InputMismatchException
                sc.nextLine(); // Limpiar buffer

                switch (opcion) {
                    case 1:
                        System.out.print("Nombre: "); String n = sc.nextLine();
                        System.out.print("Teléfono: "); String t = sc.nextLine();
                        System.out.print("Correo: "); String e = sc.nextLine();
                        if(n.isEmpty() || t.isEmpty()) {
                            System.out.println("Error: Nombre y Teléfono son obligatorios.");
                        } else {
                            miAgenda.añadirContacto(new Contacto(n, t, e));
                        }
                        break;
                    case 2:
                        miAgenda.listarContactos();
                        break;
                    case 3:
                        System.out.print("Nombre a eliminar: ");
                        miAgenda.eliminarContacto(sc.nextLine());
                        break;
                }
            } catch (InputMismatchException e) {
                System.out.println("ERROR: Debe ingresar un número del menú.");
                sc.nextLine(); // IMPORTANTE: Limpiar el error del Scanner
            }
        } while (opcion != 4);
        System.out.println("Cerrando sistema...");
    }
}
```

---

### **Ejercicios de Validación de Conocimientos (Sesión 6)**

#### **Ejercicio 6.1: Búsqueda Avanzada (Reto de Lógica)**
**Instrucción:** Añade a la clase `Agenda` un método llamado `buscarPorNombre(String filtro)` que no solo busque coincidencias exactas, sino que muestre todos los contactos cuyo nombre **comience** con las letras ingresadas (usa el método `.startsWith()`).

---
- Ejemplo para buscar:
```java
public void buscarPorNombre(String nombreBuscado) {
    for (Contacto c : contactos) {
        if (c.nombre.equalsIgnoreCase(nombreBuscado)) {
            c.mostrar();
            return;
        }
    }
    System.out.println("Contacto no encontrado.");
}
```


#### **Ejercicio 6.2: El Escudo de Datos (Excepciones)**
**Instrucción:** Modifica el proceso de agregar contacto para que, si el usuario ingresa un número de teléfono con letras, el programa lance una excepción personalizada o maneje el error avisando que el formato es incorrecto.

---

#### **Resumen de Buenas Prácticas Profesionales (Sesión 6)**
1.  **Limpieza de Buffer:** Siempre usa `sc.nextLine()` después de `sc.nextInt()` para evitar que el menú se salte pasos.
2.  **Validación Temprana:** Comprueba que los campos obligatorios no estén vacíos antes de crear un objeto.
3.  **Mensajes Claros:** En los bloques `catch`, ofrece soluciones al usuario en lugar de solo mostrar códigos de error técnicos.
4.  **Modularidad Final:** Mantén la lógica de la lista en la clase `Agenda` y deja que el `Main` solo se encargue de hablar con el usuario.

---

### **Dinámica Final de Aula**
1.  **Planificación:** Los equipos definen las tareas y el diseño de sus objetos.
2.  **Desarrollo:** Implementación supervisada por el facilitador asegurando una estructura POO adecuada.
3.  **Presentación:** Cada equipo presenta su código, explica las funcionalidades extra y recibe retroalimentación del grupo.

---

### **Resumen de Cierre y Preguntas Clave**
Al finalizar, el estudiante debe ser capaz de responder:
*   ¿Qué ventajas trajo el uso de un `ArrayList` en la agenda frente a un arreglo fijo?
*   ¿Cómo mejora la seguridad de la app el uso de métodos y encapsulamiento?
*   ¿Cómo aplicaría herencia si el sistema creciera para manejar "Contactos Familiares" y "Contactos de Trabajo"?

**Consejos para el Futuro:** No detenerse aquí. Continuar practicando con proyectos pequeños como inventarios o juegos, y explorar recursos como YouTube, Stack Overflow y la documentación oficial de Java.


*Esta guía instruccional fue desarrollada para el IUJO por el Facilitador José Daniel Cadenas Lucero, Barquisimeto, 2026.*