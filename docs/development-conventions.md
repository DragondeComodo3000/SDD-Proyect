# Convenciones de desarrollo

Versión: 1.0. Estado: **aprobada como parte de la baseline el 2026-10-26**. Se
adapta de forma selectiva la constitución técnica de DINOCO, facilitada como
referencia. No hereda su dominio, sus obligaciones de repositorio ni la aprobación
de su equipo.

## Propósito y precedencia

Este documento define cómo organizar y mantener el futuro código del catálogo.
La spec aprobada define el comportamiento; estas reglas técnicas no pueden crear
funciones o políticas para usuarios. La constitución del proyecto gobierna los
principios.

Usar los niveles siguientes al convertirla en norma:

- **MUST:** obligatorio y comprobable.
- **SHOULD:** recomendado; una excepción se registra con motivo.
- **MAY:** opcional según necesidad demostrada.

## Idioma y nombres

- **MUST:** documentación, interfaz, contenido del catálogo y mensajes dirigidos
  a participantes en español, conforme a DEC-014.
- **MUST:** identificadores de código, módulos, variables, tablas y
  columnas en inglés; el inglés no cambia el idioma visible del sitio.
- **MUST:** el vocabulario de dominio se define una vez en el plan y se usa de
  forma consistente en todos los módulos.
- **MUST:** vincular cambios de código con IDs CAT-RF, CAT-CA o CAT-PLAN; no
  incorporar reglas de negocio desde comentarios o nombres técnicos.

## Estructura física aprobada

Una sola aplicación Django organizada por funcionalidades, con límites internos
claros:

```text
repo/
├── AGENTS.md
├── README.md
├── pyproject.toml
├── .python-version
├── .gitignore
├── .env.example
├── manage.py
├── config/
│   ├── settings/
│   │   ├── base.py
│   │   ├── development.py
│   │   └── production.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
├── apps/
│   ├── catalog/
│   ├── discovery/
│   ├── community/
│   ├── accounts/
│   └── editorial/
├── templates/
├── static/
├── tests/
│   ├── integration/
│   └── flows/
└── docs/
```

### ¿Un árbol o dos?

El árbol anterior corresponde a la arquitectura aprobada: Django renderiza las
páginas. El frontend reside dentro de la misma aplicación, en `templates/` y
`static/`; no existe un proyecto frontend independiente.
`apps/` y `config/` contienen el backend Django.

Las apps contendrán su propio modelo, rutas, vistas/formularios, administración
y tests unitarios cuando corresponda. `tests/flows/` recorre flujos HTTP completos
con el cliente de pruebas de Django; no significa pruebas automatizadas en
navegador. La revisión de teclado, viewport y accesibilidad se documenta como
verificación manual del producto. No se añade Playwright al MVP.

Las responsabilidades lógicas se ubican así: `catalog`, `discovery`, `community`,
`accounts` y `editorial` corresponden a `apps/<módulo>/`; `config` corresponde a
`config/`; `web` es responsabilidad transversal en `config/urls.py`, las rutas y
vistas de cada app, más `templates/` y `static/`. No se crea una app `web` vacía.

La vista HTTP coordina entrada y respuesta;
las reglas de dominio se ubican en servicios o funciones de dominio cuando su
complejidad lo justifique. Consultas compartidas se extraen solo si mejoran la
claridad. No crear capas vacías, paquetes separados ni microservicios por simetría.

`templates/` y `static/` alojan recursos públicos de servidor. Las imágenes reales
de catálogo y secretos no se guardan en Git. Los ejemplos, fixtures y cuentas de
prueba son sintéticos. El layout final puede variar por una necesidad documentada.

## Stack y herramientas

### Base que mejor encaja con el alcance actual

La arquitectura Django con HTML renderizado por servidor quedó confirmada por
DEC-024. Se conserva la base de versiones propuestas en ADE-016: Python 3.13,
Django 6.1 y PostgreSQL 18, sujetas a revalidación previa a implementación.
Django Admin sirve para operaciones sencillas; los flujos
de publicación y moderación usan pantallas propias cuando necesiten pasos,
permisos o auditoría específicos.

Motivo: el MVP requiere un catálogo consultable, filtros, cuentas opcionales,
formularios y trabajo editorial manual. Una aplicación integrada concentra el
despliegue y evita mantener por separado una API y un cliente web sin requisito
confirmado que los exija.

### Stack de la constitución de referencia

Node.js 24, TypeScript 6, NestJS 11, Prisma 7, React 19/Vite y PostgreSQL 18
**son técnicamente aplicables**, y se pueden usar para construir el mismo producto.
PostgreSQL 18 también es aplicable junto con Django. NestJS/React sería una
alternativa razonable si el equipo ya domina TypeScript, necesita una API pública
o varios clientes, o la interfaz requiere interacciones cliente complejas; DEC-024
la deja fuera del MVP actual.
Para el alcance descrito agrega una separación frontend/API, contratos de red,
tipado generado y más piezas de operación; por eso no sustituye automáticamente
la arquitectura Django confirmada.

No se recomienda mezclar Django con NestJS/Prisma como dos backends ni añadir
React/Vite al MVP. Se reconsideraría una arquitectura completa si una necesidad
concreta justifica mantener frontend y API separados.

No se adopta por ahora React Query, DTOs/OpenAPI, Prisma, npm workspaces ni la
estructura monorepo de DINOCO: cada elemento depende de escoger el stack separado.
La comparación es una evaluación, no un veto ni una decisión definitiva.

### Herramientas Python aprobadas para el MVP

- **Dependencias:** `uv` con `pyproject.toml`; versionar `uv.lock` para mantener
  instalaciones reproducibles. No mantener un segundo lockfile equivalente.
- **Pruebas:** usar el test runner incluido en Django y `django.test.TestCase`;
  ejecutar `uv run python manage.py test`. No añadir pytest al MVP sin una
  necesidad concreta.
- **Formato y lint:** Ruff, con `uv run ruff format --check .` y
  `uv run ruff check .`.
- **Base local:** Docker Compose con PostgreSQL 18, imagen etiquetada por major;
  ejecutar la misma major en CI para probar consultas, restricciones y migraciones.
- **Comprobaciones comunes de CI:** `uv lock --check`, formato Ruff, lint Ruff,
  `uv run python manage.py check`,
  `uv run python manage.py makemigrations --check --dry-run` y
  `uv run python manage.py test`.
- **Proveedor de CI:** queda ligado al hosting Git que el equipo elija; el orden y
  los comandos anteriores no dependen de GitLab o GitHub.

Las versiones concretas de uv, Django, Ruff y PostgreSQL se revalidan y fijan en
los archivos de configuración antes de implementar; se actualizan mediante un
cambio revisado. Esta baseline no instala herramientas.

La documentación oficial consultada indica que Django 6.1 admite Python 3.12–3.15
y PostgreSQL 15 o posterior; PostgreSQL 18 tiene soporte oficial hasta noviembre
de 2030. NestJS también admite el runtime Node actual de línea LTS y React 19 está
publicado oficialmente. Esto confirma compatibilidad general de los candidatos,
no que un stack sea mejor para el equipo. El criterio de simplicidad favorece
Django para el alcance actual; esta última es una inferencia de arquitectura.

Fuentes oficiales consultadas el 26-10-2026: [Django 6.1](https://docs.djangoproject.com/en/6.1/releases/6.1/),
[versiones compatibles de PostgreSQL](https://www.postgresql.org/support/versioning/),
[uv y su lockfile](https://docs.astral.sh/uv/concepts/projects/layout/),
[Ruff](https://docs.astral.sh/ruff/) y
[pruebas en Django](https://docs.djangoproject.com/en/6.1/topics/testing/overview/).

## Git y revisión de cambios

Flujo neutral al proveedor, adaptado de GEN-07 a GEN-10. GitLab, GitHub u otra
plataforma pueden aplicar estas mismas reglas:

- **MUST:** proteger `main`; no hacer push directo; integrar por Pull Request o
  Merge Request con al menos una aprobación de otra persona y CI verde.
- **MUST:** ramas cortas por propósito: `feat/<id>-<slug>`, `fix/<id>-<slug>`,
  `docs/<slug>` y `chore/<slug>`. El ID es CAT-RF/CAT-PLAN cuando corresponda.
- **MUST:** mensajes Conventional Commits en inglés y minúscula,
  `<type>(<scope>): <imperative subject>`; tipos iniciales `feat`, `fix`,
  `docs`, `refactor`, `test`, `chore` y `perf`.
- **MUST:** cada PR/MR describe el propósito, referencia los IDs cubiertos,
  criterios y evidencia de verificación; incluye cambios documentales afectados.
- **MUST:** nunca versionar secretos, `.env` real, datos personales ni imágenes sin
  permiso verificable. Mantener `.env.example` con valores ficticios.
- No se exige rama de release, squash ni trailer de coautoría para este MVP.

Los commits y el código quedan en inglés; la documentación y el producto quedan
en español. DEC-014 solo fija el idioma dirigido al público; esta convención
técnica define los idiomas internos.

## Pruebas, CI y Definition of Done

- Cada criterio CAT-CA implementado tendrá prueba automatizada pertinente; los
  flujos principales se cubrirán también desde la interfaz cuando sea viable.
- Validar comportamiento, permisos y estados visibles; no acoplar pruebas a
  nombres privados o detalles internos sin valor observable.
- Proteger restricciones de unicidad y consistencia en la base de datos cuando
  apliquen; validar permisos en servidor aunque la interfaz oculte acciones.
- La tarea termina cuando cumple los criterios asignados, lint y tests acordados
  pasan, no contiene secretos/datos reales, actualiza artefactos SDD afectados y
  deja evidencia del comando y resultado ejecutados.
- La CI debe aplicar los mismos comandos y versiones acordados para el equipo.
  Un paso sin ejecutar se registra como pendiente, nunca como exitoso.

## Decisiones operativas diferidas

Antes de implementar se revalidarán versiones concretas compatibles y se fijarán
en el lockfile. El equipo elegirá un proveedor CI antes de configurar el pipeline.
DEC-024 confirma la arquitectura Django del MVP. La alternativa NestJS/React/Vite
queda descartada para el alcance actual; reabrirla requeriría una nueva decisión
de alcance o una necesidad técnica documentada.
