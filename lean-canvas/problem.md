# Problem

Top 1–3 problems.

## Summary
The short answer that goes into the [canvas](lean-canvas.md).

### Customer problems
1. **Making molecules is slow and expensive (the "Make" gap)**: molecules designed by AI or chemists can't be synthesized quickly or cheaply, so the design-make-test loop is slow (finding B below). Roche and AstraZeneca both call "Make" the bottleneck of the design-make-test cycle ([Roche 2025](https://doi.org/10.1039/d5md00672d); [AstraZeneca 2012](https://www.sciencedirect.com/science/article/abs/pii/S1359644611003023)). No peer-reviewed cycle-time number found. Rough estimate: ~$1k (China) to $5k+ (US) of labor per compound, based on [WuXi's](https://www.wuxiapptec.com/news/wuxi-news/wuxi-apptec-beat-full-year-guidance-and-achieved-record-performance-in-2025) 420k compounds/year and full-time-equivalent rates (secondary). *Partly verified.*
2. **Finding reaction conditions is trial and error**: AstraZeneca lab notebooks show 39.9% of 781 Buchwald–Hartwig reactions gave no product (some due to human error) ([Chem Sci 2023](https://europepmc.org/article/pmc/10189898)). Across 10k+ Suzuki reactions, conditions follow habit rather than the substrate ([Beker et al., JACS 2022](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8949728/)). *Partly verified; strongest data.*
3. **Waste** (secondary): process mass intensity (PMI: kg of material used per kg of drug) is 168–308 for small-molecule drugs ([ACS GCI, JOC 2024](https://pubs.acs.org/doi/pdf/10.1021/acs.joc.3c01494)); pharma E-factor is ~25–100+ kg of waste per kg of product ([Sheldon 2017](https://doi.org/10.1039/c6gc02157c)). This is a cost and ESG driver more than a pain point customers pay to fix directly. *Confirmed.*

Not added after verification: scale-up (overstated, since route redesign is routine), purification (claimed but unquantified), literature reproducibility (survey-based only), chemist shortage (no evidence), outsourcing risk (real, but not binding yet), hard to automate (real, but orthogonal: not a problem we solve, and it doesn't hurt us more than the alternatives).

## Existing Alternatives
Initial list, to be verified:
- Expert chemists' intuition plus trial and error at the bench.
- Retrosynthesis and reaction-prediction tools trained on known reactions from the literature and patents (template-based or neural).
- High-throughput experimentation: run many reactions in parallel.
- Quantum chemistry simulations (e.g., DFT) by computational chemists: accurate in some cases, but slow and needing an expert for each case.

### Why current AI tools fall short
1. **Models don't generalize to new chemistry**: most models are trained only on known reactions, so they only work on similar chemistry (finding D below).
2. **Lack of negative examples**: failed reactions are rarely published, so models overestimate success and can't learn where the boundary is between reactions that work and ones that fail (finding C below). Evidence: [Raccuglia et al., Nature 2016](https://doi.org/10.1038/nature17439); Strieth-Kalthoff et al., *Angew. Chem.* 2022, "Machine Learning for Chemical Reactivity: The Importance of Failed Experiments".
3. **Literature data is a weak training base**: yield models reach R² ≈ 0.27 on real-world lab notebook records vs ≈ 0.9 on high-throughput data ([Chem Sci 2023](https://europepmc.org/article/pmc/10189898)), and ML barely beats "use the most popular conditions" ([Beker et al., JACS 2022](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8949728/)). Systematic experiments work much better.

## Research

### How to find problems
What people pay for tells us more than what they do, and what they do tells us more than what they say.

1. **Talk to practitioners.** The best source: medicinal chemists, lab heads, and R&D directors. Ask about recent, concrete pain ("What took longest last month?"). *The Mom Test* by Rob Fitzpatrick is the standard guide to running these conversations.
2. **Follow the money.**
   - Job postings show what companies hire people to fix.
   - Grant calls and prize challenges describe problems in detail: ARPA-H, BARDA, CARB-X, the EU's Horizon program, XPRIZE.
   - Industry R&D budgets show where the spending goes.
3. **Industry conferences, not academic ones.** BIO International, Drug Discovery Chemistry, Bio-IT World, ACS, and CPHI are where buyers talk about problems. NeurIPS and ICML show techniques, not pain.
4. **Complaints online.** X/Twitter, Reddit (r/labrats, r/chempros), LinkedIn, and Derek Lowe's blog *In the Pipeline*.
5. **Investor theses.** YC's *Requests for Startups*, a16z Bio + Health, Lux, and Flagship write about the gaps they see.
6. **Failure data.** Why clinical trials fail, why startups died, and what new regulations force companies to change (e.g., PFAS bans).

### Findings: online research (Nov 2026)
Five research agents covered sources 2–6 above. Many items come from search snippets or secondary sources, so verify them before quoting externally.

Sources: 💰 Money · 🎤 Conferences · 💬 Complaints · 📈 Investors · ❌ Failures

| # | Problem | Seen in | Key evidence |
|---|---|---|---|
| A | **Clinical attrition: efficacy and toxicity still kill ~90% of candidates; AI hasn't changed this yet** | 💰🎤💬📈❌ | Failures: efficacy 40–50%, toxicity ~30%, drug-like properties 10–15% ([Sun et al.](https://pmc.ncbi.nlm.nih.gov/articles/PMC9293739/)). Cost per drug $2.67B in 2025 ([Deloitte](https://www.deloitte.com/uk/en/Industries/life-sciences-health-care/research/measuring-return-from-pharmaceutical-innovation.html)). BenevolentAI and Recursion clinical failures. Clinical impact of AI "disappointingly limited" (Bender et al., NRDD 2026, via [Booth](https://lifescivc.com/2026/10/the-fruits-of-ai-drug-abundance-indigestion-in-the-near-term/)). |
| B | **The "Make" gap: designed molecules can't be synthesized quickly or cheaply; the design-make-test loop is slow** | 💰🎤💬📈 | "Designs that cannot be synthesized are worthless" ([DCH 2027](https://www.drugdiscoverychemistry.com/generative-ai)). Chemists criticize retrosynthesis tools for "unrealistic disconnections" ([ACS Med Chem Lett](https://pmc.ncbi.nlm.nih.gov/articles/PMC12434529/)). ARPA-E $34M aims to cut ~10-year catalyst development to ~1 year with autonomous labs ([ARPA-E](https://arpa-e.energy.gov/news-and-events/news-and-insights/us-department-energy-announces-34-million-pair-artificial-intelligence-autonomous-labs-accelerate-catalyst-development-0)). YC wants full "discovery engines" ([YC RFS](https://www.ycombinator.com/rfs)). |
| C | **Data: too little high-quality experimental data; literature is noisy, negative results are missing, and pharma data is siloed and not AI-ready** | 🎤💬📈 | Lowe: reaction literature is "often inconsistent or flat-out wrong" ([Bio-IT World](https://www.bio-itworld.com/news/2025/04/15/derek-lowe-on-ai-in-drug-discovery-between-hype-and-hope)). "Not a model problem, but a data problem" ([Bio-IT 2026](https://www.bio-itworldexpo.com/26/ai-biologics)). a16z: "you need to run the experiment" ([Periodic Labs](https://a16z.com/announcement/investing-in-periodic-labs/)). |
| D | **Generalization: models fail on new chemistry and targets, and benchmarks are inflated by leakage** | 🎤💬📈 | AI "struggles to extrapolate beyond known data" ([DCH 2026](https://www.drugdiscoverychemistry.com/26/artificial-intelligence)). Docking/scoring benchmark leakage ([arXiv 2512.05386](https://arxiv.org/html/2512.05386)). Air Street: a model can do well on familiar pockets but struggle on new chemistry ([State of AI 2025](https://www.stateof.ai/2025)). |
| E | **Toxicity and ADMET prediction, needed to replace animal testing (NAMs)** | 🎤❌ | FDA is phasing out animal testing and qualified its first AI drug development tool in Dec 2025 ([FDA](https://www.fda.gov/news-events/press-announcements/fda-achieves-year-1-goals-reducing-animal-testing-drug-development)). Zero-shot ADME is a DCH 2027 topic. ARPA-H funds in silico ADMET. |
| F | **PFAS replacement: >10,000 substances face EU restriction, and many uses have no drop-in alternative** | 💰📈❌ | RAC opinion adopted March 2026; SEAC final opinion expected end of 2026 ([LawBC](https://www.lawbc.com/rac-and-draft-seac-opinions-support-reach-pfas-restriction-with-targeted-derogations-comments-on-draft-seac-opinion-due-may-25/)). Horizon Europe calls: €30M and €38M. 16 US states have PFAS product laws. |
| G | **Materials: AI predictions are plentiful, but synthesized and validated materials lag** | 💰🎤📈 | Only 736 of GNoME's 2.2M predicted structures independently synthesized ([FSX](https://futurescalex.com/ai-led-material-discovery-investment), secondary). DOE Genesis Mission: $293M. Critical minerals and rare-earth substitution. |
| H | **Crop protection: $307M and 11.4 years per new active ingredient; the EU toolbox is shrinking** | 💰📈❌ | [CropLife/AgbioInvestor](https://www.global-agriculture.com/crop-protection/new-crop-protection-molecule-now-costs-307-million-to-reach-market/). EU farmers have 92 fewer active substances than in 2019, and one new approval in seven years ([CropLife Europe](https://croplifeeurope.eu/when-regulation-doesnt-keep-pace-with-innovation/); lobby source). |
| I | **"Undruggable" targets: disordered proteins and conformational dynamics can't be modeled** | 💰📈 | ARPA-H BIOGAMI and DARPA Protean (2026). Booth: "cracking the undruggable… remains elusive". |
| J | **Antibiotics: almost no new scaffolds against Gram-negative bacteria** | 💰 | CARB-X "Novel Chemistry for AMR Challenge"; next funding round Q4 2026 ([CARB-X](https://carb-x.org/carb-x-news/carb-x-announces-new-chemistry-focused-theme-ahead-of-2026-funding-call/)). |

**Crowded or overhyped (according to investors):**
- AI molecular design against known targets: "most 'proprietary' AI models quickly disseminate" (Booth).
- Yet another structure or co-folding model: open models such as Boltz and Chai are available.
- Pure AI-pipeline companies: down 80–90% from peak valuations; no AI-discovered drug approved yet.
- Materials-AI funding is ahead of proof: CuspAI is valued at $2.6B with no commercial candidate yet.

**Still to check:** talking to practitioners (source 1); non-pharma voices (agro, chemicals, materials); primary sources for items marked "secondary".
