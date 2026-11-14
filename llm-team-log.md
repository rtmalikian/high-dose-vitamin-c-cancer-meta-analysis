# LLM Team Log — Review 5 (results of the team process, 2026-11-13)

Roles (prompt version: task briefs issued 2026-11-13, archived in the coordinator transcript): Information Specialist (Stage 0); Search (coordinator, scripts in stage1-search/scripts); Screeners A and B (two written rule sets implemented as separate passes, screening-rules.md); Adjudicators x4 (one per 200-record chunk, reading title and abstract); Anchor Verifier; Citation Chaser; Full-Text Assessor; Extractors A and B; Settlement Reader; RoB Assessors A and B; RoB Adjudicator; Statistician (coordinator); GRADE assessor (coordinator, checked by Reviewer 6); Visual QA (coordinator); Peer panel of 6 (separate record in peer-review/).

Search counts: PubMed 620/620; Europe PMC 8,521/8,521 (full pagination after a capped first pull was discarded); ClinicalTrials.gov 56/56; raw 9,197; deduped 8,818. Not run: Embase, Scopus, Web of Science, CENTRAL, CINAHL, WHO ICTRP (reasons in search log). Blocked: OpenAlex, HTTP 429 on two attempts, hard stop applied.

Screening: agreement 94.7%; kappa 0.61 (three-level), 0.70 (binary). A: include 234, maybe 429, exclude 8,155. B: include 288, maybe 297, exclude 8,233. Three-level disagreements 466; records sent to adjudication (either pass include/maybe) 800. Adjudication outcomes: include to full text 45, exclude 753, flagged for author 2 (R1550, R2607).

Corrections surfaced by the process, all logged in stage0-protocol/amendments.md: (1) competing review first author is Qu, not Wang; (2) Shahzad 2026 added as competitor; (3) Ma 2014 and Ou 2023 reinstated after adjudication errors were caught by citation chasing; (4) Cameron and Campbell 1991 and Zhao 2018 added via chasing after being missed by all database retrievals; (5) R5493/R6240 deduplicated as one study.

Extraction: 702 cells compared across two independent passes; critical-field discrepancy rate 6.4% (23 of 360); all critical discrepancies settled by re-reading; Extractor A was correct on all six contested critical items (documented in settlement.md). Text-inclusive discrepancy rate 29.8%, driven by wording, abbreviation and completeness differences in free-text fields.

Risk of bias: 18 overall judgments, 16 agreed (88.9%), 2 disagreements settled by an adjudicator reading the papers (Paller 2024 Low; Simmons 2024 Serious). Final: RoB 2 Low 2, Some concerns 5, High 4; ROBINS-I Serious 5, Critical 2, Moderate 0.

Analysis corrections after first run: one sensitivity pool added after RoB adjudication (low-bias pair, HR 1.26). Figure builds: 2 failed visual inspections, rebuilt, third build passed (visual-qa-log.md).

Incidents kept visible: Europe PMC first pull was capped at 1,000 of 8,521 and was discarded, not counted; deduped file carried wrong DOIs on at least 3 records (R3031, R5530, R8331), so study matching used PMID plus title plus DOI; the Ou 2020 paper prints a PFS confidence interval that is internally impossible, transcribed verbatim everywhere it appears.

## Corrections after first build (Gate 3-4, 2026-11-13)
- Randomised total for the four-trial IV pool corrected from 685 to 625 (arithmetic slip at drafting; caught independently by Reviewers 1, 2 and 6).
- Cohort pooled HR 0.54 withdrawn at peer review (Reviewer 3 Blocker): the two studies are clinically unrelated and Lee 2026's mistletoe co-therapy had not been disclosed. Both studies now reported individually; Figure 3 regenerated without a diamond.
- Low-bias sensitivity pool demoted from headline status; Hartung-Knapp interval (0.03 to 52.8) and I2 (51.6%) now printed; verified by lowbias_check.py and Reviewer 2's recomputation. An intermediate script (analysis_revision.py) produced a wrong first value for this pool (HR 1.204, tau2 0); the error is recorded in analysis-revision.json and the verified script supersedes it.
- GRADE changes: pancreatic OS Low to Very low; harms Moderate to Low; Paller derivation corrected; entries added for the low-bias pool and the oral stratum.
- One interim PDF build was stale (LibreOffice conversion not refreshed) and was caught at visual inspection; the shipped PDF is the 18-page build inspected page by page.
- Gate 5/6 closure (2026-11-13): re-reviews R1 Accept, R2 Accept with conditions (all met), R3 Accept with minor revision (Blocker withdrawn), R4 Minor revision (residues fixed). Final build: 18 pages, figures inspected. Two open items carried to the journal stage, named in gate-log.md: PM/SJ estimators not run; condensed Table 2 formatting.
- Gate 5 closure (2026-11-13): Reviewer 1 returned Major revision (narrow, text-only) and showed the first response matrix had overstated four fixes. All seven of its must-fix items were then applied for real and verified by grep on the final 19-page build; the matrix carries a third addendum correcting its own earlier claims. Reviewers 2, 3, 4 passed with conditions, all met. Gate 6 integrity: PASS. Final state: no Blocker or Major open; three named journal-stage items (PM/SJ estimators, Table 2 formatting, Ou precision nit).
