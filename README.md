---
tipas: "repo_aprasymas"
licencija: "https://creativecommons.org/licenses/by/4.0/"
---

# Lietuvos įstatymai

Public, latest-only Lietuvos Respublikos įstatymų korpusas Markdown ir JSON formatais.

Šiame repo laikomi tik sugeneruoti vieši duomenys. Generatorius gyvena atskirame repo: [alzyras/lietuvos-istatymai-gen](https://github.com/alzyras/lietuvos-istatymai-gen).

Šaltinis: [Teisės aktų registro duomenys](https://data.gov.lt/datasets/2613/). Licencija: [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/). Priskyrimas: Valstybės duomenų agentūra; Lietuvos Respublikos Seimo kanceliarija.

## Kas čia yra

- Tik galiojantys dokumentai, kurių TAR `rusis` yra `Įstatymas`.
- Tik naujausia kiekvieno įstatymo versija.
- Stable keliai pagal TAR dokumento ID: `latest/{etar_id}.md` ir `latest/{etar_id}.json`.
- Markdown tekstuose automatiškai sulinkinti deterministiškai atpažinti straipsniai, dalys, punktai ir kitų aktų nuorodos.
- Oficialūs TAR source laukų indeksai ir pavadinimų indeksas.

## Struktūra

```text
00 Pradžia.md
latest/{etar_id}.md
latest/{etar_id}.json
Indeksai/pavadinimai.jsonl
Indeksai/Pagal pavadinimą.md
Indeksai/latest/{metai}.jsonl
Indeksai/aktai-lite/{metai}.jsonl
Indeksai/source/*.jsonl
Atnaujinimai/*.md
Ataskaitos/*.md
schemas/*.schema.json
```

## Pagrindiniai entrypointai

- `latest/` - patys įstatymų tekstai ir jų JSON metaduomenys.
- `Indeksai/pavadinimai.jsonl` - paieška pagal oficialų ir sutrumpintą pavadinimą, pvz. `Lietuvos Respublikos žemės įstatymas` ir `žemės įstatymas`.
- `Indeksai/latest/{metai}.jsonl` - pilnesni latest įrašai pagal priėmimo metus.
- `Indeksai/aktai-lite/{metai}.jsonl` - lengvesnis sąrašas pagal metus.
- `Indeksai/source/` - oficialūs TAR metaduomenų pjūviai.

## Atnaujinimas

Šis repo neatnaujinamas ranka. Naudok generatoriaus repo:

```bash
cd ../lietuvos-istatymai-gen
./scripts/update-latest-laws-text.sh
```

Po generavimo komanda validuoja šį repo.
