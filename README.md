# Codelab_bi
HOLA!!!!
## **Tabla de Contenidos**
- [Descripción](#descripción)
- [Características](#características)
- [Instalación](#instalación)
- [Uso](#uso)
- [Ejemplo de Configuración de la Base de Datos](#ejemplo-de-configuración-de-la-base-de-datos)
- [Obtener y Guardar Datos de Clientes Aleatorios](#Obtener y Guardar Datos de Clientes Aleatorios)
- [Contribuciones](#contribuciones)
- [Licencia](#licencia)
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
