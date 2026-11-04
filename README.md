# Predicción de enfermedad cardiovascular con Python, visualización y redes neuronales

Proyecto final de la asignatura de Análisis de Datos — **Andres Hinojosa**, UNICIENCIA (Bucaramanga, Colombia).

> **Versión 1.0** — Bloques 1 a 3 (planteamiento, limpieza e ingeniería de características, análisis exploratorio). El modelado (regresión logística, árbol de decisión, Random Forest y red neuronal) se incluirá en la siguiente versión.

## Problema

Las enfermedades cardiovasculares (ECV) son la principal causa de muerte en el mundo y muchas personas no saben que están en riesgo hasta que tienen un evento. El objetivo es predecir si un paciente tiene o no ECV (`cardio`) a partir de datos de un examen médico básico: edad, sexo, estatura, peso, presión arterial, colesterol, glucosa y hábitos.

Los usuarios de la predicción serían médicos de atención primaria y programas de prevención de una EPS o IPS, para priorizar qué pacientes enviar a exámenes más completos.

## Dataset

- **Nombre:** Cardiovascular Disease dataset
- **Autor:** Svetlana Ulianova (Kaggle, 2019)
- **Enlace:** https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset
- **Tamaño:** 70.000 registros, 11 variables predictoras y la variable objetivo `cardio`
- **Archivo:** `cardio_train.csv` (separado por punto y coma `;`)

El CSV **no se incluye en el repositorio**; se descarga desde Kaggle (ver `data/README.md`).

## Contenido de la versión 1.0

**Bloque 1. Planteamiento, carga e inspección**
Carga del archivo, estructura, tipos de datos, nulos, duplicados, diccionario de datos y función `informe_calidad()` reutilizable para cualquier DataFrame.

**Bloque 2. Limpieza, transformación e ingeniería de características**
Eliminación de 24 duplicados, edad de días a años, codificación de sexo y de variables ordinales, reglas clínicas para marcar como faltantes los valores imposibles (presiones negativas o de 16.020 mm Hg, estaturas de 55 cm), comparación media vs mediana, revisión de atípicos con IQR, dos variables nuevas (`imc` y `presion_pulso`) y un `Pipeline` de imputación y escalado para evitar fuga de datos.

**Bloque 3. Análisis exploratorio y visualización**
Distribución de la variable objetivo, histogramas, diagramas de caja por diagnóstico, mapa de calor de correlaciones, dispersión edad vs presión sistólica, porcentaje de ECV por colesterol, glucosa y grupo de edad.

## Hallazgos principales

- La variable objetivo está balanceada (≈50% con ECV y 50% sin ECV).
- La presión sistólica es la variable más relacionada con ECV (correlación 0,43), seguida de la diastólica, la presión de pulso, la edad y el colesterol.
- El porcentaje con ECV sube con el colesterol (44% → 76,5%) y con la edad (23,8% entre 30–40 años → 67,4% entre 60–65 años).

## Estructura del repositorio

```
.
├── Hinojosa_Andres_proyecto_V_1.ipynb   # Notebook principal
├── data/
│   └── README.md                        # Instrucciones para descargar el dataset
├── requirements.txt                     # Librerías necesarias
├── CHANGELOG.md                         # Historial de versiones
├── .gitignore
└── README.md
```

## Cómo ejecutarlo

### Opción 1: Google Colab (recomendada)

1. Abrir el notebook en Colab (desde GitHub: *File → Open notebook → GitHub* y pegar la URL del repositorio).
2. Descargar `cardio_train.csv` desde Kaggle.
3. Ejecutar las celdas en orden. En la celda 1.D aparece un botón para subir el CSV.

### Opción 2: local

```bash
git clone <URL-del-repositorio>
cd <nombre-del-repositorio>
pip install -r requirements.txt
jupyter notebook
```

En local `google.colab` no existe, así que la celda 1.D se reemplaza por:

```python
df = pd.read_csv("data/cardio_train.csv", sep=";")
```

## Tecnologías

Python 3.12 · NumPy · Pandas · Matplotlib · Seaborn · SciPy · scikit-learn · TensorFlow/Keras

## Autor

**Andres Hinojosa** — Estudiante de Ingeniería Biomédica y de Sistemas, UNICIENCIA.
