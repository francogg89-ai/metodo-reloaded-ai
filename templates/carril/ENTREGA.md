# TEMPLATE — ENTREGA DE EVENTO

Artefacto que cierra un evento material. Contiene lo que la fuente no infiere por sí
misma.

## Identidad

```text
WORK_ID=            CARRIL=              UNIDAD=
WORK_EVENT_ID=      EVENT_TYPE=          CONSTRUCTOR_ROUND=
ORIGINATOR_ROLE=    BASE_WORK_SHA=       METODO_REF=

ACTOR_INSTANCE_ID=      <instancia que produjo el evento — metadata>
ACTOR_INSTANCE_ROUND=   <su ronda propia dentro de esa instancia — metadata>
```

La identidad de salida del evento **no** se escribe aquí: la produce el commit que este
archivo integra, y se obtiene de la fuente después del cierre.

Los dos campos de instancia son **metadata de observación**. No forman parte de la
identidad del evento, no se usan como referencia y no sustituyen a `WORK_EVENT_ID` ni a
`CONSTRUCTOR_ROUND`, que siguen siendo los contadores del trabajo.

## Secciones

Objetivo · motivo · decisiones tomadas dentro del plan · pruebas ejecutadas ·
limitaciones · riesgos · impacto esperado · alcance del cambio.

## Pruebas ejecutadas

> `[[#1a]]` Cada prueba declarada en una entrega lleva su clase de procedencia, y ninguna se da por independiente sin decir quién la ejecutó y contra qué fuente.

Por cada verificación: comando exacto, salida, código de retorno, limitaciones. El
contenido mínimo vive en el procedimiento de evidencia —ver `[[#4]]`—.

## Observabilidad

> `[[#16]]` Cada evento registra la instancia de actor que lo produjo como metadata, y ese identificador nunca altera la numeración de eventos ni de rondas, ni se acumula como padrón de actores.

Es instrumento de observación, no autoridad. Permite estudiar con datos preguntas que hoy
se responden por intuición.

## Checklist de cierre

- [ ] el árbol contiene sólo los cambios del evento
- [ ] el candidato queda coherente
- [ ] existe exactamente una entrega nueva
- [ ] el SHA base es el predecesor inmediato real
- [ ] identificador y ronda constituidos tras comprobar la historia
- [ ] cada prueba declara su procedencia
- [ ] no se reescribió evidencia previa
- [ ] miniprompt emitido
