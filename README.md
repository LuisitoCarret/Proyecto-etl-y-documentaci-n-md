# Proyecto ETL
SSIS (Integration Services de SQL Server) es una plataforma de Microsoft utilizada para la integración de datos y la administración de procesos de extracción, transformación y carga (ETL).

En este proyecto se documenta la creacion de un ETL del data warehouse DATAMARTVENTAS, 
con el objetivo de llenar sus tablas, utilizando los datos de la base de datos NORTHWIND.
Para despues crear un JOB en base al proyecto de ETL realizado con anterioridad.


<img src="./Fotos Proyecto/Clientes10.jpg" alt="MarineGEO circle logo" style="height: 500px; width:800px;"/>


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