# Proyecto Final - Base de Datos Universitaria

## Descripción

Proyecto de base de datos relacional para gestionar información de una universidad, incluyendo estudiantes, docentes, carreras, materias, notas y horarios.

El proyecto fue desarrollado utilizando SQL y MariaDB, aplicando consultas con JOIN, funciones definidas por el usuario, vistas y triggers para la gestión, consulta y auditoría de la información.

## Tecnologías utilizadas

- SQL
- MariaDB
- DataGrip
- MySQL Workbench

## Funcionalidades

### Consultas SQL

El proyecto incluye consultas utilizando `INNER JOIN` para obtener información relacionada entre diferentes tablas.

### Funciones

Se implementaron 3 funciones:

- `promedioEstudiante` — obtiene el promedio de notas de un estudiante.
- `informacionEstudiante` — obtiene información de un estudiante y la materia en la que está matriculado.
- `mejorEstudiante` — obtiene el estudiante con la nota más alta de una materia.

### Vistas

Se implementaron 5 vistas para consultar información de:

- Docentes que imparten clases lunes y miércoles.
- Docentes que imparten Programación.
- Estudiantes de Ingeniería en Sistemas.
- Estudiantes que tienen clases con el docente William Barra.
- Estudiantes con notas mayores a 5 en Base de Datos.

### Triggers

Se implementaron 3 triggers:

- `eliminarEstudiante` — evita eliminar estudiantes que tengan notas registradas.
- `auditoriaNotas` — registra cambios realizados en las notas.
- `auditoriaMaterias` — registra cambios realizados en los nombres de las materias.

## Modelo de datos

El proyecto utiliza tablas relacionadas para representar estudiantes, docentes, carreras, materias, notas, clases y horarios.

El diagrama entidad-relación se encuentra incluido en este proyecto.

## Documentación

El informe completo del proyecto se encuentra en:

`INFORME_PROYECTO_FINAL_2.0.pdf`

También se incluye la presentación utilizada para la exposición.

## Video

Video del funcionamiento del proyecto:

https://youtu.be/sXkik8vP3Dc

## Autoría

Proyecto académico desarrollado como parte de Ingeniería de Sistemas.
