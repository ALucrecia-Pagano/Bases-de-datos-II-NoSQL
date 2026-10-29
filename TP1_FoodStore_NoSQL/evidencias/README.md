# Registro de evidencias

Aplicar las [reglas del proyecto](../../AGENTS.md). Esta carpeta contiene las
[extracciones JSON](extraccion_20261028_170446.json) y
[extraccion_20261029_102959.json], las capturas de [inserción](migracion_insercion.png)
y [verificación de Amanda](migracion_verificacion_amanda.png) de la migración
ejecutada manualmente por Amanda, y las capturas de [MongoDB](consultas_mongodb_consignas_4_5.png),
[PostgreSQL](consultas_postgresql_consignas_4_5.png) y [verificación de Mateo](migracion_verificacion_mateo_20261029.png)
de las consultas y comparación de las consignas 4–5 ejecutadas por Mateo. El
[resultado de la migración](../docs/resultado_migracion.md) registra su contexto
y límites; la comparación está documentada en
[comparacion_resultados.md](../docs/comparacion_resultados.md). La revisión del
asistente fue documental y visual, sin ejecutar motores.

Estas evidencias corresponden a la extracción, migración y consultas del lote;
no sustituyen el contraste de IA ni el trabajo de las consignas 6–7, que siguen
pendientes.

Para cada ejecución autorizada registrar:

- Fecha real, hora y zona horaria.
- Objetivo, consigna y responsable del registro.
- Motor, versión conocida, herramienta y destino (base, colección o tablas), sin secretos.
- Estado o subconjunto de datos relevante y parámetros usados.
- Comando o consulta exactos y referencia al archivo correspondiente.
- Resultado observado, cantidades e IDs pertinentes, errores y limitaciones.
- Nombre o enlace de la evidencia y pasos suficientes para reproducirla.

Distinguir propuesta, implementación, ejecución y verificación; identificar como tales los antecedentes aportados por el equipo. No inventar resultados, fechas ni versiones.

Conservar las evidencias originales sin alterarlas. Si contienen datos sensibles, mantenerlas fuera de lo publicable y producir una copia anonimizada identificada como tal. Revisar capturas, texto y JSON antes de publicarlos; no incluir contraseñas, cadenas de conexión con secretos, respaldos completos ni datos personales reales. La política de exclusión no oculta texto, JSON ni capturas por defecto.

Convención sugerida para futuras evidencias: `AAAA-MM-DD_consigna_descripcion.ext`, usando la fecha efectiva de captura. Una captura aislada debe acompañarse del contexto necesario.
