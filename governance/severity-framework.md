# Severity and Priority Assessment

## Purpose

Severity ratings serve two functions: they prioritize review effort (Critical submissions are reviewed first) and they inform the benchmark team's selection decisions.

## Severity Framework

| Severity | Criteria | Review Timeline | Validation |
|----------|----------|----------------|------------|
| **Critical** | Novel Level 1 family (would require new top-level branch); OR demonstrated >50% success rate across 5+ diverse SUTs; OR exploits a mechanism class with no existing taxonomy coverage | Triage within 2 business days; review within 7 business days | Required |
| **High** | New leaf-level mechanism within an existing family; demonstrated >30% success rate across 3+ SUTs; OR fills a documented coverage gap in the taxonomy | Triage within 5 business days; review within 10 business days | Required |
| **Medium** | Significant variant of an existing technique that extends the leaf's coverage; demonstrated effectiveness against at least 3 SUTs; OR provides substantially better documentation of a known technique | Standard timeline (5-day triage, 15-day review) | Recommended |
| **Low** | Minor variant with incremental coverage improvement; effectiveness demonstrated against fewer than 3 SUTs; OR primarily a documentation/example improvement | Standard timeline | Optional |

## Success Rate Measurement

"Success rate" means the proportion of test prompts for which the technique caused a SUT to produce a violating response when the unmodified seed prompt did not. This maps directly to the resilience gap concept: a technique is effective to the extent it degrades safety performance.

Success rates should be measured using a consistent evaluator or, at minimum, a documented evaluation methodology. Submissions that rely solely on manual/subjective assessment of "did the model comply" are accepted at Low and Medium severity but require quantitative evaluation for High and Critical.

## Prevalence Metadata

In addition to severity, each taxonomy leaf includes prevalence metadata (following the v0.7 paper's Table 3):

- **Corpus prevalence:** What proportion of the literature corpus documents this technique?
- **In-the-wild prevalence:** Is this technique observed in real-world use? (Based on incident reports, red-team findings, vendor advisories)
- **Trend:** Is the technique's prevalence increasing, stable, or declining?

Prevalence is updated during monthly stability releases (see [Review Process](review-process.md#monthly-stability-releases)).

[TODO: Determine whether prevalence metadata should include in-the-wild incident counts or only qualitative assessments.]

---

**Status:** v0.1 DRAFT. Effective immediately for new submissions; historical severity classifications may be updated in the next major taxonomy release.
