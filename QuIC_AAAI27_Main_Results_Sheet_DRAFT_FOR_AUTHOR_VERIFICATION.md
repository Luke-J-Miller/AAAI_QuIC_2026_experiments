# QuIC AAAI-27 Main Results Sheet

**Status:** Draft for author verification. Do not upload as an author-verified source until the checklist in Section 11 is complete.

**Purpose:** This is the only numerical-results source that should be available to the main-paper writing model. It contains the approved main-paper experiments, exact display values, protocol summaries, copy-safe claims, mandatory qualifications, and appendix pointers. It is intentionally narrower than the full scientific record.

**Canonical sources used:**

- QuIC_AAAI27_Curated_Evidence_Record(1).md;
- QuIC_Experimental_Results (5)(1).md, canonical sections E1, E2, E3C, E7, E14, E15, and E24C;
- e29f-hx-synthesis.ipynb only through the curated E29F-HX summary.

If this sheet conflicts with a canonical notebook or an author correction, flag the conflict and update this sheet. Never choose the more impressive value.

---

## 1. Global experimental conventions

### 1.1 Feature map

Unless explicitly stated otherwise, the representation is the exact descending-sorted Born probability vector

\[
\Phi_{\mathrm{QuIC}}(G)=p_G^\downarrow
\]

from one circuit repetition at

\[
\eta=2.875,\qquad \gamma=2.0,\qquad \beta=0.1.
\]

The regular-graph encoder is uniform. All exact-vector experiments are noiseless statevector calculations.

### 1.2 Exhaustive cubic censuses

| Order | Complete connected cubic graphs | Full QuIC dimension |
|---:|---:|---:|
| \(n=14\) | 509 | \(2^{14}=16{,}384\) |
| \(n=16\) | 4,060 | \(2^{16}=65{,}536\) |
| \(n=18\) | 41,301 | \(2^{18}=262{,}144\) |

E1, E2, E3C, E7, and E15 use the complete \(n=14\) and \(n=16\) censuses. E14 reconstructs exact cospectral classes across the complete \(n=18\) census but selectively simulates the qualifying witness groups rather than all full vectors.

### 1.3 Three distinct evidence levels

The manuscript must preserve:

\[
\text{information contained}
\not\equiv
\text{information linearly accessible}
\not\equiv
\text{information statistically accessible}.
\]

- E1 concerns representation geometry.
- E2 and E7 concern held-out linear accessibility from exact vectors.
- E14 concerns explicit finite-angle spectrum-fixed witnesses.
- E3C/E24C are strong classical controls.
- E15 concerns finite-shot accessibility of global sorting.
- E29F-HX is a supplementary counterpoint showing that accessibility depends on readout design.

---

## 2. E1 — exhaustive hierarchical geometry

### 2.1 Design

For every graph pair in a census, E1 compares the \(L_1\) distance between exact sorted QuIC vectors with absolute differences in cycle counts. Spearman Mantel tests are applied globally, then within fixed-\(C_3\) strata, then within fixed-\((C_3,C_4)\) strata.

The pairwise observations are dependent. The reported one-sided \(p\)-values use permutation inference and raw pair counts must not be interpreted as independent sample sizes.

### 2.2 Global Mantel results

| Structural quantity | \(n=14\) \(\rho\) | \(n=14\) \(p\) | \(n=16\) \(\rho\) | \(n=16\) \(p\) |
|---|---:|---:|---:|---:|
| \(C_3\) | 0.903 | 0.0001 | 0.900 | 0.0001 |
| \(C_4\) | 0.290 | 0.0001 | 0.303 | 0.0001 |
| \(C_5\) | 0.109 | 0.0001 | 0.079 | 0.0001 |
| random scalar control | 0.005 | 0.3152 | -0.007 | 0.9720 |

**Primary result:** triangle count dominates the global geometry and replicates almost identically across graph orders.

### 2.3 Conditional four-cycle organization

After fixing \(C_3\):

- every sufficiently populated \(n=14\) stratum has a \(C_4\) Mantel correlation in \([0.898,0.968]\);
- every sufficiently populated \(n=16\) stratum has a \(C_4\) Mantel correlation in \([0.853,0.964]\);
- fixed-triangle effective ranks lie approximately between 2.79 and 3.06.

Within the four largest fixed-triangle strata at \(n=16\):

| \(C_3\) stratum | PC1 variance | \(\rho(\mathrm{PC1},C_4)\) |
|---:|---:|---:|
| 0 | 0.541 | -0.985 |
| 1 | 0.547 | -0.980 |
| 2 | 0.536 | -0.978 |
| 3 | 0.541 | -0.981 |

The sign of a principal component is arbitrary; report the alignment as

\[
|\rho(\mathrm{PC1},C_4)|=0.978\text{--}0.985.
\]

### 2.4 Conditional five-cycle organization

After fixing both \(C_3\) and \(C_4\):

- all 16 qualifying \(n=14\) strata have positive \(C_5\) organization;
- all 43 qualifying \(n=16\) strata have positive \(C_5\) organization;
- the 43 qualifying \(n=16\) strata cover approximately 97.1% of that census.

### 2.5 Copy-safe main-paper claim

> Across the exhaustive connected cubic censuses at \(n=14\) and \(n=16\), QuIC geometry is organized hierarchically by short-cycle structure: triangles dominate globally, four-cycles define the leading direction after conditioning on triangles, and five-cycles organize the residual geometry after conditioning on both.

### 2.6 Mandatory qualification

E1 establishes metric organization, not causal encoding, a unique invariant coordinate, or completeness. It is exhaustive only for connected cubic graphs at the tested orders, circuit, angles, and exact readout.

### 2.7 Placement

Main paper: Figure 2 hierarchy panel.  
Supplement: Appendix~\(\ref{app:E1}\) for all strata, PCA details, and permutation protocols.

---

## 3. E2 — held-out linear accessibility

### 3.1 Design

E2 uses full exact sorted vectors on the same complete censuses. Five frozen shuffled outer folds and nested ridge regression estimate held-out linear accessibility.

### 3.2 Full-vector scores

Values are mean \(R^2\pm\) standard deviation across the five outer folds.

| Target | \(n=14\) QuIC \(R^2\) | \(n=16\) QuIC \(R^2\) | Main display? |
|---|---:|---:|:---:|
| \(C_3\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) | yes |
| \(C_4\) | \(0.998\pm0.002\) | \(1.000\pm0.000\) | yes |
| \(C_5\) | \(0.928\pm0.092\) | \(0.982\pm0.015\) | yes |
| \(C_6\) | \(0.485\pm0.326\) | \(0.642\pm0.122\) | yes, cautiously |
| girth | \(0.993\pm0.014\) | \(0.999\pm0.003\) | control table or supplement |
| diameter | \(0.548\pm0.058\) | \(0.737\pm0.019\) | control table or supplement |
| spectral gap | \(0.944\pm0.010\) | \(0.932\pm0.007\) | control table or supplement |

The principal accessibility hierarchy is

\[
C_3,C_4\ \longrightarrow\ C_5\ \longrightarrow\ C_6.
\]

### 3.3 Low-order probability-moment control

Probability power sums through order eight recover triangles and eventually four-cycles, but not the strong full-vector \(C_5\) result:

| Target | \(n=14\), moments through 8 | \(n=16\), moments through 8 |
|---|---:|---:|
| \(C_3\) | 1.000 | 1.000 |
| \(C_4\) | 0.997 | 0.998 |
| \(C_5\) | 0.106 | 0.084 |
| \(C_6\) | 0.198 | 0.144 |

This establishes failure of the tested low-order compression, not failure of every possible symmetric summary.

### 3.4 Copy-safe main-paper claim

> Simple held-out linear probes recover the geometric hierarchy: triangles and four-cycles are essentially exact, five-cycles remain strongly accessible, and six-cycles form a weaker and less stable layer.

### 3.5 Mandatory qualification

These are high-dimensional ridge probes on exact vectors. They establish linear accessibility under the stated protocol, not a unique coordinate, efficient measurement, causal encoding, or computational advantage. Replication at \(n=16\) is important because the \(n=14\) feature dimension greatly exceeds the number of graphs.

### 3.6 Placement

Main paper: compact \(C_3\)–\(C_6\) table.  
Supplement: Appendix~\(\ref{app:E2}\) for folds, hyperparameters, auxiliary targets, power sums, and validation checks.

---

## 4. E7 — rank localization

### 4.1 Design

E7 repeats the E2 cycle probes after retaining only the first

\[
k\in\{25,50,100,200,400,1000,4000\}
\]

sorted probabilities. The truncated head is not renormalized.

### 4.2 Representative saturation points

| Target | \(k\) | \(n=14\) \(R^2\) | \(n=16\) \(R^2\) |
|---|---:|---:|---:|
| \(C_3\) | 25 | \(1.000\pm0.000\) | \(1.000\pm0.000\) |
| \(C_4\) | 100 | \(0.993\pm0.004\) | \(0.996\pm0.001\) |
| \(C_5\) | 400 | \(0.927\pm0.092\) | \(0.981\pm0.015\) |
| \(C_6\) | 1,000 | \(0.484\pm0.327\) | \(0.640\pm0.121\) |

At \(n=16\), increasing from \(k=1000\) to \(k=4000\) changes \(C_6\) only from \(0.640\pm0.121\) to \(0.642\pm0.122\), with essentially no gain for the other cycle targets.

### 4.3 Approved interpretation

| Target | Practical rank location |
|---|---|
| \(C_3\) | extreme head, at most 25 in the tested grid |
| \(C_4\) | approximately first \(10^2\) |
| \(C_5\) | approximately first \(2\text{--}4\times10^2\) |
| \(C_6\) | approximately first \(4\times10^2\text{--}10^3\), with weaker stability |

### 4.4 Copy-safe main-paper claim

> QuIC’s structural information is rank stratified: triangles occupy the extreme probability head, four-cycles appear within roughly the first hundred ranks, five-cycles within a few hundred, and the weaker six-cycle signal extends to roughly the first thousand.

### 4.5 Mandatory qualification

This is rank localization, not proof of a polynomial-size representation or efficient measurability. The identities of top outcomes must still be discovered from samples. The grid is coarse and does not establish minimal cutoffs or asymptotic scaling.

### 4.6 Placement

Main paper: Figure 2 rank-depth panel.  
Supplement: Appendix~\(\ref{app:E7}\) for complete curves and fold variation.

---

## 5. E14 — theorem-backed adjacency-cospectral witnesses

### 5.1 Design

E14 reconstructs exact adjacency-cospectral classes across all 41,301 connected cubic graphs at \(n=18\) using integer trace tuples. Six cospectral classes contain a pair that exchanges exactly one pair-incidence diamond for one six-cycle:

\[
|\Delta D_\diamond|=1,\qquad \Delta C_6=-\Delta D_\diamond.
\]

### 5.2 Witness identifiers and separations

| Group | Graph indices | \(D_\diamond\) | \(C_6\) | Full-vector \(L_1\) separation |
|---:|---|---|---|---:|
| 257 | 12,891 / 29,287 | 1 / 0 | 6 / 7 | \(1.619\times10^{-5}\) |
| 401 | 29,752 / 31,179 | 1 / 0 | 5 / 6 | \(1.590\times10^{-5}\) |
| 438 | 36,289 / 40,737 | 0 / 1 | 6 / 5 | \(1.590\times10^{-5}\) |
| 451 | 37,702 / 39,791 | 1 / 0 | 8 / 9 | \(1.624\times10^{-5}\) |
| 461 | 38,826 / 40,082 | 1 / 0 | 4 / 5 | \(1.592\times10^{-5}\) |
| 468 | 39,793 / 40,655 | 0 / 1 | 11 / 10 | \(1.626\times10^{-5}\) |

The within-pair separations were checked with exact/high-precision supporting audits.

### 5.3 Primary result

- QuIC correctly ranks diamond count in all six held-out pairs.
- Equivalently, it ranks \(C_6\) in the reverse direction.
- The primary top-100 representation gives 6/6.
- The result is 6/6 at every tested ridge regularization.
- It is also 6/6 at every tested truncation depth \(k\in\{50,100,200,500,1000,262144\}\).
- The selection-corrected sign-flip result is \(p=0.0462\), computed conservatively as \(3/65\).

### 5.4 Copy-safe main-paper claim

> The theorem’s diamond term is realized by six exact adjacency-cospectral cubic witness pairs at \(n=18\): each pair exchanges one diamond for one six-cycle, and QuIC ranks all six correctly using the first 100 sorted probabilities.

### 5.5 Mandatory qualification

This is an explicit theorem-backed witness set, not universal cospectral separation. “Beyond spectrum” means beyond adjacency-spectrum equivalence on these pairs; it does not mean beyond classical computation. E14 selectively simulates qualifying cospectral groups and is not a full-vector probe over all 41,301 graphs.

### 5.6 Placement

Main paper: immediately after the cospectral corollary or in the controlled-comparison section.  
Supplement: Appendix~\(\ref{app:E14}\) for identifiers, exact spectra/traces, precision, selection correction, and all depths.

---

## 6. E3C — folklore 2-WL control

### 6.1 Design

The implemented baseline is **folklore 2-WL on ordered vertex pairs**, not an unspecified “2-WL.” Two readouts are tested:

- cumulative histograms over refinement rounds;
- stable-only final histograms.

Color vocabularies are synchronized over each complete census. This construction is target-free but transductive and must be documented in the supplement.

Ordinary 1-WL is constant on each fixed-order cubic census and therefore has no predictive variation.

### 6.2 Discrimination

- Stable folklore 2-WL distinguishes all 509 graphs at \(n=14\).
- Stable folklore 2-WL distinguishes all 4,060 graphs at \(n=16\).
- It separates all 3 exact cospectral pairs at \(n=14\) and all 43 pairwise cospectral comparisons at \(n=16\).
- QuIC separates those same tested cospectral comparisons.
- Stable-only graph-unique histograms nevertheless have near-zero held-out ridge performance because their coordinates are graph-specific.

### 6.3 Linear-probe comparison

Values are mean \(R^2\pm\) standard deviation across the same five outer folds.

| Target | \(n=14\) folklore 2-WL | \(n=14\) QuIC | \(n=16\) folklore 2-WL | \(n=16\) QuIC |
|---|---:|---:|---:|---:|
| \(C_3\) | \(0.998\pm0.001\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) |
| \(C_4\) | \(0.993\pm0.004\) | \(0.998\pm0.002\) | \(0.999\pm0.000\) | \(1.000\pm0.000\) |
| \(C_5\) | \(0.917\pm0.038\) | \(0.928\pm0.092\) | \(0.993\pm0.002\) | \(0.982\pm0.015\) |
| \(C_6\) | \(0.879\pm0.061\) | \(0.485\pm0.326\) | \(0.983\pm0.003\) | \(0.642\pm0.122\) |
| girth | \(0.787\pm0.071\) | \(0.993\pm0.014\) | \(0.844\pm0.016\) | \(0.999\pm0.003\) |
| diameter | \(0.779\pm0.031\) | \(0.548\pm0.058\) | \(0.861\pm0.012\) | \(0.737\pm0.019\) |
| spectral gap | \(0.947\pm0.028\) | \(0.944\pm0.010\) | \(0.982\pm0.002\) | \(0.932\pm0.007\) |

### 6.4 Copy-safe main-paper claim

> Folklore 2-WL is a strong classical control: it distinguishes every tested census graph and nearly saturates cycle prediction, substantially exceeding QuIC on six-cycles and diameter. QuIC remains stronger on girth and closely matched on the shorter-cycle targets. Final discrimination and transferable linear accessibility are not the same property.

### 6.5 Mandatory qualification

Do not describe folklore 2-WL as defeated, infer formal incomparability, or claim a universal expressive ordering. Feature dimensions are also not directly comparable measures of computational complexity: both tested representations are high dimensional, with different sparsity and construction costs.

### 6.6 Placement

Main paper: one compact comparison table.  
Supplement: Appendix~\(\ref{app:E3C}\) for update rules, synchronized vocabularies, dimensions, fold variation, and stable-only behavior.

---

## 7. E24C — protocol-matched ranking control

This result belongs in the supplement but supports one main-paper scope sentence.

Within exact cospectral classes under the E14N protocol:

| Representation | Wiener direction A | Wiener direction B | aggregate |
|---|---:|---:|---:|
| QuIC top-100 | 0.603 | 0.607 | 0.605 |
| cumulative folklore 2-WL | 0.904 | 0.878 | 0.892 |

The aggregate advantage of folklore 2-WL is 0.287, with group-bootstrap interval \([0.223,0.348]\). The automorphism-order difference is unresolved because its interval includes zero.

**Permitted main-paper sentence:**

> A protocol-matched comparison within exact cospectral classes likewise favors cumulative folklore 2-WL over QuIC for Wiener-index ranking; see Appendix~\(\ref{app:E24C}\).

Do not display this as a second major 2-WL experiment in the main paper.

---

## 8. E15 — finite-shot accessibility of global sorting

### 8.1 Design

E15 uses the complete \(n=14\) and \(n=16\) cubic censuses. Independent multinomial samples are generated for training and test representations. The experiment completed all 198 planned grid cells with 30 unique replicates per cell:

- 180 \(n=14\) cells;
- 18 \(n=16\) cells.

Reported uncertainty is across replicate-level mean outer-fold \(R^2\) values. This is ideal multinomial sampling, not a hardware or device-noise experiment.

### 8.2 Exact and sampled results

At \(n=14\), using the unrenormalized top \(k=500\):

| Target | \(2^{20}\) shots | \(2^{22}\) shots | \(2^{24}\) shots | exact top-500 |
|---|---:|---:|---:|---:|
| \(C_3\) | 0.715 | 0.950 | 0.994 | 1.000 |
| \(C_4\) | -0.010 | 0.167 | 0.684 | 0.998 |
| \(C_5\) | -0.016 | -0.013 | -0.015 | 0.927 |
| \(C_6\) | 0.043 | 0.105 | 0.140 | 0.524 |
| \(D_\diamond\) | 0.314 | 0.522 | 0.588 | 0.994 |
| girth | 0.358 | 0.734 | 0.888 | 0.993 |

At \(n=16\), using top \(k=1000\):

| Target | \(2^{20}\) shots | \(2^{22}\) shots | \(2^{24}\) shots | exact top-1000 |
|---|---:|---:|---:|---:|
| \(C_3\) | 0.718 | 0.951 | 0.994 | 1.000 |
| \(C_4\) | 0.003 | 0.199 | 0.668 | 1.000 |
| \(C_5\) | -0.001 | -0.001 | -0.001 | 0.982 |

### 8.3 Triangle recovery thresholds

| Census | 90% of exact score | approximate shots | 95% of exact score | approximate shots |
|---|---:|---:|---:|---:|
| \(n=14\) | \(2^{21.57}\) | \(3.11\times10^6\) | \(2^{22.00}\) | \(4.19\times10^6\) |
| \(n=16\) | \(2^{21.56}\) | \(3.10\times10^6\) | \(2^{21.99}\) | \(4.17\times10^6\) |

### 8.4 Cospectral separation versus sampling noise

Across the tested shot ladder, the ratio of an exact cospectral-mate distance to repeat-sampling distance remains of order one. At \(2^{24}\) shots, the mean ratios are 1.215 at \(n=14\) and 1.004 at \(n=16\). This supports the narrow statement that the tested exact cospectral separations remain comparable to sampling variation.

### 8.5 Copy-safe main-paper claim

> The ideal hierarchy is also a hierarchy of measurement difficulty. Triangle prediction becomes reliable only at millions of shots per graph; four-cycles and diamonds remain partially recovered at \(2^{24}\) shots; five-cycle prediction remains absent despite strong exact-vector accessibility; and exact cospectral separations remain near the sampling-noise scale.

### 8.6 Mandatory qualification

This result concerns independent ideal multinomial sampling of the globally sorted readout. It is not a hardware result, universal shot lower bound, or statement about every possible invariant readout.

### 8.7 Placement

Main paper: one compact curve, inset, or table in the controlled-boundaries section.  
Supplement: Appendix~\(\ref{app:E15}\) for the complete shot ladder, all truncations, uncertainty, head discovery, and distance diagnostics.

---

## 9. Required supplementary counterpoint: E29F-HX

The main paper may use exactly one substantive sentence from this experiment:

> The finite-shot limitation is not uniform across readouts: supplementary experiments on four irregular graph strata show that degree-sector aggregation recovers analytical joint-degree mixing at 90% of its exact ceiling using approximately \(2^{14.6}\)–\(2^{17.1}\) shots, while global sorting and Hamming pooling remain substantially weaker; see Appendix~\(\ref{app:E29-HX}\).

Supporting values retained for verification:

- four fixed-degree-sequence strata, 400 graphs each;
- H-X circuit;
- target: the E30 analytical joint-degree mixing coordinate;
- exact R2 scores: 0.9997, 1.0000, 0.9991, 0.9992;
- R2 at \(2^{16}\) shots: 0.916, 0.963, 0.845, 0.912;
- R2 at \(2^{20}\) shots: 0.9931, 0.9974, 0.9830, 0.9919;
- all 576 paired replicate comparisons favor R2 over R0 or R1.

Here R0 is global sorting, R1 is Hamming-weight pooling, and R2 is degree-sector mass pooling.

**Do not claim:** general sample efficiency, cycle recovery, transfer of the cubic theorem, or quantum advantage. The detailed experiment belongs only in Appendix~\(\ref{app:E29-HX}\).

---

## 10. Main-paper display budget and claim map

### Figure 2: hierarchy and rank localization

Use:

- E1 global \(C_3\) Mantel result at both orders;
- fixed-\(C_3\) \(C_4\) range or PC1 alignment;
- fixed-\((C_3,C_4)\) positive \(C_5\) result;
- E7 representative \(k\) locations for \(C_3\)–\(C_6\).

Do not place all stratum tables in the main paper.

### Main accessibility table

Use:

- E2 \(C_3\)–\(C_6\) full-vector scores;
- cumulative folklore 2-WL means for the same targets;
- optionally girth if space permits and its role is explained.

Do not add a broad GNN benchmark table.

### Cospectral witness box

Use:

- six exact \(n=18\) pairs;
- 6/6 with top 100;
- \(p=0.0462\);
- one sentence that each pair exchanges \(D_\diamond\) and \(C_6\).

Do not add the larger Wiener or automorphism E14 results to this box.

### Finite-shot boundary

Use:

- triangle 90% threshold near \(3.1\times10^6\);
- \(2^{24}\) values for \(C_4\), \(C_5\), and diamonds at \(n=14\), or a compact cross-order view;
- one E29F-HX appendix sentence to prevent a universal-readout interpretation.

---

## 11. Author verification checklist

### Global

- [ ] The circuit angles and one-repetition description match the released artifacts.
- [ ] Census counts and QuIC dimensions are correct.
- [ ] “Exact” consistently means noiseless numerical statevector output, not symbolic arithmetic.

### E1

- [ ] Global Mantel coefficients and permutation \(p\)-values match E1.
- [ ] Conditional \(C_4\) ranges and PC1 values match the qualifying-stratum rules.
- [ ] The 16/43 positive \(C_5\) stratum counts and 97.1% coverage are correct.

### E2/E7

- [ ] All displayed \(R^2\) values use the same frozen-fold/nested-ridge protocol.
- [ ] Standard deviations are across the five outer folds.
- [ ] The E7 head is unrenormalized and the \(n=16\) full-vector E7 run did not complete.
- [ ] The main paper does not convert tested \(k\) values into minimum or asymptotic bounds.

### E14

- [ ] Graph indices match the final canonical census ordering.
- [ ] Exact-cospectral reconstruction and precision checks are complete.
- [ ] The six pairs use the pair-incidence diamond convention in the theorem sheet.
- [ ] \(p=0.0462\) is described as the selection-corrected conservative add-one value.

### E3C/E24C

- [ ] The implementation is named folklore 2-WL on ordered pairs.
- [ ] Synchronized vocabulary is described as target-free but transductive.
- [ ] The manuscript does not claim a general ordering against the WL hierarchy.
- [ ] E24C is supplementary and its automorphism comparison is not called resolved.

### E15/E29F-HX

- [ ] E15 consists of 198 cells with 30 unique replicates per cell.
- [ ] Training and test measurement realizations are independent.
- [ ] Shot thresholds and \(2^{24}\) values match the final E15 artifact.
- [ ] E15 is described as ideal multinomial sampling of global sorting.
- [ ] E29F-HX values match the synthesis notebook and appear only as a readout counterpoint.

After verification, rename this file:

**QuIC_AAAI27_Main_Results_Sheet_VERIFIED.md**

---

## 12. Claims prohibited even if suggested by another source

- universal or generic injectivity;
- complete graph invariance;
- quantum advantage or speedup;
- practical dominance over classical graph representations;
- dominance over 1-WL, folklore 2-WL, or \(k\)-WL;
- universal cospectral separation;
- a theorem that \(C_3\to C_4\to C_5\) holds for arbitrary graph families;
- a claim that the second-purity theorem explains the full \(\beta=0.1\) geometry quantitatively;
- polynomial-size or sample-efficient recovery inferred from E7;
- a universal finite-shot barrier inferred from E15;
- general irregular-graph transfer;
- promotion of E29F-HX to a fourth contribution.
