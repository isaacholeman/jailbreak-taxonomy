# Datasheet: MLCommons Jailbreak Attack Taxonomy

This datasheet follows the framework from [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) (Gebru et al., 2021).

## Motivation

**Purpose.** The taxonomy provides a mechanism-first classification of single-turn, inference-time jailbreak attacks on large language models. It is intended to help defenders, researchers, standards bodies, and policymakers understand the landscape of known attack mechanisms. It also serves as the public universe from which the MLCommons Jailbreak Benchmark privately selects its test suite.

**Creators.** The taxonomy was developed by the MLCommons AI Risk and Reliability (AIRR) working group, a multi-stakeholder initiative including participants from industry, academia, civil society, and government.

**Funding.** MLCommons is an independent nonprofit. See [mlcommons.org](https://mlcommons.org) for information about the organization's funding and governance.

## Composition

**What does the dataset consist of?** The taxonomy is a hierarchical classification of jailbreak mechanisms, not a dataset of attack prompts. It contains:

- 4 families, 8 categories, and 18 leaf-level mechanisms organized by how attacks manipulate models at inference time
- 113 documented attacks mapped to those leaves, each with paper link, repository link (where available), publication venue, year, and models tested
- Prevalence data from a literature corpus analysis (the v0.7 paper's PRISMA review)

**What does it not contain?** The taxonomy does not contain copy-paste-ready attack prompts, benchmark test cases, evaluator prompts, grading parameters, or information about which techniques are included in the benchmark.

**Instances.** Each attack entry includes: name, taxonomy placement (family > category > leaf), link to the published paper, repository link (if available), publication venue, year, and list of models tested. Each leaf includes: definition, splitting rule, inclusion/exclusion cues, canonical examples (structural descriptions only), and prevalence.

**Completeness.** The taxonomy covers attacks published through approximately February 2026. It is not exhaustive. Coverage depends on the PRISMA literature review conducted for the v0.7 methodology and on community contributions.

**Confidentiality.** None. All content is drawn from published academic literature, practitioner reports, or community submissions. No proprietary or confidential information is included.

## Collection Process

**How was the data collected?** The taxonomy structure was developed through the methodology described in Section 5.1 of the [v0.7 methodology paper](https://mlcommons.org/wp-content/uploads/2026/02/MLCommons___Security___Jailbreak_0_7_Paper_Collaborative.pdf). Attack entries were identified through a PRISMA systematic literature review and corpus analysis. Prevalence data is derived from the distribution of attack types in the literature corpus.

**Who was involved?** The AIRR working group, which includes researchers and practitioners from multiple organizations. See the v0.7 paper for the full author list.

**Time period.** The v0.7 taxonomy reflects the literature as of February 2026. The attack catalog will be updated on a rolling basis with monthly stability releases.

## Preprocessing

**Was any preprocessing applied?** Attacks from the literature were classified into the taxonomy according to six design requirements (R1-R6) described in the v0.7 paper. One near-duplicate entry was removed during catalog construction (two entries referencing the same paper/repository), bringing the total from 114 to 113.

## Uses

**Intended uses:**
- Structuring red-teaming exercises by mechanism family
- Understanding the threat surface of jailbreak attacks on LLMs
- Informing evaluation requirements and benchmark coverage claims
- Contributing new attacks or taxonomy refinements through the open process

**Not intended for:**
- Generating or executing attacks (the taxonomy deliberately excludes copy-paste prompts and working exploit code)
- Determining which techniques are tested in the MLCommons Jailbreak Benchmark (that selection is private)

## Distribution

**License.** [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/).

**Where is it available?** [github.com/mlcommons/jailbreak-taxonomy](https://github.com/mlcommons/jailbreak-taxonomy)

**Format.** Human-readable Markdown documentation and machine-readable YAML files (`taxonomy.yaml` for the taxonomy structure, `attacks.yaml` for the attack catalog).

## Maintenance

**Who maintains it?** The MLCommons AIRR working group, with roles and processes defined in the [governance documentation](governance/).

**Update cadence.** Individual contributions are reviewed and merged on a rolling basis. Monthly stability releases produce a tagged snapshot with a stopping-rule check, prevalence update, and changelog entry. See [review-process.md](governance/review-process.md) for details.

**How to contribute.** See [CONTRIBUTING.md](CONTRIBUTING.md).

**Contact.** Isaac Holeman (ih@mlcommons.org), Chris Knotz (chris.knotz@mlcommons.org).
