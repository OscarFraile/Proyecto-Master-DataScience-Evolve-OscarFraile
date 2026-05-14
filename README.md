# Análisis del Mercado de Alquiler Turístico en Madrid — Predicción de Rentabilidad con XGBoost

Modelo de clasificación binaria para predecir si un alojamiento de Airbnb en Madrid tiene alta o baja rentabilidad, a partir de datos de Inside Airbnb 2025. Incluye mapa interactivo con recomendaciones de inversión por barrios.

## Tecnologías

Python · Pandas · Scikit-learn · XGBoost · Folium · Matplotlib · Jupyter Notebook

## Estructura del repositorio

```
├── 01_Documentos/
│   ├── 007_airbnb.yml                                      # Configuración del entorno
│   ├── FaseDesarrollo_Produccion_Plantilla_Transformaciones_Procesos.xlsx
│   └── stop_words_spanish.txt
│
├── 02_Datos/
│   ├── 01_Originales/
│   │   ├── Airbnb_5k34/
│   │   ├── listings.csv.gz                                 # Dataset Inside Airbnb
│   │   └── neighbourhoods.geojson                         # Geometría de barrios
│   └── 03_Trabajo/
│       ├── cat_resultado_calidad.pickle
│       ├── cat_resultado_eda.pickle
│       ├── df_tablon.pickle
│       ├── mapa_resultado.pickle
│       ├── muestras.csv
│       ├── num_resultado_calidad.pickle
│       ├── num_resultado_eda.pickle
│       ├── x_preseleccionado.pickle
│       └── y_preseleccionado.pickle
│
├── 03_Notebooks/
│   └── 02_Desarrollo/
│       ├── df_descartados/                                 # Notebooks de versiones previas descartadas
│       │   ├── 10_Transformacion_de_datos_DF1.ipynb
│       │   ├── 10_Transformacion_de_datos_DF2.ipynb
│       │   ├── 10_Transformacion_de_datos_DF3.ipynb
│       │   ├── 11_Preseleccion_de_variables_DF1.ipynb
│       │   ├── 11_Preseleccion_de_variables_DF2.ipynb
│       │   ├── 11_Preseleccion_de_variables_DF3.ipynb
│       │   ├── 13_Modelizacion_para_Clasificacion_DF1.ipynb
│       │   ├── 13_Modelizacion_para_Clasificacion_DF2.ipynb
│       │   └── 13_Modelizacion_para_Clasificacion_DF3.ipynb
│       ├── 01_Diseño_del_proyecto.ipynb
│       ├── 02_Analisis_de_ficheros_y_preparacion_del_caso.ipynb
│       ├── 03_Creacion_del_datamart_analitico.ipynb
│       ├── 04_Preparacion_de_datos.ipynb
│       ├── 05_Analisis_e_insights.ipynb
│       ├── 06_Comunicacion_de_resultados.ipynb
│       ├── 07_Set_Up_Automation.ipynb
│       ├── 08_Calidad_de_Datos_Automation.ipynb
│       ├── 09_Exploratory_Data_Analysis_EDA.ipynb
│       ├── 10_Transformacion_de_datos_DF4.ipynb
│       ├── 11_Preseleccion_de_variables_DF4.ipynb
│       ├── 12_Balanceo.ipynb
│       ├── 13_Modelizacion_para_Clasificacion_DF4.ipynb
│       ├── 14_Preparacion_del_codigo_de_produccion.ipynb
│       ├── 15_Codigo_de_reentrenamiento_CON_PIPELINES.ipynb
│       ├── 15_Codigo_de_reentrenamiento_SIN_PIPELINES.ipynb
│       ├── 16_Codigo_de_ejecucion.ipynb
│       └── 17_Aplicacion_Marzo2025.ipynb
│
├── 04_Modelos/
│   ├── count_vectorizer.pickle
│   ├── pipe_ejecucion.pickle
│   ├── pipe_gestion_variables.pickle
│   ├── pipe_clasificacion.pickle
│   ├── pipe_entrenamiento.pickle
│   └── pipe_preparacion.pickle
│
├── 05_Resultados/
│   ├── variables_finales.pickle
│   └── mapa.html                                          # Mapa interactivo de resultados
│
├── requirements.txt
├── .gitignore
└── README.md
```

## El problema

A partir de datos públicos de Inside Airbnb, predecir qué alojamientos tienen alta rentabilidad antes de invertir en ellos. El modelo genera una clasificación binaria (alta/baja rentabilidad) y visualiza los resultados en un mapa interactivo por barrios de Madrid.

## Dataset

[Inside Airbnb](https://insideairbnb.com/get-the-data/) — más de 30.000 registros de alojamientos en Madrid con información de precio, ubicación, tipo de propiedad, disponibilidad y reseñas.

## Pipeline

El proyecto sigue un pipeline end-to-end estructurado en notebooks numerados:

1. Diseño del problema y definición del target
2. Análisis de ficheros y preparación del caso
3. Creación del datamart analítico
4. Preparación y limpieza de datos
5. Análisis exploratorio (EDA) e insights
6. Comunicación de resultados intermedios
7. Automatización del set up
8. Calidad de datos automatizada
9. EDA completo
10. Transformación de variables (versión final DF4)
11. Preselección de features (versión final DF4)
12. Balanceo del dataset
13. Modelización para clasificación (versión final DF4)
14. Preparación del código de producción
15. Código de reentrenamiento (con y sin pipelines)
16. Código de ejecución
17. Aplicación final

La carpeta `df_descartados/` contiene versiones anteriores de transformación, preselección y modelización (DF1, DF2, DF3) que fueron exploradas y descartadas durante el desarrollo.

## Resultados

- **Modelo final:** XGBoost Classifier con búsqueda de hiperparámetros
- **AUC-ROC sobre validación: 0.997**
- El modelo se ejecuta sobre datasets no vistos durante el entrenamiento
- Los resultados se visualizan en `05_Resultados/mapa.html` — mapa interactivo con alojamientos coloreados por potencial de rentabilidad y segmentados por barrio

## Cómo ejecutarlo

```bash
pip install -r requirements.txt

# Ejecutar notebooks en orden numérico desde 03_Notebooks/02_Desarrollo/
# Empezar por: 01_Diseño_del_proyecto.ipynb

# Para ver el mapa de resultados abrir directamente:
# 05_Resultados/mapa.html
```

---

Proyecto académico desarrollado durante el Master en Data Science de Evolve.
