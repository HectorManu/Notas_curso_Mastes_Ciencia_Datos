# Definición
 
- Tenemos que comprender nuestros datos, es decir, ¿de qué se trata? Por ejemplo:
    - ¿Cuántos registros hay?
    - ¿Están todas laas filas completas ó tnemos campos con valores nulos? En caso que haya demasiados nulos: ¿Queda el resto de información inútil?
    - ¿Qué datos son discretos y cuales continuos? Muchas veces sirve obtener el tipo de datos: text, int, double, float.
    - Si es un problema supervisado(binaria/multiclase, balanceo de clase) o un problema no supervisado.
    -¿Cuáles parecen ser características importantes? ¿cuáles podemos descartar?
    -¿Siguen alguna distribución? ¿Hay correlación entre caracteríticas?
    - ¿Cuáles son los Outliers? unos pocos datos aislados que difieren drácticamente del resto y «contaminan» ó desvían las distribuciones
    -¿Tenemos posible sesgo de datos?
- Veamos los pasos a seguir.

# 2. Cargar un CSV y librerías

> import pandas as pd

> import numpy as np

>import matplotlib.pyplot as plt

> import statsmodels.api as sm

> import seaborn as sns

> dataset = 'data/countries.csv'

> df = pd.read_csv(dataset, sep=";")

> df


# 3. Información básica 

- Lo primero que tenemos que conocer es el tamaño de nuestro dataset y los nombres de las columnas que tiene.

> print('Cantidad de filas y columnas: ',df.shape)

> print('Nombre columnas: ',df.columns)

## 3.1 Información básica (II)

- Las columnas que no tengan el tipo correcto deberemos transformarlar.
    - Cambiar el tipo de dato

-Cuanod tenemos características numéricas y categóricas deberemos uniformizarlo
    - One-Hot Encoding

-Ver si alguna columna tiene valores NaN que deberemos de tratar.

> print(df.insnull().sum())

> df.info()

## 3.2 Información básica (III)

- Conocer los rangos de nuestros datos.
> df.describe()

# 4. Visualización
- Ver la correlción entre datos.

## 4.1 Extracción de información (I)

- Crecimiento en España

>df_pop_es = df_pop[df_pop["country"] == 'Spain']

>print(df_pop_es.head())

>df_pop_es.drop(['country'],axis=1['population'].plot(kind='bar'))



# PROCESAMIENTO DE DDATOS

- aprendizaje supervisado
proporciona una ruta directa para convertir los datos en información real y procesada, permite comprender resultados no deseados

- aprendizaje no supervisado
cuando tenemos un closter y debemos descubrir cuál es la clase 

Este es un reconocimiento  de patrones para ver qué comportamientos tienen

- Los modelos deben ser reconstruidos periódicamente con el fin de mantener sus predicciones sin que se conviertean en obsoletas. **FORCASTING**

## Diferencia entre un problema de clasificación y Regresión

| Clasificación                                                                                                                                                       | Regresión                                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| El algoritmo intenta etiquetas cada <br> ejempo eligiendo entre dos o más clases <br>diferentes                                                                     | Donde se predice un valor real basado en<br> entradas pasadas                                                                                                                                                               |
| Usan las características aprendidas de los <br> datos de capacitación sobre datos nuevos,<br> no vistos previamnete, para predecir sus<br> etiquetas de clase.      | Estos algoritmos se usan para predeicir <br> valores de salida basados en algunoas <br> caracterísitcas de entrada obtenidas de los <br> datos.                                                                             |
| Elegir entre dos clasese se denomia <br> clasificación binaria. Elegir entre más de <br> dos clases se denomina clasificación <br> multiclase.                      | Los valores de salida en este caso son <br> continuos                                                                                                                                                                       |
| Algunso ejemplos de este algoritmo son: <br> predecir si un cliente va a cancelar o no su <br> tarjeta de crédito, predecir si un alumno <br> pasará o no una clase | Algunos ejemplos de este algoritmo son: <br>predecir los precios de la vivienda, predecir <br> las cantidades de compra, predecir la <br> candtidad de ingresos se genera a partir de <br>  una nueva campaña de marketing. |
