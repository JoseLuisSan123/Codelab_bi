# Codelab_bi
HOLA!!!!
# **Nombre del Proyecto**

Descripción breve del proyecto, qué hace y por qué es útil.

## **Tabla de Contenidos**
- [Descripción](#descripción)
- [Características](#características)
- [Instalación](#instalación)
- [Uso](#uso)
- [Ejemplo de Configuración de la Base de Datos](#ejemplo-de-configuración-de-la-base-de-datos)
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
