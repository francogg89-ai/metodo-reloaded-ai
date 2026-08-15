# TEMPLATE — REGISTRO DE GATE

Bloque de campos compartido. **No es un documento ceremonial ni un evento propio:** es la
forma que adopta el registro de un gate dentro del artefacto que ya lo aloja —el
descriptor del plan aprobado, una evidencia de auditoría, o el artefacto de cierre de la
unidad final—.

Existe una sola vez para que la forma tenga una autoridad única, y los artefactos que
registran un gate la instancian.

## Campos

```text
GATE=<identificador del gate>
GATE_RESULT=<APROBADO | RECHAZADO | DIFERIDO>
APPROVED_BY=<humano que decidio>
APPROVAL_DATE=<fecha>
DECIDE=<que queda decidido, enumerado>
NO_DECIDE=<que NO queda decidido, enumerado>
```

## La obligación

> `[[PE-01b]]` Todo registro de gate enumera qué decidió y qué explícitamente no decidió, y un gate sin esa enumeración nunca se da por suficiente para actuar sobre lo que no comprendió.

## Por qué los dos campos, y no sólo el primero

`DECIDE` sin `NO_DECIDE` deja el alcance abierto a la interpretación del actor siguiente,
que es el modo de falla que este campo evita: leer una aprobación como si cubriera más de
lo que cubrió.

La propiedad de autoridad que este registro vuelve comprobable es `[[I-09]]`, enunciada
en `00 §6`: el alcance de un gate es el que ese gate comprendió. Sin el registro, esa
propiedad no puede contrastarse contra nada.

## Instanciación

El artefacto que aloja el gate copia el bloque de campos y lo completa. No reenuncia la
obligación: la referencia.
