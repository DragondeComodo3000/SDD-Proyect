# Instrucciones para agentes — catálogo de tecnología y gaming

## Encargo vigente

La fase actual es exclusivamente de planificación SDD. No escribir código del
producto, instalar dependencias, generar una aplicación ni desplegarla sin una
instrucción posterior y explícita del usuario que autorice implementación.

## Lectura obligatoria

Antes de trabajar, leer `README.md`, `docs/constitution.md`,
`docs/product-vision.md`, `docs/decisions.md` y `docs/sdd-workflow.md`.
Para una funcionalidad, leer además su spec, trazabilidad y, cuando existan, plan,
contratos y tareas. No asumir que el último documento leído tiene prioridad.

## Autoridad y estados

- Las instrucciones explícitas del usuario prevalecen sobre estos documentos.
- Una propuesta del agente requiere aprobación explícita; la baseline actual está aprobada según `docs/baseline.md`.
- Las decisiones confirmadas tienen su fundamento en `docs/decisions.md`.
- La constitución y la spec actuales están aprobadas como baseline; no habilitan por sí solas implementar.
- Si dos documentos se contradicen, registrar el conflicto y resolverlo antes de
  ejecutar trabajo que dependa de él. Se puede continuar trabajo independiente.
- No inventar RF ausentes ni reinterpretar silenciosamente un requisito para
  adaptarlo a la implementación.

## Cambios documentales

Se pueden redactar y mejorar borradores dentro del encargo de planificación.
Una decisión confirmada solo cambia por una nueva instrucción del responsable.
Un cambio a una baseline aprobada requiere análisis de impacto y nueva aprobación
del alcance afectado; correcciones editoriales sin cambio de significado se
registran sin crear un circuito de aprobación innecesario.

## Evidencia y ejecución futura

- Los IDs son estables; no renumerar requisitos eliminados ni reutilizar sus IDs.
- Cada criterio de aceptación tendrá un escenario verificable y un resultado
  esperado concreto. Cada tarea señalará los criterios que satisface.
- No marcar una tarea hecha por existir el archivo ni una spec cumplida porque
  una suite parcial pase.
- Cuando se autorice implementar, ejecutar solo la tarea o conjunto autorizado.
  Registrar resultados reales y detenerse al alcanzar ese límite.
- Nunca fabricar salidas de comandos, datos de productos, precios, fuentes,
  popularidad, resultados de tests ni aprobaciones humanas.
- Los datos de ejemplo deben estar identificados como ficticios y no convertirse
  en datos publicados por accidente.
- No versionar secretos, credenciales ni datos personales reales de participantes.
  Los ejemplos y fixtures deben ser ficticios o estar anonimizados; no copiar
  contenido de terceros sin una fuente y permiso de uso adecuados.

## Idioma y herramientas

Documentación, interfaz y contenidos dirigidos al público en español, según
DEC-014. Las convenciones del futuro código se resolverán durante el descubrimiento.
Consultar `docs/development-conventions.md` y ADE-017 como convenciones aprobadas;
la arquitectura Django está registrada en DEC-024. No imponer otra arquitectura
o herramienta por preferencia del agente.
No iniciar implementación hasta que el responsable apruebe la baseline.
El flujo SDD debe poder entenderse con los archivos del repositorio, sin depender
de skills privadas o del historial de esta conversación.
