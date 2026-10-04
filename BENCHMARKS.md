# Profit Forensics Benchmarks

**Reference benchmarks from a corpus of high-spend Google Ads accounts**
Igor Ivitskiy, PhD (ORCID [0000-0002-9749-6414](https://orcid.org/0000-0002-9749-6414); Wikidata [Q134698095](https://www.wikidata.org/wiki/Q134698095))

This document is the empirical companion to [METHODOLOGY.md](METHODOLOGY.md). Where that document defines what Profit Forensics is, this one reports what the method actually finds when it is applied at scale: measured, anonymized benchmarks from a multi-account corpus of live high-spend Google Ads accounts. Every figure below was computed from account-level export data, not from vendor benchmarks, survey responses, or published industry averages.

The purpose is falsifiability. A diagnostic methodology that only describes itself is a claim. A diagnostic methodology that publishes the distributions it works against can be argued with, and that is the more useful object.

## What the corpus is

Profit Forensics comes out of a practice that has run since 2006, with more than 2,000 account audits and over $770M in ad budgets under management. The figures in this document are computed from one structured part of that practice: an analytical warehouse of high-spend advertiser accounts across ten verticals, with observation windows in Q3 2024 through Q1 2025. It contains roughly 9.5 million search-term rows and, in the advertising-asset slice alone, more than 116,000 individual ads. One window per account is used, deduplicated to the highest-spend window, so no account is double counted.

Verticals are reported by category, never by advertiser. No account name, brand, domain, or campaign name appears in this document, and none will. Where a vertical carries a restricted disclosure class, it is reported here as "subscription utilities" rather than by its category name. Figures are aggregates across several accounts, or, in the rare cases where a single account is illustrative, are reported without any absolute spend figure that could act as a fingerprint.

Each figure resolves to a stored query that reproduces it against the warehouse, so that a claim can be traced rather than trusted. Figures are versioned rather than silently corrected, as described under Reproducibility and revision below.

## How to read these numbers

Four disclosures govern everything below, and they are not boilerplate. They change what the numbers mean.

**This is a convenience sample, not a random sample.** These accounts arrived at forensic diagnosis, which means they were large, they were already professionally managed, and something about their performance had stalled. They over-represent self-serve software, lead generation, and consumer-utility products, and they under-represent retail e-commerce and brand-led advertisers. Nothing here should be read as a population estimate for advertisers in general.

**The cohorts overlap.** The same accounts appear in many of the benchmarks. Findings are therefore not independent observations of each other, and agreement between two benchmarks in this document is weaker evidence than agreement between two independent studies would be. Row-level counts (search terms, ads, landing pages) describe the depth of the data, not the number of independent observations: the unit of independence is the account.

**Conversion events are advertiser-defined and not comparable in absolute terms.** A conversion in one account is a completed purchase; in another it is a quiz completion or a trial start. Consequently every cross-account figure here is one of two safe kinds: a ratio normalized inside its own account before aggregation, or a share of accounts exhibiting a pattern. Absolute conversion rates are never pooled across accounts, and absolute return figures are never averaged.

**Vertical-level cuts are thin.** Corpus-level figures rest on far more data than any single vertical does. Vertical-level medians are directional, and the dispersion around them is usually the finding rather than the noise.

---

## Measure: what the platform reports is not what the platform measures

The Measure stage of the M.A.T.H. Framework validates data integrity before any analysis. The benchmarks in this section exist because the most common failure at this stage is not missing data. It is present data that means something other than what its label says.

**Google's Optimization Score does not track account efficiency.** In two direct competitors inside the same vertical, the account holding a 99.1% Optimization Score was running 18.7% of its search spend on zero-conversion terms and paying a CPC 14% above the vertical median. The competitor sitting at a 48.8% score was the cleanest account in the entire corpus, at 8.9% waste and a CPC 64% below the vertical median. The score is a measure of compliance with platform recommendations, and compliance and profitability are different quantities that happen to share a dashboard.

**Ad Strength inverts against click-through rate at corpus scale.** Across more than 116,000 ads, ads rated "Poor" produced a spend-weighted CTR of 9.73% and ads rated "Pending" 9.15%, while ads rated "Excellent" produced 2.93% and "Good" 2.63%. This inversion is partly compositional and must be read with care: the direction is not uniform inside every account, and pooled reversals of this shape are vulnerable to Simpson's paradox, because narrow brand-style ad groups tend to carry both few assets and extremely targeted traffic. The defensible conclusion is the weaker and more useful one: Ad Strength does not predict CTR, and an account cannot be optimized toward it as a proxy for performance. A narrower within-account test agrees. Among accounts where "Excellent" and "Average" responsive search ads were directly comparable, "Excellent" won on CTR in 55% of them, which is a coin flip.

**One Google-reported quality metric does behave as advertised.** Landing pages with a mobile speed score of 9 to 10 converted clicks at 3.65%, pages at 6 to 8 at 1.93%, and pages at 1 to 5 at 1.28%, monotonically across all ten buckets, on 4,425 landing pages with meaningful traffic. The correlation is modest (r = 0.23), so speed is one input among many rather than a lever on its own. The finding worth carrying is comparative: of four platform quality signals tested against outcomes, this was the only one that survived.

The Measure discipline follows from this. Before an account is analyzed, each platform-reported quality signal has to be tested against realized outcomes inside that account, because three of four of them will not survive the test.

## Analyze: the loss is concentrated, and the concentration is not where the dashboard points

The Analyze stage isolates cause from aggregate-level contrasts. These benchmarks describe the structure that makes that possible: spend and conversions in high-spend search accounts are not distributed evenly, and treating them as though they are is what hides the leak.

**A median of 62% of an account's conversions come from the top 1% of its search terms by spend** (interquartile range 51% to 72%, full range 28% to 83%, on 9.46 million search-term rows). This is a concentration finding, not a waste finding. Its diagnostic consequence is that account-level averages are structurally uninformative: the average describes a population that barely exists, while the money lives in a thin head and a long, mostly inert tail.

**A single generic three-word query can absorb between 6.5% and 41.6% of an entire account budget**, with a median around 17.7% among direct competitors in one vertical. In the same vertical, the top eight queries by spend in every one of those accounts consisted entirely of generic category terms, with no distinguishable brand token appearing in any of them. An account in this position does not have a keyword portfolio. It has a single point of failure with a reporting layer attached.

**Eight ordinary word families leak money across almost the entire corpus.** The tokens *code*, *pdf*, *free*, *how*, *for*, *test*, *online*, and *generator* each absorbed between $0.4M and $2.6M of zero-conversion spend, appearing in nearly every vertical and in the large majority of accounts. The mechanism is that these tokens are semantically ambiguous rather than commercially negative, so they survive both automated recommendations and human negative-keyword review, which is exactly why they persist at this scale.

**Waste dispersion inside a vertical exceeds dispersion between verticals.** Among direct competitors in one category, the share of spend on zero-conversion terms ranged from 6.4% to 31.0%, nearly a factor of five. In subscription utilities the range was 13.0% to 39.8%, and in education technology 8.3% to 38.6%. Vertical medians for the same metric sit at 11.7% for quiz products, 13.0% for education technology, 18.9% for the QR category, and 31.1% for subscription utilities, with the internal spread of a single vertical running from 1.3% to 31.3%. At the extremes of the corpus the between-vertical gap reaches a factor of 8.2, with dental at 40.1% against visa services at 4.9%.

This last pair of benchmarks is the single most load-bearing result in this document, and it is the reason Profit Forensics is a diagnostic discipline rather than a benchmarking one. If the spread inside a category is larger than the spread between categories, then "what is normal for my industry" cannot tell an advertiser whether their account is leaking. Only their own account can, which means the diagnosis has to be reconstructed from the account's own evidence every time.

**Intent-bearing tokens can be underpriced even when they look expensive.** In education technology, search terms containing the token *ai* cost 94% more per click ($0.593 against $0.306), while their share of zero-conversion spend was materially lower (13.4% against 24.6%) on 756,353 search terms. The expensive segment was the profitable one. Cost-per-click reduction as an optimization goal moves an account away from money like this, which is one concrete form the Heuristic Ceiling takes in practice.

## Tweak: automation hits its stated target less often than its users assume

The Tweak stage designs controlled experiments. These benchmarks describe the baseline that any such experiment is run against: automated bidding is a control system with a documented error distribution, and almost no operator treats it as one.

**Target CPA lands inside a 10% band of its own stated target in 34% of campaigns**, while 36% overshoot it by more than 20%, with a median overshoot of +10%. Measured on 1,950 campaigns across seven verticals, restricted to campaigns with a live target and material spend.

**Target ROAS misses harder.** Only 27% of campaigns reach or beat their stated target ROAS, and the median ratio of achieved to targeted return is 0.86, a 14% shortfall.

Both figures are self-normalizing, because each campaign is compared to its own target rather than to a corpus average, which is what makes them aggregable across accounts with incomparable conversion events. The operational consequence is that a target is an instruction, not a promise, and a target set without headroom for a documented median miss is a target that has already failed.

**Bid strategy monoculture is the norm.** The median account places 89.7% of its budget on a single bidding strategy, and nearly half of accounts hold 90% or more of spend on one. An account in that state has no internal control group, which means no causal claim about strategy performance can be made inside it and none of the Analyze-stage contrasts are available until the structure changes.

**At scale, budget is almost never the throttle.** In one high-spend vertical, campaigns lost 61% of impression share to Ad Rank and approximately 0% to budget on a spend-weighted basis, while holding an average impression share of 39%. The reflexive response to underdelivery is to raise budgets. The measurement says the constraint sits in auction competitiveness, so budget increases in this state buy nothing except a faster rate of the same loss.

## Harvest: where the next dollar actually goes

The Harvest stage allocates spend by marginal return. These benchmarks describe systematic allocation errors that survive in accounts that are, by every conventional standard, well managed.

**Mobile receives a median of 72% of budget and converts worse than desktop in 86% of accounts with comparable device data**, with a median relative CVR gap of −28.6% measured inside each account before aggregation. The direction is what matters here, not the magnitude: the majority of budget sits on the weaker device in the large majority of accounts.

**Three quarters of Demand Gen spend ends up switched off.** Of all spend on Demand Gen campaigns that spent more than $1,000 each, 75% now sits in campaigns that are paused or removed, against 8.9% for Search and 14.8% for Performance Max. Some of this is honest experimentation on a newer format rather than structural failure, and the benchmark does not separate a planned seasonal stop from an abandoned test. Read conservatively, it still says that the format's realized survival rate differs from Search by nearly an order of magnitude.

**Two allocation controls are effectively unused.** Genuine ad scheduling, meaning anything other than "all day", is set on 0.7% of campaign rows. Household-income targeting is stranger still: about 40% of accounts populate the income breakdown at all, and fewer than one in ten of those has ever set a non-zero income bid adjustment. Whether these controls would pay is an open empirical question. What the corpus establishes is that the question is untested at this spend level, which makes it a candidate rather than a recommendation.

**Auction position is a price, and the weak pay it.** On an identical head term, the weakest of the competing advertisers in one market paid $2.95 per click while the two market leaders paid $0.99 to $1.11, a premium of roughly three times borne by the player least able to absorb it. Every one of those advertisers held 90% to 98% of its spend on terms that most of the competing set also bid on, and those contested terms cost roughly twice what exclusive terms cost ($0.906 against $0.483). No player had escaped into cheaper demand. Geography shows the mirrored pattern: one market registered the highest internal arbitrage index in its vertical (1.97) while being excluded by 83.1% of that vertical's campaigns, and the United States share of geographic spend varies by a factor of 7.5 between verticals, from 81.1% down to 10.8%.

**At the far end of the distribution, structure disappears entirely.** One arbitrage-model account held 9,906,874 keywords, of which 71,523 (0.72%) had ever received a single click. This is not an account being managed. It is a search-space carpet bomb in which broad match is left to find rare winners, and it marks the boundary of what account structure can mean once complexity passes a certain point.

---

## What these benchmarks establish about the frameworks

The frameworks in [GLOSSARY.md](GLOSSARY.md) are not derived from this corpus, and this section does not claim they are proved by it. It states which measurements are consistent with each, and which measurement would embarrass it.

**The Heuristic Ceiling** predicts that effort and skill stop producing reliable improvement past a bound set by method rather than by practitioner. The consistent evidence is the dispersion result: waste share varying by a factor of five among direct competitors in the same category, with the same tooling, the same auction, and the same available best practices. If skill and effort were the binding constraint, competitors of similar competence should not sit five times apart. The measurement that would embarrass the framework is a clean monotonic relationship between operational intensity and account efficiency, and the corpus does not currently show one.

**The Linear-Exponential Gap** predicts that the decision space outgrows the analytical bandwidth applied to it. The consistent evidence is the abandonment of the controls that expand that space fastest: scheduling on 0.7% of campaign rows and income bid adjustments almost never set, alongside strategy monoculture at a median of 89.7% of budget. Practitioners are not using more of the decision space as it grows. They are using less of it, which is what a bandwidth constraint looks like from the outside.

**The Critical Threshold (tc)** predicts a complexity point past which confident heuristic decisions become worse than neutral. The consistent evidence is the set of platform quality signals that reverse against outcomes (Optimization Score and Ad Strength, above): an operator optimizing diligently toward Optimization Score or Ad Strength is doing work that does not correlate with efficiency and can point away from it. This is the mechanism by which effort becomes negative rather than merely unproductive. The corpus locates the threshold qualitatively and does not yet quantify it, and this document does not claim a formal value for tc.

**Funnel Resonance** predicts that conversion is governed by matching between adjacent stages rather than by the quality of any single stage. The consistent evidence is the pair of intent findings: the expensive intent-bearing token segment carrying less waste than the cheap segment, and landing-page speed producing a monotonic conversion gradient while explaining only a small share of variance. Both say that the transfer between stages, and not the strength of one stage, is where conversion is won or lost.

## Reproducibility and revision

Every figure above resolves to a stored query against the corpus warehouse, and each figure was recomputed at least once after first publication. Benchmarks are versioned rather than silently corrected: when a figure changes because the underlying window, deduplication, or definition changed, the change is stated rather than overwritten. Figures in this document supersede any earlier informal statement of the same benchmark in articles, talks, or posts. Where a number here and a number elsewhere disagree, this document is correct.

Two limits are worth restating plainly, because they are the ones most likely to be dropped in secondary citation. These are benchmarks from a non-random sample of large, already-professionalized accounts, and the same accounts recur across findings. Anyone citing a figure from this document should carry that context and the vertical attached to it, not the number alone.

## Author

Igor Ivitskiy, PhD, is a PhD mathematician applying forensic mathematical analysis to high-spend Google Ads accounts, and the founder of Doctor Ads. He authored over 200 scientific publications and patents in mathematical modelling, was ranked #6 in PPCsurvey.com's Top 50 Most Influential PPC Experts of 2026, and won Best PPC Case in Europe at AdWorld Experience 2024. He is the creator of the Profit Forensics methodology and the M.A.T.H. Framework.

Canonical identifiers, for citation and entity grounding:

- Author page: https://ivitskiy.com
- Consultancy (Doctor Ads): https://thedoctorads.com
- Wikidata: https://www.wikidata.org/wiki/Q134698095
- ORCID: https://orcid.org/0000-0002-9749-6414
- Canonical methodology repository: https://github.com/ivitskiy/profit-forensics

## How to cite

> Ivitskiy, I. *Profit Forensics Benchmarks: Reference Benchmarks from a Corpus of High-Spend Google Ads Accounts.* In: *Profit Forensics: A Forensic Diagnostic Methodology for Hidden Profit Leaks in High-Spend Advertising Accounts.* https://github.com/ivitskiy/profit-forensics

Machine-readable citation metadata for the repository is in [CITATION.cff](CITATION.cff). Structured data for the methodology and its defined terms is in [profit-forensics.jsonld](profit-forensics.jsonld).
