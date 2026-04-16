# Changelog

All notable changes to the MLCommons Jailbreak Attack Taxonomy are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added
- `scripts/generate_tables.py` generates Attack Catalog tables in family READMEs and category documents from `taxonomy/attacks.yaml`
- Combined attack catalog at the family level, grouped by category with per-attack leaf labels
- `taxonomy/attacks-overview.md` provides a single auto-generated cross-family catalog with collapsible sections per family, listing all 113 attacks with taxonomy placement, paper, repository, venue, and year
- `.github/workflows/check-tables.yml` enforces drift-free tables on every pull request

### Changed
- `taxonomy/attacks.yaml` is now the single source of truth for attack catalog tables; per-leaf, per-family, and cross-family overview tables are regenerated from it
- Governance documentation simplified: `governance/maintainers.md` and `governance/review-process.md` now reference the v0.7 methodology paper (Maple et al., 2026) as the canonical source of maintenance methodology, and state that all submissions are reviewed by the Security Workstream of the MLCommons AI Risk and Reliability working group

### Removed
- `governance/severity-framework.md` and all cross-references (README, `mkdocs.yml`, `CONTRIBUTING.md`, issue and taxonomy-structure templates). Severity assessment is used internally by MLCommons staff for benchmark construction and is not published as a commitment of taxonomy maintenance

## [0.7.0] - 2026-02-16

### Added
- Initial public release of the mechanism-first jailbreak attack taxonomy
- Four top-level families: Perturbation, Encoding Abuse, Overt Carriers, Composition & Ordering
- Eight categories and eighteen leaf-level attack mechanisms with structured definitions
- Machine-readable taxonomy definition in YAML format (taxonomy.yaml)
- Human-readable taxonomy overview with prevalence data and evidence summaries
- Contribution guidelines and structured submission templates
- Governance framework documentation: maintainer roles and peer review process
- GitHub issue and pull request templates for community contributions
- Initial attack placements with evidence from testing across open-weight models
- Cross-referencing guide for related attacks across taxonomy branches

### Documentation
- Taxonomy overview with family descriptions and motivations
- Contribution workflow documentation for new mechanisms, categories, and placements
- Examples of structural descriptions (without exposing attack payloads)

### References
- Maple et al., "A Robust, Defensible, and Reproducible Methodology for Benchmarking Single-Turn Jailbreak Attacks on Large Language Models," February 2026
- Goel et al., "AILuminate Security: Introducing v0.5 of the Jailbreak Benchmark from MLCommons," October 2025

---

## Versioning Policy

- **MAJOR** version changes: significant structural reorganization of taxonomy families/categories, breaking changes to taxonomy schema
- **MINOR** version changes: new leaves (mechanisms), new categories, new substantive evidence for existing mechanisms
- **PATCH** version changes: clarifications to definitions, documentation corrections, metadata updates, evidence refinements

## Contribution and Review

To propose changes to the taxonomy, open a GitHub issue using the Taxonomy Contribution template or submit a pull request with the structured submission template completed. All contributions are reviewed by the working group for consistency with the taxonomy methodology.
