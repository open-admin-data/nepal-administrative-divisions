# Nepal Administrative Divisions / नेपाल

Open dataset of Nepal's administrative hierarchy — 7 provinces, 77 districts, and 775 local units (municipalities and rural municipalities). This repository provides structured, bilingual (Nepali/Devanagari + English) reference data with geographic coordinates and postal codes at every level. Designed for developers, researchers, government agencies, and AI agents.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| Province | 7 |
| District | 77 |
| Local Unit | 775 |
| Coordinates | ✅ Included (all levels) |
| Postal Codes | ✅ Included (local unit level) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-06-01 |
| Website | [openadmindata.org/np](https://openadmindata.org/np/) |
| API | [openadmindata.org/api/np](https://openadmindata.org/api/np/) |

## Browse by Province

| # | Province | Districts | Local Units | Link |
|---|----|----|----|------|
| 1 | बागमती (Bagmati) | 13 | 124 | [Browse](divisions/bagmati-np03/) |
| 2 | गण्डकी (Gandaki) | 11 | 88 | [Browse](divisions/gandaki-np04/) |
| 3 | कर्णाली (Karnali) | 10 | 79 | [Browse](divisions/karnali-np06/) |
| 4 | कोशी (Koshi) | 14 | 139 | [Browse](divisions/koshi-np01/) |
| 5 | लुम्बिनी (Lumbini) | 12 | 112 | [Browse](divisions/lumbini-np05/) |
| 6 | मधेश (Madhesh) | 8 | 140 | [Browse](divisions/madhesh-np02/) |
| 7 | सुदूरपश्चिम (Sudur Paschim) | 9 | 93 | [Browse](divisions/sudur-paschim-np07/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-province.json](data/all-province.json) | JSON | All 7 province records |
| [all-district.json](data/all-district.json) | JSON | All 77 district records |
| [all-local_unit.json](data/all-local_unit.json) | JSON | All 775 local unit records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-2 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-province.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['district']} districts")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-province.json", "utf-8"));
console.log(`Total: ${data.length} provinces`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=province, 2=district, 3=local unit |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{province-slug}/
divisions/{province-slug}/{district-slug}/
```

Local Units are listed inline in each district's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-province links
- [Per-province data](docs/llms-full/) — Full data by province

## Citation

```
Nepal Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/nepal-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [Open Admin Data](https://openadmindata.org) — Browse, search and explore administrative divisions for every country
- [open-admin-data](https://github.com/open-admin-data) — GitHub organization with all country repos
- [ListBase](https://www.listbase.org) — Structured reference data for every country
