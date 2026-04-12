# Governance Roles and Responsibilities

Roles, responsibilities, and selection processes for governing the MLCommons Jailbreak Taxonomy project.

## Roles

| Role | Responsibilities | Minimum count |
|------|-----------------|---------------|
| Taxonomy Lead | Overall process ownership; monthly release sign-off; escalation point for disputes | 1 |
| Taxonomy Maintainer | Triage, review, merge authority; stopping-rule checks; prevalence updates | 3 active |
| Domain Expert Reviewer | Technical review of submissions in their area of expertise | Rotating pool, minimum 5 |
| Benchmark Liaison | Communicates benchmark team needs to taxonomy maintainers; flags evaluator compatibility issues | 1 |

## Maintainer Selection and Rotation

[TODO: Define process. Considerations:]

- Maintainers should represent a diversity of organizations and perspectives
- Term limits (e.g., 2-year terms, renewable once) to prevent stagnation
- Onboarding process including review of the v0.7 methodology and the six design requirements (R1-R6)

[TODO: Define process for onboarding and rotating domain experts.]

## Reviewer Pool

The reviewer pool consists of:

- **Taxonomy maintainers** (minimum 3 active at any time): responsible for structural consistency and design requirement compliance
- **Domain experts** (rotating): researchers and practitioners with demonstrated expertise in LLM security, red-teaming, or adversarial ML

## Conflict of Interest

A reviewer who is employed by or affiliated with a model provider whose SUT is referenced in the submission's evidence recuses from that review. Reviewers who are co-authors of the cited provenance paper may participate but must disclose the relationship.

## Appeals

A contributor whose submission is rejected may appeal:

1. Submit a written appeal to the Taxonomy Lead within 14 days of rejection, addressing the specific review feedback
2. The Taxonomy Lead assigns a fresh reviewer (not involved in the original review)
3. The fresh reviewer's recommendation is discussed at the next monthly stability release meeting
4. Final decision rests with the Taxonomy Lead, documented in the PR

## Code of Conduct

All contributors and reviewers adhere to the [MLCommons Code of Conduct](https://mlcommons.org/policies/). Additionally:

- Submissions must not include ready-to-use attack tools designed for malicious exploitation
- Reviewers must disclose conflicts of interest
- Discussion of specific SUT vulnerabilities in public GitHub issues is prohibited; use the private review channel

[TODO: Establish a private communication channel for security-sensitive review discussions.]

---

**Status:** v0.1 DRAFT. Initial maintainers and appointments will be finalized by the AIRR working group.
