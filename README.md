# EIF-201 — Semana_01

**Curso:** Programación I (C++) · II Ciclo 2026  
**Proyecto CLion:** `EIF201_Semana_01`  
**Estándar:** C++11 (`g++ -std=c++11 -Wall`)

## Abrir en CLion

1. **File → Open** y seleccione esta carpeta (`Semana_01`).
2. Confirme como proyecto CMake.
3. Ejecute el target `EIF201_Semana_01`.

## Material de la semana

| Archivo | Descripción |
|---------|-------------|
| `Sesion_01_s1.md` / `Sesion_02_s1.md` | Sesiones completas |
| `Sesion_01_Estudiantes.md` / `Sesion_02_Estudiantes.md` | Versión estudiante |
| `Practica_Semanal.md` | Práctica integradora |
| `Tarea_Moral.md` | Tarea moral |

## Compilar en terminal

```bash
cmake -S . -B cmake-build-debug
cmake --build cmake-build-debug
./cmake-build-debug/EIF201_Semana_01
```
