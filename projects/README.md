# ARTEFACTOS DE PROYECTO

Esta familia aloja los metadatos estables de cada proyecto sobre el que se abren trabajos:
un archivo por proyecto, con la forma que fija su template.

## Por qué existe la familia

Un carril declara a qué proyecto pertenece, y el proyecto es lo único común a varios
carriles. Sin un lugar propio, ese dato compartido se copiaría dentro de cada carril y
envejecería en cada copia por separado.

Es también la última capa de la regla de asignación: lo que cambia de proyecto a proyecto
no es del método.

## Qué no contiene

Ni una segunda copia mutable del estado de un trabajo, ni la identidad del candidato de un
carril, ni el estado del entorno compartido.

El registro de trabajos activos de un proyecto es lógico y se re-deriva desde los eventos
de sus carriles —ver `[[#14]]`—. Esta familia guarda el puntero hacia esas fuentes; el
resultado de la derivación no se almacena aquí como autoridad.

## Instancias

Un proyecto puede instanciarse aquí desde `templates/project/PROJECT.md`. Quién lo hace y
en qué momento no lo fija esta familia: depende del proyecto y de los trabajos que se
abran sobre él.

La familia define dónde y con qué forma, no exige poblarse, y puede quedar sin instancias.
