# 📊 Actividad 2: Carga de datos en Python  
## Aprendizaje de máquina

**Integrantes:**
* González Pérez Monserrat  
* Escamilla Lazcano Saúl  
* Pérez Méndez Nancy Esmeralda  
* Valencia Hernandez Kevin Guadalupe  
* Zamudio López Leonardo  

**Grupo:** 5BV1  
**Profesora:** Dra. Camacho Vázquez Vanessa Alejandra  
**Fecha:** 03/09/25  

[![Python](https://img.shields.io/badge/Python-3.10-blue.svg)](https://www.python.org/)
[![ML](https://img.shields.io/badge/Aplicación-Machine%20Learning-green.svg)]()

---

## 🚀 Descripción General del Proyecto

Este repositorio contiene el código base para la **carga, exploración y preprocesamiento inicial de datos** que serán utilizados en tareas de **Aprendizaje de Máquina**.

El enfoque principal es implementar, desde cero y sin librerías externas de ML, funciones que:

1. Lean archivos de datos con diferentes delimitadores (`,`, `;`, etc.).  
2. Representen los datos en una **matriz (lista de listas)** en Python.  
3. Permitan identificar el **número de patrones (instancias)** y **atributos (features)**.  
4. Faciliten la selección y el análisis de la **columna clase (etiqueta)**.  
5. Realicen una **clasificación simple** de calidad de vino a partir de sus atributos fisicoquímicos.

---

## 📂 1. Estructura del Repositorio

**Archivos principales:**

- `CargaDatos.py`  
  Script genérico para cargar matrices de datos desde archivos de texto, contar patrones/atributos y trabajar con la columna clase.  
- `Wine_Quality.py`  
  Ejemplo específico de análisis de la **calidad del vino tinto** usando el conjunto de datos `winequality-red.csv`.  
- `iris.data` / `bezdekIris.data`  
  Conjunto de datos clásico de **flores Iris**, utilizado como ejemplo de datos para clasificación.  
- `winequality-red.csv`  
  Conjunto de datos de vino tinto (Vinho Verde) con atributos fisicoquímicos y una etiqueta de **calidad** numérica (0–10).  

---

## 🧱 2. Carga Genérica de Datos (`CargaDatos.py`)

El núcleo del proyecto es la función `cargarDatos`, que permite leer archivos de texto y convertirlos en una matriz de Python.

### 2.1. Funcionalidad principal

- **Entrada desde teclado:**
  - Nombre del archivo (ruta relativa o absoluta).
  - Delimitador utilizado en el archivo (`,` para CSV, `;` para algunos datasets, etc.).
- **Procesamiento:**
  - Lectura línea por línea.
  - Eliminación de espacios en blanco (`strip`).
  - Separación de atributos con `split(delimitador)`.
  - Acumulación de los registros en una **lista de listas** (`matriz`).
- **Salida:**
  - Matriz con todos los patrones, o `0` si el archivo no se encuentra.

### 2.2. Cálculo de patrones y atributos

Con la matriz cargada, el programa:

- Calcula el **número de patrones** (`len(matriz)`).
- Calcula el **número de atributos** (`len(matriz[0])`).
- Muestra ambos valores por pantalla para tener una primera idea de la dimensionalidad del problema.

---

## 🎯 3. Columna Clase y Exploración de Etiquetas

Para tareas de Aprendizaje de Máquina es fundamental identificar la **columna clase** (etiqueta):

1. El programa solicita al usuario el índice de la columna que será considerada como **clase**.  
2. La función `imprimirColumnaClase(matriz, columna_clase)`:
   - Recorre toda la matriz.
   - Imprime el valor de la columna clase para cada patrón.
3. Esto permite:
   - Ver la **distribución de clases**.
   - Detectar posibles valores atípicos o errores de formato.
   - Confirmar si la etiqueta es numérica, categórica o mixta.

---

## 🍷 4. Clasificación de Vino por Calidad

El proyecto incluye un ejemplo específico de clasificación simple para el conjunto de datos de **vino tinto**:

### 4.1. Script `Wine_Quality.py`

- Lee el archivo `winequality-red.csv`.
- Usa una lista de nombres de **atributos fisicoquímicos**:
  - Acidez fija, acidez volátil, ácido cítrico, azúcar residual, cloruros, dióxido de azufre libre, dióxido de azufre total, densidad, pH, sulfatos, alcohol.
- Extrae la columna **quality** (calidad) y la convierte a `int`.
- Imprime para cada vino:
  - Sus atributos.
  - Su nivel de calidad.

### 4.2. Clasificación cualitativa

Se agrupan las calidades en tres niveles:

- `calidad ≤ 5`  → **Vino de baja calidad**  
- `calidad = 6`  → **Vino de calidad media**  
- `calidad ≥ 7`  → **Vino de alta calidad**

La función `clasificarVinoPorCalidad(matriz, columna_clase)` (en `CargaDatos.py`) reproduce esta lógica siempre que el nombre del archivo contenga la palabra `"wine"`.

---

## 🌸 5. Conjuntos de Datos Incluidos

### 5.1. Iris (`iris.data`, `bezdekIris.data`)

- 150 instancias (50 por clase).
- 4 atributos numéricos:
  - Largo y ancho de sépalo.
  - Largo y ancho de pétalo.
- 1 columna clase:
  - `Iris-setosa`
  - `Iris-versicolor`
  - `Iris-virginica`

Este dataset es ideal para practicar:

- Carga de datos delimitados por comas.
- Análisis de la columna clase.
- Futuras tareas de clasificación supervisada.

### 5.2. Vino Tinto (`winequality-red.csv`)

- Atributos fisicoquímicos (tipo `float`).
- Etiqueta de calidad (entera de 0 a 10).
- Clases desbalanceadas (más vinos de calidad media que extrema).

Sirve como base para:

- Problemas de **regresión** (predecir calidad numérica).
- Problemas de **clasificación** (baja, media, alta calidad).
- Análisis de desbalance de clases.

---

## ⚙️ 6. Ejecución de los Scripts

### 6.1. Ejecutar el cargador genérico

Desde la terminal, en la carpeta del proyecto:


El script recorrerá el CSV y mostrará, para cada patrón, los atributos y la calidad del vino.

---

## 🔭 7. Posibles Extensiones

A partir de esta base, se pueden desarrollar las siguientes actividades:

1. **Normalización y estandarización** de atributos numéricos.  
2. **Manejo de valores faltantes** o ruidosos.  
3. **Selección de características** para reducir dimensionalidad.  
4. Implementación de algoritmos de:
   - Clasificación (k-NN, regresión logística, árboles, etc.).
   - Regresión (regresión lineal, SVR, etc.).  
5. Generar reportes de:
   - Distribución de clases.
   - Estadísticos descriptivos (media, varianza, mínimos, máximos).  

Estas extensiones permitirán transformar este proyecto de **carga y exploración de datos** en una base sólida para prácticas más avanzadas de **Aprendizaje de Máquina**.