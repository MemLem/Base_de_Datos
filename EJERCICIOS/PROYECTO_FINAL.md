# Proyecto Final de base de datos.
### Indicaciones de lo que se debe realizar

● Diseña el modelo entidad-relación del siguiente problema.

● Crea el script para la base de datos.
Proveedores

Tenemos que diseñar una base de datos sobre proveedores y disponemos de
la siguiente información:

● De cada proveedor conocemos su nombre, dirección, ciudad, provincia y
un código de proveedor que será único para cada uno de ellos.

● Nos interesa llevar un control de las piezas que nos suministra cada
proveedor. Es importante conocer la cantidad de las diferentes piezas
que nos suministra y en qué fecha lo hace. Tenga en cuenta que un
mismo proveedor nos puede suministrar una pieza con el mismo código
en diferentes fechas. El diseño de la base de datos debe permitir
almacenar un histórico con todas las fechas y las cantidades que nos ha
proporcionado un proveedor.

● Una misma pieza puede ser suministrada por diferentes proveedores.

● De cada pieza conocemos un código que será único, nombre, color,
precio y categoría.

● Pueden existir varias categorías y para cada categoría hay un nombre y
un código de categoría único.

● Una pieza sólo puede pertenecer a una categoría.


![image](https://user-images.githubusercontent.com/75552884/171750311-c19d50bb-87e2-4367-bb59-3b00d2470e67.png)






- ESQUEMA SQL: https://www.db-fiddle.com/f/ov9TMGri4QEXwGrHJBbTuU/2

            CREATE DATABASE proveedores;

            USE proveedores;

            CREATE TABLE repartidores(
              cod_rep VARCHAR(15) PRIMARY KEY,
              nombre_rep VARCHAR(30) NOT NULL, 
              direccion_rep VARCHAR(80) NOT NULL,
              ciudad_rep VARCHAR(30) NOT NULL,
              provincia_rep VARCHAR(30) NOT NULL
            );

            CREATE TABLE categorias(
              cod_categoria VARCHAR(8) PRIMARY KEY,
              nombre_cate VARCHAR(10) NOT NULL
            );

            CREATE TABLE piezas(
              cod_pieza VARCHAR(8) PRIMARY KEY,
              cod_categoria1 VARCHAR(8) NOT NULL, 
              nombre_pieza VARCHAR(10) NOT NULL,
              color VARCHAR(10) NOT NULL,
              precio FLOAT UNSIGNED NOT NULL,
              categoria VARCHAR(10) NOT NULL,
              FOREIGN KEY (cod_categoria1) REFERENCES categorias(cod_categoria)
            );

            CREATE TABLE provedores_piezas(
              cod_rep1 VARCHAR(15),
              cod_pieza1 VARCHAR(8),
              cantidad INT UNSIGNED NOT NULL,
              fecha DATE NOT NULL,
              FOREIGN KEY (cod_rep1) REFERENCES repartidores(cod_rep),
              FOREIGN KEY (cod_pieza1) REFERENCES piezas(cod_pieza)
            );
