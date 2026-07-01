# FDS-2026-1-16310 - Trabajo Final de Data Science

## Proyecto: Análisis de tendencias de videos de YouTube en Canadá aplicando CRISP-DM

Este repositorio contiene el desarrollo del Trabajo Final del curso **Fundamentos de Data Science (1ACC0216)**. El proyecto aplica la metodología **CRISP-DM** para analizar un conjunto de datos de videos en tendencia de YouTube correspondientes a Canadá, con el objetivo de generar conocimiento útil para una empresa de marketing digital.

---

## Integrantes

- Francesco Andre Meza Dagnino
- Ian Landauro La Rosa

---

## Objetivo del proyecto

Analizar las tendencias de los videos de YouTube en Canadá aplicando la metodología CRISP-DM, con la finalidad de identificar patrones relevantes relacionados con categorías de videos, canales, evolución temporal, distribución geográfica e indicadores de interacción como vistas, “Me gusta”, “No me gusta” y comentarios.

Además, se busca evaluar la factibilidad de construir un modelo predictivo que permita estimar el número de vistas (`views`) de los videos en tendencia, utilizando variables relevantes del conjunto de datos preparado.

---

## Metodología utilizada

El proyecto se desarrolló siguiendo las fases de la metodología **CRISP-DM**:

1. **Comprensión del negocio:** definición del problema, objetivos y requerimientos del cliente.
2. **Comprensión de los datos:** carga, inspección, exploración, visualización y verificación de calidad del dataset.
3. **Preparación de los datos:** limpieza, tratamiento de valores faltantes, integración del CSV con el JSON de categorías, creación de variables derivadas y generación del dataset final.
4. **Modelado y evaluación:** construcción y comparación de modelos de regresión para predecir el número de vistas.

---

## Descripción del conjunto de datos

El conjunto de datos utilizado corresponde a videos de YouTube que fueron tendencia en Canadá. Para el análisis se utilizaron dos archivos principales:

- `CAvideos_cc50_202101.csv`: contiene los registros de videos en tendencia.
- `CA_category_id.json`: contiene la información de las categorías de YouTube.

El dataset incluye variables como:

- `video_id`: identificador del video.
- `trending_date`: fecha en que el video apareció como tendencia.
- `title`: título del video.
- `channel_title`: canal que publicó el video.
- `category_id`: código de categoría del video.
- `publish_time`: fecha y hora de publicación del video.
- `views`: número de vistas.
- `likes`: cantidad de “Me gusta”.
- `dislikes`: cantidad de “No me gusta”.
- `comment_count`: cantidad de comentarios.
- `comments_disabled`: indica si los comentarios fueron desactivados.
- `ratings_disabled`: indica si las valoraciones fueron desactivadas.
- `video_error_or_removed`: indica si el video tuvo error o fue removido.
- `description`: descripción del video.
- `state`, `lat`, `lon`, `geometry`: variables geográficas incorporadas al dataset del proyecto.

Durante la preparación de datos se integró el archivo JSON para crear la variable `category_title`, que permite analizar los videos por nombre de categoría.

---

## Estructura del repositorio

```text
FDS-2026-1-16310/
│
├── data/
│   ├── CAvideos_cc50_202101.csv
│   ├── CA_category_id.json
│   └── CAvideos_clean.csv
│
├── code/
│   └── upc-2026-01-16310-5-tf.ipynb
│
└── README.md
```

---

## Herramientas utilizadas

El análisis fue desarrollado en Python mediante un notebook. Las principales librerías utilizadas fueron:

- Pandas
- NumPy
- Matplotlib
- Scikit-learn

---

## Archivos principales

### Carpeta `data`

Contiene los archivos de datos utilizados en el proyecto:

- `CAvideos_cc50_202101.csv`: dataset original de videos en tendencia de YouTube Canadá.
- `CA_category_id.json`: archivo JSON con las categorías de YouTube.
- `CAvideos_clean.csv`: dataset final preparado después del proceso de limpieza, integración y construcción de variables.

### Carpeta `code`

Contiene el notebook desarrollado en Python:

- `upc-2026-01-16310-5-tf.ipynb`: notebook principal con el desarrollo del proyecto según la metodología CRISP-DM.

---

## Variables derivadas creadas

Durante la fase de preparación de datos se crearon nuevas variables para enriquecer el análisis:

- `category_title`: nombre de la categoría del video, obtenido desde el archivo JSON.
- `days_to_trend`: cantidad de días entre la publicación del video y su aparición como tendencia.
- `like_dislike_ratio`: proporción entre “Me gusta” y “No me gusta”.
- `views_comments_ratio`: proporción entre vistas y comentarios.
- `like_rate`: proporción de likes respecto a vistas.
- `dislike_rate`: proporción de dislikes respecto a vistas.
- `comment_rate`: proporción de comentarios respecto a vistas.
- `log_views`: transformación logarítmica del número de vistas.
- `log_likes`: transformación logarítmica de likes.
- `log_dislikes`: transformación logarítmica de dislikes.
- `log_comment_count`: transformación logarítmica del número de comentarios.
- `trending_year`: año de tendencia.
- `trending_month`: mes de tendencia.
- `trending_weekday`: día de la semana en que el video fue tendencia.
- `is_weekend`: indica si el video fue tendencia durante fin de semana.
- `title_length`: longitud del título del video.
- `description_length`: longitud de la descripción del video.
- `tag_count`: cantidad de etiquetas asociadas al video.

---

## Requerimientos respondidos

El proyecto responde los siguientes requerimientos del cliente:

1. ¿Qué categorías de videos son las de mayor tendencia?
2. ¿Qué categorías de videos son las que más gustan? ¿Y cuáles son las que menos gustan?
3. ¿Qué categorías de videos tienen la mejor proporción entre “Me gusta” y “No me gusta”?
4. ¿Qué categorías de videos tienen la mejor proporción entre “Vistas” y “Comentarios”?
5. ¿Cómo ha cambiado el volumen de los videos en tendencia a lo largo del tiempo?
6. ¿Qué canales de YouTube son tendencia más frecuentemente? ¿Y cuáles aparecen con menor frecuencia?
7. ¿En qué estados se presenta el mayor número de “Vistas”, “Me gusta” y “No me gusta”?
8. ¿Los videos en tendencia son los que reciben mayor cantidad de comentarios positivos?
9. ¿Es factible predecir el número de “Vistas”, “Me gusta” o “No me gusta”?

---

## Principales resultados

- La categoría con mayor presencia en tendencia fue **Entertainment**.
- Algunas categorías como **Music** destacaron por altos niveles de “Me gusta”.
- Se identificaron canales con alta frecuencia de aparición en tendencia, como **SET India**, **MSNBC**, **FBE**, **The Young Turks** y **REACT**.
- Se calcularon ratios de interacción como `like_dislike_ratio` y `views_comments_ratio` para comparar categorías.
- Se verificó que no es posible afirmar directamente si los comentarios son positivos, debido a que el dataset no contiene el texto de los comentarios.
- Se construyó un modelo predictivo para estimar `views`, utilizando modelos de regresión.
- El modelo **Random Forest Regressor** obtuvo el mejor desempeño entre los modelos evaluados.

---

## Modelado

La variable dependiente seleccionada fue:

- `views`: número de vistas del video.

Para reducir el efecto de valores extremos, se utilizó la transformación logarítmica `log_views`.

Los modelos evaluados fueron:

- Baseline
- Ridge Regression
- Random Forest Regressor

Las métricas utilizadas para evaluar los modelos fueron:

- MAE
- RMSE
- R²

---

## Conclusiones generales

El proyecto permitió demostrar que los datos de YouTube pueden convertirse en conocimiento útil para una empresa de marketing digital. A partir del análisis, fue posible identificar categorías, canales y métricas de interacción relevantes para orientar decisiones de contenido y campañas digitales.

También se concluyó que sí es factible construir un modelo predictivo para estimar el número de vistas, aunque los resultados deben interpretarse como una herramienta de apoyo y no como una predicción exacta. La viralidad de los videos puede depender de factores externos no incluidos en el dataset, como eventos coyunturales, recomendaciones del algoritmo de YouTube o campañas fuera de la plataforma.

---

## Limitaciones

- El dataset no contiene el texto de los comentarios, por lo que no se pudo realizar análisis de sentimiento.
- Las variables geográficas fueron incorporadas de forma aleatoria, por lo que los resultados por estado deben interpretarse con cautela.
- Algunos videos aparecen más de una vez porque pueden mantenerse en tendencia durante varios días.
- Existen valores extremos en variables como vistas, likes, dislikes y comentarios.
- No se cuenta con variables adicionales como duración del video, número de suscriptores del canal, idioma, miniatura, inversión publicitaria o comportamiento histórico del canal.

---

## Trabajo futuro

Como trabajo futuro, se recomienda incorporar el texto real de los comentarios para realizar análisis de sentimiento y responder con mayor precisión si los comentarios son positivos, negativos o neutrales.

También sería útil comparar los resultados de Canadá con otros países incluidos en el conjunto de datos, como Estados Unidos, México, Gran Bretaña o India. Esto permitiría identificar diferencias entre mercados y observar si las categorías, canales y patrones de interacción cambian según el país.

Además, se podrían implementar modelos más avanzados, como Gradient Boosting, XGBoost o redes neuronales, y realizar ajuste de hiperparámetros para mejorar el desempeño predictivo.

Finalmente, se recomienda desarrollar un dashboard interactivo que permita explorar los resultados por categoría, canal, fecha y estado, facilitando la comunicación de resultados para una empresa de marketing digital.

---

## Instrucciones de uso

Para ejecutar el proyecto:

1. Clonar o descargar este repositorio.
2. Abrir el notebook ubicado en la carpeta `code`.
3. Verificar que los archivos de datos estén dentro de la carpeta `data`.
4. Ejecutar las celdas del notebook en orden.
5. Revisar las tablas, visualizaciones, limpieza de datos, respuestas a requerimientos y modelos generados.

---

## Licencia

Este proyecto fue desarrollado con fines académicos para el curso **Fundamentos de Data Science**.

El contenido del repositorio puede ser utilizado únicamente con fines educativos.
