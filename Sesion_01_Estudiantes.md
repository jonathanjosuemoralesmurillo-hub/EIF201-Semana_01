| <div align="right"><img src="../Logo-UNA-Rojo_FondoTransparente%20(2).png" width="120" alt="Logo UNA" /></div> | | <p align="right"><img src="../images.jpeg" width="120" alt="Logo EscINF" /></p> |
|:----------------------------------------------------|:-------------------------------------------------------------:|------------------------------------------------------------:|

**Programa de curso** · **Programación I** · **C++**
**Carrera:** Ingeniería de Sistemas de Información con grado en Bachillerato y salida lateral de Diplomado en Programación de Aplicaciones Informáticas.

**Lenguaje del curso:** EIF-201 desarrolla **todas** las soluciones en **C++** (compilación con `g++ -std=c++11 -Wall`). Use archivos `.h` / `.cpp` cuando el diseño lo requiera, `using namespace std;` en ejemplos de clase, y buenas prácticas del estándar C++.

---


# Semana 1 – Sesión 1 (Estudiantes) · Clase 1

**Material del profesor:** [Sesion_01_s1.md](Sesion_01_s1.md)

**Duración:** 1 hora y 30 minutos
**Fecha aproximada:** 20/07/26 – 26/07/26 (Lunes o Martes)
**Tema:** Paradigmas de programación: programación estructurada vs orientada a objetos

---

## Objetivo de la sesión

Distinguir el paradigma estructurado del orientado a objetos, identificar ventajas del modelado por entidades y preparar el vocabulario académico del curso (clase, objeto, mensaje, estado).

## Explicación (resumen)

- La Programación Orientada a Objetos (POO) surge como respuesta a la complejidad creciente del software.
- Mientras la programación estructurada organiza la solución en funciones y procedimientos que operan sobre datos separados, la POO integra datos y comportamiento en una unidad coherente llamada **objeto**.
- Un objeto es una instancia concreta de una **clase**, que actúa como plantilla o molde: define atributos (estado) y métodos (comportamiento).
- El paradigma estructurado —heredero del modelo de Von Neumann— privilegia la descomposición funcional: se identifican las tareas y se implementan como funciones.

---

## Espacio para tu código

### Ejercicio 1

Diseñe e implemente en C++ un sistema de venta de boletos de cine con al menos cinco clases (`Pelicula`, `Sala`, `Funcion`, `Cliente`, `Boleto` u otras justificadas).

**Requisitos:** Archivos `.h` y `.cpp` por clase (o agrupación razonable), `main.cpp`, `using namespace std;`.
**Restricciones:** Sin herencia ni punteros dinámicos aún; objetos automáticos en `main`.

```cpp
// Su solución aquí — use using namespace std;
```

### Ejercicio 2

Convierta a C++ un programa estructurado con función `calcularPromedio(int arr[], int n)` usando la clase `ConjuntoNotas` que encapsule el arreglo y el cálculo.

**Requisitos:** Clase en `.h`/`.cpp`, `main.cpp` de prueba, `g++ -std=c++11 -Wall`.
**Restricciones:** Arreglo fijo máximo 30 elementos, atributos privados.

```cpp
// Su solución aquí
```

### Ejercicio 3

Reemplace una variable global `contadorClientes` por la clase C++ `RegistroClientes` con métodos para registrar y consultar el total.

**Requisitos:** Implementación completa en C++ con encapsulamiento (`private`).
**Restricciones:** Prohibido usar variables globales de conteo.

```cpp
// Su solución aquí
```

---

## Tarea de la sesión

Leer Joyanes cap. introductorio y Deitel sección de clases en C++. Implementar en C++ un ejemplo propio que contraste enfoque estructurado vs OO; documentar en MD con código fuente y salida de `g++`.

## Ejercicios adicionales (nivel alto · C++)

Resuelva en estudio independiente los ejercicios 4 al 10 en [Sesion_01_s1.md](Sesion_01_s1.md). **Todos requieren implementación en C++** salvo indicación de repaso escrito.

---

## Criterios de validación (para el profesor)

- [ ] Uso de `using namespace std;` cuando corresponda
- [ ] Encapsulamiento y nombres significativos
- [ ] Código compila sin errores ni warnings evitables
- [ ] Documentación MD con diseño, pruebas y conclusiones
- [ ] Sin fugas de memoria (si aplica a esta sesión)
