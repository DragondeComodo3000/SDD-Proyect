# Revisión de la constitución técnica externa

Estado: revisión documental.  
Material leído en modo solo lectura: carpeta `ai-context/constitution/`
facilitada por el responsable; no es una dependencia de este repositorio.
La constitución externa rige otro proyecto (DINOCO, sistema de taller mecánico),
con un stack y reglas de negocio propios. Por eso se evaluaron principios
generales y no se copiaron sus reglas de implementación literalmente.

## Aportes incorporados a la constitución aprobada

| Tema del material externo | Adaptación para el catálogo | Ubicación |
|---|---|---|
| La constitución define cómo se trabaja, no qué comportamiento de negocio tiene el producto (GEN-11) | La constitución no puede crear funciones, permisos o resultados públicos fuera de las decisiones y requisitos aprobados | `docs/constitution.md`, CONST-11 |
| Las reglas faltantes se documentan y vinculan a preguntas/supuestos (GEN-12) | Se conserva el registro de decisiones y propuestas; en este SDD un comportamiento que cambia alcance no se implementa por defecto conservador: bloquea la aprobación de esa parte hasta resolverlo | CONST-02 y `docs/sdd-workflow.md` |
| IDs trazables hacia adelante y atrás (GEN-13) | Mantener la relación decisión → requisito → criterio → caso → tarea → evidencia y poder recorrerla en sentido inverso | CONST-10, CONST-12 y `specs/001-catalogo/traceability.md` |
| No versionar secretos ni datos personales reales (GEN-14, TL-14) | No introducir secretos ni información real de participantes; marcar ejemplos y datos de prueba como ficticios o anonimizados | CONST-13 y `AGENTS.md` |
| Definition of Done explícita (GEN-15) | Una tarea no se completa por terminar de escribirla: necesita criterios aplicables, verificación real y evidencia documental | CONST-06, CONST-14 y `docs/sdd-workflow.md` |
| Estados de carga, error y vacío en vistas con datos (FE-13) | Adoptarlo como elemento obligatorio al detallar contratos de interfaz, sin imponer aún una implementación visual | CONST-09, `specs/001-catalogo/spec.md` y `acceptance.md` |
| Seguridad en el servidor y no solo ocultando controles de interfaz (BE-29, FE-19) | Exigir autorización en servidor para las operaciones de edición y moderación incluidas en la baseline | CONST-09, CAT-CA-039 y `specs/001-catalogo/plan.md` |
| Módulos por funcionalidad con capas internas (BE-02, FE-05) | Usar apps Django por área de producto; separar responsabilidades sin copiar la estructura de repositorios de Nest/React | `specs/001-catalogo/plan.md` y `docs/development-conventions.md` |
| Convenciones de ramas, commits y revisión (GEN-07 a GEN-10) | Proponer Conventional Commits e integración por PR/MR, dejando proveedor Git y aprobación para el equipo local | `docs/development-conventions.md` |
| Configuración, CI y entorno local reproducibles (TL-03, TL-07, TL-09) | Proponer herramientas equivalentes del stack Python y decidir CI/Docker según hosting y capacidad del equipo | `docs/development-conventions.md` |

## Reglas externas que no se trasladan

- NestJS, Prisma, React, Vite, Node, npm, TypeScript y la estructura separada de
  frontend/backend no son requisitos de este producto. DEC-024 confirma Django
  como arquitectura del MVP; ADE-016 conserva los detalles de versiones a validar.
- Vocabulario de vehículos, repuestos, órdenes de taller, bahías, roles y sus
  estados: pertenece al dominio DINOCO y no tiene equivalentes asumidos aquí.
- Stock no negativo, asignación de bahías, secuencia de presupuestos, concurrencia
  de órdenes y scripts de importación de papeles: reglas específicas del taller.
- GitLab, npm/lockfiles, ESLint/Prettier y comandos de CI: específicos de ese
  equipo o stack. Sus propósitos se adaptaron como propuestas; no se trasladan
  sus herramientas ni proveedor Git sin confirmación.
- Reglas detalladas de JWT, React Query, DTOs, OpenAPI, Prisma, PostgreSQL Docker
  y datos semilla: dependen del stack y de la operación que se aprueben aquí.
- La regla de documentación/producto en español e identificadores/commits en
  inglés se adoptó mediante ADE-017; DEC-014 por sí sola fija el idioma público.

## Comprobación de coherencia del paquete SDD

- `README.md` informa que Django quedó elegido, y que las versiones y herramientas
  exactas aún requieren validación; también resume votos y moderación.
- La única condición mínima de contenido es una ficha revisada por categoría,
  sin cuota adicional ni promesa de catálogo exhaustivo (DEC-022/023).
- El plan registra la arquitectura Django confirmada. La estructura física,
  herramientas y Git están aprobados en `docs/development-conventions.md`, sujetos
  a revalidar versiones y elegir proveedor CI al implementar.
- La constitución, la spec, el plan y las convenciones están aprobados como
  baseline; el código sigue sin autorización y el backlog no está ejecutado.

La constitución v1.0 se aprobó el 2026-10-26 junto con la baseline. Esta revisión
no representa autorización para implementar la aplicación.
