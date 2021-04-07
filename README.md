# quechua-nlp

Obtaining quality (Standard Southern) Quechua data for NLP applications

- ¿Cuánta data en Quechua hay en la Web? ¿La podemos obtener?
- ¿La podemos limpiar o filtrarla de acuerdo a su calidad?
- ¿Será de utilidad para mejorar un modelo de traducción automática?

## Calidad de datos existentes

### Auditoría de calidad datos (data quality auditing)
Revisar los corpus paralelos que se han publicado hasta ahora para Quechua (Bible, Jehovaa Witnesess), y analizar su calidad como en este paper: https://arxiv.org/abs/2103.12028

### Sentence Aligner
Implementar un sentence aligner que mejore el alineamiento de los corpus paralelos de Quechua (Bible, JW300), ya que el scrapping ha sido deficiente y no hay buena relacion source-target. Si no es relevante... el alineamiento puede rehacerse de forma manual.

## Nuevos datos monolingües

### Crawling Internet archive
Crawlear el Internet archive usando el LangIdentification (se debe re-entrenar?) de Quechua, e identificar potenciales websites con textos monolingues en Quechua

### Wikipedia dump
Obtener el dump de Wikipedia en Quechua y limpiarlo: p.e. descartar las páginas que sólo son "números"

### PDF extraction
Extraer textos de los libros de PDF del repositorio de PeruEduca y otros

## Lexicons

## MT: downstream task
Usar toda la nueva data en un downstream/probing task de MT: la data obtenida es lo suficientemente limpia como para mejorar un modelo de traduccion con respecto a una línea base?
