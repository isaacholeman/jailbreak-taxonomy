# Overt Carriers Family

## Definition

The Overt Carriers family pursues bypass through confrontation, not concealment. These attacks directly reshape the model's perceived operating rules, authority structure, and normative obligations. They work by reframing the context in which the model operates: establishing new personas, invoking alternative rule systems, or claiming override authority to convince the model that harmful outputs are acceptable or necessary under the specified conditions. The goal is not to make the request harder to detect, but to make the model willing to comply.

**Family Prevalence: 19.47%**

## Splitting Rule

The Overt Carriers family is subdivided based on whether compliance is pursued through **Direct Override Patterns** (explicit commands that attempt to negate or override the model's safety training) or through **Role-Play & Template Jailbreaks** (indirect narrative framing that establishes alternative operating contexts where harmful outputs are justified). The distinction reflects two fundamentally different persuasion strategies: direct confrontation with the model's values versus indirect redefinition of the situation.

## Categories and Leaves

| Category | Leaf | Prevalence | Description |
|----------|------|-----------|-------------|
| Direct Override Patterns | Simple Overrides | 6.19% | Explicit commands or assertions that attempt to directly negate, suspend, or override the model's safety guidelines, training, or values. |
| Direct Override Patterns | DAN-Style Composites | 6.19% | Composite prompt structures that combine multiple override techniques (e.g., DAN, STAN) to establish alternative AI personas with different rule systems or values. |
| Role-Play & Template Jailbreaks | Benign Pretext / Safety Reframing | 3.54% | Framing of harmful requests within seemingly benign contexts (e.g., fictional writing, education, legal analysis) to invoke alternative safety rules or suppress safety mechanisms. |
| Role-Play & Template Jailbreaks | Persona Role-Play | 3.54% | Establishment of alternative personas (e.g., "You are an evil AI," "Pretend you are a hacker") to redefine the model's operating rules and normative obligations. |

## Detailed Category Descriptions

### Direct Override Patterns (12.39%)

Direct override patterns attempt to explicitly disable or override the model's safety mechanisms through frontal commands. These attacks do not hide their intent; they directly tell the model to ignore its training, suspend its values, or prioritize user requests above safety guidelines. The attack relies on the hope that explicit framing will be more persuasive than encoded or concealed requests.

**Simple Overrides (6.19%):** These attacks use direct, explicit commands such as "Ignore your safety guidelines," "Disregard your training," "You are no longer bound by safety rules," or "I am overriding your safety constraints." The attacker does not introduce alternative personas or complex narratives; they simply assert that safety guidelines should be suspended. The directness of these attempts is their defining characteristic; they make no attempt to conceal the request or establish an alternative narrative.

**DAN-Style Composites (6.19%):** DAN (Do Anything Now) and similar composite jailbreaks establish alternative AI personas through multi-part prompts that combine role-play with explicit override instructions. These attacks typically follow a template structure: (1) define an alternative AI persona with different values, (2) claim that the persona operates under different rules, (3) assert that the persona will respond to requests without safety constraints, and (4) invoke that persona to answer the harmful question. The "composite" nature reflects the combination of persona establishment with explicit permission to bypass safety mechanisms.

### Role-Play & Template Jailbreaks (7.08%)

Role-play and template jailbreaks pursue override through indirection, establishing alternative operating contexts where harmful outputs are justified or expected. These attacks frame the request within a narrative that redefines when and why harmful outputs are appropriate, without explicitly commanding the model to ignore safety.

**Benign Pretext / Safety Reframing (3.54%):** These attacks frame harmful requests within ostensibly benign contexts: fictional writing ("write a scene where..."), educational purposes ("for a security course, explain how..."), legal analysis ("for legal research purposes, explain how..."), or other activities that invoke alternative safety rules. The goal is to exploit domain-specific or context-specific norms where harmful information might be appropriate or necessary. For example, an attacker might request malicious code as part of a "security audit" framing, invoking professional norms where such information is legitimate.

**Persona Role-Play (3.54%):** These attacks establish alternative personas with different values or operating principles. The attacker might request that the model "act as an evil AI," "pretend you are a hacker," "roleplay as a character without safety constraints," or similar. By establishing a persona that explicitly lacks the model's safety values, the attacker attempts to create a context where harmful outputs are what the persona would naturally produce. The persona serves as the agent of harmful outputs, distancing them from the model's actual values.

## See Also

- [Simple Overrides - Category Documentation](simple-overrides.md)
- [DAN-Style Composites - Category Documentation](dan-style-composites.md)
- [Benign Pretext / Safety Reframing - Category Documentation](benign-pretext-safety-reframing.md)
- [Persona Role-Play - Category Documentation](persona-role-play.md)

For an overview of all families, see [Taxonomy Overview](../taxonomy-overview.md).
