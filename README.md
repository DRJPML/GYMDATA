<p align="center">
  <img src=(https://github.com/user-attachments/assets/3bb12fd4-a8da-4957-b74d-7c058b764294) alt="Descripción de la imagen" width="300" />

# Análisis de factores de entrenamiento y fisiología en usuarios de gimnasio

## Selección y justificación de la base de datos
La base de datos fue extraída de Kaggle https://www.kaggle.com/datasets/valakhorasani/gym-members-exercise-dataset y se tradujo al español por comodidad en la lectura del análisis en el cuadernillo. Consta de 15 columnas y 973 registros; es información de los usuarios de un gimnasio que contiene datos con características fisiológicas que evalúan el rendimiento por persona en las siguientes categorías: edad, genero, peso (kg), altura (m), latidos por minuto máximo, latidos por minuto promedio, latidos por minuto en reposo, duración de la sesión (horas), calorías quemadas, porcentaje de grasa, e índice de masa corporal. Los datos también aportan detalles sobre su entrenamiento y hábitos: tipo de entrenamiento, ingesta de agua (litros), frecuencia de entrenamiento (días/semana) y nivel de experiencia.

**Objetivo de análisis:** Comprender el estado físico de los usuarios durante su entrenamiento a fin de mejorarlo. Esto es importante para evaluar su salud general y estado físico a fin de ayudarle, y a su instructor, a establecer objetivos de entrenamiento y monitorear su progreso.

**Objetivo de predicción:** Predecir el porcentaje de grasa corporal de los usuarios del gimnasio utilizando sus datos fisiológicos y hábitos de entrenamiento.

El análisis y la predicción son valiosos para diseñar programas de entrenamiento personalizados (puede ayudar a los entrenadores a ajustar planes de entrenamiento y nutrición) y mejorar la retención de clientes en el gimnasio (con programas de fidelización, por ejemplo).

### Preguntas de investigación
Las preguntas que se pretenden responder son: **¿Qué características fisiológicas y de entrenamiento tienen un mayor impacto en el porcentaje de grasa corporal de los usuarios? ¿Es posible predecir con precisión el porcentaje de grasa corporal en función de variables como el género, peso, frecuencia de entrenamiento, y duración de la sesión?**

## Preparación y Limpieza de los Datos
Para una primera exploración se utilizó el software Microsoft Excel. En éste se hizo una traducción al español de la base de datos. La segunda exploración se realizó a través de Python, desde aquí se hizo la manipulación, análisis y presentación de los primeros histogramas y gráficas de dispersión para visualizar todos los datos.
La base de datos tiene 976 registros, con quince variables: 
Hábitos de entrenamiento: duración de la sesión (horas), tipo de entrenamiento, ingesta de agua (litros), frecuencia de entrenamiento (días/semana) y nivel de experiencia.
Características fisiológicas: edad, genero, peso (kg), altura (m), latidos por minuto máximo, latidos por minuto promedio, latidos por minuto en reposo, calorías quemadas, porcentaje de grasa, e índice de masa corporal.
El dataframe no contiene valores nulos y sin errores visibles en la captura de datos. Se eliminaron tres variables que no se consideraron relevantes para el análisis, las relacionadas con latidos por minuto.
El tipo de datos es 7 integer (int64), 6 numeric (float 64) y 2 varchar (object). La columna género (object) se modificó a valores 1 y 0 para hombre y mujer respectivamente.

![Limpieza de los datos](https://github.com/user-attachments/assets/54eede55-0609-4cd6-80bf-96fb14ab7490)

 
## Análisis Exploratorio de los Datos
El análisis exploratorio arroja datos de la fisiología y dinámica del gimnasio, que nos aporta una descripción de su población y características generales:
La edad promedio es de 38.6 años, existe una buena distribución de los datos como muestra el histograma de edad, hay un equilibrio entre adultos mayores y jóvenes, mismo que se observa entre hombres y mujeres con una relación de 52.5% de hombres respecto a un 48.5% de mujeres. La mayoría de los usuarios están por debajo de los 80 kg, con un promedio de 73.85. La mayoría usa el gimnasio entre hora y hora y media (promedio 1.25 horas).
La mayoría de los usuarios quema en su sesión entre 750 y 1000 calorías, y su porcentaje de grasa está cargado entre el 25 y 30%. El promedio de ingesta de agua es de 2.62 litros, con picos de hasta 3.7 litros. La mayoría entrena 3 días a la semana (media de 3.32) y la mayoría tiene un nivel de experiencia intermedio, aunque hay un gran grupo que son principiantes.
En general existen datos esperados en el funcionamiento de un gimnasio, se han localizado grupos de gymrats que representan una clientela fidelizada frente a grupos promedio. Es interesante la segmentación por género y son datos esperados por la complexión física.
La correlación no indica grandes hallazgos: a mayor frecuencia de entrenamiento (días a la semana), mayor nivel de experiencia, o entrenan más quienes tienen más expertiz (corelación del 84%). Es esperada también la correlación entre peso e índice de masa corporal de 85%, así como la duración de la sesión y calorías quemadas: mientras más se entrena más se adelgaza.
Para toda la población hay un muy buen índice de masa corporal con poca obesidad; el tipo de entrenamiento es homologado: no hay una preferencia visible. Hay una ligera variación en los ejercicios de fuerza, donde hay un poco más de mujeres que de hombres. Las mujeres beben menos agua y los hombres más; el dato es esperado por la complexión física.


Hay 53% de hombres y 47% de mujeres. Los índices de masa corporal muestran datos homogéneos que representan el 90.6% de los  usuarios que varían de entre 12 y 49 puntos de IMC. Se separa un grupo, de gymrats, de peso asociado a nivel de experiencia y bajo porcentaje de grasa corporal.



Durante el estudio efectuado, se nota una dispersión homogénea en la mayoría de los datos, esto indica un elevado grado de variabilidad entre las observaciones, lo que podría afectar la exactitud de los modelos predictivos y la interpretación de los resultados. Es importante considerar esta organización al analizar la conducta de las variables, dado que podría ser una señal de factores subyacentes o de variabilidad intrínseca en el conjunto de datos.
La variable a predecir es el porcentaje de grasa, que no es significativo con respecto a la edad, hay un entorno heterogéneo. Los datos muestran que en este gimnasio los hombres tienen de media menos porcentaje de grasa corporal que las mujeres.
Gymrats: Con relación al peso hay dos grupos que se separan del resto: mujeres con una media de 60 kilos y bajo porcentaje de grasa corporal y hombres de entre 80 y 90 kilos con un muy bajo porcentaje de grasa corporal. La separación de los grupos también es visible con relación a la altura, aunque hay más dispersión en este caso, así como a la duración de la sesión.
Lo anterior es claramente observable en las gráficas de dispersión en el porcentaje de grasa, duración de la sesión, y peso, y además es visible con un mayor grado de dispersión en otras como calorías quemadas , ingesta de agua y nivel de experiencia.  

## Visualización de resultados




## Conclusiones
El análisis busca responder a las preguntas planteadas y se arrojan las siguientes conclusiones:
¿Qué características fisiológicas y de entrenamiento tienen un mayor impacto en el porcentaje de grasa corporal de los usuarios? Con base en el análisis realizado, las características fisiológicas y de entrenamiento que parecen tener un mayor impacto en el porcentaje de grasa corporal de los usuarios son:
**Peso:** Existe una clara diferenciación entre grupos de peso y porcentaje de grasa corporal. Los usuarios con menor porcentaje de grasa se encuentran en el grupo de mayor peso, particularmente entre los hombres (80-90 kg), y en el grupo de mujeres alrededor de los 60 kg.
**Género:** Se observó que, en promedio, los hombres tienen un porcentaje de grasa corporal menor en comparación con las mujeres, lo cual se asocia con diferencias en el tipo de entrenamiento y en el consumo de agua.
**Duración de la sesión de entrenamiento:** Los usuarios que entrenan por períodos más largos tienden a tener un menor porcentaje de grasa corporal. Esto sugiere que la duración de la sesión podría estar vinculada a un mayor consumo de calorías y una reducción en el porcentaje de grasa corporal.
¿Es posible predecir con precisión el porcentaje de grasa corporal en función de variables como el género, peso, frecuencia de entrenamiento, y duración de la sesión? Sobre la Predicción del Porcentaje de Grasa Corporal Es posible predecir el porcentaje de grasa corporal utilizando variables como género, peso, frecuencia de entrenamiento y duración de la sesión con una certeza del 81.4%. Sin embargo, el modelo actual tiene un margen de error de entre 2.3 y 2.7 puntos porcentuales en promedio, lo cual es aceptable para ciertas aplicaciones. Aun así, estos resultados deben interpretarse como estimaciones y no valores absolutos.

### Recomendaciones
Hay dos grupos identificados: a) especializado y b) homogéneo, que genera pocos resultados con su entrenamiento y no se sale del promedio. Para el primero se pueden plantear programas de fidelización y recompensas. Para el segundo, personalización en programas especializados de nutrición y duración de las sesiones. Algunas recomendaciones son: 
Tarjetas y/o programas de fidelización. 
Programas de recompensas y regalos con artículos de entrenamiento y  promocionales. 
Programas personalizados (de alimentación, suplementación o hábitos de sueño) para mejorar las condiciones fisiológicas. 
Rutinas personalizadas con base en las características fisiológicas del usuario y sus hábitos de entrenamiento.

### Posibles limitaciones del análisis
Tamaño y diversidad de la muestra: si la base de datos no incluye suficientes usuarios o diversidad en los perfiles (edad, género, tipo de entrenamiento), los resultados podrían no ser representativos de una población más amplia. El modelo podría beneficiarse de mejoras adicionales, como la inclusión de más datos o el ajuste de parámetros para optimizar la precisión.
Falta de datos cualitativos: datos importantes como hábitos alimenticios, calidad del sueño, y nivel de estrés no se incluyen, lo que puede limitar la comprensión de otros factores que influyen en la composición corporal.
Sesgo en el tipo de entrenamiento: si el gimnasio se especializa en un tipo específico de entrenamiento, o no hay registro de la elección de los usuarios (por ejemplo, en un mismo día), los datos podrían no reflejar una variedad suficiente en las preferencias de ejercicio.

### Sugerencias para trabajos futuros
Ampliar el alcance de la base de datos: incluir una mayor diversidad de usuarios y recopilar datos en varios gimnasios para mejorar la representatividad.
Incluir factores adicionales: recopilar datos sobre hábitos alimenticios, calidad de sueño, nivel de actividad física fuera del gimnasio y otros indicadores de salud como padecimientos crónicos, etcétera.
Segmentación temporal: analizar datos a lo largo del tiempo para identificar cambios en la composición corporal y ver cómo los patrones de entrenamiento afectan a largo plazo.
Grupos de control: comparar los datos del gimnasio con los de personas que entrenan en otros contextos (como en casa o al aire libre) para obtener una perspectiva más amplia.


