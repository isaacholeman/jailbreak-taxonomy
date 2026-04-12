---
name: Attack Submission
description: Report a jailbreak attack that should be added to the taxonomy catalog (published or novel)
labels: ["attack-submission", "triage"]
---

## Attack Name

What is the attack called? Use the name from the paper or report if available, or propose a descriptive name.

## Paper or Report Link

Provide a link to the published paper, blog post, or technical report describing this attack. If this is a novel unpublished technique, write "Pre-publication" and provide a detailed mechanism description below instead.

**Link:**

## Brief Mechanism Description

In a few sentences, describe how the attack works: what does the prompt manipulation do to bypass the model's safety alignment? Focus on the mechanism, not the harm category. For pre-publication attacks, be as detailed as possible here since there is no paper to reference.

## Suggested Taxonomy Placement (optional)

If you have a sense of where this attack belongs, indicate the family, category, and/or leaf. If you're unsure, leave this blank and the maintainers will determine placement.

**Family > Category > Leaf:**

**Or, if uncertain, list similar attacks already in the taxonomy:**

## Evidence of Effectiveness (optional)

If available, summarize what models were tested and how effective the attack was. Partial information is welcome.

| Model | Success Rate | Notes |
|-------|-------------|-------|
| | | |
| | | |
| | | |

## Repository Link (optional)

If the attack has a public code repository, provide the link here.

**Repository:**

## Additional Context

Any other relevant information: related attacks, venue/year of publication, or notes that would help maintainers evaluate and place this attack.

## Checklist

- [ ] I have checked the existing [attack catalog](../../taxonomy/attacks.yaml) to verify this attack is not already listed
- [ ] I have not included copy-paste attack prompts in this issue
- [ ] The attack is documented in a published source (paper, report, blog post) OR I have provided a detailed mechanism description and testing evidence for a novel technique
- [ ] I understand this taxonomy is CC-BY-4.0 licensed and my contribution will be openly available
