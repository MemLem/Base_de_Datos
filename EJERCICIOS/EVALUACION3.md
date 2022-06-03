
## Práctica 4
### Data warehouse

Objetivo: Demostrar la identificación de los elementos que componen data warehouse y
su esquema

Ejercicio:

1. ¿Qué es un DataWarehouse?(valor 2)

        Es un sistema que agrega y combina información de diferentes fuentes en un almacén de datos único y centralizado. Data warehouse permite ejecutar análisis potentes en grandes volúmenes (petabytes), cuestión que una base de datos estándar no puede.

2. Realiza un diseño del modelo en estrella (valor 2)

3. Realiza un diseño del modelo copo de nieve (valor 2)


## Práctica 7
### Funciones en SQL
Objetivo: Demostrar el uso y aplicación en una base de datos para mejorar la gestión

DataBase "tienda_informatica": https://www.db-fiddle.com/f/5tnmKj19B6eguYfFcrh6Jf/0

Ejercicio:

1. Calcula el número total de productos que hay en la tabla productos. (valor 4.5)

        USE tienda_informatica;

        SELECT COUNT(nombre_producto) FROM productos

![image](https://user-images.githubusercontent.com/75552884/171664023-615b3696-59a1-4220-bcf6-8255474d1798.png)



2. Muestra el número total de productos que tiene cada uno de los fabricantes. El listado
también debe incluir los fabricantes que no tienen ningún producto. El resultado
mostrará dos columnas, una con el nombre del fabricante y otra con el número de
productos que tiene. Ordene el resultado descendentemente por el número de
productos. (valor 4.5)

        USE tienda_informatica;

        SELECT nombre_fabricante, COUNT(codigo_producto) FROM fabricante
        INNER JOIN productos ON productos.id_fabricante1 = fabricante.id_fabricante
        GROUP BY(nombre_fabricante)
        ORDER BY (COUNT(codigo_producto)) DESC;
        
![image](https://user-images.githubusercontent.com/75552884/171881515-37f2742f-9086-4675-b57d-8723fab34921.png)



3. Muestra el precio máximo, precio mínimo y precio medio de los productos de cada
uno de los fabricantes. El resultado mostrará el nombre del fabricante junto con los
datos que se solicitan. (valor 4.5)

        USE tienda_informatica;

        SELECT nombre_fabricante,
            MAX(precio_producto), 	
            MIN(precio_producto), 
            AVG(precio_producto) FROM productos
        INNER JOIN fabricante 
            ON productos.id_fabricante1 = fabricante.id_fabricante
        GROUP BY(nombre_fabricante);

![image](https://user-images.githubusercontent.com/75552884/171664797-d102e75e-3544-46f5-a8c8-f1086d07eb79.png)


4. Muestra el nombre de cada fabricante, junto con el precio máximo, precio mínimo,
precio medio y el número total de productos de los fabricantes que tienen un precio
medio superior a 200€. Es necesario mostrar el nombre del fabricante. (valor 4.5)


        USE tienda_informatica;

        SELECT nombre_fabricante,
                COUNT(nombre_producto),
                MAX(precio_producto), 	
            MIN(precio_producto), 
            AVG(precio_producto) FROM productos
        INNER JOIN fabricante 
                ON productos.id_fabricante1 = fabricante.id_fabricante
        GROUP BY(nombre_fabricante);
        -- WHERE AVG(precio_producto) > 200;

## Práctica 8.
### Disparadores (Triggers)

Objetivo: Demostrar las operaciones que se realizan en una base de datos.

Ejercicio: Crea una base de datos llamada test que contenga una tabla llamada
alumnos con las siguientes columnas. (valor 18)

Evaluación:

Creación de la base de datos : 9 puntos.

Creación de los Disparadores(Triggers): 9 puntos.

Tabla alumnos:

● id (entero sin signo)

● nombre (cadena de caracteres)

● apellido1 (cadena de caracteres)

● apellido2 (cadena de caracteres)

● nota (número real)

Una vez creada la tabla escriba dos triggers con las siguientes características:

● Trigger 1: trigger_check_nota_before_insert

  o Se ejecuta sobre la tabla alumnos.
  
  o Se ejecuta antes de una operación de inserción.
  
  o Si el nuevo valor de la nota que se quiere insertar es negativo, se guarda
  como 0.
  
  o Si el nuevo valor de la nota que se quiere insertar es mayor que 10, se
  guarda como 10.

● Trigger2 : trigger_check_nota_before_update
  o Se ejecuta sobre la tabla alumnos.
  
  o Se ejecuta antes de una operación de actualización.
  
  o Si el nuevo valor de la nota que se quiere actualizar es negativo, se guarda
  como 0.
  
  o Si el nuevo valor de la nota que se quiere actualizar es mayor que 10, se
  guarda como 10.
  
Una vez creados los triggers escribe varias sentencias de inserción y actualización
sobre la tabla alumnos y verifica que los triggers se están ejecutando
correctamente.
