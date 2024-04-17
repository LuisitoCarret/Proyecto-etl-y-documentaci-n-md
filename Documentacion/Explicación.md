# Proyecto ETL
En este proyecto se documenta la creacion de un ETL del data warehouse DATAMARTVENTAS, 
con el objetivo de llenar sus tablas, utilizando los datos de la base de datos NORTHWIND.
Para despues crear un JOB en base al proyecto de ETL realizado con anterioridad.

### Tabla 'Clientes'
##### 1. Primeramente se hace una conexion a la base de datos NORTHWIND para obtener los datos de la tabla Customers (clientes)

<img src="./Clientes1.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 2. Despues se hace la conexión a la base de datos DATAMARTVENTAS e igual se extraen los datos de la tabla DimCliente.

<img src="./Clientes2.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 3. Consecuentemente se ordenan primero los datos de la tabla Customers de la base de datos NORTHWIND de forma ascendente

<img src="./Clientes3.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 4. Teniendo eso, se realiza un left join y se relacionan los campos id de ambas tablas para comparar.

<img src="./Clientes4.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 5. Por ultimo se hace una comparación, la cual es que si en la tabla de Clientes de DATAMARTVENTAS no tiene la misma cantidad de registros que la tabla Customers de NORTHWIND, se insertaran los nuevos datos en la tabla de Clientes

<img src="./Clientes5.jpg" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

### Tabla 'Tiempo'
##### 1. Primeramente se hace una conexion a la base de datos NORTHWIND para obtener los datos de la tabla Order

<img src="./Cliente6.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 2. De igual manera se hace una conexión a la base de datos DATAMARTVENTAS para obtener los datos de la tabla Tiempo 

<img src="./Cliente7.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 3. Ahora, para ambas tablas se deben de ordenar sus datos de manera ascendente

<img src="./Cliente8.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 4. Consucuentemente, se realiza un merge de las 2 tablas, en este caso es un left join del lado de la tabla de NORTHWIND


<img src="./Cliente9.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 5. Antes de finalizar se realiza una condición, la cual compara si la cantidad de registros que hay en la tabla de NORTHWIND son los mismos que en la tabla de DATAMARVENTAS, en caso de que no sea así, insertara los nuevos registros que tiene NORTHWIND.

<img src="./Cliente10.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>

##### 6. Finalmente, todo registro nuevo que se encuentre en la tabla de NORTHWIND, se ingresa en la tabla de DimTiempo de DATAMARTVENTA

<img src="./Cliente11.png" alt="MarineGEO circle logo" style="height: 400px; width:500px;"/>