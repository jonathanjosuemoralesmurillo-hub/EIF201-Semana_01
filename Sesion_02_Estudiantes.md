| <div align="right"><img src="../Logo-UNA-Rojo_FondoTransparente%20(2).png" width="120" alt="Logo UNA" /></div> | | <p align="right"><img src="../images.jpeg" width="120" alt="Logo EscINF" /></p> |
|:----------------------------------------------------|:-------------------------------------------------------------:|------------------------------------------------------------:|

**Programa de curso** · **Programación I** · **C++**
**Carrera:** Ingeniería de Sistemas de Información con grado en Bachillerato y salida lateral de Diplomado en Programación de Aplicaciones Informáticas.

**Lenguaje del curso:** EIF-201 desarrolla **todas** las soluciones en **C++** (compilación con `g++ -std=c++11 -Wall`). Use archivos `.h` / `.cpp` cuando el diseño lo requiera, `using namespace std;` en ejemplos de clase, y buenas prácticas del estándar C++.

---


# Semana 1 – Sesión 2 (Estudiantes) · Clase 2

**Material del profesor:** [Sesion_02_s1.md](Sesion_02_s1.md)

**Duración:** 1 hora y 30 minutos
**Fecha aproximada:** 20/07/26 – 26/07/26 (Miércoles o Jueves)
**Tema:** Clases, encapsulamiento, abstracción y ocultamiento de información

---

## Objetivo de la sesión

Aplicar especificadores de acceso (private, public, protected), diseñar interfaces públicas mínimas y comprender la abstracción como filtro de complejidad.

## Explicación (resumen)

- El **encapsulamiento** es el mecanismo mediante el cual una clase agrupa datos y funciones que operan sobre esos datos, controlando el acceso externo mediante especificadores `public`, `private` y `protected`.
- Los atributos deben declararse típicamente como `private` para garantizar que ningún código externo modifique el estado de forma inconsistente.
- La interfaz pública —métodos `public`— constituye el **contrato** del objeto: define qué puede hacer el mundo exterior sin revelar cómo lo hace internamente.
- La **abstracción** complementa el encapsulamiento: al diseñar una clase, se seleccionan solo los atributos y operaciones relevantes para el problema.

---

## Espacio para tu código

### Ejercicio 1

Diseñe e implemente clase `Estudiante` con carné, nombre y promedio; el promedio solo se modifica mediante `agregarNota()`.

**Requisitos:** Archivos .h y .cpp.
**Restricciones:** Promedio entre 0 y 100; carné no vacío.

```cpp
// Su solución aquí — use using namespace std;
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
```

### Ejercicio 2

Refactorice clase con atributos publicos a diseño encapsulado sin cambiar comportamiento observable.

**Requisitos:** Código antes/después en MD. **Implementación obligatoria en C++** (`.cpp` / `.h` según diseño), compilable con `g++ -std=c++11 -Wall`.
**Restricciones:** Misma salida en main.

```cpp
// Su solución aquí
```

### Ejercicio 3

Implemente `Fecha` con día, mes, año privados y método `esValida()`; constructor rechaza fechas inválidas.

**Requisitos:** Un .cpp o .h/.cpp.
**Restricciones:** Considerar meses 1-12 y días por mes.

```cpp
// Su solución aquí
```

---

## Tarea de la sesión

Completar clase `CuentaBancaria` con método `mostrarEstado()` y documentar en MD la interfaz pública vs implementación.

## Ejercicios adicionales (nivel alto · C++)

Resuelva en estudio independiente los ejercicios 4 al 10 en [Sesion_02_s1.md](Sesion_02_s1.md). **Todos requieren implementación en C++** salvo indicación de repaso escrito.

---

## Criterios de validación (para el profesor)

- [ ] Uso de `using namespace std;` cuando corresponda
- [ ] Encapsulamiento y nombres significativos
- [ ] Código compila sin errores ni warnings evitables
- [ ] Documentación MD con diseño, pruebas y conclusiones
- [ ] Sin fugas de memoria (si aplica a esta sesión)
