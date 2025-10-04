# Predicci-n-del-Tipo-de-Cambio-con-FFNN-y-API-de-Banxico
# 📊 Predicción del Tipo de Cambio con FFNN y API de Banxico

En esta actividad aplicaremos conceptos de **series de tiempo** y **redes neuronales feed-forward (FFNN)** para predecir el comportamiento del **tipo de cambio FIX (MXN/USD)** proporcionado por la API de Banxico.

A diferencia de los modelos estadísticos tradicionales (**ARIMA, SARIMA**), una FFNN no utiliza supuestos sobre la estructura del proceso generador de datos, sino que **aprende patrones directamente de los rezagos históricos** de la serie. Esto abre la posibilidad de capturar **relaciones no lineales**, aunque también requiere diseñar cuidadosamente los hiperparámetros (capas, neuronas, funciones de activación, epochs, batch size) y la ventana temporal que se utilizará como entrada del modelo.

---

## 👥 Integrantes del equipo

- Mari  
- Stivi  
- Ivo  
- Remi  
- Cheve  

---

## 🛠️ Tecnologías utilizadas

<p align="center">
  <img src="https://www.python.org/static/community_logos/python-logo.png" alt="Python" width="100"/>
  <img src="https://upload.wikimedia.org/wikipedia/commons/a/ab/TensorFlow_logo.svg" alt="TensorFlow" width="100"/>
  <img src="https://keras.io/img/logo.png" alt="Keras" width="80"/>
  <img src="https://upload.wikimedia.org/wikipedia/commons/8/84/Plotly-logo.png" alt="Plotly" width="100"/>
  <img src="https://upload.wikimedia.org/wikipedia/commons/e/ed/Pandas_logo.svg" alt="Pandas" width="120"/>
  <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="Scikit-learn" width="120"/>
  <img src="https://www.banxico.org.mx/favicon.ico" alt="Banxico API" width="40"/>
</p>

---

## 🔹 1. Obtención de datos

- Conéctense a la **API de Banxico** para descargar la serie histórica del tipo de cambio FIX.  
- Usen al menos **2 años de datos** para entrenar.  
- Conserven los **últimos 15 días** como conjunto de prueba (test set).  

---

## 🔹 2. Preparación de datos

- Normalicen los datos (ejemplo: **MinMaxScaler**).  
- Construyan ventanas deslizantes de tamaño definido (ejemplo: 10, 15, 30 días).  
- Justifiquen el tamaño de la ventana: ¿por qué ese número de rezagos es razonable?  

---

## 🔹 3. Construcción del modelo FFNN

Definan una red neuronal secuencial en **Keras** con:

- Una o más capas densas ocultas con funciones de activación no lineales (ej. **ReLU**, **tanh**).  
- Una capa de salida con 1 neurona (valor del tipo de cambio).  
- Selección de hiperparámetros: número de capas, neuronas, epochs, batch size, optimizador.  

📌 **Nota:** Expliquen brevemente las decisiones que tomaron en el diseño del modelo.

---

## 🔹 4. Entrenamiento y predicción

- Entrenen el modelo con los datos de entrenamiento.  
- Generen predicciones para los últimos **15 días** (test).  
- Transformen nuevamente los valores a su escala original.  

---

## 🔹 5. Evaluación del modelo


---

## 🔹 6. Análisis
---

## ✅ Checklist

- [ ] Descargar datos de Banxico (2+ años).  
- [ ] Preparar y normalizar datos.  
- [ ] Construir ventanas deslizantes.  
- [ ] Definir arquitectura de la FFNN.  
- [ ] Entrenar modelo y generar predicciones.  
- [ ] Evaluar con MAPE y compararlo contra un modelo ingenuo.  
- [ ] Agregar gráficas en este README.  

---
