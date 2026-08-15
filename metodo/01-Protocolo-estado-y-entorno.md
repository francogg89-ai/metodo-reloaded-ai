# 01 — PROTOCOLO DE ESTADO MATERIAL Y ENTORNO

**Objeto de este documento:** el estado material y el entorno. Cuándo un artefacto tiene
efecto material, qué estados puede atravesar, cómo se comprueba el entorno real y cómo
se tratan la concurrencia y el drift.

La autoridad sobre quién decide y qué constituye un veredicto vive en `00`. La identidad
y la estructura del trabajo viven en `02`.

---

## 1. Efecto material

Un artefacto tiene efecto material cuando, al aplicarse, ejecutarse, desplegarse o ser
consumido por el sistema, puede modificar o afectar datos, estado, permisos, seguridad,
contratos, comportamiento en runtime, resultados observables o recursos lógicos del
proyecto.

Ante duda razonable sobre si un artefacto carece de efecto material, se lo trata como
material. El gate que se aplica en consecuencia, y su veredicto, viven en `00 §11`.

---

## 2. Estados materiales

Los estados materiales pertenecen a un namespace propio y describen el recorrido de un
candidato por el entorno de verificación:

- **preparado** — existe un candidato exacto listo para verificación material, todavía
  no aplicado;
- **aplicado** — el cambio fue materialmente aplicado o ejecutado;
- **verificado** — la evidencia disponible demuestra la propiedad material prevista;
- **fallido** — la verificación produjo un resultado insatisfactorio;
- **revertido** — el cambio fue revertido y la reversión quedó registrada;
- **superseded** — el candidato fue reemplazado por uno posterior;
- **canonizado** — el cambio fue incorporado al estado canónico por el proceso
  autorizado.

Estos estados no sustituyen al historial ni eliminan evidencia anterior. Alcanzar
el estado verificado no equivale por sí solo a la aprobación de la unidad, que es un
veredicto y vive en `00`.

---

## 3. Entorno suficiente

La verificación material ocurre en el entorno capaz de demostrar la propiedad concreta:
ejecución local, suite automatizada, entorno de desarrollo, entorno aislado, entorno
compartido de prueba u otro suficiente.

Un entorno más cómodo no sustituye a uno real cuando la propiedad sólo puede demostrarse
allí. La regla que lo obliga es `[[I-18]]`, enunciada en `00 §11`.

---

## 4. Autoridad del entorno real

Aplicación material del principio de `[[#2a]]`, enunciado en `00 §4`. Aquí se fija su
consecuencia operativa, no el principio.

El registro representa el estado conocido y respaldado por evidencia; el entorno material
real es la autoridad sobre sí mismo.

> `[[#2a]]` Antes de una operación sensible, y siempre que la decisión dependa de ello, el estado real se comprueba contra su fuente material en el punto de uso, y el registro no se toma como suficiente.

Una representación derivada puede materializarse como caché de conveniencia cuando no es
autoridad, puede regenerarse desde sus fuentes, se verifica en el punto de uso contra el
recurso real cuando corresponde, y no se convierte en verdad manual. La tercera
condición es la que hace el trabajo: regenerable no es lo mismo que regenerado.

---

## 5. Drift

El entorno puede haber cambiado por fuera del registro. Comprobarlo admite consulta,
export, hash, captura, comando de diagnóstico, lectura de API o comparación.

> `[[#2a]]` Cuando el estado real contradice al registro se declara drift, y el flujo se detiene hasta reconciliarlo.

El drift es una condición operativa de bloqueo, no un estado material del candidato.

---

## 6. Concurrencia

Varios trabajos activos pueden compartir un mismo proyecto y un mismo entorno.

> `[[#13]]` Una colisión de código y una colisión de recurso material son problemas distintos: la primera se resuelve por integración de cambios, y la segunda exige serialización y no se resuelve integrando texto.

El registro de trabajos activos se reconstruye desde los eventos append-only de los
carriles del mismo proyecto, y no desde una copia central editable. Su forma
procedimental vive en los procedimientos compartidos.

El entorno compartido no equivale al estado canónico: contiene además
los cambios no canonizados activos y los cambios externos detectados.

Clasificación de conflicto: sin conflicto conocido, superposición potencial, conflicto
reconciliable, recurso compartido no aislable, conflicto bloqueante.

---

## 7. Artefactos de verificación

Smokes, validadores, fixtures y tests no se consideran adecuados porque el auditor pueda
leerlos y entender su intención. La exigencia de discriminación es `[[I-18]]`, enunciada
en `00 §11`; aquí se fija qué la satisface.

Formas admisibles, proporcionales al riesgo: caso feliz junto a caso negativo, condición
deliberadamente incorrecta, mutante conocido, fixture adversarial u otra comprobación que
demuestre que el mecanismo falla cuando debe fallar.

No se exige automáticamente prueba de mutación formal para todo mecanismo.

---

## 8. Procedencia de la verificación

Toda verificación material registra su procedencia: si la propiedad quedó demostrada por
evidencia producida por ejecución humana, o por comprobación directa del actor cuando
ello no viola una exclusión del trabajo.

La clasificación de evidencia que gobierna esta distinción es `[[I-11]]`, enunciada en
`00 §5.2`.
