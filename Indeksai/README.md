---
tipas: "indeksu_dokumentacija"
licencija: "https://creativecommons.org/licenses/by/4.0/"
---
# Indeksai

`aktai.jsonl` turi po vieną JSON objektą kiekvienam teisės aktui.
`redakcijos.jsonl` turi po vieną JSON objektą kiekvienai suvestinei redakcijai.

`pavadinimai.jsonl` turi paieškos laukus pagal oficialų ir sutrumpintą pavadinimą.

`latest/` turi stabilias Markdown ir JSON nuorodas pagal `etar_id` į naujausią redakciją.

`source/` turi kategorijų indeksus, sugeneruotus tik iš oficialių TAR `Dokumentas` laukų: `rusis`, `dok_grupe`, `pobudis`, būsenų, institucijų ir boolean požymių.

`ryšiai.jsonl`, `unresolved.jsonl`, `sections.jsonl` ir `ai/chunks.jsonl` yra deterministinis linkinimo sluoksnis AI/RAG sistemoms; originalūs Markdown tekstai dėl linkinimo nemutuojami.

Archyviniai failai yra `Aktai/...`; stabilios nuorodos yra `latest/...`. Keliai yra reliatyvūs nuo korpuso šaknies. Oficialus šaltinis išlieka TAR.
Laukų aprašus ir validavimo taisykles rasite `schemas/` aplanke.
