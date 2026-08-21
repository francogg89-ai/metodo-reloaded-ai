# PROJECT — Equity

Metadatos estables del proyecto Equity para Metodo-Reloaded-AI.

Este archivo describe la identidad estable del proyecto, sus fuentes canónicas conocidas,
su taxonomía documental mínima y el puntero para reconstruir sus trabajos. No almacena
estado vivo de trabajos ni determina qué ideas constituyen el canon intelectual vigente de
Equity.

## Identidad

```text
PROJECT_ID=equity
CANONICAL_REPO=francogg89-ai/Equity-corpus
CANONICAL_BRANCH=main
```

`Equity` es actualmente el nombre de trabajo del proyecto y del cuerpo de ideas. No implica
que una futura organización deba conservar necesariamente ese nombre.

El carácter canónico de `Equity-corpus` en esta etapa es **documental**: es la fuente
autoritativa del corpus histórico reunido sobre el proyecto. No implica que todo contenido
presente en el repositorio represente una posición vigente o canónica de Equity.

## Fuentes canónicas relevantes

### Corpus documental de Equity

```text
REPO=francogg89-ai/Equity-corpus
BRANCH=main
```

| Ruta | Función estable como fuente |
|---|---|
| `01_material_propio/` | Material propio e histórico relacionado con Equity: documentos, borradores, fundamentos, propuestas, versiones, notas y otros materiales producidos durante la evolución del proyecto. |
| `02_extracciones_chatgpt/` | Fuentes derivadas de conversaciones sobre Equity. Preservan y estructuran conocimiento surgido en esas conversaciones, pero no sustituyen las fuentes primarias ni constituyen canon por sí mismas. |
| `README.md` | Descripción general y reglas básicas de interpretación del corpus. |
| `MANIFIESTO_TRABAJO.md` | Manifiesto aprobado del primer trabajo formal orientado a constituir el corpus maestro y preparar la arquitectura posterior. Su identidad exacta para ejecución debe fijarse en el baseline del trabajo. |

Regla documental fundamental:

> **Estar presente en el corpus no significa que Equity sostenga actualmente esa posición.**

Las fuentes pueden contener ideas vigentes, históricas, contradictorias, experimentales,
superadas o todavía no evaluadas. La evolución intelectual debe poder reconstruirse sin
destruir esas diferencias.

### Repositorio del método

```text
METHOD_REPO=francogg89-ai/metodo-reloaded-ai
METHOD_BRANCH=main
```

| Ruta | Función estable como fuente |
|---|---|
| `metodo/` | Documentos canónicos de Metodo-Reloaded-AI. |
| `roles/PROCEDIMIENTOS_COMPARTIDOS.md` | Procedimientos compartidos, incluida la reconstrucción lógica de trabajos activos. |
| `roles/` | Instrucciones operativas de los roles. |
| `templates/project/PROJECT.md` | Template de este mapa de proyecto. |

La referencia exacta del método y las referencias exactas del corpus que gobiernan un
trabajo concreto pertenecen a ese trabajo; no se duplican acá.

## Naturaleza estable del proyecto

Equity es un proyecto de investigación, construcción intelectual y eventual experimentación
institucional orientado al desarrollo de nuevas formas de organización económica, social y
tecnológica.

Su conocimiento puede evolucionar. El repositorio documental debe permitir preservar esa
evolución, incluidas versiones históricas, contradicciones, hipótesis y mecanismos que puedan
ser posteriormente revisados o descartados.

La determinación concreta de qué constituye principio, hipótesis, argumento, mecanismo,
objeción, tensión, formulación superada o canon vigente pertenece a trabajos específicos y no
se almacena como estado vivo en este archivo.

## Entornos materiales conocidos

En la etapa actual, Equity no posee entornos técnicos operativos estables equivalentes a
`DEV`, `TEST` u `OPS`.

El proyecto se encuentra inicialmente centrado en:

- corpus documental;
- investigación;
- construcción de conocimiento;
- diseño institucional;
- trabajos asistidos por agentes de IA.

Si en el futuro aparecen plataformas, servicios, sistemas productivos o entornos técnicos
estables, su definición podrá incorporarse aquí mediante una modificación explícita de este
archivo.

## Taxonomía de recursos

La taxonomía estable se mantiene deliberadamente mínima en esta etapa para no anticipar la
arquitectura intelectual que debe surgir de trabajos posteriores.

| Tipo de recurso | Forma del identificador lógico | Alcance |
|---|---|---|
| `source_document` | `source:<slug>` | Documento o fuente primaria incorporada al corpus. |
| `derived_extraction` | `extraction:<slug>` | Extracción o representación derivada de una fuente o conversación. |

La existencia de una fuente o extracción no implica que su contenido haya sido aprobado como
parte del canon intelectual vigente.

Nuevos tipos de recurso sólo deberían incorporarse aquí cuando hayan demostrado ser estables
a través de los trabajos que los utilizan.

## Separación entre corpus y conocimiento derivado

En la etapa inicial, `francogg89-ai/Equity-corpus` es la fuente documental histórica canónica
del proyecto.

Se prevé que trabajos posteriores puedan producir uno o más repositorios derivados destinados
a conocimiento estructurado, mapas conceptuales, reconstrucción histórica, canon,
investigaciones externas u otras funciones.

Esos repositorios no se declaran anticipadamente aquí. Su creación, identidad y función deben
resultar de trabajos aprobados y, una vez estabilizados como infraestructura permanente del
proyecto, podrán incorporarse como fuentes canónicas relevantes mediante actualización de
este archivo.

## Cómo reconstruir los trabajos activos

```text
PROJECT_ID=equity
WORK_REPO_PATTERN=francogg89-ai/work-claude-<carril_en_minuscula>
AUDIT_REPO_PATTERN=francogg89-ai/audit-chatgpt-<carril_en_minuscula>
WORK_ID_PATH=00_control/WORK_ID.md
```

Puntero de reconstrucción: consultar los pares `work-claude-*` / `audit-chatgpt-*`
existentes, seleccionar únicamente los trabajos cuyo `00_control/WORK_ID.md` declare
`PROJECT_ID=equity` y re-derivar su existencia, terminalidad y ownership desde los eventos
append-only conforme al procedimiento vigente del método.

El resultado de esa derivación —trabajos activos, carril actual, candidato, SHAs, estado y
ownership— no se almacena en este archivo.
