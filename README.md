## Sentiment Classification in Movie Reviews

Informe: [Informe](informe.pdf)

### Resumen

Este proyecto implementa un sistema de **clasificación automática de sentimiento** aplicado a reseñas de películas. El objetivo es determinar si una reseña expresa una **opinión positiva o negativa** utilizando técnicas de **Procesamiento de Lenguaje Natural (NLP)** y **aprendizaje automático**.

---

## Descripción del Problema y Dataset

El objetivo es clasificar reseñas de películas según su **polaridad de sentimiento**.

El dataset utilizado contiene:

- **50,000 reseñas**
- **25,000 para entrenamiento**
- **25,000 para evaluación**

La distribución está balanceada:

- **25,000 reseñas positivas**
- **25,000 reseñas negativas**

Las etiquetas se definieron según la puntuación otorgada por los usuarios:

- **Positivas:** puntuación ≥ 7/10  
- **Negativas:** puntuación ≤ 4/10  

Las reseñas con puntuaciones intermedias fueron excluidas para evitar ambigüedad en las etiquetas.

Además, el dataset fue diseñado para mejorar la capacidad de generalización del modelo:

- Máximo **30 reseñas por película**
- Películas **distintas entre entrenamiento y prueba**

Esto evita que el modelo memorice características específicas de una película en lugar de aprender patrones generales de sentimiento.

---

## Metodología

### Preprocesamiento de Texto

Antes de extraer características, las reseñas fueron limpiadas y normalizadas.

Las principales etapas del preprocesamiento incluyen:

- **Tokenización**
- Eliminación de **stopwords**
- Eliminación de **números**
- **Stemming** utilizando Porter Stemmer
- Filtrado de palabras fuera del diccionario inglés de **NLTK**

El objetivo de este proceso es reducir el ruido lingüístico y mantener únicamente términos relevantes para la clasificación.

---

### Representación de Texto con TF-IDF

Para convertir el texto en datos numéricos se utilizó **TF-IDF (Term Frequency – Inverse Document Frequency)**.

Este método:

- asigna mayor peso a palabras informativas
- reduce la influencia de palabras muy frecuentes dentro del corpus

Después de la vectorización, cada reseña se representa como un vector dentro de un espacio de aproximadamente:

**19,212 características**

---

### Reducción de Dimensionalidad con PCA

La representación generada por TF-IDF produce un espacio de características muy grande. Para reducir esta dimensionalidad se aplicó **PCA (Principal Component Analysis)**.

Los resultados del análisis mostraron que:

- **11,923 componentes** explican aproximadamente **95 % de la varianza**

Esto permite reducir el tamaño del espacio de características manteniendo la mayor parte de la información relevante para el modelo.

---

## Pipeline del Sistema

El flujo completo de procesamiento utilizado en el proyecto es:

Texto
↓
Preprocesamiento
↓
Vectorización TF-IDF
↓
Escalamiento
↓
PCA
↓
Clasificación


Este pipeline permite estructurar el procesamiento de datos y facilita experimentar con distintos enfoques manteniendo una arquitectura clara.

---

## Resultados

Las pruebas realizadas muestran que:

- **TF-IDF es una representación efectiva para clasificación de texto**
- **PCA reduce significativamente la dimensionalidad** manteniendo la mayor parte de la información
- El sistema logra clasificar reseñas positivas y negativas de manera consistente

También se exploraron métodos alternativos de procesamiento de texto, como técnicas de análisis sintáctico, pero no mostraron mejoras significativas frente al enfoque basado en TF-IDF.

---

## Tecnologías Utilizadas

- Python  
- Scikit-learn  
- NLTK  
- NumPy  
- Pandas  
- Matplotlib  
- PyTorch