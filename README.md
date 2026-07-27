# EIF-201 — Semana 01

**Curso:** Programación I (C++) · II Ciclo 2026
**Proyecto CLion:** `EIF201_Semana_01`
**Estándar:** C++11 (`g++ -std=c++11 -Wall`)

## Abrir el proyecto en CLion

1. Seleccione **File → Open**.
2. Abra la carpeta `Semana_01`.
3. Confirme la apertura como un proyecto de **CMake**.
4. Ejecute el target `EIF201_Semana_01`.

## Material de la semana

| Orden | Archivo                    | Descripción                                                           |
| :---: | -------------------------- | --------------------------------------------------------------------- |
|   1   | `Sesion_01_Estudiantes.md` | Material correspondiente a la primera sesión de la semana.            |
|   2   | `Sesion_02_Estudiantes.md` | Material correspondiente a la segunda sesión de la semana.            |
|   3   | `Practica_Semanal.md`      | Práctica integradora de los contenidos estudiados durante la semana.  |
|   4   | `Actividad_Guiada.md`      | Actividad para desarrollar con la orientación del docente.            |
|   5   | `Tarea_Moral.md`           | Actividad complementaria para reforzar los aprendizajes de la semana. |

## Orden recomendado de trabajo

Los archivos deben revisarse y desarrollarse en el siguiente orden:

1. `Sesion_01_Estudiantes.md`
2. `Sesion_02_Estudiantes.md`
3. `Practica_Semanal.md`
4. `Actividad_Guiada.md`
5. `Tarea_Moral.md`

> Se recomienda completar cada archivo antes de continuar con el siguiente, ya que las actividades están organizadas de manera progresiva.

## Compilar desde la terminal

```bash
cmake -S . -B cmake-build-debug
cmake --build cmake-build-debug
./cmake-build-debug/EIF201_Semana_01
```
