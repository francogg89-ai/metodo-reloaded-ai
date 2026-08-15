# 00 — MANIFIESTO DEL MÉTODO OPERATIVO

**Objeto de este documento:** autoridad y decisión. Qué constituye un trabajo, quién
decide qué, cómo se emiten veredictos y qué principios gobiernan a todos los actores.

El estado material y el entorno viven en `01`. La identidad y la estructura del trabajo
viven en `02`. El *cómo* de cada obligación vive en los procedimientos compartidos.

Cada cláusula normativa declara su clave entre dobles corchetes. La clave identifica el
invariante preservado o la disposición aprobada que la sostiene, y **una clave se
enuncia como autoridad en un solo documento**: los demás la referencian.

---

## 1. Principio fundamental

Un pedido humano inicial no constituye por sí mismo un trabajo suficientemente definido.
El proceso comienza con una etapa de descubrimiento cuyo objetivo es entendimiento real
entre el humano y el agente.

Durante el descubrimiento, el agente reconstruye lo entendido, pregunta ante ambigüedad
material, cuestiona supuestos, propone alternativas, distingue objetivo de
implementación, y detecta exclusiones, restricciones y riesgos.

> `[[I-13]]` Ninguna etapa posterior puede reescribir silenciosamente la intención humana aprobada: si aparece información que modifica materialmente objetivo, alcance, exclusiones, riesgo aceptado o criterio de éxito, el trabajo regresa a descubrimiento.

## 2. Constitución del trabajo

El descubrimiento produce un `MANIFIESTO_TRABAJO` que define proporcionalmente objetivo,
motivo, resultado observable, alcance, exclusiones, proyecto afectado, recursos,
restricciones, riesgos, intervención humana esperada, modalidad de verificación y
criterios de éxito.

> `[[I-09]]` El trabajo queda constituido únicamente cuando el humano aprueba el manifiesto mediante un gate explícito; nunca por ausencia de objeciones ni por inferencia de un agente.

### 2.1. Secuencia de arranque

> `[[#7a]]` El loop constructor–auditor arranca sobre un manifiesto ya aprobado, el auditor es el punto de entrada que prepara el kickoff, y la primera unidad con eventos materiales es el plan.

La aprobación se identifica dentro del propio manifiesto mediante `APPROVED_BY` y
`APPROVAL_EVIDENCE`. El SHA que la fija es el commit de constitución del carril, y no se
almacena aparte.

## 3. Inmutabilidad del manifiesto aprobado

Una vez aprobado, el manifiesto queda congelado y se identifica por trabajo, versión,
fecha de aprobación, repositorio canónico y rama canónica.

> `[[I-13]]` Las decisiones técnicas posteriores no modifican el manifiesto; si es necesario cambiar materialmente objetivo, alcance, exclusiones, riesgo aceptado o criterio de éxito, se produce una versión nueva sometida otra vez a aprobación humana.

Una aclaración humana de dominio que no modifique materialmente esos elementos se
incorpora como decisión durable del trabajo, sin reabrir el manifiesto.

---

## 4. Derivar, no almacenar

Principio general del método, y el de mayor alcance: gobierna toda representación de
estado, sea derivable de Git o del entorno material.

> `[[#2a]]` `[[I-20]]` Ningún agente escribe manualmente como autoridad algo que pueda obtenerse de forma determinista de su fuente; una afirmación no constituye el estado cuando existe una fuente material capaz de demostrarlo, y ninguna representación documental sustituye a esa fuente cuando puede consultarse razonablemente.

Alcance de la fuente, según el caso: el repositorio para archivos, deltas, renames,
snapshots, SHA e historia; el entorno material real para capacidades, permisos, recursos
y estado de ejecución.

El corolario operativo —cuándo comprobar la fuente real y qué ocurre si contradice al
registro— vive en `01`. El procedimiento de derivación vive en los procedimientos
compartidos. Ninguno de los dos reenuncia este principio.

---

## 5. El auditor

### 5.1. Independencia epistemológica

La independencia no proviene de usar otro agente, otro modelo, otro proveedor, otra
conversación ni otro repositorio.

> `[[I-02]]` El auditor forma su veredicto mediante comprobaciones independientes de las afirmaciones materiales del constructor, y puede conocer su razonamiento sin heredarlo como autoridad.

### 5.2. Clasificación de evidencia

> `[[I-11]]` Cada auditoría distingue proporcionalmente la procedencia de su evidencia entre fuente autoritativa directa, evidencia producida por el constructor, comprobación independiente del auditor y lo no verificable en esa etapa.

Lo no verificable en esa etapa —por permisos, acceso, capacidad material, entorno o
intervención humana requerida— se declara como tal y limita el veredicto en consecuencia.

### 5.3. Corrección asistida

> `[[I-19]]` El auditor corrige cuando la solución está determinada y no cuando tiene que elegirla: corrige defectos, y el constructor resuelve problemas.

Una corrección asistida no se habilita por cantidad de líneas ni por aparente
simplicidad. Requiere un mecanismo de verificación independiente definido antes del
parche y ausencia de decisión técnica o de diseño nueva.

### 5.4. Reparto de la decisión

Regla de asignación de decisiones entre actores. Gobierna **todo** el método, no sólo el
ruteo de un defecto detectado en auditoría.

> `[[PE-01a]]` Una decisión de dominio corresponde al humano; una decisión técnica o de diseño corresponde al constructor y nunca se somete al humano ni se resuelve por el auditor.

Aplicada al ruteo de un defecto, produce las tres rutas que los procedimientos
compartidos operacionalizan. Aplicada a un gate, delimita qué se le pide al humano.

---

## 6. Gates humanos

Un gate es una decisión humana explícita, situada y acotada.

> `[[I-09]]` El alcance de un gate es el que ese gate comprendió, y nunca se extiende por analogía a decisiones que no le fueron sometidas.

Gates previstos: aprobación del manifiesto y del plan; apertura de cada unidad; cierre
de la unidad final; y toda autorización de ejecución que exceda la autoridad del agente.

> `[[I-14]]` La aprobación de una unidad no abre la siguiente: cierre y apertura son actos separados, y la apertura requiere su propio gate humano.

La **forma del registro** de un gate —los campos que enumeran lo que decidió y lo que
explícitamente no decidió— vive en su template, bajo `[[PE-01b]]`. Este documento no la
enuncia: fija que el gate existe, cuál es su alcance y qué consecuencias tiene, no cómo
se escribe.

La distinción importa. Que el alcance de un gate no se extienda es una propiedad de la
autoridad, y vive aquí. Que ese alcance quede **registrado de forma legible** es la
instrucción que lo vuelve comprobable, y vive en el template: sin ese registro, la
propiedad de arriba no puede contrastarse contra nada.

---

## 7. Proporcionalidad

> `[[I-17]]` La intensidad documental, de auditoría y de traspaso es proporcional al riesgo, al impacto, a la complejidad y al grado de decisión requerido, y la eficiencia nunca se obtiene eliminando controles materiales.

La eficiencia se obtiene evitando repetir lo que la fuente ya conserva, lo que el auditor
ya aceptó, lo que no cambió y lo que no fue impactado por cambios posteriores.

### 7.1. Vía liviana

Existe una vía liviana para cambios de bajo alcance y baja complejidad, que reduce
ceremonia documental y round-trips.

> `[[I-17]]` La vía liviana nunca relaja el gate de verificación material, la trazabilidad, la fuente única del candidato, la auditoría, la condición previa de corrección asistida ni la política append-only.

Si durante un cambio liviano aparece mayor complejidad, riesgo o alcance, se escala a
carril completo conservando los eventos ya cerrados.

---

## 8. Readiness

> `[[#8a]]` Todo plan evalúa la readiness de su carril antes del trabajo sustantivo, distinguiendo instalado, capacidad, permiso, entorno suficiente y autoridad para mutar; el resultado nunca se almacena como inventario vigente.

La evaluación se cierra en una línea cuando no hay necesidades nuevas, y sólo se expande
ante un faltante. No constituye una unidad obligatoria: la preparación proporcional de
cada unidad ya existe y no se duplica.

> `[[#8a]]` Toda comprobación de readiness declara qué demuestra, y no sólo su resultado: un código de salida favorable que no discrimina no constituye evidencia de capacidad ni de permiso.

Cuando una capacidad no puede comprobarse sin violar una exclusión del manifiesto, la
respuesta correcta es declararla no verificable en esa etapa.

---

## 9. Memoria material y traspaso

> `[[I-01]]` El repositorio transporta el estado y la conversación transporta instrucciones; una narrativa explica los hechos materiales, y nunca los sustituye.

### 9.1. Referencias exactas

> `[[I-06]]` Toda referencia a estado usa el SHA exacto y la ruta exacta, y nunca expresiones ambiguas como «lo último», «la última ronda» o «el archivo nuevo».

### 9.2. Miniprompts

Al cerrar cada evento o intervención relevante, el agente produce un miniprompt exacto
para el actor siguiente, con rol, trabajo, carril, repositorio, SHA literal, rutas
exactas y próxima acción.

> `[[I-01]]` El miniprompt transporta instrucciones suficientes para reconstruir el estado desde la fuente, y nunca sustituye a esa fuente.

---

## 10. Relevos, checkpoints y actor fresco

Cualquier sesión puede reemplazarse cuando el contexto es excesivo, cambia la etapa,
aparece contaminación narrativa o conviene una instancia fresca.

> `[[I-16]]` El actor entrante reconstruye el trabajo sin necesitar la conversación anterior, a partir del checkpoint durable y de las fuentes que éste identifica por SHA exacto.

> `[[I-15]]` Todo relevo se audita antes de que un actor fresco dependa de él.

La evaluación de handoff se escribe como preguntas abiertas —qué hizo el actor saliente,
dónde quedó inseguro, qué convendría reconsiderar—.

> `[[I-15]]` La evaluación de handoff es contexto e hipótesis para el actor entrante, nunca un veredicto, y el actor entrante re-deriva por su cuenta.

### 10.1. Cuándo el actor fresco es obligatorio

Un relevo puede ordenarse en cualquier borde de evento. Existe además un caso en el que
no es opcional, y se conserva sin cambio porque la corrida lo demostró load-bearing.

> `[[I-15]]` Cuando un auditor realizó una o más correcciones asistidas y después escala por una decisión técnica, de diseño o un cambio material, el próximo candidato sustantivo nunca lo audita él: lo audita un auditor fresco.

El disparador son dos hechos encadenados —haber corregido y luego escalar—, no cualquiera
de los dos por separado. Quien corrigió ya intervino sobre el candidato, y pedirle que
juzgue el resultado de su propia intervención es exactamente lo que la independencia del
auditor existe para impedir.

Fuera de ese caso, la frescura del actor queda disponible y no obligatoria: convertirla en
regla general sin datos de costo y beneficio no está fundado.

---

## 11. Veredictos

Los veredictos de la construcción ordinaria están gobernados por el gate material.

> `[[I-18]]` Todo artefacto con efecto material exige verificación material, y ninguno alcanza aprobación de unidad por la sola rama offline.

Conjunto de veredictos: requiere correcciones; apto para verificación material;
aprobado offline, admisible únicamente para artefactos sin efecto material; unidad
aprobada, como estado final; y escalar al constructor, cuando durante una corrección
asistida aparece una decisión técnica o de diseño.

> `[[I-18]]` Un mecanismo de verificación es admisible como evidencia sólo si existe demostración de que discrimina entre éxito y fallo; leerlo y entender su intención nunca alcanza.

La distinción operativa es «con verificación material» frente a «sin efecto material»,
no la presencia de un entorno concreto. El vocabulario de estados materiales y los
entornos suficientes viven en `01`.

---

## 12. Replanificación y cierre de unidad

> `[[I-13]]` Una replanificación conserva la historia: el trabajo, el carril, la cronología y los eventos previos se preservan, y la versión reemplazada queda marcada como superseded en vez de borrarse.

Una unidad aprobada produce cierre durable, identificación del candidato validado,
evidencia de verificación material cuando corresponde, checkpoint, artefactos definitivos
y preparación de la unidad siguiente.

> `[[I-14]]` Los artefactos aceptados para arrastre no se reentregan sin cambio, y pueden reabrirse cuando cambios posteriores afectan materialmente su contexto de validez.

---

## 13. Promoción

Después de la integración final existen auditoría final, gate humano, canonización y
promoción cuando corresponde.

> `[[I-09]]` La promoción requiere autorización humana explícita, y ningún agente la ejecuta por inferencia ni la asume otorgada por un gate anterior.

La promoción parte de comprobar el estado canónico vigente, que puede diferir del que
tenía al comenzar.

---

## 14. Principios rectores

Índice de lectura. Cada principio se enuncia como autoridad en la sección indicada; aquí
sólo se listan sus claves para poder recorrerlos juntos.

| Principio | Clave | Autoridad |
|---|---|---|
| Fidelidad al objetivo humano | `[[I-09]]` | §2, §6 |
| Independencia por comprobación | `[[I-02]]` | §5.1 |
| Derivar, no almacenar | `[[#2a]]` | §4 |
| Estado durable y referencias exactas | `[[I-01]]` `[[I-06]]` | §9 |
| Sesiones reemplazables | `[[I-16]]` | §10 |
| Efecto material exige verificación material | `[[I-18]]` | §11 |
| Proporcionalidad sin eliminar controles | `[[I-17]]` | §7 |
| Reparto de la decisión | `[[PE-01a]]` | §5.4 |

---

## 15. Validación diferida

La portabilidad multi-proveedor del método —que un actor de otro proveedor continúe el
trabajo con la fuente y el handoff como única entrada— es una validación **definida y no
ejecutada**, referenciada aquí como `[[#17]]` y sin obligación derivada en este corpus.

El método queda diseñado para ser testeable así; el diseño no constituye la prueba.
