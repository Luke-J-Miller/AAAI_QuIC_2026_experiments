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



## Full Description of Experiments

### E1 - Stratified Residue
#### N14
##### Experimental design

The notebook analyzes the complete set of **509 connected 3-regular graphs on 14 vertices**. Each graph is represented by its full, sorted QuIC probability vector of dimension \(2^{14}=16{,}384\), generated with one noiseless circuit repetition and fixed canonical angles.

This is a particularly clean test bed:

- Every graph has the same order and degree sequence.
- The degree-encoding rotations are therefore identical across graphs.
- Bitstring identities are discarded by sorting the probabilities.
- Any geometric separation must arise from topology transmitted through the entangling circuit, rather than vertex degree or labeling.

The experiment compares pairwise \(L_1\) distances between QuIC embeddings with absolute differences in triangle, 4-cycle, and 5-cycle counts. Spearman Mantel tests assess whether graphs with more different cycle counts also lie farther apart in embedding space.

The stratified analyses then remove the dominant structural variables sequentially:

\[
\text{all graphs}
\rightarrow
\text{fixed triangle count}
\rightarrow
\text{fixed triangle and 4-cycle counts}.
\]

This is the central strength of the experiment. It does not merely observe correlations among several mutually correlated graph statistics; it progressively conditions out the stronger statistics and examines the residual geometry.

##### Global results

Across all 509 graphs:

| Structural quantity | Mantel \(\rho\) | Permutation \(p\) |
|---|---:|---:|
| Triangle count | 0.903 | 0.0001 |
| 4-cycle count | 0.290 | 0.0001 |
| 5-cycle count | 0.109 | 0.0001 |
| Random control | 0.005 | 0.3152 |

The embedding geometry is therefore dominated by triangle count. Graphs differing substantially in their number of triangles are almost invariably farther apart in QuIC space.

The weaker global values for 4- and 5-cycles should not be interpreted as weak encoding. Globally, triangle variation dominates the distance ordering and masks lower-order structural effects. The subsequent strata demonstrate this directly.

The random-scalar control produces essentially zero correlation and a nonsignificant permutation result. This supports the claim that the observed associations are structural rather than generic consequences of comparing pairwise distance matrices.

##### Fixed-triangle strata

Five triangle-count strata contain at least 15 graphs, covering **490 of the 509 graphs**, or approximately **96.3%** of the enumeration.

Within each fixed-triangle stratum, the association with 4-cycle count becomes extremely strong:

| Triangle stratum | \(n\) | C4 \(\rho\) | C5 \(\rho\) | Effective rank |
|---|---:|---:|---:|---:|
| 0 triangles | 110 | 0.968 | 0.320 | 2.90 |
| 1 triangle | 122 | 0.954 | 0.179 | 2.88 |
| 2 triangles | 139 | 0.926 | 0.200 | 3.06 |
| 3 triangles | 74 | 0.906 | 0.175 | 2.87 |
| 4 triangles | 45 | 0.898 | 0.203 | 2.79 |

Once triangle count is fixed, 4-cycle differences almost completely organize pairwise embedding distances. The consistency is more important than any single value: every sufficiently large triangle stratum produces \(\rho\) between 0.898 and 0.968.

The PCA results make the geometric claim more concrete. In the four largest strata, PC1 explains approximately 53–56% of the variance and has Spearman correlation between \(-0.978\) and \(-0.988\) with 4-cycle count. The sign is arbitrary because PCA eigenvectors may be reversed. In magnitude, PC1 is essentially a 4-cycle axis.

This is stronger than saying that 4-cycle count is statistically associated with the embedding. It shows that, after triangle count is held constant, 4-cycle count corresponds almost directly to the leading direction of variation.

The effective ranks near 3 are also notable. Although the raw vectors have 16,384 coordinates, most within-stratum variation occupies only a few effective dimensions. This is consistent with a compact structural organization of the probability spectrum. It does not prove that exactly three graph statistics determine the embedding, but it indicates that the observed geometry is highly constrained.

##### Fixed-triangle and fixed-4-cycle strata

The second stratification exposes the 5-cycle signal. Across all 16 joint strata with at least 12 graphs, the association between embedding distance and 5-cycle-count difference is positive:

\[
\rho \in [0.316,0.926].
\]

Several strata show very strong relationships:

- \((\text{tri}=0,\text{C4}=1)\): \(\rho=0.926\)
- \((1,2)\): \(\rho=0.893\)
- \((0,2)\): \(\rho=0.871\)
- \((1,1)\): \(\rho=0.870\)
- \((2,1)\): \(\rho=0.836\)

These joint strata contain **340 graphs**, approximately **66.8%** of the complete enumeration. Thus, the result is not based on a small exceptional subset.

This resolves the apparently weak global 5-cycle result. Globally, 5-cycle variation is buried beneath triangle and 4-cycle organization. Once both are fixed, 5-cycle count becomes a substantial residual organizing variable.

The resulting interpretation is hierarchical:

\[
\boxed{
\text{triangles}
\;\rightarrow\;
\text{4-cycles}
\;\rightarrow\;
\text{5-cycles}
}
\]

The QuIC probability spectrum appears to organize these cubic graphs lexicographically or onion-like: shorter-cycle structure dominates first, while longer-cycle information remains recoverable in the residual geometry.

## What the experiment establishes

The results provide strong evidence that the QuIC embedding is not merely injective or collision-free. Its metric geometry is meaningfully related to classical graph structure.

More specifically, the experiment establishes that:

1. The sorted probability vector retains substantial local-cycle information despite discarding bitstring identities.
2. The representation distinguishes topology beyond graph order and degree sequence.
3. Short-cycle statistics appear in an ordered hierarchy rather than as an undifferentiated collection of correlated features.
4. Weak marginal correlation can conceal strong conditional structure.
5. The embedding geometry is substantially lower-dimensional than its ambient probability-vector dimension.

This makes the result more interesting than a straightforward cycle-count correlation. The stratification suggests that QuIC has an internally organized structural spectrum.

##### Necessary qualifications

The Mantel tests establish **metric organization**, not direct decodability. They show that differences in cycle counts track embedding distances. They do not demonstrate that a decoder can recover the exact count of each cycle type from a previously unseen embedding. A cross-validated regression or classification experiment would be needed for that stronger wording.

The permutation \(p\)-values have resolution \(1/(10{,}000+1)\). Values printed as 0.0001 are therefore at the Monte Carlo floor. Feeding these floor values into Fisher’s method produces extremely small combined values such as \(10^{-15}\) and \(10^{-40}\), but those numbers imply more precision than the permutation runs provide. The defensible conclusion is overwhelming combined evidence, not the exact reported exponent. More permutations or separate analytical treatment would be needed to emphasize the numerical combined \(p\)-values.

The tests are one-sided. That is appropriate for a prespecified hypothesis that greater cycle-count differences should produce greater embedding distances, but it should be stated explicitly.

The same random seed is reused for each stratum’s permutation test. This does not explain the effect sizes, but independent seed streams would be cleaner when the resulting \(p\)-values are combined using Fisher’s method.

Finally, the study concerns one graph family, one graph size, and one circuit parameterization. It establishes the hierarchy exhaustively for connected cubic graphs at \(n=14\); it does not yet establish that the same hierarchy persists across graph orders, degree distributions, circuit angles, or repetitions.

##### Overall assessment

This is a strong experiment for the claim that QuIC geometry reflects interpretable graph structure. The global test identifies triangle dominance, while the stratified tests reveal that 4- and 5-cycle information survives underneath that dominant axis. The near-perfect PC1 alignment with 4-cycle count is the clearest result.

The appropriate central claim is:

> On the exhaustive set of connected cubic graphs with 14 vertices, QuIC organizes graph space hierarchically by short-cycle structure: triangle count dominates globally, 4-cycle count dominates after conditioning on triangles, and 5-cycle count organizes the remaining geometry after conditioning on both.

That claim is fully supported by the notebook. Claims of universal hierarchy or exact cycle-count decoding would require additional experiments.


#### N16 
Still broken--working on it.

### E2 Ridge Probe
##### Experimental design

This notebook evaluates the structural information contained in the exact QuIC probability vector for the complete connected cubic-graph censuses at two graph orders:

* **509 graphs at (n=14)**;
* **4,060 graphs at (n=16)**.

Each graph is represented by its full sorted probability vector generated using the fixed canonical angles and one circuit repetition:

[
\mathbf p(G)\in\mathbb R^{2^n}.
]

The resulting feature dimensions are:

[
2^{14}=16{,}384,
\qquad
2^{16}=65{,}536.
]

The notebook contains four related analyses:

1. linear decoding of graph invariants from the full QuIC vector;
2. compression through low-order power sums of the QuIC probabilities;
3. decomposition of QuIC geometry into adjacency-spectral and residual components;
4. direct separation of adjacency-cospectral graphs.

All supervised probes use five frozen shuffled folds. The full-vector models use ridge regression with inner cross-validation over the regularization parameter.

Two kinds of moments appear in the notebook and should be distinguished:

* **QuIC probability moments**
  [
  \sum_z p_z^k,
  ]
  used to test whether a few scalar summaries reproduce the information in the full probability vector;

* **adjacency spectral moments**
  [
  \operatorname{tr}(A^k),
  ]
  used to determine how much of QuIC geometry is explained by the classical adjacency spectrum.

##### Full-vector decodability

The first experiment asks whether graph invariants are linearly accessible from the complete sorted QuIC vector.

| Target       | (n=14) QuIC (R^2) | (n=16) QuIC (R^2) |
| ------------ | ----------------: | ----------------: |
| Triangles    |   (1.000\pm0.000) |   (1.000\pm0.000) |
| 4-cycles     |   (0.998\pm0.002) |   (1.000\pm0.000) |
| 5-cycles     |   (0.928\pm0.092) |   (0.982\pm0.015) |
| 6-cycles     |   (0.485\pm0.326) |   (0.642\pm0.122) |
| Girth        |   (0.993\pm0.014) |   (0.999\pm0.003) |
| Diameter     |   (0.548\pm0.058) |   (0.737\pm0.019) |
| Spectral gap |   (0.944\pm0.010) |   (0.932\pm0.007) |

The main pattern is strongly replicated across graph orders.

QuIC predicts triangles and 4-cycles essentially exactly. Five-cycle count is also highly accessible, with performance increasing from

[
R^2=0.928
]

at (n=14) to

[
R^2=0.982
]

at (n=16). The fold variance also decreases substantially, indicating that the weaker (n=14) result was partly a finite-census or split-composition effect.

Girth is nearly perfectly decoded at both graph orders. This is consistent with the strong short-cycle representation: within these cubic censuses, girth is largely determined by the presence or absence of short cycles.

Six-cycle count is substantially weaker. Performance nevertheless improves from

[
R^2=0.485\pm0.326
]

to

[
R^2=0.642\pm0.122.
]

The larger census therefore confirms that 6-cycle information is present, but less directly organized than the shorter-cycle information.

Diameter also improves considerably with scale:

[
0.548\rightarrow0.737.
]

This suggests that the full probability vector contains meaningful global metric information, although diameter remains much less accessible than local cycle structure.

The spectral-gap result remains high but does not improve with graph order. QuIC therefore contains substantial adjacency-spectral information, but it does not reproduce the relevant eigenvalue coordinate exactly under a linear probe.

##### Scaling from (n=14) to (n=16)

The (n=16) census largely strengthens the (n=14) conclusions.

* Triangle and 4-cycle prediction remain effectively exact.
* Five-cycle prediction becomes stronger and substantially more stable.
* Six-cycle prediction improves while remaining the weakest cycle target.
* Diameter prediction rises by approximately (0.19).
* Girth remains almost perfectly accessible.
* Spectral-gap prediction remains near (0.93).

This is important because the (n=14) full-vector feature dimension greatly exceeds the number of graphs. Replication on 4,060 graphs does not remove the high-dimensional setting, but it shows that the central effects are not peculiar to the 509-graph census or a single favorable set of folds.

The hierarchy suggested by the decoding results is

[
C_3,\ C_4
;\rightarrow;
C_5
;\rightarrow;
C_6,
]

with progressively weaker and less stable linear accessibility as cycle length increases.

## QuIC probability power sums

The next experiment tests whether the full-vector results can be reduced to a small number of global probability moments.

Using only

[
\sum_z p_z^2,\qquad
\sum_z p_z^3,\qquad
\sum_z p_z^4,
]

the probe obtains:

| Target    |          (n=14) |          (n=16) |
| --------- | --------------: | --------------: |
| Triangles | (1.000\pm0.000) | (1.000\pm0.000) |
| 4-cycles  | (0.754\pm0.043) | (0.750\pm0.022) |
| 5-cycles  | (0.064\pm0.066) | (0.056\pm0.008) |

Triangle count is therefore almost entirely encoded by the lowest probability moments. Four-cycle count is partially recoverable from the first three power sums, while 5-cycle count is almost completely absent from this compressed representation.

The nested power-sum ladder sharpens the result.

###### (n=14) power-sum ladder

| Moments included | Triangles | 4-cycles | 5-cycles | 6-cycles |
| ---------------- | --------: | -------: | -------: | -------: |
| Through (k=2)    |     0.999 |    0.001 |    0.022 |    0.144 |
| Through (k=3)    |     1.000 |    0.677 |    0.066 |    0.184 |
| Through (k=4)    |     1.000 |    0.755 |    0.069 |    0.182 |
| Through (k=5)    |     1.000 |    0.997 |    0.045 |    0.189 |
| Through (k=8)    |     1.000 |    0.997 |    0.106 |    0.198 |

###### (n=16) power-sum ladder

| Moments included | Triangles | 4-cycles | 5-cycles | 6-cycles |
| ---------------- | --------: | -------: | -------: | -------: |
| Through (k=2)    |     0.999 |    0.003 |    0.024 |    0.100 |
| Through (k=3)    |     1.000 |    0.691 |    0.056 |    0.142 |
| Through (k=4)    |     1.000 |    0.752 |    0.058 |    0.143 |
| Through (k=5)    |     1.000 |    0.998 |    0.060 |    0.146 |
| Through (k=8)    |     1.000 |    0.998 |    0.084 |    0.144 |

The same transition occurs at both graph orders:

[
\text{4-cycle information saturates when }
\sum_z p_z^5
\text{ is added}.
]

This replication indicates that the (k=5) transition is structural rather than an (n=14) anomaly.

In contrast, neither 5-cycle nor 6-cycle count is recovered by probability power sums through degree eight. Their best ladder scores remain near (0.10) and (0.20), far below the corresponding full-vector scores.

The complete sorted probability vector therefore contains information that is discarded by low-order global moments.

##### Quadratic interaction check for 5-cycles

A degree-two polynomial model was applied to the first four probability power sums:

[
\sum_z p_z^2,\ldots,\sum_z p_z^5.
]

The resulting 5-cycle scores are:

[
R^2=0.143\pm0.103
\quad\text{at }n=14,
]

and

[
R^2=0.132\pm0.015
\quad\text{at }n=16.
]

The strong full-vector 5-cycle result is therefore not explained by a simple quadratic interaction among the low-order moments.

The correct conclusion is not that 5-cycle information is absent from all symmetric functions of the probability vector. A sufficiently rich collection of moments can recover a finite probability multiset. The result is narrower:

> Five-cycle information is carried by finer probability-spectrum structure that is not captured by moments through degree eight or by quadratic interactions among the first four moments.

##### Principal-component decomposition

The notebook next decomposes the centered QuIC vectors using singular-value decomposition and asks how well the leading principal components can be reconstructed from:

* triangle, 4-cycle, and 5-cycle counts;
* adjacency moments (\operatorname{tr}(A^k)), (k=3,\ldots,8);
* the complete nonconstant adjacency spectrum;
* adjacency moments concatenated with the three cycle counts.

###### (n=14)

| Component | Variance | Cycle (R^2) | Moment (R^2) | Full-spectrum (R^2) |
| --------- | -------: | ----------: | -----------: | ------------------: |
| PC1       |    51.2% |       0.962 |        0.962 |               0.954 |
| PC2       |    15.3% |      -0.002 |        0.060 |               0.195 |
| PC3       |     7.8% |       0.128 |        0.119 |               0.097 |
| PC4       |     7.7% |       0.802 |        0.811 |               0.809 |
| PC5       |     5.3% |      -0.014 |       -0.017 |               0.010 |
| PC6       |     2.6% |      -0.033 |       -0.040 |              -0.065 |

###### (n=16)

| Component | Variance | Cycle (R^2) | Moment (R^2) | Full-spectrum (R^2) |
| --------- | -------: | ----------: | -----------: | ------------------: |
| PC1       |    50.7% |       0.957 |        0.958 |               0.957 |
| PC2       |    15.1% |       0.021 |        0.052 |               0.275 |
| PC3       |     8.4% |       0.013 |        0.013 |               0.016 |
| PC4       |     7.6% |       0.923 |        0.933 |               0.927 |
| PC5       |     5.5% |       0.003 |        0.010 |               0.076 |
| PC6       |     2.4% |      -0.004 |       -0.000 |               0.016 |

The first and fourth components form a clear spectral backbone.

PC1 accounts for approximately half of the total QuIC variance and is almost completely predicted by either short-cycle counts or adjacency moments. PC4 accounts for another (7.6%)–(7.7%) and is also strongly spectral.

Together, these two components account for approximately

[
59%
]

of the total embedding variance.

PC2 behaves differently. It contains approximately (15%) of the total variance but is poorly explained by short-cycle counts or the first six adjacency moments:

[
R^2_{\mathrm{moments}}=0.060
\quad\text{at }n=14,
]

and

[
R^2_{\mathrm{moments}}=0.052
\quad\text{at }n=16.
]

The full adjacency spectrum explains more:

[
R^2_{\mathrm{spectrum}}=0.195
\quad\text{and}\quad
0.275,
]

but most of PC2 remains unexplained.

PC3, PC5, and PC6 are also weakly related to the tested spectral and cycle features. These components are individually smaller, but together with PC2 they show that the QuIC representation is not exhausted by its dominant spectral axis.

A variance-weighted aggregation across the first six components attributes approximately:

* (57%) of total QuIC variance to the six adjacency moments at both graph orders;
* (59%) at (n=14) and (60%) at (n=16) to the complete adjacency spectrum.

The representation therefore has a large and stable spectral backbone, but a substantial residual component remains.

## Six-cycle contribution to PC2

Six-cycle count alone does not predict PC2:

[
R^2=-0.028
\quad\text{at }n=14,
]

and

[
R^2=-0.003
\quad\text{at }n=16.
]

After the adjacency moments are included, however, adding 6-cycle count raises the PC2 score from

[
0.060\rightarrow0.210
]

at (n=14), and from

[
0.052\rightarrow0.158
]

at (n=16).

Thus, the useful 6-cycle signal is conditional rather than marginal. Six-cycle count becomes informative only after the dominant spectral component has been accounted for.

This is consistent with the later residual-probe result: the spectrum strongly constrains 6-cycle count, while QuIC retains information about the remaining non-spectral division between 6-cycles and diamonds.

The PC2 result should nevertheless be treated as suggestive rather than definitive. Most of PC2 remains unexplained even after 6-cycle count is included.

##### Adjacency-cospectral graphs

The strongest direct test asks whether QuIC distinguishes graphs having exactly the same adjacency spectrum.

Spectrum hashing identifies:

* **3 cospectral groups and 3 pairs at (n=14)**;
* **41 cospectral groups and 43 pairs at (n=16)**.

The (n=14) analysis recovers the three expected pairs:

[
(79,458),\qquad
(201,203),\qquad
(234,239).
]

Every discovered cospectral pair has a nonzero QuIC separation.

At (n=14), the full-vector (L_1) distances range from

[
5.87\times10^{-8}
]

to

[
1.69\times10^{-5}.
]

At (n=16), the distances range from

[
1.92\times10^{-8}
]

to

[
1.68\times10^{-5}.
]

Because adjacency-cospectral graphs have identical classical spectra, these separations demonstrate that the ideal QuIC probability vector is not a function of the adjacency spectrum alone.

This is the notebook's cleanest direct evidence for a non-spectral component.

## Why the global percentiles are small

Relative to all graph pairs, the cospectral separations occupy low percentiles.

At (n=14), the three global percentiles are approximately:

[
0.00077,\qquad
0.0611,\qquad
5.817.
]

At (n=16), the global percentiles range from approximately zero to

[
6.324.
]

This does not contradict the existence of non-spectral information. Arbitrary graph pairs differ along the dominant triangle, 4-cycle, and adjacency-spectral axes. Cospectral pairs have all of those major differences removed and therefore occupy a much smaller distance scale.

The global pairwise distribution is consequently not the most informative reference class for cospectral mates.

## Count-identical reference class

A more appropriate comparison restricts the reference population to graph pairs with identical

[
(C_3,C_4,C_5)
]

counts.

This produces:

* **715 count-identical pairs at (n=14)**;
* **52,181 count-identical pairs at (n=16)**.

For the full (n=14) vectors, the three cospectral pairs lie at approximately the:

[
0.0\text{th},\qquad
10.9\text{th},\qquad
92.7\text{th}
]

percentiles of this count-identical reference class.

Thus, one cospectral pair is among the most strongly separated count-identical pairs, one is modestly separated, and one is extremely close.

At (n=16), the 43 full-vector percentiles range from approximately

[
0
]

to

[
92.0,
]

with median approximately

[
11.7.
]

Of the 43 pairs:

* 19 lie at or above the 25th percentile;
* 4 lie near or above the 90th percentile;
* 20 lie below the 5th percentile.

The non-spectral separation is therefore heterogeneous. QuIC distinguishes all discovered cospectral pairs in exact simulation, but many differences are small, while a minority are large even relative to graphs already matched on the first three cycle counts.

This distinction matters:

* **nonzero separation** establishes that QuIC is not spectrally determined;
* **high reference-class percentile** establishes that the non-spectral difference is geometrically substantial.

The notebook provides both, but not for every pair.

##### Truncation behavior

The truncation experiment evaluates only the largest (k) entries of the sorted probability vector.

At (n=14), reducing the representation to its first 25–100 probabilities increases the relative standing of two of the three cospectral pairs. For example, pair ((201,203)) rises from approximately the 5.82nd global percentile using the full vector to:

[
18.30
]

at (k=50).

At (n=16), the four most strongly separated full-vector pairs lie near the 92nd percentile of the count-identical class. These same pairs remain near the 93rd percentile at (k=100).

Relative to all graph pairs, their percentiles rise from approximately

[
6.2\text{--}6.3
]

for the full vector to approximately

[
20.5
]

at (k=50).

This indicates that the strongest cospectral residue is concentrated disproportionately in the head of the sorted probability distribution. The effect is not uniform across all pairs, but the largest non-spectral separations do not require the full (2^n)-dimensional tail.

##### What the experiment establishes

The combined results support five main conclusions.

1. **Graph invariants are strongly linearly accessible from the full QuIC vector.**
   Triangle count, 4-cycle count, 5-cycle count, girth, and spectral gap are predicted with high accuracy at both graph orders.

2. **The decodability hierarchy is stable with scale.**
   Short cycles are easiest, 5-cycles remain strong, and 6-cycles form a weaker fourth layer.

3. **Low-order probability moments do not explain the full-vector results.**
   They recover triangles and 4-cycles, but fail to recover the strong full-vector 5-cycle signal or most of the 6-cycle signal.

4. **QuIC has a dominant classical spectral backbone.**
   PC1 and PC4, accounting for approximately (59%) of total variance, are almost completely explained by adjacency spectral quantities.

5. **QuIC also contains a reproducible non-spectral residue.**
   PC2 and several smaller components are weakly spectral, and every discovered adjacency-cospectral pair is separated by the exact QuIC vector.

The appropriate interpretation is not that QuIC is unrelated to classical spectral graph theory. Most of its leading geometry is spectral. The stronger result is that the representation contains both:

[
\boxed{
\text{a dominant spectral backbone}
+
\text{a smaller non-spectral residue}
}
]

##### Necessary qualifications

The ridge results demonstrate linear decodability, not that the corresponding graph invariant is uniquely represented along a single embedding direction.

The full vectors are extremely high-dimensional relative to the graph censuses. Five-fold testing and replication at (n=16) reduce the risk of a purely in-sample artifact, but the near-floor selected regularization parameters indicate a near-interpolating regime.

The experiments use exact noiseless probability vectors at one fixed circuit depth and one canonical angle configuration. Very small cospectral distances may not remain resolvable under finite-shot sampling or hardware noise.

Cospectral groups are identified by adjacency eigenvalues rounded to eight decimal places. The known (n=14) pairs provide a regression check, but a formal exact-cospectrality claim should ultimately be verified using characteristic polynomials or exact algebraic invariants.

The probability-moment experiment only tests powers through (k=8) and one degree-two interaction model. It establishes failure of low-order compression, not failure of all possible symmetric summaries.

The PCA analysis is descriptive. The principal axes are fitted to each complete census before the spectral probes are evaluated, so the reported component decomposition should be interpreted as an analysis of the observed geometry rather than as an independently fitted out-of-sample representation.

Finally, ideal-state separation of cospectral graphs establishes non-spectral information but does not by itself establish that the information is useful for a downstream task. The residual-probe experiment supplies the stronger functional result for diamond and 6-cycle prediction.

## Overall assessment

The (n=16) replication materially strengthens the earlier (n=14) findings.

The full QuIC vector preserves an exceptionally strong hierarchy of local graph structure. Triangle and 4-cycle counts are essentially exact, 5-cycle prediction becomes more stable at the larger graph order, and weaker 6-cycle and diameter signals improve with census size.

The representation is not reducible to a handful of probability moments. Its leading geometry is nevertheless substantially classical: approximately (59%) of total variance lies in two principal directions that are strongly explained by adjacency spectral quantities.

Beyond that backbone, QuIC retains additional structure. The weakly spectral PC2 replicates at both graph orders, conditional 6-cycle information appears within it, and all 46 discovered cospectral pairs across the two censuses receive distinct ideal QuIC vectors.

The appropriate central claim is:

> Across the complete connected cubic-graph censuses at (n=14) and (n=16), QuIC exhibits a stable spectral backbone together with a reproducible non-spectral residue. Its dominant components encode short-cycle and adjacency-spectral structure, while finer probability-spectrum information supports strong 5-cycle decoding, conditional 6-cycle information, and separation of every discovered adjacency-cospectral pair.


### E2S - Spectral Baseline
##### Experimental design

This notebook asks whether QuIC predicts graph properties that are not already recoverable from the adjacency spectrum.

The experiment uses the complete connected cubic-graph censuses at two orders:

- **509 graphs at \(n=14\)**
- **4,060 graphs at \(n=16\)**

Four feature representations are compared using the same five frozen train/test folds and the same ridge-regression protocol:

1. **QuIC:** the full sorted probability vector from the original E2 experiment.
2. **Eigenvalues:** the sorted adjacency eigenvalues, excluding the constant Perron eigenvalue \(\lambda_{\max}=3\).
3. **Spectral moments:**  
   \[
   \operatorname{tr}(A^k), \qquad k=3,\ldots,8.
   \]
4. **QuIC + spectrum:** the QuIC vector concatenated with the eigenvalue and moment features.

The seven prediction targets are:

- triangle count,
- 4-cycle count,
- 5-cycle count,
- 6-cycle count,
- girth,
- diameter,
- spectral gap.

The spectral-only features are standardized. In the concatenated representation, QuIC remains raw, while the spectral block is rescaled within each training fold to have the same root-mean-square magnitude as the QuIC block.

The primary comparison is

\[
\Delta R^2
=
R^2_{\text{QuIC+spec}}
-
\max\left(
R^2_{\text{eigenvalues}},
R^2_{\text{moments}}
\right).
\]

A positive value indicates that the combined representation predicts better than either linear spectral representation alone.

## Spectral identity checks

For cubic graphs, the first three cycle-count targets are exact linear functions of adjacency moments:

\[
C_3=\frac{\operatorname{tr}(A^3)}{6},
\]

\[
C_4=\frac{\operatorname{tr}(A^4)-15n}{8},
\]

and

\[
C_5=
\frac{
\operatorname{tr}(A^5)-10\operatorname{tr}(A^3)
}{10}.
\]

The notebook verifies these identities exactly across all 509 graphs at \(n=14\) and all 4,060 graphs at \(n=16\).

These checks serve two purposes:

- They confirm that the graph statistics and spectra were computed consistently.
- They provide positive controls for the linear-probe protocol.

As expected, the moment representation obtains \(R^2=1.000\) for triangle, 4-cycle, and 5-cycle counts at both graph orders.

## Main results

The reported values are mean \(R^2\) with standard deviation across the five frozen folds.

###### \(n=14\)

| Target | QuIC | Eigenvalues | Moments | QuIC + spectrum | \(\Delta R^2\) |
|---|---:|---:|---:|---:|---:|
| Triangles | \(1.000\pm0.000\) | \(0.987\pm0.004\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) | \(-0.000\) |
| 4-cycles | \(0.998\pm0.002\) | \(0.972\pm0.004\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) | \(-0.000\) |
| 5-cycles | \(0.928\pm0.092\) | \(0.905\pm0.013\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) | \(-0.000\) |
| 6-cycles | \(0.485\pm0.326\) | \(0.842\pm0.059\) | \(0.983\pm0.005\) | \(1.000\pm0.000\) | \(+0.017\) |
| Girth | \(0.993\pm0.014\) | \(0.611\pm0.100\) | \(0.376\pm0.045\) | \(0.993\pm0.014\) | \(+0.382\) |
| Diameter | \(0.548\pm0.058\) | \(0.560\pm0.049\) | \(0.711\pm0.012\) | \(0.741\pm0.030\) | \(+0.030\) |
| Spectral gap | \(0.944\pm0.010\) | \(1.000\pm0.000\) | \(0.871\pm0.032\) | \(1.000\pm0.000\) | \(-0.000\) |

###### \(n=16\)

| Target | QuIC | Eigenvalues | Moments | QuIC + spectrum | \(\Delta R^2\) |
|---|---:|---:|---:|---:|---:|
| Triangles | \(1.000\pm0.000\) | \(0.989\pm0.001\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) | \(-0.000\) |
| 4-cycles | \(1.000\pm0.000\) | \(0.974\pm0.002\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) | \(-0.000\) |
| 5-cycles | \(0.982\pm0.015\) | \(0.918\pm0.009\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) | \(-0.000\) |
| 6-cycles | \(0.642\pm0.122\) | \(0.857\pm0.009\) | \(0.983\pm0.001\) | \(1.000\pm0.000\) | \(+0.017\) |
| Girth | \(0.999\pm0.003\) | \(0.543\pm0.042\) | \(0.382\pm0.020\) | \(0.999\pm0.003\) | \(+0.456\) |
| Diameter | \(0.737\pm0.019\) | \(0.657\pm0.006\) | \(0.775\pm0.016\) | \(0.802\pm0.014\) | \(+0.026\) |
| Spectral gap | \(0.932\pm0.007\) | \(1.000\pm0.000\) | \(0.865\pm0.005\) | \(1.000\pm0.000\) | \(-0.000\) |

##### Eigenvalues versus spectral moments

The comparison between eigenvalues and moments illustrates that linear-probe performance depends strongly on the coordinates used to express the same spectral information.

The sorted eigenvalue representation performs well but not perfectly on short-cycle counts:

\[
R^2\approx0.91\text{--}0.99.
\]

This is expected because cycle counts are power sums of the eigenvalues. They are spectral functions, but they are not linear functions of the individual sorted eigenvalue coordinates.

In contrast, the moment representation contains those power sums directly and therefore recovers triangle, 4-cycle, and 5-cycle counts exactly.

The reverse occurs for the spectral gap. For a connected cubic graph,

\[
\lambda_{\max}=3,
\qquad
\text{gap}=3-\lambda_2.
\]

The spectral gap is therefore an exact linear function of a sorted eigenvalue coordinate. The eigenvalue probe obtains \(R^2=1.000\), while the moment representation reaches only approximately \(0.87\).

This establishes an important methodological point: poor performance from a linear model on sorted eigenvalues does not imply that a target is non-spectral. It may instead mean that the target is nonlinear in those particular spectral coordinates.

## Short-cycle counts

The results for triangles, 4-cycles, and 5-cycles behave exactly as expected.

The moment representation recovers all three perfectly because the relevant identities are built into the feature coordinates. QuIC also performs strongly:

- exact or nearly exact prediction for triangles and 4-cycles,
- \(R^2=0.928\) at \(n=14\) and \(0.982\) at \(n=16\) for 5-cycles.

The lower and more variable \(n=14\) 5-cycle result suggests that the finite census or fold composition makes this target less stable at the smaller graph order. The larger census produces substantially stronger and more consistent prediction.

The concatenated representation provides no improvement because the spectral moments already solve these targets exactly.

These rows therefore confirm that QuIC contains the same short-cycle structure identified in the stratified-distance experiment, but they do not identify information beyond the adjacency spectrum.

##### Six-cycle count

The 6-cycle row is the most striking interaction result.

QuIC alone predicts 6-cycle count relatively poorly:

\[
R^2=0.485\pm0.326
\quad\text{at }n=14,
\]

and

\[
R^2=0.642\pm0.122
\quad\text{at }n=16.
\]

The spectral moment representation is already very strong:

\[
R^2=0.983
\]

at both graph orders.

Nevertheless, concatenating QuIC with the spectral features raises the reported score to \(1.000\pm0.000\), giving

\[
\Delta R^2=+0.017
\]

at both \(n=14\) and \(n=16\).

The replication of the same gain across two complete graph censuses is notable. It indicates that QuIC contains information or transformed structure that complements the linear spectral coordinates used by the baseline.

The result is better interpreted as **complementarity** than as strong standalone 6-cycle decoding. QuIC by itself is not a competitive 6-cycle predictor, particularly at \(n=14\). Its contribution becomes useful only when combined with the spectral representation.

##### Girth

QuIC predicts girth almost perfectly:

\[
R^2=0.993\pm0.014
\quad\text{at }n=14,
\]

and

\[
R^2=0.999\pm0.003
\quad\text{at }n=16.
\]

The linear spectral baselines are much weaker. The best spectral score is only \(0.611\) at \(n=14\) and \(0.543\) at \(n=16\).

This produces the largest nominal improvements:

\[
\Delta R^2=+0.382
\quad\text{and}\quad
+0.456.
\]

However, these large values should not be interpreted as evidence that girth is non-spectral. Within these censuses, girth is determined by the presence or absence of short cycles and is therefore a nonlinear threshold function of spectrally determined cycle counts.

The girth result instead shows that QuIC provides a coordinate system in which this nonlinear spectral property is nearly linearly accessible. The concatenated model does not improve on QuIC; it simply retains QuIC's near-perfect score.

This is strong evidence for favorable representation geometry, but not for information absent from the spectrum.

##### Diameter

Diameter is the clearest open structural target.

At \(n=14\):

\[
R^2_{\text{QuIC}}=0.548,
\qquad
R^2_{\text{moments}}=0.711,
\qquad
R^2_{\text{combined}}=0.741.
\]

At \(n=16\):

\[
R^2_{\text{QuIC}}=0.737,
\qquad
R^2_{\text{moments}}=0.775,
\qquad
R^2_{\text{combined}}=0.802.
\]

The resulting improvements are modest but consistent:

\[
\Delta R^2=+0.030
\quad\text{at }n=14,
\]

and

\[
\Delta R^2=+0.026
\quad\text{at }n=16.
\]

Unlike girth, the combined representation outperforms both QuIC and the spectral baselines. The replication across graph orders supports the presence of complementary structural information.

The absolute gains are small, however, and no fold-level uncertainty or paired significance test is reported for \(\Delta R^2\). The appropriate conclusion is that the combined representation provides a consistent predictive improvement, not that a large independent diameter signal has been established.

##### Spectral gap

The spectral-gap row acts as another positive control.

The sorted-eigenvalue representation obtains perfect prediction because the target is explicitly a linear function of the two largest adjacency eigenvalues. QuIC reaches approximately \(R^2=0.93\text{--}0.94\), demonstrating that it captures substantial spectral information but does not reproduce the relevant eigenvalue coordinate exactly under a linear probe.

The concatenated model returns to perfect prediction because the exact spectral feature is present. There is no improvement beyond the spectral baseline.

This result argues against treating QuIC as a simple replacement for the adjacency spectrum. Its representation emphasizes some structural quantities while making other explicitly spectral quantities less directly accessible.

##### What the experiment establishes

The experiment supports several conclusions.

1. **QuIC contains substantial spectral and short-cycle information.**  
   Its full probability vector linearly predicts triangles, 4-cycles, 5-cycles, girth, and spectral gap with high accuracy.

2. **QuIC is not equivalent to sorted adjacency eigenvalues under a linear probe.**  
   It is much better for girth, but worse for spectral gap and 6-cycle count.

3. **Feature parameterization matters.**  
   Eigenvalues and spectral moments contain closely related information, yet their linear-probe performance differs substantially depending on the target.

4. **QuIC and spectral features are complementary for 6-cycle count and diameter.**  
   The combined representation consistently outperforms the stronger spectral baseline at both graph orders.

5. **The complementarity is reproducible.**  
   The same qualitative pattern appears in both the \(n=14\) and \(n=16\) complete censuses.

The experiment therefore strengthens the interpretation of QuIC as a structurally organized representation rather than merely an injective graph identifier.

##### Necessary qualifications

The central limitation is that positive

\[
\Delta R^2
\]

does not, by itself, prove that QuIC contains non-spectral information.

The spectral baselines are linear models on two specific coordinate systems. QuIC may provide nonlinear transformations of information that is already determined by the spectrum. The girth result demonstrates this directly: QuIC dramatically outperforms the linear spectral baselines even though girth is spectrally determined within these graph censuses.

Consequently, the 6-cycle and diameter improvements establish that QuIC adds information useful beyond these **linear spectral probes**, but not necessarily information absent from the full adjacency spectrum.

A stronger non-spectral claim would require at least one of the following:

- analysis restricted to adjacency-cospectral graph classes,
- examples of cospectral graphs with different target values that QuIC separates,
- prediction of target residuals after a sufficiently expressive nonlinear spectral model,
- or a direct conditional test showing that QuIC varies meaningfully when the complete spectrum is fixed.

The notebook also reports no paired uncertainty estimate for the differences in \(R^2\). Because every method uses the same frozen folds, the foldwise score differences could be analyzed directly. This would clarify whether the \(+0.017\), \(+0.030\), and \(+0.026\) gains are stable across folds rather than driven by one split.

The concatenated model also has far higher dimensionality than either spectral baseline, especially at \(n=16\). The comparison is valid as a predictive test, but the improvement may reflect both additional information and a richer transformed feature basis.

Finally, scores printed as \(1.000\pm0.000\) are exact only to the displayed precision unless separately guaranteed by an algebraic identity. Exact recoverability is established for \(C_3\), \(C_4\), and \(C_5\); the reported combined 6-cycle result should be described as numerically perfect or perfect to displayed precision.

##### Overall assessment

This notebook provides a useful classical baseline and materially sharpens the interpretation of the QuIC probe results.

The spectral controls behave correctly:

- moments exactly recover \(C_3\), \(C_4\), and \(C_5\);
- sorted eigenvalues exactly recover spectral gap;
- the difference between eigenvalue and moment probes exposes the importance of feature coordinates.

Against these controls, QuIC shows two distinct behaviors.

First, it makes some nonlinear structural properties, particularly girth, almost linearly accessible. Second, it provides small but repeatable improvements when combined with spectral features for 6-cycle count and diameter.

The appropriate central claim is:

> Across the complete connected cubic-graph censuses at \(n=14\) and \(n=16\), QuIC is neither reducible to nor uniformly stronger than a linear adjacency-spectral representation. It provides a different structural coordinate system: one that makes girth highly accessible and adds reproducible predictive value to spectral features for 6-cycle count and diameter.

The notebook supports complementarity beyond linear spectral baselines. A claim of genuinely non-spectral information requires the planned cospectral or conditional-residual analysis.


### E2R - Residual Probe [Partial Results]

##### Experimental design

This experiment tests whether QuIC contains functionally useful information beyond a linear adjacency-spectral representation.

The spectral representation contains:

* the sorted adjacency eigenvalues, excluding the constant cubic-graph eigenvalue (\lambda_{\max}=3);
* the spectral moments
  [
  \operatorname{tr}(A^k), \qquad k=3,\ldots,8.
  ]

Each target is evaluated using the same five frozen outer folds used in the earlier ridge-probe experiment. Within each outer fold, prediction proceeds in two stages:

1. A standardized spectral ridge model is fitted on the training fold.
2. Cross-fitted spectral predictions are generated for the training points using five inner folds.
3. The difference between each observed target and its cross-fitted spectral prediction becomes the residual target.
4. A second ridge model learns those residuals from the raw QuIC probability vectors.
5. The final prediction is
   [
   \hat y_{\mathrm{two-stage}}
   ===========================

   \hat y_{\mathrm{spectrum}}
   +
   \hat r_{\mathrm{QuIC}}.
   ]

The primary statistic is

[
\Delta R^2
==========

##### R^2_{\mathrm{two-stage}}

R^2_{\mathrm{spectrum}}.
]

A positive value indicates that QuIC predicts variation missed by the linear spectral model.

The experiment also reports residual-space (R^2):

[
R^2_{\mathrm{residual}}
=======================

R^2
\left(
y-\hat y_{\mathrm{spectrum}},
\hat r_{\mathrm{QuIC}}
\right).
]

This measures QuIC's ability to predict the spectral model's remaining error directly.

##### Available results

The (n=14) run completed all eleven targets. The (n=16) run completed through the diamonds target before the notebook timed out.

###### Complete (n=14) results

| Target       |      QuIC alone |        Spectrum |       Two-stage |    (\Delta R^2) |  Residual (R^2) |          |          |
| ------------ | --------------: | --------------: | --------------: | --------------: | --------------: | -------- | -------- |
| Triangles    | (1.000\pm0.000) | (1.000\pm0.000) | (1.000\pm0.000) |        (+0.000) |        (-0.042) |          |          |
| 4-cycles     | (0.998\pm0.002) | (1.000\pm0.000) | (1.000\pm0.000) |        (+0.000) |        (-0.034) |          |          |
| 5-cycles     | (0.928\pm0.092) | (1.000\pm0.000) | (1.000\pm0.000) |        (+0.000) |        (-0.066) |          |          |
| 6-cycles     | (0.485\pm0.326) | (0.985\pm0.003) | (0.994\pm0.002) |        (+0.008) |        (+0.533) |          |          |
| Girth        | (0.993\pm0.014) | (0.686\pm0.072) | (0.907\pm0.030) |        (+0.221) |        (+0.701) |          |          |
| Diameter     | (0.548\pm0.058) | (0.744\pm0.030) | (0.744\pm0.030) |        (-0.000) |        (-0.009) |          |          |
| Spectral gap | (0.944\pm0.010) | (1.000\pm0.000) | (1.000\pm0.000) |        (+0.000) |        (-0.043) |          |          |
| Diamonds     | (0.993\pm0.003) | (0.585\pm0.032) | (0.927\pm0.090) |        (+0.341) |        (+0.827) |          |          |
| Radius       | (0.164\pm0.128) | (0.345\pm0.081) | (0.344\pm0.096) |        (-0.000) |        (-0.001) |          |          |
| Wiener index | (0.832\pm0.151) | (0.973\pm0.006) | (0.961\pm0.021) |        (-0.012) |        (-0.438) |          |          |
| (\log_2      | \mathrm{Aut}(G) |               ) | (0.438\pm0.067) | (0.678\pm0.027) | (0.684\pm0.025) | (+0.006) | (-0.003) |

###### Partial (n=16) results

| Target       |      QuIC alone |        Spectrum |       Two-stage | (\Delta R^2) | Residual (R^2) |
| ------------ | --------------: | --------------: | --------------: | -----------: | -------------: |
| Triangles    | (1.000\pm0.000) | (1.000\pm0.000) | (1.000\pm0.000) |     (+0.000) |       (-0.890) |
| 4-cycles     | (1.000\pm0.000) | (1.000\pm0.000) | (1.000\pm0.000) |     (+0.000) |       (-0.159) |
| 5-cycles     | (0.982\pm0.015) | (1.000\pm0.000) | (1.000\pm0.000) |     (+0.000) |       (-1.911) |
| 6-cycles     | (0.642\pm0.122) | (0.985\pm0.002) | (0.997\pm0.000) |     (+0.012) |       (+0.808) |
| Girth        | (0.999\pm0.003) | (0.635\pm0.041) | (0.938\pm0.008) |     (+0.303) |       (+0.829) |
| Diameter     | (0.737\pm0.019) | (0.789\pm0.014) | (0.802\pm0.015) |     (+0.014) |       (+0.062) |
| Spectral gap | (0.932\pm0.007) | (1.000\pm0.000) | (1.000\pm0.000) |     (+0.000) |       (-4.766) |
| Diamonds     | (0.996\pm0.004) | (0.636\pm0.032) | (0.947\pm0.009) |     (+0.310) |       (+0.854) |

##### Protocol checks

Triangles, 4-cycles, 5-cycles, and spectral gap behave as expected.

The spectral representation predicts each of these targets perfectly:

[
R^2_{\mathrm{spectrum}}=1.000.
]

Adding a QuIC residual model therefore produces no improvement:

[
\Delta R^2=0.
]

The negative residual-space values on these rows are not evidence that QuIC systematically loses structural information. The spectral model has already reduced the residual target to approximately numerical or regularization noise. When the residual variance is nearly zero, residual-space (R^2) becomes unstable and can take strongly negative values, as seen for the (n=16) spectral-gap row.

These rows confirm that the cross-fitting and two-stage machinery do not manufacture an improvement when the spectral stage already solves the target.

##### Diamond count

Diamond count provides the strongest result.

At (n=14),

[
R^2_{\mathrm{spectrum}}=0.585\pm0.032,
]

while the two-stage model reaches

[
R^2_{\mathrm{two-stage}}=0.927\pm0.090.
]

This gives

[
\Delta R^2=+0.341
]

and

[
R^2_{\mathrm{residual}}=0.827.
]

The same result appears at (n=16):

[
R^2_{\mathrm{spectrum}}=0.636\pm0.032,
]

[
R^2_{\mathrm{two-stage}}=0.947\pm0.009,
]

[
\Delta R^2=+0.310,
]

and

[
R^2_{\mathrm{residual}}=0.854.
]

QuIC alone also predicts diamond count almost perfectly:

[
R^2_{\mathrm{QuIC}}=0.993
\quad\text{at }n=14,
]

and

[
R^2_{\mathrm{QuIC}}=0.996
\quad\text{at }n=16.
]

This result is especially important because the sixth spectral moment obeys the cubic-graph identity

[
\operatorname{tr}(A^6)
======================

12(C_6+D)
+
87n
+
6C_3
+
96C_4,
]

where (C_6) is the number of 6-cycles and (D) is the number of diamonds.

The spectrum therefore determines the sum

[
C_6+D,
]

but does not generally determine how that sum is divided between 6-cycles and diamonds.

The diamond result shows that QuIC can predict this unresolved component. It is not merely supplying a more convenient linearization of a spectrally fixed quantity. It is recovering graph variation that remains after conditioning on the spectral representation.

The replication at both (n=14) and (n=16) makes this the clearest functional evidence for non-spectral information in the QuIC embedding.

## Six-cycle count

The 6-cycle results complement the diamond findings.

At (n=14),

[
R^2_{\mathrm{spectrum}}=0.985\pm0.003,
]

and the two-stage model reaches

[
R^2_{\mathrm{two-stage}}=0.994\pm0.002.
]

At (n=16),

[
R^2_{\mathrm{spectrum}}=0.985\pm0.002,
]

and the two-stage score rises to

[
R^2_{\mathrm{two-stage}}=0.997\pm0.000.
]

The total gains are numerically small:

[
\Delta R^2=+0.008
\quad\text{at }n=14,
]

and

[
\Delta R^2=+0.012
\quad\text{at }n=16.
]

However, the residual-space results are substantial:

[
R^2_{\mathrm{residual}}=0.533
\quad\text{at }n=14,
]

and

[
R^2_{\mathrm{residual}}=0.808
\quad\text{at }n=16.
]

These two observations are compatible. The spectral model already explains approximately (98.5%) of the total 6-cycle variance, leaving only a small residual component. QuIC predicts a substantial fraction of that residual, but the residual itself represents only a small fraction of the total target variance.

The improvement is therefore small in total (R^2) but strong when evaluated specifically on the variation the spectrum misses.

The relation between 6-cycles and diamonds supplies a structural explanation. Because the spectrum constrains (C_6+D), information about diamonds also provides information about the unresolved 6-cycle component.

The 6-cycle and diamond rows should therefore be interpreted jointly:

* the spectrum predicts their constrained sum;
* QuIC predicts how that sum is divided;
* the residual probe detects this division in both directions.

##### Girth

QuIC also predicts the residuals of the linear spectral model for girth.

At (n=14),

[
R^2_{\mathrm{spectrum}}=0.686\pm0.072,
]

while the two-stage model reaches

[
R^2_{\mathrm{two-stage}}=0.907\pm0.030.
]

At (n=16),

[
R^2_{\mathrm{spectrum}}=0.635\pm0.041,
]

while the two-stage result is

[
R^2_{\mathrm{two-stage}}=0.938\pm0.008.
]

The improvements are large:

[
\Delta R^2=+0.221
\quad\text{at }n=14,
]

and

[
\Delta R^2=+0.303
\quad\text{at }n=16.
]

Residual-space performance is similarly strong:

[
R^2_{\mathrm{residual}}=0.701
\quad\text{and}\quad
0.829.
]

QuIC alone remains stronger than the two-stage model, reaching approximately perfect prediction at both graph orders. This indicates that QuIC provides a coordinate system in which girth is especially accessible.

The girth result should not be treated as clean evidence of non-spectral information. Within these cubic-graph censuses, girth is determined by the presence or absence of short cycles. It is therefore a nonlinear function of cycle information already encoded by the spectrum.

The result instead demonstrates that QuIC recovers nonlinear structural information missed by a linear spectral ridge model. It is evidence for representational advantage, rather than evidence that girth itself is not spectrally determined.

## Diameter

The diameter results are weak and inconsistent across the two available orders.

At (n=14), the two-stage model does not improve on the spectral baseline:

[
\Delta R^2\approx0,
\qquad
R^2_{\mathrm{residual}}=-0.009.
]

At (n=16), there is a small improvement:

[
R^2_{\mathrm{spectrum}}=0.789\pm0.014,
]

[
R^2_{\mathrm{two-stage}}=0.802\pm0.015,
]

and

[
\Delta R^2=+0.014.
]

The residual-space score is only

[
R^2_{\mathrm{residual}}=0.062.
]

This is not strong evidence that QuIC contains a useful diameter component beyond the spectrum. The (n=16) gain may indicate a weak signal, but the effect is absent at (n=14) and small relative to the diamond, 6-cycle, and girth results.

## Radius, Wiener index, and automorphism order

Only (n=14) results are currently available for these targets.

###### Radius

The spectral baseline reaches

[
R^2=0.345\pm0.081,
]

while the two-stage model obtains

[
R^2=0.344\pm0.096.
]

The residual-space score is approximately zero:

[
R^2_{\mathrm{residual}}=-0.001.
]

QuIC provides no detectable residual information for radius at (n=14).

### Wiener index

The spectral baseline is already strong:

[
R^2=0.973\pm0.006.
]

Adding the QuIC residual model reduces performance slightly:

[
R^2_{\mathrm{two-stage}}=0.961\pm0.021,
]

with

[
\Delta R^2=-0.012
]

and

[
R^2_{\mathrm{residual}}=-0.438.
]

There is no evidence that QuIC predicts the remaining Wiener-index variation at (n=14).

### Automorphism-group order

For

[
\log_2|\mathrm{Aut}(G)|,
]

the spectral baseline obtains

[
R^2=0.678\pm0.027,
]

and the two-stage model obtains

[
R^2=0.684\pm0.025.
]

The apparent gain is only

[
\Delta R^2=+0.006,
]

while residual-space performance is slightly negative:

[
R^2_{\mathrm{residual}}=-0.003.
]

The small total-score difference is therefore not supported by direct residual prediction and should be treated as fold or regularization variation rather than evidence of useful non-spectral decoding.

The pending (n=16) results will determine whether any of these three targets behave differently at the larger graph order.

##### Interpreting residual-space and total (R^2)

The two reported improvement measures answer different questions.

The total-score change,

[
\Delta R^2,
]

measures how much the complete target prediction improves after adding QuIC.

Residual-space (R^2) measures how well QuIC predicts only the component left unexplained by the spectral model.

A target can therefore have:

* high residual (R^2) but small (\Delta R^2), when the spectral residual is real but small relative to total target variance;
* large values for both, when the spectrum leaves a substantial and predictable residual;
* or negative residual (R^2), when QuIC cannot predict the remaining variation.

The 6-cycle row illustrates the first case. Diamonds illustrate the second. Radius and Wiener index illustrate the third.

##### What the experiment establishes

The completed results support four main conclusions.

1. **The residual protocol behaves correctly on spectrally solved controls.**
   Triangles, 4-cycles, 5-cycles, and spectral gap receive no artificial improvement once the spectral model reaches (R^2=1).

2. **QuIC contains a strong functionally useful non-spectral diamond signal.**
   It explains more than (82%) of the spectral residual variance at both graph orders and raises total predictive performance by approximately (0.31) to (0.34).

3. **QuIC predicts the unresolved 6-cycle component.**
   Although the total gain is small because the spectral baseline is already near perfect, residual-space (R^2) reaches (0.533) at (n=14) and (0.808) at (n=16).

4. **QuIC linearizes girth more effectively than the spectral coordinates.**
   The large girth improvements demonstrate a representational advantage, although not necessarily non-spectral information.

The strongest claim is therefore not that QuIC improves every graph invariant. It does not improve radius or Wiener index at (n=14), and the evidence for diameter and automorphism order is weak.

The supported claim is narrower:

> QuIC contains a reproducible non-spectral component associated with the division between 6-cycles and diamonds. This component is functionally decodable: a QuIC residual model substantially improves diamond prediction beyond adjacency-spectrum features and predicts a large fraction of the remaining 6-cycle error at both (n=14) and (n=16).

##### Necessary qualifications

The (n=16) run is incomplete. Conclusions about radius, Wiener index, and automorphism-group order currently rely only on (n=14).

No paired statistical test is reported for the foldwise changes in (R^2). The diamond effects are sufficiently large and consistent across graph orders to be persuasive descriptively, but formal uncertainty for

[
\Delta R^2
]

would strengthen the presentation.

The two-stage model is not intended to outperform QuIC alone on every target. For diamonds and girth, QuIC alone is stronger than the combined model. The purpose of the two-stage experiment is narrower: determine whether QuIC predicts the component missed by the spectrum.

The spectral model is also linear in the supplied eigenvalue and moment coordinates. Girth improvements may therefore reflect nonlinear repackaging of spectral information. The diamond result is stronger because the target varies independently of the adjacency spectrum, while the sixth-moment identity explains why QuIC's diamond signal also appears in the 6-cycle residual.

Finally, residual-space (R^2) should not be interpreted on targets whose spectral residual variance is essentially zero. The strongly negative values for exact spectral controls are numerical artifacts of evaluating (R^2) on an almost constant residual target.

##### Overall assessment

The timeout does not prevent a clear interpretation of the principal result. The most important rows completed at both graph orders.

The experiment provides strong, replicated evidence that QuIC predicts a non-spectral structural component associated with diamonds and 6-cycles. The diamond result is large in both total and residual-space (R^2), while the 6-cycle result shows that QuIC recovers much of the small residual left after a nearly perfect spectral prediction.

The current evidence does not support a broad claim that QuIC improves prediction of all non-spectral graph invariants. Radius and Wiener index show no improvement at (n=14), diameter is at most weak, and the automorphism result is negligible.

The appropriate central conclusion is:

> Across complete connected cubic-graph censuses at (n=14) and (n=16), QuIC contains a functionally useful non-spectral residue. The clearest signal is diamond count: QuIC explains more than (82%) of the spectral residual variance and improves total (R^2) by approximately (0.31)–(0.34). The corresponding 6-cycle residual is also predictable, consistent with the spectral identity that fixes (C_6+D) but not its decomposition.

### E2C precision Audit
##### Experimental design

This notebook audits whether the reported QuIC separations between adjacency-cospectral graphs are genuine properties of the ideal circuit or artifacts of the original float64 implementation.

The audit covers the complete connected cubic-graph censuses at:

* (n=14): 509 graphs;
* (n=16): 4,060 graphs.

The adjacency-cospectral census contains:

| Order     | Cospectral groups | Group members | Within-group pairs |
| --------- | ----------------: | ------------: | -----------------: |
| (n=14)    |                 3 |             6 |                  3 |
| (n=16)    |                41 |            83 |                 43 |
| **Total** |            **44** |        **89** |             **46** |

At (n=16), 40 groups are pairs and one group is a mutually cospectral triple.

The audit performs four checks:

1. independently recompute every relevant QuIC vector using a pure NumPy circuit implementation;
2. recompute all 89 cospectral-group members in extended precision;
3. recompute the 30 closest pairs using 40-digit `mpmath` arithmetic;
4. measure how each separation is distributed across the sorted probability-vector coordinates.

The circuit parameters and float64 angles are held fixed. Extended precision is applied to the circuit arithmetic rather than to a modified set of angles.

##### Dataset and census checks

The stored probability vectors have the expected dimensions, are sorted in descending order, and remain normalized to near machine precision.

The maximum stored-vector normalization errors are:

[
2.00\times10^{-15}
\quad\text{at }n=14,
]

and

[
2.66\times10^{-15}
\quad\text{at }n=16.
]

The adjacency-cospectral groups are independently reconstructed using exact integer trace sequences. The resulting census exactly matches the previously certified enumeration:

* 3 groups and 3 pairs at (n=14);
* 41 groups and 43 pairs at (n=16);
* 89 total graph members;
* 46 total within-group pairs.

This verifies that the precision audit is being applied to the intended set of cospectral comparisons.

## Circuit smoke tests

The independent extended-precision implementation satisfies normalization and permutation invariance on representative graphs.

| Order  |  Normalization error | Permutation-invariance (L_1) |
| ------ | -------------------: | ---------------------------: |
| (n=14) | (9.76\times10^{-19}) |         (7.90\times10^{-20}) |
| (n=16) | (4.34\times10^{-19}) |         (1.31\times10^{-19}) |

These values are consistent with the numerical floor of the long-double computation.

The permutation test is especially relevant because QuIC sorts the output probabilities and therefore claims invariance to vertex relabeling. The independent implementation reproduces that behavior to approximately (10^{-19}).

##### Independent reconstruction gate

Every one of the 89 relevant vectors is recomputed using a pure NumPy implementation independent of the stored producer pipeline.

The largest coordinate-wise disagreement between the independent float64 vectors and the stored vectors is:

[
1.89\times10^{-15}
\quad\text{at }n=14,
]

and

[
2.22\times10^{-15}
\quad\text{at }n=16.
]

The global worst case is therefore

[
\max_{G,z}
\left|
p^{\mathrm{independent}}_z(G)
-----------------------------

p^{\mathrm{stored}}_z(G)
\right|
=======

2.22\times10^{-15},
]

well below the preregistered validation threshold

[
10^{-12}.
]

This gate is load-bearing. It establishes that the stored vectors used elsewhere in the analysis are reproduced by an independently implemented circuit rather than by reusing the original simulation code.

##### Measured float64 reconstruction floor

Each graph is recomputed in 80-bit long-double arithmetic. The numerical floor of the float64 pipeline is measured directly as

[
\left|
\mathbf p_{\mathrm{float64}}(G)
-------------------------------

\mathbf p_{\mathrm{longdouble}}(G)
\right|_1.
]

The observed per-graph floors are:

| Order  |              Minimum |               Median |              Maximum |
| ------ | -------------------: | -------------------: | -------------------: |
| (n=14) | (7.44\times10^{-17}) | (3.49\times10^{-16}) | (5.82\times10^{-16}) |
| (n=16) | (9.05\times10^{-17}) | (5.72\times10^{-16}) | (1.11\times10^{-15}) |

These are empirical reconstruction errors for the actual circuit and graphs, not estimates based only on machine epsilon.

The measured floors are several orders of magnitude below even the smallest cospectral separation.

##### Multiprecision certification

Every pair with long-double separation below

[
10^{-6}
]

is recomputed using 40-digit `mpmath` arithmetic.

This includes:

* 30 of the 46 cospectral pairs;
* 60 distinct graphs.

The measured long-double-to-`mpmath` floor per graph ranges from

[
4.63\times10^{-19}
]

to

[
1.03\times10^{-18},
]

with median approximately

[
6.87\times10^{-19}.
]

For all 30 audited pairs, the float64, long-double, and 40-digit pair distances agree to the precision displayed in the report.

The closest (n=14) pair remains separated by

[
5.868\times10^{-8}
]

under all three arithmetic implementations.

The closest (n=16) pair remains separated by

[
1.917\times10^{-8}.
]

The smallest reported distances therefore survive both an independent implementation and two successive increases in arithmetic precision.

##### Separation relative to the measured numerical floor

For each pair, the audit compares the long-double separation with the sum of the two graphs' measured float64 reconstruction floors:

[
\text{floor ratio}
==================

\frac{
\left|
\mathbf p_i-\mathbf p_j
\right|_1
}{
\left|
\mathbf p_i^{64}-\mathbf p_i^{LD}
\right|_1
+
\left|
\mathbf p_j^{64}-\mathbf p_j^{LD}
\right|_1
}.
]

The smallest ratio across all 46 pairs is

[
2.48\times10^7.
]

The largest is

[
2.91\times10^{10}.
]

Thus, every reported cospectral separation is at least approximately **25 million times larger** than its measured float64 reconstruction floor.

No pair lies within ten times the numerical floor:

[
0\text{ of }46
]

pairs are flagged as unresolved.

This is the central precision result. The cospectral separations are not accumulated float64 rounding differences.

## Separation ranges

The certified pairwise (L_1) ranges are:

| Order  |   Minimum separation |   Maximum separation |
| ------ | -------------------: | -------------------: |
| (n=14) | (5.868\times10^{-8}) | (1.692\times10^{-5}) |
| (n=16) | (1.917\times10^{-8}) | (1.680\times10^{-5}) |

The similarity of these ranges across graph orders is notable. Increasing from (n=14) to (n=16) introduces many more cospectral pairs, including several extremely close pairs, but the largest non-spectral separations remain near

[
1.7\times10^{-5}.
]

Representative pairs include:

| Order  | Pair        |      Certified (L_1) | Multiple of float64 floor |
| ------ | ----------- | -------------------: | ------------------------: |
| (n=14) | ((234,239)) | (5.868\times10^{-8}) |          (1.36\times10^8) |
| (n=14) | ((79,458))  | (3.908\times10^{-7}) |          (4.12\times10^8) |
| (n=14) | ((201,203)) | (1.692\times10^{-5}) |       (2.91\times10^{10}) |
| (n=16) | ((594,601)) | (1.917\times10^{-8}) |          (2.48\times10^7) |
| (n=16) | ((1,5))     | (1.680\times10^{-5}) |       (1.29\times10^{10}) |

Even the weakest certified separation is vastly larger than the measured arithmetic uncertainty.

##### Position within the census distance scale

The complete (n=14) pairwise distribution contains 129,286 graph pairs. At (n=16), the reference distribution is estimated using 299,918 seeded random graph pairs.

The median census-wide QuIC distance is approximately:

[
8.5\times10^{-5}
\quad\text{at }n=14,
]

and

[
7.7\times10^{-5}
\quad\text{at }n=16.
]

The cospectral separations occupy the lower tail of these distributions.

At (n=14), their percentile standings range from approximately

[
0
]

to

[
5.82.
]

At (n=16), they range from approximately

[
0
]

to

[
6.37.
]

Relative to the median arbitrary-pair distance, the cospectral separations range from:

[
6.91\times10^{-4}
]

to

[
1.99\times10^{-1}
]

at (n=14), and from

[
2.49\times10^{-4}
]

to

[
2.18\times10^{-1}
]

at (n=16).

This is expected. Cospectral graphs have their dominant adjacency-spectral differences removed, so their remaining QuIC separations should be much smaller than those between arbitrary graph pairs.

The low census percentiles do not weaken the precision certification. They describe the geometric magnitude of the non-spectral residue, not whether the residue is numerically real.

## Head/tail decomposition

For each pair, the notebook measures how the total (L_1) separation is distributed across the sorted probability ranks.

The reported quantities are:

* `hf50`: fraction of total separation contained in the 50 largest probabilities;
* `hf90`: fraction contained in the 90 largest probabilities;
* `k50`: number of leading coordinates needed to capture 50% of the separation;
* `k90`: number needed to capture 90%.

The results are heterogeneous.

### Strongly head-concentrated pairs

The largest-separation pairs place most of their difference in the leading coordinates.

For the (n=14) pair ((201,203)):

[
66.8%
]

of the separation lies in the top 50 coordinates, and

[
85.6%
]

lies in the top 90.

Half of the total separation is reached by coordinate

[
k_{50}=42,
]

and 90% by

[
k_{90}=167.
]

The four largest (n=16) pairs behave similarly:

* approximately (66%) of their separation occurs in the top 50 coordinates;
* approximately (85%) occurs in the top 90;
* (k_{50}\approx49\text{--}51);
* (k_{90}\approx197\text{--}202).

These pairs directly support the earlier observation that the strongest non-spectral differences are visible in the head of the sorted distribution.

###### Diffuse pairs

Many of the smaller (n=16) separations are less concentrated.

For several pairs, the top 50 coordinates contain only approximately

[
2%\text{--}10%
]

of the total separation. Their (k_{50}) values can exceed 400 and reach as high as 875.

The most diffuse reported pair requires

[
k_{90}=2804
]

coordinates to accumulate 90% of its separation.

The strongest possible statement is therefore not that every cospectral difference is concentrated in the first 50 or 90 probabilities. That expectation is supported primarily for the largest-separation pairs.

Nevertheless, all pairs remain concentrated within a relatively small leading portion of the complete vector:

* at (n=14), every pair reaches 90% by coordinate 1,133, less than 7% of the 16,384-dimensional vector;
* at (n=16), every pair reaches 90% by coordinate 2,804, less than 4.3% of the 65,536-dimensional vector.

Thus, the non-spectral residue is broadly head-weighted, but its concentration within the very first 50–90 coordinates varies substantially by pair.

##### What the experiment establishes

The audit supports five conclusions.

1. **The stored QuIC vectors are independently reproducible.**
   A separate pure NumPy circuit matches every audited vector with maximum coordinate error (2.22\times10^{-15}).

2. **All 46 cospectral separations survive extended precision.**
   Float64 and long-double calculations agree to the reported precision, and the closest 30 pairs are independently confirmed at 40 decimal digits.

3. **The separations are far above numerical uncertainty.**
   The weakest pair is approximately (2.48\times10^7) times above its measured float64 reconstruction floor.

4. **No pair is numerically unresolved.**
   None of the 46 pairs falls within even ten times the measured floor.

5. **The strongest separations are concentrated in the probability head.**
   The largest pairs place approximately two-thirds of their total difference in the top 50 probabilities, although smaller separations can be more diffuse.

The primary conclusion is therefore:

[
\boxed{
\text{The reported cospectral separations are genuine ideal-circuit differences, not floating-point artifacts.}
}
]

## Necessary qualifications

The audit establishes numerical reality, not experimental observability.

A separation of order

[
10^{-8}
]

can be many millions of times larger than floating-point error while still being too small to resolve using practical finite-shot sampling or noisy hardware. Numerical certification and measurement feasibility are separate questions.

The 40-digit calculation is applied only to pairs whose long-double separation is below (10^{-6}). Larger pairs are not recomputed using `mpmath` because their float64-to-long-double separation ratios are already between approximately (10^8) and (10^{10}).

The (n=16) census percentile estimates use a random sample of approximately 300,000 graph pairs rather than the complete set of more than eight million pairs. These percentile values are therefore estimates. They do not affect the arithmetic certification.

The exact same float64 circuit angles are lifted into extended precision. This is the correct design for measuring the arithmetic error of the original circuit. It does not test sensitivity to small perturbations in the angles themselves.

Finally, the head-concentration hypothesis receives a qualified result. It is strongly supported for the largest separations, but many smaller pairs distribute their differences across hundreds or thousands of leading coordinates.

## Overall assessment

This notebook closes the principal numerical objection to the cospectral analysis.

The stored vectors are independently reproduced, the exact cospectral census is recovered, and every one of the 46 pair separations remains stable under long-double arithmetic. The 30 closest pairs are additionally confirmed using 40-digit arithmetic.

The smallest separation,

[
1.917\times10^{-8},
]

is still approximately

[
2.48\times10^7
]

times larger than its measured float64 reconstruction floor. No pair is remotely close to being explained by numerical roundoff.

The appropriate central claim is:

> Independent circuit reconstruction and extended-precision arithmetic certify every QuIC separation among the 46 adjacency-cospectral pairs at (n=14) and (n=16). All separations lie at least (2.48\times10^7) times above the measured float64 reconstruction floor, and the 30 closest pairs are reproduced using 40-digit arithmetic. The non-spectral residue is therefore numerically genuine, although its practical shot-level resolvability remains a separate question.

### E3 - GNN Controls
##### Experimental design

This experiment compares the fixed QuIC representation with four task-trained graph neural network baselines on the complete connected cubic-graph censuses at:

* (n=14): 509 graphs;
* (n=16): 4,060 graphs.

The seven targets are:

* triangle count;
* 4-cycle count;
* 5-cycle count;
* 6-cycle count;
* girth;
* diameter;
* spectral gap.

The GNN comparison contains four arms:

1. **GIN with constant node features**;
2. **GCN with constant node features**;
3. **GIN with random node initialization**;
4. **GIN with Laplacian positional encodings**.

All GNNs use width 64 and sum pooling. Depth and learning rate are selected from:

[
\text{depth}\in{3,5},
\qquad
\eta\in{10^{-3},10^{-2}}.
]

The selected configuration for each graph order, model, and target is determined using the fold-0, seed-0 validation split and then reused across:

* 5 frozen outer folds;
* 3 random seeds.

Each reported GNN score therefore summarizes 15 trained runs per table cell.

The random-node-initialization model resamples its features every epoch. Validation is averaged over five random draws, and test predictions and embeddings are averaged over ten draws.

The Laplacian positional encoding contains the first eight nonconstant Laplacian eigenvectors. Random sign flips are used during training.

QuIC is not trained on any target. Its column uses ridge regression on the full sorted ideal probability vector:

[
\mathbf p(G)\in\mathbb R^{2^n}.
]

The QuIC feature dimensions are therefore:

[
2^{14}=16{,}384,
\qquad
2^{16}=65{,}536.
]

##### Headline results: trained-network predictions

The primary table compares each task-trained network's own prediction head with a linear probe on QuIC.

###### (n=14)

| Target       |            QuIC |        GIN-const |        GCN-const |          GIN-RNI |       GIN-LapPE |
| ------------ | --------------: | ---------------: | ---------------: | ---------------: | --------------: |
| Triangles    | (1.000\pm0.000) | (-0.013\pm0.026) | (-0.008\pm0.009) |  (0.430\pm0.052) | (0.824\pm0.240) |
| 4-cycles     | (0.998\pm0.002) | (-0.036\pm0.050) | (-0.024\pm0.028) |  (0.048\pm0.076) | (0.524\pm0.258) |
| 5-cycles     | (0.928\pm0.092) | (-0.024\pm0.024) | (-0.028\pm0.027) | (-0.021\pm0.027) | (0.470\pm0.132) |
| 6-cycles     | (0.485\pm0.326) | (-0.019\pm0.024) | (-0.020\pm0.029) |  (0.034\pm0.035) | (0.420\pm0.094) |
| Girth        | (0.993\pm0.014) | (-0.015\pm0.026) | (-0.016\pm0.029) |  (0.140\pm0.042) | (0.820\pm0.098) |
| Diameter     | (0.548\pm0.058) | (-0.023\pm0.032) | (-0.023\pm0.030) |  (0.268\pm0.093) | (0.664\pm0.193) |
| Spectral gap | (0.944\pm0.010) | (-0.012\pm0.023) | (-0.008\pm0.009) |  (0.506\pm0.068) | (0.994\pm0.004) |

###### (n=16)

| Target       |            QuIC |        GIN-const |        GCN-const |         GIN-RNI |       GIN-LapPE |
| ------------ | --------------: | ---------------: | ---------------: | --------------: | --------------: |
| Triangles    | (1.000\pm0.000) | (-0.003\pm0.002) | (-0.002\pm0.001) | (0.566\pm0.029) | (0.941\pm0.012) |
| 4-cycles     | (1.000\pm0.000) | (-0.002\pm0.002) | (-0.002\pm0.002) | (0.201\pm0.030) | (0.614\pm0.267) |
| 5-cycles     | (0.982\pm0.015) | (-0.002\pm0.002) | (-0.003\pm0.002) | (0.099\pm0.067) | (0.568\pm0.051) |
| 6-cycles     | (0.642\pm0.122) | (-0.003\pm0.004) | (-0.003\pm0.003) | (0.068\pm0.010) | (0.498\pm0.023) |
| Girth        | (0.999\pm0.003) | (-0.005\pm0.006) | (-0.006\pm0.006) | (0.250\pm0.026) | (0.923\pm0.030) |
| Diameter     | (0.737\pm0.019) | (-0.003\pm0.004) | (-0.003\pm0.004) | (0.459\pm0.053) | (0.807\pm0.017) |
| Spectral gap | (0.932\pm0.007) | (-0.006\pm0.006) | (-0.007\pm0.006) | (0.620\pm0.058) | (0.996\pm0.001) |

QuIC numerically outperforms all four GNN arms on every cycle-count target at both graph orders. The margins are decisive for triangles, 4-cycles, and 5-cycles.

The (n=14) 6-cycle comparison is weaker:

[
R^2_{\mathrm{QuIC}}=0.485\pm0.326,
\qquad
R^2_{\mathrm{LapPE}}=0.420\pm0.094.
]

The QuIC mean is higher, but the fold variance is too large to treat this as a strong separation. At (n=16), the result is clearer:

[
0.642\pm0.122
\quad\text{versus}\quad
0.498\pm0.023.
]

LapPE outperforms QuIC on diameter and spectral gap at both graph orders. These results are important controls: the comparison does not uniformly favor QuIC, and the strongest GNN arm wins on two targets outside the local-cycle hierarchy.

## Constant-feature collapse

The constant-feature GIN and GCN arms fail exactly as predicted by their expressiveness class.

For a regular graph with uniform initial node features, every vertex receives the same representation after every message-passing layer. Since every graph in a census has the same number of vertices and sum pooling is used, the graph-level embedding is identical for every graph.

The measured collapse statistic is

[
\frac{
\max_{i,j}|\mathbf h(G_i)-\mathbf h(G_j)|_2
}{
\operatorname{mean}_i|\mathbf h(G_i)|_2
}.
]

For every constant-feature run at both graph orders, this ratio is:

[
0.00\times10^0.
]

This covers 210 runs per graph order:

[
2\text{ architectures}
\times
7\text{ targets}
\times
3\text{ seeds}
\times
5\text{ folds},
]

or 420 completed constant-feature runs across the two censuses.

The resulting test scores remain at the constant-predictor floor. Slightly negative cross-validated (R^2) values arise because predicting the training mean can perform marginally worse than predicting the test-fold mean.

These columns are not merely weak baselines. They are measured demonstrations of the standard 1-WL failure mode on fixed-order regular graphs with uniform features.

##### Random node initialization

Random node initialization breaks the exact symmetry, but the resulting models recover only limited structural information.

At (n=16), the trained prediction heads obtain:

[
R^2=
0.566,\ 0.201,\ 0.099,\ 0.068
]

for (C_3,C_4,C_5,C_6), respectively.

The pattern deteriorates rapidly with cycle length. The model recovers a moderate triangle signal, a weak 4-cycle signal, and little 5- or 6-cycle information.

This is not explained by an insufficient training budget. The (n=16) RNI models commonly train for several hundred epochs, with median best epochs between approximately 250 and 414 depending on the target. They also receive fresh random features every epoch and noise-averaged evaluation.

Performance improves between (n=14) and (n=16), especially for triangles and diameter, but the larger census does not close the gap with QuIC or LapPE.

The result illustrates the difference between theoretical symmetry-breaking capacity and practical learnability. Random identifiers prevent exact collapse, but the trained network does not reliably organize the induced stochastic representation around deeper cycle invariants.

##### Laplacian positional encoding

LapPE is the strongest GNN baseline.

At (n=16), its cycle-count scores decrease monotonically with cycle length:

[
0.941
\rightarrow
0.614
\rightarrow
0.568
\rightarrow
0.498.
]

The same ordering appears at (n=14):

[
0.824
\rightarrow
0.524
\rightarrow
0.470
\rightarrow
0.420.
]

LapPE therefore recovers the shallowest cycle information most effectively and loses accessibility as the required structural depth increases.

QuIC exhibits the same qualitative hierarchy but retains substantially stronger scores through the 5-cycle layer:

[
1.000,\ 1.000,\ 0.982,\ 0.642
]

at (n=16).

The LapPE 4-cycle score is notably unstable:

[
0.524\pm0.258
\quad\text{at }n=14,
]

and

[
0.614\pm0.267
\quad\text{at }n=16.
]

This variation may reflect sensitivity to folds, training seeds, eigenvector signs, or eigenspace-basis choices. The experiment reports the instability rather than selecting a favorable run.

LapPE wins the two non-cycle targets for which its inductive bias is most favorable:

[
R^2_{\mathrm{diameter}}=0.807
\quad\text{at }n=16,
]

and

[
R^2_{\mathrm{spectral\ gap}}=0.996.
]

This prevents the result from being interpreted as a generic failure of the trained architecture. LapPE can outperform QuIC where the target aligns with its representation.

##### Linear probes on the learned GNN embeddings

A second analysis replaces each GNN's trained prediction head with the same ridge-probe protocol used for QuIC.

The GNN embeddings remain target-specific: each was produced by a network trained using labels for the target being probed. The analysis therefore tests whether the final hidden representation contains information that the network's original head failed to use.

###### (n=14)

| Target       |            QuIC |        GIN-const |        GCN-const |          GIN-RNI |       GIN-LapPE |
| ------------ | --------------: | ---------------: | ---------------: | ---------------: | --------------: |
| Triangles    | (1.000\pm0.000) | (-0.002\pm0.004) | (-0.003\pm0.004) |  (0.660\pm0.054) | (0.887\pm0.106) |
| 4-cycles     | (0.998\pm0.002) | (-0.008\pm0.006) | (-0.010\pm0.014) |  (0.059\pm0.042) | (0.594\pm0.103) |
| 5-cycles     | (0.928\pm0.092) | (-0.011\pm0.012) | (-0.013\pm0.014) | (-0.008\pm0.021) | (0.468\pm0.161) |
| 6-cycles     | (0.485\pm0.326) | (-0.006\pm0.008) | (-0.005\pm0.008) |  (0.086\pm0.052) | (0.429\pm0.099) |
| Girth        | (0.993\pm0.014) | (-0.012\pm0.015) | (-0.008\pm0.012) |  (0.210\pm0.056) | (0.783\pm0.072) |
| Diameter     | (0.548\pm0.058) | (-0.008\pm0.007) | (-0.008\pm0.006) |  (0.387\pm0.081) | (0.720\pm0.061) |
| Spectral gap | (0.944\pm0.010) | (-0.002\pm0.002) | (-0.002\pm0.002) |  (0.546\pm0.057) | (0.993\pm0.003) |

###### (n=16)

| Target       |            QuIC |        GIN-const |        GCN-const |         GIN-RNI |       GIN-LapPE |
| ------------ | --------------: | ---------------: | ---------------: | --------------: | --------------: |
| Triangles    | (1.000\pm0.000) | (-0.001\pm0.001) | (-0.001\pm0.001) | (0.718\pm0.024) | (0.948\pm0.011) |
| 4-cycles     | (1.000\pm0.000) | (-0.002\pm0.002) | (-0.002\pm0.002) | (0.186\pm0.053) | (0.666\pm0.143) |
| 5-cycles     | (0.982\pm0.015) | (-0.001\pm0.001) | (-0.001\pm0.001) | (0.269\pm0.129) | (0.571\pm0.044) |
| 6-cycles     | (0.642\pm0.122) | (-0.002\pm0.003) | (-0.002\pm0.003) | (0.120\pm0.022) | (0.501\pm0.020) |
| Girth        | (0.999\pm0.003) | (-0.005\pm0.008) | (-0.005\pm0.008) | (0.257\pm0.029) | (0.799\pm0.114) |
| Diameter     | (0.737\pm0.019) | (-0.001\pm0.001) | (-0.001\pm0.001) | (0.510\pm0.052) | (0.782\pm0.020) |
| Spectral gap | (0.932\pm0.007) | (-0.004\pm0.005) | (-0.004\pm0.005) | (0.618\pm0.021) | (0.993\pm0.002) |

The post-hoc linear probe often improves the RNI representation substantially. At (n=16), triangle performance rises from

[
0.566\rightarrow0.718,
]

and 5-cycle performance rises from

[
0.099\rightarrow0.269.
]

This indicates that some target information reaches the final hidden representation but is not fully exploited by the trained nonlinear head.

The same effect appears more modestly for LapPE. Its linear probe remains below QuIC on every cycle target and above QuIC on diameter and spectral gap.

The constant-feature embeddings remain exactly uninformative under the replacement readout, confirming that their failure occurs in the representation rather than only in the prediction head.

##### Matched-dimension comparison

The full QuIC vector is much larger than the 64-dimensional GNN embeddings. The notebook therefore reads the existing QuIC truncation curve at:

[
k=50
\quad\text{and}\quad
k=100,
]

which bracket the GNN width of 64.

###### (n=14)

| Target    | QuIC (k=50) | QuIC (k=100) |
| --------- | ----------: | -----------: |
| Triangles |       1.000 |        1.000 |
| 4-cycles  |       0.988 |        0.993 |
| 5-cycles  |    (-0.026) |        0.272 |
| 6-cycles  |       0.228 |        0.235 |

###### (n=16)

| Target    | QuIC (k=50) | QuIC (k=100) |
| --------- | ----------: | -----------: |
| Triangles |       1.000 |        1.000 |
| 4-cycles  |       0.981 |        0.996 |
| 5-cycles  |       0.167 |        0.335 |
| 6-cycles  |       0.179 |        0.184 |

At approximately matched representation dimension, QuIC retains essentially perfect triangle and 4-cycle prediction and outperforms every trained GNN baseline on those targets.

The deeper cycle layers behave differently. At (k=100), QuIC remains below the LapPE representation for 5- and 6-cycle prediction:

[
0.335<0.571
]

for 5-cycles at (n=16), and

[
0.184<0.501
]

for 6-cycles.

The full-vector advantage on deeper cycles therefore depends on information distributed farther down the sorted probability vector. It is not preserved under aggressive truncation to approximately 64 coordinates.

This gives a more precise interpretation of QuIC's advantage:

* shallow-cycle information is concentrated in the probability head;
* deeper-cycle information requires a substantially larger portion of the representation.

##### Scaling from (n=14) to (n=16)

The larger census strengthens most of the conclusions.

For QuIC:

[
R^2_{C_5}: 0.928\rightarrow0.982,
]

[
R^2_{C_6}: 0.485\rightarrow0.642,
]

and

[
R^2_{\mathrm{diameter}}: 0.548\rightarrow0.737.
]

For RNI, scaling improves triangles, 4-cycles, diameter, and spectral gap, but the deeper cycle scores remain weak.

For LapPE, the larger census improves triangle, 4-cycle, 5-cycle, 6-cycle, girth, and diameter prediction. The cycle-depth decline nevertheless remains.

The constant-feature arms approach (R^2=0) more closely at (n=16), as expected when the test folds become larger, while their embeddings remain exactly collapsed.

The (n=16) results therefore replicate the qualitative ordering:

[
\text{QuIC}

>

\text{LapPE}

>

\text{RNI}

>

\text{constant-feature message passing}
]

for the cycle-count targets.

This ordering does not hold universally. LapPE remains stronger on diameter and spectral gap.

## Cospectral graph pairs

The consumer identifies:

* 3 adjacency-cospectral pairs at (n=14);
* 43 adjacency-cospectral pairs at (n=16).

The (n=16) set includes one mutually cospectral triple:

[
(582,3061,3800).
]

For each trained model, the analysis computes:

[
\frac{
|\mathbf h(G_i)-\mathbf h(G_j)|*2
}{
\operatorname{median}*{a<b}
|\mathbf h(G_a)-\mathbf h(G_b)|_2
}
]

for each cospectral pair, using the triangle-target runs.

###### Constant-feature models

Both constant-feature models assign zero distance to every cospectral pair because they assign the same embedding to every graph:

[
d_{\mathrm{mate}}=0.
]

###### Random node initialization

The normalized RNI mate distances are:

* (0.884)–(0.954) at (n=14);
* (0.764)–(1.031) at (n=16).

Their median (n=16) value is approximately:

[
0.898.
]

Cospectral pairs are therefore almost as far apart as ordinary graph pairs in the averaged RNI embedding space.

This should not automatically be interpreted as meaningful structural separation. RNI is stochastic, and evaluation averages only ten feature draws. Some separation may reflect finite-draw random-feature variation rather than a stable graph invariant. The result mainly shows that RNI does not place cospectral mates in a distinctively close region.

###### Laplacian positional encoding

The normalized LapPE mate distances are:

* (0.181)–(0.517) at (n=14);
* (0.198)–(0.896) at (n=16).

The median at (n=16) is approximately:

[
0.349.
]

Cospectral pairs are therefore closer than typical graph pairs but not collapsed.

This corrects an incorrect statement in the producer notebook. Adjacency-cospectral graphs share eigenvalues, but LapPE supplies eigenvectors. Their eigenvectors need not agree, so LapPE is not theoretically required to map cospectral graphs to the same representation.

The observed separation remains an empirical property of this implementation. Raw eigenvectors have sign and degenerate-eigenspace ambiguities. Training-time sign flips address sign ambiguity but not arbitrary rotations within repeated eigenspaces. The LapPE mate distances should therefore not be treated as a certified invariant separation comparable to the exact QuIC cospectral audit.

## What the experiment establishes

The completed results support five principal conclusions.

1. **Constant-feature GIN and GCN are exactly blind on these graph families.**
   Their embeddings collapse identically across every graph, target, fold, and seed.

2. **Breaking node symmetry is necessary but not sufficient.**
   RNI prevents collapse but yields weak and rapidly degrading cycle-count performance.

3. **LapPE is a strong but incomplete repair.**
   It captures triangles well, then loses predictive power monotonically through longer cycles.

4. **The full QuIC representation provides the strongest cycle-count accessibility.**
   It numerically outperforms all tested GNN arms on (C_3) through (C_6) at both graph orders, with the (n=14) 6-cycle comparison remaining statistically weak because of QuIC's large fold variance.

5. **QuIC is not uniformly superior.**
   LapPE outperforms it on diameter and spectral gap, demonstrating that the result is specific to the structural information emphasized by each representation.

The experiment therefore characterizes a difference in representational coverage rather than a universal model ranking.

##### Necessary qualifications

The full-vector QuIC comparison is not dimension matched. QuIC uses 16,384 or 65,536 probability coordinates, whereas each GNN graph embedding has width 64. The truncation analysis shows that QuIC's deeper-cycle advantage is reduced or reversed near matched dimensionality.

QuIC also uses exact ideal probabilities. The experiment evaluates structural decodability, not finite-shot performance, hardware robustness, runtime, or memory efficiency. Producing the complete probability vector is exponentially expensive in the number of qubits.

The baseline set does not represent all graph-learning architectures. It includes conventional GIN and GCN, plus RNI and LapPE repairs. Higher-order GNNs, subgraph methods, graph transformers, and architectures explicitly designed to exceed 1-WL are not evaluated.

The constant-feature arms are theoretically guaranteed negative controls on fixed-order regular graphs. They demonstrate the expected message-passing limitation but should not be presented as strong practical competitors.

Hyperparameter tuning uses one fold-0, seed-0 validation split per model and target rather than a fully nested tuning procedure. No test-fold labels enter selection, but the four-point grid may not identify the best configuration for every fold.

The reported standard deviations are not directly equivalent across methods. QuIC summarizes five folds, whereas the GNN columns summarize 15 correlated seed-fold runs. No paired significance tests are reported for the differences.

The post-hoc probes operate on target-trained GNN embeddings. They are useful for separating representation failure from head failure, but they do not compare target-independent frozen embeddings in the same sense as QuIC.

Finally, the RNI and LapPE cospectral analyses are geometric diagnostics rather than invariance certificates. RNI is stochastic, and LapPE is sensitive to eigenvector-basis conventions.

##### Overall assessment

The experiment provides a clear hierarchy of baseline behavior.

Uniform-feature message passing collapses exactly and cannot distinguish any graphs in either cubic census. Random node initialization restores variation but learns little beyond triangles and coarse global structure. Laplacian positional encoding is substantially stronger and nearly solves triangles, diameter, and spectral gap, but its cycle-count performance declines steadily with cycle length.

Against these baselines, the fixed QuIC representation provides exceptionally broad cycle accessibility. At (n=16), a linear readout obtains:

[
1.000,\ 1.000,\ 0.982,\ 0.642
]

for (C_3,C_4,C_5,C_6), compared with LapPE's:

[
0.941,\ 0.614,\ 0.568,\ 0.498.
]

The advantage is not universal. LapPE is stronger for diameter and spectral gap, and at approximately matched representation dimension it also exceeds truncated QuIC on 5- and 6-cycle prediction.

The appropriate central claim is:

> On the complete connected cubic-graph censuses at (n=14) and (n=16), conventional constant-feature message passing collapses exactly, while RNI and Laplacian positional encodings recover progressively more structure but lose accessibility with cycle depth. The full, fixed QuIC probability representation provides the strongest linear decodability across all tested cycle-count targets, although its deeper-cycle advantage depends on a substantially higher-dimensional readout and does not extend to diameter or spectral gap.

### E5 - Exploration of linear vs non linear methods.

##### Experimental design

This experiment tests whether nonlinear readouts recover structural information that was inaccessible to the earlier linear probes.

It contains two separate analyses.

###### Probability-moment analysis

The first analysis compresses each sorted QuIC probability vector into the seven nonconstant power sums

[
M_k(G)=\sum_z p_z(G)^k,
\qquad
k=2,\ldots,8.
]

Three regression families are then used to predict:

* 4-cycle count;
* 5-cycle count;
* 6-cycle count.

The regressors are:

1. ordinary linear least squares;
2. RBF kernel ridge regression;
3. a two-layer MLP with hidden widths ((64,64)).

Four-cycle count is the positive control because the earlier power-sum ladder showed that it is almost completely recoverable once moments through order five are included.

Five- and 6-cycle counts are the substantive targets. The question is whether their weak linear scores reflect a nonlinear relationship with the low-order power sums or whether the power-sum compression has discarded the relevant information.

### Full-vector nonlinear analysis

The second analysis applies RBF kernel ridge regression directly to the complete sorted QuIC probability vectors:

[
\mathbf p(G)\in\mathbb R^{2^n}.
]

The feature dimensions are:

[
2^{14}=16{,}384,
\qquad
2^{16}=65{,}536.
]

The nonlinear results are compared with the earlier full-vector linear ridge scores on seven targets:

* triangles;
* 4-cycles;
* 5-cycles;
* 6-cycles;
* girth;
* diameter;
* spectral gap.

Both experiments use the five frozen outer folds from the original E2 ridge-probe experiment. Kernel ridge hyperparameters are selected through five-fold inner cross-validation over:

[
\alpha\in
{10^{-10},10^{-8},10^{-6},10^{-4},10^{-2},1},
]

with three RBF bandwidths defined relative to the median squared feature distance.

##### Nonlinear prediction from probability power sums

###### (n=14)

| Target   |          Linear | RBF kernel ridge |   MLP ((64,64)) |
| -------- | --------------: | ---------------: | --------------: |
| 4-cycles | (0.997\pm0.000) |  (0.996\pm0.003) | (0.357\pm0.339) |
| 5-cycles | (0.106\pm0.048) |  (0.049\pm0.172) | (0.008\pm0.031) |
| 6-cycles | (0.198\pm0.072) |  (0.018\pm0.479) | (0.111\pm0.081) |

###### (n=16)

| Target   |          Linear | RBF kernel ridge |   MLP ((64,64)) |
| -------- | --------------: | ---------------: | --------------: |
| 4-cycles | (0.998\pm0.000) |  (0.995\pm0.007) | (0.798\pm0.013) |
| 5-cycles | (0.084\pm0.008) | (-0.169\pm0.534) | (0.024\pm0.014) |
| 6-cycles | (0.144\pm0.021) |  (0.168\pm0.018) | (0.102\pm0.021) |

##### Four-cycle control

The linear and kernel models recover 4-cycle count almost perfectly at both graph orders:

[
R^2_{\mathrm{linear}}\approx0.998,
\qquad
R^2_{\mathrm{KRR}}\approx0.995.
]

This confirms that the power-sum representation contains a strong and stable 4-cycle signal. It also shows that the RBF kernel implementation can recover target information when it is present in these features.

The MLP control is less satisfactory. It reaches only

[
R^2=0.357\pm0.339
]

at (n=14), despite the existence of an almost exact linear relationship, and improves to

[
R^2=0.798\pm0.013
]

at (n=16).

The MLP therefore does not provide a fully reliable positive control. Its poor (n=14) score is more indicative of optimization or regularization behavior than of missing information. The linear and kernel results should carry more weight in interpreting the moment experiment.

##### Five-cycle count

Five-cycle count remains essentially unrecoverable from the power sums through order eight.

At (n=14), the strongest score is the linear result:

[
R^2=0.106\pm0.048.
]

Neither nonlinear model improves on it:

[
R^2_{\mathrm{KRR}}=0.049\pm0.172,
]

[
R^2_{\mathrm{MLP}}=0.008\pm0.031.
]

At (n=16), the linear score falls to

[
0.084\pm0.008,
]

the MLP remains near zero, and kernel ridge becomes strongly unstable:

[
-0.169\pm0.534.
]

This should be contrasted with full-vector QuIC prediction:

[
R^2=0.928
\quad\text{at }n=14,
]

and

[
R^2=0.982
\quad\text{at }n=16.
]

The strong full-vector 5-cycle signal is therefore not reproduced by nonlinear functions learned from these seven low-order power sums.

The evidence supports the interpretation that 5-cycle information depends on finer structure in the sorted probability distribution rather than on the tested low-order moment coordinates alone.

## Six-cycle count

The 6-cycle results show the same general pattern.

At (n=14), linear prediction reaches

[
R^2=0.198\pm0.072.
]

The MLP performs more weakly, while kernel ridge is highly unstable:

[
R^2_{\mathrm{KRR}}=0.018\pm0.479.
]

At (n=16), kernel ridge produces a small improvement over the linear probe:

[
0.144\rightarrow0.168.
]

The improvement is only

[
\Delta R^2=0.024,
]

and the MLP remains near

[
R^2=0.102.
]

The first seven nonconstant power sums therefore contain a small amount of 6-cycle information, but no tested nonlinear readout turns them into a strong predictor.

The difference from the full-vector scores remains substantial:

[
R^2_{\mathrm{full}}=0.485
\quad\text{at }n=14,
]

and

[
R^2_{\mathrm{full}}=0.642
\quad\text{at }n=16.
]

As with 5-cycles, much of the useful signal is lost when the full probability distribution is reduced to moments through order eight.

##### What the probability-moment experiment shows

The moment results support a clear empirical distinction:

[
\boxed{
\text{low-order probability moments recover shallow cycle structure,
but not the deeper cycle signal present in the full vector}
}
]

Four-cycle count is nearly exact from the moment coordinates. Five-cycle prediction remains near zero, while 6-cycle prediction remains weak under linear, kernel, and neural readouts.

This is stronger than the earlier linear-only result because two nonlinear estimator families fail to uncover a large hidden relationship.

It does not establish that no mathematical function of these moments can determine 5- or 6-cycle count. It establishes that no useful relationship is recovered by the tested models at the available sample sizes and under the tested regularization protocol.

##### Full-vector nonlinear results

###### (n=14)

| Target       |    Linear ridge | RBF kernel ridge | Difference |
| ------------ | --------------: | ---------------: | ---------: |
| Triangles    | (1.000\pm0.000) |  (1.000\pm0.000) |   (+0.000) |
| 4-cycles     | (0.998\pm0.002) |  (0.996\pm0.003) |   (-0.002) |
| 5-cycles     | (0.928\pm0.092) |  (0.950\pm0.049) |   (+0.022) |
| 6-cycles     | (0.485\pm0.326) |  (0.703\pm0.057) |   (+0.218) |
| Girth        | (0.993\pm0.014) |  (0.993\pm0.014) |   (+0.000) |
| Diameter     | (0.548\pm0.058) |  (0.526\pm0.051) |   (-0.022) |
| Spectral gap | (0.944\pm0.010) |  (0.952\pm0.005) |   (+0.008) |

###### (n=16)

| Target       |    Linear ridge | RBF kernel ridge | Difference |
| ------------ | --------------: | ---------------: | ---------: |
| Triangles    | (1.000\pm0.000) |  (0.999\pm0.001) |   (-0.001) |
| 4-cycles     | (1.000\pm0.000) |  (0.999\pm0.000) |   (-0.001) |
| 5-cycles     | (0.982\pm0.015) |  (0.945\pm0.045) |   (-0.037) |
| 6-cycles     | (0.642\pm0.122) |  (0.613\pm0.024) |   (-0.029) |
| Girth        | (0.999\pm0.003) |  (0.998\pm0.003) |   (-0.001) |
| Diameter     | (0.737\pm0.019) |  (0.699\pm0.028) |   (-0.038) |
| Spectral gap | (0.932\pm0.007) |  (0.937\pm0.003) |   (+0.005) |

##### Saturated targets

Triangles, 4-cycles, and girth remain essentially saturated under both readouts.

Kernel ridge cannot materially improve these targets because the linear model already obtains approximately perfect prediction. The small negative differences are within the scale expected from alternative regularization and finite-fold variation.

This confirms that nonlinear readout is unnecessary for the structural layers that are already strongly aligned with linear directions in QuIC space.

##### Five-cycle count

At (n=14), kernel ridge raises the mean score from

[
0.928
]

to

[
0.950
]

and reduces the fold standard deviation from

[
0.092
]

to

[
0.049.
]

This is a modest improvement in both average accuracy and stability.

The effect does not replicate at (n=16). On the larger census, kernel ridge performs worse:

[
0.982\rightarrow0.945.
]

The (n=14) result therefore does not support a general conclusion that 5-cycle information is encoded primarily through nonlinear full-vector geometry. The larger census instead indicates that the available 5-cycle signal is already very effectively accessed by the linear ridge probe.

## Six-cycle count

The most substantial nonlinear improvement occurs for 6-cycle count at (n=14):

[
R^2:
0.485\pm0.326
\rightarrow
0.703\pm0.057.
]

The kernel model improves the mean by

[
0.218
]

and sharply reduces fold variance.

This could reflect a nonlinear relationship in the smaller census, better regularization of a difficult high-dimensional target, or both.

The effect does not replicate at (n=16):

[
0.642\pm0.122
\rightarrow
0.613\pm0.024.
]

The nonlinear model is more stable but slightly less accurate on average.

The (n=14) improvement should therefore be treated as a finite-census result rather than as evidence for a stable nonlinear 6-cycle layer. The larger dataset provides no indication that RBF kernel ridge unlocks a major source of 6-cycle information unavailable to the linear probe.

##### Diameter

Kernel ridge does not improve diameter prediction.

At (n=14),

[
0.548\rightarrow0.526,
]

and at (n=16),

[
0.737\rightarrow0.699.
]

The deficit is larger at the graph order where more training examples are available.

This suggests that the incomplete diameter prediction is not simply caused by the use of a linear readout. Under the tested RBF kernel, the full QuIC vector does not expose a stronger diameter signal.

This conclusion concerns the representation and readouts tested here. It does not establish an absolute information ceiling for all possible nonlinear estimators.

##### Spectral gap

Kernel ridge gives small improvements for spectral gap at both orders:

[
0.944\rightarrow0.952
\quad\text{at }n=14,
]

and

[
0.932\rightarrow0.937
\quad\text{at }n=16.
]

These gains are consistent in sign but small in magnitude. QuIC still does not match the exact linear accessibility of spectral gap from the sorted adjacency eigenvalues.

The result indicates minor nonlinear organization of spectral information, not a substantive change in the representation's spectral-gap capability.

##### Linear versus nonlinear accessibility

The full-vector results show no general advantage for the nonlinear kernel.

At (n=16), kernel ridge is weaker on six of the seven targets and improves only spectral gap by a negligible amount. The strongest QuIC results—triangles, 4-cycles, 5-cycles, and girth—are therefore not artifacts of restricting the readout to a linear model.

For the tested targets, the dominant structural content of the full QuIC vector is already organized in a form that ridge regression can access efficiently.

The nonlinear model occasionally changes finite-sample bias and variance, particularly for 6-cycles at (n=14), but it does not reveal a reproducible hidden layer of target information.

##### What the experiment establishes

The completed results support four principal conclusions.

1. **Low-order probability moments do not explain the full-vector 5- and 6-cycle results.**
   Linear, RBF-kernel, and MLP readouts on the power sums through order eight remain weak for both targets.

2. **The strong 5-cycle signal is carried by finer probability-distribution structure.**
   Full-vector prediction reaches (R^2=0.982) at (n=16), while every tested moment-based model remains near zero.

3. **Nonlinear full-vector readout provides no consistent improvement over linear ridge.**
   The largest gain occurs for 6-cycles at (n=14), but it does not replicate at (n=16).

4. **The incomplete diameter and 6-cycle scores are not resolved by the tested RBF kernel.**
   Their limitations cannot be attributed solely to the use of a linear probe.

The experiment therefore separates two questions:

* nonlinear models do not recover the information discarded by low-order moment compression;
* nonlinear models also do not systematically improve prediction once the complete QuIC vector is retained.

##### Necessary qualifications

The code uses seven nonconstant probability power sums:

[
k=2,\ldots,8.
]

Descriptions such as “eight power sums” should be replaced by “power sums through order eight” or “seven nonconstant power sums.” The (k=1) power sum is the constant normalization condition

[
\sum_z p_z=1.
]

The moment experiment does not prove that no function of these power sums can recover 5- or 6-cycle count. Kernel ridge and finite-width MLPs are flexible estimators, but negative finite-sample performance is not a mathematical nonexistence result.

The MLP's weak performance on the 4-cycle control, particularly at (n=14), shows that its training procedure does not reliably recover even an available simple relationship. Its negative C5 and C6 results should therefore be treated as corroborating evidence rather than as a decisive test.

The power-sum features are standardized using the complete census before the outer folds are evaluated. In addition, the RBF bandwidth grid is anchored using the median distance over the complete dataset. Both operations use unlabeled test-fold feature information. This is a mild transductive leakage and should be replaced with fold-local scaling and outer-training-only bandwidth estimation in a strict cross-validation implementation.

The full-vector analysis tests one nonlinear family with a limited bandwidth and regularization grid. Failure of this RBF kernel to improve prediction does not establish the absolute nonlinear ceiling of the representation.

No paired foldwise significance analysis is reported. Differences such as

[
+0.022,\quad +0.008,\quad -0.029
]

should be interpreted descriptively. The (n=14) 6-cycle difference is larger, but its failure to replicate remains the more important result.

The reported MLP standard deviations summarize 15 seed-fold evaluations, whereas linear and kernel scores summarize five folds. Their uncertainty values are therefore not directly comparable.

Finally, all results use exact ideal probability vectors. They characterize representational accessibility rather than finite-shot sample complexity or hardware-level performance.

##### Overall assessment

The probability-moment experiment provides the more important result.

Four-cycle count remains nearly exact under both linear and nonlinear readouts, confirming that shallow-cycle information is present in the low-order moment coordinates. Five- and 6-cycle prediction remains weak across estimator families, while the complete QuIC vector predicts the same targets much more strongly.

The natural interpretation is that deeper cycle information depends on the detailed shape and ordering statistics of the probability spectrum rather than on a small collection of global power sums.

The full-vector nonlinear analysis is largely negative. RBF kernel ridge does not systematically improve upon linear ridge and performs worse on most targets in the larger (n=16) census. The (n=14) 6-cycle improvement is substantial but does not replicate.

The appropriate central claim is:

> Across the complete connected cubic-graph censuses at (n=14) and (n=16), the strong QuIC 5-cycle signal and the weaker 6-cycle signal cannot be reproduced from probability power sums through order eight using linear, RBF-kernel, or MLP readouts. Once the complete probability vector is retained, RBF kernel ridge provides no consistent advantage over linear ridge, indicating that most of the accessible structural information is already organized in approximately linear form.


### E6 - Irregular Graphs
## Experimental design

This experiment tests whether the structural accessibility observed for cubic graphs persists when QuIC is applied to nonregular graphs without explicitly encoding vertex degrees.

The dataset contains four fixed-degree-sequence strata at (n=14), with 400 connected, nonisomorphic graphs per stratum:

| Stratum          | Degree sequence                     | Edges | Maximum degree |
| ---------------- | ----------------------------------- | ----: | -------------: |
| S1: near-regular | ((4,4,3^{\times10},2,2))            |    21 |              4 |
| S2: bimodal      | ((4^{\times7},2^{\times7}))         |    21 |              4 |
| S3: skewed       | ((5,5,4,4,3^{\times6},2^{\times4})) |    22 |              5 |
| S4: hub          | ((6,4,4,3^{\times8},2,2,2))         |    22 |              6 |

Graphs are generated using degree-preserving connected double-edge swaps and deduplicated through canonical graph6 representations.

The circuit uses the same flat initialization that arises automatically on cubic graphs:

[
R_X(2.875)
]

on every qubit, followed by one round of:

* (R_{ZZ}(2.0)) on each graph edge;
* a uniform (R_X(0.1)) mixer.

The encoder deliberately ignores vertex degree. This keeps the circuit map consistent with the cubic experiments and prevents nonregular graphs from receiving degree information as an explicit node feature.

For each target, four representations are evaluated:

1. sorted adjacency eigenvalues;
2. adjacency trace moments
   [
   \operatorname{tr}(A^k),\qquad k=3,\ldots,8;
   ]
3. the full sorted QuIC probability vector;
4. QuIC concatenated with a rescaled eigenvalue block.

All analyses are performed separately within each fixed-degree-sequence stratum. Five frozen outer folds and nested ridge regularization are used.

The reported differences are:

[
\Delta_{\mathrm{QuIC}}
======================

## R^2_{\mathrm{QuIC}}

\max(R^2_{\mathrm{eig}},R^2_{\mathrm{moments}}),
]

and

[
\Delta_{\mathrm{concat}}
========================

## R^2_{\mathrm{concat}}

\max(R^2_{\mathrm{eig}},R^2_{\mathrm{moments}}).
]

## Dataset construction and viability

The sampler produced nearly complete uniqueness among its 600 candidates:

| Stratum | Distinct candidates | Retained graphs |
| ------- | ------------------: | --------------: |
| S1      |             600/600 |             400 |
| S2      |             593/600 |             400 |
| S3      |             600/600 |             400 |
| S4      |             600/600 |             400 |

All 1,600 retained graphs are connected, have the required degree sequence, and possess distinct canonical graph6 strings.

The live cycle targets have substantial within-stratum variation:

| Stratum | C5 range | C5 standard deviation | C6 range | C6 standard deviation |
| ------- | -------: | --------------------: | -------: | --------------------: |
| S1      |      0–9 |                 1.840 |     1–16 |                 2.323 |
| S2      |     0–13 |                 2.266 |     0–18 |                 3.147 |
| S3      |     1–14 |                 2.484 |     2–22 |                 3.299 |
| S4      |     1–14 |                 2.353 |     2–25 |                 3.339 |

No target is constant within any stratum, although girth and radius have relatively little variation in several strata.

The stored vectors pass normalization, sortedness, degree-sequence, and trace-identity checks. Independent NumPy circuit reconstructions agree with the stored vectors to maximum coordinate errors between

[
4.51\times10^{-17}
]

and

[
1.33\times10^{-15}.
]

The results therefore correspond to the intended flat-encoder circuit.

## Main results

### S1: near-regular

| Target       |      Eigenvalues |         Moments |             QuIC |      QuIC + eig. | (\Delta_{\mathrm{QuIC}}) | (\Delta_{\mathrm{concat}}) |
| ------------ | ---------------: | --------------: | ---------------: | ---------------: | -----------------------: | -------------------------: |
| C3           |  (0.990\pm0.002) | (1.000\pm0.000) |  (0.449\pm0.714) |  (0.989\pm0.002) |                 (-0.551) |                   (-0.011) |
| C4           |  (0.968\pm0.006) | (1.000\pm0.000) |  (0.095\pm0.048) |  (0.967\pm0.006) |                 (-0.905) |                   (-0.033) |
| C5           |  (0.723\pm0.050) | (0.802\pm0.037) | (-0.017\pm0.056) |  (0.863\pm0.045) |                 (-0.819) |                   (+0.061) |
| C6           |  (0.669\pm0.052) | (0.757\pm0.015) | (-0.021\pm0.012) |  (0.661\pm0.058) |                 (-0.778) |                   (-0.096) |
| Girth        |  (0.468\pm0.048) | (0.343\pm0.072) |  (0.007\pm0.228) |  (0.436\pm0.063) |                 (-0.461) |                   (-0.032) |
| Diameter     |  (0.372\pm0.069) | (0.369\pm0.089) | (-0.093\pm0.122) |  (0.257\pm0.146) |                 (-0.465) |                   (-0.115) |
| Radius       | (-0.005\pm0.026) | (0.028\pm0.044) | (-0.064\pm0.077) | (-0.033\pm0.018) |                 (-0.092) |                   (-0.061) |
| Wiener index |  (0.790\pm0.051) | (0.841\pm0.025) |  (0.184\pm0.147) |  (0.754\pm0.083) |                 (-0.657) |                   (-0.087) |
| Spectral gap |  (1.000\pm0.000) | (0.891\pm0.009) |  (0.389\pm0.061) |  (1.000\pm0.000) |                 (-0.611) |                   (-0.000) |

### S2: bimodal

| Target       |     Eigenvalues |          Moments |             QuIC |      QuIC + eig. | (\Delta_{\mathrm{QuIC}}) | (\Delta_{\mathrm{concat}}) |
| ------------ | --------------: | ---------------: | ---------------: | ---------------: | -----------------------: | -------------------------: |
| C3           | (0.987\pm0.004) |  (1.000\pm0.000) |  (0.991\pm0.001) |  (0.991\pm0.002) |                 (-0.009) |                   (-0.009) |
| C4           | (0.963\pm0.005) |  (1.000\pm0.000) |  (0.295\pm0.137) |  (0.962\pm0.004) |                 (-0.705) |                   (-0.038) |
| C5           | (0.611\pm0.079) |  (0.716\pm0.088) |  (0.284\pm0.135) |  (0.834\pm0.031) |                 (-0.432) |                   (+0.118) |
| C6           | (0.667\pm0.058) |  (0.710\pm0.016) |  (0.296\pm0.150) |  (0.693\pm0.109) |                 (-0.415) |                   (-0.018) |
| Girth        | (0.159\pm0.130) |  (0.045\pm0.297) | (-0.014\pm0.044) |  (0.140\pm0.097) |                 (-0.173) |                   (-0.019) |
| Diameter     | (0.280\pm0.127) |  (0.316\pm0.128) |  (0.110\pm0.052) |  (0.284\pm0.118) |                 (-0.206) |                   (-0.032) |
| Radius       | (0.008\pm0.082) | (-0.010\pm0.150) | (-0.070\pm0.323) | (-0.118\pm0.340) |                 (-0.078) |                   (-0.126) |
| Wiener index | (0.770\pm0.055) |  (0.813\pm0.061) |  (0.409\pm0.120) |  (0.833\pm0.027) |                 (-0.404) |                   (+0.019) |
| Spectral gap | (1.000\pm0.000) |  (0.870\pm0.043) |  (0.595\pm0.123) |  (1.000\pm0.000) |                 (-0.405) |                   (-0.000) |

### S3: skewed

| Target       |     Eigenvalues |         Moments |             QuIC |     QuIC + eig. | (\Delta_{\mathrm{QuIC}}) | (\Delta_{\mathrm{concat}}) |
| ------------ | --------------: | --------------: | ---------------: | --------------: | -----------------------: | -------------------------: |
| C3           | (0.990\pm0.002) | (1.000\pm0.000) | (-0.047\pm0.042) | (0.990\pm0.002) |                 (-1.047) |                   (-0.010) |
| C4           | (0.966\pm0.005) | (1.000\pm0.000) | (-0.018\pm0.025) | (0.965\pm0.006) |                 (-1.018) |                   (-0.035) |
| C5           | (0.674\pm0.046) | (0.707\pm0.031) | (-0.019\pm0.017) | (0.687\pm0.034) |                 (-0.726) |                   (-0.020) |
| C6           | (0.600\pm0.041) | (0.645\pm0.045) | (-0.023\pm0.019) | (0.630\pm0.035) |                 (-0.668) |                   (-0.015) |
| Girth        | (0.166\pm0.050) | (0.091\pm0.031) | (-0.017\pm0.028) | (0.083\pm0.028) |                 (-0.183) |                   (-0.083) |
| Diameter     | (0.262\pm0.049) | (0.255\pm0.049) |  (0.019\pm0.062) | (0.249\pm0.051) |                 (-0.243) |                   (-0.013) |
| Radius       | (0.095\pm0.040) | (0.056\pm0.031) | (-0.013\pm0.038) | (0.071\pm0.054) |                 (-0.108) |                   (-0.024) |
| Wiener index | (0.792\pm0.053) | (0.798\pm0.052) |  (0.097\pm0.049) | (0.790\pm0.051) |                 (-0.701) |                   (-0.008) |
| Spectral gap | (1.000\pm0.000) | (0.922\pm0.017) |  (0.153\pm0.128) | (1.000\pm0.000) |                 (-0.847) |                   (-0.000) |

### S4: hub

| Target       |      Eigenvalues |         Moments |             QuIC |      QuIC + eig. | (\Delta_{\mathrm{QuIC}}) | (\Delta_{\mathrm{concat}}) |
| ------------ | ---------------: | --------------: | ---------------: | ---------------: | -----------------------: | -------------------------: |
| C3           |  (0.988\pm0.003) | (1.000\pm0.000) |  (0.378\pm0.161) |  (0.987\pm0.004) |                 (-0.622) |                   (-0.013) |
| C4           |  (0.964\pm0.007) | (1.000\pm0.000) | (-0.034\pm0.079) |  (0.963\pm0.007) |                 (-1.034) |                   (-0.037) |
| C5           |  (0.569\pm0.076) | (0.625\pm0.060) | (-0.050\pm0.057) |  (0.603\pm0.068) |                 (-0.675) |                   (-0.021) |
| C6           |  (0.603\pm0.120) | (0.651\pm0.093) | (-0.038\pm0.038) |  (0.604\pm0.132) |                 (-0.688) |                   (-0.046) |
| Girth        | (-0.008\pm0.240) | (0.009\pm0.222) | (-0.017\pm0.020) | (-0.036\pm0.203) |                 (-0.026) |                   (-0.045) |
| Diameter     |  (0.214\pm0.092) | (0.182\pm0.082) | (-0.028\pm0.021) |  (0.164\pm0.080) |                 (-0.242) |                   (-0.051) |
| Radius       |  (0.119\pm0.117) | (0.125\pm0.105) | (-0.035\pm0.023) |  (0.106\pm0.133) |                 (-0.160) |                   (-0.019) |
| Wiener index |  (0.796\pm0.068) | (0.827\pm0.058) |  (0.075\pm0.075) |  (0.795\pm0.068) |                 (-0.752) |                   (-0.032) |
| Spectral gap |  (1.000\pm0.000) | (0.884\pm0.028) |  (0.167\pm0.080) |  (1.000\pm0.000) |                 (-0.833) |                   (-0.000) |

## Equal-weight aggregate

The aggregate is the unweighted mean of the four stratum-level means. It is not a pooled regression across all 1,600 graphs.

| Target       | Eigenvalues | Moments |     QuIC | QuIC + eig. | (\Delta_{\mathrm{QuIC}}) | (\Delta_{\mathrm{concat}}) |
| ------------ | ----------: | ------: | -------: | ----------: | -----------------------: | -------------------------: |
| C3           |       0.989 |   1.000 |    0.443 |       0.989 |                 (-0.557) |                   (-0.011) |
| C4           |       0.965 |   1.000 |    0.085 |       0.964 |                 (-0.915) |                   (-0.036) |
| C5           |       0.644 |   0.712 |    0.050 |       0.747 |                 (-0.663) |                   (+0.035) |
| C6           |       0.635 |   0.691 |    0.053 |       0.647 |                 (-0.637) |                   (-0.044) |
| Girth        |       0.196 |   0.122 | (-0.010) |       0.156 |                 (-0.211) |                   (-0.045) |
| Diameter     |       0.282 |   0.281 |    0.002 |       0.238 |                 (-0.289) |                   (-0.053) |
| Radius       |       0.054 |   0.050 | (-0.045) |       0.006 |                 (-0.109) |                   (-0.058) |
| Wiener index |       0.787 |   0.820 |    0.191 |       0.793 |                 (-0.629) |                   (-0.027) |
| Spectral gap |       1.000 |   0.892 |    0.326 |       1.000 |                 (-0.674) |                   (-0.000) |

## Consistency controls

The classical controls behave as required.

For every graph,

[
\operatorname{tr}(A^3)=6C_3.
]

Therefore the moment probe obtains:

[
R^2=1.000
]

for triangle count in every stratum.

For general graphs,

[
\operatorname{tr}(A^4)
======================

8C_4
+
2\sum_v d_v^2
-------------

\sum_v d_v.
]

Because the complete degree sequence is fixed within each stratum, both degree-dependent terms are constant. The moment probe therefore also obtains:

[
R^2=1.000
]

for 4-cycle count in every stratum.

The sorted-eigenvalue probe obtains:

[
R^2=1.000
]

for spectral gap in all four strata, as expected.

These rows validate the dataset, target computations, spectral features, and cross-validation pipeline.

They also demonstrate an important coordinate effect. The sorted eigenvalue representation reaches only approximately (0.96)–(0.99) on C3 and C4 despite containing the same spectral information. The moment coordinates expose the relevant power sums directly and make the relationships linear.

## Five-cycle count

C5 is the primary live target because the simple cubic identity relating (\operatorname{tr}(A^5)) to C3 and C5 no longer applies on nonregular graphs.

The spectral baselines remain moderately strong but no longer exact:

[
R^2_{\mathrm{moments}}
======================

0.802,\ 0.716,\ 0.707,\ 0.625
]

across S1 through S4.

The decline from S1 to S4 suggests that the moment coordinates become less sufficient as the degree distribution permits more heterogeneous local configurations. This is descriptive rather than a monotonic theorem, but the pattern is consistent across the selected strata.

QuIC alone does not retain the strong C5 accessibility observed on cubic graphs:

[
R^2_{\mathrm{QuIC}}
===================

-0.017,\ 0.284,\ -0.019,\ -0.050.
]

Only the bimodal stratum contains a meaningful standalone signal.

The concatenated representation gives a more nuanced result.

For the two maximum-degree-4 strata:

[
\Delta R^2_{\mathrm{concat}}
============================

+0.061
\quad\text{and}\quad
+0.118.
]

In S1, QuIC has essentially no standalone C5 accessibility but improves the eigenvalue representation enough to exceed the stronger moment baseline. This indicates conditional or complementary structure that is not useful in isolation.

In S2, QuIC has both a moderate standalone signal and a larger complementary contribution.

The result does not persist in the more degree-skewed strata:

[
\Delta R^2_{\mathrm{concat}}
============================

-0.020
\quad\text{and}\quad
-0.021.
]

The aggregate gain is therefore only:

[
+0.035.
]

The defensible conclusion is that QuIC contributes limited complementary C5 information in two strata, but the effect is not robust across all four fixed-degree-sequence families.

## Six-cycle count

The spectral moment probe remains moderately strong for C6:

[
R^2=0.645\text{--}0.757.
]

QuIC alone is near zero in three strata and reaches only:

[
R^2=0.296
]

in S2.

The concatenated representation fails to outperform the best spectral baseline in every stratum:

[
\Delta R^2_{\mathrm{concat}}
============================

-0.096,\ -0.018,\ -0.015,\ -0.046.
]

There is therefore no evidence that the flat QuIC representation supplies useful additional C6 information beyond the tested spectral coordinates on these graph families.

This contrasts with the cubic residual experiment, where QuIC recovered part of the spectral residual associated with the C6–diamond decomposition. That effect does not transfer automatically to nonregular fixed-degree-sequence strata.

## Metric targets

### Girth

Girth has little variation within the strata, usually taking only the values three and four.

The best spectral scores range from approximately zero to (0.47). QuIC remains near zero in all four strata, and concatenation does not improve the best spectral result.

The near-perfect cubic girth accessibility therefore disappears under the flat nonregular experiment.

### Diameter

Eigenvalue and moment probes obtain modest scores:

[
R^2\approx0.18\text{--}0.37.
]

QuIC is approximately uninformative:

[
R^2=-0.093,\ 0.110,\ 0.019,\ -0.028.
]

Concatenation reduces performance in every stratum.

### Radius

Radius is poorly accessible from all tested representations. Spectral scores remain near zero, and QuIC scores are negative in all four strata.

The target also has limited spread, particularly in S1, so these values should be treated as evidence of no detected signal rather than a precise performance hierarchy.

### Wiener index

The Wiener index is strongly linearly accessible from the spectral features:

[
R^2_{\mathrm{moments}}
======================

0.798\text{--}0.841.
]

QuIC alone ranges from:

[
0.075
]

to

[
0.409.
]

The only positive concatenation difference is the small S2 gain:

[
\Delta R^2=+0.019.
]

This does not replicate across the other strata. The aggregate concatenated score remains below the aggregate moment score.

## Spectral gap

The eigenvalue representation recovers spectral gap exactly, while QuIC obtains:

[
R^2=
0.389,\ 0.595,\ 0.153,\ 0.167.
]

These values show that the flat QuIC vector retains some adjacency-spectral information, especially in S2, but far less than it retained on the cubic census.

Adding the exact eigenvalue coordinate restores perfect performance, as expected.

## Comparison with the cubic census

The same flat encoder is used implicitly on cubic graphs because every vertex has the same degree. The change in performance is therefore not caused by changing the initial rotation angle or circuit depth.

| Target       | Cubic (n=14) QuIC | E6 aggregate QuIC |
| ------------ | ----------------: | ----------------: |
| C3           |             1.000 |             0.443 |
| C4           |             0.998 |             0.085 |
| C5           |             0.928 |             0.050 |
| C6           |             0.485 |             0.053 |
| Girth        |             0.993 |          (-0.010) |
| Diameter     |             0.548 |             0.002 |
| Spectral gap |             0.944 |             0.326 |

The short-cycle hierarchy observed on cubic graphs does not transfer to these nonregular families under the unchanged flat encoder.

The failure is especially clear for C4 and C5. Both were strongly linearly accessible from cubic QuIC vectors, but their aggregate E6 scores fall to approximately zero.

The S2 triangle result shows that the circuit is not uniformly uninformative on every nonregular family. Instead, accessibility is highly dependent on the degree-sequence stratum.

## Interpretation

The results are consistent with regularity playing a central role in the cubic QuIC geometry.

On cubic graphs:

* all vertices begin with the same encoder angle because their degrees are identical;
* local walk-count identities simplify;
* degree-related structural variation is absent;
* sorted probabilities can organize the remaining topology along a small number of dominant directions.

On nonregular graphs, the flat encoder deliberately treats degree-2, degree-4, degree-5, and degree-6 vertices identically before entanglement. The circuit must infer all degree-role information indirectly through the edge interactions.

After the probabilities are sorted, coordinate identities are also discarded. The resulting representation may therefore lose access to which portions of the amplitude distribution arose from high-degree or low-degree structural roles.

This offers a plausible explanation for the collapse in linear accessibility, but it is an interpretation rather than a causal result. A direct comparison with the degree-proportional encoder would be required to isolate the effect of degree injection.

The experiment should therefore not be interpreted as showing that QuIC generally fails on nonregular graphs. It shows that the **flat-start QuIC representation characterized on cubic graphs is not robustly transferable to nonregular fixed-degree-sequence strata without degree encoding**.

## What the experiment establishes

The completed results support five main conclusions.

1. **The dataset and analysis pipeline behave correctly.**
   Exact C3 and C4 moment identities and exact spectral-gap decoding are recovered in every stratum.

2. **The strong cubic QuIC hierarchy is not robust off the regular manifold.**
   Standalone QuIC accessibility collapses for nearly every target across the four nonregular strata.

3. **Classical spectral coordinates remain substantially stronger.**
   Adjacency moments dominate QuIC for C3 through C6 and the Wiener index, while eigenvalues exactly recover spectral gap.

4. **C5 contains limited conditional QuIC information.**
   QuIC plus eigenvalues exceeds the strongest spectral baseline in S1 and S2, but the gain disappears in S3 and S4.

5. **No corresponding complementarity appears for C6 or the metric targets.**
   Concatenation generally matches or degrades the spectral baseline.

The experiment is therefore primarily a negative robustness result, with a restricted positive C5 interaction in two degree-sequence families.

## Necessary qualifications

The four strata are sampled rather than exhaustively enumerated. Each stratum is generated from one degree-preserving swap chain. Canonical deduplication guarantees distinct graphs, but no mixing-time or autocorrelation analysis establishes that the 400 graphs are uniform or statistically independent samples from the realization space.

Only four hand-selected degree sequences at (n=14) are tested. The results should not be generalized to all nonregular graphs or larger graph orders.

The flat encoder is deliberately atypical for practical nonregular use. Degree-proportional encoding may restore substantial accessibility by supplying vertex-degree information. That arm is not evaluated here.

The concatenated representation contains QuIC plus eigenvalues, but not the adjacency moment block. Its score is nevertheless compared against the better of eigenvalues and moments. Positive (\Delta_{\mathrm{concat}}) is therefore conservative, but negative values do not directly establish that QuIC contains no information beyond the full spectral feature set. A cleaner complementarity test would concatenate QuIC with both spectral blocks or fit a cross-fitted residual model.

The run emits repeated ill-conditioned-matrix warnings during ridge fitting. The alpha grid extends to (10^{-14}), and the QuIC feature matrix has 16,384 columns but only 320 training graphs per outer fold. The main negative results are large enough to be qualitatively clear, but the exact QuIC and concatenated scores should be verified with a numerically stable solver or a safer regularization range.

The large S1 triangle variance,

[
0.449\pm0.714,
]

is a visible example of fold instability.

No paired statistical tests are reported for the fold-level differences. The C5 gains of (+0.061) and (+0.118) are descriptively meaningful, but their uncertainty should be evaluated directly before making inferential claims.

Finally, several metric targets have low within-stratum variance. In particular, girth is nearly binary and radius occupies a narrow range. Cross-validated (R^2) is correspondingly sensitive to fold composition.

## Overall assessment

This experiment sharply limits the scope of the cubic results.

The flat QuIC circuit retains exceptional short-cycle accessibility on connected cubic graphs, but that structure largely disappears once the graph family becomes nonregular. Across four fixed-degree-sequence strata, QuIC alone is substantially weaker than the spectral baselines on every target and is approximately uninformative for C4, C5, C6, girth, diameter, and radius.

The only substantive positive result is conditional C5 complementarity in S1 and S2. In those strata, adding QuIC to the eigenvalue representation raises performance above the stronger moment baseline by (0.061) and (0.118). The effect does not survive in the skewed and hub strata.

The appropriate central claim is:

> The structural hierarchy observed for flat-start QuIC on cubic graphs is not robust to nonregular fixed-degree-sequence families. Without explicit degree encoding, QuIC loses most standalone linear accessibility to cycle and metric invariants, while classical spectral coordinates remain substantially stronger. QuIC contributes limited complementary C5 information in two maximum-degree-4 strata, but no consistent advantage appears across all four families.

### E7 - Truncation


##### Experimental design

This experiment measures how much of QuIC’s cycle-count information is retained when the sorted probability vector is truncated to its (k) largest entries.

The analysis uses the complete connected cubic-graph censuses at:

* (n=14): 509 graphs;
* (n=16): 4,060 graphs.

For each graph, the full QuIC representation is the descending sorted probability vector

[
\mathbf p(G)
============

\left(
p_{(1)},p_{(2)},\ldots,p_{(2^n)}
\right),
\qquad
p_{(1)}\ge p_{(2)}\ge\cdots.
]

The truncated representation is

[
\mathbf p_k(G)
==============

\left(
p_{(1)},\ldots,p_{(k)}
\right).
]

The tested truncation lengths are:

[
k\in
{25,50,100,200,400,1000,4000},
]

plus the full (16{,}384)-dimensional vector at (n=14).

The (n=16) run completed through (k=4000) but did not reach the full (65{,}536)-dimensional point before termination.

Four cycle-count targets are evaluated:

* triangles;
* 4-cycles;
* 5-cycles;
* 6-cycles.

Each score is produced using the same five shuffled folds and nested ridge-regression protocol as the earlier E2 analysis.

##### Completed results

###### (n=14)

|    (k) |       Triangles |        4-cycles |         5-cycles |        6-cycles |
| -----: | --------------: | --------------: | ---------------: | --------------: |
|     25 | (1.000\pm0.000) | (0.957\pm0.009) |  (0.034\pm0.062) | (0.163\pm0.056) |
|     50 | (1.000\pm0.000) | (0.988\pm0.004) | (-0.026\pm0.036) | (0.228\pm0.077) |
|    100 | (1.000\pm0.000) | (0.993\pm0.004) |  (0.272\pm0.142) | (0.235\pm0.079) |
|    200 | (1.000\pm0.000) | (0.995\pm0.003) |  (0.920\pm0.081) | (0.391\pm0.083) |
|    400 | (1.000\pm0.000) | (0.998\pm0.002) |  (0.927\pm0.092) | (0.478\pm0.113) |
|  1,000 | (1.000\pm0.000) | (0.998\pm0.002) |  (0.928\pm0.092) | (0.484\pm0.327) |
|  4,000 | (1.000\pm0.000) | (0.998\pm0.002) |  (0.928\pm0.092) | (0.485\pm0.326) |
| 16,384 | (1.000\pm0.000) | (0.998\pm0.002) |  (0.928\pm0.092) | (0.485\pm0.326) |

###### (n=16)

|   (k) |       Triangles |        4-cycles |        5-cycles |        6-cycles |
| ----: | --------------: | --------------: | --------------: | --------------: |
|    25 | (1.000\pm0.000) | (0.968\pm0.011) | (0.169\pm0.031) | (0.126\pm0.014) |
|    50 | (1.000\pm0.000) | (0.981\pm0.003) | (0.167\pm0.032) | (0.179\pm0.013) |
|   100 | (1.000\pm0.000) | (0.996\pm0.001) | (0.335\pm0.041) | (0.184\pm0.011) |
|   200 | (1.000\pm0.000) | (0.998\pm0.002) | (0.743\pm0.060) | (0.190\pm0.027) |
|   400 | (1.000\pm0.000) | (0.998\pm0.003) | (0.981\pm0.015) | (0.363\pm0.023) |
| 1,000 | (1.000\pm0.000) | (1.000\pm0.000) | (0.982\pm0.015) | (0.640\pm0.121) |
| 4,000 | (1.000\pm0.000) | (1.000\pm0.000) | (0.982\pm0.015) | (0.642\pm0.122) |

##### Triangle count

Triangle prediction is completely preserved at the smallest tested truncation:

[
R^2=1.000
]

using only the 25 largest probabilities at both graph orders.

Those 25 coordinates represent:

[
\frac{25}{16{,}384}\approx0.153%
]

of the (n=14) vector, and

[
\frac{25}{65{,}536}\approx0.038%
]

of the (n=16) vector.

The experiment does not determine whether fewer than 25 coordinates would suffice, because no smaller truncation was tested. It does establish that the triangle signal is concentrated extremely strongly in the probability head.

This agrees with the earlier probability-moment results, where triangle count was almost exactly recoverable from the lowest power sums. Both experiments indicate that triangle count primarily controls coarse concentration properties of the sorted distribution.

##### Four-cycle count

Four-cycle information is also highly head-concentrated, although less completely than triangle information.

At (k=25), the scores are already:

[
R^2=0.957
\quad\text{at }n=14,
]

and

[
R^2=0.968
\quad\text{at }n=16.
]

By (k=100), performance reaches:

[
0.993
\quad\text{and}\quad
0.996.
]

The remaining coordinates produce little additional improvement.

Thus, approximately 100 leading probabilities are sufficient to retain nearly all linearly accessible 4-cycle information. This corresponds to:

[
0.61%
]

of the (n=14) vector and only

[
0.15%
]

of the (n=16) vector.

The result is consistent with the power-sum ladder, where 4-cycle count became essentially exact using low-order global summaries. Its information is distributed more broadly than the triangle signal but remains concentrated near the probability head.

##### Five-cycle count

Five-cycle count exhibits a distinct truncation threshold.

At (n=14), the score remains weak through (k=100):

[
R^2=0.272\pm0.142.
]

It then rises sharply at (k=200):

[
R^2=0.920\pm0.081,
]

and reaches its full-vector value by approximately (k=400).

At (n=16), the transition occurs later:

[
R^2=0.335
\quad\text{at }k=100,
]

[
R^2=0.743
\quad\text{at }k=200,
]

and

[
R^2=0.981
\quad\text{at }k=400.
]

The score then remains unchanged through (k=4000).

The 5-cycle information is therefore not spread uniformly throughout the complete vector. It becomes accessible after a relatively narrow rank window is included:

[
k\approx200\text{--}400.
]

This differs from the gradual accumulation expected if every additional tail coordinate contributed a small independent amount of information. The sharp rise suggests that the relevant probability-spectrum structure is concentrated around a specific portion of the sorted head.

At (n=16), 400 coordinates constitute only:

[
\frac{400}{65{,}536}\approx0.61%
]

of the full representation.

The strong full-vector 5-cycle result therefore does not require most of the exponentially large probability vector. It does, however, require substantially more than the first 50–100 entries that already solve triangles and 4-cycles.

## Six-cycle count

Six-cycle information is the deepest and most diffusely represented of the four tested targets.

At (n=14), performance rises gradually:

[
0.163
\rightarrow
0.228
\rightarrow
0.235
\rightarrow
0.391
\rightarrow
0.478
]

as (k) increases from 25 to 400.

The mean then saturates near the full-vector result:

[
R^2\approx0.485.
]

At (n=16), the early head contains little 6-cycle information:

[
R^2=0.126
\quad\text{at }k=25,
]

and only

[
R^2=0.190
]

at (k=200).

The score rises to

[
0.363
]

at (k=400), followed by a large jump to

[
0.640
]

at (k=1000.
]

Increasing to (k=4000) produces almost no further gain:

[
0.642.
]

The 6-cycle signal therefore extends considerably farther into the probability vector than the C3–C5 signals, but it still saturates within the first approximately 1,000 entries.

At (n=16), this is only:

[
\frac{1000}{65{,}536}\approx1.53%
]

of the full vector.

The (n=14) results also reveal a bias–variance effect. At (k=400),

[
R^2=0.478\pm0.113,
]

which is almost the same mean as the full-vector result:

[
0.485\pm0.326.
]

Adding the tail beyond (k=400) contributes almost no average predictive value but substantially increases fold variability. For this target and census, truncation acts as an effective regularizer.

## Rank-stratified structural hierarchy

The truncation curves reveal a clear ordering in the amount of the probability head required for each structural layer:

[
\boxed{
C_3
;\rightarrow;
C_4
;\rightarrow;
C_5
;\rightarrow;
C_6
}
]

A practical summary is:

| Target    | Approximate saturation scale |
| --------- | ---------------------------: |
| Triangles |                     (k\le25) |
| 4-cycles  |                (k\approx100) |
| 5-cycles  |    (k\approx200\text{--}400) |
| 6-cycles  |   (k\approx400\text{--}1000) |

The hierarchy should be interpreted as a rank-depth ordering, not as a strict ordering of (R^2) at every small (k).

For example, at (n=14), the 6-cycle score exceeds the 5-cycle score at (k=25) and (k=50). The meaningful pattern is that each target reaches its eventual predictive plateau at progressively larger truncation lengths.

##### Scaling from (n=14) to (n=16)

The ambient representation dimension increases by a factor of four:

[
16{,}384
\rightarrow
65{,}536.
]

The truncation length needed to retain each target increases much more slowly.

* Triangle count remains exact at (k=25).
* Four-cycle count remains nearly saturated by (k=100).
* Five-cycle saturation shifts from approximately (k=200)–400 to approximately (k=400).
* Six-cycle saturation remains near (k=1000).

Consequently, the fraction of the full vector required for each target decreases as (n) increases.

For example:

|   (k) | Fraction at (n=14) | Fraction at (n=16) |
| ----: | -----------------: | -----------------: |
|    25 |             0.153% |             0.038% |
|   100 |             0.610% |             0.153% |
|   400 |             2.441% |             0.610% |
| 1,000 |             6.104% |             1.526% |
| 4,000 |            24.414% |             6.104% |

With only two graph orders, this does not establish an asymptotic scaling law. It does show that the usable structural information does not expand proportionally with the ambient (2^n)-dimensional state vector over the tested range.

##### Compact representations

The experiment identifies several useful operating points.

###### (k=25)

Using only 25 probabilities preserves:

* exact triangle prediction;
* (R^2\approx0.96\text{--}0.97) for 4-cycles.

It does not preserve meaningful 5- or 6-cycle prediction.

###### (k=100)

Using 100 probabilities preserves:

* exact triangle prediction;
* nearly complete 4-cycle prediction;
* only partial 5-cycle information;
* weak 6-cycle information.

This is approximately dimension matched to the 64-dimensional GNN embeddings used in the E3 experiment. At this scale, truncated QuIC remains exceptionally strong on triangles and 4-cycles but does not retain its full-vector advantage for deeper cycles.

###### (k=400)

Using 400 probabilities preserves:

* all triangle and 4-cycle information;
* essentially all 5-cycle information;
* most of the (n=14) 6-cycle signal;
* approximately 57% of the (n=16) full 6-cycle score.

###### (k=1000)

Using 1,000 probabilities preserves essentially all observed cycle-count performance at both graph orders.

The remaining tail—from coordinate 1,001 through 16,384 or 65,536—adds no material predictive value for the tested cycle targets.

## Relation to the probability-moment results

The truncation and moment experiments address different forms of compression.

Power sums reduce the entire probability vector to a few global scalars:

[
\sum_zp_z^k.
]

Truncation retains the detailed shape of the largest probabilities but discards the long tail.

The results show that:

* triangles and 4-cycles survive both forms of compression;
* 5-cycles survive head truncation but not low-order moment compression;
* 6-cycles require a larger portion of the head and are also poorly captured by low-order moments.

The 5-cycle result is particularly informative. Its signal is present almost entirely within the first 200–400 ranked probabilities, yet it cannot be reconstructed from power sums through order eight.

Thus, 5-cycle accessibility depends on the detailed arrangement of probability magnitudes within the head, rather than only on coarse concentration summaries.

##### Uncompleted cospectral tracer

The notebook planned a second analysis measuring how the global percentile of each cospectral-pair separation changes under truncation.

That analysis did not produce completed outputs in this run. Consequently, the notebook supports conclusions about cycle-count decodability under truncation, but not about how truncation changes the relative standing of cospectral separations.

No claim about cospectral mate percentiles should be based on this run alone.

##### What the experiment establishes

The completed results support five conclusions.

1. **Most cycle-count information is concentrated in a small leading portion of the sorted probability vector.**
   None of the tested targets benefits materially from retaining more than approximately 1,000 coordinates.

2. **The structural hierarchy appears as a truncation-depth hierarchy.**
   Triangles require the fewest coordinates, followed by 4-cycles, 5-cycles, and 6-cycles.

3. **The full 5-cycle signal is highly compressible.**
   It reaches its full performance using only 200–400 probabilities.

4. **Six-cycle information is deeper and less stable.**
   It requires approximately 400–1,000 coordinates and exhibits greater fold sensitivity, particularly at (n=14).

5. **The required fraction of the full vector decreases from (n=14) to (n=16).**
   The relevant absolute head grows slowly compared with the fourfold growth in ambient dimension.

The experiment therefore refines the earlier claim that QuIC contains a structural hierarchy. That hierarchy is not only visible in predictive strength; it is spatially ordered within the sorted probability vector.

##### Necessary qualifications

The (n=16) full-vector point did not complete in this notebook. Saturation is inferred from the negligible differences between (k=1000) and (k=4000), together with the previously established full-vector scores. The current run alone does not directly measure the final (61{,}536) coordinates.

The vectors contain exact ideal probabilities. The experiment does not determine how many circuit shots are required to identify and estimate the largest (k) probabilities.

In particular, extracting the exact top-(k) sorted vector from finite samples is not equivalent to measuring only (k) predetermined bitstrings. The identities of the highest-probability outcomes must first be discovered, and ranking errors may occur when probabilities are close.

The truncated vectors are not renormalized. A ridge model may therefore use both:

* the relative shape of the retained probabilities;
* the cumulative retained mass
  [
  \sum_{i=1}^{k}p_{(i)}.
  ]

This is appropriate for measuring predictive information in the raw head, but it does not isolate shape information from retained-mass information. A normalized-head control would answer that separate question.

Only cycle-count targets are included. The results do not establish suitable truncation lengths for girth, diameter, spectral gap, diamonds, or other graph invariants.

The truncation grid is coarse. Statements such as “C5 saturates at (k=200)” mean that 200 is the first tested point near saturation, not that it is the true minimum sufficient dimension.

The ridge models operate in a high-dimensional, low-sample regime, particularly at (n=14). The increase in 6-cycle variance after (k=400) indicates that the tail can amplify fold instability even when its average predictive contribution is negligible.

Finally, no paired statistical test is performed between adjacent truncation levels. Small differences near saturation should be treated descriptively.

##### Overall assessment

The experiment shows that the exponentially large QuIC probability vector is highly redundant for cycle-count decoding.

Triangle count is completely accessible from the first 25 probabilities. Four-cycle count is nearly saturated by 100. Five-cycle count undergoes a sharp transition between approximately 100 and 400 entries. Six-cycle information extends deeper, but performance saturates by approximately 1,000 entries.

At (n=16), those 1,000 coordinates represent only about 1.5% of the complete vector. Increasing to 4,000 entries produces essentially no additional gain.

The appropriate central claim is:

> QuIC’s cycle-count information is rank-stratified within the sorted probability distribution. Triangle and 4-cycle structure is concentrated in the extreme head, 5-cycle information emerges within the first few hundred probabilities, and 6-cycle information extends to approximately the first thousand. Across (n=14) and (n=16), the useful absolute head grows far more slowly than the full (2^n)-dimensional representation, although practical finite-shot recovery of that head remains untested.

### E8 - CoSpectral Audit

##### Experimental design

This experiment audits the adjacency-cospectral graph census and determines which graph invariants actually vary within cospectral classes.

The analysis uses the complete connected cubic-graph censuses at:

* (n=14): 509 graphs;
* (n=16): 4,060 graphs.

It has two objectives:

1. replace the earlier rounded-eigenvalue grouping with an exact cospectrality test;
2. identify targets that vary among graphs having exactly the same adjacency spectrum.

For each graph with adjacency matrix (A), the exact signature is

[
\left(
\operatorname{tr}(A),
\operatorname{tr}(A^2),
\ldots,
\operatorname{tr}(A^n)
\right).
]

Because (A) is an integer matrix, these traces are exact integer walk counts. Newton’s identities imply that the first (n) power sums of the eigenvalues determine the characteristic polynomial. Two (n)-vertex graphs are therefore adjacency-cospectral exactly when all (n) traces agree.

The within-group audit computes:

* cycle counts (C_3) through (C_7);
* girth;
* diameter;
* radius;
* Wiener index;
* node connectivity;
* edge connectivity;
* maximum matching size;
* clique number;
* automorphism-group order.

The purpose is not to test whether QuIC separates the graphs. It is to determine whether a downstream target varies after the complete adjacency spectrum has been fixed.

##### Exact cospectral census

The exact integer-trace grouping reproduces the earlier spectrum-hash census without any disagreement.

| Order  | Exact groups | Graphs in groups | Group sizes             | Within-group pairs |
| ------ | -----------: | ---------------: | ----------------------- | -----------------: |
| (n=14) |            3 |                6 | three pairs             |                  3 |
| (n=16) |           41 |               83 | 40 pairs and one triple |                 43 |

At both graph orders, the exact groups are identical to those obtained by rounding adjacency eigenvalues to eight decimal places.

This closes the numerical-tolerance concern for these two censuses. No false cospectral groups were created by rounding, and no exact group was missed.

The agreement validates the earlier census, but only for these datasets. It does not imply that eight-decimal eigenvalue hashing is universally safe on larger or different graph families.

##### Invariant audit

###### Group-level variation counts

| Invariant          | (n=14): differing groups | (n=16): differing groups |
| ------------------ | -----------------------: | -----------------------: |
| (C_3)              |                        0 |                        0 |
| (C_4)              |                        0 |                        0 |
| (C_5)              |                        0 |                        0 |
| (C_6)              |                        0 |                        0 |
| (C_7)              |                        0 |                        0 |
| Girth              |                        0 |                        0 |
| Diameter           |                        0 |                        0 |
| Radius             |                        0 |                        4 |
| Wiener index       |                        1 |                       25 |
| Node connectivity  |                        0 |                        0 |
| Edge connectivity  |                        0 |                        0 |
| Matching number    |                        0 |                        0 |
| Clique number      |                        0 |                        0 |
| Automorphism order |                        3 |                       14 |

A group is counted once when at least two of its members differ on the invariant. Because the (n=16) census contains one cospectral triple, these are group counts rather than pair counts.

The number of groups differing on at least one audited non-spectral target is:

[
3\text{ of }3
\quad\text{at }n=14,
]

and

[
29\text{ of }41
\quad\text{at }n=16.
]

Thus, most (n=16) cospectral groups are not isomorphic copies with identical audited structure. They differ on at least one global metric or symmetry quantity.

##### Spectrally fixed controls

The short-cycle controls behave exactly as expected.

Every cospectral group agrees on:

[
C_3,\quad C_4,\quad C_5.
]

For regular graphs, these quantities are determined by low-order adjacency traces. Their agreement is therefore a theorem-level consistency check on:

* the exact cospectral grouping;
* the cycle-count implementation;
* the graph ordering;
* and the invariant audit.

Girth also agrees in every group. In this census, that equality is reinforced by the observed agreement of all cycle counts through (C_7).

No pinned-control violation occurs. There is therefore no indication that the cospectral census or invariant calculations are misaligned.

##### Six-cycle count and diamonds

Every cospectral group agrees on (C_6).

For cubic graphs, the notebook verifies the identity

[
\operatorname{tr}(A^6)
======================

12(C_6+D)
+
87n
+
6C_3
+
96C_4,
]

where (D) is the number of diamonds, or copies of (K_4) with one edge removed.

The identity holds exactly for every graph in both complete censuses.

Because the spectrum fixes

[
\operatorname{tr}(A^6),
]

and also fixes (n), (C_3), and (C_4), it fixes the sum

[
C_6+D.
]

The audit shows that (C_6) itself does not vary within any cospectral group at (n=14) or (n=16). It follows that diamond count also does not vary within those groups.

This does not establish that (C_6) or (D) is universally adjacency-spectral for all cubic graphs. The identity fixes only their sum. A larger census could contain cospectral mates that trade one 6-cycle against one diamond.

The present result is narrower:

> No such (C_6)-diamond tradeoff occurs among the exact cospectral cubic groups at (n=14) or (n=16).

Consequently, these groups cannot support a within-cospectral-class challenge based on (C_6) or diamonds.

##### Seven-cycle count

Every exact group also agrees on (C_7).

Unlike the (C_3)–(C_6) results, the notebook does not derive a spectral identity explaining this agreement. The (C_7) result is therefore empirical.

It establishes that (C_7) is unusable as a varying cospectral target in these two censuses. It does not establish that 7-cycle count is generally determined by the adjacency spectrum of cubic graphs.

##### Diameter and radius

Diameter agrees in all 44 exact cospectral groups:

[
0\text{ differing groups}.
]

Radius behaves differently. Four (n=16) groups have different radii despite identical adjacency spectra.

The four radius-varying groups include changes of the form

[
3\leftrightarrow4.
]

This distinction is structurally meaningful. Diameter records the maximum eccentricity, while radius records the minimum eccentricity. The cospectral mates preserve the worst-case graph distance but can differ in how centrally positioned their most central vertices are.

The result demonstrates that the adjacency spectrum does not determine radius within this census, even though it happens to determine diameter across the observed cospectral classes.

Radius is therefore a valid non-spectral challenge target, but the sample is small:

[
4\text{ usable groups}.
]

That is insufficient for a strong standalone statistical experiment without combining it with other evidence.

##### Wiener index

The Wiener index is the most common varying invariant.

It differs in:

[
1\text{ of }3
]

groups at (n=14), and

[
25\text{ of }41
]

groups at (n=16).

The Wiener index is

[
W(G)
====

\sum_{{u,v}\subseteq V}
d(u,v),
]

the sum of all unordered pairwise shortest-path distances.

Most within-group differences are small:

[
1\text{--}3
]

units on total values approximately between 270 and 360 at (n=16).

The small absolute differences do not make the result trivial. The entire adjacency spectrum is identical within each group. Any repeatable prediction of which mate has the larger Wiener index must therefore use information not determined by that spectrum.

The prevalence of Wiener variation shows that cospectral mates often differ in the detailed distribution of shortest-path lengths even when they share:

* diameter;
* short-cycle counts;
* connectivity;
* matching number;
* and clique number.

This makes the Wiener index the strongest audited target for a functional cospectral challenge.

Its main advantages are:

* it varies in a majority of the (n=16) groups;
* it is precisely defined and inexpensive to compute;
* it measures global graph organization rather than another local motif;
* it supports within-group ranking without target-scale confounding.

The principal limitation is that the differences are usually narrow, so ordinary unrestricted regression may obscure the relevant comparison. A within-group ranking or paired prediction task is better aligned with the structure of the data.

##### Automorphism-group order

Automorphism-group order differs in:

[
3\text{ of }3
]

groups at (n=14), and

[
14\text{ of }41
]

groups at (n=16).

Examples include:

[
1\leftrightarrow2,
\qquad
2\leftrightarrow4,
\qquad
4\leftrightarrow8,
\qquad
12\leftrightarrow48.
]

This shows that adjacency-cospectral graphs can have substantially different symmetry groups.

The (n=14) result is particularly clear: all three cospectral pairs differ in automorphism order, even though only one differs in Wiener index.

Automorphism order therefore captures a different non-spectral direction from the metric quantities. It is not merely a proxy for radius or Wiener index.

Because its distribution is highly skewed and multiplicative, a transformed target such as

[
\log_2|\operatorname{Aut}(G)|
]

is more suitable for regression or ranking than raw group order.

The usable sample remains limited, particularly if groups are divided into training and test sets. Automorphism order is therefore a strong secondary challenge target rather than the best primary target.

##### Invariants that do not vary

No exact cospectral group differs in:

* node connectivity;
* edge connectivity;
* maximum matching size;
* clique number.

These negative results should be interpreted as census-specific.

They show that these invariants cannot support the planned cospectral challenge at (n\le16). They do not imply that any of them is generally determined by the adjacency spectrum.

The same qualification applies to diameter, (C_6), and (C_7): agreement across all observed groups is a property of the available census, not a universal spectral theorem unless separately proved.

##### Structure of the usable challenge set

At (n=16), 29 of the 41 exact groups differ on at least one of:

* Wiener index;
* radius;
* automorphism order.

The overlap among these targets is substantial but incomplete.

Some groups differ only in automorphism order. Others differ only in Wiener index. A smaller number differ in radius together with Wiener index or automorphism order.

The cospectral triple

[
(582,3061,3800)
]

has Wiener values

[
283,\ 282,\ 283.
]

This illustrates why the natural unit of cross-validation is the cospectral group rather than an arbitrary graph or graph pair. All members of a group must remain in the same fold to prevent the model from seeing a spectral duplicate of a test graph during training.

The audit therefore determines not only the viable targets but also the required evaluation structure:

[
\boxed{
\text{group-preserving folds with within-group comparisons}
}
]

##### What the experiment establishes

The completed audit supports five conclusions.

1. **The earlier rounded-spectrum census is exact for these datasets.**
   Integer trace tuples recover exactly the same 3 groups at (n=14) and 41 groups at (n=16).

2. **Short-cycle structure is constant within every cospectral class.**
   All groups agree on (C_3) through (C_7) and on girth.

3. **The obvious cycle-based challenge targets are not viable.**
   Neither (C_6) nor (C_7) varies within any exact group.

4. **Non-spectral variation is concentrated in global metric and symmetry structure.**
   Wiener index differs in 25 (n=16) groups, automorphism order in 14, and radius in 4.

5. **A functional cospectral challenge remains viable.**
   Twenty-nine of the 41 (n=16) groups differ on at least one audited non-spectral invariant.

The audit therefore changes the interpretation of the non-spectral residue. Within these cubic censuses, it is not expressed through additional short-cycle counts. It appears through global distance organization and graph symmetry.

##### Necessary qualifications

The exact trace test relies on the fact that the graphs have the same order. Traces through (A^n) determine the characteristic polynomial for an (n\times n) matrix through Newton’s identities.

The use of signed 64-bit integers is safe at (n\le16) for cubic graphs because the relevant closed-walk counts remain far below the integer limit. This implementation would require reassessment at substantially larger graph orders or degrees.

The audit covers only graph invariants explicitly listed in the notebook. Cospectral groups may differ on many other quantities that were not computed.

The sample contains only 44 exact groups in total. Group-level statistical power is therefore limited, especially for radius and automorphism order.

The (n=14) results are based on only three groups. The fact that all three differ in automorphism order is structurally interesting but does not provide a precise population-frequency estimate.

Wiener-index differences are usually small relative to the total index. A successful downstream result must demonstrate genuine within-group discrimination rather than exploiting global scale or graph-order information.

The invariant audit establishes target variation, not QuIC decodability. A separate experiment is required to show that QuIC can predict which cospectral mate has the larger Wiener index, radius, or automorphism group.

Finally, the absence of variation is not proof of spectral determination. For (C_7), diameter, connectivity, matching number, and clique number, the correct wording is that no variation occurs in these censuses.

##### Overall assessment

The audit successfully performs its viability-gate function.

Exact integer arithmetic confirms that the original rounded-eigenvalue census contains precisely the correct cospectral groups. The short-cycle controls agree everywhere, and the cubic sixth-moment identity explains why the spectrum constrains the combined (C_6)-diamond quantity.

The intended cycle-based challenge does not survive. Every cospectral group agrees on cycle counts through (C_7), as well as girth and diameter.

The non-spectral variation instead appears in:

* Wiener index;
* radius;
* automorphism-group order.

Wiener index is the strongest primary target because it differs in 25 of the 41 (n=16) groups. Automorphism order provides an independent symmetry-based secondary target, while radius offers a smaller metric exhibit.

The appropriate central claim is:

> Exact integer certification identifies 3 adjacency-cospectral groups at (n=14) and 41 at (n=16), exactly matching the earlier rounded-spectrum census. All groups agree on cycle counts through (C_7), girth, and diameter, but 29 of the 41 (n=16) groups differ in Wiener index, radius, or automorphism-group order. The non-spectral variation available for functional testing is therefore global metric and symmetry structure rather than additional short-cycle information.

