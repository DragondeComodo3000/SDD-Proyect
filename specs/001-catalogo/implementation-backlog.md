# CAT — Backlog de implementación planificada

Versión: 1.0. Estado: **planificado; ninguna tarea ejecutada**. Baseline: spec 0.20 y plan 0.3,
aprobados el 2026-10-26. Este archivo define trabajo futuro y no contiene código.

## Reglas de ejecución

- La especificación y el plan aprobados son el contrato. Si una tarea revela una
  contradicción o cambia el comportamiento, detener esa tarea y proponer un cambio
  de baseline antes de seguir.
- Cada tarea incluye verificación automatizada pertinente, cambios de código y
  actualización de trazabilidad; no existe una tarea de «escribir todos los tests»
  separada de la funcionalidad.
- Estimaciones orientativas: 30–60 minutos. Si la tarea excede una sesión de
  trabajo corta, dividirla antes de ejecutarla y conservar los enlaces CAT-RF,
  CAT-CA y CAT-CP.
- Registrar para cada ejecución el commit, entorno, comando/procedimiento,
  resultado real y evidencia. En planificación todos los casos siguen «diseñados».
- No cargar productos reales ni publicar datos sin procedencia y permiso de uso.
- Ejecutar este backlog requiere una instrucción explícita posterior del
  responsable. Su aprobación actual es únicamente aprobación de SDD.

## Fase A — Base técnica e identidad

### [CAT-T-001] Crear el esqueleto Django y configuración reproducible

- Estado: pendiente. Depende de: ninguna. Tamaño: 30–60 min.
- Requisitos/criterios: habilitador; estructura ADE-017.
- Módulos/contratos: `config/`, `apps/`, `pyproject.toml`, `.python-version`, `uv.lock`.
- Verificación: checks Django y Ruff definidos por ADE-017.
- Hecho cuando: el proyecto arranca en entorno local documentado, sin secretos ni datos reales, y la estructura coincide con convenciones aprobadas.

### [CAT-T-002] Configurar PostgreSQL local y ajustes por entorno

- Estado: pendiente. Depende de: CAT-T-001. Tamaño: 30–60 min.
- Requisitos/criterios: persistencia y configuración, ADE-016/017.
- Módulos/contratos: `config/settings/`, Docker Compose, variables `.env.example`.
- Verificación: conexión, migraciones vacías y `manage.py check` contra PostgreSQL.
- Hecho cuando: desarrollo y CI usan PostgreSQL de la versión revalidada; secretos están fuera del repositorio.

### [CAT-T-003] Configurar CI con comandos acordados

- Estado: pendiente. Depende de: CAT-T-001, CAT-T-002. Tamaño: 30–60 min.
- Requisitos/criterios: calidad técnica ADE-017.
- Módulos/contratos: proveedor CI a elegir por el equipo; comandos de `development-conventions.md`.
- Verificación: `uv lock --check`, Ruff, checks Django, migraciones y `manage.py test`.
- Hecho cuando: CI ejecuta los mismos checks documentados en PostgreSQL y publica resultados reales por cambio.

### [CAT-T-004] Crear el modelo de cuenta configurado desde la migración inicial

- Estado: pendiente. Depende de: CAT-T-001, CAT-T-002. Tamaño: 30–60 min.
- Requisitos/criterios: CAT-RF-014; CAT-CA-034.
- Módulos/contratos: `apps/accounts/`, `AUTH_USER_MODEL`, email único y alias público.
- Verificación: CAT-CP-034; unicidad y privacidad del email.
- Hecho cuando: el modelo Django usa email como identificador, no publica el correo y no requiere iniciar sesión para consultar el catálogo.

### [CAT-T-005] Implementar registro, verificación, sesión y recuperación

- Estado: pendiente. Depende de: CAT-T-004. Tamaño: 30–60 min.
- Requisitos/criterios: CAT-RF-014; CAT-CA-034.
- Módulos/contratos: `apps/accounts/`, vistas y formularios en español; correo productivo sujeto a PND-012.
- Verificación: CAT-CP-034; pruebas de estados no verificado, verificado y enlace de recuperación.
- Hecho cuando: registro opcional, verificación y recuperación funcionan según la spec; la configuración local no envía correos reales.

### [CAT-T-006] Configurar roles, grupos y comprobación de permisos

- Estado: pendiente. Depende de: CAT-T-004. Tamaño: 30–60 min.
- Requisitos/criterios: CAT-RF-010, CAT-RF-015, CAT-RNF-004; CAT-CA-025, 033, 039.
- Módulos/contratos: `apps/accounts/`, `apps/editorial/`, grupos Editor, Revisor y Moderador.
- Verificación: CAT-CP-016, CAT-CP-038; acceso directo a vistas restringidas.
- Hecho cuando: los permisos se comprueban en servidor y las cuentas públicas no adquieren privilegios internos.

## Fase B — Catálogo y edición

### [CAT-T-007] Crear taxonomía inicial de categorías y marcas

- Estado: pendiente. Depende de: CAT-T-001, CAT-T-002. Tamaño: 30–60 min.
- Requisitos/criterios: CAT-RF-003, CAT-RF-011; CAT-CA-004, 005, 017.
- Módulos/contratos: `apps/catalog/`; ocho categorías fijadas en DEC-007.
- Verificación: CAT-CP-004, CAT-CP-005, CAT-CP-017.
- Hecho cuando: categorías y marcas pueden administrarse sin agregar categorías al MVP fuera de decisión aprobada.

### [CAT-T-008] Implementar definiciones y valores tipados de atributos

- Estado: pendiente. Depende de: CAT-T-007. Tamaño: 30–60 min.
- Requisitos/criterios: CAT-RF-003, CAT-RF-006; CAT-CA-005, 024.
- Módulos/contratos: `AttributeDefinition`, `AttributeValue`, `category-data.md`.
- Verificación: CAT-CP-005, CAT-CP-024; cero real, unidades y estados de ausencia.
- Hecho cuando: cada atributo tiene tipo, unidad y categoría; las ausencias no se interpretan como cero.

### [CAT-T-009] Crear productos y revisiones editoriales

- Estado: pendiente. Depende de: CAT-T-007, CAT-T-006. Tamaño: 30–60 min.
- Requisitos/criterios: CAT-RF-004, CAT-RF-010, CAT-RF-011; CAT-CA-025, 026.
- Módulos/contratos: `Product`, `ProductRevision`, puntero a revisión pública vigente.
- Verificación: CAT-CP-025, CAT-CP-026.
- Hecho cuando: una corrección genera una nueva revisión sin modificar la ficha pública vigente antes de su aprobación.

### [CAT-T-010] Implementar variantes y su relación con atributos

- Estado: pendiente. Depende de: CAT-T-008, CAT-T-009. Tamaño: 30–60 min.
- Requisitos/criterios: CAT-RF-005, CAT-RF-006; CAT-CA-023, 024.
- Módulos/contratos: `Variant`, `AttributeValue`, identidad de producto de ADE-006.
- Verificación: CAT-CP-023, CAT-CP-024.
- Hecho cuando: cambiar variante muestra únicamente sus especificaciones, precio e imagen propios; incompatibilidades se representan en fichas distintas.

### [CAT-T-011] Guardar fuentes técnicas e imágenes con permiso y texto alternativo

- Estado: pendiente. Depende de: CAT-T-009. Tamaño: 30–60 min.
- Requisitos/criterios: CAT-RF-004, CAT-RF-009, CAT-RF-010; CAT-CA-026, 029.
- Módulos/contratos: `FactSource`, `ProductImage`, `development-conventions.md`.
- Verificación: CAT-CP-026, CAT-CP-029.
- Hecho cuando: los hechos técnicos obligatorios tienen fuente interna y no se publica una imagen sin permiso verificado y alt.

### [CAT-T-012] Implementar precio, fecha y contenido pros/contras

- Estado: pendiente. Depende de: CAT-T-009, CAT-T-010.
- Requisitos/criterios: CAT-RF-007 a CAT-RF-009; CAT-CA-010, 023, 027, 028, 029.
- Módulos/contratos: `PriceEntry`, precisión de fecha, contenido editorial español.
- Verificación: CAT-CP-010, CAT-CP-023, CAT-CP-027, CAT-CP-028, CAT-CP-029.
- Hecho cuando: precio opcional se presenta como «Precio aproximado» en USD, fechas conservan su precisión y pros/contras están sustentados.

### [CAT-T-013] Validar checklist de publicación por categoría

- Estado: pendiente. Depende de: CAT-T-008 a CAT-T-012.
- Requisitos/criterios: CAT-RF-010, CAT-RF-011; CAT-CA-026.
- Módulos/contratos: servicio de validación editorial y mínimos de `category-data.md`.
- Verificación: CAT-CP-026 con una ficha candidata por cada categoría.
- Hecho cuando: cada campo obligatorio desconocido impide publicar; precio y fecha ausentes no bloquean.

### [CAT-T-014] Publicar atómicamente una nueva revisión

- Estado: pendiente. Depende de: CAT-T-009, CAT-T-013.
- Requisitos/criterios: CAT-RF-010; CAT-CA-025, 026.
- Módulos/contratos: `apps/editorial/`, transición de borrador a revisión y publicación.
- Verificación: CAT-CP-025, CAT-CP-026.
- Hecho cuando: solo un Revisor autorizado puede intercambiar el puntero público tras validar; se conserva la revisión anterior, se rechazan guardados obsoletos y el retiro quita la ficha de la vista pública.

### [CAT-T-015] Auditar cambios, revisiones periódicas y destacados manuales

- Estado: pendiente. Depende de: CAT-T-006, CAT-T-009, CAT-T-014.
- Requisitos/criterios: CAT-RF-001, CAT-RF-010, CAT-RF-011; CAT-CA-012, 017, 025, 040.
- Módulos/contratos: `EditorialEvent`, selección de destacados y actor/fecha.
- Verificación: CAT-CP-012, CAT-CP-017, CAT-CP-025, CAT-CP-039.
- Hecho cuando: cambios de publicación/retiro y revisiones periódicas quedan auditados; el equipo puede definir destacados iniciales.

## Fase C — Descubrimiento y fichas públicas

### [CAT-T-016] Crear layout público y estados de interfaz en español

- Estado: pendiente. Depende de: CAT-T-001.
- Requisitos/criterios: CAT-RF-019, CAT-RNF-001; CAT-CA-011, 041.
- Módulos/contratos: `templates/`, `static/`, navegación compartida.
- Verificación: CAT-CP-011, CAT-CP-040.
- Hecho cuando: navegación, controles y mensajes se muestran en español y distinguen estados de carga, error, vacío y dato no disponible.

### [CAT-T-017] Mostrar portada y destacados cuando no hay actividad válida

- Estado: pendiente. Depende de: CAT-T-015, CAT-T-016.
- Requisitos/criterios: CAT-RF-001; CAT-CA-012.
- Módulos/contratos: `apps/discovery/`, tarjetas de productos publicados.
- Verificación: CAT-CP-012, CAT-CP-018.
- Hecho cuando: sin aperturas válidas la portada presenta destacados vigentes y no les atribuye popularidad ficticia.

### [CAT-T-018] Registrar eventos de apertura desde resultados y calcular 30 días

- Estado: pendiente. Depende de: CAT-T-009, CAT-T-017.
- Requisitos/criterios: CAT-RF-001; CAT-CA-013, 018.
- Módulos/contratos: `ProductOpenEvent`, UTC, intervalo `(ahora - 30 días, ahora]`.
- Verificación: CAT-CP-013, CAT-CP-018 con evento dentro, justo en el límite y fuera de la ventana.
- Hecho cuando: cada apertura válida suma una vez, impresiones/directas/rastreadores no cuentan, no se guarda identificador personal y una tarea de mantenimiento elimina eventos expirados.

### [CAT-T-019] Implementar búsqueda normalizada de marca, modelo y nombre

- Estado: pendiente. Depende de: CAT-T-007, CAT-T-009.
- Requisitos/criterios: CAT-RF-002; CAT-CA-019.
- Módulos/contratos: `apps/discovery/`, query GET, normalización sin caja ni diacríticos.
- Verificación: CAT-CP-019.
- Hecho cuando: se cumple el límite de 100 caracteres y la relevancia inicial ordena coincidencias exactas, prefijos y parciales.

### [CAT-T-020] Implementar orden, desempates y paginación

- Estado: pendiente. Depende de: CAT-T-018, CAT-T-019, CAT-T-021.
- Requisitos/criterios: CAT-RF-016; CAT-CA-006, 019, 022.
- Módulos/contratos: `apps/discovery/`, orden por búsqueda, popularidad, fecha y precio.
- Verificación: CAT-CP-006, CAT-CP-019, CAT-CP-022.
- Hecho cuando: 24 resultados por página, orden explícito prevalece y empates/valores ausentes siguen reglas aprobadas.

### [CAT-T-021] Implementar filtros generales y rangos inclusivos

- Estado: pendiente. Depende de: CAT-T-007, CAT-T-008, CAT-T-012.
- Requisitos/criterios: CAT-RF-003, CAT-RF-017; CAT-CA-004, 020, 021.
- Módulos/contratos: filtros de categoría, marcas, precio y año.
- Verificación: CAT-CP-004, CAT-CP-020, CAT-CP-021.
- Hecho cuando: grupos distintos combinan AND, marcas combinan OR, límites son inclusivos y rango inválido no aplica sus extremos.

### [CAT-T-022] Implementar filtros técnicos y cambio de categoría

- Estado: pendiente. Depende de: CAT-T-008, CAT-T-021.
- Requisitos/criterios: CAT-RF-003, CAT-RF-006, CAT-RF-017; CAT-CA-005, 022, 024.
- Módulos/contratos: diccionario de filtros por categoría y unidades normalizadas.
- Verificación: CAT-CP-005, CAT-CP-022, CAT-CP-024.
- Hecho cuando: solo atributos definidos son filtrables; cambiar categoría limpia e informa filtros incompatibles.

### [CAT-T-023] Mostrar conteos, filtros activos y acción de limpieza

- Estado: pendiente. Depende de: CAT-T-021, CAT-T-022.
- Requisitos/criterios: CAT-RF-017; CAT-CA-007, 008, 021, 022.
- Módulos/contratos: formularios GET de resultados y estado validado de filtros.
- Verificación: CAT-CP-007, CAT-CP-008, CAT-CP-021, CAT-CP-022.
- Hecho cuando: conteo es previo a paginación, filtros activos se identifican y «Limpiar filtros» conserva búsqueda y orden.

### [CAT-T-024] Mostrar ficha pública y selector de variantes

- Estado: pendiente. Depende de: CAT-T-010 a CAT-T-012, CAT-T-016.
- Requisitos/criterios: CAT-RF-004 a CAT-RF-009; CAT-CA-023, 026 a 029.
- Módulos/contratos: página de detalle y revisión pública vigente.
- Verificación: CAT-CP-023, CAT-CP-026 a CAT-CP-029.
- Hecho cuando: la ficha presenta imagen, descripción, atributos, variante, precio, fecha y pros/contras sin mezclar datos ni inventar faltantes.

## Fase D — Participación, cuentas y moderación

### [CAT-T-025] Implementar identidad anónima de primera parte

- Estado: pendiente. Depende de: CAT-T-001, CAT-T-016.
- Requisitos/criterios: CAT-RF-012, CAT-RF-013; CAT-CA-031.
- Módulos/contratos: `AnonymousActor`, cookie segura de 12 meses, sin IP como identidad.
- Verificación: CAT-CP-031.
- Hecho cuando: el token original no se persiste, borrar cookie genera identidad nueva y no hay fusión automática al registrarse.

### [CAT-T-026] Implementar voto editable y conteos separados

- Estado: pendiente. Depende de: CAT-T-024, CAT-T-025, CAT-T-004.
- Requisitos/criterios: CAT-RF-012; CAT-CA-014, 030.
- Módulos/contratos: `UsefulnessVote`, unicidad actor/producto y transacción de reemplazo.
- Verificación: CAT-CP-014, CAT-CP-030.
- Hecho cuando: una identidad conserva un voto vigente por producto, lo cambia sin duplicar, no afecta popularidad y no puede votar por ficha retirada.

### [CAT-T-027] Recibir y validar comentarios

- Estado: pendiente. Depende de: CAT-T-024, CAT-T-025, CAT-T-004.
- Requisitos/criterios: CAT-RF-013; CAT-CA-001, 002, 031, 032.
- Módulos/contratos: `Comment`, texto plano, longitud 1–2.000 y límite por identidad.
- Verificación: CAT-CP-001, CAT-CP-002, CAT-CP-031, CAT-CP-032.
- Hecho cuando: comentario válido de una ficha publicada queda pendiente, confirmación visible y contenido no aprobado no aparece en ninguna respuesta pública; fichas retiradas no reciben comentarios.

### [CAT-T-028] Implementar aprobación y auditoría de moderación

- Estado: pendiente. Depende de: CAT-T-006, CAT-T-027.
- Requisitos/criterios: CAT-RF-015; CAT-CA-003, 015, 016, 033, 039.
- Módulos/contratos: permisos del Moderador designado y estados de comentario.
- Verificación: CAT-CP-003, CAT-CP-015, CAT-CP-016, CAT-CP-033, CAT-CP-038.
- Hecho cuando: solo Moderador puede aprobar/rechazar/retirar; únicamente aprobados se listan en orden reciente y cada acción queda auditada.

### [CAT-T-029] Implementar eliminación de cuenta y anonimización

- Estado: pendiente. Depende de: CAT-T-004, CAT-T-026 a CAT-T-028.
- Requisitos/criterios: CAT-RF-014, CAT-RNF-004; CAT-CA-035, 039.
- Módulos/contratos: servicio de eliminación y autoría pública de comentario.
- Verificación: CAT-CP-034.
- Hecho cuando: votos y comentarios pendientes se eliminan y los aprobados quedan bajo «Anónimo», sin exponer correo.

## Fase E — Calidad transversal

### [CAT-T-030] Implementar tema del sistema y preferencia manual

- Estado: pendiente. Depende de: CAT-T-016.
- Requisitos/criterios: CAT-RF-018; CAT-CA-009, 036.
- Módulos/contratos: `static/`, persistencia local del tema independiente del query.
- Verificación: CAT-CP-009, CAT-CP-035.
- Hecho cuando: primera visita sigue tema del dispositivo y selección manual persiste solo en ese navegador.

### [CAT-T-031] Asegurar límites de autorización y salida segura

- Estado: pendiente. Depende de: CAT-T-005, CAT-T-006, CAT-T-025 a CAT-T-029.
- Requisitos/criterios: CAT-RNF-004; CAT-CA-031, 033 a 035, 039.
- Módulos/contratos: permisos de servidor, CSRF, renderizado de texto y minimización de datos.
- Verificación: CAT-CP-031, CAT-CP-033, CAT-CP-034, CAT-CP-038.
- Hecho cuando: accesos directos sin permiso fallan, texto no ejecuta HTML y no se exponen credenciales, emails ni comentarios no públicos.

### [CAT-T-032] Verificar accesibilidad y adaptación móvil

- Estado: pendiente. Depende de: CAT-T-016, CAT-T-020 a CAT-T-030.
- Requisitos/criterios: CAT-RNF-002; CAT-CA-037.
- Módulos/contratos: vistas públicas y de equipo, teclado, foco, nombres y errores.
- Verificación: CAT-CP-036; revisión manual y auditoría WCAG 2.2 AA.
- Hecho cuando: controles operables con teclado, foco/errores visibles y sin scroll horizontal de página a 360 CSS px; hallazgos bloqueantes resueltos.

### [CAT-T-033] Instrumentar y medir rendimiento de campo

- Estado: pendiente. Depende de: CAT-T-001, CAT-T-016, CAT-T-019 a CAT-T-024.
- Requisitos/criterios: CAT-RNF-003; CAT-CA-038.
- Módulos/contratos: instrumentación respetuosa de privacidad y tablero/procedimiento tras elegir hosting.
- Verificación: CAT-CP-037.
- Hecho cuando: se registran LCP/INP/CLS p75 por dispositivo durante ventana de 28 días; si falta tráfico el resultado dice «no medible».

### [CAT-T-034] Completar validación de flujos y trazabilidad de ejecución

- Estado: pendiente. Depende de: CAT-T-001 a CAT-T-033.
- Requisitos/criterios: todos los CAT-RF y CAT-RNF.
- Módulos/contratos: suite Django, `tests/integration/`, `tests/flows/`, `traceability.md`.
- Verificación: CAT-CP-001 a CAT-CP-040 y CAT-CA-001 a CAT-CA-041.
- Hecho cuando: cada criterio tiene prueba implementada y resultado real; fallos e inmedibles quedan identificados, sin declarar éxito por cobertura parcial.

## Fase F — Gates operativos previos a producción

### [CAT-T-035] Definir proveedor, respaldos y recuperación

- Estado: pendiente, bloqueada hasta resolver PND-012. No bloquea el desarrollo local.
- Depende de: selección de presupuesto, hosting, región y responsables.
- Requisitos/criterios: decisiones operativas asociadas a CAT-RNF-003/004.
- Verificación: restauración ensayada con datos ficticios y evidencia de RPO/RTO acordados.
- Hecho cuando: proveedor y costos están aprobados, copias de datos/medios se restauran en ensayo y responsables están identificados.

### [CAT-T-036] Cerrar revisión legal y privacidad de los mercados elegidos

- Estado: pendiente, bloqueada hasta resolver PND-020. Requisito para habilitar cuentas/comentarios públicamente.
- Depende de: selección de jurisdicciones y revisión legal competente.
- Requisitos/criterios: CAT-RNF-004; CAT-CA-031, 033 a 035, 039.
- Verificación: políticas de privacidad, cookies, términos, retención y derechos de imágenes revisados para los mercados seleccionados.
- Hecho cuando: decisiones y evidencias de revisión están registradas antes de publicación pública.

### [CAT-T-037] Resolver marca y dominio antes de publicar

- Estado: pendiente, bloqueada hasta resolver PND-021. No bloquea diseño ni desarrollo local.
- Depende de: decisión de nombre y disponibilidad de activos/dominio.
- Requisitos/criterios: ninguno funcional; gate de publicación.
- Verificación: nombre, dominio y permisos de marca confirmados por el responsable.
- Hecho cuando: los activos aprobados sustituyen el nombre interno «Catálogo» en la publicación.

## Orden y gates

Las fases A–E constituyen el trabajo planificado para la versión inicial y requieren
una instrucción explícita de implementación antes de ejecutarse. Las tareas
CAT-T-035 a CAT-T-037 no se inician hasta resolver sus decisiones PND respectivas;
no deben adelantarse ni bloquear desarrollo que no dependa de ellas. Tras completar
las tareas funcionales se debe ejecutar la verificación de CAT-T-034 antes de
declarar cumplimiento de la spec.
