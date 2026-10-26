# Defaults de producto resueltos por delegación

Estado: **defaults ADE-001 a ADE-023 adoptados en la baseline y su revisión correctiva**.
El responsable pidió que el agente resolviera las ambigüedades restantes sin
contradecir el alcance existente. Se conserva que fueron decisiones delegadas;
su adopción como baseline no autoriza implementación.

## Producto y comportamiento

| ID | Propuesta concreta | Motivo | Dónde impacta |
|---|---|---|---|
| PROP-001 | Resuelta como ADE-002: ventana móvil de 30 días, toda apertura válida suma, rastreadores conocidos se excluyen, manual si no hay actividad válida; orden descendente con desempate estable. | Completa DEC-015 a DEC-019 sin contar impresiones. | CAT-RF-001/016. |
| PROP-002 | Resuelta como ADE-011/014: cuenta por email; anónimo por cookie aleatoria 12 meses; sin huella digital ni fusión automática. | Permite participar sin registro con limitación explícita. | CAT-RF-012/013/014, privacidad. |
| PROP-003 | Resuelta como ADE-012: conteos «Útil» y «No útil» separados; sin rating del hardware. | Mide utilidad de la ficha. | CAT-RF-012. |
| PROP-004 | Resuelta como ADE-013: texto plano 1–2.000 caracteres; pendiente hasta moderación; aprobados primero; sin hilos, adjuntos ni edición del autor. | Limita el flujo de moderación a lo esencial. | CAT-RF-013/015. |
| PROP-005 | Resuelta como ADE-013/014: confirmación pendiente; sin correo transaccional en MVP; cuenta usa correo solo para verificación y recuperación. | Evita dependencia de notificaciones en comentarios. | CAT-RF-013/014. |
| PROP-006 | Resuelta como ADE-005: Editor, Revisor de catálogo y Moderador con permisos separados; un integrante puede tener más de un rol. | Separa edición, publicación y comentarios. | CAT-RF-010/015. |
| PROP-007 | Resuelta como ADE-009: checklist de publicación, actor/fecha auditados, faltantes explícitos y revisión anual/manual de ficha activa. | Hace verificable la condición de contenido revisado. | CAT-RF-010/011. |
| PROP-008 | Resuelta por DEC-022/023: una ficha publicada y revisada por categoría; sin cuota adicional ni promesa de exhaustividad. | Mínimo de lanzamiento verificable. | CAT-RF-011. |
| PROP-009 | Resuelta como ADE-003: búsqueda parcial sin acentos/mayúsculas por marca/modelo/nombre; relevancia exacta/prefijo/substring como inicial; límite 100; 24 por página. | Evita prometer búsqueda en especificaciones o motor externo. | CAT-RF-002. |
| PROP-010 | Resuelta como ADE-004: AND entre grupos, OR en marcas, rangos inclusivos, precio desconocido excluido, error de rango inválido sin aplicar sus límites y limpieza que preserva query/orden. | Hace predecible la combinación de filtros. | CAT-RF-003/017. |
| PROP-011 | Resuelta como ADE-004/ADE-023: conteo de productos antes de paginar; datos ausentes al final, incluido precio en ambos sentidos; orden principal explícito, relevancia secundaria con búsqueda y luego nombre normalizado/slug. | Orden determinista sin mezclar fichas ni dar prioridad accidental a valores ausentes. | CAT-RF-003/016/017. |
| PROP-012 | Resuelta como ADE-015: preferencia de sistema en primera visita, selección manual persistida solo localmente. | Sencillo y consistente con cuenta opcional. | CAT-RF-018. |

## Catálogo y publicación

- Una ficha identifica modelo comercial, marca y categoría; una variante puede
  representar color, distribución o configuración. Diferencias de generación,
  plataforma o compatibilidad crean ficha separada.
- Mostrar solo campos conocidos; separar «No informado» de «No corresponde».
  No completar detalles, pros o contras mediante una conjetura de la IA.
- Los campos y filtros por categoría se enumeran en
  `specs/001-catalogo/category-data.md`; números usan valor/unidad
  normalizados y faltantes no equivalen a cero.
- El precio se ingresa manualmente por el equipo con etiqueta «Precio aproximado»
  y moneda USD. Fuentes y método los decide el equipo al cargarlo. Si no hay valor,
  no mostrar un número inventado ni hacerlo coincidir con rangos de precio; en
  órdenes por precio, colocar esos resultados después de los precios conocidos,
  tanto ascendente como descendentemente.
- Aceptar año, mes o fecha completa para lanzamiento según precisión disponible.
  Mostrar la precisión cargada sin inventar día o región.
- Preferir fuente oficial del fabricante para especificaciones; registrar fuente
  técnica reconocida si aquella falta. Pros y contras son análisis editorial
  contextualizado. Imágenes requieren permiso de uso verificado.
- El Revisor de catálogo aplica la lista de publicación; se conserva quién revisó
  y cuándo. Se revisan fichas activas anualmente y ante corrección verificada.
- No incluir comparación, favoritos, enlaces de compra, afiliación, ventas ni pagos.

## Calidad, seguridad y operación

- Objetivo WCAG 2.2 AA; uso completo por teclado; sin scroll horizontal de página
  a 360 CSS px; imágenes con texto alternativo.
- Contenido público, controles y mensajes en español; nombres propios y unidades
  conservan su grafía técnica.
- Escapar texto de comentarios al mostrarlo; no ejecutar contenido incluido por
  usuarios. Límites: cinco comentarios y 60 votos por identidad reconocida/hora.
- Proteger las rutas en servidor por rol; Editor edita, Revisor publica y
  Moderador designado modera comentarios. Auditar cambios y decisiones.
- Hacer visibles errores de lectura, fichas inexistentes, datos vacíos y carga
  pendiente; no exponer comentarios pendientes en vistas públicas.
- Objetivo Core Web Vitals p75 móvil/escritorio: LCP ≤2,5 s, INP ≤200 ms,
  CLS ≤0,1 en 28 días cuando exista tráfico suficiente. Disponibilidad y
  recuperación se fijan al elegir hosting/presupuesto (PND-012).

## Estado de las decisiones

PROP-001 a PROP-012 quedaron convertidas en decisiones delegadas ADE-001 a
ADE-016 y criterios CAT-CA-018 a CAT-CA-041. ADE-017 a ADE-019 completan
convenciones, campos mínimos y ventana de popularidad. La revisión correctiva
actualiza los defaults afectados y los criterios hasta CAT-CA-047. ADE-020 a ADE-023 resuelven
los hallazgos de revisión registrados en `docs/sdd-review.md`. Permanecen diferidos hosting/presupuesto, revisión legal por
mercado y marca/dominio (PND-012, PND-020 y PND-021); no bloquean desarrollo local,
pero sí las operaciones de producción/publicación que requieren resolverlos.
