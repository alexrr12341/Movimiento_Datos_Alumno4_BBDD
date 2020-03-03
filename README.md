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
### 5. Exporta todos los documentos de las colecciones de MongoDB que tengan más de cuatro documentos e impórtalos en otra base de datos.

Vamos a exportar los documentos que contienen las colecciones de MongoDB de nuestro usuario user

```
root@mongo:/home/vagrant# mongo --host localhost -u user -p --authenticationDatabase clientedb
connecting to: mongodb://localhost:27017/?authSource=clientedb&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("602e105c-968e-49d7-8d33-ab13f7be473f") }
MongoDB server version: 4.0.12

> use clientedb
switched to db clientedb
> show collections
cps
phptest
productos


> db.productos.find()
{ "_id" : "ac7", "name" : "AC7 Phone", "brand" : "ACME", "type" : "phone", "price" : 320, "warranty_years" : 1, "available" : false }
{ "_id" : ObjectId("507d95d5719dbef170f15bf9"), "name" : "AC3 Series Charger", "type" : [ "accessory", "charger" ], "price" : 19, "warranty_years" : 0.25, "for" : [ "ac3", "ac7", "ac9" ] }
{ "_id" : ObjectId("507d95d5719dbef170f15bfa"), "name" : "AC3 Case Green", "type" : [ "accessory", "case" ], "color" : "green", "price" : 12, "warranty_years" : 0 }
{ "_id" : ObjectId("507d95d5719dbef170f15bfb"), "name" : "Phone Extended Warranty", "type" : "warranty", "price" : 38, "warranty_years" : 2, "for" : [ "ac3", "ac7", "ac9", "qp7", "qp8", "qp9" ] }
{ "_id" : "ac3", "name" : "AC3 Phone", "brand" : "ACME", "type" : "phone", "price" : 200, "warranty_years" : 1, "available" : true }
{ "_id" : ObjectId("507d95d5719dbef170f15bfc"), "name" : "AC3 Case Black", "type" : [ "accessory", "case" ], "color" : "black", "price" : 12.5, "warranty_years" : 0.25, "available" : false, "for" : "ac3" }
{ "_id" : ObjectId("507d95d5719dbef170f15bfd"), "name" : "AC3 Case Red", "type" : [ "accessory", "case" ], "color" : "red", "price" : 12, "warranty_years" : 0.25, "available" : true, "for" : "ac3" }
{ "_id" : ObjectId("507d95d5719dbef170f15bfe"), "name" : "Phone Service Basic Plan", "type" : "service", "monthly_price" : 40, "limits" : { "voice" : { "units" : "minutes", "n" : 400, "over_rate" : 0.05 }, "data" : { "units" : "gigabytes", "n" : 20, "over_rate" : 1 }, "sms" : { "units" : "texts sent", "n" : 100, "over_rate" : 0.001 } }, "term_years" : 2 }
{ "_id" : ObjectId("507d95d5719dbef170f15bff"), "name" : "Phone Service Core Plan", "type" : "service", "monthly_price" : 60, "limits" : { "voice" : { "units" : "minutes", "n" : 1000, "over_rate" : 0.05 }, "data" : { "n" : "unlimited", "over_rate" : 0 }, "sms" : { "n" : "unlimited", "over_rate" : 0 } }, "term_years" : 1 }
{ "_id" : ObjectId("507d95d5719dbef170f15c00"), "name" : "Phone Service Family Plan", "type" : "service", "monthly_price" : 90, "limits" : { "voice" : { "units" : "minutes", "n" : 1200, "over_rate" : 0.05 }, "data" : { "n" : "unlimited", "over_rate" : 0 }, "sms" : { "n" : "unlimited", "over_rate" : 0 } }, "sales_tax" : true, "term_years" : 2 }
{ "_id" : ObjectId("507d95d5719dbef170f15c01"), "name" : "Cable TV Basic Service Package", "type" : "tv", "monthly_price" : 50, "term_years" : 2, "cancel_penalty" : 25, "sales_tax" : true, "additional_tarriffs" : [ { "kind" : "federal tarriff", "amount" : { "percent_of_service" : 0.06 } }, { "kind" : "misc tarriff", "amount" : 2.25 } ] }

> db.cps.find()
{ "_id" : "35004", "city" : "ACMAR", "loc" : [ -86.51557, 33.584132 ], "pop" : 6055, "state" : "AL" }
{ "_id" : "35005", "city" : "ADAMSVILLE", "loc" : [ -86.959727, 33.588437 ], "pop" : 10616, "state" : "AL" }
{ "_id" : "35007", "city" : "KEYSTONE", "loc" : [ -86.812861, 33.236868 ], "pop" : 14218, "state" : "AL" }
{ "_id" : "35006", "city" : "ADGER", "loc" : [ -87.167455, 33.434277 ], "pop" : 3205, "state" : "AL" }
{ "_id" : "35010", "city" : "NEW SITE", "loc" : [ -85.951086, 32.941445 ], "pop" : 19942, "state" : "AL" }
{ "_id" : "35016", "city" : "ARAB", "loc" : [ -86.489638, 34.328339 ], "pop" : 13650, "state" : "AL" }
{ "_id" : "35019", "city" : "BAILEYTON", "loc" : [ -86.621299, 34.268298 ], "pop" : 1781, "state" : "AL" }
{ "_id" : "35020", "city" : "BESSEMER", "loc" : [ -86.947547, 33.409002 ], "pop" : 40549, "state" : "AL" }
{ "_id" : "35023", "city" : "HUEYTOWN", "loc" : [ -86.999607, 33.414625 ], "pop" : 39677, "state" : "AL" }
{ "_id" : "35031", "city" : "BLOUNTSVILLE", "loc" : [ -86.568628, 34.092937 ], "pop" : 9058, "state" : "AL" }
{ "_id" : "35033", "city" : "BREMEN", "loc" : [ -87.004281, 33.973664 ], "pop" : 3448, "state" : "AL" }
{ "_id" : "35034", "city" : "BRENT", "loc" : [ -87.211387, 32.93567 ], "pop" : 3791, "state" : "AL" }
{ "_id" : "35035", "city" : "BRIERFIELD", "loc" : [ -86.951672, 33.042747 ], "pop" : 1282, "state" : "AL" }
{ "_id" : "35040", "city" : "CALERA", "loc" : [ -86.755987, 33.1098 ], "pop" : 4675, "state" : "AL" }
{ "_id" : "35042", "city" : "CENTREVILLE", "loc" : [ -87.11924, 32.950324 ], "pop" : 4902, "state" : "AL" }
{ "_id" : "35014", "city" : "ALPINE", "loc" : [ -86.208934, 33.331165 ], "pop" : 3062, "state" : "AL" }
{ "_id" : "35043", "city" : "CHELSEA", "loc" : [ -86.614132, 33.371582 ], "pop" : 4781, "state" : "AL" }
{ "_id" : "35044", "city" : "COOSA PINES", "loc" : [ -86.337622, 33.266928 ], "pop" : 7985, "state" : "AL" }
{ "_id" : "35049", "city" : "CLEVELAND", "loc" : [ -86.559355, 33.992106 ], "pop" : 2369, "state" : "AL" }
{ "_id" : "35051", "city" : "COLUMBIANA", "loc" : [ -86.616145, 33.176964 ], "pop" : 4486, "state" : "AL" }

```


Vamos a realizar un script para que podamos detectar si una coleción tiene mas de 4 documentos
```

#!/bin/bash
mongo clientedb --host localhost -u user -p user --authenticationDatabase clientedb --eval 'printjson(db.getCollectionNames())' > hola.txt
cuenta=`cat hola.txt | wc -l`

cuenta2=$((cuenta-4))

coleciones=`cat hola.txt | tail -n $cuenta2`
echo '' > colect.txt
for i in $coleciones
do
        col=`echo $i | cut -d '"' -f 2`
        echo $col >> colect.txt
done
cuentacol=`cat colect.txt | wc -l`
cuentacol2=$((cuentacol-2))
colect=`cat colect.txt | tail -n $cuentacol2 | head -n -1`
for i in $colect
do
        cuentadocs=`mongo clientedb --host localhost -u user -p user --authenticationDatabase clientedb --eval "db.$i.count()" | tail -n $cuenta2`
        if [ $cuentadocs -gt 4 ];
        then
                mongoexport --collection=$i --db=clientedb --out $i.json --username=user --password=user
        fi
done


```

Vamos a ejecutar el script y deberá salirnos un cps.json y product.json
```
root@mongo:/home/vagrant# ls
coleciones.txt	colect.txt  mongo  script.sh

root@mongo:/home/vagrant# sh script.sh 
2020-03-03T18:47:35.228+0000	connected to: localhost
2020-03-03T18:47:35.691+0000	exported 29467 records
2020-03-03T18:47:35.838+0000	connected to: localhost
2020-03-03T18:47:36.013+0000	exported 462 records
2020-03-03T18:47:36.193+0000	connected to: localhost
2020-03-03T18:47:36.194+0000	exported 11 records
root@mongo:/home/vagrant# ls
coleciones.txt	colect.txt  cps.json  hola.txt	mongo  phptest.json  productos.json  script.sh

```

Vamos a observar los productos:
```
root@mongo:/home/vagrant# cat productos.json 
{"_id":"ac3","name":"AC3 Phone","brand":"ACME","type":"phone","price":200,"warranty_years":1,"available":true}
{"_id":"ac7","name":"AC7 Phone","brand":"ACME","type":"phone","price":320,"warranty_years":1,"available":false}
{"_id":{"$oid":"507d95d5719dbef170f15bf9"},"name":"AC3 Series Charger","type":["accessory","charger"],"price":19,"warranty_years":0.25,"for":["ac3","ac7","ac9"]}
{"_id":{"$oid":"507d95d5719dbef170f15bfa"},"name":"AC3 Case Green","type":["accessory","case"],"color":"green","price":12,"warranty_years":0}
{"_id":{"$oid":"507d95d5719dbef170f15bfb"},"name":"Phone Extended Warranty","type":"warranty","price":38,"warranty_years":2,"for":["ac3","ac7","ac9","qp7","qp8","qp9"]}
{"_id":{"$oid":"507d95d5719dbef170f15bfc"},"name":"AC3 Case Black","type":["accessory","case"],"color":"black","price":12.5,"warranty_years":0.25,"available":false,"for":"ac3"}
{"_id":{"$oid":"507d95d5719dbef170f15bfd"},"name":"AC3 Case Red","type":["accessory","case"],"color":"red","price":12,"warranty_years":0.25,"available":true,"for":"ac3"}
{"_id":{"$oid":"507d95d5719dbef170f15bfe"},"name":"Phone Service Basic Plan","type":"service","monthly_price":40,"limits":{"voice":{"units":"minutes","n":400,"over_rate":0.05},"data":{"units":"gigabytes","n":20,"over_rate":1},"sms":{"units":"texts sent","n":100,"over_rate":0.001}},"term_years":2}
{"_id":{"$oid":"507d95d5719dbef170f15bff"},"name":"Phone Service Core Plan","type":"service","monthly_price":60,"limits":{"voice":{"units":"minutes","n":1000,"over_rate":0.05},"data":{"n":"unlimited","over_rate":0},"sms":{"n":"unlimited","over_rate":0}},"term_years":1}
{"_id":{"$oid":"507d95d5719dbef170f15c00"},"name":"Phone Service Family Plan","type":"service","monthly_price":90,"limits":{"voice":{"units":"minutes","n":1200,"over_rate":0.05},"data":{"n":"unlimited","over_rate":0},"sms":{"n":"unlimited","over_rate":0}},"sales_tax":true,"term_years":2}
{"_id":{"$oid":"507d95d5719dbef170f15c01"},"name":"Cable TV Basic Service Package","type":"tv","monthly_price":50,"term_years":2,"cancel_penalty":25,"sales_tax":true,"additional_tarriffs":[{"kind":"federal tarriff","amount":{"percent_of_service":0.06}},{"kind":"misc tarriff","amount":2.25}]}


root@mongo:/home/vagrant# cat cps.json
{"_id":"98403","city":"TACOMA","loc":[-122.457538,47.26428],"pop":7493,"state":"WA"}
{"_id":"98404","city":"TACOMA","loc":[-122.412625,47.211312],"pop":27135,"state":"WA"}
{"_id":"98405","city":"TACOMA","loc":[-122.46435,47.248351],"pop":23918,"state":"WA"}
{"_id":"98406","city":"TACOMA","loc":[-122.499349,47.26325],"pop":22971,"state":"WA"}
{"_id":"98407","city":"TACOMA","loc":[-122.503881,47.282479],"pop":19881,"state":"WA"}
{"_id":"98408","city":"TACOMA","loc":[-122.444381,47.207267],"pop":28753,"state":"WA"}
{"_id":"98409","city":"TACOMA","loc":[-122.482503,47.20381],"pop":25045,"state":"WA"}
{"_id":"98421","city":"TACOMA","loc":[-122.401457,47.266373],"pop":508,"state":"WA"}
{"_id":"98422","city":"TACOMA","loc":[-122.398349,47.294805],"pop":10385,"state":"WA"}
{"_id":"98424","city":"FIFE","loc":[-122.350962,47.243632],"pop":5626,"state":"WA"}
{"_id":"98433","city":"FORT LEWIS","loc":[-122.583486,47.100864],"pop":27463,"state":"WA"}
{"_id":"98439","city":"LAKEWOOD CENTER","loc":[-122.529326,47.122905],"pop":3064,"state":"WA"}
{"_id":"98443","city":"TACOMA","loc":[-122.372815,47.204369],"pop":5457,"state":"WA"}
{"_id":"98444","city":"PARKLAND","loc":[-122.448842,47.156553],"pop":27406,"state":"WA"}
{"_id":"98445","city":"PARKLAND","loc":[-122.411614,47.133967],"pop":20298,"state":"WA"}
{"_id":"98446","city":"PARKLAND","loc":[-122.37
.....

```

Vamos a crear un usuario en una nueva base de datos, la llamaremos práctica y al usuario user2
```
> use practica
switched to db practica
> db.createUser({user: "user2",pwd: "user2",roles: [{ role: "userAdmin", db: "practica" },{ role: "dbAdmin",   db: "practica" },{ role: "readWrite", db: "practica" }]});
Successfully added user: {
	"user" : "user2",
	"roles" : [
		{
			"role" : "userAdmin",
			"db" : "practica"
		},
		{
			"role" : "dbAdmin",
			"db" : "practica"
		},
		{
			"role" : "readWrite",
			"db" : "practica"
		}
	]
}

```

Y importamos en una nueva base de datos con mongoimport

```
root@mongo:/home/vagrant# mongoimport --db practica --collection cps --drop --file cps.json -u user2 -p user2
2020-03-03T18:55:04.323+0000	connected to: localhost
2020-03-03T18:55:04.344+0000	dropping: practica.cps
2020-03-03T18:55:04.582+0000	imported 29467 documents.

root@mongo:/home/vagrant# mongoimport --db practica --collection productos --drop --file productos.json -u user2 -p user2
2020-03-03T18:55:09.801+0000	connected to: localhost
2020-03-03T18:55:09.822+0000	dropping: practica.productos
2020-03-03T18:55:09.867+0000	imported 11 documents

```

Observamos que están en la nueva base de datos
```
root@mongo:/home/vagrant# mongo practica -u user2 -p user2 --authenticationDatabase=practica
MongoDB shell version v4.0.12
connecting to: mongodb://127.0.0.1:27017/practica?authSource=practica&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("2cc520a9-172b-469e-8beb-4108a3714796") }
MongoDB server version: 4.0.12
> show collections
cps
productos
> db.productos.count()
11
> db.cps.count()
29467

```
