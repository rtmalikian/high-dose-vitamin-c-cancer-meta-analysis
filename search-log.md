# Stage 1 Search Log — Review 5 (run 2026-11-13, America/Los_Angeles)

## Sources RUN in full
| Source | String / query as run | Hits | Retrieved | File |
|---|---|---|---|---|
| PubMed / MEDLINE via E-utilities | ("Ascorbic Acid"[Mesh] OR ascorbate OR "vitamin C") AND ("Neoplasms"[Mesh] OR cancer OR carcinoma OR malignancy OR neoplasm) AND (intravenous OR pharmacologic OR "high-dose" OR parenteral OR oral) AND (randomized OR randomised OR cohort OR trial OR placebo) | 620 | 620 records (efetch XML in 4 batches) | pubmed_records.json, raw/pubmed_efetch_*.xml |
| Europe PMC (REST, cursor pagination, 9 pages) | (ascorbate OR "vitamin C") AND cancer AND (intravenous OR "high-dose" OR pharmacologic) AND (randomized OR cohort OR trial) | 8,521 | 8,521 | europepmc_records.json, raw/europepmc_full_log.json |
| ClinicalTrials.gov API v2 | query.term = "vitamin C ascorbate cancer" | 56 | 56 | ctgov_records.json |

Raw total 9,197. Deduped (DOI, then PMID, then NCT, then normalised title): 8,818. Dedupe script: scripts/dedupe.py; counts: stage2-screening/dedupe_counts.json.

## Sources NOT RUN (never implied as searched)
- Embase — no access. Ready string: ('ascorbic acid'/exp OR ascorbate OR 'vitamin C') AND ('neoplasm'/exp OR cancer) AND (intravenous OR pharmacologic OR 'high dose') AND ('randomized controlled trial'/exp OR cohort)
- Scopus — no access. Ready string: TITLE-ABS-KEY(ascorbate OR "vitamin C") AND TITLE-ABS-KEY(cancer OR neoplasm) AND TITLE-ABS-KEY(intravenous OR pharmacologic OR "high-dose")
- Web of Science — no access. Ready string: TS=(ascorbate OR "vitamin C") AND TS=(cancer OR neoplasm*) AND TS=(intravenous OR pharmacologic OR "high-dose") AND TS=(randomized OR cohort)
- CENTRAL (Cochrane Library) — no direct access in this environment. Ready string: (ascorbate OR "vitamin C") AND (cancer OR neoplasm) AND (intravenous OR "high-dose") in Title/Abstract/Keywords.
- CINAHL — no access, low expected yield for this drug question. Ready string as for CENTRAL with CINAHL headings.
- WHO ICTRP — portal is an interactive form with no usable API. Route 1 (search page) returned a redirect; route 2 (single-trial page for NCT02905578) loaded in full, which verifies single records but is not a registry search. Two routes tried. Logged as NOT RUN as a search, with ready query: condition = cancer / neoplasm; intervention = ascorbate / vitamin C; recruitment = all.
- OpenAlex — RETRIED TWICE, both HTTP 429 (shared free daily budget exhausted, per the API response). Hard stop for this provider in this run per rate-limit rule. Logged as BLOCKED (rate limit), not searched. No further OpenAlex calls in this run.

## Citation chasing
Run on: Qu et al 2025 (PMID 40613397), Shahzad et al 2026 (PMID 42507830, added by Amendment 2026-11-13-01), Bodeker 2024, Wang F VITALITY 2022, NCI PDQ, J Med Life 2026 (PMID 41815850). Method and yield in citation-chasing.md (added after included set is fixed, plus forward chasing on the anchor set done at Stage 1).

## Notes
- No capped or first-N sample was counted as searched. Europe PMC first pull capped at 1,000 was discarded and replaced by full cursor pagination (8,521/8,521).
- Search date for the manuscript: 13 November 2026 (run date in this workspace; all outputs dated 2026-11-13 per author instruction).
