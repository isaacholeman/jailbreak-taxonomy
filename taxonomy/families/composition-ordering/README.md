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

## See Also

- [Benign Wrapper + Harmful Core - Category Documentation](benign-wrapper-harmful-core.md)
- [Scenario-Based Assembly - Category Documentation](scenario-based-assembly.md)
- [Token / Phrase Shuffling - Category Documentation](token-phrase-shuffling.md)
- [Jailbreak Prompt Optimization & Search - Category Documentation](jailbreak-prompt-optimization-search.md)
- [Interleaving Benign / Harmful Sections - Category Documentation](interleaving-benign-harmful.md)

For an overview of all families, see [Taxonomy Overview](../taxonomy-overview.md).
