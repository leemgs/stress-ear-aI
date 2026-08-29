# Cover Letter (Draft)

> Draft for the SAFE-EAR submission to the *Journal of the American Medical
> Informatics Association* (JAMIA), Oxford University Press. Optionally address
> the letter to the handling editor by name; otherwise the generic "Dear Editor"
> greeting is submission-ready.

---

**August 28, 2026**

To the Editor-in-Chief
*Journal of the American Medical Informatics Association* (JAMIA)
Oxford University Press / American Medical Informatics Association

**Re: Submission of "A Deterministic, Guideline-Derived Referral-Safety Layer over Open Medical-LLM Extraction for Time-Critical Otologic Symptoms: An Open Benchmark and Reproducible Evaluation (SAFE-EAR)."**

Dear Editor,

I am pleased to submit my manuscript, **SAFE-EAR**, for consideration in *JAMIA* as a **Research and Applications** article. It reports a patient-safety engineering contribution for LLM-assisted clinical documentation and triage, released with an open benchmark and a fully reproducible evaluation harness.

**What the manuscript is.** When a language model assists otology documentation or triage, a low model score must **never** suppress referral for a time-critical emergency such as sudden sensorineural hearing loss (SSNHL), where the treatment window is roughly two weeks. The safe design is not a better classifier but a **non-overridable floor**: a deterministic, guideline-derived red-flag layer, placed last, that overrides any probabilistic output. The paper specifies that layer and — unlike a design-only proposal — **evaluates** it, and then measures, honestly, that end-to-end safety is bounded by the *extraction* step rather than the rule layer.

**Real results, and why they are credible.** On correctly-extracted features the deterministic layer reaches **100% rule coverage** (recall 19/19; specificity 15/15; 0% over-referral) — a guarantee achieved without a model. End-to-end, on an open 71-case benchmark (34 structured, 37 free-text; **no patient data**), red-flag recall is extraction-bound and spans three independent systems scored through one identical harness and adapter: **naive 56% → `google/medgemma-4b-it` 78%** (14/18; 95% Wilson CI 55–91%; specificity 100%; macro-F1 0.75; urgency-changing error 10.8%; run-to-run consistency 1.00) **→ tuned 100%**. Because MedGemma neither authored the benchmark nor saw its cue lists, its 78% is an **extractor-independent** measurement — evidence the benchmark is neither saturated (a capable open medical LLM still misses four of eighteen urgent cases) nor gamed (the tuned 100% reflects benchmark-specific tuning). This directly answers the circularity concern raised against author-curated benchmarks. I present the comparison as a descriptive, deliberately small-sample study with numerators, denominators, and Wilson intervals — not a model-ranking claim.

**Why it fits JAMIA.** The work sits squarely in clinical informatics and the safe deployment of AI: it is a concrete, guideline-traceable instance of wrapping a probabilistic component in a deterministic guardrail for a time-critical decision, reported with an open benchmark and honest end-to-end numbers rather than an asserted target. The honest off-the-shelf expectation (~78%) is precisely why **mandatory clinician verification is load-bearing** — a message of direct interest to informatics readers building LLM-assisted clinical tooling.

**Contributions.**
1. A deterministic red-flag safety layer (seven rules from the SSNHL and tinnitus clinical practice guidelines) that overrides model output and cannot be suppressed by a low predicted risk.
2. An open 71-case benchmark and a two-level evaluation that separates *rule coverage* from *end-to-end* performance, isolating where risk actually arises.
3. A real open-medical-LLM (MedGemma) result, scored through the same harness/adapter as the rule-based references, that resolves the self-authored-benchmark circularity concern with an extractor-independent number.
4. A fully reproducible open release — rules, benchmark, schema-to-feature adapter, metrics, the MedGemma runner, and a free-GPU notebook — that reproduces the MedGemma row.

**Rigor and reporting.** The evaluation is TRIPOD+AI-aligned (a completed checklist is provided in `checklists/`), decoding is deterministic (greedy), and the full extraction-to-metrics path is exercised by unit tests with a deterministic no-model stand-in. All code, rules, benchmark, and metrics are openly available at <https://github.com/leemgs/stars-audiology>.

**Relationship to a companion paper.** SAFE-EAR is the executed, results-bearing version of the prospective safety component specified in a companion epidemiologic study (STARS; perceived stress tracks the tinnitus symptom more than the audiometric threshold), submitted separately to an audiology venue. The two papers are complementary — STARS is *why the problem matters*, SAFE-EAR is *how to make the AI-assisted pipeline safe* — and neither claims the other's results. This manuscript is self-contained and does not depend on STARS's acceptance.

**Responsible-AI statement.** Any prediction model here is a research tool with a declared intended use — never a screening, diagnostic, or triage device — and the deterministic layer is designed so that a model can only *escalate*, never suppress, an urgent referral. Generative AI tools assisted in drafting; the author reviewed and takes full responsibility for all content.

**Declarations.** This manuscript is original, is not under consideration elsewhere, and has not been published previously. Every benchmark case is expert-authored or synthetic; **no patient data** are used, so the work does not constitute human-subjects research. The author has approved the submission and agrees to be accountable for the work. The author declares no competing interests. No external funding supported this work.

I believe SAFE-EAR offers JAMIA readers a transparent, reproducible template for making LLM-assisted clinical pipelines safe against rare, time-critical failures, and I thank you for considering it.

Sincerely,

**Geunsik Lim** (sole and corresponding author) — Sungkyunkwan University, Republic of Korea — leemgs@g.skku.edu — ORCID [0000-0003-1845-7132](https://orcid.org/0000-0003-1845-7132)
