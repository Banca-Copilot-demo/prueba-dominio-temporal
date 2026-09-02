---
name: demo-sdlc-marcador-beta
description: "MARCADOR de prueba: existe SOLO en la version 0.2.0-beta.1. Si aparece instalado, el cliente tomo la entrada de la beta; si no aparece, tomo la estable."
metadata:
  id: demo-sdlc-marcador-beta
  owner_team: squad-sdlc
  owner_contact: squad-sdlc@ejemplo.dev
  data_classification: internal
  status: draft
  version: "0.2.0-beta.1"
  standard_version: "8.0.0"
---

# Marcador de la beta

Este skill no hace nada util. Existe para una sola medicion: **saber que version del plugin instalo
el cliente** cuando el indice ofrece dos entradas del mismo artefacto.

```
aparece      →  se instalo  0.2.0-beta.1
no aparece   →  se instalo  0.1.0
```
