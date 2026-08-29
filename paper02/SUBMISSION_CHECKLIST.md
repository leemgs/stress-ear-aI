# SAFE-EAR submission-readiness checklist

Target article category: **Research and Applications**. Recheck the journal's
live author instructions in the submission portal immediately before upload;
requirements can change.

## Files and disclosures

- [x] Manuscript has a structured abstract and a concise title.
- [x] Author, affiliation, corresponding-author email, and ORCID are present.
- [x] Funding, conflicts, author contributions, ethics, data/code availability,
      and AI-use disclosures are present.
- [x] No patient data are used; the manuscript does not imply IRB review of a
      nonexistent patient cohort.
- [x] Generated tables identify their generating scripts.
- [x] PDF rebuild succeeds with cross-references resolved.
- [ ] Confirm journal-specific word, table/figure, keyword, and reference limits
      against the live portal.
- [ ] Provide repository release/DOI and immutable commit hash before submission;
      replace the generic repository description in Data and Code Availability.
- [ ] Confirm whether the journal requires a separate title page or blinded main
      document, and export the files accordingly.
- [ ] Complete any journal-specific generative-AI disclosure form.

## Scientific claim audit

- [x] The manuscript calls the cases author-curated rather than clinical notes.
- [x] It states that labels, cases, rules, and v2 share authorship.
- [x] It treats structured 100% as implementation consistency, not clinical
      validation.
- [x] It treats v2 as an in-sample tuned reference, not model superiority.
- [x] It reports numerators, denominators, and Wilson intervals for the primary
      descriptive results.
- [x] It does not extrapolate 4/18 MedGemma misses to clinical prevalence.
- [x] It distinguishes a software override invariant from end-to-end safety.
- [x] It labels clinician verification and monitoring as future requirements,
      not evaluated workflow components.

## Material acceptance risks that require new work

These cannot be repaired by prose and should be disclosed rather than hidden:

1. No independently adjudicated clinical notes or external validation cohort.
2. No independent clinician review of benchmark labels or rule appropriateness.
3. One author, one medical-LLM checkpoint, one zero-shot prompt, and 18 urgent
   free-text cases.
4. No prevalence-weighted alert burden, human-factors evaluation, fairness
   assessment, clinical outcome, or time-to-referral analysis.
5. No powered paired model comparison and no case-level MedGemma output artifact
   supporting reanalysis of individual errors.

The highest-value revision after submission is a locked pilot on consecutively
sampled, deidentified notes with two clinical annotators and adjudication. Adding
more synthetic tuning is not a substitute.
