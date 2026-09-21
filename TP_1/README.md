# TP 1 — Regresión: predicción de precios de casas

Primer trabajo práctico de **Aprendizaje Automático 1**. Los integrantes y las
instrucciones para armar el entorno están en el [README del
repositorio](../README.md).

## Problema

Predecir el valor mediano de las viviendas de cada barrio de Boston (`MEDV`, en
miles de dólares) a partir de 13 características de la vivienda y su entorno:
criminalidad, cantidad de habitaciones, accesibilidad a autopistas, nivel
socioeconómico de la zona, entre otras.

Como la variable a predecir es numérica y continua, es un problema de regresión.
Lo resolvemos con regresión lineal múltiple por tres caminos distintos —mínimos
cuadrados, gradiente descendiente y métodos de regularización— y después los
comparamos entre sí.

## Archivos

| Archivo | Descripción |
|---|---|
| `TP-regresion-AA1.ipynb` | **Notebook con el desarrollo completo.** Es la entrega |
| `house-prices-tp.csv` | Dataset: 556 filas y 14 columnas |
| `TrabajoPrácticoRegresiónAA1_2026C2.pdf` | Consigna de la cátedra |
| `Implementaciones-Descenso-del-Gradiente.ipynb` | Notebook de la Unidad 2, de donde salen las implementaciones de gradiente que usamos |

## Cómo correrlo

Con el entorno activado (ver el [README del repositorio](../README.md)):

```bash
jupyter notebook TP-regresion-AA1.ipynb
```

El notebook lee el dataset desde esta misma carpeta y se ejecuta de principio a
fin en orden, sin pasos manuales intermedios. La semilla está fijada, así que los
números son los mismos en cada corrida.

## Cómo está organizado el notebook

**Análisis descriptivo y preprocesamiento**

Recorrido de las 14 variables, tratamiento de los datos faltantes, división en
entrenamiento / validación / prueba, visualizaciones, matriz de correlación, test
de colinealidad (VIF), transformación logarítmica y escalado.

Las dos decisiones de limpieza que más pesan en el resultado, ambas justificadas
en el notebook:

- Se eliminan las 50 filas con valores faltantes en lugar de imputarlas.
- Se eliminan las 16 viviendas con `MEDV = 50`, donde el precio está censurado y
  el valor real es desconocido. Como consecuencia, **el modelo describe viviendas
  de menos de 50 mil dólares** y no cubre el segmento más caro.

Quedan 490 observaciones, repartidas en 343 / 49 / 98.

**Regresión lineal múltiple**

- `LinearRegression` (mínimos cuadrados) como modelo de referencia.
- Gradiente descendiente en sus tres variantes: por lotes, estocástico y
  mini-batch, con las curvas de error contra épocas.
- Regularización: Ridge, Lasso y Elastic Net, más un test de estabilidad de los
  coeficientes por remuestreo.

Las métricas elegidas son **R², RMSE y MAE**, reportadas sobre los tres conjuntos
para cada modelo.

## Estado

| Ítem de la consigna | Estado |
|---|---|
| 3 — Análisis descriptivo y preprocesamiento | Completo |
| 4 — Regresión lineal múltiple | Completo |
| 5 — Optimización de hiperparámetros | Pendiente |
| 6 — Comparación de modelos | Pendiente |
| 7 — Conclusión | Pendiente |
