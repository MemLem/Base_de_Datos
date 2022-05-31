En base al ejercicio (https://www.db-fiddle.com/f/kDgwhn4K8WTeUwXwQX35BK/2) realiza las siguientes consultas

Por error se capturaron mal los siguientes datos, se deben corregir.

![image](https://user-images.githubusercontent.com/91554777/171071745-a92dfd2f-2cf2-4bed-a081-8728f93fc005.png)


    USE tienda;

    UPDATE producto
    SET nom_prod = 'SHAMPOO 500 ML'
    WHERE clave_prod = 119;

    UPDATE producto
    SET precio = 90.99
    WHERE nom_prod = 'SHAMPOO 500 ML';

    UPDATE producto
    SET precio = 20
    WHERE nom_prod = 'SAL BOLSA';

    UPDATE producto
    SET nom_prod = 'JABON POLVO 1KG'
    WHERE clave_prod = 252;

    UPDATE producto
    SET precio = 56.9
    WHERE nom_prod = 'JABON POLVO 1KG';

    UPDATE cliente 
    SET nom_clie = 'Daniel Sánchez'
    WHERE clave_clie = 111;

    UPDATE cliente 
    SET clave_clie = 107
    WHERE nom_clie = 'Pedro Olmedo';

    SELECT * FROM producto;
    SELECT * FROM cliente;


Realiza las siguientes notas

    INSERT INTO nota VALUES (1, 226, 67, 5, NULL);
    INSERT INTO nota VALUES (2, 173, 45, 4, NULL);
    INSERT INTO nota VALUES (3, 12, 155, 6, NULL);
    INSERT INTO nota VALUES (4, 173, 23, 2, NULL);


![image](https://user-images.githubusercontent.com/91554777/171071841-ef5e3549-0235-4c77-846d-62aee10873cf.png)


Agrega un campo en nota que se llame IVA, sabiendo el IVA es de 16% este campo contendrá el valor que corresponda al IVA del subtotal, además de otro campo total donde se mostrará el total de la nota con el IVA.

