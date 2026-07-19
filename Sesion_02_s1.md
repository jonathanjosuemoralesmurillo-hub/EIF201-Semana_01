| <div align="right"><img src="../Logo-UNA-Rojo_FondoTransparente%20(2).png" width="120" alt="Logo UNA" /></div> | | <p align="right"><img src="../images.jpeg" width="120" alt="Logo EscINF" /></p> |
|:----------------------------------------------------|:-------------------------------------------------------------:|------------------------------------------------------------:|

**Programa de curso** · **Programación I** · **C++**
**Carrera:** Ingeniería de Sistemas de Información con grado en Bachillerato y salida lateral de Diplomado en Programación de Aplicaciones Informáticas.

**Lenguaje del curso:** EIF-201 desarrolla **todas** las soluciones en **C++** (compilación con `g++ -std=c++11 -Wall`). Use archivos `.h` / `.cpp` cuando el diseño lo requiera, `using namespace std;` en ejemplos de clase, y buenas prácticas del estándar C++.

---

CLASE #: 2
SEMANA: 1
FECHA APROXIMADA: 20/07/26 – 26/07/26 (Miércoles o Jueves)
TEMA PRINCIPAL: Clases, encapsulamiento, abstracción y ocultamiento de información
DURACIÓN: 1 hora y 30 minutos

---

## 1. Objetivo de la clase

Aplicar especificadores de acceso (private, public, protected), diseñar interfaces públicas mínimas y comprender la abstracción como filtro de complejidad.

## 2. Conocimientos previos necesarios

Clase 1: paradigma OO, distinción clase/objeto, sintaxis básica de class en C++.

## 3. Explicación teórica de la clase

El **encapsulamiento** es el mecanismo mediante el cual una clase agrupa datos y funciones que operan sobre esos datos, controlando el acceso externo mediante especificadores `public`, `private` y `protected`. Los atributos deben declararse típicamente como `private` para garantizar que ningún código externo modifique el estado de forma inconsistente. La interfaz pública —métodos `public`— constituye el **contrato** del objeto: define qué puede hacer el mundo exterior sin revelar cómo lo hace internamente.

La **abstracción** complementa el encapsulamiento: al diseñar una clase, se seleccionan solo los atributos y operaciones relevantes para el problema. Un objeto `Automovil` en un sistema de renta no necesita modelar el torque del motor; incluirlo sería ruido conceptual. La abstracción reduce la carga cognitiva y permite razonar sobre el sistema a nivel de responsabilidades, no de bits.

El **ocultamiento de información** (information hiding), formulado por Parnas, establece que los detalles de implementación deben permanecer ocultos y sujetos a cambio sin afectar a los clientes de la clase. Si `CuentaBancaria` almacena el saldo como `double` o como `long` centavos es irrelevante para quien llama a `depositar()`. Cambiar la representación interna no debe romper el código cliente si la interfaz pública se mantiene.

En C++, violar el encapsulamiento declarando todo `public` es un error común que expone el programa a estados inválidos: saldos negativos no controlados, índices fuera de rango asignados directamente. Los **métodos de acceso** (getters y setters) permiten validación en la escritura: un `setEdad(int e)` puede rechazar valores negativos. Sin embargo, el abuso de getters/setters para todos los campos —sin lógica— produce clases anémicas que no aportan comportamiento.

Las buenas prácticas incluyen: interfaz pública mínima (principio de menor privilegio), métodos `const` cuando no modifican estado, inicialización de atributos en constructores (próxima sesión) y nombres que expresen intención. La sección `protected` se reserva para herencia (semana 9): permite acceso a clases derivadas manteniendo ocultamiento respecto al exterior.

**Referencia (APA):** (Deitel & Deitel, 2016; Joyanes, 1996). Encapsulamiento y especificadores de acceso; diseño de interfaces de clase.

El encapsulamiento no es un capricho sintáctico de C++, sino una respuesta directa al principio de ocultamiento de información de Parnas: los detalles que pueden cambiar deben quedar atrapados detrás de una interfaz estable. Cuando una clase expone sus campos, cualquier módulo cliente puede dejarla en un estado inválido; por ejemplo, asignar una capacidad negativa a un contenedor o una fecha imposible a un evento. Los métodos públicos deben expresar operaciones significativas del dominio (`matricular`, `depositar`, `cancelar`) en lugar de simples mutadores genéricos sin regla de negocio. En la práctica académica se exige que el estudiante justifique cada miembro público: si no hay razón semántica para exponerlo, debe ser privado. Los métodos `const` comunican al lector que una consulta no altera el estado observable del objeto, lo cual facilita razonar sobre invariantes y usar objetos en contextos de solo lectura. También es importante distinguir abstracción de simplificación excesiva: abstraer no es omitir atributos relevantes, sino omitir los irrelevantes para el problema actual. Finalmente, la separación en archivos `.h` y `.cpp` refuerza el encapsulamiento físico: el header declara el contrato; la implementación permanece oculta al compilador de los clientes.

## 4. Ejemplo guiado en C++

```cpp
// CuentaBancaria.h
#ifndef CUENTA_BANCARIA_H
#define CUENTA_BANCARIA_H
#include <string>
using namespace std;

class CuentaBancaria {
    string titular;   // oculto
    double saldo;     // oculto
public:
    CuentaBancaria(const string& t, double s);
    void depositar(double monto);
    bool retirar(double monto);
    double consultarSaldo() const;
    string obtenerTitular() const;
};
#endif

// CuentaBancaria.cpp
#include "CuentaBancaria.h"
#include <iostream>
using namespace std;

CuentaBancaria::CuentaBancaria(const string& t, double s)
    : titular(t), saldo(s >= 0 ? s : 0) {}

void CuentaBancaria::depositar(double monto) {
    if (monto > 0) saldo += monto;
}

bool CuentaBancaria::retirar(double monto) {
    if (monto > 0 && monto <= saldo) { saldo -= monto; return true; }
    return false;
}

double CuentaBancaria::consultarSaldo() const { return saldo; }
string CuentaBancaria::obtenerTitular() const { return titular; }

// main.cpp
#include "CuentaBancaria.h"
using namespace std;

int main() {
    CuentaBancaria c("Ana Perez", 1000.0);
    c.depositar(500.0);
    cout << c.obtenerTitular() << ": " << c.consultarSaldo() << endl;
    // c.saldo = -999; // ERROR: saldo es private
    return 0;
}
```

## 5. Actividad práctica guiada en clase

**Profesor:** Demuestra en vivo qué ocurre al intentar acceder a miembro private desde main. Guía diseño de clase `Termometro` con validación de temperatura.

**Estudiante:** Implementan `Termometro` con atributo privado y métodos publicos; prueban valores inválidos y discuten qué quedó oculto.

## 6. Cierre de la clase

Encapsulamiento = datos privados + interfaz pública controlada. Abstracción = modelar lo esencial. Próxima semana: constructores y práctica intensiva.

## 7. Tarea o práctica sugerida

Completar clase `CuentaBancaria` con método `mostrarEstado()` y documentar en MD la interfaz pública vs implementación.

## 8. Diez ejercicios de nivel alto

> **C++ obligatorio:** salvo clases de repaso escrito (14, 24, 32), cada ejercicio exige **diseño de clases e implementación en C++** compilable. Documente en MD el análisis y adjunte el código fuente.

### Ejercicio 1

**Enunciado:** Diseñe e implemente clase `Estudiante` con carné, nombre y promedio; el promedio solo se modifica mediante `agregarNota()`.

**Requisitos técnicos:** Archivos .h y .cpp.

**Restricciones:** Promedio entre 0 y 100; carné no vacío.

**Criterios de evaluación:** Encapsulamiento, validación, const en consultas.

**Resultado esperado:** Objeto que rechace notas inválidas.

**Sugerencia opcional:** Mantenga suma y cantidad internamente para eficiencia.

### Ejercicio 2

**Enunciado:** Refactorice clase con atributos publicos a diseño encapsulado sin cambiar comportamiento observable.

**Requisitos técnicos:** Código antes/después en MD. **Implementación obligatoria en C++** (`.cpp` / `.h` según diseño), compilable con `g++ -std=c++11 -Wall`.

**Restricciones:** Misma salida en main.

**Criterios de evaluación:** Preservación funcional, mejora de diseño.

**Resultado esperado:** Versión con private y métodos de acceso.

**Sugerencia opcional:** Identifique invariantes que debe proteger.

### Ejercicio 3

**Enunciado:** Implemente `Fecha` con día, mes, año privados y método `esValida()`; constructor rechaza fechas inválidas.

**Requisitos técnicos:** Un .cpp o .h/.cpp.

**Restricciones:** Considerar meses 1-12 y días por mes.

**Criterios de evaluación:** Validación completa.

**Resultado esperado:** No se crean fechas inválidas.

**Sugerencia opcional:** Febrero: 28 días (sin bisiesto).

### Ejercicio 4

**Enunciado:** Explique por qué exponer un arreglo interno como public es peligroso; proponga alternativa con métodos.

**Requisitos técnicos:** Ensayo 250 palabras + ejemplo código. **Implementación obligatoria en C++** (`.cpp` / `.h` según diseño), compilable con `g++ -std=c++11 -Wall`.

**Restricciones:** Sin STL avanzada.

**Criterios de evaluación:** Argumentación técnica.

**Resultado esperado:** Texto con ejemplo de corrupción de datos.

**Sugerencia opcional:** Anticipe arreglos en semana 5.

### Ejercicio 5

**Enunciado:** Clase `InventarioProducto` con cantidad privada; operaciones `ingresar`, `egresar`, `nivelBajo()`.

**Requisitos técnicos:** .h/.cpp.

**Restricciones:** Cantidad nunca negativa.

**Criterios de evaluación:** Invariantes respetadas.

**Resultado esperado:** Simulación de movimientos en main.

**Sugerencia opcional:** Umbral de nivel bajo configurable en constructor.

### Ejercicio 6

**Enunciado:** Diseñe interfaz mínima para `Biblioteca` que preste libros sin revelar estructura de almacenamiento.

**Requisitos técnicos:** Solo declaración de clase en .h (sin implementar almacenamiento).

**Restricciones:** Mínimo 4 métodos públicos.

**Criterios de evaluación:** Abstracción de la representación.

**Resultado esperado:** Header con contrato claro.

**Sugerencia opcional:** Pregunte: ¿qué debe saber el usuario de la clase?

### Ejercicio 7

**Enunciado:** Implemente `Contrasena` que almacene texto de forma que main no pueda leerla directamente; solo `esCorrecta(string)`.

**Requisitos técnicos:** Clase con atributo string privado.

**Restricciones:** No mostrar contraseña en pantalla.

**Criterios de evaluación:** Ocultamiento real.

**Resultado esperado:** Comparación funcional sin exposición.

**Sugerencia opcional:** No usar hash aún; string simple.

### Ejercicio 8

**Enunciado:** Analice violaciones de encapsulamiento en código dado y proponga correcciones.

**Requisitos técnicos:** Informe MD. **Implementación obligatoria en C++** (`.cpp` / `.h` según diseño), compilable con `g++ -std=c++11 -Wall`.

**Restricciones:** Al menos 5 violaciones.

**Criterios de evaluación:** Diagnóstico preciso.

**Resultado esperado:** Lista corregida con justificación.

**Sugerencia opcional:** Clasifique: acceso directo, interfaz hinchada, datos expuestos.

### Ejercicio 9

**Enunciado:** Clase `Circulo` con radio privado; métodos `setRadio`, `getArea`, `getPerimetro` con validación.

**Requisitos técnicos:** const en métodos de consulta. **Implementación obligatoria en C++** (`.cpp` / `.h` según diseño), compilable con `g++ -std=c++11 -Wall`.

**Restricciones:** Radio > 0.

**Criterios de evaluación:** Uso de PI, métodos const.

**Resultado esperado:** Cálculos correctos.

**Sugerencia opcional:** Use `<cmath>` para M_PI o constante propia.

### Ejercicio 10

**Enunciado:** Documente en MD la interfaz pública de tres clases del dominio universitario siguiendo principio de menor privilegio.

**Requisitos técnicos:** Tabla: método | público/privado | justificación. **Implementación obligatoria en C++** (`.cpp` / `.h` según diseño), compilable con `g++ -std=c++11 -Wall`.

**Restricciones:** Tres clases distintas.

**Criterios de evaluación:** Criterio de diseño explícito.

**Resultado esperado:** Documentación revisable por pares.

**Sugerencia opcional:** Evite métodos get para todo; prefiera comportamiento.


## 9. Errores comunes esperados

- Todo public por comodidad.
- Setters sin validación.
- Getters para cada campo sin necesidad.
- Confundir abstracción con simplificación excesiva del dominio.

## 10. Recomendaciones para el profesor

Insista en compilar código que viola private para que el error sea memorable. Use .h/.cpp para acostumbrar modularización.

---

**Formato de entrega:** Código y documentación en archivos **MD (Markdown)** según política del curso.
