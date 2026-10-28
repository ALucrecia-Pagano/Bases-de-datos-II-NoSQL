# Aporte de Amanda — modelo, integridad y migración

Borrador breve para integrar al futuro PDF grupal, consignas 1–3. Revisión grupal pendiente; no constituye el informe final ni su conclusión.

Se representó el subconjunto de cinco pedidos de FoodStore en `foodstore_unidad7.pedidos`, con un documento por pedido, cliente mínimo embebido y un arreglo de líneas. Se conservó el ID del pedido como `_id`; los identificadores de pedido, cliente y producto usan BSON Long, las cantidades Int32, las fechas Date en UTC y los importes Decimal128. El cliente contiene su ID y un alias sintético `Cliente <id>`, sin nombres ni contactos reales. Se excluyeron observaciones. Los precios históricos proceden de `detalle_pedido.precio_unitario`; los nombres de productos son descripciones actuales del origen.

Se conservaron dos reglas principales de integridad:

1. Cantidad entera positiva e importes finitos no negativos.
2. Subtotal igual a cantidad por precio histórico y total igual a suma de subtotales.

El procedimiento controla además IDs, existencia de referencias al extraer y ausencia de productos duplicados por pedido. Los cálculos se realizan de forma exacta y se comprueba que las fechas no pierdan precisión al convertirlas a BSON Date. Estos controles del procedimiento no son restricciones de PostgreSQL trasladadas automáticamente ni validadores permanentes de MongoDB.

Se embebieron cliente y líneas para recuperar el pedido completo en una sola estructura. Esto duplica datos descriptivos entre pedidos y exige una política explícita si cambian; no se midió rendimiento ni se acreditó un historial de nombres.

Amanda realizó manualmente la extracción de solo lectura desde `foodstore_dev.public` y la migración en Compass desde el JSON conservado con SHA-256. El script validó el lote, comprobó IDs existentes e insertó mediante `insertMany` ordenado. La verificación posterior comparó todos los campos con el lote fuente y comprobó tipos BSON. Las capturas inspeccionadas documentan inserción confirmada de IDs Long 1–5 y verificación satisfactoria de cinco pedidos y siete líneas. La revisión del asistente fue documental y visual, sin nuevas ejecuciones en motores.

El resultado cubre este lote y su correspondencia con la extracción, no el estado futuro de las bases. Una inserción ordenada no es una transacción del lote. Permanecen pendientes la aprobación grupal del diseño y la confirmación académica de la suficiencia del cliente con ID y alias.

Referencias para integrar: [modelo documental](../docs/modelo_documental.md), [resultado y límites de migración](../docs/resultado_migracion.md), [extracción original](../evidencias/extraccion_20261028_170446.json), [captura de inserción](../evidencias/migracion_insercion.png) y [captura de verificación](../evidencias/migracion_verificacion.png). Este aporte no completa las consultas de Mateo ni el análisis de IA y la conclusión de Lucas.
