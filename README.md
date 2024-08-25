# Codelab_bi
HOLA!!!!
## **Tabla de Contenidos**
- [Descripción](#descripción)
- [Características](#características)
- [Instalación](#instalación)
- [Ejemplo de Configuración de la Base de Datos](#ejemplo-de-configuración-de-la-base-de-datos)
- [Obtener y Guardar Datos de Clientes Aleatorios](#Obtener-y-Guardar-Datos-de-Clientes-Aleatorios)
- [Crear y Guardar Datos de Sucursales](#Crear-y-Guardar-Datos-de-Sucursales)
- [Crear y Guardar Tipos de Transacciones](#Crear-y-Guardar-Tipos-de-Transacciones)
- [Crear y Guardar Datos de Transacciones](#Crear-y-Guardar-Datos-de-Transacciones)
- [Verificar la Creación de Tablas en SQLite3](#Verificar-la-Creación-de-Tablas-en-SQLite3)
- [Autor(es)](#autores)

## **Descripción**
Este proyecto se enfoca en la creación y gestión de una base de datos SQLite destinada a almacenar datos financieros ficticios. Utiliza la biblioteca `Faker` para generar datos realistas, lo que facilita la simulación y prueba de sistemas que manejan información financiera.

## **Características**
- **Generación de Datos Ficticios**: Utiliza la biblioteca `Faker` para generar datos de clientes, sucursales y transacciones.
- **Base de Datos SQLite**: Configuración automática de una base de datos SQLite con tablas interrelacionadas para gestionar datos financieros.
- **Consultas SQL**: Función integrada para ejecutar consultas SQL de manera segura y eficiente.

## **Instalación**
Para la realización de este codigo necesitaremos intalar las siguientes librerias:
- sqlite3
- pandas 
- requests
- random
- uuid
- faker
- numpy
- shutil

## **Ejemplo de Configuración de la Base de Datos**
Este proyecto incluye un script que configura una base de datos SQLite para almacenar datos financieros ficticios. A continuación, se explica el propósito de cada sección del código:

1.) Se inicializa una instancia de la biblioteca Faker, utilizada para generar datos falsos realistas, como nombres de clientes y direcciones. (# Inicializar Faker)

2.) Se establece una conexión con una base de datos SQLite llamada financial_data.db. Si el archivo de la base de datos no existe, se crea automáticamente.(# Crear la conexión a la base de datos SQLite3)

3.) Esta función permite ejecutar consultas SQL de forma segura y garantiza que cualquier cambio en la base de datos sea confirmado automáticamente. (# Función para ejecutar consultas SQL)

4.) TABLAS
   - **Customer:** Esta tabla almacena información sobre los clientes, incluyendo su ID, nombre, dirección, número de teléfono y correo electrónico.
   - **Branches:** Esta tabla almacena datos sobre las sucursales, como el ID de la sucursal, la ubicación, el nombre del gerente y el número de contacto.
   - **transaction_types:** Esta tabla define los diferentes tipos de transacciones (por ejemplo, "retiro", "depósito") y proporciona una descripción para cada uno.
   - **transactions:** Esta tabla registra cada transacción realizada, incluyendo detalles como el ID de la transacción, el cliente involucrado, la fecha, el monto, la ubicación, el tipo de transacción, si es fraudulenta, y la sucursal donde ocurrió.

## **Obtener y Guardar Datos de Clientes Aleatorios**
Este proyecto incluye una funcionalidad para obtener datos de clientes ficticios desde la API de Random User y guardarlos en una base de datos SQLite3. A continuación, se describe el proceso y el propósito de cada sección del código:

**1.) Función para obtener datos de clientes desde la API Random User:**

- **Descripción**: Esta función (get_random_users) solicita un número específico de usuarios (por defecto 10) a la API de Random User. La API devuelve datos de usuarios ficticios, como nombres, direcciones, y correos electrónicos.

- **Funcionamiento**:

Se construye una URL que incluye el número de usuarios solicitados (num_users).
Se realiza una solicitud GET a la API.
Si la solicitud es exitosa (status_code == 200), se procesan los datos recibidos en formato JSON y se extraen los resultados.
En caso de error, se imprime un mensaje y se retorna una lista vacía

**2.) Función para crear la tabla de clientes y guardarla en SQLite3:**

- **Descripción:** 
Esta función (create_customers_table) genera una tabla de clientes basada en los datos obtenidos de la API de Random User, y la guarda en una base de datos SQLite3.

- **Funcionamiento:**

Llama a get_random_users para obtener datos de un número específico de clientes.
Crea un diccionario customers_data que organiza la información de los clientes en columnas como customer_id, name, address, phone_number, y email.
Utiliza pandas para convertir este diccionario en un DataFrame (customers_df).
Guarda este DataFrame en una tabla llamada customers en la base de datos SQLite. Si la tabla ya existe, se reemplaza.

**3.) Creación de la Tabla de Clientes**
- **Descripción:** Finalmente, se crea una tabla de clientes con 100 entradas llamando a la función create_customers_table.

- **Resultado:** Los datos de los clientes generados se almacenan en la tabla customers de la base de datos SQLite3, listos para ser utilizados en otras partes del proyecto.

## **Crear y Guardar Datos de Sucursales**
Este proyecto incluye una funcionalidad para generar datos ficticios de sucursales y guardarlos en una base de datos SQLite3. A continuación, se describe el propósito y funcionamiento del código correspondiente.

**1.) Función para Crear la Tabla de Sucursales y Guardarla en SQLite3**
-**Descripción**: Esta función (create_branches_table) genera una tabla de sucursales utilizando datos ficticios generados por la biblioteca Faker. La tabla se guarda en una base de datos SQLite3.

-**Funcionamiento**:

**Generación de Datos**:
**branch_id**: Se genera un identificador único para cada sucursal usando uuid.uuid4().
**branch_location**: Se crea una ciudad ficticia para cada sucursal utilizando fake.city().
**manager_name**: Se genera un nombre ficticio para el gerente de cada sucursal con fake.name().
**contact_number**: Se crea un número de teléfono ficticio para cada sucursal con fake.phone_number().

- **Creación del DataFrame**:
Los datos generados se organizan en un diccionario (branch_data) y se convierten en un DataFrame de pandas (branches_df).
Guardar en SQLite3:
El DataFrame se guarda en una tabla llamada branches en la base de datos SQLite. Si la tabla ya existe, se reemplaza.

**2.) Crear la Tabla de Sucursales**
- **Descripción:** Se llama a la función create_branches_table para crear una tabla con 20 sucursales ficticias.

- **Resultado:** Los datos generados se almacenan en la tabla branches de la base de datos SQLite3, listos para su uso en otras partes del proyecto.

## **Crear y Guardar Tipos de Transacciones**
Esta sección del proyecto incluye una funcionalidad para generar una tabla de tipos de transacciones y guardarla en una base de datos SQLite3. A continuación, se detalla el propósito y funcionamiento del código correspondiente.

**1.) Función para Crear la Tabla de Tipos de Transacciones y Guardarla en SQLite3**

-**Descripción:** Esta función (create_transaction_types_table) crea una tabla que define los tipos de transacciones y sus descripciones, utilizando datos predefinidos. La tabla se guarda en una base de datos SQLite3.

-**Funcionamiento:**

**Datos de Transacciones:**
**transaction_type:** Se definen dos tipos de transacciones: "online" y "in-store".
**description:** Se proporcionan descripciones correspondientes para cada tipo de transacción.
**Creación del DataFrame:**
Los datos se organizan en un diccionario (transaction_types_data) y se convierten en un DataFrame de pandas (transaction_types_df).
Guardar en SQLite3:
El DataFrame se guarda en una tabla llamada transaction_types en la base de datos SQLite. Si la tabla ya existe, se reemplaza.

**2.) Crear la Tabla de Tipos de Transacciones**

-**Descripción:** Se llama a la función create_transaction_types_table para crear y guardar la tabla de tipos de transacciones en la base de datos.

-**Resultado:** Los tipos de transacciones predefinidos se almacenan en la tabla transaction_types de la base de datos SQLite3, listos para ser utilizados en otras partes del proyecto.

## **Crear y Guardar Datos de Transacciones**
Esta sección del proyecto incluye una funcionalidad para generar una tabla de transacciones y guardarla en una base de datos SQLite3. A continuación, se detalla el propósito y funcionamiento del código correspondiente.

**1.) Función para Crear la Tabla de Transacciones y Guardarla en SQLite3**

-**Descripción:** Esta función (create_transactions_table) genera una tabla de transacciones ficticias utilizando datos aleatorios y la guarda en una base de datos SQLite3.

-**Funcionamiento:**

**Generación de Datos:**
**transaction_id:** Se genera un identificador único para cada transacción usando uuid.uuid4().
**customer_id:** Se asigna un identificador de cliente aleatorio tomado de customers_df.
**transaction_date:** Se crea una fecha de transacción aleatoria dentro del año en curso utilizando fake.date_time_this_year().
**transaction_amount:** Se genera un monto de transacción aleatorio entre 10 y 1000 dólares.
**transaction_location:** Se crea una ciudad ficticia para cada transacción usando fake.city().
**transaction_type:** Se asigna aleatoriamente un tipo de transacción, "online" o "in-store".
**fraudulent:** Se inicializa en 0, indicando que la transacción no es fraudulenta.

-**Introducción de Transacciones Fraudulentas:**
Se seleccionan aleatoriamente un número de transacciones para ser fraudulentas.
Estas transacciones fraudulentas tienen un monto mayor (entre 1000 y 5000 dólares) y un tipo de transacción establecido como "online".

-**Asignación de branch_id:**
Solo se asigna un branch_id a las transacciones de tipo "in-store" usando identificadores aleatorios de branches_df.
Para las transacciones de tipo "online", se establece branch_id en 'None'.
Guardar en SQLite3:
El DataFrame transactions_df se guarda en una tabla llamada transactions en la base de datos SQLite. Si la tabla ya existe, se reemplaza.

**2.) Crear la Tabla de Transacciones**

-**Descripción:** Se llama a la función create_transactions_table para generar y guardar una tabla de 500 transacciones ficticias en la base de datos.

-**Resultado:** Los datos de transacciones generados se almacenan en la tabla transactions de la base de datos SQLite3, listos para su análisis y uso en otras partes del proyecto.

## **Verificar la Creación de Tablas en SQLite3**
Este fragmento de código permite verificar que las tablas se han creado correctamente en la base de datos SQLite3 y cierra la conexión a la base de datos. A continuación, se describe el propósito y funcionamiento del código.

**1.) Verificar la Creación de Tablas**

- **Descripción:** Este bloque de código consulta la base de datos SQLite para listar todas las tablas existentes y luego imprime los resultados.

- **Funcionamiento:**

**Consulta SQL:**
La consulta SQL SELECT name FROM sqlite_master WHERE type='table'; selecciona los nombres de todas las tablas en la base de datos.
**Ejecutar Consulta:**
La consulta se ejecuta usando pd.read_sql(), que recupera los resultados y los almacena en un DataFrame (tables).
**Imprimir Resultados:**
Los nombres de las tablas se imprimen en la consola para verificar que las tablas deseadas están presentes en la base de datos.

**2.) Cerrar la Conexión**
- **Descripción:** Este comando cierra la conexión a la base de datos SQLite, liberando los recursos asociados.

- **Importancia:**

Cerrar la conexión es una buena práctica para asegurar que no queden conexiones abiertas que podrían causar bloqueos o problemas de rendimiento en la base de datos.

## **Autor(es)**
Autor(es)
Creado por **Jose Luis Sanchez Rios**
