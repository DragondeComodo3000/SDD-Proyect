# Diccionario inicial de datos por categoría

Versión: 1.0. Estado: **contrato de datos aprobado el 2026-10-26**. Los campos
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

