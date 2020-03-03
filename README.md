# Movimiento_Datos_Alumno4_BBDD



### 3. Realiza una exportación de la estructura de todas las tablas de la base de datos usando el comando expdp de Oracle Data Pump utilizando un DBLink desde otra base de datos. Prueba todas las posibles opciones que ofrece dicho comando y documentándolas adecuadamente.

### 4. Intenta realizar operaciones similares de importación y exportación con una herramienta gráfica de administración de MySQL, documentando el proceso.

Vamos a nuestro phpMyAdmin del cloud en sql.alejandro.gonzalonazareno.org

![](/imagenes/PhpMyAdmin.png)

Vamos a exportar la base de datos nextcloud1 a un usuario que crearemos posteriormente.

![](/imagenes/PhpMyAdmin2.png)

Damos click a Exportar Y le damos a Exportación personalizada.

Activamos la opción para renombrar la base de datos.

![](/imagenes/PhpMyAdmin3.png)


Y le damos click a Continuar abajo del todo.

![](/imagenes/PhpMyAdmin4.png)


Vamos ahora a un usuario que crearemos en nuestra base de datos tortilla
```
MariaDB [(none)]> create database nextcloudexport;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> create user pruebamov identified by 'pruebamov';
Query OK, 0 rows affected (0.09 sec)

MariaDB [(none)]> grant all privileges on nextcloudexport.* to pruebamov;
Query OK, 0 rows affected (0.03 sec)

MariaDB [(none)]> flush privileges;
Query OK, 0 rows affected (0.02 sec)

```

Ahora entramos al usuario y damos click a Importar->Seleccionar archivo

![](/imagenes/PhpMyAdmin6.png)

![](/imagenes/PhpMyAdmin5.png)


Y le damos a Continuar.


Después de varios minutos observaremos que tenemos la estructura de tablas creada

![](/imagenes/PhpMyAdmin7.png)
### 5. Exporta todos los documentos de las colecciones de MongoDB que tengan más de cuatro documentos e impórtalos en otra base de datos .
