# TP 2 — Clasificación: predicción de lluvia en Australia

Segundo trabajo práctico de **Aprendizaje Automático 1**. Los integrantes y las instrucciones para armar el entorno están en el [README del repositorio](../README.md).

## Problema

Predecir, a las 23:59 de cada día, si al día siguiente va a llover en una ciudad de Australia (`RainTomorrow`, `Yes` / `No`), a partir de las observaciones meteorológicas de ese día: temperaturas, lluvia, sol, nubosidad, viento, humedad y presión, junto con la ciudad y la fecha.

Como la variable a predecir es una de dos categorías, es un problema de clasificación binaria. El enunciado pide resolverlo con regresión logística y con una red neuronal, compararlos, y poner el modelo elegido en producción con Docker.

## Archivos

| Archivo | Descripción |
|---|---|
| `TP-clasificacion-AA1.ipynb` | **Notebook con el desarrollo.** Es la entrega |
| `weatherAUS_2026C2.csv` | Dataset: 145.412 filas y 25 columnas, 49 ciudades entre 2007 y 2017 |
| `TrabajoPrácticoClasificacionAA1_2026C2.pdf` | Consigna de la cátedra |

Las definiciones de las variables son las de la [descripción del dataset en Kaggle](https://www.kaggle.com/datasets/arunavakrchakraborty/australia-weather-data/data).

## Cómo correrlo

Con el entorno activado (ver el [README del repositorio](../README.md)):

```bash
jupyter notebook TP-clasificacion-AA1.ipynb
```

El notebook lee el dataset desde esta misma carpeta y se ejecuta de principio a fin en orden, sin pasos manuales intermedios. La semilla está fijada, así que los números son los mismos en cada corrida. Una corrida completa tarda unos cuatro minutos, casi todos en la imputación por regresión, que se ajusta dos veces: en la comparación de métodos y en el preprocesamiento final.

## Cómo está organizado el notebook

### Análisis descriptivo y preprocesamiento

Recorrido de las variables, chequeos de consistencia, análisis de faltantes, balance de clases, división en entrenamiento / validación / prueba, visualizaciones, transformación logarítmica, codificación, imputación, matriz de correlación y escalado.

Las decisiones que más pesan en el resultado, todas justificadas en el notebook:

- Se descarta `RainfallTomorrow`: `RainTomorrow` es exactamente esa columna cortada en 1 mm, así que es la respuesta. También `RainToday`, que es `Rainfall` cortada en 1 mm y no agrega información.
- Se eliminan las 3.259 filas sin `RainTomorrow` y las 2.085 con la mitad o más de las variables vacías: el 3,68% del archivo.
- La división es por fecha (70% / 10% / 20%), no al azar: el modelo siempre predice el futuro, y las ciudades vecinas coinciden en la lluvia el mismo día. Prueba va de noviembre de 2015 a junio de 2017.
- Los faltantes son en su mayoría estructurales (estaciones que nunca miden una variable). Se imputan con regresión a partir de las otras variables del mismo día (`IterativeImputer`), elegida comparando contra la mediana global y la mediana por ciudad y mes sobre valores ocultos a propósito.
- Las direcciones de viento y el mes se codifican con seno y coseno. Los momentos de calma, que no tienen dirección, van al centro del círculo. La ciudad va con one-hot.

Todo el preprocesamiento está en un único `Pipeline` de scikit-learn, ajustado sólo con entrenamiento. Quedan 98.004 / 14.016 / 28.048 filas con 73 columnas.

## Estado

| Ítem de la consigna | Estado |
|---|---|
| 1. Análisis descriptivo y preprocesamiento | Completo |
| 2. Regresión logística | Pendiente |
| 3. Modelo base | Pendiente |
| 4. Optimización de hiperparámetros | Pendiente |
| 5. Explicabilidad | Pendiente |
| 6. AutoML con PyCaret | Pendiente |
| 7. Red neuronal | Pendiente |
| 8. Comparación de modelos | Pendiente |
| 9. MLOps | Pendiente |
| 10. Conclusión | Pendiente |

Entregas parciales: ítems 1 a 3 hasta el 30/10, 4 a 6 hasta el 13/11, y 7 a 10 hasta el 27/11.
