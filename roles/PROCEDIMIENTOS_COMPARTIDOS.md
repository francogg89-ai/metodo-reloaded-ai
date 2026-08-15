# PROCEDIMIENTOS COMPARTIDOS

**Objeto de este documento:** el *cómo*. Operacionaliza obligaciones que los documentos
canónicos ya fijan, y aloja las obligaciones procedimentales propias que las
disposiciones aprobadas introducen.

Un procedimiento describe pasos. Cuando un paso constituye una obligación nueva —y no la
ejecución de una obligación ya enunciada— lleva su clave, y esa clave se enuncia como
autoridad aquí y en ningún otro documento.

Ante conflicto prevalecen, en orden: `00`, `01`, `02`, este archivo, las instrucciones de
rol, y los templates.

---

# PC-01 — Bootstrap y carga exacta de autoridad

**Propósito.** Conectar a un agente que abre o retoma un carril con la única copia
autoritativa de las reglas.

**Activación.** Al iniciar una sesión nueva, o cuando un miniprompt ordene continuar un
trabajo existente.

## Procedimiento

1. Leer el bootstrap del carril antes de ejecutar trabajo sustantivo.
2. Resolver el repositorio del método a la referencia literal fijada allí, y comprobar
   que ese commit existe.
3. Leer a esa referencia los tres canónicos, este archivo y la instrucción del rol.
4. Continuar desde el miniprompt y el estado indicado.

> `[[CF-1]]` La lista de artefactos de control que el bootstrap manda leer se declara aquí y en ningún otro documento; ningún otro archivo la enumera por segunda vez.

Lista vigente: bootstrap, identificador del trabajo, manifiesto, baseline, descriptor
del plan aprobado y, cuando exista, el espacio de situaciones extraordinarias.

## Espacio de situaciones extraordinarias

> `[[#15b-ii]]` Cuando el espacio de situaciones extraordinarias existe y no está vacío, se lee durante el bootstrap y antes de actuar.

Su costo es una línea del procedimiento. Existe sólo si hay copias etiquetadas,
excepciones activas o limitaciones de fuente que puedan escribirse en él.

## Sincronización del carril

> `[[#12]]` Todo actor trabaja sobre la rama de trabajo declarada por el carril, y ninguna instrucción, comando ni ejemplo de este método fija el nombre de esa rama.

> `[[#12]]` La sincronización se hace por avance rápido sobre la rama de trabajo declarada; ningún actor reescribe historia ni fuerza una actualización para hacer coincidir un estado inesperado, y ante precondición fallida se detiene y reporta.

Requisitos ordinarios antes de construir: rama esperada, árbol de trabajo limpio y
sincronización exitosa.

## Abortar o escalar cuando

Falta el bootstrap; la referencia del método no existe; no puede leerse el repositorio
del método; el rol no coincide con el carril; o se pretende continuar usando un puntero
móvil en lugar de la referencia fijada.

---

# PC-02 — Referencias exactas

**Propósito.** Evitar que identidad del candidato, commit de control y evidencia de
auditoría se confundan.

El vocabulario de identidad —SHA base, resultado, vigente, de control y de auditoría— y
su semántica viven en `02 §2`. Este procedimiento sólo fija cómo se obtiene y se
comprueba una referencia.

## Procedimiento

1. Resolver el valor desde la fuente, o recibirlo literal en un miniprompt.
2. Comprobar que el objeto existe y pertenece al repositorio esperado.
3. Comprobar que su función coincide con la afirmada: un puntero de rama que apunta a un
   commit de control no es el candidato vigente.
4. Referenciar el nombre que corresponde a lo que se quiere señalar.

---

# PC-03 — Derivación mecánica

**Propósito.** Operacionalizar el principio de `[[#2a]]`, enunciado en `00 §4`. Este
procedimiento no lo reenuncia: describe cómo se ejecuta.

## Procedimiento

Se derivan desde la fuente, y no se transcriben a mano como autoridad: archivos
modificados, nuevos y eliminados; renames; snapshots; historia; e identidad.

Una narrativa puede explicar el resultado; el resultado se obtiene de la fuente.

### Recálculo de hash

Cuando un hash es material para la propiedad auditada: se obtiene el archivo exacto a la
identidad exacta, se recalcula con el algoritmo especificado, se compara contra el valor
declarado, y se registra el resultado como comprobación y no como repetición.

## Abortar o escalar cuando

La referencia base o resultado es ambigua, el repositorio no coincide, o la derivación no
puede realizarse con la evidencia disponible.

---

# PC-04 — Constitución de eventos

**Propósito.** Mantener una línea temporal material atómica y diferenciarla de los
eventos que sólo transportan control.

La atomicidad, la numeración y la distinción entre evento material y evento de control
viven en `02 §3`. Este procedimiento fija el orden de los pasos.

## Evento material

1. Confirmar que transforma el candidato.
2. Resolver el siguiente identificador cronológico del trabajo completo.
3. Tratar un identificador esperado recibido por miniprompt sólo como expectativa.
4. Comprobar que no apareció otro evento material intermedio.
5. Constituir definitivamente el identificador y, si el originador es el constructor,
   la ronda siguiente.
6. Crear la entrega del evento en la unidad activa.
7. Dejar candidato y entrega en estado coherente.
8. Cerrar mediante un único commit autoritativo y publicarlo.
9. Obtener el SHA resultado desde la fuente.

## Evento de función control

1. Confirmar que no transforma el candidato.
2. No asignar identificador material ni ronda.
3. Crear el checkpoint o registro durable.
4. Cerrar mediante un commit coherente y obtener su SHA de control.
5. Comprobar que el SHA vigente sigue siendo el del último evento material.

## Abortar o escalar cuando

El supuesto evento contiene varios commits durables parciales; el identificador esperado
dejó de ser el siguiente; un evento de control transforma el candidato; o un evento
material no deja un candidato coherente.

---

# PC-05 — Append-only e impacto

**Propósito.** Preservar historia y evitar reentrega innecesaria, sin convertir una
aceptación previa en aprobación irreversible.

Los invariantes de append-only, el conjunto de estados de artefacto y la transición por
impacto viven en `02 §6` y `02 §7`. Este procedimiento fija el orden del impacto.

## Procedimiento de impacto

1. El constructor declara el impacto esperado de su cambio.
2. El auditor re-deriva el delta e inspecciona dependencias, interfaces, contratos,
   supuestos, comportamiento, seguridad e integración.
3. Si un artefacto aceptado para arrastre perdió su contexto de validez, el auditor
   declara su reapertura.
4. La reapertura se registra en un evento de auditoría nuevo.

## Abortar o escalar cuando

Se intenta editar evidencia histórica para actualizarla, en vez de agregar un evento
nuevo.

---

# PC-06 — Miniprompt exacto

**Propósito.** Transportar sólo las instrucciones suficientes para que el actor siguiente
reconstruya el estado desde la fuente.

Incluir proporcionalmente: rol; trabajo; carril; repositorio a sincronizar; SHA literal
correcto según lo que se señale; rutas exactas; próxima acción; ronda cuando corresponda;
e identificador de evento esperado, sólo como expectativa.

La prohibición de usar referencias ambiguas es `[[I-06]]`, enunciada en `00 §9.1`.

---

# PC-07 — Checkpoint y relevo

**Propósito.** Permitir relevo sin depender de la conversación anterior y sin anclar al
actor entrante.

## Relevo a demanda dentro de una unidad

1. Cerrar primero la unidad de trabajo actual de forma consistente.
2. Construir el checkpoint como evento de función control.
3. No modificar el candidato.
4. Cerrar con commit y obtener el SHA de control.
5. Someter el evento de handoff a auditoría antes de que un actor fresco dependa de él.
6. Emitir el miniprompt de arranque fresco con SHA y rutas exactas.

## Cambio de unidad

1. Completar las verificaciones necesarias.
2. Alcanzar la aprobación de la unidad.
3. El actor que cierra puede emitir directamente el kickoff de la unidad siguiente.
4. No crear un evento de control separado sólo por simetría.

El contenido y la naturaleza de la evaluación de handoff son `[[I-15]]` e `[[I-16]]`,
enunciadas en `00 §10`.

---

# PC-08 — Evaluación de vía liviana

**Propósito.** Reducir ceremonia sin relajar controles materiales.

## Criterios acumulativos

Todos deben cumplirse: un solo recurso lógico afectado, o ninguno si es documento puro;
sin dependencia declarada por otro trabajo activo sobre ese recurso; rollback trivial;
verificación de un paso o ausencia de efecto material; y sin decisión técnica o de diseño
nueva.

Si falla cualquiera, corresponde el carril completo.

## Qué puede colapsarse

Un artefacto de control por cambio; un evento; una auditoría; la ausencia de subunidades;
una entrega reducida; y el relevo sólo si el contexto lo exige.

Qué nunca se relaja es `[[I-17]]`, enunciado en `00 §7.1`.

---

# PC-09 — Corrección asistida

**Propósito.** Permitir correcciones determinadas sin transformar al auditor en
constructor.

El principio —el auditor corrige defectos, el constructor resuelve problemas— es
`[[I-19]]`, enunciado en `00 §5.3`. El reparto de decisión que gobierna el ruteo es
`[[PE-01a]]`, enunciado en `00 §5.4`. Este procedimiento aplica ambos.

## Precondiciones

Antes del parche corresponde poder afirmar que la causa está identificada; la solución
está determinada; la corrección es acotada; no requiere decisión técnica o de diseño nueva; no
cambia objetivo, alcance, exclusiones ni criterio de éxito; no altera materialmente
contrato, seguridad ni permisos; no cambia pruebas de forma oportunista; el candidato
resultante puede congelarse; y existe un mecanismo independiente previo, objetivo,
discriminante y no derivado del parche.

Ante duda, no es defecto determinado: escalar.

## Ruteo

- **Defecto determinado** — corrección asistida.
- **Falta decisión de dominio** — decide el humano; luego se reevalúa si quedó
  determinado, si sigue exigiendo diseño, o si modifica materialmente el manifiesto.
- **Falta decisión técnica o de diseño** — escalar al constructor, siempre.

## Tres controles obligatorios

1. **Criterio independiente definido antes.** Se registra objetivo, discriminante y
   mecanismo no derivado del parche.
2. **Integridad de aplicación.** El delta del evento correctivo coincide exactamente con
   el parche autorizado. Demuestra integridad de aplicación, no corrección funcional.
3. **Resultado independiente.** Se ejecuta o comprueba efectivamente el mecanismo
   definido en el primer control.

## Correcciones sucesivas

Cada corrección determinada adicional consume un identificador de evento, parte de un SHA
base nuevo, produce un SHA resultado nuevo y genera evidencia nueva. No consume ronda del
constructor.

Si después de una o más correcciones asistidas aparece un problema que exige decisión
técnica, de diseño o cambio material, el auditor cierra su ciclo, deja evidencia,
escala, produce checkpoint y miniprompt, y prepara el relevo. Quién audita el candidato
siguiente en ese caso lo fija `[[I-15]]`, enunciado en `00 §10.1`.

---

# PC-10 — Verificación material y separación de entornos

**Propósito.** Asegurar que todo efecto material se demuestre en un entorno suficiente,
sin permitir mutaciones de agentes en entornos reales.

La regla que obliga la verificación y la noción de entorno suficiente son `[[I-18]]` y
`01 §3`.

## Separación de autoridad

> `[[I-10]]` Los agentes poseen acceso material de sólo lectura a los entornos de prueba y producción: nunca aplican cambios mutativos, despliegan, promueven, ejecutan migraciones mutativas, alteran flujos de trabajo, modifican permisos ni tocan datos o recursos reales.

> `[[I-10]]` Cuando la propiedad exige una mutación en un entorno real, el agente prepara instrucciones humanas exactas y detiene toda mutación propia; la ejecución humana nunca se sustituye por una mutación del agente.

## Rama material

Auditoría offline satisfactoria → candidato apto para verificación material → congelar el
candidato exacto → preparar instrucciones humanas → detener mutaciones de agentes → el
humano ejecuta → evidencia → el auditor la interpreta → estado material correspondiente →
auditoría de cierre.

## Procedencia

Se registra si la propiedad quedó demostrada por evidencia de ejecución humana, o por
comprobación directa del actor cuando ello no viola una exclusión.

---

# PC-11 — Registro lógico de trabajos activos

**Propósito.** Evitar aplicar o verificar candidatos sobre un entorno compartido
ignorando cambios de otros trabajos.

## Forma del registro

> `[[#14]]` El registro de trabajos activos es lógico y se re-deriva desde los eventos append-only de los carriles del mismo proyecto; nunca se crea un registro almacenado ni una copia central editable.

## Procedimiento de uso

1. Re-derivar el registro desde los carriles activos del proyecto.
2. Verificar el recurso material real cuando la decisión dependa de su estado.
3. Ejecutar —el humano, cuando corresponde por separación de autoridad—.
4. Registrar la evidencia en el evento.

> `[[#14]]` El resultado de la derivación puede materializarse como caché de conveniencia cuando no es autoridad, puede regenerarse desde sus fuentes y se verifica en el punto de uso contra el recurso real; sin esa verificación es un inventario almacenado.

La clasificación de conflicto y la condición de drift viven en `01 §5` y `01 §6`.

---

# PC-12 — Cierre de unidad e integración

**Propósito.** Cerrar unidades sin copiar artefactos innecesariamente y preparar
continuidad segura.

## Cierre de unidad

1. Identificar el candidato validado por identidad y ruta.
2. Identificar la evidencia material cuando corresponda.
3. Marcar los artefactos definitivos.
4. Producir el índice de artefactos definitivos sólo cuando aporte valor; puede ser un
   índice de referencias y no de copias.
5. Registrar riesgos no bloqueantes.
6. Preparar el kickoff de la unidad siguiente.

## Integración final

1. Reunir las salidas aprobadas de todas las unidades.
2. Obtener el estado canónico vigente y compararlo contra el baseline original.
3. Incorporar los cambios canónicos aparecidos durante el trabajo.
4. Detectar conflicto textual y funcional.
5. Reabrir por impacto lo necesario y repetir las verificaciones afectadas.
6. Comprobar que ninguna copia etiquetada quedó sin reconciliar.
7. Producir el candidato final y someterlo a auditoría final y gate humano.

---

# PC-13 — Replanificación por impacto

**Propósito.** Consolidar en un solo lugar el tratamiento de un cambio de plan que no
cambia la intención aprobada. Su contenido normativo nuevo es cero: reúne reglas que ya
existen y estaban dispersas.

## Ruteo

- Si cambia la intención humana aprobada, el trabajo regresa a descubrimiento.
- Si cambia el plan sin cambiar la intención, corresponde replanificación.
- Si no cambia ninguno de los dos, corresponde una copia de trabajo etiquetada.

## Procedimiento

> `[[#3]]` Una replanificación conserva trabajo, carril, cronología y eventos previos, y la versión reemplazada queda marcada como superseded sin borrarse ni editarse.

El descriptor del plan aprobado sigue apuntando a la versión vigente mientras la nueva es
candidata, y sólo avanza cuando ésta recibe su gate.

## Abortar o escalar cuando

Al redactar la replanificación aparece una obligación que hoy no existe: se detiene y se
escala. Una regla nueva no se cuela dentro de un procedimiento.

---

# PC-14 — Evidencia de verificación

**Propósito.** Fijar qué sobrevive a la ejecución de una verificación, incluida la
que ocurre en un entorno efímero o la que ejecuta un humano.

## Contenido mínimo

> `[[#4]]` `[[#5]]` Toda evidencia de verificación preserva el comando exacto, su salida, su código de retorno, las versiones relevantes, la identidad del candidato, el entorno y las limitaciones declaradas.

> `[[#4]]` Ninguna evidencia se da por suficiente cuando el entorno que la produjo desaparece sin haberla preservado.

Este procedimiento no fija formato ni construye herramientas: nombrar qué se preserva
ataca los modos de falla observados —pérdida de salida, pérdida de código de retorno,
confusión de versiones y errores de transporte— y el resto queda abierto.

---

# PC-15 — Readiness y capacidades por unidad

**Propósito.** Operacionalizar el principio de readiness enunciado en `00 §8`, y tratar
la necesidad de una capacidad que aparece durante el trabajo.

## Chequeo

> `[[#8b]]` La comprobación de readiness registra qué demuestra cada resultado y su procedencia, y vive dentro de la entrega del evento que la produjo; nunca se acumula como inventario vigente del carril.

Sólo las decisiones son durables. El estado de capacidad no lo es.

## Capacidad no anticipada

> `[[#11]]` Cuando durante una unidad aparece la necesidad de una capacidad no anticipada, el constructor la declara en su entrega, explica por qué apareció e indica su impacto, y nunca amplía permisos en silencio.

> `[[#11]]` El auditor verifica la necesidad, evalúa una sustitución, informa al humano cuando corresponde y registra el resultado; la necesidad queda resuelta, sustituida, diferida explícitamente o escalada antes de la segunda ronda de la unidad.

El plazo es disciplina de este procedimiento, no un principio canónico.

---

# PC-16 — Copias de trabajo no canónicas

**Propósito.** Permitir el uso de copias como medio de trabajo sin que ninguna se
convierta en segunda fuente autoritativa.

La propiedad preservada es la fuente única del candidato, `[[I-03]]`, enunciada en
`02 §5`.

## Etiquetado

> `[[#15a]]` Toda copia no canónica declara, en el momento de crearse, su procedencia, el SHA de origen, el motivo, el alcance, su autorización y la obligación de reconciliarse; una copia sin esa declaración nunca se usa como insumo.

## Reconciliación

La comprobación de que ninguna copia quedó sin reconciliar ocurre dentro del gate de
integración que ya existe. No se crea un gate nuevo.

## Abortar o escalar cuando

Una copia se consulta como autoridad sin contrastar la fuente, o el candidato queda
vigente en ella.
