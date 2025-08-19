# 🍟 Análisis de Reseñas de McDonald's en EE. UU.

## 📁 1. Definición del Proyecto  

### 🎯 Objetivo General  
Analizar las reseñas de clientes de sucursales de McDonald's en EE. UU. con el fin de identificar **patrones de satisfacción**, **desempeño de sucursales**, **palabras clave asociadas a reseñas positivas/negativas** y **tendencias ocultas** que ayuden a mejorar la experiencia del cliente y la toma de decisiones estratégicas.  

### ❓ Preguntas guía  
- ¿Qué tan satisfechos están los clientes en general?  
- ¿Cuáles son las sucursales con mejores y peores puntuaciones promedio?  
- ¿Qué palabras y frases se asocian más con reseñas positivas y negativas?  
- ¿Se pueden segmentar las reseñas o sucursales según patrones comunes?  
- ¿Existen relaciones entre las calificaciones numéricas y las palabras clave de los textos?  
- ¿Se observan tendencias geográficas en la satisfacción de los clientes?  

---
## Resumen del proyecto en un articulo
![Ejemplo de gráfico3](/reports/cartel.png)

## 🧹 2. Carga y Limpieza de Datos  

El dataset se obtuvo de **Kaggle**: *Exploring Customer Sentiments in McDonald's US Store Reviews*.  
- Contiene más de **33,000 reseñas anónimas** recopiladas de Google Reviews en distintas sucursales de McDonald's en EE. UU.  
- Incluye información clave como: nombre de la sucursal, ubicación (dirección, ciudad, estado, coordenadas), calificación numérica, texto de la reseña y fecha.  

### ✔️ Checklist de limpieza inicial  
- Importación de librerías principales: `pandas`, `numpy`, `matplotlib`, `seaborn`, `nltk`, `sklearn`.  
- Exploración básica con `head()`, `info()` y `describe()`.  
- Detección y tratamiento de **valores nulos**.  
- Eliminación de **duplicados** en reseñas.  
- Normalización de nombres de columnas (`snake_case`).  
- Conversión de `timestamp` a formato de fecha/hora.  
- Creación de columnas derivadas:  
  - Longitud de la reseña (`len(review_text)`).  
  - Calificación categórica (`positiva` ≥ 4, `negativa` ≤ 2, `neutral` = 3).  

---

## 🧼 3. Limpieza de Texto  

Se aplicó un preprocesamiento de **NLP (Procesamiento de Lenguaje Natural)** para preparar los textos de reseñas:  

- Conversión a **minúsculas**.  
- Eliminación de signos de puntuación, números y símbolos.  
- Eliminación de **stopwords** (palabras sin valor semántico como *el, la, de, to, and*).  
- **Lematización** (reducción de palabras a su forma base: “comiendo” → “comer”).  
- Creación de representaciones numéricas:  
  - **Bag of Words** (conteo simple de palabras).  
  - **TF-IDF** (ponderación de importancia de términos en todo el corpus).  

---

## 📊 4. Análisis Exploratorio de Datos (EDA)  

En esta etapa se exploraron las tendencias generales:  

- Distribución de calificaciones (¿predominan 5 estrellas o 1 estrella?).  
- Ranking de sucursales con mayor volumen de reseñas.  
- Promedio de calificaciones por sucursal.  
- Relación entre la **longitud del texto** y la calificación (reseñas largas suelen ser más negativas o más detalladas).  
- WordClouds de palabras frecuentes en reseñas positivas y negativas.  
- Matriz de correlación entre variables (ej. longitud de reseña vs calificación).  

---

## 🔎 5. Análisis de Texto  

Se aplicaron técnicas de **Text Mining** para profundizar en el contenido:  

- WordClouds diferenciados: palabras más comunes en reseñas positivas vs negativas.  
- Extracción de **bigramas y trigramas** (ej. “bad service”, “fast food cold”).  
- Asociación entre palabras y puntuaciones (ej. “frío” aparece en reseñas ≤ 2 estrellas).  
- Construcción de un **clasificador de sentimiento**:  
  - **Naive Bayes** y **Logistic Regression** como baseline.  
  - Input: TF-IDF.  
  - Output: positiva / negativa.  

---

## 📊 6. Modelado (Machine Learning Básico)  

Se probaron enfoques de **aprendizaje no supervisado y supervisado**:  

- **Clustering** con K-Means para agrupar reseñas según similitud de vocabulario.  
- **Clasificación supervisada** para predecir si una reseña es positiva o negativa en base a su texto.  
- **Reducción de dimensionalidad** con PCA/T-SNE para visualizar clusters en 2D.  

---

## 📍 7. Dashboard / Visualización Final  

Para hacer el análisis accesible a **stakeholders** se diseñó un dashboard interactivo (con **Streamlit** o **Power BI**) que incluye:  

- Mapa de calor con la distribución geográfica de reseñas.  
- Promedio de calificación por sucursal / región.  
- WordClouds dinámicos de palabras positivas y negativas.  
- Gráficos comparativos de evolución temporal de reseñas.  

---

## 📝 8. Conclusiones & Recomendaciones  

### Conclusiones (ejemplo ficticio):  
- Las sucursales del **estado de Texas** muestran calificaciones bajas (< 3).  
- Palabras negativas frecuentes: *frío, caro, lento*.  
- El 25% de las reseñas negativas se concentran en 3 sucursales específicas.  
- Clientes satisfechos mencionan *rápido* y *amable* con mayor frecuencia.  

### Recomendaciones:  
- Capacitar al personal en sucursales con menor calificación en **tiempos de atención**.  
- Mejorar control de **temperatura de alimentos** en zonas donde aparece “frío”.  
- Implementar campañas de fidelización en regiones con mala reputación.  
- Reforzar prácticas de **servicio rápido y amabilidad** en las sucursales mejor valoradas.  

---
