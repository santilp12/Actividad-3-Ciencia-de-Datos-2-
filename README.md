# Actividad-3-Ciencia-de-Datos-2-
# TP3 – Aprendizaje No Supervisado: PCA, selección de variables y K-means

## Dataset
**Wine Recognition** (UCI Machine Learning Repository, disponible también en Kaggle; se carga con `sklearn.datasets.load_wine`). 178 vinos italianos de 3 cultivares con análisis químicos. Se usaron **9 variables numéricas**: `alcohol`, `malic_acid`, `alcalinity_of_ash`, `magnesium`, `total_phenols`, `flavanoids`, `color_intensity`, `hue`, `proline`. Sin valores faltantes ni categóricas. Las etiquetas de cultivar no se usan para entrenar, solo como validación externa (ARI).

## Objetivo
Comparar tres versiones de los datos para agrupar con K-means (K = 2 a 6): (1) variables originales estandarizadas, (2) dos componentes principales, (3) variables seleccionadas por correlación.

## Contenido
- `TP3_aprendizaje_no_supervisado.ipynb`: análisis completo con gráficos y comentarios.
- `requirements.txt`

## Principales hallazgos
- PC1 + PC2 explican **62,4 %** de la varianza; se necesitan 4 componentes para superar 80 %.
- Selección por correlación (|r| > 0,70): solo se elimina `flavanoids` (r = 0,86 con `total_phenols`), quedan 8 variables.
- **K = 3** es la mejor opción en los tres enfoques (o casi): codo claro con PCA y coincidencia con los 3 cultivares reales.

| Enfoque (K=3) | Silhouette | ARI vs cultivar |
|---|---|---|
| Original (9 vars) | 0,325 | 0,866 |
| PCA (2 comp.) | 0,567 | 0,801 |
| Selección (8 vars) | 0,314 | 0,802 |

## Conclusiones
PCA con K=3 es el más apropiado para explorar e interpretar (codo nítido, mayor silhouette, visualizable), aunque el silhouette no es estrictamente comparable entre espacios de distinta dimensión. Las variables originales dan el agrupamiento más fiel (mejor ARI) y la selección por correlación logra casi lo mismo con una variable menos.

## Cómo ejecutar
```bash
pip install -r requirements.txt
jupyter notebook TP3_aprendizaje_no_supervisado.ipynb
```
