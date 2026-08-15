# TEMPLATE — DESCRIPTOR DEL PLAN APROBADO

Puntero durable al plan aprobado. **No es una copia del plan.**

```text
WORK_ID=   CARRIL=   PLAN_STATUS=   PLAN_VERSION=
PLAN_PATH=            PLAN_RESULT_WORK_SHA=<hecho historico congelado>
PLAN_AUDIT_SHA=       PLAN_GATE=   APPROVED_BY=   APPROVAL_DATE=
```

El plan autoritativo se lee desde su ruta a la identidad exacta declarada.

## Estado vigente — derivado

Este descriptor no almacena la identidad del candidato vigente: se deriva de la fuente.
La identidad del plan aprobado sí se almacena porque es un hecho histórico congelado que
no envejece.

La distinción entre ambos es aplicación directa de `[[#2a]]`, enunciado en `00 §4`, y el
defecto que la motivó fue exactamente confundirlos.

## Gate

El registro de la aprobación instancia el bloque de campos de `REGISTRO_GATE`.

## Historial

Sólo la fila vigente tiene autoridad. Las anteriores se conservan como hechos históricos
congelados y no gobiernan nada.
