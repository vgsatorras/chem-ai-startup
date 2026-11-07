# Lean Canvas

Milestone 1 toward the [mission](../mission.md).

One-page summary; deep research lives in each section's file.
Every entry starts as a guess. Test the riskiest one first, then update.

Sections follow the canvas layout. Fill them in this order (number in brackets):
Customer Segments → Problem → Unique Value Proposition → Solution → Channels → Revenue Streams → Cost Structure → Key Metrics → Unfair Advantage.

## [Problem](problem.md) (2)
Top 1–3 problems.

- Making molecules is slow, expensive, and sometimes not even possible (the "Make" gap).
- Finding reaction conditions is trial and error.
- Waste (secondary).

### [Existing Alternatives](existing-alternatives.md)
How these problems are solved today.

- Chemists' intuition and trial and error; retrosynthesis tools; high-throughput experiments; DFT.
- Current AI tools fall short: they don't generalize to new chemistry, lack negative examples, and train on weak literature data.

## [Solution](solution.md) (4)
Top 3 features that solve the problems.

- Pre-train on large-scale simulations (generalization).
- Fine-tune on experimental data (accuracy).
- Autonomous closed loop: simulation → experiment.

## [Key Metrics](key-metrics.md) (8)
The few numbers that show the business is working.

## [Unique Value Proposition](unique-value-proposition.md) (3)
One clear, compelling message: why you are different and worth buying.

**Synthesis routes that work in the lab on the first try.**

- Know if a reaction will work before you run it.
- Know if a synthesis route exists for a given molecule.
- Make molecules no one has made before, using newly explored chemistry.

### High-Level Concept
X for Y analogy (e.g., "YouTube = Flickr for video").

The most accurate simulator of chemical reactions.

## [Unfair Advantage](unfair-advantage.md) (9)
Something that can't easily be copied or bought.

- Founder expertise in both AI and reaction modelling → state of the art quickly (E(n) Equivariant GNNs, E(3) Equivariant Diffusion; leads reaction-modelling research at Microsoft).

## [Channels](channels.md) (5)
Path to customers.

- **Now: direct, founder-led sales** to early adopters (pharma HTE groups, agrochemical majors). Run paid pilots on their own reactions.
- **Papers and public benchmarks**: prove the "most accurate" claim in the open; the founder's research reputation brings inbound interest.
- **Network**: Microsoft Research, University of Amsterdam, investors' portfolio companies.
- **Later: partnerships** with CROs (e.g., WuXi, Enamine) and HTE hardware makers (e.g., Unchained Labs, Mettler-Toledo), plus a free web demo for chemists.

## [Customer Segments](customer-segments.md) (1)
Target customers and users.

- Pharma medicinal chemistry and HTE groups.
- Agrochemical R&D.
- CROs and make-on-demand suppliers (also a channel).
- Process chemistry and CDMOs.

### Early Adopters
Characteristics of the ideal first customers.

- Teams that already run HTE or automation, have data scientists, and name synthesis as a bottleneck (e.g., AstraZeneca, Merck/MSD, Novartis, Roche; agrochemical majors).

## [Cost Structure](cost-structure.md) (7)
Fixed and variable costs.

## [Revenue Streams](revenue-streams.md) (6)
How the company makes money.

1. **Paid pilots** on customers' own reactions (price to be tested in customer calls).
2. **Enterprise license** after a successful pilot (annual; Schrödinger is the template).
3. **Outcome-based pricing**: pay per validated route that works in the lab.
4. **Later, upside**: partnerships with upfront fee, milestones and royalties.
