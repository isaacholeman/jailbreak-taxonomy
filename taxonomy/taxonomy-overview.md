# MLCommons Jailbreak Attack Taxonomy v0.7.0: Overview

## Introduction

The MLCommons Jailbreak Attack Taxonomy v0.7.0 classifies single-turn, inference-time jailbreak attacks on large language models (LLMs). The taxonomy is organized by **mechanism** (how the prompt manipulates or evades the model's safety mechanisms) rather than by hazard (what potential harms result). This mechanism-first approach supports systematic analysis of attack patterns and informs targeted defense strategies.

MLCommons does not create or discover novel attacks. This taxonomy organizes and classifies techniques that are already published in the academic literature, documented in practitioner reports, or submitted by external contributors through the open contribution process described in [CONTRIBUTING.md](../CONTRIBUTING.md).

## Taxonomy Hierarchy

The taxonomy organizes jailbreak attacks across four families, eight categories, and eighteen leaf nodes:

```
Single-Turn Jailbreak Attacks on LLMs
│
├── Perturbation (36.28%)
│   │
│   ├── Plain Perturbations (9.73%)
│   │   ├── Character-Level Micro-Edits (7.96%)
│   │   └── Local Paraphrase & Rewording (1.77%)
│   │
│   └── Transfer Text Perturbations (26.55%)
│       ├── Adversarial Triggers (23.89%)
│       └── Paraphrase-Based Transfer (2.65%)
│
├── Encoding Abuse (20.35%)
│   │
│   ├── Encoding & Unicode Tricks (13.27%)
│   │   ├── ASCII Encoding (2.65%)
│   │   ├── Base64 / URL / Obfuscation (8.85%)
│   │   └── Unicode / Bidi / Zero-Width (1.77%)
│   │
│   └── Wrappers & Schemas (7.08%)
│       ├── JSON / Markdown / Code-Blocks (4.42%)
│       └── Length / Prefix-Suffix Wrappers (2.65%)
│
├── Overt Carriers (19.47%)
│   │
│   ├── Direct Override Patterns (12.39%)
│   │   ├── Simple Overrides (6.19%)
│   │   └── DAN-Style Composites (6.19%)
│   │
│   └── Role-Play & Template Jailbreaks (7.08%)
│       ├── Benign Pretext / Safety Reframing (3.54%)
│       └── Persona Role-Play (3.54%)
│
└── Composition & Ordering (23.89%)
    │
    ├── Context Framing & Deception (14.16%)
    │   ├── Benign Wrapper + Harmful Core (8.85%)
    │   └── Scenario-Based Assembly (5.31%)
    │
    └── Fragment Assembly (9.73%)
        ├── Token/Phrase Shuffling (0.88%)
        ├── Jailbreak Prompt Optimization & Search (7.96%)
        └── Interleaving Benign / Harmful Sections (0.88%)
```

## Design Principles

The taxonomy adheres to five core design principles:

1. **Mechanism-First Placement**: Attacks are classified by *how* they manipulate the model, not by the harm they cause. This enables mechanistic understanding of attack effectiveness.

2. **One-Instance-to-One-Leaf Mapping**: Each jailbreak instance in the corpus maps to exactly one leaf node. This enables consistent labeling and precise prevalence tracking.

3. **Consistent Splitting Rules**: Categories and leaves are defined by mutually exclusive, technically meaningful distinctions (e.g., encoding method, structural pattern, assembly strategy).

4. **Executability and Corpus Suitability**: All categories and leaves are defined to be reliably identifiable from attack text alone, making the taxonomy practical for annotation and empirical validation.

5. **Prevalence-Aware Validation**: The taxonomy was validated against empirical prevalence data from a large corpus of real jailbreak attempts to confirm that it reflects actual attack diversity.

## Scope

This taxonomy covers:
- **Single-turn attacks**: One-shot prompts requiring no multi-turn conversation.
- **Inference-time attacks**: Manipulations applied at query time, not during model training or fine-tuning.
- **Prompt-only attacks**: Attacks delivered purely through prompt text, with no auxiliary files, API calls, or out-of-band channels.

The taxonomy explicitly excludes:
- Multi-turn conversational attacks.
- Training-time or fine-tuning attacks.
- Infrastructure-level exploits or zero-day vulnerabilities.
- Indirect prompt injection attacks (e.g., adversarial data in external documents).
- Attacks whose primary mechanism is social engineering or deception outside the prompt itself.

## Prevalence Distribution

| Family                | Category                      | Leaf                                       | Prevalence |
|-----------------------|-------------------------------|-------------------------------------------|------------|
| Perturbation          | Plain Perturbations           | Character-Level Micro-Edits               | 7.96%      |
| Perturbation          | Plain Perturbations           | Local Paraphrase & Rewording              | 1.77%      |
| Perturbation          | Transfer Text Perturbations   | Adversarial Triggers                      | 23.89%     |
| Perturbation          | Transfer Text Perturbations   | Paraphrase-Based Transfer                 | 2.65%      |
| Encoding Abuse        | Encoding & Unicode Tricks     | ASCII Encoding                            | 2.65%      |
| Encoding Abuse        | Encoding & Unicode Tricks     | Base64 / URL / Obfuscation                | 8.85%      |
| Encoding Abuse        | Encoding & Unicode Tricks     | Unicode / Bidi / Zero-Width               | 1.77%      |
| Encoding Abuse        | Wrappers & Schemas            | JSON / Markdown / Code-Blocks             | 4.42%      |
| Encoding Abuse        | Wrappers & Schemas            | Length / Prefix-Suffix Wrappers           | 2.65%      |
| Overt Carriers        | Direct Override Patterns      | Simple Overrides                          | 6.19%      |
| Overt Carriers        | Direct Override Patterns      | DAN-Style Composites                      | 6.19%      |
| Overt Carriers        | Role-Play & Template          | Benign Pretext / Safety Reframing         | 3.54%      |
| Overt Carriers        | Role-Play & Template          | Persona Role-Play                         | 3.54%      |
| Composition & Ordering| Context Framing & Deception   | Benign Wrapper + Harmful Core             | 8.85%      |
| Composition & Ordering| Context Framing & Deception   | Scenario-Based Assembly                   | 5.31%      |
| Composition & Ordering| Fragment Assembly             | Token/Phrase Shuffling                    | 0.88%      |
| Composition & Ordering| Fragment Assembly             | Jailbreak Prompt Optimization & Search    | 7.96%      |
| Composition & Ordering| Fragment Assembly             | Interleaving Benign / Harmful Sections    | 0.88%      |

## Attack Catalog

Each category documentation page includes an **Attack Catalog** section listing all documented attacks within its leaf nodes, with links to the original paper, repository, publication venue, and year. There are currently **113 documented attacks** across the 18 leaves.

For programmatic access, the full attack catalog is available as a machine-readable YAML file: [`attacks.yaml`](attacks.yaml).

## Family-Level Documentation

Detailed documentation for each family is available in the `families/` subdirectory:

- [Perturbation Family](families/perturbation/)
- [Encoding Abuse Family](families/encoding-abuse/)
- [Overt Carriers Family](families/overt-carriers/)
- [Composition & Ordering Family](families/composition-ordering/)

## Citation

This taxonomy is presented in:

> Maple, C., et al. (2026). "A Robust, Defensible, and Reproducible Methodology for Benchmarking Single-Turn Jailbreak Attacks on Large Language Models." *MLCommons Security Initiative*. February 2026.
>
> Available at: https://mlcommons.org/wp-content/uploads/2026/02/MLCommons___Security___Jailbreak_0_7_Paper_Collaborative.pdf

For technical details on taxonomy construction, validation methodology, and empirical findings, please refer to the full paper.
