## Práctica 1.

1. Introducción a base de datos

Objetivo: Identificar el nivel de comprensión de los conceptos de base de datos,
mediante preguntas abiertas.
 
Preguntas:

1. ¿Cuáles son las cinco funciones principales del administrador de bases de datos?
(valor 1.5)

       1. Asegurar el buen funcionamiento de las BD
       2. Retención de información de las BD
       3. Evitar pérdida de datos
       4. Solucionar incidencias y pérdidas de datos
       5. Asegurar la seguridad de los datos

2. Indíque cinco responsabilidades del sistema gestor de bases de datos (valor 1.5)

       1. Instalar, configurar y gestionar bases de datos.
       2. Dar soporte al equipo de desarrollo, seguridad informática y redes.
       3. Definir el esquema del diccionario de datos.
       4. Especificar restricciones de integridad para asegurar los datos.
       5. Garantizar la alta disponibilidad de la base de datos.

3. En una BD al usuario del sistema se le brindarán recursos para realizar diversas
operaciones sobre estos archivos, tales como: (valor 1.5)

       - Entrada
       - Almacenamiento
       - Procesamiento
       - Salida de información.

4. ¿Qué es un Sistema de Información? (valor 1.5)

       Conjunto de elementos orientados al tratamiento y administración de datos e información, organizados y listos para su posterior uso, generados para cubrir necesidad.

## Práctica 2.

2. Diseño de un modelo relacional

Objetivo: Representar desde un modelo entidad relación un problema


Ejercicio:

Tenemos que diseñar una base de datos sobre proveedores y disponemos de la siguiente
información:

Realiza el modelo entidad relación. (valor 6)

Tenemos esta información sobre una cadena editorial:

● La editorial tiene varias sucursales, con su domicilio, teléfono y un código de
sucursal.

● Cada sucursal tiene varios empleados, de los cuales tendremos su nombre,
apellidos, NIF y teléfono. Un empleado trabaja en una única sucursal.

● En cada sucursal se publican varias revistas, de las que almacenaremos su título,
número de registro, periodicidad y tipo.

● Una revista puede ser publicada por varias sucursales.

● La editorial tiene periodistas (que no trabajan en las sucursales) que pueden
escribir artículos para varias revistas. Almacenaremos los mismos datos que para
los empleados, añadiendo su especialidad.

● También es necesario guardar las secciones fijas que tiene cada revista, que
constan de un título y una extensión.

● Para cada revista, almacenaremos información de cada ejemplar, que incluirá la
fecha, número de páginas y el número de ejemplares vendidos.



![image](https://user-images.githubusercontent.com/75552884/170139663-fc578674-4a27-42b4-a9df-d22f3aa72029.png)



- ESQUEMA SQL: https://www.db-fiddle.com/f/q1JxBLim4V94m9vfQjRXMd/5

      CREATE DATABASE editorial;
      USE editorial;

      CREATE TABLE sucursales (
        codigo VARCHAR(6) PRIMARY KEY,
        domicilio VARCHAR(100) NOT NULL,  
        telefono BIGINT UNSIGNED NOT NULL
      );

      CREATE TABLE revistas (
        num_registro VARCHAR(7) PRIMARY KEY,
        titulo VARCHAR(50) NOT NULL,
        periodicidad VARCHAR(50) NOT NULL,
        tipo VARCHAR(50) NOT NULL
      );

      CREATE TABLE periodistas (
        nif INT UNSIGNED PRIMARY KEY,
        nombre VARCHAR(50) NOT NULL,
        apellido VARCHAR(50) NOT NULL,
        telefono VARCHAR(10) NOT NULL,
        especialidad VARCHAR(25) NOT NULL
      );

      CREATE TABLE empleados (
        nif INT UNSIGNED PRIMARY KEY,
        nombre VARCHAR(50) NOT NULL,
        apellido VARCHAR(50) NOT NULL,
        telefono VARCHAR(10) NOT NULL,
        codigo1 VARCHAR(6) NOT NULL,
        FOREIGN KEY (codigo1) REFERENCES sucursales(codigo)
      );

      CREATE TABLE secciones (
        id INT UNSIGNED PRIMARY KEY,
        titulo VARCHAR(50) NOT NULL,
        extension VARCHAR(3) NOT NULL,
        num_registro1 VARCHAR(7) NOT NULL,
        FOREIGN KEY (num_registro1) REFERENCES revistas(num_registro)
      );

      CREATE TABLE ejemplares (
        id VARCHAR(3) PRIMARY KEY,
        fecha YEAR NOT NULL,
        num_paginas INT UNSIGNED, 
        num_vendidos INT UNSIGNED,
        num_registro2 VARCHAR(7) NOT NULL,
        FOREIGN KEY (num_registro2) REFERENCES revistas(num_registro)
      );

      CREATE TABLE sucursales_revistas (
        codigo2 VARCHAR(6),
        num_registro3 VARCHAR(7),
        FOREIGN KEY (codigo2) REFERENCES sucursales(codigo),
        FOREIGN KEY (num_registro3) REFERENCES revistas(num_registro)
      );

      CREATE TABLE revistas_periodistas (
        num_registro4 VARCHAR(7),
        nif1 INT UNSIGNED,
        FOREIGN KEY (num_registro4) REFERENCES revistas(num_registro),
        FOREIGN KEY (nif1) REFERENCES periodistas(nif)
      );


1:N  SE crean claves foraneas en cada entidad, las cuales corresponden a la claves primarias de la entidad origen.

N:M Se crea una nueva tabla (derivada) cuyos atributos son las claves primarias de cada entidad.



