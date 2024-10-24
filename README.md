# Análisis de Morbilidad de Enfermedades Infecciosas en Colombia

Analizar la morbilidad de enfermedades infecciosas en Colombia para identificar patrones y tendencias según la edad y unidades funcionales. Utiliza Python (Pandas, Matplotlib) o R (dplyr, ggplot2) para la limpieza y análisis de datos. Contacto: [tuemail@example.com](mailto:tuemail@example.com).

## Instrucciones para la Ejecución
1. [**Instalar dependencias**](https://www.bing.com/search?form=SKPBOT&q=Instalar%20dependencias):
```bash
pip install pandas matplotlib seaborn

1. 
Ejecutar el análisis:

python analisis_morbilidad.py

Subir tu Código

from pyspark.sql import SparkSession, functions as F
from pyspark.sql.types import IntegerType

# Inicializa la sesión de Spark
spark = SparkSession.builder.appName('Tarea3').getOrCreate()

# Define la ruta del archivo .csv en HDFS
file_path = 'hdfs://localhost:9000/Tarea3/rows.csv.3'
df = spark.read.format('csv').option('header', 'true').option('inferSchema', 'true').load(file_path)

# Limpieza y transformación de datos
df = df.dropna()
df = df.withColumn('EDAD DE ATENCION (AÑOS)', F.col('EDAD DE ATENCION (AÑOS)').cast(IntegerType()))

# Análisis exploratorio de datos (EDA)
df.printSchema()
df.show()
df.summary().show()

# Filtrar y seleccionar columnas
dias = df.filter(F.col('EDAD DE ATENCION (AÑOS)') > 50).select('EDAD DE ATENCION (AÑOS)', 'NOMBRE DEL DIAGNOSTICO', 'AÑO REPORTADO')
dias.show()

# Ordenar filas por los valores en la columna "EDAD DE ATENCION (AÑOS)" en orden descendente
sorted_df = df.sort(F.col('EDAD DE ATENCION (AÑOS)').desc())
sorted_df.show()

# Almacenar los resultados procesados
output_path = 'hdfs://localhost:9000/Tarea3/processed_data'
sorted_df.write.format('csv').option('header', 'true').save(output_path)

1. 
Inicializar el repositorio:

git init

1. 
Agregar archivos:

git add README.md
git add <nombre_de_tu_archivo_de_codigo>.py

1. 
Hacer un commit:

git commit -m "Initial commit"

1. 
Conectar con el repositorio remoto:

git remote add origin https://github.com/Edison98742323/codigo-de-tarea3-.git

1. 
Subir los cambios:

git push -u origin main
