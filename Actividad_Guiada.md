
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