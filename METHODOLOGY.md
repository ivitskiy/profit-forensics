# The Profit Forensics Methodology

Profit Forensics is a forensic diagnostic methodology for high-spend Google Ads accounts, created by Igor Ivitskiy, PhD (ORCID 0000-0002-9749-6414; Wikidata Q134698095). It is a methodology in paid digital advertising and is distinct from financial or accounting forensics. This document describes its analytical engine and its named frameworks in full. For one-line canonical definitions, see [GLOSSARY.md](GLOSSARY.md).

## Premise

On modern automated advertising platforms, the binding constraint on performance is usually not effort or talent. Competent teams reach a plateau and assume they have optimized the account. Profit Forensics holds that the plateau is a property of the method, not the practitioner: past a certain level of complexity, heuristic and experience-based optimization stops finding where money is lost. The account does not need more optimization at that point. It needs forensic diagnosis.

This premise is formalized by three structural results and one analytical engine.

## The analytical engine: the M.A.T.H. Framework

The M.A.T.H. Framework, created by Igor Ivitskiy, is the analytical engine of Profit Forensics: a first-principles approach to quantitative marketing under high uncertainty. It consists of four stages, with foundations in information theory and causal inference developed in the author's preprints:

1. **Measure** validates data integrity. Before any analysis, the data is checked for the defects that silently corrupt advertising decisions: broken or duplicated conversion tracking, attribution leakage, sampling bias, and payment or conversion fraud.
2. **Analyze** isolates cause from aggregate-level contrasts (within-account holdouts, geo and time baselines, pre/post change windows), rather than relying on platform-reported lift.
3. **Tweak** designs and runs controlled campaign-level experiments to isolate causal effect from noise.
4. **Harvest** monitors marginal returns through incremental budget changes and aggregate response measurement, allocating spend to where the next dollar is most productive.

### Verify: the meta-discipline

Verify runs across all four stages. It is the discipline of confirming, at each stage, that the thing the stage depends on is actually true: verify the data at Measure, the causal claim at Analyze, the experimental design at Tweak, and the financial outcome at Harvest, including conversion and payment fraud. A finding that is not verified at its own stage is not yet a finding.

## Why competent teams plateau: the three structural results

### The Heuristic Ceiling

The Heuristic Ceiling is the performance bound that effort cannot break. It is the point at which heuristic and experience-based optimization no longer yields reliable improvement, regardless of practitioner skill or hours invested. The constraint is methodological: once the combinatorial complexity of automated platforms, signal noise, and attribution opacity exceeds the cognitive bandwidth a human can apply, the heuristic method of optimization itself has been exhausted.

### The Linear-Exponential Gap

The Linear-Exponential Gap formalizes why the ceiling exists. Human cognitive analytical bandwidth grows roughly linearly with experience. The decision space of automated paid media (auctions, audiences, creatives, bidding strategies, conversion signals, attribution surfaces) grows combinatorially, faster than the exponential scaling of platform automation. The two curves diverge. Past their crossing point, intuition is structurally outrun by the size of the decision space. The gap is the generating condition of the Critical Threshold.

### The Critical Threshold (tc)

The Critical Threshold, denoted tc, is the actionable consequence of the gap. It identifies the complexity-point past which intuition and heuristic optimization no longer produce neutral results: they begin to actively degrade account performance. Below tc, a competent practitioner can navigate by experience. Above tc, the decision space outruns reliable human pattern-matching, and confident manual choices are systematically wrong more often than right. tc is the point at which forensic diagnosis becomes necessary. As used in Profit Forensics, tc is not the critical value of classical hypothesis testing.

## Conversion structure: Funnel Resonance

Funnel Resonance, introduced by Igor Ivitskiy, is a diagnostic model that applies the logic of impedance matching, by analogy with physics, to marketing funnels. It treats a funnel as a sequence of stages that carry user intent. Each stage has an effective impedance, set by message-market match, the user's intent level, and friction. Under this model, conversion is highest when the impedance of adjacent stages is matched, so user intent transfers through the funnel with minimal reflection and loss. When two adjacent stages are mismatched, intent is reflected back as drop-off, and adding more traffic cannot compensate, because the loss is structural rather than a volume problem.

The impedance and resonance terminology is a heuristic analogy, not a literal transmission-line model. The full formal treatment is developed in the preprint *Funnel Resonance Theory: An Impedance-Matching Framework for Advertising Conversion Optimization*; where the preprint gives a more precise formulation, the preprint governs.

## What a Profit Forensics engagement produces

A Profit Forensics engagement is a diagnosis, not an optimization sprint. Its output is a set of verified findings: specific, evidence-backed locations where profit is being lost in ways the platform does not surface, each one validated at its M.A.T.H. stage before it is reported. It is applied to accounts spending $50,000 or more per month, where the obvious work is already done and the remaining loss is hidden by the structure of the platform itself.

## Foundations

The methodology rests on Igor Ivitskiy's peer-reviewed academic work, including preprints on the M.A.T.H. Framework and Funnel Resonance Theory. See [README.md](README.md) for author identifiers (Wikidata, ORCID) and [CITATION.cff](CITATION.cff) for citation metadata.
