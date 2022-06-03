En la BD utilizada (https://www.db-fiddle.com/f/q1JxBLim4V94m9vfQjRXMd/12) en clase realiza las siguientes consultas:

* La tabla empleado

      USE editorial;

      SELECT * FROM empleados;

![image](https://user-images.githubusercontent.com/75552884/170736175-8df7edc5-0f46-4f86-a48b-107e6bc0091a.png)



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

      USE editorial; 

      SELECT nif_peri, nombre_peri, apellido_peri, titulo_rev, codigo_suc FROM periodistas
      INNER JOIN revistas_periodistas ON periodistas.nif_peri = revistas_periodistas.nif_peri1
      INNER JOIN revistas ON revistas.num_registro_rev = revistas_periodistas.num_registro_rev4
      INNER JOIN sucursales_revistas ON revistas.num_registro_rev = sucursales_revistas.num_registro_rev3
      INNER JOIN sucursales ON sucursales.codigo_suc = sucursales_revistas.codigo_suc2
      WHERE titulo_rev = 'POLITICA HOY'

![image](https://user-images.githubusercontent.com/75552884/171052708-55786cd9-8ab6-4d6d-b31b-9c72d8c88518.png)



* Mustra que seccion esta en x revista, en que sucursal se imprimio y que empleados estan en esa sucursal.

      USE editorial; 

      SELECT titulo_secc, titulo_rev, codigo_suc, nombre_emple, apellido_emple FROM secciones
      INNER JOIN revistas ON secciones.num_registro_rev1 = revistas.num_registro_rev
      INNER JOIN sucursales_revistas ON revistas.num_registro_rev = sucursales_revistas.num_registro_rev3
      INNER JOIN sucursales ON sucursales.codigo_suc = sucursales_revistas.codigo_suc2
      INNER JOIN empleados ON sucursales.codigo_suc = empleados.codigo_suc1
      WHERE titulo_rev = 'POLITICA HOY'

![image](https://user-images.githubusercontent.com/75552884/171054917-3f865816-547d-484f-b15b-b90413b3f957.png)


* En la tabla peridistas muestra solo los que escriban sobre cine

      USE editorial; 

      SELECT * FROM periodistas
      WHERE especialidad_peri = 'CINE'

![image](https://user-images.githubusercontent.com/75552884/171055237-fac5f937-0dc1-45e1-b78a-40b7fc29cc2d.png)

* De la tabla revistas muestra las que sean de publicacion quincenal

      USE editorial; 

      SELECT * FROM revistas
      WHERE periodicidad_rev = 'QUINCENAL'

![image](https://user-images.githubusercontent.com/75552884/171055430-b52e1e50-e9e5-4300-82e8-ee87133b2df4.png)

* Muestra el nombre de ka revista que se hayan impreso despues del 30 de septiembre del 2021

      USE editorial;

      SELECT titulo_rev, fecha_emjemp FROM ejemplares
      INNER JOIN revistas ON ejemplares.num_registro_rev2 = revistas.num_registro_rev
      WHERE fecha_emjemp > "2021-09-30"

![image](https://user-images.githubusercontent.com/75552884/171056811-937c97ac-4257-444e-af28-5e794a0ad5bc.png)

* Muestra el nombre de la revista que se haya publicado en la sucursal 1 cuyos ejemplares tengan más de 80 páginas.

https://www.db-fiddle.com/f/iAUjGLoFoHtam2pK68Xh1B/1


RESPUESTAS: https://www.db-fiddle.com/f/iAUjGLoFoHtam2pK68Xh1B/0

EJEMPLO
https://www.db-fiddle.com/f/f5YQQo1MCXhD95LFCdiYFB/13


https://www.db-fiddle.com/f/uQShSiNHxLbsUXhW2bbe8D/4
