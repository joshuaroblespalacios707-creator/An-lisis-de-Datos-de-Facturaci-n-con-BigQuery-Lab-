📊 Análisis de Datos de Facturación con BigQuery — Lab

Documentación técnica de un laboratorio práctico de análisis de datos a gran escala usando BigQuery en Google Cloud, sobre un dataset real de facturación con más de 415,000 registros.

📌 Resumen

En este laboratorio se exploró el uso de BigQuery para analizar un volumen masivo de datos de facturación (más de 415,000 registros). Se importaron datos estructurados en formato Avro, almacenados en un bucket público de Google Cloud Storage, y se ejecutaron consultas SQL para extraer métricas de costos, uso y servicios más utilizados.

🛠️ Stack y Herramientas
Categoría	Detalle
Plataforma	Google Cloud Platform (GCP)
Servicio principal	BigQuery
Origen de datos	Google Cloud Storage (bucket público)
Formato de datos	Avro
Lenguaje de consulta	SQL
📋 Paso a Paso
1. Importar los datos a BigQuery
Abrir el panel de BigQuery Studio.
Ubicar el proyecto en el panel izquierdo, hacer clic en los tres puntos (⋮) junto al dataset (billing_dataset) y seleccionar Crear tabla.
En Crear tabla a partir de, seleccionar Google Cloud Storage.
Pegar la ruta del archivo en GCS:
   cloud-training/archinfra/BillingExport-2020-09-18.avro
En Formato de archivo, seleccionar Avro.
Asignar el nombre de tabla sample_info_table y hacer clic en Crear tabla.
2. Consultar y analizar datos con SQL
Verificar el volumen de datos: consulta SELECT básica para confirmar la carga de las 415,602 filas.
Filtrar cargos activos: aplicar WHERE cost > 0 y WHERE cost > 10 para identificar consumo real y gastos elevados.
Agrupar consumo por servicio: usar GROUP BY service.description junto con COUNT(*) para descubrir qué servicio genera la mayor cantidad de registros (ej. Compute Engine).
Analizar costos totales: usar SUM(cost) agrupado por servicio para identificar qué producto generó el mayor gasto total.
3. Limpieza del entorno

Para eliminar los recursos generados y no acumular elementos innecesarios:

bash
bq rm -r -f billing_dataset
🎓 Conceptos Aprendidos
Ingesta de datos estructurados (Avro) desde Cloud Storage hacia BigQuery
Análisis de grandes volúmenes de datos mediante SQL estándar
Agregación y agrupación de datos para generar métricas de negocio (costos, uso por servicio)
Buenas prácticas de limpieza de recursos para evitar cargos innecesarios
📌 Notas

Este laboratorio forma parte de mi preparación continua para la certificación Google Associate Cloud Engineer (ACE), con enfoque práctico en análisis de datos y almacenamiento en GCP.

⬆ Español version above

📊 BigQuery Billing Data Analysis — Lab

Technical documentation of a hands-on, large-scale data analysis lab using BigQuery on Google Cloud, working with a real billing dataset of over 415,000 records.

📌 Summary

This lab focused on using BigQuery to analyze a large-scale billing dataset (over 415,000 records). We ingested structured data in Avro format, stored in a public Google Cloud Storage bucket, and ran SQL queries to extract insights on costs, usage, and top-utilized cloud services.

🛠️ Stack and Tools
Category	Detail
Platform	Google Cloud Platform (GCP)
Core service	BigQuery
Data source	Google Cloud Storage (public bucket)
Data format	Avro
Query language	SQL
📋 Step-by-Step
1. Import Data into BigQuery
Open the BigQuery Studio panel.
Locate the project in the left navigation panel, click the three dots (⋮) next to the dataset (billing_dataset), and select Create table.
Under Create table from, select Google Cloud Storage.
Paste the GCS file path:
   cloud-training/archinfra/BillingExport-2020-09-18.avro
Under File format, select Avro.
Name the table sample_info_table and click Create Table.
2. Query and Analyze Data using SQL
Verify data ingestion: run a basic SELECT query to confirm all 415,602 rows were successfully loaded.
Filter active charges: apply WHERE cost > 0 and WHERE cost > 10 to isolate actual spend and high-value transactions.
Aggregate usage by service: use GROUP BY service.description together with COUNT(*) to identify which cloud service logged the highest number of transactions (e.g., Compute Engine).
Calculate total costs: use SUM(cost) grouped by service to determine which product generated the highest overall billing amount.
3. Environment Cleanup

To remove all created resources and keep the workspace clean:

bash
bq rm -r -f billing_dataset
🎓 Key Concepts Learned
Ingesting structured data (Avro) from Cloud Storage into BigQuery
Analyzing large-scale datasets using standard SQL
Aggregating and grouping data to produce business-level metrics (cost, usage per service)
Resource cleanup best practices to avoid unnecessary charges
📌 Notes

This lab is part of my ongoing preparation for the Google Associate Cloud Engineer (ACE) certification, with a hands-on focus on data analysis and storage in GCP.
