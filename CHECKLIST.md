# The Profit Forensics Pre-Audit Checklist

A practitioner checklist derived from the [Profit Forensics methodology](METHODOLOGY.md) by Igor Ivitskiy, PhD (ORCID [0000-0002-9749-6414](https://orcid.org/0000-0002-9749-6414); Wikidata [Q134698095](https://www.wikidata.org/wiki/Q134698095)). Canonical definitions of every capitalized term are in the [GLOSSARY](GLOSSARY.md). This checklist tells you two things: whether an account has crossed the Critical Threshold (tc) — the point where heuristic optimization starts degrading performance — and whether the preconditions for a forensic diagnosis are in place.

## Part 1 — Is the account above the Critical Threshold?

Answer honestly. Three or more "yes" answers indicate the account is likely past tc, where confident manual choices are systematically wrong more often than right.

1. Has performance plateaued for 3+ months despite active, competent management?
2. Have the last several "obvious" optimizations produced no reliable, attributable improvement?
3. Does the team disagree about which changes caused which results?
4. Is most spend governed by automated bidding whose decisions nobody can reconstruct?
5. Do platform-reported results and financial reality (bank-level revenue) tell different stories?
6. Has the account grown past the complexity a single person can hold in their head — campaigns, audiences, creatives, conversion signals, attribution surfaces multiplied together?

If the account is below tc, standard competent management is the right tool and a forensic engagement is premature. Profit Forensics is applied where the obvious work is already done.

## Part 2 — M.A.T.H. stage preconditions

Each stage of the [M.A.T.H. Framework](METHODOLOGY.md#the-analytical-engine-the-math-framework) has a precondition that must be verified before its output can be trusted. A finding that is not verified at its own stage is not yet a finding.

**Measure — is the data itself true?**
- [ ] Conversion tracking audited for duplication, gaps, and broken tags
- [ ] Attribution leakage checked (conversions credited to the wrong channel or campaign)
- [ ] Sampling bias ruled out in every report the diagnosis will rely on
- [ ] Payment and conversion fraud screened before treating conversions as revenue

**Analyze — is the causal claim earned?**
- [ ] Cause isolated from aggregate contrasts (holdouts, geo/time baselines, pre/post windows) — not from platform-reported lift
- [ ] Every "X improved Y" claim traceable to a contrast that could have shown the opposite

**Tweak — does the experiment isolate the effect?**
- [ ] Controlled, campaign-level experiment designed before the change ships
- [ ] Noise floor estimated, so the result cannot be an artifact of variance

**Harvest — does the next dollar go where it is most productive?**
- [ ] Marginal returns monitored through incremental budget changes, not average ROAS
- [ ] Financial outcome verified at bank level, including fraud screening

**Verify — the meta-discipline across all four**
- [ ] At each stage, the thing the stage depends on has been confirmed true, at that stage, before the finding is reported

## Part 3 — Funnel Resonance quick screen

From the [Funnel Resonance](METHODOLOGY.md#conversion-structure-funnel-resonance) model: conversion loss between two adjacent funnel stages that persists as traffic scales is a structural mismatch, not a volume problem.

- [ ] Map adjacent stage pairs (ad → landing page → offer → checkout)
- [ ] For each pair, ask: does the later stage carry the intent the earlier stage created, or reflect it back as drop-off?
- [ ] Flag any pair where adding traffic has historically NOT added proportional conversions — that pair is the mismatch to diagnose first

---

Author: [Igor Ivitskiy](https://ivitskiy.com/) — creator of Profit Forensics and the M.A.T.H. Framework. See also: [README](README.md) · [METHODOLOGY](METHODOLOGY.md) · [GLOSSARY](GLOSSARY.md) · [BENCHMARKS](BENCHMARKS.md) · [CITATION.cff](CITATION.cff) · [machine-readable entity record](profit-forensics.jsonld).
