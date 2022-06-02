## Práctica 3.
### Introducción a SQL
Objetivo: Demostrar la correcta identificación de los conceptos del lenguaje SQL
Ejercicio:

1. Menciona los comandos DML (DML = Data Manipulation Language): (valor .85):

        - SELECT: Sirve para consultar resgistros de una BD que satisfacen un criterio detemrinado.
        - INSERT: Encargado de cargar lostes de datos en la BD en uan unica operaicón.
        - UPDATE: Se utiliza para modificar los valores de los campos y registros especificados.
        - DELETE: Elimina resgitros de una tabla. 


2. Menciona 3 tipos de datos que existen: (valor .85)
   
        - Caracter
        - Númerico
        - Fecha y hora


3. ¿Qué diferencia existe entre TRUNCATE y DELETE?(valor .85)

        - DELETE: Elimina una serie de registros de una tabla y permite el borrado selectivo.
        - TRUNCATE: Elimina todo el contenido de la tabla, pero sin elminar la tabla. También resetea los contadores.
        

4. ¿Para qué se utiliza el atributo UNIQUE?(valor .85)

        Para impedir que se puedan repetir datos en un atributo.

5. ¿Qué diferencia hay entre los tipos de datos VARCHAR y CHAR? (valor .85)

        - CHAR(): Define una cadena de caracteres de longitud fija, la cual es especificada por el usuario.
        - VARCHAR(): Define una cadena de caracteres de longitud variable con una longitud maxima especificada por el usuario.


6. Defina brevemente el significado de las siglas SQL(valor .85)

        SQL (Structured Query Language) es un lenguaje estándar e interactivo de acceso a bases de datos relacionales que permite especificar diversos tipos de operaciones en ellas, gracias a la utilización del álgebra y de cálculos relacionales.

7. Defina brevemente qué es MySQL WorkBench (valor .85)

        Es un editor visual de base de datos MySQL basado en software libre que cuenta con el respaldo oficial de MySQL. Una herramienta que lo caracteriza es su editor de diagramas

## Práctica 5.
### Gestores de base de datos

Objetivo: Categorizar los distintos gestores de base de datos que existen y señalar las
ventajas y desventajas

Evaluación: Conoce los tipos de gestores de base de datos 3 puntos.

Domina sus diferencias de los gestores de base de datos mencionados 3 puntos

Ejercicio:

En un mapa conceptual presenta 3 gestores de bases de datos, sus características
principales, las ventajas y desventajas. (valor 6)

![image](https://user-images.githubusercontent.com/75552884/170532180-cdaa559d-10db-4ee6-be1a-3a884c6d04d4.png)



## Práctica 6.
### Herramienta en línea y ejercicio necesarios para realizar las prácticas

Creación de base de datos.

Objetivo: Demostrar mediante la creación de una base de datos el uso y la aplicación de
las funciones

Ejercicio: Creación de la base de datos (valor 18 puntos)

Tienda de informática

![image](https://user-images.githubusercontent.com/91554777/170415101-717bca19-3644-46a9-8a57-8d5940c5d283.png)




Modelo entidad/relación

![image](https://user-images.githubusercontent.com/75552884/170527911-0fe18ec8-0770-4164-9688-69be21582b9e.png)





Base de datos para MySQL

- Esquema SQL: https://www.db-fiddle.com/f/5tnmKj19B6eguYfFcrh6Jf/0

        CREATE DATABASE tienda_informatica;
        USE tienda_informatica;

        CREATE TABLE fabricante(
          id_fabricante INT UNSIGNED PRIMARY KEY,
          nombre_fabricante VARCHAR(50)
        );


        INSERT INTO fabricante VALUES (1,'SEAGATE');
        INSERT INTO fabricante VALUES (2,'CRUCIAL' );
        INSERT INTO fabricante VALUES (3,'SAMSUNG');
        INSERT INTO fabricante VALUES (4,'GIGABYTE');
        INSERT INTO fabricante VALUES (5,'ASUS');
        INSERT INTO fabricante VALUES (6,'LENOVO');
        INSERT INTO fabricante VALUES (7,'HP');



        CREATE TABLE productos(
          codigo_producto VARCHAR(5) PRIMARY KEY,
          nombre_producto VARCHAR(50),
          precio_producto FLOAT,
          id_fabricante1 INT UNSIGNED,
          FOREIGN KEY (id_fabricante1) REFERENCES fabricante(id_fabricante)
        );


        INSERT INTO productos VALUES ('DD-23', 'Disco duro SATA3 1TB', 86.99, 1);
        INSERT INTO productos VALUES ('MM-34', 'Memoria RAM DDR4 8GB', 120.6, 2);
        INSERT INTO productos VALUES ('DD-98', 'Disco SSD 1TB', 150.99, 3);
        INSERT INTO productos VALUES ('MM-98', 'GeForce GTX 1050Ti', 185.7, 4);
        INSERT INTO productos VALUES ('MM-23', 'GeForce GTX 1080 Xtreme', 755.6, 2);
        INSERT INTO productos VALUES ('MT-12', 'Monitor 24 LED Full HD', 202.1, 5);
        INSERT INTO productos VALUES ('MT-08', 'Monitor 27 LED Full HD', 245.99, 5);
        INSERT INTO productos VALUES ('LP-19', 'Portátil Yoga 520', 559.2, 6);
        INSERT INTO productos VALUES ('LP-11', 'Portátil Ideapd 320', 444.2, 6);
        INSERT INTO productos VALUES ('IM-56', 'Impresora HP Deskjet 3720', 59.99, 7);
        INSERT INTO productos VALUES ('IP-54', 'Impresora HP Laserjet Pro M26nw', 180.3, 7);

