# Console Gym Challenge

Es un proyecto de deportistas para deportistas, con el fin de ayudar a llevar el control de rangos en el gimnasio.

## Índice

1. [Descripción del proyecto](#1-descripción-del-proyecto)
2. [Objetivos](#2-objetivos)
3. [Funcionamiento general](#3-funcionamiento-general)
4. [Datos del deportista e IMC](#4-datos-del-deportista-e-imc)
5. [Estructura del programa](#5-estructura-del-programa)
6. [Sistema de rangos](#6-sistema-de-rangos)
7. [Ejercicios y niveles por ejercicio](#7-ejercicios-y-niveles-por-ejercicio)
8. [Cálculo del rendimiento general](#8-cálculo-del-rendimiento-general)
9. [Progreso hacia el siguiente rango](#9-progreso-hacia-el-siguiente-rango)
10. [Registro de rendimiento](#10-registro-de-rendimiento)
11. [Reglas del sistema](#11-reglas-del-sistema)
12. [Flujo básico del programa](#12-flujo-básico-del-programa)
13. [Ejemplo de funcionamiento](#13-ejemplo-de-funcionamiento)
14. [Tecnologías](#14-tecnologías)
15. [Resultado esperado](#15-resultado-esperado)

---

## 1. Descripción del proyecto

Console Gym Challenge es un proyecto de programación que busca desarrollar un sistema de control deportivo mediante consola.

El sistema permitirá registrar deportistas, almacenar sus datos físicos (género, peso, estatura e IMC), registrar sus resultados en distintos ejercicios del gimnasio, evaluar su rendimiento y clasificarlos en diferentes rangos o niveles.

El objetivo principal es que cada deportista pueda conocer su estado actual, consultar su progreso y saber cuánto necesita mejorar para alcanzar el siguiente nivel.

## 2. Objetivos

- Registrar nuevos deportistas con sus datos básicos y físicos (género, peso y estatura).
- Calcular y clasificar automáticamente el Índice de Masa Corporal (IMC).
- Guardar y consultar la información de cada deportista.
- Registrar los resultados obtenidos en diferentes ejercicios (sentadilla, flexiones, press de pecho, etc.).
- Asignar un nivel a cada ejercicio según el resultado y el género del deportista.
- Calcular el rendimiento general de cada deportista.
- Asignar un rango dependiendo del rendimiento obtenido.
- Mostrar el progreso del deportista.
- Indicar cuánto le falta para alcanzar el siguiente rango.
- Permitir consultar, actualizar y eliminar información.

## 3. Funcionamiento general

El programa funcionará mediante un menú en consola.

El usuario podrá seleccionar diferentes opciones, por ejemplo:

```
===== CONSOLE GYM CHALLENGE =====

1. Registrar deportista
2. Registrar ejercicio
3. Registrar rendimiento
4. Consultar deportista
5. Mostrar clasificación
6. Actualizar información
7. Eliminar deportista
8. Salir

Seleccione una opción:
```

Dependiendo de la opción seleccionada, el sistema realizará la operación correspondiente.

## 4. Datos del deportista e IMC

### 4.1 Datos que se registran

Al registrar un deportista se le pedirán estos datos:

| Dato | Descripción | Ejemplo |
|------|-------------|---------|
| Nombre | Nombre del deportista (obligatorio) | Carlos |
| Edad | Edad en años | 20 |
| Género | Hombre o Mujer | Hombre |
| Peso | Peso corporal en kilogramos (kg) | 70 |
| Estatura | Estatura en metros (m) | 1.75 |
| Deporte | Disciplina que practica | Voleibol |

El género es importante porque los niveles de los ejercicios son distintos para hombres y mujeres (ver sección 7). El peso también se usa para calcular el nivel en los ejercicios con carga.

### 4.2 Índice de Masa Corporal (IMC)

El IMC se calcula automáticamente con el peso y la estatura:

```
IMC = peso (kg) / estatura (m) ²
```

Ejemplo: una persona de 70 kg y 1.75 m

```
IMC = 70 / (1.75 × 1.75) = 70 / 3.0625 = 22.86
```

Clasificación del IMC (según la OMS):

| IMC | Clasificación |
|-----|---------------|
| Menor a 18.5 | Bajo peso |
| 18.5 - 24.9 | Peso normal |
| 25.0 - 29.9 | Sobrepeso |
| 30.0 o más | Obesidad |

> El IMC es solo un dato informativo. No mide la masa muscular, por lo que un deportista con mucho músculo puede salir con sobrepeso. **No influye en el rango del deportista.**

## 5. Estructura del programa

Para organizar el proyecto se recomienda utilizar programación orientada a objetos.

### Clase Deportista

Esta clase representará a cada persona registrada en el sistema.

**Atributos sugeridos**

- `id`: identificador único del deportista.
- `nombre`: nombre del deportista.
- `edad`: edad del deportista.
- `genero`: "Hombre" o "Mujer".
- `peso`: peso corporal en kg.
- `estatura`: estatura en metros.
- `imc`: índice de masa corporal (se calcula solo).
- `deporte`: disciplina deportiva que practica.
- `ejercicios`: diccionario con el resultado de cada ejercicio (ejemplo: `{"Sentadilla": 90, "Flexiones": 25}`).
- `rendimiento`: puntuación general actual (0 a 100).
- `rango`: nivel actual del deportista.

**Métodos sugeridos**

- `calcular_imc()`: calcula el IMC con el peso y la estatura.
- `clasificar_imc()`: indica si está en bajo peso, normal, sobrepeso u obesidad.
- `registrar_ejercicio()`: guarda el resultado de un ejercicio.
- `calcular_nivel_ejercicio()`: determina el nivel de un ejercicio según el resultado, el género y el peso.
- `calcular_rendimiento()`: calcula el rendimiento general a partir de los ejercicios.
- `mostrar_informacion()`: muestra los datos del deportista.
- `actualizar_rendimiento()`: permite modificar su rendimiento.
- `calcular_rango()`: determina el rango según su rendimiento.
- `progreso_siguiente_rango()`: calcula cuánto necesita mejorar para alcanzar el siguiente nivel.

### Clase SistemaGym

Esta clase se encargará de administrar todos los deportistas registrados.

**Atributos sugeridos**

- `deportistas`: colección donde se almacenarán los deportistas.

**Métodos sugeridos**

- `registrar_deportista()`
- `buscar_deportista()`
- `actualizar_deportista()`
- `eliminar_deportista()`
- `mostrar_deportistas()`
- `mostrar_clasificacion()`

Esta clase será la encargada de controlar las operaciones principales del sistema.

## 6. Sistema de rangos

Los deportistas serán clasificados dependiendo de su rendimiento general (0 a 100).

| Rendimiento | Rango |
|-------------|-------|
| 0 - 49 | Principiante |
| 50 - 69 | Básico |
| 70 - 84 | Intermedio |
| 85 - 94 | Avanzado |
| 95 - 100 | Élite |

Estos valores pueden modificarse dependiendo de las reglas definidas para el proyecto.

## 7. Ejercicios y niveles por ejercicio

Cada ejercicio tiene su propia tabla de niveles. Los niveles son los mismos del sistema de rangos: **Principiante, Básico, Intermedio, Avanzado y Élite.**

Hay dos tipos de ejercicios:

- **Ejercicios con carga (pesas y máquinas):** se registra el peso máximo que el deportista puede levantar en **1 repetición**, en kg. El nivel depende de cuántas veces su peso corporal levanta (`peso levantado / peso corporal`). Así un deportista pequeño y uno grande se comparan de forma justa.
- **Ejercicios de peso corporal:** se registra el número de repeticiones (o los segundos, en el caso de la plancha) que logra el deportista.

Como los hombres y las mujeres tienen capacidades distintas, cada tabla tiene sus valores por género.

> Los valores de las tablas son una referencia y pueden ajustarse según las reglas del proyecto.

### 7.1 Ejercicios con carga

**Valor que se compara:** `peso levantado (1 repetición) / peso corporal`

Ejemplo: un hombre de 70 kg que hace sentadilla con 105 kg → 105 / 70 = 1.5 → nivel **Avanzado** (ver tabla).

#### Sentadilla

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | menos de 0.75 | menos de 0.50 |
| Básico | 0.75 - 0.99 | 0.50 - 0.74 |
| Intermedio | 1.00 - 1.49 | 0.75 - 1.24 |
| Avanzado | 1.50 - 1.99 | 1.25 - 1.74 |
| Élite | 2.00 o más | 1.75 o más |

#### Cargas en pecho (press de banca)

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | menos de 0.50 | menos de 0.25 |
| Básico | 0.50 - 0.74 | 0.25 - 0.49 |
| Intermedio | 0.75 - 0.99 | 0.50 - 0.74 |
| Avanzado | 1.00 - 1.49 | 0.75 - 0.99 |
| Élite | 1.50 o más | 1.00 o más |

#### Cargas en espalda (remo con barra)

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | menos de 0.50 | menos de 0.30 |
| Básico | 0.50 - 0.74 | 0.30 - 0.49 |
| Intermedio | 0.75 - 0.99 | 0.50 - 0.74 |
| Avanzado | 1.00 - 1.24 | 0.75 - 0.99 |
| Élite | 1.25 o más | 1.00 o más |

#### Extensión de cuádriceps (máquina)

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | menos de 0.40 | menos de 0.25 |
| Básico | 0.40 - 0.69 | 0.25 - 0.49 |
| Intermedio | 0.70 - 0.99 | 0.50 - 0.74 |
| Avanzado | 1.00 - 1.39 | 0.75 - 1.09 |
| Élite | 1.40 o más | 1.10 o más |

#### Peso muerto

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | menos de 1.00 | menos de 0.75 |
| Básico | 1.00 - 1.49 | 0.75 - 1.24 |
| Intermedio | 1.50 - 1.99 | 1.25 - 1.74 |
| Avanzado | 2.00 - 2.49 | 1.75 - 2.24 |
| Élite | 2.50 o más | 2.25 o más |

#### Press militar (hombros)

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | menos de 0.35 | menos de 0.20 |
| Básico | 0.35 - 0.54 | 0.20 - 0.34 |
| Intermedio | 0.55 - 0.79 | 0.35 - 0.54 |
| Avanzado | 0.80 - 1.09 | 0.55 - 0.79 |
| Élite | 1.10 o más | 0.80 o más |

#### Curl de bíceps (barra)

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | menos de 0.20 | menos de 0.10 |
| Básico | 0.20 - 0.39 | 0.10 - 0.24 |
| Intermedio | 0.40 - 0.59 | 0.25 - 0.39 |
| Avanzado | 0.60 - 0.79 | 0.40 - 0.59 |
| Élite | 0.80 o más | 0.60 o más |

### 7.2 Ejercicios de peso corporal

**Valor que se compara:** número de repeticiones en 1 minuto (la plancha se mide en segundos que logra mantener la posición).

#### Flexiones (repeticiones en 1 minuto)

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | menos de 10 | menos de 5 |
| Básico | 10 - 19 | 5 - 11 |
| Intermedio | 20 - 34 | 12 - 24 |
| Avanzado | 35 - 49 | 25 - 39 |
| Élite | 50 o más | 40 o más |

#### Abdominales (repeticiones en 1 minuto)

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | menos de 20 | menos de 15 |
| Básico | 20 - 29 | 15 - 24 |
| Intermedio | 30 - 39 | 25 - 34 |
| Avanzado | 40 - 49 | 35 - 44 |
| Élite | 50 o más | 45 o más |

#### Dominadas (repeticiones seguidas)

| Nivel | Hombre | Mujer |
|-------|--------|-------|
| Principiante | 0 | 0 |
| Básico | 1 - 4 | 1 - 2 |
| Intermedio | 5 - 9 | 3 - 5 |
| Avanzado | 10 - 14 | 6 - 9 |
| Élite | 15 o más | 10 o más |

#### Plancha (segundos)

| Nivel | Hombre y Mujer |
|-------|----------------|
| Principiante | menos de 30 s |
| Básico | 30 - 59 s |
| Intermedio | 60 - 89 s |
| Avanzado | 90 - 179 s |
| Élite | 180 s o más |

## 8. Cálculo del rendimiento general

El rendimiento general (0 a 100) se calcula a partir de los niveles de todos los ejercicios que el deportista haya registrado.

**Paso 1.** Cada nivel de ejercicio vale una cantidad de puntos (corresponde al punto medio de cada rango de la sección 6):

| Nivel del ejercicio | Puntos |
|---------------------|--------|
| Principiante | 25 |
| Básico | 60 |
| Intermedio | 77 |
| Avanzado | 90 |
| Élite | 98 |

**Paso 2.** El rendimiento general es el promedio de los puntos de todos los ejercicios registrados.

**Paso 3.** Con ese rendimiento se calcula el rango del deportista (tabla de la sección 6).

Ejemplo:

| Ejercicio | Nivel | Puntos |
|-----------|-------|--------|
| Sentadilla | Avanzado | 90 |
| Flexiones | Intermedio | 77 |
| Abdominales | Básico | 60 |

```
Rendimiento = (90 + 77 + 60) / 3 = 75.67  →  76
Rango = Intermedio
```

## 9. Progreso hacia el siguiente rango

El sistema deberá identificar el siguiente rango que puede alcanzar el deportista.

Por ejemplo:

```
Deportista: Juan
Rendimiento actual: 72
Rango: Intermedio

Siguiente rango: Avanzado
Rendimiento necesario: 85

Te faltan: 13 puntos
```

Si el deportista ya se encuentra en el rango máximo, el sistema deberá indicar que ha alcanzado el nivel más alto.

## 10. Registro de rendimiento

El sistema deberá permitir registrar o actualizar el rendimiento de un deportista de dos formas:

1. **Por ejercicio (recomendado):** se registra el resultado de un ejercicio y el sistema calcula el nivel del ejercicio, el rendimiento general y el rango.
2. **Manual:** se escribe directamente una puntuación entre 0 y 100.

Ejemplo por ejercicio:

```
Ingrese el ID del deportista: 001
Ejercicio: Sentadilla
Peso levantado (kg): 105

Nivel en Sentadilla: Avanzado
Rendimiento general: 76
Rango actual: Intermedio
```

Ejemplo manual:

```
Ingrese el ID del deportista: 001
Ingrese el nuevo rendimiento: 87

Rendimiento actualizado correctamente.
Rango actual: Avanzado
```

El programa deberá validar que los datos ingresados sean correctos (la puntuación entre 0 y 100, y los pesos y repeticiones mayores o iguales a 0).

## 11. Reglas del sistema

El programa deberá cumplir las siguientes reglas:

1. Cada deportista debe tener un identificador único.
2. No se deben registrar dos deportistas con el mismo identificador.
3. El nombre del deportista es obligatorio.
4. La edad debe ser un valor válido.
5. El género debe ser "Hombre" o "Mujer".
6. El peso y la estatura deben ser números mayores que 0.
7. El IMC debe calcularse automáticamente con el peso y la estatura.
8. El resultado de un ejercicio no puede ser negativo.
9. El nivel de cada ejercicio debe calcularse según el género del deportista.
10. El rendimiento debe estar entre 0 y 100.
11. El rango debe calcularse automáticamente según el rendimiento.
12. El usuario debe poder consultar la información de un deportista.
13. El usuario debe poder actualizar el rendimiento y los ejercicios.
14. El sistema debe indicar el progreso necesario para alcanzar el siguiente rango.
15. El programa debe controlar las opciones incorrectas del menú.

## 12. Flujo básico del programa

```
INICIO
  ↓
Mostrar menú
  ↓
Seleccionar opción
  ↓
¿Registrar deportista?
  ↓
Guardar información (nombre, edad, género, peso, estatura, deporte)
  ↓
Calcular IMC
  ↓
¿Registrar ejercicio / rendimiento?
  ↓
Calcular nivel del ejercicio
  ↓
Calcular rendimiento general
  ↓
Calcular rango
  ↓
Calcular progreso
  ↓
Mostrar resultado
  ↓
Volver al menú
  ↓
¿Salir?
  ↓
FIN
```

## 13. Ejemplo de funcionamiento

```
===== CONSOLE GYM CHALLENGE =====

1. Registrar deportista
2. Registrar ejercicio
3. Registrar rendimiento
4. Consultar deportista
5. Mostrar clasificación
6. Actualizar información
7. Eliminar deportista
8. Salir

Seleccione una opción: 1

Nombre: Carlos
Edad: 20
Género (Hombre/Mujer): Hombre
Peso (kg): 70
Estatura (m): 1.75
Deporte: Voleibol

Deportista registrado correctamente.
ID asignado: 001
IMC: 22.86 (Peso normal)
```

Posteriormente:

```
Seleccione una opción: 2

ID del deportista: 001
Ejercicio: Flexiones
Repeticiones en 1 minuto: 25

Nivel en Flexiones: Intermedio

Seleccione una opción: 2

ID del deportista: 001
Ejercicio: Sentadilla
Peso levantado (kg): 105

Nivel en Sentadilla: Avanzado

Rendimiento general: 84
Rango actual: Intermedio
Siguiente rango: Avanzado
Te falta 1 punto para alcanzar el siguiente rango.
```

## 14. Tecnologías

El proyecto será desarrollado utilizando:

- Python
- Programación Orientada a Objetos (POO)
- Aplicación de consola
- Estructuras de datos para almacenar los deportistas (listas y diccionarios)

## 15. Resultado esperado

Al finalizar el proyecto, se espera tener un programa funcional que permita administrar deportistas desde la consola, registrar sus datos físicos y sus resultados en distintos ejercicios, calcular su IMC, clasificarlos automáticamente por nivel y rango, y realizar un seguimiento de su progreso.
