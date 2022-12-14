<h1 align="center"> PORTAFOLIO BASE DE DATOS II  </h1>

<img align="right" src="https://www.certus.edu.pe/blog/wp-content/uploads/2021/06/que-es-sql-todo-debes-saber-lenguaje.jpg" height="400" width="1000">


<h1 align="center"> PORTAFOLIO</h1>

![snake gif](https://media3.giphy.com/media/RtdRhc7TxBxB0YAsK6/200w.gif?cid=6c09b952bsrrw3z12wsg7gxa239tiqjtzxogsdu0v2h3txjx&rid=200w.gif&ct=g)


## ➤ HITO 2 
## ➤ FUNCTIONS
- 📝 Repositorio del  [Hito 2](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%202)
### [LABORATORIOS](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%202/Labs)
### [PROCESUAL](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%202/PROCESUAL) 

## ➤ Code SQL

```javascript
create database libreria;
use libreria;

create table categories
(
    category_id integer auto_increment primary key not null,
    name varchar (20)
);

create table publishers
(
    publishers_id int auto_increment primary key not null,
    name varchar(20)
);

create table books
(
    book_id int auto_increment primary key not null,
    title varchar (20),
    isbn varchar (20),
    publisher_date date,
    description varchar (20),
    category_id int,
    publisher_id int,


    foreign key (category_id)references categories(category_id),
    foreign key (publisher_id)references publishers(publishers_id)
);
```

## ➤ HITO 3  
##  MANEJOS DE ESTRUCTURAS DE CONTROL
- 📝 Repositorio del  [Hito 3](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%203)
### [PROCESUAL](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%203/procesual) 

## ➤ Code SQL
```javascript
CREATE DATABASE POLLOS_COPA;
 USE POLLOS_COPA;

CREATE TABLE CLIENTE
(
    ID_CLIENTE INTEGER AUTO_INCREMENT PRIMARY KEY NOT NULL ,
    FULLNAME VARCHAR(30),
    LASTNAME VARCHAR(30),
    EDAD INTEGER,
    DOMICILIO VARCHAR(40)
);
CREATE TABLE PEDIDO
(
    ID_PEDIDO INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
    ARTICULO VARCHAR(30),
    COSTO FLOAT,
    FECHA DATE
);

CREATE TABLE  DETALLE_PEDIDO
(
    ID_DETALLE_PEDIDO INTEGER AUTO_INCREMENT NOT NULL PRIMARY KEY,
    ID_PEDIDO INTEGER NOT NULL,
    ID_CLIENTE INTEGER NOT NULL,
    FOREIGN KEY (ID_PEDIDO) REFERENCES PEDIDO(ID_PEDIDO),
    FOREIGN KEY (ID_CLIENTE) REFERENCES CLIENTE(ID_CLIENTE)
);

INSERT INTO CLIENTE(FULLNAME, LASTNAME, EDAD, DOMICILIO)
VALUES('PEDRO','SALAZAR GOMEZ',19,'RIO SECO'),
      ('MARIA','DELGADO MENDOZA',20,'BALLIVIAN');

INSERT INTO PEDIDO(ARTICULO, COSTO, FECHA)
VALUES('LECHE',21.2,'2022-08-02'),
      ('CARNE',7.4,'2022-09-12');

INSERT INTO DETALLE_PEDIDO(ID_PEDIDO, ID_CLIENTE)
VALUES(1,2),
      (2,1);

#12
SELECT DETALLE_PEDIDO.ID_DETALLE_PEDIDO AS CODIGO_COMPRA,
       CONCAT(CLIENTE.FULLNAME,CLIENTE.LASTNAME) AS NOMBRE_COMPLETO,
       PEDIDO.ARTICULO,PEDIDO.COSTO

FROM DETALLE_PEDIDO
INNER JOIN CLIENTE ON DETALLE_PEDIDO.ID_CLIENTE = CLIENTE.ID_CLIENTE
INNER JOIN PEDIDO ON DETALLE_PEDIDO.ID_PEDIDO = PEDIDO.ID_PEDIDO;

#13

CREATE DATABASE tareaHito2;
USE tareaHito2;

CREATE TABLE estudiantes
(
 id_est INTEGER AUTO_INCREMENT PRIMARY KEY NOT NULL,
 nombres VARCHAR(50),
 apellidos VARCHAR(50),
 edad INTEGER,
 gestion INTEGER,
 fono INTEGER,
 email VARCHAR(100),
 direccion VARCHAR(100),
 sexo VARCHAR(10)
);

CREATE TABLE materias
(
  id_mat INTEGER AUTO_INCREMENT PRIMARY KEY  NOT NULL,
  nombre_mat VARCHAR(100),
  cod_mat VARCHAR(100)
);

CREATE TABLE inscripcion
(
  id_ins INTEGER AUTO_INCREMENT PRIMARY KEY NOT NULL,
  semestre VARCHAR(20),
  gestion INTEGER,

  id_est INT NOT NULL,
  id_mat INT NOT NULL,
  FOREIGN KEY (id_est) REFERENCES estudiantes (id_est),
  FOREIGN KEY (id_mat) REFERENCES materias (id_mat)
);

INSERT INTO estudiantes (nombres, apellidos, edad, fono, email,direccion, sexo)
VALUES  ('Miguel', 'Gonzales Veliz', 20, 2832115,'miguel@gmail.com', 'Av. 6 de Agosto', 'masculino'),
        ('Sandra', 'Mavir Uria', 25, 2832116, 'sandra@gmail.com','Av. 6 de Agosto', 'femenino'),
        ('Joel', 'Adubiri Mondar', 30, 2832117, 'joel@gmail.com','Av. 6 de Agosto', 'masculino'),
        ('Andrea', 'Arias Ballesteros', 21, 2832118,'andrea@gmail.com', 'Av. 6 de Agosto', 'femenino'),
        ('Santos', 'Montes Valenzuela', 24, 2832119,'santos@gmail.com', 'Av. 6 de Agosto', 'masculino');


INSERT INTO materias (nombre_mat, cod_mat)
VALUES  ('Introduccion a la Arquitectura', 'ARQ-101'),
        ('Urbanismo y Diseno', 'ARQ-102'),
        ('Dibujo y Pintura Arquitectonico', 'ARQ-103'),
        ('Matematica discreta', 'ARQ-104'),
        ('Fisica Basica', 'ARQ-105');

INSERT INTO inscripcion (id_est, id_mat, semestre, gestion)
VALUES  (1, 1, '1er Semestre', 2018),
        (1, 2, '2do Semestre', 2018),
        (2, 4, '1er Semestre', 2019),
        (2, 3, '2do Semestre', 2019),
        (3, 3, '2do Semestre', 2020),
        (3, 1, '3er Semestre', 2020),
        (4, 4, '4to Semestre', 2021),
        (5, 5, '5to Semestre', 2021);



CREATE OR REPLACE FUNCTION COMPARA_MATERIAS(CODI_MAT VARCHAR(100),NOMBRE_MAT VARCHAR(100))
RETURNS BOOLEAN
BEGIN
    DECLARE RESPUESTA BOOLEAN;

        IF CODI_MAT=NOMBRE_MAT
        THEN
        SET RESPUESTA=1;
        END IF;
    RETURN RESPUESTA;
END;

SELECT ESTUDIANTES.id_est, ESTUDIANTES.NOMBRES,ESTUDIANTES.APELLIDOS,
       MATERIAS.NOMBRE_MAT,MATERIAS.COD_MAT
FROM inscripcion
INNER JOIN estudiantes ON inscripcion.id_est = estudiantes.id_est
INNER JOIN materias ON inscripcion.id_mat = materias.id_mat

WHERE COMPARA_MATERIAS(materias.cod_mat,'ARQ-105');

#14
CREATE OR REPLACE FUNCTION PROMEDIO_GENERO_MATERIA( GENERO VARCHAR(11),MATERIA_COD VARCHAR(100))
RETURNS INTEGER
BEGIN
    DECLARE PROMEDIO INTEGER DEFAULT 0;

    SELECT AVG(estudiantes.edad) INTO PROMEDIO
    FROM inscripcion
    INNER JOIN estudiantes ON inscripcion.id_est = estudiantes.id_est
    INNER JOIN materias ON inscripcion.id_mat = materias.id_mat
    WHERE estudiantes.sexo= GENERO AND materias.cod_mat=MATERIA_COD;
    RETURN PROMEDIO;
END;

SELECT PROMEDIO_GENERO_MATERIA('femenino','ARQ-104');

#15

CREATE OR REPLACE FUNCTION CONCATENAR_PALABRAS (A1 VARCHAR(30),A2 VARCHAR(30),A3 VARCHAR(30))
RETURNS VARCHAR(90)
BEGIN
    DECLARE CADENA_TOTAL VARCHAR(90) DEFAULT '';
    SET CADENA_TOTAL= CONCAT('(',A1,') (',A2,') (',A3,')');

    RETURN CADENA_TOTAL ;
END;

SELECT CONCATENAR_PALABRAS('PEPITO','PEP','50') AS CONCATENADO_TOTAL;

#16


CREATE OR REPLACE FUNCTION EST_SEGUN_EDAD_GENERO(SEXO VARCHAR(11),EDAD INTEGER)
RETURNS BOOLEAN
BEGIN
    DECLARE SUMA INTEGER DEFAULT 0;
    DECLARE SIoNO BOOLEAN;

    SELECT SUM(ESTUDIANTES.EDAD) INTO SUMA
    FROM estudiantes
    WHERE estudiantes.SEXO=SEXO;

    IF SUMA%2=0 AND SUMA>EDAD
    THEN
        SET SIoNO=1;
    END IF;
    RETURN SIoNO;
END;

SELECT ESTUDIANTES.NOMBRES, ESTUDIANTES.APELLIDOS,ESTUDIANTES.EDAD,INSCRIPCION.SEMESTRE
FROM inscripcion
INNER  JOIN estudiantes ON inscripcion.id_est = estudiantes.id_est
WHERE EST_SEGUN_EDAD_GENERO('MASCULINO',22);

SELECT SUM(EDAD)
FROM estudiantes
GROUP BY(ESTUDIANTES.SEXO);

# 17

CREATE OR REPLACE FUNCTION BUSCA_NOMBRES_APELLIDOS(nombre varchar(100),apellidos varchar(100),nombre_c varchar (100),apellido_c varchar(100))

    RETURNS BOOLEAN
    BEGIN
        DECLARE DECISION BOOLEAN;
        if nombre=nombre_c and apellidos=apellido_c
        then
        set DECISION=1;
        end if;
        RETURN DECISION;

    END;
SELECT EST.*
from estudiantes as est
where BUSCA_NOMBRES_APELLIDOS(est.nombres,est.apellidos,'sandra','mavir uria')

```
## ➤ HITO 4  
##  VISTAS Y TRIGGERS
- 📝 Repositorio del  [Hito 4](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%204)
### [LABORATORIOS](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%204/laboratorios)
### [PROCESUAL](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%204/procesual)
### [EVALUCION](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%204/examen)

## ➤ Code SQL  
```javascript
import 'package:flutter/material.dart';
import 'package:flutter_memory_game/constants.dart';
import 'package:flutter_memory_game/pages/nivel_page.dart';
import 'package:flutter_memory_game/theme.dart';
import 'package:flutter_memory_game/widgets/logo.dart';
import 'package:flutter_memory_game/widgets/recordes.dart';
import 'package:flutter_memory_game/widgets/start_button.dart';

class HomePage extends StatelessWidget {
  const HomePage({Key? key}) : super(key: key);

  selecionarNivel(Modo modo, BuildContext context) async { //async es necesario para usar await
    await Navigator.push( //Navigator es un widget que administra una pila de rutas
      // y proporciona métodos para gestionar la pila, como Navigator.push y Navigator.pop.
      // Navigator.push es un método que se usa para navegar a una nueva ruta y esperar a que se complete.
      //Navigator.pop es un método que se usa para volver a la ruta anterior.
      context,
      MaterialPageRoute( //MaterialPageRoute es una clase que implementa la transición de una página a otra.
        builder: (context) => NivelPage(modo: modo), //builder es un método que se usa para construir una nueva ruta.
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold( //Scaffold es un widget que implementa la estructura visual básica de Material Design.
      body: Padding( //Padding es un widget que inserta un borde alrededor.
        padding: const EdgeInsets.all(24.0), //EdgeInsets es un widget que representa los bordes de un rectángulo.
        child: Column( //Column es un widget que implementa una columna vertical.
          mainAxisAlignment: MainAxisAlignment.center, //alinea sus objetos en el eje principal
          crossAxisAlignment: CrossAxisAlignment.center, // alinea sus objetos en el eje transversal
          children: [ //children es una lista de widgets
            const Logo(), //Logo es un widget que muestra el logo de la app
            StartButton( //StartButton es un widget que muestra un botón de inicio
              title: 'Modo Normal', //title es el titulo del boton
              color: Colors.white, //color es el color del boton
              action: () => selecionarNivel(Modo.normal, context), //action es la accion que se ejecuta al presionar el boton
            ),
            StartButton(
              title: 'Modo Insano',
              color: ShitpostThemeColor.color, //color es el color del boton
              action: () => selecionarNivel(Modo.dificil, context), //action es la accion que se ejecuta al presionar el boton
            ),
            const SizedBox(height: 60), //SizedBox le da un tamaño fijo
            const Recordes(), //Recordes es un widget que muestra los recordes
          ],
        ),
      ),
    );
  }
}
```
## ➤ HITO 5  
##  PROYECTO FINAL
- 📝 Repositorio del  [Hito 5](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%205)
### [PROYECTO FINAL](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%205/Proyecto%20final)
## ➤ Code SQL
```javascript
create database DB_Universidad;
use DB_Universidad;


-- Tabla de Carreras
create table Carreras(
    idCarrera int primary key auto_increment,
    nombre varchar(50) not null,
    descripcion varchar(100) not null
);

-- Tabla de Estudiantes
create table Estudiantes(
    idEstudiante int primary key auto_increment,
    nombre varchar(50) not null,
    apellido varchar(50) not null,
    fechaNacimiento date not null,
    direccion varchar(100) not null,
    telefono varchar(10) not null,
    email varchar(50) not null,
    idCarrera int not null,
    foreign key (idCarrera) references Carreras(idCarrera)
);


-- Tabla de Materias
create table Materias(
    idMateria int primary key auto_increment,
    nombre varchar(50) not null,
    descripcion varchar(100) not null,
    idCarrera int not null,
    foreign key (idCarrera) references Carreras(idCarrera)
);

-- Tabla de docentes
create table Docentes(
    idDocente int primary key auto_increment,
    nombre varchar(50) not null,
    apellido varchar(50) not null,
    fechaNacimiento date not null,
    direccion varchar(100) not null,
    telefono varchar(10) not null,
    email varchar(50) not null,
    idMateria int not null,
    foreign key (idMateria) references Materias(idMateria)
);

-- Tabla de notas
create table Notas(
    idNota int primary key auto_increment,
    nota int not null,
    idEstudiante int not null,
    idMateria int not null,
    foreign key (idEstudiante) references Estudiantes(idEstudiante),
    foreign key (idMateria) references Materias(idMateria)
);


-- tabla de clases
create table Clases(
    idClase int primary key auto_increment,
    idDocente int not null,
    idMateria int not null,
    foreign key (idDocente) references Docentes(idDocente),
    foreign key (idMateria) references Materias(idMateria)
);

-- tabla de horarios
create table Horarios(
    idHorario int primary key auto_increment,
    idClase int not null,
    dia varchar(50) not null,
    horaInicio time not null,
    horaFin time not null,
    foreign key (idClase) references Clases(idClase)
);


-- insertar datos

-- insertar datos en la tabla carreras
insert into Carreras(nombre, descripcion)
values('Ingenieria en Sistemas', 'Ingenieria en Sistemas'),
      ('Ingenieria en Mecatronica', 'Ingenieria en Mecatronica'),
      ('Ingenieria en Mecanica', 'Ingenieria en Mecanica'),
      ('Ingenieria en Electrica', 'Ingenieria en Electrica'),
      ('Ingenieria en Electronica', 'Ingenieria en Electronica'),
      ('Ingenieria en Industrial', 'Ingenieria en Industrial'),
      ('Ingenieria en Mecanica Industrial', 'Ingenieria en Mecanica Industrial'),
      ('Derecho',' Derecho'),
      ('Medicina', 'Medicina'),
      ('Psicologia', 'Psicologia');

-- insertar datos en la tabla estudiantes
insert into Estudiantes(nombre, apellido, fechaNacimiento, direccion, telefono, email, idCarrera)
values('Juan', 'Perez', '1990-01-01', 'Calle 1', '1234567890', 'juan@gmial.com', 1),
      ('Maria', 'Gomez', '1990-01-01', 'Calle 2', '1234567890', 'maria@gmail.com', 2),
      ('Pedro', 'Gonzales', '1990-01-01', 'Calle 3', '1234567890', 'pedro@gmail.com', 3),
      ('Jose', 'Lopez', '1990-01-01', 'Calle 4', '1234567890', 'jose@gmail.com', 4),
      ('Luis', 'Martinez', '1990-01-01', 'Calle 5', '1234567890', 'luis@gmail.com', 5),
      ('Ana', 'Rodriguez', '1990-01-01', 'Calle 6', '1234567890', 'ana@gmail.com', 6),
      ('Lorena', 'Gutierrez', '1990-01-01', 'Calle 7', '1234567890', 'lorena@gmail.com', 7),
      ('Sofia', 'Hernandez', '1990-01-01', 'Calle 8', '1234567890', 'sofia@gmail.com', 8),
      ('Miguel', 'Diaz', '1990-01-01', 'Calle 9', '1234567890', 'miguel@gmail.com', 9),
      ('Carlos', 'Perez', '1990-01-01', 'Calle 10', '1234567890', 'carlos@gmail.com', 10);

-- insertar datos en la tabla materias
insert into Materias(nombre, descripcion, idCarrera)
values('Matematicas', 'Matematicas', 1),
      ('Fisica', 'Fisica', 2),
      ('Quimica', 'Quimica', 3),
      ('Biologia', 'Biologia', 4),
      ('Programacion', 'Programacion', 5),
      ('Base de datos', 'Base de datos', 6),
      ('Redes', 'Redes', 7),
      ('Ingles', 'Ingles', 8),
      ('Frances', 'Frances', 9),
      ('Aleman', 'Aleman', 10);

-- insertar datos en la tabla docentes
insert into Docentes(nombre, apellido, fechaNacimiento, direccion, telefono, email, idMateria)
values('Carlos', 'Condori', '1990-01-01', 'Calle 1', '1234567890', 'carlos@gmail.com', 1),
      ('Alejandro', 'Plata', '1990-01-01', 'Calle 2', '1234567890', 'alejandro@gmail.com', 2),
      ('Abel', 'Quispe', '1990-01-01', 'Calle 3', '1234567890', 'abel@gmail.com', 3),
      ('Alex', 'Gonzales', '1990-01-01', 'Calle 4', '1234567890', 'alex@gmail.com', 4),
      ('Luis', 'Rojas', '1990-01-01', 'Calle 5', '1234567890', 'luis@gmail.com', 5),
      ('Bocaro', 'Rodriguez', '1990-01-01', 'Calle 6', '1234567890', 'bocaro@gmail.com', 6),
      ('Raul', 'Gutierrez', '1990-01-01', 'Calle 7', '1234567890', 'raul@gmail.com', 7),
      ('Misael', 'Paredes', '1990-01-01', 'Calle 8', '1234567890', 'misael@gmail.com', 8),
      ('Minerva', 'Torrez', '1990-01-01', 'Calle 9', '1234567890', 'minerva@gmail.com', 9),
      ('Estefani', 'Maldonado', '1990-01-01', 'Calle 10', '1234567890', 'estefani@gmail.com', 10);

-- insertar datos en la tabla notas
insert into Notas(idEstudiante, idMateria, nota)
values(1, 1, 15),
      (2, 2, 16),
      (3, 3, 17),
      (4, 4, 18),
      (5, 5, 19),
      (6, 6, 20),
      (7, 7, 21),
      (8, 8, 22),
      (9, 9, 23),
      (10, 10, 24);


-- insertar datos en la tabla clases
insert into Clases(idDocente, idMateria) values(1, 1);
insert into Clases(idDocente, idMateria) values(2, 2);
insert into Clases(idDocente, idMateria) values(3, 3);
insert into Clases(idDocente, idMateria) values(4, 4);
insert into Clases(idDocente, idMateria) values(5, 5);
insert into Clases(idDocente, idMateria) values(6, 6);
insert into Clases(idDocente, idMateria) values(7, 7);
insert into Clases(idDocente, idMateria) values(8, 8);
insert into Clases(idDocente, idMateria) values(9, 9);
insert into Clases(idDocente, idMateria) values(10, 10);

-- insertar datos en la tabla horarios
insert into Horarios(idClase, dia, horaInicio, horaFin)
values(1, 'Lunes', '08:00:00', '10:00:00'),
      (2, 'Martes', '08:00:00', '10:00:00'),
      (3, 'Miercoles', '08:00:00', '10:00:00'),
      (4, 'Jueves', '08:00:00', '10:00:00'),
      (5, 'Viernes', '08:00:00', '10:00:00'),
      (6, 'Sabado', '08:00:00', '10:00:00'),
      (7, 'Domingo', '08:00:00', '10:00:00'),
      (8, 'Lunes', '10:00:00', '12:00:00'),
      (9, 'Martes', '10:00:00', '12:00:00'),
      (10, 'Miercoles', '10:00:00', '12:00:00');

-- insertar datos en la tabla estudiantes todos en la misma carrera y materia para probar el procedimiento almacenado
insert into Estudiantes(nombre, apellido, fechaNacimiento, direccion, telefono, email, idCarrera)
values('Carlos', 'Condori', '1990-01-01', 'Calle 1', '1234567890', '', 6),
      ('Alejandro', 'Plata', '1990-01-01', 'Calle 2', '1234567890', '', 6),
      ('Abel', 'Quispe', '1990-01-01', 'Calle 3', '1234567890', '', 6),
      ('Alex', 'Gonzales', '1990-01-01', 'Calle 4', '1234567890', '', 6),
      ('Luis', 'Rojas', '1990-01-01', 'Calle 5', '1234567890', '', 6),
      ('Bocaro', 'Rodriguez', '1990-01-01', 'Calle 6', '1234567890', '', 6),
      ('Raul', 'Gutierrez', '1990-01-01', 'Calle 7', '1234567890', '', 6),
      ('Misael', 'Paredes', '1990-01-01', 'Calle 8', '1234567890', '', 6),
      ('Minerva', 'Torrez', '1990-01-01', 'Calle 9', '1234567890', '', 6),
      ('Estefani', 'Maldonado', '1990-01-01', 'Calle 10', '1234567890', '', 6);

-- todos los estudiantes de la carrera de base de datos
select * from Estudiantes
         inner join Carreras on Estudiantes.idCarrera = Carreras.idCarrera
         inner join Materias M on Carreras.idCarrera = M.idCarrera
         where idMateria = 6;


# 1. Consultas SQL que maneja JOINS = 5 Consultas
# 2. Funciones UDF = 3 FUNCIONES
# 3. Vistas = 5 Vistas
# a. Reutiliza 3 consultas
# b. Crear 2 nuevas
# 4. Triggers = 3 TRIGGERS
# a. 1 trigger de validación
# b. 2 triggers de autoria

# 1. Consultas SQL que maneja JOINS = 5 Consultas
# 1.1. Cuales son los estudiantes que tienen notas mayores a 18
select e.nombre, e.apellido, n.nota
from Estudiantes e
inner join Notas n on e.idEstudiante = n.idEstudiante
where n.nota > 5;

# 1.2. Cuales son los estudiantes que estan en la carrera de Ingenieria de Sistemas
select e.nombre, e.apellido, c.nombre
from Estudiantes e
inner join Carreras c on e.idCarrera = c.idCarrera
where c.nombre = 'Ingenieria en Sistemas';



# 1.3. que docentes imparten clases los lunes y miercoles
select d.nombre, d.apellido, h.dia
from Docentes d
inner join Clases c on d.idDocente = c.idDocente
inner join Horarios h on c.idClase = h.idClase
where h.dia = 'Lunes' or h.dia = 'Miercoles';

# 1.4. que docentes tienen a cargo la materia de Base de datos
select d.nombre, d.apellido, m.nombre
from Docentes d
inner join Clases c on d.idDocente = c.idDocente
inner join Materias m on c.idMateria = m.idMateria
where m.nombre = 'Base de datos';

# 1.5. que estudiantes tienen notas mayores a 5 en la materia de Base de datos
select e.nombre, e.apellido, m.nombre, n.nota
from Estudiantes e
inner join Notas n on e.idEstudiante = n.idEstudiante
inner join Materias m on n.idMateria = m.idMateria
where m.nombre = 'Base de datos' and n.nota > 5;

# 2. Funciones UDF = 3 FUNCIONES
# 2.1. Funcion que retorne el promedio de notas de un estudiantes mediante su Id
create function promedioEstudiante(idEstudiante int)
returns float
begin
    declare promedio float;
    select avg(n.nota) into promedio
    from Notas n
    where n.idEstudiante = idEstudiante;
    return promedio;
end;

select promedioEstudiante(1);

# 2.2. Funcion para obtener la informacion de un estudiante matriculado en una materia
# la funcion debe recibir como parametro el nombre del estudiante y el nombre de la materia
create function informacionEstudiante(nombreEstudiante varchar(50), nombreMateria varchar(50))
returns varchar(100)
begin
    declare informacion varchar(100);
    select concat(e.nombre, ' ', e.apellido, ' ', m.nombre) into informacion
    from Estudiantes e
    inner join Notas n on e.idEstudiante = n.idEstudiante
    inner join Materias m on n.idMateria = m.idMateria
    where e.nombre = nombreEstudiante and m.nombre = nombreMateria;
    return informacion;
end;

select informacionEstudiante('Ana', 'Base de datos');

# 2.3. Funcion para eligir el mejor estudiante de una materia
# la funcion debe recibir como parametro el nombre de la materia
create function mejorEstudiante(nombreMateria varchar(50))
returns varchar(100)
begin
    declare mejor varchar(100);
    select concat(e.nombre, ' ', e.apellido, ' ', m.nombre) into mejor
    from Estudiantes e
    inner join Notas n on e.idEstudiante = n.idEstudiante
    inner join Materias m on n.idMateria = m.idMateria
    where m.nombre = nombreMateria and n.nota = (select max(nota) from Notas);
    return mejor;
end;

select mejorEstudiante('programacion');

# 3. Vistas = 5 Vistas
# a. Reutiliza 3 consultas
# b. Crear 2 nuevas

# 3.1. Vistas de estudiantes que tienen notas mayores a 5 en la materia de Base de datos
create view estudiantesNotasBaseDatos as
select e.nombre as 'Nombre',
       e.apellido as 'Apellido',
       m.nombre as 'Materia',
       n.nota as 'Nota'
from Estudiantes e
inner join Notas n on e.idEstudiante = n.idEstudiante
inner join Materias m on n.idMateria = m.idMateria
where m.nombre = 'Base de datos' and n.nota > 5;

select * from estudiantesNotasBaseDatos;

# 3.2. Vistas de estudiantes que estan en la carrera de Ingenieria de Sistemas
create view estudiantesCarreraIngenieriaSistemas as
select e.nombre as 'Nombre',
       e.apellido as 'Apellido',
       c.nombre as 'Carrera'
from Estudiantes e
inner join Carreras c on e.idCarrera = c.idCarrera
where c.nombre = 'Ingenieria en Sistemas';

select * from estudiantesCarreraIngenieriaSistemas;

# 3.3. Vistas de que docentes imparten clases los lunes y miercoles
create view docentesImpartenClasesLunesMiercoles as
select d.nombre as 'Nombre',
       d.apellido as 'Apellido',
       h.dia as 'Dia'
from Docentes d
inner join Clases c on d.idDocente = c.idDocente
inner join Horarios h on c.idClase = h.idClase
where h.dia = 'Lunes' or h.dia = 'Miercoles';

select * from docentesImpartenClasesLunesMiercoles;

# 3.4. Vistas de que docentes tienen a cargo la materia de programacion
create view docentesMateriaProgramacion as
select d.nombre as 'Nombre',
       d.apellido as 'Apellido',
       m.nombre as 'Materia'
from Docentes d
inner join Clases c on d.idDocente = c.idDocente
inner join Materias m on c.idMateria = m.idMateria
where m.nombre = 'Programacion';

select * from docentesMateriaProgramacion;

# 3.5. Vistas de estudiantes que tiene clases con el docente william barra
create or replace view estudiantesClasesDocenteWilliamBarra as
select e.nombre as 'Nombre',
       e.apellido as 'Apellido',
       d.nombre as 'Docente'
from Estudiantes e
inner join Clases c on e.idEstudiante = c.idMateria
inner join Docentes d on c.idDocente = d.idDocente
where d.nombre = 'William' and d.apellido = 'Barra';

select * from estudiantesClasesDocenteWilliamBarra;


# 4. Triggers = 3 Triggers
# a. 1 trigger de validacion
# b. 2 triggers de auditoria

# 4.1. Trigger de validacion para que se elimine un estudiante solo si no tiene notas
create trigger eliminarEstudiante
before delete on Estudiantes
for each row
begin
    if (select count(*) from Notas where idEstudiante = old.idEstudiante) > 0 then
        signal sqlstate '45000'
        set message_text = 'No se puede eliminar el estudiante porque tiene notas';
    end if;
end;

delete from Estudiantes where idEstudiante = 1;

# 4.2. Trigger de auditoria para que se registre cuando se haga un cambio en las notas

create table AuditoriaNotas (
    idEstudiante int,
    idMateria int,
    notaAnterior int,
    notaActual int
);

create trigger auditoriaNotas
after update on Notas
for each row
begin
    insert into AuditoriaNotas values (old.idEstudiante, old.idMateria, old.nota, new.nota);
end;

update Notas set nota = 5 where idEstudiante = 1 and idMateria = 1;

select * from AuditoriaNotas;

# 4.3. Trigger de auditoria para que se registre cuando se haga un cambio en las materias

create or replace table AuditoriaMaterias (
    idMateria int,
    materiaAnterior varchar(50),
    materiaActual varchar(50)
);

create or replace trigger auditoriaMaterias
after update on Materias
for each row
begin
    insert into AuditoriaMaterias values (old.idMateria, old.nombre, new.nombre);
end;

update Materias set nombre = 'Base de datos' where idMateria = 2;

select * from AuditoriaMaterias;
```

<h2 align='center'> Thank you⭐ </h2>
<br>
<p align='center'>
<img src="https://i.giphy.com/media/SY2hQpAMLnuxtgLT5C/giphy.gif" width="200" height="200" frameBorder="0" class="giphy-embed" allowFullScreen></img></p>
<br>
- 🔭 docente LIC. WILLIAM BARRA
- 🌱 MATERIA BASE DE DATOS II
- 👯 UNIVERSIDAD UNIFRANZ
