# RappiPlus: dashboard ejecutivo en Power BI

> Paso final del proyecto: comunicar los resultados de rentabilidad a quien toma decisiones.

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
<!-- Completa con tus palabras, por ejemplo: -->
- Por qué elegí estas métricas como KPIs principales.
- Cómo definí Profit Bruto y Profit Neto (qué costos resta cada uno).
- Qué hice con las filas marcadas como no confiables en la limpieza.
- Por qué organicé el reporte en una vista ejecutiva y una vista de detalle.

## Resultado o aprendizaje
<!-- Escribe aquí 2–3 hallazgos reales que veas en el dashboard (producto con más profit, tendencia, etc.). No inventes cifras. -->

## Evidencias
- Archivo: [`Proyecto_Final.pbix`](Proyecto_Final.pbix)
- Capturas de ambas páginas: carpeta `img/` (agrégalas con *Archivo → Exportar → PDF* o con una captura de pantalla)

## Herramientas
Power BI Desktop: modelo de datos, medidas DAX, segmentadores, gráficos y navegación entre páginas.
