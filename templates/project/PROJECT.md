# TEMPLATE — METADATOS DE PROYECTO

Forma de los metadatos estables de un proyecto: lo que vale para todos sus trabajos y no
pertenece a ningún carril en particular. **Es un bloque de campos, no una regla:** ninguna
obligación del método se enuncia aquí.

## Identidad

```text
PROJECT_ID=<identificador estable del proyecto>
CANONICAL_REPO=<repositorio canónico del proyecto>
CANONICAL_BRANCH=<la rama canónica declarada del proyecto>
```

El campo de rama existe por la misma razón que su equivalente en el identificador del
trabajo —ver `[[#12]]`—: cada proyecto declara la suya y el método no fija ninguna.

`PROJECT_ID` es la clave que une este archivo con los carriles. El identificador del
trabajo lo declara, y por él se seleccionan los carriles de un mismo proyecto.

## Secciones

| Sección | Qué aloja |
|---|---|
| Fuentes canónicas relevantes | repositorios, rutas y documentación que los trabajos del proyecto consultan |
| Entornos materiales conocidos | qué entornos existen y para qué sirven, sin credenciales |
| Taxonomía de recursos | extensiones a la noción de recurso lógico propias del proyecto |
| Cómo reconstruir los trabajos activos | desde dónde se re-derivan — ver `[[#14]]` |

La última sección aloja el puntero, no el resultado: qué carriles consultar y bajo qué
identificador de proyecto.

## Qué no vive aquí

El estado del entorno compartido, la lista de trabajos activos, la identidad del
candidato de un carril y el resultado de una verificación material. Cada uno tiene fuente
propia y se obtiene de ella; el principio es `[[#2a]]`, enunciado en `00 §4`.

Las fuentes exactas y el punto de partida de un trabajo concreto se fijan en su manifiesto
y en su baseline, con identidad literal. Este archivo los referencia sin replicarlos.

## Criterio de estabilidad

Un dato entra aquí cuando sobrevive a los trabajos que lo usan. Un dato que cambia por
trabajo pertenece al carril; uno que cambia por evento se deriva.
