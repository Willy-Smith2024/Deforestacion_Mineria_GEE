# Deforestación por Minería Aurífera – Google Earth Engine

Clasificación automática de cuerpos de agua (pozas mineras), suelo desnudo y vegetación generados por la minería aurífera en Madre de Dios, Perú, usando imágenes **Landsat 8/9 (Collection 2, Level 2)** y **Machine Learning (SVM)** en Google Earth Engine.

## Zonas de estudio
- Huepetuhe
- Delta
- La Pampa
- Corredor minero

## Flujo de trabajo
1. Carga del área de estudio (`StudyArea_2024`) y sectorización por zona.
2. Filtrado de colecciones Landsat 8 y 9 por fecha, ROI y nubosidad.
3. Escalado a reflectancia de superficie (`× 0.0000275 − 0.2`) y mosaico del corredor.
4. Reproyección a **EPSG:32719** (UTM 19S) a 30 m.
5. Clasificación supervisada con `ee.Classifier.libsvm()` (clases: 1 = agua, 2 = suelo, 3 = vegetación).
6. Exportación de clasificaciones e imágenes a Google Drive (GeoTIFF).

## Uso
1. Abre el [Code Editor de GEE](https://code.earthengine.google.com/).
2. Copia `Clasificacion_Mineria_Landsat_SVM.js`.
3. Reemplaza el asset del área de estudio por el tuyo.
4. Dibuja/importa las muestras de entrenamiento (`rios_*`, `suelo_*`, `vegetacion_*`) con la propiedad `land_class`.
5. Descomenta las secciones de clasificación y exportación.

## Autor
**Willy Smith Gonzaga Huayama** – Especialista SIG y Teledetección · Sky Map Tech · Puerto Maldonado, Madre de Dios, Perú
