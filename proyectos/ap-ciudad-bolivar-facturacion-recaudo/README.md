# Facturación y recaudo, Ciudad Bolívar (agosto 2026)

> Análisis que cruza la facturación del mes con los recaudos recibidos, para medir el recaudo y hacer seguimiento de cartera en el sector energético.

## ⚠️ Antes de publicar este proyecto
Los archivos originales contienen **datos personales reales** (nombres, números de identificación y direcciones) de usuarios del servicio. **No subas los Excel a GitHub.** En Colombia, la Ley 1581 de 2012 (protección de datos personales) aplica, y además son datos de tu empleador.
- Deja los archivos fuera del repositorio (el `.gitignore` de esta carpeta ya excluye `*.xlsx` y `*.csv`).
- Si quieres mostrar el trabajo, usa una versión **anonimizada**: elimina `DIRECCION`, `SUJETO_PASIVO_PDTO_DEP` e `IDENTIFICACION_SUJETO`, y reemplaza `SUSCRIPCION` y `NRO_FACTURA` por códigos.
- Pide autorización a tu empresa antes de compartir cifras reales.

## Contexto o problema
Cada mes se genera la facturación y llegan los recaudos asociados. La pregunta es **¿cuánto de lo facturado se recaudó y qué parte queda pendiente?** Este proyecto une dos reportes: el de facturación y el de recaudos de Ciudad Bolívar (departamento 5, municipio 101), servicio "Energía mercado regulado".

## Mi contribución
Es un trabajo del área comercial donde preparo y analizo estas bases (ver mi experiencia en Canales y Contactos S.A.). Aquí lo presento como un caso de análisis: unir las dos bases, validarlas y calcular indicadores de recaudo.

## Datos
| Archivo | Filas | Contenido |
|---|---|---|
| Facturación (`AP_CIUDAD_BOLIVAR…_SF.xlsx`) | 8,808 | Facturas del período 202608: valor del impuesto, intereses de mora, total facturado, categoría, consumo de energía |
| Recaudos (`AP_CIUDAD_BOLIVAR_Recaudos…_SF.xlsx`) | 8,667 | Pagos recibidos: recaudo de impuesto, intereses y total, fecha de pago, período de la factura |

Llave de unión: `NRO_FACTURA`. Las dos bases no tienen valores vacíos.

## Qué encontré al explorarlas
- **Facturación:** un solo período (agosto 2026), 8,799 facturas únicas y un total facturado de unos 190.3 millones (la moneda no está indicada; asumo pesos).
- **Recaudos:** 8,667 pagos de **varios períodos de facturación** (de enero a agosto de 2026, la mayoría de julio y agosto), con un total de unos 205.3 millones. Por eso el recaudo total no se puede comparar directamente con lo facturado en agosto.
- **Cruce:** solo cerca del 32% de los pagos corresponde a facturas de agosto; el resto son facturas de meses anteriores.
- **Posibles problemas a revisar:** 9 números de factura repetidos en facturación y 18 en recaudos (pueden ser pagos parciales o duplicados), y 4 recaudos con valor negativo (posibles reversos).
- **Cartera:** la columna `VALOR_CARTERA` está en cero en todo el archivo de facturación.

> Estas cifras son una primera exploración, no conclusiones finales. Falta definir la regla de negocio del recaudo (por período de factura vs. por fecha de pago).

## Proceso y decisiones
<!-- Completa con tus palabras: -->
- Cómo uniste las dos bases y por qué elegiste `NRO_FACTURA`.
- Cómo trataste los números de factura repetidos y los valores negativos.
- Cómo definiste el indicador de recaudo (por período de factura o por fecha de pago).
- Qué segmentos comparaste (categoría, subcategoría, ciclo).

## Resultado o aprendizaje
<!-- Escribe aquí los hallazgos que puedas respaldar con las bases. No inventes métricas. -->

## Evidencias
Capturas del análisis y de tablas **sin datos personales**, en la carpeta `img/`. Notebook o libro de Excel con datos anonimizados.

## Herramientas
Excel avanzado (tablas dinámicas) y/o Python con pandas (lectura de Excel, cruce de tablas y agregaciones); SQL para consultar la base unida.
