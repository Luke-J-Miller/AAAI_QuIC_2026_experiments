# QuIC Characterization — Experimental Results

Full per-experiment write-ups for the AAAI 2027 QuIC characterization study: experimental design, results, what each experiment establishes, qualifications, and overall assessment, for every experiment E1 through E8B. This is a results record only — for the object definition, mathematical framework, project status, and the direction the work is currently taking, see the companion project-state document.

## Full Description of Experiments

### E1 - Stratified Residue

#### Experimental design

The experiment analyzes the complete connected cubic-graph censuses at two graph orders:

* **509 graphs at (n=14)**;
* **4,060 graphs at (n=16)**.

Each graph is represented by its full sorted QuIC probability vector:

$$
\mathbf p(G)\in\mathbb R^{2^n},
$$

with dimensions

$$
2^{14}=16{,}384,
\qquad
2^{16}=65{,}536.
$$

The vectors are generated using one noiseless circuit repetition and the same fixed canonical angles at both graph orders.

These censuses provide a particularly clean test bed:

* every graph within a census has the same order;
* every graph is 3-regular and therefore has the same degree sequence;
* the degree-encoding rotations are identical across all graphs;
* bitstring identities are discarded by sorting the output probabilities;
* any remaining geometric separation must arise from topology transmitted through the entangling circuit rather than from vertex degree or labeling.

The experiment compares pairwise (L_1) distances between QuIC embeddings with absolute differences in:

* triangle count;
* 4-cycle count;
* 5-cycle count.

Spearman Mantel tests evaluate whether graphs that differ more strongly in a cycle statistic also lie farther apart in QuIC space.

The analysis then removes the dominant structural variables sequentially:

$$
\text{all graphs}
\rightarrow
\text{fixed triangle count}
\rightarrow
\text{fixed triangle and 4-cycle counts}.
$$

This stratified design distinguishes marginal association from residual organization. It does not merely observe that several correlated graph statistics are related to the embedding. It conditions out the stronger statistics and examines how the remaining geometry is organized.

#### Global results

##### (n=14)

| Structural quantity | Mantel (\rho) | Permutation (p) |
| ------------------- | ------------: | --------------: |
| Triangle count      |         0.903 |          0.0001 |
| 4-cycle count       |         0.290 |          0.0001 |
| 5-cycle count       |         0.109 |          0.0001 |
| Random control      |         0.005 |          0.3152 |

##### (n=16)

| Structural quantity | Mantel (\rho) | Permutation (p) |
| ------------------- | ------------: | --------------: |
| Triangle count      |         0.900 |          0.0001 |
| 4-cycle count       |         0.303 |          0.0001 |
| 5-cycle count       |         0.079 |          0.0001 |
| Random control      |      (-0.007) |          0.9720 |

The global geometry is dominated by triangle count at both graph orders:

$$
\rho_{\triangle}
=

0.903
\quad\text{and}\quad
0.900.
$$

The replication is unusually close. Increasing the census from 509 to 4,060 graphs changes the global triangle correlation by only (0.003).

The 4-cycle association is weaker globally but also stable:

$$
0.290
\rightarrow
0.303.
$$

The global 5-cycle association remains positive and statistically detectable but is small:

$$
0.109
\quad\text{at }n=14,
$$

and

$$
0.079
\quad\text{at }n=16.
$$

These smaller marginal values should not be interpreted as evidence that 4- and 5-cycle information is absent. Triangle differences dominate the pairwise distance ordering and mask the lower structural layers. The stratified analyses expose those layers directly.

The random-scalar controls remain near zero and nonsignificant. This argues against the observed Mantel relationships arising generically from the dependence structure of pairwise distance matrices.

#### Fixed-triangle strata

##### (n=14)

Five triangle-count strata contain at least 15 graphs. Together they include:

$$
490\text{ of }509
$$

graphs, or approximately:

$$
96.3%
$$

of the complete census.

| Triangle stratum | (n) | C4 (\rho) | C5 (\rho) | Effective rank |
| ---------------- | --: | --------: | --------: | -------------: |
| 0 triangles      | 110 |     0.968 |     0.320 |           2.90 |
| 1 triangle       | 122 |     0.954 |     0.179 |           2.88 |
| 2 triangles      | 139 |     0.926 |     0.200 |           3.06 |
| 3 triangles      |  74 |     0.906 |     0.175 |           2.87 |
| 4 triangles      |  45 |     0.898 |     0.203 |           2.79 |

##### (n=16)

Seven triangle-count strata contain at least 15 graphs. Together they include:

$$
4{,}054\text{ of }4{,}060
$$

graphs, or approximately:

$$
99.85%.
$$

| Triangle stratum |   (n) | C4 (\rho) | C5 (\rho) | Effective rank |
| ---------------- | ----: | --------: | --------: | -------------: |
| 0 triangles      |   792 |     0.964 |     0.238 |           2.99 |
| 1 triangle       | 1,098 |     0.956 |     0.163 |           2.91 |
| 2 triangles      | 1,094 |     0.928 |     0.139 |           3.06 |
| 3 triangles      |   613 |     0.907 |     0.133 |           3.04 |
| 4 triangles      |   319 |     0.900 |     0.169 |           3.01 |
| 5 triangles      |   101 |     0.883 |     0.312 |           3.05 |
| 6 triangles      |    37 |     0.853 |     0.503 |           3.04 |

Once triangle count is fixed, 4-cycle differences almost completely organize pairwise QuIC distances.

At (n=14),

$$
\rho_{\mathrm{C4}}
\in
$$0.898,0.968$$.
$$

At (n=16),

$$
\rho_{\mathrm{C4}}
\in
$$0.853,0.964$$.
$$

The slight decline in the smallest high-triangle strata does not change the central result. Every sufficiently populated triangle stratum at both graph orders shows a very strong positive association between 4-cycle-count difference and embedding distance.

The result is not driven by one dominant triangle class. It persists across:

* triangle-free graphs;
* low-triangle graphs;
* and the rarer high-triangle strata.

The direct replication across seven (n=16) strata substantially strengthens the interpretation that 4-cycle count forms the second structural layer of QuIC geometry.

#### Principal-component alignment within fixed-triangle strata

The principal-component analysis asks whether 4-cycle count merely correlates with pairwise distances or directly defines the leading within-stratum direction.

##### (n=14)

In the four largest triangle strata:

* PC1 explains approximately (53%)–(56%) of the variance;
* its Spearman correlation with 4-cycle count lies between
  $$
  -0.978
  \quad\text{and}\quad
  -0.988.
  $$

##### (n=16)

| Triangle stratum | PC1 variance | PC1–C4 Spearman (\rho) |
| ---------------- | -----------: | ---------------------: |
| 0 triangles      |        0.541 |               (-0.985) |
| 1 triangle       |        0.547 |               (-0.980) |
| 2 triangles      |        0.536 |               (-0.978) |
| 3 triangles      |        0.541 |               (-0.981) |

The PCA result replicates almost exactly.

Across the four largest (n=16) strata, PC1 explains:

$$
53.6%\text{--}54.7%
$$

of the within-stratum variance and correlates with 4-cycle count at:

$$
|\rho|
=

0.978\text{--}0.985.
$$

The sign is arbitrary because PCA eigenvectors may be reversed. In magnitude, PC1 is effectively a 4-cycle axis.

This is stronger than a generic statistical association. After triangle count is fixed, the leading geometric direction in QuIC space is almost a monotone coordinate for 4-cycle count.

The effective-rank results are equally stable. Across both censuses, the fixed-triangle strata have effective ranks near:

$$
3.
$$

Although the raw vectors contain tens of thousands of coordinates, most within-stratum variation occupies only a few effective dimensions.

This does not prove that the embedding is determined by exactly three cycle statistics. It shows that the observed geometry is highly constrained and substantially lower-dimensional than its ambient representation.

#### Fixed-triangle and fixed-4-cycle strata

The second stratification fixes both triangle and 4-cycle counts and tests whether 5-cycle differences organize the remaining geometry.

##### (n=14)

Sixteen joint strata contain at least 12 graphs.

Across these strata:

$$
\rho_{\mathrm{C5}}
\in
$$0.316,0.926$$.
$$

All reported associations are positive.

Several strata show particularly strong relationships:

| ((C_3,C_4)) | (n) | C5 (\rho) |
| ----------- | --: | --------: |
| ((0,1))     |   — |     0.926 |
| ((1,2))     |   — |     0.893 |
| ((0,2))     |   — |     0.871 |
| ((1,1))     |   — |     0.870 |
| ((2,1))     |   — |     0.836 |

The sixteen strata contain:

$$
340
$$

graphs, or approximately:

$$
66.8%
$$

of the complete (n=14) census.

##### (n=16)

Forty-three joint strata contain at least 12 graphs.

Together they include:

$$
3{,}944\text{ of }4{,}060
$$

graphs, or approximately:

$$
97.1%.
$$

Across all 43 strata:

$$
\rho_{\mathrm{C5}}
\in
$$0.193,0.974$$.
$$

Every association is positive, and 42 of the 43 strata have permutation:

$$
p<0.05.
$$

The only nonsignificant stratum is the smallest and weakest reported case:

$$
(C_3,C_4)=(5,5),
\qquad
n=12,
\qquad
\rho=0.193,
\qquad
p=0.1463.
$$

Representative strong strata include:

| ((C_3,C_4)) | (n) | C5 (\rho) |
| ----------- | --: | --------: |
| ((0,0))     |  49 |     0.974 |
| ((1,0))     |  64 |     0.964 |
| ((3,0))     |  51 |     0.958 |
| ((2,0))     |  80 |     0.955 |
| ((0,1))     | 107 |     0.950 |
| ((4,0))     |  23 |     0.950 |
| ((0,2))     | 184 |     0.912 |
| ((1,1))     | 199 |     0.888 |
| ((1,2))     | 301 |     0.843 |
| ((0,3))     | 170 |     0.805 |

The (n=16) result resolves the weak global C5 correlation decisively.

Globally,

$$
\rho_{\mathrm{C5}}=0.079.
$$

After triangles and 4-cycles are fixed, 5-cycle-count difference becomes a strong residual organizing variable across a broad range of joint strata.

The effect is especially pronounced in strata with few or no 4-cycles. As the fixed 4-cycle count increases, the C5 correlation often becomes weaker, although it generally remains positive. This suggests that the residual geometry becomes more structurally heterogeneous in higher-cycle-density regions rather than following one uniform C5 axis.

#### Replicated structural hierarchy

The combined (n=14) and (n=16) results support the hierarchy:

$$
\boxed{
\text{triangles}
\rightarrow
\text{4-cycles}
\rightarrow
\text{5-cycles}
}
$$

The hierarchy appears in three distinct forms:

1. **Marginal dominance**
   Triangle count has the strongest global association with embedding distance.

2. **Conditional dominance**
   Once triangles are fixed, 4-cycle count becomes the dominant within-stratum variable.

3. **Residual organization**
   Once both triangles and 4-cycles are fixed, 5-cycle count organizes the remaining geometry.

The structure is therefore closer to a lexicographic or onion-like organization than to an undifferentiated mixture of motif statistics.

Shorter-cycle variation controls the largest geometric scale. Longer-cycle information remains present but becomes visible only after the dominant shorter-cycle layers are conditioned out.

The near-identical global, PCA, effective-rank, and stratified results across the two exhaustive censuses indicate that this is not an (n=14) artifact.

#### Relationship to the later decoding experiments

The Mantel analyses establish metric organization rather than direct prediction. The later E2 ridge-probe experiment supplies the missing decodability result.

Using the complete QuIC vectors, linear probes obtain:

| Target    | (n=14) (R^2) | (n=16) (R^2) |
| --------- | -----------: | -----------: |
| Triangles |        1.000 |        1.000 |
| 4-cycles  |        0.998 |        1.000 |
| 5-cycles  |        0.928 |        0.982 |

The E1 hierarchy is therefore not merely geometric. The same structural quantities can be recovered from held-out embeddings with high predictive accuracy.

E1 and E2 answer complementary questions:

* E1 shows how graph space is organized;
* E2 shows that the corresponding statistics are decodable.

#### What the experiment establishes

The combined results provide strong evidence that the QuIC embedding is not merely injective or collision-free. Its metric geometry is systematically organized by classical graph structure.

More specifically, the experiment establishes that:

1. **The sorted probability vector retains substantial local-cycle information despite discarding bitstring identities.**

2. **The representation distinguishes topology beyond graph order and degree sequence.**

3. **Short-cycle statistics appear in a replicated hierarchy rather than as an undifferentiated collection of correlated features.**

4. **Weak marginal correlations can conceal strong conditional structure.**

5. **Four-cycle count closely aligns with the dominant within-triangle-stratum principal direction.**

6. **Five-cycle count organizes residual geometry after both stronger cycle statistics are fixed.**

7. **The within-stratum geometry has effective rank near three despite ambient dimensions of (16{,}384) and (65{,}536).**

8. **The hierarchy persists across both complete connected cubic-graph censuses.**

The (n=16) replication changes the status of the result. The hierarchy is no longer an observation restricted to one small graph order. It is a stable property across two exhaustive censuses differing eightfold in sample size and fourfold in representation dimension.

#### Necessary qualifications

The Mantel tests establish metric organization, not causation or unique coordinate recovery. The later ridge probes demonstrate decodability, but E1 alone does not show that cycle counts uniquely determine the embedding.

The permutation (p)-values have resolution:

$$
\frac{1}{10{,}000+1}.
$$

Values printed as (0.0001) are therefore at the Monte Carlo floor. Fisher combinations such as:

$$
10^{-20}
\quad\text{or}\quad
10^{-101}
$$

should not be interpreted as numerically precise tail probabilities. They indicate overwhelming aggregate evidence under the tested permutation scheme, but their exact exponents are artifacts of replacing unresolved smaller values with the Monte Carlo floor.

The tests are one-sided. This is appropriate for the prespecified hypothesis that larger cycle-count differences should correspond to larger embedding distances, but the directionality should be stated explicitly.

The same random seed is reused across the stratum-level permutation tests. This does not explain the consistently large effect sizes, but independent random streams would be cleaner if Fisher-combined (p)-values are reported.

The pairwise observations within a Mantel test are not independent. The permutation procedure addresses this dependence for each test, but raw pair counts should not be interpreted as the effective sample size.

The joint-stratum threshold is:

$$
n\ge12.
$$

The weakest (n=16) result occurs in a stratum of exactly 12 graphs. Small-stratum estimates should be treated as less stable than the large-stratum results.

The study still concerns one graph family, one circuit depth, and one canonical parameter setting. Replication from (n=14) to (n=16) establishes cross-order stability within connected cubic graphs. It does not establish the same hierarchy across arbitrary degree sequences, angles, or circuit repetitions.

The nonregular E6 experiment shows that the flat-start hierarchy does not automatically transfer outside regular graph families. The degree-encoded E6 run is required to determine whether explicit degree information restores that structure.

Finally, the embedded (n=16) dataset README is stale and incorrectly describes the (n=14), 509-graph dataset. The loaded arrays and stratum counts correspond to the 4,060-graph (n=16) census, but the metadata should be corrected before release.

#### Overall assessment

E1 now provides a strong replicated characterization of QuIC geometry.

At both (n=14) and (n=16):

* triangle count dominates global embedding distances;
* 4-cycle count becomes the leading geometric axis after conditioning on triangles;
* 5-cycle count organizes the residual geometry after conditioning on both triangles and 4-cycles;
* the effective within-stratum dimension remains near three.

The (n=16) results are particularly strong because the second-layer analysis covers approximately:

$$
97.1%
$$

of the complete census and finds positive C5 organization in all 43 sufficiently large joint strata.

The appropriate central claim is:

> Across the exhaustive connected cubic-graph censuses at (n=14) and (n=16), QuIC organizes graph space hierarchically by short-cycle structure. Triangle count dominates globally, 4-cycle count defines the leading direction after conditioning on triangles, and 5-cycle count organizes the remaining geometry after conditioning on both. The hierarchy is stable across graph orders and occupies only a few effective dimensions despite the exponentially large ambient representation.


### E2 Ridge Probe
#### Experimental design

This notebook evaluates the structural information contained in the exact QuIC probability vector for the complete connected cubic-graph censuses at two graph orders:

* **509 graphs at (n=14)**;
* **4,060 graphs at (n=16)**.

Each graph is represented by its full sorted probability vector generated using the fixed canonical angles and one circuit repetition:

$$
\mathbf p(G)\in\mathbb R^{2^n}.
$$

The resulting feature dimensions are:

$$
2^{14}=16{,}384,
\qquad
2^{16}=65{,}536.
$$

The notebook contains four related analyses:

1. linear decoding of graph invariants from the full QuIC vector;
2. compression through low-order power sums of the QuIC probabilities;
3. decomposition of QuIC geometry into adjacency-spectral and residual components;
4. direct separation of adjacency-cospectral graphs.

All supervised probes use five frozen shuffled folds. The full-vector models use ridge regression with inner cross-validation over the regularization parameter.

Two kinds of moments appear in the notebook and should be distinguished:

* **QuIC probability moments**
  $$
  \sum_z p_z^k,
  $$
  used to test whether a few scalar summaries reproduce the information in the full probability vector;

* **adjacency spectral moments**
  $$
  	ext{tr}(A^k),
  $$
  used to determine how much of QuIC geometry is explained by the classical adjacency spectrum.

#### Full-vector decodability

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

$$
R^2=0.928
$$

at (n=14) to

$$
R^2=0.982
$$

at (n=16). The fold variance also decreases substantially, indicating that the weaker (n=14) result was partly a finite-census or split-composition effect.

Girth is nearly perfectly decoded at both graph orders. This is consistent with the strong short-cycle representation: within these cubic censuses, girth is largely determined by the presence or absence of short cycles.

Six-cycle count is substantially weaker. Performance nevertheless improves from

$$
R^2=0.485\pm0.326
$$

to

$$
R^2=0.642\pm0.122.
$$

The larger census therefore confirms that 6-cycle information is present, but less directly organized than the shorter-cycle information.

Diameter also improves considerably with scale:

$$
0.548\rightarrow0.737.
$$

This suggests that the full probability vector contains meaningful global metric information, although diameter remains much less accessible than local cycle structure.

The spectral-gap result remains high but does not improve with graph order. QuIC therefore contains substantial adjacency-spectral information, but it does not reproduce the relevant eigenvalue coordinate exactly under a linear probe.

#### Scaling from (n=14) to (n=16)

The (n=16) census largely strengthens the (n=14) conclusions.

* Triangle and 4-cycle prediction remain effectively exact.
* Five-cycle prediction becomes stronger and substantially more stable.
* Six-cycle prediction improves while remaining the weakest cycle target.
* Diameter prediction rises by approximately (0.19).
* Girth remains almost perfectly accessible.
* Spectral-gap prediction remains near (0.93).

This is important because the (n=14) full-vector feature dimension greatly exceeds the number of graphs. Replication on 4,060 graphs does not remove the high-dimensional setting, but it shows that the central effects are not peculiar to the 509-graph census or a single favorable set of folds.

The hierarchy suggested by the decoding results is

$$
C_3,\ C_4
;\rightarrow;
C_5
;\rightarrow;
C_6,
$$

with progressively weaker and less stable linear accessibility as cycle length increases.

#### QuIC probability power sums

The next experiment tests whether the full-vector results can be reduced to a small number of global probability moments.

Using only

$$
\sum_z p_z^2,\qquad
\sum_z p_z^3,\qquad
\sum_z p_z^4,
$$

the probe obtains:

| Target    |          (n=14) |          (n=16) |
| --------- | --------------: | --------------: |
| Triangles | (1.000\pm0.000) | (1.000\pm0.000) |
| 4-cycles  | (0.754\pm0.043) | (0.750\pm0.022) |
| 5-cycles  | (0.064\pm0.066) | (0.056\pm0.008) |

Triangle count is therefore almost entirely encoded by the lowest probability moments. Four-cycle count is partially recoverable from the first three power sums, while 5-cycle count is almost completely absent from this compressed representation.

The nested power-sum ladder sharpens the result.

##### (n=14) power-sum ladder

| Moments included | Triangles | 4-cycles | 5-cycles | 6-cycles |
| ---------------- | --------: | -------: | -------: | -------: |
| Through (k=2)    |     0.999 |    0.001 |    0.022 |    0.144 |
| Through (k=3)    |     1.000 |    0.677 |    0.066 |    0.184 |
| Through (k=4)    |     1.000 |    0.755 |    0.069 |    0.182 |
| Through (k=5)    |     1.000 |    0.997 |    0.045 |    0.189 |
| Through (k=8)    |     1.000 |    0.997 |    0.106 |    0.198 |

##### (n=16) power-sum ladder

| Moments included | Triangles | 4-cycles | 5-cycles | 6-cycles |
| ---------------- | --------: | -------: | -------: | -------: |
| Through (k=2)    |     0.999 |    0.003 |    0.024 |    0.100 |
| Through (k=3)    |     1.000 |    0.691 |    0.056 |    0.142 |
| Through (k=4)    |     1.000 |    0.752 |    0.058 |    0.143 |
| Through (k=5)    |     1.000 |    0.998 |    0.060 |    0.146 |
| Through (k=8)    |     1.000 |    0.998 |    0.084 |    0.144 |

The same transition occurs at both graph orders:

$$
\text{4-cycle information saturates when }
\sum_z p_z^5
\text{ is added}.
$$

This replication indicates that the (k=5) transition is structural rather than an (n=14) anomaly.

In contrast, neither 5-cycle nor 6-cycle count is recovered by probability power sums through degree eight. Their best ladder scores remain near (0.10) and (0.20), far below the corresponding full-vector scores.

The complete sorted probability vector therefore contains information that is discarded by low-order global moments.

#### Quadratic interaction check for 5-cycles

A degree-two polynomial model was applied to the first four probability power sums:

$$
\sum_z p_z^2,\ldots,\sum_z p_z^5.
$$

The resulting 5-cycle scores are:

$$
R^2=0.143\pm0.103
\quad\text{at }n=14,
$$

and

$$
R^2=0.132\pm0.015
\quad\text{at }n=16.
$$

The strong full-vector 5-cycle result is therefore not explained by a simple quadratic interaction among the low-order moments.

The correct conclusion is not that 5-cycle information is absent from all symmetric functions of the probability vector. A sufficiently rich collection of moments can recover a finite probability multiset. The result is narrower:

> Five-cycle information is carried by finer probability-spectrum structure that is not captured by moments through degree eight or by quadratic interactions among the first four moments.

#### Principal-component decomposition

The notebook next decomposes the centered QuIC vectors using singular-value decomposition and asks how well the leading principal components can be reconstructed from:

* triangle, 4-cycle, and 5-cycle counts;
* adjacency moments (	ext{tr}(A^k)), (k=3,\ldots,8);
* the complete nonconstant adjacency spectrum;
* adjacency moments concatenated with the three cycle counts.

##### (n=14)

| Component | Variance | Cycle (R^2) | Moment (R^2) | Full-spectrum (R^2) |
| --------- | -------: | ----------: | -----------: | ------------------: |
| PC1       |    51.2% |       0.962 |        0.962 |               0.954 |
| PC2       |    15.3% |      -0.002 |        0.060 |               0.195 |
| PC3       |     7.8% |       0.128 |        0.119 |               0.097 |
| PC4       |     7.7% |       0.802 |        0.811 |               0.809 |
| PC5       |     5.3% |      -0.014 |       -0.017 |               0.010 |
| PC6       |     2.6% |      -0.033 |       -0.040 |              -0.065 |

##### (n=16)

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

$$
59%
$$

of the total embedding variance.

PC2 behaves differently. It contains approximately (15%) of the total variance but is poorly explained by short-cycle counts or the first six adjacency moments:

$$
R^2_{\mathrm{moments}}=0.060
\quad\text{at }n=14,
$$

and

$$
R^2_{\mathrm{moments}}=0.052
\quad\text{at }n=16.
$$

The full adjacency spectrum explains more:

$$
R^2_{\mathrm{spectrum}}=0.195
\quad\text{and}\quad
0.275,
$$

but most of PC2 remains unexplained.

PC3, PC5, and PC6 are also weakly related to the tested spectral and cycle features. These components are individually smaller, but together with PC2 they show that the QuIC representation is not exhausted by its dominant spectral axis.

A variance-weighted aggregation across the first six components attributes approximately:

* (57%) of total QuIC variance to the six adjacency moments at both graph orders;
* (59%) at (n=14) and (60%) at (n=16) to the complete adjacency spectrum.

The representation therefore has a large and stable spectral backbone, but a substantial residual component remains.

#### Six-cycle contribution to PC2

Six-cycle count alone does not predict PC2:

$$
R^2=-0.028
\quad\text{at }n=14,
$$

and

$$
R^2=-0.003
\quad\text{at }n=16.
$$

After the adjacency moments are included, however, adding 6-cycle count raises the PC2 score from

$$
0.060\rightarrow0.210
$$

at (n=14), and from

$$
0.052\rightarrow0.158
$$

at (n=16).

Thus, the useful 6-cycle signal is conditional rather than marginal. Six-cycle count becomes informative only after the dominant spectral component has been accounted for.

This is consistent with the later residual-probe result: the spectrum strongly constrains 6-cycle count, while QuIC retains information about the remaining non-spectral division between 6-cycles and diamonds.

The PC2 result should nevertheless be treated as suggestive rather than definitive. Most of PC2 remains unexplained even after 6-cycle count is included.

#### Adjacency-cospectral graphs

The strongest direct test asks whether QuIC distinguishes graphs having exactly the same adjacency spectrum.

Spectrum hashing identifies:

* **3 cospectral groups and 3 pairs at (n=14)**;
* **41 cospectral groups and 43 pairs at (n=16)**.

The (n=14) analysis recovers the three expected pairs:

$$
(79,458),\qquad
(201,203),\qquad
(234,239).
$$

Every discovered cospectral pair has a nonzero QuIC separation.

At (n=14), the full-vector (L_1) distances range from

$$
5.87\times10^{-8}
$$

to

$$
1.69\times10^{-5}.
$$

At (n=16), the distances range from

$$
1.92\times10^{-8}
$$

to

$$
1.68\times10^{-5}.
$$

Because adjacency-cospectral graphs have identical classical spectra, these separations demonstrate that the ideal QuIC probability vector is not a function of the adjacency spectrum alone.

This is the notebook's cleanest direct evidence for a non-spectral component.

#### Why the global percentiles are small

Relative to all graph pairs, the cospectral separations occupy low percentiles.

At (n=14), the three global percentiles are approximately:

$$
0.00077,\qquad
0.0611,\qquad
5.817.
$$

At (n=16), the global percentiles range from approximately zero to

$$
6.324.
$$

This does not contradict the existence of non-spectral information. Arbitrary graph pairs differ along the dominant triangle, 4-cycle, and adjacency-spectral axes. Cospectral pairs have all of those major differences removed and therefore occupy a much smaller distance scale.

The global pairwise distribution is consequently not the most informative reference class for cospectral mates.

#### Count-identical reference class

A more appropriate comparison restricts the reference population to graph pairs with identical

$$
(C_3,C_4,C_5)
$$

counts.

This produces:

* **715 count-identical pairs at (n=14)**;
* **52,181 count-identical pairs at (n=16)**.

For the full (n=14) vectors, the three cospectral pairs lie at approximately the:

$$
0.0\text{th},\qquad
10.9\text{th},\qquad
92.7\text{th}
$$

percentiles of this count-identical reference class.

Thus, one cospectral pair is among the most strongly separated count-identical pairs, one is modestly separated, and one is extremely close.

At (n=16), the 43 full-vector percentiles range from approximately

$$
0
$$

to

$$
92.0,
$$

with median approximately

$$
11.7.
$$

Of the 43 pairs:

* 19 lie at or above the 25th percentile;
* 4 lie near or above the 90th percentile;
* 20 lie below the 5th percentile.

The non-spectral separation is therefore heterogeneous. QuIC distinguishes all discovered cospectral pairs in exact simulation, but many differences are small, while a minority are large even relative to graphs already matched on the first three cycle counts.

This distinction matters:

* **nonzero separation** establishes that QuIC is not spectrally determined;
* **high reference-class percentile** establishes that the non-spectral difference is geometrically substantial.

The notebook provides both, but not for every pair.

#### Truncation behavior

The truncation experiment evaluates only the largest (k) entries of the sorted probability vector.

At (n=14), reducing the representation to its first 25–100 probabilities increases the relative standing of two of the three cospectral pairs. For example, pair ((201,203)) rises from approximately the 5.82nd global percentile using the full vector to:

$$
18.30
$$

at (k=50).

At (n=16), the four most strongly separated full-vector pairs lie near the 92nd percentile of the count-identical class. These same pairs remain near the 93rd percentile at (k=100).

Relative to all graph pairs, their percentiles rise from approximately

$$
6.2\text{--}6.3
$$

for the full vector to approximately

$$
20.5
$$

at (k=50).

This indicates that the strongest cospectral residue is concentrated disproportionately in the head of the sorted probability distribution. The effect is not uniform across all pairs, but the largest non-spectral separations do not require the full (2^n)-dimensional tail.

#### What the experiment establishes

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

$$
\boxed{
\text{a dominant spectral backbone}
+
\text{a smaller non-spectral residue}
}
$$

#### Necessary qualifications

The ridge results demonstrate linear decodability, not that the corresponding graph invariant is uniquely represented along a single embedding direction.

The full vectors are extremely high-dimensional relative to the graph censuses. Five-fold testing and replication at (n=16) reduce the risk of a purely in-sample artifact, but the near-floor selected regularization parameters indicate a near-interpolating regime.

The experiments use exact noiseless probability vectors at one fixed circuit depth and one canonical angle configuration. Very small cospectral distances may not remain resolvable under finite-shot sampling or hardware noise.

Cospectral groups are identified by adjacency eigenvalues rounded to eight decimal places. The known (n=14) pairs provide a regression check, but a formal exact-cospectrality claim should ultimately be verified using characteristic polynomials or exact algebraic invariants.

The probability-moment experiment only tests powers through (k=8) and one degree-two interaction model. It establishes failure of low-order compression, not failure of all possible symmetric summaries.

The PCA analysis is descriptive. The principal axes are fitted to each complete census before the spectral probes are evaluated, so the reported component decomposition should be interpreted as an analysis of the observed geometry rather than as an independently fitted out-of-sample representation.

Finally, ideal-state separation of cospectral graphs establishes non-spectral information but does not by itself establish that the information is useful for a downstream task. The residual-probe experiment supplies the stronger functional result for diamond and 6-cycle prediction.

#### Overall assessment

The (n=16) replication materially strengthens the earlier (n=14) findings.

The full QuIC vector preserves an exceptionally strong hierarchy of local graph structure. Triangle and 4-cycle counts are essentially exact, 5-cycle prediction becomes more stable at the larger graph order, and weaker 6-cycle and diameter signals improve with census size.

The representation is not reducible to a handful of probability moments. Its leading geometry is nevertheless substantially classical: approximately (59%) of total variance lies in two principal directions that are strongly explained by adjacency spectral quantities.

Beyond that backbone, QuIC retains additional structure. The weakly spectral PC2 replicates at both graph orders, conditional 6-cycle information appears within it, and all 46 discovered cospectral pairs across the two censuses receive distinct ideal QuIC vectors.

The appropriate central claim is:

> Across the complete connected cubic-graph censuses at (n=14) and (n=16), QuIC exhibits a stable spectral backbone together with a reproducible non-spectral residue. Its dominant components encode short-cycle and adjacency-spectral structure, while finer probability-spectrum information supports strong 5-cycle decoding, conditional 6-cycle information, and separation of every discovered adjacency-cospectral pair.


### E2S - Spectral Baseline
#### Experimental design

This notebook asks whether QuIC predicts graph properties that are not already recoverable from the adjacency spectrum.

The experiment uses the complete connected cubic-graph censuses at two orders:

- **509 graphs at $n=14$**
- **4,060 graphs at $n=16$**

Four feature representations are compared using the same five frozen train/test folds and the same ridge-regression protocol:

1. **QuIC:** the full sorted probability vector from the original E2 experiment.
2. **Eigenvalues:** the sorted adjacency eigenvalues, excluding the constant Perron eigenvalue $\lambda_{\max}=3$.
3. **Spectral moments:**  
   $$
   	ext{tr}(A^k), \qquad k=3,\ldots,8.
   $$
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

$$
\Delta R^2
=
R^2_{\text{QuIC+spec}}
-
\max\left(
R^2_{\text{eigenvalues}},
R^2_{\text{moments}}
\right).
$$

A positive value indicates that the combined representation predicts better than either linear spectral representation alone.

#### Spectral identity checks

For cubic graphs, the first three cycle-count targets are exact linear functions of adjacency moments:

$$
C_3=\frac{	ext{tr}(A^3)}{6},
$$

$$
C_4=\frac{	ext{tr}(A^4)-15n}{8},
$$

and

$$
C_5=
\frac{
	ext{tr}(A^5)-10	ext{tr}(A^3)
}{10}.
$$

The notebook verifies these identities exactly across all 509 graphs at $n=14$ and all 4,060 graphs at $n=16$.

These checks serve two purposes:

- They confirm that the graph statistics and spectra were computed consistently.
- They provide positive controls for the linear-probe protocol.

As expected, the moment representation obtains $R^2=1.000$ for triangle, 4-cycle, and 5-cycle counts at both graph orders.

#### Main results

The reported values are mean $R^2$ with standard deviation across the five frozen folds.

##### $n=14$

| Target | QuIC | Eigenvalues | Moments | QuIC + spectrum | $\Delta R^2$ |
|---|---:|---:|---:|---:|---:|
| Triangles | $1.000\pm0.000$ | $0.987\pm0.004$ | $1.000\pm0.000$ | $1.000\pm0.000$ | $-0.000$ |
| 4-cycles | $0.998\pm0.002$ | $0.972\pm0.004$ | $1.000\pm0.000$ | $1.000\pm0.000$ | $-0.000$ |
| 5-cycles | $0.928\pm0.092$ | $0.905\pm0.013$ | $1.000\pm0.000$ | $1.000\pm0.000$ | $-0.000$ |
| 6-cycles | $0.485\pm0.326$ | $0.842\pm0.059$ | $0.983\pm0.005$ | $1.000\pm0.000$ | $+0.017$ |
| Girth | $0.993\pm0.014$ | $0.611\pm0.100$ | $0.376\pm0.045$ | $0.993\pm0.014$ | $+0.382$ |
| Diameter | $0.548\pm0.058$ | $0.560\pm0.049$ | $0.711\pm0.012$ | $0.741\pm0.030$ | $+0.030$ |
| Spectral gap | $0.944\pm0.010$ | $1.000\pm0.000$ | $0.871\pm0.032$ | $1.000\pm0.000$ | $-0.000$ |

##### $n=16$

| Target | QuIC | Eigenvalues | Moments | QuIC + spectrum | $\Delta R^2$ |
|---|---:|---:|---:|---:|---:|
| Triangles | $1.000\pm0.000$ | $0.989\pm0.001$ | $1.000\pm0.000$ | $1.000\pm0.000$ | $-0.000$ |
| 4-cycles | $1.000\pm0.000$ | $0.974\pm0.002$ | $1.000\pm0.000$ | $1.000\pm0.000$ | $-0.000$ |
| 5-cycles | $0.982\pm0.015$ | $0.918\pm0.009$ | $1.000\pm0.000$ | $1.000\pm0.000$ | $-0.000$ |
| 6-cycles | $0.642\pm0.122$ | $0.857\pm0.009$ | $0.983\pm0.001$ | $1.000\pm0.000$ | $+0.017$ |
| Girth | $0.999\pm0.003$ | $0.543\pm0.042$ | $0.382\pm0.020$ | $0.999\pm0.003$ | $+0.456$ |
| Diameter | $0.737\pm0.019$ | $0.657\pm0.006$ | $0.775\pm0.016$ | $0.802\pm0.014$ | $+0.026$ |
| Spectral gap | $0.932\pm0.007$ | $1.000\pm0.000$ | $0.865\pm0.005$ | $1.000\pm0.000$ | $-0.000$ |

#### Eigenvalues versus spectral moments

The comparison between eigenvalues and moments illustrates that linear-probe performance depends strongly on the coordinates used to express the same spectral information.

The sorted eigenvalue representation performs well but not perfectly on short-cycle counts:

$$
R^2\approx0.91\text{--}0.99.
$$

This is expected because cycle counts are power sums of the eigenvalues. They are spectral functions, but they are not linear functions of the individual sorted eigenvalue coordinates.

In contrast, the moment representation contains those power sums directly and therefore recovers triangle, 4-cycle, and 5-cycle counts exactly.

The reverse occurs for the spectral gap. For a connected cubic graph,

$$
\lambda_{\max}=3,
\qquad
\text{gap}=3-\lambda_2.
$$

The spectral gap is therefore an exact linear function of a sorted eigenvalue coordinate. The eigenvalue probe obtains $R^2=1.000$, while the moment representation reaches only approximately $0.87$.

This establishes an important methodological point: poor performance from a linear model on sorted eigenvalues does not imply that a target is non-spectral. It may instead mean that the target is nonlinear in those particular spectral coordinates.

#### Short-cycle counts

The results for triangles, 4-cycles, and 5-cycles behave exactly as expected.

The moment representation recovers all three perfectly because the relevant identities are built into the feature coordinates. QuIC also performs strongly:

- exact or nearly exact prediction for triangles and 4-cycles,
- $R^2=0.928$ at $n=14$ and $0.982$ at $n=16$ for 5-cycles.

The lower and more variable $n=14$ 5-cycle result suggests that the finite census or fold composition makes this target less stable at the smaller graph order. The larger census produces substantially stronger and more consistent prediction.

The concatenated representation provides no improvement because the spectral moments already solve these targets exactly.

These rows therefore confirm that QuIC contains the same short-cycle structure identified in the stratified-distance experiment, but they do not identify information beyond the adjacency spectrum.

#### Six-cycle count

The 6-cycle row is the most striking interaction result.

QuIC alone predicts 6-cycle count relatively poorly:

$$
R^2=0.485\pm0.326
\quad\text{at }n=14,
$$

and

$$
R^2=0.642\pm0.122
\quad\text{at }n=16.
$$

The spectral moment representation is already very strong:

$$
R^2=0.983
$$

at both graph orders.

Nevertheless, concatenating QuIC with the spectral features raises the reported score to $1.000\pm0.000$, giving

$$
\Delta R^2=+0.017
$$

at both $n=14$ and $n=16$.

The replication of the same gain across two complete graph censuses is notable. It indicates that QuIC contains information or transformed structure that complements the linear spectral coordinates used by the baseline.

The result is better interpreted as **complementarity** than as strong standalone 6-cycle decoding. QuIC by itself is not a competitive 6-cycle predictor, particularly at $n=14$. Its contribution becomes useful only when combined with the spectral representation.

#### Girth

QuIC predicts girth almost perfectly:

$$
R^2=0.993\pm0.014
\quad\text{at }n=14,
$$

and

$$
R^2=0.999\pm0.003
\quad\text{at }n=16.
$$

The linear spectral baselines are much weaker. The best spectral score is only $0.611$ at $n=14$ and $0.543$ at $n=16$.

This produces the largest nominal improvements:

$$
\Delta R^2=+0.382
\quad\text{and}\quad
+0.456.
$$

However, these large values should not be interpreted as evidence that girth is non-spectral. Within these censuses, girth is determined by the presence or absence of short cycles and is therefore a nonlinear threshold function of spectrally determined cycle counts.

The girth result instead shows that QuIC provides a coordinate system in which this nonlinear spectral property is nearly linearly accessible. The concatenated model does not improve on QuIC; it simply retains QuIC's near-perfect score.

This is strong evidence for favorable representation geometry, but not for information absent from the spectrum.

#### Diameter

Diameter is the clearest open structural target.

At $n=14$:

$$
R^2_{\text{QuIC}}=0.548,
\qquad
R^2_{\text{moments}}=0.711,
\qquad
R^2_{\text{combined}}=0.741.
$$

At $n=16$:

$$
R^2_{\text{QuIC}}=0.737,
\qquad
R^2_{\text{moments}}=0.775,
\qquad
R^2_{\text{combined}}=0.802.
$$

The resulting improvements are modest but consistent:

$$
\Delta R^2=+0.030
\quad\text{at }n=14,
$$

and

$$
\Delta R^2=+0.026
\quad\text{at }n=16.
$$

Unlike girth, the combined representation outperforms both QuIC and the spectral baselines. The replication across graph orders supports the presence of complementary structural information.

The absolute gains are small, however, and no fold-level uncertainty or paired significance test is reported for $\Delta R^2$. The appropriate conclusion is that the combined representation provides a consistent predictive improvement, not that a large independent diameter signal has been established.

#### Spectral gap

The spectral-gap row acts as another positive control.

The sorted-eigenvalue representation obtains perfect prediction because the target is explicitly a linear function of the two largest adjacency eigenvalues. QuIC reaches approximately $R^2=0.93\text{--}0.94$, demonstrating that it captures substantial spectral information but does not reproduce the relevant eigenvalue coordinate exactly under a linear probe.

The concatenated model returns to perfect prediction because the exact spectral feature is present. There is no improvement beyond the spectral baseline.

This result argues against treating QuIC as a simple replacement for the adjacency spectrum. Its representation emphasizes some structural quantities while making other explicitly spectral quantities less directly accessible.

#### What the experiment establishes

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
   The same qualitative pattern appears in both the $n=14$ and $n=16$ complete censuses.

The experiment therefore strengthens the interpretation of QuIC as a structurally organized representation rather than merely an injective graph identifier.

#### Necessary qualifications

The central limitation is that positive

$$
\Delta R^2
$$

does not, by itself, prove that QuIC contains non-spectral information.

The spectral baselines are linear models on two specific coordinate systems. QuIC may provide nonlinear transformations of information that is already determined by the spectrum. The girth result demonstrates this directly: QuIC dramatically outperforms the linear spectral baselines even though girth is spectrally determined within these graph censuses.

Consequently, the 6-cycle and diameter improvements establish that QuIC adds information useful beyond these **linear spectral probes**, but not necessarily information absent from the full adjacency spectrum.

A stronger non-spectral claim would require at least one of the following:

- analysis restricted to adjacency-cospectral graph classes,
- examples of cospectral graphs with different target values that QuIC separates,
- prediction of target residuals after a sufficiently expressive nonlinear spectral model,
- or a direct conditional test showing that QuIC varies meaningfully when the complete spectrum is fixed.

The notebook also reports no paired uncertainty estimate for the differences in $R^2$. Because every method uses the same frozen folds, the foldwise score differences could be analyzed directly. This would clarify whether the $+0.017$, $+0.030$, and $+0.026$ gains are stable across folds rather than driven by one split.

The concatenated model also has far higher dimensionality than either spectral baseline, especially at $n=16$. The comparison is valid as a predictive test, but the improvement may reflect both additional information and a richer transformed feature basis.

Finally, scores printed as $1.000\pm0.000$ are exact only to the displayed precision unless separately guaranteed by an algebraic identity. Exact recoverability is established for $C_3$, $C_4$, and $C_5$; the reported combined 6-cycle result should be described as numerically perfect or perfect to displayed precision.

#### Overall assessment

This notebook provides a useful classical baseline and materially sharpens the interpretation of the QuIC probe results.

The spectral controls behave correctly:

- moments exactly recover $C_3$, $C_4$, and $C_5$;
- sorted eigenvalues exactly recover spectral gap;
- the difference between eigenvalue and moment probes exposes the importance of feature coordinates.

Against these controls, QuIC shows two distinct behaviors.

First, it makes some nonlinear structural properties, particularly girth, almost linearly accessible. Second, it provides small but repeatable improvements when combined with spectral features for 6-cycle count and diameter.

The appropriate central claim is:

> Across the complete connected cubic-graph censuses at $n=14$ and $n=16$, QuIC is neither reducible to nor uniformly stronger than a linear adjacency-spectral representation. It provides a different structural coordinate system: one that makes girth highly accessible and adds reproducible predictive value to spectral features for 6-cycle count and diameter.

The notebook supports complementarity beyond linear spectral baselines. A claim of genuinely non-spectral information requires the planned cospectral or conditional-residual analysis.


### E2R - Residual Probe (Partial Results)

#### Experimental design

This experiment tests whether QuIC contains functionally useful information beyond a linear adjacency-spectral representation.

The spectral representation contains:

* the sorted adjacency eigenvalues, excluding the constant cubic-graph eigenvalue (\lambda_{\max}=3);
* the spectral moments
  $$
  	ext{tr}(A^k), \qquad k=3,\ldots,8.
  $$

Each target is evaluated using the same five frozen outer folds used in the earlier ridge-probe experiment. Within each outer fold, prediction proceeds in two stages:

1. A standardized spectral ridge model is fitted on the training fold.
2. Cross-fitted spectral predictions are generated for the training points using five inner folds.
3. The difference between each observed target and its cross-fitted spectral prediction becomes the residual target.
4. A second ridge model learns those residuals from the raw QuIC probability vectors.
5. The final prediction is
   $$
   \hat y_{\mathrm{two-stage}}
   ===========================

   \hat y_{\mathrm{spectrum}}
   +
   \hat r_{\mathrm{QuIC}}.
   $$

The primary statistic is

$$
\Delta R^2 = R^2_{\mathrm{two-stage}} - R^2_{\mathrm{spectrum}}.
$$

A positive value indicates that QuIC predicts variation missed by the linear spectral model.

The experiment also reports residual-space (R^2):

$$
R^2_{\mathrm{residual}}
=

R^2
\left(
y-\hat y_{\mathrm{spectrum}},
\hat r_{\mathrm{QuIC}}
\right).
$$

This measures QuIC's ability to predict the spectral model's remaining error directly.

#### Available results

The (n=14) run completed all eleven targets. The (n=16) run completed through the diamonds target before the notebook timed out.

#### Complete (n=14) results

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

#### Partial (n=16) results

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

#### Protocol checks

Triangles, 4-cycles, 5-cycles, and spectral gap behave as expected.

The spectral representation predicts each of these targets perfectly:

$$
R^2_{\mathrm{spectrum}}=1.000.
$$

Adding a QuIC residual model therefore produces no improvement:

$$
\Delta R^2=0.
$$

The negative residual-space values on these rows are not evidence that QuIC systematically loses structural information. The spectral model has already reduced the residual target to approximately numerical or regularization noise. When the residual variance is nearly zero, residual-space (R^2) becomes unstable and can take strongly negative values, as seen for the (n=16) spectral-gap row.

These rows confirm that the cross-fitting and two-stage machinery do not manufacture an improvement when the spectral stage already solves the target.

#### Diamond count

Diamond count provides the strongest result.

At (n=14),

$$
R^2_{\mathrm{spectrum}}=0.585\pm0.032,
$$

while the two-stage model reaches

$$
R^2_{\mathrm{two-stage}}=0.927\pm0.090.
$$

This gives

$$
\Delta R^2=+0.341
$$

and

$$
R^2_{\mathrm{residual}}=0.827.
$$

The same result appears at (n=16):

$$
R^2_{\mathrm{spectrum}}=0.636\pm0.032,
$$

$$
R^2_{\mathrm{two-stage}}=0.947\pm0.009,
$$

$$
\Delta R^2=+0.310,
$$

and

$$
R^2_{\mathrm{residual}}=0.854.
$$

QuIC alone also predicts diamond count almost perfectly:

$$
R^2_{\mathrm{QuIC}}=0.993
\quad\text{at }n=14,
$$

and

$$
R^2_{\mathrm{QuIC}}=0.996
\quad\text{at }n=16.
$$

This result is especially important because the sixth spectral moment obeys the cubic-graph identity

$$
	ext{tr}(A^6)
=

12(C_6+D)
+
87n
+
6C_3
+
96C_4,
$$

where (C_6) is the number of 6-cycles and (D) is the number of diamonds.

The spectrum therefore determines the sum

$$
C_6+D,
$$

but does not generally determine how that sum is divided between 6-cycles and diamonds.

The diamond result shows that QuIC can predict this unresolved component. It is not merely supplying a more convenient linearization of a spectrally fixed quantity. It is recovering graph variation that remains after conditioning on the spectral representation.

The replication at both (n=14) and (n=16) makes this the clearest functional evidence for non-spectral information in the QuIC embedding.

#### Six-cycle count

The 6-cycle results complement the diamond findings.

At (n=14),

$$
R^2_{\mathrm{spectrum}}=0.985\pm0.003,
$$

and the two-stage model reaches

$$
R^2_{\mathrm{two-stage}}=0.994\pm0.002.
$$

At (n=16),

$$
R^2_{\mathrm{spectrum}}=0.985\pm0.002,
$$

and the two-stage score rises to

$$
R^2_{\mathrm{two-stage}}=0.997\pm0.000.
$$

The total gains are numerically small:

$$
\Delta R^2=+0.008
\quad\text{at }n=14,
$$

and

$$
\Delta R^2=+0.012
\quad\text{at }n=16.
$$

However, the residual-space results are substantial:

$$
R^2_{\mathrm{residual}}=0.533
\quad\text{at }n=14,
$$

and

$$
R^2_{\mathrm{residual}}=0.808
\quad\text{at }n=16.
$$

These two observations are compatible. The spectral model already explains approximately (98.5%) of the total 6-cycle variance, leaving only a small residual component. QuIC predicts a substantial fraction of that residual, but the residual itself represents only a small fraction of the total target variance.

The improvement is therefore small in total (R^2) but strong when evaluated specifically on the variation the spectrum misses.

The relation between 6-cycles and diamonds supplies a structural explanation. Because the spectrum constrains (C_6+D), information about diamonds also provides information about the unresolved 6-cycle component.

The 6-cycle and diamond rows should therefore be interpreted jointly:

* the spectrum predicts their constrained sum;
* QuIC predicts how that sum is divided;
* the residual probe detects this division in both directions.

#### Girth

QuIC also predicts the residuals of the linear spectral model for girth.

At (n=14),

$$
R^2_{\mathrm{spectrum}}=0.686\pm0.072,
$$

while the two-stage model reaches

$$
R^2_{\mathrm{two-stage}}=0.907\pm0.030.
$$

At (n=16),

$$
R^2_{\mathrm{spectrum}}=0.635\pm0.041,
$$

while the two-stage result is

$$
R^2_{\mathrm{two-stage}}=0.938\pm0.008.
$$

The improvements are large:

$$
\Delta R^2=+0.221
\quad\text{at }n=14,
$$

and

$$
\Delta R^2=+0.303
\quad\text{at }n=16.
$$

Residual-space performance is similarly strong:

$$
R^2_{\mathrm{residual}}=0.701
\quad\text{and}\quad
0.829.
$$

QuIC alone remains stronger than the two-stage model, reaching approximately perfect prediction at both graph orders. This indicates that QuIC provides a coordinate system in which girth is especially accessible.

The girth result should not be treated as clean evidence of non-spectral information. Within these cubic-graph censuses, girth is determined by the presence or absence of short cycles. It is therefore a nonlinear function of cycle information already encoded by the spectrum.

The result instead demonstrates that QuIC recovers nonlinear structural information missed by a linear spectral ridge model. It is evidence for representational advantage, rather than evidence that girth itself is not spectrally determined.

#### Diameter

The diameter results are weak and inconsistent across the two available orders.

At (n=14), the two-stage model does not improve on the spectral baseline:

$$
\Delta R^2\approx0,
\qquad
R^2_{\mathrm{residual}}=-0.009.
$$

At (n=16), there is a small improvement:

$$
R^2_{\mathrm{spectrum}}=0.789\pm0.014,
$$

$$
R^2_{\mathrm{two-stage}}=0.802\pm0.015,
$$

and

$$
\Delta R^2=+0.014.
$$

The residual-space score is only

$$
R^2_{\mathrm{residual}}=0.062.
$$

This is not strong evidence that QuIC contains a useful diameter component beyond the spectrum. The (n=16) gain may indicate a weak signal, but the effect is absent at (n=14) and small relative to the diamond, 6-cycle, and girth results.

#### Radius, Wiener index, and automorphism order

Only (n=14) results are currently available for these targets.

#### Radius

The spectral baseline reaches

$$
R^2=0.345\pm0.081,
$$

while the two-stage model obtains

$$
R^2=0.344\pm0.096.
$$

The residual-space score is approximately zero:

$$
R^2_{\mathrm{residual}}=-0.001.
$$

QuIC provides no detectable residual information for radius at (n=14).

#### Wiener index

The spectral baseline is already strong:

$$
R^2=0.973\pm0.006.
$$

Adding the QuIC residual model reduces performance slightly:

$$
R^2_{\mathrm{two-stage}}=0.961\pm0.021,
$$

with

$$
\Delta R^2=-0.012
$$

and

$$
R^2_{\mathrm{residual}}=-0.438.
$$

There is no evidence that QuIC predicts the remaining Wiener-index variation at (n=14).

#### Automorphism-group order

For

$$
\log_2|\mathrm{Aut}(G)|,
$$

the spectral baseline obtains

$$
R^2=0.678\pm0.027,
$$

and the two-stage model obtains

$$
R^2=0.684\pm0.025.
$$

The apparent gain is only

$$
\Delta R^2=+0.006,
$$

while residual-space performance is slightly negative:

$$
R^2_{\mathrm{residual}}=-0.003.
$$

The small total-score difference is therefore not supported by direct residual prediction and should be treated as fold or regularization variation rather than evidence of useful non-spectral decoding.

The pending (n=16) results will determine whether any of these three targets behave differently at the larger graph order.

#### Interpreting residual-space and total (R^2)

The two reported improvement measures answer different questions.

The total-score change,

$$
\Delta R^2,
$$

measures how much the complete target prediction improves after adding QuIC.

Residual-space (R^2) measures how well QuIC predicts only the component left unexplained by the spectral model.

A target can therefore have:

* high residual (R^2) but small (\Delta R^2), when the spectral residual is real but small relative to total target variance;
* large values for both, when the spectrum leaves a substantial and predictable residual;
* or negative residual (R^2), when QuIC cannot predict the remaining variation.

The 6-cycle row illustrates the first case. Diamonds illustrate the second. Radius and Wiener index illustrate the third.

#### What the experiment establishes

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

#### Necessary qualifications

The (n=16) run is incomplete. Conclusions about radius, Wiener index, and automorphism-group order currently rely only on (n=14).

No paired statistical test is reported for the foldwise changes in (R^2). The diamond effects are sufficiently large and consistent across graph orders to be persuasive descriptively, but formal uncertainty for

$$
\Delta R^2
$$

would strengthen the presentation.

The two-stage model is not intended to outperform QuIC alone on every target. For diamonds and girth, QuIC alone is stronger than the combined model. The purpose of the two-stage experiment is narrower: determine whether QuIC predicts the component missed by the spectrum.

The spectral model is also linear in the supplied eigenvalue and moment coordinates. Girth improvements may therefore reflect nonlinear repackaging of spectral information. The diamond result is stronger because the target varies independently of the adjacency spectrum, while the sixth-moment identity explains why QuIC's diamond signal also appears in the 6-cycle residual.

Finally, residual-space (R^2) should not be interpreted on targets whose spectral residual variance is essentially zero. The strongly negative values for exact spectral controls are numerical artifacts of evaluating (R^2) on an almost constant residual target.

#### Overall assessment

The timeout does not prevent a clear interpretation of the principal result. The most important rows completed at both graph orders.

The experiment provides strong, replicated evidence that QuIC predicts a non-spectral structural component associated with diamonds and 6-cycles. The diamond result is large in both total and residual-space (R^2), while the 6-cycle result shows that QuIC recovers much of the small residual left after a nearly perfect spectral prediction.

The current evidence does not support a broad claim that QuIC improves prediction of all non-spectral graph invariants. Radius and Wiener index show no improvement at (n=14), diameter is at most weak, and the automorphism result is negligible.

The appropriate central conclusion is:

> Across complete connected cubic-graph censuses at (n=14) and (n=16), QuIC contains a functionally useful non-spectral residue. The clearest signal is diamond count: QuIC explains more than (82%) of the spectral residual variance and improves total (R^2) by approximately (0.31)–(0.34). The corresponding 6-cycle residual is also predictable, consistent with the spectral identity that fixes (C_6+D) but not its decomposition.

### E2C precision Audit
#### Experimental design

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

#### Dataset and census checks

The stored probability vectors have the expected dimensions, are sorted in descending order, and remain normalized to near machine precision.

The maximum stored-vector normalization errors are:

$$
2.00\times10^{-15}
\quad\text{at }n=14,
$$

and

$$
2.66\times10^{-15}
\quad\text{at }n=16.
$$

The adjacency-cospectral groups are independently reconstructed using exact integer trace sequences. The resulting census exactly matches the previously certified enumeration:

* 3 groups and 3 pairs at (n=14);
* 41 groups and 43 pairs at (n=16);
* 89 total graph members;
* 46 total within-group pairs.

This verifies that the precision audit is being applied to the intended set of cospectral comparisons.

#### Circuit smoke tests

The independent extended-precision implementation satisfies normalization and permutation invariance on representative graphs.

| Order  |  Normalization error | Permutation-invariance (L_1) |
| ------ | -------------------: | ---------------------------: |
| (n=14) | (9.76\times10^{-19}) |         (7.90\times10^{-20}) |
| (n=16) | (4.34\times10^{-19}) |         (1.31\times10^{-19}) |

These values are consistent with the numerical floor of the long-double computation.

The permutation test is especially relevant because QuIC sorts the output probabilities and therefore claims invariance to vertex relabeling. The independent implementation reproduces that behavior to approximately (10^{-19}).

#### Independent reconstruction gate

Every one of the 89 relevant vectors is recomputed using a pure NumPy implementation independent of the stored producer pipeline.

The largest coordinate-wise disagreement between the independent float64 vectors and the stored vectors is:

$$
1.89\times10^{-15}
\quad\text{at }n=14,
$$

and

$$
2.22\times10^{-15}
\quad\text{at }n=16.
$$

The global worst case is therefore

$$
\max_{G,z}
\left|
p^{\mathrm{independent}}_z(G)
-----------------------------

p^{\mathrm{stored}}_z(G)
\right|
=

2.22\times10^{-15},
$$

well below the preregistered validation threshold

$$
10^{-12}.
$$

This gate is load-bearing. It establishes that the stored vectors used elsewhere in the analysis are reproduced by an independently implemented circuit rather than by reusing the original simulation code.

#### Measured float64 reconstruction floor

Each graph is recomputed in 80-bit long-double arithmetic. The numerical floor of the float64 pipeline is measured directly as

$$
\left|
\mathbf p_{\mathrm{float64}}(G)
-------------------------------

\mathbf p_{\mathrm{longdouble}}(G)
\right|_1.
$$

The observed per-graph floors are:

| Order  |              Minimum |               Median |              Maximum |
| ------ | -------------------: | -------------------: | -------------------: |
| (n=14) | (7.44\times10^{-17}) | (3.49\times10^{-16}) | (5.82\times10^{-16}) |
| (n=16) | (9.05\times10^{-17}) | (5.72\times10^{-16}) | (1.11\times10^{-15}) |

These are empirical reconstruction errors for the actual circuit and graphs, not estimates based only on machine epsilon.

The measured floors are several orders of magnitude below even the smallest cospectral separation.

#### Multiprecision certification

Every pair with long-double separation below

$$
10^{-6}
$$

is recomputed using 40-digit `mpmath` arithmetic.

This includes:

* 30 of the 46 cospectral pairs;
* 60 distinct graphs.

The measured long-double-to-`mpmath` floor per graph ranges from

$$
4.63\times10^{-19}
$$

to

$$
1.03\times10^{-18},
$$

with median approximately

$$
6.87\times10^{-19}.
$$

For all 30 audited pairs, the float64, long-double, and 40-digit pair distances agree to the precision displayed in the report.

The closest (n=14) pair remains separated by

$$
5.868\times10^{-8}
$$

under all three arithmetic implementations.

The closest (n=16) pair remains separated by

$$
1.917\times10^{-8}.
$$

The smallest reported distances therefore survive both an independent implementation and two successive increases in arithmetic precision.

#### Separation relative to the measured numerical floor

For each pair, the audit compares the long-double separation with the sum of the two graphs' measured float64 reconstruction floors:

$$
\text{floor ratio}
=

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
$$

The smallest ratio across all 46 pairs is

$$
2.48\times10^7.
$$

The largest is

$$
2.91\times10^{10}.
$$

Thus, every reported cospectral separation is at least approximately **25 million times larger** than its measured float64 reconstruction floor.

No pair lies within ten times the numerical floor:

$$
0\text{ of }46
$$

pairs are flagged as unresolved.

This is the central precision result. The cospectral separations are not accumulated float64 rounding differences.

#### Separation ranges

The certified pairwise (L_1) ranges are:

| Order  |   Minimum separation |   Maximum separation |
| ------ | -------------------: | -------------------: |
| (n=14) | (5.868\times10^{-8}) | (1.692\times10^{-5}) |
| (n=16) | (1.917\times10^{-8}) | (1.680\times10^{-5}) |

The similarity of these ranges across graph orders is notable. Increasing from (n=14) to (n=16) introduces many more cospectral pairs, including several extremely close pairs, but the largest non-spectral separations remain near

$$
1.7\times10^{-5}.
$$

Representative pairs include:

| Order  | Pair        |      Certified (L_1) | Multiple of float64 floor |
| ------ | ----------- | -------------------: | ------------------------: |
| (n=14) | ((234,239)) | (5.868\times10^{-8}) |          (1.36\times10^8) |
| (n=14) | ((79,458))  | (3.908\times10^{-7}) |          (4.12\times10^8) |
| (n=14) | ((201,203)) | (1.692\times10^{-5}) |       (2.91\times10^{10}) |
| (n=16) | ((594,601)) | (1.917\times10^{-8}) |          (2.48\times10^7) |
| (n=16) | ((1,5))     | (1.680\times10^{-5}) |       (1.29\times10^{10}) |

Even the weakest certified separation is vastly larger than the measured arithmetic uncertainty.

#### Position within the census distance scale

The complete (n=14) pairwise distribution contains 129,286 graph pairs. At (n=16), the reference distribution is estimated using 299,918 seeded random graph pairs.

The median census-wide QuIC distance is approximately:

$$
8.5\times10^{-5}
\quad\text{at }n=14,
$$

and

$$
7.7\times10^{-5}
\quad\text{at }n=16.
$$

The cospectral separations occupy the lower tail of these distributions.

At (n=14), their percentile standings range from approximately

$$
0
$$

to

$$
5.82.
$$

At (n=16), they range from approximately

$$
0
$$

to

$$
6.37.
$$

Relative to the median arbitrary-pair distance, the cospectral separations range from:

$$
6.91\times10^{-4}
$$

to

$$
1.99\times10^{-1}
$$

at (n=14), and from

$$
2.49\times10^{-4}
$$

to

$$
2.18\times10^{-1}
$$

at (n=16).

This is expected. Cospectral graphs have their dominant adjacency-spectral differences removed, so their remaining QuIC separations should be much smaller than those between arbitrary graph pairs.

The low census percentiles do not weaken the precision certification. They describe the geometric magnitude of the non-spectral residue, not whether the residue is numerically real.

#### Head/tail decomposition

For each pair, the notebook measures how the total (L_1) separation is distributed across the sorted probability ranks.

The reported quantities are:

* `hf50`: fraction of total separation contained in the 50 largest probabilities;
* `hf90`: fraction contained in the 90 largest probabilities;
* `k50`: number of leading coordinates needed to capture 50% of the separation;
* `k90`: number needed to capture 90%.

The results are heterogeneous.

#### Strongly head-concentrated pairs

The largest-separation pairs place most of their difference in the leading coordinates.

For the (n=14) pair ((201,203)):

$$
66.8%
$$

of the separation lies in the top 50 coordinates, and

$$
85.6%
$$

lies in the top 90.

Half of the total separation is reached by coordinate

$$
k_{50}=42,
$$

and 90% by

$$
k_{90}=167.
$$

The four largest (n=16) pairs behave similarly:

* approximately (66%) of their separation occurs in the top 50 coordinates;
* approximately (85%) occurs in the top 90;
* (k_{50}\approx49\text{--}51);
* (k_{90}\approx197\text{--}202).

These pairs directly support the earlier observation that the strongest non-spectral differences are visible in the head of the sorted distribution.

#### Diffuse pairs

Many of the smaller (n=16) separations are less concentrated.

For several pairs, the top 50 coordinates contain only approximately

$$
2%\text{--}10%
$$

of the total separation. Their (k_{50}) values can exceed 400 and reach as high as 875.

The most diffuse reported pair requires

$$
k_{90}=2804
$$

coordinates to accumulate 90% of its separation.

The strongest possible statement is therefore not that every cospectral difference is concentrated in the first 50 or 90 probabilities. That expectation is supported primarily for the largest-separation pairs.

Nevertheless, all pairs remain concentrated within a relatively small leading portion of the complete vector:

* at (n=14), every pair reaches 90% by coordinate 1,133, less than 7% of the 16,384-dimensional vector;
* at (n=16), every pair reaches 90% by coordinate 2,804, less than 4.3% of the 65,536-dimensional vector.

Thus, the non-spectral residue is broadly head-weighted, but its concentration within the very first 50–90 coordinates varies substantially by pair.

#### What the experiment establishes

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

$$
\boxed{
\text{The reported cospectral separations are genuine ideal-circuit differences, not floating-point artifacts.}
}
$$

#### Necessary qualifications

The audit establishes numerical reality, not experimental observability.

A separation of order

$$
10^{-8}
$$

can be many millions of times larger than floating-point error while still being too small to resolve using practical finite-shot sampling or noisy hardware. Numerical certification and measurement feasibility are separate questions.

The 40-digit calculation is applied only to pairs whose long-double separation is below (10^{-6}). Larger pairs are not recomputed using `mpmath` because their float64-to-long-double separation ratios are already between approximately (10^8) and (10^{10}).

The (n=16) census percentile estimates use a random sample of approximately 300,000 graph pairs rather than the complete set of more than eight million pairs. These percentile values are therefore estimates. They do not affect the arithmetic certification.

The exact same float64 circuit angles are lifted into extended precision. This is the correct design for measuring the arithmetic error of the original circuit. It does not test sensitivity to small perturbations in the angles themselves.

Finally, the head-concentration hypothesis receives a qualified result. It is strongly supported for the largest separations, but many smaller pairs distribute their differences across hundreds or thousands of leading coordinates.

#### Overall assessment

This notebook closes the principal numerical objection to the cospectral analysis.

The stored vectors are independently reproduced, the exact cospectral census is recovered, and every one of the 46 pair separations remains stable under long-double arithmetic. The 30 closest pairs are additionally confirmed using 40-digit arithmetic.

The smallest separation,

$$
1.917\times10^{-8},
$$

is still approximately

$$
2.48\times10^7
$$

times larger than its measured float64 reconstruction floor. No pair is remotely close to being explained by numerical roundoff.

The appropriate central claim is:

> Independent circuit reconstruction and extended-precision arithmetic certify every QuIC separation among the 46 adjacency-cospectral pairs at (n=14) and (n=16). All separations lie at least (2.48\times10^7) times above the measured float64 reconstruction floor, and the 30 closest pairs are reproduced using 40-digit arithmetic. The non-spectral residue is therefore numerically genuine, although its practical shot-level resolvability remains a separate question.

### E3 - GNN Controls
#### Experimental design

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

$$
\text{depth}\in{3,5},
\qquad
\eta\in{10^{-3},10^{-2}}.
$$

The selected configuration for each graph order, model, and target is determined using the fold-0, seed-0 validation split and then reused across:

* 5 frozen outer folds;
* 3 random seeds.

Each reported GNN score therefore summarizes 15 trained runs per table cell.

The random-node-initialization model resamples its features every epoch. Validation is averaged over five random draws, and test predictions and embeddings are averaged over ten draws.

The Laplacian positional encoding contains the first eight nonconstant Laplacian eigenvectors. Random sign flips are used during training.

QuIC is not trained on any target. Its column uses ridge regression on the full sorted ideal probability vector:

$$
\mathbf p(G)\in\mathbb R^{2^n}.
$$

The QuIC feature dimensions are therefore:

$$
2^{14}=16{,}384,
\qquad
2^{16}=65{,}536.
$$

#### Headline results: trained-network predictions

The primary table compares each task-trained network's own prediction head with a linear probe on QuIC.

##### (n=14)

| Target       |            QuIC |        GIN-const |        GCN-const |          GIN-RNI |       GIN-LapPE |
| ------------ | --------------: | ---------------: | ---------------: | ---------------: | --------------: |
| Triangles    | (1.000\pm0.000) | (-0.013\pm0.026) | (-0.008\pm0.009) |  (0.430\pm0.052) | (0.824\pm0.240) |
| 4-cycles     | (0.998\pm0.002) | (-0.036\pm0.050) | (-0.024\pm0.028) |  (0.048\pm0.076) | (0.524\pm0.258) |
| 5-cycles     | (0.928\pm0.092) | (-0.024\pm0.024) | (-0.028\pm0.027) | (-0.021\pm0.027) | (0.470\pm0.132) |
| 6-cycles     | (0.485\pm0.326) | (-0.019\pm0.024) | (-0.020\pm0.029) |  (0.034\pm0.035) | (0.420\pm0.094) |
| Girth        | (0.993\pm0.014) | (-0.015\pm0.026) | (-0.016\pm0.029) |  (0.140\pm0.042) | (0.820\pm0.098) |
| Diameter     | (0.548\pm0.058) | (-0.023\pm0.032) | (-0.023\pm0.030) |  (0.268\pm0.093) | (0.664\pm0.193) |
| Spectral gap | (0.944\pm0.010) | (-0.012\pm0.023) | (-0.008\pm0.009) |  (0.506\pm0.068) | (0.994\pm0.004) |

##### (n=16)

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

$$
R^2_{\mathrm{QuIC}}=0.485\pm0.326,
\qquad
R^2_{\mathrm{LapPE}}=0.420\pm0.094.
$$

The QuIC mean is higher, but the fold variance is too large to treat this as a strong separation. At (n=16), the result is clearer:

$$
0.642\pm0.122
\quad\text{versus}\quad
0.498\pm0.023.
$$

LapPE outperforms QuIC on diameter and spectral gap at both graph orders. These results are important controls: the comparison does not uniformly favor QuIC, and the strongest GNN arm wins on two targets outside the local-cycle hierarchy.

#### Constant-feature collapse

The constant-feature GIN and GCN arms fail exactly as predicted by their expressiveness class.

For a regular graph with uniform initial node features, every vertex receives the same representation after every message-passing layer. Since every graph in a census has the same number of vertices and sum pooling is used, the graph-level embedding is identical for every graph.

The measured collapse statistic is

$$
\frac{
\max_{i,j}|\mathbf h(G_i)-\mathbf h(G_j)|_2
}{
	ext{mean}_i|\mathbf h(G_i)|_2
}.
$$

For every constant-feature run at both graph orders, this ratio is:

$$
0.00\times10^0.
$$

This covers 210 runs per graph order:

$$
2\text{ architectures}
\times
7\text{ targets}
\times
3\text{ seeds}
\times
5\text{ folds},
$$

or 420 completed constant-feature runs across the two censuses.

The resulting test scores remain at the constant-predictor floor. Slightly negative cross-validated (R^2) values arise because predicting the training mean can perform marginally worse than predicting the test-fold mean.

These columns are not merely weak baselines. They are measured demonstrations of the standard 1-WL failure mode on fixed-order regular graphs with uniform features.

#### Random node initialization

Random node initialization breaks the exact symmetry, but the resulting models recover only limited structural information.

At (n=16), the trained prediction heads obtain:

$$
R^2=
0.566,\ 0.201,\ 0.099,\ 0.068
$$

for (C_3,C_4,C_5,C_6), respectively.

The pattern deteriorates rapidly with cycle length. The model recovers a moderate triangle signal, a weak 4-cycle signal, and little 5- or 6-cycle information.

This is not explained by an insufficient training budget. The (n=16) RNI models commonly train for several hundred epochs, with median best epochs between approximately 250 and 414 depending on the target. They also receive fresh random features every epoch and noise-averaged evaluation.

Performance improves between (n=14) and (n=16), especially for triangles and diameter, but the larger census does not close the gap with QuIC or LapPE.

The result illustrates the difference between theoretical symmetry-breaking capacity and practical learnability. Random identifiers prevent exact collapse, but the trained network does not reliably organize the induced stochastic representation around deeper cycle invariants.

#### Laplacian positional encoding

LapPE is the strongest GNN baseline.

At (n=16), its cycle-count scores decrease monotonically with cycle length:

$$
0.941
\rightarrow
0.614
\rightarrow
0.568
\rightarrow
0.498.
$$

The same ordering appears at (n=14):

$$
0.824
\rightarrow
0.524
\rightarrow
0.470
\rightarrow
0.420.
$$

LapPE therefore recovers the shallowest cycle information most effectively and loses accessibility as the required structural depth increases.

QuIC exhibits the same qualitative hierarchy but retains substantially stronger scores through the 5-cycle layer:

$$
1.000,\ 1.000,\ 0.982,\ 0.642
$$

at (n=16).

The LapPE 4-cycle score is notably unstable:

$$
0.524\pm0.258
\quad\text{at }n=14,
$$

and

$$
0.614\pm0.267
\quad\text{at }n=16.
$$

This variation may reflect sensitivity to folds, training seeds, eigenvector signs, or eigenspace-basis choices. The experiment reports the instability rather than selecting a favorable run.

LapPE wins the two non-cycle targets for which its inductive bias is most favorable:

$$
R^2_{\mathrm{diameter}}=0.807
\quad\text{at }n=16,
$$

and

$$
R^2_{\mathrm{spectral\ gap}}=0.996.
$$

This prevents the result from being interpreted as a generic failure of the trained architecture. LapPE can outperform QuIC where the target aligns with its representation.

#### Linear probes on the learned GNN embeddings

A second analysis replaces each GNN's trained prediction head with the same ridge-probe protocol used for QuIC.

The GNN embeddings remain target-specific: each was produced by a network trained using labels for the target being probed. The analysis therefore tests whether the final hidden representation contains information that the network's original head failed to use.

##### (n=14)

| Target       |            QuIC |        GIN-const |        GCN-const |          GIN-RNI |       GIN-LapPE |
| ------------ | --------------: | ---------------: | ---------------: | ---------------: | --------------: |
| Triangles    | (1.000\pm0.000) | (-0.002\pm0.004) | (-0.003\pm0.004) |  (0.660\pm0.054) | (0.887\pm0.106) |
| 4-cycles     | (0.998\pm0.002) | (-0.008\pm0.006) | (-0.010\pm0.014) |  (0.059\pm0.042) | (0.594\pm0.103) |
| 5-cycles     | (0.928\pm0.092) | (-0.011\pm0.012) | (-0.013\pm0.014) | (-0.008\pm0.021) | (0.468\pm0.161) |
| 6-cycles     | (0.485\pm0.326) | (-0.006\pm0.008) | (-0.005\pm0.008) |  (0.086\pm0.052) | (0.429\pm0.099) |
| Girth        | (0.993\pm0.014) | (-0.012\pm0.015) | (-0.008\pm0.012) |  (0.210\pm0.056) | (0.783\pm0.072) |
| Diameter     | (0.548\pm0.058) | (-0.008\pm0.007) | (-0.008\pm0.006) |  (0.387\pm0.081) | (0.720\pm0.061) |
| Spectral gap | (0.944\pm0.010) | (-0.002\pm0.002) | (-0.002\pm0.002) |  (0.546\pm0.057) | (0.993\pm0.003) |

##### (n=16)

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

$$
0.566\rightarrow0.718,
$$

and 5-cycle performance rises from

$$
0.099\rightarrow0.269.
$$

This indicates that some target information reaches the final hidden representation but is not fully exploited by the trained nonlinear head.

The same effect appears more modestly for LapPE. Its linear probe remains below QuIC on every cycle target and above QuIC on diameter and spectral gap.

The constant-feature embeddings remain exactly uninformative under the replacement readout, confirming that their failure occurs in the representation rather than only in the prediction head.

#### Matched-dimension comparison

The full QuIC vector is much larger than the 64-dimensional GNN embeddings. The notebook therefore reads the existing QuIC truncation curve at:

$$
k=50
\quad\text{and}\quad
k=100,
$$

which bracket the GNN width of 64.

##### (n=14)

| Target    | QuIC (k=50) | QuIC (k=100) |
| --------- | ----------: | -----------: |
| Triangles |       1.000 |        1.000 |
| 4-cycles  |       0.988 |        0.993 |
| 5-cycles  |    (-0.026) |        0.272 |
| 6-cycles  |       0.228 |        0.235 |

##### (n=16)

| Target    | QuIC (k=50) | QuIC (k=100) |
| --------- | ----------: | -----------: |
| Triangles |       1.000 |        1.000 |
| 4-cycles  |       0.981 |        0.996 |
| 5-cycles  |       0.167 |        0.335 |
| 6-cycles  |       0.179 |        0.184 |

At approximately matched representation dimension, QuIC retains essentially perfect triangle and 4-cycle prediction and outperforms every trained GNN baseline on those targets.

The deeper cycle layers behave differently. At (k=100), QuIC remains below the LapPE representation for 5- and 6-cycle prediction:

$$
0.335<0.571
$$

for 5-cycles at (n=16), and

$$
0.184<0.501
$$

for 6-cycles.

The full-vector advantage on deeper cycles therefore depends on information distributed farther down the sorted probability vector. It is not preserved under aggressive truncation to approximately 64 coordinates.

This gives a more precise interpretation of QuIC's advantage:

* shallow-cycle information is concentrated in the probability head;
* deeper-cycle information requires a substantially larger portion of the representation.

#### Scaling from (n=14) to (n=16)

The larger census strengthens most of the conclusions.

For QuIC:

$$
R^2_{C_5}: 0.928\rightarrow0.982,
$$

$$
R^2_{C_6}: 0.485\rightarrow0.642,
$$

and

$$
R^2_{\mathrm{diameter}}: 0.548\rightarrow0.737.
$$

For RNI, scaling improves triangles, 4-cycles, diameter, and spectral gap, but the deeper cycle scores remain weak.

For LapPE, the larger census improves triangle, 4-cycle, 5-cycle, 6-cycle, girth, and diameter prediction. The cycle-depth decline nevertheless remains.

The constant-feature arms approach (R^2=0) more closely at (n=16), as expected when the test folds become larger, while their embeddings remain exactly collapsed.

The (n=16) results therefore replicate the qualitative ordering:

$$
\text{QuIC}

>

\text{LapPE}

>

\text{RNI}

>

\text{constant-feature message passing}
$$

for the cycle-count targets.

This ordering does not hold universally. LapPE remains stronger on diameter and spectral gap.

#### Cospectral graph pairs

The consumer identifies:

* 3 adjacency-cospectral pairs at (n=14);
* 43 adjacency-cospectral pairs at (n=16).

The (n=16) set includes one mutually cospectral triple:

$$
(582,3061,3800).
$$

For each trained model, the analysis computes:

$$
\frac{
|\mathbf h(G_i)-\mathbf h(G_j)|*2
}{
	ext{median}*{a<b}
|\mathbf h(G_a)-\mathbf h(G_b)|_2
}
$$

for each cospectral pair, using the triangle-target runs.

#### Constant-feature models

Both constant-feature models assign zero distance to every cospectral pair because they assign the same embedding to every graph:

$$
d_{\mathrm{mate}}=0.
$$

#### Random node initialization

The normalized RNI mate distances are:

* (0.884)–(0.954) at (n=14);
* (0.764)–(1.031) at (n=16).

Their median (n=16) value is approximately:

$$
0.898.
$$

Cospectral pairs are therefore almost as far apart as ordinary graph pairs in the averaged RNI embedding space.

This should not automatically be interpreted as meaningful structural separation. RNI is stochastic, and evaluation averages only ten feature draws. Some separation may reflect finite-draw random-feature variation rather than a stable graph invariant. The result mainly shows that RNI does not place cospectral mates in a distinctively close region.

#### Laplacian positional encoding

The normalized LapPE mate distances are:

* (0.181)–(0.517) at (n=14);
* (0.198)–(0.896) at (n=16).

The median at (n=16) is approximately:

$$
0.349.
$$

Cospectral pairs are therefore closer than typical graph pairs but not collapsed.

This corrects an incorrect statement in the producer notebook. Adjacency-cospectral graphs share eigenvalues, but LapPE supplies eigenvectors. Their eigenvectors need not agree, so LapPE is not theoretically required to map cospectral graphs to the same representation.

The observed separation remains an empirical property of this implementation. Raw eigenvectors have sign and degenerate-eigenspace ambiguities. Training-time sign flips address sign ambiguity but not arbitrary rotations within repeated eigenspaces. The LapPE mate distances should therefore not be treated as a certified invariant separation comparable to the exact QuIC cospectral audit.

#### What the experiment establishes

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

#### Necessary qualifications

The full-vector QuIC comparison is not dimension matched. QuIC uses 16,384 or 65,536 probability coordinates, whereas each GNN graph embedding has width 64. The truncation analysis shows that QuIC's deeper-cycle advantage is reduced or reversed near matched dimensionality.

QuIC also uses exact ideal probabilities. The experiment evaluates structural decodability, not finite-shot performance, hardware robustness, runtime, or memory efficiency. Producing the complete probability vector is exponentially expensive in the number of qubits.

The baseline set does not represent all graph-learning architectures. It includes conventional GIN and GCN, plus RNI and LapPE repairs. Higher-order GNNs, subgraph methods, graph transformers, and architectures explicitly designed to exceed 1-WL are not evaluated.

The constant-feature arms are theoretically guaranteed negative controls on fixed-order regular graphs. They demonstrate the expected message-passing limitation but should not be presented as strong practical competitors.

Hyperparameter tuning uses one fold-0, seed-0 validation split per model and target rather than a fully nested tuning procedure. No test-fold labels enter selection, but the four-point grid may not identify the best configuration for every fold.

The reported standard deviations are not directly equivalent across methods. QuIC summarizes five folds, whereas the GNN columns summarize 15 correlated seed-fold runs. No paired significance tests are reported for the differences.

The post-hoc probes operate on target-trained GNN embeddings. They are useful for separating representation failure from head failure, but they do not compare target-independent frozen embeddings in the same sense as QuIC.

Finally, the RNI and LapPE cospectral analyses are geometric diagnostics rather than invariance certificates. RNI is stochastic, and LapPE is sensitive to eigenvector-basis conventions.

#### Overall assessment

The experiment provides a clear hierarchy of baseline behavior.

Uniform-feature message passing collapses exactly and cannot distinguish any graphs in either cubic census. Random node initialization restores variation but learns little beyond triangles and coarse global structure. Laplacian positional encoding is substantially stronger and nearly solves triangles, diameter, and spectral gap, but its cycle-count performance declines steadily with cycle length.

Against these baselines, the fixed QuIC representation provides exceptionally broad cycle accessibility. At (n=16), a linear readout obtains:

$$
1.000,\ 1.000,\ 0.982,\ 0.642
$$

for (C_3,C_4,C_5,C_6), compared with LapPE's:

$$
0.941,\ 0.614,\ 0.568,\ 0.498.
$$

The advantage is not universal. LapPE is stronger for diameter and spectral gap, and at approximately matched representation dimension it also exceeds truncated QuIC on 5- and 6-cycle prediction.

The appropriate central claim is:

> On the complete connected cubic-graph censuses at (n=14) and (n=16), conventional constant-feature message passing collapses exactly, while RNI and Laplacian positional encodings recover progressively more structure but lose accessibility with cycle depth. The full, fixed QuIC probability representation provides the strongest linear decodability across all tested cycle-count targets, although its deeper-cycle advantage depends on a substantially higher-dimensional readout and does not extend to diameter or spectral gap.


### E3C — Folklore 2-WL Baseline

#### Experimental design

This experiment adds a stronger classical graph representation baseline to the QuIC analysis.

The earlier constant-feature GIN and GCN models are useful negative controls, but they are not competitive structural representations on fixed-order regular graphs. Ordinary 1-WL message passing collapses by construction because every vertex begins with the same feature and receives the same multiset of neighbor features.

The present experiment therefore evaluates **folklore 2-WL**, defined on ordered vertex pairs. For each ordered pair ((u,v)), refinement updates its color according to

$$
c_{t+1}(u,v)
=

	ext{hash}
\left(
c_t(u,v),
\left{!\left{
\left(c_t(u,w),c_t(w,v)\right)
:
w\in V
\right}!\right}
\right).
$$

Initial pair colors distinguish:

* diagonal pairs;
* adjacent pairs;
* nonadjacent pairs.

The analysis uses the complete connected cubic-graph censuses at:

* (n=14): 509 graphs;
* (n=16): 4,060 graphs.

The seven prediction targets are:

* triangle count (C_3);
* 4-cycle count (C_4);
* 5-cycle count (C_5);
* 6-cycle count (C_6);
* girth;
* diameter;
* spectral gap.

Two 2-WL representations are evaluated.

#### Cumulative all-rounds representation

For each refinement round, the histogram of pair colors is computed. Histograms from all rounds are concatenated into a sparse feature vector:

$$
\mathbf h_{\mathrm{cumulative}}(G)
=

\mathbf h_0(G)
\oplus
\mathbf h_1(G)
\oplus
\cdots
\oplus
\mathbf h_T(G).
$$

This is the primary baseline. Early rounds retain shared motif-level colors that can transfer between training and test graphs.

#### Stable-only representation

The second arm uses only the histogram at the final stable refinement round:

$$
\mathbf h_{\mathrm{stable}}(G).
$$

This representation has maximal distinguishing power on the tested censuses, but its final colors are highly graph-specific. It is included to separate two different properties:

* ability to distinguish graphs;
* ability to support transferable linear prediction.

All graphs in a census are refined synchronously using one shared color vocabulary per round. Ridge probes use the same five shuffled folds and regularization grid as the QuIC E2 experiment.

#### Target and protocol checks

The graph invariants are recomputed directly from the adjacency matrices.

The cubic trace identities

$$
	ext{tr}(A^3)=6C_3
$$

and

$$
	ext{tr}(A^4)=8C_4+15n
$$

hold exactly for every graph at both orders.

The ordinary 1-WL control also behaves exactly as expected. Every vertex retains the same color on every graph because the censuses are fixed-order and 3-regular. The resulting graph histogram is the constant vector:

$$
(n).
$$

Ordinary 1-WL therefore has no predictive variation and remains at the constant-predictor floor:

$$
R^2=0.
$$

This is asserted directly rather than estimated through unnecessary ridge fits.

#### Refinement behavior

Folklore 2-WL stabilizes after five refinement checks at both graph orders.

##### (n=14)

The per-round vocabulary sizes are:

$$
3,\ 8,\ 1{,}894,\ 56{,}352,\ 56{,}708.
$$

The cumulative representation has dimension:

$$
114{,}965.
$$

The stable-only representation has dimension:

$$
56{,}708.
$$

All 509 graphs have distinct stable histograms:

$$
509/509.
$$

##### (n=16)

The per-round vocabulary sizes are:

$$
3,\ 8,\ 2{,}230,\ 741{,}367,\ 757{,}353.
$$

The cumulative representation has dimension:

$$
1{,}500{,}961.
$$

The stable-only representation has dimension:

$$
757{,}353.
$$

All 4,060 graphs have distinct stable histograms:

$$
4{,}060/4{,}060.
$$

The refinement therefore distinguishes every graph in both complete censuses.

The rapid vocabulary expansion is also notable. Most final-round colors are highly specific to individual graph structures. This produces excellent graph discrimination but little coordinate sharing between independently held-out graphs.

#### Cospectral separation

The exact adjacency-cospectral groups are reconstructed using integer trace tuples.

The censuses contain:

* 3 cospectral pairs at (n=14);
* 43 within-group pairs at (n=16), arising from 40 pairs and one triple.

Stable 2-WL histograms separate every exact cospectral pair:

$$
3/3
\quad\text{at }n=14,
$$

and

$$
43/43
\quad\text{at }n=16.
$$

The comparisons use exact integer histogram counts. No numerical tolerance is involved.

| Representation     | (n=14) cospectral pairs | (n=16) cospectral pairs |
| ------------------ | ----------------------: | ----------------------: |
| Ordinary 1-WL      |                     0/3 |                    0/43 |
| Adjacency spectrum |                     0/3 |                    0/43 |
| Folklore 2-WL      |                     3/3 |                   43/43 |
| QuIC               |                     3/3 |                   43/43 |

Folklore 2-WL and QuIC both distinguish every tested adjacency-cospectral pair. The adjacency spectrum ties by definition, while ordinary 1-WL assigns the same representation to every graph in each census.

This result shows that cospectral separation is not unique to QuIC once a sufficiently strong higher-order classical representation is included.

#### Ridge-probe results

##### (n=14)

| Target       | 2-WL all rounds | 2-WL stable only |  QuIC |
| ------------ | --------------: | ---------------: | ----: |
| (C_3)        | (0.998\pm0.001) | (-0.005\pm0.003) | 1.000 |
| (C_4)        | (0.993\pm0.004) | (-0.025\pm0.022) | 0.998 |
| (C_5)        | (0.917\pm0.038) | (-0.011\pm0.013) | 0.928 |
| (C_6)        | (0.879\pm0.061) | (-0.004\pm0.002) | 0.485 |
| Girth        | (0.787\pm0.071) | (-0.020\pm0.013) | 0.993 |
| Diameter     | (0.779\pm0.031) | (-0.010\pm0.011) | 0.548 |
| Spectral gap | (0.947\pm0.028) | (-0.004\pm0.004) | 0.944 |

##### (n=16)

| Target       | 2-WL all rounds | 2-WL stable only |  QuIC |
| ------------ | --------------: | ---------------: | ----: |
| (C_3)        | (1.000\pm0.000) | (-0.007\pm0.007) | 1.000 |
| (C_4)        | (0.999\pm0.000) | (-0.018\pm0.009) | 1.000 |
| (C_5)        | (0.993\pm0.002) | (-0.001\pm0.001) | 0.982 |
| (C_6)        | (0.983\pm0.003) | (-0.002\pm0.001) | 0.642 |
| Girth        | (0.844\pm0.016) | (-0.006\pm0.002) | 0.999 |
| Diameter     | (0.861\pm0.012) | (-0.010\pm0.007) | 0.737 |
| Spectral gap | (0.982\pm0.002) | (-0.014\pm0.016) | 0.932 |

#### Short-cycle prediction

The cumulative 2-WL representation nearly saturates the short-cycle targets.

At (n=14), it obtains:

$$
R^2=
0.998,\ 0.993,\ 0.917
$$

for (C_3,C_4,C_5).

At (n=16), these increase to:

$$
1.000,\ 0.999,\ 0.993.
$$

QuIC and cumulative 2-WL are therefore closely matched on the first three cycle counts.

At (n=14), QuIC is numerically slightly stronger:

$$
1.000>0.998,
$$

$$
0.998>0.993,
$$

and

$$
0.928>0.917.
$$

At (n=16), the representations are effectively tied on (C_3) and (C_4), while cumulative 2-WL is slightly stronger on (C_5):

$$
0.993>0.982.
$$

The differences on these targets are small relative to the general conclusion: both representations make short-cycle information highly linearly accessible.

The classical spectral moments remain exact controls for (C_3,C_4,) and (C_5). Neither QuIC nor 2-WL exceeds the direct spectral identities on those targets.

#### Six-cycle count

The largest 2-WL advantage occurs for (C_6).

At (n=14):

$$
R^2_{\mathrm{2WL}}=0.879\pm0.061,
$$

compared with:

$$
R^2_{\mathrm{QuIC}}=0.485\pm0.326.
$$

At (n=16):

$$
R^2_{\mathrm{2WL}}=0.983\pm0.003,
$$

compared with:

$$
R^2_{\mathrm{QuIC}}=0.642\pm0.122.
$$

Cumulative 2-WL therefore captures substantially more transferable 6-cycle information.

The (n=16) score is almost saturated and has very little fold variation. This contrasts with QuIC, where 6-cycle accessibility is weaker and much less stable than the (C_3)–(C_5) hierarchy.

The result limits any claim that QuIC provides uniquely broad cycle-count accessibility. A higher-order classical refinement recovers the longer-cycle target more effectively.

#### Girth

Girth is the clearest QuIC advantage.

At (n=14):

$$
R^2_{\mathrm{QuIC}}=0.993,
$$

compared with:

$$
R^2_{\mathrm{2WL}}=0.787.
$$

At (n=16):

$$
R^2_{\mathrm{QuIC}}=0.999,
$$

compared with:

$$
R^2_{\mathrm{2WL}}=0.844.
$$

QuIC makes girth almost perfectly linearly accessible, whereas cumulative 2-WL remains strong but incomplete.

This result is notable because 2-WL already predicts the individual short-cycle counts extremely well. Nevertheless, its cumulative histogram does not translate those signals into an equally direct girth coordinate.

QuIC’s near-perfect girth score therefore reflects a particularly favorable organization of short-cycle presence and absence within its probability geometry.

#### Diameter

Cumulative 2-WL is substantially stronger on diameter.

At (n=14):

$$
0.779\pm0.031
$$

versus QuIC’s:

$$
0.548.
$$

At (n=16):

$$
0.861\pm0.012
$$

versus:

$$
0.737.
$$

The ordering replicates across graph orders and becomes more stable in the larger census.

This shows that the higher-order pair refinement captures global distance organization that is only partially accessible from the QuIC vector.

The result also confirms that the comparison is not simply determined by local motif recovery. QuIC is stronger on girth, while 2-WL is stronger on diameter, despite both being shortest-path-related graph invariants.

#### Spectral gap

Cumulative 2-WL predicts spectral gap strongly:

$$
0.947\pm0.028
$$

at (n=14), and

$$
0.982\pm0.002
$$

at (n=16).

QuIC obtains:

$$
0.944
\quad\text{and}\quad
0.932.
$$

The two representations are approximately matched at (n=14), while 2-WL has a clearer advantage at (n=16).

The sorted adjacency eigenvalue representation remains exact:

$$
R^2=1.000.
$$

Thus, both QuIC and 2-WL recover substantial spectral information, but neither improves upon directly providing the relevant eigenvalue coordinate.

#### Stable refinement versus transferable prediction

The stable-only results are near or below the constant-predictor floor for every target:

$$
R^2\approx0.
$$

This occurs despite the fact that the stable histograms distinguish every graph in both censuses.

There is no contradiction.

The final refinement round creates highly graph-specific colors. A test graph may activate coordinates that appear rarely or never among the training graphs. A linear model therefore cannot learn useful coefficients for those coordinates.

The cumulative representation avoids this failure by retaining early-round colors. Those colors are less discriminating but are shared across many graphs and correspond to recurring local or mesoscopic structures.

The experiment therefore demonstrates a direct distinction:

$$
\boxed{
\text{distinguishing power}
\neq
\text{transferable linear accessibility}
}
$$

A representation can uniquely identify every graph while supporting no useful out-of-sample linear prediction.

Conversely, the less-refined cumulative representation can sacrifice none of the relevant predictive structure because its earlier shared coordinates remain available.

#### Representation dimension

The tested representation dimensions are:

##### (n=14)

| Representation          | Dimension |
| ----------------------- | --------: |
| Ordinary 1-WL histogram |         1 |
| Adjacency spectrum      |        14 |
| QuIC                    |    16,384 |
| 2-WL stable only        |    56,708 |
| 2-WL cumulative         |   114,965 |

##### (n=16)

| Representation          | Dimension |
| ----------------------- | --------: |
| Ordinary 1-WL histogram |         1 |
| Adjacency spectrum      |        16 |
| QuIC                    |    65,536 |
| 2-WL stable only        |   757,353 |
| 2-WL cumulative         | 1,500,961 |

The cumulative 2-WL vocabulary is approximately:

$$
7.0
$$

times larger than the QuIC vector at (n=14), and approximately:

$$
22.9
$$

times larger at (n=16).

The stable-only vocabulary is approximately:

$$
3.5
$$

and

$$
11.6
$$

times larger than QuIC at the two graph orders.

These dimensions describe the ambient synchronized vocabulary. The 2-WL matrices are sparse, whereas the QuIC probability vectors are dense. Dimension alone therefore does not provide a complete storage or runtime comparison.

Nevertheless, the classical baseline is not a compact feature representation. Its strong predictive performance is obtained using a very large census-specific vocabulary whose growth is substantially faster than the fourfold increase in QuIC dimension from (n=14) to (n=16).

#### Relationship to the GNN baselines

The result clarifies the earlier E3 GNN comparison.

Constant-feature GIN and GCN fail because their message-passing representations remain within the ordinary 1-WL regime. Their collapse is not evidence that classical graph representations generally lack access to these invariants.

Folklore 2-WL provides the appropriate stronger control:

* it distinguishes every graph;
* it separates every adjacency-cospectral pair;
* it nearly saturates (C_3) through (C_6);
* it predicts diameter and spectral gap more strongly than QuIC.

The QuIC contribution therefore should not be framed as superior expressive power over higher-order classical methods.

The stronger framing is comparative:

* QuIC and folklore 2-WL organize different targets with different linear accessibility;
* QuIC provides nearly perfect girth and a compact probability-rank hierarchy;
* 2-WL provides stronger (C_6), diameter, and spectral-gap accessibility;
* both contain information beyond the adjacency spectrum;
* their representation sizes and computational constructions are substantially different.

#### What the experiment establishes

The completed results support six conclusions.

1. **Ordinary 1-WL is exactly blind on the fixed-order cubic censuses.**
   Its graph histogram is constant for every graph.

2. **Folklore 2-WL distinguishes every graph at both orders.**
   All 509 and all 4,060 stable histograms are unique.

3. **Folklore 2-WL separates every exact adjacency-cospectral pair.**
   It matches QuIC’s 3/3 and 43/43 cospectral-separation record.

4. **The cumulative representation is a strong predictive baseline.**
   It nearly saturates all cycle-count targets and performs strongly on diameter and spectral gap.

5. **QuIC and 2-WL emphasize different structural quantities.**
   QuIC is substantially stronger on girth, while 2-WL is substantially stronger on (C_6) and diameter.

6. **Maximal refinement does not imply transferable prediction.**
   The graph-unique stable histograms distinguish everything but produce near-zero held-out (R^2).

The experiment therefore replaces the weak classical comparison with a meaningful higher-order baseline without eliminating the QuIC contribution.

#### Necessary qualifications

The synchronized 2-WL vocabulary is constructed using the complete unlabeled census before the ridge folds are evaluated. No target labels are used, so this is not supervised target leakage. It is nevertheless a transductive feature-construction protocol.

For a strictly inductive evaluation, the color-signature vocabulary should be fitted on the training graphs and then applied to unseen graphs using a deterministic treatment of previously unseen signatures. The present results characterize linear accessibility within the complete censuses under a shared unsupervised vocabulary.

The cumulative representation has extremely high ambient dimension:

$$
114{,}965
\quad\text{and}\quad
1{,}500{,}961.
$$

Although the matrices are sparse, comparisons based only on feature count should not imply that QuIC is more computationally efficient. Exact QuIC state-vector construction also scales exponentially.

The experiment evaluates linear probes on histogram counts. Other readouts, normalizations, or kernel functions could change the stable-only and cumulative results.

The stable-only failure is specific to transfer through globally indexed histogram coordinates. It does not mean that the stable 2-WL partition lacks structural information. Its perfect census discrimination proves the opposite.

The comparison does not establish a general expressive ordering between QuIC and folklore 2-WL. Both separate every tested cospectral pair, and no known pair in these censuses distinguishes one representation while tying the other.

The target set is limited to seven graph invariants. In particular, the experiment does not test whether 2-WL’s cospectral differences predict Wiener index, radius, or automorphism-group order, which are the targets used in the QuIC functional cospectral challenge.

The reported uncertainty reflects five graph folds. No paired significance analysis is reported for differences between the QuIC and 2-WL scores.

Finally, the terminology must remain explicit. The implemented method is **folklore 2-WL on ordered pairs**, not the weaker oblivious pair-refinement convention that is sometimes also called 2-WL.

#### Overall assessment

Folklore 2-WL is a strong and necessary classical baseline.

It confirms that the failures of constant-feature GNNs arise from the ordinary 1-WL limitation rather than from a general inability of classical graph representations to recover the tested structure.

The cumulative 2-WL representation nearly solves all four cycle counts at (n=16):

$$
1.000,\ 0.999,\ 0.993,\ 0.983,
$$

and it substantially outperforms QuIC on (C_6) and diameter. QuIC remains distinctly stronger on girth and closely matched on the first three cycle-count targets.

The stable-only arm provides a second important result: perfect graph discrimination and perfect cospectral separation do not guarantee transferable linear prediction. Shared intermediate refinement colors, rather than maximally specific final colors, carry the useful predictive structure.

The appropriate central claim is:

> Folklore 2-WL provides a strong higher-order classical baseline for the complete cubic censuses. Its cumulative color histograms distinguish every graph, separate every adjacency-cospectral pair, and nearly saturate cycle-count prediction, substantially exceeding QuIC on 6-cycles and diameter. QuIC remains stronger on girth and comparably effective on shorter cycles. The stable-only 2-WL representation further shows that maximal distinguishing power can coexist with no transferable linear accessibility.

### E5 - Exploration of linear vs non linear methods.

#### Experimental design

This experiment tests whether nonlinear readouts recover structural information that was inaccessible to the earlier linear probes.

It contains two separate analyses.

#### Probability-moment analysis

The first analysis compresses each sorted QuIC probability vector into the seven nonconstant power sums

$$
M_k(G)=\sum_z p_z(G)^k,
\qquad
k=2,\ldots,8.
$$

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

#### Full-vector nonlinear analysis

The second analysis applies RBF kernel ridge regression directly to the complete sorted QuIC probability vectors:

$$
\mathbf p(G)\in\mathbb R^{2^n}.
$$

The feature dimensions are:

$$
2^{14}=16{,}384,
\qquad
2^{16}=65{,}536.
$$

The nonlinear results are compared with the earlier full-vector linear ridge scores on seven targets:

* triangles;
* 4-cycles;
* 5-cycles;
* 6-cycles;
* girth;
* diameter;
* spectral gap.

Both experiments use the five frozen outer folds from the original E2 ridge-probe experiment. Kernel ridge hyperparameters are selected through five-fold inner cross-validation over:

$$
\alpha\in
{10^{-10},10^{-8},10^{-6},10^{-4},10^{-2},1},
$$

with three RBF bandwidths defined relative to the median squared feature distance.

#### Nonlinear prediction from probability power sums

##### (n=14)

| Target   |          Linear | RBF kernel ridge |   MLP ((64,64)) |
| -------- | --------------: | ---------------: | --------------: |
| 4-cycles | (0.997\pm0.000) |  (0.996\pm0.003) | (0.357\pm0.339) |
| 5-cycles | (0.106\pm0.048) |  (0.049\pm0.172) | (0.008\pm0.031) |
| 6-cycles | (0.198\pm0.072) |  (0.018\pm0.479) | (0.111\pm0.081) |

##### (n=16)

| Target   |          Linear | RBF kernel ridge |   MLP ((64,64)) |
| -------- | --------------: | ---------------: | --------------: |
| 4-cycles | (0.998\pm0.000) |  (0.995\pm0.007) | (0.798\pm0.013) |
| 5-cycles | (0.084\pm0.008) | (-0.169\pm0.534) | (0.024\pm0.014) |
| 6-cycles | (0.144\pm0.021) |  (0.168\pm0.018) | (0.102\pm0.021) |

#### Four-cycle control

The linear and kernel models recover 4-cycle count almost perfectly at both graph orders:

$$
R^2_{\mathrm{linear}}\approx0.998,
\qquad
R^2_{\mathrm{KRR}}\approx0.995.
$$

This confirms that the power-sum representation contains a strong and stable 4-cycle signal. It also shows that the RBF kernel implementation can recover target information when it is present in these features.

The MLP control is less satisfactory. It reaches only

$$
R^2=0.357\pm0.339
$$

at (n=14), despite the existence of an almost exact linear relationship, and improves to

$$
R^2=0.798\pm0.013
$$

at (n=16).

The MLP therefore does not provide a fully reliable positive control. Its poor (n=14) score is more indicative of optimization or regularization behavior than of missing information. The linear and kernel results should carry more weight in interpreting the moment experiment.

#### Five-cycle count

Five-cycle count remains essentially unrecoverable from the power sums through order eight.

At (n=14), the strongest score is the linear result:

$$
R^2=0.106\pm0.048.
$$

Neither nonlinear model improves on it:

$$
R^2_{\mathrm{KRR}}=0.049\pm0.172,
$$

$$
R^2_{\mathrm{MLP}}=0.008\pm0.031.
$$

At (n=16), the linear score falls to

$$
0.084\pm0.008,
$$

the MLP remains near zero, and kernel ridge becomes strongly unstable:

$$
-0.169\pm0.534.
$$

This should be contrasted with full-vector QuIC prediction:

$$
R^2=0.928
\quad\text{at }n=14,
$$

and

$$
R^2=0.982
\quad\text{at }n=16.
$$

The strong full-vector 5-cycle signal is therefore not reproduced by nonlinear functions learned from these seven low-order power sums.

The evidence supports the interpretation that 5-cycle information depends on finer structure in the sorted probability distribution rather than on the tested low-order moment coordinates alone.

#### Six-cycle count

The 6-cycle results show the same general pattern.

At (n=14), linear prediction reaches

$$
R^2=0.198\pm0.072.
$$

The MLP performs more weakly, while kernel ridge is highly unstable:

$$
R^2_{\mathrm{KRR}}=0.018\pm0.479.
$$

At (n=16), kernel ridge produces a small improvement over the linear probe:

$$
0.144\rightarrow0.168.
$$

The improvement is only

$$
\Delta R^2=0.024,
$$

and the MLP remains near

$$
R^2=0.102.
$$

The first seven nonconstant power sums therefore contain a small amount of 6-cycle information, but no tested nonlinear readout turns them into a strong predictor.

The difference from the full-vector scores remains substantial:

$$
R^2_{\mathrm{full}}=0.485
\quad\text{at }n=14,
$$

and

$$
R^2_{\mathrm{full}}=0.642
\quad\text{at }n=16.
$$

As with 5-cycles, much of the useful signal is lost when the full probability distribution is reduced to moments through order eight.

#### What the probability-moment experiment shows

The moment results support a clear empirical distinction:

$$
\boxed{
\text{low-order probability moments recover shallow cycle structure,
but not the deeper cycle signal present in the full vector}
}
$$

Four-cycle count is nearly exact from the moment coordinates. Five-cycle prediction remains near zero, while 6-cycle prediction remains weak under linear, kernel, and neural readouts.

This is stronger than the earlier linear-only result because two nonlinear estimator families fail to uncover a large hidden relationship.

It does not establish that no mathematical function of these moments can determine 5- or 6-cycle count. It establishes that no useful relationship is recovered by the tested models at the available sample sizes and under the tested regularization protocol.

#### Full-vector nonlinear results

##### (n=14)

| Target       |    Linear ridge | RBF kernel ridge | Difference |
| ------------ | --------------: | ---------------: | ---------: |
| Triangles    | (1.000\pm0.000) |  (1.000\pm0.000) |   (+0.000) |
| 4-cycles     | (0.998\pm0.002) |  (0.996\pm0.003) |   (-0.002) |
| 5-cycles     | (0.928\pm0.092) |  (0.950\pm0.049) |   (+0.022) |
| 6-cycles     | (0.485\pm0.326) |  (0.703\pm0.057) |   (+0.218) |
| Girth        | (0.993\pm0.014) |  (0.993\pm0.014) |   (+0.000) |
| Diameter     | (0.548\pm0.058) |  (0.526\pm0.051) |   (-0.022) |
| Spectral gap | (0.944\pm0.010) |  (0.952\pm0.005) |   (+0.008) |

##### (n=16)

| Target       |    Linear ridge | RBF kernel ridge | Difference |
| ------------ | --------------: | ---------------: | ---------: |
| Triangles    | (1.000\pm0.000) |  (0.999\pm0.001) |   (-0.001) |
| 4-cycles     | (1.000\pm0.000) |  (0.999\pm0.000) |   (-0.001) |
| 5-cycles     | (0.982\pm0.015) |  (0.945\pm0.045) |   (-0.037) |
| 6-cycles     | (0.642\pm0.122) |  (0.613\pm0.024) |   (-0.029) |
| Girth        | (0.999\pm0.003) |  (0.998\pm0.003) |   (-0.001) |
| Diameter     | (0.737\pm0.019) |  (0.699\pm0.028) |   (-0.038) |
| Spectral gap | (0.932\pm0.007) |  (0.937\pm0.003) |   (+0.005) |

#### Saturated targets

Triangles, 4-cycles, and girth remain essentially saturated under both readouts.

Kernel ridge cannot materially improve these targets because the linear model already obtains approximately perfect prediction. The small negative differences are within the scale expected from alternative regularization and finite-fold variation.

This confirms that nonlinear readout is unnecessary for the structural layers that are already strongly aligned with linear directions in QuIC space.

#### Five-cycle count

At (n=14), kernel ridge raises the mean score from

$$
0.928
$$

to

$$
0.950
$$

and reduces the fold standard deviation from

$$
0.092
$$

to

$$
0.049.
$$

This is a modest improvement in both average accuracy and stability.

The effect does not replicate at (n=16). On the larger census, kernel ridge performs worse:

$$
0.982\rightarrow0.945.
$$

The (n=14) result therefore does not support a general conclusion that 5-cycle information is encoded primarily through nonlinear full-vector geometry. The larger census instead indicates that the available 5-cycle signal is already very effectively accessed by the linear ridge probe.

#### Six-cycle count

The most substantial nonlinear improvement occurs for 6-cycle count at (n=14):

$$
R^2:
0.485\pm0.326
\rightarrow
0.703\pm0.057.
$$

The kernel model improves the mean by

$$
0.218
$$

and sharply reduces fold variance.

This could reflect a nonlinear relationship in the smaller census, better regularization of a difficult high-dimensional target, or both.

The effect does not replicate at (n=16):

$$
0.642\pm0.122
\rightarrow
0.613\pm0.024.
$$

The nonlinear model is more stable but slightly less accurate on average.

The (n=14) improvement should therefore be treated as a finite-census result rather than as evidence for a stable nonlinear 6-cycle layer. The larger dataset provides no indication that RBF kernel ridge unlocks a major source of 6-cycle information unavailable to the linear probe.

#### Diameter

Kernel ridge does not improve diameter prediction.

At (n=14),

$$
0.548\rightarrow0.526,
$$

and at (n=16),

$$
0.737\rightarrow0.699.
$$

The deficit is larger at the graph order where more training examples are available.

This suggests that the incomplete diameter prediction is not simply caused by the use of a linear readout. Under the tested RBF kernel, the full QuIC vector does not expose a stronger diameter signal.

This conclusion concerns the representation and readouts tested here. It does not establish an absolute information ceiling for all possible nonlinear estimators.

#### Spectral gap

Kernel ridge gives small improvements for spectral gap at both orders:

$$
0.944\rightarrow0.952
\quad\text{at }n=14,
$$

and

$$
0.932\rightarrow0.937
\quad\text{at }n=16.
$$

These gains are consistent in sign but small in magnitude. QuIC still does not match the exact linear accessibility of spectral gap from the sorted adjacency eigenvalues.

The result indicates minor nonlinear organization of spectral information, not a substantive change in the representation's spectral-gap capability.

#### Linear versus nonlinear accessibility

The full-vector results show no general advantage for the nonlinear kernel.

At (n=16), kernel ridge is weaker on six of the seven targets and improves only spectral gap by a negligible amount. The strongest QuIC results—triangles, 4-cycles, 5-cycles, and girth—are therefore not artifacts of restricting the readout to a linear model.

For the tested targets, the dominant structural content of the full QuIC vector is already organized in a form that ridge regression can access efficiently.

The nonlinear model occasionally changes finite-sample bias and variance, particularly for 6-cycles at (n=14), but it does not reveal a reproducible hidden layer of target information.

#### What the experiment establishes

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

#### Necessary qualifications

The code uses seven nonconstant probability power sums:

$$
k=2,\ldots,8.
$$

Descriptions such as “eight power sums” should be replaced by “power sums through order eight” or “seven nonconstant power sums.” The (k=1) power sum is the constant normalization condition

$$
\sum_z p_z=1.
$$

The moment experiment does not prove that no function of these power sums can recover 5- or 6-cycle count. Kernel ridge and finite-width MLPs are flexible estimators, but negative finite-sample performance is not a mathematical nonexistence result.

The MLP's weak performance on the 4-cycle control, particularly at (n=14), shows that its training procedure does not reliably recover even an available simple relationship. Its negative C5 and C6 results should therefore be treated as corroborating evidence rather than as a decisive test.

The power-sum features are standardized using the complete census before the outer folds are evaluated. In addition, the RBF bandwidth grid is anchored using the median distance over the complete dataset. Both operations use unlabeled test-fold feature information. This is a mild transductive leakage and should be replaced with fold-local scaling and outer-training-only bandwidth estimation in a strict cross-validation implementation.

The full-vector analysis tests one nonlinear family with a limited bandwidth and regularization grid. Failure of this RBF kernel to improve prediction does not establish the absolute nonlinear ceiling of the representation.

No paired foldwise significance analysis is reported. Differences such as

$$
+0.022,\quad +0.008,\quad -0.029
$$

should be interpreted descriptively. The (n=14) 6-cycle difference is larger, but its failure to replicate remains the more important result.

The reported MLP standard deviations summarize 15 seed-fold evaluations, whereas linear and kernel scores summarize five folds. Their uncertainty values are therefore not directly comparable.

Finally, all results use exact ideal probability vectors. They characterize representational accessibility rather than finite-shot sample complexity or hardware-level performance.

#### Overall assessment

The probability-moment experiment provides the more important result.

Four-cycle count remains nearly exact under both linear and nonlinear readouts, confirming that shallow-cycle information is present in the low-order moment coordinates. Five- and 6-cycle prediction remains weak across estimator families, while the complete QuIC vector predicts the same targets much more strongly.

The natural interpretation is that deeper cycle information depends on the detailed shape and ordering statistics of the probability spectrum rather than on a small collection of global power sums.

The full-vector nonlinear analysis is largely negative. RBF kernel ridge does not systematically improve upon linear ridge and performs worse on most targets in the larger (n=16) census. The (n=14) 6-cycle improvement is substantial but does not replicate.

The appropriate central claim is:

> Across the complete connected cubic-graph censuses at (n=14) and (n=16), the strong QuIC 5-cycle signal and the weaker 6-cycle signal cannot be reproduced from probability power sums through order eight using linear, RBF-kernel, or MLP readouts. Once the complete probability vector is retained, RBF kernel ridge provides no consistent advantage over linear ridge, indicating that most of the accessible structural information is already organized in approximately linear form.


### E6 - Irregular Graphs
#### Experimental design

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

$$
R_X(2.875)
$$

on every qubit, followed by one round of:

* (R_{ZZ}(2.0)) on each graph edge;
* a uniform (R_X(0.1)) mixer.

The encoder deliberately ignores vertex degree. This keeps the circuit map consistent with the cubic experiments and prevents nonregular graphs from receiving degree information as an explicit node feature.

For each target, four representations are evaluated:

1. sorted adjacency eigenvalues;
2. adjacency trace moments
   $$
   	ext{tr}(A^k),\qquad k=3,\ldots,8;
   $$
3. the full sorted QuIC probability vector;
4. QuIC concatenated with a rescaled eigenvalue block.

All analyses are performed separately within each fixed-degree-sequence stratum. Five frozen outer folds and nested ridge regularization are used.

The reported differences are:

$$
\Delta_{\mathrm{QuIC}} = R^2_{\mathrm{QuIC}} - \max(R^2_{\mathrm{eig}},R^2_{\mathrm{moments}}),
$$

and

$$
\Delta_{\mathrm{concat}} = R^2_{\mathrm{concat}} - \max(R^2_{\mathrm{eig}},R^2_{\mathrm{moments}}).
$$

#### Dataset construction and viability

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

$$
4.51\times10^{-17}
$$

and

$$
1.33\times10^{-15}.
$$

The results therefore correspond to the intended flat-encoder circuit.

#### Main results

#### S1: near-regular

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

#### S2: bimodal

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

#### S3: skewed

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

#### S4: hub

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

#### Equal-weight aggregate

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

#### Consistency controls

The classical controls behave as required.

For every graph,

$$
	ext{tr}(A^3)=6C_3.
$$

Therefore the moment probe obtains:

$$
R^2=1.000
$$

for triangle count in every stratum.

For general graphs,

$$
	ext{tr}(A^4)
=

8C_4
+
2\sum_v d_v^2
-------------

\sum_v d_v.
$$

Because the complete degree sequence is fixed within each stratum, both degree-dependent terms are constant. The moment probe therefore also obtains:

$$
R^2=1.000
$$

for 4-cycle count in every stratum.

The sorted-eigenvalue probe obtains:

$$
R^2=1.000
$$

for spectral gap in all four strata, as expected.

These rows validate the dataset, target computations, spectral features, and cross-validation pipeline.

They also demonstrate an important coordinate effect. The sorted eigenvalue representation reaches only approximately (0.96)–(0.99) on C3 and C4 despite containing the same spectral information. The moment coordinates expose the relevant power sums directly and make the relationships linear.

#### Five-cycle count

C5 is the primary live target because the simple cubic identity relating (	ext{tr}(A^5)) to C3 and C5 no longer applies on nonregular graphs.

The spectral baselines remain moderately strong but no longer exact:

$$
R^2_{\mathrm{moments}}
=

0.802,\ 0.716,\ 0.707,\ 0.625
$$

across S1 through S4.

The decline from S1 to S4 suggests that the moment coordinates become less sufficient as the degree distribution permits more heterogeneous local configurations. This is descriptive rather than a monotonic theorem, but the pattern is consistent across the selected strata.

QuIC alone does not retain the strong C5 accessibility observed on cubic graphs:

$$
R^2_{\mathrm{QuIC}}
=

-0.017,\ 0.284,\ -0.019,\ -0.050.
$$

Only the bimodal stratum contains a meaningful standalone signal.

The concatenated representation gives a more nuanced result.

For the two maximum-degree-4 strata:

$$
\Delta R^2_{\mathrm{concat}}
=

+0.061
\quad\text{and}\quad
+0.118.
$$

In S1, QuIC has essentially no standalone C5 accessibility but improves the eigenvalue representation enough to exceed the stronger moment baseline. This indicates conditional or complementary structure that is not useful in isolation.

In S2, QuIC has both a moderate standalone signal and a larger complementary contribution.

The result does not persist in the more degree-skewed strata:

$$
\Delta R^2_{\mathrm{concat}}
=

-0.020
\quad\text{and}\quad
-0.021.
$$

The aggregate gain is therefore only:

$$
+0.035.
$$

The defensible conclusion is that QuIC contributes limited complementary C5 information in two strata, but the effect is not robust across all four fixed-degree-sequence families.

#### Six-cycle count

The spectral moment probe remains moderately strong for C6:

$$
R^2=0.645\text{--}0.757.
$$

QuIC alone is near zero in three strata and reaches only:

$$
R^2=0.296
$$

in S2.

The concatenated representation fails to outperform the best spectral baseline in every stratum:

$$
\Delta R^2_{\mathrm{concat}}
=

-0.096,\ -0.018,\ -0.015,\ -0.046.
$$

There is therefore no evidence that the flat QuIC representation supplies useful additional C6 information beyond the tested spectral coordinates on these graph families.

This contrasts with the cubic residual experiment, where QuIC recovered part of the spectral residual associated with the C6–diamond decomposition. That effect does not transfer automatically to nonregular fixed-degree-sequence strata.

#### Metric targets

#### Girth

Girth has little variation within the strata, usually taking only the values three and four.

The best spectral scores range from approximately zero to (0.47). QuIC remains near zero in all four strata, and concatenation does not improve the best spectral result.

The near-perfect cubic girth accessibility therefore disappears under the flat nonregular experiment.

#### Diameter

Eigenvalue and moment probes obtain modest scores:

$$
R^2\approx0.18\text{--}0.37.
$$

QuIC is approximately uninformative:

$$
R^2=-0.093,\ 0.110,\ 0.019,\ -0.028.
$$

Concatenation reduces performance in every stratum.

#### Radius

Radius is poorly accessible from all tested representations. Spectral scores remain near zero, and QuIC scores are negative in all four strata.

The target also has limited spread, particularly in S1, so these values should be treated as evidence of no detected signal rather than a precise performance hierarchy.

#### Wiener index

The Wiener index is strongly linearly accessible from the spectral features:

$$
R^2_{\mathrm{moments}}
=

0.798\text{--}0.841.
$$

QuIC alone ranges from:

$$
0.075
$$

to

$$
0.409.
$$

The only positive concatenation difference is the small S2 gain:

$$
\Delta R^2=+0.019.
$$

This does not replicate across the other strata. The aggregate concatenated score remains below the aggregate moment score.

#### Spectral gap

The eigenvalue representation recovers spectral gap exactly, while QuIC obtains:

$$
R^2=
0.389,\ 0.595,\ 0.153,\ 0.167.
$$

These values show that the flat QuIC vector retains some adjacency-spectral information, especially in S2, but far less than it retained on the cubic census.

Adding the exact eigenvalue coordinate restores perfect performance, as expected.

#### Comparison with the cubic census

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

#### Interpretation

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

#### What the experiment establishes

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

#### Necessary qualifications

The four strata are sampled rather than exhaustively enumerated. Each stratum is generated from one degree-preserving swap chain. Canonical deduplication guarantees distinct graphs, but no mixing-time or autocorrelation analysis establishes that the 400 graphs are uniform or statistically independent samples from the realization space.

Only four hand-selected degree sequences at (n=14) are tested. The results should not be generalized to all nonregular graphs or larger graph orders.

The flat encoder is deliberately atypical for practical nonregular use. Degree-proportional encoding may restore substantial accessibility by supplying vertex-degree information. That arm is not evaluated here.

The concatenated representation contains QuIC plus eigenvalues, but not the adjacency moment block. Its score is nevertheless compared against the better of eigenvalues and moments. Positive (\Delta_{\mathrm{concat}}) is therefore conservative, but negative values do not directly establish that QuIC contains no information beyond the full spectral feature set. A cleaner complementarity test would concatenate QuIC with both spectral blocks or fit a cross-fitted residual model.

The run emits repeated ill-conditioned-matrix warnings during ridge fitting. The alpha grid extends to (10^{-14}), and the QuIC feature matrix has 16,384 columns but only 320 training graphs per outer fold. The main negative results are large enough to be qualitatively clear, but the exact QuIC and concatenated scores should be verified with a numerically stable solver or a safer regularization range.

The large S1 triangle variance,

$$
0.449\pm0.714,
$$

is a visible example of fold instability.

No paired statistical tests are reported for the fold-level differences. The C5 gains of (+0.061) and (+0.118) are descriptively meaningful, but their uncertainty should be evaluated directly before making inferential claims.

Finally, several metric targets have low within-stratum variance. In particular, girth is nearly binary and radius occupies a narrow range. Cross-validated (R^2) is correspondingly sensitive to fold composition.

#### Overall assessment

This experiment sharply limits the scope of the cubic results.

The flat QuIC circuit retains exceptional short-cycle accessibility on connected cubic graphs, but that structure largely disappears once the graph family becomes nonregular. Across four fixed-degree-sequence strata, QuIC alone is substantially weaker than the spectral baselines on every target and is approximately uninformative for C4, C5, C6, girth, diameter, and radius.

The only substantive positive result is conditional C5 complementarity in S1 and S2. In those strata, adding QuIC to the eigenvalue representation raises performance above the stronger moment baseline by (0.061) and (0.118). The effect does not survive in the skewed and hub strata.

The appropriate central claim is:

> The structural hierarchy observed for flat-start QuIC on cubic graphs is not robust to nonregular fixed-degree-sequence families. Without explicit degree encoding, QuIC loses most standalone linear accessibility to cycle and metric invariants, while classical spectral coordinates remain substantially stronger. QuIC contributes limited complementary C5 information in two maximum-degree-4 strata, but no consistent advantage appears across all four families.


### E6D — Degree-Encoding Ablation

#### Experimental design

This experiment tests whether explicit degree encoding restores the structural accessibility that the flat QuIC encoder lost on nonregular graphs.

The analysis uses the same 1,600 connected, nonisomorphic (n=14) graphs from E6, divided into four fixed-degree-sequence strata:

| Stratum          | Degree sequence                     | Maximum degree |
| ---------------- | ----------------------------------- | -------------: |
| S1: near-regular | ((4,4,3^{\times10},2,2))            |              4 |
| S2: bimodal      | ((4^{\times7},2^{\times7}))         |              4 |
| S3: skewed       | ((5,5,4,4,3^{\times6},2^{\times4})) |              5 |
| S4: hub          | ((6,4,4,3^{\times8},2,2,2))         |              6 |

Each stratum contains 400 graphs.

The graph instances, target values, cross-validation folds, spectral features, ridge probes, and circuit depth are identical to the flat-encoder experiment. The only changed component is the initial single-qubit encoding.

#### Flat encoder

Every qubit receives the same rotation:

$$
R_X(2.875).
$$

#### Degree encoder

Vertex (i) receives:

$$
R_X\left(
2.875\frac{d_i}{\Delta}
\right),
$$

where (d_i) is its degree and (\Delta) is the maximum degree within the graph.

The highest-degree vertices therefore receive the full (2.875) rotation, while lower-degree vertices receive proportionally smaller rotations.

Both encoders then use:

* (R_{ZZ}(2.0)) on every edge;
* a uniform (R_X(0.1)) mixer;
* one entangler–mixer repetition;
* the full sorted ideal probability vector.

The comparison evaluates nine targets:

* (C_3);
* (C_4);
* (C_5);
* (C_6);
* girth;
* diameter;
* radius;
* Wiener index;
* spectral gap.

Four probe columns are considered:

1. the strongest classical spectral baseline;
2. flat QuIC;
3. degree-encoded QuIC;
4. QuIC concatenated with the sorted eigenvalue vector.

Because the graph sets and folds are identical, the flat-to-degree differences are paired comparisons at the fold level.

#### Validation checks

The degree-encoded and flat datasets contain exactly the same canonical graph6 strings in the same order.

For every stratum:

* all 400 graph identities match;
* the stored degree-encoded vectors are sorted and normalized;
* the frozen five-fold splits exactly match the flat experiment;
* the eigenvalue and adjacency-moment scores reproduce the flat analysis to within (10^{-6});
* an independent Qiskit reconstruction of one vector per stratum matches the stored vector exactly to displayed precision.

The ablation therefore changes only the initial degree-dependent rotation.

#### Aggregate results

The aggregate values are equal-weight means over the four degree-sequence strata.

| Target       | Best spectral | Flat QuIC | Degree QuIC | Degree − flat | Flat concat. | Degree concat. | Degree − flat |
| ------------ | ------------: | --------: | ----------: | ------------: | -----------: | -------------: | ------------: |
| (C_3)        |         1.000 |     0.443 |       0.057 |      (-0.386) |        0.989 |          0.975 |      (-0.014) |
| (C_4)        |         1.000 |     0.085 |       0.031 |      (-0.054) |        0.964 |          0.920 |      (-0.044) |
| (C_5)        |         0.712 |     0.050 |    (-0.003) |      (-0.053) |        0.747 |          0.600 |      (-0.147) |
| (C_6)        |         0.691 |     0.053 |    (-0.005) |      (-0.058) |        0.647 |          0.560 |      (-0.087) |
| Girth        |         0.201 |  (-0.010) |    (-0.018) |      (-0.008) |        0.156 |          0.032 |      (-0.124) |
| Diameter     |         0.291 |     0.002 |       0.033 |      (+0.031) |        0.238 |          0.169 |      (-0.069) |
| Radius       |         0.064 |  (-0.045) |    (-0.029) |      (+0.016) |        0.006 |       (-0.020) |      (-0.026) |
| Wiener index |         0.820 |     0.191 |       0.085 |      (-0.106) |        0.793 |          0.691 |      (-0.102) |
| Spectral gap |         1.000 |     0.326 |       0.123 |      (-0.203) |        1.000 |          0.996 |      (-0.004) |

Explicit degree encoding does not restore the cubic structural hierarchy.

Across the four cycle-count targets, standalone degree-encoded QuIC performs worse than the flat encoder:

$$
\Delta R^2=
-0.386,\ -0.054,\ -0.053,\ -0.058.
$$

The degree-encoded representation is approximately uninformative for:

$$
C_4,\quad C_5,\quad C_6.
$$

It also reduces the QuIC contribution to Wiener index and spectral gap.

The only aggregate improvements occur for diameter and radius:

$$
+0.031
\quad\text{and}\quad
+0.016.
$$

Both degree-encoded scores remain near zero and far below the spectral baselines. These changes do not constitute a useful recovery of metric information.

#### S1: near-regular stratum

| Target       | Best spectral |        Flat QuIC |      Degree QuIC | Difference |     Flat concat. |   Degree concat. | Difference |
| ------------ | ------------: | ---------------: | ---------------: | ---------: | ---------------: | ---------------: | ---------: |
| (C_3)        |         1.000 |  (0.449\pm0.714) |  (0.260\pm0.080) |   (-0.189) |  (0.989\pm0.002) |  (0.982\pm0.004) |   (-0.007) |
| (C_4)        |         1.000 |  (0.095\pm0.048) |  (0.035\pm0.086) |   (-0.061) |  (0.967\pm0.006) |  (0.933\pm0.010) |   (-0.034) |
| (C_5)        |         0.802 | (-0.017\pm0.056) | (-0.015\pm0.014) |   (+0.001) |  (0.863\pm0.045) |  (0.759\pm0.066) |   (-0.104) |
| (C_6)        |         0.757 | (-0.021\pm0.012) | (-0.022\pm0.017) |   (-0.001) |  (0.661\pm0.058) |  (0.588\pm0.049) |   (-0.073) |
| Girth        |         0.468 |  (0.007\pm0.228) |  (0.015\pm0.033) |   (+0.008) |  (0.436\pm0.063) |  (0.252\pm0.051) |   (-0.184) |
| Diameter     |         0.372 | (-0.093\pm0.122) | (-0.003\pm0.011) |   (+0.090) |  (0.257\pm0.146) |  (0.241\pm0.032) |   (-0.016) |
| Radius       |         0.028 | (-0.064\pm0.077) | (-0.016\pm0.035) |   (+0.048) | (-0.033\pm0.018) | (-0.009\pm0.031) |   (+0.023) |
| Wiener index |         0.841 |  (0.184\pm0.147) |  (0.009\pm0.077) |   (-0.175) |  (0.754\pm0.083) |  (0.698\pm0.047) |   (-0.057) |
| Spectral gap |         1.000 |  (0.389\pm0.061) |  (0.072\pm0.051) |   (-0.317) |  (1.000\pm0.000) |  (0.996\pm0.001) |   (-0.004) |

The degree encoder reduces the extreme variance of the flat (C_3) probe:

$$
0.449\pm0.714
\rightarrow
0.260\pm0.080.
$$

It therefore stabilizes that cell numerically, but only by lowering its mean performance.

No cycle target improves materially. The flat encoder’s positive C5 concatenation result also disappears. The degree-encoded concatenation reaches:

$$
R^2=0.759,
$$

below the moment baseline:

$$
R^2=0.802.
$$

#### S2: bimodal stratum

| Target       | Best spectral |        Flat QuIC |      Degree QuIC | Difference |     Flat concat. |   Degree concat. | Difference |
| ------------ | ------------: | ---------------: | ---------------: | ---------: | ---------------: | ---------------: | ---------: |
| (C_3)        |         1.000 |  (0.991\pm0.001) |  (0.038\pm0.045) |   (-0.953) |  (0.991\pm0.002) |  (0.976\pm0.005) |   (-0.015) |
| (C_4)        |         1.000 |  (0.295\pm0.137) |  (0.072\pm0.074) |   (-0.223) |  (0.962\pm0.004) |  (0.922\pm0.014) |   (-0.041) |
| (C_5)        |         0.716 |  (0.284\pm0.135) |  (0.083\pm0.036) |   (-0.201) |  (0.834\pm0.031) |  (0.549\pm0.083) |   (-0.286) |
| (C_6)        |         0.710 |  (0.296\pm0.150) |  (0.068\pm0.090) |   (-0.228) |  (0.693\pm0.109) |  (0.631\pm0.064) |   (-0.062) |
| Girth        |         0.159 | (-0.014\pm0.044) | (-0.020\pm0.018) |   (-0.006) |  (0.140\pm0.097) | (-0.009\pm0.017) |   (-0.149) |
| Diameter     |         0.316 |  (0.110\pm0.052) |  (0.117\pm0.039) |   (+0.006) |  (0.284\pm0.118) |  (0.315\pm0.060) |   (+0.031) |
| Radius       |         0.008 | (-0.070\pm0.323) | (-0.056\pm0.201) |   (+0.014) | (-0.118\pm0.340) | (-0.024\pm0.214) |   (+0.094) |
| Wiener index |         0.813 |  (0.409\pm0.120) |  (0.238\pm0.063) |   (-0.171) |  (0.833\pm0.027) |  (0.783\pm0.038) |   (-0.050) |
| Spectral gap |         1.000 |  (0.595\pm0.123) |  (0.270\pm0.094) |   (-0.325) |  (1.000\pm0.000) |  (1.000\pm0.000) |   (-0.000) |

S2 produced the strongest flat-encoder results in E6. Degree encoding removes nearly all of that advantage.

The most dramatic change is triangle count:

$$
R^2:
0.991
\rightarrow
0.038.
$$

The C4–C6 scores also fall sharply.

The flat concatenated representation exceeded the strongest spectral C5 baseline:

$$
0.834>0.716.
$$

With degree encoding, the concatenated score falls to:

$$
0.549.
$$

Thus, the strongest positive complementarity result in the flat experiment does not survive the encoder change.

#### S3: skewed stratum

| Target       | Best spectral |        Flat QuIC |      Degree QuIC | Difference |    Flat concat. |   Degree concat. | Difference |
| ------------ | ------------: | ---------------: | ---------------: | ---------: | --------------: | ---------------: | ---------: |
| (C_3)        |         1.000 | (-0.047\pm0.042) | (-0.024\pm0.036) |   (+0.023) | (0.990\pm0.002) |  (0.968\pm0.007) |   (-0.022) |
| (C_4)        |         1.000 | (-0.018\pm0.025) |  (0.037\pm0.056) |   (+0.055) | (0.965\pm0.006) |  (0.901\pm0.016) |   (-0.063) |
| (C_5)        |         0.707 | (-0.019\pm0.017) | (-0.011\pm0.010) |   (+0.008) | (0.687\pm0.034) |  (0.575\pm0.014) |   (-0.112) |
| (C_6)        |         0.645 | (-0.023\pm0.019) | (-0.023\pm0.023) |   (-0.000) | (0.630\pm0.035) |  (0.477\pm0.058) |   (-0.152) |
| Girth        |         0.166 | (-0.017\pm0.028) | (-0.006\pm0.004) |   (+0.011) | (0.083\pm0.028) | (-0.006\pm0.004) |   (-0.089) |
| Diameter     |         0.262 |  (0.019\pm0.062) |  (0.053\pm0.034) |   (+0.034) | (0.249\pm0.051) |  (0.072\pm0.044) |   (-0.177) |
| Radius       |         0.095 | (-0.013\pm0.038) | (-0.018\pm0.020) |   (-0.006) | (0.071\pm0.054) | (-0.018\pm0.020) |   (-0.089) |
| Wiener index |         0.798 |  (0.097\pm0.049) |  (0.105\pm0.067) |   (+0.008) | (0.790\pm0.051) |  (0.602\pm0.048) |   (-0.188) |
| Spectral gap |         1.000 |  (0.153\pm0.128) |  (0.105\pm0.116) |   (-0.048) | (1.000\pm0.000) |  (0.994\pm0.001) |   (-0.006) |

The standalone differences in S3 are small because both encoders are approximately uninformative.

Degree encoding produces minor positive changes for C3, C4, C5, girth, diameter, and Wiener index, but none reaches a competitive score.

The concatenated representation becomes weaker for every target.

#### S4: hub stratum

| Target       | Best spectral |        Flat QuIC |      Degree QuIC | Difference |     Flat concat. |   Degree concat. | Difference |
| ------------ | ------------: | ---------------: | ---------------: | ---------: | ---------------: | ---------------: | ---------: |
| (C_3)        |         1.000 |  (0.378\pm0.161) | (-0.045\pm0.108) |   (-0.423) |  (0.987\pm0.004) |  (0.974\pm0.006) |   (-0.013) |
| (C_4)        |         1.000 | (-0.034\pm0.079) | (-0.020\pm0.030) |   (+0.014) |  (0.963\pm0.007) |  (0.924\pm0.012) |   (-0.039) |
| (C_5)        |         0.625 | (-0.050\pm0.057) | (-0.069\pm0.062) |   (-0.019) |  (0.603\pm0.068) |  (0.519\pm0.072) |   (-0.084) |
| (C_6)        |         0.651 | (-0.038\pm0.038) | (-0.043\pm0.031) |   (-0.005) |  (0.604\pm0.132) |  (0.543\pm0.083) |   (-0.061) |
| Girth        |         0.009 | (-0.017\pm0.020) | (-0.062\pm0.080) |   (-0.045) | (-0.036\pm0.203) | (-0.109\pm0.157) |   (-0.074) |
| Diameter     |         0.214 | (-0.028\pm0.021) | (-0.034\pm0.036) |   (-0.006) |  (0.164\pm0.080) |  (0.049\pm0.081) |   (-0.115) |
| Radius       |         0.125 | (-0.035\pm0.023) | (-0.026\pm0.019) |   (+0.010) |  (0.106\pm0.133) | (-0.029\pm0.038) |   (-0.134) |
| Wiener index |         0.827 |  (0.075\pm0.075) | (-0.012\pm0.106) |   (-0.087) |  (0.795\pm0.068) |  (0.680\pm0.092) |   (-0.115) |
| Spectral gap |         1.000 |  (0.167\pm0.080) |  (0.045\pm0.062) |   (-0.122) |  (1.000\pm0.000) |  (0.995\pm0.001) |   (-0.005) |

Degree encoding does not rescue the most heterogeneous stratum.

Standalone scores remain at or below zero for nearly every structural target, and the remaining flat C3 signal disappears:

$$
0.378
\rightarrow
-0.045.
$$

The degree-encoded concatenated representation is weaker than the flat concatenation on every target.

#### Cycle-count results

The central question was whether explicit degree rotations would restore cycle accessibility.

They do not.

#### Aggregate standalone QuIC

| Target |  Flat | Degree encoded |
| ------ | ----: | -------------: |
| (C_3)  | 0.443 |          0.057 |
| (C_4)  | 0.085 |          0.031 |
| (C_5)  | 0.050 |       (-0.003) |
| (C_6)  | 0.053 |       (-0.005) |

The cubic hierarchy:

$$
C_3\rightarrow C_4\rightarrow C_5
$$

does not reappear.

The degree encoder is not merely unable to recover the deeper-cycle targets. It also removes much of the limited triangle signal retained by the flat representation.

The result is especially clear in the two strata where the flat encoder had meaningful cycle accessibility:

* S2 (C_3):
  $$
  0.991\rightarrow0.038;
  $$
* S2 (C_5):
  $$
  0.284\rightarrow0.083;
  $$
* S2 (C_6):
  $$
  0.296\rightarrow0.068;
  $$
* S4 (C_3):
  $$
  0.378\rightarrow-0.045.
  $$

Explicit degree information therefore does not provide the missing ingredient needed to transfer the cubic cycle geometry.

#### Complementarity with the adjacency spectrum

The flat experiment contained two positive C5 concatenation results:

$$
\Delta R^2_{\mathrm{concat}}
=

+0.061
\quad\text{in S1},
$$

and

$$
+0.118
\quad\text{in S2}.
$$

Neither persists under degree encoding.

For S1:

$$
R^2_{\mathrm{degree+eig}}=0.759
<
R^2_{\mathrm{moments}}=0.802.
$$

For S2:

$$
R^2_{\mathrm{degree+eig}}=0.549
<
R^2_{\mathrm{moments}}=0.716.
$$

Across all strata and targets, the degree-encoded concatenated representation generally performs worse than the flat concatenated representation.

The aggregate concatenation losses are largest for:

* C5:
  $$
  -0.147;
  $$
* girth:
  $$
  -0.124;
  $$
* Wiener index:
  $$
  -0.102;
  $$
* C6:
  $$
  -0.087.
  $$

Degree encoding therefore weakens not only standalone linear accessibility but also the useful interaction between QuIC and the spectral coordinates.

#### Degree-heterogeneity gradient

The flat experiment suggested that the representation was healthiest in the two (\Delta=4) strata and largely inactive in the more heterogeneous (\Delta=5) and (\Delta=6) strata.

Degree encoding does not invert that pattern.

The (\Delta=4) strata retain slightly more nonzero signal than S3 and S4 on some targets, but their strongest flat effects are substantially reduced. The result is therefore not a successful flattening of the degree-heterogeneity gradient.

Instead, degree encoding makes the representation weak across nearly all four strata.

The distinction between low- and high-maximum-degree families becomes less visible largely because the useful signal in S1 and S2 has been removed, not because S3 and S4 have improved.

#### Interpretation

The negative result is informative because the degree encoder was a natural proposed explanation for the failure of flat QuIC on nonregular graphs.

The cubic experiments use degree-proportional encoding, but all cubic vertices have degree three. The encoder is therefore uniform:

$$
R_X(2.875)
$$

on every qubit.

It was plausible that nonregular graphs failed under the flat encoder because vertices of different degrees received identical initial rotations.

The ablation rejects that simple explanation.

Within every E6 stratum, the degree multiset is already fixed. Explicit degree encoding therefore does not add graph-level degree-sequence information. It changes how degree roles are distributed through the circuit and how those roles interact with the graph topology.

The resulting probability geometry is generally less aligned with the tested graph invariants.

One plausible interpretation is that the uniform initialization creates a comparatively clean topology-only interference pattern. Degree-dependent rotations introduce additional local heterogeneity that is not aligned with the dominant cycle and metric directions. Once the output probabilities are sorted, that heterogeneity may disperse rather than clarify the structural signal.

This interpretation is consistent with the results but is not directly established by the experiment. The causal statement supported by the ablation is narrower:

> Replacing the uniform encoder with the canonical degree-proportional encoder does not restore linear structural accessibility on these fixed-degree-sequence nonregular graph families and generally reduces it.

#### What the experiment establishes

The completed ablation supports five conclusions.

1. **Degree encoding does not restore the cubic QuIC hierarchy on nonregular graphs.**
   Cycle-count scores remain near zero and generally decline relative to the flat encoder.

2. **The strongest flat effects are removed rather than generalized.**
   S2 triangle prediction falls from (0.991) to (0.038).

3. **The flat C5 complementarity does not survive.**
   The positive S1 and S2 concatenation gains disappear under degree encoding.

4. **The degree-heterogeneity gradient is not repaired.**
   The higher-degree strata do not improve, while the healthier lower-degree strata become weaker.

5. **The flat encoder is the stronger of the two tested encoders for these strata.**
   It retains more standalone and complementary structural information despite ignoring degree explicitly.

The result therefore rules out the simplest proposed repair for E6.

#### Necessary qualifications

The experiment compares only two encoder choices:

* a uniform (R_X(2.875)) encoder;
* a linear degree-proportional encoder normalized by maximum degree.

Failure of the proportional encoder does not imply that all attribute-aware encoders will fail.

Alternative constructions could include:

* centered degree rotations;
* nonlinear degree maps;
* separately optimized feature channels;
* degree-dependent phase rotations;
* repeated data reuploading;
* or jointly encoded degree and topology features.

No circuit parameters are retuned after changing the encoder. This is desirable for a controlled ablation, but it means the canonical entangler and mixer angles may be poorly matched to the new degree-dependent initialization.

The graph families remain limited to four sampled fixed-degree-sequence strata at (n=14). The result does not establish behavior across all nonregular graphs.

The probes measure linear accessibility from exact sorted probability vectors. A different nonlinear readout could recover information that ridge regression does not expose, although the earlier E5 analysis found no consistent nonlinear advantage on the cubic vectors.

The ridge grid extends to extremely small regularization values in a regime with 16,384 features and 320 training graphs per fold. Ill-conditioning warnings occurred in the original flat analysis. The large negative encoder differences are unlikely to be explained entirely by numerical instability, but exact small differences should be treated cautiously.

No paired significance tests are reported for the foldwise flat-to-degree changes. The largest effects, such as the S2 C3 decline of (0.953), are descriptively unambiguous. Smaller changes near zero should not be overinterpreted.

Finally, the result concerns predictive accessibility, not injectivity. The degree-encoded vectors may still distinguish graphs even when the tested invariants are not linearly recoverable.

#### Overall assessment

The degree-encoding ablation produces a clear negative result.

Explicitly rotating each qubit according to vertex degree does not recover the strong structural organization observed on cubic graphs. Instead, it reduces aggregate cycle-count accessibility, weakens spectral complementarity, and removes the strongest positive cells from the flat nonregular experiment.

The result changes the interpretation of E6. The flat encoder did not fail merely because it omitted vertex degree. The cubic behavior appears to depend more fundamentally on the regular graph family and the geometry induced by uniform initialization.

The appropriate central claim is:

> On four fixed-degree-sequence nonregular graph strata, replacing QuIC’s uniform initialization with the canonical degree-proportional encoder does not restore the cubic structural hierarchy. Degree encoding reduces aggregate accessibility for all four cycle-count targets, eliminates the flat encoder’s C5 complementarity with spectral features, and leaves the higher-heterogeneity strata near the prediction floor. The failure of flat QuIC off the regular manifold therefore cannot be explained simply by missing degree information.

### E6R — Circuit-Depth Ablation

#### Experimental design

This experiment tests whether increasing QuIC circuit depth restores the structural accessibility lost on nonregular graph families.

The analysis uses the same 1,600 connected, nonisomorphic (n=14) graphs introduced in E6, divided into four fixed-degree-sequence strata:

| Stratum          | Degree sequence                     | Maximum degree |
| ---------------- | ----------------------------------- | -------------: |
| S1: near-regular | ((4,4,3^{\times10},2,2))            |              4 |
| S2: bimodal      | ((4^{\times7},2^{\times7}))         |              4 |
| S3: skewed       | ((5,5,4,4,3^{\times6},2^{\times4})) |              5 |
| S4: hub          | ((6,4,4,3^{\times8},2,2,2))         |              6 |

Each stratum contains 400 graphs.

The graph instances, targets, cross-validation folds, spectral features, encoder, gate angles, and probe protocol are identical to the original flat-encoder E6 experiment. The only changed variable is the number of entangler–mixer repetitions.

##### One-repetition circuit

> $$
\text{Encoder}
\rightarrow
R_{ZZ}(2.0)
\rightarrow
R_X(0.1).
$$

##### Two-repetition circuit

> $$
\text{Encoder}
\rightarrow
R_{ZZ}(2.0)
\rightarrow
R_X(0.1)
\rightarrow
R_{ZZ}(2.0)
\rightarrow
R_X(0.1).
$

Both arms use the flat initialization

> $$
R_X(2.875)
$$

on every qubit.

The two-repetition circuit is not equivalent to simply doubling either gate angle. The second entangler acts on a state already transformed by the first mixer, creating a genuinely deeper interference process.

Nine graph targets are evaluated:

* (C_3);
* (C_4);
* (C_5);
* (C_6);
* girth;
* diameter;
* radius;
* Wiener index;
* spectral gap.

The experiment addresses three prespecified questions:

1. Does greater depth improve cycle-count accessibility, particularly (C_5)?
2. Does the original maximum-degree gradient persist?
3. Do the positive C5 concatenation results in S1 and S2 persist or strengthen?

#### Validation checks

The comparison is exactly paired at the graph and fold levels.

For every stratum:

* all 400 graph6 identifiers match the one-repetition dataset;
* graph ordering is identical;
* targets are identical;
* the five frozen folds are identical;
* the two-repetition vectors are sorted and normalized;
* independently reconstructed Qiskit vectors match the stored vectors exactly to displayed precision.

The eigenvalue and adjacency-moment probes are recomputed and asserted to match the original E6 fold scores within:

> $$
10^{-6}.
$$

The classical controls also retain their expected identities:

> $$
R^2_{\mathrm{moments}}=1.000
$$

for (C_3) and (C_4), and

> $$
R^2_{\mathrm{eig}}=1.000
$$

for spectral gap.

The resulting differences therefore isolate circuit depth rather than graph selection, fold composition, or classical-feature drift.

#### Aggregate results

The aggregate values are equal-weight means over the four degree-sequence strata rather than a pooled regression over all 1,600 graphs.

| Target       | Best spectral | QuIC, 1 rep. | QuIC, 2 reps. | Difference | Concat., 1 rep. | Concat., 2 reps. | Difference |
| ------------ | ------------: | -----------: | ------------: | ---------: | --------------: | ---------------: | ---------: |
| (C_3)        |         1.000 |        0.443 |         0.553 |   (+0.110) |           0.989 |            0.990 |   (+0.001) |
| (C_4)        |         1.000 |        0.085 |         0.064 |   (-0.021) |           0.964 |            0.964 |   (-0.000) |
| (C_5)        |         0.712 |        0.050 |         0.066 |   (+0.016) |           0.747 |            0.733 |   (-0.014) |
| (C_6)        |         0.691 |        0.053 |         0.047 |   (-0.006) |           0.647 |            0.653 |   (+0.006) |
| Girth        |         0.201 |     (-0.010) |      (-0.009) |   (+0.002) |           0.156 |            0.167 |   (+0.011) |
| Diameter     |         0.291 |        0.002 |         0.046 |   (+0.044) |           0.238 |            0.252 |   (+0.014) |
| Radius       |         0.064 |     (-0.045) |      (-0.043) |   (+0.002) |           0.006 |         (-0.026) |   (-0.033) |
| Wiener index |         0.820 |        0.191 |         0.088 |   (-0.103) |           0.793 |            0.801 |   (+0.008) |
| Spectral gap |         1.000 |        0.326 |         0.236 |   (-0.090) |           1.000 |            1.000 |   (-0.000) |

The second repetition does not broadly restore structural accessibility.

The largest aggregate standalone improvement is for triangle count:

> $$
0.443\rightarrow0.553.
$$

Diameter also improves modestly:

> $$
0.002\rightarrow0.046.
$$

The remaining changes are small or negative. In particular:

> $$
C_4:
0.085\rightarrow0.064,
$$

> $$
C_5:
0.050\rightarrow0.066,
$$

and

> $$
C_6:
0.053\rightarrow0.047.
$$

The deeper circuit therefore does not recover the cubic hierarchy for (C_4), (C_5), or (C_6).

#### S1: near-regular stratum

| Target       | Best spectral |     QuIC, 1 rep. |    QuIC, 2 reps. | Difference |  Concat., 1 rep. | Concat., 2 reps. | Difference |
| ------------ | ------------: | ---------------: | ---------------: | ---------: | ---------------: | ---------------: | ---------: |
| (C_3)        |         1.000 |  (0.449\pm0.714) |  (0.729\pm0.176) |   (+0.280) |  (0.989\pm0.002) |  (0.989\pm0.002) |   (-0.000) |
| (C_4)        |         1.000 |  (0.095\pm0.048) |  (0.053\pm0.105) |   (-0.042) |  (0.967\pm0.006) |  (0.967\pm0.005) |   (-0.000) |
| (C_5)        |         0.802 | (-0.017\pm0.056) |  (0.029\pm0.068) |   (+0.045) |  (0.863\pm0.045) |  (0.776\pm0.120) |   (-0.087) |
| (C_6)        |         0.757 | (-0.021\pm0.012) | (-0.032\pm0.034) |   (-0.011) |  (0.661\pm0.058) |  (0.657\pm0.056) |   (-0.004) |
| Girth        |         0.468 |  (0.007\pm0.228) | (-0.093\pm0.469) |   (-0.099) |  (0.436\pm0.063) |  (0.417\pm0.069) |   (-0.019) |
| Diameter     |         0.372 | (-0.093\pm0.122) | (-0.007\pm0.007) |   (+0.086) |  (0.257\pm0.146) |  (0.339\pm0.057) |   (+0.082) |
| Radius       |         0.028 | (-0.064\pm0.077) | (-0.020\pm0.010) |   (+0.044) | (-0.033\pm0.018) | (-0.041\pm0.026) |   (-0.008) |
| Wiener index |         0.841 |  (0.184\pm0.147) | (-0.359\pm1.080) |   (-0.543) |  (0.754\pm0.083) |  (0.785\pm0.053) |   (+0.031) |
| Spectral gap |         1.000 |  (0.389\pm0.061) |  (0.133\pm0.489) |   (-0.256) |  (1.000\pm0.000) |  (1.000\pm0.000) |   (+0.000) |

The main positive result in S1 is triangle count:

$$
R^2:
0.449\rightarrow0.729.
$$

The large one-repetition fold variance also falls substantially:

$$
0.714\rightarrow0.176.
$$

Thus, greater depth makes the S1 triangle coordinate both stronger and more stable.

This improvement does not extend to the deeper cycle targets. (C_4) declines, (C_5) remains near zero, and (C_6) remains below the prediction floor.

The original positive C5 concatenation result also disappears. At one repetition:

$$
R^2_{\mathrm{concat}}=0.863

>

R^2_{\mathrm{moments}}=0.802.
$$

At two repetitions:

$$
R^2_{\mathrm{concat}}=0.776
<
0.802.
$$

The S1 Wiener and spectral-gap standalone results are highly unstable. Their large fold standard deviations indicate that the corresponding mean changes should not be treated as reliable structural effects.

#### S2: bimodal stratum

| Target       | Best spectral |     QuIC, 1 rep. |    QuIC, 2 reps. | Difference |  Concat., 1 rep. | Concat., 2 reps. | Difference |
| ------------ | ------------: | ---------------: | ---------------: | ---------: | ---------------: | ---------------: | ---------: |
| (C_3)        |         1.000 |  (0.991\pm0.001) |  (0.998\pm0.001) |   (+0.007) |  (0.991\pm0.002) |  (0.996\pm0.001) |   (+0.005) |
| (C_4)        |         1.000 |  (0.295\pm0.137) |  (0.317\pm0.233) |   (+0.022) |  (0.962\pm0.004) |  (0.962\pm0.005) |   (-0.000) |
| (C_5)        |         0.716 |  (0.284\pm0.135) |  (0.302\pm0.061) |   (+0.018) |  (0.834\pm0.031) |  (0.879\pm0.023) |   (+0.045) |
| (C_6)        |         0.710 |  (0.296\pm0.150) |  (0.313\pm0.101) |   (+0.018) |  (0.693\pm0.109) |  (0.746\pm0.075) |   (+0.053) |
| Girth        |         0.159 | (-0.014\pm0.044) |  (0.132\pm0.280) |   (+0.145) |  (0.140\pm0.097) |  (0.248\pm0.152) |   (+0.108) |
| Diameter     |         0.316 |  (0.110\pm0.052) |  (0.198\pm0.039) |   (+0.088) |  (0.284\pm0.118) |  (0.291\pm0.106) |   (+0.008) |
| Radius       |         0.008 | (-0.070\pm0.323) | (-0.112\pm0.345) |   (-0.042) | (-0.118\pm0.340) | (-0.205\pm0.315) |   (-0.086) |
| Wiener index |         0.813 |  (0.409\pm0.120) |  (0.536\pm0.079) |   (+0.127) |  (0.833\pm0.027) |  (0.829\pm0.036) |   (-0.004) |
| Spectral gap |         1.000 |  (0.595\pm0.123) |  (0.679\pm0.085) |   (+0.084) |  (1.000\pm0.000) |  (1.000\pm0.000) |   (-0.000) |

S2 remains the healthiest nonregular stratum.

Two repetitions improve every standalone target except radius. The largest stable improvements occur for:

* diameter:
  $$
  0.110\rightarrow0.198;
  $$
* Wiener index:
  $$
  0.409\rightarrow0.536;
  $$
* spectral gap:
  $$
  0.595\rightarrow0.679.
  $$

The standalone cycle improvements are smaller:

$$
C_5:
0.284\rightarrow0.302,
$$

and

$$
C_6:
0.296\rightarrow0.313.
$$

The most important result is the C5 concatenation:

$$
R^2_{\mathrm{concat}}
=====================

0.879\pm0.023.
$$

This exceeds the strongest spectral baseline:

$$
R^2_{\mathrm{moments}}
======================

0.716
$$

by:

$$
\Delta R^2=+0.163.
$$

The corresponding one-repetition advantage was:

$$
+0.118.
$$

Greater depth therefore strengthens the C5 complementarity in S2.

The two-repetition concatenation also exceeds the strongest spectral baseline for:

$$
C_6:
0.746>0.710,
$$

and nominally for:

$$
\text{girth}:
0.248>0.159,
$$

and

$$
\text{Wiener index}:
0.829>0.813.
$$

The C6 gain is modest, while the girth estimate has substantial fold variance. C5 remains the clearest positive complementarity result.

#### S3: skewed stratum

| Target       | Best spectral |     QuIC, 1 rep. |    QuIC, 2 reps. | Difference | Concat., 1 rep. | Concat., 2 reps. | Difference |
| ------------ | ------------: | ---------------: | ---------------: | ---------: | --------------: | ---------------: | ---------: |
| (C_3)        |         1.000 | (-0.047\pm0.042) | (-0.014\pm0.030) |   (+0.033) | (0.990\pm0.002) |  (0.990\pm0.002) |   (-0.000) |
| (C_4)        |         1.000 | (-0.018\pm0.025) | (-0.018\pm0.077) |   (+0.000) | (0.965\pm0.006) |  (0.964\pm0.005) |   (-0.001) |
| (C_5)        |         0.707 | (-0.019\pm0.017) | (-0.019\pm0.017) |   (-0.001) | (0.687\pm0.034) |  (0.684\pm0.033) |   (-0.004) |
| (C_6)        |         0.645 | (-0.023\pm0.019) | (-0.017\pm0.022) |   (+0.006) | (0.630\pm0.035) |  (0.608\pm0.045) |   (-0.022) |
| Girth        |         0.166 | (-0.017\pm0.028) | (-0.010\pm0.012) |   (+0.007) | (0.083\pm0.028) |  (0.068\pm0.013) |   (-0.015) |
| Diameter     |         0.262 |  (0.019\pm0.062) |  (0.027\pm0.079) |   (+0.008) | (0.249\pm0.051) |  (0.214\pm0.056) |   (-0.034) |
| Radius       |         0.095 | (-0.013\pm0.038) | (-0.015\pm0.023) |   (-0.003) | (0.071\pm0.054) |  (0.059\pm0.023) |   (-0.012) |
| Wiener index |         0.798 |  (0.097\pm0.049) |  (0.116\pm0.079) |   (+0.019) | (0.790\pm0.051) |  (0.791\pm0.048) |   (+0.001) |
| Spectral gap |         1.000 |  (0.153\pm0.128) |  (0.150\pm0.130) |   (-0.003) | (1.000\pm0.000) |  (1.000\pm0.000) |   (+0.000) |

Depth has almost no effect in S3.

Standalone QuIC remains near zero for all four cycle counts, girth, diameter, and radius. The small positive changes do not produce useful accessibility.

The concatenated representation is also nearly unchanged or slightly weaker.

This stratum therefore remains effectively inactive under both tested depths.

#### S4: hub stratum

| Target       | Best spectral |     QuIC, 1 rep. |    QuIC, 2 reps. | Difference |  Concat., 1 rep. | Concat., 2 reps. | Difference |
| ------------ | ------------: | ---------------: | ---------------: | ---------: | ---------------: | ---------------: | ---------: |
| (C_3)        |         1.000 |  (0.378\pm0.161) |  (0.498\pm0.134) |   (+0.120) |  (0.987\pm0.004) |  (0.986\pm0.004) |   (-0.000) |
| (C_4)        |         1.000 | (-0.034\pm0.079) | (-0.097\pm0.116) |   (-0.063) |  (0.963\pm0.007) |  (0.963\pm0.007) |   (+0.001) |
| (C_5)        |         0.625 | (-0.050\pm0.057) | (-0.047\pm0.059) |   (+0.003) |  (0.603\pm0.068) |  (0.592\pm0.069) |   (-0.011) |
| (C_6)        |         0.651 | (-0.038\pm0.038) | (-0.075\pm0.070) |   (-0.037) |  (0.604\pm0.132) |  (0.600\pm0.113) |   (-0.004) |
| Girth        |         0.009 | (-0.017\pm0.020) | (-0.063\pm0.058) |   (-0.046) | (-0.036\pm0.203) | (-0.064\pm0.228) |   (-0.028) |
| Diameter     |         0.214 | (-0.028\pm0.021) | (-0.032\pm0.027) |   (-0.004) |  (0.164\pm0.080) |  (0.164\pm0.079) |   (+0.000) |
| Radius       |         0.125 | (-0.035\pm0.023) | (-0.026\pm0.017) |   (+0.009) |  (0.106\pm0.133) |  (0.081\pm0.151) |   (-0.025) |
| Wiener index |         0.827 |  (0.075\pm0.075) |  (0.060\pm0.103) |   (-0.014) |  (0.795\pm0.068) |  (0.798\pm0.070) |   (+0.003) |
| Spectral gap |         1.000 |  (0.167\pm0.080) | (-0.017\pm0.081) |   (-0.184) |  (1.000\pm0.000) |  (1.000\pm0.000) |   (+0.000) |

S4 gains a stronger triangle coordinate:

$$
0.378\rightarrow0.498.
$$

No corresponding improvement appears for (C_4), (C_5), or (C_6).

Spectral-gap accessibility declines to the prediction floor, and the metric targets remain approximately uninformative.

Greater depth therefore strengthens one shallow motif coordinate without repairing the broader structural collapse.

## Cycle-count accessibility

The aggregate cycle results are:

| Target | One repetition | Two repetitions | Difference |
| ------ | -------------: | --------------: | ---------: |
| (C_3)  |          0.443 |           0.553 |   (+0.110) |
| (C_4)  |          0.085 |           0.064 |   (-0.021) |
| (C_5)  |          0.050 |           0.066 |   (+0.016) |
| (C_6)  |          0.053 |           0.047 |   (-0.006) |

Depth selectively improves triangle accessibility but does not move the deeper-cycle targets away from the aggregate prediction floor.

This is important because (C_5) was the primary live target. Its aggregate gain is only:

$$
+0.016.
$$

The improvement is concentrated in S2 and, to a smaller extent, S1. S3 and S4 remain inactive.

The strong cubic hierarchy therefore cannot be recovered merely by adding a second identical entangler–mixer block.

#### Maximum-degree gradient

The original flat E6 experiment showed a pronounced degree-heterogeneity pattern:

* S1 and especially S2 retained some useful QuIC structure;
* S3 and S4 were largely inactive.

That pattern persists under greater depth.

##### Maximum-degree-4 strata

S1 gains stronger triangle accessibility, while S2 improves across several targets and retains the strongest C5 result.

##### Maximum-degree-5 stratum

S3 remains near zero across nearly every standalone target.

##### Maximum-degree-6 stratum

S4 retains a moderate triangle signal but remains near zero on the other cycle and metric targets.

The gradient therefore neither inverts nor disappears. Greater depth improves selected cells inside the healthier strata but does not make the more heterogeneous strata competitive.

The broad ordering remains:

$$
\boxed{
\Delta=4
\text{ strata}
;>;
\Delta=5,6
\text{ strata}
}
$$

for useful standalone structural accessibility.

#### Spectral complementarity

The most important positive E6 result was the C5 improvement obtained by concatenating QuIC with the adjacency eigenvalues.

At one repetition:

$$
\Delta R^2_{\mathrm{concat}}
============================

+0.061
$$

in S1 and:

$$
+0.118
$$

in S2.

At two repetitions, the result separates by stratum.

##### S1

The complementarity disappears:

$$
0.776<0.802.
$$

### S2

The complementarity strengthens:

$$
0.879-0.716
===========

+0.163.
$$

The two-repetition S2 representation also produces smaller positive margins for C6 and Wiener index.

The aggregate C5 concatenation score nevertheless declines:

$$
0.747\rightarrow0.733.
$$

Thus, greater depth does not produce general spectral complementarity. It concentrates a stronger complementary signal in the bimodal stratum while removing the corresponding result from the near-regular stratum.

The S2 C5 result is real and substantial within that family, but it is not robust across degree-sequence strata.

## Metric and spectral targets

Depth produces modest standalone improvements for diameter:

$$
0.002\rightarrow0.046
$$

in the aggregate.

This is driven primarily by S1 and S2. The resulting scores remain below the spectral baselines and do not indicate strong metric accessibility.

Wiener index improves in S2:

$$
0.409\rightarrow0.536,
$$

but the aggregate score falls because of the unstable S1 result.

Spectral-gap accessibility also improves in S2 but declines in S1 and S4, yielding an aggregate reduction:

$$
0.326\rightarrow0.236.
$$

The effects of depth are therefore family-specific rather than consistently beneficial.

#### Interpretation

The experiment rules out insufficient one-layer depth as a complete explanation for QuIC’s failure on nonregular graphs.

A second entangler–mixer repetition changes the representation meaningfully. It improves triangle accessibility in several strata and strengthens C5 complementarity in S2. The circuit is therefore not simply saturated after one repetition.

However, these changes do not produce a broad restoration of the cubic geometry.

The deeper cycle targets remain near zero in the aggregate, the high-heterogeneity strata remain inactive, and the positive complementarity remains confined to one degree-sequence family.

A plausible interpretation is that additional interference amplifies structural directions already present in a favorable graph family but does not create a common topology coordinate across heterogeneous local degree roles.

The supported causal conclusion is narrower:

> Increasing the flat QuIC circuit from one to two entangler–mixer repetitions selectively strengthens some existing signals, especially triangles and S2 C5 complementarity, but does not restore general structural accessibility on nonregular fixed-degree-sequence graphs.

#### What the experiment establishes

The completed depth ablation supports six conclusions.

1. **A second repetition does not restore the cubic hierarchy.**
   Aggregate (C_4), (C_5), and (C_6) accessibility remains near zero.

2. **Triangle accessibility improves.**
   Aggregate (C_3) rises from (0.443) to (0.553), with clear gains in S1 and S4.

3. **The maximum-degree gradient persists.**
   S1 and S2 remain healthier than S3 and S4.

4. **C5 complementarity becomes concentrated in S2.**
   The S2 concatenated score rises to (0.879), exceeding the spectral baseline by (0.163).

5. **The S1 C5 complementarity disappears.**
   The positive one-repetition result does not survive greater depth.

6. **Depth produces selective rather than general improvement.**
   Some target–stratum cells improve, but the aggregate representation remains substantially weaker than the classical spectral baselines.

Together with E6D, the result shows that neither the canonical degree encoder nor one additional circuit repetition repairs the off-regularity collapse.

#### Necessary qualifications

The experiment evaluates only:

$$
\text{reps}=1
\quad\text{and}\quad
\text{reps}=2.
$$

Failure at two repetitions does not imply that all deeper circuits will behave similarly.

Only the flat encoder is tested at two repetitions. The interaction between degree encoding and additional depth remains unmeasured.

The circuit angles are not retuned after increasing depth. This preserves a clean ablation but may disadvantage the deeper circuit if its optimal angles differ from those of the one-repetition model.

The analysis measures linear accessibility from exact sorted probability vectors. Nonlinear readouts could expose additional information, although the earlier nonlinear-readout experiment found no consistent improvement on the cubic representation.

The QuIC feature matrices contain 16,384 coordinates with only 320 training graphs per outer fold. The alpha grid extends to:

$$
10^{-14}.
$$

Several cells exhibit substantial fold instability, most visibly:

$$
R^2=-0.359\pm1.080
$$

for S1 Wiener index. Such cells should not be interpreted from their means alone.

No paired statistical tests are reported for the fold-level one- versus two-repetition differences. Large and stable changes are descriptively meaningful, while differences of a few hundredths should be treated cautiously.

The concatenated representation rescales the eigenvalue block to match the QuIC block’s training-fold RMS. Because the QuIC RMS changes with circuit depth, the effective spectral scaling also changes between arms. Small concatenation differences may therefore reflect feature-block scaling as well as new complementary information.

The four degree-sequence strata are sampled graph families at (n=14), not exhaustive nonregular censuses. The findings should not be generalized to all nonregular graphs.

All results use ideal probabilities. E7S shows that much of QuIC’s exact structural accessibility requires very large shot budgets, so these depth effects should not be interpreted as immediately hardware-accessible.

Finally, several notebook comments still refer to the depth dataset as degree encoded. The metadata assertions, graph checks, and Qiskit reconstruction confirm that the actual vectors use the flat encoder with two repetitions, but the stale comments should be corrected before release.

#### Overall assessment

E6R produces a mixed but ultimately negative depth-ablation result.

Adding a second entangler–mixer block does affect the representation. Triangle accessibility improves, the bimodal stratum becomes stronger on several targets, and its C5 concatenation advantage grows from (0.118) to (0.163).

These gains do not extend across the full experiment. The deeper cycle targets remain near the aggregate prediction floor, S3 and S4 remain largely inactive, and the near-regular C5 complementarity disappears.

The result therefore strengthens the scope conclusion established by E6 and E6D. QuIC’s strong cubic organization is not recovered on these nonregular families by either explicit degree encoding or a second circuit repetition.

The appropriate central claim is:

> Increasing flat QuIC from one to two entangler–mixer repetitions selectively strengthens triangle accessibility and amplifies C5 complementarity in the bimodal degree-sequence stratum, but it does not restore the broader cubic hierarchy. Four-, five-, and six-cycle accessibility remains near the aggregate prediction floor, and the higher-heterogeneity strata remain largely inactive. The off-regularity collapse therefore cannot be attributed solely to insufficient circuit depth.


### E7 - Truncation


#### Experimental design

This experiment measures how much of QuIC’s cycle-count information is retained when the sorted probability vector is truncated to its (k) largest entries.

The analysis uses the complete connected cubic-graph censuses at:

* (n=14): 509 graphs;
* (n=16): 4,060 graphs.

For each graph, the full QuIC representation is the descending sorted probability vector

$$
\mathbf p(G)
=

\left(
p_{(1)},p_{(2)},\ldots,p_{(2^n)}
\right),
\qquad
p_{(1)}\ge p_{(2)}\ge\cdots.
$$

The truncated representation is

$$
\mathbf p_k(G)
=

\left(
p_{(1)},\ldots,p_{(k)}
\right).
$$

The tested truncation lengths are:

$$
k\in
{25,50,100,200,400,1000,4000},
$$

plus the full (16{,}384)-dimensional vector at (n=14).

The (n=16) run completed through (k=4000) but did not reach the full (65{,}536)-dimensional point before termination.

Four cycle-count targets are evaluated:

* triangles;
* 4-cycles;
* 5-cycles;
* 6-cycles.

Each score is produced using the same five shuffled folds and nested ridge-regression protocol as the earlier E2 analysis.

#### Completed results

##### (n=14)

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

##### (n=16)

|   (k) |       Triangles |        4-cycles |        5-cycles |        6-cycles |
| ----: | --------------: | --------------: | --------------: | --------------: |
|    25 | (1.000\pm0.000) | (0.968\pm0.011) | (0.169\pm0.031) | (0.126\pm0.014) |
|    50 | (1.000\pm0.000) | (0.981\pm0.003) | (0.167\pm0.032) | (0.179\pm0.013) |
|   100 | (1.000\pm0.000) | (0.996\pm0.001) | (0.335\pm0.041) | (0.184\pm0.011) |
|   200 | (1.000\pm0.000) | (0.998\pm0.002) | (0.743\pm0.060) | (0.190\pm0.027) |
|   400 | (1.000\pm0.000) | (0.998\pm0.003) | (0.981\pm0.015) | (0.363\pm0.023) |
| 1,000 | (1.000\pm0.000) | (1.000\pm0.000) | (0.982\pm0.015) | (0.640\pm0.121) |
| 4,000 | (1.000\pm0.000) | (1.000\pm0.000) | (0.982\pm0.015) | (0.642\pm0.122) |

#### Triangle count

Triangle prediction is completely preserved at the smallest tested truncation:

$$
R^2=1.000
$$

using only the 25 largest probabilities at both graph orders.

Those 25 coordinates represent:

$$
\frac{25}{16{,}384}\approx0.153%
$$

of the (n=14) vector, and

$$
\frac{25}{65{,}536}\approx0.038%
$$

of the (n=16) vector.

The experiment does not determine whether fewer than 25 coordinates would suffice, because no smaller truncation was tested. It does establish that the triangle signal is concentrated extremely strongly in the probability head.

This agrees with the earlier probability-moment results, where triangle count was almost exactly recoverable from the lowest power sums. Both experiments indicate that triangle count primarily controls coarse concentration properties of the sorted distribution.

#### Four-cycle count

Four-cycle information is also highly head-concentrated, although less completely than triangle information.

At (k=25), the scores are already:

$$
R^2=0.957
\quad\text{at }n=14,
$$

and

$$
R^2=0.968
\quad\text{at }n=16.
$$

By (k=100), performance reaches:

$$
0.993
\quad\text{and}\quad
0.996.
$$

The remaining coordinates produce little additional improvement.

Thus, approximately 100 leading probabilities are sufficient to retain nearly all linearly accessible 4-cycle information. This corresponds to:

$$
0.61%
$$

of the (n=14) vector and only

$$
0.15%
$$

of the (n=16) vector.

The result is consistent with the power-sum ladder, where 4-cycle count became essentially exact using low-order global summaries. Its information is distributed more broadly than the triangle signal but remains concentrated near the probability head.

#### Five-cycle count

Five-cycle count exhibits a distinct truncation threshold.

At (n=14), the score remains weak through (k=100):

$$
R^2=0.272\pm0.142.
$$

It then rises sharply at (k=200):

$$
R^2=0.920\pm0.081,
$$

and reaches its full-vector value by approximately (k=400).

At (n=16), the transition occurs later:

$$
R^2=0.335
\quad\text{at }k=100,
$$

$$
R^2=0.743
\quad\text{at }k=200,
$$

and

$$
R^2=0.981
\quad\text{at }k=400.
$$

The score then remains unchanged through (k=4000).

The 5-cycle information is therefore not spread uniformly throughout the complete vector. It becomes accessible after a relatively narrow rank window is included:

$$
k\approx200\text{--}400.
$$

This differs from the gradual accumulation expected if every additional tail coordinate contributed a small independent amount of information. The sharp rise suggests that the relevant probability-spectrum structure is concentrated around a specific portion of the sorted head.

At (n=16), 400 coordinates constitute only:

$$
\frac{400}{65{,}536}\approx0.61%
$$

of the full representation.

The strong full-vector 5-cycle result therefore does not require most of the exponentially large probability vector. It does, however, require substantially more than the first 50–100 entries that already solve triangles and 4-cycles.

#### Six-cycle count

Six-cycle information is the deepest and most diffusely represented of the four tested targets.

At (n=14), performance rises gradually:

$$
0.163
\rightarrow
0.228
\rightarrow
0.235
\rightarrow
0.391
\rightarrow
0.478
$$

as (k) increases from 25 to 400.

The mean then saturates near the full-vector result:

$$
R^2\approx0.485.
$$

At (n=16), the early head contains little 6-cycle information:

$$
R^2=0.126
\quad\text{at }k=25,
$$

and only

$$
R^2=0.190
$$

at (k=200).

The score rises to

$$
0.363
$$

at (k=400), followed by a large jump to

$$
0.640
$$

at (k=1000.
$$

Increasing to (k=4000) produces almost no further gain:

$$
0.642.
$$

The 6-cycle signal therefore extends considerably farther into the probability vector than the C3–C5 signals, but it still saturates within the first approximately 1,000 entries.

At (n=16), this is only:

$$
\frac{1000}{65{,}536}\approx1.53%
$$

of the full vector.

The (n=14) results also reveal a bias–variance effect. At (k=400),

$$
R^2=0.478\pm0.113,
$$

which is almost the same mean as the full-vector result:

$$
0.485\pm0.326.
$$

Adding the tail beyond (k=400) contributes almost no average predictive value but substantially increases fold variability. For this target and census, truncation acts as an effective regularizer.

#### Rank-stratified structural hierarchy

The truncation curves reveal a clear ordering in the amount of the probability head required for each structural layer:

$$
\boxed{
C_3
;\rightarrow;
C_4
;\rightarrow;
C_5
;\rightarrow;
C_6
}
$$

A practical summary is:

| Target    | Approximate saturation scale |
| --------- | ---------------------------: |
| Triangles |                     (k\le25) |
| 4-cycles  |                (k\approx100) |
| 5-cycles  |    (k\approx200\text{--}400) |
| 6-cycles  |   (k\approx400\text{--}1000) |

The hierarchy should be interpreted as a rank-depth ordering, not as a strict ordering of (R^2) at every small (k).

For example, at (n=14), the 6-cycle score exceeds the 5-cycle score at (k=25) and (k=50). The meaningful pattern is that each target reaches its eventual predictive plateau at progressively larger truncation lengths.

#### Scaling from (n=14) to (n=16)

The ambient representation dimension increases by a factor of four:

$$
16{,}384
\rightarrow
65{,}536.
$$

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

#### Compact representations

The experiment identifies several useful operating points.

##### (k=25)

Using only 25 probabilities preserves:

* exact triangle prediction;
* (R^2\approx0.96\text{--}0.97) for 4-cycles.

It does not preserve meaningful 5- or 6-cycle prediction.

##### (k=100)

Using 100 probabilities preserves:

* exact triangle prediction;
* nearly complete 4-cycle prediction;
* only partial 5-cycle information;
* weak 6-cycle information.

This is approximately dimension matched to the 64-dimensional GNN embeddings used in the E3 experiment. At this scale, truncated QuIC remains exceptionally strong on triangles and 4-cycles but does not retain its full-vector advantage for deeper cycles.

##### (k=400)

Using 400 probabilities preserves:

* all triangle and 4-cycle information;
* essentially all 5-cycle information;
* most of the (n=14) 6-cycle signal;
* approximately 57% of the (n=16) full 6-cycle score.

##### (k=1000)

Using 1,000 probabilities preserves essentially all observed cycle-count performance at both graph orders.

The remaining tail—from coordinate 1,001 through 16,384 or 65,536—adds no material predictive value for the tested cycle targets.

#### Relation to the probability-moment results

The truncation and moment experiments address different forms of compression.

Power sums reduce the entire probability vector to a few global scalars:

$$
\sum_zp_z^k.
$$

Truncation retains the detailed shape of the largest probabilities but discards the long tail.

The results show that:

* triangles and 4-cycles survive both forms of compression;
* 5-cycles survive head truncation but not low-order moment compression;
* 6-cycles require a larger portion of the head and are also poorly captured by low-order moments.

The 5-cycle result is particularly informative. Its signal is present almost entirely within the first 200–400 ranked probabilities, yet it cannot be reconstructed from power sums through order eight.

Thus, 5-cycle accessibility depends on the detailed arrangement of probability magnitudes within the head, rather than only on coarse concentration summaries.

#### Uncompleted cospectral tracer

The notebook planned a second analysis measuring how the global percentile of each cospectral-pair separation changes under truncation.

That analysis did not produce completed outputs in this run. Consequently, the notebook supports conclusions about cycle-count decodability under truncation, but not about how truncation changes the relative standing of cospectral separations.

No claim about cospectral mate percentiles should be based on this run alone.

#### What the experiment establishes

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

#### Necessary qualifications

The (n=16) full-vector point did not complete in this notebook. Saturation is inferred from the negligible differences between (k=1000) and (k=4000), together with the previously established full-vector scores. The current run alone does not directly measure the final (61{,}536) coordinates.

The vectors contain exact ideal probabilities. The experiment does not determine how many circuit shots are required to identify and estimate the largest (k) probabilities.

In particular, extracting the exact top-(k) sorted vector from finite samples is not equivalent to measuring only (k) predetermined bitstrings. The identities of the highest-probability outcomes must first be discovered, and ranking errors may occur when probabilities are close.

The truncated vectors are not renormalized. A ridge model may therefore use both:

* the relative shape of the retained probabilities;
* the cumulative retained mass
  $$
  \sum_{i=1}^{k}p_{(i)}.
  $$

This is appropriate for measuring predictive information in the raw head, but it does not isolate shape information from retained-mass information. A normalized-head control would answer that separate question.

Only cycle-count targets are included. The results do not establish suitable truncation lengths for girth, diameter, spectral gap, diamonds, or other graph invariants.

The truncation grid is coarse. Statements such as “C5 saturates at (k=200)” mean that 200 is the first tested point near saturation, not that it is the true minimum sufficient dimension.

The ridge models operate in a high-dimensional, low-sample regime, particularly at (n=14). The increase in 6-cycle variance after (k=400) indicates that the tail can amplify fold instability even when its average predictive contribution is negligible.

Finally, no paired statistical test is performed between adjacent truncation levels. Small differences near saturation should be treated descriptively.

#### Overall assessment

The experiment shows that the exponentially large QuIC probability vector is highly redundant for cycle-count decoding.

Triangle count is completely accessible from the first 25 probabilities. Four-cycle count is nearly saturated by 100. Five-cycle count undergoes a sharp transition between approximately 100 and 400 entries. Six-cycle information extends deeper, but performance saturates by approximately 1,000 entries.

At (n=16), those 1,000 coordinates represent only about 1.5% of the complete vector. Increasing to 4,000 entries produces essentially no additional gain.

The appropriate central claim is:

> QuIC’s cycle-count information is rank-stratified within the sorted probability distribution. Triangle and 4-cycle structure is concentrated in the extreme head, 5-cycle information emerges within the first few hundred probabilities, and 6-cycle information extends to approximately the first thousand. Across (n=14) and (n=16), the useful absolute head grows far more slowly than the full (2^n)-dimensional representation, although practical finite-shot recovery of that head remains untested.

### E8 - CoSpectral Audit

#### Experimental design

This experiment audits the adjacency-cospectral graph census and determines which graph invariants actually vary within cospectral classes.

The analysis uses the complete connected cubic-graph censuses at:

* (n=14): 509 graphs;
* (n=16): 4,060 graphs.

It has two objectives:

1. replace the earlier rounded-eigenvalue grouping with an exact cospectrality test;
2. identify targets that vary among graphs having exactly the same adjacency spectrum.

For each graph with adjacency matrix (A), the exact signature is

$$
\left(
	ext{tr}(A),
	ext{tr}(A^2),
\ldots,
	ext{tr}(A^n)
\right).
$$

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

#### Exact cospectral census

The exact integer-trace grouping reproduces the earlier spectrum-hash census without any disagreement.

| Order  | Exact groups | Graphs in groups | Group sizes             | Within-group pairs |
| ------ | -----------: | ---------------: | ----------------------- | -----------------: |
| (n=14) |            3 |                6 | three pairs             |                  3 |
| (n=16) |           41 |               83 | 40 pairs and one triple |                 43 |

At both graph orders, the exact groups are identical to those obtained by rounding adjacency eigenvalues to eight decimal places.

This closes the numerical-tolerance concern for these two censuses. No false cospectral groups were created by rounding, and no exact group was missed.

The agreement validates the earlier census, but only for these datasets. It does not imply that eight-decimal eigenvalue hashing is universally safe on larger or different graph families.

#### Invariant audit

#### Group-level variation counts

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

$$
3\text{ of }3
\quad\text{at }n=14,
$$

and

$$
29\text{ of }41
\quad\text{at }n=16.
$$

Thus, most (n=16) cospectral groups are not isomorphic copies with identical audited structure. They differ on at least one global metric or symmetry quantity.

#### Spectrally fixed controls

The short-cycle controls behave exactly as expected.

Every cospectral group agrees on:

$$
C_3,\quad C_4,\quad C_5.
$$

For regular graphs, these quantities are determined by low-order adjacency traces. Their agreement is therefore a theorem-level consistency check on:

* the exact cospectral grouping;
* the cycle-count implementation;
* the graph ordering;
* and the invariant audit.

Girth also agrees in every group. In this census, that equality is reinforced by the observed agreement of all cycle counts through (C_7).

No pinned-control violation occurs. There is therefore no indication that the cospectral census or invariant calculations are misaligned.

#### Six-cycle count and diamonds

Every cospectral group agrees on (C_6).

For cubic graphs, the notebook verifies the identity

$$
	ext{tr}(A^6)
=

12(C_6+D)
+
87n
+
6C_3
+
96C_4,
$$

where (D) is the number of diamonds, or copies of (K_4) with one edge removed.

The identity holds exactly for every graph in both complete censuses.

Because the spectrum fixes

$$
	ext{tr}(A^6),
$$

and also fixes (n), (C_3), and (C_4), it fixes the sum

$$
C_6+D.
$$

The audit shows that (C_6) itself does not vary within any cospectral group at (n=14) or (n=16). It follows that diamond count also does not vary within those groups.

This does not establish that (C_6) or (D) is universally adjacency-spectral for all cubic graphs. The identity fixes only their sum. A larger census could contain cospectral mates that trade one 6-cycle against one diamond.

The present result is narrower:

> No such (C_6)-diamond tradeoff occurs among the exact cospectral cubic groups at (n=14) or (n=16).

Consequently, these groups cannot support a within-cospectral-class challenge based on (C_6) or diamonds.

#### Seven-cycle count

Every exact group also agrees on (C_7).

Unlike the (C_3)–(C_6) results, the notebook does not derive a spectral identity explaining this agreement. The (C_7) result is therefore empirical.

It establishes that (C_7) is unusable as a varying cospectral target in these two censuses. It does not establish that 7-cycle count is generally determined by the adjacency spectrum of cubic graphs.

#### Diameter and radius

Diameter agrees in all 44 exact cospectral groups:

$$
0\text{ differing groups}.
$$

Radius behaves differently. Four (n=16) groups have different radii despite identical adjacency spectra.

The four radius-varying groups include changes of the form

$$
3\leftrightarrow4.
$$

This distinction is structurally meaningful. Diameter records the maximum eccentricity, while radius records the minimum eccentricity. The cospectral mates preserve the worst-case graph distance but can differ in how centrally positioned their most central vertices are.

The result demonstrates that the adjacency spectrum does not determine radius within this census, even though it happens to determine diameter across the observed cospectral classes.

Radius is therefore a valid non-spectral challenge target, but the sample is small:

$$
4\text{ usable groups}.
$$

That is insufficient for a strong standalone statistical experiment without combining it with other evidence.

#### Wiener index

The Wiener index is the most common varying invariant.

It differs in:

$$
1\text{ of }3
$$

groups at (n=14), and

$$
25\text{ of }41
$$

groups at (n=16).

The Wiener index is

$$
W(G)
=

\sum_{{u,v}\subseteq V}
d(u,v),
$$

the sum of all unordered pairwise shortest-path distances.

Most within-group differences are small:

$$
1\text{--}3
$$

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

#### Automorphism-group order

Automorphism-group order differs in:

$$
3\text{ of }3
$$

groups at (n=14), and

$$
14\text{ of }41
$$

groups at (n=16).

Examples include:

$$
1\leftrightarrow2,
\qquad
2\leftrightarrow4,
\qquad
4\leftrightarrow8,
\qquad
12\leftrightarrow48.
$$

This shows that adjacency-cospectral graphs can have substantially different symmetry groups.

The (n=14) result is particularly clear: all three cospectral pairs differ in automorphism order, even though only one differs in Wiener index.

Automorphism order therefore captures a different non-spectral direction from the metric quantities. It is not merely a proxy for radius or Wiener index.

Because its distribution is highly skewed and multiplicative, a transformed target such as

$$
\log_2|	ext{Aut}(G)|
$$

is more suitable for regression or ranking than raw group order.

The usable sample remains limited, particularly if groups are divided into training and test sets. Automorphism order is therefore a strong secondary challenge target rather than the best primary target.

#### Invariants that do not vary

No exact cospectral group differs in:

* node connectivity;
* edge connectivity;
* maximum matching size;
* clique number.

These negative results should be interpreted as census-specific.

They show that these invariants cannot support the planned cospectral challenge at (n\le16). They do not imply that any of them is generally determined by the adjacency spectrum.

The same qualification applies to diameter, (C_6), and (C_7): agreement across all observed groups is a property of the available census, not a universal spectral theorem unless separately proved.

#### Structure of the usable challenge set

At (n=16), 29 of the 41 exact groups differ on at least one of:

* Wiener index;
* radius;
* automorphism order.

The overlap among these targets is substantial but incomplete.

Some groups differ only in automorphism order. Others differ only in Wiener index. A smaller number differ in radius together with Wiener index or automorphism order.

The cospectral triple

$$
(582,3061,3800)
$$

has Wiener values

$$
283,\ 282,\ 283.
$$

This illustrates why the natural unit of cross-validation is the cospectral group rather than an arbitrary graph or graph pair. All members of a group must remain in the same fold to prevent the model from seeing a spectral duplicate of a test graph during training.

The audit therefore determines not only the viable targets but also the required evaluation structure:

$$
\boxed{
\text{group-preserving folds with within-group comparisons}
}
$$

#### What the experiment establishes

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

#### Necessary qualifications

The exact trace test relies on the fact that the graphs have the same order. Traces through (A^n) determine the characteristic polynomial for an (n\times n) matrix through Newton’s identities.

The use of signed 64-bit integers is safe at (n\le16) for cubic graphs because the relevant closed-walk counts remain far below the integer limit. This implementation would require reassessment at substantially larger graph orders or degrees.

The audit covers only graph invariants explicitly listed in the notebook. Cospectral groups may differ on many other quantities that were not computed.

The sample contains only 44 exact groups in total. Group-level statistical power is therefore limited, especially for radius and automorphism order.

The (n=14) results are based on only three groups. The fact that all three differ in automorphism order is structurally interesting but does not provide a precise population-frequency estimate.

Wiener-index differences are usually small relative to the total index. A successful downstream result must demonstrate genuine within-group discrimination rather than exploiting global scale or graph-order information.

The invariant audit establishes target variation, not QuIC decodability. A separate experiment is required to show that QuIC can predict which cospectral mate has the larger Wiener index, radius, or automorphism group.

Finally, the absence of variation is not proof of spectral determination. For (C_7), diameter, connectivity, matching number, and clique number, the correct wording is that no variation occurs in these censuses.

#### Overall assessment

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


### E8B  Functional exact-cospectral challenge

#### Experimental design

This experiment tests whether QuIC’s numerically certified non-spectral differences are functionally related to graph invariants that vary within exact adjacency-cospectral classes.

The analysis uses the complete connected cubic-graph census at (n=16):

* 4,060 total graphs;
* 41 exact adjacency-cospectral groups;
* 83 graphs belonging to those groups;
* 40 cospectral pairs and one cospectral triple.

Exact cospectrality is established using integer trace tuples

$$
\left(
	ext{tr}(A),
	ext{tr}(A^2),
\ldots,
	ext{tr}(A^{16})
\right),
$$

rather than rounded numerical eigenvalues.

The three targets identified by the preceding invariant audit are:

* Wiener index;
* (\log_2|	ext{Aut}(G)|);
* radius.

Only groups whose members differ on the target are included. This produces:

| Target       |        Varying groups | Unequal-value pairs |    |    |
| ------------ | --------------------: | ------------------: | -- | -- |
| Wiener index |                    25 |                  26 |    |    |
| (\log_2      | 	ext{Aut}(G) |                   ) | 14 | 14 |
| Radius       |                     4 |                   4 |    |    |

One equal-Wiener pair inside the cospectral triple is excluded.

For each unequal pair ((G_i,G_j)), the task is to predict

$$
	ext{sign}(y_i-y_j)
$$

from the QuIC difference vector

$$
\mathbf p_k(G_i)-\mathbf p_k(G_j),
$$

where (\mathbf p_k) contains the (k) largest entries of the sorted QuIC probability vector.

The tested truncation depths are:

$$
k\in{100,400,1000,65536}.
$$

Evaluation uses leave-one-cospectral-group-out cross-validation. All members and all pairs from a held-out group remain outside training. Both orientations of each training pair are included, and an intercept-free logistic model ensures that the decision function is antisymmetric:

$$
f(\mathbf p_i-\mathbf p_j)
=

-f(\mathbf p_j-\mathbf p_i).
$$

The regularization parameter is selected using group-wise inner cross-validation on the training groups only.

#### Main results

| Target  |                (k) | Correct pairs | Accuracy | Balanced accuracy | Nominal one-sided (p) |       |        |
| ------- | -----------------: | ------------: | -------: | ----------------: | --------------------: | ----- | ------ |
| Wiener  |                100 |         18/26 |    0.692 |             0.709 |                0.0378 |       |        |
| Wiener  |                400 |         18/26 |    0.692 |             0.721 |                0.0378 |       |        |
| Wiener  |              1,000 |         16/26 |    0.615 |             0.606 |                0.1635 |       |        |
| Wiener  |             65,536 |         14/26 |    0.538 |             0.539 |                0.4225 |       |        |
| (\log_2 | 	ext{Aut} |             ) |      100 |             14/14 |                 1.000 | 1.000 | 0.0001 |
| (\log_2 | 	ext{Aut} |             ) |      400 |             11/14 |                 0.786 | 0.771 | 0.0287 |
| (\log_2 | 	ext{Aut} |             ) |    1,000 |             10/14 |                 0.714 | 0.688 | 0.0898 |
| (\log_2 | 	ext{Aut} |             ) |   65,536 |             11/14 |                 0.786 | 0.771 | 0.0287 |
| Radius  |                100 |           3/4 |    0.750 |             0.500 |                0.3125 |       |        |
| Radius  |                400 |           4/4 |    1.000 |             1.000 |                0.0625 |       |        |
| Radius  |              1,000 |           4/4 |    1.000 |             1.000 |                0.0625 |       |        |
| Radius  |             65,536 |           4/4 |    1.000 |             1.000 |                0.0625 |       |        |

The reported (p)-values are those produced by the notebook’s one-sided binomial test against chance accuracy (0.5).

#### Automorphism-group order

Automorphism-group order provides the strongest functional result.

Using only the first 100 sorted probabilities, QuIC correctly ranks all 14 unequal cospectral pairs:

$$
14/14,
\qquad
\text{accuracy}=1.000.
$$

The nominal exact binomial result is

$$
p\approx6.1\times10^{-5},
$$

with a one-sided exact 95% confidence interval beginning at approximately

$$
0.807.
$$

Performance remains above chance at larger truncation depths:

$$
11/14
$$

at (k=400) and for the complete vector, although the (k=1000) result falls to

$$
10/14.
$$

The perfect (k=100) result establishes that QuIC’s within-cospectral differences are aligned with graph symmetry rather than merely providing arbitrary numerical separation.

Because every pair has exactly the same adjacency spectrum, this relationship cannot be recovered from any function of that spectrum alone.

The automorphism result therefore supplies the clearest functional evidence for useful non-spectral information in the QuIC representation.

#### Wiener index

The Wiener-index result is weaker but suggestive.

At both

$$
k=100
\quad\text{and}\quad
k=400,
$$

the ranker correctly orders

$$
18/26
$$

pairs:

$$
\text{accuracy}=0.692.
$$

The nominal one-sided binomial value is

$$
p=0.0378,
$$

with balanced accuracies of (0.709) and (0.721).

Performance declines as more coordinates are included:

$$
16/26
$$

at (k=1000), and

$$
14/26
$$

for the complete vector.

This pattern suggests that the Wiener-related signal is concentrated in the leading probability ranks and is diluted by the lower-probability tail.

However, the evidence is marginal. The best QuIC result exceeds the numerical-spectrum control by only one correctly ranked pair:

$$
18/26
\quad\text{versus}\quad
17/26.
$$

Moreover, the permutation-null audit does not fully support the claimed exact binomial tail. The empirical null mean is close to one half,

$$
0.5066,
$$

but the empirical 95th percentile is 19 correct pairs, compared with 17 under the nominal binomial model. The observed Wiener result of 18 correct pairs therefore does not lie in the upper 5% of the notebook’s own empirical null distribution.

The current result supports a possible Wiener signal, but it is not yet sufficient for a strong inferential claim.

#### Radius

Radius is correctly ranked for all four varying cospectral pairs using:

$$
k=400,\quad
k=1000,
\quad\text{and the full vector}.
$$

At (k=100), three of four pairs are correct.

The result is structurally interesting but cannot establish statistical evidence. Even perfect performance on four independent fair-coin comparisons has probability

$$
\frac{1}{2^4}=0.0625.
$$

Radius should therefore be presented as an illustrative exhibit rather than as a primary quantitative result.

#### Spectrum control

The same ranking pipeline is applied to differences between the sorted adjacency eigenvalue vectors.

The largest within-group eigenvalue discrepancy is only

$$
5.77\times10^{-15},
$$

consistent with floating-point eigensolver noise.

| Target  |      Correct pairs | Accuracy | Nominal (p) |       |        |
| ------- | -----------------: | -------: | ----------: | ----- | ------ |
| Wiener  |              17/26 |    0.654 |      0.0843 |       |        |
| (\log_2 | 	ext{Aut} |        ) |        9/14 | 0.643 | 0.2120 |
| Radius  |                3/4 |    0.750 |      0.3125 |       |        |

None of the spectrum controls reaches nominal significance.

This is consistent with the exact-cospectral construction: the complete adjacency spectrum contains no information with which to distinguish members of a group.

The nonzero control accuracies arise from the extremely small numerical eigensolver differences and the small number of evaluated pairs. The appropriate null comparison is ultimately a permutation distribution for the complete ranking pipeline rather than the numerical-spectrum scores alone.

#### Localization within the probability head

The strongest results occur at the smallest tested truncation depth.

At (k=100):

* automorphism order is ranked correctly for all 14 pairs;
* Wiener index is ranked correctly for 18 of 26 pairs;
* radius is ranked correctly for 3 of 4 pairs.

Adding more coordinates does not consistently improve any target.

This behavior is consistent with the preceding truncation and precision analyses, which found that the strongest structural and cospectral differences are concentrated disproportionately among the largest sorted probabilities.

The result also reflects the statistical regime. The number of training groups is extremely small relative to the feature dimension. Increasing from 100 to 65,536 coordinates introduces substantial estimation variance without adding enough examples to constrain the additional coefficients.

The experiment therefore demonstrates functional compression rather than a benefit from using the complete exponentially large vector.

#### Permutation-null audit

The notebook performs 500 complete sign-flip refits for Wiener index at (k=100).

The empirical null mean is:

$$
0.5066,
$$

close to the expected value (0.5). This provides evidence that the pipeline has no systematic directional bias or direct train/test leakage.

The empirical and nominal null tails do not match exactly:

$$
\text{empirical 5/50/95 percentiles}
=

(9,13,19),
$$

while the binomial values are:

$$
(9,13,17).
$$

This discrepancy matters because leave-one-group-out predictions are generated from heavily overlapping training sets. The correctness indicators are therefore not guaranteed to be mutually independent, even if every held-out label is marginally independent of its prediction.

Consequently, the nominal binomial test should not be described as exact for this pipeline. Target- and truncation-specific sign-flip permutation tests should be used for the final inferential results.

#### What the experiment establishes

The completed results support four conclusions.

1. **QuIC’s non-spectral residue is functionally organized.**
   Its within-group differences are related to at least one invariant that varies among exact adjacency-cospectral graphs.

2. **Automorphism-group order provides the strongest evidence.**
   The first 100 probabilities correctly rank all 14 unequal cospectral pairs.

3. **The Wiener-index evidence is suggestive but not yet conclusive.**
   The nominal (18/26) result is significant under an independent-binomial model but does not exceed the empirical 95th percentile of the notebook’s permutation audit.

4. **The useful signal is concentrated in the probability head.**
   The (k=100) representation performs as well as or better than longer truncations and the complete vector.

The strongest supported statement is therefore about symmetry rather than shortest-path structure.

#### Necessary qualifications

The nominal binomial (p)-values assume independent pairwise correctness events. This assumption is not guaranteed because the leave-one-group-out models use overlapping training groups. The empirical null’s heavier upper tail confirms that the binomial distribution is not an exact description of the complete pipeline.

A full sign-flip permutation test should be run separately for every reported target and truncation depth. The resulting empirical tail probabilities should replace the nominal binomial values.

Four truncation depths are tested for each target. Unless one depth was designated as primary before examining the outputs, selecting the best result introduces a multiple-comparison issue. The Wiener value

$$
p=0.0378
$$

does not survive even a simple four-arm Bonferroni correction. The automorphism (k=100) result is much stronger and is likely to remain significant, but this should be verified empirically.

The effective sample sizes are small:

* 25 groups for Wiener index;
* 14 for automorphism order;
* 4 for radius.

The results characterize the complete (n=16) cubic census, but they do not provide a broad population-level estimate across graph orders or graph families.

The feature dimensions range from 100 to 65,536, while the training set contains at most 25 groups. Regularization and nested group-wise selection reduce overfitting, but the full-vector arms remain statistically extreme.

The task demonstrates QuIC information beyond the adjacency spectrum. It does not establish superiority over other non-spectral classical graph representations such as higher-order Weisfeiler–Lehman features, graph kernels, or explicit symmetry descriptors.

Finally, the inputs are exact ideal QuIC probabilities. The experiment does not test whether these within-cospectral ranking signals survive finite-shot sampling.

#### Overall assessment

This experiment fills the main logical gap left by the exact cospectral and precision audits.

The earlier analyses established that QuIC assigns distinct, numerically genuine vectors to adjacency-cospectral graphs. The present experiment shows that those differences are not entirely arbitrary: the first 100 sorted probabilities correctly rank automorphism-group order for every one of the 14 unequal cospectral pairs.

That is the strongest functional non-spectral result currently available.

The Wiener-index result is less secure. Its nominal significance depends on an independence assumption not reproduced by the empirical permutation tail, and it does not clearly exceed the numerical-spectrum control. It should remain secondary unless a target-specific permutation analysis confirms it.

The appropriate central claim is:

> Within the complete (n=16) cubic census, QuIC’s certified non-spectral residue is functionally related to graph symmetry. A group-preserving ranker using only the first 100 sorted probabilities correctly orders automorphism-group size for all 14 unequal adjacency-cospectral pairs. Wiener-index ranking is suggestive but requires permutation-based confirmation, while radius remains an illustrative four-group exhibit.


### E9 — Mixer-Angle Expansion and Perturbative Mechanism

#### Experimental design

This experiment tests the perturbative interpretation of the QuIC mixer rather than inferring the mechanism from results obtained only at the canonical mixer angle.

The mixer angle

$$
\beta
$$

is varied while all other circuit choices remain fixed:

* degree-proportional (R_X) encoder;
* entangler angle (2.0);
* one (R_{ZZ}) gate per graph edge;
* one entangler–mixer repetition;
* canonical encoding rotation (2.875);
* computational-basis measurement;
* descending probability sorting.

Because every graph is cubic, all vertices receive the same encoding rotation. The tested graph sets are:

* the complete 509-graph census at (n=14);
* a seeded subset of 500 graphs from the complete (n=16) census.

The (n=16) subset is sampled without replacement using seed 0. It is used as a qualitative replication of the mechanism rather than as a second exhaustive-census result.

The experiment tests four claims:

1. the sorted probability representation collapses to a graph-independent vector at (\beta=0);
2. the local cut finite differences take the predicted cubic-graph values;
3. the analytic first-order coefficient matches the numerical derivative of the circuit probabilities;
4. different graph properties become linearly accessible from different perturbative coefficients.

A separate mixer-angle ladder evaluates:

$$
\beta\in
{0.0125,0.025,0.05,0.1,0.2,0.4,0.8}.
$$

At each angle, the experiment measures:

* median pairwise (L_1) distance between sorted QuIC vectors;
* ridge-probe (R^2) for seven graph properties.

All probe experiments use the first 1,000 sorted coordinates. The earlier truncation experiment showed that (k=1000) is effectively saturated for the tested targets at (n=14).

#### Collapse at zero mixer angle

At

$$
\beta=0,
$$

the circuit contains only the encoder and diagonal (R_{ZZ}) entanglers before measurement.

The entangler changes computational-basis phases but not probability magnitudes. Since the cubic encoder is uniform, the probability of a bitstring depends only on its Hamming weight.

For every graph at both orders, the notebook verifies that:

* all bitstrings within each Hamming-weight level have the same probability;
* the complete sorted probability vector is identical across graphs to within the (10^{-14}) audit tolerance.

Thus,

$$
\mathbf p_{\beta=0}(G)
======================

\mathbf p_{\beta=0}(H)
$$

for every pair of graphs (G,H) in each tested set.

The graph structure is therefore not directly visible in the zero-mixer measurement distribution. It is stored only in relative phases created by the entangler.

The mixer is the operation that converts those graph-dependent phases into graph-dependent measurement probabilities.

This establishes a clear mechanistic decomposition:

$$
\boxed{
\text{entangler stores topology in phase}
\quad\longrightarrow\quad
\text{mixer converts phase into probability}
}
$$

#### Cubic cut finite differences

For a bitstring (x), write

$$
z_i\in{-1,+1}
$$

for the sign associated with bit (i). Flipping bit (i) changes the graph-cut contribution according to

$$
\Delta_i c(x)
=============

z_i\sum_{j\in N(i)}z_j.
$$

Because every vertex has degree three,

$$
\sum_{j\in N(i)}z_j
\in
{-3,-1,+1,+3}.
$$

The notebook verifies in exact integer arithmetic that

$$
\Delta_i c(x)
\in
{-3,-1,+1,+3}
$$

for every bitstring, every vertex, and every graph in both tested sets.

This restricts the local phase differences mixed at first order to four discrete cut-change classes.

#### Analytic first-order coefficient

Let

$$
\phi(y)
$$

denote the pre-mixer amplitude of computational-basis state (y), after the encoder and entangler.

The proposed first-order probability coefficient is

$$
D_1(y)
======

\sum_i
\operatorname{Im}
\left[
\overline{\phi(y)}
\phi(y\oplus e_i)
\right],
$$

where (y\oplus e_i) denotes the bitstring obtained by flipping bit (i).

The notebook independently estimates the derivative using the central difference

$$
D_1^{(h)}(y)
============

\frac{
p_y(+h)-p_y(-h)
}{
2h
},
\qquad
h=10^{-3}.
$$

The analytic and numerical values agree on every graph.

| Graph set                | Worst coordinate error | Richardson-ratio range |
| ------------------------ | ---------------------: | ---------------------: |
| (n=14), complete census  |    (4.37\times10^{-6}) |  (3.999987)–(4.000000) |
| (n=16), 500-graph subset |    (5.39\times10^{-6}) |  (3.999989)–(3.999999) |

Halving the finite-difference step reduces the error by a factor of approximately four. This is the expected behavior of a central difference with error

$$
O(h^2).
$$

The result verifies that the analytic expression is the actual first-order coefficient of the implemented Qiskit circuit, rather than merely a qualitative analogy.

#### Derivative representations

The probability vector is degenerate at (\beta=0): all coordinates within the same Hamming-weight level have equal baseline probability.

The ordinary sorted map is therefore not two-sided differentiable at zero. The physically relevant direction is:

$$
\beta\rightarrow0^+,
$$

toward the canonical positive mixer angle.

The first-order feature vector is constructed by:

1. ordering Hamming-weight blocks by their common (\beta=0) probability;
2. ordering coordinates within each block by descending (D_1);
3. retaining the first 1,000 coefficients.

The second-order coefficient is estimated using:

$$
D_2(y)
======

\frac{
p_y(+h)-2p_y(0)+p_y(-h)
}{
h^2
}
$$

and placed in the ordering induced by the first-order coefficients.

The resulting representations isolate information available from:

* the first derivative (D_1);
* the second derivative (D_2).

#### Perturbative-order probe results

##### (n=14): complete census

| Target       | First-order (D_1) (R^2) | Second-order (D_2) (R^2) |
| ------------ | ----------------------: | -----------------------: |
| Triangles    |                   0.150 |                    1.000 |
| 4-cycles     |                   0.204 |                    0.612 |
| 5-cycles     |                   0.052 |                    0.180 |
| 6-cycles     |                   0.046 |                    0.166 |
| Girth        |                   0.025 |                    0.615 |
| Diameter     |                (-0.008) |                    0.455 |
| Spectral gap |                   0.419 |                    0.615 |

##### (n=16): seeded 500-graph subset

| Target       | First-order (D_1) (R^2) | Second-order (D_2) (R^2) |
| ------------ | ----------------------: | -----------------------: |
| Triangles    |                   0.183 |                    0.999 |
| 4-cycles     |                   0.149 |                    0.260 |
| 5-cycles     |                   0.083 |                    0.240 |
| 6-cycles     |                   0.026 |                    0.204 |
| Girth        |                   0.031 |                    0.317 |
| Diameter     |                   0.011 |                    0.321 |
| Spectral gap |                   0.063 |                    0.479 |

The qualitative pattern is consistent across the two graph sets:

* (D_1) provides limited linear accessibility to most targets;
* (D_2) is stronger for every tested target;
* triangle count is essentially exact from (D_2);
* 5- and 6-cycle counts remain only weakly accessible from either isolated coefficient.

#### Triangle count and second-order accessibility

Triangle count is the clearest perturbative-order result.

At both graph orders:

$$
R^2_{D_2}
\approx1,
$$

while:

$$
R^2_{D_1}
\approx0.15\text{--}0.18.
$$

Thus, triangle count is not linearly organized in the individual first-order coefficient coordinates. It becomes exactly linearly accessible from the second-order probability response.

This is consistent with the previously derived purity mechanism. If

$$
p_y(\beta)
==========

p_y(0)
+
\beta D_1(y)
+
O(\beta^2),
$$

then a quadratic probability statistic contains a graph-dependent term proportional to

$$
\beta^2\sum_yD_1(y)^2.
$$

Triangle count can therefore enter through a quantity quadratic in the first-order amplitudes while remaining poorly accessible through a linear probe on (D_1) itself.

The experiment refines the perturbative interpretation:

> The mixer creates graph-dependent probability differences at first order, but the dominant linearly accessible triangle coordinate appears in the second-order probability response.

#### Four-cycle count

Four-cycle count also favors the second-order coefficient:

$$
0.204\rightarrow0.612
$$

at (n=14), and

$$
0.149\rightarrow0.260
$$

on the (n=16) subset.

The effect is weaker and less stable than the triangle result. In particular, the (n=16) second-order score is substantially below the (n=14) score.

The appropriate interpretation is that (D_2) contains meaningful 4-cycle information, but does not by itself reproduce the near-perfect 4-cycle accessibility of the finite-(\beta) sorted vector.

The remaining signal may depend on:

* higher perturbative orders;
* interactions among derivative coefficients;
* or changes in coordinate ordering as (\beta) moves away from zero.

#### Five- and six-cycle counts

Neither derivative block strongly predicts the longer-cycle targets.

At (n=14):

$$
R^2_{D_2}
=========

0.180
\quad\text{for }C_5,
$$

and

$$
0.166
\quad\text{for }C_6.
$$

On the (n=16) subset:

$$
R^2_{D_2}
=========

0.240
\quad\text{and}\quad
0.204.
$$

The corresponding first-order scores remain near zero.

This places the deeper cycle layers beyond the isolated first- and second-order linear coefficients. Their finite-angle accessibility must depend on higher-order terms, nonlinear combinations of lower-order coefficients, or both.

The result is consistent with the truncation experiment:

* triangle information appears in the extreme probability head;
* 4-cycle information follows;
* 5- and 6-cycle information requires progressively more of the developed finite-(\beta) distribution.

#### Girth, diameter, and spectral gap

Second-order coefficients also contain global structural information.

At (n=14), (D_2) reaches:

$$
R^2=0.615
$$

for girth,

$$
0.455
$$

for diameter, and

$$
0.615
$$

for spectral gap.

The (n=16) subset reproduces the ordering qualitatively, with scores of:

$$
0.317,\quad0.321,\quad0.479.
$$

These targets are not fully determined by the second-order response, but they are substantially more accessible from (D_2) than from (D_1).

The (n=14) first-order spectral-gap score of (0.419) does not replicate on the (n=16) subset, where it falls to (0.063). That cell should therefore not be treated as a stable first-order assignment.

#### Small-(\beta) geometric scaling

The mixer-angle ladder directly measures how quickly the graph-dependent geometry emerges from the collapsed representation.

##### Median pairwise (L_1) distance

| (\beta) |  (n=14) median (L_1) | (n=16) subset median (L_1) |
| ------: | -------------------: | -------------------------: |
|  0.0125 | (1.230\times10^{-5}) |       (1.136\times10^{-5}) |
|   0.025 | (2.398\times10^{-5}) |       (2.202\times10^{-5}) |
|    0.05 | (4.600\times10^{-5}) |       (4.162\times10^{-5}) |
|     0.1 | (8.493\times10^{-5}) |       (7.779\times10^{-5}) |
|     0.2 | (1.805\times10^{-4}) |       (1.726\times10^{-4}) |
|     0.4 | (8.624\times10^{-4}) |       (8.106\times10^{-4}) |
|     0.8 | (3.119\times10^{-3}) |       (2.799\times10^{-3}) |

Over the three smallest mixer angles, the log-log slopes are:

$$
0.951
\quad\text{at }n=14,
$$

and

$$
0.937
$$

on the (n=16) subset.

First-order geometric emergence predicts:

$$
d(\beta)
\propto
\beta.
$$

The measured slopes are close to one, providing direct evidence that the initial separation of graph embeddings is dominated by the first-order probability response.

At larger angles, the growth becomes nonlinear. From (\beta=0.2) to (0.8), the median geometry increases much faster than the small-(\beta) linear extrapolation.

Thus, the canonical angle

$$
\beta=0.1
$$

lies near the end of the approximately perturbative geometric regime, before the much stronger expansion observed at (\beta=0.4) and (0.8).

#### Target accessibility across the mixer-angle ladder

##### (n=14): complete census

| (\beta) | (C_3) | (C_4) | (C_5) | (C_6) | Girth | Diameter | Spectral gap |
| ------: | ----: | ----: | ----: | ----: | ----: | -------: | -----------: |
|  0.0125 | 1.000 | 0.995 | 0.856 | 0.612 | 0.992 |    0.554 |        0.939 |
|   0.025 | 1.000 | 0.994 | 0.789 | 0.522 | 0.992 |    0.539 |        0.936 |
|    0.05 | 1.000 | 0.990 | 0.832 | 0.536 | 0.992 |    0.537 |        0.921 |
|     0.1 | 1.000 | 0.998 | 0.928 | 0.484 | 0.993 |    0.548 |        0.944 |
|     0.2 | 1.000 | 0.999 | 0.954 | 0.500 | 0.993 |    0.547 |        0.915 |
|     0.4 | 1.000 | 0.999 | 0.971 | 0.500 | 0.990 |    0.550 |        0.942 |
|     0.8 | 1.000 | 0.997 | 0.962 | 0.876 | 0.991 |    0.684 |        0.947 |

##### (n=16): seeded 500-graph subset

| (\beta) | (C_3) | (C_4) | (C_5) | (C_6) | Girth | Diameter | Spectral gap |
| ------: | ----: | ----: | ----: | ----: | ----: | -------: | -----------: |
|  0.0125 | 1.000 | 0.994 | 0.850 | 0.472 | 0.986 |    0.573 |        0.897 |
|   0.025 | 1.000 | 0.994 | 0.761 | 0.137 | 0.986 |    0.568 |        0.874 |
|    0.05 | 1.000 | 0.993 | 0.766 | 0.319 | 0.987 |    0.515 |        0.832 |
|     0.1 | 1.000 | 0.993 | 0.960 | 0.459 | 0.987 |    0.627 |        0.861 |
|     0.2 | 1.000 | 0.995 | 0.949 | 0.307 | 0.986 |    0.619 |        0.882 |
|     0.4 | 1.000 | 0.994 | 0.901 | 0.498 | 0.986 |    0.558 |        0.857 |
|     0.8 | 1.000 | 0.998 | 0.970 | 0.775 | 0.977 |    0.672 |        0.878 |

#### Robust structural targets

Triangle count is completely robust across the entire ladder:

[
R^2=1.000
]

at every tested angle and both graph orders.

Four-cycle count is similarly stable:

[
R^2\ge0.990
]

at (n=14), and

[
R^2\ge0.993
]

on the (n=16) subset.

Girth also remains nearly saturated:

[
R^2\ge0.990
]

at (n=14), and approximately:

[
0.977\text{--}0.987
]

on the (n=16) subset.

These properties do not depend sensitively on selecting the canonical mixer angle. Their accessibility is stable across a 64-fold range of positive (\beta).

This is a strong parameter-robustness result for the first two cycle layers and girth.

## Five-cycle count

Five-cycle accessibility is high throughout the ladder but varies more than (C_3), (C_4), and girth.

At (n=14), performance ranges from:

[
0.789
]

to

[
0.971.
]

On the (n=16) subset, it ranges from:

[
0.761
]

to

[
0.970.
]

The canonical angle performs strongly:

[
R^2=0.928
\quad\text{and}\quad
0.960.
]

Larger angles generally improve the 5-cycle score, although the relationship is not monotone.

The 5-cycle layer is therefore robustly present but less uniformly exposed than the shallower cycle targets.

## Six-cycle count

Six-cycle count is the most angle-sensitive target.

At (n=14), scores range from:

[
0.484
]

to

[
0.876.
]

On the (n=16) subset, they range from:

[
0.137
]

to

[
0.775.
]

The strongest result occurs at:

[
\beta=0.8
]

for both graph sets.

Relative to the canonical angle:

[
0.484\rightarrow0.876
]

at (n=14), and

[
0.459\rightarrow0.775
]

on the (n=16) subset.

Thus, the weak canonical (C_6) result is not an invariant limitation of the circuit topology. A larger mixer angle makes substantially more 6-cycle information linearly accessible.

This also shows that the canonical angle is not universally optimal. It preserves the shallow hierarchy well but underexposes the deepest tested cycle layer.

## Diameter

Diameter shows a smaller version of the same large-angle improvement.

At (n=14):

[
R^2=0.548
]

at the canonical angle and

[
0.684
]

at (\beta=0.8).

On the (n=16) subset:

[
0.627\rightarrow0.672.
]

The effect is weaker than for (C_6), but both graph sets attain their strongest diameter score at the largest tested mixer angle.

## Spectral gap

Spectral-gap prediction remains strong throughout the ladder but exhibits no simple monotone relationship with (\beta).

At (n=14), scores remain within:

[
0.915\text{--}0.947.
]

On the (n=16) subset, they range from:

[
0.832
]

to

[
0.897.
]

The representation therefore retains substantial spectral information across all tested mixer angles.

## Geometry magnitude versus decodability

The small-(\beta) geometry is first-order in magnitude, but this does not imply that target decodability is carried linearly by the isolated first-order coefficient.

For example:

* (D_1) predicts triangle count poorly;
* the complete sorted vector at (\beta=0.0125) predicts triangle count perfectly.

This is not contradictory.

A ridge model can amplify small higher-order differences when exact probabilities are available. The perturbative order governing the magnitude of the embedding distance is therefore not necessarily the same as the order at which a particular target becomes linearly decodable.

The experiment distinguishes two concepts:

[
\boxed{
\text{geometric emergence order}
\neq
\text{linear target-accessibility order}
}
]

The overall graph geometry emerges at first order in (\beta), while triangle count is most directly organized in the second-order coefficient.

## What the experiment establishes

The completed results support seven conclusions.

1. **QuIC collapses exactly at zero mixer angle.**
   Before mixing, the sorted probability distribution is graph-independent and determined only by Hamming weight.

2. **The mixer converts graph-dependent phase information into probability information.**
   All measured structural accessibility is created by interference induced by the mixer.

3. **The analytic first-order coefficient is correct.**
   It matches the numerical derivative on every tested graph, with the expected second-order finite-difference convergence.

4. **The initial graph geometry emerges linearly in the mixer angle.**
   The small-(\beta) median-distance slopes are (0.951) and (0.937).

5. **Triangle count is predominantly second-order in linear accessibility.**
   It is nearly exact from (D_2) but weakly predicted from (D_1).

6. **The shallow structural hierarchy is robust across a broad mixer-angle range.**
   Triangles, 4-cycles, and girth remain almost perfectly accessible throughout the ladder.

7. **Deeper structural accessibility is mixer-angle dependent.**
   Six-cycle and diameter prediction improve substantially at (\beta=0.8).

The experiment converts the small-mixer interpretation from a plausible narrative into a directly tested circuit mechanism.

## Necessary qualifications

The derivative features are constructed from unsorted probability derivatives and then block-sorted according to the (\beta\rightarrow0^+) ordering. Because the zero-angle vector contains large degenerate Hamming-weight blocks, the globally sorted representation is not ordinarily differentiable at zero.

The second-order feature vector is evaluated in the ordering induced by (D_1). It is therefore an operational second-order representation rather than a complete coordinate-free decomposition of the sorted map.

Linear accessibility from (D_2) does not prove that a target first appears mathematically at order (\beta^2). A target may be present nonlinearly in (D_1), and higher-order coefficients may also contain the same information.

Conversely, strong (R^2) at very small positive (\beta) does not imply practical observability. At (\beta=0.0125), the median pairwise separation is only approximately:

[
10^{-5}.
]

Exact statevector probabilities allow a ridge model to exploit such differences. Finite-shot sampling may not resolve them.

The beta-ladder scores use raw exact probabilities. Since ridge coefficients can rescale arbitrarily small feature differences, the ladder measures representational information rather than shot-efficient information.

The (n=16) results use a seeded 500-graph subset, not the complete 4,060-graph census. They support qualitative replication of the mechanism but should not be presented as exhaustive (n=16) results.

The first 1,000 coordinates are used rather than the full vectors. This is justified by the earlier truncation study at (n=14), but the same full-vector-equivalence guarantee was not independently established on the sampled (n=16) set for every beta value.

The mixer-angle ladder is a finite grid. The result that (\beta=0.8) is best for (C_6) and diameter does not establish that it is globally optimal. Larger angles may improve or degrade performance further.

No circuit angles other than (\beta) are varied. The experiment establishes robustness and mechanism with respect to the mixer, not the encoder or entangler parameters.

Finally, the angle sweep evaluates several targets at seven parameter values. Small score differences should be treated descriptively rather than as separately tested inferential claims.

## Overall assessment

E9 provides the direct mechanistic test missing from the earlier structural experiments.

At zero mixer angle, all cubic graphs produce the same sorted probability distribution. The entangler has encoded the graph only in phase. The mixer converts those phases into measurable probability differences, and the analytic first-order expression matches the implemented circuit derivative on every tested graph.

The resulting graph geometry grows approximately linearly with (\beta) near zero, confirming first-order geometric emergence. The target-level decomposition is more structured: triangle count is nearly perfectly accessible from the second-order coefficient, while 4-cycles, longer cycles, girth, diameter, and spectral gap are only partially captured by the isolated first two orders.

The parameter sweep also shows that the principal QuIC hierarchy is not a fragile consequence of choosing (\beta=0.1). Triangle, 4-cycle, and girth prediction remain nearly saturated over the complete tested range. Five-cycle prediction remains strong, while 6-cycle and diameter accessibility increase substantially at larger mixer angles.

The appropriate central claim is:

> QuIC’s structural geometry is created by mixer-induced conversion of graph-dependent phases into measurement probabilities. The zero-mixer representation collapses across all cubic graphs, the analytic first-order probability coefficient is verified against the implemented circuit, and median graph separation grows linearly with (\beta) near zero. Triangle information is predominantly accessible through the second-order response, while deeper cycle and metric information develops across higher orders and becomes substantially more visible at larger mixer angles.



### E10 - High-Dimensional Probe Validation and Shuffled-Target Control

#### Experimental design

E10 tests whether the strongest full-vector ridge-probe results are genuine properties of the QuIC representation or artifacts of:

* one numerical solver;
* the high-dimensional regime;
* extremely small regularization values;
* or a pipeline capable of manufacturing positive out-of-sample scores from noise.

The analysis uses the complete connected cubic-graph censuses at:

* **509 graphs at (n=14)**;
* **4,060 graphs at (n=16)**.

Each graph is represented by its complete sorted QuIC probability vector:

$$
\mathbf p(G)\in\mathbb R^{2^n},
$$

with dimensions:

$$
2^{14}=16{,}384,
\qquad
2^{16}=65{,}536.
$$

No truncation is applied.

Four representative targets are selected:

* triangle count ((C_3)), as a near-exact positive control;
* 5-cycle count ((C_5)), as a strong nontrivial structural target;
* 6-cycle count ((C_6)), as a weaker and less stable target;
* diamond count, as the strongest result from the spectral-residual experiment.

Diamond count is computed directly and checked through the cubic sixth-moment identity:

$$
\operatorname{tr}(A^6)
======================

87n
+
6C_3
+
96C_4
+
12(C_6+D),
$$

where (D) is the number of diamonds.

The identity is verified exactly for every graph at both orders.

The experiment contains three principal arms.

1. **Independent solver agreement**

   The ridge predictions are recomputed through:

   * a centered economy-SVD implementation;
   * an independent dual Gram-matrix implementation.

   Both implementations use the same outer folds, inner folds, selected regularization parameter, and centered training data.

2. **Regularization-grid ablation**

   The complete grid is:

   $$
   \alpha\in
   {10^{-14},10^{-13},\ldots,10^2}.
   $$

   It is compared with a conservative grid beginning at:

   $$
   \alpha=10^{-8}.
   $$

3. **Shuffled-target control**

   The target values are permuted and the complete nested pipeline is rerun, including inner-fold selection of (\alpha).

   The shuffled control therefore tests the entire model-selection procedure rather than evaluating one fixed estimator after hyperparameter selection.

The outer folds are the frozen shuffled seed-0 folds used by the earlier probe experiments.

One implementation difference is important. The original recorded results were produced by `RidgeCV(cv=5)`, whose internal folds are unshuffled. The custom SVD and dual pipeline uses shuffled seed-0 inner folds. The custom arms therefore reproduce the same ridge estimator under a different inner-fold partition, not the exact original model-selection path.

#### Numerical implementation checks

Before the graph data are used, both custom ridge implementations are tested on synthetic data against sklearn ridge regression.

Across the tested synthetic regularization values, both implementations match sklearn predictions within:

$$
10^{-8}.
$$

On the complete QuIC datasets, the SVD and dual predictions agree to substantially tighter than the prespecified:

$$
10^{-6}
$$

tolerance.

##### (n=14)

| Target   | Worst SVD–dual prediction difference |
| -------- | -----------------------------------: |
| (C_3)    |                  (6.7\times10^{-13}) |
| (C_5)    |                  (9.9\times10^{-11}) |
| (C_6)    |                  (9.6\times10^{-10}) |
| Diamonds |                  (1.1\times10^{-11}) |

##### (n=16)

| Target   | Worst SVD–dual prediction difference |
| -------- | -----------------------------------: |
| (C_3)    |                  (8.3\times10^{-12}) |
| (C_5)    |                   (3.9\times10^{-9}) |
| (C_6)    |                   (5.6\times10^{-9}) |
| Diamonds |                  (7.2\times10^{-11}) |

The agreement establishes that the custom results do not depend on choosing either the primal SVD formulation or the dual sample-space formulation.

It does not by itself establish agreement with the original `RidgeCV` protocol, because the inner-fold partitions differ.

#### Solver and regularization results

##### (n=14)

| Target   | Recorded sklearn (R^2) | Live sklearn (R^2) | Custom SVD (R^2) | Custom dual (R^2) | Conservative grid (R^2) |
| -------- | ---------------------: | -----------------: | ---------------: | ----------------: | ----------------------: |
| (C_3)    |                  1.000 |              1.000 |            1.000 |             1.000 |                   0.953 |
| (C_5)    |                  0.928 |              0.928 |            0.937 |             0.937 |                   0.058 |
| (C_6)    |                  0.485 |              0.485 |            0.553 |             0.553 |                   0.192 |
| Diamonds |                  0.993 |              0.993 |            0.997 |             0.997 |                   0.562 |

The live sklearn arm exactly reproduces all four recorded (n=14) results.

This is the cleanest validation in E10. It confirms that the prior values can be regenerated from:

* the stored vectors;
* the stored targets;
* the original folds;
* the original alpha grid;
* and the original sklearn estimator.

The custom SVD and dual paths produce the same qualitative conclusions. Their values differ slightly because their inner folds are shuffled rather than matching sklearn’s unshuffled internal partitions.

The differences are small for:

* (C_3);
* (C_5);
* diamonds.

The custom (C_6) score is somewhat higher:

$$
0.553
\quad\text{versus}\quad
0.485.
$$

Both values indicate moderate but fold-sensitive accessibility.

##### (n=16)

| Target   | Recorded sklearn (R^2) | Custom SVD (R^2) | Custom dual (R^2) | Conservative grid (R^2) |
| -------- | ---------------------: | ---------------: | ----------------: | ----------------------: |
| (C_3)    |                  1.000 |            1.000 |             1.000 |                   0.996 |
| (C_5)    |                  0.982 |            0.893 |             0.893 |                   0.083 |
| (C_6)    |                  0.642 |         (-0.127) |          (-0.127) |                   0.174 |
| Diamonds |                  0.996 |            0.995 |             0.995 |                   0.629 |

No live sklearn arm is run at (n=16). The table compares the stored original results with the custom SVD and dual pipeline.

The custom results reproduce:

* exact triangle accessibility;
* near-exact diamond accessibility;
* strong, although reduced, 5-cycle accessibility.

For (C_5), the score changes from:

$$
0.982
\rightarrow
0.893.
$$

This is a meaningful numerical difference, but both inner-fold protocols support the qualitative conclusion that (C_5) is strongly decodable.

The (C_6) result does not reproduce:

$$
0.642
\rightarrow
-0.127.
$$

This is not a minor solver discrepancy. The SVD and dual implementations agree on the negative score, so the disagreement is not caused by choosing one linear-algebra formulation over the other.

The principal protocol difference is the inner-fold partition used to select (\alpha). The result therefore shows that the (n=16) (C_6) probe is highly sensitive to the model-selection path.

The original (R^2=0.642) value cannot be described as independently validated by E10.

#### Dependence on near-zero regularization

The full-grid models consistently select values near the bottom of the alpha grid.

##### (n=14)

| Target   | Selected full-grid values          | Selected conservative value |
| -------- | ---------------------------------- | --------------------------- |
| (C_3)    | (10^{-14}), (10^{-13}), (10^{-12}) | (10^{-8})                   |
| (C_5)    | (10^{-14}), (10^{-13})             | (10^{-8})                   |
| (C_6)    | (10^{-14}), (10^{-13})             | (10^{-8})                   |
| Diamonds | (10^{-14}), (10^{-13}), (10^{-12}) | (10^{-8})                   |

##### (n=16)

| Target   | Selected full-grid values | Selected conservative value |
| -------- | ------------------------- | --------------------------- |
| (C_3)    | (10^{-14})                | (10^{-8})                   |
| (C_5)    | (10^{-14}), (10^{-12})    | (10^{-8})                   |
| (C_6)    | (10^{-13}), (10^{-12})    | (10^{-8})                   |
| Diamonds | (10^{-14}), (10^{-13})    | (10^{-8})                   |

The conservative grid does not reproduce the principal structural scores.

At (n=14):

$$
C_5:
0.937
\rightarrow
0.058,
$$

and:

$$
D:
0.997
\rightarrow
0.562.
$$

At (n=16):

$$
C_5:
0.893
\rightarrow
0.083,
$$

and:

$$
D:
0.995
\rightarrow
0.629.
$$

The experiment therefore does not support a claim that the probe conclusions are robust to ordinary regularization scales.

Instead, the useful signal occupies low-variance directions that are strongly suppressed once (\alpha) reaches (10^{-8}).

#### Singular-spectrum diagnostic

The singular values of the centered training matrices explain the regularization behavior.

##### (n=14)

The fold-1 singular-value percentiles are:

|     Percentile |                   1 |                   5 |                  25 |                  50 |                  75 |                  95 |                  99 |
| -------------: | ------------------: | ------------------: | ------------------: | ------------------: | ------------------: | ------------------: | ------------------: |
| Singular value | (2.93\times10^{-9}) | (4.88\times10^{-9}) | (2.09\times10^{-8}) | (9.34\times10^{-8}) | (3.33\times10^{-7}) | (1.15\times10^{-5}) | (6.62\times10^{-5}) |

The fraction of singular directions satisfying:

$$
s_i^2>\alpha
$$

is:

| (\alpha)   | Retained fraction |
| ---------- | ----------------: |
| (10^{-12}) |             0.135 |
| (10^{-8})  |             0.005 |
| (10^{-4})  |             0.000 |

##### (n=16)

|     Percentile |                    1 |                    5 |                   25 |                  50 |                  75 |                  95 |                  99 |
| -------------: | -------------------: | -------------------: | -------------------: | ------------------: | ------------------: | ------------------: | ------------------: |
| Singular value | (5.92\times10^{-11}) | (9.19\times10^{-11}) | (4.43\times10^{-10}) | (1.74\times10^{-9}) | (9.98\times10^{-9}) | (5.88\times10^{-7}) | (1.59\times10^{-5}) |

The retained fractions are:

| (\alpha)   | Retained fraction |
| ---------- | ----------------: |
| (10^{-12}) |             0.034 |
| (10^{-8})  |             0.002 |
| (10^{-4})  |             0.000 |

Ridge regression shrinks singular direction (i) according to:

$$
\frac{s_i^2}{s_i^2+\alpha}.
$$

At:

$$
\alpha=10^{-8},
$$

almost every graph-varying direction is strongly suppressed.

The dependence on very small (\alpha) is therefore consistent with the numerical scale of the QuIC representation. It is not, by itself, evidence of a software error.

It does mean that the probe operates close to the interpolation regime and that its conclusions require explicit controls for overfitting and model-selection artifacts.

#### Shuffled-target results

The shuffled-target arm repeats the complete nested custom-SVD pipeline after independently permuting each target.

##### (n=14)

| Target   | Observed (R^2) | Null mean | Null 95th percentile | Null maximum | Permutations | Empirical (p) |
| -------- | -------------: | --------: | -------------------: | -----------: | -----------: | ------------: |
| (C_3)    |          1.000 |  (-0.014) |             (-0.004) |     (-0.002) |           25 |        0.0385 |
| (C_5)    |          0.937 |  (-0.016) |             (-0.003) |        0.000 |          100 |        0.0099 |
| (C_6)    |          0.553 |  (-0.018) |             (-0.005) |     (-0.005) |           25 |        0.0385 |
| Diamonds |          0.997 |  (-0.019) |             (-0.003) |        0.002 |           25 |        0.0385 |

Every observed (n=14) score exceeds every corresponding shuffled-target run.

The null scores remain at or below the constant-predictor floor even though the null models have access to the same near-zero alpha values as the observed models.

This is strong evidence that the large positive (n=14) scores are not automatically generated by:

* the high feature dimension;
* the near-interpolation alpha grid;
* or the nested model-selection procedure.

##### (n=16)

| Target   | Observed (R^2) | Null mean | Null 95th percentile | Null maximum | Permutations | Empirical (p) |
| -------- | -------------: | --------: | -------------------: | -----------: | -----------: | ------------: |
| (C_3)    |          1.000 |  (-0.002) |             (-0.000) |     (-0.000) |           25 |        0.0385 |
| (C_5)    |          0.893 |  (-0.002) |             (-0.000) |        0.001 |           25 |        0.0385 |
| (C_6)    |       (-0.127) |  (-0.002) |             (-0.000) |        0.001 |           25 |        1.0000 |
| Diamonds |          0.995 |  (-0.002) |             (-0.001) |     (-0.000) |           25 |        0.0385 |

The (n=16) shuffled controls validate the custom-pipeline results for:

* (C_3);
* (C_5);
* diamonds.

Each observed score exceeds every shuffled run.

The (C_6) result fails:

$$
R^2_{\mathrm{observed}}=-0.127,
$$

while the shuffled null is centered near:

$$
-0.002.
$$

The empirical result is:

$$
p=1.000.
$$

Thus, under the custom inner-fold protocol, (C_6) performs worse than the shuffled-target distribution.

This failure should not be hidden by a checklist restricted to (C_3), (C_5), and diamonds. It is direct evidence that the recorded (n=16) (C_6) result is protocol sensitive.

#### Interpretation of the permutation control

The permutation results answer a narrower question than the conservative-grid ablation.

They show that making near-zero regularization available does not automatically produce high positive out-of-sample (R^2) from arbitrary labels.

The results therefore support the statement:

> The strong (C_3), (C_5), and diamond probes exploit repeatable alignment between QuIC features and the graph targets rather than a generic tendency of the high-dimensional ridge pipeline to fit shuffled labels.

They do not support the stronger statement that:

> The results are insensitive to regularization or cross-validation choices.

That stronger statement is false.

The informative directions require near-zero regularization, and the (n=16) (C_6) score changes qualitatively when the inner-fold partition is changed.

#### What the experiment establishes

The completed results establish that:

1. **The original (n=14) probe results are exactly reproducible.**

   A live sklearn rerun recovers the recorded values for all four targets.

2. **Independent ridge formulations agree numerically.**

   The SVD and dual predictions agree to approximately (10^{-9}) or better on the real QuIC matrices.

3. **The strongest probe results are not generic high-dimensional artifacts.**

   Shuffled targets remain at or below the prediction floor under the same nested pipeline and alpha grid.

4. **The structural signal requires near-interpolation regularization.**

   Raising the alpha floor to (10^{-8}) removes most of the (C_5), (C_6), and diamond accessibility.

5. **The strong (n=16) (C_5) conclusion survives a change in inner-fold partition.**

   Its score decreases from (0.982) to (0.893) but remains strongly positive.

6. **The diamond result is highly stable.**

   It remains near exact under both custom solvers and at both graph orders.

7. **The recorded (n=16) (C_6) result is not validated.**

   Under the custom nested protocol, its score falls from (0.642) to (-0.127) and does not exceed the shuffled null.

E10 therefore validates the principal triangle, 5-cycle, and diamond probe results while exposing a genuine weakness in the 6-cycle result.

#### Necessary qualifications

The custom SVD and dual paths do not use the same inner folds as the original `RidgeCV(cv=5)` implementation.

Their agreement establishes estimator and numerical consistency under one common protocol. It does not constitute an exact independent reproduction of the original protocol.

A complete validation of the (n=16) recorded values requires either:

* a live sklearn rerun at (n=16);
* or custom SVD and dual paths using the exact unshuffled inner folds used by sklearn.

The synthetic sklearn validation tests alpha values down to:

$$
10^{-6},
$$

but not the:

$$
10^{-14}\text{--}10^{-12}
$$

range selected on the QuIC data.

The real-data SVD–dual agreement provides a stronger check at those scales, but both custom paths still use the same centered data and selected alpha values.

Most shuffled-target arms use only 25 permutations. Their empirical (p)-values therefore have minimum resolution:

$$
\frac{1}{25+1}
==============

0.0385.
$$

The C5 arm at (n=14) uses 100 permutations and has minimum resolution:

$$
\frac{1}{100+1}
===============

0.0099.
$$

These controls are adequate for detecting gross pipeline failure but do not provide precise tail probabilities.

The shuffled-target runs validate the custom SVD pipeline, not the exact original sklearn inner-fold protocol.

The conservative-grid failure should not be reframed as robustness. The observed signal is genuinely concentrated in low-singular-value directions.

The diamond result is a strong validation of QuIC accessibility beyond a linear spectral readout. It should not be described as proof of information beyond the complete adjacency spectrum. The exact cospectral audit found no diamond variation within the available cospectral groups.

The experiment uses ideal complete probability vectors. It does not address the finite-shot inaccessibility established by E7S.

Finally, E10 validates probe behavior rather than strengthening the underlying structural interpretation. It establishes that several large (R^2) values are genuine and repeatable under controlled estimators; it does not independently explain why the representation contains those targets.

#### Overall assessment

E10 provides a valuable but mixed validation result.

The strongest outcomes are clear:

* the complete (n=14) sklearn results reproduce exactly;
* independent SVD and dual implementations agree to high precision;
* shuffled targets remain at the prediction floor;
* triangle, 5-cycle, and diamond accessibility remains strong under the custom pipeline.

The experiment also establishes that the useful information occupies exceptionally low-variance directions. The strong structural scores disappear when the regularization floor is increased to (10^{-8}). Near-interpolation regularization is therefore a required feature of the analysis rather than an incidental implementation choice.

The principal negative result is the (n=16) 6-cycle probe. Its score changes from the recorded:

$$
0.642
$$

to:

$$
-0.127
$$

when the inner-fold partition changes. It also fails the shuffled-target comparison.

The appropriate central claim is:

> Independent SVD and dual ridge implementations, exact (n=14) sklearn reproduction, and full-pipeline shuffled-target controls confirm that QuIC’s triangle, 5-cycle, and diamond probe results are not numerical or high-dimensional chance artifacts. These signals require near-interpolation regularization because they occupy low-singular-value feature directions. The (n=16) 6-cycle result does not survive a change in the inner cross-validation partition and should be treated as protocol sensitive rather than validated.

