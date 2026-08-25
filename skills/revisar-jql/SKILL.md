---
name: revisar-jql
description: Revisa una consulta JQL y explica por que cada cambio la mejora. Usar cuando alguien comparta una consulta de Jira que va lenta o devuelve resultados inesperados.
---

# Revisar JQL

Cuando recibas una consulta JQL, revisa en este orden y explica el porque de cada cambio:

1. **Filtro de proyecto.** Sin `project = ` la consulta recorre toda la instancia.
2. **Comodin por delante.** `~ "*texto"` impide aprovechar el indice de texto.
3. **Negacion amplia.** `status != Done` no aprovecha el indice.
4. **Orden por campo personalizado.** `ORDER BY cf[...]` obliga a ordenar en memoria.

Devuelve siempre la consulta corregida Y la razon de cada cambio.
