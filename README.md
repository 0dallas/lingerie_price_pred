# 🔥 Predicción de Precios de Lencería con Vertex AI y Kubeflow Pipelines

Este proyecto implementa un pipeline de Machine Learning en Vertex AI utilizando Kubeflow Pipelines para entrenar y desplegar un modelo de predicción de precios de lencería. Se emplea el dataset load_lingerie de eccd_datasets, y el modelo resultante se expone a través de un endpoint en Vertex AI para realizar predicciones en tiempo real.  

<img src="https://i.ibb.co/m5LcKSpx/pipeline.png" alt="Descripción de la imagen" width="500">

## 🚀 Tecnologías utilizadas

- Google Cloud Platform (GCP)
    - Vertex AI (para entrenar y desplegar el modelo)
    - Cloud Storage (para almacenar datos y modelos)
    - Cloud Run (para exponer el endpoint públicamente)
- Kubeflow Pipelines (automatización del flujo de entrenamiento)
- Pandas y NumPy (manipulación de datos)
- Scikit-learn (entrenamiento, métricas)

##  Flujo del pipeline
- Ingesta de datos desde load_lingerie.
- Preprocesamiento: limpieza, transformación y selección de características.
- Entrenamiento del modelo con Vertex AI.
- Evaluación del desempeño del modelo.
- Despliegue del modelo en un endpoint de Vertex AI.
- Predicciones en tiempo real desde el endpoint.

## Archivos
```batch
📂 lingerie_price_pred/
│── 📂 features/                   # Carpeta de diccionario de caracteristicas
│   ├── brand_name_dict.json       # Diccionario de la columna brand_name  
│   ├── color_dict.json            # Diccionario de la columna color
│   └── product_category_dict.json # Diccionario de la columna product_category 
│── analisis_dataset.ipynb        # Notebook para el procesamiento de datos 
│── pipeline.ipynb                # Notebook de implementación de pielines con Kubeflow 
│── model_pipeline.json           # Archivo json generado de la configuración del pipeline
```


## 🌎 Hacer una predicción usando el endpoint
```python
import requests

url = "https://api-lingerieprice-93305744778.europe-west4.run.app/hello_htpp"
data = {"product_category": [2,1], "brand_name": [2,1], "color": [2,1]} # Varios datos
# data = {"product_category": 1, "brand_name": 2, "color": 3} # Un solo dato

response = requests.post(url, json=data)
print(response.text)
```
