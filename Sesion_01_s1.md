| <div align="right"><img src="../Logo-UNA-Rojo_FondoTransparente%20(2).png" width="120" alt="Logo UNA" /></div> | | <p align="right"><img src="../images.jpeg" width="120" alt="Logo EscINF" /></p> |
|:----------------------------------------------------|:-------------------------------------------------------------:|------------------------------------------------------------:|

**Programa de curso** · **Programación I** · **C++**
**Carrera:** Ingeniería de Sistemas de Información con grado en Bachillerato y salida lateral de Diplomado en Programación de Aplicaciones Informáticas.

**Lenguaje del curso:** EIF-201 desarrolla **todas** las soluciones en **C++** (compilación con `g++ -std=c++11 -Wall`). Use archivos `.h` / `.cpp` cuando el diseño lo requiera, `using namespace std;` en ejemplos de clase, y buenas prácticas del estándar C++.

---

CLASE #: 1
SEMANA: 1
FECHA APROXIMADA: 20/07/26 – 26/07/26 (Lunes o Martes)
TEMA PRINCIPAL: Paradigmas de programación: programación estructurada vs orientada a objetos
DURACIÓN: 1 hora y 30 minutos

---

## 1. Objetivo de la clase

Distinguir el paradigma estructurado del orientado a objetos, identificar ventajas del modelado por entidades y preparar el vocabulario académico del curso (clase, objeto, mensaje, estado).

## 2. Conocimientos previos necesarios

EIF200: variables, tipos de datos, estructuras de control, funciones, arreglos unidimensionales y modularización básica en C++.

## 3. Explicación teórica de la clase

La Programación Orientada a Objetos (POO) surge como respuesta a la complejidad creciente del software. Mientras la programación estructurada organiza la solución en funciones y procedimientos que operan sobre datos separados, la POO integra datos y comportamiento en una unidad coherente llamada **objeto**. Un objeto es una instancia concreta de una **clase**, que actúa como plantilla o molde: define atributos (estado) y métodos (comportamiento).

El paradigma estructurado —heredero del modelo de Von Neumann— privilegia la descomposición funcional: se identifican las tareas y se implementan como funciones. Este enfoque es eficaz para programas pequeños, pero cuando el sistema crece, las funciones tienden a compartir variables globales o estructuras de datos amplias, incrementando el acoplamiento y dificultando el mantenimiento. La POO propone modelar el dominio del problema con entidades reconocibles: un `Estudiante`, una `CuentaBancaria`, un `Producto`. Cada entidad encapsula su estado y expone operaciones controladas.

Los **principios fundamentales** que se desarrollarán en el curso son: **abstracción** (representar lo esencial ignorando detalles irrelevantes), **encapsulamiento** (ocultar la representación interna y proteger la integridad del estado), **ocultamiento de información** (restringir el acceso mediante especificadores de acceso) y, en semanas posteriores, **herencia** y **polimorfismo**. En esta primera sesión se enfatiza la transición conceptual: de pensar en "qué funciones necesito" a pensar en "qué objetos interactúan y qué responsabilidades tiene cada uno".

Un error frecuente en estudiantes principiantes es crear clases que son meros contenedores de datos sin comportamiento, reproduciendo estructuras `struct` con métodos triviales. La POO exige diseñar responsabilidades: un método debe tener sentido respecto al objeto que lo ejecuta. Otra confusión común es creer que usar `class` en lugar de `struct` ya implica programación orientada a objetos; sin embargo, la orientación a objetos es un estilo de diseño, no solo una palabra clave.

Las buenas prácticas iniciales incluyen: nombrar clases con sustantivos en singular (`Libro`, no `Libros`), identificar sustantivos del enunciado como candidatos a clases y verbos como candidatos a métodos, y evitar clases "dios" que concentran demasiadas responsabilidades. La POO favorece la reutilización mediante composición y herencia, la extensibilidad sin modificar código existente y la verificación de diseño mediante diagramas (introducidos formalmente en semanas posteriores).

**Referencia (APA):** (Joyanes, 1996; Deitel & Deitel, 2016). Joyanes, capítulos introductorios al paradigma; Deitel, transición de programación estructurada a POO.

En ingeniería de software, la transición al paradigma orientado a objetos implica reorganizar la forma en que se particionan responsabilidades. Un módulo estructurado concentra lógica en funciones que reciben estructuras; cuando el dominio evoluciona, cualquier cambio en la estructura obliga a revisar todas las funciones asociadas. En cambio, al agrupar estado y operaciones, el impacto del cambio queda acotado al interior de la clase siempre que la interfaz pública se mantenga estable. Este principio de ocultamiento será formalizado con `private` en la sesión siguiente, pero ya en esta clase el estudiante debe reconocer que la POO es ante todo una disciplina de diseño. Asimismo, conviene contrastar objeto con valor: dos variables estructuradas pueden compartir campos copiados sin relación; dos objetos interactúan mediante mensajes y mantienen identidad propia. En laboratorio se sugiere construir un diagrama simple de objetos en tiempo de ejecución (cajas con nombre de clase y valor de atributos) para fijar la noción de estado. Por último, la POO no elimina la necesidad de algoritmos correctos: los métodos siguen empleando secuencia, selección e iteración; lo que cambia es dónde reside la lógica y cómo se protege el estado.

## 4. Ejemplo guiado en C++

```cpp
// Ejemplo comparativo: enfoque estructurado vs primer acercamiento OO
#include <iostream>
#include <string>
using namespace std;

// --- Enfoque estructurado: datos y funciones separados ---
struct RectanguloE {
    double ancho, alto;
};

double areaEstructurada(const RectanguloE& r) {
    return r.ancho * r.alto;
}

// --- Enfoque OO: datos y comportamiento unidos ---
class Rectangulo {
    double ancho, alto;
public:
    Rectangulo(double a, double h) : ancho(a), alto(h) {}

    double calcularArea() const {
        return ancho * alto;
    }

    void mostrar() const {
        cout << "Rectangulo OO: " << ancho << " x " << alto
             << " area=" << calcularArea() << endl;
    }
};

int main() {
    RectanguloE re = {4.0, 5.0};
    cout << "Area estructurada: " << areaEstructurada(re) << endl;

    Rectangulo ro(4.0, 5.0);
    ro.mostrar();
    return 0;
}
```

## 5. Actividad práctica guiada en clase

**Profesor:** Presenta un enunciado real (biblioteca universitaria) y pide identificar sustantivos (Libro, Estudiante, Préstamo) y verbos (prestar, devolver, buscar). Modela en pizarra una clase `Libro` con atributos mínimos y un método `mostrar()`.

**Estudiante:** En parejas, proponen dos clases del dominio "sistema de matrícula" con al menos dos atributos y un método cada una. Comparten en plenario y el profesor corrige nomenclatura y responsabilidades.

## 6. Cierre de la clase

Se sintetiza la diferencia paradigma estructurado/OO, se recuerda que toda clase necesita diseño previo de responsabilidades y se anticipa la sesión 2 sobre encapsulamiento formal.

## 7. Tarea o práctica sugerida

Leer Joyanes cap. introductorio y Deitel sección de clases en C++. Implementar en C++ un ejemplo propio que contraste enfoque estructurado vs OO; documentar en MD con código fuente y salida de `g++`.

## 8. Diez ejercicios de nivel alto

> **C++ obligatorio:** salvo clases de repaso escrito (14, 24, 32), cada ejercicio exige **diseño de clases e implementación en C++** compilable. Documente en MD el análisis y adjunte el código fuente.

### Ejercicio 1

**Enunciado:** Diseñe e implemente en C++ un sistema de venta de boletos de cine con al menos cinco clases (`Pelicula`, `Sala`, `Funcion`, `Cliente`, `Boleto` u otras justificadas).

**Requisitos técnicos:** Archivos `.h` y `.cpp` por clase (o agrupación razonable), `main.cpp`, `using namespace std;`.

**Restricciones:** Sin herencia ni punteros dinámicos aún; objetos automáticos en `main`.

**Criterios de evaluación:** Cohesión de clases, compilación sin errores, encapsulamiento.

**Resultado esperado:** Programa que cree objetos, reserve un boleto y muestre datos por consola.

**Sugerencia opcional:** Cada clase con al menos un método con comportamiento, no solo getters.

### Ejercicio 2

**Enunciado:** Convierta a C++ un programa estructurado con función `calcularPromedio(int arr[], int n)` usando la clase `ConjuntoNotas` que encapsule el arreglo y el cálculo.

**Requisitos técnicos:** Clase en `.h`/`.cpp`, `main.cpp` de prueba, `g++ -std=c++11 -Wall`.

**Restricciones:** Arreglo fijo máximo 30 elementos, atributos privados.

**Criterios de evaluación:** Encapsulamiento, compilación sin errores.

**Resultado esperado:** El arreglo no es accedido desde `main`; promedio vía método del objeto.

**Sugerencia opcional:** Incluya constructor que inicialice el arreglo.

### Ejercicio 3

**Enunciado:** Reemplace una variable global `contadorClientes` por la clase C++ `RegistroClientes` con métodos para registrar y consultar el total.

**Requisitos técnicos:** Implementación completa en C++ con encapsulamiento (`private`).

**Restricciones:** Prohibido usar variables globales de conteo.

**Criterios de evaluación:** Estado protegido, interfaz pública mínima.

**Resultado esperado:** Dos escenarios en `main` demuestran que el contador es consistente.

**Sugerencia opcional:** Anticipe el patrón `static` de la semana 7 como mejora futura.

### Ejercicio 4

**Enunciado:** Implemente clase `Punto2D` con coordenadas y método `distanciaAlOrigen()` sin usar funciones libres para el cálculo.

**Requisitos técnicos:** Archivo `.cpp` único o `.h`/`.cpp`, `using namespace std;`.

**Restricciones:** Coordenadas tipo double; método const.

**Criterios de evaluación:** Correctitud matemática, uso de const, compilación sin warnings.

**Resultado esperado:** Programa que cree dos puntos e imprima distancias.

**Sugerencia opcional:** Use `sqrt` de `<cmath>`.

### Ejercicio 5

**Enunciado:** Implemente en C++ la colaboración entre clases `Cajero` y `Cuenta` para una operación de retiro con validación de saldo.

**Requisitos técnicos:** Mínimo dos clases en `.h`/`.cpp`, `main.cpp` con escenario de prueba.

**Restricciones:** Monto válido y saldo suficiente; sin lógica de negocio en `main`.

**Criterios de evaluación:** Mensajes entre objetos vía métodos públicos.

**Resultado esperado:** Ejecución que muestre retiro exitoso y retiro rechazado.

**Sugerencia opcional:** Las validaciones viven en `Cuenta`, no en `main`.

### Ejercicio 6

**Enunciado:** Compare `struct` y `class` en C++: implemente el mismo tipo `Vector2D` una vez como `struct` y otra como `class`, demostrando el acceso por defecto.

**Requisitos técnicos:** Dos versiones en archivos separados o ramas comentadas, con `main` de prueba.

**Restricciones:** Basarse en el estándar C++.

**Criterios de evaluación:** Precisión técnica y código ejecutable.

**Resultado esperado:** Salida que demuestre diferencia de acceso por defecto.

**Sugerencia opcional:** En POO moderna, `class` es la elección habitual.

### Ejercicio 7

**Enunciado:** Implemente clase `RelojDigital` con hora y minuto; métodos `avanzarMinuto()` y `mostrar()` con formato HH:MM.

**Requisitos técnicos:** Un `.cpp` o `.h`/`.cpp`, `using namespace std;`.

**Restricciones:** Validar desbordamiento 59->0 y hora.

**Criterios de evaluación:** Manejo de estado interno correcto.

**Resultado esperado:** Salida correcta tras varios avances.

**Sugerencia opcional:** No usar arreglos; solo enteros.

### Ejercicio 8

**Enunciado:** Refactorice a C++ orientado a objetos un fragmento estructurado dado (funciones + variables sueltas) conservando la funcionalidad.

**Requisitos técnicos:** Entregar `antes.cpp` y `despues.cpp` (o carpetas) compilables.

**Restricciones:** Al menos dos clases en la versión OO.

**Criterios de evaluación:** Calidad de la refactorización.

**Resultado esperado:** Ambas versiones compilan; la OO usa encapsulamiento.

**Sugerencia opcional:** Busque datos que viajan juntos entre funciones.

### Ejercicio 9

**Enunciado:** Implemente en C++ un programa con dos clases que ilustren un error de diseño estructurado y su corrección OO (comentarios explicativos en el código).

**Requisitos técnicos:** Un `main.cpp` y clases en `.h`/`.cpp`, más breve informe MD con captura de salida.

**Restricciones:** Nivel intermedio, código compilable.

**Criterios de evaluación:** Calidad pedagógica y uso de C++.

**Resultado esperado:** Programa ejecutable y documentación MD.

**Sugerencia opcional:** Incluya comentarios `//` explicando cada decisión.

### Ejercicio 10

**Enunciado:** Implemente clases `Cajero` y `CuentaBancaria` en C++ con métodos `retirar` y `consultarSaldo`; simule en `main` una secuencia de 6–10 operaciones.

**Requisitos técnicos:** Proyecto C++ modular `.h`/`.cpp`.

**Restricciones:** Monto válido, saldo suficiente, sin atributos públicos.

**Criterios de evaluación:** Secuencia lógica completa en tiempo de ejecución.

**Resultado esperado:** Traza de operaciones coherente impresa en consola.

**Sugerencia opcional:** Toda validación dentro de `CuentaBancaria`.


## 9. Errores comunes esperados

- Confundir clase con objeto (molde vs instancia).
- Nombrar clases en plural o con verbos.
- Crear clases sin métodos (solo datos públicos).
- Pensar que POO elimina la necesidad de planificar.

## 10. Recomendaciones para el profesor

Use analogías concretas (planos arquitectónicos = clase, casa construida = objeto). Evite introducir herencia o punteros hoy. Refuerce vocabulario en español académico.

---

**Formato de entrega:** Código y documentación en archivos **MD (Markdown)** según política del curso.
