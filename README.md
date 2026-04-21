# MLCommons Jailbreak Attack Taxonomy

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Version](https://img.shields.io/badge/version-0.7.0-blue.svg)](CHANGELOG.md)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)

A mechanism-first classification of single-turn, inference-time prompt attacks on large language models, developed by the [MLCommons AI Risk and Reliability (AIRR)](https://mlcommons.org/working-groups/ai-risk-reliability/ai-risk-reliability/) working group.

**MLCommons does not create or discover novel attacks.** This taxonomy organizes and classifies jailbreak techniques that are already published in the academic literature, documented in practitioner reports, or submitted by external contributors through the [open contribution process](CONTRIBUTING.md). Its purpose is to help defenders, researchers, and standards bodies understand the landscape of known attack mechanisms.

## Quick Overview

The taxonomy organizes known jailbreak mechanisms into four families based on the dominant prompt-manipulation strategy:

| Family                                                            | Prevalence | Categories | Leaves | Description                                               |
| ----------------------------------------------------------------- | ---------- | ---------- | ------ | --------------------------------------------------------- |
| [Perturbation](taxonomy/families/perturbation/)                   | 36.28%     | 2          | 4      | Modifies surface form while preserving semantic intent    |
| [Encoding Abuse](taxonomy/families/encoding-abuse/)               | 20.35%     | 2          | 5      | Manipulates representation or structural formatting       |
| [Overt Carriers](taxonomy/families/overt-carriers/)               | 19.47%     | 2          | 4      | Applies explicit rhetorical pressure or narrative framing |
| [Composition & Ordering](taxonomy/families/composition-ordering/) | 23.89%     | 2          | 5      | Arranges prompt structure to embed harmful objectives     |

Total: 4 families, 8 categories, 18 leaf-level mechanisms.

> **See all 113 attacks in one place →** [Attacks Overview](taxonomy/attacks-overview.md) — a collapsible catalog organized by family, covering every attack documented in this taxonomy.

## Repository Structure

```
jailbreak-taxonomy/
├── README.md                    # This file
├── CHANGELOG.md                 # Version history
├── CITATION.cff                 # Machine-readable citation metadata
├── CONTRIBUTING.md              # How to contribute
├── DATASHEET.md                 # Dataset documentation (Gebru et al. framework)
├── LICENSE                      # CC-BY-4.0
├── taxonomy/
│   ├── taxonomy.yaml            # Machine-readable taxonomy structure
│   ├── attacks.yaml             # Machine-readable attack catalog (113 attacks)
│   ├── taxonomy-overview.md     # Human-readable summary with tree diagram
│   ├── attacks-overview.md      # Auto-generated cross-family catalog (collapsible by family)
│   └── families/
│       ├── perturbation/
│       │   ├── README.md
│       │   ├── plain-perturbations.md
│       │   └── transfer-text-perturbations.md
│       ├── encoding-abuse/
│       │   ├── README.md
│       │   ├── encoding-unicode-tricks.md
│       │   └── wrappers-and-schemas.md
│       ├── overt-carriers/
│       │   ├── README.md
│       │   ├── direct-override-patterns.md
│       │   └── roleplay-and-template-jailbreaks.md
│       └── composition-ordering/
│           ├── README.md
│           ├── context-framing-and-deception.md
│           └── fragment-assembly.md
├── .github/
│   ├── ISSUE_TEMPLATE/          # GitHub issue templates (attack submission, taxonomy contribution, bug report)
│   ├── PULL_REQUEST_TEMPLATE.md # Default PR template
│   └── TAXONOMY_STRUCTURE_TEMPLATE.md  # Detailed form for taxonomy structure proposals
├── governance/
│   ├── maintainers.md           # Working group ownership, conflicts of interest, code of conduct, contact
│   └── review-process.md        # Review pipeline and technical review criteria
└── releases/
    └── v0.7.0/
        └── taxonomy-snapshot.yaml
```

## Key Concepts

### Mechanism-First Classification

Attacks are grouped by **how the prompt manipulates the model at inference time**, not by the hazards they target or the outcomes they produce. A role-play attack and a Base64-encoded attack may both aim to extract the same harmful content, but they exploit fundamentally different mechanisms and require different defenses. The taxonomy classifies them separately for this reason.

### Three-Tier Hierarchy

The taxonomy uses a Family > Category > Leaf structure. **Families** capture the broadest mechanism distinction (surface perturbation vs. encoding manipulation vs. rhetorical override vs. compositional arrangement). **Categories** subdivide by a single explicit splitting rule. **Leaves** are the atomic units: each corresponds to a specific, testable manipulation strategy with documented instances in the literature.

### The Taxonomy Is Not the Benchmark

This is a critical distinction. The taxonomy is the **public universe** of known jailbreak mechanisms, organized and documented for community use. The MLCommons Jailbreak Benchmark is a **private selection** from the taxonomy, instantiated with specific prompts and evaluated against specific systems under test.

All techniques in this taxonomy originate from published academic research, practitioner reports, or community submissions — MLCommons classifies and organizes these techniques but does not develop or discover them. Publishing the taxonomy does not reveal which techniques are tested in the benchmark. A model provider that defends against the entire taxonomy improves genuinely; one that tries to guess the benchmark's subset gains no reliable advantage. The taxonomy benefits defenders, researchers, and standards bodies. The benchmark's integrity is preserved by the separation.

### Design Requirements

The taxonomy satisfies six requirements from the v0.7 methodology (Section 5.2):

1. **Mechanism-first placement**: classification depends on the dominant bypass mechanism observable in the prompt
2. **One-instance-to-one-leaf mapping**: each attack instance maps to exactly one leaf, enabling deterministic labeling
3. **Consistent splitting rules**: every internal node applies a single explicit axis to distinguish its children
4. **Executability and corpus suitability**: every leaf supports concrete, testable prompt instances
5. **Prevalence-aware validation**: empirical prevalence is recorded to guide balanced sampling
6. **Coverage across major families**: all major prompt-manipulation strategies observed in the literature are represented

## How to Use This Taxonomy

**Researchers**: Start with the [taxonomy overview](taxonomy/taxonomy-overview.md) for the full tree, then read family and leaf documentation for mechanism details, inclusion/exclusion cues, canonical examples, and the attack catalog for each leaf. The [attacks overview](taxonomy/attacks-overview.md) provides a single collapsible index of all 113 attacks grouped by family, useful for scanning the complete catalog in one place. The [taxonomy.yaml](taxonomy/taxonomy.yaml) provides the machine-readable taxonomy structure; [attacks.yaml](taxonomy/attacks.yaml) provides the machine-readable attack catalog with paper links, repositories, and model coverage for all 113 documented attacks.

**Security teams and red-team practitioners**: Use the leaf-level documentation to structure red-teaming exercises by mechanism family for coverage across structurally distinct attack strategies. The prevalence data helps prioritize testing.

**Standards bodies and policymakers**: Reference the taxonomy when specifying evaluation requirements or assessing benchmark coverage claims. The governance framework and versioning ensure longitudinal stability.

**Contributors**: See [CONTRIBUTING.md](CONTRIBUTING.md) for how to propose new mechanisms, place new attacks, or improve documentation.

## Versioning

The taxonomy uses semantic versioning:

- **Major** (e.g., 1.0 → 2.0): A new Level 1 family is added or fundamentally restructured
- **Minor** (e.g., 1.0 → 1.1): New leaves or categories are added; existing leaves are refined
- **Patch** (e.g., 1.0.0 → 1.0.1): Documentation fixes, example updates, metadata corrections

Monthly stability releases produce a tagged snapshot with a stopping-rule check, prevalence update, and changelog entry. See [CHANGELOG.md](CHANGELOG.md) for version history.

## Governance

The taxonomy is maintained by the Security Workstream of the MLCommons AI Risk and Reliability working group. All submissions are reviewed against the criteria documented in [`governance/review-process.md`](governance/review-process.md). The methodological basis is described in the v0.7 methodology paper.

See also:

- [Governance overview](governance/maintainers.md)
- [Review process](governance/review-process.md)
- [MLCommons Code of Conduct](https://mlcommons.org/policies/)

## License

This work is licensed under the [Creative Commons Attribution 4.0 International License](LICENSE) (CC-BY-4.0).

## Citation

If you use or reference this taxonomy, please cite the relevant papers:

### v0.7 Jailbreak Methodology Paper (2026)

```bibtex
@article{maple2026robust,
  title={A Robust, Defensible, and Reproducible Methodology for Benchmarking
         Single-Turn Jailbreak Attacks on Large Language Models},
  author={Maple, Carsten and Tapwal, Riya and Knotz, Chris and Ezick, James
          and Goel, James and Parrish, Alicia and Ricciuti, Federico and
          Petit, Jonathan and Hui, Ong Chen and Lim, Seok Min and others},
  year={2026},
  month={February},
  url={https://mlcommons.org/wp-content/uploads/2026/02/MLCommons___Security___Jailbreak_0_7_Paper_Collaborative.pdf}
}
```

### v0.5 Jailbreak Benchmark Paper (2025)

```bibtex
@article{goel2025ailuminate,
  title={AILuminate Security: Introducing v0.5 of the Jailbreak Benchmark
         from MLCommons},
  author={Goel, James and Parrish, Alicia and Knotz, Chris and Ezick, James
          and Petit, Jonathan and Aroyo, Lora and Gruen, Andrew and
          Bollacker, Kurt and Pietri, William and Hillenbrand, Bennett
          and others},
  year={2025},
  month={October},
  url={https://mlcommons.org/wp-content/uploads/2025/10/MLCommons___Security___Jailbreak_0_5_Paper-5.pdf}
}
```

### AILuminate v1.0 Safety Benchmark Paper (2025)

```bibtex
@article{ghosh2025ailuminate,
  title={AILuminate: Introducing v1.0 of the AI Safety Benchmark from
         MLCommons},
  author={Ghosh, Shaona and Parrish, Alicia and Bollacker, Kurt and
          Goel, James and Pietri, William and Gruen, Andrew and
          Aroyo, Lora and Knotz, Chris and Ezick, James and others},
  year={2025},
  eprint={2503.05731},
  archivePrefix={arXiv},
  url={https://arxiv.org/abs/2503.05731}
}
```

## Contributors

<a href="https://github.com/agruen"><img src="https://github.com/agruen.png" width="70px" alt="agruen" /></a>
<a href="https://github.com/ChristopherKnotz"><img src="https://github.com/ChristopherKnotz.png" width="70px" alt="ChristopherKnotz" /></a>
<a href="https://github.com/faizaai"><img src="https://github.com/faizaai.png" width="70px" alt="faizaai" /></a>
<a href="https://github.com/foundjem"><img src="https://github.com/foundjem.png" width="70px" alt="foundjem" /></a>
<a href="https://github.com/hillenbrandb"><img src="https://github.com/hillenbrandb.png" width="70px" alt="hillenbrandb" /></a>
<a href="https://github.com/isaacholeman"><img src="https://github.com/isaacholeman.png" width="70px" alt="isaacholeman" /></a>
<a href="https://github.com/jacqueline-mlc"><img src="https://github.com/jacqueline-mlc.png" width="70px" alt="jacqueline-mlc" /></a>
<a href="https://github.com/mserrhini"><img src="https://github.com/mserrhini.png" width="70px" alt="mserrhini" /></a>
<a href="https://github.com/petit-security"><img src="https://github.com/petit-security.png" width="70px" alt="petit-security" /></a>
<a href="https://github.com/saifulislamPhD"><img src="https://github.com/saifulislamPhD.png" width="70px" alt="saifulislamPhD" /></a>

Contributions welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) to get started.

## Links

- [MLCommons](https://mlcommons.org)
- [AIRR Working Group](https://mlcommons.org/working-groups/ai-risk-reliability/ai-risk-reliability/)
- [v0.7 Methodology Paper (PDF)](https://mlcommons.org/wp-content/uploads/2026/02/MLCommons___Security___Jailbreak_0_7_Paper_Collaborative.pdf)
- [v0.5 Jailbreak Benchmark Paper (PDF)](https://mlcommons.org/wp-content/uploads/2025/10/MLCommons___Security___Jailbreak_0_5_Paper-5.pdf)
- [AILuminate v1.0 Paper (arXiv)](https://arxiv.org/abs/2503.05731)
