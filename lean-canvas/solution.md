# Solution

Top 3 features that solve the problems.

## Summary
The short answer that goes into the [canvas](lean-canvas.md).

Hypothesis (not yet validated):
1. **Pre-train on large-scale simulations** so the model generalizes to new chemistry, beyond known reactions.
2. **Fine-tune on experimental data** to gain real-world accuracy.
3. **Autonomous closed loop, simulation → experiment**: experiments correct the model, and the model picks the next experiments.

Result: the generalization of large-scale simulation combined with the accuracy of experimental data.

It also gives us negative examples: simulations produce them naturally (a high energy barrier means the reaction won't happen), and the autonomous lab records every failure.

## Research

### Precedents
- **ANI-1ccx (Smith et al., Nat. Commun. 2019)**: pre-trained on DFT, then transfer-learned on a smaller set of near-exact CCSD(T) calculations. Reached close to CCSD(T) accuracy and generalized well. This is the same idea, applied simulation→simulation.
- **OMol25 (Meta, 2025)**: a dataset of over 100M DFT calculations. Large-scale simulation data is now practical.

### Risks
1. **The gap between simulation and reality**: DFT errors, solvent effects, and conformations are systematic biases that fine-tuning has to correct.
2. **A flask isn't a calculation**: yield, side products, and purification depend on conditions, impurities, and scale, which are hard to simulate.
3. **Competition**: Periodic Labs (backed by a16z) runs a simulation + autonomous-lab loop for materials. We need a clear point of difference.
4. **Lab cost**: a closed loop needs a lab: our own, or a partner such as a contract research lab.

### Investor views (Nov 2026)
Several items rely on press releases or secondary sources, so verify them before quoting externally.

**Support:**
- **Physics for out-of-distribution generalization**: Lux/Dimension (Achira): "the only viable path to truly robust out-of-sample prediction… is learning the underlying physical laws" ([Achira](https://achira.ai/)). This is the closest match to our hypothesis, but it focuses on drugs, not reactions.
- **Physical data**: a16z (Periodic Labs): literature labels are noisy, negative results go unpublished, and "nature becomes the reinforcement learning environment" ([a16z](https://a16z.com/announcement/investing-in-periodic-labs/)).
- **The "Make" gap**: Insight Partners (Chemify): "most of the molecules don't, and can't, exist outside of a computer screen" ([Insight](https://www.insightpartners.com/ideas/chemify-leadership-story/)). Deerfield and Khosla (Excelsior) want to fix "the slow, artisanal process of small molecule synthesis" ([Excelsior](https://excelsiorsci.com/blog/changes-how-small-molecules-discovered-manufactured/)). YC asks for AI-native "discovery engines" ([YC RFS](https://www.ycombinator.com/rfs)).
- **Negative data**: no investor thesis found yet. It's only mentioned indirectly through Periodic ("failures retrain the model").

**Skepticism:**
- **Out-of-distribution prediction is "poor" and proprietary models "quickly disseminate"**: Bruce Booth, Atlas ([LifeSciVC](https://lifescivc.com/2026/10/the-fruits-of-ai-drug-abundance-indigestion-in-the-near-term/)).
- **Weak evidence for AI materials**: only 736 of GNoME's 2.2M predicted structures have been independently synthesized, and CuspAI has no commercial candidate yet (secondary).
- **Lab cost and valuations**: Chemify's facility cost $16M; Periodic's valuation is called "stretched" (secondary).

### Competitors
| Name | Focus | Approach | Funding / investors |
|---|---|---|---|
| [Periodic Labs](https://a16z.com/announcement/investing-in-periodic-labs/) | Materials | Simulation + autonomous lab + RL on physical outcomes | $300M seed (2025), a16z lead |
| [Lila Sciences](https://www.lila.ai/news/announcing-the-close-of-our-series-a) | Life science, chemistry, materials | "AI Science Factories" (autonomous labs) | $550M total, Flagship |
| [CuspAI](https://www.nea.com/blog/from-algorithms-to-atoms-part-ii-doubling-down-on-cuspai) | Materials | Generative models + simulation + lab network | $450M Series B (2026), $2.6B valuation |
| [Chemify](https://www.businesswire.com/news/home/20251021496528/en/) | **Synthesis** | Robots ("chemputation") + reaction library | $43M Series A + $50M+ Series B (Wing, Insight) |
| [Excelsior Sciences](https://excelsiorsci.com/blog/changes-how-small-molecules-discovered-manufactured/) | **Synthesis** (small molecules) | Building blocks machines can assemble + closed-loop AI | $70M Series A (Deerfield, Khosla, Lilly) |
| [Achira](https://achira.ai/) | Drugs | Physics-based and synthetic-data atomistic models | $33M (Dimension, NVentures) |
| [Orbital Industries](https://resiliencemedia.co/orbital-industries-an-alphafold-for-materials-science-raises-50m/) | Materials → data-center hardware | Orb interatomic potential + own lab | $71M total |
| [Radical AI](https://intelligence.mts.now/atlas/radical-ai) | Alloys | Self-driving lab | $55M seed+ |
| [Rowan](https://rowansci.com/blog/rowan-announces-pre-seed-funding) | Computational chemistry software | ML potentials, DFT replacement | $2.1M pre-seed |
| [Iambic](https://www.businesswire.com/news/home/20251110232927/en/) | Drugs | Physics + ML (NeuralPLexer) | $100M+ |
| [Genesis Molecular AI](https://sacra.com/c/genesis-therapeutics/) | Drugs | Co-folding models | ~$327M total |
| [Emerald Cloud Lab](https://bioai-agents.com/en/compare/emerald-cloud-lab-vs-strateos/) | Cloud lab | Remote robotic lab execution | $56M total |

Not yet verified: PostEra, Iktos, Molecule.one (retrosynthesis, thinly funded), Synthia (owned by Merck KGaA).

### White space (inference)
- **Funded**: simulation for materials and drugs (Achira, Orbital, CuspAI, Periodic) and synthesis hardware (Chemify, Excelsior).
- **Not found**: a funded startup whose core is a **reaction-level foundation model**: pre-trained on DFT and transition-state simulations, fine-tuned on experimental data including failed reactions, in an autonomous loop.
- **Possible wedge**: be the model and data layer that synthesis-hardware companies lack. Predict reaction success under specific conditions on new substrates, with negative data as the moat.
