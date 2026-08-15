# TEMPLATE — BOOTSTRAP DEL CARRIL

Primer artefacto que un actor lee. Conecta al agente con la autoridad exacta.

## Contenido

```text
ROLE=          WORK_ID=       CARRIL=
WORK_REPO=     AUDIT_REPO=    CANONICAL_REPO=
METODO_REPO=   METODO_REF=<identidad literal, no un puntero movil>
ESTADO=<ACTIVO | LIBRE>
```

## Arranque

El procedimiento de bootstrap fija los pasos y la lista de artefactos de control a leer
—ver `[[CF-1]]`—. Este template no la enumera por segunda vez.

Si el estado es libre, no corresponde ejecutar trabajo sustantivo.
