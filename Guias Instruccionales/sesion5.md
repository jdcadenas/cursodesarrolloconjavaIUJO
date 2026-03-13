<div style="display: flex; justify-content: space-between; align-items: center;">
  <div><br>
    <h2>Guía Instruccional</h2><br>
  </div>
  <div>
    <img src="LOGO_UPP_IUJO.png" alt="Logo IUJO" width="150">
  </div>
</div>

### **Introducción al Desarrollo con Java y POO**
### **Sesión 5: Colecciones Fijas y Dinámicas**

#### **Contenidos de esta sesión:**
1. Conceptos Fundamentales: Estructuras Dinámicas e Interoperabilidad.
2. Tipos Genéricos (`Generics`) y Seguridad de Tipos.
3. `ArrayList`: El arreglo redimensionable.
4. `HashMap`: Gestión de datos por Clave-Valor.
5. `HashSet` y la eliminación automática de duplicados.
6. Iteración Avanzada con el bucle `for-each`.

---
#### **5.1 Arreglos Fijos (Arrays)**


Un array es una caja con un número de compartimientos que no puede cambiar una vez definida. 

**Práctica:** Crea una lista de nombres de estudiantes. Muestra cómo agregar, eliminar y recorrer la lista con un ciclo `for-each`.

**Código de Ejemplo:**
```java
ArrayList<String> estudiantes = new ArrayList<>();
estudiantes.add("Ana");
estudiantes.add("Luis");
for (String e : estudiantes) {
    System.out.println("Estudiante: " + e);
}
```

**Ejercicio 5.1: Manipulación de Índices**  
Crea un arreglo de 5 números enteros. Imprime su longitud total, luego modifica el valor del tercer elemento (índice 2) e imprime el valor antes y después del cambio.  

**Solución sugerida:**
```java
int[] numeros = {10, 20, 30, 40, 50};
System.out.println("Longitud: " + numeros.length); // Imprime 5
numeros = 99; // Cambia 30 por 99
```

---


#### **5.2 El Poder de las Colecciones Dinámicas**
A diferencia de los arreglos tradicionales que tienen un tamaño inamovible, las colecciones de Java crecen o disminuyen su tamaño en memoria automáticamente según sea necesario.
*   **Generics (`<E>`):** Es la sintaxis de diamantes que usamos para decirle a Java exactamente qué tipo de objeto guardará la colección. Esto evita errores de tipo en tiempo de ejecución.

#### **5.2 ArrayList: Listas Dinámicas**
Es la colección más utilizada en el mundo laboral. Permite mantener una secuencia ordenada de elementos donde la posición (índice) es fundamental.
Las colecciones permiten guardar listas de datos sin preocuparse por el tamaño final.

A diferencia de los arreglos fijos, el `ArrayList` puede crecer o decrecer según necesites agregar o eliminar elementos.

**Ejercicio 5.2: Gestión de Estudiantes**  
Crea una lista llamada `listaEstudiantes`. Realiza las siguientes acciones:
1. Agrega cuatro nombres de compañeros.
2. Elimina al segundo compañero de la lista.
3. Verifica si un nombre específico existe en la lista usando el método `.contains()`.
4. Ordena la lista alfabéticamente usando `Collections.sort()`.

*   **Operaciones Clave:**
    *   `add(elemento)`: Añade al final de la lista.
    *   `get(indice)`: Recupera el objeto en esa posición.
    *   `remove(indice)`: Elimina el elemento y compacta la lista automáticamente.

**Código de apoyo:**
```java
ArrayList<String> lista = new ArrayList<>();
lista.add("Pedro"); 
lista.remove(1); // Elimina el elemento en el índice 1
Collections.sort(lista); // Requiere import java.util.Collections
```

---

#### **5.3 HashMap: Diccionarios de Datos - Mapas de Clave-Valor**
Funciona bajo una lógica de pares: cada elemento consta de una **Clave única** y un **Valor** asociado.
*   **Regla de Oro:** No puede haber claves duplicadas. Si insertas una clave que ya existe, el nuevo valor reemplazará al anterior ("machaca" el dato).

**Ejercicio 5.4: Directorio IUJO**  
Desarrolla un programa que almacene nombres de estudiantes como clave y su número de teléfono como valor.
1. Añade 3 contactos.
2. Modifica el teléfono de uno de ellos usando el método `.put()` con la misma clave.
3. Busca y muestra en pantalla el teléfono de un estudiante ingresando su nombre con `.get()`.

---

#### **5.5 HashSet: Conjuntos Únicos**
Se utiliza cuando la prioridad absoluta es que **no existan datos duplicados**. No garantiza un orden específico, pero es extremadamente eficiente para asegurar que cada elemento sea único.

**Ejercicio 5.5: Evitando Duplicados**  
Crea un `HashSet` de países. Intenta agregar "Venezuela" dos veces y otros tres países distintos. Imprime el tamaño del conjunto y observa que el duplicado fue ignorado automáticamente.

**Resultado esperado:**  
Si agregas 5 elementos pero 1 es repetido, el método `.size()` debe retornar 4.

---

### **Ejemplos Técnicos de la Sesión 5 **

#### **Ejemplo 5.1: Gestión de Lista de Tareas (ArrayList)**
**Objetivo:** Mostrar cómo agregar y recorrer elementos dinámicamente.

```java
import java.util.ArrayList; // Inicialización dinámica

public class GestionTareas {
    public static void main(String[] args) {
        // Definición con Genéricos <String>
        ArrayList<String> tareas = new ArrayList<>(); // Inicialización dinámica

        // Añadir elementos
        tareas.add("Configurar JDK");
        tareas.add("Instalar VS Code");
        tareas.add("Crear primera Clase");

        System.out.println("Lista inicial: " + tareas);
        System.out.println("Total tareas: " + tareas.size());

        // Eliminar por índice
        tareas.remove(1); // Elimina "Instalar VS Code"

        // Recorrer con for-each (Iteración moderna)
        System.out.println("Tareas pendientes:");
        for (String t : tareas) {
            System.out.println("- " + t);
        }
    }
}
```

#### **Ejemplo 5.2: Directorio de Puntuaciones (HashMap)**
**Objetivo:** Implementar la búsqueda rápida mediante claves.

```java
import java.util.HashMap;

public class SistemaPuntos {
    public static void main(String[] args) {
        // Clave: Nombre (String), Valor: Puntos (Integer)
        HashMap<String, Integer> ranking = new HashMap<>();

        ranking.put("Ana", 1500); // put() se usa en lugar de add()
        ranking.put("Luis", 1200);
        ranking.put("Carla", 1800);

        // Buscar un valor por su clave
        String usuario = "Ana";
        if (ranking.containsKey(usuario)) {
            System.out.println(usuario + " tiene " + ranking.get(usuario) + " puntos.");
        }
    }
}
```

---

### **Ejercicios Prácticos de la Sesión 5**

#### **Ejercicio 5.1: Registro de Estudiantes Dinámico**
**Objetivo:** Crear un programa que reciba nombres hasta que el usuario decida parar.

```java
import java.util.ArrayList;
import java.util.Scanner;

public class RegistroEstudiantes {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<String> lista = new ArrayList<>();
        String nombre;

        System.out.println("Ingrese nombres (escriba 'fin' para terminar):");
        while (true) {
            nombre = sc.nextLine();
            if (nombre.equalsIgnoreCase("fin")) break;
            lista.add(nombre);
        }

        System.out.println("Grupo registrado: " + lista);
        if (lista.size() >= 2) {
            lista.remove(1); // Eliminar al segundo
            System.out.println("Lista actualizada: " + lista);
        }
    }
}
```

#### **Ejercicio 5.2: Eliminador Automático de Duplicados**
**Objetivo:** Demostrar cómo el `HashSet` filtra datos repetidos.

```java
import java.util.ArrayList;
import java.util.HashSet;

public class FiltroDuplicados {
    public static void main(String[] args) {
        ArrayList<String> nombres = new ArrayList<>();
        nombres.add("Pedro");
        nombres.add("Ana");
        nombres.add("Pedro"); // Repetido
        nombres.add("Luis");
        nombres.add("Ana");   // Repetido

        // Transferir a un HashSet para limpiar
        HashSet<String> unicos = new HashSet<>(nombres);

        System.out.println("Lista original (con repetidos): " + nombres);
        System.out.println("Conjunto único (limpio): " + unicos);
    }
}
```

---

#### **Conceptos Fundamentales de esta Unidad**
*   **Estructuras Dinámicas:** A diferencia de los arreglos tradicionales, estas colecciones crecen o disminuyen su tamaño en memoria automáticamente según sea necesario.
*   **Tipos Genéricos (`Generics`):** Java utiliza la sintaxis de diamantes `<E>` para especificar qué tipo de objeto guardará la colección, garantizando la seguridad del código y evitando errores de tipo en tiempo de ejecución.
*   **Interoperabilidad:** El marco de colecciones está diseñado para que diferentes tipos de estructuras (listas, conjuntos, mapas) trabajen de manera similar y sean fáciles de adaptar.

---

### **Prácticas de Desarrollo de la Sesión 5**

**Ejercicio 5.1: Registro de Estudiantes (`ArrayList`)**
Crea un programa que permita al usuario ingresar nombres de estudiantes hasta que escriba "fin". Al terminar, el programa debe mostrar la lista completa, eliminar al segundo estudiante de la lista y mostrar el tamaño final del grupo.

**Ejercicio 5.2: Inventario de Productos (`HashMap`)**
Desarrolla un sistema de inventario donde la **Clave** sea el nombre del producto y el **Valor** sea su precio.
1. Agrega 3 productos.
2. Solicita al usuario el nombre de un producto para buscarlo.
3. Si existe, muestra el precio; si no, informa que no está en stock.

**Ejercicio 5.3: Eliminador de Duplicados (`HashSet`)**
Crea un `ArrayList` con 5 nombres, asegurándote de repetir al menos dos. Luego, transfiere todos los elementos a un `HashSet` e imprime el resultado para demostrar cómo desaparecen los duplicados automáticamente.

**Reto Final: Mini Sistema de Biblioteca (Integración)**
En equipos, construyan una jerarquía básica:
*   Usen un `ArrayList<Libro>` para registrar el inventario total.
*   Usen un `HashMap<String, String>` para asociar el nombre de un usuario con el título del libro que tiene prestado.

---

#### **Resumen de Buenas Prácticas Profesionales (Sesión 5)**
- Diferencias entre estructuras estáticas (Array) y dinámicas (`ArrayList`).
- Uso de `HashSet` para garantizar la unicidad de los datos.
- Implementación de `HashMap` para búsquedas rápidas por clave.
- Métodos esenciales: `add`, `put`, `remove`, `get` y `contains`.

1.  **Programar para Interfaces:** Declara tus colecciones usando la interfaz (ej: `List<String> lista = new ArrayList<>();`) para que tu código sea más flexible.
2.  **Seguridad de Tipos:** Usa siempre los Genéricos `< >`. Evita las colecciones "crudas" para prevenir errores inesperados de conversión de datos.
3.  **Verificación de Vacío:** Prefiere usar el método `.isEmpty()` en lugar de comparar el tamaño con cero (`.size() == 0`), ya que es semánticamente más claro.
4.  **Eficiencia en Búsqueda:** Si tu aplicación requiere buscar elementos constantemente entre miles de registros, utiliza un `HashMap` o `HashSet`, ya que son mucho más rápidos que recorrer un `ArrayList` posición por posición.

***
