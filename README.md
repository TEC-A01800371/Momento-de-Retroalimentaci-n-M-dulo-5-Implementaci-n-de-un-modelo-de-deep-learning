# Momento-de-Retroalimentaci-n-M-dulo-5-Implementaci-n-de-un-modelo-de-deep-learning.
A01800371 - Erik Castro Flores

# Clasificación de enfermedades en hojas de frijol (Deep Learning)

Proyecto del módulo "Implementación de un modelo de deep learning" (Keras + TensorFlow).

Clasifica fotografías de hojas de frijol en tres clases: `healthy`, `angular_leaf_spot` y `bean_rust`.

## Dataset
Beans (iBean), AI Lab de Makerere University (Uganda). Fotos reales tomadas en campo, 1,295 imágenes, 3 clases.
Fuente original: https://github.com/AI-Lab-Makerere/ibean
Se descarga automáticamente desde el notebook con `load_dataset("AI-Lab-Makerere/beans")` (Hugging Face),
ya separado en entrenamiento (1,034), validación (133) y prueba (128).

## Modelos comparados
| Modelo | Val acc | Test acc |
|---|---|---|
| CNN base (desde cero) | 0.759 | 0.773 |
| Iteración 1: regularización (augmentation, BatchNorm, Dropout, L2, GlobalAveragePooling) | 0.820 | 0.836 |
| Iteración 2: MobileNetV2 (transferencia de aprendizaje) | 0.880 | **0.906** |

El modelo final es la Iteración 2 (elegido con validación) y se guarda en `modelo_final.keras`.

## Contenido del repositorio
- `notebook.ipynb`: reporte completo (introducción, datos, desarrollo del modelo, ajuste, resultados, conclusiones y aplicación).
- `modelo_final.keras`: arquitectura + pesos del modelo final.
- `ejemplos/`: imágenes de prueba para la función de predicción.
- `requirements.txt`: dependencias.

## Cómo ejecutarlo
1. Abrir `notebook.ipynb` en Google Colab (con GPU) y ejecutar todas las celdas.
2. Para predecir con una imagen: `predecir("ejemplos/healthy_1.jpg")` (devuelve la clase y la probabilidad).
