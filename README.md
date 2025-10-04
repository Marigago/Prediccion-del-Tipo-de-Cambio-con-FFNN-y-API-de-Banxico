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

---

## 🔹 6. Análisis 
---

## 📄 Resultados intermedios / Ejemplo de salida

```python
datetime64[ns]
(8520, 1)
            TipoCambio
Fecha                 
1991-11-12      3.0735
1991-11-13      3.0712
1991-11-14      3.0718
            TipoCambio
Fecha                 
2025-10-01     18.3477
2025-10-02     18.4843
2025-10-03     18.3902

Días entre 2021-01-01 y hoy: 1736

array([[0.64018385, 0.65805793, 0.61816955, ..., 0.59159554, 0.6207777 ,
        0.66528051],
       [0.65805793, 0.61816955, 0.65191143, ..., 0.6207777 , 0.66528051,
        0.69747209],
       [0.61816955, 0.65191143, 0.66294594, ..., 0.66528051, 0.69747209,
        0.67109871],
       ...,
       [0.44913183, 0.4416539 , 0.44466331, ..., 0.44174509, 0.42742759,
        0.42301379],
       [0.4416539 , 0.44466331, 0.41207047, ..., 0.42742759, 0.42301379,
        0.41942073],
       [0.44466331, 0.41207047, 0.41969432, ..., 0.42301379, 0.41942073,
        0.41152331]], shape=(1168, 15))

array([[0.41207047, 0.41969432, 0.42835777, 0.42961625, 0.4225031 ,
        0.42100751, 0.42137229, 0.43253447, 0.42890494, 0.44174509,
        0.42742759, 0.42301379, 0.41942073, 0.41152331, 0.39997811],
       [0.41969432, 0.42835777, 0.42961625, 0.4225031 , 0.42100751,
        0.42137229, 0.43253447, 0.42890494, 0.44174509, 0.42742759,
        0.42301379, 0.41942073, 0.41152331, 0.39997811, 0.39031152],
       [0.42835777, 0.42961625, 0.4225031 , 0.42100751, 0.42137229,
        0.43253447, 0.42890494, 0.44174509, 0.42742759, 0.42301379,
        0.41942073, 0.41152331, 0.39997811, 0.39031152, 0.36984752],
       ...,
       [0.39997811, 0.39031152, 0.36984752, 0.36295324, 0.36939155,
        0.37453491, 0.37800029, 0.36249726, 0.38219523, 0.38483986,
        0.37331291, 0.36751295, 0.36450354, 0.36696578, 0.39188006]])

array([0.69747209, 0.67109871, 0.70786824, ..., 0.41942073, 0.41152331,
       0.39997811], shape=(1168,))

array([0.39031152, 0.36984752, 0.36295324, 0.36939155, 0.37453491,
       0.37800029, 0.36249726, 0.38219523, 0.38483986, 0.37331291,
       0.36751295, 0.36450354, 0.36696578, 0.39188006, 0.3747173 ])


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
