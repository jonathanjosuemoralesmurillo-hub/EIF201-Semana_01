| <div align="right"><img src="../Logo-UNA-Rojo_FondoTransparente%20(2).png" width="120" alt="Logo UNA" /></div> | | <p align="right"><img src="../images.jpeg" width="120" alt="Logo EscINF" /></p> |
|:----------------------------------------------------|:-------------------------------------------------------------:|------------------------------------------------------------:|

**Programa de curso** · **Programación I** · **C++**
**Carrera:** Ingeniería de Sistemas de Información con grado en Bachillerato y salida lateral de Diplomado en Programación de Aplicaciones Informáticas.

**Lenguaje del curso:** EIF-201 desarrolla **todas** las soluciones en **C++** (compilación con `g++ -std=c++11 -Wall`). Use archivos `.h` / `.cpp` cuando el diseño lo requiera, `using namespace std;` en ejemplos de clase, y buenas prácticas del estándar C++.

---


# Tarea Moral 1 — Cooperativa de Ahorro Comunal «El Progreso»

**Semana:** 1 · **Periodo:** 20/07/26 – 26/07/26  
**Temas evaluados:** Encapsulamiento · Abstracción · Clases y objetos  
**Preparación para:** Examen I y Proyecto I  
**Modalidad:** Práctica formativa **autoevaluada** (no sustituye entregas oficiales del Aula Virtual)

> **Propósito:** Simular la exigencia de un parcial o proyecto integrador. Si su programa pasa **todos** los casos de prueba de esta guía, está en buen camino para las evaluaciones sumativas del curso.

---

## Contexto / Problema

La cooperativa **El Progreso** administra cuentas de ahorro de sus asociados. Cada cuenta tiene un número único, titular y saldo que **nunca** debe quedar negativo ni exponerse públicamente.

Debe modelar el dominio con POO: la clase `CuentaAhorro` protege su estado interno y expone solo operaciones de negocio (`depositar`, `retirar`, `consultarSaldo`, `mostrarResumen`). Un `ControlCooperativa` ofrece menú para abrir cuentas (máximo 8), realizar movimientos y listar cuentas con saldo mayor a un umbral indicado por el usuario.

---

## Requerimientos Técnicos (Restricciones de código)

### Arquitectura (mínimo 4 archivos)
| Archivo | Rol |
|---------|-----|
| `CuentaAhorro.h` / `.cpp` | Entidad de dominio encapsulada |
| `ControlCooperativa.h` / `.cpp` | Menú y arreglo `CuentaAhorro cuentas[8]`, `int cantidad` |
| `main.cpp` | Ejecuta el menú |

### Clase `CuentaAhorro`
- Privados: `string numero`, `string titular`, `double saldo`.
- Constructor valida `numero` no vacío y `saldoInicial >= 0`.
- `bool depositar(double monto)` — retorna `false` si `monto <= 0`.
- `bool retirar(double monto)` — retorna `false` si `monto <= 0` o excede saldo.
- `double consultarSaldo() const`, `void mostrarResumen() const`.
- **Prohibido** atributos públicos.

### Menú
```
===== Cooperativa El Progreso - Tarea Moral 1 =====
(1) Abrir cuenta
(2) Depositar
(3) Retirar
(4) Listar cuentas sobre umbral
(0) Salir
Opcion:
```

### Restricciones
- `g++ -std=c++11 -Wall CuentaAhorro.cpp ControlCooperativa.cpp main.cpp -o cooperativa`
- Sin `try/catch`, sin STL de contenedores.
- Sin `system("cls")`.

**Compilación de referencia:** `g++ -std=c++11 -Wall *.cpp -o programa`

**Prohibido en todas las Tareas Morales:** `try`, `catch`, `throw`; contenedores STL (`vector`, `list`, `map`, etc.); `system("cls")` / `system("clear")`.

---

## Validaciones Obligatorias (Filtros de entrada requeridos)

Implemente **únicamente** con `if`, `while` y/o `do-while`:

| Dato | Regla | Si falla |
|------|-------|----------|
| Opción menú | 0–4 | `Opcion invalida.` |
| Número cuenta | 5–10 caracteres alfanuméricos, único | Repetir lectura |
| Titular | No vacío (`getline`) | `Titular invalido.` |
| Saldo inicial | `>= 0` | `Monto invalido.` |
| Depósito/retiro | `> 0` | `Monto invalido.` |
| Abrir cuenta | `cantidad < 8` | `Limite de cuentas alcanzado.` |
| Retiro | No dejar saldo negativo | `Fondos insuficientes.` |
| Umbral (opc. 4) | `>= 0` | Repetir lectura |

---

## Casos de Prueba (Ejemplos detallados de Entrada / Salida)

> Copie las entradas **tal cual** (una línea por lectura). Compare su salida con la esperada respetando **datos y orden** de listados; mensajes de error pueden variar levemente en mayúsculas si el significado es idéntico.

### Caso 1 — Menú inválido y salida
**Entrada:** `9` `0` → mensaje `Opcion invalida.` y termina sin crash.

### Caso 2 — Apertura y depósito
**Entrada:**
```
1
ACC001
Maria Lopez
500.00
2
ACC001
250.50
4
400
0
```
**Salida esperada (fragmentos):**
```
Cuenta ACC001 abierta. Saldo: 500.00
Deposito exitoso. Nuevo saldo: 750.50
--- Cuentas sobre umbral ---
ACC001 | Maria Lopez | Saldo: 750.50
```

### Caso 3 — Retiro rechazado
Con saldo 750.50, retirar `800` → `Fondos insuficientes.` Saldo sin cambios.

### Caso 4 — Número duplicado
Abrir `ACC001` otra vez → `Numero de cuenta ya existe.`

---

## Pistas para el Éxito

**Evalúa:** encapsulamiento real (invariante saldo ≥ 0), no un `main` con variables sueltas.
**Cuidado:** no implemente `retirar` accediendo al saldo desde fuera; use métodos. Compare con proyectos tipo clínica/cine: la clase es dueña de sus datos.

### Checklist de autoevaluación

- [ ] Compila con `-Wall` sin warnings evitables
- [ ] Todos los casos de prueba de esta guía pasan
- [ ] Código modular en `.h` / `.cpp` (salvo semana 17 parte B, ≤200 líneas de lógica)
- [ ] Validación de entradas sin excepciones
- [ ] Sin fugas de memoria cuando aplica (`delete` / `delete[]` emparejados)
- [ ] Diagrama o traza de memoria en MD cuando el enunciado lo sugiera

---

**Material de referencia del curso:** carpeta `Examenes/` y `proyectos/` en `EIF201_Lecciones/`.  
**Sesiones de la semana:** [Sesion_01_s1.md](Sesion_01_s1.md) · [Sesion_02_s1.md](Sesion_02_s1.md) · [Practica_Semanal.md](Practica_Semanal.md)
