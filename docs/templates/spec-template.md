# Plantilla de especificación

Copiar a specs/NNN-nombre/spec.md. Completar la cabecera y conservar los IDs
asignados. Eliminar instrucciones de plantilla al publicar una versión aprobada.

## Cabecera

- Versión y estado: borrador, en revisión, aprobada o sustituida.
- Responsable y fuente de decisiones:
- Aprobación para implementación:
- Spec que reemplaza, si aplica:

## Contexto y objetivo
## Usuarios, necesidades y permisos
## Glosario de términos del producto
## Historias de usuario
Como [persona], quiero [acción] para [resultado].

## Alcance
### Incluido
### Excluido
### Dependencias y restricciones

## Requisitos funcionales

### [AREA]-RF-001: [nombre verificable]

Descripción, actor y referencia a decisiones que lo sustentan.

#### Criterios de aceptación

- [AREA]-CA-001: Cuando [evento y condiciones], el sistema deberá [resultado observable].
- [AREA]-CA-002: Si [entrada o condición de rechazo], el sistema deberá [error y efecto en datos].

## Contratos de datos

| Entidad o campo | Tipo/unidad | Obligatorio | Valores válidos | Tratamiento si falta | Fuente |
|---|---|---|---|---|---|

Marcar ejemplos ficticios. No usar valores inventados como datos reales.

## Estados y transiciones

| Estado inicial | Evento | Estado final | Visible para |
|---|---|---|---|

## Requisitos no funcionales

### [AREA]-RNF-001

Definir medida, condición y umbral verificable, o registrar qué decisión pendiente
impide fijarlos.

## Errores, datos incompletos y recuperación
## Seguridad, privacidad y permisos
## Accesibilidad e idioma
## Casos límite y fuera de alcance
## Criterios de finalización
## Decisiones abiertas

| ID | Pregunta | Efecto en el producto | Responsable | Estado |
|---|---|---|---|---|

## Historial de cambios

| Versión | Cambio de comportamiento | Requisitos afectados | Aprobación |
|---|---|---|---|

Una spec no pasa a aprobada mientras tenga decisiones abiertas que cambien el
comportamiento incluido. Registrar quién tomó una decisión delegada; no atribuirla
al usuario.
