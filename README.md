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
- Obsidian `Backlinks`, `Outgoing Links`, vietinis grafas ir generuojamas `Ryšiai.canvas`.
- Žmogui skaitomi kiekvieno įstatymo incoming ir outgoing ryšiai su oficialiais pavadinimais.
- Neišspręstos ar dviprasmiškos citatos nelinkinamos kaip faktai ir laikomos atskirame audito indekse.
- Oficialūs TAR source laukų indeksai ir pavadinimų indeksas.

## Struktūra

```text
00 Pradžia.md
latest/{etar_id}.md
latest/{etar_id}.json
Indeksai/pavadinimai.jsonl
Indeksai/Pagal pavadinimą.md
Indeksai/aktų-ryšiai.jsonl
Indeksai/ryšiai/*.jsonl
Indeksai/backlinks/*.jsonl
Indeksai/išoriniai-ryšiai/*.jsonl
Indeksai/unresolved/*.jsonl
Indeksai/latest/{metai}.jsonl
Indeksai/aktai-lite/{metai}.jsonl
Indeksai/source/*.jsonl
Ryšiai/{etar_id}.md
Ryšiai.canvas
.obsidian/{app,core-plugins,graph}.json
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
- `Ryšiai/{etar_id}.md` - paspaudžiami konkretaus įstatymo incoming ir outgoing ryšiai.
- `Indeksai/aktų-ryšiai.jsonl` - agreguoti įstatymas → įstatymas ryšiai.
- `Indeksai/ryšiai/`, `backlinks/`, `unresolved/` - detalūs hash prefiksu suskaidyti ryšių indeksai.
- `Ryšiai.canvas` - ribotas svarbiausių aktų Obsidian canvas su žmonėms skaitomais pavadinimais.

## Obsidian

Atidaryk repo šaknį kaip Obsidian vault. Papildomi bendruomenės pluginai nereikalingi: bendri Graph, Backlinks, Outgoing Links ir Canvas nustatymai yra repo, o asmeninis `workspace.json` ir išvaizdos nustatymai nekomituojami.

## Atnaujinimas

Šis repo neatnaujinamas ranka. Pilnas procesas paleidžiamas privataus
generatoriaus repo `Refresh laws` GitHub Actions workflow. Jis parsisiunčia
šaltinį, perkuria tekstus, inline nuorodas ir Obsidian ryšius, validuoja korpusą
bei Pages preflight ir tik tada pushina šį repo. Push automatiškai perrenderina
GitHub Pages. Naudota generatoriaus versija fiksuojama `generator-version.txt`.

Lokaliai tą patį procesą galima paleisti generatoriaus repo:

```bash
cd ../lietuvos-istatymai-gen
./scripts/refresh-laws.sh
```

Po generavimo komanda validuoja šį repo ir pastato laikiną Pages versiją.
