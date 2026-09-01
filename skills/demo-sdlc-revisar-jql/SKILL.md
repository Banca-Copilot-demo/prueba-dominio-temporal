---
name: demo-sdlc-revisar-jql
description: "Revisa una consulta JQL de Jira y senala los filtros que faltan, las proyecciones excesivas y las clausulas que degradan el rendimiento. Usalo cuando alguien escriba o pegue una consulta JQL, o pida optimizar una busqueda de incidencias."
metadata:
  id: demo-sdlc-revisar-jql
  owner_team: squad-sdlc
  owner_contact: squad-sdlc@ejemplo.dev
  data_classification: internal
  status: draft
  version: "0.1.0"
  standard_version: "8.0.0"
---

# Revisar una consulta JQL

Recibes una consulta JQL y devuelves los hallazgos. **Reportas: no reescribes la consulta** salvo que
te la pidan explicitamente — quien la escribio conoce su caso mejor que tu.

## Lo que se revisa, en orden de coste

**1 · Falta el filtro de proyecto.** Sin `project = ...`, la consulta recorre todas las incidencias de
la instancia. Es el defecto mas caro y el mas frecuente.

**2 · Falta acotar el tiempo.** Una consulta sin `created >=` o `updated >=` crece sola: hoy tarda
un segundo y en un ano tarda un minuto, sin que nadie cambie nada.

**3 · Proyeccion excesiva.** Pedir todos los campos cuando se usan tres. Se corrige con `fields`.

**4 · Clausulas que impiden el indice.** `~` al principio de un termino, negaciones amplias como
`status != Done`, y `ORDER BY` sobre campos personalizados.

## Formato de la respuesta

Una linea por hallazgo, con la clausula exacta y el porque:

```
[grave]  falta `project = ...`  →  recorre toda la instancia
[aviso]  `status != Done`       →  no usa indice; considera enumerar los estados que si quieres
```

Si la consulta esta bien, **dilo y no inventes hallazgos**. Una revision que siempre encuentra algo
deja de creerse.

## Lo que NO haces

- No ejecutas la consulta ni te conectas a Jira: sólo lees el texto.
- No propones reescribirla entera salvo que te lo pidan.
- No opinas sobre el flujo de trabajo del equipo ni sobre sus estados.
