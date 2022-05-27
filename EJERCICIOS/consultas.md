En la BD utilizada (https://www.db-fiddle.com/f/q1JxBLim4V94m9vfQjRXMd/9) en clase realiza las siguientes consultas:

* La tabla empleado

      USE editorial;

      SELECT * FROM empleados;

![image](https://user-images.githubusercontent.com/75552884/170730280-d52fc6e5-1638-4458-a464-53eee72f549a.png)


* Los titulos de las revistas

      USE editorial;

      SELECT titulo_rev FROM revistas;

![image](https://user-images.githubusercontent.com/75552884/170729514-ba798086-1202-4fd8-a426-13067e9f3258.png)

* Los nombres, apellidos y especialidad de los periodostas

      USE editorial;

      SELECT nombre_peri, apellido_peri, especialidad_peri FROM periodistas;

![image](https://user-images.githubusercontent.com/75552884/170729946-0189fb3d-14c1-475d-ba75-10986a9b206c.png)


* Muestra los empleados que estan en x sucursal

      USE editorial;

      SELECT nif_emple, nombre_emple, apellido_emple, codigo_suc FROM empleados
      INNER JOIN sucursales ON empleados.codigo_suc1 = sucursales.codigo_suc
      WHERE codigo_suc = 'suc-02'


![image](https://user-images.githubusercontent.com/75552884/170735137-6a7f1dfe-e228-4aca-a96e-d385708dabfc.png)

* Muestra que periodistas colaboraron en x revista y en que sucursal se publico la revista
* Mustra que seccion esta en x revista, en que sucursal se imprimio y que empleados estan en esa sucursal.
* En la tabla peridistas muestra solo los que escriban sobre cine
* De la tabla revistas muestra las que sean de publicacion quincenal
* Muestra el nombre de ka revista que se hayan impreso despues del 30 de septiembre del 2021
* Muestra el nombre de la revista que se haya publicado en la sucursal 1 cuyos ejemplares tengan más de 80 páginas.

https://www.db-fiddle.com/f/iAUjGLoFoHtam2pK68Xh1B/1

EJEMPLO
https://www.db-fiddle.com/f/f5YQQo1MCXhD95LFCdiYFB/13
