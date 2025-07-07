
## Abstract

Este trabajo propone un sistema de recomendación de videojuegos que incorpora el estado emocional que el usuario desea experimentar. Para lograrlo, se combinan dos enfoques: un modelo tradicional DeepFM, que utiliza datos explícitos e implícitos del usuario, y un componente basado en NLP que interpreta un prompt emocional mediante un modelo BERT fine-tuneado. Ambos modelos se integran mediante un ensamble ponderado que permite recomendaciones personalizadas según emociones buscadas en los videojuegos. Los resultados muestran que el modelo NLP no es competitivo por sí solo, pero el ensamble logra incorporar la emoción deseada sin sacrificar demasiado rendimiento.

## 📁 Principales archivos

Se realizaron dos cuadernillos .ipynb trabajados en Google Colab:

- `Proyecto_NLP_G06.ipynb`: Cuadernillo donde se cargo el BERT finetuneado y se utilizó para predecir el score de las 6 emociones de cada emoción, utilizando games.csv para precomputar las emociones de todos los juegos disponibles y no solo los filtrados, obteniendo games_emotion para futuros calculos en el otro cuadernillo. Para correr el archivo es necesario solo subir en colab el archivo games.csv y game-metadata.json, y luego ejecutar las celdas.
- `Proyecto_G06.ipynb`: Cuadernillo con el todo el análisis de datos y prueba de modelos, en este solo se debe importar todos los csv filtrados, el csv de games_emotion y el de metadata. Esto funcionará, no obstante es importante ir corriendo el código secuencialmente en orden, debido a que en el modelo NLP por ejemplo, es necesario que se hayan ejecutado otras celdas anteriores. Por otro lado, también en la primera sección se deja el código para descargar el dataset completo de kaggle. Sin embargo, esto no es necesario y se puede empezar el código directamente desde la sección de análisis de datos subiendo los archivos antes mencionados.

## 📚 Dataset

Se usaron datos públicos de Steam:

- `filter_games.csv`: Información general de los juegos (35.032 registros).
- `filter_recommendations.csv`: Recomendaciones y reviews de usuarios (1.5M registros).
- `filter_users.csv`: Datos de usuarios (8.364 registros).
- `game-metadata.json`: Descripciones y etiquetas (50.872 registros).
- `games_emotion.csv`: CSV con los puntajes para cada una de las 6 emociones en cada juego que tenia descripciones y tags.


Para mejorar eficiencia, solo se consideraron juegos con más de 100 reviews.

---

## 💬 Prompts emocionales de ejemplo

Estos son los prompts usados para mapear emociones y obtener las métricas relacionadas al uso del NLP:

- `"i want to play a sad game, i want to cry"` → sadness  
- `"i want to play a horror game, i wanna feel fear"` → fear  
- `"idk, i just wanna play a game about a relationship"` → love  
- `"i just wanna play a normal and fun game"` → joy  
- `"i want to play a game about wars that make me feel anger"` → anger  
- `"i want to feel surprise"` → surprise  

---

## ⚠️ Limitaciones

- El modelo BERT fue fine-tuneado en un dataset genérico (GoEmotions), no específico del dominio de videojuegos.
- No todos los juegos tenían descripciones o tags, lo cual limita el alcance del modelo NLP. Además que no contaban con otro tipo de información
como imágenes, comentarios o demás.
- Se trabajó en Google Colab, por lo que la capacidad de procesamiento fue restringida.

---

## 👨‍💻 Autores

- Benito Alonso Oliva Tesla  
- Justo Matías Solís Zlatar  
- Daniel Ignacio Vera Ortiz  

Asignatura: *Sistemas de Recomendación*, Pontificia Universidad Católica de Chile  
Profesor: Denis Parra Santander

---

## 🔗 Enlace al paper

Puedes consultar el paper en formato PDF [aquí](./Emotion-based-recommendation_G06.pdf).

---
