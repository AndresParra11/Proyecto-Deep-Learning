# Proyecto de Detección de Objetos con YOLO Simplificado
Video de referencia: [Explicación en YouTube](https://www.youtube.com/watch?v=o7dZM_UrRQU).


## Introducción

En este proyecto, se utilizó el conjunto de datos titulado *traffic-detection-project* disponible en Kaggle, creado por el usuario **yusufberksardoan**. Este conjunto incluye imágenes de tráfico etiquetadas en formato `.txt`, organizadas en las categorías estándar de aprendizaje automático: **entrenamiento (train)**, **validación (valid)** y **prueba (test)**. El objetivo principal fue construir y entrenar un modelo básico de detección de objetos basado en la arquitectura YOLO (*You Only Look Once*), aprovechando las herramientas de **TensorFlow** y **Keras**.

## Desarrollo del Proyecto

### Descarga y Preparación de los Datos
Se utilizó la librería **kagglehub** para descargar el conjunto de datos desde Kaggle. Posteriormente, las imágenes y sus etiquetas correspondientes fueron preprocesadas. Este paso incluyó:
- La normalización de las imágenes y su redimensionamiento a un tamaño estándar.
- La conversión de las etiquetas para que las coordenadas de las cajas delimitadoras se ajustaran a los valores normalizados requeridos por el modelo.

### Construcción del Modelo YOLO
Se desarrolló un modelo básico de YOLO utilizando **Keras**. El diseño incluyó:
1. **Capas convolucionales**: Para extraer características relevantes de las imágenes.
2. **Capas densas**: Para predecir las cajas delimitadoras y clasificar los objetos en cada celda de la cuadrícula.

El modelo realiza las siguientes predicciones por celda:
- Clase del objeto.
- Centro del objeto (coordenadas normalizadas).
- Tamaño del objeto (ancho y alto normalizados).

### Entrenamiento
El modelo fue entrenado utilizando:
- **Optimizador**: Adam.
- **Función de pérdida**: Error cuadrático medio (*Mean Squared Error*, MSE).

Se entrenó con los datos de entrenamiento y validación. Además, se aplicaron técnicas como:
- **Precisión mixta**: Para optimizar el uso de recursos de hardware.
- **Supresión de no máximos (NMS)**: Para evitar predicciones duplicadas.

## Conclusiones y Recomendaciones

### Resultados
Aunque el modelo logró reducir su pérdida durante el entrenamiento, las predicciones finales no fueron satisfactorias. Las cajas delimitadoras generadas no lograron identificar correctamente los objetos en las imágenes de prueba.

### Análisis de Desempeño
El desempeño limitado puede atribuirse a varios factores:
- **Arquitectura del modelo**: El diseño del modelo básico puede no ser lo suficientemente robusto para manejar la complejidad del conjunto de datos.
- **Función de pérdida**: El uso de MSE no captura adecuadamente las necesidades de la tarea de detección de objetos. Métricas específicas como el *mean Average Precision* (mAP) podrían ofrecer mejores resultados.
- **Calidad del conjunto de datos**: La variabilidad en las imágenes y etiquetas puede afectar el rendimiento del modelo.

### Recomendaciones para Mejoras
1. Implementar una función de pérdida específica para detección de objetos, como *YOLO Loss, mAP o una desarrollada.*.
2. Ampliar la arquitectura del modelo con técnicas más avanzadas para la extracción de características.
3. Utilizar técnicas de aumento de datos para mejorar la generalización del modelo.
4. Evaluar las predicciones con métricas más adecuadas, como el mAP, en lugar de confiar únicamente en la pérdida del modelo.
5. Evaluar si el procesado de los datos es correcto y/o la decodificación de las predicciones son correctas.

## Trabajo Futuro
Se continuará trabajando en el ajuste del modelo y en la implementación de técnicas adicionales para lograr predicciones más precisas y optimizadas.

---

**Referencias:**
- Conjunto de datos: *traffic-detection-project* de Kaggle ([Enlace al dataset](https://www.kaggle.com/yusufberksardoan/traffic-detection-project)).
- Video de referencia: [Explicación en YouTube](https://www.youtube.com/watch?v=o7dZM_UrRQU).

