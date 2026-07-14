# QuIC Characterization: What a Training-Free Quantum Graph Embedding Knows

## The angle, and why AAAI

Modern graph representation learning is organized around an expressivity question. Standard message-passing networks provably cannot count cycles (Chen et al. 2020), and the field's response has been to inject structure: precomputed motif counts (GSN), random node identifiers (RNI), and Laplacian positional encodings (LapPE). Every one of these fixes works by handing the network information it cannot compute.

QuIC sits at the opposite pole. It is a three-layer quantum circuit with **no trained parameters, no injected features, and no structural side channels**: a uniform rotation layer, one phase per edge, one mixing layer, then measurement and sorting. The sorted output distribution is the representation. The question this paper answers is what structural information that fixed representation carries, how that information is organized geometrically, how much of it is classical spectral information in disguise, and whether the non-spectral remainder does functional work.

The answer is a characterization with four connected findings, each carried jointly by a theorem and a pre-registered experiment:

1. **Hierarchical geometry.** The embedding organizes cycle counts lexicographically: triangles globally, 4-cycles within fixed-triangle strata, 5-cycles within joint strata.
2. **Broad linear accessibility.** A ridge probe on the raw sorted vector linearly decodes cycle counts, girth, and spectral summaries at high fidelity, with no training of the representation itself.
3. **A spectral backbone with a real non-spectral residue.** Most of the embedding's variance is classical spectral information, and we prove why. The residue separates cospectral graphs at certified precision, and its functional carriers are metric and symmetry invariants (Wiener index, radius, automorphism group order) plus one signed motif combination the spectrum provably aggregates away.
4. **A readout-depth tradeoff.** Finer structural content costs coordinate depth in the sorted vector, quantified by truncation curves and a per-pair head/tail decomposition.

Why this fits AAAI rather than a quantum venue: the contribution is a representation-learning result. The methodology is the field's own (linear probes, spectral baselines, GNN comparisons, exhaustive rather than sampled benchmarks), the theory is combinatorial rather than quantum-algorithmic, and the claims discipline is strict. **We make no quantum-advantage or efficiency claims anywhere.** The cospectral separations that evidence the non-spectral residue are certified real (Section: E2C) and simultaneously certified unmeasurable behind a 10^10 to 10^14 shot wall. The paper's honesty about that tension is part of the contribution.

## Summary of experimental proof.

**Proved.** The QuIC entangler encodes the complete graph cut function into computational-basis phases, and the whole circuit is a fixed, permutation-invariant hypercube transform of that cut landscape (Propositions 1 and 2). The labeled cut function determines the adjacency matrix exactly, so the transform's input contains the whole graph (Proposition 3; injectivity of the measured, sorted output is explicitly not claimed). The transform's Walsh coefficients factor by boundary sector into generating polynomials of edge subsets (Theorem 4). On cubic graphs the closed sector's first coefficients are exactly $C_3$, $C_4$, $C_5$, and its sixth coefficient carries $C_6 - D$ while the adjacency spectrum carries $C_6 + D$, where $D$ counts diamonds: the two representations expose complementary signed combinations that jointly pin both quantities (Corollaries 5 and 6). Pair-boundary sectors carry graph distances, hence the Wiener index and radius, in their lowest-degree terms (Corollary 7). Every constant-feature message-passing network provably collapses to a single point on a fixed-degree regular census (Proposition 8). Supporting exact identities verified on both full censuses: $C_3$, $C_4$, $C_5$, and girth are spectral invariants on cubic graphs, and $\text{tr}(A^6) = 87n + 6C_3 + 96C_4 + 12(C_6 + D)$.

**Measured, on complete enumerations (509 + 4,060 cubic graphs).** The embedding geometry realizes the proved hierarchy: triangles globally, $C_4$ within triangle strata, $C_5$ within joint strata (Fisher $p \le 3.31\times10^{-40}$). A ridge probe on the untrained sorted vector linearly decodes $C_3$ and $C_4$ at 1.000, $C_5$ at 0.98, and girth at 0.999 at n = 16, and the strongest trained GNN arm (GIN + LapPE) loses every cycle row to it while the constant-feature arms collapse with spread exactly zero across 210 models, as Proposition 8 requires. There is no nonlinear headroom anywhere: the linear table is the representation's ceiling. All 46 cospectral pairs across both censuses separate, and an independent reimplementation plus extended-precision recompute certifies every separation at 2.5e+07 to 2.9e+10 times its measured float64 rounding floor, with three arithmetics agreeing to every displayed digit. The residue's functional carriers match Corollary 7's prediction exactly: within cospectral groups, only Wiener index, radius, and automorphism order vary.

**Open and in flight.** The diamond sign split (Corollary 6) awaits its direct test in the running E2R diamonds row. E6 (built) asks whether QuIC beats the spectral baseline on $C_5$ off regularity, where the $C_5$ identity provably breaks. E8B asks whether the certified residue does predictive work on Wiener ranking inside cospectral groups, where the spectrum ties by construction.

---

This repository contains the theory, experiments, and artifacts for an AAAI 2027 submission characterizing **QuIC**, a fixed, training-free quantum graph embedding. QuIC is the object introduced in our IEEE QCE 2026 paper (*QuIC: A Training-Free Quantum Graph Embedding with Large-Scale Hardware Validation*, arXiv:2604.18841). This study asks a different question about the same object: not whether it runs on hardware, but what it represents.



## The object

For a graph $G$ with $n$ vertices and $m$ edges, one repetition of the circuit is

$$U_G = U_M(\beta)\, U_E(G,\gamma)\, U_D(\boldsymbol{\alpha}), \qquad |\psi_G\rangle = U_G|0^n\rangle,$$

where $U_D$ applies $R_X$ rotations (uniform on regular graphs), $U_E$ applies $R_{ZZ}(\gamma)$ on every edge, and $U_M$ applies a uniform $R_X(\beta)$ mixer. The representation is the descending-sorted Born distribution $q_G = \text{sort}_\downarrow \{|\langle y|\psi_G\rangle|^2\}$.

The configuration is locked for the entire study: canonical angles $(\theta_{\mathrm{enc}}, \gamma, \beta) = (2.875, 2.0, 0.1)$, one repetition, exact statevector simulation, full sorted vectors, SEED = 0. The primary datasets are the **complete enumerations** of connected cubic graphs at $n = 14$ (509 graphs) and $n = 16$ (4,060 graphs), generated by nauty. Exhaustive censuses mean cross-validation folds partition a complete population, so we say "linearly decodable" and never "generalizes."

## Mathematical framework, in brief

Full statements and proofs are in `Mathematical_Framework_QuIC.ipynb`. Every identity below is additionally verified numerically inside the experiment notebooks that use it.

**Proposition 1 (cut-phase identity).** The entangler acts diagonally as $U_E|x\rangle = e^{-i\gamma m/2} e^{i\gamma c_G(x)}|x\rangle$, where $c_G(x)$ is the number of edges crossing the cut induced by the bitstring $x$. The circuit therefore encodes the complete graph cut landscape into phases, and QuIC is a fixed hypercube-convolution transform of that landscape.

**Proposition 2 (permutation equivariance).** $q_{\pi G} = q_G$ for every vertex permutation $\pi$. Sorting quotients out the label action, so the representation is a graph-isomorphism invariant.

**Proposition 3 (cut-function completeness).** The labeled cut function determines the adjacency matrix exactly via $A_{ij} = \tfrac{1}{2}\left(c_G(\{i\}) + c_G(\{j\}) - c_G(\{i,j\})\right)$. The signal entering the transform contains the whole graph. This does **not** imply injectivity of the measured, sorted output, and we do not claim it (see the limitations note below).

**Theorem 4 (boundary-resolved Fourier expansion).** The Walsh coefficient of the pure cut-phase function on character $T \subseteq V$ is

$$\widehat{f}_G(T) = e^{i\gamma m/2} \cos(\gamma/2)^m \, Z_{G,T}\!\left(-i\tan\tfrac{\gamma}{2}\right), \qquad Z_{G,T}(z) = \sum_{F \subseteq E,\ \partial F = T} z^{|F|},$$

where $\partial F$ is the odd-degree boundary of the edge subset $F$. The transform organizes the graph by boundary sector: the closed sector ($T = \varnothing$) enumerates even subgraphs, and open sectors enumerate $T$-joins. One qualification is stated up front: at the canonical angle, $|\tan(\gamma/2)| \approx 1.557 > 1$, so the expansion orders which structures occur and at what edge order, not their numerical influence. Fixed-angle dominance is established by the experiments, and the small mixer angle ($\tan(\beta/2) \approx 0.05$) supplies the perturbative handle, exposing finite differences of the cut landscape at first order.

**Corollary 5 (cubic closed-sector coefficients).** On cubic graphs, even subgraphs are vertex-disjoint cycle unions, so $[z^3]Z_{G,\varnothing} = C_3$, $[z^4] = C_4$, $[z^5] = C_5$, and $[z^6] = C_6 + \binom{C_3}{2} - D$, where $D$ counts diamonds ($K_4$ minus an edge). The theory hands the experiments the exact hierarchy $C_3 \to C_4 \to C_5$ that E1 then observes geometrically.

**Corollary 6 (diamond sign split).** On cubic graphs the sixth spectral moment satisfies $\text{tr}(A^6) = 87n + 6C_3 + 96C_4 + 12(C_6 + D)$, so the spectrum pins $S_6 = C_6 + D$, while the sixth closed cut sector carries $Q_6 = C_6 - D$. The two representations expose complementary signed combinations, and jointly they pin $C_6$ and $D$ individually. This is the sharpest exact distinction between QuIC and the spectrum, and the E2R diamonds row is its direct empirical test.

**Corollary 7 (distance valuation).** The lowest-degree term of the pair-boundary polynomial satisfies $\text{val} Z_{G,\{u,v\}} = d_G(u,v)$, with leading coefficient equal to the number of shortest paths. The boundary-resolved transform structurally contains the distance matrix, hence the Wiener index and radius. This is the theoretical explanation for exactly the invariants the cospectral audit (E8A) found in the non-spectral residue.

**Proposition 8 (constant-feature MPNN collapse).** Any permutation-invariant message-passing network with uniform initial features produces the identical embedding for every graph in a fixed-$(n, d)$ regular census. This is the theorem behind the E3 constant-feature rows, where the collapse is also **measured** rather than assumed.

**Supporting spectral identities on cubic graphs** (all verified exactly on both censuses): $C_3 = \text{tr}(A^3)/6$, $\ C_4 = (\text{tr}(A^4) - 15n)/8$, $\ C_5 = (\text{tr}(A^5) - 10\text{tr}(A^3))/10$, and girth is a threshold function of $C_3$ through $C_5$ at these sizes. The entire cycle table is spectral information on cubic graphs, which is what makes the residue question sharp. Off regularity, the general identities $\text{tr}(A^3) = 6C_3$ and $\text{tr}(A^4) = 8C_4 + 2\sum d_i^2 - \sum d_i$ survive, while the $C_5$ identity breaks. E6 is designed around exactly that breakage schedule.

**What is not proved.** Injectivity of the measured, sorted representation is not claimed. The Born map erases coordinate-dependent phases and sorting erases output permutations, so measured injectivity would require a uniform anti-aliasing theorem we do not have. Choosing $\pi$-irrational angles prevents periodic aliasing of distinct integer cut values and nothing more.

## Results to date

All probes use RidgeCV (alpha grid $10^{-14}$ to $10^2$, nested cv = 5) on frozen KFold(5, shuffle, seed 0) splits shared across every experiment. Fisher-combined p-values are reported as upper bounds.

**E1, stratified residue (n = 14 complete; n = 16 replication in flight).** The global embedding geometry tracks triangles (Mantel $\rho = +0.903$). Within fixed-triangle strata, $C_4$ claims the first principal component ($|\rho|$ 0.978 to 0.988, Fisher $p \le 2.05\times10^{-15}$). Within joint $(C_3, C_4)$ strata, $C_5$ organizes the residue (Fisher $p \le 3.31\times10^{-40}$). The hierarchy Corollary 5 makes available is the hierarchy the geometry exhibits.

**E2, linear decodability (both censuses).** Full-vector linear $R^2$, mean over frozen folds:

| target | n = 14 | n = 16 |
|---|---|---|
| $C_3$ | 1.000 | 1.000 |
| $C_4$ | 0.998 | 1.000 |
| $C_5$ | 0.928 ± 0.092 | 0.982 ± 0.015 |
| $C_6$ | 0.485 ± 0.326 | 0.642 ± 0.122 |
| girth | 0.993 | 0.999 |
| diameter | 0.548 | 0.737 |
| spectral gap | 0.944 | 0.932 |

The n = 14 to n = 16 comparison is an exhaustive replication at two graph orders (every row holds or improves), and we describe it that way rather than as a scale law.

**Moment ladder (both censuses).** Probability power sums $\sum_j p_j^r$ grade the hierarchy exactly: triangles are recovered by purity alone ($M_2$, $R^2 \to 0.999$), $C_4$ saturates at exactly $r = 5$ at its full-vector ceiling (0.997), and $C_5$ is absent from moments through $r = 8$ ($R^2 \le 0.11$) and is not quadratic in them (0.14) despite being linearly accessible from the full vector. Finer structure lives beyond the lowest symmetric summaries, consistent with Section 18 of the framework.

**E2.5, spectral decomposition (n = 14).** Spectral moments explain 57 to 59% of embedding variance. The second principal component (15.3% of variance) is non-spectral (full-spectrum $R^2 = 0.195$), with $C_6$'s non-spectral component accounting for roughly 0.21 of it.

**Cospectral suite (both censuses).** Exact integer cospectrality over trace tuples certifies 3 mate pairs at n = 14 and 41 groups (83 graphs, 43 pairs, including one mutually cospectral triple) at n = 16. Every pair separates in QuIC. Global percentile standing is small (0.0 to 6.4) because the moment axis dominates global distances; within the count-identical fine-structure class the mates rank at the 14th to 93rd percentile, so the non-spectral channel carries the same separation scale as spectral fine structure. The showcase pair (201, 203) sits at the 79th to 93rd percentile with exactly zero spectral distance.

**E3, GNN comparison (both censuses, four arms, 3 seeds × 5 frozen folds).** Constant-feature GIN and GCN collapse with embedding-spread ratio exactly 0.00e+00 across 210 trained models, matching Proposition 8 as a measurement. GIN with full-strength random node initialization recovers a weak triangle signal (0.57 net, 0.72 probe at n = 16) and little else. GIN with Laplacian positional encodings, the strongest arm, loses every cycle row to the untrained QuIC probe at n = 16 (0.94 / 0.61 / 0.57 / 0.50 against 1.000 / 1.000 / 0.982 / 0.642) and degrades monotonically down the hierarchy. The trained arms win two honest, pre-registered non-cycle cells: diameter (0.807 vs 0.737) and spectral gap (0.996 vs 0.932), and those wins anchor the table's credibility. All claims are scoped to the tested message-passing and LapPE configurations on cycle decoding.

**E5, nonlinear readout (both censuses).** Two load-bearing negatives. First, $C_5$ and $C_6$ are unrecoverable from eight probability power sums across linear, kernel-ridge, and MLP estimator families ($R^2 \le 0.20$) while the $C_4$ control hits 0.995+ under the identical protocol, phrased as estimator-family robustness. Second, the full vector has no nonlinear headroom anywhere ($C_5$ 0.982 → 0.945, $C_6$ 0.642 → 0.613, diameter 0.737 → 0.699 under kernel ridge), so the E2 table is the representation's ceiling rather than the probe's.

**E7, truncation curves (both censuses).** At k = 50 retained coordinates: $C_3$ 1.000, $C_4$ 0.98 to 0.99, $C_5$ and $C_6$ near zero. Deeper structural content costs readout depth. The companion figure pairs falling $R^2(k)$ with rising cospectral-mate percentile under the same truncation knob.

**E8A, cospectral group audit (both censuses).** The exact integer census reproduces the earlier spectrum-hash census identically, closing the tolerance question with no tolerance at all. The spectrally pinned invariants ($C_3, C_4, C_5$, girth) tie in all 44 groups, as the identities require. The pre-registered challenge targets fail their gate: $C_6$, $C_7$, diameter, connectivity, matching number, and clique number differ in **zero** groups, and the $C_6$ tie is explained rather than observed once the $\text{tr}(A^6)$ identity shows the spectrum pins $C_6 + D$. The gate passers, and therefore the residue's functional carriers, are the Wiener index (25 of 41 groups), automorphism group order (14), and radius (4). Corollary 7 explains why those in particular.

**E2C, precision audit (complete).** An independent pure-numpy reimplementation of the circuit reproduces every stored vector across all 89 cospectral group members to a worst coordinate deviation of 2.22e-15 against a 1e-12 gate. Float64 reconstruction floors are measured per graph (7.4e-17 to 1.1e-15), longdouble recomputes all members, and mpmath at 40 digits certifies longdouble in turn (floors near 9e-19). **Zero of 46 pairs are unresolved**: the smallest separation in either census (1.917e-08) exceeds its own measured float64 floor by a factor of 2.48e+07, and the three arithmetics agree to every displayed digit. The separations are properties of the circuit, not artifacts of the arithmetic. The head/tail decomposition adds structure: 90% of every pair's separation lives within the top 7% of sorted coordinates, and the pairs form families (a maximally head-weighted loud cluster with k50 between 42 and 51, and fixed-depth families whose 50%-mass coordinate recurs at 203 to 213 and 448 to 456 across unrelated pairs), so truncated readouts retain between 54 to 67% and as little as 1.8% of a pair's separation depending on family.

## In flight

Three notebooks are launched with results pending: the **E1 n = 16** replication (after a 100× exact-statistic Mantel rewrite with an in-call correctness assert), **E2S**, the direct spectral baseline (eigenvalues / trace moments / QuIC / concatenation on frozen folds, with the $C_6$ null result now pre-registered as expected via the $\text{tr}(A^6)$ identity, leaving diameter as the live cell), and **E2R**, the cross-fitted spectral-residual probe over eleven targets. E2R's diamonds row is the direct empirical test of Corollary 6: QuIC decoding a quantity the spectrum provably cannot supply alone.

## Remaining experiments

**E0, shuffled-target control.** One cell at n = 14 addressing the $p \gg n$ concern: shuffled targets must decode at chance.

**E6, fixed-degree-sequence robustness (built, not yet run).** Four strata of 400 connected graphs at n = 14, each stratum a fixed nonregular degree sequence (near-regular, bimodal, skewed, hub), sampled by degree-preserving connected edge swaps with canonical-form deduplication. Degree information cannot leak into any comparison because it is constant within a stratum, and the spectral identities degrade on schedule: $C_3$ stays pinned everywhere, $C_4$ stays pinned within strata (since $\sum d_i^2$ is a stratum constant), and $C_5$ is the first live row. The encoder is deliberately flat here, RX(2.875) on every qubit, which is exactly what the canonical degree-proportional encoder reduces to on regular graphs (verified bit-identically), so E6 varies the graphs while holding the representation fixed, and a degree-proportional encoder would have reintroduced per-vertex degree as an injected node feature, the very move the E3 comparison criticizes. The consumer runs the E2S column set within each stratum on frozen splits, with the C3/C4/spectral-gap rows serving as built-in consistency checks. The pre-registered question: does QuIC beat the direct spectral baseline on $C_5$ once the spectrum loses its identity?

**E8B, cospectral challenge (design fixed by E8A).** Within-group Wiener-index ranking with group-in-fold cross-validation, where the spectrum ties by construction. Roughly 26 usable comparisons, so the sign test needs about 18 of 25 for one-sided p < 0.05, a thinness we state up front. Automorphism-order ranking is secondary, and a label-efficiency experiment (QuIC ridge vs spectral ridge vs LapPE-GIN at 2 to 80% training fractions) runs as a companion.

**Optional.** A PPGN / 2-WL arm joins E3 only if time remains.

Writing begins on schedule regardless of experiment state. The core paper already exists in E1, E2, E2.5 with E2S and E2R, E3, E7, the cospectral suite, and the framework.

## Repository contents

| Path | Role |
|---|---|
| `Mathematical_Framework_QuIC.ipynb` | Full framework: propositions, theorem, corollaries, proofs, and the theory-to-experiment pairing table |
| `n14-aaai-dataset.ipynb`, `n16-aaai-dataset.ipynb` | Dataset producers: exhaustive cubic censuses, exact statevectors, cycle counts, spectra |
| `AAAI_n14_E2_ridge_probe_exploration.ipynb` | Provenance record of the two probe failures and their diagnoses (kept intact by policy) |
| `AAAI_n14n16_E2_ridge_probe.ipynb` | E2, moment ladder, E2.5, cospectral discovery, count-identical class |
| `aaai-n14-e1-stratified-residue.ipynb`, `aaai-n16-e1-stratified-residue.ipynb` | E1 stratified hierarchy |
| `AAAI_n14n16_E3_gnn_training_producer.ipynb`, `AAAI_n14n16_E3_gnn_analysis_consumer.ipynb` | E3 four-arm GNN comparison |
| `AAAI_n14n16_E5_nonlinear.ipynb` | E5 nonlinear readout |
| `AAAI_n14n16_E7_truncation.ipynb` | E7 truncation curves and tracer figure |
| `AAAI_n14n16_E8A_cospectral_audit.ipynb` | E8A exact census and invariant audit |
| `AAAI_n14n16_E2S_spectral_baseline.ipynb`, `AAAI_n14n16_E2R_residual_probe.ipynb` | Spectral baseline and residual probe (in flight) |
| `AAAI_n14n16_E2C_precision_audit.ipynb` | E2C independent recompute and extended-precision certification |
| `AAAI_n14_E6_dataset_producer.ipynb`, `AAAI_n14_E6_analysis_consumer.ipynb` | E6 fixed-degree-sequence strata (built, pending run) |

Producer/consumer discipline holds throughout: producers generate expensive artifacts (statevectors, trained models) as pickles, consumers load them, cheap quantities are recomputed rather than cross-loaded, split identity is hard-asserted before any table prints, and failed runs are preserved in the notebooks as the record of what broke and why.

## Provenance and reproducibility

Every dataset is a complete enumeration or a seeded, deduplicated sample. SEED = 0 end to end. The circuit configuration is locked and appears identically in every producer. Load-bearing identities carry in-notebook exact asserts on the full censuses. The stored vectors have been reproduced by a second, independent implementation to 2.2e-15. The cross-validation splits are pickled once and asserted everywhere they are reused.
