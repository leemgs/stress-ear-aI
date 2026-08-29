# Paper B contribution audit

This audit separates manuscript claims that are supported now from additions
that require new data. It is intended to prevent cosmetic model-count expansion
from being mistaken for stronger clinical evidence.

## Contribution hierarchy after revision

1. **Primary methodological contribution — contract decomposition.** The paper
   separates a deterministic monotone-override invariant from the extraction
   assumption on which end-to-end recall depends.
2. **Primary empirical contribution — localization of residual risk.** Holding
   the safety layer and notes fixed while changing the extractor yields 56%,
   78%, and 100% recall, showing how extraction controls observed safety.
3. **Supporting contribution — authorship-independent stress test.** MedGemma
   did not generate benchmark cues or rule logic. This reduces circularity but
   does not make author-curated notes an external validation set.
4. **Infrastructure contribution — replaceable components.** The shared schema,
   adapter, rule layer, benchmark, metrics, and tests allow either notes or
   extractors to be replaced while the other components remain fixed.

## Claim boundary

| Claim | Current support | Permitted wording |
|---|---|---|
| A fired rule cannot be suppressed by a model score | Architecture and unit tests | Structural invariant |
| Encoded red-flag taxonomy is covered | 19/19 structured positives | Benchmark coverage |
| Complete clinical safety | Not evaluated | Must not be claimed |
| MedGemma performance on this benchmark | Executed 14/18 result | Descriptive benchmark result |
| Model superiority | Only 18 urgent notes | Must not be claimed |
| Real-note transportability | No patient notes | Prospective only |

## Highest-value next study

A locked pilot on consecutively sampled, deidentified otology notes would add
more value than additional tuning on synthetic cases. Before annotation or
model execution, freeze the eligibility criteria, schema, rules, prompt, and
primary endpoint. Use two independent clinical annotators plus adjudication and
report case flow, sensitivity/specificity with confidence intervals, parse or
abstention failures, clinician review time, and inter-annotator disagreement.

## Secondary extensions

- Compare two additional independently developed LLMs only after fixing the
  prompt and analysis plan; retain per-case outputs for paired analysis.
- Add Korean notes as a separately reported transportability cohort rather than
  translating the existing benchmark and pooling results.
- Evaluate reviewer workload and false-alert burden at realistic prevalence.
- Version the guideline-to-rule traceability matrix and have it reviewed by an
  otologist before any clinical deployment claim.
