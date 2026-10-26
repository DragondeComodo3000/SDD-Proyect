# Proceso SDD y criterios de paso

Versión: 1.0. Estado: proceso SDD adoptado como parte de la baseline el 2026-10-26.

## 1. Descubrimiento

Registrar propósito, personas, recorrido, alcance, restricciones y decisiones.
Preguntar sobre decisiones que cambian el producto. Usar propuestas explícitas
para detalles que el responsable delegue. No esconder dudas dentro del código.

Salida: visión coherente, decisiones identificadas y alcance delimitado.
El descubrimiento del MVP está documentado y aprobado en baseline 1.0.

## 2. Especificación y contratos de dominio

Describir comportamientos observables con IDs estables y criterios EARS:
«Cuando [evento y condiciones], el sistema deberá [resultado verificable]».
Para rechazo: «Si [condición inválida], el sistema deberá [respuesta y efecto
sobre los datos]». No utilizar «rápido», «intuitivo» o «completo» sin medida.

Cada criterio debe fijar precondiciones, entrada, salida y cambios de estado
cuando apliquen. Especificar vacíos, errores, datos faltantes y permisos.

En este proyecto deben existir contratos para identidad y variantes, atributos
por categoría, precios, fuentes, publicación, búsqueda y popularidad. Cada
contrato tendrá ejemplos válidos e inválidos claramente ficticios.

Salida: spec revisable y plan de validación. En este proyecto, la spec 0.20 y el
plan 0.3 están aprobados; cualquier decisión futura que cambie comportamiento
requiere control de cambios de baseline.

## 3. Revisión de calidad de la spec

Revisar ambigüedades, contradicciones, casos límite, criterios no verificables,
alcance accidental y conflictos con la constitución. Registrar cada hallazgo,
su requisito afectado, severidad, resolución y estado.

Una revisión vacía no demuestra ausencia de problemas: documentar qué escenarios
se comprobaron. Una revisión independiente es deseable antes de cerrar la baseline.

Salida: hallazgos bloqueantes resueltos y aprobación explícita de una versión
del alcance por el responsable del producto. Conservar la evidencia de aprobación.

## 4. Plan técnico

A partir de la spec aprobada, definir módulos, responsabilidades, interfaces,
persistencia, permisos, flujos de datos, estados, errores y dependencias.
Cada decisión técnica relevante tendrá justificación y alternativa descartada.
Definir versiones y comandos concretos cuando se haya elegido el stack.
Cerrar también estructura física, herramientas de calidad, flujo Git, formato de
commits y CI antes de descomponer el backlog de implementación. Estas decisiones
son técnicas y no pueden introducir comportamiento de producto.

No introducir reglas de negocio nuevas en el plan: deben volver a la spec.
Un contrato técnico todavía abierto bloquea las tareas que dependan de él.

Durante descubrimiento se permite un **borrador de arquitectura** para hacer
visibles opciones y riesgos antes de cerrar la spec. Debe marcarse como propuesta,
no puede fijar decisiones del producto por omisión, y no cuenta como plan aprobado
ni habilita tareas de implementación. El plan de este proyecto dejó ese estado al
ser aprobado como v0.3; futuros cambios de arquitectura deben pasar por control de
cambios de baseline.

## 5. Tareas de implementación

Después de aprobar la baseline, preparar el backlog es trabajo de planificación;
no autoriza implementar código. Este proyecto tiene el backlog en
`specs/001-catalogo/implementation-backlog.md`. Cada tarea tendrá ID, objetivo, dependencias,
archivos o módulos, interfaces que consume y produce, criterios cubiertos, casos
de prueba y «Hecho cuando».
El tamaño lo determina un resultado independiente que pueda verificarse.
No separar artificialmente «escribir todos los tests» de todo el desarrollo.

La tarea deberá prever prueba que detecte el comportamiento ausente, implementación,
verificación y actualización de evidencias. Esa previsión no afirma que el ciclo
ya se haya ejecutado. No marcar tareas futuras como hechas durante planificación.

## 6. Implementación futura

Esta etapa exige una nueva instrucción explícita del usuario: el encargo vigente
solo cubre documentación SDD. La IA ejecutará el alcance autorizado, conservará la
trazabilidad y se detendrá al completarlo. Una desviación se registra antes de
continuar trabajo dependiente.

## 7. Verificación y aceptación

Revisar todos los requisitos que realmente existen en la versión aprobada;
no asumir un rango numérico tomado de un prompt antiguo. Para cada criterio:
caso diseñado, prueba implementada, ejecución real, resultado y evidencia.

La aceptación requiere todos los criterios aplicables verificados, ninguna
incidencia bloqueante abierta y cumplimiento de los objetivos no funcionales.
Las exclusiones necesitan justificación aprobada. Una suite verde con cobertura
incompleta no permite declarar la spec cumplida.

## Estados y versiones

| Artefacto | Estados permitidos |
|---|---|
| Spec | borrador → en revisión → aprobada → sustituida |
| Decisión | pendiente → propuesta → confirmada; una confirmada puede ser sustituida |
| Tarea futura | pendiente → en curso → bloqueada o completada |
| Caso de prueba | diseñado → implementado → ejecutado |
| Resultado de ejecución | no ejecutado, aprobado, fallido o bloqueado |

Las flechas describen un flujo, no obligan a completar una fase que todavía no
fue autorizada. La evidencia de cada aprobación debe identificar versión y alcance.

## Identificadores y trazabilidad

Usar prefijos por funcionalidad, por ejemplo `CAT-RF-001`, `CAT-CA-001`,
`CAT-RNF-001`, `CAT-CP-001`, `CAT-T-001` y `CAT-INC-001`.
Un criterio tiene su propio ID aunque pertenezca a un RF con varios criterios.
No reutilizar ni renumerar IDs retirados; conservar el motivo de retiro.

La cadena mínima es: decisión → requisito → criterio → caso de prueba → tarea
→ evidencia. Los requisitos no funcionales también participan de esta cadena.

## Gestión de cambios

Antes de cambiar una baseline, describir motivo, comportamiento anterior y nuevo,
requisitos afectados, efectos sobre datos e interfaces, pruebas y tareas.
Un cambio de alcance necesita autorización del responsable. Un ajuste técnico
delegado que conserva el contrato se documenta con su justificación.

No mantener versiones contradictorias del mismo contrato en varios documentos:
definir una fuente y enlazarla. El plan y las tareas referencian los requisitos.
