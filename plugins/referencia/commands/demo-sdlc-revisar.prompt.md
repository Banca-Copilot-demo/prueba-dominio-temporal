---
name: demo-sdlc-revisar
description: "Lanza una revision del cambio actual y devuelve los hallazgos priorizados por severidad."
metadata:
  id: demo-sdlc-revisar
  owner_team: squad-sdlc
  owner_contact: squad-sdlc@ejemplo.dev
  data_classification: internal
  status: draft
  version: "0.1.0"
  standard_version: "8.0.0"
---

Revisa el cambio pendiente en esta rama y devuelve los hallazgos.

Antes de opinar, mira **qué cambió de verdad**: el diff contra la rama base, no el estado final de los
archivos. Un archivo puede estar bien y aun asi el cambio haber roto algo.

Devuelve una linea por hallazgo, con archivo y linea:

```
[grave]  ruta/al/archivo:42   qué está mal y qué pasaría
[aviso]  otra/ruta:8          idem
[nota]   otra/mas:15          preferencia, no bloquea
```

Prioriza **lo que falla en silencio** sobre lo que falla ruidosamente: lo segundo lo encuentra
cualquiera al ejecutarlo.

Si el cambio esta bien, dilo en una linea. **No inventes hallazgos para justificar la revision.**
