# TP Regresión — Predicción de precios de casas

Trabajo práctico de **Aprendizaje Automático 1**, Tecnicatura en Inteligencia
Artificial, FCEIA — UNR. Cuatrimestre 2, 2026.

## Integrantes

- Sofia Grando
- Amanda Tardugno
- Lucas Díaz
- Facundo Ferrerira

## Problema

Predecir el valor mediano de viviendas (`MEDV`, en miles de dólares) del dataset
de precios de casas de Boston, a partir de 13 características de la vivienda y su
entorno (criminalidad, cantidad de habitaciones, accesibilidad, nivel
socioeconómico de la zona, entre otras).

Se resuelve con regresión lineal múltiple: mínimos cuadrados (`LinearRegression`),
gradiente descendiente y métodos de regularización (Ridge, Lasso, Elastic Net),
comparando los modelos entre sí.

## Contenido

| Archivo | Descripción |
|---|---|
| `TP-regresion-AA1.ipynb` | Notebook con el desarrollo completo del trabajo |
| `house-prices-tp.csv` | Dataset (556 filas, 14 columnas) |

## Cómo ejecutarlo

Requiere Python 3 y las siguientes bibliotecas:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Luego, desde la raíz del repositorio:

```bash
jupyter notebook TP-regresion-AA1.ipynb
```

El notebook lee el dataset desde la misma carpeta y se ejecuta de principio a fin
en orden.
