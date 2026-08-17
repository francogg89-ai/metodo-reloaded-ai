# PROJECT — Vita Delta Reservas

Metadatos estables del proyecto Vita Delta Reservas para Metodo-Reloaded-AI.
Este archivo describe identidad, fuentes, clases de entorno, taxonomía de recursos y el
puntero de reconstrucción de trabajos. No almacena estado vivo.

## Identidad

```text
PROJECT_ID=vita-delta-reservas
CANONICAL_REPO=francogg89-ai/vita-delta-reservas
CANONICAL_BRANCH=main
```

## Fuentes canónicas relevantes

### Repositorio del proyecto

```text
REPO=francogg89-ai/vita-delta-reservas
BRANCH=main
```

| Ruta | Función estable como fuente |
|---|---|
| `Docs/Arquitectura/` | Decisiones y contratos arquitectónicos del proyecto. El trabajo concreto fija los documentos y la identidad exacta que le correspondan. |
| `Docs/Implementacion/6B_SCHEMA_SQL.md` | Schema PostgreSQL canónico y fuente técnica para objetos de base de datos. |
| `Docs/Implementacion/` | Documentación de implementación, bootstrap y procedimientos técnicos relacionados con la materialización del sistema. |
| `Docs/Supabase/` | Guías, runbooks y material técnico específico de Supabase. |
| `Docs/API_CONTRACTS/` | Contratos técnicos de interfaces determinísticas y workflows. |
| `Workflows/n8n/Supabase/` | Templates sanitizados de workflows n8n contra Supabase/PostgreSQL. |
| `Apps/portal-operativo/` | Código fuente del Portal Operativo. |
| `Docs/Implementacion/Carril_C/PORTAL_FRONTEND/` | Contratos de la interfaz Portal ↔ gateway/backend. El trabajo concreto fija el documento y la identidad exacta que le correspondan. |
| `Docs/Bitacora/` | Evidencia histórica de ejecución, cierres y trazabilidad. Es fuente histórica; no sustituye la derivación del estado vivo. |
| `Docs/Operacional/DECISIONES_NO_REABRIR.md` | Registro de decisiones de proyecto declaradas como no reabribles. |
| `Docs/Operacional/Lecciones_Aprendidas.md` | Lecciones y restricciones operativas acumuladas del proyecto. |

### Repositorio del método

```text
METHOD_REPO=francogg89-ai/metodo-reloaded-ai
METHOD_BRANCH=main
```

| Ruta | Función estable como fuente |
|---|---|
| `metodo/` | Documentos canónicos del método. |
| `roles/PROCEDIMIENTOS_COMPARTIDOS.md` | Procedimientos compartidos, incluida la reconstrucción lógica de trabajos activos. |
| `roles/` | Instrucciones operativas de los roles. |
| `templates/project/PROJECT.md` | Template de este mapa de proyecto. |

La referencia exacta del método y las referencias exactas del proyecto que gobiernan un
trabajo concreto pertenecen a ese trabajo; no se duplican acá.

## Entornos materiales conocidos

| Entorno | Propósito estable |
|---|---|
| `DEV` | Desarrollo, reconstrucción e integración técnica aislada de la operación real. |
| `TEST` | Verificación material e integración previa a la operación real, separada de `OPS`. |
| `OPS` | Operación real interna de Vita Delta; se trata como entorno real y no como entorno de prueba. |

No se registran acá IDs de proyectos Supabase, URLs, credenciales, secrets, fingerprints, versiones
instaladas ni paridad entre entornos.

## Taxonomía de recursos

Los identificadores siguientes son **lógicos y agnósticos de entorno**. El entorno material
se registra por separado cuando un trabajo necesita distinguir `DEV`, `TEST` u `OPS`.

| Tipo de recurso | Forma del identificador lógico | Alcance |
|---|---|---|
| `postgres_object` | `postgres:<kind>:<qualified_name>` | Objetos del backend PostgreSQL/Supabase: tablas, vistas, funciones, secuencias, constraints, triggers, policies y otros objetos de schema. Para funciones, `<qualified_name>` incluye firma cuando sea necesaria para desambiguar. |
| `n8n_workflow` | `n8n:<workflow_name>` | Workflow n8n identificado por su nombre lógico/canónico. No usar el ID numérico/runtime de n8n como identidad lógica. |
| `supabase_edge_function` | `edge:<function_slug>` | Edge Function de Supabase identificada por su slug estable, independientemente del entorno donde exista una instancia. |
| `supabase_auth_surface` | `auth:<surface_slug>` | Superficie de autenticación/autorización basada en Supabase Auth asociada a una aplicación o gateway del proyecto. |
| `portal_frontend` | `portal:<surface_slug>` | Frontend interno del Portal Operativo y sus superficies funcionales. |
| `public_web` | `web:<surface_slug>` | Superficie web pública del proyecto, separada del portal interno. |

Las rutas documentales, contratos y bitácoras son **fuentes sobre recursos**, no instancias
materiales de esta taxonomía.

## Cómo reconstruir los trabajos activos

```text
PROJECT_ID=vita-delta-reservas
WORK_REPO_PATTERN=francogg89-ai/work-claude-<carril_en_minuscula>
AUDIT_REPO_PATTERN=francogg89-ai/audit-chatgpt-<carril_en_minuscula>
WORK_ID_PATH=00_control/WORK_ID.md
```

Puntero de reconstrucción: consultar todos los pares `work-claude-*` / `audit-chatgpt-*`
existentes, seleccionar únicamente los trabajos cuyo `00_control/WORK_ID.md` declare
`PROJECT_ID=vita-delta-reservas` y re-derivar su existencia, terminalidad y ownership
desde los eventos append-only conforme al procedimiento vigente del método.

El resultado de esa derivación —trabajos activos, carril actual, candidato, SHAs, estado y
ownership— no se almacena en este archivo.
