# CAT — Catálogo público y mantenimiento editorial

Versión: 0.20. Estado: **baseline aprobada el 2026-10-26**.
Implementación: **no autorizada**. Ver [`docs/baseline.md`](../../docs/baseline.md).
Fuentes: `docs/product-vision.md`, decisiones DEC-001 a DEC-024 y decisiones
delegadas ADE-001 a ADE-019 de `docs/decisions.md`.

## Objetivo

Permitir descubrir y consultar dispositivos de ocho categorías con información
técnica, editorial y de precio, mantenida manualmente por un equipo. Permitir
que los visitantes indiquen si esa información les fue útil y comenten el producto.

Esta especificación define el contrato aprobado para el MVP. Las decisiones
diferidas de operación no autorizan a inventar comportamiento fuera de estos
requisitos.

## Requisitos funcionales aprobados

| ID | Comportamiento solicitado | Fuente | Criterios asociados |
|---|---|---|---|
| CAT-RF-001 | Mostrar productos más buscados según aperturas de fichas desde búsquedas internas durante los últimos 30 días; al no haber actividad válida, usar destacados manuales. Cada apertura repetida suma. | DEC-003 y DEC-015 a DEC-019; ADE-002 | CAT-CA-012, 013 y 018. |
| CAT-RF-002 | Permitir encontrar productos mediante un buscador superior. | DEC-003; ADE-003 | CAT-CA-019 define campos, normalización, límite y orden. |
| CAT-RF-003 | Filtrar por categoría, marcas, precio USD, año y atributos técnicos de la categoría. | DEC-003, DEC-011; ADE-004, ADE-007 | CAT-CA-004, 005 y 020 a 022; diccionarios en `category-data.md`. |
| CAT-RF-004 | Mostrar imagen y descripción inicial del producto. | DEC-004; ADE-008, ADE-009 | CAT-CA-026 y 029; autorización de imagen verificable antes de publicar. |
| CAT-RF-005 | Mostrar variantes de colores o modelos. | DEC-004; ADE-006 | CAT-CA-023 fija identidad y diferencias técnicas. |
| CAT-RF-006 | Mostrar detalles técnicos correspondientes a la categoría y variante. | DEC-004, DEC-007; ADE-006, ADE-007 | CAT-CA-023 y 024. |
| CAT-RF-007 | Mostrar el importe cargado manualmente bajo «Precio aproximado», en USD. | DEC-004, DEC-006, DEC-013; ADE-004, ADE-006 | CAT-CA-010, 023 y 027. Fuente y método del precio quedan a cargo del equipo al cargarlo. |
| CAT-RF-008 | Mostrar fecha de lanzamiento conservando la precisión conocida. | DEC-004; ADE-004 | CAT-CA-028. |
| CAT-RF-009 | Mostrar pros y contras del producto como juicio editorial sustentado. | DEC-004; ADE-008, ADE-009 | CAT-CA-026 y 029. |
| CAT-RF-010 | Permitir al equipo introducir y mantener manualmente los datos con revisión, auditoría y revisión anual de fichas activas. | DEC-005; ADE-005, ADE-009 | CAT-CA-025, 026 y 040. |
| CAT-RF-011 | Incluir ocho categorías, cada una con al menos una ficha revisada al lanzamiento; sin cuota adicional. | DEC-007, DEC-022, DEC-023; ADE-005, ADE-007, ADE-009 | CAT-CA-017, 025 y 026. |
| CAT-RF-012 | Permitir un voto editable por identidad y producto sobre la utilidad de la información; mostrar resultados separados. | DEC-008, DEC-009, DEC-020; ADE-011, ADE-012 | CAT-CA-014, 030 y 031. |
| CAT-RF-013 | Permitir comentarios anónimos o con cuenta sujetos a aprobación previa. | DEC-008 a DEC-010; ADE-011, ADE-013 | CAT-CA-001 a 003, 031 a 033. |
| CAT-RF-014 | Ofrecer registro/inicio de sesión opcionales y recuperación de acceso. | DEC-009; ADE-014 | CAT-CA-034 y 035; revisión legal de privacidad queda como gate público PND-020. |
| CAT-RF-015 | Permitir que el Moderador designado modere comentarios; pendientes/rechazados no son públicos. | DEC-010, DEC-021; ADE-005, ADE-013 | CAT-CA-001 a 003, 015, 016 y 033. |
| CAT-RF-016 | Ofrecer órdenes por más buscados, lanzamiento y precio; con búsqueda textual, ofrecer además «Relevancia». | DEC-011; ADE-002 a ADE-004 | CAT-CA-006, 018, 019 y 022. |
| CAT-RF-017 | Mostrar filtros activos y conteo, permitir limpiar filtros. | DEC-011; ADE-004 | CAT-CA-007, 008, 020 a 022. |
| CAT-RF-018 | Permitir tema claro u oscuro desde menú separado, con preferencia persistente local. | DEC-011; ADE-015 | CAT-CA-009 y 036. |
| CAT-RF-019 | Mostrar estados diferenciados de carga, error, vacío y dato no disponible en las vistas públicas correspondientes. | ADE-010 | CAT-CA-041. |

### Criterio inicial de portada (CAT-RF-001)

- **CAT-CA-012:** Mientras no haya aperturas válidas de fichas desde resultados
  internos en la ventana móvil de 30 días, el sistema deberá mostrar los productos
  publicados elegidos manualmente como destacados.

El Editor puede proponer destacados y el Revisor de catálogo puede publicarlos.
La señal parte de la búsqueda interna (DEC-016). Solo cuenta el producto cuya
ficha abre la persona desde los resultados (DEC-017); cada apertura cuenta,
incluso si la persona ya la abrió antes (DEC-018). Solo se cuentan aperturas en
los últimos 30 días (DEC-019). ADE-002 define exclusión de rastreadores conocidos,
desempate y transición entre destacados manuales y orden por actividad. No
presentar los destacados manuales como si fueran datos estadísticos.

- **CAT-CA-013:** Cuando una persona abra la ficha de un producto desde los
  resultados de una búsqueda interna, el sistema deberá sumar esa apertura al
  conteo de ese producto. Los demás productos mostrados en los resultados no
  deberán recibir un incremento por esa búsqueda.

## Navegación y apariencia confirmadas

La barra lateral incluye categoría, marca con selección de una o varias, precio
estimado mínimo y máximo en USD, año de lanzamiento y filtros técnicos adaptados
a la categoría. Los controles técnicos iniciales aprobados como base son:

| Categoría | Filtros técnicos de referencia |
|---|---|
| Monitores | Tamaño, resolución, frecuencia de actualización |
| Laptops | Procesador, memoria RAM, almacenamiento |
| Mouses | Conexión por cable o inalámbrica |
| Tarjetas de video | Memoria de video |

Los filtros técnicos por categoría están definidos en `category-data.md`
según ADE-007. La lista de filtros es explícita; otros atributos se pueden mostrar
como especificaciones, pero no se vuelven filtrables sin una nueva decisión.

Los órdenes disponibles serán «Más buscados», «Lanzamiento más reciente»,
«Precio: menor a mayor» y «Precio: mayor a menor». CAT-CA-018 y CAT-CA-022
definen la métrica, ausencias y desempates.

La interfaz mostrará los filtros activos, la cantidad de resultados y la acción
«Limpiar filtros». El tratamiento de rangos inválidos, ausencias y reinicio se
define en CAT-CA-020 a CAT-CA-022. Claro y oscuro estarán en un menú separado.

### Criterios iniciales de navegación

Derivados de DEC-011 y concretados por ADE-003, ADE-004, ADE-007 y ADE-015.

- **CAT-CA-004 (CAT-RF-003):** Cuando una persona explore el catálogo, el sistema
  deberá ofrecer filtros por categoría, marca con selección de una o varias,
  precio estimado mínimo y máximo en USD y año de lanzamiento.
- **CAT-CA-005 (CAT-RF-003):** Cuando se seleccione una categoría, el sistema
  deberá ofrecer los filtros técnicos que le correspondan según su diccionario,
  sin mostrar como propios los exclusivos de otra categoría.
- **CAT-CA-006 (CAT-RF-016):** Cuando se consulten resultados, el sistema deberá
  ofrecer encima de ellos los cuatro órdenes definidos en esta sección. Si hay
  una búsqueda textual, «Relevancia» será el orden seleccionado por defecto y
  aparecerá como opción adicional.
- **CAT-CA-007 (CAT-RF-017):** Cuando una persona active «Limpiar filtros», el
  sistema deberá desactivar todos los filtros del catálogo y actualizar los
  resultados, conservando búsqueda y orden (CAT-CA-022).
- **CAT-CA-008 (CAT-RF-017):** Mientras haya filtros aplicados, el sistema deberá
  identificarlos visualmente y mostrar la cantidad total de resultados de la
  consulta, diferenciada de la cantidad visible en una página cuando haya paginación.
- **CAT-CA-009 (CAT-RF-018):** Cuando una persona elija claro u oscuro en el menú
  de apariencia, el sistema deberá aplicar el tema elegido sin cambiar los filtros.

## Participación confirmada y límites por precisar

El registro es opcional. Una visita sin cuenta usa el token anónimo descrito en
CAT-CA-031; no se promete anonimato técnico absoluto ni deduplicación de personas.

Los comentarios requieren aprobación previa del equipo, independientemente de
que el autor tenga una cuenta. Recibir un comentario no equivale a publicarlo.
La revisión previa no se extiende a los votos. Los aportes anónimos no se vinculan
automáticamente a una cuenta, incluso si después se registra (CAT-CA-031/035).

La votación tiene dos respuestas de utilidad: «sí» y «no». Su objeto es la
información de la ficha. No define una valoración por estrellas del dispositivo
ni modifica por sí misma la métrica de productos más buscados.

- **CAT-CA-014:** Cuando una persona con cuenta o anónima vote la utilidad de la
  información de un producto, el sistema deberá guardar una sola respuesta activa
  de esa persona para ese producto. Si vuelve a votar, deberá reemplazar su
  respuesta anterior, sin contar ambas.

Los conteos se muestran como votos «Útil» y «No útil», sin puntuación del
dispositivo (CAT-CA-030). La identidad anónima está limitada a un navegador/token.

Los comentarios pertenecen a un producto. El MVP no ofrece hilos, archivos,
edición por el autor, reportes ni notificaciones por correo (ADE-013).

### Criterios iniciales de moderación (CAT-RF-015)

Derivados de DEC-010 y precisados por ADE-013. «Recibido» presupone que el envío
cumple el límite de 1–2.000 caracteres y el límite de frecuencia.

- **CAT-CA-001:** Cuando el sistema reciba un comentario de un visitante con
  cuenta o anónimo, deberá dejarlo pendiente de aprobación, sin publicarlo.
- **CAT-CA-002:** Mientras un comentario esté pendiente de aprobación, el sistema
  deberá excluirlo de los comentarios visibles en las consultas públicas.
- **CAT-CA-003:** Cuando un integrante del equipo con permiso de moderación
  apruebe un comentario pendiente de un producto publicado, el sistema deberá
  cambiarlo a aprobado y hacerlo visible en la sección de comentarios del producto.
- **CAT-CA-015:** Cuando se asigne el permiso de moderación, el sistema deberá
  permitir que la persona designada apruebe comentarios pendientes.
- **CAT-CA-016:** Si una persona sin permiso de moderación intenta aprobar un
  comentario pendiente, el sistema deberá rechazar la operación y mantenerlo sin
  publicar.

Los escenarios documentales están en [acceptance.md](acceptance.md). No son
tests implementados ni ejecutados. El rol designado está confirmado por DEC-021.
El acceso se asigna por rol; el Moderador puede aprobar, rechazar o retirar la
aprobación. No puede editar el texto del autor.

## Categorías

Mouses, monitores, laptops, teclados, tarjetas madre, procesadores, tarjetas de
video y consolas de videojuego. Cada categoría tendrá un diccionario de atributos
propio, con nombre, significado, tipo, unidad, valores admitidos, obligatoriedad,
reglas de validación, fuente y comportamiento cuando falte el dato.

## Campo de precio confirmado

La ficha tendrá un campo «Precio aproximado» en USD. El equipo introducirá y
actualizará el importe manualmente. La etiqueta fue elegida por el agente entre
las alternativas autorizadas por el responsable en DEC-013.

Las fuentes y el método para obtener el importe se decidirán al llenar los datos.
La IA no deberá inventar precios ni implementar cálculos, promedios, integraciones
o campos obligatorios de procedencia y fecha para resolver esa decisión editorial.
La falta de un método acordado ahora no bloquea el diseño del campo.

- **CAT-CA-010 (CAT-RF-007):** Cuando se consulte una ficha con un importe cargado
  por el equipo, el sistema deberá mostrar ese importe identificado como
  «Precio aproximado» y expresado en USD.

La validación y tratamiento de ausencia se fijan en CAT-CA-023/027. El precio
puede faltar; el sistema no completa ni estima automáticamente su valor. El
equipo conserva la elección de fuente y método al cargarlo según DEC-013.

## Requisitos no funcionales iniciales

| ID | Requisito | Fuente | Criterios y condiciones |
|---|---|---|---|
| CAT-RNF-001 | La interfaz, mensajes y contenidos editoriales públicos de la primera versión estarán en español. | DEC-014 | CAT-CA-011, 019 a 041. |
| CAT-RNF-002 | Las vistas públicas y de equipo apuntarán a WCAG 2.2 AA y serán utilizables por teclado y a 360 CSS px sin scroll horizontal de página. | ADE-010 | CAT-CA-037; requiere revisión automatizada y manual al implementar. |
| CAT-RNF-003 | Las vistas públicas cumplirán metas Core Web Vitals en el percentil 75 por dispositivo cuando exista tráfico suficiente. | ADE-010 | CAT-CA-038; hosting y medición operativa son previos al despliegue. |
| CAT-RNF-004 | Los datos personales y aportes del público se protegerán con minimización de datos, autorización en servidor y salida segura de contenido. | ADE-011 a ADE-014 | CAT-CA-031, 033 a 035 y 039; política legal por mercado es gate PND-020. |

- **CAT-CA-011 (CAT-RNF-001):** Cuando una persona use la primera versión del
  sitio, el sistema deberá presentar en español la navegación, controles,
  mensajes y contenidos editoriales publicados. Nombres de marcas, modelos y
  unidades técnicas pueden conservar su grafía propia.
- **CAT-CA-017 (CAT-RF-011):** Cuando el equipo prepare el lanzamiento, el sistema
  deberá tener al menos un producto publicado y revisado para cada una de las
  ocho categorías acordadas.

## Contratos funcionales concretados por delegación

Los criterios CAT-CA-018 a CAT-CA-041 aplican las decisiones delegadas ADE-001 a
ADE-016 y las precisiones ADE-018/ADE-019. ADE-017 gobierna el diseño técnico,
no el comportamiento de producto. Son defaults de diseño y cierres técnicos,
no respuestas textuales anteriores. El responsable aprobó estos defaults junto
con la baseline; su origen delegado queda conservado en el registro de decisiones.

### Descubrimiento, búsqueda y filtros

- **CAT-CA-018 (CAT-RF-001):** Cuando exista al menos una apertura válida de ficha
  desde resultados internos dentro de la ventana UTC exacta `(ahora - 30 días,
  ahora]`, la portada deberá ordenar productos publicados por aperturas
  descendentes, nombre normalizado y slug. Cada apertura cuenta, aunque la misma
  persona vuelva a abrir la ficha. No se almacenan identidad, IP ni user-agent.
  Si no existe ninguna, deberá mostrar los destacados manuales vigentes. No se
  contarán impresiones, navegación directa ni rastreadores conocidos.
- **CAT-CA-019 (CAT-RF-002, CAT-RF-016):** Cuando se envíe una consulta de hasta 100 caracteres,
  el sistema deberá buscar coincidencias parciales sin distinguir mayúsculas ni
  diacríticos en marca, modelo y nombre. Con término, ordenará exactas antes que
  prefijos y estos antes que coincidencias internas; el selector ofrecerá
  «Relevancia» como orden inicial, además de las cuatro opciones de CAT-RF-016.
  Cuando la persona elija otro orden, este prevalecerá y relevancia servirá de
  desempate. Una consulta vacía mostrará el catálogo con orden inicial «Más
  buscados». Se mostrarán 24 resultados por página y la consulta/filtros/orden
  quedarán en parámetros GET. Una consulta de más de 100 caracteres se rechazará
  con mensaje en español y no ejecutará búsqueda ni devolverá resultados.
- **CAT-CA-020 (CAT-RF-003):** Cuando se apliquen filtros de grupos distintos,
  el sistema deberá exigir que el producto coincida con todos; dentro del grupo
  de marcas, bastará coincidir con una marca seleccionada. Los rangos de precio
  y año incluirán ambos extremos; los productos sin ese dato no coincidirán con
  el filtro correspondiente.
- **CAT-CA-021 (CAT-RF-003, CAT-RF-017):** Si el precio mínimo supera al máximo,
  el sistema deberá mostrar un error y no aplicar ninguno de los dos límites; los
  demás filtros válidos sí se aplicarán y se mostrarán con el conteo actualizado.
- **CAT-CA-022 (CAT-RF-003, CAT-RF-017):** Cuando cambie la categoría, el sistema
  deberá limpiar solo los filtros técnicos incompatibles y explicar cuáles quitó.
  Cuando se elija «Limpiar filtros», deberá quitar categoría, marca, precio, año
  y filtros técnicos, pero conservar el término de búsqueda y el orden actual.
  El conteo mostrado será el total antes de paginar. En cualquier orden, los datos
  ausentes irán después de los conocidos; los empates se resolverán por nombre
  normalizado y slug.

### Identidad y calidad del catálogo

- **CAT-CA-023 (CAT-RF-005, CAT-RF-006, CAT-RF-007):** Cuando una ficha tenga
  variantes del mismo producto, el sistema deberá identificar la seleccionada y
  mostrar solo sus atributos, imagen y precio propios; no heredará valores
  incompatibles. Diferencias de generación, plataforma o compatibilidad que
  cambien la identidad técnica deberán tener fichas separadas.
- **CAT-CA-024 (CAT-RF-006):** Cuando un atributo numérico se use en filtros u
  orden, el sistema deberá guardar valor y unidad normalizados. Un valor ausente
  deberá distinguirse de cero, «No corresponde» y «Pendiente de verificar»; solo
  los valores conocidos participarán en filtros y órdenes.
- **CAT-CA-025 (CAT-RF-010, CAT-RF-011):** Cuando un Editor envíe una ficha nueva
  o una corrección publicada a revisión, el contenido público deberá permanecer
  en su versión anterior o no publicado hasta que un Revisor de catálogo la
  publique. Si el borrador cambió desde que el Editor lo abrió, el sistema deberá
  rechazar el guardado obsoleto sin sobrescribir la versión más reciente. Cuando
  un Revisor retire una ficha, esta dejará de aparecer en listados públicos, su
  URL directa mostrará estado no disponible y no aceptará nuevos votos o
  comentarios. El sistema deberá registrar autor, revisor, fecha y acción.
- **CAT-CA-026 (CAT-RF-010, CAT-RF-011):** Cuando un Revisor publique una ficha,
  el sistema deberá comprobar identidad, descripción en español, imagen con texto
  alternativo y permiso verificado, al menos un pro y un contra editoriales
  sustentados, fuentes internas y los atributos técnicos obligatorios de su
  categoría definidos en `category-data.md` (ADE-018). Un dato obligatorio
  desconocido o pendiente de verificar bloqueará la publicación. Si fuentes
  técnicas fiables se contradicen, el Revisor deberá resolver y registrar el
  criterio antes de publicar. Precio y fecha de lanzamiento podrán faltar y se
  mostrarán como no disponibles; nunca se completarán por conjetura.
- **CAT-CA-027 (CAT-RF-007):** Cuando exista precio, el sistema deberá mostrarlo
  como «Precio aproximado» en USD, con valor positivo de hasta dos decimales y
  formato español. Si falta, mostrará «No disponible»; no lo tratará como cero,
  no coincidirá con filtros de precio y quedará al final al ordenar por precio.
  Solo mostrará el precio de la revisión pública vigente; no expondrá historial
  de precios ni afirmará que el importe siga vigente. Fuentes y método editorial
  serán los elegidos por el equipo al cargarlo.
- **CAT-CA-028 (CAT-RF-008):** Cuando exista fecha de lanzamiento, el sistema
  deberá conservar su precisión original (año, mes o día) y mostrar solo esa
  precisión. Si se filtra por año, una fecha parcial coincidirá por su año
  conocido; sin fecha, no coincidirá y quedará al final al ordenar.
- **CAT-CA-029 (CAT-RF-009):** Cuando se publique un pro o contra, deberá estar
  redactado en español, contextualizado como valoración editorial y respaldado
  por material de revisión fiable. Los hechos técnicos se basarán preferentemente
  en fuente oficial del fabricante; si no existe, se registrará internamente una
  fuente técnica reconocida. La imagen solo se publicará con procedencia y permiso
  de uso verificados.

- **CAT-CA-040 (CAT-RF-010):** Mientras una ficha permanezca activa, el equipo
  deberá revisar su contenido al menos una vez en cada período de 12 meses y
  cuando reciba una corrección técnica verificada. El sistema deberá registrar
  quién realizó cada revisión y cuándo. La revisión es manual; no exige aviso
  automático ni garantiza que un precio aproximado siga vigente.

### Votos, comentarios y cuentas

- **CAT-CA-030 (CAT-RF-012):** Cuando haya votos para una ficha, el sistema deberá
  mostrar por separado los conteos «Útil» y «No útil». Un voto nuevo de una
  identidad ya reconocida para ese producto reemplazará el anterior; una
  corrección editorial no reiniciará esos votos. Los votos no cambiarán la
  popularidad del producto. Cada identidad podrá emitir como máximo 60 votos
  por hora. Ante cambios simultáneos de una identidad, se conservará un único
  voto y la operación confirmada en último lugar según el orden de transacción
  determinará su valor vigente. No se aceptarán votos sobre fichas retiradas.
- **CAT-CA-031 (CAT-RF-012, CAT-RF-013):** Cuando una visita sin cuenta participe,
  el sistema deberá usar un token aleatorio de primera parte en una cookie
  `Secure`, `HttpOnly` y `SameSite=Lax`, con vigencia de 12 meses, sin usar la IP
  como identidad ni crear huella digital. La persona recibirá información visible
  sobre la cookie antes de participar.
  La interfaz deberá mostrar «Anónimo». Si se borra la cookie o cambia de
  navegador, podrá generarse otra identidad; el sistema no afirmará que deduplica
  personas reales y no fusionará aportes anónimos al iniciar sesión o registrarse.
- **CAT-CA-032 (CAT-RF-013):** Si el texto de un comentario, después de recortar
  espacios, tiene menos de 1 o más de 2.000 caracteres, el sistema deberá
  rechazarlo sin guardarlo y mostrar un error asociado al formulario.
- **CAT-CA-033 (CAT-RF-013, CAT-RF-015):** Cuando se acepte un comentario válido,
  quedará pendiente; solo el Moderador designado podrá aprobarlo, rechazarlo o
  retirar su aprobación. Solo los aprobados serán públicos y se ordenarán del
  más reciente al más antiguo. No habrá hilos, adjuntos, edición por el autor ni
  notificaciones por correo en la primera versión. Cada identidad podrá enviar
  como máximo cinco comentarios por hora; al excederlo se rechazará el envío y se
  informará el límite. Solo se aceptarán comentarios para productos publicados.
- **CAT-CA-034 (CAT-RF-014):** Cuando una persona se registre, el sistema deberá
  solicitar correo, contraseña y alias público, verificar el correo y permitir
  recuperar acceso por enlace. El correo nunca se mostrará en contenido público.
  El registro seguirá siendo opcional para votar y comentar.
- **CAT-CA-035 (CAT-RF-014):** Cuando una persona elimine su cuenta, el sistema
  deberá eliminar sus votos y comentarios pendientes, y conservar los comentarios
  aprobados solo bajo el nombre «Anónimo». Los aportes enviados antes sin cuenta
  no se vincularán automáticamente a la nueva cuenta. La política final de
  retención y privacidad requiere revisión para los mercados de lanzamiento.

### Apariencia y calidad de servicio

- **CAT-CA-036 (CAT-RF-018):** En la primera visita, el sistema deberá usar la
  preferencia de apariencia del dispositivo. Una selección manual de claro u
  oscuro prevalecerá y se guardará solo en ese navegador; cambiar el tema no
  modificará búsqueda, filtros ni orden.
- **CAT-CA-037 (CAT-RNF-002):** En vistas públicas y de equipo, toda función deberá
  ser operable con teclado, tener foco visible, nombre accesible y errores
  asociados al control; el producto apuntará a WCAG 2.2 nivel AA. A un ancho de
  360 CSS px no habrá desplazamiento horizontal de la página.
- **CAT-CA-038 (CAT-RNF-003):** Cuando haya tráfico de campo suficiente, las vistas
  públicas deberán alcanzar en percentil 75, por separado en móvil y escritorio,
  LCP ≤ 2,5 s, INP ≤ 200 ms y CLS ≤ 0,1 en una ventana de 28 días. Antes de contar
  con tráfico suficiente, el resultado se registrará como no medible, no como
  aprobado.
- **CAT-CA-039 (CAT-RNF-004):** Cuando una solicitud intente editar fichas o
  moderar comentarios, el servidor deberá exigir la sesión y el rol correspondiente;
  ocultar un botón en la interfaz no bastará. El sistema no deberá exponer correos,
  contraseñas, comentarios pendientes o rechazados a vistas públicas, ni interpretar
  como HTML el texto enviado por participantes. Los datos usados en desarrollo y
  pruebas serán ficticios o anonimizados.
- **CAT-CA-041 (CAT-RF-019):** Cuando se carguen datos, falle una consulta,
  una búsqueda/lista no tenga resultados o un campo opcional carezca de valor,
  el sistema deberá mostrar el estado correspondiente en español. Los estados
  de carga, error, vacío y dato no disponible deberán distinguirse visualmente;
  un dato ausente no se representará como cero ni como una lista vacía.

## Límites editoriales del contrato

- El precio aproximado no se presentará como garantía de disponibilidad o costo
  de compra en cualquier país; el campo acordado se describe en la sección anterior.
- Un dato desconocido no se representará como cero, falso o «no compatible».
- Una variante que cambie especificaciones tendrá datos propios identificables.
- Los pros y contras se distinguirán de las especificaciones del fabricante.
- La información incompleta no se completará automáticamente con texto inventado.

Las reglas anteriores se formalizaron en CAT-CA-023 a CAT-CA-029. Ningún criterio
autoriza inferir o inventar información faltante.

## Fuera del alcance de la primera versión

Por DEC-012, no se incluirá un comparador de productos lado a lado ni un flujo
para seleccionar varios productos con ese propósito. Los filtros y las fichas
individuales permanecen en el alcance confirmado. Una futura incorporación del
comparador requerirá una nueva decisión de alcance; no se planifica ahora.
Por DEC-014, una interfaz o contenidos editoriales en otro idioma también quedan
fuera de la primera versión. Por ADE-001, favoritos, enlaces de compra, afiliación,
ventas y pagos también quedan fuera. La automatización mediante API y categorías
adicionales se dejan para una decisión de alcance futura.

## Alcance aún por resolver

Quedan diferidos el proveedor/hosting, el presupuesto, las metas de disponibilidad
y recuperación (PND-012), la revisión legal de privacidad/cookies/derechos por
mercado (PND-020) y el nombre comercial/dominio (PND-021). PND-012 y PND-021 no
bloquean la aprobación funcional; PND-020 es gate antes del lanzamiento público.

## Disposición de casos de borde

Los casos recogidos durante el descubrimiento tienen contrato o exclusión expresa;
no quedan como una agenda abierta de decisiones:

| Caso | Disposición aprobada |
|---|---|
| Catálogo/categoría vacíos; búsqueda sin coincidencias | Estado vacío definido por CAT-CA-041; búsqueda y límites por CAT-CA-019. |
| Nombres similares, marca/región y variantes | Identidad comercial/técnica por ADE-006 y CAT-CA-023; relevancia de búsqueda por CAT-CA-019. |
| Dato desconocido, no aplicable o pendiente | Estados tipados y unidades de CAT-CA-024. |
| Precio ausente, viejo, contradictorio o de una variante | Precio manual aproximado sin promesa de vigencia ni historial público; precio por variante/revisión en CAT-CA-023/027 y DEC-013. |
| Fecha parcial y opiniones editoriales contextualizadas | CAT-CA-028/029. |
| Fuentes técnicas contradictorias | Resolver y registrar antes de publicar según CAT-CA-026. |
| Correcciones, guardado obsoleto y retiro de ficha | Revisión pública inmutable, rechazo de guardado obsoleto y retiro de la vista pública por CAT-CA-025. |
| Portada sin actividad y visita repetida | CAT-CA-012/013/018. |
| Voto simultáneo y voto tras corregir ficha | Unicidad, reemplazo atómico y persistencia según CAT-CA-030. |
| Comentario vacío/largo, moderación, retirada o edición | Validación y aprobación en CAT-CA-032/033; reportes, hilos, adjuntos y edición por autor están fuera de alcance. |
| Participación anónima, registro posterior, logout y cookie borrada | Cookie limitada y no fusión de aportes según CAT-CA-031/034/035. |
| Rangos inválidos, cambio de categoría, marcas múltiples, paginación y tema | CAT-CA-020/021/022/036. |
| Revisión anual y estados de interfaz | CAT-CA-040/041. |

## Condiciones de cierre documental

- Resolver todas las decisiones que bloquean los requisitos del alcance elegido.
- Escribir criterios EARS con IDs y resultados verificables para cada RF.
- Definir los requisitos no funcionales con medidas y contexto de verificación.
- Completar los contratos de información y sus ejemplos.
- Resolver los hallazgos bloqueantes de la revisión.
- Obtener aprobación explícita de versión y alcance del responsable del producto
  (**completado** para la versión 0.20; ver `docs/baseline.md`).

## Estado de verificación

No hay implementación ni tests ejecutables. La especificación está aprobada como
contrato de comportamiento, pero el producto aún no puede declararse cumplido.
Las tareas futuras están en `implementation-backlog.md` y siguen pendientes.

## Historial de cambios

| Versión | Cambio de comportamiento o alcance | Requisitos afectados | Aprobación |
|---|---|---|---|
| 0.17 | Aclara que el mínimo de lanzamiento es una ficha revisada por categoría, sin cuota total adicional de productos o variantes ni promesa de cobertura exhaustiva. | CAT-RF-011 | DEC-023 confirmada. |
| 0.18 | Incorpora contratos para búsqueda, filtros, catálogo editorial, cuentas, votos, comentarios y requisitos no funcionales a partir de ADE-001 a ADE-016. | CAT-RF-001 a CAT-RF-018; CAT-RNF-001 a CAT-RNF-004 | Defaults delegados; después adoptados en la baseline. |
| 0.19 | Define campos mínimos de publicación por categoría y precisión exacta/retención de la ventana de popularidad. | CAT-CA-018, CAT-CA-026 | ADE-018/ADE-019; baseline aprobada 2026-10-26. |
| 0.20 | Expresa como criterios la revisión anual ya adoptada en ADE-009 y los estados de interfaz de ADE-010. | CAT-RF-010, CAT-RF-019; CAT-CA-040/041 | Alineación con defaults ya adoptados; no cambia el alcance aprobado. |
