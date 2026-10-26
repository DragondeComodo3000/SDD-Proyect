# CAT — Backlog de planificación

Estado: **seguimiento aprobado de la baseline**. Spec de referencia: versión
0.20. Las tareas CAT-T son trabajo futuro planificado; ninguna está ejecutada.

Las tareas CAT-PLAN-001 a CAT-PLAN-010 quedan completadas como trabajo documental
por delegación del responsable. Sus decisiones se registran como ADE; los casos de
aceptación son escenarios diseñados, no pruebas implementadas ni ejecutadas.

## Tareas de planificación completadas

### [CAT-PLAN-001] Cerrar popularidad de portada

- Estado: completada.
- Requisitos: CAT-RF-001, CAT-RF-016.
- Criterios: CAT-CA-018; decisiones ADE-002.
- Evidencia: `docs/decisions.md`, `specs/001-catalogo/spec.md`, `acceptance.md` (CAT-CP-018).
- Hecho cuando: fuente de actividad, ventana, fallback, rastreadores y desempates quedaron definidos y trazables.

### [CAT-PLAN-002] Cerrar contrato de búsqueda

- Estado: completada.
- Requisitos: CAT-RF-002.
- Criterios: CAT-CA-019; decisión ADE-003.
- Evidencia: `spec.md` y `acceptance.md` (CAT-CP-019).
- Hecho cuando: campos, normalización, orden de coincidencia, límite y consulta vacía tienen resultado esperado.

### [CAT-PLAN-003] Cerrar filtros y orden

- Estado: completada.
- Requisitos: CAT-RF-003, CAT-RF-016, CAT-RF-017.
- Criterios: CAT-CA-020 a CAT-CA-022; decisión ADE-004.
- Evidencia: `spec.md` y `acceptance.md` (CAT-CP-020 a CAT-CP-022).
- Hecho cuando: combinación, rangos, ausencias, limpieza, conteo, desempates y valores faltantes son deterministas.

### [CAT-PLAN-004] Cerrar identidad de productos y variantes

- Estado: completada.
- Requisitos: CAT-RF-005 a CAT-RF-007.
- Criterios: CAT-CA-023; decisión ADE-006.
- Evidencia: `spec.md` y `category-data.md`; CAT-CP-023.
- Hecho cuando: se especifica qué separa ficha de variante y se prohíbe heredar datos incompatibles.

### [CAT-PLAN-005] Definir diccionarios de las ocho categorías

- Estado: completada.
- Requisitos: CAT-RF-003, CAT-RF-006, CAT-RF-011.
- Criterios: CAT-CA-005, CAT-CA-024; decisión ADE-007.
- Evidencia: `category-data.md`; CAT-CP-024.
- Hecho cuando: las ocho categorías tienen filtros iniciales, campos mostrables, unidades y tratamiento de ausencia.

### [CAT-PLAN-006] Definir fuentes y revisión editorial

- Estado: completada.
- Requisitos: CAT-RF-004, CAT-RF-009 a CAT-RF-011.
- Criterios: CAT-CA-025, CAT-CA-026, CAT-CA-029; decisiones ADE-005, ADE-008, ADE-009.
- Evidencia: `spec.md`; CAT-CP-025, CAT-CP-026, CAT-CP-029.
- Hecho cuando: roles, checklist, procedencia y estados de publicación tienen comportamiento esperado.

### [CAT-PLAN-007] Cerrar precio y fecha

- Estado: completada.
- Requisitos: CAT-RF-007, CAT-RF-008.
- Criterios: CAT-CA-027, CAT-CA-028; decisiones DEC-013 y ADE-004.
- Evidencia: `spec.md`; CAT-CP-027 y CAT-CP-028.
- Hecho cuando: formato, ausencias, filtros y orden están definidos sin inventar datos.

### [CAT-PLAN-008] Cerrar cuentas, identidad anónima y votos

- Estado: completada.
- Requisitos: CAT-RF-012, CAT-RF-014.
- Criterios: CAT-CA-030, CAT-CA-031, CAT-CA-034, CAT-CA-035; decisiones ADE-011, ADE-012, ADE-014.
- Evidencia: `spec.md`; CAT-CP-030, CAT-CP-031, CAT-CP-034.
- Hecho cuando: unicidad por identidad, anonimato limitado, conteos, registro y eliminación tienen resultados esperados.

### [CAT-PLAN-009] Cerrar comentarios y moderación

- Estado: completada.
- Requisitos: CAT-RF-013, CAT-RF-015.
- Criterios: CAT-CA-032, CAT-CA-033; decisión ADE-013.
- Evidencia: `spec.md`; CAT-CP-032 y CAT-CP-033.
- Hecho cuando: validación, estados, permisos, visibilidad y límites por identidad están definidos.

### [CAT-PLAN-010] Cerrar apariencia y RNF

- Estado: completada.
- Requisitos: CAT-RF-018, CAT-RNF-002, CAT-RNF-003.
- Criterios: CAT-CA-036 a CAT-CA-038; decisiones ADE-010 y ADE-015.
- Evidencia: `spec.md`; CAT-CP-035 a CAT-CP-037.
- Hecho cuando: tema, accesibilidad y objetivos medibles de rendimiento están especificados.

## Tareas pendientes

### [CAT-PLAN-011] Cerrar gates operativos antes de lanzamiento

- Estado: pendiente antes de producción/publicación; no bloquea el desarrollo local.
- Depende de: resolver PND-012, PND-020 y PND-021 según cada gate.
- Requisitos: CAT-RNF-003, CAT-RNF-004.
- Decisiones: PND-012, PND-020 y PND-021.
- Archivos/contratos: `docs/decisions.md`, plan §11 y §13.
- Hecho cuando: proveedor/presupuesto/recuperación están definidos antes del despliegue; privacidad, cookies y derechos se revisan para los mercados elegidos; marca/dominio se resuelve antes de publicación.
- Evidencia: gates y tareas separadas en `docs/baseline.md` y CAT-T-035 a CAT-T-037.

### [CAT-PLAN-012] Hacer revisión QA independiente del paquete SDD 0.20

- Estado: completada; hallazgos bloqueantes resueltos en spec 0.20 y plan 0.3.
- Depende de: CAT-PLAN-001 a CAT-PLAN-010.
- Requisitos: todos los CAT-RF y CAT-RNF.
- Criterios: CAT-CA-001 a CAT-CA-041.
- Archivos/contratos: `spec.md`, `acceptance.md`, `traceability.md`, `plan.md`, `category-data.md`, `docs/development-conventions.md`, `docs/constitution-review.md`.
- Hecho cuando: otra lectura detecta contradicciones, ambigüedades y fallos de trazabilidad en spec, plan y convenciones; los hallazgos bloqueantes se resuelven y todos los criterios tienen escenario.
- Evidencia: la revisión independiente identificó brechas de campos obligatorios por categoría, versionado de correcciones, precisión de la ventana de popularidad, modelo de cuenta Django y separación de gates. Resoluciones: ADE-018/ADE-019, `category-data.md`, `ProductRevision` y modelo `User`/grupos en `plan.md`; se corrigió TDEC-005. El cierre añadió criterios explícitos para ADE-009/ADE-010, estados retirados y validación de precio; CAT-CA-001 a CAT-CA-041 tienen escenarios y tareas trazables.

### [CAT-PLAN-015] Cerrar convenciones de desarrollo con la referencia externa

- Estado: completada; convenciones aprobadas como versión 1.0.
- Depende de: CAT-PLAN-012.
- Requisitos: ninguno funcional; gobierna la estructura y el flujo de implementación.
- Decisiones: ADE-017, DEC-024; `docs/development-conventions.md`.
- Hecho cuando: árbol Django, idioma interno, gestor, pruebas, lint/formato, comandos CI y flujo Git agnóstico al proveedor están documentados; toda versión de herramienta se revalidará al implementar.
- Evidencia: `docs/development-conventions.md`; aprobación registrada en `docs/baseline.md`.

### [CAT-PLAN-013] Preparar y registrar aprobación de baseline

- Estado: completada el 2026-10-26.
- Depende de: CAT-PLAN-012 y CAT-PLAN-015.
- Requisitos: alcance elegido de CAT-RF y CAT-RNF.
- Archivos/contratos: spec v0.20, plan v0.3, decisions, acceptance, traceability, constitution y convención ADE-017.
- Hecho cuando: el responsable aprueba por versión y alcance o devuelve cambios; la evidencia identifica quién y cuándo.
- Evidencia: aprobación explícita del responsable, registrada en `docs/baseline.md`; incluye constitución v1.0, spec 0.20, plan 0.3, decisiones ADE-001 a ADE-019 y convenciones v1.0. La v0.20 hace explícitos defaults ADE-009/ADE-010 ya adoptados y no amplía el alcance.

### [CAT-PLAN-014] Crear tareas de implementación después de la aprobación

- Estado: completada como trabajo documental; tareas de implementación pendientes y no ejecutadas.
- Depende de: CAT-PLAN-013.
- Requisitos: los de la baseline aprobada.
- Archivos/contratos: plan aprobado, criterios CAT-CA y escenarios CAT-CP.
- Hecho cuando: cada tarea de código es pequeña, ordenada por dependencias y ligada a criterios, casos de verificación, interfaces afectadas y un resultado observable. Crear el backlog no implementa código; iniciar la implementación requerirá una instrucción explícita posterior.
- Evidencia: `implementation-backlog.md` contiene CAT-T-001 a CAT-T-037 con dependencias, criterios, casos de verificación y resultados observables.

La aprobación de baseline no autoriza iniciar CAT-T. Para ejecutar cualquier
tarea CAT-T se requiere una instrucción posterior explícita del responsable.
