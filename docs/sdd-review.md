# Registro de revisión correctiva SDD

Revisión: `REV-SDD`  
Alcance: baseline del catálogo gaming; spec 0.20 → 0.21, plan 0.3 → 0.4.  
Autorización: el responsable solicitó implementar el plan de correcciones.  
Estado: correcciones aplicadas; verificación documental registrada al cierre.

## Hallazgos y resolución

| ID | Hallazgo | Resolución | Artefactos principales | Estado |
|---|---|---|---|---|
| REV-SDD-001 | El modelo ER exigía autoría para votos/comentarios, pero se requería conservar comentarios aprobados tras borrar la cuenta. | Aportes nuevos exigen exactamente una identidad; comentarios aprobados retenidos tras borrar cuenta quedan sin ambas referencias. | `spec.md` CAT-CA-044/045; `plan.md`; `acceptance.md` CAT-CP-043 | Resuelto |
| REV-SDD-002 | La tabla de permisos asignaba publicación al Editor en conflicto con los roles acordados. | Editor crea/edita y envía borradores; Revisor publica/retira; Moderador designado modera comentarios. | `spec.md`; `plan.md`; `acceptance.md`; `implementation-backlog.md` | Resuelto |
| REV-SDD-003 | Filtros técnicos y de precio podían combinar datos de variantes distintas. | Todos esos filtros deben coincidir en una misma variante; el producto y el conteo aparecen una vez. | `spec.md` CAT-CA-042; `decisions.md` ADE-020; `acceptance.md` CAT-CP-041 | Resuelto |
| REV-SDD-004 | No se definía qué variante representa una tarjeta ni qué selección llega a la ficha/URL. | Se define variante representante dentro del conjunto coincidente, desempates, variante predeterminada solo si coincide, enlace con clave, URL directa y respuesta ante clave retirada. | `spec.md` CAT-CA-023/043; `decisions.md` ADE-020; `acceptance.md` CAT-CP-042 | Resuelto |
| REV-SDD-005 | El borrado de cuenta no invalidaba explícitamente sesiones ni aclaraba identidad recreada con el mismo correo. | Se invalidan sesiones; se borran votos y aportes no públicos; comentarios aprobados quedan anónimos; nuevo registro no recupera aportes. | `spec.md` CAT-CA-035/045; `decisions.md` ADE-021; `acceptance.md` CAT-CP-043 | Resuelto |
| REV-SDD-006 | La caducidad anónima no aclaraba la retención de aportes ni cuándo se borra el hash. | Vencimiento exacto a los 365 días; en ese instante el token deja de autenticar y se borra el hash; se conserva identidad interna solo para sostener aportes. | `spec.md` CAT-CA-046; `plan.md`; `decisions.md` ADE-021; `acceptance.md` CAT-CP-045 | Resuelto |
| REV-SDD-007 | El diccionario no especificaba tipo, unidad, cardinalidad y validación concretos para cada campo. | Se completan esquemas por categoría; se fijan conversiones de capacidad, resolución y validación al guardar/publicar. | `category-data.md`; `spec.md` CAT-CA-047; `decisions.md` ADE-022; `acceptance.md` CAT-CP-044 | Resuelto |
| REV-SDD-008 | El precio ausente se excluía de filtros y podía no tener posición definida en orden por precio. | Sigue sin coincidir con un rango; en orden ascendente y descendente queda después de precios conocidos. | `spec.md` CAT-CA-027; `decisions.md` ADE-023; `acceptance.md` CAT-CP-027 | Resuelto |
| REV-SDD-009 | No era inequívoco si el orden elegido o la relevancia prevalecían, ni cómo ordenar fechas parciales. | Orden elegido es principal; relevancia desempata antes de nombre/slug. Fechas usan tupla descendente `(año, mes conocido o 0, día conocido o 0)` y conservan precisión visible. | `spec.md` CAT-CA-019/022/028; `decisions.md` ADE-023; `acceptance.md` CAT-CP-022/028/046 | Resuelto |

## Efectos en el paquete SDD

- La revisión añade seis criterios: CAT-CA-042 a CAT-CA-047; total vigente: 47.
- Se añaden seis escenarios CAT-CP-041 a CAT-CP-046; total vigente: 46.
- `traceability.md` enlaza cada criterio con al menos un escenario y una tarea futura.
- El backlog define CAT-T-038 para medir los objetivos de rendimiento en campo tras despliegue y una ventana válida de 28 días. CAT-T-033 solo instala la instrumentación y CAT-T-034 no declara cumplimiento de campo.
- Se eliminan dependencias circulares: CAT-T-035/036/037 son el trabajo que cierra sus gates; CAT-T-038 depende de los gates cerrados.
- No se escribió código funcional, no se instalaron dependencias y no se ejecutaron pruebas del producto.

## Verificación documental

La verificación documental obtuvo 47 CAT-CA, 46 CAT-CP y 47 filas de trazabilidad;
cada criterio enlaza al menos un escenario y una tarea existente. El control de
enlaces locales encontró cero enlaces rotos y `git diff --check` no señaló errores
de espacios. Los casos CAT-CP siguen diseñados y no ejecutados.
