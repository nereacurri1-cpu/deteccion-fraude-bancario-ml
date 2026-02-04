# Detección de Fraude Bancario con Machine Learning

##  Descripción del proyecto
Este proyecto tiene como objetivo desarrollar un sistema de detección de fraude bancario utilizando técnicas de Machine Learning. El problema abordado presenta un fuerte desbalance de clases, ya que las transacciones fraudulentas representan una proporción muy pequeña del total.

Se comparan distintos modelos de clasificación y se evalúan utilizando múltiples métricas, priorizando la capacidad de detección de fraudes reales.



##  Objetivos
- Analizar un conjunto de datos real de transacciones bancarias.
- Preparar los datos para modelos de Machine Learning.
- Manejar el desbalance de clases mediante estratificación y ponderación.
- Entrenar y comparar distintos modelos de clasificación.
- Optimizar hiperparámetros del mejor modelo.
- Evaluar el desempeño final sobre un conjunto de prueba.
- Interpretar resultados y métricas desde una perspectiva práctica.



##  Dataset
- **Fuente:** Kaggle – Credit Card Fraud Detection
- **Registros:** 284.807 transacciones
- **Variables:** 31
- **Variable objetivo:** `Class`  
  - 0: Transacción legítima  
  - 1: Transacción fraudulenta  

### Variables principales
- `V1` – `V28`: Variables numéricas anonimizadas mediante PCA.
- `Time`: Segundos desde la primera transacción registrada.
- `Amount`: Monto de la transacción.
- `Class`: Variable objetivo.

El dataset presenta un **fuerte desbalance**, con menos del 1% de transacciones fraudulentas.



##  Análisis Exploratorio
- Análisis de correlación entre variables y la clase objetivo.
- Identificación de variables más relevantes.
- Evaluación de la hipótesis sobre la variable `Amount`, observando que no presenta una relación directa fuerte con el fraude.



##  Preparación de los datos
- Separación en conjuntos de entrenamiento y prueba con **estratificación**.
- Uso de pipelines para:
  - Escalado de variables numéricas.
  - Integración de preprocesamiento y modelos.
- La variable objetivo no es escalada.



##  Modelos evaluados
- Regresión Lineal (modelo de referencia)
- Regresión Logística
- Árbol de Decisión
- Random Forest

La regresión lineal se utiliza únicamente como referencia, ya que no es adecuada para problemas de clasificación binaria desbalanceada.



##  Evaluación
Se utilizaron las siguientes métricas:
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

La evaluación se realizó mediante **validación cruzada estratificada**, priorizando métricas adecuadas para datasets desbalanceados.



##  Optimización de hiperparámetros
Se aplicó **RandomizedSearchCV** sobre el modelo Random Forest debido a su amplio espacio de hiperparámetros, optimizando principalmente la métrica ROC-AUC.



##  Resultados finales
El modelo Random Forest optimizado fue evaluado sobre el conjunto de prueba, obteniendo:
- Alta capacidad de detección de fraudes (recall elevado).
- Buen poder de discriminación entre clases (ROC-AUC alto).
- Presencia de falsos positivos, aceptable en un sistema de alerta temprana.



##  Conclusiones
- Random Forest fue el modelo con mejor desempeño general.
- El uso de métricas adecuadas es clave en problemas desbalanceados.
- La variable `Amount` no resulta tan determinante como se podría suponer inicialmente.
- El modelo es adecuado como sistema de apoyo para detección de fraude, con revisión humana posterior.



##  Trabajo futuro
- Ajuste del umbral de decisión para reducir falsos positivos.
- Aplicación de técnicas de sobremuestreo (SMOTE).
- Evaluación de modelos avanzados como Gradient Boosting o XGBoost.



##  Tecnologías utilizadas
- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Google Colab
