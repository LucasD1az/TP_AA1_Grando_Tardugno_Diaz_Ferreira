# TP Regresión: predicción de precios de casas

Trabajo práctico de **Aprendizaje Automático 1**, Tecnicatura en Inteligencia
Artificial, FCEIA, UNR. Cuatrimestre 2, 2026.

## Integrantes

- Sofia Grando
- Amanda Tardugno
- Lucas Díaz
- Facundo Ferreira

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
| `requirements.txt` | Versiones exactas de las bibliotecas usadas |

## Cómo ejecutarlo

Requiere **Python 3.12**. Las dependencias se instalan en un entorno virtual
(`.venv/`), que no se versiona: cada uno lo crea en su máquina.

### Preparar el entorno (una sola vez)

Desde la raíz del repositorio:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

En Windows, la segunda línea es `.venv\Scripts\activate`.

### Entrar al entorno (cada vez)

Una vez creado, en cada sesión nueva de terminal alcanza con activarlo:

```bash
source .venv/bin/activate
```

Se sabe que está activo porque el prompt pasa a mostrar `(.venv)` adelante. Para
salir, `deactivate`.

### Ejecutar el notebook

Con el entorno activo:

```bash
jupyter notebook TP-regresion-AA1.ipynb
```

El notebook lee el dataset desde la misma carpeta y se ejecuta de principio a fin
en orden, sin pasos manuales intermedios.

> Si lo abrís desde VS Code en lugar de Jupyter, elegí `.venv` como kernel
> (**Select Kernel** arriba a la derecha). Si no, corre con el Python del sistema,
> que no tiene las bibliotecas instaladas.

### Actualizar las dependencias

`requirements.txt` lista sólo las bibliotecas que usamos directamente, no sus
dependencias internas. Si se suma una nueva, se la agrega a mano al archivo con
la versión que quedó instalada:

```bash
pip show <biblioteca> | grep -i version
```
