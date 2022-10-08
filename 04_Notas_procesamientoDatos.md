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


## tratamiendo de datos

la parte de mantenimiento es el 80% y el otro 20% es la aplicación de 

# 4. Necesiad de procesmaiento 
- los datos en bruto deben ser procesados. 
    - por ejemño, algoritmos de tipo árbol de comportan mejor con atributos de tipo nominal.
- Problemas empíritco -> necesidad de probar diefrentes transformaciones de datos
- Algunas reglas generales: 
  - los métodos basados en instancias son más efectivos si los atributos de entreda tienen la misma escala. 
  - Los métodos de regresión pueden funcinoar mejor si los atributos de entrada están estandarizados.

# 5. Tansformación de datos
- cuando tengamos mucha varianza en los diferentes atributos de un cojunto de datos.  Por ejemplo: 
  - Edad tiene 2 dígitos y sueldo 5 o más dígitos. 
  - el modelo le otorgará más importancia a salario que a edad
- Por tanto, debemos unificar las diferentes variables.
- Raw data -> Structure data -> data preprocessing -> Esploration Data analysus -> inisight reports, visual graphs

# 6. Transformación de los datos 
- Utilizararemos el paquete "*sklearn.preprocessing*" de Python
- Dos métodos 
  - **Ajuste y transformación múltiple** es el enfoque preferido.
    - Llama a la función ***fit()*** para preparar los parámetros de la transformación una vez en sus datos.
    - Luego, puede usar la función ***transform()*** en los mismos datos para prepararos para el modelo y nuevamente en el conjunto de datos de prueba o validación a los nuevos datos que puede ser en el futuro \. 
  - **Ajuste y transformación combinaos** en una conveniencia que puede usar para tareas únicas. Esto puede ser útil si eestá interesado en trazar o resumir los datos transformados y se utilizará la función ***fit_transform()***. 
- Existe una gran cantidad de funciones que podemos aplicar en esta fase de preprocesamiento según la necesidad de nuestros datos.
  

# 1. Métodos de transformación 

Hay una cantidad de métoso de transformación muy grande. todo depende de las necesidad de los datos 

# 2. Escalamiento (i)

- Esta transformación es útil para los algoritmos de optimicazión utilizados en el núcleo de los algoritmos de aprendiaje automático con Grandiente Descendiente.
- También es útil para lagoritmo que pondera entradas como Regression y Neural Networks y algoritmos que usan mediada de distancia como K-Nearest Neighbours. 
- Puede reecalar sus datos usando la clase <u>*MinMaxScalar*</u>.
- Después de reescalar puede ver todos los valores están en en rango 
> From sklear-preprocessing import Min MaxScaler
> 
> scaler= MimMaxScaler(feature_range=(0,1))
> 
> rescaledx = scaler.fit_transform(X)
>  
> #*summarize transformed data*
> 
> np.set_printoptions(precision=3
> 
> print(names)
> 
> pring(rescaledx[0:5,:])
> 
> print(type(rescaledX))




Es más adecuada para técnicas que asumen una distribución gaussiana en las variables de entrada y funcionan mejor con datos reescalados, como LiR, LoR y LDA 
Puede estandarizar datos utilizando la clase anterior
Los valores para cada atributo  ahora tiene una valor medio de 0 y una devisaión estándar de 1


> From sklear-preprocessing import Min MaxScaler
> 
> scaler= StandarScaler().fit(x
> 
> rescaledx = scaler.transform(X)
>  
> #*summarize transformed data*
> 
> np.set_printoptions(precision=3
> 
> print(names)
> 
> pring(rescaledx[0:5,:])
> 
> print(type(rescaledX))


# 4. normalización 
- Los valores de lso datos pueden escalar en el rango de [0,1] es decir, con el valor mínimo 0 y máximo 1. 
- Este método de preproesamiento puede ser útil para conjuntos de taod dispersos (muchos ceros) con atributos de escalas variables.
  - Cuando se utilizan algoritmos queponderan valores de entrada ocmo NN y algoritmos que usa medidad de distancia Ik-NN.
- Puede normalizar datos en Python con la clase <u>*Normalizer*</u>.

> from slearn.preprocessing import Normalizer <br>
> scaler = Normalizer()fit(X)<br>
> normalizedX = scaler.transform(X)<br>
> #summarize transformed dta<br>
> np.set_printoptions(precision=2)<br>
> print(names)
> <br>
> print(normalizedX[0:5,:])

# 5. Binarización
- Puede crear nuevos atributos binarios en Python usando la clase Binarizer.
- puede ver que todos los valore siguales o menores que 0 están marcados con 0 y todos los que están pro encima de 0 están marcados con 1.

> From sklearn-preprocessing import Binarizer<br>
> binarizer = Binarizer(threshold=(0.0)).fit(x)<br>
> binaryX = binarizer.transform(X)<br>
> #summarize transfformed data<br>
> np.set_printoptions(presicion=3)<br>
> print(names)
> print(binaryX[0:5],5)


# 6. Box-Cox 
- los atributos representan un sesgo o inclinación (Gaussiana desplazada).
  - Box-Cox asume todos los atributos positovos.
  - Aplica la transformación a los atributos que parecen tener sesgo.
  - Corrige la no linealidad en relación (mejorar correlación entre las variables).
  - 