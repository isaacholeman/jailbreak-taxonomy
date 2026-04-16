# Taxonomy Structure Proposal Template

Use this template when proposing changes to the taxonomy structure itself: new families, categories, or leaf nodes, or revisions to existing definitions and splitting rules. Include the completed template in your pull request.

For attack catalog additions (adding a documented attack to an existing leaf), use the standard PR template instead. You do not need this form.

## Proposal Type

- [ ] New Leaf (attack mechanism)
- [ ] New Category (grouping of mechanisms)
- [ ] New Family (top-level branch)
- [ ] Structural Revision (reorganizing or redefining existing nodes)

**Proposed Name:**
[Concise and descriptive name for the mechanism, category, or family.]

**Proposed Placement:**
[Family > Category > Leaf path. Example: "Perturbation > Transfer Text Perturbations > New Leaf Name"]

---

## Definition

[Mechanism description in terms of observable prompt properties. What makes this technique distinct? What transformation is applied to the input, or how is the model's context manipulated? Focus on the structural pattern, not specific content.]

**Splitting Rule:** (Required for new categories or families)
[The single primary axis that distinguishes this node's children. Example: "Whether the perturbation is human-crafted for a specific instance or engineered for transferable reuse."]

---

## Identification Criteria

**Inclusion Cues:**
[3-5 observable properties that place an attack instance into this category. These should be structural characteristics, not specific keywords.]
- 
- 
- 

**Exclusion Cues:**
[2-4 properties that would redirect a candidate attack to a sibling category or different branch.]
- 
- 

---

## Evidence and Examples

**Canonical Examples:**
[1-3 structural descriptions of attacks that exemplify this mechanism. Describe the transformation pattern and approach, not verbatim prompts.]

1. 

2. 

3. 

**Evidence of Effectiveness:** (Required for new leaves)
[Testing evidence across 3+ distinct open-weight models.]

| Model | Version | Test Prompts | Success Rate | Methodology |
|-------|---------|--------------|--------------|-------------|
| | | | | |
| | | | | |
| | | | | |

- **Aggregate success rate across models:** [%]
- **Testing methodology:** [Evaluation approach, success criteria]
- **Failure modes:** [Where this attack fails or has reduced effectiveness]

---

## References

[Academic papers, practitioner reports, or community discussions supporting this proposal.]

- 
- 
- 

---

## Checklist

- [ ] No copy-paste attack prompts included
- [ ] Mechanisms described in structural terms
- [ ] Evidence provided across 3+ distinct open-weight models (for new leaves)
- [ ] All required fields completed (definition, inclusion/exclusion cues, examples, references)
- [ ] Reviewed existing taxonomy to confirm this is not a duplicate
- [ ] This contribution is CC-BY-4.0 licensed and will be openly available
