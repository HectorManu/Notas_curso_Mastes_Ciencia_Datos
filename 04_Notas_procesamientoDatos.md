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
