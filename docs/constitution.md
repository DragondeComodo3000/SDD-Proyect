# Constitución del proyecto

Versión: 1.0. Estado: **aprobada como parte de la baseline el 2026-10-26**.
Estos principios gobiernan el proceso SDD del catálogo. La aprobación no autoriza
por sí sola la implementación del producto.

| ID | Principio | Cómo comprobarlo |
|---|---|---|
| CONST-01 | La spec precede a la implementación. | Cada cambio funcional referencia una versión aprobada y criterios de aceptación identificados. |
| CONST-02 | Ninguna ambigüedad bloqueante se resuelve en silencio. | Las decisiones que cambian alcance, datos o experiencia tienen resolución registrada y responsable. |
| CONST-03 | La información publicada es verificable. | Las reglas del catálogo exigen procedencia, revisión y tratamiento explícito de datos faltantes; una IA no inventa hechos. |
| CONST-04 | Las variantes preservan su identidad técnica. | Los contratos establecen cuándo dos variantes comparten especificaciones y cuándo son productos distintos. |
| CONST-05 | El precio se presenta como aproximado. | La ficha usa «Precio aproximado» en USD con el importe cargado por el equipo; la selección de fuentes y del método de estimación corresponde al equipo durante la carga y no bloquea el diseño. |
| CONST-06 | La evidencia gobierna la finalización. | Cada criterio aplicable tiene cobertura y un resultado real; los pendientes y fallos impiden declarar cumplimiento. |
| CONST-07 | Se elige la solución más sencilla que cumpla los requisitos. | Cada dependencia o servicio relevante tiene una necesidad identificada y una alternativa evaluada. |
| CONST-08 | El trabajo avanza dentro del alcance autorizado. | Tareas, cambios y entregas pueden vincularse con la autorización vigente; no se continúa por iniciativa fuera de ella. |
| CONST-09 | La accesibilidad y la protección del catálogo se especifican. | Los contratos incluyen uso por teclado, estados de interfaz y permisos de publicación con criterios verificables. |
| CONST-10 | La documentación evoluciona con el producto. | Un cambio de comportamiento actualiza la cadena afectada de decisiones, requisitos, criterios, casos, tareas y evidencia. |
| CONST-11 | La constitución gobierna el proceso; la spec define el comportamiento. | Ningún principio o regla técnica inventa una función, permiso o resultado visible que no tenga fuente en una decisión o requisito aprobado. |
| CONST-12 | La trazabilidad funciona en ambas direcciones. | Desde cualquier requisito se localizan sus decisiones, criterios, casos, tareas y evidencia; desde una decisión se identifican los requisitos que afecta. |
| CONST-13 | Los ejemplos y evidencias protegen los datos. | No se versionan secretos ni datos personales reales; ejemplos y fixtures se identifican como ficticios o se anonimizan. |
| CONST-14 | Todo cambio cumple una definición de terminado acordada. | La tarea verifica criterios aplicables, evidencia real, calidad requerida y actualización de los artefactos afectados antes de marcarse completa. |

## Aplicación

Una excepción debe describir la necesidad, el principio afectado, el alcance y
la autorización correspondiente. La IA puede proponerla, pero no aprobarla en
nombre del responsable del producto.

Una corrección documental que no cambia el comportamiento puede realizarse
directamente, dejando constancia de qué se corrigió.

## Relación con otras constituciones técnicas

Se revisó como material de referencia la constitución técnica externa facilitada
por el responsable. Se incorporaron a la constitución aprobada principios generales de separación entre proceso y
comportamiento, trazabilidad, protección de datos y definición de terminado. No se
importaron reglas específicas del sistema de taller ni su stack, herramientas,
estructura de repositorios o convenciones de equipo. La evaluación está resumida
en [`constitution-review.md`](constitution-review.md).

## Historial de cambios

| Versión | Cambio | Aprobación |
|---|---|---|
| 0.2 | Incorpora principios generales de separación entre constitución y spec, trazabilidad, protección de datos y definición de terminado. | Propuesta revisada. |
| 1.0 | Se aprueba la constitución como parte de la baseline del proyecto. | Aprobación del responsable, 2026-10-26; `baseline.md`. |
