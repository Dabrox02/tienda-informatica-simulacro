### Consultas sobre una tabla

1. Lista el nombre de todos los productos que hay en la tabla `producto`.

   ```sql
   SELECT nombre FROM producto;
   ```

2. Lista los nombres y los precios de todos los productos de la tabla `producto`.

   ```sql
   SELECT nombre, precio FROM producto;
   ```

3. Lista todas las columnas de la tabla `producto`.

   ```sql
   SELECT * FROM producto;
   ```

4. Lista el nombre de los productos, el `precio` en euros y el `precio` en dólares estadounidenses (USD).

   ```sql
   SELECT nombre, precio as precio_CAD, ROUND(precio * 0.68, 2) as precio_EUR, ROUND(precio * 0.73, 2) as precio_USD FROM producto;
   ```

5. Lista el nombre de los productos, el `precio` en euros y el `precio` en dólares estadounidenses (USD). Utiliza los siguientes alias para las columnas: `nombre de producto`, `euros`, `dólares`.

   ```sql
   SELECT nombre, ROUND(precio * 0.68, 2) as euros, ROUND(precio * 0.73, 2) as dolares FROM producto;
   ```

6. Lista los nombres y los precios de todos los productos de la tabla `producto`, convirtiendo los nombres a mayúscula.

   ```sql
   SELECT UPPER(nombre) as NOMBRE, precio FROM producto; 
   ```

7. Lista los nombres y los precios de todos los productos de la tabla `producto`, convirtiendo los nombres a minúscula.

   ```sql
   SELECT LOWER(nombre) as nombre, precio FROM producto; 
   ```

8. Lista el nombre de todos los fabricantes en una columna, y en otra columna obtenga en mayúsculas los dos primeros caracteres del nombre del fabricante.

   ```sql
   SELECT nombre, UPPER(SUBSTRING(nombre, 1,2)) as Primeros_2 FROM fabricante; 
   ```

9. Lista los nombres y los precios de todos los `productos` de la tabla producto, redondeando el valor del precio.

   ```sql
   SELECT nombre, ROUND(precio, 0) as precio_redondeado FROM producto;
   ```

10. Lista los nombres y los precios de todos los `productos` de la tabla producto, truncando el valor del precio para mostrarlo sin ninguna cifra decimal.

   ```sql
   SELECT nombre, TRUNCATE(precio, ".") as precio_truncado FROM producto;
   ```

11. Lista el identificador de los fabricantes que tienen productos en la tabla `producto`.

   ```sql
   SELECT fab.id FROM fabricante as fab 
   INNER JOIN producto as prod
   ON fab.id = prod.id_fabricante;
   ```

12. Lista el identificador de los fabricantes que tienen `productos` en la tabla producto, eliminando los identificadores que aparecen repetidos.

   ```sql
   SELECT fab.id FROM fabricante as fab 
   INNER JOIN producto as prod
   ON fab.id = prod.id_fabricante
   GROUP BY fab.id;
   ```

13. Lista los nombres de los fabricantes ordenados de forma ascendente.

   ```sql
   SELECT nombre FROM fabricante ORDER BY nombre ASC;
   ```

14. Lista los nombres de los fabricantes ordenados de forma descendente.

   ```sql
   SELECT nombre FROM fabricante ORDER BY nombre DESC;
   ```

15. Lista los nombres de los productos ordenados en primer lugar por el nombre de forma ascendente y en segundo lugar por el precio de forma descendente.

   ```sql
   SELECT nombre, precio FROM producto
   ORDER BY nombre ASC, precio DESC;
   ```

16. Devuelve una lista con las 5 primeras filas de la tabla `fabricante`.

   ```sql
   SELECT * FROM fabricante LIMIT 5;
   ```

17. Devuelve una lista con 2 filas a partir de la cuarta fila de la tabla `fabricante`. La cuarta fila también se debe incluir en la respuesta.

   ```sql
   SELECT * FROM fabricante WHERE id >= 4 ORDER BY id ASC LIMIT 2;
   ```

18. Lista el nombre y el precio del producto más barato. (Utilice solamente las cláusulas `ORDER BY` y `LIMIT`)

   ```sql
   SELECT nombre, precio FROM producto ORDER BY precio ASC LIMIT 1;
   ```

19. Lista el nombre y el precio del producto más caro. (Utilice solamente las cláusulas `ORDER BY` y `LIMIT`)

   ```sql
   SELECT nombre, precio FROM producto ORDER BY precio DESC LIMIT 1;
   ```

20. Lista el nombre de todos los productos del fabricante cuyo identificador de fabricante es igual a 2.

   ```sql
   SELECT nombre FROM producto WHERE id_fabricante = 2;
   ```