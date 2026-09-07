# Console-Gym-Challenge
Es un proyecto de deportistas para deportistas, con el fin ayudar a llevar el control de rangos en el gimnasio. 

## 1. Descripción del proyecto

Console Gym Challenge es un proyecto de programación que busca desarrollar un sistema de control deportivo mediante consola.

El sistema permitirá registrar deportistas, almacenar información sobre su rendimiento, evaluar sus resultados y clasificarlos en diferentes rangos o niveles según su desempeño.

El objetivo principal es que cada deportista pueda conocer su estado actual, consultar su progreso y saber cuánto necesita mejorar para alcanzar el siguiente nivel.



## 2. Objetivos

* Registrar nuevos deportistas.
* Guardar y consultar la información de cada deportista.
* Registrar los resultados obtenidos en diferentes pruebas deportivas.
* Calcular el rendimiento de cada deportista.
* Asignar un rango dependiendo del rendimiento obtenido.
* Mostrar el progreso del deportista.
* Indicar cuánto le falta para alcanzar el siguiente rango.
* Permitir consultar, actualizar y eliminar información.


## 3. Funcionamiento general

El programa funcionará mediante un menú en consola.

El usuario podrá seleccionar diferentes opciones, por ejemplo:


===== CONSOLE GYM CHALLENGE =====

1. Registrar deportista
2. Registrar rendimiento
3. Consultar deportista
4. Mostrar clasificación
5. Actualizar información
6. Eliminar deportista
7. Salir

Seleccione una opción:

Dependiendo de la opción seleccionada, el sistema realizará la operación correspondiente.


# 4. Estructura del programa

Para organizar el proyecto se recomienda utilizar programación orientada a objetos.

## Clase Deportista

Esta clase representará a cada persona registrada en el sistema.

### Atributos sugeridos

* `id`: identificador único del deportista.
* `nombre`: nombre del deportista.
* `edad`: edad del deportista.
* `deporte`: disciplina deportiva que practica.
* `rendimiento`: resultado o puntuación actual.
* `rango`: nivel actual del deportista.

### Métodos sugeridos

* `mostrar_informacion()`: muestra los datos del deportista.
* `actualizar_rendimiento()`: permite modificar su rendimiento.
* `calcular_rango()`: determina el rango según su rendimiento.
* `progreso_siguiente_rango()`: calcula cuánto necesita mejorar para alcanzar el siguiente nivel.


## Clase SistemaGym

Esta clase se encargará de administrar todos los deportistas registrados.

### Atributos sugeridos

* `deportistas`: colección donde se almacenarán los deportistas.

### Métodos sugeridos

* `registrar_deportista()`
* `buscar_deportista()`
* `actualizar_deportista()`
* `eliminar_deportista()`
* `mostrar_deportistas()`
* `mostrar_clasificacion()`

Esta clase será la encargada de controlar las operaciones principales del sistema.


# 5. Sistema de rangos

Los deportistas serán clasificados dependiendo de su rendimiento.

Como ejemplo, se pueden establecer los siguientes rangos:

| Rendimiento | Rango        |
| ----------- | ------------ |
| 0 - 49      | Principiante |
| 50 - 69     | Básico       |
| 70 - 84     | Intermedio   |
| 85 - 94     | Avanzado     |
| 95 - 100    | Élite        |

Estos valores pueden modificarse dependiendo de las reglas definidas para el proyecto.


# 6. Progreso hacia el siguiente rango

El sistema deberá identificar el siguiente rango que puede alcanzar el deportista.

Por ejemplo:

Deportista: Juan
Rendimiento actual: 72
Rango: Intermedio

Siguiente rango: Avanzado
Rendimiento necesario: 85

Te faltan: 13 puntos


Si el deportista ya se encuentra en el rango máximo, el sistema deberá indicar que ha alcanzado el nivel más alto.


# 7. Registro de rendimiento

El sistema deberá permitir registrar o actualizar el rendimiento de un deportista.

El rendimiento puede estar representado mediante una puntuación entre **0 y 100**.

Ejemplo:

Ingrese el ID del deportista: 001
Ingrese el nuevo rendimiento: 87

Rendimiento actualizado correctamente.

Rango actual: Avanzado

El programa deberá validar que la puntuación ingresada se encuentre dentro del rango permitido.


# 8. Reglas del sistema

El programa deberá cumplir las siguientes reglas:

1. Cada deportista debe tener un identificador único.
2. No se deben registrar dos deportistas con el mismo identificador.
3. El nombre del deportista es obligatorio.
4. La edad debe ser un valor válido.
5. El rendimiento debe estar entre 0 y 100.
6. El rango debe calcularse automáticamente según el rendimiento.
7. El usuario debe poder consultar la información de un deportista.
8. El usuario debe poder actualizar el rendimiento.
9. El sistema debe indicar el progreso necesario para alcanzar el siguiente rango.
10. El programa debe controlar las opciones incorrectas del menú.


# 9. Flujo básico del programa

El funcionamiento general será:

INICIO
   ↓
Mostrar menú
   ↓
Seleccionar opción
   ↓
¿Registrar deportista?
   ↓
Guardar información
   ↓
¿Registrar/actualizar rendimiento?
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


# 10. Ejemplo de funcionamiento


===== CONSOLE GYM CHALLENGE =====

1. Registrar deportista
2. Registrar rendimiento
3. Consultar deportista
4. Mostrar clasificación
5. Salir

Seleccione una opción: 1

Nombre: Carlos
Edad: 20
Deporte: Voleibol

Deportista registrado correctamente.

Posteriormente:

Seleccione una opción: 2

ID del deportista: 001
Rendimiento: 78

Rango actual: Intermedio
Siguiente rango: Avanzado
Te faltan 7 puntos para alcanzar el siguiente rango.


# 11. Tecnologías

El proyecto será desarrollado utilizando:

* **Python**
* Programación Orientada a Objetos (POO)
* Aplicación de consola
* Estructuras de datos para almacenar los deportistas



# 12. Resultado esperado

Al finalizar el proyecto, se espera tener un programa funcional que permita administrar deportistas desde la consola, registrar sus resultados, clasificarlos automáticamente y realizar un seguimiento de su progreso.

