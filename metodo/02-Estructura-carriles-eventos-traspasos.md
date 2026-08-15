# 02 — ESTRUCTURA: CARRILES, EVENTOS Y TRASPASOS

**Objeto de este documento:** la identidad y la estructura del trabajo. Cómo se organiza
un carril, qué es un evento, cómo se nombran los SHA, cómo se preserva la historia y
cómo se traspasa el trabajo entre actores.

La autoridad sobre quién decide vive en `00`. El estado material y el entorno viven en
`01`.

---

## 1. Carril

Un carril representa **un trabajo activo completo**, no una etapa ni una unidad. Consta
de un repositorio de trabajo y un repositorio de auditoría, y conserva su identidad
durante planificación, construcción, auditoría, verificación material, unidades,
integración final y cierre.

Los agentes se renuevan tantas veces como sea necesario sin cambiar de carril.

### 1.1. Artefactos de control del carril

Un carril tiene artefactos de control que declaran su identidad y su estado.

**Este documento no los enumera.** La lista vive en el procedimiento de bootstrap —ver
`[[CF-1]]`—, porque una lista enunciada en dos lugares envejece por separado y una de las
dos queda falsa sin que nadie lo note.

---

## 2. Vocabulario de identidad

Cuatro nombres distintos para cuatro cosas distintas. Confundirlos es el modo de falla
más frecuente del traspaso.

| Nombre | Qué identifica |
|---|---|
| SHA base | commit inmediatamente anterior del que parte un evento: su predecesor real |
| SHA resultado | commit de cierre de un evento material; identidad autoritativa de ese evento |
| SHA vigente | SHA resultado del último evento material; el candidato vigente |
| SHA de control | commit de cierre de un evento de función control |
| SHA de auditoría | commit producido en el repositorio de auditoría |

> `[[I-08]]` El SHA vigente se deriva de la fuente, no se almacena, y no avanza sobre un evento de función control.

> `[[I-06]]` Toda referencia usa el nombre que corresponde a lo que señala, y ningún SHA se infiere desde una narración: se resuelve desde la fuente o se recibe literal y se comprueba su existencia.

El delta de un evento se computa siempre contra su predecesor inmediato, de modo que un
evento de control previo no contamina el delta de un evento material posterior.

---

## 3. Eventos materiales

Una ronda del constructor y una corrección asistida del auditor son mecánicamente la
misma clase de cosa: un evento atómico que transforma el candidato desde un SHA base
hasta un SHA resultado nuevo.

> `[[I-04]]` Un evento material se cierra mediante un único commit autoritativo, y nunca mediante una secuencia durable de commits parciales que pretenda representarlo.

Si un actor necesita trabajo intermedio, lo consolida antes de entregar el evento
durable.

> `[[I-07]]` El identificador de evento y la ronda del constructor son contadores distintos: el identificador pertenece a la línea temporal material del trabajo completo y no se reinicia al cambiar de unidad, y una corrección asistida consume identificador de evento sin consumir ronda del constructor.

El identificador de evento es cronológico dentro del trabajo completo, aunque los eventos
se almacenen físicamente dentro de unidades distintas.

### 3.1. Eventos de función control

Un relevo, un checkpoint o un registro de gate pueden cerrarse como evento de función
control.

> `[[I-08]]` Un evento de función control no transforma el candidato, no recibe identificador de evento material y no hace avanzar el SHA vigente.

Tras un evento de control, el puntero de la rama puede quedar en el SHA de control
mientras el SHA vigente permanece en el último commit material: pueden diferir sin que el
candidato haya cambiado.

---

## 4. Derivación mecánica

Aplicación del principio de `[[#2a]]`, enunciado en `00 §4`. Aquí se fija su alcance
sobre la identidad del trabajo, no el principio.

La fuente determina archivos, modificaciones, eliminaciones, renames, snapshots, SHA e
historia. Una narrativa explica esos datos; la fuente los determina.

---

## 5. Fuente única del candidato

> `[[I-03]]` Todo artefacto ejecutable o material del candidato vive únicamente en el repositorio de trabajo, y el repositorio de auditoría nunca conserva una segunda copia autoritativa del artefacto.

El repositorio de auditoría conserva veredictos, descriptores, evidencia, pruebas,
resultados, checkpoints y referencias de identidad.

### 5.1. Copias de trabajo no canónicas

Una copia no canónica puede usarse como insumo, andamiaje o conveniencia. La propiedad a
preservar es la fuente única **autoritativa**, no la prohibición de usar copias.

El etiquetado que las hace admisibles y su obligación de reconciliación viven en el
procedimiento correspondiente —ver `[[#15a]]`—. Aquí se fija sólo el límite:

> `[[I-03]]` Una copia puede ser dónde se trabaja y nunca dónde vive el candidato: consultarla como autoridad sin contrastar la fuente, referenciarla como identidad del candidato, dejarla sin reconciliar más allá del gate de integración, o dejar que el candidato quede vigente en ella, viola la fuente única.

---

## 6. Append-only

> `[[I-05]]` Un evento cerrado no se pisa y un veredicto previo no se sobrescribe cuando aparece nueva evidencia: el conocimiento nuevo se agrega.

Un veredicto no se vuelve falso retrospectivamente cuando una verificación posterior
falla: significa que, con la evidencia disponible en ese momento, el candidato estaba
listo para verificarse.

---

## 7. Estados de artefacto

Un artefacto del candidato atraviesa estados propios, distintos de los estados materiales
de `01` y de los veredictos de `00`:

en revisión · requiere corrección · aceptado para arrastre · reabierto por impacto ·
candidato de verificación · verificado · final de unidad · superseded.

> `[[I-05]]` No se crea sin gate humano un segundo vocabulario de estado materialmente equivalente a éste.

### 7.1. Invalidación por impacto

Un artefacto aceptado para arrastre conserva ese estado sólo mientras cambios posteriores
no afecten materialmente su contexto de validez. Puede reabrirse por impacto sobre
dependencias, interfaces, contratos, supuestos, comportamiento, seguridad o integración.

> `[[I-12]]` El constructor declara el impacto esperado de su cambio y el auditor lo comprueba de forma independiente; una declaración del constructor nunca constituye por sí sola la reapertura, que declara quien audita.

---

## 8. Traspasos

Un relevo puede ser ordenado en cualquier borde de evento, no sólo al agotarse una
sesión. Se produce como evento de función control, cierra como commit atómico y no
transforma el candidato.

El checkpoint de relevo incluye, proporcionalmente, la identidad del trabajo, las
autoridades con su SHA exacto, el estado semántico no derivable, los abiertos, las
prohibiciones de alcance y la evaluación de handoff.

La obligación de auditar el relevo antes de que un actor fresco dependa de él, y la
naturaleza de la evaluación de handoff, son `[[I-15]]` e `[[I-16]]`, enunciadas en
`00 §10`.

### 8.1. Cambio de unidad

El cambio de unidad es un handoff disparado por la aprobación de la unidad. Produce el
kickoff de la siguiente siguiendo el orden del plan, y puede incluir la evaluación de
handoff como retrospectiva.

Se distingue del relevo a demanda por su disparador y por su destino. En el cambio de
unidad el kickoff puede dejarlo el actor que cierra, sin construir un evento de control
separado; ese evento separado queda reservado al relevo a demanda mientras la unidad
sigue abierta.

La separación entre cerrar una unidad y abrir la siguiente es `[[I-14]]`, enunciada en
`00 §6`.

---

## 9. Preparación de la unidad siguiente

Después de aprobar una unidad se deja proporcionalmente: cierre, estado actualizado,
candidato verificado, evidencia, riesgos pendientes, relación con el plan, información
necesaria para la unidad siguiente, capacidades requeridas, conflictos de concurrencia
conocidos y miniprompt de kickoff.

La unidad nueva puede comenzar con una sesión fresca.
