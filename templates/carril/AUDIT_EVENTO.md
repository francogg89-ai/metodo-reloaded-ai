# TEMPLATE — EVENTO DE AUDITORÍA

Artefacto que registra un veredicto. Vive en el repositorio de auditoría.

## Identidad

```text
WORK_ID=   CARRIL=   UNIDAD=   METODO_REF=

FUNCION_AUDITADA=<MATERIAL | CONTROL>
OBJETO_AUDITADO=<identidad literal de lo auditado>
BASE_WORK_SHA=<predecesor inmediato del objeto auditado>
CURRENT_WORK_SHA=<candidato vigente al momento de auditar>

# sólo cuando FUNCION_AUDITADA=MATERIAL
WORK_EVENT_ID=      CONSTRUCTOR_ROUND=

VEREDICTO=
```

## Qué se auditó

`OBJETO_AUDITADO` toma el resultado del evento cuando la función es material, y el
control cuando la función es control. Un evento de función control no tiene identificador
de evento material ni ronda, y asignárselos contradiría el vocabulario de identidad
—ver `[[I-08]]`—; por eso esos dos campos quedan vacíos en ese caso.

`CURRENT_WORK_SHA` se registra siempre porque un control no lo hace avanzar: auditar un
relevo exige poder decir cuál era el candidato vigente en ese momento.

El caso de la auditoría de un relevo no es opcional: un actor fresco depende de ella
antes de tomar el trabajo —ver `[[I-15]]`—.

## Secciones

Delta re-derivado · comprobaciones propias · bloqueantes · impacto · veredicto ·
miniprompt siguiente.

## Qué re-derivó el auditor

> `[[#1b]]` Toda auditoría enuncia qué re-derivó por su cuenta y qué aceptó como evidencia producida por el constructor, y nunca presenta como comprobación independiente algo que sólo leyó.

Es la contracara de la procedencia que la entrega declara: sin esta sección, la
independencia se afirma y no se muestra.

## Bloqueantes

Por cada uno: identificador, causa, alcance y qué lo cerraría. Un bloqueante sin alcance
declarado no permite acotar la corrección.

## Impacto

Qué artefactos previamente aceptados quedan reabiertos, con su causal y su alcance; y
cuáles conservan su aceptación.
