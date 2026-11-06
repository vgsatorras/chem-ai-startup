# Existing Alternatives

How the [problems](problem.md) are solved today.

## Summary
The short answer that goes into the [canvas](lean-canvas.md).

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

### Tools and prices (Nov 2026)
✔ = verified on a primary or procurement page · ~ = estimate or secondary source. Most vendors publish no list price; the best real prices come from government procurement records.

#### Retrosynthesis (route planning)
| Tool | Owner | Trained on | Paid? | Price |
|---|---|---|---|---|
| [SYNTHIA](https://www.sigmaaldrich.com/GB/en/product/mm/925618) | Merck KGaA | Expert-coded rules | Paid | ✔ Academic: £2,580/year list. Commercial: quote only |
| [Reaxys Predictive Retrosynthesis](https://www.usaspending.gov/award/CONT_AWD_68HERH25P0054_6800_-NONE-_-NONE-) | Elsevier | Reaxys literature and patent reactions | Paid | ✔ US EPA: $53,077 for 20 users per year (~$2.65k/user) |
| [CAS SciFinder-n](https://canadabuys.canada.ca/en/tender-opportunities/contract-history/cw2333994-001) | CAS (ACS) | CAS-curated reactions | Paid | ✔ Environment Canada: CAD 63,350/year. ~ €25–60k/year for small companies, six figures for large ones |
| Spaya | Iktos | Proprietary | Paid | Quote only |
| Manifold | PostEra | Not verified | Paid | Not found |
| [M1 / Maria](https://molecule.one) | Molecule.one | ✔ **Proprietary HTE: >300k micro-scale experiments** | Paid | Quote only |
| [ChemAIRS](https://pr.mono.ipros.com/en/patcore/product/detail/2001636723/) | Chemical.AI | Not verified | Paid | Quote only; 2-week free trial |
| [IBM RXN](https://github.com/rxn4chemistry/rxn4chemistry) | IBM Research | Patents and literature | Was free | ✔ **Hosted service ended 28 Oct 2026**; code is open source |
| ASKCOS | MIT | Reaxys / USPTO | Free, open source | $0 |
| AiZynthFinder | AstraZeneca | USPTO + templates | Free, open source | $0 |

#### Reaction conditions and optimization
| Tool | Owner | How it works | Price |
|---|---|---|---|
| Atinary SDLabs | Atinary | Bayesian optimization on your own experiments | ~ $25k for a 2-month pilot |
| EDBO / EDBO+ | Doyle and Burke groups | Bayesian optimization, open source | $0 |
| Reaxys, SciFinder, ASKCOS | — | Condition recommendation from literature | Bundled |
| [Synple 2](https://www.sigmaaldrich.com/US/en/product/sial/synpleh007) | SynpleChem | Automated synthesis with pre-optimized cartridges | ✔ $312 per cartridge; instrument price not found |
| Chemify | Chemify | "Chemifarm" synthesis service | Not published |

#### HTE and lab automation hardware
| Tool | Price |
|---|---|
| Analytical Sales & Services HTE kits | ~$5–6k per kit |
| Chemspeed SWING | ~ US$70–85k (sample-prep configuration; synthesis configurations cost more) |
| Unchained Labs Big Kahuna + Junior | ✔ NIH: $62,318/year for the service agreement alone |
| Mettler-Toledo EasyMax 402 | ✔ US government purchases: $252k–302k |
| Full HTE lab | ~ $0.3–1M+ (inference) |

#### Computational chemistry
| Tool | Owner | Price |
|---|---|---|
| Schrödinger | Schrödinger | ~ Academic from ~$7,500/year; commercial quote only. Software annual contract value (ACV): $198.5M (2025) |
| Gaussian 16 | Gaussian Inc. | ✔ $17,325 (single machine) to $40,325 (site), via a distributor |
| [Q-Chem](https://www.q-chem.com) | Q-Chem | ✔ Commercial: $6,480 (single seat) to $25,920 (site); academic $1,080 |
| ORCA | FAccTs / MPI | Free for academics; ~ $30k/year commercial (Reddit report) |
| AMS | SCM | ✔ Academic: €2,000/year per module |
| [Rowan](https://rowansci.com/pricing) | Rowan | Free tier; Team and Enterprise tiers; ~ $75k/year enterprise |
| Meta UMA / OMol25, MACE, Orb | Meta, Cambridge, Orbital | Free (open or royalty-free licenses) |

#### Outsourcing
| Option | Price |
|---|---|
| Chemist per year (one full-time chemist) | ~ China $60–100k, India $50–80k, US/EU $250–350k (single secondary source) |
| [Enamine REAL](https://enamine.net) make-on-demand | Flat tiered prices (not published); success rates 85%+ (simple), 75%+ (medium), 65%+ (hard); 3–4 weeks |

### Gaps: what none of these do
- **Conditions for new chemistry**: condition recommendation is either bundled from literature (Reaxys, SciFinder, ASKCOS) or needs your own experiments from scratch (EDBO, Atinary).
- **Simulation-based prediction**: physics tools (Schrödinger, Gaussian, UMA) exist, but no reaction-prediction product found is built on them.
- **Negative data**: only Molecule.one has proprietary HTE data (>300k experiments) — **the closest competitor** to our data approach.
- **Planning and making are separate purchases**: route planners cost thousands to tens of thousands per year, but making still needs HTE hardware ($250k+) or a CRO.
- **Single-vendor risk**: IBM RXN's hosted service shut down in Oct 2026.
