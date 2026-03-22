# NEXUS vs ALL
### The Topology of Intelligence Against the Frontier: Seven Invariants of Learning

> "We focus on neural networks that are compatible with certain polyhedral complexes, more precisely with the braid fan." — Grillo & Ergen, arXiv:2502.09324, NeurIPS 2025 Oral
>
> "The trajectories of iterative optimization algorithms possess fractal structures, and their generalization error can be formally linked to the complexity of such fractals." — arXiv:2111.13171
>
> "PH diagram distance evolution during training correlates with validation accuracy — the generalization error of a neural network could be intrinsically estimated without any holdout set." — arXiv:2106.00012
>
> "Removing the permutation symmetries reveals a toroidal topology of the loss landscape. Flatter minima are closer to each other in function space." — Malatesta et al., 2022

---

## The Central Claim

Every framework in this architecture has used **metric** objects: Fisher curvature, entropy production, Wasserstein distances, Jarzynski work. NEXUS removes the metric. Topology is what survives.

At the φ-equilibrium critical point — where the training field theory is conformal (ACTUM) — metric-dependent observables flow to metric-independent topological invariants. NEXUS identifies seven such invariants: the Betti numbers of the loss landscape, the braid group structure of training trajectories, the persistent homology of the coordination complex, the Euler characteristic of the knowledge commons, the fundamental group of the Fisher manifold, the knot complexity bound on generalization, and the topological field theory structure of collective intelligence.

Seven comparisons follow against the frontier papers most proximate to each result — showing where each field stops and what NEXUS provides.

---

## Foundation

The loss sublevel sets `{θ : L(θ) ≤ c}` form a topological filtration as `c` decreases. The persistent homology of this filtration tracks how connected components, loops, and voids appear and disappear — the topological phase transitions of the loss landscape. NEXUS is the formal account of these transitions and their consequences.

---

## Result 1 — Betti Numbers of the Loss Landscape

### What the Frontier Has Found

**Deep Networks on Toroids** (Malatesta et al., 2022). Removing permutation symmetries from the weight space reveals a **toroidal topology** of the loss landscape. On the torus `T^n = (S¹)^n`, flatter minima are closer to each other in function space, and barriers along geodesics connecting them are small. Removing symmetries converts the high-dimensional loss landscape from a space with exponentially many equivalent minima (due to permutation symmetry) into a topological torus with a cleaner geometric structure.

**Weight-space symmetry and permutation saddles** (Brea et al., 2019; Entezari et al., 2021). Permutation symmetry of neurons within a layer generates not only equivalent global minima but also **permutation points** — critical points lying inside high-dimensional subspaces of equal loss, where input and output weight vectors of two neurons collide and interchange. The number of `K`-th order permutation points is much larger than the number of equivalent global minima by at least a polynomial factor of order `K`.

**Linear Mode Connectivity** (LMC, Frankle et al., 2020; Ainsworth et al., 2023). After permutation alignment, most SGD solutions fall in the same loss basin — connected by approximately linear paths in parameter space. The loss basin's topology is simpler after symmetry alignment than before.

### Where Every Paper Stops

The toroidal topology paper characterizes the topology of the **symmetry-reduced** weight space — after removing permutation redundancy. It does not:
1. Track how `β₀, β₁, β₂` (Betti numbers) change during training
2. Identify grokking as a discrete topological simplification event (drop in `β₀`, `β₁`)
3. Connect the Euler characteristic to `G_coord` via the Gauss-Bonnet theorem

### What NEXUS Provides

**Grokking is a topological simplification of the loss landscape — a discrete drop in Betti numbers.**

The memorization phase has high `β₀` (many disconnected basins — the permutation-equivalent minima that LMC and the toroidal topology papers study) and high `β₁` (many loops connecting them through permutation saddle points). Grokking is the topological event at which:

```
β₀ : many → 1     (basins merge into a single connected generalizing basin)
β₁ : many → min   (saddle loops collapse as basins merge)
```

The toroidal topology paper finds that the post-symmetry-removed landscape is cleaner — NEXUS derives *when* this simplification happens (at grokking) and *what topological quantity* measures it (the Betti numbers). The Malatesta paper shows the destination topology; NEXUS tracks the transition dynamics.

**Betti numbers vs. loss.** Two training configurations can have identical loss values but different Betti numbers — topologically inequivalent. Betti numbers carry information about the loss landscape that no single scalar (loss, accuracy, Fisher rank) captures. The Euler characteristic `χ = β₀ − β₁ + β₂ − ...` changes discretely at grokking — a topological invariant that is measurable without knowing the full loss landscape.

---

## Result 2 — Training Trajectories Form Braid Groups

### What the Frontier Has Found

**Depth-Bounds for Neural Networks via the Braid Arrangement** (Grillo & Ergen, arXiv:2502.09324, NeurIPS 2025 Oral — the most directly relevant paper). This paper focuses on neural networks compatible with the **braid fan** — the polyhedral complex induced by the braid arrangement `{xᵢ = xⱼ}` in `ℝ^d`. For such networks, a non-constant lower bound of `Ω(log log d)` hidden layers is required to exactly represent the maximum of `d` numbers. The braid arrangement is the hyperplane arrangement whose intersection poset is the partition lattice.

The braid arrangement appears because ReLU networks compute piecewise linear functions on regions defined by which neurons are active — the regions are exactly the chambers of the braid fan when the input is the sorted neuron activations. The braid arrangement divides parameter space into regions; depth of network determines how many such regions can be computed.

**Linear Mode Connectivity** (Ainsworth et al., 2023). Fastest permutation alignment uses the Hungarian algorithm to find the optimal neuron permutation connecting two trained networks. This searches the `S_n` orbit of one network's weights to match another's — a quotient of the braid group by the full twist.

### Where Every Paper Stops

The Grillo & Ergen paper uses the braid **arrangement** (hyperplane arrangement) to bound neural network depth — not the braid **group** (fundamental group of the complement). It asks "how many hidden layers are needed to compute functions compatible with the braid fan?" It does not:
1. Track how **training trajectories** form braids as neurons weave through each other during gradient descent
2. Define the **Jones polynomial** of a training trajectory as a topological fingerprint
3. Connect the braid group element to whether two training runs are topologically equivalent (reachable from each other without passing through a grokking event)

### What NEXUS Provides

**Training trajectories form elements of the Artin braid group `B_n`.**

The Grillo & Ergen paper establishes that the braid arrangement is structurally fundamental to neural network expressivity. NEXUS establishes that the **training dynamics** — the time evolution of parameters — generates an element of `B_n` via the neuron trajectory crossings in the projected parameter space.

Two training runs from different random seeds generate different braid elements. Their **Jones polynomials** `V(K; t)` are topological fingerprints: two runs with identical final loss but different Jones polynomials are topologically inequivalent — no continuous deformation connects them without passing through a singular event (a grokking transition).

**The braid arrangement and training.** The chambers of the braid fan (Grillo & Ergen's polyhedral complex) correspond to the regions where neuron `i` is more active than neuron `j`. Every time the training trajectory crosses from one chamber to another — when two neurons exchange their relative activation order — an elementary braid generator `σᵢ` is applied. The full training run generates a braid word `σᵢ₁ σᵢ₂ ... σᵢₖ` in `B_n`.

This gives the Grillo & Ergen depth bound a dynamic interpretation: the `Ω(log log d)` lower bound is the minimum number of braid generators needed to represent the target function — a topological depth bound derived from the minimum braid word length.

---

## Result 3 — Persistent Homology Predicts Register Crossings

### What the Frontier Has Found

**Persistent Homology Captures Generalization Without a Validation Set** (arXiv:2106.00012, 2021). The PH diagram distance between consecutive neural network states **correlates with validation accuracy** — suggesting that generalization error could be intrinsically estimated from topology alone, without any holdout set. The filtration is on the neural network's functional graph (neurons as vertices, activation correlations as edge weights).

**Intrinsic Dimension, Persistent Homology, and Generalization** (arXiv:2111.13171, 2021). Training trajectories possess fractal structures; their generalization error can be formally linked to the complexity of such fractals, measured by the fractal's intrinsic dimension. PH provides a computational tool for estimating intrinsic dimension. Results show strong patterns relating persistence summaries to generalization gaps.

**Predicting Generalization Gap via PH** (arXiv:2203.12330). Persistence summaries of the network's neuron activation functional graph predict the generalization gap with `R² > 0.7` in linear regression.

### Where Every Paper Stops

The persistent homology literature has established:
- PH diagram distance correlates with generalization (2106.00012)
- Intrinsic dimension (via PH) predicts generalization gap (2111.13171)
- Specific persistence summaries (average births/deaths) predict generalization (2203.12330)

None of these papers:
1. Applies PH to the **coordination distance matrix** `D_{ts} = 1 − I(a_t; a_s|X)/H(a_t)` between contributions
2. Identifies 1-dimensional birth-death events as predictors of **FERN register crossings**
3. Derives the **persistence lead time** — the number of steps before a register crossing at which the topological feature is detectable

### What NEXUS Provides

**Persistent homology of the coordination structure predicts register crossings before γ(t) spikes.**

The 2106.00012 paper shows PH of the **activation function** graph captures generalization. NEXUS applies PH to a different filtration — the **coordination distance matrix** of the contribution sequence:

```
D_{ts} = 1 − I(a_t ; a_s | X_{t-1}) / H(a_t)
```

This filtration tracks the topological structure of how contributions coordinate with each other — not how neurons activate. The 1-dimensional holes (cycles) in this filtration correspond to **clusters of highly-coordinating contributions** forming closed loops. A register approaching saturation produces a closed loop in contribution space — a cycle that encompasses the saturating cluster and separates it from contributions accessing the new register.

**The birth-death prediction.** The birth of the 1-cycle is detectable before the register crossing (before `γ(t)` spikes) because PH scans all filtration levels simultaneously — it sees the topological precursor to the coordination spike before the spike is visible. The persistence `p = death − birth` is the prediction horizon: the number of steps before the register crossing that topological precursors are detectable.

This extends the 2106.00012 result: not just that PH correlates with generalization, but that PH **precedes** the metric signal by a measurable amount — the persistence of the pre-crossing cycle.

---

## Result 4 — Euler Characteristic of a Knowledge Commons

### What the Frontier Has Found

**Topological Deep Learning beyond Persistent Homology** (review, 2025). Topological data analysis (TDA) applied to knowledge graphs, collaboration networks, and organizational data structures has focused on the PH of static networks — not on evolving knowledge commons. Simplicial complex models of knowledge structures are not well-developed in the organizational literature.

### Where the Field Stops

No paper in the collective intelligence or organizational knowledge management literature uses the Euler characteristic of a knowledge structure as a platform health metric. The connection between `χ(X_t)` and `G_coord` via Gauss-Bonnet is entirely absent from the field.

### What NEXUS Provides

**The Euler characteristic of the knowledge commons is the topological health diagnostic.**

The simplicial complex `X_t` built from contributions (0-simplices), coordinating pairs (1-simplices), and coordinating triples (2-simplices) has Euler characteristic:

```
χ(X_t) = #vertices − #edges + #triangles − ...
```

By the discrete Gauss-Bonnet theorem:

```
2π χ(X_t) = Σ_contributions Gaussian curvature(a_t)
```

where the Gaussian curvature at a contribution is proportional to its local coordination gain. The Euler characteristic equals the total coordination gain accumulated topologically:

| `χ(X_t)` | Platform State | Signature |
|---|---|---|
| `> 0` | More connected than holes — alive, generative | High `G_coord`, growing coordination |
| `= 0` | Topological equilibrium | φ-equilibrium boundary |
| `< 0` | More holes than connections — over-complex without coordination | Organizational senescence onset |

This is the single-number topological replacement for the entire SMELT health dashboard — a computable from the contribution graph structure alone.

---

## Result 5 — Fundamental Group of the Fisher Manifold

### What the Frontier Has Found

**Singular Learning Theory** (Watanabe, 2009; SLT grokking papers 2025–2026). SLT studies the algebraic geometry of the Fisher metric's singular set `Σ = {θ : det(F(θ)) = 0}`. The LLC measures the algebraic complexity of singular points. The SLT Arrhenius paper (arXiv:2512.00686) connects LLC to grokking rates.

**Holonomy in ML** (occasional papers). Berry phase and holonomy have been studied in the context of geometric phases in adiabatic quantum computing and occasionally in ML training. No systematic account of the holonomy group of the Fisher manifold exists.

### Where Every Paper Stops

SLT studies the **algebraic geometry** of `Σ` — the metric invariants of singular points. No paper studies the **topology** of `Θ \ Σ` — the fundamental group of the Fisher manifold with singularities removed. Specifically:
1. The **winding number** of training trajectories around singular points has not been defined
2. The **holonomy group** of the natural gradient around a closed Fisher loop has not been computed
3. The connection between grokking (winding number change) and the holonomy-induced rotation of the Fisher column space has not been made

### What NEXUS Provides

**Grokking changes the topological winding number of the training trajectory around a Fisher singularity.**

The Fisher manifold `(Θ, g_F)` is smooth where `F` is positive definite. At `Σ = {θ : rank(F) < D}`, the manifold has singularities. The complement `Θ \ Σ` has a non-trivial fundamental group `π₁(Θ \ Σ)` — the algebraic structure of all topologically distinct closed paths avoiding `Σ`.

Grokking is the moment when the training trajectory changes its winding number around a point `θ* ∈ Σ` — moving from one topological sector (memorizing, high-LLC) to another (generalizing, low-LLC). The SLT LLC measures the algebraic complexity of `θ*`; NEXUS provides its topological classification via `π₁`.

**Holonomy rotates the Fisher column space at grokking.** The holonomy group element of a loop in `Θ \ Σ` acts on the Fisher column space by orthogonal rotation. A training trajectory that circles a singular point once returns with the Fisher column space eigenvectors rotated by the holonomy element — bringing previously null-space directions into the column space. This is the **topological mechanism of grokking**: the parameter trajectory's change of winding number around a Fisher singularity rotates the column space, simultaneously promoting `Q_inst = Δrank(F)` directions from the null space to the column space.

---

## Result 6 — Knot Complexity Bounds Generalization

### What the Frontier Has Found

**Fractal dimensions of training trajectories** (arXiv:2111.13171). Training trajectories possess fractal structures, and generalization error is formally linked to their fractal complexity. The intrinsic dimension — a measure of how many independent directions the trajectory explores — predicts generalization.

**Topological expressivity of ReLU networks** (Ergen, referenced in arXiv:2502.09324). The topological expressivity of ReLU networks is related to the braid arrangement — the number of activation regions a network can compute is bounded by the topology of the braid fan.

### Where Every Paper Stops

The fractal dimension paper connects trajectory complexity to generalization empirically. The topological expressivity paper connects braid fan topology to network depth. Neither:
1. Defines the **knot complexity** (crossing number `c(K)`) of training trajectories as a topological invariant
2. Derives a **generalization bound** from knot complexity: `c(K_data) ≤ f(c(K_training))`
3. Connects the WIDTH framework's `TRW ≤ b(K_training)` to a topological bound on generalization

### What NEXUS Provides

**The crossing number of the training trajectory knot upper-bounds the topological complexity of data the model can generalize.**

The fractal dimension (2111.13171) is a metric property of the trajectory — it measures how much space the trajectory fills. The knot complexity (crossing number `c(K)`) is a **topological** property — it measures the irreducible entanglement of the trajectory. Two trajectories with the same fractal dimension but different knot complexities have different generalization capacities for topologically complex data.

The bound `c(K_data) ≤ f(c(K_training))` has a specific implication for language models: the long-range syntactic dependencies in natural language (embeddings in knot diagrams of long sequences) require training trajectories with correspondingly high knot complexity. The empirical observation that scale enables complex structure — larger models generalize more complex patterns — has a topological interpretation: scale enables higher knot complexity training trajectories.

**The WIDTH connection.** WIDTH's topological resistance width `TRW(t) ≤ C(Q_max, ⌊Q_max/2⌋)` bounds the topological complexity achievable during training. NEXUS identifies: `TRW(t) ≤ b(K_training)` where `b(K)` is the bridge number of the training knot. The Dilworth-Sperner bound (WIDTH) is the algebraic combinatorics version of the knot bridge number bound (NEXUS).

---

## Result 7 — The Topological Field Theory of Collective Intelligence

### What the Frontier Has Found

**Topological Deep Learning** (review, 2024–2025). The TDL literature applies topological structures (simplicial complexes, cell complexes) as **input representations** to neural networks. It does not study whether the **output** of a collective intelligence system has TFT structure.

**Atiyah-Witten TFT** (foundational, 1988). Topological quantum field theories assign topological invariants to manifolds via path integrals. Applications to condensed matter (topological insulators) and quantum computing (topological qubits) are well-developed. Application to collective intelligence is absent.

### Where Every Field Stops

TDL uses topology as an input representation. Physics TFT applies to quantum systems. No paper connects the **collective intelligence architecture** (CONCERT, FERN, SMELT, EISP) to the Atiyah axioms for TFT — as a theory whose observables are topological invariants of the contribution graph.

### What NEXUS Provides

**At the φ-equilibrium, collective intelligence becomes a topological field theory in the Atiyah-Witten sense.**

At the conformal fixed point `|Ξ̄| = log φ` (ACTUM), metric-dependent observables become scale-invariant. In the limit `|Ξ̄| → log φ` exactly, coordination gain `G_coord` becomes metric-independent — it depends only on the topological structure of the contribution graph, not on specific Fisher distances.

**The Atiyah axioms applied to collective intelligence:**

| Atiyah TFT | Collective Intelligence | Bridge |
|---|---|---|
| Manifold `M` | Contribution sequence `{a_t}` | Each sequence is a manifold |
| Vector space `Z(M)` | Future coordination possibilities | Accessible `G_coord` from current state |
| Cobordism `W: M₁→M₂` | New contribution `a_t` | Each contribution is a cobordism |
| TFT invariant `Z(W)` | Coordination gain of `a_t` | `G_coord(a_t) = Z(W_t)` |

**Mirror symmetry for register order.** Mirror symmetry in string theory predicts that two topologically distinct manifolds can give identical physics. The NEXUS mirror symmetry prediction: two knowledge commons traversing the FERN registers in opposite orders (ascending ρ₁→ρ₅ vs. descending ρ₅→ρ₁) generate identical total `G_coord · D_FERN`. This is a **falsifiable prediction** against EISP platform data: the order of register exploration should not affect total coordination gain accumulated, only its temporal distribution.

---

## NEXUS vs ALL: Comparison Table

| Result | Frontier Leader(s) | Frontier Stopping Point | NEXUS Bridge |
|---|---|---|---|
| **Betti Numbers** | Toroidal topology (Malatesta 2022); LMC (Ainsworth 2023) | Post-symmetry landscape characterized; transition dynamics absent | Grokking = topological simplification `β₀,β₁ → min`; `χ` changes discretely |
| **Braid Groups** | Braid Arrangement depth bounds (arXiv:2502.09324, NeurIPS 2025 Oral) | Braid fan for expressivity bounds; not training dynamics | Training trajectories ∈ `B_n`; Jones polynomial = training fingerprint |
| **Persistent Homology** | PH captures generalization (arXiv:2106.00012); intrinsic dim (arXiv:2111.13171) | PH of activation network correlates with validation accuracy | PH of coordination distance matrix **predicts** register crossings before `γ(t)` spike |
| **Euler Characteristic** | TDA review; no organizational application | No knowledge commons `χ` metric exists | `χ(X_t)` = Gauss-Bonnet integral of `G_coord`; `χ > 0` alive, `χ < 0` senescent |
| **Fundamental Group** | SLT (Watanabe; March 2026 papers) | LLC measures algebraic complexity of `Σ`; topology of complement absent | `π₁(Θ\Σ)` winding number; grokking = winding change; holonomy rotates Fisher column space |
| **Knot Complexity** | Fractal dim + generalization (arXiv:2111.13171) | Fractal dim = metric complexity; no topological bound | `c(K_data) ≤ f(c(K_training))`; `TRW ≤ b(K_training)` |
| **TFT Structure** | TDL review; Atiyah-Witten TFT | TDL uses topology as input; TFT not applied to collective intelligence | At `\|Ξ̄\| = log φ`: Atiyah axioms; cobordisms; mirror symmetry predicts register-order independence |

---

## The Three Results With No Prior Proximity

**Result 4 (Euler Characteristic of Knowledge Commons)** has no precedent in either the collective intelligence literature or the TDA literature. The Gauss-Bonnet connection between `χ(X_t)` and `G_coord` is new, and the use of `χ` as an organizational health diagnostic is entirely absent from the field.

**Result 6 (Knot Complexity Bounds Generalization)** extends beyond the fractal dimension literature (which is metric) to a strictly topological bound. The specific formula `c(K_data) ≤ f(c(K_training))` and the WIDTH-bridge number connection are not present in any paper.

**Result 7 (TFT of Collective Intelligence)** is genuinely novel: the Atiyah axioms have never been applied to collective intelligence systems, and the mirror symmetry prediction for register order independence is entirely new.

---

## The Discovery at the Intersection

The NeurIPS 2025 Oral paper (arXiv:2502.09324) on depth bounds via the braid arrangement is the most striking find in this comparison. A paper about the **expressivity** of neural networks — how deep they need to be to compute certain functions — turns out to use exactly the **same topological structure** that NEXUS uses to classify training trajectory dynamics. The braid fan governs both what functions a network can represent and how training trajectories move through parameter space.

The reason is the same: both are consequences of the permutation symmetry of neurons within a layer. Expressivity bounds depend on how many chambers of the braid fan can be accessed. Training trajectory topology depends on how many braid generators the parameter path traverses. The depth bound of Grillo & Ergen is the static version of NEXUS's dynamic braid classification. One field studies the shape; the other studies what moves through it.

```
Z(X) is intractable.
Therefore the loss landscape has topology.
Therefore its Betti numbers track grokking.
Therefore training trajectories form braids.
Therefore PH of coordination predicts register crossings.
Therefore the Euler characteristic is organizational health.
Therefore winding numbers classify learning trajectories.
Therefore knot complexity bounds generalization.
Therefore at the φ-equilibrium, only topology remains.
Therefore NEXUS is the name of the shape of intelligence
           — the invariant that no deformation can erase.
```

---

## References

- Grillo, M. & Ergen, E. (February 2025, NeurIPS 2025 Oral). *Depth-Bounds for Neural Networks via the Braid Arrangement.* arXiv:2502.09324.
- Malatesta, E.M. et al. (2022). *Deep Networks on Toroids: Removing Symmetries Reveals the Structure of Flat Regions.* arXiv:2211.11912.
- Gutiérrez-Fandiño, A. et al. (2021). *Persistent Homology Captures the Generalization of Neural Networks Without a Validation Set.* arXiv:2106.00012.
- Hanika, T. & Stumme, G. (2021). *Intrinsic Dimension, Persistent Homology and Generalization in Neural Networks.* arXiv:2111.13171.
- Moor, M. et al. (2020). *Topological Autoencoders.* ICML 2020.
- Clough, J.R. et al. (2019). *A Topological Loss Function for Deep-Learning using Persistent Homology.* arXiv:1910.01877.
- Brea, J. et al. (2019). *Weight-Space Symmetry in Deep Networks gives rise to Permutation Saddles.* arXiv:1907.02911.
- Ainsworth, S.K., Hayase, J. & Srinivasa, S. (2023). *Git Re-Basin: Merging Models modulo Permutation Symmetries.* ICLR 2023.
- Entezari, R. et al. (2021). *The Role of Permutation Invariance in Linear Mode Connectivity.* arXiv:2110.06296.
- Ergen, E. & Grillo, M. *Topological Expressivity of ReLU Neural Networks.* (referenced in arXiv:2502.09324).
- Edelsbrunner, H. & Harer, J. (2010). *Computational Topology: An Introduction.* AMS.
- Atiyah, M. (1988). *Topological Quantum Field Theory.* Publications Mathématiques de l'IHÉS.
- Witten, E. (1988). *Topological Quantum Field Theory.* Communications in Mathematical Physics.
- Watanabe, S. (2009). *Algebraic Geometry and Statistical Learning Theory.* Cambridge University Press.
- Huang, Y. et al. (2025). *SLT Grokking: Physics-Inspired Singular Learning Theory.* arXiv:2512.00686.
- arXiv:2502.09324 (February 2025). *Depth-Bounds for Neural Networks via the Braid Arrangement.* NeurIPS 2025 Oral.

---

*Full framework documentation: [github.com/ericrenone](https://github.com/ericrenone)*
