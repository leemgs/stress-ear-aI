# JAMIA Submission Readiness Checklist — SAFE-EAR (v0.9)

Cross-checked against the *Journal of the American Medical Informatics
Association* (JAMIA, Oxford University Press) author requirements for the
**Research and Applications** article type. JAMIA uses a structured abstract,
**ICMJE/Vancouver numbered references**, and ScholarOne (Manuscript Central)
submission.

> **Verify before submitting.** JAMIA/OUP update their instructions
> periodically. Treat every "⚠️ verify" item as *check the current JAMIA
> "Instructions for Authors" page and the ScholarOne portal*, not as a settled
> fact. Items are marked ✅ present / ⚠️ needs attention / ❌ missing.

---

## 0. Article type — decide first

The manuscript is framed as **Research and Applications** (a methods /
open-benchmark study; safety engineering for clinical AI), stated on the title
block of `main.tex`. This is the natural JAMIA category for a reproducible
evaluation with an open benchmark and real model results. Confirm the category
with the editorial office if in doubt, since it drives word and structure limits.

---

## 1. Manuscript structure & formatting

| Item | Status | Notes |
|------|--------|-------|
| Title, running head, author + affiliation | ✅ | In `main.tex`; running head "SAFE-EAR / Deterministic Referral Safety over LLM Extraction". |
| Sole/corresponding author + ORCID | ✅ | Geunsik Lim; ORCID 0000-0003-1845-7132 on the title block and in Declarations. Enter in the portal metadata too. |
| IMRaD for Research and Applications | ✅ | Background and Significance → Materials and Methods → Results → Discussion → Conclusion. |
| Double-spaced | ✅ | `\doublespacing`. |
| Page numbers | ✅ | `fancyhdr` centered footer. |
| ⚠️ Blinded/anonymized manuscript | ⚠️ verify | JAMIA review is **not** double-anonymized by default (unlike the AJA companion), so no masking toggle is provided. Confirm the current JAMIA policy; if masked review is requested, remove author/affiliation/ORCID and the repository URL for the review copy. |
| Continuous line numbers | ⚠️ verify | Not currently enabled (the AJA companion uses `lineno`). Add `lineno` if the JAMIA portal requires line numbers for review. |

## 2. Abstract & keywords

| Item | Status | Notes |
|------|--------|-------|
| Structured abstract | ✅ | Objective / Materials and Methods / Results / Discussion / Conclusion headings present. |
| Abstract word limit | ✅ | ≈244 words. Verify against the current JAMIA limit (commonly ~250) at upload. |
| Keywords | ✅ | Ten focused keywords. ⚠️ verify the JAMIA maximum and trim if needed. |

## 3. References (ICMJE / Vancouver, numbered)

| Item | Status | Notes |
|------|--------|-------|
| Numbered citation style | ✅ | `natbib` with `[numbers,sort&compress]`; inline `thebibliography`. |
| Citations ↔ entries resolve | ✅ | 10 distinct `\cite` keys ↔ 10 `\bibitem` entries; no orphan citations, no uncited entries. |
| Complete bibliographic data (vol/issue/pages/DOI) | ⚠️ verify | DOIs were web-verified for the five clinical-LLM/evaluation/safety references added earlier; re-confirm all 10 entries carry complete Vancouver-format data before upload. |

## 4. Tables & figures

| Item | Status | Notes |
|------|--------|-------|
| All tables cited in text, in order | ✅ | Four result tables are auto-generated from the evaluation JSONs and `\input` by `main.tex` — `tab:redflag_results`, `tab:redflag_bycat`, `tab:extraction`, `tab:llm_compare` — each cited in text. ⚠️ Note: `tables/table_extraction_compare.tex` (`tab:extraction_compare`) exists but is **not** `\input` or cited — remove the orphan file or wire it in before submission. |
| All figures cited in text | ✅ | One TikZ architecture figure (`fig:arch`) cited in text. ⚠️ verify JAMIA's figure file-format/resolution rules if separate uploaded figure files are required rather than inline TikZ. |
| Captions self-contained | ✅ | Define abbreviations and the "no patient data" caveat. |
| Numbers match committed outputs | ✅ | Every reported value matches `outputs/*.json`: rule coverage 100% (19/19; specificity 15/15); end-to-end recall naive 56% (10/18) → MedGemma 78% (14/18; Wilson 55–91%; specificity 100%; macro-F1 0.75; urgency-changing error 10.8%; consistency 1.00) → tuned 100% (18/18). Regenerate tables via the `run_*_eval.py` scripts before final build. |

## 5. Required disclosures & statements

| Item | Status | Notes |
|------|--------|-------|
| Competing interests (ICMJE) | ✅ | "None declared" in Declarations. ⚠️ complete the ICMJE disclosure form in the portal too. |
| Funding | ✅ | "None." |
| Author contributions (CRediT) | ✅ | Present in Declarations. |
| Ethics / human-subjects statement | ✅ | No human-subjects data; all cases expert-authored or synthetic; prospective clinical evaluation only under IRB approval. |
| Data availability | ✅ | Benchmark, rules, extractors, harness, tests openly in the repository; no patient data used or redistributed. |
| Code availability | ✅ | Named source files + free-GPU reproduction notebook. |
| AI-use disclosure | ✅ | Generative-AI drafting/code-scaffolding disclosed; model roles constrained to clinician-verified extraction. |
| Reporting-guideline checklist (TRIPOD+AI) | ✅ | Completed checklist in `checklists/TRIPOD-AI_checklist.md`; upload as a supplement. |

## 6. Cover letter

| Item | Status | Notes |
|------|--------|-------|
| Cover letter present | ✅ | `cover_letter.md` — states article type, headline results, circularity resolution, and relationship to the STARS companion (self-contained; no dependence on STARS acceptance). |
| Placeholders filled | ✅ | Date (2026-08-28) and ORCID filled; generic "Dear Editor" salutation is submission-ready. |
| Originality / not-under-review statement | ✅ | Included. |
| Dual-submission / companion-paper note | ✅ | Discloses the separately-submitted STARS companion and states neither claims the other's results. ⚠️ if the portal asks about related submissions, mention STARS there too. |
| Suggested reviewers | ⚠️ verify | Supply names only if the ScholarOne portal requests them. |

## 7. Reproducibility (Paper B's core selling point)

| Item | Status | Notes |
|------|--------|-------|
| Numbers regenerate from committed code | ✅ | `run_redflag_eval.py`, `run_extraction_eval.py`, `run_llm_eval.py` regenerate the tables/JSONs; unit tests exercise the full path with a deterministic no-model stand-in. |
| MedGemma row reproducible without local GPU | ✅ | `code/notebooks/medgemma_eval_colab.ipynb` reproduces the row on a free-tier T4. |
| Determinism | ✅ | Greedy decoding; run-to-run consistency 1.00 reported. |

---

## Pre-submission action list (ordered)

1. **Confirm the JAMIA article category** (Research and Applications) and current word/reference/keyword limits. *(author — editorial office / portal)*
2. **Confirm the review-anonymization policy**; add masking + `lineno` only if JAMIA requests them for review (§1).
3. Re-verify all **10 references** carry complete Vancouver-format data incl. DOIs (§3).
4. Regenerate result tables from the `run_*_eval.py` scripts and re-build the PDF (`bash build.sh`); confirm no `??`/`[?]` cross-references remain (§4).
5. Complete the **ICMJE competing-interest form** in the portal (§5).
6. Upload the **TRIPOD+AI checklist** as a supplement (§5).
7. In the portal, disclose the **related STARS companion submission** if asked (§6).
8. Enter **ORCID** in the portal metadata (§1).
