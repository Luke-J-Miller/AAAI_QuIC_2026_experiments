# QuIC AAAI-27 Supplement Writing Packet

## 0. Operating instruction for the supplement model

Use this packet only after the seven-page main manuscript is structurally frozen.

The supplement exists to substantiate claims already made in the main paper. It must not mutate the thesis, add a contribution, introduce a competing theoretical framework, or turn the submission into an omnibus QuIC report.

The supplement model receives:

1. the frozen main manuscript;
2. this supplement packet;
3. the author-verified final formalism;
4. only the canonical notebooks or result artifacts named here.

Do not provide the complete experimental archive unless a specific provenance question cannot be resolved from the canonical artifacts.

If supplementary evidence suggests a new paper-level claim, label it **deferred** rather than revising the main paper.

## 1. Acceptance objective

The supplement should increase reviewer confidence without increasing the conceptual burden of the main paper.

Optimize for:

- auditable proofs;
- reproducible experiments;
- explicit protocol qualifications;
- clean mapping from every main claim to supporting evidence;
- easy reviewer navigation.

Do not optimize for maximum breadth. A reviewer should be able to open the appendix cited by the main paper, verify the relevant claim, and stop.

## 2. Label contract

The supplement must implement the labels already promised by the main manuscript.

| Label | Required content |
|---|---|
| `app:boundary-transform` | weighted boundary-sector derivation and normalization |
| `app:sorting` | sorted-distance/quantile proof |
| `app:M2-proof` | full purity carrier enumeration and coefficient algebra |
| `app:cospectral-proof` | spectral identities used by the diamond corollary |
| `app:E1` | full hierarchy strata and PCA |
| `app:E2` | complete ridge protocol and fold results |
| `app:E7` | complete truncation curves |
| `app:E9` | perturbative mechanism check |
| `app:E14` | witness identifiers, precision, and significance |
| `app:E3C` | full folklore 2-WL construction and results |
| `app:E15` | complete finite-shot protocol and curves |
| `app:E24C` | protocol-matched Wiener ranking |
| `app:E29-HX` | readout capabilities beyond global sorting |
| `app:irregular` | irregular-graph scope synthesis |
| `app:numerics` | precision, relabeling, and finite-census diagnostics |

Do not rename labels after the main paper uses them.

## 3. Mathematical supplement

### Appendix `app:boundary-transform`

Required:

- complete circuit and Fourier/Walsh normalization conventions;
- encoder amplitude \(a_\eta(x)\);
- exact degree-/encoder-weighted boundary-sector transform;
- reduction to the unweighted sector polynomial used for motif interpretation;
- derivation of the closed-sector coefficients through six edges;
- sign and global-phase checks;
- executable assertion or symbolic check references.

Guardrail: do not collapse the encoder-weighted transform into the pure unweighted polynomial.

### Appendix `app:sorting`

Required:

- definition of \(\nu_G=2^{-n}\sum_x\delta_{2^np_G(x)}\);
- rearrangement proof that descending sorting minimizes equal-cardinality \(L_1\) matching;
- proof of the stated \(W_1\) identity under the chosen scaling;
- explicit statement that global sorting is coarser than vertex relabeling and is not proved complete.

Do not expand into general moment reconstruction, replica models, or a full quotient theory.

### Appendix `app:M2-proof`

Required:

- exact definition of \(M_2(G;\beta)\) and derivative convention;
- zeroth- and first-order common-mode results for same-order regular graphs;
- full second-order expansion;
- carrier classification;
- algebraic third-difference cancellation;
- explicit formulas for \(A_n,b_3,b_4,b_D\);
- numerical coefficient evaluation at the canonical \(n=14,\eta=2.875,\gamma=2.0\) setting;
- author-verified symbolic or executable checks.

The supplement may provide full proof detail, but the main paper must retain the theorem statement, assumptions, cancellation idea, and enough proof to be independently credible.

### Appendix `app:cospectral-proof`

Required:

- spectral trace identities fixing the relevant lower motif quantities on cubic cospectral graphs;
- proof that a diamond difference yields unequal second derivatives when \(b_D\neq0\);
- analytic argument from unequal local Taylor coefficient to separation for sufficiently small nonzero \(\beta\);
- explicit distinction between local theorem and E14’s independent finite-\(\beta=0.1\) verification.

## 4. Main-experiment appendices

### Appendix `app:E1`: exhaustive hierarchy

Include:

- census generation and verification;
- graph counts \(509\) and \(4{,}060\);
- circuit configuration;
- pairwise-distance construction;
- Mantel permutation protocol;
- every fixed-\(C_3\) and fixed-\((C_3,C_4)\) qualifying stratum;
- PCA protocol and effective-rank definition;
- complete numerical tables and uncertainty;
- random-control construction.

Qualification: dependent pairwise observations and one-sided permutation inference must be stated.

### Appendix `app:E2`: linear accessibility

Include:

- frozen outer folds and nested ridge protocol;
- exact feature construction;
- all targets and definitions;
- fold-level \(R^2\);
- selected regularization diagnostics;
- shuffled-target and solver checks if needed to validate the high-dimensional fits;
- complete results beyond the four cycle targets shown in the main paper.

Do not turn supplementary targets into new contribution claims.

### Appendix `app:E7`: rank localization

Include:

- truncation grid \(k\in\{25,50,100,200,400,1000,4000\}\);
- whether the truncated head is renormalized;
- complete curves at both graph orders;
- folds and decoder protocol;
- statement that outcome identities must still be discovered from samples;
- statement that the grid does not establish minimal cutoffs or polynomial complexity.

### Appendix `app:E9`: perturbative mechanism check

Include:

- common collapse at \(\beta=0\);
- analytic first-derivative implementation check;
- small-\(\beta\) geometry scaling;
- second-order triangle emergence;
- tested angle ladder and target behavior.

E9 is confirmatory. Do not present it as a separate contribution or substitute it for the exact theorem.

### Appendix `app:E14`: cospectral witnesses

Include:

- complete connected cubic \(n=18\) census construction;
- exact cospectral-class reconstruction;
- graph identifiers for the six witness pairs;
- adjacency spectra or exact trace certificates;
- \(C_3,C_4,C_6,D_\diamond\) and other relevant invariants;
- exact/high-precision QuIC distances;
- all tested truncations and regularization settings;
- selection-corrected sign-flip protocol and \(p=0.0462\);
- explicit statement that this is a selected theorem-backed witness set, not universal cospectral separation.

### Appendix `app:E3C`: folklore 2-WL

Include:

- ordered-pair initialization and update rule;
- number of refinement rounds;
- cumulative and stable-only histogram definitions;
- synchronized-vocabulary construction;
- complete representation dimensions;
- all graph-discrimination and cospectral results;
- full target table;
- fold and ridge protocol;
- stable-only transfer result.

Required qualifications:

- the shared vocabulary is target-free but transductive because it is constructed over the complete census;
- 2-WL representations are high-dimensional and sparse;
- exact QuIC vectors are dense and exponentially sized;
- feature dimension alone does not establish a computational ordering;
- discrimination and transferable linear accessibility are different properties.

### Appendix `app:E15`: finite-shot global sorting

Include:

- independent multinomial sampling of train and test representations;
- complete shot ladder;
- all 198 grid cells and 30 replicates per cell;
- exact-vector normalization used for recovery thresholds;
- full target curves at both graph orders;
- uncertainty and threshold interpolation;
- repeat-sampling distances and exact cospectral-mate distances;
- distinction between ideal sampling and hardware noise.

Do not infer a universal shot barrier. The result concerns the tested global sorted readout.

## 5. Required readout counterpoint

### Appendix `app:E29-HX`

Scientific question:

> Can a structurally aligned invariant readout expose irregular-graph information that is poorly accessible through global sorting or generic Hamming pooling?

#### Configuration

- \(n=14\);
- four fixed-degree-sequence strata, 400 graphs each;
- circuit: \(H^{\otimes n}\), \(R_{ZZ}(2.0)\) on graph edges, then \(R_X(0.1)\);
- 12 deterministic paired sampling replicates;
- shot ladder \(2^{10},2^{12},2^{14},2^{16},2^{18},2^{20}\);
- nested ridge with five outer and five inner folds;
- target: E30 analytical joint-degree mixing coordinates of ranks \(3,1,6,5\) for S1–S4.

#### Readouts

- **R0:** top-1,000 globally sorted probabilities used by the decoder; full sorted distribution used only for the total-variation diagnostic;
- **R1:** 15 Hamming-weight masses;
- **R2:** degree-sector masses with 99, 64, 315, and 216 sectors across S1–S4.

#### Exact-vector linear-probe ceilings

| Stratum | R0 | R1 | R2 |
|---|---:|---:|---:|
| S1 near-regular | 0.0700 | 0.6063 | 0.9997 |
| S2 bimodal | 0.5531 | 0.9958 | 1.0000 |
| S3 skewed | 0.1242 | 0.4670 | 0.9991 |
| S4 hub | 0.0900 | 0.3823 | 0.9992 |

These are cross-validated exact-statevector \(R^2\) values, not information-theoretic ceilings.

#### Finite-shot results

At \(2^{16}\) shots, R2 achieves:

\[
0.916,\quad0.963,\quad0.845,\quad0.912
\]

across S1–S4. It reaches 90% of its exact-vector ceiling at approximately

\[
2^{15.79},\quad2^{14.59},\quad2^{17.05},\quad2^{15.86}
\]

shots, respectively.

Across 48 stratum/budget/readout comparisons, each evaluated with 12 paired sampling replicates, the R2-R0 and R2-R1 mean differences are positive with bootstrap intervals excluding zero; every individual paired replicate difference is also positive.

#### Required interpretation

The result shows that statistical accessibility depends on readout design. R1 controls for generic aggregation and lower dimension; its failure despite occasionally high exact-vector ceilings supports a specifically degree-conditioned advantage.

#### Required limitations

- target and readout are intentionally structurally aligned;
- this is not cycle or diamond recovery;
- it does not extend the cubic theorem;
- R0 uses a top-1,000 decoder head rather than the full exact vector;
- matched-shot absolute \(R^2\) and raw curves should be emphasized over ratios relative to different ceilings;
- thresholds use monotone summaries, so raw mean curves must also be shown;
- no claim of quantum advantage or general sample efficiency is permitted.

## 6. Additional required supplementary controls

### Appendix `app:E24C`

Report the protocol-matched within-cospectral-class Wiener-ranking comparison:

- folklore 2-WL: 0.904 and 0.878;
- QuIC: 0.603 and 0.607;
- aggregate advantage: 0.287;
- group-bootstrap interval: \([0.223,0.348]\).

Automorphism-order superiority is unresolved because its aggregate interval includes zero.

Use this as a scope control, not as proof of formal representational incomparability.

### Appendix `app:irregular`

Synthesize only the canonical irregular results needed to define scope.

#### Regularity transfer

On the complete 4-regular \(n=12\) census, exact QuIC ridge scores are

\[
1.000,\ 0.999,\ 0.787,\ 0.922,\ 0.935
\]

for \(C_3,C_4,C_5,C_6,D_\diamond\). On the mixed-degree \(n=8\) census, the canonical hierarchy collapses near the prediction floor.

#### Joint-degree dominance

Within four fixed-degree-sequence irregular strata, analytical joint-degree mixing is the dominant accessible coordinate. Use only the corrected E25R interpretation.

#### Degree-sector readout

Under the corrected matched protocol, sector masses improve:

- S2 \(C_4\): 0.295 \(\rightarrow\) 0.783;
- S2 \(C_5\): 0.284 \(\rightarrow\) 0.463;
- S3 \(C_3\): -0.047 \(\rightarrow\) 0.807;
- S1 \(C_3\): 0.449 \(\rightarrow\) 0.987.

Sector mass is stronger than sorting within sectors. Do not claim a general irregular motif hierarchy.

#### Analytical target basis

E30 replaces sample-fitted SVD targets with a fixed-stub analytical basis of ranks \(3,1,6,5\). It is supporting infrastructure for E29-HX, not an independent contribution.

### Appendix `app:numerics`

Include only:

- high-precision audit of selected ideal separations;
- relabeling invariance checks;
- finite-census collision diagnostics;
- explicit statement that none proves universal injectivity.

## 7. Claim-to-run index

The supplement must contain a one-page navigation table:

| Main claim or asset | Appendix label | Canonical experiment/formal source | Script/notebook | Output artifact | Status |
|---|---|---|---|---|---|

Statuses must be one of:

- proved;
- exhaustive empirical;
- replicated empirical;
- numerical diagnostic;
- prior work.

Do not use “validated” as a substitute for identifying whether a result is proved or empirical.

## 8. Material prohibited from the supplement

Do not include merely because space is available:

- additional theorem families not cited by the main paper;
- universal injectivity or completeness arguments;
- unproved higher-order motif closure;
- broad circuit-family and angle screens;
- protocol-sensitive residual analyses;
- superseded experiment versions;
- incomplete or timed-out experiments;
- application benchmarks not used by the main paper;
- QCE hardware or CFI experiments reproduced as new evidence;
- an omitted-experiment catalog.

The full scientific archive remains separate. The supplement is curated support, not a second archive.

## 9. Supplement writing order

1. Implement the appendix labels already cited by the frozen main paper.
2. Write `app:M2-proof`, `app:boundary-transform`, and `app:cospectral-proof` first.
3. Build the claim-to-run index.
4. Write the canonical main-experiment appendices in manuscript order.
5. Add E29-HX and the irregular scope synthesis.
6. Add numerical and relabeling diagnostics last.
7. Audit every supplement statement against the frozen main claim it supports.
8. Remove any result that creates a new abstract-level contribution.

## 10. Final instruction

The supplement should let a skeptical reviewer verify the paper without discovering a different paper inside it.

Its structure is:

\[
\text{main claim}
\rightarrow
\text{named appendix}
\rightarrow
\text{complete proof or canonical protocol}
\rightarrow
\text{reproducible artifact}.
\]

Do not allow supplementary abundance to weaken the main paper’s narrow acceptance strategy.
