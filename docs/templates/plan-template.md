# Plantilla de plan técnico

Guardar junto a la spec o en el directorio de planes del proyecto. El plan técnico
ejecutable solo se prepara para una versión aprobada de la spec. Durante
descubrimiento puede existir un borrador de arquitectura, pero debe identificarse
como propuesta previa a baseline y no autoriza implementación.

## Cabecera

- Objetivo:
- Spec y versión:
- Estado:
- Stack y versiones propuestos:
- Restricciones globales:
- Riesgos que bloquean tareas:

## Arquitectura

Describir responsabilidades, límites entre componentes y flujos principales.
Añadir un diagrama cuando aclare dependencias o el flujo de datos.

## Interfaces y contratos

| Componente | Interfaz exacta | Entrada | Salida/error | Requisitos |
|---|---|---|---|---|

## Modelo de datos y persistencia

Esquemas, claves, restricciones, índices, migraciones, historial y tratamiento de
datos ausentes. Identificar los ejemplos ficticios.

## Acceso, privacidad y seguridad

Actores y permisos; datos personales; abuso; contenido público; retención y borrado;
riesgos relevantes y medidas verificables.

## Decisiones técnicas

| ID | Decisión | Alternativa considerada | Motivo | Requisitos |
|---|---|---|---|---|

## Estrategia de verificación

| Criterio/caso | Capa de verificación | Procedimiento o comando | Resultado esperado |
|---|---|---|---|

Incluir datos faltantes, errores, permisos, accesibilidad, rendimiento y flujos de
extremo a extremo que exija la spec.

## Migración, publicación y operación

Incluir cambios de datos, entornos, monitoreo y recuperación ante fallos cuando
apliquen. Indicar el responsable de operar el sistema.

## Riesgos y supuestos

Separar hechos confirmados, decisiones del responsable y propuestas del agente.
No convertir una suposición en requisito de forma silenciosa.

## Revisión de cobertura

Relacionar cada requisito de la spec con una parte del plan. Enumerar los contratos
que sigan sin resolverse y qué tareas dependen de ellos.
