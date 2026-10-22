# @red-cup-engineering/glossary-census-service

<!-- 561-group-standards:badges:start -->
[![Red Cup Engineering](https://img.shields.io/badge/561%20Group-Red%20Cup%20Engineering-c0392b)](https://github.com/red-cup-engineering)
[![License: MIT](https://img.shields.io/badge/license-MIT-c0392b)](LICENSE)
[![Indigenous data: CARE](https://img.shields.io/badge/Indigenous%20data-CARE-4b6f44)](https://github.com/red-cup-engineering/.github/blob/main/GOVERNANCE.md)
[![Tips welcome](https://img.shields.io/badge/tips-welcome-d4a017)](https://github.com/561-group/.github/blob/main/TIPS.md)
<!-- 561-group-standards:badges:end -->

Census of a glossary index, so the 561 Group can see the state of its glossaries in one record.
The term owner ([term-engineering](../term-engineering-services-section/README.md)) admits or refuses each carrier; this service only counts what it judged.

`src/glossary-census.mjs` exports `censusGlossaryIndex(index, { date })`, a pure fold over a `computer-glossary-index.v2` index, which carries every glossary facet (terms, concepts and topics).
It returns a dated `computer-glossary-census.v1` record and one row per carrier.
The record carries:

- admitted and refused carriers;
- refusals by rule and by message;
- admission per concept scheme (owning section);
- empty-bodied stubs;
- identities that more than one scheme carries.

`scripts/census-glossary.mjs` (bin `census-glossary`, `--root <dir> [--out-dir <dir>] [--date YYYY-MM-DD]`) indexes every glossary term under a root through the term owner and writes `<date>.json` plus a `<date>.rows.tsv` sidecar (path, scheme, identity, admitted, refusal rules).
`--out-dir` defaults to `services/561-group-services-section/data/records/knowledge-census-records/glossary/census/` beneath the root.
