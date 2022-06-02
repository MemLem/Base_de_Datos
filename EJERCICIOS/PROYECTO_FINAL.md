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






![image](https://user-images.githubusercontent.com/75552884/171548212-2e494e97-39c7-45ea-914a-9b4e17c2f66c.png)




- ESQUEMA SQL: https://www.db-fiddle.com/f/ov9TMGri4QEXwGrHJBbTuU/0

      CREATE DATABASE almacen;

      USE almacen;

      CREATE TABLE proveedores(
        cod_proveedor INT UNSIGNED PRIMARY KEY,
        nombre_prov VARCHAR(30) NOT NULL, 
        direccion_prov VARCHAR(80) NOT NULL,
        ciudad_prov VARCHAR(30) NOT NULL,
        provincia_prov VARCHAR(30) NOT NULL
      );

      CREATE TABLE categorias(
        cod_categoria VARCHAR(8) PRIMARY KEY,
        nombre_cate VARCHAR(10) NOT NULL
      );

      CREATE TABLE piezas(
        id_entrega VARCHAR(15) PRIMARY KEY,
        cod_categoria1 VARCHAR(8) NOT NULL, 
        codigo_pieza VARCHAR(8) NOT NULL,
        nombre_pieza VARCHAR(10) NOT NULL,
        cantidad INT UNSIGNED NOT NULL,
        fecha DATE NOT NULL,
        color VARCHAR(10),
        precio FLOAT UNSIGNED NOT NULL,
        FOREIGN KEY (cod_categoria1) REFERENCES categorias(cod_categoria)
      );

