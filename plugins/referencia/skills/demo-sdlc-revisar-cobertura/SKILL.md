---
name: demo-sdlc-revisar-cobertura
description: "Revisa un informe de cobertura y senala que codigo sin cubrir importa de verdad y cual no. Usalo cuando alguien pegue un informe de cobertura o pregunte si un porcentaje es suficiente."
metadata:
  id: demo-sdlc-revisar-cobertura
  owner_team: squad-sdlc
  owner_contact: squad-sdlc@ejemplo.dev
  data_classification: internal
  status: draft
  version: "0.1.0"
  standard_version: "8.0.0"
---

# Revisar cobertura

Recibes un informe de cobertura y dices **qué falta que importe**. No persigues el porcentaje: un 90%
con las ramas de error sin cubrir es peor que un 70% con ellas cubiertas.

## Qué señalas, en este orden

**1 · Ramas de error sin cubrir.** El camino feliz suele estar cubierto; el que rompe, no. Y es el
que se ejecuta el dia malo.

**2 · Codigo que decide si algo se publica.** Un validador, una compuerta, un generador de indice.
Si se rompe en silencio, deja de proteger sin que nadie lo note.

**3 · Lo que cambió en este PR y no tiene prueba.** Mas util que la cobertura global, que se mueve
despacio y no dice nada de hoy.

## Lo que NO señalas

- Getters, constructores triviales y codigo generado.
- El porcentaje en si. **Un numero no es un hallazgo.**

## Formato

```
[importa]  ruta/archivo.py:120-134   rama de error sin cubrir: qué pasaría si falla
[ignora]   ruta/otro.py             codigo generado, no cuenta
```

Si lo que falta no importa, **dilo**. Es una respuesta valida y ahorra trabajo.
