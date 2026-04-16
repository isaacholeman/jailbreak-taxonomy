# Composition & Ordering Family

## Definition

The Composition & Ordering family manipulates prompt-level structure rather than wording or representation. These attacks focus on global arrangement (narrative flow, sequencing effects, instruction placement) to exploit how models process extended prompts. By strategically organizing and structuring the components of a request, attackers can take advantage of attention mechanisms, context ordering effects, and how models synthesize information from multiple instructions distributed across a prompt. The goal is to arrange harmful intent in a way that makes the model more likely to comply with it.

**Family Prevalence: 23.89%**

## Splitting Rule

The Composition & Ordering family is subdivided based on how harmful intent is distributed across the prompt. **Context Framing & Deception** carries harmful intent through extended narrative scaffolding—building a story, scenario, or contextual frame into which the harmful request is embedded. **Fragment Assembly**, by contrast, distributes pieces of the harmful request across the prompt, relying on the model to synthesize them into a coherent harmful output. The distinction reflects a fundamental difference in structural strategy: establishing a narrative context where harm is justified versus strategically fragmenting the request itself.

## Categories and Leaves

| Category | Leaf | Prevalence | Description |
|----------|------|-----------|-------------|
| Context Framing & Deception | Benign Wrapper + Harmful Core | 8.85% | Embedding a harmful request within a larger benign narrative or procedural context that establishes justification or urgency for the harmful output. |
| Context Framing & Deception | Scenario-Based Assembly | 5.31% | Constructing detailed fictional or hypothetical scenarios designed to establish emotional investment, authority, or perceived necessity that motivates harmful outputs. |
| Fragment Assembly | Token/Phrase Shuffling | 0.88% | Distributing tokens or phrases of a harmful request across the prompt in non-sequential order, relying on the model to reconstruct the harmful intent from fragments. |
| Fragment Assembly | Jailbreak Prompt Optimization & Search | 7.96% | Using automated methods to search for and optimize prompt structures that fragment or distribute harmful requests in ways that maximize model compliance. |
| Fragment Assembly | Interleaving Benign / Harmful Sections | 0.88% | Alternating between benign and harmful request segments throughout the prompt to obscure the overall structure and exploit sequential processing. |

## Detailed Category Descriptions

### Context Framing & Deception (14.16%)

Context framing and deception establish a narrative scaffolding that contextualizes and justifies harmful requests. The attacker builds a story, scenario, or procedural context that makes harmful outputs appear justified, necessary, or even benign within that frame, avoiding direct requests for harmful content.

**Benign Wrapper + Harmful Core (8.85%):** This is the second-most prevalent technique in the entire taxonomy. The attack embeds a harmful request within a larger benign or seemingly legitimate narrative. For example, an attacker might preface a malicious code request with "I'm teaching a security course" or request harmful information with "for a historical analysis." The benign wrapper provides context and perceived justification for the harmful core. Safety mechanisms that focus on isolated segments may miss the harmful intent if they do not adequately consider how the request is embedded within its narrative context.

**Scenario-Based Assembly (5.31%):** These attacks construct detailed fictional or hypothetical scenarios designed to establish emotional investment, authority relationships, or a sense of perceived necessity. For example, an attacker might create an elaborate scenario describing an emergency situation, a person in distress, or a hypothetical authority figure requesting assistance with harmful activities. By building narrative and emotional context, these attacks aim to trigger the model's helpfulness instincts and override safety mechanisms that would activate in response to direct harmful requests.

### Fragment Assembly (9.73%)

Fragment assembly distributes the pieces of a harmful request across the prompt, never presenting them as a coherent whole. The model is then prompted to synthesize these fragments into a coherent harmful output. This approach exploits how models process extended prompts and the possibility that safety mechanisms applied to individual fragments may not recognize the harmful synthesis.

**Token/Phrase Shuffling (0.88%):** These attacks distribute tokens or phrases of a harmful request across the prompt in non-sequential or scrambled order, relying on the model to reconstruct the harmful intent from fragments. For example, harmful instructions might be interspersed throughout the prompt in reverse order, or split across multiple paragraphs. The attacker then requests that the model "put the pieces together" or "respond based on all instructions." This low-prevalence technique exploits the possibility that token-level safety mechanisms may not recognize fragments as harmful.

**Jailbreak Prompt Optimization & Search (7.96%):** This technique uses automated methods (genetic algorithms, reinforcement learning, gradient-based search) to discover prompt structures that fragment or distribute harmful requests in ways that maximize model compliance. Attackers use machine learning to search across the space of possible prompt arrangements, identifying structures that are particularly effective at eliciting harmful outputs. The automation distinguishes this from hand-crafted composition techniques. This technique represents a more sophisticated, transferable approach to composition-based jailbreaks.

**Interleaving Benign / Harmful Sections (0.88%):** These attacks alternate between benign and harmful request segments throughout the prompt, interspersing them in a way that obscures the overall structure and exploits sequential processing. For example, an attacker might alternate between requests for helpful information and requests for harmful information, or structure the prompt so that harmful sections follow benign ones in patterns that may confuse safety classifiers. The interleaving aims to distribute attention and prevent the model from recognizing the cumulative harmful intent.


<!-- BEGIN GENERATED: attack-catalog -->
<!-- This section is generated by scripts/generate_tables.py. Do not edit by hand. Update taxonomy/attacks.yaml instead. -->

## Attack Catalog

*29 documented attacks across Composition & Ordering. Grouped by category; see category docs for inclusion cues, canonical examples, and models tested.*

### Context Framing & Deception ([details](context-framing-and-deception.md)) — 17 attacks

| Attack | Leaf | Paper | Repository | Venue | Year |
|--------|------|-------|------------|-------|------|
| A False Sense of Safety: Unsafe Information Leakage in Aligned Language Models | Benign Wrapper + Harmful Core | [Link](https://arxiv.org/html/2407.02551v1) | — | ICLR 2025 | 2025 |
| Adaptive Log-Prob | Benign Wrapper + Harmful Core | [Link](https://arxiv.org/abs/2404.02151) | [Repo](https://github.com/tml-epfl/llm-adaptive-attacks) | ICLR 2025 | 2025 |
| CodeChameleon | Benign Wrapper + Harmful Core | [Link](https://arxiv.org/abs/2402.16717) | [Repo](https://github.com/huizhang-L/CodeChameleon) | Arxiv | 2024 |
| DRA: Jailbreaking Large Language Models in A Disguise of Review Assistant | Benign Wrapper + Harmful Core | [Link](https://arxiv.org/abs/2402.18104) | [Repo](https://github.com/LLM-DRA/DRA) | USENIX Security ’24 | 2024 |
| Echo Chamber: Context Poisoning Jailbreak | Benign Wrapper + Harmful Core | [Link](https://neuraltrust.ai/blog/echo-chamber-context-poisoning-jailbreak) | [Repo](https://github.com/NeuralTrust/echo-chamber) | NeuralTrust Blog | 2025 |
| Harnessing Task Overload for Scalable Jailbreak Attacks | Benign Wrapper + Harmful Core | [Link](https://arxiv.org/abs/2410.04190) | — | ICLR 2025 (Under review) | 2025 |
| Hide Your Malicious Goal into Benign Narratives: Jailbreaking LLMs via Neural Carrier Articles | Benign Wrapper + Harmful Core | [Link](https://arxiv.org/abs/2408.11182) | — | Arxiv | 2024 |
| LIAR: Long-Instruction Adversarial Red-teaming | Benign Wrapper + Harmful Core | [Link](https://arxiv.org/abs/2412.05232) | — | Arxiv | 2024 |
| LLM-Fuzzer: Scaling Assessment of Large Language Model Jailbreaks | Benign Wrapper + Harmful Core | [Link](https://www.usenix.org/system/files/usenixsecurity24-yu-jiahao.pdf) | [Repo](https://github.com/sherdencooper/GPTFuzz) | USENIX Security ’24 | 2024 |
| LLMs Can Be Dangerous Reasoners: Analyzing-based Jailbreak Attack on LLMs | Benign Wrapper + Harmful Core | [Link](https://arxiv.org/abs/2407.16205) | [Repo](https://github.com/theshi-1128/llm-defense) | arXiv | 2024 |
| Attention Shifting | Scenario-Based Assembly | [Link](https://ojs.aaai.org/index.php/AAAI/article/view/34553/36708) | — | AAAI 2025 | 2025 |
| DeepInception: Hypnotize Large Language Model to Be Jailbreaker | Scenario-Based Assembly | [Link](https://arxiv.org/abs/2311.03191) | [Repo](https://github.com/tmlr-group/DeepInception) | Arxiv | 2023 |
| PathSeeker: Reinforcement Learning Guided Path Exploration for Jailbreaking Large Language Models | Scenario-Based Assembly | [Link](https://arxiv.org/abs/2409.14177) | — | ArXiv | 2024 |
| Playing the Fool: Jailbreaking LLMs and Multimodal LLMs with Out-of-Distribution Strategy (JOOD) | Scenario-Based Assembly | [Link](https://arxiv.org/abs/2503.20823) | [Repo](https://github.com/naver-ai/JOOD) | CVPR 2025 | 2025 |
| ReNeLLM | Scenario-Based Assembly | [Link](https://arxiv.org/abs/2311.08268) | [Repo](https://github.com/NJUNLP/ReNeLLM) | NAACL 2024 | 2024 |
| SoP: Jailbreaking LLMs via Social Facilitation | Scenario-Based Assembly | [Link](https://arxiv.org/abs/2407.01902) | [Repo](https://github.com/sufenlp/SeqAR) | NAACL 2025 | 2025 |
| TASTLE: Distract Large Language Models via Automatic Jailbreak Attack Generation | Scenario-Based Assembly | [Link](https://arxiv.org/abs/2403.08424) | [Repo](https://github.com/sufenlp/AttanttionShiftJailbreak) | EMNLP 2024 | 2024 |

### Fragment Assembly ([details](fragment-assembly.md)) — 12 attacks

| Attack | Leaf | Paper | Repository | Venue | Year |
|--------|------|-------|------------|-------|------|
| ICA (In-context Attack) | Interleaving Benign / Harmful Sections | [Link](https://arxiv.org/pdf/2310.06387) | [Repo](https://github.com/llm-attacks/llm-attacks/) | EMNLP | 2023 |
| Plentiful Jailbreaks with String Compositions | Interleaving Benign / Harmful Sections | [Link](https://arxiv.org/abs/2411.01084) | — | NeurIPS 2024 | 2024 |
| Breaking the Ceiling | Jailbreak Prompt Optimization & Search | [Link](https://arxiv.org/abs/2505.21277) | [Repo](https://github.com/Aries-iai/CL-GSO) | ACL 2025 | 2025 |
| Diversity Helps Jailbreak LLMs | Jailbreak Prompt Optimization & Search | [Link](https://arxiv.org/abs/2411.04223) | — | NAACL 2025 | 2025 |
| EasyJailbreak — Modular Attack Framework | Jailbreak Prompt Optimization & Search | [Link](https://arxiv.org/abs/2403.12171) | [Repo](https://github.com/EasyJailbreak/EasyJailbreak) | arXiv | 2024 |
| EnJa: Ensemble Jailbreak on Large Language Models | Jailbreak Prompt Optimization & Search | [Link](https://arxiv.org/abs/2408.03603) | — | arXiv | 2024 |
| GCG+PAIR Hybrid | Jailbreak Prompt Optimization & Search | [Link](https://arxiv.org/abs/2506.21972) | — | ArXiv | 2025 |
| PAIR: Prompt Automatic Iterative Refinement | Jailbreak Prompt Optimization & Search | [Link](https://arxiv.org/abs/2310.08419) | [Repo](https://github.com/patrickrchao/Jailbreaking-LLMs) | 2025 IEEE Conference on Secure and Trustworthy Machine Learning (SaTML) | 2025 |
| Quack: Evolutionary Jailbreaking | Jailbreak Prompt Optimization & Search | [Link](https://openreview.net/forum?id=1zt8GWZ9sc) | — | ICLR 2024 via OpenReview | 2024 |
| TAP: Tree of Attacks with Pruning | Jailbreak Prompt Optimization & Search | [Link](https://arxiv.org/html/2312.02119v3) | [Repo](https://github.com/RICommunity/TAP) | NeurIPS 2024 | 2024 |
| When LLM Meets DRL: Targeted Adversarial Jailbreak Attack via Deep Reinforcement Learning (RLbreaker) | Jailbreak Prompt Optimization & Search | [Link](https://arxiv.org/abs/2406.08705) | [Repo](https://github.com/XuanChen-xc/RLbreaker) | NeurIPS 2024 | 2024 |
| DrAttack: Prompt Decomposition and Reconstruction Makes Powerful Attack | Token/Phrase Shuffling | [Link](https://arxiv.org/abs/2402.16914) | [Repo](https://github.com/xirui-li/DrAttack) | EMNLP 2024 | 2024 |

<!-- END GENERATED: attack-catalog -->

## See Also

- [Context Framing & Deception](context-framing-and-deception.md) — covers Benign Wrapper + Harmful Core and Scenario-Based Assembly
- [Fragment Assembly](fragment-assembly.md) — covers Token/Phrase Shuffling, Jailbreak Prompt Optimization & Search, and Interleaving Benign/Harmful Sections

For an overview of all families, see [Taxonomy Overview](../../taxonomy-overview.md).
