# Catálogo de tecnología y gaming — planificación SDD

Estado: **baseline SDD aprobada; backlog de implementación planificado, no ejecutado**.

Este repositorio contiene la planificación de una web que ayuda a compradores y
personas curiosas a conocer dispositivos, variantes y especificaciones técnicas.
El nombre del producto aún no está decidido. En esta fase solo se crean documentos.

## Por dónde empezar

1. Leer [la visión y las decisiones confirmadas](docs/product-vision.md).
2. Consultar la [constitución aprobada](docs/constitution.md).
3. Consultar [las decisiones pendientes](docs/decisions.md).
4. Seguir [el proceso SDD](docs/sdd-workflow.md).
5. Revisar [la especificación aprobada](specs/001-catalogo/spec.md).
6. Consultar [la trazabilidad y el estado real](specs/001-catalogo/traceability.md).
7. Consultar los [campos técnicos por categoría](specs/001-catalogo/category-data.md).
8. Reutilizar las [plantillas de spec, plan y tareas](docs/templates/spec-template.md).
9. Consultar los [defaults adoptados](docs/resolved-defaults.md).
10. Consultar el [plan técnico aprobado](specs/001-catalogo/plan.md).
11. Seguir el [backlog SDD y de implementación planificada](specs/001-catalogo/tasks.md).
12. Consultar la [revisión de la constitución técnica de referencia](docs/constitution-review.md).
13. Consultar las [convenciones de desarrollo, estructura física y Git](docs/development-conventions.md).
14. Revisar los [hallazgos y correcciones de la revisión SDD](docs/sdd-review.md).

## Qué significa «listo»

Una spec solo estará lista para planificar su implementación cuando sus reglas
sean verificables, las decisiones que bloquean su alcance estén resueltas y el
responsable del producto haya aprobado esa versión. Tener documentos o tests
que pasan no basta para declarar cumplido el producto.

Las decisiones pendientes están identificadas en el registro y no autorizan a
inventar comportamiento. Un caso de prueba diseñado no equivale a una prueba
implementada ni ejecutada.

## Alcance confirmado de la primera versión

- Categorías: mouses, monitores, laptops, teclados, tarjetas madre, procesadores,
  tarjetas de video y consolas de videojuego.
- Al lanzamiento habrá al menos una ficha publicada y revisada en cada categoría.
- Portada con productos más buscados y buscador superior. Al inicio, sin historial
  de búsquedas, el equipo elegirá manualmente los productos destacados; después,
  «más buscados» se basará en aperturas de fichas desde los resultados de búsqueda;
  cada apertura cuenta, incluso las repetidas por la misma persona.
- Filtros por categoría, una o varias marcas, precio estimado en USD, año de
  lanzamiento y características técnicas propias de la categoría.
- Orden por popularidad, relevancia de búsqueda, lanzamiento y precio; filtros activos, cantidad de
  resultados y acción para limpiarlos. Tema claro u oscuro en un menú separado.
- Ficha con imagen, variantes, descripción, detalles técnicos, «Precio aproximado»
  en USD cargado manualmente, fecha de lanzamiento y pros y contras.
- Incorporación y mantenimiento manuales por el equipo.
- Votación sobre si la información de una ficha fue útil y sección de comentarios
  del producto: un voto editable por participante y ficha; identidad anónima y
  registrada disponibles; comentarios con aprobación previa de un moderador
  designado. Los defaults detallados quedaron en ADE-011 a ADE-014; privacidad
  legal por mercado sigue como gate de lanzamiento.
- Registro opcional: se podrá votar y comentar también sin cuenta, como anónimo.
- Los comentarios requieren aprobación del equipo antes de publicarse.
- La interfaz y los contenidos dirigidos al público estarán en español.
- Vocación de cobertura amplia y sin limitar el catálogo a marcas seleccionadas.

## Fuera del alcance de la primera versión

- Comparación de productos lado a lado en una tabla.

## Estado de la planificación

- Baseline inicial aprobada el 2026-10-26 y revisión correctiva aprobada al
  solicitar aplicar el plan: spec v0.21, plan v0.4 y decisiones ADE-001 a ADE-023.
- Los 47 criterios CAT-CA tienen cobertura en 46 escenarios CAT-CP; son diseños,
  no pruebas implementadas ni ejecutadas.
- El backlog detallado está en `specs/001-catalogo/implementation-backlog.md`;
  todas las tareas están pendientes y no representan implementación realizada.
- Las versiones de Django, Python, PostgreSQL y herramientas se revalidarán antes
  de implementar. Los gates de hosting, legal/privacidad y marca siguen antes de
  producción/publicación, según aplique.

El [registro de baseline](docs/baseline.md) conserva el alcance y la aprobación.
La aprobación de la SDD permite usar el backlog solo tras una instrucción de
implementación. La instrucción vigente sigue limitada a documentación SDD.

El producto no tiene código funcional, pruebas ejecutables ni despliegue. La SDD
está terminada como baseline aprobada; esto no afirma que el producto esté construido.
