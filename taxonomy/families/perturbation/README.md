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

## See Also

- [Adversarial Triggers - Category Documentation](adversarial-triggers.md)
- [Character-Level Micro-Edits - Category Documentation](character-level-micro-edits.md)
- [Local Paraphrase & Rewording - Category Documentation](local-paraphrase-rewording.md)
- [Paraphrase-Based Transfer - Category Documentation](paraphrase-based-transfer.md)

For an overview of all families, see [Taxonomy Overview](../taxonomy-overview.md).
