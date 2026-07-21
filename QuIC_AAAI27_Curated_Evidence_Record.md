# QuIC AAAI-27 Curated Evidence Record

## Purpose

This document is the paper-facing evidence source for **Characterizing the Structural Inductive Bias of a Quantum Graph Feature Map**. It is intentionally narrower than the complete experimental archive.

Use it together with:

* `AAAI27_QuIC_Final_Strategy.md`, which controls the paper thesis, scope, terminology, and main-text allocation;
* `QuIC_Experimental_Results (6).md`, which remains the full scientific log and provenance archive.

The writing model should treat this document as the default source of experimental claims. The full archive should be opened only when this document points to an experiment or when a specific provenance question must be resolved.

---

## Source authority and supersession rules

1. **The final strategy document controls inclusion.** An experiment may be valid yet excluded because it creates a new conceptual branch, duplicates stronger evidence, or exceeds the page budget.
2. **The final formalism supersedes every earlier formalism and moment-bridge draft.** Use only `Final QuIC Formalism - Boundary Transforms, Rooted Incidence Hierarchies, and the Measured Probability Spectrum` for mathematical claims.
3. **Main-paper experiments are authoritative only in the versions listed below.** Do not substitute semantically similar exploratory runs.
4. **Corrected versions supersede originals.** In particular:
   * E24C supersedes the original protocol-mismatched E24 ranking comparison;
   * E25R supersedes the original E25 decoder interpretation;
   * E26R supersedes the original E26 representation comparison;
   * E29D-R supersedes the invalid stacking portion of E29D;
   * E29C-Rv2 supersedes E29C-R v1;
   * E29C-OV2 supersedes E29C-O for exact linear-span residualization.
5. **E15 is the main-paper finite-shot experiment.** E29F-HX is a required supplementary counterpoint showing that statistical accessibility depends on readout design. E28 is archival supporting work and does not replace either.
6. **E14 is the main theorem-backed non-spectral witness experiment.** Earlier cospectral audits provide provenance and diagnostics, not the primary manuscript claim.
7. **Protocol-sensitive E29 residual claims do not belong in the main paper.** They may be consulted for later papers or a narrowly scoped supplement, but they must not influence the abstract, contribution list, or principal results table.
8. **The omitted-experiment index at the end is discovery-only.** Do not use an omitted experiment in manuscript prose without reopening its full archival section and verifying its final status.

---

# 1. Paper thesis and evidence hierarchy

## One-sentence thesis

> A shallow phase-encoded quantum circuit defines a training-free graph feature map whose weak-mixer Born readout has an identifiable combinatorial inductive bias: on regular graphs, short-cycle and rooted-incidence structure appears in a predictable hierarchy and includes a diamond-sensitive component beyond the adjacency spectrum. Its finer globally sorted motif content is increasingly costly to recover from finite measurements, while structure-aware aggregation can make other low-dimensional graph signals substantially more accessible.

## Three contribution blocks

### Contribution 1 — Exact representation mechanism

The paper derives how the circuit transforms graph structure into a permutation-invariant measurement representation:

* the commuting \(R_{ZZ}\) layer encodes the graph cut-phase landscape;
* Walsh coefficients are boundary-sector weight enumerators;
* the \(R_X\) mixer interferes cuts related by Hamming flips;
* sorting produces a canonical empirical distribution of probability masses.

### Contribution 2 — Cubic motif theorem and spectral separation

For simple cubic graphs:

$$M_2''(G;0)=A_n+b_3C_3(G)+b_4C_4(G)+b_DD_\diamond(G).$$

The theorem yields:

* explicit separation of same-order regular graphs collapsed by ordinary 1-WL;
* explicit separation of adjacency-cospectral cubic graphs with unequal diamond count;
* a direct formal interpretation of the six \(n=18\) diamond/\(C_6\) exchange witnesses.

### Contribution 3 — Exhaustive characterization of accessibility

Across the complete connected cubic censuses at \(n=14\) and \(n=16\):

* triangles dominate global representation geometry;
* four-cycles organize geometry after triangles are fixed;
* five-cycles organize the remaining geometry after triangles and four-cycles are fixed;
* simple ridge probes recover the same hierarchy;
* the targets occur at progressively deeper probability ranks;
* folklore 2-WL and finite-shot experiments delimit the representational claim.

---

# 2. Required AI framing

The circuit is a fixed graph feature map consumed by an ordinary downstream learner:

$$G\longmapsto\Phi_{\mathrm{QuIC}}(G)\longmapsto f_w\!\left(\Phi_{\mathrm{QuIC}}(G)\right).$$

The paper distinguishes three questions:

$$\text{information contained}\not\equiv\text{information linearly accessible}\not\equiv\text{information statistically accessible}.$$

Use the following terminology:

* quantum graph feature map;
* frozen or training-free representation;
* structural inductive bias;
* representation geometry;
* linear accessibility or linear decodability;
* statistical or finite-shot accessibility;
* permutation-invariant sorted probability representation;
* boundary-sector polynomial;
* weak-mixer response;
* controlled comparison with folklore 2-WL.

Do not make “quantum graph invariant” the only framing. It emphasizes graph discrimination but obscures the downstream representation-learning question.

---

# 3. Main mathematical evidence

## 3.1 Canonical circuit and representation

The ideal one-repetition circuit is:

$$|\psi_G\rangle=R_X(\beta)^{\otimes n}\left[\prod_{uv\in E}R_{ZZ}^{(u,v)}(\gamma)\right]\left[\bigotimes_iR_X(\eta_i)\right]|0^n\rangle.$$

The canonical regular-graph angles are:

$$\eta=2.875,\qquad\gamma=2.0,\qquad\beta=0.1.$$

The labeled Born vector is \(p_G\), and the graph feature map is its descending rearrangement:

$$\Phi_{\mathrm{QuIC}}(G)=p_G^\downarrow.$$

For irregular graphs, the normalized degree encoder uses:

$$\eta_i=\eta\frac{d_i}{\Delta}.$$

## 3.2 Cut phase and mixer interference

The entangler acts as:

$$\prod_{uv\in E}e^{-i\gamma z_uz_v/2}=e^{-i\gamma|E|/2}e^{i\gamma c_G(x)}.$$

Up to global phase, the graph is encoded as the complex cut-phase function:

$$f_G(x)=e^{i\gamma c_G(x)}.$$

The product mixer has the exact hypercube expansion:

$$\psi_G(x;\beta)=\cos^n(\beta/2)\sum_{S\subseteq V}[-i\tan(\beta/2)]^{|S|}\phi_G(x\oplus S).$$

This is the mechanism-level explanation for why mixer order corresponds to the number of flipped roots.

## 3.3 Boundary-sector transform

For:

$$Z_{G,T}(z)=\sum_{F\subseteq E:\,\partial F=T}z^{|F|},$$

the pre-mixer Walsh coefficients are boundary-sector weight enumerators at imaginary Ising coupling. On cubic graphs, the relevant closed-sector coefficients are:

$$[z^3]Z_{G,\varnothing}=C_3,$$

$$[z^4]Z_{G,\varnothing}=C_4,$$

$$[z^5]Z_{G,\varnothing}=C_5,$$

$$[z^6]Z_{G,\varnothing}=C_6+\binom{C_3}{2}-D_\diamond.$$

These identities explain why short cycles and diamonds are natural structural carriers rather than post-hoc regression targets.

## 3.4 Distributional meaning of sorting

Define the empirical Born-value measure:

$$\nu_G=\frac{1}{2^n}\sum_x\delta_{2^np_G(x)}.$$

The sorted vector is its empirical quantile representation. For equal graph order:

$$\min_{\sigma\in S_{2^n}}\|p_G-\sigma p_H\|_1=\|p_G^\downarrow-p_H^\downarrow\|_1=W_1(\nu_G,\nu_H).$$

This permits the paper to describe the readout as a distribution of probability masses rather than an arbitrary sort operation. It does **not** make sorting lossless: sorting quotients over all outcome permutations and can destroy semantic structure.

## 3.5 Central theorem

For every simple cubic graph under the theorem’s stated angle assumptions:

$$\boxed{M_2''(G;0)=A_n+b_3C_3(G)+b_4C_4(G)+b_DD_\diamond(G).}$$

At the canonical \(n=14\) parameters, the coefficients are:

| Motif | Coefficient in \(M_2''(0)\) |
|---|---:|
| \(C_3\) | \(3.73045185\times10^{-5}\) |
| total \(C_4\) | \(3.34368946\times10^{-8}\) |
| pair-incidence diamond | \(3.99102708\times10^{-8}\) |

The triangle coefficient is roughly three orders of magnitude larger than the other two coefficients. This is coefficient dominance, not a universal statement that every graph contrast is dominated by triangle count.

The algebraic third-difference cancellation is part of the proof and must appear in the main paper. The proof cannot be delegated entirely to the supplement.

## 3.6 Corollary A — explicit separation from ordinary 1-WL

All same-order regular graphs receive the same ordinary 1-WL coloring when initialized uniformly. If the theorem’s motif combination differs and the corresponding coefficient is nonzero, the purity derivatives differ, and the sorted Born distributions differ for sufficiently small nonzero \(\beta\).

Use the triangular prism and \(K_{3,3}\) as the explicit witness. State only explicit separation from ordinary 1-WL, not general superiority over the WL hierarchy.

## 3.7 Corollary B — adjacency-cospectral diamond separation

For adjacency-cospectral cubic graphs, the spectrum fixes the lower spectral quantities entering the theorem. If:

$$D_\diamond(G)\ne D_\diamond(H),$$

then:

$$M_2''(G;0)-M_2''(H;0)=b_D\left[D_\diamond(G)-D_\diamond(H)\right]\ne0.$$

The sorted Born distributions therefore differ for sufficiently small nonzero mixer angle. E14 supplies the canonical finite-angle witnesses.

## 3.8 Formal material not used in the main argument

The final formalism notebook contains additional correct or computationally supported material. Do not promote the following into the main paper:

* complete moment reconstruction of the sorted vector;
* all-orders rooted-incidence locality;
* third-order closure on the full three-root incidence census;
* triple-defect \(C_5/ C_6\) formulas as headline theorems;
* generic or universal injectivity;
* repeated-layer space-time boundary polynomials;
* broad quotient-group theory;
* interval-certified head ordering beyond the exact settings needed by the paper.

These results are candidates for a later theory paper or optional supplementary notes. They do not strengthen the acceptance-oriented central theorem enough to justify their proof surface.

---

# 4. Main experimental evidence

## Experimental Question 1 — Does the ideal representation exhibit the predicted motif hierarchy?

### Canonical experiment: E1 — Stratified Residue

#### Design

E1 analyzes the complete connected cubic censuses:

* 509 graphs at \(n=14\);
* 4,060 graphs at \(n=16\).

Every graph in one census has the same order and degree sequence. The feature is the full exact sorted QuIC vector at one circuit repetition and the canonical angles.

The experiment tests pairwise \(L_1\) geometry against absolute differences in \(C_3\), \(C_4\), and \(C_5\), then conditions sequentially:

$$\text{all graphs}\rightarrow\text{fixed }C_3\rightarrow\text{fixed }(C_3,C_4).$$

#### Main results

| Quantity | \(n=14\) global Mantel \(\rho\) | \(n=16\) global Mantel \(\rho\) |
|---|---:|---:|
| triangles | 0.903 | 0.900 |
| four-cycles | 0.290 | 0.303 |
| five-cycles | 0.109 | 0.079 |
| random control | 0.005 | -0.007 |

After fixing triangle count:

* \(n=14\): every sufficiently populated stratum has \(C_4\) correlation between 0.898 and 0.968;
* \(n=16\): the corresponding range is 0.853 to 0.964.

Within the largest fixed-triangle strata at \(n=16\):

* PC1 explains 53.6%–54.7% of variance;
* \(|\rho(\mathrm{PC1},C_4)|=0.978\)–0.985;
* effective rank remains near three.

After fixing both \(C_3\) and \(C_4\):

* all 16 qualifying \(n=14\) strata have positive \(C_5\) organization;
* all 43 qualifying \(n=16\) strata have positive \(C_5\) organization;
* those 43 strata cover approximately 97.1% of the \(n=16\) census.

#### Permitted manuscript claim

> Across the exhaustive connected cubic censuses at \(n=14\) and \(n=16\), QuIC geometry is organized hierarchically by short-cycle structure: triangles dominate globally, four-cycles define the leading direction after conditioning on triangles, and five-cycles organize the remaining geometry after conditioning on both.

#### Required qualification

E1 establishes metric organization, not causal encoding or unique coordinate recovery. The pairwise observations are dependent, and the one-sided Mantel tests use permutation inference. The result is exhaustive only within connected cubic graphs at the tested orders and canonical circuit.

#### Paper placement

Main paper, Figure 2 or a consolidated hierarchy panel. Full stratum tables belong in the supplement.

---

## Experimental Question 2 — Is the hierarchy accessible to a downstream learner?

### Canonical experiment: E2 — Ridge Probe

#### Design

E2 uses the same complete cubic censuses and full exact sorted vectors. Five frozen shuffled outer folds and nested ridge regression test linear accessibility of graph invariants.

#### Full-vector results

| Target | \(n=14\) QuIC \(R^2\) | \(n=16\) QuIC \(R^2\) |
|---|---:|---:|
| \(C_3\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) |
| \(C_4\) | \(0.998\pm0.002\) | \(1.000\pm0.000\) |
| \(C_5\) | \(0.928\pm0.092\) | \(0.982\pm0.015\) |
| \(C_6\) | \(0.485\pm0.326\) | \(0.642\pm0.122\) |
| girth | \(0.993\pm0.014\) | \(0.999\pm0.003\) |
| diameter | \(0.548\pm0.058\) | \(0.737\pm0.019\) |
| spectral gap | \(0.944\pm0.010\) | \(0.932\pm0.007\) |

The principal cycle hierarchy is:

$$C_3,C_4\rightarrow C_5\rightarrow C_6.$$

Probability power sums reproduce triangles and eventually four-cycles but do not reproduce the strong full-vector \(C_5\) result. Through moment order eight, \(C_5\) remains near 0.08–0.11, far below the full-vector scores.

#### Permitted manuscript claim

> Simple held-out linear probes recover the geometric hierarchy: triangles and four-cycles are essentially exact, five-cycles remain strongly accessible, and six-cycles form a weaker and less stable layer.

#### Required qualification

These are high-dimensional ridge probes on exact vectors. They establish linear accessibility under the stated protocol, not a unique invariant coordinate, practical measurement efficiency, or computational advantage. The near-floor selected regularization values require ordinary caution about near-interpolating fits, although replication at \(n=16\) materially strengthens the result.

#### Paper placement

Main paper, compact table with \(C_3\), \(C_4\), \(C_5\), and cautious \(C_6\). The remaining targets and fold-level details belong in the supplement.

---

## Experimental Question 2b — Where is the information located in the sorted vector?

### Canonical experiment: E7 — Truncation

#### Design

E7 repeats the E2 cycle probes after retaining only the \(k\) largest probabilities:

$$k\in\{25,50,100,200,400,1000,4000\}.$$

#### Rank-localization results

| Target | Practical head location | Representative result |
|---|---|---|
| \(C_3\) | extreme head | \(R^2=1.000\) at \(k=25\) for both orders |
| \(C_4\) | approximately first \(10^2\) | \(R^2=0.993/0.996\) at \(k=100\) |
| \(C_5\) | several hundred | \(R^2=0.927/0.981\) at \(k=400\) |
| \(C_6\) | approximately first \(10^3\) | \(R^2=0.484/0.640\) at \(k=1000\) |

At \(n=16\), increasing from 1,000 to 4,000 coordinates produces essentially no further gain for the tested cycle targets.

#### Permitted manuscript claim

> QuIC’s structural information is rank stratified: triangles occupy the extreme probability head, four-cycles appear within roughly the first hundred ranks, five-cycles within a few hundred, and the weaker six-cycle signal extends to roughly the first thousand.

#### Required qualification

This is rank localization, not proof that the complete representation is polynomial size or efficiently measurable. The identities of top outcomes must still be discovered from samples, the head is not renormalized, and the grid does not identify a mathematically minimal cutoff.

#### Paper placement

Main paper, combined with E1 in Figure 2. Complete curves belong in the supplement.

---

## Experimental Question 3 — Does the theorem identify information beyond the adjacency spectrum?

### Canonical experiment: E14 — \(n=18\) Exact-Cospectral Functional Witnesses

#### Design

E14 analyzes the complete connected cubic census at:

$$n=18,\qquad 41{,}301\text{ graphs}.$$

Exact adjacency-cospectral classes are reconstructed from integer trace tuples. Six classes contain pairs that exchange one diamond for one six-cycle while preserving the complete adjacency spectrum.

#### Primary result

* QuIC correctly ranks the diamond count in all six held-out witness pairs.
* Equivalently, it ranks \(C_6\) with reversed labels.
* The result is 6/6 at every tested regularization value and truncation depth.
* The first 100 sorted probabilities suffice.
* The selection-corrected sign-flip result is \(p=0.0462\).

The within-group sorted-vector separations are nonzero and were checked with exact/high-precision supporting audits.

#### Permitted manuscript claim

> The theorem’s diamond term is realized by six exact adjacency-cospectral cubic witness pairs at \(n=18\): each pair exchanges one diamond for one six-cycle, and QuIC ranks all six correctly using only the first 100 sorted probabilities.

#### Required qualification

This is an explicit theorem-backed witness set, not universal cospectral separation. “Beyond spectrum” means beyond adjacency-spectrum equivalence on these pairs, not beyond classical computation. The larger Wiener-index and automorphism-order results are supplementary and should not distract from the diamond corollary.

#### Paper placement

Main paper, Section 4 corollary followed by a compact Section 6 witness result. Exact graph identifiers, precision checks, and significance protocol belong in the supplement.

---

## Experimental Question 4 — How does QuIC compare with a strong classical structural representation?

### Canonical experiment: E3C — Folklore 2-WL Baseline

#### Design

The baseline is folklore 2-WL on ordered vertex pairs with synchronized color vocabularies. Two representations are tested:

* cumulative histograms from all refinement rounds;
* stable-only final histograms.

Ordinary 1-WL is a constant representation on fixed-order cubic graphs and has no predictive variation.

#### Discrimination results

* folklore 2-WL distinguishes all 509 graphs at \(n=14\) and all 4,060 at \(n=16\);
* stable 2-WL separates all 3 exact cospectral pairs at \(n=14\) and all 43 pairwise cospectral comparisons at \(n=16\);
* QuIC separates the same tested pairs;
* stable-only final-color histograms nevertheless fail transferable ridge prediction because their coordinates are graph specific.

#### Linear-probe results

##### \(n=14\)

| Target | cumulative folklore 2-WL | QuIC |
|---|---:|---:|
| \(C_3\) | 0.998 | 1.000 |
| \(C_4\) | 0.993 | 0.998 |
| \(C_5\) | 0.917 | 0.928 |
| \(C_6\) | 0.879 | 0.485 |
| girth | 0.787 | 0.993 |
| diameter | 0.779 | 0.548 |
| spectral gap | 0.947 | 0.944 |

##### \(n=16\)

| Target | cumulative folklore 2-WL | QuIC |
|---|---:|---:|
| \(C_3\) | 1.000 | 1.000 |
| \(C_4\) | 0.999 | 1.000 |
| \(C_5\) | 0.993 | 0.982 |
| \(C_6\) | 0.983 | 0.642 |
| girth | 0.844 | 0.999 |
| diameter | 0.861 | 0.737 |
| spectral gap | 0.982 | 0.932 |

#### Permitted manuscript claim

> Folklore 2-WL is a strong classical control: it distinguishes every tested census graph and nearly saturates cycle prediction, substantially exceeding QuIC on six-cycles and diameter. QuIC remains stronger on girth and closely matched on the shorter-cycle targets. Final discrimination and transferable linear accessibility are not the same property.

#### Required qualification

Do not describe 2-WL as defeated, do not infer formal incomparability, and do not imply a universal expressive ordering. The implemented method must be named folklore 2-WL on ordered pairs.

#### Paper placement

Main paper, one compact comparison table. Full vocabulary construction, dimensions, and stable-only results belong in the supplement.

---

## Experimental Question 5 — Is the ideal information statistically accessible?

### Canonical experiment: E15 — Finite-Shot Recovery Under Independent Sampling

#### Design

E15 uses the complete \(n=14\) and \(n=16\) cubic censuses. Independent multinomial realizations are generated for training and test representations. The completed experiment contains all 198 planned grid cells with 30 unique replicates per cell.

#### Principal results

* Triangle recovery reaches 90% of the exact-vector score at approximately \(3.1\times10^6\) shots per graph.
* Triangle recovery reaches 95% near \(4.2\times10^6\) shots.
* The thresholds are nearly identical at \(n=14\) and \(n=16\).
* At \(2^{24}\) shots:
  * \(C_3\) reaches approximately 0.994 at both orders;
  * \(C_4\) reaches approximately 0.684 and 0.668;
  * \(C_5\) remains at the prediction floor at both orders;
  * girth reaches approximately 0.89;
  * diamonds reach approximately 0.59;
  * \(C_6\) remains near 0.14.
* Exact cospectral mate distances remain comparable to repeat-sampling variation throughout the tested ladder.

#### Permitted manuscript claim

> The ideal hierarchy is also a hierarchy of measurement difficulty. Triangle prediction becomes reliable only at millions of shots per graph; four-cycles and diamonds remain partially recovered at \(2^{24}\) shots; five-cycle prediction remains absent despite strong exact-vector accessibility; and exact cospectral separations remain near the sampling-noise scale.

#### Required qualification

This is ideal multinomial sampling, not hardware execution. The result characterizes statistical accessibility of the globally sorted readout and must not be presented as a quantum speedup, hardware failure, or universal shot barrier.

#### Paper placement

Main paper, one compact curve, inset, or table in the controlled-boundaries section. Full estimators, uncertainty, and shot curves belong in the supplement.

---

# 5. Required supplementary evidence

## 5.1 E29F-HX — readout-specific finite-shot counterpoint

E29F-HX tests the H-X circuit on four irregular fixed-degree-sequence strata of 400 graphs each. The target is the E30 analytical joint-degree mixing coordinate.

The three readouts are:

* R0: global sorting;
* R1: Hamming-weight pooling;
* R2: degree-sector mass pooling.

### Exact-state references

| Stratum | R0 | R1 | R2 |
|---|---:|---:|---:|
| S1 | 0.0700 | 0.6063 | 0.9997 |
| S2 | 0.5531 | 0.9958 | 1.0000 |
| S3 | 0.1242 | 0.4670 | 0.9991 |
| S4 | 0.0900 | 0.3823 | 0.9992 |

### Finite-shot R2 results

At \(2^{16}\) shots, R2 reaches:

$$0.916,\quad0.963,\quad0.845,\quad0.912$$

for S1 through S4.

Estimated 90% recovery occurs at:

$$2^{14.59}\text{--}2^{17.05}$$

shots per graph.

At \(2^{20}\) shots, R2 reaches:

$$0.9931,\quad0.9974,\quad0.9830,\quad0.9919.$$

Every one of the 576 paired replicate comparisons favors R2 over R0 or R1.

R1 is lower dimensional and more accurately sampled than R2 but remains much less predictive. This shows that the gain comes from preserving degree-class allocation, not generic pooling or dimensionality reduction alone.

### Permitted main-text sentence

> The finite-shot limitation is not uniform across readouts: supplementary experiments on four irregular graph strata show that degree-sector aggregation recovers analytical joint-degree mixing at 90% of its exact ceiling using approximately \(2^{14.6}\)–\(2^{17.1}\) shots, while global sorting and Hamming pooling remain substantially weaker.

### Scope

This is a readout-mechanism result. It does not establish general sample efficiency, cycle recovery, transfer of the cubic theorem, or quantum advantage.

---

## 5.2 E9 — optional perturbative mechanism check

E9 experimentally verifies the mixer mechanism:

* all cubic graphs collapse to the same sorted distribution at \(\beta=0\);
* the analytic first probability derivative matches the implemented circuit;
* median graph separation grows approximately linearly near zero, with slopes 0.951 and 0.937;
* triangles are weak in the isolated first-order feature and nearly exact in the second-order response;
* triangles, four-cycles, and girth remain robust over the tested mixer-angle ladder;
* six-cycle and diameter accessibility improve at larger mixer angles.

Use E9 only as a short mechanism confirmation. The theorem and exact circuit algebra are load bearing; E9 is not.

---

## 5.3 E2S — linear spectral baseline

E2S clarifies the difference between spectral content and linear accessibility.

* adjacency moments recover \(C_3\), \(C_4\), and \(C_5\) exactly by trace identities;
* sorted eigenvalues recover spectral gap exactly;
* QuIC makes girth almost linearly exact even when the tested spectral coordinates do not;
* QuIC plus spectral features improves displayed \(C_6\) prediction by 0.017 at both graph orders and diameter by 0.030/0.026.

Do not use these increments as proof of non-spectral information. They establish complementarity beyond specific **linear spectral coordinate systems**. E14 supplies the actual spectrum-fixed witness.

---

## 5.4 E24C — protocol-matched folklore 2-WL ranking

Within exact cospectral classes, cumulative folklore 2-WL substantially outperforms QuIC on Wiener-index ordering under the E14N protocol:

* folklore 2-WL: 0.904 and 0.878;
* QuIC: 0.603 and 0.607;
* aggregate advantage: 0.287;
* group-bootstrap interval: [0.223, 0.348].

The automorphism-order difference is unresolved because the aggregate interval includes zero.

This belongs in the supplement. The main paper may mention in one sentence that a protocol-matched functional comparison also favors 2-WL on Wiener ranking.

---

## 5.5 Irregular-graph scope synthesis

The main theorem and hierarchy are cubic. The irregular experiments define the boundary of transfer rather than extending the theorem.

### E21 — regularity transfer

On the complete 4-regular \(n=12\) census, QuIC retains strong decodability:

$$R^2=1.000,\ 0.999,\ 0.787,\ 0.922,\ 0.935$$

for \(C_3\), \(C_4\), \(C_5\), \(C_6\), and diamonds.

On the complete mixed-degree \(n=8\) census, the canonical representation collapses near the prediction floor. The hierarchy therefore transfers across regularities but not unchanged to arbitrary degree sequences.

### E25R — degree mixing dominates off-regular geometry

Under the exact E6 probe, joint-degree edge-type counts are nearly perfectly decoded within four fixed-degree-sequence strata:

* S1 and S2: 1.000;
* S3 mean: 0.962;
* S4 mean: 0.990.

Ordinary cycle totals remain much weaker outside the bimodal stratum. This supports joint-degree mixing as the dominant off-regular coordinate.

### E26R — degree-sector readout restores hidden structure

Under the matched E6 protocol, sector masses improve all four selected cells:

* S2 \(C_4\): 0.295 \(\rightarrow\) 0.783;
* S2 \(C_5\): 0.284 \(\rightarrow\) 0.463;
* S3 \(C_3\): -0.047 \(\rightarrow\) 0.807;
* S1 \(C_3\): 0.449 \(\rightarrow\) 0.987.

Sector masses are consistently stronger than sorting within sectors. The mechanism is aggregate degree-sector allocation, not within-sector rank shape.

### E30 — analytical mixing basis

E30 replaces the graph-sample-fitted SVD coordinates with the fixed-stub null-space basis. The analytical ranks are:

$$3,\quad1,\quad6,\quad5$$

for S1 through S4, with reconstruction error at floating-point precision and principal angles near machine zero relative to the empirical SVD subspace.

E30 is required to define the E29F target. It is not a main-paper experiment.

### Permitted scope statement

> The regular-graph hierarchy does not transfer unchanged to arbitrary degree sequences. In fixed-degree irregular strata, joint-degree mixing dominates the representation, and degree-conditioned readouts can make that channel both linearly and statistically accessible.

Do not claim a general irregular motif hierarchy.

---

## 5.6 Reproducibility and readout diagnostics

### E2C — precision audit

Use as supporting evidence that the ideal cospectral separations are not float64 artifacts. It is a numerical certification aid, not an independent contribution.

### E14N — split-null confirmation

Use for the computationally tractable confirmatory protocol behind the larger E14 Wiener and automorphism effects. The six diamond witnesses remain the main theorem-backed result.

### E16/E17 — relabeling and quotient diagnostics

These experiments verify that global sorting is label invariant and test whether the quotient collapses distinct graphs in small complete censuses. Use only as empirical diagnostics, never as proof of completeness.

### E20 — exact partition audit

E20 provides stronger numerical evidence that the sorted readout separates every graph in the complete \(n=8\) census under the tested parameters and precision checks. It remains an empirical finite-census result, not a universal injectivity theorem.

---

# 6. Claim-to-evidence index

| Manuscript claim | Canonical source | Status | Main-paper use |
|---|---|---|---|
| \(ZZ\) layer encodes the cut phase | Final formalism | proved | Section 3 |
| Walsh coefficients are boundary-sector enumerators | Final formalism | proved | Section 3 |
| sorting has a quantile/optimal-matching interpretation | Final formalism | proved | Section 2 |
| cubic \(M_2''(0)\) closes on \(C_3,C_4,D_\diamond\) | Final formalism | proved | Section 4, central theorem |
| explicit separation from ordinary 1-WL | Final formalism, prism/\(K_{3,3}\) | theorem corollary | Section 4 |
| explicit adjacency-cospectral diamond separation | Final formalism + E14 | theorem plus canonical witnesses | Sections 4 and 6 |
| complete cubic geometry follows \(C_3\rightarrow C_4\rightarrow C_5\) | E1 | exhaustive empirical | Section 5 |
| hierarchy is linearly accessible | E2 | held-out empirical | Section 5 |
| information is rank localized | E7 | held-out empirical | Section 5 / Figure 2 |
| folklore 2-WL is a strong classical control | E3C | exhaustive empirical | Section 6 |
| deeper motifs are harder to recover from samples | E15 | replicated finite-shot empirical | Section 6 |
| shot limitation depends on readout design | E29F-HX | required supplementary empirical | one main-text sentence |
| regular hierarchy does not transfer generally to irregular graphs | E21/E25R/E26R | supplementary scope evidence | discussion/supplement |
| precision and relabeling controls pass on tested data | E2C, E16/E17, E20 | numerical diagnostics | supplement only |
| prior CFI separation exists | QCE paper | prior work, not new AAAI evidence | one sentence only |

---

# 7. Planned manuscript assets

## Figure 1 — feature-map mechanism

Show:

$$G\rightarrow\text{cut phases}\rightarrow\text{hypercube mixing}\rightarrow\text{sorted Born distribution}\rightarrow\text{linear readout}.$$

Annotate:

* information contained;
* linearly accessible;
* statistically accessible.

## Figure 2 — exhaustive hierarchy and rank localization

Combine:

* E1 global and conditional hierarchy across \(n=14,16\);
* E7 truncation depth for \(C_3\) through \(C_6\).

The figure should make the structural ordering and rank ordering visually parallel.

## Table 1 or Figure 3 — controlled comparison

Include compactly:

* QuIC linear probe results;
* cumulative folklore 2-WL comparison;
* six exact cospectral diamond witnesses;
* finite-shot transition or limitation.

Do not add a large GNN table. If the object becomes too dense, retain the QuIC/2-WL table and place finite shots as an inset or short textual result.

---

# 8. Claim discipline for writing models

## Claims permitted directly

* The \(ZZ\) layer encodes the graph cut phase exactly.
* The boundary transform and stated low-order sector coefficients are exact.
* The mixer identity is exact.
* The sorted vector is permutation invariant and has the stated distributional interpretation.
* The cubic \(M_2''(0)\) closure is exact under its assumptions.
* The theorem yields explicit 1-WL and adjacency-cospectral separation witnesses.
* The complete \(n=14,16\) cubic censuses exhibit the reported hierarchy.
* The ridge probes quantify linear accessibility under the stated protocol.
* Folklore 2-WL is stronger on specified targets and separates every tested census graph.
* Fine motif recovery becomes substantially harder under finite sampling.

## Claims requiring explicit qualification

* “QuIC separates beyond \(k\)-WL” may refer only to prior tested CFI instances and must cite the QCE paper.
* “The representation contains \(C_5\) or \(C_6\)” is empirical unless tied to a proved coefficient or exact weak-mixer identity.
* “Useful head” means sufficient ranks on the tested censuses, not polynomial end-to-end complexity.
* “Beyond spectrum” means separation inside explicit adjacency-cospectral classes.
* “Shallow” refers to circuit depth, not measurement or classical postprocessing cost.
* “Training free” describes feature construction, not the downstream ridge probe.
* “Triangle dominated” means coefficient or empirical alignment at the canonical parameters, not exact triangle-only dependence.

## Claims prohibited in this submission

* universal completeness or injectivity of globally sorted probabilities;
* general dominance over 1-WL, 2-WL, or \(k\)-WL;
* formal incomparability with the WL hierarchy;
* quantum computational advantage;
* runtime, memory, storage, or sample-complexity advantage;
* practical sample efficiency for deep motifs;
* general irregular-graph motif hierarchy;
* exact finite-\(\beta\) motif decoding from infinitesimal derivatives;
* novelty of the general Ising/QAOA cut mapping;
* a claim that sorting merely removes vertex labels without additional information loss;
* protocol-sensitive E29 residual claims in the main paper;
* presentation of QCE hardware or CFI results as new AAAI evidence.

---

# 9. Main-paper, supplement, and archive allocation

## Main paper

Use only:

* selected final formalism required for the mechanism and central theorem;
* E1;
* E2;
* E7;
* E14 diamond witnesses;
* E3C in compact form;
* E15 in compact form;
* one E29F-HX discussion sentence;
* one prior-QCE CFI sentence.

E9 may appear as a small mechanism inset only if space remains.

## Required supplement

Include:

* complete final-formalism derivations needed to audit the theorem;
* complete E1 strata and PCA results;
* full E2 folds and targets;
* complete E7 curves;
* E9 perturbative validation;
* exact E14 graph identifiers, precision audit, and significance protocol;
* complete E3C construction and results;
* E24C;
* complete E15 curves and uncertainty;
* complete E29F-HX results and diagnostics;
* concise irregular scope synthesis using E21, E25R, E26R, and E30;
* E16/E17/E20 diagnostics, clearly labeled as empirical checks.

## Archive only unless the paper mutates

Everything in the omitted-experiment index below remains available in the full record but should not be supplied automatically to a writing model.

---

# 10. Omitted experimental data index

The entries below are retained so that a later manuscript revision can locate relevant work quickly. Descriptions are deliberately short. “Omitted” means omitted from the default paper-facing evidence set, not necessarily invalid.

| Experiment | Status | Very short description and reason for omission |
|---|---|---|
| E2R — Residual Probe | Partial | Early attempt to residualize spectral information; incomplete and replaced by stronger spectrum-fixed witnesses and later controls. |
| E3 — GNN Controls | Valid negative control | Constant-feature GIN/GCN-style models expose the ordinary 1-WL collapse, but a large weak-baseline table is strategically excluded once E3C is available. |
| E5 — Linear vs nonlinear methods | Exploratory | Nonlinear probes and probability-moment models did not materially improve the core argument. |
| E6 — Irregular Graphs | Valid scope result | Establishes off-regular collapse under flat encoding; later E25R/E26R identify the dominant mechanism more cleanly. |
| E6D — Degree-Encoding Ablation | Valid ablation | Tests explicit normalized degree encoding on irregular strata; useful if the irregular-readout discussion expands. |
| E6R — Circuit-Depth Ablation | Valid negative result | Increasing depth does not generally restore the lost irregular cycle hierarchy. |
| E8 — Cospectral Audit | Provenance | Reconstructs cospectral classes and identifies which invariants vary; superseded as a headline by E14. |
| E8B — Functional Cospectral Challenge | Earlier witness | Early \(n=16\) functional test inside exact cospectral classes; E14 is larger and theorem aligned. |
| E10 — Probe Validation | Diagnostic | Solver and shuffled-target controls for high-dimensional ridge results; useful for rebuttal or supplement but not a contribution. |
| E11 — Nonlinear Spectral Adequacy | Supporting | Tests a nonlinear spectral baseline and diamond residuals; E14 provides the cleaner exact spectrum-fixed statement. |
| E12 — Automorphism Audit | Incomplete | Timed out after partial results; no complete main-paper claim. |
| E13 — Truncation Decomposition | Supporting | Separates head shape from retained mass and completes some cospectral tracing; E7 is the cleaner main rank-localization result. |
| E14N — Split-Null Confirmation | Supplementary | Confirmatory split-null protocol for Wiener and automorphism ranking; retained for E14 support. |
| E16/E17 — Quotient and Label Control | Supplementary diagnostic | Verifies relabeling invariance and tests collapse under sorting on finite censuses; never proof of completeness. |
| E18 — Circuit Family Screen | Deferred | Broad screen of alternative circuit architectures; creates a separate circuit-design paper branch. |
| E19 — Angle Map | Deferred | Broad parameter map across circuit families; E9 is the mechanism-focused angle result and E29E-L is the local robustness result. |
| E20 — Exact Partition Audit | Supplementary diagnostic | Strong finite-census collision audit at \(n=8\); not a universal injectivity theorem. |
| E22 — Readout Geometry / Spectral Complementarity | Partial/qualified | Global geometry results are usable, but local-neighbor analysis contains a self-index defect and the second arm is incomplete. |
| E23 — Invariantization by Sorting | Exploratory | Compares sorting and alternative invariantizations; the final sorting proposition and E26R provide cleaner conclusions. |
| E24 — Original 2-WL Ranking | Superseded | Protocol mismatch degraded QuIC; use E24C instead. |
| E25 — Original Degree-Typed Decoding | Superseded | Decoder differences created unstable typed-target interpretations; use E25R. |
| E26 — Original Degree-Sector Ablation | Superseded | Protocol mismatch produced a false near-regular counterexample; use E26R. |
| E27 — Conditional Structure Audit | Valid but protocol sensitive | Tests mixing after cycle and spectral residualization; strategically excluded from the main paper. |
| E28-P0 — Finite-Shot Pilot | Incomplete | Runtime pilot terminated before a complete result. |
| E28 — Global vs Degree-Sector Finite Shots | Valid supporting experiment | R2 improves finite-shot mixing recovery but ideal cycle advantages remain inaccessible; E15 and E29F-HX provide the cleaner paper narrative. |
| E29A — Original Circuit/Readout Screen | Superseded | Uses empirical SVD mixing targets; use E29A-R if needed. |
| E29B — Original Conditional Audit | Superseded | Uses empirical target basis; use E29B-R if needed. |
| E29C — Original Classical Location | Superseded | Warning-prone concatenation analysis; use E29C-Rv2 and E29C-OV2 only for future work. |
| E29D — Original Complementarity | Partially invalid | Representation geometry is descriptive, but stacking was implemented incorrectly; use E29D-R for stacking. |
| E29P-R — Validated Producer | Infrastructure | Canonical circuit/readout artifact producer for revised E29 runs; provenance rather than a scientific claim. |
| E29A-R — Analytical-Basis Screen | Valid supplement/deferred | Confirms circuit-general mixing accessibility with the E30 basis; too broad for the current paper. |
| E29B-R — Analytical Conditional Audit | Valid but protocol sensitive | Conditional linear structure across circuits; excluded by the strategy’s main-paper claim discipline. |
| E29C-R v1 — Stabilized Classical Location | Invalid/superseded | Custom GCV omitted an orthogonal residual term and produced catastrophic values; replaced by Rv2. |
| E29C-O — Ridge-Residual Increment | Superseded | Ridge residuals were not exact projections; use E29C-OV2 for future work. |
| E29D-R — Corrected Stacking | Valid deferred result | Shows target-specific circuit complementarity, especially H-H on even cycles; separate ensemble branch. |
| E29E-L — Local Angle Robustness | Valid deferred result | H-X/F-Y mixing is locally robust, while H-H is strongly angle dependent; not needed for the narrow paper. |
| E29C-Rv2 — Explicit-SVD Classical Location | Valid but noncentral | Repairs numerical failures and supplies the corrected raw-concatenation table; strategy excludes protocol-sensitive residual narratives. |
| E29C-OV2 — Exact Linear-Span Increment | Valid but noncentral | Prespecified deeper-cycle residual gains survive exact projection, but augmented ridge fits remain ill conditioned; future/supplement only. |
| E30 — Analytical Mixing Basis | Supporting infrastructure | Defines a sample-independent fixed-stub basis used by E29F; include only where the irregular supplement requires it. |
| Earlier moment-bridge notebooks | Superseded formalism | Contained an incorrect unweighted purity correlator interpretation; replaced by the final formalism. |
| Earlier formalism notebook | Superseded formalism | Intermediate version before the final second- and third-order corrections and final theorem scope. |
| QCE CFI and hardware experiments | Prior work | Cite the QCE paper in one sentence; do not present as new AAAI evidence. |

---

# 11. Final instruction to writing models

Build the manuscript around one narrow chain:

$$\text{exact mechanism}\rightarrow\text{cubic motif theorem}\rightarrow\text{exhaustive hierarchy}\rightarrow\text{linear accessibility}\rightarrow\text{controlled boundaries}.$$

The paper is not an omnibus QuIC report. It does not need every positive result. It succeeds by showing:

1. what the feature map computes structurally;
2. one exact theorem with sharp consequences;
3. replication over complete graph populations;
4. honest comparison with a strong classical representation;
5. separation of ideal content, linear accessibility, and finite-shot accessibility.

When in doubt, omit an optional result rather than creating a new conceptual branch. Preserve the archive for later mutation of the paper, but do not allow the archive to determine the narrative.
