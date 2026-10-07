# RappiPlus: calidad y limpieza de datos con Python

> Paso 1 de un proyecto de análisis de negocio: decidir si los datos son confiables antes de calcular cualquier métrica.

## Contexto o problema
El proyecto evalúa el desempeño del servicio RappiPlus para apoyar decisiones de negocio. Antes de analizar rentabilidad, conversión o retención, había que responder una pregunta previa: **¿podemos confiar en los datos?** Este notebook cubre esa primera etapa con tres fuentes:

| Archivo | Contenido | Tamaño inicial |
|---|---|---|
| `rappiplus_orders_raw.csv` | Pedidos, precios, descuentos y montos | 25,100 filas |
| `rappiplus_catalog.csv` | Catálogo de productos, costos y proveedores | 7 filas |
| `rappiplus_marketing_spend.csv` | Gasto de marketing por fecha, país y canal | 1,620 filas |

## Mi contribución
Trabajo individual: carga, diagnóstico, limpieza, validación y documentación de cada decisión en el notebook `rappiplus_cleaning.ipynb`.

## Proceso y decisiones
Primero cuantifiqué los problemas y después limpié, para decidir con evidencia. Las decisiones principales:

| Problema | Decisión | Por qué |
|---|---|---|
| 100 pedidos duplicados exactos | Eliminar la copia | Son idénticos; no hay ambigüedad |
| `pais` con mayúsculas mezcladas (6 variantes → 3 países) | Normalizar el texto | Evita contar el mismo país como dos |
| "Electronica" sin tilde vs. "Electrónica" en el catálogo | Alinear con el catálogo | El catálogo es la fuente de verdad |
| 80 categorías vacías | Recuperar 50 desde el nombre del producto; 30 quedan "Desconocido" | Relación 1:1 real, no una suposición |
| 50 filas sin cantidad, precio ni descuento | Dejar vacías y marcarlas con una bandera | No hay base para inventar montos |
| 4 cantidades negativas y 10 cantidades de 10,000–20,000 | Conservar la fila y marcarla como no válida | No se puede adivinar el valor correcto; se excluye de los KPIs |
| 101 canales vacíos en marketing | Recuperarlos desde `id_campaña` (patrón `canal_pais`) | El dato ya existía en otra columna |

Un criterio que apliqué: **no imputar valores numéricos inventados**. En su lugar creé la bandera `incluir_en_kpis_financieros` para que los pasos siguientes sepan qué filas son confiables.

## Resultado o aprendizaje
- `orders_clean`: 25,000 pedidos únicos (20 columnas), sin nulos en las columnas de identidad y categóricas.
- `catalog_clean` (7 filas) y `marketing_clean` (1,620 filas) listos para el siguiente paso.
- Aprendí que los errores de formato (mayúsculas, tildes) no dan error, pero generan cifras de negocio incorrectas, y que conviene marcar un dato dudoso en lugar de corregirlo a ciegas.

## Evidencias
- Notebook: [`rappiplus_cleaning.ipynb`](rappiplus_cleaning.ipynb)

## Herramientas
Python, pandas y numpy: diagnóstico de nulos y duplicados, normalización de texto, validación de montos (`cantidad × precio − descuento`) y conversión de fechas.

## Cómo reproducirlo
1. Pon los tres CSV originales junto al notebook.
2. Instala las dependencias: `pip install pandas numpy jupyter`
3. Ejecuta `rappiplus_cleaning.ipynb`; genera los tres archivos `*_clean.csv`.
