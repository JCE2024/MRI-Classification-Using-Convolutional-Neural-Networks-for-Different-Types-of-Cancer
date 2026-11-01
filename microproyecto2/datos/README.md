# Datos de reseñas de películas

El enunciado enlaza a [IMDB Movie Ratings Sentiment Analysis en Kaggle](https://www.kaggle.com/datasets/yasserh/imdb-movie-ratings-sentiment-analysis/data). El ZIP de esta carpeta contiene el `movie.csv` proporcionado para el curso; no se ha comprobado su identidad contra una descarga nueva de Kaggle. Consultar la página de origen para sus condiciones de uso y atribución.

## Archivo incluido

| Propiedad | Valor observado |
|---|---|
| Filas de datos | 40.000 |
| Columnas | `text`, `label` |
| Etiqueta `0` | 20.019 filas |
| Etiqueta `1` | 19.981 filas |
| Tamaño del CSV | 52.724.248 bytes |
| Textos vacíos o solo espacios | 0 |
| Repeticiones exactas adicionales de texto | 277 |
| Textos idénticos con etiquetas contradictorias | 0 |

Hay 39.723 textos distintos por igualdad exacta. La comprobación no identifica necesariamente reseñas casi iguales. El significado positivo/negativo de las etiquetas debe confirmarse en la documentación de origen. Aunque el enunciado describe ratings, el archivo recibido solo contiene `text` y `label`.

Los datos están sin limpiar, sin deduplicar y sin dividir. No asumir que los archivos tienen una partición de entrenamiento/prueba predefinida.

## Extracción y comprobación

Desde la raíz del repositorio:

```powershell
Expand-Archive -LiteralPath ".\microproyecto2\datos\movie.csv.zip" -DestinationPath ".\microproyecto2\datos"
Get-FileHash -LiteralPath ".\microproyecto2\datos\movie.csv" -Algorithm SHA256
```

SHA-256 esperado:

```text
787cf9e018a7d039d77532065be28d2523412b8de0209224b1baa9ad63fe8760
```

Si el archivo ya está extraído, no es necesario ejecutar de nuevo la extracción.
