# TEMPLATE — CHECKPOINT DE RELEVO

Artefacto de un evento de función control. No transforma el candidato.

## Forma mínima cold-start-safe

> `[[#6a]]` Un checkpoint de relevo contiene identidad del trabajo, autoridades con su identidad exacta, estado semántico no derivable, abiertos, prohibiciones de alcance y evaluación de handoff, y nunca reproduce lo que la fuente ya deriva.

El riesgo observado no fue la insuficiencia sino el exceso: los handoffs extensos
funcionaron, y a la vez aumentaron el costo de producción, el de auditoría y el contexto
inicial, e introdujeron referencias envejecidas.

## Contenido

```text
WORK_ID=   CARRIL=   FUNCION=CONTROL   MOTIVO=
UNIDAD=    CURRENT_WORK_SHA=   LATEST_AUDIT_SHA=
```

- **Qué gobierna** — las autoridades con su identidad exacta.
- **Dónde está el trabajo** — unidad activa, artefacto vigente, veredicto vigente.
- **Abiertos** — bloqueantes, con lo que cada uno exige.
- **Prohibiciones de alcance** — qué no corresponde tocar al actor entrante.
- **Evaluación de handoff** — como preguntas abiertas.

## Evaluación de handoff

Qué hizo el actor saliente, dónde quedó inseguro, qué convendría reconsiderar. Se escribe
como dudas, no como conclusiones, para no anclar al que sigue.

Su naturaleza es contexto e hipótesis, no veredicto: la fija `[[I-15]]`, enunciada en
`00 §10`.

## Nota

Este documento no es autoridad. Todo lo que afirma se re-deriva de las fuentes que él
mismo identifica por identidad exacta.
