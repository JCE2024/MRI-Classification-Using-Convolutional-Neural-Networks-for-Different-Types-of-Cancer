# Entrega 1 — Clasificación de imágenes MRI con CNNs

Miniproyecto 1 del curso Técnicas de Deep Learning (MAIA). Clasifica cortes 2D de resonancia magnética cerebral en cuatro clases (glioma, meningioma, tumor pituitario y tejido sano) y compara una CNN propia entrenada desde cero con una ResNet18 preentrenada en ImageNet y ajustada por fine-tuning.

## Contenido

| Archivo | Descripción |
|---|---|
| `microproyecto1_CNN_MRI.ipynb` | Notebook con todo el código y las salidas: carga de datos, modelos, entrenamiento, métricas y figuras |
| `imagenes/` | Dataset (7023 imágenes JPEG, una carpeta por clase) |
| `figuras/` | Figuras generadas por el notebook y usadas en el informe |
| `resultados/resultados.json` | Métricas, curvas y predicciones de cada entrenamiento (modelo × semilla) |
| `informe_microproyecto1.docx` | Informe en el formato de la plantilla del curso |
| `microproyecto_CNN.pdf`, `202611_Rubrica_MNP_MAIA_4213.pdf`, `word_template.docx` | Enunciado, rúbrica y plantilla |

## Cómo ejecutar

Requisitos: Python 3.10 o superior con `torch`, `torchvision`, `scikit-learn`, `matplotlib`, `pillow` y `numpy`.

```bash
pip install torch torchvision scikit-learn matplotlib pillow numpy
```

Abrir `microproyecto1/microproyecto1_CNN_MRI.ipynb` y ejecutar las celdas. El notebook admite como directorio de trabajo tanto la raíz del repositorio como `microproyecto1/`; busca las imágenes y guarda figuras y resultados dentro de esta entrega. En CPU (Ryzen 7 5700) la ejecución completa, con 2 modelos × 3 semillas, toma alrededor de hora y media; con GPU es mucho más rápida. La primera vez descarga los pesos de ResNet18 (unos 45 MB).

## Decisiones principales

- Se eliminan 426 archivos duplicados exactos (hash MD5) antes de dividir los datos. Sin este paso, el 7,1 % de las imágenes de prueba tendría una copia idéntica en entrenamiento.
- División estratificada 70/15/15 (entrenamiento/validación/prueba) con semilla fija. La validación se usa para escoger la mejor época; la prueba solo para reportar.
- Imágenes en escala de grises a 128×128, normalizadas a [0, 1], con volteo horizontal aleatorio como aumento de datos.
- Cada modelo se entrena con 3 semillas y se reporta promedio ± desviación estándar.
