# Contributing to the Jailbreak Taxonomy

MLCommons does not create or discover novel attacks. This taxonomy organizes and classifies jailbreak techniques that are already published in the academic literature, documented in practitioner reports, or submitted by external contributors. Keeping it comprehensive and current depends on community contributions.

## Why Contribute

The jailbreak taxonomy is a public good that no single organization could maintain alone. A more complete map of known attack mechanisms means better tools for defenders, researchers, and regulators.

MLCommons is an independent nonprofit that works across industry, academia, civil society, and government. That independence is what allows MLCommons to build consensus that regulators take seriously and that competing organizations can jointly contribute to. This public taxonomy is also complemented by the [MLCommons Jailbreak Benchmark](https://mlcommons.org/working-groups/ai-risk-reliability/ai-risk-reliability/), a private, instrumented benchmark with integrity protections that most academic taxonomy and benchmark projects cannot sustain. The taxonomy documents the full universe of known mechanisms; the benchmark privately selects from that universe to evaluate systems under test, with protections against data contamination and benchmark gaming. Contributions to the taxonomy directly improve the coverage and rigor of that benchmark.

## Who Can Contribute

We welcome contributions from:

- MLCommons working group members
- Academic researchers in AI security and adversarial machine learning
- Industry security teams and red-team practitioners
- Independent security researchers
- Standards body representatives
- Anyone with a documented novel jailbreak mechanism or taxonomy insight

## Types of Contributions

Listed from simplest to most involved.

### 1. Get Involved

- **Star the repository.** Helps others in the AI security community find this work. [Star mlcommons/jailbreak-taxonomy on GitHub](https://github.com/mlcommons/jailbreak-taxonomy).
- **Join the Security Workstream of the MLCommons AI Risk and Reliability working group.** The workstream that maintains this taxonomy and the broader risk and reliability benchmarking effort. [Sign up at mlcommons.org](https://mlcommons.org/working-groups/ai-risk-reliability/ai-risk-reliability/).
- **Share the project.** Link to this repository in papers, blog posts, talks, or social media.

### 2. Documentation Improvements

Fixes, clarifications, examples, and metadata corrections. Good entry point for new contributors.

**Examples:** typo fixes, improved definitions or examples, clarified splitting rules, updated references and citations.

Open a pull request with your changes. No issue or template needed for small fixes.

### 3. Attack List Contributions

Add documented jailbreak attacks to the taxonomy. This is the most common substantive contribution.

Most submissions reference an existing paper, blog post, or technical report. Submissions for novel attacks that have not yet been formally published are also accepted, provided there is enough documentation to evaluate the mechanism and evidence of effectiveness (see below).

**What we need:**

- Attack name and a link to documentation (paper, blog post, technical report, or pre-print)
- A brief description of the mechanism: how does the prompt manipulation work?
- Evidence of effectiveness (ideally tested against 3+ models, though partial information is welcome)
- Repository link, if available

**Pre-publication or novel attacks:** In place of a paper link, provide a written description of the mechanism and your testing results. More models tested, reproducible methodology, and quantified success rates will speed up review. Submitting an attack here does not constitute academic publication. Contributors should pursue formal publication separately if relevant.

**How to submit:**

- **If you know where the attack belongs in the taxonomy**, open a pull request adding a new entry to `taxonomy/attacks.yaml` (see [Regenerating Attack Tables](#regenerating-attack-tables) below). That single file is the source of truth; the category and family Attack Catalog tables are generated from it.
- **If you're unsure about placement or have partial information**, [open an Attack Submission issue](../../issues/new?template=attack-submission.md). The issue template will guide you through what to include. The maintainers will handle taxonomy placement.

A paper link with a sentence about the mechanism is enough to open an issue. Partial information is fine.

#### Regenerating Attack Tables

The Attack Catalog tables in each family README and each category document are generated from `taxonomy/attacks.yaml`. After editing that file, regenerate the tables locally and commit the result:

```
pip install pyyaml
python scripts/generate_tables.py
```

CI runs `python scripts/generate_tables.py --check` on every pull request and fails if the generated tables are out of sync with `attacks.yaml`.

Sections between the `<!-- BEGIN GENERATED: attack-catalog -->` and `<!-- END GENERATED: attack-catalog -->` markers are overwritten by the script; edit `attacks.yaml` instead.

### 4. Coded Attack Contributions

If you have implemented code that reproduces an attack, you can contribute that alongside an attack list entry.

Coded contributions follow the same submission paths as attack list contributions (issue or PR), but should additionally include:

- A link to a public repository with the implementation
- Documentation of the testing methodology and models evaluated
- Test cases or scripts that demonstrate the attack mechanism

A coded contribution without a corresponding attack catalog entry will be asked to provide one. The catalog entry (name, paper, mechanism description, models tested) is the minimum unit; code supplements it.

### 5. Taxonomy Structure Contributions

Propose changes to the taxonomy structure itself: new Family, Category, or Leaf nodes, or revisions to existing definitions and splitting rules.

**Substantial structural changes (adding new families, merging categories, redefining splitting rules) should typically be discussed within the MLCommons Security workstream before submitting a proposal.** [Join the working group](https://mlcommons.org/working-groups/ai-risk-reliability/ai-risk-reliability/) to participate in those discussions.

Minor structural proposals (e.g., a new leaf node with clear evidence and placement) can be submitted directly.

**Requirements:**

- Complete all required fields from the taxonomy schema:
  - Definition: Clear, concise description of the concept
  - Splitting rule: Criteria for distinguishing this node from siblings (if internal node)
  - Inclusion cues: Indicators that an attack belongs here
  - Exclusion cues: Indicators that an attack does not belong here
  - Canonical examples: 2-3 representative attacks that exemplify this category
  - Provenance references: Academic papers, documentation, or reports supporting the taxonomy decision

**Process:**

1. Review the existing taxonomy structure in `taxonomy/` directory
2. [Open a Taxonomy Contribution issue](../../issues/new?template=taxonomy-contribution.md) or draft PR to propose the new node
3. Provide detailed justification for the addition and its placement within the hierarchy
4. Prepare for discussion with the taxonomy maintainers

## What NOT to Submit

Do not submit:

- **Working exploit code or attack generation scripts** - We focus on documentation and categorization, not functional attack tools
- **Actual harmful prompts** - Structural descriptions and mechanistic explanations are sufficient; do not include copy-paste attack examples
- **Proprietary model details or API keys** - Keep contributions to publicly known information and models
- **Unsubstantiated claims** - Contributions should be grounded in evidence: published research, documented testing results, or reproducible demonstrations

## How to Submit

### Option 1: GitHub Issues

Use the issue templates to submit attack reports, taxonomy proposals, or bug reports.

- [Submit an attack](../../issues/new?template=attack-submission.md): Report an attack that should be in the catalog (published or novel)
- [Propose a taxonomy change](../../issues/new?template=taxonomy-contribution.md): Suggest structural changes to the taxonomy
- [Report a bug](../../issues/new?template=bug-report.md): Flag errors in documentation or data

### Option 2: Pull Requests

1. **Fork the repository** at [mlcommons/jailbreak-taxonomy](https://github.com/mlcommons/jailbreak-taxonomy)

2. **Create a feature branch** with a descriptive name:
   
   ```
   git checkout -b attacks/add-new-attack-name
   git checkout -b docs/fix-typo-in-overview
   git checkout -b taxonomy/propose-new-leaf
   ```

3. **Make your changes.** For attack additions, add an entry to `taxonomy/attacks.yaml` and run `python scripts/generate_tables.py` to refresh the catalog tables (see [Regenerating Attack Tables](#regenerating-attack-tables)). For taxonomy structure proposals, include a completed [taxonomy structure template](.github/TAXONOMY_STRUCTURE_TEMPLATE.md) in your PR.

4. **Open a Pull Request** with a clear title and a link to any supporting papers or documentation.

5. **Engage in review.**

### Option 3: Direct Contact

For questions about scope or placement before submitting:

- **Isaac Holeman** (Product Management): ih@mlcommons.org
- **Chris Knotz** (Technical): chris.knotz@mlcommons.org

## Submission Requirements by Type

### For Taxonomy Structure Additions

Proposals to add or modify families, categories, or leaves must include:

| Field              | Description                                                   |
| ------------------ | ------------------------------------------------------------- |
| Definition         | What does this taxonomy node represent?                       |
| Splitting Rule     | How do you distinguish this from siblings? (if internal node) |
| Inclusion Cues     | What indicators suggest an attack belongs here?               |
| Exclusion Cues     | What disqualifies an attack from this category?               |
| Canonical Examples | 2-3 attacks that exemplify this category                      |
| Provenance         | Papers, documentation, or reports supporting this decision    |

All fields must be completed for review.

### For Attack List Additions

At minimum, include a link to the published paper or report and a brief description of the attack mechanism. More complete submissions speed up review:

1. **Mechanism Description**: How the prompt manipulation works
2. **Evidence of Effectiveness**: Which models were tested and with what results
3. **Suggested Placement**: Where you think the attack belongs in the taxonomy (if you have a view)
4. **Repository Link**: If the attack has public code

If you only have a paper link and aren't sure about placement, [open an issue](../../issues/new?template=attack-submission.md).

## Review Process

All submissions follow a structured review process:

### Timeline

- **Triage**: Within 5 business days, submissions are evaluated for completeness and scope
- **Reviewer Assignment**: One taxonomy maintainer + one domain expert
- **Technical Review**: Within 15 business days of assignment
- **Resolution**: Maintainers communicate outcomes and next steps

### Possible Outcomes

1. **New Leaf** - Attack is novel and well-documented; added to taxonomy as new leaf node
2. **Variant Enrichment** - Attack is variant of existing category; enriches existing node with new evidence
3. **Structural Revision Needed** - Taxonomy structure should be modified to accommodate this attack
4. **Request for Iteration** - Does not yet meet criteria; feedback provided on how to strengthen the submission

### Review Criteria

Submissions are evaluated on:

- **Novelty** - Is this a genuinely new attack or a well-documented variant?
- **Placement** - Does the categorization fit the existing taxonomy structure?
- **Evidence** - Are claims about effectiveness well-documented and reproducible?
- **Splitting Rules** - Are definitions and boundaries clear and unambiguous?
- **Executability** - Can peers reproduce the testing or understand the mechanism?
- **Responsible framing** - Does the submission describe mechanisms structurally, consistent with the "What NOT to Submit" guidelines?

### Severity Assessment

Contributions are prioritized based on attack severity:

| Level    | Description                                          | Priority         |
| -------- | ---------------------------------------------------- | ---------------- |
| Critical | Affects broad model families with high success rates | Expedited review |
| High     | Significant risk to important model classes          | High priority    |
| Medium   | Moderate risk or narrow applicability                | Standard review  |
| Low      | Niche applicability or lower effectiveness           | Standard review  |

See `governance/severity-framework.md` for detailed severity criteria.

## Community Standards

### Code of Conduct

All contributors must adhere to the [MLCommons Code of Conduct](https://mlcommons.org/codeofconduct/).

## Contact and Questions

**Primary Contacts:**

- Isaac Holeman (Product Management): ih@mlcommons.org
- Chris Knotz (Technical): chris.knotz@mlcommons.org

**For:**

- Product, process, or administrative questions: Contact Isaac
- Technical or taxonomy structure questions: Contact Chris
- General discussion: Open an issue in the repository

**Community Discussion:**

- GitHub Issues: For bugs, suggestions, or general discussion
- Pull Requests: For direct contributions with code or content

## Resources

- [Taxonomy Schema](taxonomy/SCHEMA.md) - Detailed specification for all taxonomy fields
- [Attack Coding Guidelines](docs/attack-coding-process.md) - Patterns and conventions for attack implementations
- [Taxonomy Structure Template](.github/TAXONOMY_STRUCTURE_TEMPLATE.md) - Detailed form for taxonomy structure proposals
- [Severity Framework](governance/severity-framework.md) - Detailed severity assessment criteria
- [MLCommons Code of Conduct](https://mlcommons.org/codeofconduct/)

## Getting Started

1. Read this file and browse the existing taxonomy in `taxonomy/`
2. Check open issues and PRs to avoid duplicate work
3. Start with a documentation fix or attack submission to get familiar with the process
4. Reach out to maintainers if you have questions
