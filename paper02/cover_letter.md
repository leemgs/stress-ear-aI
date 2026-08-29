# Cover Letter (Draft)

**August 29, 2026**

To the Editor-in-Chief  
*Journal of the American Medical Informatics Association*

**Re: “A Deterministic Referral-Safety Contract for Medical-LLM Extraction of Time-Critical Otologic Symptoms: An Open Benchmark Evaluation”**

Dear Editor,

I submit this manuscript for consideration as a Research and Applications
article. SAFE-EAR examines a narrow safety-engineering question: how can a
probabilistic text extractor be composed with a deterministic rule layer so that
an extracted red flag cannot subsequently be suppressed by a reassuring model
score?

The main contribution is a contract-based decomposition. The software invariant
(a fired rule forces the urgent path) is evaluated separately from the extraction
assumption (the relevant feature must first be represented correctly). This
prevents perfect execution of rule logic from being reported as complete
end-to-end safety. In the 37 author-curated free-text cases, recall was 56%
(10/18) for a naive rule extractor, 78% (14/18) for MedGemma-4B, and 100%
(18/18) for an explicitly in-sample tuned rule reference. All systems used the
same schema, adapter, final rules, and metrics.

The manuscript may interest JAMIA readers because it provides an executable
method for localizing safety failures at the boundary between clinical language
understanding and auditable decision logic. The benchmark, rules, adapter,
metrics, tests, and model runner are released at
<https://github.com/leemgs/stars-audiology>.

I have deliberately bounded the claims. The 71 cases are author-curated or
synthetic, not patient records; there was no independent clinical adjudication;
only one medical-LLM checkpoint and 18 urgent text cases were evaluated; and the
tuned rule extractor is not an external comparator. Accordingly, the paper makes
no clinical-effectiveness, transportability, fairness, or model-superiority
claim. Its proposed next step is a locked pilot on consecutively sampled,
deidentified notes with two clinical annotators and adjudication.

This computational study used no human-subjects data. I am the sole author, have
approved the manuscript, and accept responsibility for its content. I declare no
competing interests and no external funding. Generative AI tools assisted with
drafting and code scaffolding; I reviewed all content, and generated text was not
treated as clinical evidence or independent annotation. The manuscript is
original and is not under consideration elsewhere. Please verify these statements
and the journal's current administrative requirements before using this draft in
the submission portal.

Thank you for considering the manuscript.

Sincerely,

**Geunsik Lim**  
Sungkyunkwan University, Republic of Korea  
leemgs@g.skku.edu  
ORCID: [0000-0003-1845-7132](https://orcid.org/0000-0003-1845-7132)
