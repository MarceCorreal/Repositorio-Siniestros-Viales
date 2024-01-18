PROYECTO DATA ANALYTICS
Marcela Correal García
Enero 17 de 2007

**Generalidades**

El presente repositorio, tiene como fin presentar el segundo proyecto individual de la cursada de Data analysis de Henry.
La finalidad del proyecto es estudiar la información de siniestros viales, con el fin de tener las herramientas para ayudar a las autoridades a definir proyectos y acciones 
que disminuyan la cantidad de víctimas mortales en los siniestros viales en la ciudad ded Buenos Aires.

**Data**

Se recibió un data set en excel que fué necesario estudiar al detalle. Con el fin de hacer el EDA la información para facilitar indicadores y herramientas se radicó en
Data Frames de Pandas, que a mi juicio es más fácil de manipular.
El Data Set consistió en tabla de Hechos y tabla de víctimas que posteriormete se unieron en un solo data set donde se radicó toda la información.

Además de esta información se incluyo la información de la población de la ciudad de buenos aires con el fin de calcular los KPIs. Queda en este repositorio el archivo original en excel que se bajó de internet y el data frame que se hizo con dicha tabla.

**EDA**

El paso a paso de las manipulaciones que se hicieron en la información inicial se encuentra en el archivo de Jupyter
"C:\Users\Usuario\Henry\Proyecto 2 Data Analytics\Repositorio Siniestros Viales\EDA_Siniestros_viales.ipynb"

La informacón de las columnas transformadas en  dicho archivo se encuetra a continuación:
<class 'pandas.core.frame.DataFrame'> RangeIndex: 30108 entries, 0 to 30107 Data columns (total 19 columns)
Data columns (total 19 columns):

 #   Column               Non-Null Count  Dtype  
---  ------               --------------  -----  
 0   IDENTIFICADOR        30108 non-null  object 
 1   ID                   30108 non-null  object 
 2   No_VICTIMAS          717 non-null    float64
 3   FECHA             717 non-null    object 
 4   HORA                 717 non-null    object 
 5   HH                   717 non-null    object 
 6   CALLE                716 non-null    object 
 7   CRUCE                540 non-null    object 
 8   DIRECCIÓN            708 non-null    object 
 9   COMUNA               717 non-null    float64
 10  XY (CABA)            717 non-null    object 
 11  LATITUD              717 non-null    object 
 12  LONGITUD             717 non-null    object 
 13  PARTICIPANTES        717 non-null    object 
 14  VICTIMA              717 non-null    object 
 15  ACUSADO              717 non-null    object 
 16  SEXO                 717 non-null    object 
 17  EDAD                 717 non-null    object 
 18  FECHA_FALLECIMIENTO  717 non-null    object 
dtypes: float64(2), object(17)
memory usage: 4.4+ MB

**KPIs**

Se solicitó desarrollar en la consigna del proyecto  los siguientes 2 KPis:

KPI1 = Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos 6 meses en CABA (geocodificación plana), en comparación con
la tasa de homicidios de siniestros viales del semestre anterior. Se define la tasa de homicidios en siniestros viales como el número de víctimas fatales en accidentes 
de tránsito por cada 100.000 habitantes en un área geográfica durante un periodo de tiempo específico

Para poder calcular este KPI fué necesario encontrar el censo de la población en buenos aires por años, desde 2016 a 2021, dado que es el rango de la información recibida. 
El censo año por año queda en el archivo "C:\Users\Usuario\Henry\Proyecto 2 Data Analytics\Repositorio Siniestros Viales\proy_1025_depto_caba.xls" (https://www.indec.gob.ar/ftp/cuadros/poblacion/proy_1025_depto_caba.xls) 
Esta información se convirtió a un data frame y se incluyó en el archivo EDA.
Su fórmula es: 

    (Número de homicidios en siniestros viales / Población total)*100.000

 Con el fin del cálculo de este KPI se hicieron en el dataframe original 5 columnas adicionales, a saber:
 Población_Actual= Refiriendose a la Población de Buenos Aires en el año del siniestro
 Población_Anterior: Refiriendose a la Población del Año anterior al siniestro
 Tasa_Víctimas_Actual: Cálculo de la tasa de homicidios utilizando el númedo de víctimas y homicidios del año de estdio
 Tasa Víctimas_Anterio: Cálculo de la tasa de homicidios utilizando el númedo de víctimas y homicidios del año anterior
KPI-1 =Calculando  la resta entre la Tasa_Víctimas_Anterior y Taza_Víctimas actual

Este valor se incluyó el la herramienta de KPI de POWER Bi, indicando como valor tope una nueva medida del 10%
   


KPI2 = Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior.
Se define la cantidad de accidentes mortales de motociclistas en siniestros viales como el numero absoluto de accidentes fatales en los que estuvieron involucrados víctimas que viajaban en moto en un determinado periodo temporal. Su fórmula para medir la evolución de los accidentes mortales con víctimas en moto es:

 (número de accidentes mortales con víctimas en moto en el año anterior - número de accidentes mortales con víctimas en moto en el año actual) / 
  número de accidentes mortales con víctimas en moto en el año anterior.
  
Posteriormente esta información se rá llevada a una base de datos, se utilizará el motor de búsqueda MySQL y la información y herramientas de datos se presentará en un dashboarde de PowerBI.
Por todo lo anterior, en este repositorio se presentan los siguientes archivos:



