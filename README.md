
Este enfoque balancea la calidad de las recomendaciones con el componente emocional deseado por el usuario. Se experimentó con distintos valores de α (0.5, 0.7, 0.9), concluyendo que **α = 0.9** logra un buen equilibrio sin sacrificar rendimiento.

---

## 📈 Resultados y Métricas

| Modelo     | Recall@10 | MAP@10 | nDCG@10 | Novelty@10 | Diversity@10 |
|------------|-----------|--------|---------|------------|---------------|
| DeepFM     | 0.4560    | 0.7164 | 0.9100  | 12.7133    | 0.9506        |
| NLP        | 0.0001    | 0.0001 | 0.0018  | **18.8589**| **0.9939**    |
| Ensamble   | 0.4508    | 0.7059 | 0.9064  | 12.8310    | 0.9470        |

> 💡 Aunque el modelo NLP no es competitivo por sí solo en ranking, **mejora la diversidad y novedad** de las recomendaciones. Su incorporación en el ensamble permite adaptar las recomendaciones al estado emocional del usuario sin perder calidad.

---

## 📚 Dataset

Se usaron datos públicos de Steam:

- `games.csv`: Información general de los juegos (35.032 registros).
- `recommendations.csv`: Recomendaciones y reviews de usuarios (1.5M registros).
- `users.csv`: Datos de usuarios (8.364 registros).
- `game-metadata.json`: Descripciones y etiquetas (50.872 registros).

Para mejorar eficiencia, solo se consideraron juegos con más de 100 reviews.

---

## 💬 Prompts emocionales de ejemplo

Estos son algunos de los prompts usados para mapear emociones:

- `"i want to play a sad game, i want to cry"` → sadness  
- `"i want to play a horror game, i wanna feel fear"` → fear  
- `"idk, i just wanna play a game about a relationship"` → love  
- `"i just wanna play a normal and fun game"` → joy  
- `"i want to play a game about wars that make me feel anger"` → anger  
- `"i want to feel surprise"` → surprise  

---

## ⚠️ Limitaciones

- El modelo BERT fue fine-tuneado en un dataset genérico (GoEmotions), no específico del dominio de videojuegos.
- No todos los juegos tenían descripciones o tags, lo cual limita el alcance del modelo NLP.
- Se trabajó en Google Colab, por lo que la capacidad de procesamiento fue restringida.

---

## 🛠️ Requisitos técnicos

- Python 3.8+
- PyTorch
- Transformers (HuggingFace)
- deepctr-torch
- pandas, numpy, scikit-learn, etc.

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

## 📎 Licencia

Este proyecto es con fines educativos y de investigación. Puedes reutilizar el código citando la fuente.
