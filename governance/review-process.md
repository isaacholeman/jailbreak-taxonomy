# Review Process

The review pipeline for evaluating and integrating submissions into the MLCommons Jailbreak Taxonomy.

## Review Pipeline

Submission (PR) → Triage → Technical Review → Placement Decision → Merge/Reject

### Triage (within 5 business days of submission)

- A taxonomy maintainer confirms the submission is complete (all required fields present)
- Assigns a severity label (see [Severity Framework](severity-framework.md)) for prioritization
- Assigns two reviewers: one taxonomy maintainer + one domain expert
- Incomplete submissions are returned with specific feedback

### Technical Review (within 15 business days of triage)

Reviewers evaluate against these criteria:

| Criterion | Question |
|-----------|----------|
| Novelty | Does this represent a genuinely distinct mechanism, or is it a variant of an existing leaf? |
| Placement | Is the proposed taxonomy placement correct? Does it satisfy the one-instance-to-one-leaf rule (R3)? |
| Evidence | Is the evidence of effectiveness sufficient and credible? (3+ models, documented methodology) |
| Splitting rules | If a new leaf is proposed, is the splitting rule consistent with the parent node's axis? (R4) |
| Executability | Is the mechanism described with enough structural precision to be independently reproduced? (R5) |
| Sanitization | Does the submission avoid providing copy-paste attack prompts? |

### Placement Decision

Based on review, the submission follows one of four paths:

1. **New leaf:** The technique is genuinely novel and creates a new leaf node. The PR is merged with the new leaf added to the appropriate family.

2. **Variant enrichment:** The technique is a variant of an existing leaf. The PR is merged as additional documentation/examples under the existing leaf, not as a new node.

3. **Structural revision needed:** The technique is novel but its placement requires a split, merge, or restructuring of existing nodes. This triggers the stabilization process (see Monthly Stability Releases below) before the PR is merged.

4. **Rejection:** The submission does not meet the evidence threshold, describes a known technique without novelty, or cannot be placed without violating the taxonomy's design requirements. Rejection includes a written rationale and is appealable (see [Appeals](maintainers.md#appeals)).

## Validating Submitted Techniques

When a submission's evidence is based solely on self-reported testing, the review team may conduct independent validation:

- Select 2-3 open-weight models not used in the original evidence
- Apply the described mechanism to a small set of seed prompts (drawn from the public AILuminate demo set)
- Evaluate whether the technique produces the claimed effect (elevated violating response rate compared to unmodified prompts)

Independent validation is **required** for submissions rated Critical or High severity. It is **recommended** for Medium severity and **optional** for Low.

## Evaluator Compatibility

For techniques that produce unusual response formats (e.g., encoded outputs, fragmented text, role-play-embedded responses), the review team assesses whether the current benchmark evaluator can correctly classify the resulting SUT responses. If not, this is flagged as an evaluator gap and documented in the leaf's metadata. Evaluator gaps do not block taxonomy inclusion but may affect benchmark integration timing.

## Update Cadence

### Rolling Updates (Continuous)

Individual PRs are reviewed and merged on a rolling basis following the review process above. Merged PRs update the main branch of the repository immediately.

### Monthly Stability Releases

On a defined day each month [TODO: pick a day, e.g., first Monday], a stability release is produced:

1. **Snapshot:** The current main branch is tagged with a version number (following semantic versioning).

2. **Stopping-rule check:** The full taxonomy is evaluated against the objective stopping rules from the v0.7 methodology (Section 5.1.3):
   - No new top-level branch is required by merged content
   - No node needs to be split or merged to maintain clear boundaries
   - No two nodes encode the same mechanism
   - Every leaf is supported by at least one documented instance
   - Every documented instance maps to exactly one leaf

3. **Prevalence update:** Prevalence metadata for all leaves is reviewed and updated based on new literature, incident reports, and community input.

4. **Changelog:** A dated entry in CHANGELOG.md summarizes all changes since the last release.

5. **Notification:** MLCommons members and the benchmark team are notified of the new release.

### Rationale for Monthly Cadence

- **Pace of research:** New jailbreak techniques appear in the literature at a rate of roughly several per month (based on the PRISMA corpus analysis in the v0.7 paper). Monthly releases capture emerging techniques without accumulating a large backlog.
- **Alignment with disclosure timeline:** The 45-day embargo in the Responsible Disclosure Policy means taxonomy updates can inform the benchmark team's tactic selection for the next release cycle.
- **Review capacity:** Given the review requirements (two reviewers, 15-day technical review), monthly releases allow 1-2 full review cycles per release window.
- **CVE/NVD analogy:** The National Vulnerability Database publishes on a continuous basis with periodic summary updates. Monthly taxonomy releases follow a similar model.
- **Standards alignment:** ISO SC 42 working group meetings and MLCommons working group cycles operate on roughly monthly cadences.

### High-Priority Updates

If a jailbreak technique emerges that represents an immediate, widespread, and severe threat (e.g., a technique that bypasses safety alignment on a majority of deployed models with high reliability), the following accelerated process applies:

1. Taxonomy maintainers convene within 48 hours to assess
2. If confirmed as Critical severity, the technique is added to the taxonomy via an expedited review (single reviewer, 3-day turnaround)
3. A patch-level stability release is issued immediately
4. The benchmark team is notified and may initiate an out-of-cycle benchmark run at their discretion

High-priority updates are documented in the CHANGELOG with an explicit "HIGH-PRIORITY" label and rationale.

---

**Status:** v0.1 DRAFT. Effective immediately for new submissions; timelines apply prospectively.
