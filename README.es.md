# Plantilla de Proyecto de Ciencia de Datos

Esta plantilla está diseñada para impulsar proyectos de ciencia de datos proporcionando una configuración básica para conexiones de base de datos, procesamiento de datos, y desarrollo de modelos de aprendizaje automático. Incluye una organización estructurada de carpetas para tus conjuntos de datos y un conjunto de paquetes de Python predefinidos necesarios para la mayoría de las tareas de ciencia de datos.

## Estructura

El proyecto está organizado de la siguiente manera:

- `app.py` - El script principal de Python que ejecutas para tu proyecto.
- `explore.py` - Un notebook para que puedas hacer tus exploraciones, idealmente el codigo de este notebook se migra hacia app.py para subir a produccion.
- `utils.py` - Este archivo contiene código de utilidad para operaciones como conexiones de base de datos.
- `requirements.txt` - Este archivo contiene la lista de paquetes de Python necesarios.
- `models/` - Este directorio debería contener tus clases de modelos SQLAlchemy.
- `data/` - Este directorio contiene los siguientes subdirectorios:
  - `interim/` - Para datos intermedios que han sido transformados.
  - `processed/` - Para los datos finales a utilizar para el modelado.
  - `raw/` - Para datos brutos sin ningún procesamiento.

## Configuración

**Prerrequisitos**

Asegúrate de tener Python 3.11+ instalado en tu máquina. También necesitarás pip para instalar los paquetes de Python.

**Instalación**

Clona el repositorio del proyecto en tu máquina local.

Navega hasta el directorio del proyecto e instala los paquetes de Python requeridos:

```bash
pip install -r requirements.txt
```

**Crear una base de datos (si es necesario)**

Crea una nueva base de datos dentro del motor Postgres personalizando y ejecutando el siguiente comando: `$ createdb -h localhost -U <username> <db_name>`
Conéctate al motor Postgres para usar tu base de datos, manipular tablas y datos: `$ psql -h localhost -U <username> <db_name>`
NOTA: Recuerda revisar la información del archivo ./.env para obtener el nombre de usuario y db_name.

¡Una vez que estés dentro de PSQL podrás crear tablas, hacer consultas, insertar, actualizar o eliminar datos y mucho más!

**Variables de entorno**

Crea un archivo .env en el directorio raíz del proyecto para almacenar tus variables de entorno, como tu cadena de conexión a la base de datos:

```makefile
DATABASE_URL="your_database_connection_url_here"
```

## Ejecutando la Aplicación

Para ejecutar la aplicación, ejecuta el script app.py desde la raíz del directorio del proyecto:

```bash
python app.py
```

## Añadiendo Modelos

Para añadir clases de modelos SQLAlchemy, crea nuevos archivos de script de Python dentro del directorio models/. Estas clases deben ser definidas de acuerdo a tu esquema de base de datos.

Definición del modelo de ejemplo (`models/example_model.py`):

```py
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy import Column, Integer, String

Base = declarative_base()

class ExampleModel(Base):
    __tablename__ = 'example_table'
    id = Column(Integer, primary_key=True)
    name = Column(String)

```

## Trabajando con Datos

Puedes colocar tus conjuntos de datos brutos en el directorio data/raw, conjuntos de datos intermedios en data/interim, y los conjuntos de datos procesados listos para el análisis en data/processed.

Para procesar datos, puedes modificar el script app.py para incluir tus pasos de procesamiento de datos, utilizando pandas para la manipulación y análisis de datos.

## Descripción
### Bienvenidos
El Grupo Acea es uno de los principales operadores multiservicios italianos. Cotizada en la Bolsa de Valores italiana desde 1999, la empresa gestiona y desarrolla redes de agua y electricidad y servicios medioambientales. Acea es el principal operador italiano en el sector de los servicios hídricos, abasteciendo a 9 millones de habitantes en Lacio, Toscana, Umbría, Molise y Campania.

En este concurso nos centraremos únicamente en el sector del agua para ayudar al Grupo Acea a preservar los valiosos cuerpos de agua. Como es fácil de imaginar, una empresa de suministro de agua lucha con la necesidad de pronosticar el nivel de agua en un cuerpo de agua (manantial, lago, río o acuífero) para gestionar el consumo diario. Durante el otoño y el invierno, los cuerpos de agua se rellenan, pero durante la primavera y el verano comienzan a vaciarse. Para ayudar a preservar la salud de estos cuerpos de agua, es importante predecir la disponibilidad de agua más eficiente, en términos de nivel y caudal de agua para cada día del año.

### Datos
La realidad es que cada cuerpo de agua tiene características tan únicas que sus atributos no están vinculados entre sí. Esta competencia analítica utiliza conjuntos de datos que son completamente independientes entre sí. Sin embargo, es fundamental comprender la disponibilidad total para preservar el agua en todo el país.

Cada conjunto de datos representa un tipo diferente de cuerpo de agua. Como cada cuerpo de agua es diferente del otro, las características relacionadas también son diferentes. Entonces, si, por ejemplo, consideramos un manantial de agua, notamos que sus características son diferentes a las de un lago. Estas variaciones son esperables en función del comportamiento y las características únicas de cada cuerpo de agua. El Grupo Acea trabaja con cuatro tipos diferentes de cuerpos de agua: manantiales de agua, lagos, ríos y acuíferos.

### Desafío
¿Puedes construir una historia para predecir la cantidad de agua en cada cuerpo de agua único? El desafío es determinar cómo las características influyen en la disponibilidad de agua de cada cuerpo de agua presentado. Para ser más directos, obteniendo una mejor comprensión de los volúmenes, podrán garantizar la disponibilidad de agua para cada intervalo de tiempo del año.

El intervalo de tiempo se define como día/mes según las medidas disponibles para cada cuerpo de agua. Los modelos deben capturar los volúmenes de cada cuerpo de agua (por ejemplo, para un modelo que funciona en un intervalo mensual, se espera un pronóstico para el mes).

El resultado deseado es un cuaderno que pueda generar cuatro modelos matemáticos, uno para cada categoría de cuerpo de agua (acuíferos, manantiales de agua, río, lago) que puedan aplicarse a cada cuerpo de agua individual.

![img](https://www.googleapis.com/download/storage/v1/b/kaggle-user-content/o/inbox%2F6195295%2Fcca952eecc1e49c54317daf97ca2cca7%2FAcea-Input.png?generation=1606932492951317&alt=media)

## Contribuyentes

Esta plantilla fue construida como parte del [Data Science and Machine Learning Bootcamp](https://4geeksacademy.com/us/coding-bootcamps/datascience-machine-learning) de 4Geeks Academy por [Alejandro Sanchez](https://twitter.com/alesanchezr) y muchos otros contribuyentes. Descubre más sobre [los programas BootCamp de 4Geeks Academy](https://4geeksacademy.com/us/programs) aquí.

Otras plantillas y recursos como este se pueden encontrar en la página de GitHub de la escuela.