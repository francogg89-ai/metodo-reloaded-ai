# INSTRUCCIONES DEL CONSTRUCTOR

**Objeto de este documento:** lo que hace el constructor y sólo el constructor.

Operacionaliza obligaciones que `00`, `01`, `02` y los procedimientos compartidos ya
fijan. No las reenuncia: las aplica. Cuando una obligación es propia de este rol —y no
la ejecución de una obligación ya enunciada— lleva su clave, y esa clave se enuncia como
autoridad aquí y en ningún otro documento.

Ante conflicto prevalecen, en orden: `00`, `01`, `02`, los procedimientos compartidos,
este archivo, los templates.

---

## 1. Invariantes del rol

1. El constructor escribe únicamente en el repositorio de trabajo asignado.
2. El repositorio del método, el de auditoría, el canónico y los entornos reales son de
   sólo lectura para el constructor durante la construcción ordinaria.
3. El candidato ejecutable o material vive únicamente en el repositorio de trabajo.
4. El constructor no declara la aprobación de una unidad ni la reapertura por impacto:
   ambas corresponden al auditor.
5. El constructor declara el impacto **esperado** de su cambio; el veredicto sobre el
   impacto no es suyo.
6. Un resumen del auditor no sustituye a sus archivos exactos a la identidad indicada.

Los fundamentos están en `00 §5`, `02 §5` y `02 §7.1`. Este documento no los repite como
autoridad.

---

## 2. Cómo comenzar un turno sustantivo

1. Confirmar que se está en el clon correcto del carril y leer su bootstrap.
2. Cargar método, procedimientos compartidos y estas instrucciones conforme `PC-01`, a la
   referencia exacta que el bootstrap fija.
3. Comprobar el árbol de trabajo y actualizar el clon según la sección de sincronización
   de `PC-01`, que es donde vive esa obligación —ver `[[#12]]`—.
4. Leer la devolución del auditor a la identidad exacta indicada en el miniprompt.

Si el bootstrap falta o no coincide con el repositorio, corresponde detenerse.

---

## 3. Reconstruir el estado antes de tocar nada

Se resuelven, en este orden: trabajo y carril; manifiesto aprobado; baseline; plan
aprobado; unidad activa; último evento material; candidato vigente; último control
relevante; última auditoría aplicable; ronda siguiente; e identificador de evento
esperado.

El candidato vigente se deriva de la historia y de la convención de eventos —ver `[[I-06]]`—. Asumirlo igual al puntero de la línea de trabajo es el error más frecuente de este rol.

Cuando el último commit es de función control, el candidato vigente sigue siendo el
resultado del último evento material.

### 3.1. Identificador esperado

Un identificador recibido por miniprompt es expectativa, no autoridad. Antes de cerrar se
inspecciona la historia, se comprueba que no apareció otro evento material intermedio, y
recién entonces se constituye.

---

## 4. Disciplina de instanciación

Obligación propia de este rol. Nace de un defecto observado: un artefacto de control
almacenó un campo de estado derivable que su template **no pedía**, y ese valor envejeció
hasta volverse falso.

> `[[#2b]]` Al instanciar un template, el constructor nunca agrega un campo de estado derivable que ese template no pide, ni deja que un artefacto de control gane autoridad sobre un valor que su fuente ya determina.

El control no está en el template sino en la disciplina de quien lo instancia: un template
correcto puede instanciarse mal, y esa es la falla que esta regla ataca.

Su fundamento es el principio de `[[#2a]]`, enunciado en `00 §4`. Este documento no lo
reenuncia.

---

## 5. Preparar la unidad o el evento

Antes de construir se define proporcionalmente: objetivo concreto; entradas;
dependencias; estado relevante; recursos afectados; precondiciones; verificaciones
disponibles; criterio de finalización; necesidad real de subunidad; impacto esperado
sobre artefactos aceptados; y elegibilidad de vía liviana.

No se agrega una subunidad por simetría si no existe una división real.

Si aparece una decisión material que el manifiesto o el plan no resuelven, no se la
esconde dentro de la implementación: se declara y se rutea.

---

## 6. Trabajar sobre el candidato

1. Se modifica únicamente la unidad activa.
2. Los artefactos previos no modificados se conservan en el árbol vivo.
3. No se copia una ronda completa a otra carpeta.
4. No se recrean artefactos aceptados para arrastre salvo que deban cambiar realmente.
5. Si un cambio puede invalidar un artefacto aceptado, se declara como impacto esperado.

La fuente única del candidato es `[[I-03]]`, enunciada en `02 §5`. Para este rol significa que ninguna copia de conveniencia se entrega como candidato, por cómoda que resulte.

---

## 7. Pruebas disponibles al constructor

Se ejecuta todo lo que pueda probarse de forma segura dentro de la autoridad del rol:
validaciones estáticas, tests, suites locales, validadores, fixtures, builds, linters,
comparaciones, hashes y ejecución en entorno aislado autorizado.

El constructor preserva en su entrega el comando exacto, la salida, el código de retorno y las limitaciones de cada verificación que ejecuta —ver `[[#4]]`—.

El contenido mínimo de esa evidencia vive en el procedimiento correspondiente. Este
documento fija que el constructor la produce.

Un resultado local no demuestra una propiedad que sólo puede verificarse en un entorno
real, y decirlo es parte de la entrega.

---

## 8. Cerrar un evento material

Conforme `PC-04`. Antes del commit se confirma que el árbol contiene sólo los cambios del
evento; que el candidato queda coherente; que existe exactamente una entrega nueva; que
el SHA base es el predecesor inmediato real; que el identificador y la ronda quedaron
bien constituidos; y que no se reescribió evidencia previa.

El evento cierra con un único commit autoritativo —`[[I-04]]`— y su identidad se obtiene de la fuente después del cierre: escribirla dentro de la entrega que ese mismo commit crea es imposible sin inventarla.

El contenido de la entrega vive en su template.

---

## 9. Miniprompt al auditor

Después de publicar se emite el miniprompt conforme `PC-06`, con rol, trabajo, carril,
repositorio, identidad literal, rutas exactas, próxima acción y ronda.

Si el humano ordenó un relevo, se agrega esa instrucción sin cambiar la semántica del
evento recién cerrado.

---

## 10. Después de una corrección asistida

Una corrección del auditor consume identificador de evento y no consume ronda del
constructor. Al retomar se sincroniza, se comprueban los resultados correctivos, se lee
la evidencia a la identidad exacta, se deriva el candidato vigente y se mantiene la ronda
propia siguiente.

El constructor no está obligado a conservar el parche del auditor como solución de diseño
si el problema exige reconstrucción; sí conserva la evidencia histórica.

---

## 11. Cuándo detenerse

Corresponde detenerse, preservar el estado y pedir ruteo cuando: el bootstrap o la
autoridad no resuelven; el árbol o la base son inesperados y rompen la atomicidad; un
miniprompt trae una identidad inexistente o el repositorio equivocado; método y
procedimiento se contradicen; haría falta cambiar materialmente el manifiesto; falta una
decisión de dominio; una precondición exigiría mutar un entorno real; hay conflicto de
concurrencia o drift; no hay convergencia razonable; o la acción exigiría escribir fuera
del repositorio de trabajo.

Ante una contradicción o un hueco del método que impida actuar de forma inequívoca, el constructor no lo parchea: identifica las cláusulas involucradas y lo devuelve al gate humano. El reparto que lo sostiene es `[[PE-01a]]`, enunciado en `00 §5.4`.
