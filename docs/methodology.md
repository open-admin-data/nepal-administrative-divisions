# Methodology

## Data Sources

- **OCHA COD-AB Nepal** (CC BY-IGO) — Province, district, and local unit records with P-codes and centroid coordinates
- **w38g0ru/palika** — Nepali (Devanagari) names for all 775 local units from official palika database
- **pracharya2601/image-api-wasabi** — Nepali names for districts and local units
- **younginnovations/nepal-locallevel-map** — Cross-reference Nepali local unit names
- **samirbasnet.com.np** — District-level postal codes for all 77 districts
- **Wikidata** (CC0) — Supplementary Nepali labels

## Processing

1. Administrative records from OCHA COD-AB XLSX gazetteer
2. Nepali names merged from multiple sources (100% coverage all levels)
3. Postal codes from Nepal Post district directory (100% coverage)
4. Multi-format export: JSON, NDJSON, CSV

## Accuracy

- Coordinates: 100% at all levels (from OCHA COD-AB centroids)
- Nepali (Devanagari) names: 100% at all levels
- Postal codes: 100% at district and local unit levels
- Build script is idempotent: same input always produces same output