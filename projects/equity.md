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

## Linaje nominal estable

Los nombres `Arrebol`, `UnIdeas` y `Equity` corresponden a etapas nominales sucesivas del
mismo proyecto intelectual, no a tres proyectos independientes:

```text
Arrebol
    ↓
primer nombre histórico

UnIdeas
    ↓
segundo nombre histórico

Equity
    ↓
nombre de trabajo actual
```

`Equity` sigue siendo un nombre de trabajo. Si en el futuro existe una comunidad capaz de
materializar el proyecto, esa comunidad podrá decidir colectivamente otro nombre, identidad,
símbolos u otros elementos fundacionales. Este archivo no anticipa cuál sería esa identidad
futura.

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

### Conocimiento derivado estructurado de Equity

```text
REPO=francogg89-ai/Equity-knowledge
BRANCH=main
```

`Equity-knowledge` es el repositorio estable destinado al conocimiento derivado estructurado
y trazable del proyecto. No sustituye a `Equity-corpus`: deriva de sus fuentes y debe
conservar la posibilidad de reconstruir razonablemente la procedencia del conocimiento que
aloje.

| Ruta | Función estable como fuente |
|---|---|
| `MANIFIESTO_TRABAJO.md` | Manifiesto aprobado de `derivacion-piezas-intelectuales-equity`, trabajo destinado a constituir la primera base de conocimiento intelectual estructurado y trazable de Equity. |
| contenido derivado futuro | Conocimiento estructurado producido mediante trabajos aprobados. Su mera presencia en este repositorio no implica por sí sola pertenencia al canon doctrinario vigente de Equity. |

Separación estable:

```text
Equity-corpus
    = memoria documental histórica canónica

Equity-knowledge
    = conocimiento derivado estructurado y trazable
```

La existencia de una representación en `Equity-knowledge` tampoco equivale automáticamente a
que Equity la sostenga actualmente. La determinación de canon o vigencia doctrinaria requiere
trabajos y decisiones explícitas que correspondan.

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

La referencia exacta del método y las referencias exactas de las fuentes que gobiernan un
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
- conocimiento derivado estructurado;
- investigación;
- construcción de conocimiento;
- diseño institucional;
- trabajos asistidos por agentes de IA.

Si en el futuro aparecen plataformas, servicios, sistemas productivos o entornos técnicos
estables, su definición podrá incorporarse aquí mediante una modificación explícita de este
archivo.

## Taxonomía de recursos

La taxonomía estable se mantiene deliberadamente mínima en esta etapa para no anticipar la
arquitectura intelectual que debe demostrar estabilidad mediante los trabajos que la
construyan.

| Tipo de recurso | Forma del identificador lógico | Alcance |
|---|---|---|
| `source_document` | `source:<slug>` | Documento o fuente primaria incorporada al corpus. |
| `derived_extraction` | `extraction:<slug>` | Extracción o representación derivada de una fuente o conversación. |

La existencia de una fuente o extracción no implica que su contenido haya sido aprobado como
parte del canon intelectual vigente.

Aunque el manifiesto de `derivacion-piezas-intelectuales-equity` define conceptualmente la
`pieza intelectual` como unidad básica del conocimiento derivado, ese tipo de recurso todavía
no se incorpora aquí como taxonomía estable. Podrá incorporarse cuando el trabajo la haya
operacionalizado, verificado y demostrado como identidad durable del proyecto.

Nuevos tipos de recurso sólo deberían incorporarse aquí cuando hayan demostrado ser estables
a través de los trabajos que los utilizan.

## Separación entre corpus y conocimiento derivado

`francogg89-ai/Equity-corpus` es la fuente documental histórica canónica del proyecto.

`francogg89-ai/Equity-knowledge` es el repositorio estable destinado a recibir conocimiento
derivado estructurado y trazable mediante trabajos aprobados.

La relación entre ambos es direccional: el conocimiento derivado puede referenciar,
estructurar, relacionar e interpretar con incertidumbre declarada el contenido del corpus,
pero no sustituye ni reescribe silenciosamente sus fuentes históricas.

Otros repositorios derivados futuros —por ejemplo para funciones técnicas, investigación
especializada o servicios— no se declaran anticipadamente aquí. Su incorporación como fuente
estable deberá resultar de trabajos aprobados y de una función que haya demostrado
permanencia.

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
