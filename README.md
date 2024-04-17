# Proyecto ETL
SSIS (Integration Services de SQL Server) es una plataforma de Microsoft utilizada para la integración de datos y la administración de procesos de extracción, transformación y carga (ETL).

En este proyecto se documenta la creacion de un ETL del data warehouse DATAMARTVENTAS, 
con el objetivo de llenar sus tablas, utilizando los datos de la base de datos NORTHWIND.
Para despues crear un JOB en base al proyecto de ETL realizado con anterioridad.


<img src="./Fotos Proyecto/Clientes10.jpg" alt="MarineGEO circle logo" style="height: 500px; width:800px;"/>

### Tabla productos

##### Como en los anteriores casos necesitamos un origen OLE DB para ello arrastramos uno y su interior haremos la conexion a la base de datos y la tabla de donde recopilaremos los regsitros.Nos conectamos a la base de datos en NOTHWIND y seleccionamos la tabla Employees


<img src="./Fotos Proyecto/ConexionProductos.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Despues arrastramos un origen OLE DB, dentro hacemos la conexion a la base de datos DATAMARTVENTAS y seleccionamos la tabla DimEmployees

<img src="./Fotos Proyecto/DestinoEmpleados.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### El siguiente paso es ordenar por EmployeeID de forma acendente esto es para los 2 casos de origen

<img src="./Fotos Proyecto/Ordenamiento.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Una vez hecho lo anterior haremos un merge join, que nos servira para hacer joins a tablas en este caso haremos join de la tabla Employees de Northwind a la tabla DimEmpleados de DATAMARTVENTAS, utilizamos left join para que nso devuelva los registros de la tabla izquierda (Employees) y los registros coincidentes de la tabla derecha (DimEmpleados)

<img src="./Fotos Proyecto/MergeJoin.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Ahora vicnulamos lo utlimo a un conditional split donde pondremos una case para que no haya registros nulos 

<img src="./Fotos Proyecto/Coditional.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Para terminar agregamos el destino que sera en la tabla de DimProductos ubicada en la base de datos DATAMARTVENTAS

<img src="./Fotos Proyecto/Destino.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Como resultado tenemos lo siguiente

<img src="./Fotos Proyecto/Resultado.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

### Tabla Productos

##### Continuamos con la tabla productos agregamos un origen OLE DB seleccionamos la base de datos NORTHWIND y en lugar de seleccionar una tabla , agregamos un comando SQL como se muestra a continuacion

<img src="./Fotos Proyecto/ConexiionP.PNG.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Ahora agregamos un origen de la tabla DATAMARTVENTAS seleccionamos la tabla DimProducto

<img src="./Fotos Proyecto/OrigenP.PNG" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Ahora ordenamos en los 2 origenes seleccionamos ProductoID y de forma ascendente

<img src="./Fotos Proyecto/OrdenarP.PNG" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Agregmos un merge join para seleccionar en las 2 tablas el ProductID ya que esta fucniona para que podamos hacer el join entre las 2 tablas y cambiamos el inner join por left outer join

<img src="./Fotos Proyecto/MergeP.PNG" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Continuamos con el conditional split que de igual manera agregamos un case para no mostrar los valores nulos en un campo de la tabla

<img src="./Fotos Proyecto/SplitP.PNG" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Para terminar agregamos el destino que es en la base de datos MARTVENTAS y en la tabla DimProductos

<img src="./Fotos Proyecto/DestinoP.PNG" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Una vez terminado esto, tendremos el siguiente resultado

<img src="./Fotos Proyecto/ResultadoP.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

### Tabla FactVentas

##### Para esta tabla necesitaremos las tablas anteriores para ello haremos lo mismo que hemos estado haciendo agregar 2 origenes en este caso seran de las tablas OrderDetails y DimProducto cdad una de sus respectivas base de datos.

<img src="./Fotos Proyecto/Nort.PNG" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

<img src="./Fotos Proyecto/Vent.PNG" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### Y seguiremos haciendo el mismo proceso con sort y merge join


### Tabla 'Clientes'
##### 1. Primeramente se hace una conexion a la base de datos NORTHWIND para obtener los datos de la tabla Customers (clientes)

<img src="./Fotos Proyecto/Clientes1.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 2. Despues se hace la conexión a la base de datos DATAMARTVENTAS e igual se extraen los datos de la tabla DimCliente.

<img src="./Fotos Proyecto/Clientes2.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 3. Consecuentemente se ordenan primero los datos de la tabla Customers de la base de datos NORTHWIND de forma ascendente

<img src="./Fotos Proyecto/Clientes3.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 4. Teniendo eso, se realiza un left join y se relacionan los campos id de ambas tablas para comparar.

<img src="./Fotos Proyecto/Clientes4.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 5. Por ultimo se hace una comparación, la cual es que si en la tabla de Clientes de DATAMARTVENTAS no tiene la misma cantidad de registros que la tabla Customers de NORTHWIND, se insertaran los nuevos datos en la tabla de Clientes

<img src="./Fotos Proyecto/Clientes5.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

### Tabla 'Tiempo'
##### 1. Primeramente se hace una conexion a la base de datos NORTHWIND para obtener los datos de la tabla Order

<img src="./Fotos Proyecto/Cliente6.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 2. De igual manera se hace una conexión a la base de datos DATAMARTVENTAS para obtener los datos de la tabla Tiempo 

<img src="./Fotos Proyecto/Cliente7.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 3. Ahora, para ambas tablas se deben de ordenar sus datos de manera ascendente

<img src="./Fotos Proyecto/Cliente8.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 4. Consucuentemente, se realiza un merge de las 2 tablas, en este caso es un left join del lado de la tabla de NORTHWIND


<img src="./Fotos Proyecto/Cliente9.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 5. Antes de finalizar se realiza una condición, la cual compara si la cantidad de registros que hay en la tabla de NORTHWIND son los mismos que en la tabla de DATAMARVENTAS, en caso de que no sea así, insertara los nuevos registros que tiene NORTHWIND.

<img src="./Fotos Proyecto/Cliente10.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 6. Finalmente, todo registro nuevo que se encuentre en la tabla de NORTHWIND, se ingresa en la tabla de DimTiempo de DATAMARTVENTA

<img src="./Fotos Proyecto/Cliente11.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>