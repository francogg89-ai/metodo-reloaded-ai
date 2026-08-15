# TEMPLATE — IDENTIFICADOR DEL TRABAJO

Identifica el trabajo. No es una segunda autoridad sobre estado.

```text
WORK_ID=   WORK_NAME=   PROJECT_ID=   CARRIL=
WORK_REPO= AUDIT_REPO=  CANONICAL_REPO=
WORKING_BRANCH=<la rama de trabajo declarada del carril>
MANIFEST_PATH=  BASELINE_PATH=  PLAN_APPROVED_PATH=
```

El campo de línea de trabajo existe para que ningún procedimiento del método fije un
nombre concreto —ver `[[#12]]`—: cada carril declara el suyo aquí y el resto lo
referencia.

Este archivo no almacena identidad de candidato, ronda ni auditoría: todo eso se deriva.
