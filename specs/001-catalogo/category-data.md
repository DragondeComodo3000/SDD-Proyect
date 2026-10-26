# Diccionario inicial de datos por categoría

Versión: 1.1. Estado: **contrato de datos actualizado en la revisión correctiva autorizada**. Los campos
descritos no contienen valores de productos reales. La carga de datos requiere
fuentes y revisión editorial según los criterios aprobados.

## Reglas comunes

Toda ficha publicada identifica categoría, marca, modelo comercial, descripción
en español e imágenes. Producto y variante no son sinónimos: si una opción cambia
componentes o especificaciones, la ficha debe indicar exactamente qué variante
describe. La variante elegida se refleja en campos, precio y fotografía cuando
existan diferencias.

Para evitar que una ausencia parezca una especificación, cada campo puede estar
**informado**, **no informado**, **no corresponde** o **pendiente de verificar**.
Un cero solo representa el número cero cuando el dato realmente sea cero. Los
atributos numéricos declaran unidad; no se compara texto libre como si fueran
valores equivalentes.

Los campos de la tabla son el contrato inicial de datos, no una promesa de que
cada producto tenga todos los atributos. Los campos opcionales no disponibles se
marcan «No informado», «No corresponde» o «Pendiente de verificar» según el
conocimiento editorial; nunca se infieren. Solo los valores conocidos filtran u
ordenan. Atributos candidatos no listados como filtros se muestran, pero no se
filtran en el MVP.

## Mínimo obligatorio para publicar una ficha

Toda revisión publicable debe incluir categoría, marca, modelo comercial, nombre
visible, descripción inicial en español, imagen con texto alternativo y permiso
verificado, al menos un pro y un contra editoriales contextualizados, y fuentes
internas para los hechos técnicos obligatorios. Precio aproximado y fecha de
lanzamiento son opcionales; si faltan se muestran como «No disponible».

Además, la revisión debe conocer estos atributos centrales por categoría. Un dato
obligatorio desconocido o pendiente de verificar bloquea la publicación; no se
permite sustituirlo por un texto de ausencia. Otros atributos técnicos siguen
siendo opcionales y conservan los estados de ausencia de las reglas comunes.

| Categoría | Atributos técnicos obligatorios para publicar |
|---|---|
| Mouses | Una o más conexiones disponibles (cable, radio 2,4 GHz o Bluetooth) |
| Monitores | Diagonal, resolución nativa y frecuencia máxima |
| Laptops | Familia/modelo de CPU, capacidad de RAM y capacidad de almacenamiento |
| Teclados | Conexión, distribución del teclado y formato |
| Tarjetas madre | Socket, formato y generación de memoria |
| Procesadores | Socket, cantidad de núcleos y cantidad de hilos |
| Tarjetas de video | Capacidad de memoria de video dedicada (VRAM) |
| Consolas de videojuego | Familia/generación, edición (digital o con unidad) y capacidad de almacenamiento |

Esta es una regla de publicación del MVP (ADE-018), no una obligación de que cada
producto exponga todos los campos filtrables u opcionales de la tabla inferior.

## Campos y filtros iniciales por categoría

| Categoría | Filtros iniciales | Campos técnicos que se muestran cuando se conocen | Unidades o forma |
|---|---|---|
| Mouses | Conexión (cable, radio 2,4 GHz, Bluetooth; una o varias) | Tipo de sensor; DPI/CPI; frecuencia de sondeo; peso; botones; batería; mano/diseño | DPI/CPI; Hz; g; cantidad; mAh cuando se publique |
| Monitores | Diagonal; resolución; frecuencia máxima | Relación de aspecto; tecnología de panel; respuesta con método; brillo; puertos; sincronización variable | pulgadas; píxeles; Hz; ms; cd/m²; conector |
| Laptops | Familia de CPU; RAM; almacenamiento | GPU integrada y dedicada; tipo de almacenamiento; pantalla; sistema operativo de fábrica; peso; puertos | GB/TB; pulgadas; Hz; kg |
| Teclados | Conexión; distribución; formato | Tipo de switch; retroiluminación; teclado numérico; conexiones simultáneas | opciones declaradas; formato comercial normalizado |
| Tarjetas madre | Socket; formato; generación de memoria | Chipset; ranuras de memoria y expansión; almacenamiento admitido; red; puertos traseros | formato; estándar/conector; conteos; Gbps si se publica |
| Procesadores | Socket; núcleos; hilos | Familia/modelo; frecuencias base/turbo; caché; potencia; memoria admitida; gráficos integrados | cantidad; GHz; MB; W; tipo/velocidad de memoria |
| Tarjetas de video | Memoria dedicada (VRAM) | Modelo de GPU; tipo/ancho de memoria; frecuencia; dimensiones; potencia; conectores de energía; salidas | GB; tipo; bits; MHz/GHz; mm; W; conectores |
| Consolas de videojuego | Familia/generación; edición (digital o con unidad); almacenamiento | CPU/GPU si fabricante identifica; memoria; salida de video; puertos; control incluido; compatibilidad | GB/TB; conector; resolución y frecuencia declaradas |

Los filtros numéricos reciben mínimo/máximo inclusivos y los categóricos permiten
selección múltiple. Si un campo admite varios valores, el producto coincide si
incluye al menos una de las opciones seleccionadas.

## Esquemas de tipo, unidad y cardinalidad

Los tipos de este esquema son normativos. Enteros de conteo son mayores que cero,
salvo campos de cantidad donde cero tenga sentido físico (por ejemplo, puertos).
Las magnitudes decimales son finitas; frecuencia, peso, distancia, capacidad y
potencia conocidas son positivas. No se aceptan `NaN`, infinito, valores
negativos ni conversiones implícitas de texto a número. Identificadores de modelo,
tecnología, socket, chipset, sistema operativo, estándar y conector son texto plano
conservado según la fuente; no se inventan opciones de un catálogo cerrado.

Capacidad se normaliza a bytes: GB = 1.000.000.000; TB = 1.000.000.000.000;
GiB = 1.073.741.824; TiB = 1.099.511.627.776. Se conserva en la ficha la unidad
declarada por la fuente. Una resolución es el par ordenado de enteros positivos
`(ancho_px, alto_px)`; no se representa con un único escalar. Un atributo de tipo
conjunto conserva cero o más valores normalizados de su conjunto declarado. Los
campos marcados como no filtrables se muestran, pero no participan en consultas.

| Categoría | Atributo (clave) | Tipo, unidad y cardinalidad | Filtro |
|---|---|---|---|
| Mouses | Conexión (`connection`) | Conjunto de enum: cable, radio 2,4 GHz, Bluetooth | Sí; selección múltiple |
| Mouses | Sensor (`sensor`), mano/diseño (`hand_design`) | Texto del fabricante o editor; uno | No |
| Mouses | DPI/CPI (`sensitivity_dpi`), sondeo (`polling_hz`), peso (`weight_g`), botones (`button_count`), batería (`battery_mah`) | DPI/CPI: decimal dpi; sondeo: entero Hz; peso: decimal g; botones: entero; batería: entero mAh | No |
| Monitores | Diagonal (`diagonal_in`), frecuencia máxima (`refresh_hz`) | Decimal pulgadas; decimal Hz; uno | Sí; rango inclusivo |
| Monitores | Resolución nativa (`native_resolution`) | Par de enteros positivos ancho/alto, píxeles | Sí; selección de pares |
| Monitores | Relación de aspecto (`aspect_ratio`), panel (`panel_type`), respuesta (`response_ms`), método de respuesta (`response_method`), brillo (`brightness_nits`), puertos (`ports`), sincronización (`variable_sync`) | Aspecto/panel/método: texto; respuesta: decimal ms y método requerido cuando se informa; brillo: decimal cd/m²; puertos/sincronización: conjunto de etiquetas técnicas | No |
| Laptops | Familia/modelo CPU (`cpu_family`), almacenamiento (`storage_type`), sistema operativo (`factory_os`), puertos (`ports`) | Texto o conjunto cuando haya varias interfaces | CPU: Sí, selección múltiple; otros: no |
| Laptops | RAM (`ram_bytes`), almacenamiento (`storage_bytes`), peso (`weight_kg`) | Capacidad: entero en bytes; peso: decimal kg | RAM y capacidad: rangos inclusivos; peso: no |
| Laptops | GPU integrada (`integrated_gpu`), GPU dedicada (`dedicated_gpu`) | Texto del modelo; cada campo opcional e independiente | No |
| Laptops | Pantalla (`display_diagonal_in`), resolución (`display_resolution`), frecuencia (`display_refresh_hz`) | Decimal pulgadas; par de enteros en píxeles; decimal Hz | No |
| Teclados | Conexión (`connection`) | Conjunto de enum: cable, radio 2,4 GHz, Bluetooth | Sí; selección múltiple |
| Teclados | Distribución (`layout`), formato (`form_factor`) | Texto/código normalizado con etiqueta original conservada | Sí; selección múltiple |
| Teclados | Switch (`switch_type`), retroiluminación (`backlight`) | Texto del fabricante/editor | No |
| Teclados | Teclado numérico (`has_numpad`) | Booleano informado, desconocido o no corresponde | No |
| Teclados | Conexiones simultáneas (`simultaneous_connections`) | Entero positivo | No |
| Tarjetas madre | Socket (`socket`), formato (`form_factor`) | Texto/código normalizado con etiqueta original conservada | Sí; selección múltiple |
| Tarjetas madre | Generación de memoria (`memory_generation`) | Texto/código estandarizado (por ejemplo, DDR5) | Sí; selección múltiple |
| Tarjetas madre | Chipset (`chipset`), almacenamiento admitido (`storage_interfaces`), puertos (`rear_ports`) | Chipset: texto; interfaces/puertos: conjuntos de etiquetas | No |
| Tarjetas madre | Ranuras de memoria (`memory_slots`), expansión (`expansion_slots`) | Enteros no negativos | No |
| Tarjetas madre | Velocidad de red (`network_gbps`) | Decimal Gbit/s | No |
| Procesadores | Socket (`socket`) | Texto/código conservado | Sí; selección múltiple |
| Procesadores | Núcleos (`core_count`), hilos (`thread_count`) | Enteros positivos | Sí; rangos inclusivos |
| Procesadores | Frecuencia base/turbo (`base_clock_mhz`, `boost_clock_mhz`) | Decimal MHz | No |
| Procesadores | Caché (`cache_bytes`), potencia (`power_w`) | Entero en bytes; decimal W | No |
| Procesadores | Memoria admitida (`memory_types`) | Conjunto de tipo/velocidad declarados por el fabricante | No |
| Procesadores | Gráficos integrados (`integrated_graphics`) | Booleano informado, desconocido o no corresponde | No |
| Tarjetas de video | VRAM (`vram_bytes`) | Capacidad entera en bytes | Sí; rango inclusivo |
| Tarjetas de video | GPU (`gpu_model`), memoria (`memory_type`) | Texto del fabricante | No |
| Tarjetas de video | Ancho de bus (`memory_bus_bits`), frecuencia (`clock_mhz`), potencia (`power_w`), dimensión (`dimension_mm`) | Bus: entero bits; frecuencia: decimal MHz; potencia: decimal W; dimensión: terna de decimales mm | No |
| Tarjetas de video | Conectores de energía (`power_connectors`), salidas (`display_outputs`) | Conjuntos de etiquetas técnicas normalizadas | No |
| Consolas | Familia/generación (`family_generation`) | Texto/código normalizado con etiqueta original conservada | Sí; selección múltiple |
| Consolas | Edición (`edition`) | Enum: digital, con unidad | Sí; selección múltiple |
| Consolas | Almacenamiento (`storage_bytes`) | Capacidad entera en bytes | Sí; rango inclusivo |
| Consolas | CPU/GPU (`cpu_model`, `gpu_model`), memoria (`memory_bytes`) | Modelo: texto del fabricante; memoria: capacidad en bytes | No |
| Consolas | Salidas de video (`video_outputs`), puertos (`ports`), control (`included_controller`), compatibilidad (`compatibility`) | Conjuntos de etiquetas; compatibilidad y control en texto editorial | No |

En valores de conjunto, duplicados se eliminan después de normalizar espacios y
caja, preservando etiquetas originales para presentación. No se descartan modelos,
conectores o tecnologías desconocidos: se guardan como texto fuente y requieren
revisión editorial. Un tipo, unidad o cardinalidad incorrectos bloquea el guardado;
un atributo obligatorio incorrecto también bloquea la publicación según CAT-CA-026.

## Identidad y variantes

- Una ficha identifica categoría, marca y modelo comercial exacto. Una diferencia
  de generación, plataforma o compatibilidad crea una ficha distinta.
- Color, distribución, conexión, capacidad, CPU/GPU o panel pueden definir una
  variante de la misma familia cuando el fabricante la comercializa bajo esa
  identidad; sus atributos y precio propios no se heredan de otra variante.
- Una edición regional o revisión de hardware se distingue cuando cambia una
  especificación o compatibilidad que afecta la decisión de compra.
- La página indica la variante seleccionada; no mezcla sus datos con los de otra.

Estas reglas aplican ADE-006 y CAT-CA-023; el revisor editorial resuelve casos
de identidad nuevos registrando la razón antes de publicar.

## Uso para filtros y fichas

Solo campos con unidad y valores definidos son filtrables. El rótulo que ve la
persona debe estar en español, aunque el nombre de un estándar o conector conserve
su grafía oficial. Cada campo debe registrar: definición, unidad, tipo, validez,
categorías, disponibilidad, fuente de captura y si aparece en la ficha o como filtro.

Los rótulos visibles son españoles; los nombres oficiales de puertos, interfaces,
tecnologías y estándares pueden conservar su grafía. Las unidades se normalizan
internamente y se presentan de forma consistente.

## Reglas de revisión del diccionario

- Cada campo define etiqueta, significado, tipo, unidad, si es obligatorio, si se
  filtra y cómo se muestra cuando falta.
- Rangos numéricos incluyen los extremos; valores desconocidos nunca coinciden.
- La revisión editorial valida los valores frente a la ficha/manual del fabricante
  u otra fuente técnica reconocida, según ADE-008.
- El diccionario puede ampliarse solo mediante cambio de spec, criterios y ejemplos;
  no se agrega un filtro por conveniencia de implementación.

No publicar fichas ficticias o valores de ejemplo como si fueran datos reales.

