# RappiPlus: dashboard ejecutivo en Power BI

> Paso final del proyecto: comunicar los resultados de rentabilidad a quien toma decisiones.

## Resumen
**RappiPlus: dashboard ejecutivo | Power BI.** Construí un reporte de dos páginas que muestra ingresos, utilidad, gasto de marketing y ticket promedio, con su evolución mensual y el detalle por producto. Encontré que algunos productos de alto volumen dejan poca utilidad y que un producto se vende a pérdida, lo que permite priorizar ajustes de precio y de inversión en marketing.

## Contexto o problema
Con los datos ya limpios (ver [limpieza de datos](../rappiplus-limpieza-datos/)), el dashboard responde: **¿es rentable el negocio, qué productos aportan más y cómo evolucionan ingresos y utilidad en el tiempo?**

## Mi contribución
Trabajo individual: modelo de datos, medidas y diseño de las dos páginas del reporte (`Proyecto_Final.pbix`).

## Qué contiene
**Página 1: Overview Ejecutivo**
- Tarjetas con los KPIs: Revenue Total, Profit Neto, Gasto Marketing Total, Ticket Promedio y Cantidad Promedio por Orden.
- Evolución mensual de Revenue y Profit Neto, y Revenue acumulado en el año (YTD).
- Revenue y Profit Bruto por producto, y unidades vendidas por producto.
- Filtros por país y por año.

**Página 2: Detalle de Producto**
- Tabla con cantidad, monto total, costo total y profit por fila.
- Filtros por categoría, país, dispositivo y mes.
- Botón para volver al Overview.

## Modelo de datos
Tablas: `rappiplus_orders_clean`, `rappiplus_catalog_clean`, `rappiplus_marketing_clean` y una tabla de fechas `dim_fecha` (año y año-mes).

## Proceso y decisiones
- Definí el Profit Bruto por producto y el Profit Neto como el Profit Bruto menos el gasto de marketing.
- Excluí del análisis financiero las filas marcadas como no confiables en la etapa de limpieza.
- Organicé el reporte en una vista ejecutiva (indicadores, evolución mensual y comparación por producto) y una vista de detalle con filtros por categoría, país, dispositivo y mes.

## Resultado o aprendizaje
Entre enero y junio de 2025 el negocio generó un Revenue Total de 9.64 millones, un Profit Neto de 2.94 millones (cerca del 30% del revenue) y un gasto de marketing de 2.87 millones, equivalente a otro 30% de los ingresos. El revenue mensual se mantiene alrededor de 1.6 millones, con una caída en febrero, y el Profit Neto ronda los 0.5 millones por mes.

Hallazgos principales:
- Vender más unidades no significa ganar más. Vacuum-Pro-Black, Blender-XL-Red, Jacket-Winter-M y Sneakers-Urban-42 venden cantidades similares (cerca de 6,300 unidades cada uno), pero su profit bruto es muy distinto: Vacuum-Pro-Black y Sneakers-Urban-42 conservan cerca del 94% de su revenue como profit bruto, mientras Blender-XL-Red y Jacket-Winter-M conservan entre un cuarto y un tercio.
- Laptop-Gaming-16GB genera cerca de 1.1 millones de revenue, pero su profit bruto es negativo: se vende por debajo de su costo.
- Tablet-Standard-64GB y Phone-Pro-128GB tienen buen margen con menos unidades vendidas (cerca de 4,200 cada uno).
- Algunos registros aparecen como "Desconocido" en producto y país; vienen de datos que no se pudieron recuperar en la etapa de limpieza.

## Implicación de negocio
Con este análisis se podría: (1) revisar el precio y el costo de Laptop-Gaming-16GB, que hoy pierde dinero; (2) evaluar el margen de Blender-XL-Red y Jacket-Winter-M, que venden mucho pero dejan poca utilidad; y (3) priorizar el gasto de marketing en los productos de mayor margen, como Vacuum-Pro-Black y Sneakers-Urban-42, dado que el marketing consume cerca del 30% del revenue.

## Evidencias
- Archivo: [`Proyecto_Final.pbix`](Proyecto_Final.pbix)
- Capturas de ambas páginas: carpeta `img/` (agrégalas con *Archivo → Exportar → PDF* o con una captura de pantalla)

## Herramientas
Power BI Desktop: modelo de datos, medidas DAX, segmentadores, gráficos y navegación entre páginas.
