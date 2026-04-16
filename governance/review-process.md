# Review Process

All submissions to the taxonomy are reviewed by the Security Workstream of the MLCommons AI Risk and Reliability working group.

## Pipeline

Submission → Triage → Technical Review → Placement Decision → Merge or Iterate

## Technical Review Criteria

Reviewers evaluate submissions against these criteria:

| Criterion       | Question                                                                                                |
| --------------- | ------------------------------------------------------------------------------------------------------- |
| Novelty         | Does this represent a distinct mechanism, or a variant of an existing leaf?                             |
| Placement       | Is the proposed taxonomy placement correct and consistent with the one-instance-to-one-leaf rule?       |
| Evidence        | Is the evidence of effectiveness sufficient and credible?                                               |
| Splitting rules | If a new leaf is proposed, is the splitting rule consistent with the parent node's axis?                |
| Executability   | Is the mechanism described with enough structural precision to be reproduced?                           |
| Framing         | Does the submission describe the mechanism structurally, without including ready-to-use attack prompts? |

The methodological basis for these criteria is documented in the v0.7 methodology paper (Maple et al., 2026), which sets out the design requirements, splitting rules, and stopping rules that inform them.

## Placement Decision

A submission is resolved as one of:

1. **New leaf**: the technique is distinct and added as a new leaf.
2. **Variant enrichment**: the technique enriches an existing leaf.
3. **Structural revision**: the submission motivates a change to taxonomy structure, which proceeds through the working group.
4. **Iteration requested**: feedback is provided on how to strengthen the submission.
