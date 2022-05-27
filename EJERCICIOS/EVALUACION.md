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



![image](https://user-images.githubusercontent.com/75552884/170741473-4df670ee-080e-4c17-880b-0792294fe4d1.png)




- ESQUEMA SQL: https://www.db-fiddle.com/f/q1JxBLim4V94m9vfQjRXMd/10


      CREATE DATABASE editorial;
      USE editorial;


      -- SE CREA LA TABLA "SUCURSALES" Y SE GENERA SUS DATOS

      CREATE TABLE sucursales (
        codigo_suc VARCHAR(6) PRIMARY KEY,
        domicilio_suc VARCHAR(100) NOT NULL,  
        telefono_suc BIGINT UNSIGNED NOT NULL
      );


      INSERT INTO sucursales VALUES ('suc-01','Tenayuca 15, Colonia Porvenir',5573485948);
      INSERT INTO sucursales VALUES ('suc-02','Ahuehuetes 24, Colona Reynosa',3395847649);
      INSERT INTO sucursales VALUES ('suc-03','San Juan 12, Colonia Electricistas',7293840947);
      INSERT INTO sucursales VALUES ('suc-04','Manuel Buendía 948, Colonia Reforma',8293459375);
      INSERT INTO sucursales VALUES ('suc-05','Petroleos 12, Cpolonia Alabama',7394850983);
      INSERT INTO sucursales VALUES ('suc-06','Petén 1209, Roma Norte',5587394785);
      INSERT INTO sucursales VALUES ('suc-07','Tlahuac 10, Colonia Reyes',4593849058);
      INSERT INTO sucursales VALUES ('suc-08','Anaxagoras 15, Polanco',3384909859);
      INSERT INTO sucursales VALUES ('suc-09','Miguel Hidalgo 98, Colonia Angustura',3338930403);
      INSERT INTO sucursales VALUES ('suc-10','Cervantes 56, Colonia Juárez',2288473845);


      -- SE CREA LA TABLA "revistas" Y SE GENERA SUS DATOS

      CREATE TABLE revistas (
        num_registro_rev VARCHAR(7) PRIMARY KEY,
        titulo_rev VARCHAR(50) NOT NULL,
        periodicidad_rev VARCHAR(50) NOT NULL,
        tipo_rev VARCHAR(50) NOT NULL
      );


      INSERT INTO revistas VALUES ('REV_098','POLITICA HOY','SEMANAL','POLITICA');
      INSERT INTO revistas VALUES ('REV_099','EMOCION DEPORTIVA','QUINCENAL','DEPORTIVA');
      INSERT INTO revistas VALUES ('REV_100','MUNDO ROSA','SEMANAL','ESPECTACULOS');
      INSERT INTO revistas VALUES ('REV_101','VIDEOGAMER','MENSUAL','VIDEOJUEGOS');
      INSERT INTO revistas VALUES ('REV_102','CINE HOY','SEMANAL','CINE');
      INSERT INTO revistas VALUES ('REV_103','TODO EN CULTURA','MENSUAL','CULTURAL');



      -- SE CREA LA TABLA "periodistas" Y SE GENERA SUS DATOS

      CREATE TABLE periodistas (
        nif_peri VARCHAR(6) PRIMARY KEY,
        nombre_peri VARCHAR(50) NOT NULL,
        apellido_peri VARCHAR(50) NOT NULL,
        telefono_peri BIGINT UNSIGNED NOT NULL,
        especialidad_peri VARCHAR(25) NOT NULL
      );


      INSERT INTO periodistas VALUES ('PER_01','KARLA','JUAREZ',5534563748,'DEPORTES');
      INSERT INTO periodistas VALUES ('PER_02','BEATRIZ','LOPEZ',7289467349,'POLITICA');
      INSERT INTO periodistas VALUES ('PER_03','TITO','MARQUEZ',8203978465,'ESPECTACULOS');
      INSERT INTO periodistas VALUES ('PER_04','ISABEL','SUAREZ',8263748987,'VIDEOJUEGOS');
      INSERT INTO periodistas VALUES ('PER_05','PABLO','FERNANDEZ',5523784938,'CINE');
      INSERT INTO periodistas VALUES ('PER_06','SERGIO','INFANTE',7238946574,'CINE');
      INSERT INTO periodistas VALUES ('PER_07','CARLOS','GUIZAR',3398475840,'CULTURA');
      INSERT INTO periodistas VALUES ('PER_08','JUAN','SALAS',5682394848,'DEPORTES');
      INSERT INTO periodistas VALUES ('PER_09','PEDRO','RICO',5548738495,'POLITICA');
      INSERT INTO periodistas VALUES ('PER_10','ANGEL','HERAS',8236475894,'VIDEOJUEGOS');
      INSERT INTO periodistas VALUES ('PER_11','CESAR','SAN PEDRO',4585968495,'CINE');
      INSERT INTO periodistas VALUES ('PER_12','MAGDA','LIRA',7683749504,'POLITICA');



      -- SE CREA LA TABLA "empleados" Y SE GENERA SUS DATOS

      CREATE TABLE empleados (
        nif_emple VARCHAR(6) PRIMARY KEY,
        nombre_emple VARCHAR(50) NOT NULL,
        apellido_emple VARCHAR(50) NOT NULL,
        telefono_emple VARCHAR(10),
        codigo1 VARCHAR(6) NOT NULL,
        FOREIGN KEY (codigo1) REFERENCES sucursales(codigo_suc)
      );


      INSERT INTO empleados VALUES ('EMP_01','ANGELICA','BLANCAS',NULL,'suc-01');
      INSERT INTO empleados VALUES ('EMP_02','DAVID','ASPEITIA',NULL,'suc-02');
      INSERT INTO empleados VALUES ('EMP_03','ANGEL','GALINDO',NULL,'suc-03');
      INSERT INTO empleados VALUES ('EMP_04','ISMAEL','FERNANDEZ',NULL,'suc-04');
      INSERT INTO empleados VALUES ('EMP_05','MAURICIO','ANDA',NULL,'suc-05');
      INSERT INTO empleados VALUES ('EMP_06','ALONSO','BLANCO',NULL,'suc-06');
      INSERT INTO empleados VALUES ('EMP_07','ALMA','SALAZAR',NULL,'suc-07');
      INSERT INTO empleados VALUES ('EMP_08','BLANCA','SANTOS',NULL,'suc-08');
      INSERT INTO empleados VALUES ('EMP_09','IGNACIO','HERNANDEZ',NULL,'suc-09');
      INSERT INTO empleados VALUES ('EMP_10','MAURICIO','MARQUEZ',NULL,'suc-10');



      -- SE CREA LA TABLA "secciones" Y SE GENERA SUS DATOS

      CREATE TABLE secciones (
        id_secc INT UNSIGNED PRIMARY KEY,
        titulo_secc VARCHAR(50) NOT NULL,
        extension_secc VARCHAR(3) NOT NULL,
        num_registro1 VARCHAR(7) NOT NULL,
        FOREIGN KEY (num_registro1) REFERENCES revistas(num_registro_rev)
      );


      INSERT INTO secciones VALUES (1,'espectaculos','esp','REV_098');
      INSERT INTO secciones VALUES (2,'deportes','dep','REV_099');
      INSERT INTO secciones VALUES (3,'politica','pol','REV_100');
      INSERT INTO secciones VALUES (4,'cine','cin','REV_101');
      INSERT INTO secciones VALUES (5,'hogar','hog','REV_102');
      INSERT INTO secciones VALUES (6,'cultura','cul','REV_103');

      --HAY UN SEIS REVISTAS PERO SIETE SECCIONES.
      --¿QUÉ PASA CUANDO HAY MAS REGISTROS EN UNA BASE QUE OTRA?
      -- PUEDE EC¿XISTIR UN VALOR NULL EN OTRA TABLA QUE CONTENGA LA CLAVE FORANEA DE OTRA TABLA?
      -- INSERT INTO secciones VALUES (7,'videojuegos','vid',NULL);

      INSERT INTO secciones VALUES (7,'videojuegos','vid','REV_103');



      -- SE CREA LA TABLA "ejemplares" Y SE GENERA SUS DATOS

      CREATE TABLE ejemplares (
        id_ejemp VARCHAR(3) PRIMARY KEY,
        fecha_emjemp YEAR NOT NULL,
        num_paginas_ejemp INT UNSIGNED, 
        num_vendidos_ejemp INT UNSIGNED,
        num_registro2 VARCHAR(7) NOT NULL,
        FOREIGN KEY (num_registro2) REFERENCES revistas(num_registro_rev)
      );


      INSERT INTO ejemplares VALUES ('M01','2021',56,4855,'REV_098');
      INSERT INTO ejemplares VALUES ('M02','2021',89,1234,'REV_099');
      INSERT INTO ejemplares VALUES ('M03','2021',78,5343,'REV_100');
      INSERT INTO ejemplares VALUES ('M04','2022',90,5654,'REV_101');
      INSERT INTO ejemplares VALUES ('M05','2022',100,3434,'REV_102');
      INSERT INTO ejemplares VALUES ('M06','2021',100,6546,'REV_103');

      -- INSERT INTO ejemplares VALUES ('M07','2022',56,4534,NULL);

      INSERT INTO ejemplares VALUES ('M07','2022',56,4534,'REV_103');



      -- SE CREA LA TABLA "sucursales_revistas" Y SE GENERA SUS DATOS

      CREATE TABLE sucursales_revistas (
        codigo2 VARCHAR(6),
        num_registro3 VARCHAR(7),
        FOREIGN KEY (codigo2) REFERENCES sucursales(codigo_suc),
        FOREIGN KEY (num_registro3) REFERENCES revistas(num_registro_rev)
      );

      INSERT INTO sucursales_revistas VALUES ('suc-01','REV_098');
      INSERT INTO sucursales_revistas VALUES ('suc-02','REV_099');
      INSERT INTO sucursales_revistas VALUES ('suc-03','REV_100');
      INSERT INTO sucursales_revistas VALUES ('suc-04','REV_101');
      INSERT INTO sucursales_revistas VALUES ('suc-05','REV_102');
      INSERT INTO sucursales_revistas VALUES ('suc-06','REV_103');

      -- MISMO CASO. HAY MAS SUCURSALES QUE REVISTAS. YO ASIGNE ALEATORIAMNETE EL num_registro DE LAS RESVITAS AL codigo DE LAS SUCURSALES 
      INSERT INTO sucursales_revistas VALUES ('suc-07','REV_098');
      INSERT INTO sucursales_revistas VALUES ('suc-08','REV_099');
      INSERT INTO sucursales_revistas VALUES ('suc-09','REV_100');
      INSERT INTO sucursales_revistas VALUES ('suc-10','REV_101');





      -- SE CREA LA TABLA "revistas_periodistas" Y SE GENERA SUS DATOS

      CREATE TABLE revistas_periodistas (
        num_registro4 VARCHAR(7),
        nif1 VARCHAR(6),
        FOREIGN KEY (num_registro4) REFERENCES revistas(num_registro_rev),
        FOREIGN KEY (nif1) REFERENCES periodistas(nif_peri)
      );


      -- MISMO CASO. HAY MAS PERIODISTAS QUE REVISTAS. YO ASIGNE ALEATORIAMNETE EL nif1 DE LOS PERIODISTAS AL codigo DE LAS REVISTAS 

      INSERT INTO revistas_periodistas VALUES ('REV_098','PER_01');
      INSERT INTO revistas_periodistas VALUES ('REV_099','PER_02');
      INSERT INTO revistas_periodistas VALUES ('REV_100','PER_03');
      INSERT INTO revistas_periodistas VALUES ('REV_101','PER_04');
      INSERT INTO revistas_periodistas VALUES ('REV_102','PER_05');
      INSERT INTO revistas_periodistas VALUES ('REV_103','PER_06');
      INSERT INTO revistas_periodistas VALUES ('REV_098','PER_07');
      INSERT INTO revistas_periodistas VALUES ('REV_099','PER_08');
      INSERT INTO revistas_periodistas VALUES ('REV_100','PER_09');
      INSERT INTO revistas_periodistas VALUES ('REV_101','PER_10');
      INSERT INTO revistas_periodistas VALUES ('REV_102','PER_11');
      INSERT INTO revistas_periodistas VALUES ('REV_103','PER_12');




1:N  SE crean claves foraneas en cada entidad, las cuales corresponden a la claves primarias de la entidad origen.

N:M Se crea una nueva tabla (derivada) cuyos atributos son las claves primarias de cada entidad.



