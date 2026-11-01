# Microproyecto 2 — Clasificación de sentimientos usando RNNs

Materiales de partida para clasificar reseñas de películas de IMDb como positivas o negativas. Esta carpeta contiene el enunciado, los datos originales comprimidos y documentos de apoyo; todavía no incluye una solución ni resultados del modelo.

## Contenido

| Ruta | Descripción |
|---|---|
| `main.ipynb` | Plantilla original del notebook del microproyecto 2, sin resolver. |
| `enunciado/microproyecto_RNN.pdf` | Enunciado original del microproyecto 2. |
| `enunciado/plantilla_informe.docx` | Plantilla de Word suministrada por el curso. |
| `enunciado/rubrica_miniproyectos.pdf` | Rúbrica general ya disponible en el repositorio. |
| `datos/movie.csv.zip` | Copia comprimida, sin modificaciones, del CSV proporcionado. |
| `datos/README.md` | Fuente, extracción y características del dataset. |
| `datos/metadatos.json` | Conteos y SHA-256 del CSV original. |

## Plantilla del notebook

`main.ipynb` es la plantilla original suministrada por el curso. Contiene una celda de instrucciones y una celda de código de marcador de posición; no incluye una implementación base. Se conserva sin modificaciones para que el equipo pueda desarrollar la solución.

La plantilla recuerda que el notebook con el código debe adjuntarse a la entrega; omitirlo implica cero en la sección de calificación del código. Se pueden agregar las celdas necesarias.

## Actividades del enunciado

1. Construir un pipeline para limpiar y tokenizar las reseñas y convertirlas en secuencias numéricas utilizando embeddings. Word2Vec y GloVe son ejemplos mencionados en el enunciado.
2. Implementar una red recurrente para clasificación binaria, por ejemplo una LSTM o GRU. Se sugieren capas de embedding, capas recurrentes y una capa densa de salida con activación sigmoide. Justificar la elección de cada capa.
3. Dividir los datos en entrenamiento, validación y prueba, entrenar el modelo y reportar precision, recall y F1-score en prueba.

La arquitectura es de libre elección. El PDF original es la referencia para los requisitos específicos.

## Entrega según las instrucciones generales del curso

- Trabajo en parejas.
- Informe en PDF de máximo dos páginas, sin contar referencias, siguiendo la plantilla del curso en formato IEEE basado en CVPR.
- Jupyter Notebook con la implementación.
- PyTorch o TensorFlow; el equipo docente recomienda PyTorch.
- Revisar todos los criterios y penalizaciones de la rúbrica.

**Fecha por confirmar:** el texto de la plataforma compartido indica “05 de mayo a las 23:59 UTC-5”, sin año. No se asume que esa fecha corresponda al periodo 2026-2; verificarla en el calendario vigente del curso.

## Obtener los datos

Desde la raíz del repositorio, en PowerShell:

```powershell
Expand-Archive -LiteralPath ".\microproyecto2\datos\movie.csv.zip" -DestinationPath ".\microproyecto2\datos"
```

El archivo extraído será `microproyecto2/datos/movie.csv`. La copia extraída se excluye de Git mediante `.gitignore`; el ZIP conserva el archivo original para compartirlo sin versionar dos copias.

## Aspectos para el desarrollo posterior

Estas son recomendaciones metodológicas, no requisitos adicionales del enunciado:

- Tratar las reseñas idénticas antes de dividir los datos para evitar que una misma reseña aparezca en distintos conjuntos. El CSV original conserva esas repeticiones.
- Conservar una proporción comparable de etiquetas en entrenamiento, validación y prueba, y fijar una semilla.
- Construir el vocabulario y ajustar las transformaciones que aprenden de los datos usando únicamente entrenamiento.
- Usar validación para elegir hiperparámetros y reservar prueba para la evaluación final.
- Confirmar el significado de las etiquetas 0 y 1 antes de interpretar las predicciones.
