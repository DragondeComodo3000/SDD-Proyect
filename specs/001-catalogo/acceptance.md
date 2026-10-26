# Escenarios de aceptación CAT

Versión: 1.2. Estado: escenarios de diseño de la baseline correctiva aprobada.
No hay pruebas implementadas ni ejecutadas. `spec.md` es la fuente del
comportamiento esperado; estos escenarios describen cómo verificarlo.

## CAT-CP-001 — Recepción pendiente de revisión

- Criterio: CAT-CA-001; requisito: CAT-RF-015.
- Precondición: un producto publicado admite comentarios; el contenido satisface
  las futuras reglas de validación. Ejecutar una variante con cuenta y otra sin cuenta.
- Acción: enviar un comentario nuevo sin que intervenga un moderador.
- Resultado esperado: el comentario queda pendiente de aprobación y no publicado.
- Resultado observado: no ejecutado.

## CAT-CP-002 — Exclusión de comentarios pendientes

- Criterio: CAT-CA-002; requisito: CAT-RF-015.
- Precondición: un producto tiene un comentario pendiente y otro aprobado.
- Acción: consultar sus comentarios como visitante anónimo y como usuario
  registrado sin permisos de moderación.
- Resultado esperado: ambas consultas muestran el aprobado y excluyen el pendiente;
  el texto del pendiente tampoco se entrega en la respuesta pública subyacente.
- Resultado observado: no ejecutado.

## CAT-CP-003 — Publicación tras aprobación

- Criterio: CAT-CA-003; requisito: CAT-RF-015.
- Precondición: un producto publicado tiene un comentario pendiente; quien realiza
  la acción la realiza una persona con rol de Moderador (ADE-013).
- Acción: aprobar el comentario y consultar después la sección pública del producto.
- Resultado esperado: el estado cambia a aprobado y el comentario aparece publicado.
- Resultado observado: no ejecutado.

## CAT-CP-004 — Disponibilidad de filtros generales

- Criterio: CAT-CA-004; requisito: CAT-RF-003.
- Precondición: catálogo con productos ficticios de varias categorías y marcas.
- Acción: abrir la exploración del catálogo e inspeccionar la barra lateral.
- Resultado esperado: permite seleccionar categoría, una o varias marcas,
  precio mínimo y máximo en USD y año de lanzamiento.
- Resultado observado: no ejecutado.

## CAT-CP-005 — Filtros técnicos por categoría

- Criterio: CAT-CA-005; requisito: CAT-RF-003.
- Precondición: diccionarios aprobados para las categorías usadas en el escenario.
- Acción: seleccionar monitores y después mouses.
- Resultado esperado: en monitores se ofrecen tamaño, resolución y frecuencia
  de actualización; en mouses, conexión. Los campos exclusivos de monitores no
  se presentan como atributos de mouses. La limpieza de valores al cambiar de
  categoría se comprueba en CAT-CA-021.
- Resultado observado: no ejecutado.

## CAT-CP-006 — Opciones de orden

- Criterio: CAT-CA-006; requisito: CAT-RF-016.
- Precondición: consulta del catálogo con resultados.
- Acción: inspeccionar el control de orden situado encima de los resultados.
- Resultado esperado: ofrece más buscados, lanzamiento más reciente y precio
  ascendente y descendente. La precedencia y desempates se comprueban en
  CAT-CP-018/022/028.
- Resultado observado: no ejecutado.

## CAT-CP-007 — Limpiar filtros

- Criterio: CAT-CA-007; requisito: CAT-RF-017.
- Precondición: catálogo con filtros activos y sin texto de búsqueda introducido.
- Acción: activar «Limpiar filtros».
- Resultado esperado: quedan desactivados todos los filtros y se actualizan los
  resultados. Se conservan la búsqueda y el orden, según CAT-CA-022.
- Resultado observado: no ejecutado.

## CAT-CP-008 — Filtros activos y cantidad de resultados

- Criterio: CAT-CA-008; requisito: CAT-RF-017.
- Precondición: catálogo ficticio con tres productos de una marca y dos de otra.
- Acción: filtrar por la marca con tres productos.
- Resultado esperado: la marca seleccionada queda identificada como filtro activo
  y la cantidad de resultados indica tres; solo esos tres productos pertenecen a
  la consulta. La paginación se cubrirá en escenarios posteriores.
- Resultado observado: no ejecutado.

## CAT-CP-009 — Tema independiente de los filtros

- Criterio: CAT-CA-009; requisito: CAT-RF-018.
- Precondición: catálogo con una marca seleccionada como filtro.
- Acción: elegir oscuro y después claro en el menú separado de apariencia.
- Resultado esperado: cada selección aplica el tema correspondiente; la marca
  continúa seleccionada y los filtros no cambian. La selección manual prevalece
  sobre la preferencia del dispositivo y persiste solo en ese navegador.
- Resultado observado: no ejecutado.

## CAT-CP-010 — Presentación del precio aproximado

- Criterio: CAT-CA-010; requisito: CAT-RF-007.
- Precondición: ficha de un producto ficticio con importe manual de 250 USD;
  el valor es exclusivamente un dato de prueba, no un precio real de mercado.
- Acción: consultar la ficha pública del producto.
- Resultado esperado: muestra la etiqueta «Precio aproximado», el importe 250
  y la moneda USD, con formato español y hasta dos decimales. La comprobación no
  exige que el equipo haya acordado una fuente o un algoritmo de estimación.
- Resultado observado: no ejecutado.

## CAT-CP-011 — Idioma público inicial

- Criterio: CAT-CA-011; requisito: CAT-RNF-001.
- Precondición: catálogo ficticio con una ficha publicada, una búsqueda sin
  resultados y un comentario pendiente de moderación.
- Acción: navegar por portada y ficha, activar filtros y provocar el estado de
  búsqueda vacía como visitante sin sesión y con una cuenta de prueba.
- Resultado esperado: navegación, controles, mensajes y texto editorial público
  aparecen en español. Marcas, modelos y unidades conservan su grafía propia.
- Resultado observado: no ejecutado.

## CAT-CP-012 — Portada al iniciar sin búsquedas

- Criterio: CAT-CA-012; requisito: CAT-RF-001.
- Precondición: historial de búsquedas vacío; dos productos ficticios publicados,
  elegidos manualmente como destacados, y un tercero no elegido.
- Acción: abrir la portada pública.
- Resultado esperado: muestra los dos publicados elegidos por el equipo y no
  presenta al tercero como destacado. No atribuye un volumen de búsquedas a esa
  selección manual.
- Resultado observado: no ejecutado.

## CAT-CP-013 — Conteo de producto abierto desde resultados

- Criterio: CAT-CA-013; requisito: CAT-RF-001.
- Precondición: una búsqueda interna muestra los productos ficticios A, B y C.
- Acción: abrir la ficha de B desde los resultados.
- Resultado esperado: el conteo de B aumenta en uno; los conteos de A y C no
  cambian por haber aparecido en los mismos resultados. Si la ficha de B se abre
  otra vez desde resultados, la segunda apertura también aumenta su conteo en uno,
  incluso si la misma persona ya la abrió (DEC-018).
- Resultado observado: no ejecutado.

## CAT-CP-014 — Cambiar un voto de utilidad

- Criterio: CAT-CA-014; requisito: CAT-RF-012.
- Precondición: participante de prueba con identidad reconocida y ficha publicada.
- Acción: votar «útil» y luego cambiar el voto a «no útil».
- Resultado esperado: queda una sola respuesta activa del participante para el
  producto; la segunda reemplaza a la primera.
- Resultado observado: no ejecutado.

## CAT-CP-015 — Moderador designado aprueba

- Criterio: CAT-CA-015; requisito: CAT-RF-015.
- Precondición: comentario pendiente y cuenta de equipo con permiso de moderación.
- Acción: la cuenta aprueba el comentario.
- Resultado esperado: la operación se permite y el comentario sigue el estado de
  publicación definido por CAT-CA-003.
- Resultado observado: no ejecutado.

## CAT-CP-016 — Integrante sin permiso no aprueba

- Criterio: CAT-CA-016; requisito: CAT-RF-015.
- Precondición: comentario pendiente y cuenta de equipo sin permiso de moderación.
- Acción: intentar aprobar el comentario.
- Resultado esperado: operación rechazada; comentario permanece pendiente y no
  es visible públicamente.
- Resultado observado: no ejecutado.

## CAT-CP-017 — Cobertura mínima por categoría

- Criterio: CAT-CA-017; requisito: CAT-RF-011.
- Precondición: conjunto de datos candidato a lanzamiento.
- Acción: revisar la cobertura por categoría y el estado editorial de cada ficha.
- Resultado esperado: hay por lo menos una ficha publicada y aprobada por el equipo
  en cada categoría; la revisión no afirma cobertura de todos los productos del mercado.
- Resultado observado: no ejecutado.

## Cobertura de criterios

La revisión documental confirmó que los 47 criterios CAT-CA-001 a CAT-CA-047
aparecen en al menos uno de los 46 escenarios CAT-CP-001 a CAT-CP-046. Los
escenarios son diseños de verificación, no pruebas implementadas ni ejecutadas.
La implementación deberá añadir casos cuando revele condiciones de concurrencia
o fallos técnicos que afecten los contratos aprobados.

## Escenarios de contrato concretados por delegación

Estos casos corresponden a CAT-CA-018 a CAT-CA-047. Son escenarios diseñados para
futura verificación; no son pruebas implementadas ni ejecutadas.

### CAT-CP-018 — Popularidad y fallback

- Criterios: CAT-CA-018; requisitos CAT-RF-001/016.
- Precondición: eventos UTC para fichas A/B en `ahora - 30 días + 1 s`, exactamente
  en `ahora - 30 días`, y en `ahora`; incluir apertura repetida, impresión sin
  apertura, ruta directa y crawler identificado.
- Acción: abrir portada con actividad y repetir con todos los eventos expirados.
- Resultado esperado: cuentan las aperturas de la ventana `(ahora - 30 días,
  ahora]`, incluidas las repetidas; se excluye el evento en el límite y los demás
  eventos inválidos. Se ordena por total y desempate estable; con total cero
  aparecen destacados manuales, sin atribuirles popularidad. Los eventos no
  contienen identidad, IP ni user-agent persistido.
- Resultado observado: no ejecutado.

### CAT-CP-019 — Búsqueda normalizada y límite

- Criterios: CAT-CA-019; requisito CAT-RF-002.
- Precondición: productos ficticios cuyos nombres incluyan marca, modelo y
  coincidencias exactas, prefijo, substring y diacríticos; páginas de más de 24.
- Acción: buscar con y sin acentos, vacío y término de 101 caracteres; avanzar página.
- Resultado esperado: coincidencia sin distinguir acentos/caja, relevancia exacta
  antes de prefijo/substring por defecto, 24 por página y estados en español;
  orden explícito prevalece con relevancia como desempate; se rechazan 101
  caracteres sin ejecutar búsqueda ni mostrar resultados.
- Resultado observado: no ejecutado.

### CAT-CP-020 — Combinación e inclusividad de filtros

- Criterios: CAT-CA-020; requisito CAT-RF-003.
- Precondición: datos ficticios que incluyan múltiples marcas, extremos exactos de
  precio/año y productos con campos ausentes.
- Acción: aplicar marcas múltiples y combinar categoría, año, precio y filtro técnico.
- Resultado esperado: OR dentro de marcas; AND entre grupos; límites incluidos;
  producto con valor ausente excluido del filtro correspondiente.
- Resultado observado: no ejecutado.

### CAT-CP-021 — Rango de precio inválido

- Criterios: CAT-CA-021; requisitos CAT-RF-003/017.
- Precondición: consulta válida aplicada con resultados visibles.
- Acción: introducir mínimo mayor que máximo.
- Resultado esperado: mensaje de error; no se aplica ninguno de los dos límites
  inválidos, sí se aplican los demás filtros válidos y se actualiza el conteo.
- Resultado observado: no ejecutado.

### CAT-CP-022 — Categoría, limpieza, conteo y orden

- Criterios: CAT-CA-022; requisitos CAT-RF-003/016/017.
- Precondición: filtro técnico de monitor, marca, query, precio, fecha ausente y
  resultados distribuidos en varias páginas.
- Acción: cambiar a mouses; luego limpiar filtros; probar orden de precio/fecha.
- Resultado esperado: se limpia solo el filtro técnico incompatible y se informa;
  «Limpiar filtros» preserva query y sort; el total de productos previo a paginar
  es correcto; el criterio de orden es primario y, con query, relevancia precede
  al nombre normalizado y slug para desempatar. Ausencias al final.
- Resultado observado: no ejecutado.

### CAT-CP-023 — Selección de variantes

- Criterios: CAT-CA-023; requisitos CAT-RF-005/006/007.
- Precondición: ficha ficticia con variantes de color y capacidad técnica distinta.
- Acción: seleccionar cada variante.
- Resultado esperado: se muestran únicamente imagen, precio y atributos propios;
  no hay herencia incompatible; toda revisión publicada tiene exactamente una
  variante predeterminada; un cambio de generación/plataforma se representa con
  otra ficha.
- Resultado observado: no ejecutado.

### CAT-CP-024 — Estados y unidades de atributos

- Criterios: CAT-CA-024; requisito CAT-RF-006.
- Precondición: valores ficticios conocidos, cero real, no informado, no corresponde
  y pendiente de verificar; magnitudes comparables en unidades de origen distintas.
- Acción: consultar ficha, filtrar y ordenar.
- Resultado esperado: estados se distinguen; unidades se normalizan; desconocidos
  no se interpretan como cero ni coinciden en filtros.
- Resultado observado: no ejecutado.

### CAT-CP-025 — Revisión y reemplazo editorial

- Criterios: CAT-CA-025; requisitos CAT-RF-010/011.
- Precondición: producto publicado, dos sesiones de Editor con el mismo borrador
  y cuenta de Revisor separada.
- Acción: Editor A guarda; Editor B intenta guardar su copia obsoleta; luego
  Revisor publica una corrección y retira otra ficha.
- Resultado esperado: guardado obsoleto se rechaza sin pérdida de datos; el
  contenido público anterior permanece hasta aprobación; el retiro elimina la
  ficha de listados, bloquea nuevas participaciones y muestra no disponible en
  URL directa. Actor, fecha y acción quedan registrados.
- Resultado observado: no ejecutado.

### CAT-CP-026 — Checklist de publicación y gate de categorías

- Criterios: CAT-CA-026, CAT-CA-017; requisito CAT-RF-011.
- Precondición: una ficha candidata que satisface los campos obligatorios de cada
  una de las ocho categorías; variantes incompletas por categoría; una ficha con
  precio/fecha ausentes y otra con fuente faltante o conflicto técnico no resuelto.
- Acción: Revisor intenta publicar; corregir incompletas y preparar lanzamiento.
- Resultado esperado: se rechaza la ficha que carece de cualquier atributo técnico
  mínimo o fuente, o conserva un conflicto de fuentes sin resolver; se aceptan
  precio/fecha ausentes con estado visible. El lanzamiento requiere al menos una
  ficha revisada/publicada por cada una de las ocho categorías.
- Resultado observado: no ejecutado.

### CAT-CP-027 — Precio presente, ausente e inválido

- Criterios: CAT-CA-027; requisito CAT-RF-007.
- Precondición: fichas ficticias con precio positivo con decimales, precio ausente,
  precio cero, negativo y más de dos decimales.
- Acción: publicar y consultar fichas, filtrar y ordenar por precio.
- Resultado esperado: precio de la revisión pública se muestra «Precio aproximado»
  en USD y formato español; no se presenta historial ni garantía de vigencia;
  ausente se indica no disponible, se excluye de filtros y queda al final en ambos
  órdenes por precio; inválidos se rechazan.
- Resultado observado: no ejecutado.

### CAT-CP-028 — Precisión de fecha de lanzamiento

- Criterios: CAT-CA-028; requisito CAT-RF-008.
- Precondición: fichas con fecha de solo año, año/mes, fecha completa y fecha ausente.
- Acción: consultar, filtrar por año y ordenar por fecha.
- Resultado esperado: no se inventa precisión; las fechas parciales coinciden con
  su año conocido; en orden descendente completo, mes ausente vale 0 y día ausente
  vale 0 solo para ordenar; ausencia total no coincide y queda al final.
- Resultado observado: no ejecutado.

### CAT-CP-029 — Fuentes editoriales y permiso de imagen

- Criterios: CAT-CA-029; requisitos CAT-RF-004/009.
- Precondición: borradores ficticios con fuente oficial, fuente técnica alternativa,
  pro/contra editorial y una imagen sin permiso verificado.
- Acción: revisar y tratar de publicar.
- Resultado esperado: hechos tienen fuente interna; opiniones aparecen como
  editoriales contextualizadas; la imagen sin permiso verificado no se publica.
- Resultado observado: no ejecutado.

### CAT-CP-030 — Voto editable y conteos

- Criterios: CAT-CA-030; requisito CAT-RF-012.
- Precondición: producto publicado, identidad reconocida y contadores en cero.
- Acción: votar útil, cambiar a no útil, enviar dos cambios concurrentes y repetir
  hasta exceder 60 envíos por hora.
- Resultado esperado: un voto activo reemplazable; conteos separados; exceso rechazado;
  ninguna acción altera popularidad ni crea dos respuestas activas; las operaciones
  concurrentes dejan el valor de la transacción confirmada en último lugar.
- Resultado observado: no ejecutado.

### CAT-CP-031 — Identidad anónima y transición a cuenta

- Criterios: CAT-CA-031; requisitos CAT-RF-012/013.
- Precondición: navegador sin cuenta y navegador alterno; token anónimo existente.
- Acción: votar/comentar, borrar cookie, iniciar sesión y revisar almacenamiento.
- Resultado esperado: cookie segura con expiración de 12 meses; sin IP como identidad
  ni huella; etiqueta «Anónimo»; borrado crea otra identidad y no se fusionan aportes.
- Resultado observado: no ejecutado.

### CAT-CP-032 — Validación de comentario

- Criterios: CAT-CA-032; requisito CAT-RF-013.
- Precondición: formulario público.
- Acción: enviar espacios solamente, 1, 2.000 y 2.001 caracteres.
- Resultado esperado: espacios y 2.001 se rechazan sin guardar; 1 y 2.000 quedan
  pendientes de moderación; errores se asocian al formulario.
- Resultado observado: no ejecutado.

### CAT-CP-033 — Moderación, privacidad y límite de comentarios

- Criterios: CAT-CA-033/039; requisitos CAT-RF-013/015, CAT-RNF-004.
- Precondición: comentarios pendientes, aprobados y rechazados; usuario ordinario,
  Editor y Moderador; 5 envíos en la última hora; una ficha publicada y otra retirada.
- Acción: consultar vista pública, aprobar/rechazar/retirar, intentar hacerlo sin
  permiso, enviar sexto comentario y comentar sobre la ficha retirada.
- Resultado esperado: solo aprobados se exponen, ordenados por fecha; solo Moderador
  cambia estado; sexto envío se rechaza; texto no se interpreta como HTML ni se
  filtran datos de pendientes/rechazados; la ficha retirada no recibe comentarios.
- Resultado observado: no ejecutado.

### CAT-CP-034 — Cuenta y eliminación

- Criterios: CAT-CA-034 y CAT-CA-035; requisito CAT-RF-014.
- Precondición: usuario con correo no verificado, verificado, voto, comentario
  pendiente y comentario aprobado.
- Acción: verificar correo, recuperar acceso, iniciar sesión en dos navegadores y
  solicitar eliminación de cuenta.
- Resultado esperado: alias público y correo privado; recuperación por enlace;
  tras eliminar cuenta se invalidan ambas sesiones, se borran sus votos y
  comentarios no públicos, y el comentario aprobado se conserva sin referencias
  de autoría como «Anónimo». La auditoría no conserva correo ni alias; los aportes
  anónimos no se vinculan.
- Resultado observado: no ejecutado.

### CAT-CP-035 — Tema del sistema y preferencia manual

- Criterios: CAT-CA-036; requisito CAT-RF-018.
- Precondición: navegador nuevo con tema claro del sistema y consulta con filtros.
- Acción: cambiar tema a oscuro, recargar y visitar desde otro navegador.
- Resultado esperado: primer navegador conserva oscuro sin cambiar query/filtros;
  navegador alterno sigue su propia preferencia del sistema.
- Resultado observado: no ejecutado.

### CAT-CP-036 — Accesibilidad de teclado y móvil

- Criterios: CAT-CA-037; requisito CAT-RNF-002.
- Precondición: vistas públicas y de equipo con resultados, errores y formularios.
- Acción: revisar con teclado y viewport de 360 CSS px; ejecutar auditoría WCAG.
- Resultado esperado: todos los controles son operables, foco/nombres/errores visibles
  y no hay scroll horizontal de página; hallazgos AA bloqueantes registrados.
- Resultado observado: no ejecutado.

### CAT-CP-037 — Rendimiento de campo

- Criterios: CAT-CA-038; requisito CAT-RNF-003.
- Precondición: sitio desplegado con tráfico suficiente durante 28 días.
- Acción: obtener métricas por percentil 75 en móvil y escritorio.
- Resultado esperado: LCP ≤2,5 s, INP ≤200 ms y CLS ≤0,1; sin tráfico suficiente,
  estado «no medible», nunca «aprobado».
- Resultado observado: no ejecutado.

### CAT-CP-038 — Autorización en servidor y datos ficticios

- Criterios: CAT-CA-039; requisito CAT-RNF-004.
- Precondición: rutas de edición/moderación, sesiones con cada rol y datos ficticios.
- Acción: acceder directamente a URL restringida, enviar texto tipo HTML y consultar
  respuestas públicas.
- Resultado esperado: servidor rechaza rol insuficiente; contenido se presenta como
  texto; no se exponen correo, contraseña ni comentarios no aprobados.
- Resultado observado: no ejecutado.

### CAT-CP-039 — Revisión periódica de fichas activas

- Criterios: CAT-CA-040; requisito CAT-RF-010.
- Precondición: fichas activas ficticias con revisiones realizadas dentro y fuera
  de los últimos 12 meses; una ficha tiene una corrección técnica verificada.
- Acción: ejecutar la revisión editorial manual y registrar cada resultado.
- Resultado esperado: cada ficha activa se revisa dentro del período de 12 meses;
  la corrección verificada se revisa antes de actualizar la ficha; actor y fecha
  quedan auditados. No se presupone aviso automático ni vigencia de precio.
- Resultado observado: no ejecutado.

### CAT-CP-040 — Estados de carga, error, vacío y dato no disponible

- Criterios: CAT-CA-041; requisito CAT-RF-019.
- Precondición: vista en carga, una consulta fallida, una lista sin resultados y
  una ficha con campo opcional sin valor.
- Acción: abrir cada estado desde la interfaz pública.
- Resultado esperado: cada estado se presenta en español y se distingue de los
  otros; un campo ausente se marca como no disponible, nunca como cero ni como
  ausencia de resultados.
- Resultado observado: no ejecutado.

### CAT-CP-041 — Filtros sobre una sola variante

- Criterios: CAT-CA-042; requisitos CAT-RF-003/017.
- Precondición: producto ficticio con variante A (8 GB, USD 500) y variante B
  (32 GB, USD 1.200); filtros técnicos de RAM y precio.
- Acción: filtrar por 32 GB y precio máximo USD 600; luego por 8 GB y precio
  máximo USD 600; repetir con ambas variantes coincidentes.
- Resultado esperado: el primer conjunto no contiene el producto; el segundo lo
  contiene una vez; cuando ambas variantes coincidan, el producto y conteo siguen
  apareciendo una sola vez.
- Resultado observado: no ejecutado.

### CAT-CP-042 — Variante representada, predeterminada y URL

- Criterios: CAT-CA-043; requisitos CAT-RF-003/007/016.
- Precondición: producto con variante predeterminada A (8 GB, USD 600) y variante
  B (32 GB, USD 1.200), ambas publicadas con claves estables; producto adicional
  cuya variante predeterminada no coincide con el filtro y cuya variante coincidente
  no tiene precio.
- Acción: consultar resultados con y sin filtro de 32 GB; abrir el resultado,
  visitar la URL sin selector y solicitar una clave retirada.
- Resultado esperado: sin filtro, tarjeta representa A; con filtro de 32 GB,
  representa B y el precio de orden es USD 1.200. La URL del resultado abre B;
  la URL sin selector abre A; la clave retirada muestra «Variante no disponible»
  y no cambia de variante silenciosamente. En el producto adicional, la tarjeta
  representa la variante sin precio que sí coincide y no muestra la predeterminada
  incompatible con el filtro.
- Resultado observado: no ejecutado.

### CAT-CP-043 — Autoría exclusiva y ciclo de eliminación de cuenta

- Criterios: CAT-CA-044 y CAT-CA-045; requisitos CAT-RF-012/013/014.
- Precondición: cuentas y actores anónimos ficticios con tokens válidos.
- Acción: intentar crear voto/comentario con solo usuario, solo actor, ambos y
  ninguno; luego borrar la cuenta autora de un comentario aprobado, comprobar que
  su sesión y credenciales ya no sirven e intentar registrarse de nuevo con el mismo
  correo para votar y consultar los aportes previos.
- Resultado esperado: los dos casos con exactamente un autor se aceptan; ambos y
  ninguno se rechazan. Tras borrar cuenta, el aprobado permanece sin referencia a
  usuario ni actor y se muestra como «Anónimo». La sesión anterior no autentica;
  el nuevo registro es identidad distinta y no recupera votos ni autoría previa.
- Resultado observado: no ejecutado.

### CAT-CP-044 — Validación de esquemas de atributos

- Criterios: CAT-CA-047; requisito CAT-RF-006.
- Precondición: valores de prueba ficticios para atributos obligatorios y
  opcionales de las ocho categorías; ejemplos válidos e inválidos por tipo.
- Acción: guardar una resolución válida y una con dimensiones no enteras; una
  capacidad con unidad incompatible; una conexión fuera del conjunto declarado;
  una lista donde el campo es escalar y ausencia expresada como cero.
- Resultado esperado: valores conformes se conservan con unidad/cardinalidad
  definidas; los otros se rechazan asociados al atributo y no se convierten ni se
  publican como valores válidos.
- Resultado observado: no ejecutado.

### CAT-CP-045 — Expiración de identidad anónima

- Criterios: CAT-CA-046; requisitos CAT-RF-012/013.
- Precondición: actor anónimo con voto, comentario aprobado y token con vencimiento
  fijado a los 365 días de emisión; preparar consultas un instante antes,
  exactamente al vencer y un instante después.
- Acción: participar con el token expirado y consultar los aportes existentes.
- Resultado esperado: antes del vencimiento el token autentica; exactamente al
  vencer y después no permite escribir y su hash se elimina; el voto
  conserva su conteo y el comentario aprobado sigue visible como «Anónimo». Un
  token nuevo crea identidad nueva, sin apropiarse de los aportes anteriores.
- Resultado observado: no ejecutado.

### CAT-CP-046 — Orden completo de fechas parciales

- Criterios: CAT-CA-028; requisito CAT-RF-008.
- Precondición: fechas ficticias: 2026, 2026-03, 2026-03-12, 2025-12-31 y una
  fecha ausente.
- Acción: ordenar por lanzamiento más reciente y navegar el orden completo.
- Resultado esperado: 2026-03-12, 2026-03, 2026, 2025-12-31 y fecha ausente, en
  ese orden; solo se muestran las precisiones realmente cargadas.
- Resultado observado: no ejecutado.
