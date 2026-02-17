# Proyecto de Orquestación de Carga a Snowflake con Python

Este proyecto implementa un proceso ETL (Extract, Transform, Load) automatizado utilizando Python para cargar datos desde archivos (en este caso CSV locales) hacia un Data Warehouse en Snowflake. El flujo de trabajo está diseñado para ser robusto, manejando la creación automática de tablas, la inferencia de tipos de datos y la carga incremental mediante estrategias de *staging* y *merge*.

## 🚀 Características Principales

- **Conexión Segura**: Utiliza variables de entorno para gestionar credenciales de Snowflake de forma segura.
- **Inferencia de Esquema**: Detecta automáticamente los tipos de datos de Pandas y los mapea a tipos compatibles con Snowflake.
- **Carga Incremental (Upsert)**: Implementa un patrón de carga de datos que actualiza registros existentes e inserta nuevos registros utilizando tablas temporales de *staging* y sentencias `MERGE`. Esto será util para cuando los archivos se actualicen.
- **Integridad Referencial**: Gestiona la creación de tablas con claves primarias (PK) y foráneas (FK) definidas para mantener la consistencia del modelo de datos.
- **Manejo de Errores**: Incluye control de excepciones y manejo de codificaciones de archivos (UTF-8 / Latin1).

## 🛠️ Requisitos Previos

- Python 3.8+
- Una cuenta activa de Snowflake.
- Archivos de datos en formato CSV.

## ▶️ Ejecución

El proceso principal se encuentra en el Jupyter Notebook `Carga_Datos_Snowflake.ipynb`. Al ejecutarlo, se crearán las tablas en Snowflake y se cargarán los datos.

## 📂 Estructura del Proyecto

```text
.
├── Carga_Datos_Snowflake.ipynb   # Script principal de orquestación ETL
├── .env                          # Variables de entorno (no incluido en repo)
├── README.md                     # Documentación del proyecto
├── data/                         # Directorio de archivos fuente (CSV)
│   ├── clientes.csv
│   ├── empleados.csv
│   ├── facturas.csv
│   ├── productos.csv
│   └── sucursales.csv
├── requirements.txt              # Dependencias del proyecto
└── docs/                         # Documentación y diagramas
    ├── Diagrama ER.jpg           # Modelo Entidad-Relación
    └── Diagrama flujo.jpg        # Flujo del proceso ETL
```

## 📐 Modelo de Datos y Flujo

El proceso construye un modelo relacional en Snowflake basado en los archivos CSV. 
- **Diagrama ER**: Consulta `docs/Diagrama ER.jpg` para ver las relaciones entre tablas.
- **Flujo de Trabajo**: Consulta `docs/Diagrama flujo.jpg` para entender la secuencia de carga y transformación.
