# Changelog

All notable changes to the MLCommons Jailbreak Attack Taxonomy are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [0.7.0] - 2026-02-16

### Added
- Initial public release of the mechanism-first jailbreak attack taxonomy
- Four top-level families: Perturbation, Encoding Abuse, Overt Carriers, Composition & Ordering
- Eight categories and eighteen leaf-level attack mechanisms with structured definitions
- Machine-readable taxonomy definition in YAML format (taxonomy.yaml)
- Human-readable taxonomy overview with prevalence data and evidence summaries
- Contribution guidelines and structured submission templates
- Governance framework documentation: maintainer roles, peer review process, severity assessment methodology
- GitHub issue and pull request templates for community contributions
- Initial attack placements with evidence from testing across open-weight models
- Cross-referencing guide for related attacks across taxonomy branches

### Documentation
- Taxonomy overview with family descriptions and motivations
- Severity framework with assessment criteria and justification methodology
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

To propose changes to the taxonomy, open a GitHub issue using the Taxonomy Contribution template or submit a pull request with the structured submission template completed. All contributions are reviewed by the maintenance team for consistency with the taxonomy methodology and severity framework.
