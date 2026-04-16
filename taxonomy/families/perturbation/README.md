# Perturbation Family

## Definition

The Perturbation family encompasses mechanisms that modify the surface realization of a user request while preserving its underlying semantic intent. These attacks emphasize lexical and syntactic variation over overt instruction conflict, exploiting brittleness in tokenization, normalization, and safety classifiers. The goal is not to override the model's values but to make it harder for the model to recognize a request as harmful, through small, deliberate changes to how the request is expressed.

**Family Prevalence: 36.28%**

## Splitting Rule

The Perturbation family is subdivided based on whether edits are human-crafted for a specific instance (**Plain Perturbations**) or engineered via automated pipelines designed for transferable reuse across multiple targets (**Transfer Text Perturbations**). This distinction reflects a fundamental difference in attack design: plain perturbations are ad-hoc modifications optimized for one particular jailbreak attempt, while transfer text perturbations represent systematic techniques that attackers have engineered to generalize across diverse model architectures, safety mechanisms, and deployment contexts.

## Categories and Leaves

| Category | Leaf | Prevalence | Description |
|----------|------|-----------|-------------|
| Plain Perturbations | Character-Level Micro-Edits | 7.96% | Manual, instance-specific modifications at the character level (e.g., typos, character substitutions, spacing variations) designed to evade tokenization-based safety filters. |
| Plain Perturbations | Local Paraphrase & Rewording | 1.77% | Hand-crafted rephrasing of specific request segments to alter semantic representation while maintaining intent, applied without systematic transferability across instances. |
| Transfer Text Perturbations | Adversarial Triggers | 23.89% | Pre-engineered token sequences or trigger phrases designed to deactivate or confuse safety mechanisms, developed through adversarial search or automated optimization and intended for reuse across multiple targets. |
| Transfer Text Perturbations | Paraphrase-Based Transfer | 2.65% | Systematic paraphrase generation via templates, substitution rules, or automated NLP pipelines designed to create transferable variants of harmful requests across different models and safety mechanisms. |

## Detailed Category Descriptions

### Plain Perturbations (9.73%)

Plain perturbations are manual, instance-specific modifications applied to create single-shot jailbreak variants. Attackers craft small changes to a particular request to evade detection, without engineering a reusable technique. These modifications typically target the surface representation of harmful intent without altering the underlying semantic structure.

**Character-Level Micro-Edits (7.96%):** These attacks introduce small character-level variations (typos, whitespace changes, character substitutions, deliberate misspellings) to bypass tokenization and character-level detection. For example, an attacker might break a flagged word into pieces separated by unusual whitespace, use Unicode lookalikes, or introduce deliberate typos that a safety classifier may not recognize. These edits are crafted manually for a specific instance and are not designed to transfer to other attacks.

**Local Paraphrase & Rewording (1.77%):** These attacks employ hand-crafted rephrasing of request segments to alter how the harmful intent is linguistically expressed. An attacker might rephrase a request using synonyms, change grammatical structure, or reorganize the request without changing its core meaning. Unlike transfer text perturbations, these modifications are applied ad-hoc and are not part of a systematic, reusable pipeline.

### Transfer Text Perturbations (26.55%)

Transfer text perturbations are engineered, reusable techniques designed to generalize across multiple jailbreak attempts and model architectures. Attackers develop systematic methods that can be applied across a range of harmful requests and target models, not just a single instance.

**Adversarial Triggers (23.89%):** This is the most prevalent leaf in the entire taxonomy. Adversarial triggers are token sequences or phrases engineered to activate harmful behaviors in language models. These triggers are typically discovered through automated adversarial search methods, genetic algorithms, or gradient-based optimization and are designed to deactivate safety mechanisms or steer model behavior toward compliance with harmful requests. Common examples include nonsensical token sequences, special formatting, or learned token combinations that confuse safety classifiers. Because they are engineered for transferability, the same trigger often works across different models and safety mechanisms.

**Paraphrase-Based Transfer (2.65%):** These attacks use systematic paraphrase generation pipelines (template-based substitution, rule-based rewording, automated NLP transformations) to create transferable variants of harmful requests. Attackers use automated methods to generate multiple semantically equivalent versions of a harmful request, each bypassing safety mechanisms through structural variation. The automation is the key distinction from hand-crafted local paraphrases.


<!-- BEGIN GENERATED: attack-catalog -->
<!-- This section is generated by scripts/generate_tables.py. Do not edit by hand. Update taxonomy/attacks.yaml instead. -->

## Attack Catalog

*40 documented attacks across Perturbation. Grouped by category; see category docs for inclusion cues, canonical examples, and models tested.*

### Plain Perturbations ([details](plain-perturbations.md)) — 11 attacks

| Attack | Leaf | Paper | Repository | Venue | Year |
|--------|------|-------|------------|-------|------|
| AdvPrompter: Sparse and Imperceptible Adversarial Prompts | Character-Level Micro-Edits | [Link](https://arxiv.org/abs/2404.16873) | [Repo](https://github.com/facebookresearch/advprompter) | ICML 2025 | 2025 |
| Attacking Large Language Models with Projected Gradient Descent | Character-Level Micro-Edits | [Link](https://arxiv.org/abs/2402.09154) | [Repo](https://github.com/sigeisler/reinforce-attacks-llms) | ICML 2024 – poster | 2024 |
| DeepWordBug (2018) | Character-Level Micro-Edits | [Link](https://arxiv.org/abs/1801.04354) | [Repo](https://github.com/QData/deepWordBug) | 2018 IEEE Security and Privacy Workshops (SPW 2018) | 2018 |
| FlipAttack | Character-Level Micro-Edits | [Link](https://arxiv.org/abs/2410.02832) | [Repo](https://github.com/yueliu1999/FlipAttack) | arxiv | 2024 |
| HotFlip | Character-Level Micro-Edits | [Link](https://arxiv.org/abs/1712.06751) | [Repo](https://github.com/anyirao/WordAdver) | ACL 2018 | 2018 |
| PAP: How Johnny Can Persuade LLMs via Character-Level Paraphrasing | Character-Level Micro-Edits | [Link](https://arxiv.org/abs/2401.06373) | — | ACL 2024 | 2024 |
| Revisiting Character-level Adversarial Attacks for Language Models | Character-Level Micro-Edits | [Link](https://arxiv.org/abs/2405.04346) | [Repo](https://github.com/LIONS-EPFL/Charmer) | ICML 2024 | 2024 |
| Single Character Perturbations Break LLM Alignment | Character-Level Micro-Edits | [Link](https://arxiv.org/abs/2407.03232) | — | AAAI-25 | 2025 |
| TextBugger (2019) | Character-Level Micro-Edits | [Link](https://arxiv.org/abs/1812.05271) | [Repo](https://github.com/QData/TextAttack) | NDSS 2019 | 2019 |
| Adversarial Examples for Evaluating Reading Comprehension Systems | Local Paraphrase & Rewording | [Link](https://arxiv.org/abs/1707.07328) | [Repo](https://github.com/robinjia/adversarial-squad) | EMNLP 2017 | 2017 |
| Generating Natural Language Adversarial Examples | Local Paraphrase & Rewording | [Link](https://arxiv.org/abs/1804.07998) | [Repo](https://github.com/nesl/nlp_adversarial_examples) | EMNLP 2018 | 2018 |

### Transfer Text Perturbations ([details](transfer-text-perturbations.md)) — 29 attacks

| Attack | Leaf | Paper | Repository | Venue | Year |
|--------|------|-------|------------|-------|------|
| Advancing Adversarial Suffix Transfer Learning for Jailbreaking Large Language Models (DeGCG) | Adversarial Triggers | [Link](https://arxiv.org/abs/2408.14866) | [Repo](https://github.com/Waffle-Liu/DeGCG) | EMNLP 2024 | 2024 |
| AmpleGCG (2024) | Adversarial Triggers | [Link](https://openreview.net/pdf?id=UfqzXg95I5) | [Repo](https://github.com/OSU-NLP-Group/AmpleGCG) | COLM 2024 | 2024 |
| AmpleGCG-Plus: Faster and Stronger Adversarial Attacks Against Large Language Models | Adversarial Triggers | [Link](https://arxiv.org/abs/2410.22143) | [Repo](https://huggingface.co/osunlp/AmpleGCG-plus-llama2-sourced-llama2-7b-chat) | arXiv | 2024 |
| AttnGCG | Adversarial Triggers | [Link](https://arxiv.org/abs/2410.09040) | [Repo](https://github.com/UCSC-VLAA/AttnGCG-attack) | Transactions on Machine Learning Research | 2025 |
| Boosting Jailbreak Transferability for LLMs (SI-GCG / I-GCG family) | Adversarial Triggers | [Link](https://arxiv.org/abs/2410.15645) | [Repo](https://github.com/HqingLiu/SI-GCG) | Arxiv | 2024 |
| Broken Hill — Productionized GCG Runner | Adversarial Triggers | [Link](https://arxiv.org/pdf/2307.15043) | [Repo](https://github.com/llm-attacks/llm-attacks) | ICLR 2024 | 2024 |
| COLD-Attack: Jailbreaking Large Language Models via Conditioned Latent Direction | Adversarial Triggers | [Link](https://arxiv.org/html/2402.08679v2) | [Repo](https://github.com/Yu-Fangxu/COLD-Attack) | ICML 2024 | 2024 |
| Efficient LLM jailbreak via adaptive dense-to-sparse constrained optimization | Adversarial Triggers | [Link](https://dl.acm.org/doi/10.5555/3737916.3738647) | [Repo](https://github.com/hukkai/adc_llm_attack) | NeurIPS 2024 | 2024 |
| From Noise to Clarity: Jailbreaking LLMs via Adversarial Self-Template Contrastive Editing (ASTEF) | Adversarial Triggers | [Link](https://arxiv.org/abs/2503.00038) | — | ACL 2025 | 2025 |
| Functional Homotopy Attack: A Unified Approach to Jailbreaking White-box LLMs | Adversarial Triggers | [Link](https://arxiv.org/abs/2410.04234) | — | arXiv | 2024 |
| GASP: Efficient Black-Box Generation of Adversarial Suffixes for Jailbreaking LLMs | Adversarial Triggers | [Link](https://arxiv.org/abs/2411.14133) | — | NeurIPS 2025 | 2025 |
| GCG | Adversarial Triggers | [Link](https://arxiv.org/abs/2307.15043) | [Repo](https://github.com/llm-attacks/llm-attacks) | ICLR 2024 | 2024 |
| I-GCG | Adversarial Triggers | [Link](https://arxiv.org/abs/2410.15645) | [Repo](https://github.com/HqingLiu/SI-GCG) | Arxiv | 2024 |
| JAILMINE | Adversarial Triggers | [Link](https://arxiv.org/abs/2405.13068) | — | Arxiv | 2024 |
| Open Sesame: Universal Black Box Jailbreaking of Large Language Models | Adversarial Triggers | [Link](https://arxiv.org/abs/2309.01446) | — | Applied Sciences (MDPI) | 2024 |
| PAL: Proxy-Guided Black-Box Attack on Large Language Models | Adversarial Triggers | [Link](https://arxiv.org/abs/2402.09674) | [Repo](https://github.com/chawins/pal) | arXiv | 2024 |
| QROA: Query-Response Optimization Attack Against Large Language Models | Adversarial Triggers | [Link](https://arxiv.org/html/2406.02044v2) | [Repo](https://github.com/qroa/qroa) | CoRR | 2024 |
| Query-Based Adversarial Prompt Generation (QAPG) | Adversarial Triggers | [Link](https://arxiv.org/abs/2402.12329) | — | Neurips 2024 | 2024 |
| SM-GCG: Spatial Momentum Greedy Coordinate Gradient for Robust Jailbreak Attacks on Large Language Models | Adversarial Triggers | [Link](https://www.mdpi.com/2079-9292/14/19/3967) | — | Electronics (MDPI), Volume 14, Issue 19, Article 3967 | 2025 |
| Stealthy Jailbreaks via Benign Data | Adversarial Triggers | [Link](https://arxiv.org/abs/2410.21083) | — | NAACL-HLT 2025 | 2025 |
| Stronger Universal &amp; Transferable Attacks (NAACL 2025) | Adversarial Triggers | [Link](https://aclanthology.org/2025.naacl-long.302.pdf) | [Repo](https://github.com/SproutNan/AI-Safety_SCAV) | NAACL 2025 | 2025 |
| The Resurgence of GCG Adversarial Attacks on Large Language Models | Adversarial Triggers | [Link](https://arxiv.org/html/2509.00391v1) | — | arXiv | 2025 |
| Transferable Ensemble Black-box Jailbreak Attacks on LLMs | Adversarial Triggers | [Link](https://arxiv.org/abs/2410.23558) | [Repo](https://github.com/YQYANG2233/Large-Language-Model-Break-AI) | Arxiv | 2024 |
| Understanding and Enhancing the Transferability of Jailbreaking Attacks | Adversarial Triggers | [Link](https://arxiv.org/abs/2502.03052) | [Repo](https://github.com/tmllab/2025_ICLR_PiF) | ICLR 2025 | 2025 |
| Universal Adversarial Triggers for Attacking and Analyzing NLP | Adversarial Triggers | [Link](https://arxiv.org/abs/1908.07125) | [Repo](https://github.com/Eric-Wallace/universal-triggers) | EMNLP-IJCNLP 2019 | 2019 |
| Weak-to-Strong Jailbreaking on Large Language Models | Adversarial Triggers | [Link](https://arxiv.org/abs/2401.17256) | [Repo](https://github.com/XuandongZhao/weak-to-strong) | ICML 2025 | 2025 |
| Prompt sampling attack (Best-of-N Jailbreaking) | Paraphrase-Based Transfer | [Link](https://arxiv.org/pdf/2412.03556) | [Repo](https://github.com/jplhughes/bon-jailbreaking) | arXiv | 2024 |
| Semantic Mirror Jailbreak (SMJ) | Paraphrase-Based Transfer | [Link](https://arxiv.org/abs/2402.14872) | — | arxiv | 2024 |
| TextFooler (2019) | Paraphrase-Based Transfer | [Link](https://arxiv.org/abs/1907.11932) | [Repo](https://github.com/jind11/TextFooler) | AAAI-20 | 2020 |

<!-- END GENERATED: attack-catalog -->

## See Also

- [Plain Perturbations](plain-perturbations.md) — covers Character-Level Micro-Edits and Local Paraphrase & Rewording
- [Transfer Text Perturbations](transfer-text-perturbations.md) — covers Adversarial Triggers and Paraphrase-Based Transfer

For an overview of all families, see [Taxonomy Overview](../../taxonomy-overview.md).
