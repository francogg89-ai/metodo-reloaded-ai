# TEMPLATE — ETIQUETA DE COPIA NO CANÓNICA

Forma mínima que acompaña a toda copia de trabajo no canónica. **Es un bloque de campos,
no una regla:** la obligación de etiquetar y de reconciliar vive en el procedimiento
correspondiente —ver `[[#15a]]`—, y este template sólo materializa qué se declara.

## Campos

```text
CLASE=<COPIA_DE_TRABAJO | DERIVADA | NO_CANONICA | TEMPORAL>
FUENTE=<repositorio o artefacto del que proviene>
FUENTE_SHA=<identidad literal de origen>
MOTIVO=<por que existe esta copia>
ALCANCE=<que abarca y que no>
AUTORIZACION=<quien la autorizo, cuando aplique>
RECONCILIACION=<PENDIENTE | RECONCILIADA @ identidad>
```

## Qué hace cada campo

| Campo | Para qué |
|---|---|
| `CLASE` | separa una copia de conveniencia de un derivado y de un temporal, que envejecen distinto |
| `FUENTE` + `FUENTE_SHA` | permiten volver a la fuente y comparar; sin la identidad literal, la copia no es re-derivable |
| `MOTIVO` | una copia sin motivo declarado no puede evaluarse ni retirarse con criterio |
| `ALCANCE` | acota qué representa; una copia parcial que se lee como total es el modo de falla más frecuente |
| `AUTORIZACION` | deja trazable quién la habilitó cuando la copia toca algo sensible |
| `RECONCILIACION` | es el campo que impide que la copia sobreviva callada: mientras diga pendiente, el gate de integración la ve |

## Dónde vive la copia

Fuera del candidato. Una copia etiquetada es medio de trabajo; el límite lo fija
`[[I-03]]`, enunciado en `02 §5`: puede ser dónde se trabaja, no dónde vive el candidato.

## Nota

Etiquetar no autoriza: describe. Una copia etiquetada sigue sujeta a la comprobación de
reconciliación del gate de integración, y su etiqueta es lo que hace posible esa
comprobación.
