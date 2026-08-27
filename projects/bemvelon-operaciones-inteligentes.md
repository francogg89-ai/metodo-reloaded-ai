# PROJECT — Bemvelon Operaciones Inteligentes

Metadatos estables del proyecto Bemvelon Operaciones Inteligentes para Metodo-Reloaded-AI.

Este archivo describe identidad, fuentes canónicas conocidas, entornos materiales estables y el
puntero para reconstruir los trabajos del proyecto. No almacena estado vivo de trabajos ni
decisiones que pertenezcan a un carril concreto.

## Identidad

```text
PROJECT_ID=bemvelon-operaciones-inteligentes
CANONICAL_REPO=francogg89-ai/Bemvelon-automatizado
CANONICAL_BRANCH=main
```

## Naturaleza estable del proyecto

El proyecto reúne los trabajos destinados a mejorar y automatizar la operación de Bemvelon
mediante integraciones con Fudo y componentes propios, preservando separación entre fuentes
autoritativas, datos derivados, reglas de negocio y automatizaciones.

La prioridad inicial conocida del proyecto es desarrollar capacidades de lectura de stock,
reposición y apoyo a compras a partir de la API de Fudo. Otras capacidades podrán incorporarse
mediante trabajos independientes aprobados conforme al método.

Este archivo no fija el alcance ni el orden de esos trabajos: cada uno se constituye mediante
su propio manifiesto.

## Fuentes canónicas relevantes

### Repositorio canónico del proyecto

```text
REPO=francogg89-ai/Bemvelon-automatizado
BRANCH=main
```

| Ruta | Función estable como fuente |
|---|---|
| `MANIFIESTO_TRABAJO.md` | Manifiesto aprobado del trabajo `discovery-api-fudo-stock-reposicion`. La identidad exacta aplicable a su ejecución debe fijarse en el baseline del trabajo. |
| artefactos documentales y técnicos futuros | Material producido por trabajos aprobados del proyecto. Su mera presencia no sustituye los gates ni el estado derivado de cada carril. |

### Fudo

```text
EXTERNAL_SYSTEM=Fudo
ACCOUNT_CONTEXT=Bemvelon
PLAN=Pro
```

Fudo es una fuente externa relevante para ventas, productos, stock, compras y otras entidades
operativas que su API exponga y que sean materialmente verificadas por los trabajos
correspondientes.

La documentación pública y la API real de Fudo son fuentes técnicas externas. Las credenciales,
tokens y secretos nunca se registran en este archivo ni en Git.

### Repositorio del método

```text
METHOD_REPO=francogg89-ai/metodo-reloaded-ai
METHOD_BRANCH=main
```

| Ruta | Función estable como fuente |
|---|---|
| `metodo/` | Documentos canónicos de Metodo-Reloaded-AI. |
| `roles/PROCEDIMIENTOS_COMPARTIDOS.md` | Procedimientos compartidos, incluida la reconstrucción lógica de trabajos activos. |
| `roles/` | Instrucciones operativas de constructor y auditor. |
| `templates/project/PROJECT.md` | Template de este mapa de proyecto. |

La referencia exacta del método y de las demás fuentes que gobiernan un trabajo concreto
pertenece a ese trabajo y no se duplica acá.

## Entornos materiales conocidos

En la etapa actual no se declara todavía una topología estable completa de entornos técnicos
propios del proyecto.

Se conocen como recursos externos o de infraestructura potencialmente relevantes:

- cuenta operativa de Fudo de Bemvelon;
- API de Fudo habilitada para el restaurante;
- infraestructura propia basada en Coolify, cuya función concreta deberá fijarse en trabajos
  posteriores antes de considerarla entorno estable del proyecto.

No se registran acá URLs privadas, IDs de cuenta, tokens, secrets ni credenciales.

## Taxonomía de recursos

La taxonomía se mantiene deliberadamente mínima hasta que los trabajos técnicos demuestren qué
identidades necesitan estabilidad entre carriles.

| Tipo de recurso | Forma del identificador lógico | Alcance |
|---|---|---|
| `fudo_resource` | `fudo:<resource_kind>:<stable_id>` | Entidad de Fudo referenciada por un identificador estable expuesto por la API. |
| `business_rule` | `rule:<slug>` | Regla de negocio propia de Bemvelon que no pertenece a Fudo y cuya estabilidad haya sido demostrada por un trabajo aprobado. |
| `automation_surface` | `automation:<slug>` | Superficie o servicio propio de automatización cuando un trabajo posterior lo constituya como recurso estable. |

Los nombres físicos de tablas, servicios, workflows o aplicaciones no se elevan a taxonomía
estable mientras no haya un trabajo que demuestre su permanencia.

## Cómo reconstruir los trabajos activos

```text
PROJECT_ID=bemvelon-operaciones-inteligentes
WORK_REPO_PATTERN=francogg89-ai/work-claude-<carril_en_minuscula>
AUDIT_REPO_PATTERN=francogg89-ai/audit-chatgpt-<carril_en_minuscula>
WORK_ID_PATH=00_control/WORK_ID.md
```

Puntero de reconstrucción: consultar los pares `work-claude-*` / `audit-chatgpt-*`
existentes, seleccionar únicamente los trabajos cuyo `00_control/WORK_ID.md` declare
`PROJECT_ID=bemvelon-operaciones-inteligentes` y re-derivar existencia, terminalidad,
ownership, candidato y estado desde los eventos append-only conforme al procedimiento vigente
del método.

El resultado de esa derivación no se almacena en este archivo.
