# Registro de baseline SDD

Estado: **aprobada por el responsable el 2026-10-26**.

## Alcance aprobado

La baseline define el MVP del catálogo público gaming, la arquitectura Django
modular con HTML renderizado en servidor, las convenciones técnicas, el modelo de
datos por categoría y el proceso SDD. Incluye las decisiones confirmadas DEC-001
a DEC-024 y las decisiones delegadas ADE-001 a ADE-019, aprobadas por el
responsable en conjunto con esta baseline.

| Artefacto | Versión aprobada | Estado |
|---|---:|---|
| `docs/constitution.md` | 1.0 | Aprobada |
| `docs/product-vision.md` | 1.0 | Aprobada |
| `docs/sdd-workflow.md` | 1.0 | Aprobado |
| `specs/001-catalogo/spec.md` | 0.20 | Aprobada; armoniza criterios con ADE-009/ADE-010 adoptadas |
| `specs/001-catalogo/category-data.md` | 1.0 | Aprobado |
| `specs/001-catalogo/acceptance.md` | 1.1 | Escenarios aprobados como diseño; no ejecutados |
| `specs/001-catalogo/traceability.md` | 1.1 | Aprobada como matriz de diseño |
| `specs/001-catalogo/plan.md` | 0.3 | Aprobado |
| `docs/development-conventions.md` | 1.0 | Aprobadas |
| `docs/decisions.md` | vigente | DEC confirmadas; ADE adoptadas en esta aprobación |
| `specs/001-catalogo/implementation-backlog.md` | 1.0 | Plan de tareas generado después de la aprobación; pendiente de ejecución |

La matriz de aceptación contiene 41 criterios CAT-CA y 40 escenarios CAT-CP.
Todos los criterios tienen al menos un escenario diseñado. Esta cobertura no
significa que existan pruebas automatizadas, que se hayan ejecutado ni que el
producto esté implementado.

La spec v0.20 integra CAT-CA-040/041 para reflejar revisión anual de fichas activas
y estados de interfaz ya incluidos en ADE-009/ADE-010. Esta armonización no añade
decisiones nuevas ni amplía el alcance aprobado.

El backlog CAT-T-001 a CAT-T-037 se elaboró después de aprobar la baseline, dentro
del alcance de planificación autorizado. No modifica requisitos ni decisiones;
la matriz `traceability.md` enlaza cada criterio con sus tareas futuras.

## Decisiones y límites que siguen abiertos

Las siguientes decisiones no cambian los contratos aprobados. Son gates previos
a la operación indicada y deben resolverse antes de depender de ellas:

- **PND-012:** hosting, presupuesto, almacenamiento de medios/correo, copias,
  recuperación, disponibilidad y proveedor CI; antes de estimar costos y desplegar.
- **PND-020:** jurisdicciones, privacidad, cookies, términos y derechos de uso;
  antes de habilitar cuentas y comentarios públicamente.
- **PND-021:** nombre comercial, dominio y recursos de marca; antes de publicar.
- Revalidar las versiones efectivas de Python, Django, PostgreSQL y herramientas
  antes de iniciar implementación. La baseline conserva los valores previstos en
  ADE-016/017 como defaults aprobados, sujetos a esa comprobación técnica.

## Autorización de trabajo

Esta aprobación cierra la baseline de planificación y permite usar el backlog
documental de `specs/001-catalogo/tasks.md`. **No autoriza escribir, generar,
instalar ni ejecutar código funcional del producto.** La fase vigente sigue
limitada a SDD; iniciar implementación requiere una instrucción explícita
posterior del responsable.

## Historial

| Fecha | Evento | Evidencia |
|---|---|---|
| 2026-10-26 | El responsable aprobó la baseline completa, condicionada a que no contuviera contradicciones o incoherencias. La revisión QA independiente no dejó hallazgos bloqueantes abiertos. | Confirmación del responsable en la conversación; spec 0.20, plan 0.3 y artefactos listados arriba. |
| 2026-10-26 | Spec 0.20 y escenarios/matriz 1.1 incorporan requisitos ya adoptados en ADE-009/ADE-010 y cierran contradicciones detectadas en la revisión final. No amplían el alcance aprobado. | CAT-CA-040/041, CAT-CP-039/040; vínculos actualizados en `traceability.md`. |
