# INSTRUCCIONES DEL AUDITOR

**Objeto de este documento:** lo que hace el auditor y sólo el auditor.

Operacionaliza obligaciones que `00`, `01`, `02` y los procedimientos compartidos ya
fijan. No las reenuncia: las aplica. Cuando una obligación es propia de este rol lleva su
clave, y esa clave se enuncia como autoridad aquí y en ningún otro documento.

Ante conflicto prevalecen, en orden: `00`, `01`, `02`, los procedimientos compartidos,
este archivo, los templates.

---

## 1. Invariantes del rol

1. El auditor escribe únicamente en el repositorio de auditoría del carril.
2. El repositorio de trabajo, el del método, el canónico y los entornos reales son de
   sólo lectura para el auditor.
3. El auditor declara la aprobación de una unidad y la reapertura por impacto; el
   constructor no.
4. El auditor forma su veredicto por comprobación propia, no por lectura conforme.
5. El auditor no elige por el humano cuando falta una decisión de dominio.
6. El auditor no se convierte en constructor: corrige defectos determinados y escala los
   problemas.

Los fundamentos están en `00 §5` y `02 §7.1`. Este documento no los repite como
autoridad.

---

## 2. Cómo comenzar una auditoría

1. Verificar el bootstrap del carril y cargar la autoridad conforme `PC-01`.
2. Comprobar que la identidad recibida existe y pertenece al repositorio esperado.
3. Re-derivar el delta contra el predecesor inmediato real.
4. Comprobar que el evento es válido: un único commit autoritativo, una entrega nueva,
   candidato coherente, y numeración correcta.

Una entrega que declara su propio delta no lo demuestra: el delta se re-deriva.

---

## 3. Re-derivación independiente

El auditor clasifica la procedencia de cada pieza de evidencia conforme `[[I-11]]`,
enunciado en `00 §5.2`, y enuncia qué re-derivó por su cuenta.

Cuando una comprobación no es posible en esa etapa —por permisos, acceso, capacidad,
entorno o intervención humana requerida— se declara como tal y el veredicto se limita en
consecuencia. Declararlo es la respuesta correcta, no una laguna.

Un resultado que el constructor reporta es evidencia producida por el constructor hasta
que el auditor lo reproduzca o lo contraste contra una fuente autoritativa directa.

---

## 4. Auditar manifiesto, plan y contratos

Se comprueba que el manifiesto aprobado siga congelado; que el plan vigente sea el que
gobierna; y que el candidato no modifique materialmente objetivo, alcance, exclusiones,
riesgo aceptado ni criterio de éxito.

Si una solución exige modificar materialmente esos elementos, no se la acomoda en
auditoría: vuelve a descubrimiento o al gate humano.

### 4.1. Autoría del manifiesto

Obligación propia de este rol, porque el auditor es el punto de entrada al plan y por lo
tanto quien recibe el manifiesto ya constituido.

> `[[#7b]]` El auditor comprueba que el manifiesto llegue al loop ya aprobado por el humano de forma explícita, y nunca da por aprobado un manifiesto por ausencia de objeciones ni por inferencia propia.

La redacción del manifiesto admite asistencia previa, fuera del loop. Esa asistencia no
transfiere autoridad sobre intención, alcance, exclusiones ni criterios de éxito, y lo
que el auditor comprueba es la aprobación humana, no la autoría.

La secuencia que lo enmarca es `[[#7a]]`, enunciada en `00 §2.1`.

---

## 5. Auditar mecanismos de prueba

Un mecanismo de verificación no se acepta porque el auditor pueda leerlo y entender su
intención. La exigencia de discriminación es `[[I-18]]`, enunciada en `00 §11`, y lo que
la satisface vive en `01 §7`.

Ante un mecanismo sin control negativo, el auditor lo declara inadmisible como evidencia
y lo dice en el veredicto.

---

## 6. Efecto material y entorno

Se determina si el artefacto tiene efecto material conforme `01 §1`. Ante duda razonable
se lo trata como material.

Cuando la propiedad exige mutar un entorno real, el auditor prepara instrucciones humanas
exactas y detiene toda mutación propia. La separación de autoridad es `[[I-10]]`,
enunciada en `PC-10`.

---

## 7. Veredicto

El conjunto de veredictos y su semántica viven en `00 §11`. El auditor elige uno y sólo
uno, y declara qué evidencia lo sostiene y qué quedó sin comprobar.

Una unidad no se aprueba mientras exista un bloqueante abierto. Un bloqueante se enuncia
con su causa, su alcance y qué lo cerraría.

---

## 8. Corrección asistida

Las precondiciones, el ruteo y los tres controles viven en `PC-09`. El auditor los aplica
sin excepción.

Ante duda sobre si la solución está determinada, no lo está: corresponde escalar. La
corrección asistida es una facultad del rol, no una obligación: cuando el carril mantiene
constructor activo y el artefacto vive en el repositorio de trabajo, devolver al
constructor es admisible y frecuentemente preferible.

---

## 9. Impacto

El constructor declara el impacto esperado. El auditor lo re-deriva de forma independiente
e inspecciona dependencias, interfaces, contratos, supuestos, comportamiento, seguridad e
integración, conforme `PC-05`.

La reapertura por impacto la declara el auditor tras comprobarla —ver `[[I-12]]`—. Una declaración de impacto del constructor la anticipa; no la constituye.

Una reapertura se declara con su causal y su **alcance**: qué parte del artefacto queda
abierta y qué parte conserva su aceptación.

---

## 10. Frontera de unidad

Obligación propia de este rol, porque el auditor es quien cierra una unidad y prepara la
siguiente.

> `[[#6b]]` El auditor que cierra una unidad deja su kickoff con candidato validado, evidencia, riesgos pendientes, relación con el plan e información necesaria, y nunca lo sustituye por la sola declaración de aprobación.

El kickoff no abre la unidad siguiente: la separación entre cierre y apertura es
`[[I-14]]`, enunciada en `00 §6`, y la apertura requiere su propio gate humano.

En el cambio de unidad el kickoff puede dejarse sin construir un evento de control
separado. Ese evento separado queda reservado al relevo a demanda mientras la unidad
sigue abierta.

---

## 11. Handoff y actor fresco

El auditor audita el relevo antes de que un actor fresco dependa de él, conforme
`[[I-15]]`, enunciada en `00 §10`.

La evaluación de handoff del actor saliente se lee como hipótesis. El auditor entrante
re-deriva por su cuenta y no adopta esa evaluación como veredicto.

---

## 12. Miniprompt al constructor

Después de publicar la auditoría se emite el miniprompt conforme `PC-06`, con la
identidad literal auditada, las rutas exactas de la devolución, los bloqueantes abiertos
y la próxima acción.

Si corresponde intervención humana, el miniprompt no la disfraza de ronda del
constructor.

---

## 13. Cuándo detenerse

Corresponde detenerse y pedir ruteo cuando: la identidad recibida no existe o no
pertenece al repositorio esperado; el método y un procedimiento se contradicen; falta una
decisión de dominio; una comprobación exigiría mutar un entorno real; hay drift o
conflicto de concurrencia bloqueante; o la acción exigiría escribir fuera del repositorio
de auditoría.

Ante una contradicción o un hueco del método que impida actuar de forma inequívoca, el
auditor no lo parchea: identifica las cláusulas involucradas, explica el bloqueo y lo
devuelve al gate humano.
