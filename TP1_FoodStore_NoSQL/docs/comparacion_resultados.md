# Comparación de resultados — consignas 4 y 5

Responsable: Mateo, consignas 4–5. Referencias: [plan](plan_trabajo.md), [reglas](../../AGENTS.md) y [registro de evidencias](../evidencias/README.md).

## Contexto de ejecución

Las consultas fueron ejecutadas el 2026-10-29 sobre [consultas MongoDB](../mongodb/consultas_mongodb.js) y [consultas PostgreSQL](../postgresql/consultas_postgresql.sql). MongoDB Server fue `9.0.4` con `mongosh 2.14.0`; PostgreSQL fue `17.10` mediante `psql`. Las consultas fueron de lectura y no modificaron los datos.

- Subconjunto común: pedidos `1, 2, 3, 4 y 5`.
- Estado elegido: `ENTREGADO`, existente en los cinco pedidos del lote.
- Producto elegido: ID `1`, presente en los pedidos `1, 3 y 5`.
- Umbral de la consulta d): total estrictamente mayor que `Decimal128("3000.00")`. Se justifica porque distingue los pedidos de mayor importe del lote y no incluye el total de `2800.00`.
- Origen documentado: PostgreSQL `foodstore_dev.public`; destino documentado: MongoDB `foodstore_unidad7.pedidos`.
- La extracción utilizada fue [extraccion_20261029_102959.json](../evidencias/extraccion_20261029_102959.json), con SHA-256 `0e17c782de3063ec88fd871251b848aedac4084d4620663b336475f0db1b794f`.

## Evidencias

- [Salida de MongoDB — consignas 4–5](../evidencias/consultas_mongodb_consignas_4_5.png)
- [Salida de PostgreSQL — consignas 4–5](../evidencias/consultas_postgresql_consignas_4_5.png)
- [Verificación de migración de Mateo](../evidencias/migracion_verificacion_mateo_20261029.png)
- [Extracción utilizada](../evidencias/extraccion_20261029_102959.json)

## Parámetros y equivalencia

Las consultas b) usan el mismo estado y las consultas c) el mismo ID de producto. En MongoDB se filtra `lineas.id_producto` y se proyecta la línea coincidente; en PostgreSQL se une `detalle_pedido` y se conserva `cantidad` junto con `precio_unitario`. En ambos casos se cuentan pedidos distintos mediante sus IDs, no filas ajenas al lote.

## Resultados comparados

| Consulta | Parámetro | Cantidad PostgreSQL | IDs PostgreSQL | Cantidad MongoDB | IDs MongoDB | Evidencia |
|---|---|---|---|---|---|---|
| b) Estado | `ENTREGADO` | 5 | 1, 2, 3, 4, 5 | 5 | 1, 2, 3, 4, 5 | [psql](../evidencias/consultas_postgresql_consignas_4_5.png), [mongosh](../evidencias/consultas_mongodb_consignas_4_5.png) |
| c) Producto | ID `1` | 3 | 1, 3, 5 | 3 | 1, 3, 5 | [psql](../evidencias/consultas_postgresql_consignas_4_5.png), [mongosh](../evidencias/consultas_mongodb_consignas_4_5.png) |

## Interpretación

Los resultados coinciden en cantidad e IDs: b) devuelve los cinco pedidos con estado `ENTREGADO`, y c) devuelve los pedidos 1, 3 y 5 que contienen el producto 1. En c), ambos motores también conservaron las cantidades y precios históricos: (1, 2, 1000.00), (3, 3, 1050.00) y (5, 1, 1050.00). La consulta d) de MongoDB devolvió los pedidos 3 y 4, cuyos totales son 3150.00 y 6200.00. La comparación queda limitada al subconjunto migrado y a la ejecución registrada; no demuestra sincronización futura.
