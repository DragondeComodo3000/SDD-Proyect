# Visión de producto

Versión: 1.0. Estado: visión aprobada como parte de la baseline el 2026-10-26.
Fuente: conversación con el responsable del producto.

## Problema y propósito confirmados

Reunir información de dispositivos y elementos gamer para ayudar a elegir con
mayor precisión y para satisfacer la curiosidad de quienes se interesan por
tecnología. La cobertura buscará crecer entre categorías y marcas; no se ha
prometido disponer de todos los productos del mercado desde el lanzamiento.

## Personas y necesidades

| Persona | Necesidad confirmada | Resultado buscado |
|---|---|---|
| Comprador | Entender productos y sus detalles técnicos | Contar con información para decidir |
| Aficionado o curioso | Explorar dispositivos e información técnica | Aprender y descubrir productos |
| Equipo editorial | Introducir y actualizar la información manualmente | Mantener el catálogo |

Por ADE-001 no se incluirán ventas, pagos, favoritos, enlaces de compra,
afiliación ni recomendaciones automáticas en la primera versión.

## Recorrido confirmado hasta el momento

1. La persona llega a una portada que destaca los productos más buscados.
2. Puede usar un buscador situado en la parte superior.
3. Usa una barra lateral para filtrar por categoría, una o varias marcas, rango
   de precio estimado en USD, año de lanzamiento y características técnicas de
   la categoría. Puede consultar los filtros activos, limpiar los filtros y ver
   la cantidad de resultados. Encima de estos, puede elegir su orden.
4. Al abrir un producto, encuentra imagen, variantes de color o modelo,
   descripción inicial, detalles técnicos, precio estimado, fecha de lanzamiento
   y pros y contras.
5. Puede indicar si la información del producto le resultó útil o no y expresarse
   en una sección de comentarios asociada al producto.

Los detalles de búsqueda, filtros, popularidad y participación se concretaron
como decisiones delegadas ADE-002 a ADE-015 y criterios CAT-CA-018 a CAT-CA-041.
La votación evalúa la utilidad de la información; no es una calificación del
dispositivo.

Los órdenes disponibles son más buscados, lanzamiento más reciente y precio
ascendente o descendente; cuando hay una búsqueda, «Relevancia» se ofrece como
orden inicial. La apariencia clara u oscura se elige en un menú separado de los
filtros del catálogo.

Los filtros técnicos iniciales para las ocho categorías están detallados en
`specs/001-catalogo/category-data.md`; otros atributos se muestran como
especificaciones y no se vuelven filtros sin una nueva decisión.

Al lanzar el sitio sin aperturas válidas en los últimos 30 días, el equipo elegirá
manualmente los destacados. Con actividad válida, se ordenarán las aperturas de
fichas desde resultados internos, incluyendo repeticiones, durante la ventana
móvil de 30 días; no cuentan impresiones ni navegación directa. Se excluyen
rastreadores conocidos y los empates se resuelven por nombre normalizado y slug.

La participación está confirmada para la primera versión. El registro será
opcional: se podrá votar y comentar tanto con cuenta como sin registrarse, bajo
una identidad anónima mediante cookie limitada al navegador, sin promesa de
identificar personas reales ni fusionar aportes al crear una cuenta. Cada identidad
tendrá un voto editable por producto. El registro usa correo privado y alias
público. La comparación de productos lado a lado queda fuera de la primera versión
por decisión del responsable; favoritos también queda fuera por ADE-001.

Todos los comentarios, de participantes registrados y anónimos, deberán pasar
por aprobación del equipo antes de publicarse. Un comentario recibido no será
público mientras espere esa aprobación. Solo el Moderador designado puede aprobar,
rechazar o retirar aprobación. Comentarios son texto plano, sin hilos, adjuntos ni
edición por autor; no hay notificaciones por correo en el MVP. El registro de roles
y el flujo editorial están detallados en la spec.

## Catálogo inicial confirmado

| Categoría | Incluida en la primera versión |
|---|---|
| Mouses | Sí |
| Monitores | Sí |
| Laptops | Sí |
| Teclados | Sí |
| Tarjetas madre | Sí |
| Procesadores | Sí |
| Tarjetas de video | Sí |
| Consolas de videojuego | Sí |

La amplitud de categorías no fija todavía una cantidad mínima de fichas por
categoría más allá de la condición de lanzamiento: cada una deberá tener al menos
una ficha revisada por el equipo. Esto es un mínimo de lanzamiento, no una promesa
de cubrir todos los productos de cada categoría. Tampoco implica que todas
compartan los mismos atributos técnicos.

## Operación y precios confirmados

El equipo introducirá, mantendrá y actualizará los datos manualmente. Una API
podría evaluarse posteriormente si se encuentra una adecuada; no es una
dependencia de la primera versión.

La audiencia buscada es general e internacional. La ficha tendrá un campo
«Precio aproximado» en dólares estadounidenses (USD), cargado manualmente por el
equipo. El agente eligió esa etiqueta entre las dos alternativas permitidas por
el responsable. El equipo definirá las fuentes y el criterio de estimación al
llenar los datos; esa decisión editorial no bloquea la planificación del campo.
No se exige ahora un algoritmo de estimación ni campos adicionales de fuente o
fecha del precio. Mostrar USD no implica garantizar un precio universal de compra.

## Idioma confirmado

La primera versión se ofrecerá solo en español: interfaz, mensajes y contenidos
editoriales dirigidos al público. Se conservan nombres propios, marcas, modelos
y unidades técnicas cuando corresponda. Una traducción futura requerirá una nueva
decisión de alcance; la audiencia internacional no implica multilingüismo inicial.

## Principios editoriales adoptados

- Separar hechos técnicos, precios de referencia y opiniones editoriales.
- Asociar información publicada con fuentes y fechas de revisión.
- Mostrar explícitamente la falta de un dato, sin completarlo con una conjetura.
- Distinguir una variante cosmética de un modelo con especificaciones diferentes.
- Hacer visible el carácter estimado del precio y el contexto de los pros y contras.

Estos principios quedan concretados en CAT-CA-023 a CAT-CA-029 y en el diccionario
de categoría aprobado; no sustituyen esos contratos.

## Éxito todavía por concretar

La baseline fija los objetivos funcionales, de accesibilidad y de rendimiento
descritos en la spec. Métricas de adopción o satisfacción comercial quedan fuera
del contrato funcional inicial y podrán definirse al preparar la evaluación de
producto, sin alterar estos requisitos.
