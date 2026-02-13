# sueños
El objetivo actual del proyecto es crear un modelo que en base a señales edf realice una prediccion binaria sobre si el paciente esta teniendo un sueño agradable o desagradable.
Como esto es un poco abstracto en caso de no obtener resultados me centraria en otro objetivo distinto un poco mas simple, entrenar un modelo para distinguir entre sueño vs no sueño en base al edf.

# Estado del arte 
https://www.utupub.fi/bitstream/handle/10024/157843/Sikka%20et%20al_2019_Published.pdf?sequence=1&isAllowed=y
 
Este es el paper sobre los datos que estoy usando, en el se usan modelos para relacionar las señales cerebrales con distintas emociones vividas en sueños, la tabla en imagenes resume los resultados que obtuvieron, donde se relaciona la asimetria frontal alfa con las distintas emociones. En el proyecto explorare esta relacion y otros posibles patrones de las edf con las distintas emociones.






https://onlinelibrary.wiley.com/doi/epdf/10.1155/bmri/3585125


En este paper desarrollaron un modelo automático que clasifica si una persona estaba soñando o no durante el sueño, a partir de señales EEG.

 
✔ Usaron un dataset público del proyecto DREAM con EEG de 58 canales recolectados durante sueño REM y NREM.
✔ 28 sujetos reportaron si tuvieron sueño o no.
✔ Extrajeron características de EEG empleando:

Common Spatial Patterns (CSP)

Discrete Wavelet Transform (DWT)

Estas características alimentaron modelos ML para clasificar dream vs dreamless.

  Resultados principales

✔ Los modelos alcanzaron > 85 % de exactitud para distinguir entre sueño y no sueño.
✔ Métodos de selección de canales (permutación y NSGA-II) encontraron que sólo 8–10 canales EEG pueden ser suficientes para clasificar con buen rendimiento.
✔ Cuando se deja fuera un sujeto al entrenar (leave-one-subject-out), la generalización a sujetos nuevos fue difícil, lo que indica que los modelos aún no generalizan bien a personas no vistas.

En el caso de que la prediccion de emociones sea demasiado complicada me centrare en mejorar este ultimo punto, la generalizacion. Diseñando un modelo que se entrene con variedad de sujetos para que no tenga este problema.






https://www.nature.com/articles/s41467-025-61945-1
El artículo presenta la base de datos DREAM, un proyecto que unifica y estandariza varios estudios de aprendizaje maquina sobre el sueño, de forma que facilita el acceso a estos dependiendo de las necesidades del proyecto. En la carpeta Metadata hay csvs con informacion sobre los distintos datasets, y los registros de cada uno. 






#Ratings.csv

El archivo Ratings.csv contiene las evaluaciones emocionales asociadas a cada despertar del dataset. Cada fila corresponde a un archivo EEG (casexx_syy.edf).

Incluye:

Filename: Identificador del registro (Case ID y Subject ID).

DreamReport_Wordcount: Número de palabras del reporte del sueño.

SR_PA1–SR_PA10: Autoevaluación (0–4) de emociones positivas.

SR_NA1–SR_NA10: Autoevaluación (0–4) de emociones negativas.

ER_*: Evaluaciones externas basadas en frecuencia de aparición en el relato.

En este proyecto se utiliza principalmente la suma de emociones positivas y negativas (self-rating) para construir un índice de valencia emocional del sueño.





#Métricas de evaluación
  
Accuracy

F1-score

ROC-AUC 