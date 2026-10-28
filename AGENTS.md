# Instrucciones para asistentes de IA

## Contexto académico

FoodStore — Unidad 7: NoSQL. Bases de Datos II, Tecnicatura Universitaria en Programación, Universidad Tecnológica Nacional, Facultad Regional Mendoza. Comisión 4; profesor: Neira Sergio. Integrantes: Liendo Mateo, Ávila Lucas y Pagano Amanda.

- Repositorio actual: https://github.com/ALucrecia-Pagano/Bases-de-datos-II-NoSQL
- Antecedente relacional: https://github.com/ALucrecia-Pagano/Base_de_datos2

Este proyecto continúa FoodStore. El TP8 anterior corresponde a la Unidad 6; este trabajo corresponde a la Unidad 7 NoSQL y no al TP7 anterior de Administración y Seguridad. No asumir que los archivos del repositorio anterior describen el estado actual de las bases ni modificar ese repositorio.

Leer [README.md](README.md), [CONTRIBUTING.md](CONTRIBUTING.md) y el [plan de trabajo](docs/plan_trabajo.md). Las reglas comunes para asistentes se mantienen en este archivo.

## Alcance y entregables

- Modelar pedidos con detalles y datos esenciales del cliente.
- Migrar al menos cinco pedidos de PostgreSQL a MongoDB conservando IDs, instantes de fecha, estados, cantidades y precios históricos.
- Consultar MongoDB: a) listar identificador y estado; b) filtrar por un estado existente; c) buscar pedidos que contengan un producto; d) buscar pedidos con total superior a un umbral justificado.
- Comparar b) y c) en ambos motores, incluyendo cantidades e identificadores de pedidos.
- Consultar una IA y contrastar dos afirmaciones con documentación oficial o resultados reproducibles del laboratorio.
- Entregar un PDF de hasta cinco páginas, sin contar código adjunto, con conclusión de hasta 200 palabras; adjuntar `mongodb/consultas_mongodb.js` y `postgresql/consultas_postgresql.sql`, o equivalentes.

La etapa inicial solo prepara estructura, reglas y plantillas. No resuelve consignas, implementa validadores o consultas, migra datos ni genera el PDF.

## Forma de trabajo

- Antes de actuar, leer las instrucciones aplicables, revisar el directorio, la rama, el estado de Git y los archivos existentes.
- Trabajar exclusivamente dentro de este repositorio, por etapas y dentro de la tarea solicitada. Conservar el README de Amanda; en esta preparación solo proponer correcciones o enlaces.
- Un pedido explícito autoriza las ediciones necesarias dentro de su alcance; no pedir confirmación por cada cambio rutinario. Consultar antes de ampliar el alcance, reemplazar decisiones acordadas o realizar acciones destructivas.
- No sobrescribir cambios ajenos ni descartar trabajo pendiente. Leer antes de editar e integrar contenido válido; informar conflictos antes de reemplazarlo.
- Mantener soluciones sencillas y adecuadas al nivel de la materia. No agregar herramientas, dependencias, automatizaciones ni archivos de herramientas innecesarios; no crear una licencia sin decisión expresa del equipo.

## Bases de datos y protección de datos

- PostgreSQL se conserva como origen de lectura y comparación, sin modificaciones para este TP.
- No conectarse a motores ni ejecutar consultas, SQL o JavaScript sin autorización para esa etapa y destino. Aprobar o guardar un script no autoriza ejecutarlo.
- Antes de una ejecución autorizada, identificar motor, conexión sin secretos, base, colección o tablas y efectos esperados. La autorización de una secuencia concreta permite completarla sin repetir la misma pregunta por cada sentencia.
- No borrar, restaurar, recrear ni sobrescribir bases o colecciones como solución automática ante un error.
- Diseñar la migración para detectar IDs existentes y detenerse ante conflictos, sin reemplazar documentos silenciosamente.
- Conservar IDs de origen, instantes de fecha, estados, cantidades y precios históricos. Tomar los precios de `detalle_pedido.precio_unitario`.
- Definir y justificar tipos BSON para identificadores, fechas e importes antes de implementar la migración, evitando pérdidas de precisión.
- Resolver explícitamente la representación de datos esenciales del cliente sin publicar información personal real. El nombre de la base y colección MongoDB, los tipos BSON, el tratamiento del cliente y el método de migración siguen pendientes.

## Git y colaboración

- No ejecutar `git add`, `commit`, `push`, `merge`, `rebase`, `reset`, `clean`, `pull` ni otras operaciones que escriban en Git, ni modificar configuraciones Git, sin autorización expresa. Amanda realiza los commits y pushes salvo nuevo pedido explícito.
- No realizar force push ni configurar protecciones remotas en esta preparación.
- No agregar firmas, colaboradores ni líneas `Co-authored-by`.
- Usar ramas de trabajo y revisión mediante pull request. No modificar la parte de otro integrante fuera del alcance autorizado; proponer los cambios necesarios para revisión.
- Responsabilidades acordadas: Amanda, consignas 1–3; Mateo, 4–5; Lucas, 6–7. El equipo completo revisa la conclusión y el informe final.
- Registrar la asistencia de IA de manera académica y verificable en la documentación correspondiente.

## Evidencias y comunicación

- Usar español claro, profesional, respetuoso y neutral. Describir responsabilidades y entregables sin valoraciones personales sobre integrantes.
- No inventar resultados, tiempos, versiones, pruebas ni fuentes. Distinguir propuesta, implementación, ejecución y verificación.
- Las comprobaciones previas aportadas por el equipo no son verificaciones nuevas del asistente. No marcar tareas completas sin evidencia suficiente.
- Conservar evidencias originales en resguardo local cuando contengan información sensible; generar versiones anonimizadas para publicar. No alterar originales ni publicar credenciales, cadenas de conexión con secretos, respaldos completos o datos personales reales.
- Verificar afirmaciones técnicas con documentación oficial o resultados reproducibles; registrar sus fuentes y contexto.
- Al terminar, revisar el diff y el alcance; informar cambios, comprobaciones realizadas, limitaciones, pendientes y siguiente paso. Detenerse al completar la etapa solicitada.
