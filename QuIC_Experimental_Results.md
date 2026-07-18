### QuIC Characterization — Experimental Results

Full per-experiment write-ups for the AAAI 2027 QuIC characterization study: experimental design, results, what each experiment establishes, qualifications, and overall assessment, for every experiment E1 through E8B. This is a results record only — for the object definition, mathematical framework, project status, and the direction the work is currently taking, see the companion project-state document.

### Full Description of Experiments

### E1 - Stratified Residue

#### Experimental design

The experiment analyzes the complete connected cubic-graph censuses at two graph orders:

* **509 graphs at (n=14)**;
* **4,060 graphs at (n=16)**.

Each graph is represented by its full sorted QuIC probability vector:

$\mathbf p(G)\in\mathbb R^{2^n},$

with dimensions

$$
2^{14}=16{,}384,\qquad2^{16}=65{,}536.
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
\text{all graphs}\rightarrow\text{fixed triangle count}\rightarrow\text{fixed triangle and 4-cycle counts}.
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
\rho_{\triangle}=0.903\quad\text{and}\quad0.900.
$$

The replication is unusually close. Increasing the census from 509 to 4,060 graphs changes the global triangle correlation by only (0.003).

The 4-cycle association is weaker globally but also stable:

$$
0.290 \rightarrow 0.303.
$$

The global 5-cycle association remains positive and statistically detectable but is small:

$$
0.109\quad\text{at }n=14,
$$

and

$$
0.079 \quad\text{at }n=16.
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
\rho_{\mathrm{C4}}\in \[0.898,0.968\].
$$

At (n=16),

$$
\rho_{\mathrm{C4}} \in \[0.853,0.964\].
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
  -0.978   \quad\text{and}\quad  -0.988.
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
|\rho| = 0.978\text{--}0.985.
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
\rho_{\mathrm{C5}} \in \[0.316,0.926\].
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
\rho_{\mathrm{C5}} \in \[0.193,0.974\].
$$

Every association is positive, and 42 of the 43 strata have permutation:

$$
p<0.05.
$$

The only nonsignificant stratum is the smallest and weakest reported case:

$$
(C_3,C_4)=(5,5), \qquad n=12, \qquad \rho=0.193, \qquad p=0.1463.
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
\boxed{ \text{triangles} \rightarrow \text{4-cycles} \rightarrow \text{5-cycles} }
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
10^{-20} \quad\text{or}\quad 10^{-101}
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
2^{14}=16{,}384, \qquad 2^{16}=65{,}536.
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
C_3,\ C_4;\rightarrow; C_5 ;\rightarrow; C_6,
$$

with progressively weaker and less stable linear accessibility as cycle length increases.

#### QuIC probability power sums

The next experiment tests whether the full-vector results can be reduced to a small number of global probability moments.

Using only

$$
\sum_z p_z^2,\qquad \sum_z p_z^3,\qquad \sum_z p_z^4,
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
\text{4-cycle information saturates when } \sum_z p_z^5 \text{ is added}.
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
R^2=0.143\pm0.103 \quad\text{at }n=14,
$$

and

$$
R^2=0.132\pm0.015 \quad\text{at }n=16.
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
R^2_{\mathrm{moments}}=0.060 \quad\text{at }n=14,
$$

and

$$
R^2_{\mathrm{moments}}=0.052 \quad\text{at }n=16.
$$

The full adjacency spectrum explains more:

$$
R^2_{\mathrm{spectrum}}=0.195 \quad\text{and}\quad 0.275,
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
R^2=-0.028 \quad\text{at }n=14,
$$

and

$$
R^2=-0.003 \quad\text{at }n=16.
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
(79,458),\qquad(201,203),\qquad(234,239).
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
0.00077,\qquad0.0611,\qquad5.817.
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
0.0\text{th},\qquad 10.9\text{th},\qquad92.7\text{th}
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
\boxed{ \text{a dominant spectral backbone} + \text{a smaller non-spectral residue} }
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
\Delta R^2 = R^2_{\text{QuIC+spec}} - \max\left( R^2_{\text{eigenvalues}}, R^2_{\text{moments}} \right).
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
C_5= \frac{ 	ext{tr}(A^5)-10	ext{tr}(A^3) }{10}.
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
\lambda_{\max}=3, \qquad \text{gap}=3-\lambda_2.
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
R^2=0.485\pm0.326 \quad\text{at }n=14,
$$

and

$$
R^2=0.642\pm0.122 \quad\text{at }n=16.
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
R^2=0.993\pm0.014 \quad\text{at }n=14,
$$

and

$$
R^2=0.999\pm0.003 \quad\text{at }n=16.
$$

The linear spectral baselines are much weaker. The best spectral score is only $0.611$ at $n=14$ and $0.543$ at $n=16$.

This produces the largest nominal improvements:

$$
\Delta R^2=+0.382 \quad\text{and}\quad +0.456.
$$

However, these large values should not be interpreted as evidence that girth is non-spectral. Within these censuses, girth is determined by the presence or absence of short cycles and is therefore a nonlinear threshold function of spectrally determined cycle counts.

The girth result instead shows that QuIC provides a coordinate system in which this nonlinear spectral property is nearly linearly accessible. The concatenated model does not improve on QuIC; it simply retains QuIC's near-perfect score.

This is strong evidence for favorable representation geometry, but not for information absent from the spectrum.

#### Diameter

Diameter is the clearest open structural target.

At $n=14$:

$$
R^2_{\text{QuIC}}=0.548, \qquad R^2_{\text{moments}}=0.711, \qquad R^2_{\text{combined}}=0.741.
$$

At $n=16$:

$$
R^2_{\text{QuIC}}=0.737, \qquad R^2_{\text{moments}}=0.775, \qquad R^2_{\text{combined}}=0.802.
$$

The resulting improvements are modest but consistent:

$$
\Delta R^2=+0.030 \quad\text{at }n=14,
$$

and

$$
\Delta R^2=+0.026 \quad\text{at }n=16.
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
   $$
   
   ===========================
   $$
   \hat y_{\mathrm{spectrum}}    +    \hat r_{\mathrm{QuIC}}. 
   $$

The primary statistic is

$$
\Delta R^2 = R^2_{\mathrm{two-stage}} - R^2_{\mathrm{spectrum}}.
$$

A positive value indicates that QuIC predicts variation missed by the linear spectral model.

The experiment also reports residual-space (R^2):

$$
R^2_{\mathrm{residual}} =  R^2 \left( y-\hat y_{\mathrm{spectrum}}, \hat r_{\mathrm{QuIC}}\right).
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
	ext{tr}(A^6) =
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
$$

-----------------------------
$$
p^{\mathrm{stored}}_z(G) \right| =

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
\left| \mathbf p_{\mathrm{float64}}(G)
$$

-------------------------------
$$
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
\text{floor ratio} =

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
c_{t+1}(u,v) =

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
\mathbf h_{\mathrm{cumulative}}(G) =

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
	ext{tr}(A^4) = 8C_4+2\sum_v d_v^2
$$

-------------
$$
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
R^2_{\mathrm{moments}} =

0.802,\ 0.716,\ 0.707,\ 0.625
$$

across S1 through S4.

The decline from S1 to S4 suggests that the moment coordinates become less sufficient as the degree distribution permits more heterogeneous local configurations. This is descriptive rather than a monotonic theorem, but the pattern is consistent across the selected strata.

QuIC alone does not retain the strong C5 accessibility observed on cubic graphs:

$$
R^2_{\mathrm{QuIC}}=

-0.017,\ 0.284,\ -0.019,\ -0.050.
$$

Only the bimodal stratum contains a meaningful standalone signal.

The concatenated representation gives a more nuanced result.

For the two maximum-degree-4 strata:

$$
\Delta R^2_{\mathrm{concat}}=

+0.061
\quad\text{and}\quad
+0.118.
$$

In S1, QuIC has essentially no standalone C5 accessibility but improves the eigenvalue representation enough to exceed the stronger moment baseline. This indicates conditional or complementary structure that is not useful in isolation.

In S2, QuIC has both a moderate standalone signal and a larger complementary contribution.

The result does not persist in the more degree-skewed strata:

$$
\Delta R^2_{\mathrm{concat}}=

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
\Delta R^2_{\mathrm{concat}}=

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
R^2_{\mathrm{moments}}=

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
\Delta R^2_{\mathrm{concat}}=

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
$$

=====================
$$
0.879\pm0.023.
$$

This exceeds the strongest spectral baseline:

$$
R^2_{\mathrm{moments}}
$$

======================
$$
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
$$

============================
$$
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
$$

===========
$$
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
\mathbf p(G)=

\left(
p_{(1)},p_{(2)},\ldots,p_{(2^n)}
\right),
\qquad
p_{(1)}\ge p_{(2)}\ge\cdots.
$$

The truncated representation is

$$
\mathbf p_k(G)=

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
	ext{tr}(A^6)=

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
W(G)=

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
f(\mathbf p_i-\mathbf p_j)=

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
\text{empirical 5/50/95 percentiles}=

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
$$

=====================
$$
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
$$

=============
$$
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
$$

======
$$
\sum_i
	ext{Im}
\left[
\overline{\phi(y)}
\phi(y\oplus e_i)
\right],
$$

where (y\oplus e_i) denotes the bitstring obtained by flipping bit (i).

The notebook independently estimates the derivative using the central difference

$$
D_1^{(h)}(y)
$$

============
$$
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
$$

======
$$
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
$$

==========
$$
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
$$

=========
$$
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
$$

=========
$$
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
	ext{tr}(A^6)
$$

======================
$$
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
$$

==============
$$
0.0385.
$$

The C5 arm at (n=14) uses 100 permutations and has minimum resolution:

$$
\frac{1}{100+1}
$$

===============
$$
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

### E11 - Nonlinear Spectral Adequacy and the Diamond Residual

#### Experimental design

E11 tests whether QuIC’s diamond-count advantage over the spectral baseline survives when the first-stage spectral model is allowed to be nonlinear.

The analysis uses the complete connected cubic-graph censuses at:

* **509 graphs at (n=14)**;
* **4,060 graphs at (n=16)**.

E2R used a linear spectral first stage and found that adding a QuIC residual model improved diamond-count prediction by:

$$
\Delta R^2=+0.341\quad\text{at }n=14,
$$

and:

$$
\Delta R^2=+0.310\quad\text{at }n=16.
$$

A linear spectral baseline leaves two possible interpretations.

1. QuIC contains information that the tested spectral representation does not make available.
2. The diamond target is already encoded nonlinearly in the spectrum, and QuIC merely provides a more favorable linear coordinate system.

E11 distinguishes these possibilities empirically by replacing the linear spectral model with progressively more flexible nonlinear predictors.

The tested first-stage models are:

1. linear ridge regression;
2. degree-two polynomial ridge regression;
3. radial-basis-function kernel ridge regression;
4. ExtraTrees regression.

Each model performs its own hyperparameter selection within the outer training fold.

Three spectral feature sets are evaluated:

1. sorted adjacency eigenvalues, excluding the constant cubic eigenvalue (\lambda_{\max}=3);
2. trace moments (\text{tr}(A^k)) for (k=3,\ldots,8);
3. eigenvalues concatenated with the trace moments.

The third set reproduces the spectral representation used in E2R.

The targets are:

* diamond count;
* 6-cycle count;
* girth;
* triangle count.

Triangle count is included as an exact spectral control. On cubic graphs:

$$
\text{tr}(A^3)=6C_3.
$$

Diamond count and 6-cycle count are linked through:

$$
\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).
$$

The spectrum therefore fixes:

$$
C_6+D,
$$

but does not generally determine how that total is divided between 6-cycles and diamonds.

#### Two-stage protocol

The experiment retains the E2R residual-learning design.

For each frozen outer fold:

1. the spectral model is fitted on the outer training graphs;
2. five-fold cross-fitted spectral predictions are generated within the outer training set;
3. the cross-fitted residual target is computed;
4. a QuIC ridge model is trained to predict that residual;
5. the final held-out prediction is the sum of the spectral and QuIC residual predictions.

For graph (G), the combined predictor has the form:

$$
\widehat y_{\text{combined}}(G)=\widehat y_{\text{spectral}}(G)+\widehat r_{\text{QuIC}}(G).
$$

The principal statistic is:

$$
\Delta R^2=R^2_{\text{combined}}-R^2_{\text{spectral}}.
$$

A positive value means that the QuIC residual stage improves held-out prediction beyond the chosen spectral model.

The QuIC residual stage uses the first:

$$
k=1000
$$

sorted probability coordinates.

The earlier truncation experiments showed that the diamond signal is effectively saturated at this depth. The notebook also reruns the original full-vector E2R diamond cell as a validation gate.

#### Target and feature validation

All target values are recomputed directly from the stored adjacency matrices.

For every graph at both orders, the notebook verifies:

$$
\text{tr}(A^3)=6C_3,
$$

and:

$$
\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).
$$

Each QuIC vector is checked to be:

* descending sorted;
* normalized to unit sum;
* consistent with the expected census size.

The constructed datasets contain:

* 509 validated graphs at (n=14);
* 4,060 validated graphs at (n=16).

#### E2R validation gate

Before the nonlinear grid is interpreted, the notebook reproduces the E2R linear-ridge diamond result using:

* eigenvalues plus traces;
* complete QuIC vectors;
* the same outer folds;
* the same ridge grid.

The validation results are:

| Census | Spectral (R^2) | QuIC gain (\Delta R^2) |
| ------ | -------------: | ---------------------: |
| (n=14) |          0.585 |               (+0.341) |
| (n=16) |          0.636 |               (+0.310) |

Both values reproduce the E2R record at displayed precision.

The corresponding combined scores are:

$$
R^2_{\text{combined}}=0.926\quad\text{at }n=14,
$$

and:

$$
R^2_{\text{combined}}=0.946\quad\text{at }n=16.
$$

The same linear-stage gains are obtained when the QuIC representation is truncated to the first 1,000 coordinates:

$$
\Delta R^2=+0.341\quad\text{and}\quad+0.310.
$$

The nonlinear grid therefore compares first-stage spectral capacity at a QuIC depth that retains the complete observed diamond advantage.

#### Diamond-count results

##### (n=14)

| Spectral features       | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| ----------------------- | -----------: | ---------------: | ---------: | ---------: |
| Eigenvalues             |     (+0.425) |         (+0.119) |   (+0.111) |   (+0.050) |
| Traces                  |     (+0.336) |         (+0.073) |   (+0.135) |   (+0.176) |
| Eigenvalues plus traces |     (+0.341) |         (+0.108) |   (+0.099) |   (+0.064) |

##### (n=16)

| Spectral features       | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| ----------------------- | -----------: | ---------------: | ---------: | ---------: |
| Eigenvalues             |     (+0.406) |         (+0.181) |   (+0.132) |   (+0.057) |
| Traces                  |     (+0.386) |         (+0.188) |   (+0.145) |   (+0.195) |
| Eigenvalues plus traces |     (+0.310) |         (+0.169) |   (+0.141) |   (+0.063) |

The diamond gain remains positive in every tested cell:

$$
24/24.
$$

The smallest observed gains are:

$$
\Delta R^2=+0.050\quad\text{at }n=14,
$$

and:

$$
\Delta R^2=+0.057\quad\text{at }n=16.
$$

The nonlinear models substantially reduce the original linear-stage advantage, but they do not eliminate it.

Using the complete spectral feature set, the gains are:

| Census | Polynomial ridge | RBF kernel | ExtraTrees |
| ------ | ---------------: | ---------: | ---------: |
| (n=14) |         (+0.108) |   (+0.099) |   (+0.064) |
| (n=16) |         (+0.169) |   (+0.141) |   (+0.063) |

The persistence replicates across both exhaustive censuses and across three distinct nonlinear model families.

#### RBF results with the complete spectral feature set

The notebook reports full details for the RBF kernel model using eigenvalues plus traces.

##### (n=14)

| Quantity                  |   Result |
| ------------------------- | -------: |
| Spectral (R^2)            |    0.829 |
| Spectral plus QuIC (R^2)  |    0.928 |
| QuIC residual-space (R^2) |    0.581 |
| QuIC alone (R^2)          |    0.993 |
| QuIC gain (\Delta R^2)    | (+0.099) |

The mean reduction in absolute held-out error is:

$$
0.0506,
$$

with graph-level bootstrap interval:

$$
[0.0381,0.0635].
$$

##### (n=16)

| Quantity                  |   Result |
| ------------------------- | -------: |
| Spectral (R^2)            |    0.792 |
| Spectral plus QuIC (R^2)  |    0.933 |
| QuIC residual-space (R^2) |    0.668 |
| QuIC alone (R^2)          |    0.996 |
| QuIC gain (\Delta R^2)    | (+0.141) |

The mean reduction in absolute held-out error is:

$$
0.0620,
$$

with graph-level bootstrap interval:

$$
[0.0574,0.0669].
$$

Both intervals remain entirely positive.

The improvement is therefore not produced by a small number of extreme folds or graphs. Across the held-out predictions, the combined model reduces absolute error on average.

#### Interpretation of the diamond result

The nonlinear spectral models recover considerably more diamond information than the original linear model.

At (n=14), for example, the RBF spectral score rises from:

$$
0.585
$$

to:

$$
0.829.
$$

The ExtraTrees score reported in the notebook’s dry-run record reaches:

$$
0.871.
$$

This confirms that a substantial portion of diamond count is encoded nonlinearly in the adjacency spectrum.

QuIC nevertheless improves prediction beyond each tested nonlinear model.

The strongest conclusion supported directly by E11 is:

> QuIC provides predictive complementarity to the tested nonlinear spectral models for diamond count.

E11 alone does not prove that the additional predictive signal lies outside the complete adjacency spectrum.

At (n=14) and (n=16), the exact cospectral audit found no diamond variation within the available cospectral groups. Within these finite censuses, diamond count is therefore compatible with being a function of the complete spectrum, even if the tested models do not learn that function perfectly.

The later (n=18) experiment supplies the direct information-theoretic witness. E14 identifies exact cospectral pairs with different diamond counts and shows that QuIC consistently ranks them.

The experiments therefore play different roles:

* E11 shows persistence beyond several strong nonlinear spectral predictors;
* E14 shows that diamond count is not universally determined by the complete spectrum.

#### Six-cycle results

##### (n=14)

| Spectral features       | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| ----------------------- | -----------: | ---------------: | ---------: | ---------: |
| Eigenvalues             |     (+0.020) |         (+0.005) |   (+0.002) |   (+0.014) |
| Traces                  |     (+0.014) |         (+0.003) |   (+0.006) |   (+0.003) |
| Eigenvalues plus traces |     (+0.008) |         (-0.000) |   (+0.003) |   (-0.001) |

##### (n=16)

| Spectral features       | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| ----------------------- | -----------: | ---------------: | ---------: | ---------: |
| Eigenvalues             |     (+0.072) |         (+0.013) |   (+0.004) |   (+0.034) |
| Traces                  |     (+0.015) |         (+0.008) |   (+0.007) |   (+0.002) |
| Eigenvalues plus traces |     (+0.012) |         (+0.005) |   (+0.006) |   (+0.027) |

The C6 gains are small throughout the grid.

Using eigenvalues plus traces, the nonlinear gains lie between approximately:

$$
-0.001\quad\text{and}\quad+0.027.
$$

At (n=14), the ExtraTrees combined-feature result is slightly negative:

$$
\Delta R^2=-0.001.
$$

The C6 residual therefore largely disappears once nonlinear spectral capacity is introduced.

This contrasts sharply with diamond count, even though both quantities enter the sixth spectral moment through:

$$
C_6+D.
$$

The result suggests that the tested nonlinear spectral models can recover most of the predictable C6 component, while QuIC retains a more substantial advantage for the complementary diamond direction.

The small C6 values should also be interpreted alongside E10, which found that the (n=16) full-vector C6 probe is sensitive to the inner cross-validation partition.

E11 provides no strong evidence for robust C6 complementarity.

#### Girth results

##### (n=14)

| Spectral features       | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| ----------------------- | -----------: | ---------------: | ---------: | ---------: |
| Eigenvalues             |     (+0.284) |         (+0.071) |   (+0.139) |   (+0.110) |
| Traces                  |     (+0.602) |         (+0.219) |   (+0.109) |   (+0.000) |
| Eigenvalues plus traces |     (+0.223) |         (+0.072) |   (+0.091) |   (+0.001) |

##### (n=16)

| Spectral features       | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| ----------------------- | -----------: | ---------------: | ---------: | ---------: |
| Eigenvalues             |     (+0.401) |         (+0.116) |   (+0.001) |   (+0.074) |
| Traces                  |     (+0.615) |         (+0.296) |   (+0.001) |   (-0.000) |
| Eigenvalues plus traces |     (+0.302) |         (+0.097) |   (+0.010) |   (+0.000) |

The linear-stage girth gains are large:

$$
\Delta R^2=+0.223\quad\text{at }n=14,
$$

and:

$$
\Delta R^2=+0.302\quad\text{at }n=16
$$

using the complete spectral feature set.

These gains shrink substantially as the spectral model becomes nonlinear.

Under ExtraTrees with eigenvalues plus traces, the remaining gains are:

$$
+0.001\quad\text{and}\quad+0.000.
$$

The RBF result at (n=16) is also only:

$$
+0.010.
$$

The large linear E2R girth residual is therefore primarily a linearization effect. A flexible nonlinear spectral model recovers nearly all of the predictive advantage.

The (n=14) RBF and eigenvalue-only ExtraTrees cells retain moderate positive gains, but the persistence depends strongly on the model and spectral feature set. It does not reproduce the uniform diamond pattern.

#### Triangle control

##### (n=14)

| Spectral features       | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| ----------------------- | -----------: | ---------------: | ---------: | ---------: |
| Eigenvalues             |     (+0.006) |         (+0.000) |   (-0.000) |   (+0.030) |
| Traces                  |     (+0.000) |         (+0.000) |   (+0.000) |   (+0.000) |
| Eigenvalues plus traces |     (+0.000) |         (+0.000) |   (+0.000) |   (-0.000) |

##### (n=16)

| Spectral features       | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| ----------------------- | -----------: | ---------------: | ---------: | ---------: |
| Eigenvalues             |     (+0.006) |         (+0.000) |   (+0.000) |   (+0.013) |
| Traces                  |     (+0.000) |         (+0.000) |   (+0.000) |   (-0.000) |
| Eigenvalues plus traces |     (+0.000) |         (+0.000) |   (+0.000) |   (-0.000) |

When trace moments are supplied, the QuIC gain is zero at displayed precision for every model.

This is the expected result because:

$$
C_3=\frac{\text{tr}(A^3)}{6}.
$$

The triangle control shows that the residual pipeline does not generically add positive performance after an exact spectral coordinate has already solved the target.

The small eigenvalue-only ExtraTrees gains do not undermine the control. They reflect imperfect learning from the sorted eigenvalues rather than missing information, since the eigenvalues determine the trace exactly.

#### Target-specific comparison

The complete-feature deltas provide the cleanest comparison.

##### (n=14)

| Target   | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| -------- | -----------: | ---------------: | ---------: | ---------: |
| Diamonds |     (+0.341) |         (+0.108) |   (+0.099) |   (+0.064) |
| (C_6)    |     (+0.008) |         (-0.000) |   (+0.003) |   (-0.001) |
| Girth    |     (+0.223) |         (+0.072) |   (+0.091) |   (+0.001) |
| (C_3)    |     (+0.000) |         (+0.000) |   (+0.000) |   (-0.000) |

##### (n=16)

| Target   | Linear ridge | Polynomial ridge | RBF kernel | ExtraTrees |
| -------- | -----------: | ---------------: | ---------: | ---------: |
| Diamonds |     (+0.310) |         (+0.169) |   (+0.141) |   (+0.063) |
| (C_6)    |     (+0.012) |         (+0.005) |   (+0.006) |   (+0.027) |
| Girth    |     (+0.302) |         (+0.097) |   (+0.010) |   (+0.000) |
| (C_3)    |     (+0.000) |         (+0.000) |   (+0.000) |   (-0.000) |

Diamond count is the only target with a substantial positive gain across:

* both graph orders;
* every model family;
* every spectral feature set.

C6 is largely spectral under the tested models.

Girth is highly accessible from QuIC but its advantage over the spectrum mostly disappears once nonlinear spectral models are used.

Triangle count behaves as an exact null control.

The persistence is therefore target specific rather than a generic benefit of adding a second high-dimensional model.

#### Model capacity and feature-set effects

The diamond gain generally shrinks as the first-stage model becomes more expressive.

Using eigenvalues plus traces at (n=14):

$$
+0.341\rightarrow+0.108\rightarrow+0.099\rightarrow+0.064.
$$

At (n=16):

$$
+0.310\rightarrow+0.169\rightarrow+0.141\rightarrow+0.063.
$$

The reduction is expected. Stronger spectral models absorb the portion of the target that can be predicted from spectral correlations.

The remaining gain is not monotone across every feature-set row. For example, ExtraTrees using traces alone leaves a larger diamond residual than ExtraTrees using eigenvalues.

This does not indicate that traces contain more spectral information. The complete eigenvalue vector determines every trace moment. It indicates that the model’s ability to exploit a representation depends on:

* feature dimension;
* scaling;
* sample size;
* and the selected hyperparameter family.

The most informative cells are therefore those using the complete eigenvalue-plus-trace representation rather than the largest raw delta across all feature sets.

#### Relationship to E2R, E10, and E14

E2R established a large QuIC gain over a linear spectral first stage.

E11 shows that the diamond gain becomes smaller but remains positive after introducing nonlinear spectral models.

E10 established that the strong diamond probe:

* reproduces across independent ridge implementations;
* exceeds shuffled-target controls;
* and depends on low-variance QuIC directions.

E14 later supplies the direct exact-cospectral witness missing from E11. At (n=18), six exact cospectral pairs differ in diamond count and QuIC ranks all six correctly.

Together, the experiments support a layered conclusion:

1. **E2R:** QuIC predicts diamonds beyond a linear spectral readout.
2. **E11:** QuIC improves upon several nonlinear spectral predictors.
3. **E10:** the QuIC diamond probe is not a shuffled-target or solver artifact.
4. **E14:** diamond count genuinely varies beyond the complete adjacency spectrum and QuIC aligns with that variation.

E11 is therefore an adequacy test of practical nonlinear spectral baselines, while E14 supplies the information-theoretic separation.

#### What the experiment establishes

The completed results establish that:

1. **The E2R diamond result reproduces.**

   The full-vector validation gate recovers the recorded linear spectral scores and QuIC gains at both graph orders.

2. **The first 1,000 QuIC probabilities retain the complete linear-stage diamond gain.**

3. **Nonlinear spectral models recover substantial diamond structure.**

   The spectral first-stage score rises well above the original linear baseline.

4. **QuIC still improves every tested nonlinear diamond model.**

   All 24 model, feature-set, and graph-order cells have positive (\Delta R^2).

5. **The strongest complete-feature nonlinear baselines retain replicated QuIC gains.**

   The RBF gains are (+0.099) and (+0.141), while the ExtraTrees gains are (+0.064) and (+0.063).

6. **The RBF combined models reduce held-out absolute error at both graph orders.**

   Both bootstrap intervals remain entirely positive.

7. **The persistence is target specific.**

   C6 gains are small, girth gains largely disappear under strong nonlinear models, and triangle gains are zero when its exact trace coordinate is supplied.

8. **E11 establishes nonlinear predictive complementarity, not by itself information beyond the complete spectrum.**

The experiment closes the linear-baseline objection while preserving the distinction between model inadequacy and genuine non-spectral information.

#### Necessary qualifications

The tested nonlinear models are strong practical baselines, but they do not exhaust all possible functions of the adjacency spectrum.

Failure of:

* polynomial ridge;
* one RBF kernel grid;
* or one ExtraTrees grid

does not prove that no spectral function can recover the target.

This qualification is particularly important at (n=14) and (n=16). The exact cospectral groups at these orders do not vary in diamond count. A sufficiently expressive spectral predictor could therefore, in principle, recover diamond count on these finite censuses.

The direct beyond-spectrum claim depends on the later (n=18) exact-cospectral witnesses, not on E11 alone.

The nonlinear hyperparameter grids are limited.

The RBF search uses:

$$
\alpha\in{10^{-4},10^{-3},\ldots,10^1},
$$

and:

$$
\gamma\in{10^{-3},10^{-2},\ldots,10^1}.
$$

ExtraTrees tests:

* three maximum-depth settings;
* two minimum-leaf settings;
* 300 trees.

A larger or differently regularized search could change the first-stage ceilings.

The preprocessing is not fully nested within the internal hyperparameter searches. The `StandardScaler` is fitted before `RidgeCV` or `GridSearchCV` performs its internal folds.

This introduces mild unsupervised leakage within the outer training set during hyperparameter selection. It does not expose outer test data, but a stricter implementation would place preprocessing inside the inner cross-validation estimator.

The trace moments are redundant once the complete eigenvalue vector is available. Their inclusion reproduces E2R and supplies direct low-order coordinates, but eigenvalues plus traces do not contain more information than the eigenvalues alone.

The graph-level bootstrap resamples fixed out-of-fold errors. It does not retrain the spectral and QuIC models within each bootstrap draw.

The intervals therefore quantify variation across held-out graph errors under the fitted cross-validation procedure, not the complete uncertainty from model refitting and fold selection.

The notebook evaluates:

$$
4\text{ targets}\times3\text{ feature sets}\times4\text{ models}\times2\text{ graph orders}.
$$

No multiple-comparison correction is applied. The primary diamond hypothesis and the complete-feature RBF and ExtraTrees cells were identified in advance, but small secondary differences should remain descriptive.

The ridge residual stage uses the same near-zero regularization grid examined in E10. The diamond result survived shuffled-target controls there, but E11 does not repeat those controls for every nonlinear first-stage model.

The nonlinear spectral models and the QuIC residual model are not matched in representational dimension or computational cost. The experiment evaluates predictive adequacy rather than resource efficiency.

All analyses use exact ideal probabilities. E7S shows that the corresponding structural information is not necessarily accessible at practical shot budgets.

Finally, the experiment concerns:

* connected cubic graphs;
* (n=14) and (n=16);
* one canonical circuit configuration;
* one fixed QuIC truncation depth.

The result should not be generalized to arbitrary graph families or circuit parameters.

#### Overall assessment

E11 resolves the principal weakness of the original spectral-residual experiment.

The diamond advantage is not merely an artifact of comparing QuIC with linear regression on spectral features. Polynomial ridge, RBF kernel regression, and ExtraTrees all recover additional nonlinear spectral structure, but QuIC continues to improve held-out prediction.

Using eigenvalues plus trace moments, the QuIC gains remain:

$$
+0.099\quad\text{and}\quad+0.141
$$

over the RBF models, and:

$$
+0.064\quad\text{and}\quad+0.063
$$

over ExtraTrees.

The result replicates across both complete cubic censuses. The paired absolute-error reductions under the RBF models are also positive with nonoverlapping-zero bootstrap intervals.

The controls sharpen the interpretation. C6 gains nearly vanish, girth gains largely collapse under nonlinear spectral models, and triangle count shows no residual once its exact spectral coordinate is included. The diamond persistence is therefore target specific rather than a generic consequence of stacking QuIC after another model.

E11 should not be presented as standalone proof that QuIC contains information outside the complete spectrum. At these graph orders, the exact cospectral classes do not vary in diamond count. The experiment instead demonstrates robust complementarity to the tested nonlinear spectral predictors. E14 later supplies the direct exact-cospectral proof.

The appropriate central claim is:

> Across the exhaustive connected cubic censuses at (n=14) and (n=16), QuIC improves diamond-count prediction beyond linear ridge, polynomial ridge, RBF kernel, and ExtraTrees models trained on adjacency eigenvalues and trace moments. The gain remains positive in all 24 tested diamond configurations and replicates at approximately (+0.06) to (+0.14) over the strongest complete-feature nonlinear baselines. The effect is target specific: C6 residual gains are negligible, girth gains largely disappear under nonlinear spectral models, and triangle gains vanish when its exact trace coordinate is supplied. E11 therefore establishes predictive complementarity to strong nonlinear spectral baselines, while the later exact-cospectral witnesses are required for the stronger beyond-spectrum claim.

### E12 - Minimal Automorphism-Ordering Audit

#### Execution status

E12 did not complete.

The notebook was terminated when it reached the environment’s:

$$12\text{-hour compute limit}.$$

This limit exists to prevent a single experiment from consuming compute indefinitely. The notebook did not stop because of a methodological assertion, numerical exception, or detected error.

Before the timeout, it completed:

* census and target validation;
* construction of the 14 automorphism-varying cospectral pairs;
* the complete exact permutation null for the primary QuIC model;
* the observed QuIC regularization profile.

It did not complete:

* the folklore 2-WL comparison;
* the spectrum-tied control;
* the final comparison tables;
* or result persistence.

E12 must therefore be treated as a timed-out partial experiment rather than a completed baseline comparison.

#### Experimental purpose

E12 tests whether QuIC orders exact adjacency-cospectral graphs by automorphism-group size.

The experiment uses the complete connected cubic census at:

* **(n=16)**;
* **4,060 graphs**;
* **41 exact adjacency-cospectral groups**;
* **83 members of those groups**.

Among the 41 cospectral groups, exactly:

$$14$$

vary in:

$$\log_2|\text{Aut}(G)|.$$

Every varying group contains exactly two graphs. The experiment therefore contains 14 independent held-out group comparisons.

#### Representation and ranking protocol

The representation is the first:

$$k=100$$

coordinates of the descending-sorted exact QuIC probability vector.

For each cospectral pair $$(G_i,G_j)$$, the ranker receives the antisymmetric difference:

$$\mathbf x_{ij}=\mathbf p_{1:100}(G_i)-\mathbf p_{1:100}(G_j),$$

with label:

$$y_{ij}=\text{sign}\left(\log_2|\text{Aut}(G_i)|-\log_2|\text{Aut}(G_j)|\right).$$

The model is:

* intercept-free logistic regression;
* train-only root-mean-square scaling;
* leave-one-cospectral-group-out evaluation;
* fixed primary regularization $$C=1$$.

The primary statistic is the number of correctly ordered held-out groups:

$$T_{\text{sign}}.$$

Because every group contains only two members, the proposed Kendall statistic contains no additional information:

$$T_\tau=2T_{\text{sign}}-14.$$

#### Exact permutation null

The null independently permutes the two target assignments within each cospectral group.

With 14 two-member groups, the complete null contains:

$$2^{14}=16{,}384$$

label configurations.

The logistic ranker is refitted for every configuration at the fixed primary value:

$$C=1.$$

This exact null was computationally expensive but completed before the notebook reached the 12-hour limit.

#### Completed QuIC result

At the prespecified setting:

$$C=1,$$

QuIC correctly orders:

$$11/14$$

cospectral groups.

The corresponding statistics are:

$$T_{\text{sign}}=11,$$

and:

$$T_\tau=8.$$

The exact one-sided permutation value is:

$$p=0.0581.$$

The null distribution has:

$$\text{mean}(T_{\text{sign}})=7,$$

and a reported 95th percentile of:

$$11.$$

The observed value therefore lies at the edge of the upper null tail but does not reject the null at:

$$p<0.05.$$

The defensible completed result is:

> QuIC shows suggestive automorphism-ordering ability within exact cospectral pairs, correctly ranking 11 of 14 groups, but the prespecified exact permutation test narrowly misses conventional significance.

#### Regularization profile

Before the timeout, the notebook also evaluated the observed ranking count over:

$$C\in{10^{-3},10^{-2},10^{-1},1,10,10^2,10^3}.$$

|       $$C$$ | Correct groups |
| ----------: | -------------: |
| $$10^{-3}$$ |           9/14 |
| $$10^{-2}$$ |           9/14 |
| $$10^{-1}$$ |          11/14 |
|       $$1$$ |          11/14 |
|      $$10$$ |          14/14 |
|    $$10^2$$ |          13/14 |
|    $$10^3$$ |          11/14 |

The strongest observed value is:

$$14/14$$

at:

$$C=10.$$

This is an exploratory profile maximum, not the primary inferential result.

The exact null was evaluated only for the prespecified:

$$C=1$$

model.

The notebook did not complete a max-over-regularization permutation null before timing out.

The 14/14 value therefore cannot be assigned the fixed-$$C$$ permutation value or presented as confirmed evidence.

It establishes only that the observed ordering is sensitive to logistic regularization.

#### Model dependence

The notebook documentation reports that ridge-based alternatives produce only:

* 7/14 under a member-level construction;
* 9/14 under an antisymmetric pairwise construction.

The automorphism result is therefore not a representation-only property.

It depends materially on:

* the logistic ranking objective;
* the antisymmetric pair construction;
* and the regularization value.

This does not invalidate the fixed logistic result, but it limits any claim that automorphism order is generally linearly accessible from the top-100 QuIC representation.

#### Timed-out comparison arms

The notebook was intended to compare QuIC with:

1. cumulative folklore 2-WL;
2. the tied adjacency spectrum.

Those comparison arms did not finish before the 12-hour compute limit terminated the experiment.

This is a computational timeout, not evidence that either comparison failed statistically.

No result is available for whether the observed QuIC ordering is:

* shared by folklore 2-WL;
* stronger or weaker than folklore 2-WL;
* or distinguishable from a correctly implemented tied-spectrum control.

The spectrum is numerically equal within each cospectral group up to eigensolver deviations of approximately:

$$5.77\times10^{-15}.$$

Those differences reflect eigensolver noise.

A completed spectrum control should set the within-group spectral differences exactly to zero before scaling. Otherwise, root-mean-square normalization can amplify numerical noise into arbitrary apparent features.

Because the timeout occurred before the persistence cell, no complete E12 result artifact was written.

The runtime log and completed notebook outputs are the only record of the partial experiment.

#### What the partial experiment establishes

The work completed before the timeout establishes that:

1. **The census and target counts reproduce the earlier cospectral audit.**

   There are 41 exact cospectral groups, of which 14 two-member groups vary in automorphism order.

2. **QuIC correctly orders 11 of 14 groups at the prespecified logistic setting.**

3. **The exact permutation value is (0.0581).**

   This is suggestive but does not meet a conventional (0.05) threshold.

4. **An exploratory regularization setting reaches 14/14.**

   No selection-adjusted null was completed for that maximum.

5. **The result is model and regularization dependent.**

6. **The planned classical comparison and tied control were not completed because the notebook reached the 12-hour compute limit.**

E12 does not provide a confirmed automorphism-ordering claim or a completed classical comparison.

#### Necessary qualifications

The experiment contains only:

$$14$$

independent cospectral groups.

Its inferential resolution and power are therefore limited.

The same 14 groups are used to inspect the regularization profile. The profile cannot be interpreted as independent validation.

The exact permutation test is valid for the fixed implemented statistic, but the graphs belong to one finite census rather than a sampled graph population.

The exploratory 14/14 result is selected after examining seven regularization settings.

A valid inferential result for that profile would require recomputing the complete null distribution of:

$$\max_C T_{\text{sign}}(C).$$

That computation was not completed before the timeout.

The folklore 2-WL and spectral arms have no usable output. Their absence must not be described as a negative result.

The representation uses exact ideal probabilities. Finite-shot automorphism ordering is not evaluated.

Finally, the proposed $$T_\tau$$ statistic is redundant because every group contains exactly one unequal pair.

#### Overall assessment

E12 is a timed-out partial experiment with one completed inferential result.

The notebook was automatically terminated after reaching the environment’s 12-hour compute-protection limit. It did not complete the folklore 2-WL arm, spectrum control, final comparison, or persistence.

The completed QuIC model ranks:

$$11/14$$

exact cospectral pairs correctly at the prespecified setting, with:

$$p=0.0581.$$

This is suggestive but inconclusive.

The exploratory regularization profile reaches:

$$14/14$$

at $$C=10$$, but no max-over-$$C$$ null was completed, and ridge alternatives perform much closer to chance.

The appropriate minimal record is:

> E12 was terminated at the environment’s 12-hour compute limit before its folklore 2-WL and tied-spectrum controls completed. Before termination, the prespecified QuIC ranker correctly ordered 11 of 14 exact adjacency-cospectral pairs by automorphism-group order. The complete fixed-model permutation null gave (p=0.0581), narrowly missing conventional significance. An exploratory regularization profile reached 14/14, but no selection-adjusted null was completed. E12 is therefore retained as a timed-out, suggestive, and inconclusive result rather than a completed automorphism-ordering comparison.

### E13 - Truncation Decomposition and Completed Cospectral Tracer

#### Experimental design

E7 established that QuIC’s cycle-count information is concentrated within the leading portion of the sorted probability vector. It did not determine whether the predictive signal came from:

* the relative shape of the retained probabilities;
* the cumulative probability mass retained by the head;
* or a combination of both.

E7 also planned, but did not complete, an analysis of how exact adjacency-cospectral separations accumulate across the sorted probability ranks.

E13 addresses both questions.

The experiment uses the complete connected cubic-graph censuses at:

* **509 graphs at (n=14)**;
* **4,060 graphs at (n=16)**.

For each graph, the complete sorted QuIC representation is:

$$
\mathbf p(G)
$$

============
$$
\left(
p_{(1)},p_{(2)},\ldots,p_{(2^n)}
\right),
$$

where:

$$
p_{(1)}
\ge
p_{(2)}
\ge
\cdots.
$$

The tested truncation depths are:

$$
k\in
{25,50,100,200,400,1000}.
$$

For each depth, four representations are constructed.

1. **Raw head**

   $$
   \mathbf h_k
   $$
   
   ===========
   $$
   \left(
   p_{(1)},\ldots,p_{(k)}
   \right).
   $$

3. **Normalized head**

   $$
   \widetilde{\mathbf h}_k
   $$
   
   =======================
   $$
   \frac{\mathbf h_k}
   {\sum_{i=1}^{k}p_{(i)}}.
   $$

   This retains the shape of the probability head while removing its cumulative mass.

5. **Retained mass only**

   $$
   m_k
   $$
   
   ===
   $$
   \sum_{i=1}^{k}p_{(i)}.
   $$

   This is a one-dimensional concentration feature.

7. **Normalized head plus retained mass**

   $$
   \left[
   \widetilde{\mathbf h}_k,
   m_k
   \right].
   $$

The comparison provides an operational decomposition of linearly accessible information.

* When the normalized head matches the raw head, the relative shape is sufficient.
* When retained mass alone performs strongly, cumulative concentration is sufficient at that cutoff.
* When normalized shape plus mass exceeds either component, the two provide complementary linear coordinates.

The ridge targets are:

* triangle count ((C_3));
* 4-cycle count ((C_4));
* 5-cycle count ((C_5));
* 6-cycle count ((C_6));
* diamond count;
* girth.

The models use the standing probe protocol:

$$
\alpha\in
{10^{-14},10^{-13},\ldots,10^2},
$$

with `RidgeCV(cv=5)` inside the frozen shuffled seed-0 outer folds.

A separate group-preserving ranking experiment decomposes the automorphism-order signal previously observed among exact adjacency-cospectral graphs.

The ranking target is:

$$
\log_2|	ext{Aut}(G)|.
$$

For every unequal cospectral pair ((G_i,G_j)), the model predicts:

$$
	ext{sign}
\left(
\log_2|	ext{Aut}(G_i)|
$$

-------------------------------
$$
\log_2|	ext{Aut}(G_j)|
\right)
$$

from the difference between their truncated representations.

This arm uses:

* leave-one-cospectral-group-out evaluation;
* an intercept-free antisymmetric logistic model;
* fixed (C=1.0);
* both orientations of every training pair.

Finally, the completed cospectral tracer measures, at every depth:

* raw-head (L_1) separation;
* normalized-head (L_1) separation;
* retained-mass difference;
* fraction of the complete-vector separation retained by the head;
* percentile among graph pairs sharing the same ((C_3,C_4,C_5,C_6)) tuple.

#### Validation checks

The graph targets are recomputed directly from the adjacency matrices.

The following cubic identities hold exactly for every graph:

$$
	ext{tr}(A^3)
$$

======================
$$
6C_3,
$$

$$
	ext{tr}(A^4)
$$

======================
$$
8C_4+15n,
$$

and:

$$
	ext{tr}(A^6)
$$

======================
$$
87n
+
6C_3
+
96C_4
+
12(C_6+D),
$$

where (D) is diamond count.

Exact adjacency-cospectral groups are reconstructed through integer trace tuples:

$$
\left(
	ext{tr}(A),
	ext{tr}(A^2),
\ldots,
	ext{tr}(A^n)
\right).
$$

The resulting censuses contain:

* 3 exact cospectral groups at (n=14);
* 41 exact cospectral groups at (n=16).

These correspond to:

* 3 within-group pairs at (n=14);
* 43 within-group pairs at (n=16), including the pairs from one cospectral triple.

The sorted probability vectors are normalized and monotonically nonincreasing to numerical tolerance.

#### Triangle-count decomposition

##### (n=14)

|   (k) |        Raw head | Normalized head |       Mass only | Normalized + mass |
| ----: | --------------: | --------------: | --------------: | ----------------: |
|    25 | (1.000\pm0.000) | (0.999\pm0.000) | (0.996\pm0.000) |   (1.000\pm0.000) |
|    50 | (1.000\pm0.000) | (1.000\pm0.000) | (0.088\pm0.020) |   (1.000\pm0.000) |
|   100 | (1.000\pm0.000) | (1.000\pm0.000) | (0.965\pm0.004) |   (1.000\pm0.000) |
|   200 | (1.000\pm0.000) | (1.000\pm0.000) | (0.946\pm0.017) |   (1.000\pm0.000) |
|   400 | (1.000\pm0.000) | (1.000\pm0.000) | (0.531\pm0.033) |   (1.000\pm0.000) |
| 1,000 | (1.000\pm0.000) | (1.000\pm0.000) | (0.916\pm0.014) |   (1.000\pm0.000) |

##### (n=16)

|   (k) |        Raw head | Normalized head |       Mass only | Normalized + mass |
| ----: | --------------: | --------------: | --------------: | ----------------: |
|    25 | (1.000\pm0.000) | (0.997\pm0.001) | (0.995\pm0.000) |   (1.000\pm0.000) |
|    50 | (1.000\pm0.000) | (1.000\pm0.000) | (0.229\pm0.023) |   (1.000\pm0.000) |
|   100 | (1.000\pm0.000) | (1.000\pm0.000) | (0.966\pm0.002) |   (1.000\pm0.000) |
|   200 | (1.000\pm0.000) | (1.000\pm0.000) | (0.951\pm0.002) |   (1.000\pm0.000) |
|   400 | (1.000\pm0.000) | (1.000\pm0.000) | (0.964\pm0.003) |   (1.000\pm0.000) |
| 1,000 | (1.000\pm0.000) | (1.000\pm0.000) | (0.946\pm0.002) |   (1.000\pm0.000) |

Triangle count is perfectly accessible from both the raw and normalized probability head at every tested depth.

Thus, the triangle signal is not dependent on retaining cumulative probability mass. The relative shape of only the first 25 probabilities is already sufficient.

Retained mass is also nearly sufficient at several cutoffs:

$$
R^2_{\mathrm{mass}}
\approx
0.995
$$

at (k=25), and approximately:

$$
0.95\text{--}0.97
$$

at most cutoffs of (k\ge100).

The mass-only result is not monotone. It falls sharply at:

$$
k=50
$$

for both graph orders and at:

$$
k=400
$$

for (n=14).

The correct interpretation is therefore not that triangle count is always encoded by total head mass. Instead, triangle count has multiple redundant carriers:

* the normalized shape is uniformly sufficient;
* cumulative mass is nearly sufficient at selected rank boundaries.

The dependence of mass-only performance on the exact cutoff indicates that cumulative concentration changes differently when the boundary crosses different probability plateaus.

#### Four-cycle decomposition

##### (n=14)

|   (k) |        Raw head | Normalized head |        Mass only | Normalized + mass |
| ----: | --------------: | --------------: | ---------------: | ----------------: |
|    25 | (0.957\pm0.009) | (0.822\pm0.026) | (-0.008\pm0.006) |   (0.957\pm0.008) |
|    50 | (0.988\pm0.004) | (0.988\pm0.004) |  (0.742\pm0.020) |   (0.988\pm0.004) |
|   100 | (0.993\pm0.004) | (0.993\pm0.003) |  (0.060\pm0.041) |   (0.994\pm0.004) |
|   200 | (0.995\pm0.003) | (0.995\pm0.004) |  (0.009\pm0.018) |   (0.995\pm0.003) |
|   400 | (0.998\pm0.002) | (0.998\pm0.002) |  (0.276\pm0.047) |   (0.998\pm0.002) |
| 1,000 | (0.998\pm0.002) | (0.998\pm0.001) | (-0.007\pm0.006) |   (0.998\pm0.001) |

##### (n=16)

|   (k) |        Raw head | Normalized head |        Mass only | Normalized + mass |
| ----: | --------------: | --------------: | ---------------: | ----------------: |
|    25 | (0.968\pm0.011) | (0.789\pm0.052) | (-0.002\pm0.002) |   (0.968\pm0.011) |
|    50 | (0.981\pm0.003) | (0.981\pm0.004) |  (0.674\pm0.013) |   (0.981\pm0.003) |
|   100 | (0.996\pm0.001) | (0.997\pm0.001) |  (0.050\pm0.015) |   (0.998\pm0.001) |
|   200 | (0.998\pm0.002) | (0.998\pm0.002) |  (0.054\pm0.016) |   (0.998\pm0.002) |
|   400 | (0.998\pm0.003) | (0.999\pm0.001) | (-0.001\pm0.002) |   (1.000\pm0.000) |
| 1,000 | (1.000\pm0.000) | (1.000\pm0.000) |  (0.072\pm0.017) |   (1.000\pm0.000) |

Four-cycle count is primarily carried by the shape of the probability head.

From:

$$
k=50
$$

onward, normalized-head performance essentially matches the raw representation at both graph orders.

At:

$$
k=25,
$$

normalization reduces performance:

$$
0.957
\rightarrow
0.822
$$

at (n=14), and:

$$
0.968
\rightarrow
0.789
$$

at (n=16).

Mass alone is uninformative at this depth, but normalized shape plus mass restores the complete raw-head score. Thus, the very shallow 4-cycle signal depends on a combination of shape and cumulative scale, even though mass by itself is insufficient.

At:

$$
k=50,
$$

mass alone becomes moderately predictive:

$$
R^2=0.742
$$

and:

$$
R^2=0.674.
$$

This mass result disappears at most later cutoffs. As with triangle count, cumulative-mass accessibility is therefore rank-boundary specific rather than monotonic.

#### Five-cycle decomposition

##### (n=14)

|   (k) |         Raw head |  Normalized head |        Mass only | Normalized + mass |
| ----: | ---------------: | ---------------: | ---------------: | ----------------: |
|    25 |  (0.034\pm0.062) | (-0.022\pm0.030) | (-0.010\pm0.010) |   (0.035\pm0.059) |
|    50 | (-0.026\pm0.036) |  (0.046\pm0.077) |  (0.059\pm0.100) |   (0.057\pm0.089) |
|   100 |  (0.272\pm0.142) |  (0.182\pm0.186) | (-0.013\pm0.013) |   (0.248\pm0.135) |
|   200 |  (0.920\pm0.081) |  (0.925\pm0.085) |  (0.056\pm0.016) |   (0.930\pm0.075) |
|   400 |  (0.927\pm0.092) |  (0.913\pm0.087) |  (0.012\pm0.051) |   (0.911\pm0.089) |
| 1,000 |  (0.928\pm0.092) |  (0.938\pm0.073) | (-0.013\pm0.013) |   (0.941\pm0.069) |

##### (n=16)

|   (k) |        Raw head |  Normalized head |        Mass only | Normalized + mass |
| ----: | --------------: | ---------------: | ---------------: | ----------------: |
|    25 | (0.169\pm0.031) | (-0.001\pm0.001) | (-0.001\pm0.001) |   (0.163\pm0.022) |
|    50 | (0.167\pm0.032) |  (0.167\pm0.033) |  (0.047\pm0.010) |   (0.167\pm0.032) |
|   100 | (0.335\pm0.041) |  (0.294\pm0.062) | (-0.001\pm0.001) |   (0.346\pm0.062) |
|   200 | (0.743\pm0.060) |  (0.783\pm0.010) |  (0.003\pm0.005) |   (0.780\pm0.014) |
|   400 | (0.981\pm0.015) |  (0.984\pm0.013) |  (0.024\pm0.005) |   (0.984\pm0.012) |
| 1,000 | (0.982\pm0.015) |  (0.984\pm0.015) | (-0.001\pm0.001) |   (0.986\pm0.014) |

Five-cycle count provides the cleanest shape-dominated result.

At both graph orders, retained mass remains at or near the prediction floor across every tested depth.

By contrast, normalized-head performance follows the raw-head transition closely.

At (n=14):

$$
R^2_{\mathrm{normalized}}
$$

=========================
$$
0.925
$$

by (k=200), and:

$$
0.938
$$

at (k=1000).

At (n=16):

$$
R^2_{\mathrm{normalized}}
$$

=========================

0.783
$$

at (k=200), and:

$$
0.984
$$

at (k=400).

Adding retained mass produces no meaningful improvement over normalized shape.

The 5-cycle signal is therefore carried by the detailed relative arrangement of probabilities within the head rather than by cumulative concentration.

This agrees with the earlier probability-moment result. Low-order concentration summaries did not recover the strong full-vector 5-cycle signal, while retaining the detailed head shape does.

#### Six-cycle decomposition

##### (n=14)

|   (k) |        Raw head | Normalized head |       Mass only | Normalized + mass |
| ----: | --------------: | --------------: | --------------: | ----------------: |
|    25 | (0.163\pm0.056) | (0.158\pm0.050) | (0.150\pm0.053) |   (0.153\pm0.055) |
|    50 | (0.228\pm0.077) | (0.232\pm0.097) | (0.125\pm0.092) |   (0.232\pm0.098) |
|   100 | (0.235\pm0.079) | (0.242\pm0.083) | (0.114\pm0.045) |   (0.239\pm0.086) |
|   200 | (0.391\pm0.083) | (0.372\pm0.104) | (0.081\pm0.053) |   (0.373\pm0.105) |
|   400 | (0.478\pm0.113) | (0.483\pm0.116) | (0.226\pm0.091) |   (0.486\pm0.111) |
| 1,000 | (0.484\pm0.327) | (0.638\pm0.159) | (0.143\pm0.036) |   (0.666\pm0.145) |

##### (n=16)

|   (k) |        Raw head | Normalized head |       Mass only | Normalized + mass |
| ----: | --------------: | --------------: | --------------: | ----------------: |
|    25 | (0.126\pm0.014) | (0.112\pm0.017) | (0.101\pm0.018) |   (0.134\pm0.017) |
|    50 | (0.179\pm0.013) | (0.180\pm0.014) | (0.131\pm0.018) |   (0.178\pm0.013) |
|   100 | (0.184\pm0.011) | (0.186\pm0.010) | (0.077\pm0.014) |   (0.186\pm0.010) |
|   200 | (0.190\pm0.027) | (0.180\pm0.018) | (0.067\pm0.013) |   (0.181\pm0.019) |
|   400 | (0.363\pm0.023) | (0.394\pm0.043) | (0.126\pm0.018) |   (0.394\pm0.043) |
| 1,000 | (0.640\pm0.121) | (0.786\pm0.166) | (0.067\pm0.013) |   (0.817\pm0.151) |

Six-cycle count is also primarily shape carried, but its deepest result differs from the C5 pattern.

At:

$$
k\le400,
$$

raw and normalized heads perform similarly.

At:

$$
k=1000,
$$

normalization substantially improves the score:

$$
0.484
\rightarrow
0.638
$$

at (n=14), and:

$$
0.640
\rightarrow
0.786
$$

at (n=16).

Adding retained mass raises the results further to:

$$
0.666
$$

and:

$$
0.817.
$$

Thus, the deep C6 signal is most linearly accessible when head shape and cumulative mass are exposed as separate coordinates.

The improvement also reduces the extreme (n=14) fold variation:

$$
0.484\pm0.327
$$

for the raw head, compared with:

$$
0.666\pm0.145
$$

for normalized shape plus mass.

This suggests that multiplicatively combining shape and scale in the raw probabilities obscures part of the C6 coordinate. Separating them improves linear accessibility.

The result should nevertheless remain qualified by E10. The full-vector (n=16) C6 probe was sensitive to the inner cross-validation partition. E13 uses the standing `RidgeCV` protocol and does not resolve that protocol sensitivity.

#### Diamond-count decomposition

##### (n=14)

|   (k) |        Raw head | Normalized head |       Mass only | Normalized + mass |
| ----: | --------------: | --------------: | --------------: | ----------------: |
|    25 | (0.930\pm0.004) | (0.917\pm0.017) | (0.447\pm0.047) |   (0.931\pm0.003) |
|    50 | (0.981\pm0.005) | (0.977\pm0.009) | (0.110\pm0.011) |   (0.971\pm0.004) |
|   100 | (0.990\pm0.004) | (0.986\pm0.008) | (0.407\pm0.068) |   (0.995\pm0.007) |
|   200 | (0.993\pm0.003) | (0.993\pm0.003) | (0.406\pm0.078) |   (0.993\pm0.003) |
|   400 | (0.994\pm0.004) | (0.994\pm0.004) | (0.334\pm0.008) |   (0.994\pm0.004) |
| 1,000 | (0.993\pm0.003) | (0.993\pm0.003) | (0.474\pm0.043) |   (0.993\pm0.003) |

##### (n=16)

|   (k) |        Raw head | Normalized head |       Mass only | Normalized + mass |
| ----: | --------------: | --------------: | --------------: | ----------------: |
|    25 | (0.943\pm0.013) | (0.940\pm0.015) | (0.419\pm0.017) |   (0.943\pm0.013) |
|    50 | (0.974\pm0.005) | (0.973\pm0.005) | (0.216\pm0.017) |   (0.974\pm0.005) |
|   100 | (0.993\pm0.004) | (0.997\pm0.005) | (0.404\pm0.019) |   (0.999\pm0.001) |
|   200 | (0.995\pm0.005) | (0.995\pm0.005) | (0.391\pm0.023) |   (0.995\pm0.005) |
|   400 | (0.995\pm0.005) | (0.997\pm0.004) | (0.464\pm0.025) |   (0.998\pm0.003) |
| 1,000 | (0.996\pm0.004) | (0.996\pm0.004) | (0.379\pm0.015) |   (0.996\pm0.004) |

Diamond count is shallow and predominantly shape carried.

Using only the first 25 normalized probabilities produces:

$$
R^2=0.917
$$

at (n=14), and:

$$
R^2=0.940
$$

at (n=16).

By:

$$
k=100,
$$

normalized-head performance reaches:

$$
0.986
$$

and:

$$
0.997.
$$

Mass alone contains moderate diamond information, typically producing:

$$
R^2\approx0.3\text{--}0.47,
$$

but never approaches the normalized-head score.

Adding mass to the normalized head provides little additional value. Diamond accessibility is therefore primarily determined by the relative head shape.

This is evidence about coordinate accessibility, not information beyond the complete adjacency spectrum. E8A found no diamond variation among the exact cospectral groups in these censuses.

#### Girth decomposition

##### (n=14)

|   (k) |        Raw head | Normalized head |       Mass only | Normalized + mass |
| ----: | --------------: | --------------: | --------------: | ----------------: |
|    25 | (0.917\pm0.035) | (0.910\pm0.040) | (0.373\pm0.037) |   (0.918\pm0.034) |
|    50 | (0.921\pm0.034) | (0.921\pm0.034) | (0.067\pm0.046) |   (0.922\pm0.034) |
|   100 | (0.987\pm0.014) | (0.984\pm0.014) | (0.316\pm0.040) |   (0.986\pm0.015) |
|   200 | (0.992\pm0.013) | (0.992\pm0.013) | (0.337\pm0.058) |   (0.992\pm0.013) |
|   400 | (0.993\pm0.014) | (0.993\pm0.014) | (0.211\pm0.053) |   (0.993\pm0.014) |
| 1,000 | (0.993\pm0.014) | (0.993\pm0.014) | (0.273\pm0.063) |   (0.993\pm0.014) |

##### (n=16)

|   (k) |        Raw head | Normalized head |       Mass only | Normalized + mass |
| ----: | --------------: | --------------: | --------------: | ----------------: |
|    25 | (0.945\pm0.008) | (0.942\pm0.009) | (0.348\pm0.038) |   (0.945\pm0.008) |
|    50 | (0.951\pm0.007) | (0.951\pm0.007) | (0.099\pm0.020) |   (0.951\pm0.007) |
|   100 | (0.996\pm0.003) | (0.994\pm0.004) | (0.281\pm0.006) |   (0.996\pm0.003) |
|   200 | (0.999\pm0.003) | (0.999\pm0.003) | (0.308\pm0.010) |   (0.999\pm0.003) |
|   400 | (0.999\pm0.003) | (0.999\pm0.003) | (0.359\pm0.017) |   (0.999\pm0.003) |
| 1,000 | (0.999\pm0.003) | (0.999\pm0.003) | (0.340\pm0.012) |   (0.999\pm0.003) |

Girth is also shallow and shape dominated.

The first 25 normalized probabilities already obtain:

$$
R^2=0.910
$$

at (n=14), and:

$$
R^2=0.942
$$

at (n=16).

By:

$$
k=100,
$$

the scores reach:

$$
0.984
$$

and:

$$
0.994.
$$

Mass alone provides moderate information at selected cutoffs but remains substantially weaker than normalized shape.

The normalized-plus-mass representation does not materially improve upon shape alone. Girth accessibility therefore depends primarily on the relative organization of the largest probabilities.

#### Cross-target shape and mass summary

The decomposition identifies distinct carrier patterns.

| Target   | Primary carrier                                          | Interpretation                                                  |
| -------- | -------------------------------------------------------- | --------------------------------------------------------------- |
| (C_3)    | Shape, with redundant mass signal at selected cutoffs    | Both shape and concentration can independently expose triangles |
| (C_4)    | Shape; shallow shape–mass interaction at (k=25)          | Mass helps only at specific head boundaries                     |
| (C_5)    | Shape                                                    | Cumulative mass is essentially uninformative                    |
| (C_6)    | Deep shape, with modest mass complementarity at (k=1000) | Separating shape and scale improves linear accessibility        |
| Diamonds | Shallow shape                                            | Nearly saturated by the first 100 normalized probabilities      |
| Girth    | Shallow shape                                            | Nearly saturated by the first 100 normalized probabilities      |

The dominant general result is that the raw-head hierarchy is not primarily a cumulative-mass effect.

Normalized probability shape preserves almost all useful performance for:

* (C_4);
* (C_5);
* diamonds;
* girth.

Triangle count has redundant access through both shape and mass at selected cutoffs. Six-cycle count benefits from explicitly separating the two at the deepest tested truncation.

#### Automorphism-order ranking decomposition

##### (n=14)

The (n=14) census contains only three automorphism-varying cospectral pairs.

|   (k) | Raw head | Normalized head | Mass only | Normalized + mass |
| ----: | -------: | --------------: | --------: | ----------------: |
|    25 |      1/3 |             1/3 |       3/3 |               1/3 |
|    50 |      1/3 |             1/3 |       2/3 |               1/3 |
|   100 |      1/3 |             1/3 |       1/3 |               1/3 |
|   200 |      1/3 |             1/3 |       3/3 |               1/3 |
|   400 |      1/3 |             0/3 |       0/3 |               0/3 |
| 1,000 |      1/3 |             0/3 |       1/3 |               0/3 |

The sample is too small to support a meaningful decomposition.

Mass alone correctly ranks all three pairs at (k=25) and (k=200), while the shape-based representations generally rank only one pair. With only three held-out groups, these changes are descriptive exhibits rather than statistical evidence.

##### (n=16)

The (n=16) ranking contains 14 unequal pairs from 14 distinct cospectral groups.

|   (k) | Raw head | Normalized head | Mass only | Normalized + mass |
| ----: | -------: | --------------: | --------: | ----------------: |
|    25 |     7/14 |            7/14 |      6/14 |              6/14 |
|    50 |    11/14 |           12/14 |      9/14 |             12/14 |
|   100 |    11/14 |           11/14 |      9/14 |             11/14 |
|   200 |    13/14 |           13/14 |     10/14 |             13/14 |
|   400 |    12/14 |           12/14 |      7/14 |             12/14 |
| 1,000 |    11/14 |           11/14 |      8/14 |             11/14 |

The automorphism-order signal is primarily carried by head shape.

At:

$$
k=200,
$$

both the raw and normalized heads correctly rank:

$$
13/14
$$

pairs.

Mass alone reaches:

$$
10/14.
$$

At every depth, adding mass to the normalized head fails to improve upon normalized shape.

The strongest result is therefore not a cumulative-concentration effect. It depends on the relative arrangement of the leading probabilities.

The signal is also localized within an intermediate head rather than improving monotonically with dimension:

$$
7/14
\rightarrow
12/14
\rightarrow
11/14
\rightarrow
13/14
\rightarrow
12/14
\rightarrow
11/14.
$$

This resembles the rank-specific accessibility observed for the cycle targets. Adding more of the probability tail does not necessarily improve generalization in a very small group-level sample.

The ranking counts should remain descriptive because no permutation audit is performed in E13 and the leave-one-group-out predictions are generated from overlapping training sets.

#### Completed cospectral tracer

The tracer compares every exact cospectral pair with all graph pairs sharing the complete cycle-count tuple:

$$
(C_3,C_4,C_5,C_6).
$$

The reference classes contain:

* 114 count-identical pairs at (n=14);
* 8,474 count-identical pairs at (n=16).

##### (n=14)

|   (k) | Median raw-head (L_1) | Median fraction of full separation retained | Median count-identical percentile |
| ----: | --------------------: | ------------------------------------------: | --------------------------------: |
|    25 |  (9.422\times10^{-8}) |                                       0.155 |                              29.8 |
|    50 |  (1.155\times10^{-7}) |                                       0.335 |                              35.1 |
|   100 |  (1.299\times10^{-7}) |                                       0.472 |                              33.3 |
|   200 |  (1.488\times10^{-7}) |                                       0.585 |                              20.2 |
|   400 |  (2.938\times10^{-7}) |                                       0.752 |                              22.8 |
| 1,000 |  (3.731\times10^{-7}) |                                       0.955 |                              18.4 |

##### (n=16)

|   (k) | Median raw-head (L_1) | Median fraction of full separation retained | Median count-identical percentile |
| ----: | --------------------: | ------------------------------------------: | --------------------------------: |
|    25 |  (7.516\times10^{-9}) |                                       0.058 |                              19.5 |
|    50 |  (2.265\times10^{-8}) |                                       0.175 |                              19.5 |
|   100 |  (3.535\times10^{-8}) |                                       0.259 |                              16.5 |
|   200 |  (1.459\times10^{-7}) |                                       0.397 |                              24.0 |
|   400 |  (1.593\times10^{-7}) |                                       0.630 |                              23.0 |
| 1,000 |  (3.439\times10^{-7}) |                                       0.895 |                              23.1 |

Cospectral separations accumulate more deeply than the strongest cycle signals.

At (n=16), the first 25 coordinates retain only:

$$
5.8%
$$

of the median complete-vector separation.

The first 100 retain:

$$
25.9%.
$$

The retained fraction reaches:

$$
63.0%
$$

at (k=400), and:

$$
89.5%
$$

at (k=1000).

At (n=14), the corresponding progression is:

$$
15.5%,
\quad
47.2%,
\quad
75.2%,
\quad
95.5%.
$$

Thus, most complete cospectral separation is eventually captured by the first 1,000 probabilities, but it is not concentrated in the extreme head in the same manner as triangle, 4-cycle, diamond, or girth information.

The percentile results provide a second distinction.

Median cospectral-pair percentiles remain between approximately:

$$
16.5
\quad\text{and}\quad
35.1.
$$

They do not increase monotonically with truncation.

Cospectral mates are therefore not unusually far apart relative to other graph pairs with the same ((C_3,C_4,C_5,C_6)) counts. Their separations generally lie below the median of that reference class.

The non-spectral residue is numerically genuine, but it is subtle:

* its absolute separations are small;
* its head concentration varies by pair;
* and its relative percentile does not systematically improve as more coordinates are retained.

This result is consistent with the earlier precision and finite-shot audits. The residue exists well above numerical error but remains small relative to both ordinary graph variation and sampling noise.

#### Relationship to E7 and E8B

E13 refines both earlier conclusions.

E7 established that cycle information is rank stratified:

$$
C_3
\rightarrow
C_4
\rightarrow
C_5
\rightarrow
C_6.
$$

E13 shows that this hierarchy is primarily a hierarchy in probability-head shape, not merely a hierarchy in retained probability mass.

In particular:

* (C_5) remains strong after normalization and disappears in the mass-only representation;
* diamonds and girth are already strong in the normalized extreme head;
* (C_6) benefits from separating shape and mass at deeper truncation.

E8B established that QuIC’s exact cospectral differences are functionally aligned with graph symmetry. E13 localizes that signal to the relative shape of approximately the first 50–200 probabilities.

The tracer adds an important counterbalance. Although symmetry ranking can use an intermediate head, the total geometric separation between cospectral mates accumulates more gradually and remains modest relative to count-identical graph pairs.

Functional usefulness and total metric concentration are therefore different properties.

#### What the experiment establishes

The completed results establish that:

1. **QuIC’s truncation hierarchy is primarily shape carried.**

   Normalizing the probability head preserves nearly all (C_4), (C_5), diamond, and girth performance.

2. **Triangle count has redundant carriers.**

   The normalized shape is always sufficient, while cumulative mass is also nearly sufficient at several rank cutoffs.

3. **Five-cycle accessibility is not a retained-mass effect.**

   Mass-only probes remain at the prediction floor while normalized-head performance reaches approximately (0.94)–(0.98).

4. **Deep six-cycle accessibility improves when shape and mass are separated.**

   At (k=1000), normalized shape plus mass reaches (0.666) at (n=14) and (0.817) at (n=16).

5. **Diamond and girth information is concentrated in the extreme shape of the head.**

   Both are already strongly decodable from the first 25 normalized probabilities.

6. **The automorphism-order cospectral signal is primarily shape based.**

   The normalized head correctly ranks 13 of 14 unequal (n=16) pairs at (k=200), while mass alone reaches 10 of 14.

7. **Cospectral separations are deeper than shallow cycle signals.**

   At (n=16), only 25.9% of the median complete separation is retained by the first 100 probabilities, compared with 89.5% by the first 1,000.

8. **Cospectral separations are not unusually large among cycle-count-identical pairs.**

   Their median percentile remains below 36 at every tested depth.

E13 therefore distinguishes three properties that the raw truncation experiment had conflated:

* cumulative concentration;
* detailed probability-head shape;
* and the rank depth at which different structural signals accumulate.

#### Necessary qualifications

The four representations provide an operational decomposition for linear probes, not an information-theoretic partition.

The raw head combines shape and mass multiplicatively:

$$
\mathbf h_k
$$

===========
$$
m_k\widetilde{\mathbf h}_k.
$$

A linear model on:

$$
\left[
\widetilde{\mathbf h}_k,m_k
\right]
$$

cannot reconstruct that product without interaction terms. Consequently, differences between the raw and decomposed representations reflect both information content and coordinate geometry.

The mass-only feature is one scalar whose meaning changes with (k). Its strongly nonmonotonic results should not be interpreted as inconsistencies. Different rank cutoffs cross different probability plateaus and produce different cumulative statistics.

The representation blocks are not standardized fold by fold before ridge fitting. Ridge regularization depends on feature scale, and E10 showed that QuIC probe results can depend strongly on very small regularization values. Comparisons among raw, normalized, and mass coordinates therefore characterize the standing probe protocol rather than a scale-invariant notion of information.

The full ridge grid uses `RidgeCV(cv=5)` with the same inner-fold behavior as the earlier probe experiments. E13 does not independently validate the protocol-sensitive (n=16) C6 result identified by E10.

The automorphism-order ranking contains only:

* 3 varying pairs at (n=14);
* 14 varying pairs at (n=16).

The (n=14) decomposition is too small for inference. The (n=16) counts are more informative but still have high finite-sample uncertainty.

No target-specific permutation test is run for the automorphism-ranking grid. Testing six depths and four representations also creates a model-selection issue if the best cell is highlighted after observing the complete table.

The tracer percentile is descriptive rather than inferential. Reference pairs are not independent, and large cycle-signature classes contribute more pairs than small classes.

The count-identical reference class fixes:

$$
(C_3,C_4,C_5,C_6),
$$

but does not fix:

* the complete adjacency spectrum;
* diameter;
* Wiener index;
* automorphism order;
* or other graph structure.

A low percentile therefore means that the cospectral separation is small relative to this particular reference class, not relative to every possible structural control.

The tracer summarizes medians. Earlier experiments showed substantial pair-to-pair variation in where cospectral separation appears within the probability vector. Median retained fractions should not be interpreted as applying uniformly to every pair.

All results use exact ideal probabilities. E7S showed that the same head geometry is not practically resolved at ordinary shot budgets.

Finally, the truncation grid is coarse. A result at (k=200) or (k=1000) identifies the first tested depth with that behavior, not a mathematically minimal sufficient dimension.

#### Overall assessment

E13 resolves the two main ambiguities left by the original truncation experiment.

The cycle hierarchy is not principally caused by cumulative retained probability mass. The normalized shape of the head preserves nearly all of the useful information for 4-cycles, 5-cycles, diamonds, and girth. Five-cycle count provides the cleanest example: mass-only prediction remains at the floor, while normalized-head prediction reaches approximately:

$$
0.94
\quad\text{at }n=14,
$$

and:

$$
0.98
\quad\text{at }n=16.
$$

Triangle count has redundant access through both head shape and cumulative mass at selected cutoffs. Six-cycle count is deeper and becomes more linearly accessible when shape and mass are separated.

The automorphism-order result is also predominantly shape carried, reaching:

$$
13/14
$$

correct cospectral rankings from the first 200 normalized probabilities.

The completed tracer shows that total cospectral separation behaves differently from the shallow structural hierarchy. Only a minority of the separation lies in the first 25–100 ranks, and its percentile among cycle-count-identical pairs remains low and nonmonotonic. The residue is real, but geometrically subtle and distributed more deeply through the probability head.

The appropriate central claim is:

> QuIC’s rank-stratified structural hierarchy is primarily encoded in the relative shape of its leading probabilities rather than in cumulative retained mass. Five-cycle, diamond, and girth accessibility survives head normalization, while six-cycle accessibility improves when shape and mass are exposed separately. The functional automorphism-order signal is likewise shape dominated. Exact cospectral separations accumulate more gradually, reaching most of their complete-vector magnitude only near the first 1,000 probabilities and remaining modest relative to other cycle-count-identical graph pairs.

### E14 - n=18 Exact-Cospectral Functional Witnesses

#### Experimental design

E14 tests whether QuIC differences within exact adjacency-cospectral graph classes align with graph properties that the complete adjacency spectrum cannot determine.

The experiment uses the complete connected cubic-graph census at:

* **41,301 graphs at (n=18)**.

Exact adjacency-cospectral classes are reconstructed from integer trace tuples:

$$
\left(\text{tr}(A),\text{tr}(A^2),\ldots,\text{tr}(A^{18})\right).
$$

The census contains:

* **471 exact cospectral groups**;
* **958 total members of those groups**.

Computing full QuIC vectors of dimension:

$$
2^{18}=262{,}144
$$

for all 41,301 graphs would require substantially more storage and simulation time than the earlier censuses. The producer therefore uses a selective design.

Full sorted QuIC vectors are computed for:

* every member of a cospectral group varying in diamond count, Wiener index, or automorphism-group order;
* a producer-selected set of invariant-identical control groups.

The resulting stored set contains:

$$
906=625\text{ qualifying members}+281\text{ control members}.
$$

The circuit uses the canonical QuIC configuration:

* degree-proportional (R_X) encoding with maximum rotation (2.875);
* edgewise (R_{ZZ}(2.0)) entanglers;
* uniform (R_X(0.1)) mixer;
* one entangler–mixer repetition;
* complete descending-sorted ideal probability vectors.

The primary functional test uses pairwise ranking within exact cospectral groups.

For each unequal-target pair ((G_i,G_j)), the feature vector is:

$$
\mathbf x_{ij}^{(k)}=\mathbf p_{1:k}(G_i)-\mathbf p_{1:k}(G_j),
$$

and the label is:

$$
y_{ij}=\text{sign}\left(t(G_i)-t(G_j)\right).
$$

Evaluation uses:

* leave-one-cospectral-group-out validation;
* both orientations of every training pair;
* train-only root-mean-square feature scaling;
* intercept-free (L_2)-regularized logistic regression;
* ties counted as failures.

The tested targets are:

* diamond count;
* Wiener index;
* (\log_2|\text{Aut}(G)|).

The prespecified primary truncation depth is:

$$
k=100.
$$

The regularization profile is evaluated at:

$$
C\in{10^{-3},10^{-2},10^{-1},1,10,10^2,10^3}.
$$

The inferential null uses the fixed prespecified value:

$$
C=1.
$$

For diamond count, all:

$$
2^6=64
$$

pair-label sign patterns are enumerated. Wiener index and automorphism order use 2,000 sampled sign-flip refits.

A secondary depth analysis considers:

$$
k\in{50,100,200,500,1000,262{,}144}.
$$

The primary (k=100) tests completed for all three targets. The depth-selection correction completed for diamonds. The Wiener depth analysis completed only through (k=500), and the automorphism-order depth analysis did not complete beyond the primary checkpoint.

#### Integrity checks

The notebook applies several validation gates before using the QuIC vectors.

The stored invariant table satisfies the cubic identities:

$$
\text{tr}(A^3)=6C_3,
$$

$$
\text{tr}(A^4)=8C_4+15n,
$$

$$
\text{tr}(A^5)=10C_5+10\text{tr}(A^3),
$$

and:

$$
\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).
$$

The 471 cospectral groups are independently re-derived from the stored integer trace tuples and exactly match the producer record.

The sets of groups varying in each invariant are also recomputed independently.

| Invariant    | Exact cospectral groups with variation |   |    |
| ------------ | -------------------------------------: | - | -- |
| Diamonds     |                                      6 |   |    |
| 6-cycles     |                                      6 |   |    |
| 7-cycles     |                                     18 |   |    |
| Wiener index |                                    283 |   |    |
| Radius       |                                     75 |   |    |
| Diameter     |                                     53 |   |    |
| (\log_2      |                          \text{Aut}(G) | ) | 90 |

The diamond-varying and 6-cycle-varying group sets are identical:

$$
\mathcal G_D=\mathcal G_{C_6}.
$$

All 906 qualifying and control members are reconstructed from their graph6 strings, and their cycle, metric, and symmetry invariants exactly reproduce the stored table.

Every stored QuIC vector is:

* descending sorted;
* normalized to unit sum;
* dimension (262,144).

Three stored vectors are independently rebuilt using Qiskit. Their worst coordinate deviation is below:

$$
10^{-12}.
$$

These checks establish that the ranking results use the intended canonical circuit and correctly identified exact cospectral classes.

#### Direct diamond and 6-cycle witnesses

For cubic graphs:

$$
\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).
$$

Within an exact adjacency-cospectral class, the spectrum fixes the traces and therefore fixes:

$$
C_6+D.
$$

The (n=14) and (n=16) censuses contained no exact cospectral groups varying in diamond count. At (n=18), six such groups appear.

Each group is a pair with:

$$
|\Delta D|=1,\qquad\Delta C_6=-\Delta D.
$$

| Group | Members           | Diamond counts | 6-cycle counts |    Full-vector (L_1) |
| ----: | ----------------- | -------------: | -------------: | -------------------: |
|   257 | 12,891 and 29,287 |        1 and 0 |        6 and 7 | (1.619\times10^{-5}) |
|   401 | 29,752 and 31,179 |        1 and 0 |        5 and 6 | (1.590\times10^{-5}) |
|   438 | 36,289 and 40,737 |        0 and 1 |        6 and 5 | (1.590\times10^{-5}) |
|   451 | 37,702 and 39,791 |        1 and 0 |        8 and 9 | (1.624\times10^{-5}) |
|   461 | 38,826 and 40,082 |        1 and 0 |        4 and 5 | (1.592\times10^{-5}) |
|   468 | 39,793 and 40,655 |        0 and 1 |      11 and 10 | (1.626\times10^{-5}) |

These classes are direct witnesses that diamond count and 6-cycle count are not individually determined by the complete adjacency spectrum.

Because:

$$
\Delta C_6=-\Delta D,
$$

ranking diamond count and ranking 6-cycle count are the same test with reversed labels. The result is reported once through the diamond target.

#### Primary ranking results

| Target       | Varying groups | Unequal pairs | Correct at (k=100), (C=1) | Null mean | Null 95th percentile | Permutation (p) | Nominal binomial (p) |        |        |
| ------------ | -------------: | ------------: | ------------------------: | --------: | -------------------: | --------------: | -------------------: | ------ | ------ |
| Diamonds     |              6 |             6 |                         6 |       3.0 |                    5 |          0.0462 |               0.0156 |        |        |
| Wiener index |            283 |           302 |                       176 |     150.5 |                  167 |          0.0060 |               0.0024 |        |        |
| (\log_2      |  \text{Aut}(G) |             ) |                        90 |        94 |                   63 |            47.0 |                   57 | 0.0035 | 0.0006 |

The permutation values are the primary inferential results. The nominal binomial values treat pair outcomes as independent and do not account for shared training sets or the complete model-refitting procedure.

#### Diamond and 6-cycle ranking

QuIC correctly ranks all six witness pairs:

$$
6/6.
$$

The observed result exceeds the 95th percentile of the exact sign-flip null:

$$
6>5.
$$

The reported permutation value is:

$$
p=0.0462.
$$

The result is modest in sample size but directly targeted. The test does not ask whether QuIC merely distinguishes the six pairs. It asks whether a common direction learned from five held-out cospectral classes correctly orders the sixth by diamond count.

Every pair is ranked correctly under leave-one-group-out evaluation.

Since 6-cycle labels are the negatives of the diamond labels, the same result establishes:

> QuIC consistently identifies which member of each exact cospectral witness carries the additional diamond and, equivalently, which member carries the additional 6-cycle.

This is a direct functional result beyond the complete adjacency spectrum. It is stronger than the earlier diamond residual probe, which established information beyond a linear spectral readout but could not establish information beyond the full spectrum because no diamond-varying cospectral classes existed at (n=14) or (n=16).

#### Wiener-index ranking

At the prespecified depth and regularization:

$$
176/302
$$

Wiener-index pairs are correctly ranked.

This corresponds to approximately:

$$
58.3%.
$$

The raw accuracy is not large, but it is evaluated across 283 held-out cospectral groups. The full-refit permutation null has:

$$
\text{mean}=150.5,\qquad\text{95th percentile}=167.
$$

The observed count exceeds the null 95th percentile by nine pairs:

$$
176-167=9.
$$

The sampled permutation result is:

$$
p=0.0060.
$$

The complete adjacency spectrum is identical within every evaluated pair. The positive result therefore shows that QuIC differences contain a repeatable direction associated with relative Wiener index inside exact cospectral classes.

The result also strengthens the earlier (n=16) exhibit, which contained only 26 unequal Wiener pairs. At (n=18), the test expands to 302 pairs and obtains significance under a full-refit sign-flip null.

#### Automorphism-order ranking

For:

$$
\log_2|\text{Aut}(G)|,
$$

QuIC correctly ranks:

$$
63/94
$$

unequal pairs, or approximately:

$$
67.0%.
$$

The permutation null has:

$$
\text{mean}=47.0,\qquad\text{95th percentile}=57.
$$

The observed count exceeds that percentile by six:

$$
63-57=6.
$$

The sampled permutation result is:

$$
p=0.0035.
$$

This extends the earlier (n=16) automorphism result from 14 varying pairs to 94 pairs across 90 exact cospectral groups.

The result indicates that the symmetry-related QuIC direction found at (n=16) persists in a substantially larger and more diverse set of exact cospectral classes.

#### Regularization profile

The complete (C)-profiles are:

| Target       |     (10^{-3}) | (10^{-2}) | (10^{-1}) | (1) | (10) | (10^2) | (10^3) |    |    |
| ------------ | ------------: | --------: | --------: | --: | ---: | -----: | -----: | -- | -- |
| Diamonds     |             6 |         6 |         6 |   6 |    6 |      6 |      6 |    |    |
| Wiener index |           164 |       173 |       173 | 176 |  179 |    175 |    182 |    |    |
| (\log_2      | \text{Aut}(G) |         ) |        51 |  48 |   56 |     63 |     61 | 61 | 67 |

The diamond result is completely insensitive to the tested regularization scale.

Every value produces:

$$
6/6.
$$

The Wiener and automorphism results vary more strongly.

Wiener index ranges from:

$$
164/302
$$

to:

$$
182/302.
$$

Automorphism order ranges from:

$$
48/94
$$

to:

$$
67/94.
$$

The inferential null is evaluated at the prespecified:

$$
C=1,
$$

rather than at the best observed profile value. The larger counts at (C=10^3) are therefore descriptive and should not replace the primary values without an additional selection correction.

#### Truncation-depth results

##### Diamonds

The diamond ranking is unchanged across the complete depth grid.

| Depth (k) | Correct pairs |
| --------: | ------------: |
|        50 |           6/6 |
|       100 |           6/6 |
|       200 |           6/6 |
|       500 |           6/6 |
|     1,000 |           6/6 |
|   262,144 |           6/6 |

The max-over-depth statistic is:

$$
6/6.
$$

The selection-corrected permutation result remains:

$$
p=0.0462.
$$

The witness direction is therefore already present within the first 50 sorted probabilities and does not depend on selecting a favorable truncation depth.

##### Wiener index

The resumed depth analysis completed the following observed counts:

| Depth (k) | Correct pairs |
| --------: | ------------: |
|        50 |       161/302 |
|       100 |       176/302 |
|       200 |       186/302 |
|       500 |       214/302 |
|     1,000 | Not completed |
|   262,144 | Not completed |

The observed count increases at every completed depth:

$$
161<176<186<214.
$$

At:

$$
k=500,
$$

the descriptive accuracy reaches approximately:

$$
70.9%.
$$

This suggests that Wiener-index information is distributed more deeply through the sorted readout than the diamond witness signal.

The resumed run did not complete:

* the (k=1000) arm;
* the full-vector arm;
* the final max-over-depth permutation value.

The (214/302) result should therefore be reported only as a partial descriptive depth result. The completed inferential Wiener result remains the prespecified:

$$
176/302,\qquad p=0.0060
$$

at:

$$
k=100.
$$

##### Automorphism order

The automorphism-order primary result completed at:

$$
k=100.
$$

The per-depth sweep and max-over-depth correction did not complete.

No best-depth claim is therefore supported for this target.

#### Within-group QuIC separations

The full-vector within-group distances are:

| Group category          | Pair count |        Minimum (L_1) |         Median (L_1) |        Maximum (L_1) |
| ----------------------- | ---------: | -------------------: | -------------------: | -------------------: |
| Diamond witnesses       |          6 | (1.590\times10^{-5}) | (1.605\times10^{-5}) | (1.626\times10^{-5}) |
| Other qualifying groups |        327 | (5.704\times10^{-9}) | (2.948\times10^{-7}) | (3.336\times10^{-5}) |
| Control groups          |        145 | (1.731\times10^{-9}) | (5.874\times10^{-8}) | (1.673\times10^{-5}) |

The diamond-witness separations occupy a narrow interval around:

$$
1.6\times10^{-5}.
$$

Their median is approximately:

$$
54
$$

times the median of the other qualifying pairs and approximately:

$$
273
$$

times the control median.

The ranges nevertheless overlap. Some qualifying and control pairs have separations as large as or larger than the witness pairs.

The result therefore does not show that diamond-varying pairs are uniquely far apart. It shows that all six direct witnesses have comparatively large, consistent exact QuIC separations.

Because QuIC vectors were computed selectively, no census-wide reference distribution is available. These values cannot be converted into global pair-distance percentiles.

#### Relationship to the earlier cospectral experiments

The earlier exact cospectral audits established that QuIC distinguishes:

* all 3 exact cospectral pairs at (n=14);
* all 43 exact cospectral pairs at (n=16).

Those censuses did not contain variation in diamond count or cycle counts through (C_7) within their exact cospectral groups.

At (n=18), the larger census produces the first six direct diamond and 6-cycle witnesses.

This changes the status of the non-spectral claim.

The previous evidence established:

* numerical separation of exact cospectral graphs;
* functional alignment with Wiener index and automorphism order;
* diamond accessibility beyond a linear spectral probe.

E14 now establishes a graph invariant adjacent to the cycle hierarchy that varies inside exact cospectral classes and is consistently ranked by QuIC.

The spectrum fixes:

$$
C_6+D,
$$

while QuIC aligns with the direction that separates:

$$
C_6-D.
$$

The result therefore connects the spectral-backbone and non-spectral-residue stories directly.

#### What the experiment establishes

The completed results establish that:

1. **The complete connected cubic (n=18) census contains 471 exact cospectral groups with 958 members.**

2. **Six exact cospectral groups vary in diamond count and 6-cycle count.**

   In every case, the two quantities vary in exactly opposite directions because the spectrum fixes (C_6+D).

3. **QuIC separates all six direct witnesses by approximately (1.6\times10^{-5}) in full-vector (L_1) distance.**

4. **QuIC correctly ranks diamond count in all six held-out witness pairs.**

   The same result ranks 6-cycle count with reversed labels.

5. **The diamond result is stable across every tested regularization value and truncation depth.**

6. **QuIC ranks Wiener index above the full-refit permutation null.**

   At the prespecified depth, it obtains (176/302) with permutation (p=0.0060).

7. **QuIC ranks automorphism-group order above the full-refit permutation null.**

   It obtains (63/94) with permutation (p=0.0035).

8. **Wiener information appears to accumulate more deeply through the readout.**

   The partial depth sweep rises from (161/302) at (k=50) to (214/302) at (k=500).

9. **The functional residue is not limited to one type of graph property.**

   It appears in a local subgraph statistic, a global metric invariant, and a symmetry invariant.

E14 supplies the clearest direct evidence that QuIC’s exact cospectral residue is structurally aligned rather than merely collision breaking.

#### Necessary qualifications

The diamond experiment contains only six groups and six pairs.

All six are correctly ranked, but the inferential strength is limited by the small number of independent witness classes.

The exact 64-pattern sign-flip distribution is exhaustively enumerated, but the code applies the add-one formula:

$$
p=\frac{1+b}{B+1}.
$$

With two null patterns reaching the observed score, this produces:

$$
p=\frac{3}{65}=0.0462.
$$

The raw exhaustive tail frequency is:

$$
\frac{2}{64}=0.03125.
$$

The reported (0.0462) value is therefore a conservative add-one value rather than the unadjusted exact tail frequency.

The nominal binomial values are not the primary inferential quantities. Pair predictions share training data, and some cospectral groups contribute more than one pair.

The sampled Wiener and automorphism nulls independently flip pair labels. For groups contributing multiple pairs, such flips can create label configurations that do not correspond to any consistent ordering of the group members.

A cleaner group-structured null would permute target assignments within each exact cospectral group. The current values should be described specifically as results under the implemented pairwise sign-flip null.

The sampled nulls use 2,000 draws, giving a minimum add-one resolution of:

$$
\frac{1}{2001}\approx0.0005.
$$

The random-number seed includes Python’s built-in string hash. Unless the environment fixes `PYTHONHASHSEED`, the exact sampled draws are not guaranteed to reproduce across separate Python processes.

The fixed (C=1) results are prespecified. The larger values elsewhere in the regularization profile are post hoc descriptive comparisons.

The Wiener and automorphism max-over-depth analyses are incomplete.

Only the diamond result has a completed selection-corrected depth test. The partial Wiener increase through (k=500) cannot be presented as a selection-corrected best-depth result.

The planned descriptive ridge probe over the twelve diamond-witness members did not complete and should not be reported.

The producer computes QuIC vectors selectively rather than over the full census. E14 therefore cannot estimate:

* global collision rates;
* census-wide distance percentiles;
* or general probe performance across all 41,301 graphs.

The control set is also producer selected. Its separation distribution is a diagnostic comparison, not a random sample from all invariant-identical cospectral groups.

The ranking task establishes directional association within exact cospectral groups. It does not imply accurate absolute prediction of diamond count, Wiener index, or automorphism order from arbitrary graphs.

No higher-order classical representation is evaluated in E14. Exact cospectrality eliminates the adjacency spectrum as an explanation, but other classical graph representations may also rank these targets.

All results use exact ideal probabilities. No finite-shot or hardware experiment tests whether the observed witness separations are operationally resolvable.

Finally, the experiment concerns:

* connected cubic graphs;
* (n=18);
* one circuit repetition;
* one fixed canonical angle schedule.

It establishes a direct witness inside this census, not a universal separation theorem.

#### Overall assessment

E14 provides the strongest functional non-spectral evidence in the experimental record.

The complete (n=18) cubic census contains six exact adjacency-cospectral pairs that differ in diamond count and 6-cycle count. The spectrum fixes their sum and therefore cannot determine which member carries the diamond or the additional 6-cycle.

QuIC correctly ranks all six pairs using only the first 100 sorted probabilities. The result remains 6/6 across every tested regularization value and every truncation depth, including the complete 262,144-dimensional vector. The selection-corrected sign-flip result remains:

$$
p=0.0462.
$$

The larger metric and symmetry tests also succeed. QuIC ranks Wiener index in 176 of 302 unequal pairs with:

$$
p=0.0060,
$$

and ranks automorphism-group order in 63 of 94 pairs with:

$$
p=0.0035.
$$

These results extend the earlier small cospectral exhibits to hundreds of pairwise tests across hundreds of exact cospectral groups.

The incomplete depth sweeps do not undermine the prespecified primary results. They limit only claims about the optimal truncation depth for Wiener index and automorphism order.

The appropriate central claim is:

> In the complete connected cubic (n=18) census, QuIC functionally resolves graph properties that vary inside exact adjacency-cospectral classes. Six newly identified classes exchange one diamond for one 6-cycle while preserving the complete spectrum; QuIC correctly ranks all six at every tested truncation depth. It also ranks Wiener index and automorphism-group order significantly above full-refit sign-flip nulls across 302 and 94 unequal cospectral pairs. These results show that QuIC’s non-spectral residue is aligned with local structure, global metric geometry, and graph symmetry rather than serving only as an arbitrary collision-breaking signal.



### E14N - Split-Null Confirmation

#### Experimental design

E14N provides a computationally tractable confirmatory test for the Wiener-index and automorphism-order ranking effects observed in E14.

The experiment uses the same complete connected cubic-graph census at:

* **41,301 graphs at (n=18)**;
* **471 exact adjacency-cospectral groups**;
* **958 total members of those groups**.

As in E14, complete sorted QuIC vectors are stored for:

* every member of a cospectral group varying in diamond count, Wiener index, or automorphism-group order;
* a selected set of invariant-identical control groups.

The stored representation set contains:

$$906=625\text{ qualifying members}+281\text{ control members}.$$

E14 evaluated each varying group through leave-one-group-out ranking. That protocol provides a descriptive estimate using nearly all available groups for training, but a full permutation audit is computationally expensive because changing labels requires refitting every leave-one-group-out model.

E14N breaks this dependency through a deterministic group-level split.

For each target:

1. the varying exact-cospectral groups are partitioned into two fixed subsets;
2. one subset is used to train a single antisymmetric ranking model;
3. the trained model produces fixed margins for the held-out groups;
4. target values are permuted only within the held-out groups;
5. the fixed margins are rescored without refitting;
6. the train and test partitions are reversed and the procedure is repeated.

Because the held-out target values never enter model fitting, the within-test-group permutation test provides a valid conditional null under exchangeability of target assignments within each held-out cospectral group.

The two targets are:

* Wiener index;
* $$\log_2|\text{Aut}(G)|.$$

Diamond count is not rerun because only six diamond-varying groups exist. Dividing them into two halves would leave only three test groups in each direction. The exact six-pair E14 witness test remains the appropriate diamond analysis.

#### Frozen representation and model

No representation depth or model hyperparameter is selected in E14N.

The protocol is fixed at the E14 primary configuration:

$$k=100,\qquad C=1.$$

For every unequal-target graph pair ((G_i,G_j)) within a training cospectral group, the input is:

$$\mathbf x_{ij}=\mathbf p_{1:100}(G_i)-\mathbf p_{1:100}(G_j).$$

The pair label is:

$$y_{ij}=\text{sign}\left(t(G_i)-t(G_j)\right).$$

The model is:

* logistic regression;
* no intercept;
* (L_2) regularization;
* train-only root-mean-square feature scaling;
* both pair orientations included during training.

Including both orientations gives:

$$(-\mathbf x_{ij},-y_{ij})$$

for every:

$$(\mathbf x_{ij},y_{ij}).$$

This enforces an antisymmetric ranking rule.

For a held-out pair, the model produces a fixed decision margin. A pair is correct when the margin and the target difference have the same sign. Zero margins are counted as failures.

#### Primary and secondary statistics

The primary statistic is group-balanced accuracy.

Within each held-out cospectral group, the model’s accuracy is computed over all unequal-target pairs. These group accuracies are then averaged:

$$A_{\text{group}}=\frac{1}{|\mathcal G_{\text{test}}|}\sum_{g\in\mathcal G_{\text{test}}}\frac{\text{correct unequal pairs in }g}{\text{unequal pairs in }g}.$$

Every cospectral group therefore receives equal weight, regardless of whether it contributes one pair or several pairs.

Raw pooled pair accuracy is reported secondarily:

$$A_{\text{pooled}}=\frac{\text{correct unequal pairs across all test groups}}{\text{unequal pairs across all test groups}}.$$

The pooled statistic gives greater weight to larger cospectral groups.

#### Deterministic group partition

Each cospectral group is assigned to partition zero or one by applying SHA-256 to a content-addressed identifier constructed from the sorted graph6 strings of its members.

The assignment depends only on group content. It does not depend on:

* census enumeration order;
* a tunable random seed;
* model performance;
* or repeated split generation.

The split is therefore fixed and reproducible in principle.

The resulting partitions are:

| Target       | Total varying groups | Partition 0 | Partition 1 |    |    |
| ------------ | -------------------: | ----------: | ----------: | -- | -- |
| Wiener index |                  283 |         131 |         152 |    |    |
| $$\log_2     |        \text{Aut}(G) |          $$ |          90 | 40 | 50 |

Both directions are evaluated:

* **Direction A:** train on partition 0 and test on partition 1;
* **Direction B:** train on partition 1 and test on partition 0.

#### Integrity checks

The notebook repeats the E14 validation gates before fitting any model.

The stored census table satisfies:

$$\text{tr}(A^3)=6C_3,$$

$$\text{tr}(A^4)=8C_4+15n,$$

$$\text{tr}(A^5)=10C_5+10\text{tr}(A^3),$$

and:

$$\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).$$

The 471 exact cospectral groups are independently reconstructed from the integer trace tuples and exactly match the producer record.

The varying-group sets are independently recomputed and match the stored counts:

| Invariant    | Varying exact cospectral groups |    |    |
| ------------ | ------------------------------: | -- | -- |
| Diamonds     |                               6 |    |    |
| 6-cycles     |                               6 |    |    |
| 7-cycles     |                              18 |    |    |
| Wiener index |                             283 |    |    |
| Radius       |                              75 |    |    |
| Diameter     |                              53 |    |    |
| $$\log_2     |                   \text{Aut}(G) | $$ | 90 |

All 906 stored graph members are reconstructed from graph6, and their cycle, metric, and symmetry invariants reproduce the producer table.

Every stored QuIC vector is:

* dimension (262,144);
* descending sorted;
* normalized to unit sum.

Three members are independently recomputed using the canonical Qiskit circuit. Their worst coordinate discrepancy is below:

$$10^{-12}.$$

The representation and invariant data therefore reproduce the validated E14 inputs.

#### Permutation-null construction

For each split direction, the model is trained once.

Its held-out pair margins are then cached and remain fixed throughout the null experiment.

Each permutation draw independently shuffles the observed target-value multiset within every held-out cospectral group.

This preserves:

* the number of members in each group;
* the target values present in each group;
* all target ties;
* the number of unequal comparisons induced by each assignment.

For two-member groups, the within-group permutation reduces to randomly choosing one of the two possible target orientations.

For groups with three or more members, the complete target assignment is permuted. This preserves transitivity of the target ordering and avoids generating mutually inconsistent pair labels.

The primary null statistic is the group-balanced accuracy. The pooled-pair statistic is recomputed from the same permutations.

Each real-data split direction uses:

$$100{,}000$$

permutation draws.

The one-sided add-one value is:

$$p=\frac{1+#{A_{\text{null}}\ge A_{\text{observed}}}}{100{,}001}.$$

The minimum attainable value is therefore:

$$\frac{1}{100{,}001}\approx10^{-5}.$$

#### Synthetic null validation

The permutation machinery is tested on synthetic groups before it is applied to the QuIC data.

##### Perfect alignment

When every synthetic margin agrees with the target ordering:

$$A_{\text{group}}=1.000.$$

Using 2,000 null draws, the permutation value reaches the add-one floor:

$$p=\frac{1}{2001}=0.00050.$$

##### Perfect anti-alignment

When every margin opposes the target ordering:

$$A_{\text{group}}=0.000,\qquad p=1.000.$$

##### No-signal calibration

Four hundred independent synthetic datasets are generated with margins independent of the targets.

The observed empirical rejection frequencies are:

| Threshold  | Expected frequency | Observed frequency |
| ---------- | -----------------: | -----------------: |
| (p\le0.10) |              0.100 |              0.085 |
| (p\le0.25) |              0.250 |              0.220 |
| (p\le0.50) |              0.500 |              0.500 |

All values fall within the notebook’s prespecified tolerance of the uniform-null expectation.

The validation confirms that the implemented fixed-margin permutation procedure is calibrated under its synthetic exchangeability model.

#### Wiener-index results

##### Direction A

Direction A trains on 131 groups and tests on 152 groups.

| Statistic               | Observed |           Null mean | Permutation (p) |
| ----------------------- | -------: | ------------------: | --------------: |
| Group-balanced accuracy |    0.603 |               0.500 |          0.0050 |
| Raw pooled accuracy     |    0.589 | approximately 0.500 |          0.0153 |

The group-balanced accuracy exceeds the null mean by:

$$0.603-0.500=0.103.$$

The observed ordering is significant under the held-out within-group permutation null:

$$p=0.0050.$$

##### Direction B

Direction B trains on 152 groups and tests on 131 groups.

| Statistic               | Observed |           Null mean | Permutation (p) |
| ----------------------- | -------: | ------------------: | --------------: |
| Group-balanced accuracy |    0.607 |               0.500 |          0.0071 |
| Raw pooled accuracy     |    0.604 | approximately 0.500 |          0.0098 |

The reverse direction produces nearly the same effect:

$$0.607-0.500=0.107.$$

It is also significant:

$$p=0.0071.$$

##### Combined interpretation

Both directions satisfy:

* group-balanced accuracy above chance;
* group-balanced permutation (p<0.01);
* pooled-pair permutation (p<0.02).

The notebook reports the two-test Bonferroni omnibus value:

$$p_{\text{Bonferroni}}=2\min(0.0050,0.0071)=0.0101.$$

More importantly, the effect replicates inferentially in both directions. A model trained on either deterministic half of the Wiener-varying groups orders the held-out half above its within-group permutation null.

This is stronger than a result driven by one favorable partition.

The split accuracies are also close:

$$0.603\quad\text{and}\quad0.607.$$

The Wiener direction is therefore stable under a substantial reduction in training data and under reversal of the train/test partition.

#### Relationship to the E14 Wiener result

E14 reported:

$$176/302$$

correct unequal Wiener pairs under leave-one-group-out evaluation, with nominal pooled accuracy:

$$58.3%.$$

E14N asks a harder transfer question.

Each model sees only approximately half of the varying cospectral groups during training and is then evaluated on a completely disjoint group set.

Despite this reduction, the split group-balanced accuracies remain approximately:

$$60%.$$

The agreement between:

* the full-data leave-one-group-out result;
* Direction A;
* Direction B

supports the interpretation that QuIC contains a transferable Wiener-ordering direction across exact cospectral classes.

E14 supplies the high-data descriptive estimate. E14N supplies the clean held-out group-level inferential confirmation.

#### Automorphism-order results

##### Direction A

Direction A trains on 40 groups and tests on 50 groups.

| Statistic               | Observed |           Null mean | Permutation (p) |
| ----------------------- | -------: | ------------------: | --------------: |
| Group-balanced accuracy |    0.740 |               0.500 |          0.0004 |
| Raw pooled accuracy     |    0.745 | approximately 0.500 |          0.0003 |

This is a strong held-out result.

The group-balanced accuracy exceeds chance by:

$$0.740-0.500=0.240.$$

The permutation value is:

$$p=0.0004.$$

The pooled statistic gives the same conclusion:

$$A_{\text{pooled}}=0.745,\qquad p=0.0003.$$

##### Direction B

Direction B trains on 50 groups and tests on 40 groups.

| Statistic               | Observed |           Null mean | Permutation (p) |
| ----------------------- | -------: | ------------------: | --------------: |
| Group-balanced accuracy |    0.517 |               0.499 |          0.4269 |
| Raw pooled accuracy     |    0.512 | approximately 0.500 |          0.4968 |

The reverse direction is indistinguishable from the null.

The group-balanced excess is only:

$$0.517-0.499=0.018.$$

The permutation result is:

$$p=0.4269.$$

The raw pooled result is likewise null:

$$p=0.4968.$$

##### Combined interpretation

The notebook reports:

$$p_{\text{Bonferroni}}=2\min(0.0004,0.4269)=0.0008.$$

This is a valid familywise-corrected omnibus result for the claim that at least one of the two prespecified split directions contains an effect.

It is not evidence that the effect replicates across both directions.

The notebook labels the result as “same-direction replication” because both observed accuracies lie slightly above their corresponding null means:

$$0.740>0.500,\qquad0.517>0.499.$$

That criterion is too weak to support the word “replication.” Under a null centered near 0.5, approximately half of null results will lie above the null mean.

The statistically appropriate conclusion is:

* Direction A strongly confirms an automorphism-ordering direction.
* Direction B does not confirm it.
* The two-direction omnibus test is significant because Direction A is strong.
* Split-to-split inferential replication is not established.

The asymmetry is not explained by training-set size. The failed direction uses the larger 50-group training partition and the smaller 40-group test partition.

It more likely reflects heterogeneity between the two deterministic group subsets, although E14N does not identify which graph properties produce that heterogeneity.

#### Relationship to the E14 automorphism result

E14 reported:

$$63/94$$

correct automorphism-order pairs under leave-one-group-out evaluation, corresponding to approximately:

$$67.0%.$$

E14N produces one split substantially above that level:

$$74.0%,$$

and one split near chance:

$$51.7%.$$

The full-data E14 result remains useful as a descriptive summary across all 90 varying groups.

E14N shows that the signal is not uniformly transferable across arbitrary halves of those groups.

The strong Direction A result demonstrates that a learned QuIC symmetry direction can generalize to a disjoint set of exact cospectral classes. The failed reverse direction shows that this direction is not stably learned from both halves.

The appropriate interpretation is therefore weaker than the Wiener conclusion:

> The automorphism-order signal is present and can transfer strongly across one prespecified group split, but E14N does not establish symmetric replication across the two halves.

#### Summary of confirmatory results

| Target       | Direction A group-balanced accuracy | Direction A (p) | Direction B group-balanced accuracy | Direction B (p) | Bonferroni omnibus (p) | Inferential replication |        |    |
| ------------ | ----------------------------------: | --------------: | ----------------------------------: | --------------: | ---------------------: | ----------------------- | ------ | -- |
| Wiener index |                               0.603 |          0.0050 |                               0.607 |          0.0071 |                 0.0101 | Yes                     |        |    |
| $$\log_2     |                       \text{Aut}(G) |              $$ |                               0.740 |          0.0004 |                  0.517 | 0.4269                  | 0.0008 | No |

The distinction between the final two columns is essential.

The Bonferroni value tests whether either of the two prespecified directions is significant after accounting for the two tests.

Inferential replication requires both directions to independently reject their respective nulls in the same direction.

Wiener index satisfies both standards.

Automorphism order satisfies only the omnibus standard.

#### Relationship to the diamond witness

E14N does not alter the diamond result.

Only six exact cospectral groups vary in diamond count. A deterministic half split would produce approximately three groups per test partition, giving little meaningful inferential resolution.

E14 already provides:

* all six witness pairs correctly ranked;
* an exact enumeration of all (2^6) pair-orientation patterns;
* stability across all tested depths and regularization values.

That result should remain separate from E14N.

E14N is specifically the confirmatory inferential companion for the two larger target families.

#### What the experiment establishes

The completed results establish that:

1. **The E14 inputs reproduce under the complete integrity-gate suite.**

   The graph invariants, exact cospectral groups, stored vectors, and Qiskit spot checks all pass.

2. **The deterministic partition is content addressed rather than performance selected.**

3. **The representation and model are frozen at (k=100) and (C=1).**

   No depth or regularization search enters the confirmation test.

4. **The within-test-group permutation machinery is calibrated on synthetic null data.**

5. **The Wiener-index signal confirms in both split directions.**

   The group-balanced accuracies are (0.603) and (0.607), with permutation values (0.0050) and (0.0071).

6. **The Wiener effect is stable under reversal of the training and test partitions.**

7. **The automorphism-order signal confirms strongly in one direction.**

   Direction A reaches group-balanced accuracy (0.740) with (p=0.0004).

8. **The automorphism-order signal does not confirm in the reverse direction.**

   Direction B reaches only (0.517) with (p=0.4269).

9. **The automorphism omnibus result remains significant after two-test Bonferroni correction.**

   This establishes evidence in at least one prespecified split direction, not replication across both.

10. **Group balancing removes domination by the larger cospectral classes.**

E14N therefore provides clean confirmatory evidence for the Wiener-ordering result and partial, split-dependent confirmation of the automorphism-order result.

#### Necessary qualifications

The split test evaluates a different estimator from E14’s leave-one-group-out procedure.

E14 trains each held-out prediction on nearly all other varying groups. E14N trains on only one deterministic half.

The E14 and E14N accuracy values should therefore not be treated as repeated measurements of exactly the same model.

The validity of the permutation test depends on exchangeability of target assignments within held-out groups under the null. The synthetic calibration validates the implementation but cannot prove that the real graph targets satisfy the scientific exchangeability assumption.

The 100,000-draw values are Monte Carlo permutation estimates rather than exhaustive probabilities.

The approximate Monte Carlo uncertainty is small but nonzero, particularly for the smallest reported values.

The Bonferroni calculation:

$$2\min(p_A,p_B)$$

is an omnibus correction for searching across two directions. It is not a method for combining concordant evidence from both directions.

For Wiener index, this distinction is immaterial because both directions are independently significant.

For automorphism order, it is critical.

The notebook’s `same_direction_replication` flag checks only whether both observed accuracies exceed their null means. It should be renamed to something such as:

* `both_above_null_mean`;
* or replaced with a criterion requiring both permutation values to pass a prespecified threshold.

Under a conventional:

$$p<0.05$$

criterion, automorphism order does not replicate across splits.

The permutation random-number seed includes Python’s built-in string hash:

$$\texttt{abs(hash(target_name))}.$$

Python string hashes can vary across processes unless `PYTHONHASHSEED` is fixed. The deterministic group partition remains stable, but the exact sampled permutation values may not reproduce bit for bit across environments.

A stable cryptographic target hash should be used for the null seed if exact computational reproducibility is required.

The split was not performance selected, but only one deterministic split is examined. The automorphism asymmetry shows that the result can depend materially on group composition.

Repeated random splits would characterize split variability, but they would require an explicitly prespecified aggregation rule and should not replace the fixed confirmatory split after observing the current results.

No analysis identifies how the two automorphism partitions differ structurally.

The group-balanced statistic gives equal weight to groups, while the original E14 figures are pooled pair counts. Their percentages answer related but nonidentical questions.

Diamond count is omitted from the split confirmation. Its E14 result relies on a different exact six-pair test.

All results use exact ideal QuIC probabilities. The experiment does not test finite-shot or hardware-accessible ranking.

Finally, the confirmation concerns:

* connected cubic graphs;
* (n=18);
* exact adjacency-cospectral classes;
* one fixed circuit;
* one fixed truncation depth;
* one fixed regularization value.

It does not establish universal ranking across graph families.

#### Overall assessment

E14N resolves the principal inferential concern for Wiener index.

A model trained on either deterministic half of the Wiener-varying cospectral groups orders the disjoint held-out half at approximately 60% group-balanced accuracy. Both directions reject their within-group target-permutation nulls:

$$p=0.0050\quad\text{and}\quad p=0.0071.$$

This provides a clean replication across independent group partitions and supports the E14 conclusion that QuIC’s exact-cospectral residue contains a transferable direction associated with global metric geometry.

The automorphism-order result is more limited.

One split direction is strong:

$$A_{\text{group}}=0.740,\qquad p=0.0004.$$

The reverse direction is null:

$$A_{\text{group}}=0.517,\qquad p=0.4269.$$

The Bonferroni omnibus value of (0.0008) confirms that at least one of the two prespecified directions carries a genuine effect. It does not establish replication. The notebook’s current replication flag should therefore be revised.

The appropriate central claim is:

> Under a deterministic cospectral-group split and a fixed within-test-group target-permutation null, QuIC’s Wiener-index ordering effect confirms in both train/test directions, with group-balanced accuracies of (0.603) and (0.607) and permutation values of (0.0050) and (0.0071). The automorphism-order effect is split dependent: one direction is strong at (0.740), (p=0.0004), while the reverse direction is indistinguishable from chance at (0.517), (p=0.4269). E14N therefore supplies robust confirmatory inference for Wiener index and partial, nonreplicating confirmation for automorphism-group order.

### E15 - Finite-Shot Recovery Under Independent Sampling

#### Experimental design

E15 measures how many ideal circuit shots are required for finite-sample QuIC features to recover the structural decodability observed with exact Born probabilities.

The experiment uses the complete connected cubic-graph censuses at:

* **509 graphs at (n=14)**;
* **4,060 graphs at (n=16)**.

For each graph, the canonical QuIC circuit produces an exact descending-sorted probability vector:

$$\mathbf p(G)\in\mathbb R^{2^n}.$$

Finite-shot observations are generated through multinomial sampling:

$$\mathbf c(G)\sim\text{Multinomial}(S,\mathbf p(G)),$$

where (S) is the shot budget.

The empirical feature vector is obtained by sorting the sampled counts and retaining the leading (k) frequencies:

$$\widehat{\mathbf p}*{1:k}(G)=\frac{1}{S}\text{sort}*{\downarrow}\mathbf c(G)_{1:k}.$$

Because multinomial sampling is invariant to a permutation of category labels, sampling from the already sorted exact probabilities and then sorting the observed counts is distributionally equivalent to sampling the original bitstring probabilities and discarding bitstring identities afterward.

#### Independent train and test realizations

For every shot budget and replicate, E15 generates two independent empirical representations of every graph:

* a training realization using replicate seed (r);
* a test realization using replicate seed (r+10{,}000).

Within each outer fold, the ridge probe is fitted using the training realization of the training graphs and evaluated using the independently sampled test realization of the held-out graphs.

The primary prediction rule is therefore:

$$\widehat y_{\text{test}}=f_{\text{train-noisy}}\left(\widehat{\mathbf p}^{,\text{independent}}_{\text{test}}\right).$$

This explicitly models a deployment setting in which the representation observed for a new graph is sampled independently from the representations used to train the decoder.

The outer graph partitions are fixed five-fold splits with:

$$\text{random seed}=0.$$

The ridge grid is:

$$\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2}.$$

Each finite-shot grid cell is repeated:

$$30$$

times.

The reported standard deviation is the standard deviation across the 30 replicate-level mean outer-fold (R^2) values.

#### Relationship to the E7S protocol

E7S used one independently sampled row per graph and then divided the graphs into disjoint train and test folds.

Because different graph rows are sampled independently, the E7S train and test rows were already independent. E15’s explicit second test realization is therefore expected to be distributionally equivalent rather than systematically harder.

E15 nevertheless improves the evidence by:

* making independent test resampling explicit;
* using 30 rather than a small number of replicates;
* adding diamonds and girth;
* estimating recovery thresholds relative to exact-vector ceilings;
* and extending selected cells to the full (n=16) census.

#### Shot and truncation grids

##### (n=14)

The complete grid uses:

$$S\in{2^{10},2^{14},2^{17},2^{20},2^{22},2^{24}},$$

and:

$$k\in{50,100,200,500,1000}.$$

The targets are:

* triangle count;
* 4-cycle count;
* 5-cycle count;
* 6-cycle count;
* diamond count;
* girth.

##### (n=16)

The selected confirmation grid uses:

$$S\in{2^{20},2^{22},2^{24}},$$

and:

$$k\in{100,1000}.$$

The targets are:

* triangle count;
* 4-cycle count;
* 5-cycle count.

The (n=16) experiment does not evaluate finite-shot C6, diamond, or girth recovery.

#### Four-slice execution

The expensive 30-replicate grid was divided into four disjoint notebooks:

| Slice | Replicate indices |
| ----- | ----------------: |
| E15a  |               0–7 |
| E15b  |              8–15 |
| E15c  |             16–23 |
| E15d  |             24–29 |

The merge notebook loads the four saved partial artifacts and checks, independently for every grid cell, that:

* no replicate index appears in more than one slice;
* the union is exactly (0,\ldots,29);
* every cell contains exactly 30 replicates.

The completed merged grid contains:

| Census | Complete grid cells | Replicates per cell |
| ------ | ------------------: | ------------------: |
| (n=14) |                 180 |                  30 |
| (n=16) |                  18 |                  30 |

No executed notebook contains an error.

The attached E15d notebook itself is an unexecuted template, but its replicate-24–29 artifact was successfully loaded by the executed merge notebook. The merge output, rather than the unexecuted E15d notebook, is the artifact-of-record validation.

#### Census and target validation

The merge notebook reloads the original census artifacts and verifies that:

* the (n=14) census contains 509 graphs;
* the (n=16) census contains 4,060 graphs;
* every exact vector has dimension (2^n);
* every exact vector is descending sorted;
* every vector sums to one within (10^{-12}).

Cycle counts, diamonds, and girth are recomputed from the adjacency matrices.

The following identities hold exactly for every graph:

$$\text{tr}(A^3)=6C_3,$$

$$\text{tr}(A^4)=8C_4+15n,$$

$$\text{tr}(A^5)=10C_5+10\text{tr}(A^3),$$

and:

$$\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).$$

The diamond target is the cubic hinge count implemented as the number of edges whose endpoints have exactly two common neighbors.

#### Exact-vector reference rows

The recovery targets are defined relative to the ridge score obtained from the exact sorted probabilities at the same truncation depth.

##### (n=14)

| Target   |   (k=50) | (k=100) | (k=200) | (k=500) | (k=1000) |
| -------- | -------: | ------: | ------: | ------: | -------: |
| (C_3)    |    1.000 |   1.000 |   1.000 |   1.000 |    1.000 |
| (C_4)    |    0.988 |   0.993 |   0.995 |   0.998 |    0.998 |
| (C_5)    | (-0.026) |   0.272 |   0.920 |   0.927 |    0.928 |
| (C_6)    |    0.228 |   0.235 |   0.391 |   0.524 |    0.484 |
| Diamonds |    0.981 |   0.990 |   0.993 |   0.994 |    0.993 |
| Girth    |    0.921 |   0.987 |   0.992 |   0.993 |    0.993 |

The exact row reproduces the established rank-depth hierarchy.

Triangles are completely accessible from the first 50 probabilities. Four-cycles, diamonds, and girth are also shallow. Five-cycle accessibility appears primarily between ranks 100 and 200.

The C6 ceiling is nonmonotone:

$$R^2_{C_6}(k=500)=0.524>R^2_{C_6}(k=1000)=0.484.$$

Adding dimensions does not guarantee improved ridge performance in this high-dimensional setting.

##### (n=16)

| Target | (k=100) | (k=1000) |
| ------ | ------: | -------: |
| (C_3)  |   1.000 |    1.000 |
| (C_4)  |   0.996 |    1.000 |
| (C_5)  |   0.335 |    0.982 |

The first 100 exact probabilities retain complete triangle and 4-cycle accessibility but only partial 5-cycle accessibility.

#### Primary finite-shot results at (n=14)

The most informative common depth is:

$$k=500.$$

| Target   | (2^{20}) shots | (2^{22}) shots | (2^{24}) shots | Exact (k=500) |
| -------- | -------------: | -------------: | -------------: | ------------: |
| (C_3)    |          0.715 |          0.950 |          0.994 |         1.000 |
| (C_4)    |       (-0.010) |          0.167 |          0.684 |         0.998 |
| (C_5)    |       (-0.016) |       (-0.013) |       (-0.015) |         0.927 |
| (C_6)    |          0.043 |          0.105 |          0.140 |         0.524 |
| Diamonds |          0.314 |          0.522 |          0.588 |         0.994 |
| Girth    |          0.358 |          0.734 |          0.888 |         0.993 |

All six targets remain at the prediction floor through:

$$2^{17}=131{,}072$$

shots.

Substantial recovery first appears at:

$$2^{20}=1{,}048{,}576$$

shots, but only for selected targets and sufficiently deep heads.

#### Triangle recovery

Triangle count is the only target to recover at least 90% of its exact-vector ceiling within the tested ladder.

At (n=14), the estimated minimum-over-depth thresholds are:

$$S_{90}\approx2^{21.57}\approx3.11\times10^6,$$

and:

$$S_{95}=2^{22}=4{,}194{,}304.$$

The selected depth is:

$$k=500.$$

At the measured budgets:

$$R^2_{C_3}=0.715\quad\text{at }2^{20},$$

$$R^2_{C_3}=0.950\quad\text{at }2^{22},$$

and:

$$R^2_{C_3}=0.994\quad\text{at }2^{24}.$$

The recovery transition is sharp rather than gradual.

#### Four-cycle recovery

Four-cycle count does not reach 90% of its exact ceiling.

At:

$$2^{24}=16{,}777{,}216$$

shots, its strongest score is:

$$R^2_{C_4}=0.684,$$

compared with an exact ceiling of approximately:

$$0.998.$$

The recovered fraction is approximately:

$$68.5%.$$

The target remains near the prediction floor at (2^{20}) and reaches only approximately (0.17) at (2^{22}).

Thus, even an almost perfectly decodable exact-vector statistic remains only partially recoverable after more than sixteen million shots per graph.

#### Five-cycle recovery

Five-cycle count remains at the prediction floor across every tested shot budget and depth.

At the largest budget:

$$R^2_{C_5}\approx-0.015$$

for the deeper heads, compared with:

$$R^2_{C_5}=0.928$$

from the exact top-1,000 vector.

This is the strongest finite-shot failure in the experiment.

The result confirms that ideal rank-depth accessibility and finite-shot accessibility are different properties. The exact C5 signal is present, strong, and linearly decodable, but empirical sorting does not recover the required fine probability structure within:

$$2^{24}$$

shots.

#### Six-cycle recovery

C6 becomes weakly positive but remains far below its exact-vector ceiling.

At the largest budget:

$$R^2_{C_6}=0.140$$

at (k=500), compared with:

$$R^2_{C_6}=0.524.$$

This recovers approximately:

$$26.7%$$

of the corresponding exact score.

At (k=200), the finite score is nearly the same:

$$0.139,$$

against a lower exact ceiling of:

$$0.391.$$

The target remains substantially shot limited throughout the ladder.

#### Diamond recovery

Diamond count begins to emerge at:

$$2^{20}$$

shots when at least 200 empirical ranks are retained.

At (k=500):

$$R^2_D=0.314\quad\text{at }2^{20},$$

$$R^2_D=0.522\quad\text{at }2^{22},$$

and:

$$R^2_D=0.588\quad\text{at }2^{24}.$$

The exact ceiling is:

$$R^2_D=0.994.$$

Only approximately:

$$59.2%$$

of the exact score is recovered by the largest budget.

Diamonds emerge earlier than 4-cycles under finite sampling, despite both being almost exactly accessible from the ideal representation.

#### Girth recovery

Girth exhibits the strongest finite-shot recovery after triangles.

At (k=500):

$$R^2_{\text{girth}}=0.358\quad\text{at }2^{20},$$

$$R^2_{\text{girth}}=0.734\quad\text{at }2^{22},$$

and:

$$R^2_{\text{girth}}=0.888\quad\text{at }2^{24}.$$

The exact ceiling is:

$$0.993.$$

The recovered fraction at the largest budget is:

$$89.4%.$$

Girth therefore narrowly fails the prespecified 90% threshold. Its “not reached” classification should not be interpreted as lack of substantial recovery.

The result is instead a lower-bound statement:

$$S_{90,\text{girth}}>2^{24}$$

under the tested grid.

#### Primary finite-shot results at (n=16)

At (k=1000), the confirmation results are:

| Target | (2^{20}) shots | (2^{22}) shots | (2^{24}) shots | Exact |
| ------ | -------------: | -------------: | -------------: | ----: |
| (C_3)  |          0.718 |          0.951 |          0.994 | 1.000 |
| (C_4)  |          0.003 |          0.199 |          0.668 | 1.000 |
| (C_5)  |       (-0.001) |       (-0.001) |       (-0.001) | 0.982 |

The three recovery profiles closely reproduce the (n=14) pattern.

#### Cross-order triangle threshold

At (n=16), the estimated thresholds are:

$$S_{90}\approx2^{21.56}\approx3.09\times10^6,$$

and:

$$S_{95}\approx2^{21.99}\approx4.17\times10^6.$$

These are effectively identical to the (n=14) estimates:

| Census | 90% threshold | 95% threshold |
| ------ | ------------: | ------------: |
| (n=14) |   (2^{21.57}) |   (2^{22.00}) |
| (n=16) |   (2^{21.56}) |   (2^{21.99}) |

The replicated transition is one of E15’s strongest findings.

Within the tested cubic families and fixed circuit, triangle-count recovery is governed by a stable per-graph shot scale of approximately:

$$3\text{--}4\times10^6$$

shots.

#### Cross-order four-cycle recovery

At the maximum budget:

$$R^2_{C_4}=0.684\quad\text{at }n=14,$$

and:

$$R^2_{C_4}=0.668\quad\text{at }n=16.$$

Both exact ceilings are approximately one.

The near-identical finite-shot values indicate that the incomplete C4 recovery is not an isolated (n=14) effect.

#### Cross-order five-cycle failure

At the maximum budget:

$$R^2_{C_5}\approx-0.015\quad\text{at }n=14,$$

and:

$$R^2_{C_5}\approx-0.001\quad\text{at }n=16.$$

The corresponding exact scores are:

$$0.928\quad\text{and}\quad0.982.$$

The failure therefore replicates across graph orders despite stronger ideal C5 accessibility at (n=16).

#### Shot-recovery ordering

The finite-shot ordering differs from the exact-vector hierarchy.

At (n=14), the practical ordering by recovery at (2^{24}) is approximately:

$$C_3>\text{girth}>C_4>D>C_6\gg C_5.$$

The exact-vector ordering at the same broad depths is:

$$C_3\approx C_4\approx D\approx\text{girth}>C_5>C_6.$$

Finite sampling therefore reorders which graph properties are practically accessible.

The exact geometry predicts what information exists. It does not by itself predict how efficiently empirical rank statistics recover that information.

#### Head discovery and rank stability

The auxiliary diagnostic measures two quantities relative to the exact rank coordinates:

1. the fraction of exact top-(k) coordinates receiving at least one count;
2. the Spearman correlation between counts in those exact-rank coordinates and their exact probabilities.

This is a simulation diagnostic. A real sampler does not know the exact-rank identity of each observed bitstring after the representation is reduced to sorted counts.

##### Selected (n=14) results

|    Shots | (k=200) discovery | (k=200) (\rho) | (k=500) discovery | (k=500) (\rho) | (k=1000) discovery | (k=1000) (\rho) |
| -------: | ----------------: | -------------: | ----------------: | -------------: | -----------------: | --------------: |
| (2^{20}) |             0.994 |          0.931 |             0.733 |          0.899 |              0.421 |           0.805 |
| (2^{22}) |             1.000 |          0.948 |             0.906 |          0.916 |              0.622 |           0.853 |
| (2^{24}) |             1.000 |          0.959 |             0.998 |          0.921 |              0.850 |           0.923 |

##### Selected (n=16) results

|    Shots | (k=1000) discovery | (k=1000) (\rho) |
| -------: | -----------------: | --------------: |
| (2^{20}) |              0.561 |           0.831 |
| (2^{22}) |              0.803 |           0.850 |
| (2^{24}) |              0.977 |           0.881 |

The diagnostics explain part, but not all, of the recovery behavior.

Triangle recovery appears once the relevant deeper heads are substantially observed and rank stable.

However, complete or near-complete head discovery is not sufficient for all targets. At (n=14), the first 200 exact ranks are fully discovered with high rank correlation at (2^{24}), yet C5 remains at the prediction floor.

Finite-shot recovery therefore depends on the magnitude and organization of the target-specific probability differences, not merely on whether the head entries are observed.

#### Shallow ideal accessibility is not shallow shot accessibility

Diamonds and girth are nearly exact from the ideal first 50 probabilities:

$$R^2_D=0.981,\qquad R^2_{\text{girth}}=0.921.$$

At (2^{24}) shots, the empirical first-50 scores are only:

$$R^2_D=0.056,\qquad R^2_{\text{girth}}=0.044.$$

Their useful finite-shot recovery occurs only once approximately 200 or more empirical ranks are retained.

The “shallow” ideal signal therefore depends on probability differences too fine to be reliably reconstructed by the empirically sorted first 50 counts.

E15 refines the E13 conclusion:

> Diamonds and girth are shallow in the exact rank representation, but they are not shot-efficient shallow statistics.

#### Cospectral separation against sampling noise

E15 compares the empirical full-vector distance between exact cospectral mates with the distance between two independent samples of the same graph.

The ratio is:

$$R_{\text{sep}}=\frac{|\widehat{\mathbf p}(G)-\widehat{\mathbf p}(H)|_1}{\frac{1}{2}\left(|\widehat{\mathbf p}^{(a)}(G)-\widehat{\mathbf p}^{(b)}(G)|_1+|\widehat{\mathbf p}^{(a)}(H)-\widehat{\mathbf p}^{(b)}(H)|_1\right)}.$$

A ratio near one means that the mate separation is no larger than ordinary repeat-sampling variation.

##### (n=14)

|    Shots | Mean ratio |       Range |
| -------: | ---------: | ----------: |
| (2^{10}) |      1.054 | 0.500–2.000 |
| (2^{14}) |      1.068 | 0.737–1.720 |
| (2^{17}) |      1.011 | 0.349–2.031 |
| (2^{20}) |      1.014 | 0.612–1.253 |
| (2^{22}) |      0.873 | 0.587–1.692 |
| (2^{24}) |      1.215 | 0.932–1.654 |

##### (n=16)

|    Shots | Mean ratio |       Range |
| -------: | ---------: | ----------: |
| (2^{20}) |      1.034 | 0.370–1.972 |
| (2^{22}) |      0.991 | 0.446–1.862 |
| (2^{24}) |      1.004 | 0.465–2.189 |

The mean ratios remain approximately one throughout the ladder.

The exact cospectral distinctions therefore remain unresolved relative to multinomial sampling noise even at:

$$2^{24}$$

shots.

This confirms the finite-shot wall found in E7S.

#### Separation sample sizes

The separation diagnostic uses only three inexpensive sampling replicates.

At (n=14), three exact cospectral pairs produce:

$$3\times3=9$$

pair-replicates per budget.

At (n=16), the cospectral classes produce 43 pairwise comparisons and therefore:

$$43\times3=129$$

pair-replicates per budget.

The (n=16) result is substantially better supported. The fluctuation of the (n=14) mean ratio to (1.215) at the largest budget should not be interpreted as demonstrated resolvability from only nine dependent pair-replicates.

#### Replicate stability

The 30-replicate standard deviations are generally small compared with the large target-level differences.

At (2^{24}) and the useful deeper heads:

* triangle replicate SD is approximately (0.000)–(0.001);
* 4-cycle SD is approximately (0.007) at (n=16) and (0.023) at (n=14);
* diamond SD is approximately (0.008);
* girth SD is approximately (0.005);
* C5 remains stably at the floor.

The experiment therefore distinguishes stable finite-shot failure from a noisy estimate whose mean happens to be low.

These standard deviations measure sampling variation across the 30 simulated representation replicates. They are not confidence intervals over graph populations, folds, or alternative circuit parameters.

#### Relationship to E7S

E15 confirms the principal E7S findings under the explicit independent-test protocol:

* all targets remain at the floor at small and moderate budgets;
* triangle count emerges first;
* 4-cycle count becomes substantial only near the top of the ladder;
* C6 remains weak;
* C5 remains absent through (2^{24});
* exact cospectral separation remains comparable to sampling noise.

The 30-replicate design substantially strengthens these conclusions by showing that the observed ordering is stable across sampling realizations.

#### Relationship to E13

E13 showed that ideal structural accessibility is distributed differently through the sorted probability ranks:

* triangles are very shallow;
* diamonds and girth are shallow;
* 4- and 5-cycle information extends deeper;
* cospectral separation accumulates through a broad probability tail.

E15 shows that rank depth and shot accessibility are related but not interchangeable.

In particular:

* C3 requires approximately 200–500 empirical ranks for reliable recovery despite being exact at ideal (k=50);
* diamonds and girth also require deeper empirical heads than their ideal truncation results suggest;
* C5 remains inaccessible even when its relevant exact head is substantially sampled.

#### Relationship to the exact-cospectral experiments

E14 and E20 concern distinctions present in exact ideal probability vectors.

E15 shows that numerical distinctness in the exact representation does not imply finite-shot observability.

The complete exact readout can:

* distinguish cospectral graphs;
* carry non-spectral target directions;
* and remain census-level injective,

while its empirical estimates remain indistinguishable from repeat-sampling noise at millions of shots.

The paper should preserve this distinction explicitly:

$$\boxed{\text{ideal representational separation}\neq\text{finite-shot operational separation}}$$

#### What the experiment establishes

The completed results establish that:

1. **The four replicate slices reconstruct the complete planned experiment.**

   Every one of the 198 grid cells contains exactly 30 unique replicate indices.

2. **Independent-test finite-shot sampling reproduces the E7S recovery pattern.**

3. **Triangle recovery is replicated across graph orders.**

   Both censuses reach 90% of the exact score near (3.1\times10^6) shots and 95% near (4.2\times10^6) shots.

4. **Four-cycle prediction remains only partially recovered at (2^{24}) shots.**

   The scores are approximately (0.68) at both graph orders.

5. **Five-cycle prediction remains completely absent through (2^{24}) shots.**

   This failure replicates at (n=14) and (n=16).

6. **C6 remains weakly recoverable at (n=14).**

7. **Diamonds and girth emerge before C4 but do not reach their exact ceilings.**

8. **Girth nearly reaches the 90% criterion at the largest budget.**

9. **Ideal shallow accessibility does not guarantee shallow finite-shot recovery.**

10. **Head discovery and rank stability are necessary but insufficient explanations for target recovery.**

11. **Exact cospectral mate separation remains at the repeat-sampling noise scale through (2^{24}) shots.**

12. **The principal finite-shot conclusions are stable across 30 independent representation replicates.**

E15 therefore converts the qualitative E7S sampling wall into replicated target-specific recovery curves and explicit shot-threshold statements.

#### Necessary qualifications

The experiment models only ideal multinomial shot noise.

It does not include:

* gate error;
* readout error;
* decoherence;
* compilation effects;
* qubit connectivity;
* drift;
* or error mitigation.

The reported shot counts are therefore optimistic lower bounds for hardware execution.

The thresholds are per graph representation. A training set containing hundreds or thousands of graphs would require the stated number of shots separately for each graph.

The total acquisition cost is consequently much larger than the per-graph threshold suggests.

The threshold values near:

$$2^{21.57}$$

are interpolations between measured budgets, not directly evaluated shot counts.

The interpolation is linear in:

$$\log_2 S$$

between a sparse budget ladder. No uncertainty interval is computed for the crossing location.

Thresholds are defined relative to the exact ridge score at each depth, not relative to perfect prediction.

For example, a target with an exact score of (0.524) needs only to reach approximately (0.472) to satisfy a 90% criterion.

The threshold routine selects the earliest crossing across all tested depths. It is therefore an oracle minimum over a prespecified depth grid rather than a threshold for one fixed universal readout depth.

Finite-shot mean curves are not forced to be monotone. The threshold routine uses the first observed upward crossing without isotonic smoothing.

Only C3 crosses the threshold, so this issue does not materially affect the headline result.

The exact-vector ceilings are themselves ridge-model results and can be nonmonotone with depth. They should not be interpreted as information-theoretic ceilings.

The ridge procedure retains the near-zero regularization grid examined in E10. Some exact QuIC probes depend on low-variance directions and can be sensitive to solver and inner-fold choices.

E15 does not repeat the independent linear-algebra validation for every finite-shot cell.

The 30-replicate SD summarizes replicate-level mean outer-fold scores. It does not incorporate:

* uncertainty from alternative graph folds;
* target sampling;
* circuit parameters;
* or graph-family selection.

The discovery, rank-correlation, and cospectral-separation diagnostics use only three cheap replicates rather than the full 30.

The discovery diagnostic follows counts in the exact-rank coordinate system. It is useful for simulation analysis but is not directly available from a sorted empirical readout without knowing the exact probabilities.

The signal-versus-noise arithmetic cell appears in the unexecuted E15d template but is absent from the executed merge artifact. E15 should not report new numerical values from that diagnostic unless the cell is run or the values are taken explicitly from E7S.

The same-realization E7S results are not rebuilt inside E15. The expected equivalence is justified by independent graph-row sampling, but E15’s attached outputs do not contain a numerical cell-by-cell difference table.

The (n=16) confirmation grid is intentionally restricted. It does not establish cross-order recovery behavior for:

* C6;
* diamonds;
* or girth.

The cospectral-separation statistic uses pair-replicates that are not independent when pairs share graph members or when several pairs use one sampled count matrix.

No inferential test is attached to the separation ratios.

Finally, the experiment concerns:

* connected cubic graphs;
* two graph orders;
* one canonical circuit;
* one repetition;
* and sorted empirical frequencies.

The recovery thresholds should not be generalized to arbitrary graphs or circuit families.

#### Overall assessment

E15 provides a strong and unusually direct finite-shot characterization.

The result is not that QuIC’s ideal structure smoothly degrades as shot count decreases. Instead, the targets separate into sharply different operational regimes.

Triangle count undergoes a replicated transition near:

$$3\text{--}4\times10^6$$

shots per graph.

At more than sixteen million shots:

* triangles are essentially fully recovered;
* girth reaches approximately (0.89);
* 4-cycles reach approximately (0.67)–(0.68);
* diamonds reach approximately (0.59);
* C6 remains near (0.14);
* C5 remains at the prediction floor.

The same circuit representation that yields almost exact ideal prediction for C3, C4, C5, diamonds, and girth therefore exhibits radically different finite-shot accessibility across those targets.

The cross-order replication is particularly clean:

$$C_3:\ 0.994\text{ at both orders},$$

$$C_4:\ 0.684\text{ and }0.668,$$

$$C_5:\ \text{prediction floor at both orders}.$$

Exact cospectral separations remain comparable to ordinary repeat-sampling noise throughout the entire ladder.

The appropriate central claim is:

> Under independent multinomial train and test sampling, QuIC’s ideal structural coordinates have sharply different finite-shot recovery scales. Triangle prediction reaches 90% of its exact-vector score at approximately (3.1\times10^6) shots per graph and 95% near (4.2\times10^6), with nearly identical thresholds at (n=14) and (n=16). At (2^{24}) shots, 4-cycle prediction remains near (0.67), girth reaches (0.89), diamonds reach (0.59), C6 remains weak, and 5-cycle prediction remains at the floor despite exact scores above (0.92). Exact cospectral mate distances also remain comparable to repeat-sampling noise. E15 therefore shows that ideal injectivity and decodability do not imply practical finite-shot observability, and that the rank-stratified structural hierarchy is also a hierarchy of sampling difficulty.


### E16 / E17 - Readout Quotient and Label Control

#### Experimental design

E16 and E17 test two related properties of the sorted QuIC readout:

1. whether sorting removes dependence on vertex labeling;
2. whether the resulting label-invariant quotient collapses structurally distinct graphs.

The analysis uses two complete graph censuses:

* **11,117 connected graphs at (n=8)**;
* **509 connected cubic graphs at (n=14)**.

Each graph is mapped to its complete descending-sorted probability vector:

$$
\mathbf p(G)
$$

============
$$
	ext{sort}*{\downarrow}
\left(
|\langle z|\psi_G\rangle|^2
\right)*{z\in{0,1}^n}.
$$

The circuit uses the fixed canonical configuration:

* maximum encoding rotation (2.875);
* entangler angle (2.0);
* mixer angle (0.1);
* one entangler–mixer repetition.

The degree-proportional encoder is used in both censuses. On the cubic census, every vertex has degree three, so the encoder reduces to the uniform rotation:

$$
R_X(2.875)
$$

on every qubit.

The (n=8) census is degree heterogeneous and therefore uses genuinely different rotations for vertices of different degrees.

The experiment contains four components.

1. **Deterministic relabeling control**

   Every graph is evaluated under:

   * its canonical nauty labeling;
   * a deterministic nonidentity cyclic relabeling;
   * one seeded-random relabeling.

   The complete sorted statevector distributions must agree to floating-point precision.

   An additional sample of 200 graphs at each order is tested under 20 further random relabelings per graph.

2. **Sampled relabeling control**

   At a single shot budget:

   $$
   S=2^{20}=1{,}048{,}576,
   $$

   the distance between independently sampled readouts from two labelings of the same graph is compared with the distance between two independent samples from the same labeling.

3. **Readout quotient**

   Graphs are grouped by their sorted readout vectors.

   For each target (y), the planned quotient statistic is:

   $$
   \eta_y
   $$
   
   ======
   $$
   \frac{
   \text{collision sets preserving }y
   }{
   \text{all multi-graph collision sets}
   }.
   $$

   A value of one would indicate that every observed collision is benign for target (y), while a value below one would indicate target information lost by the quotient.

5. **Distance-ordering agreement**

   On 4,000 sampled graph pairs, the experiment computes the Spearman correlation between readout-space (L_1) distance and target-space distance.

   For scalar graph invariants, target distance is the absolute difference. For the sorted degree sequence, it is the Hamming distance between the two degree tuples.

The target lists are:

##### (n=8)

* degree sequence;
* triangle count;
* 4-cycle count;
* vertex connectivity.

##### (n=14)

* triangle count;
* 4-cycle count;
* 5-cycle count;
* 6-cycle count;
* diamond count.

Diamond count is certified through the cubic identity:

$$
	ext{tr}(A^6)
$$

======================
$$
87n
+
6C_3
+
96C_4
+
12(C_6+D).
$$

#### Why sorting is label invariant

Let (P) be a permutation matrix representing a relabeling of the graph.

The relabeled adjacency matrix is:

$$
A' ==
PAP^\top.
$$

The degree encoder, edge entanglers, and mixer are permuted consistently with the qubits. The resulting computational-basis probabilities are therefore permuted among bitstring coordinates.

Sorting discards those coordinate identities:

$$
	ext{sort}_{\downarrow}  \mathbf p(PGP^\top) 	ext{sort}_{\downarrow} \mathbf p(G).
$$

Permutation invariance is therefore a mathematical property of the readout construction. The experiment tests whether the implemented circuit and numerical pipeline preserve that equality in practice.

#### Deterministic relabeling results

| Census | Graphs checked under fixed alternates | Worst cross-label (L_1) | Graphs in extended check | Random relabelings per graph | Worst extended (L_1) |
| ------ | ------------------------------------: | ----------------------: | -----------------------: | ---------------------------: | -------------------: |
| (n=8)  |                                11,117 |    (1.86\times10^{-15}) |                      200 |                           20 | (1.69\times10^{-15}) |
| (n=14) |                                   509 |    (1.74\times10^{-15}) |                      200 |                           20 | (1.75\times10^{-15}) |

Every tested relabeling satisfies the prespecified tolerance:

$$
L_1<10^{-12}.
$$

The largest discrepancies are approximately:

$$
10^{-15},
$$

which is the expected floating-point accumulation scale for independently constructed but mathematically identical statevectors.

The result holds across:

* all 11,117 connected graphs at (n=8);
* all 509 connected cubic graphs at (n=14);
* 8,000 additional random-relabeling comparisons.

The implemented sorted readout is therefore invariant to vertex relabeling to machine precision on both complete censuses.

#### Sampled relabeling results

At:

$$
S=2^{20},
$$

the experiment reports:

$$
R
=

\frac{
L_1(\text{sample from canonical labeling},
\text{sample from relabeled graph})
}{
L_1(\text{two independent samples from canonical labeling})
}.
$$

| Census | Graphs | Mean ratio | Median ratio | 95th percentile | Maximum |
| ------ | -----: | ---------: | -----------: | --------------: | ------: |
| (n=8)  |    200 |      1.028 |        0.999 |           1.286 |   1.860 |
| (n=14) |    200 |      1.088 |        0.983 |           2.074 |   2.635 |

The median ratio is essentially one at both graph orders:

$$
0.999
\quad\text{and}\quad
0.983.
$$

Thus, the typical empirical difference between two labelings is the same size as the difference between two independent samples of one labeling.

The ratio has a wider upper tail at (n=14). This is expected because it divides two random distances, and unusually small denominator values can produce large ratios.

The result supports the narrower statement:

> At (2^{20}) shots, empirical differences between labelings are consistent with ordinary same-graph multinomial resampling variability.

The experiment does not show that independently sampled histograms from two labelings are numerically identical. They should not be identical because they are independent random samples from the same underlying distribution.

#### Readout discrimination

The quotient grouping uses coordinate-wise rounding to 12 decimal places before hashing the sorted vectors.

| Census | Distinct readouts | Census size | Multi-graph collision sets |
| ------ | ----------------: | ----------: | -------------------------: |
| (n=8)  |            11,117 |      11,117 |                          0 |
| (n=14) |               509 |         509 |                          0 |

Every graph receives a distinct computed readout at both graph orders.

Because no multi-graph collision sets exist, the target-preservation statistics are undefined:

##### (n=8)

$$
\eta_{\mathrm{degree}}, \eta_{C_3}, \eta_{C_4}, \eta_{\mathrm{connectivity}} \text{not applicable}.
$$

##### (n=14)

$$
\eta_{C_3}, \eta_{C_4}, \eta_{C_5}, \eta_{C_6}, \eta_D \text{not applicable}.
$$

There is no observed collapse whose target preservation must be classified as benign or lossy.

Distinct 12-decimal keys also rule out literal equality of the computed floating-point vectors: two exactly equal arrays would necessarily produce the same rounded key.

The experiment therefore establishes census-level injectivity of the computed readout at the tested angles. It does not prove universal injectivity for arbitrary graph orders, graph families, or parameter choices.

#### Effective rank

| Census | Readout dimension | Centered numerical rank |
| ------ | ----------------: | ----------------------: |
| (n=8)  |               256 |                     255 |
| (n=14) |            16,384 |                     508 |

The numerical rank uses the threshold:

$$
s_i

>

10^{-10}s_{\max}.
$$

Both values attain the maximum rank permitted by the corresponding data geometry.

At (n=8), every probability vector sums to one. After centering, all vectors lie in the hyperplane:

$$
\sum_z x_z=0,
$$

whose dimension is:

$$
256-1=255.
$$

The observed rank is exactly 255.

At (n=14), the centered matrix contains 509 graph rows, so its maximum possible rank is:

$$
509-1=508.
$$

The observed rank is exactly 508.

Thus, the complete census readouts are not confined to a lower-dimensional linear subspace beyond the unavoidable normalization and centering constraints.

This does not contradict the effective ranks near three observed within the E1 fixed-cycle strata. The full census can span the maximum available rank while individual structurally conditioned regions remain locally low dimensional.

#### Candidate nearest-readout distances

The notebook orders graphs by their largest probability and searches the 25 neighboring positions on either side for a close readout.

The reported local-search distances are:

| Census | Minimum candidate (L_1) |       5th percentile |               Median |
| ------ | ----------------------: | -------------------: | -------------------: |
| (n=8)  |    (2.159\times10^{-5}) | (4.400\times10^{-3}) | (3.126\times10^{-2}) |
| (n=14) |    (5.868\times10^{-8}) | (2.015\times10^{-7}) | (1.061\times10^{-6}) |

The scales differ substantially.

At (n=8), nearby readouts are typically separated by approximately:

$$
10^{-2}.
$$

At (n=14), nearby cubic-graph readouts are separated at approximately:

$$
10^{-6},
$$

with the smallest candidate distance near:

$$
6\times10^{-8}.
$$

This agrees in scale with the previously observed precision wall among close cubic and cospectral graph pairs.

However, the notebook does not compute an exhaustive nearest-neighbor search. It examines only a local window after ordering graphs by the first probability coordinate.

The reported minimum is therefore the smallest distance found by that candidate search, not a certified global nearest-neighbor minimum.

The zero-collision result does not depend on this approximation. The stronger statement that:

$$
5.868\times10^{-8}
$$

is the global separation floor of the complete cubic census requires an exhaustive or certified nearest-neighbor computation.

#### Distance-ordering agreement

##### (n=8)

| Target              | Spearman (\rho) |
| ------------------- | --------------: |
| Degree sequence     |           0.091 |
| Triangle count      |           0.064 |
| 4-cycle count       |           0.076 |
| Vertex connectivity |           0.095 |

##### (n=14)

| Target         | Spearman (\rho) |
| -------------- | --------------: |
| Triangle count |           0.906 |
| 4-cycle count  |           0.301 |
| 5-cycle count  |           0.118 |
| 6-cycle count  |           0.174 |
| Diamonds       |           0.448 |

The cubic results closely reproduce the global geometric ordering observed in E1.

Triangle count dominates:

$$
\rho=0.906.
$$

Four-cycle count has a weaker but clear marginal association:

$$
\rho=0.301.
$$

Five-cycle count remains weak globally:

$$
\rho=0.118,
$$

consistent with E1’s result that its stronger organization becomes visible only after conditioning on triangles and 4-cycles.

Diamond count has the second-largest observed association:

$$
\rho=0.448.
$$

This indicates that diamond differences are strongly reflected in global readout distances, although the result does not establish information beyond the complete adjacency spectrum.

The (n=8) correlations are uniformly small:

$$
\rho\in
[0.064,0.095].
$$

The readout distinguishes every graph in the complete heterogeneous census, but its global metric is only weakly organized by the four tested targets.

This provides an important distinction:

$$
\boxed{
\text{injectivity}
\neq
\text{target-aligned geometry}
}
$$

A representation can retain every graph-level distinction without arranging graphs according to a small set of simple invariants.

#### Relationship to the earlier experiments

E16/E17 connects several earlier observations.

E1 showed that the cubic readout geometry is hierarchically organized by:

$$
C_3
\rightarrow
C_4
\rightarrow
C_5.
$$

The current sampled-pair correlations reproduce the same global ordering.

E2 and E13 showed that cycle, diamond, and girth information is linearly accessible from the probability head. E16/E17 shows that sorting does not destroy graph-level discrimination while creating that invariant representation.

E6 showed that the same circuit construction does not produce comparably organized geometry on heterogeneous-degree graph families. The weak (n=8) ordering correlations are consistent with that limitation.

E7S showed that finite-shot structural decoding is difficult. The sampled-label control addresses a different issue: permutation invariance survives sampling even when subtle graph-to-graph structural differences remain below the sampling-noise floor.

The experiment therefore separates three properties:

1. **label invariance**;
2. **graph discrimination**;
3. **target-aligned geometry**.

They are related but not equivalent.

#### What the experiment establishes

The completed results establish that:

1. **The implemented sorted QuIC readout is permutation invariant to machine precision.**

   Across both complete censuses and the extended relabeling checks, the worst deterministic discrepancy is below:

   $$
   2\times10^{-15}.
   $$

2. **Sampled relabeling differences are consistent with same-graph resampling noise.**

   At (2^{20}) shots, the median cross-label-to-resample ratio is approximately one at both graph orders.

3. **No computed readout collisions occur in either complete census.**

   All 11,117 (n=8) graphs and all 509 (n=14) cubic graphs receive distinct sorted vectors.

4. **No target-specific quotient loss is observed.**

   The planned $\eta_y$ statistics are unnecessary because there are no collision sets.

5. **The census readout matrices attain their maximum possible numerical ranks.**

   The observed ranks are 255 at (n=8) and 508 at (n=14).

6. **Graph discrimination does not imply universal target organization.**

   The cubic geometry strongly tracks triangles and diamonds, while the heterogeneous (n=8) geometry is only weakly aligned with the tested invariants.

7. **The cubic distance-ordering hierarchy replicates under a separate sampled-pair analysis.**

   Triangle count again dominates globally, followed by diamonds and 4-cycles.

The readout quotient is therefore empirically lossless on the two tested finite censuses, while the organization of the surviving geometry remains graph-family dependent.

#### Necessary qualifications

Permutation invariance is a property of the construction rather than a newly discovered empirical phenomenon. The deterministic experiment validates the implementation and rules out labeling bugs; it does not supply the primary mathematical reason for invariance.

The quotient grouping uses 12-decimal coordinate rounding. It is not an arbitrary-precision equality test.

The absence of rounded collisions is sufficient to rule out literal floating-point equality, but the result should be described as empirical census-level injectivity rather than a proof of exact real-arithmetic injectivity.

The candidate nearest-neighbor computation is not exhaustive. Graphs are ordered by their largest probability, and only a local window of 25 positions on each side is searched.

Consequently, the reported minimum distances are upper bounds on the true nearest-neighbor minima. The claim that the (n=14) value is the global census separation floor is not established by the current implementation.

The sampled-regime ratio is descriptive. No formal equivalence test compares the cross-label and same-label distance distributions, and ratios can have heavy upper tails when the denominator is small.

Only one shot budget is tested:

$$
S=2^{20}.
$$

The result establishes consistency with resampling noise at that budget, not across the full finite-shot regime.

The sampled ordering analysis uses 4,000 randomly generated pairs. Pairs can share graphs or repeat in opposite orientations, so they are not independent observations.

No permutation significance tests or confidence intervals accompany the ordering correlations. They should be interpreted as descriptive effect sizes.

The (n=8) and (n=14) censuses differ in both graph order and graph family. The (n=8) circuit also uses a genuinely degree-dependent encoder, whereas the cubic encoder is uniform. Differences between their geometries cannot be attributed to graph order alone.

The numerical-rank result depends on the relative threshold:

$$
10^{-10}s_{\max}.
$$

It establishes full rank at that numerical resolution, not a scale-independent effective dimension.

No result in E16/E17 establishes:

* efficient decodability;
* finite-shot graph discrimination;
* hardware advantage;
* or universal injectivity.

Finally, all collision and rank results use ideal statevector probabilities. E7S shows that exact graph distinctions can remain operationally inaccessible under realistic sampling budgets.

#### Overall assessment

E16/E17 confirms that sorting performs its intended role.

Across every graph in both complete censuses, relabeling changes the sorted statevector probabilities only at the floating-point floor. At one million shots, independently sampled readouts from two labelings differ by approximately the same amount as two independent samples of one labeling.

The quotient also shows no observed loss of graph identity:

$$
11{,}117/11{,}117
$$

(n=8) graphs and:

$$
509/509
$$

(n=14) graphs have distinct computed readouts.

The centered readout matrices attain their maximum possible ranks, indicating that sorting does not collapse the censuses into a small global linear subspace.

The geometric consequences differ sharply by graph family. The cubic readout strongly respects triangle and diamond differences and reproduces the hierarchy observed in E1. The heterogeneous (n=8) readout is injective but only weakly organized by degree sequence, short cycles, or connectivity.

The appropriate central claim is:

> The descending-sorted QuIC probability vector is permutation invariant to machine precision and produces no observed graph collisions on the complete connected (n=8) census or the complete connected cubic (n=14) census. The resulting readout matrices attain their maximum possible numerical ranks, so the label quotient discards no observed graph distinction at these orders. However, injectivity does not guarantee target-aligned geometry: the cubic census retains strong cycle and diamond organization, while the heterogeneous census does not.

### E18 - Circuit Family Screen

#### Experimental design

E18 compares seven quantum graph circuits constructed from a common gate family.

The analysis uses two complete graph censuses:

* **11,117 connected graphs at (n=8)**;
* **509 connected cubic graphs at (n=14)**.

Every circuit produces a descending-sorted Born-probability vector. The decoder uses:

* the complete 256-dimensional vector at (n=8);
* the first 1,000 coordinates of the 16,384-dimensional vector at (n=14).

The tested circuits are:

1. **C0 — preparation-only control**

   A uniform graph-independent (R_X) preparation with no edge gate and no mixer.

2. **C1 — phase-only control**

   The same uniform preparation followed by graph-edge (R_{ZZ}) gates, with no mixer.

3. **C2 — one-repetition degree-encoded X-mixer circuit**

   A degree-scaled (R_X) preparation followed by one graph-edge (R_{ZZ}) layer and one uniform (R_X) mixer.

4. **C3 — QAOA-style preparation**

   A (|+\rangle^{\otimes n}) preparation followed by one graph-edge (R_{ZZ}) layer and one uniform (R_X) mixer.

5. **C4 — two-repetition degree-encoded X-mixer circuit**

   The C2 entangler–mixer block is repeated twice with tied angles.

6. **C5 — degree-encoded Y-mixer circuit**

   The C2 construction is retained, but the final (R_X) mixer is replaced by an (R_Y) mixer.

7. **C6 — non-equivariant index encoder**

   The degree encoder is replaced by an index-dependent rotation that deliberately changes under vertex relabeling.

The circuit angles are fixed throughout:

$$
\alpha=2.875,\qquad\gamma=2.0,\qquad\beta=0.1.
$$

No angle optimization is performed.

The target sets are:

##### (n=8)

* degree variance;
* triangle count;
* 4-cycle count;
* vertex connectivity.

##### (n=14)

* triangle count;
* 4-cycle count;
* 5-cycle count;
* 6-cycle count;
* diamond count;
* girth.

Diamond count is verified through the cubic identity:

$$
\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).
$$

All targets are decoded using five shuffled outer folds and the standing ridge grid:

$$
\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2}.
$$

The experiment is designed as a sequence of contrasts rather than as seven unrelated model evaluations:

* C0 and C1 test graph blindness;
* C2 versus C3 tests the preparation;
* C2 versus C4 tests circuit depth;
* C2 versus C5 tests the mixer axis;
* C2 versus C6 tests permutation equivariance.

#### Encoder implemented by the notebook

The notebook names C2 the canonical QuIC circuit, but the implementation does not use the normalized canonical encoder.

The implemented degree rotation is:

$$
R_X(\alpha d_i).
$$

The canonical QuIC encoder used in the principal characterization experiments is:

$$
R_X\left(\alpha\frac{d_i}{\Delta}\right).
$$

On the cubic (n=14) census, the notebook therefore applies:

$$
R_X(2.875\times3)=R_X(8.625)
$$

to every qubit rather than:

$$
R_X(2.875).
$$

On the heterogeneous (n=8) census, the absolute rotations also differ from the normalized encoder and can become substantially larger than the stated encoder scale.

C2, C4, and C5 should therefore be described as **unnormalized degree-encoded circuits**, not as the canonical QuIC object.

This does not invalidate the internal circuit comparisons. All three use the same encoder, so the depth and mixer-axis contrasts remain controlled within the implemented family. It does prevent direct use of their numerical values as canonical QuIC results.

#### Graph-blindness controls

C0 and C1 are tested before the full screen.

For each census, one graph is compared with 50 other graphs. The worst cross-graph sorted-readout distances are:

| Census | C0 preparation only |        C1 phase only |
| ------ | ------------------: | -------------------: |
| (n=8)  |               0.000 | (5.99\times10^{-16}) |
| (n=14) |               0.000 | (5.65\times10^{-17}) |

Both circuits satisfy the graph-blindness threshold:

$$
L_1<10^{-12}.
$$

The full-census fingerprint counts provide a stronger census-wide confirmation:

| Census | C0 distinct readouts | C1 distinct readouts |
| ------ | -------------------: | -------------------: |
| (n=8)  |             1/11,117 |             1/11,117 |
| (n=14) |                1/509 |                1/509 |

C0 is graph blind because it contains no graph-dependent operation.

C1 contains graph-dependent edge gates, but they are diagonal in the computational basis and are not followed by a noncommuting mixer. They alter phase without altering the Born probabilities.

The result reproduces the mechanism established in E9:

$$
\boxed{\text{graph-dependent phase alone does not survive the probability readout}}
$$

A noncommuting layer is required to convert the phase information into graph-dependent measurement probabilities.

#### Readout distinctness

The full sorted probability vectors are rounded to 12 decimal places and hashed before distinct fingerprints are counted.

##### (n=8)

| Circuit                    | Distinct readouts | Census size |
| -------------------------- | ----------------: | ----------: |
| C0 preparation only        |                 1 |      11,117 |
| C1 phase only              |                 1 |      11,117 |
| C2 degree encoder, X mixer |            11,117 |      11,117 |
| C3 QAOA preparation        |            11,117 |      11,117 |
| C4 two repetitions         |            11,117 |      11,117 |
| C5 Y mixer                 |            11,117 |      11,117 |
| C6 non-equivariant         |            11,117 |      11,117 |

##### (n=14)

| Circuit                    | Distinct readouts | Census size |
| -------------------------- | ----------------: | ----------: |
| C0 preparation only        |                 1 |         509 |
| C1 phase only              |                 1 |         509 |
| C2 degree encoder, X mixer |               509 |         509 |
| C3 QAOA preparation        |               509 |         509 |
| C4 two repetitions         |               509 |         509 |
| C5 Y mixer                 |               509 |         509 |
| C6 non-equivariant         |               509 |         509 |

Every graph-dependent circuit distinguishes every graph in both censuses under the 12-decimal fingerprinting rule.

For C2 through C5, this is evidence that several related equivariant circuit constructions can produce census-level injective sorted readouts.

The C6 count has a different meaning. C6 distinguishes every graph in the canonical census labeling, but it does not define an isomorphism-invariant graph representation. A relabeling of the same graph can change its output.

Distinctness also does not imply that the resulting geometry is useful for a particular target. The circuit-by-target matrix shows substantial variation in decodability despite identical fingerprint counts.

#### Retained probability mass

At (n=8), the full probability vector has only 256 entries, so the nominal top-1,000 feature bank contains the complete distribution:

$$
m_{1000}=1.
$$

At (n=14), only the first 1,000 of 16,384 probabilities are retained.

| Circuit                    | Median retained mass at (n=14) |
| -------------------------- | -----------------------------: |
| C0 preparation only        |                         1.0000 |
| C1 phase only              |                         1.0000 |
| C2 degree encoder, X mixer |                         0.9218 |
| C3 QAOA preparation        |                         0.1051 |
| C4 two repetitions         |                         0.9268 |
| C5 Y mixer                 |                         0.8959 |
| C6 non-equivariant         |                         0.9544 |

The retained-mass differences are important.

C2, C4, C5, and C6 concentrate approximately 90% or more of their probability mass within the first 1,000 entries.

The QAOA-style C3 readout retains only:

$$
10.51%
$$

of its median probability mass.

The (n=14) decoder comparison therefore evaluates circuits through raw heads containing very different fractions of their complete distributions. C3’s weaker results may reflect both a less informative circuit and a substantially more diffuse readout.

The C2–C4 and C2–C5 comparisons are cleaner because their retained masses are similar.

#### Circuit-by-target results at (n=8)

| Circuit                    | Degree variance |    (C_3) |    (C_4) | Connectivity |
| -------------------------- | --------------: | -------: | -------: | -----------: |
| C0 preparation only        |        (-0.001) | (-0.001) | (-0.001) |     (-0.000) |
| C1 phase only              |        (-0.001) | (-0.001) | (-0.001) |     (-0.000) |
| C2 degree encoder, X mixer |           0.283 |    0.770 |    0.807 |        0.573 |
| C3 QAOA preparation        |           0.009 |    0.114 |    0.105 |        0.061 |
| C4 two repetitions         |           0.196 |    0.722 |    0.757 |        0.626 |
| C5 Y mixer                 |           0.295 |    0.761 |    0.787 |        0.582 |
| C6 non-equivariant         |           0.037 | (-0.000) |    0.000 |        0.132 |

Because the complete 256-dimensional readout is used, the (n=8) comparisons are not confounded by unequal truncation mass.

#### Graph-blind controls at (n=8)

C0 and C1 remain at the constant-predictor floor for every target.

This agrees with the direct graph-blindness assertions and shows that the nested ridge pipeline does not manufacture predictive performance from constant readouts.

#### One-repetition X-mixer circuit at (n=8)

C2 provides strong short-cycle accessibility:

$$
R^2_{C_3}=0.770,\qquad R^2_{C_4}=0.807.
$$

Connectivity is moderately accessible:

$$
R^2_{\kappa}=0.573.
$$

Degree variance is weaker:

$$
R^2_{\text{degree variance}}=0.283.
$$

The representation therefore contains more linearly accessible information about short cycles than about the scalar degree-variance summary, despite degree being encoded directly.

This does not imply that the signal is independent of the degree sequence. On a heterogeneous census, the unnormalized preparation itself carries graph-dependent degree information that may correlate with cycles and connectivity.

#### QAOA preparation at (n=8)

Replacing the degree-dependent preparation with (|+\rangle^{\otimes n}) sharply reduces every target score:

$$
R^2_{C_3}=0.114,\qquad R^2_{C_4}=0.105,\qquad R^2_{\kappa}=0.061.
$$

The difference is particularly notable because the full output distribution is retained.

The result indicates that the degree-dependent preparation supplies a large portion of the useful (n=8) signal.

C2 versus C3 does not isolate only quantum-interference behavior. It also removes explicit degree information from the input state.

#### Depth at (n=8)

Adding a second tied entangler–mixer repetition changes the scores from:

| Target          | C2, one repetition | C4, two repetitions | Difference |
| --------------- | -----------------: | ------------------: | ---------: |
| Degree variance |              0.283 |               0.196 |   (-0.087) |
| (C_3)           |              0.770 |               0.722 |   (-0.048) |
| (C_4)           |              0.807 |               0.757 |   (-0.050) |
| Connectivity    |              0.573 |               0.626 |   (+0.053) |

Additional depth weakens the two short-cycle targets and degree variance but moderately improves connectivity.

There is no general depth advantage. The effect depends on the target.

#### Mixer axis at (n=8)

Replacing the X mixer with a Y mixer produces:

| Target          | C2, X mixer | C5, Y mixer | Difference |
| --------------- | ----------: | ----------: | ---------: |
| Degree variance |       0.283 |       0.295 |   (+0.012) |
| (C_3)           |       0.770 |       0.761 |   (-0.009) |
| (C_4)           |       0.807 |       0.787 |   (-0.020) |
| Connectivity    |       0.573 |       0.582 |   (+0.009) |

The results are nearly identical.

At (n=8), the useful information does not depend strongly on choosing an X rather than Y mixer at the fixed angle:

$$
\beta=0.1.
$$

#### Non-equivariant circuit at (n=8)

C6 performs poorly:

$$
R^2_{C_3}\approx0,\qquad R^2_{C_4}\approx0.
$$

Connectivity remains weakly accessible:

$$
R^2_{\kappa}=0.132.
$$

The index encoder therefore does not reproduce the cycle accessibility of the graph-aware preparation, even when evaluated only on the canonical census labeling.

#### Circuit-by-target results at (n=14)

| Circuit                    |    (C_3) |    (C_4) |    (C_5) |    (C_6) | Diamonds |    Girth |
| -------------------------- | -------: | -------: | -------: | -------: | -------: | -------: |
| C0 preparation only        | (-0.003) | (-0.008) | (-0.013) | (-0.006) | (-0.007) | (-0.008) |
| C1 phase only              | (-0.003) | (-0.008) | (-0.013) | (-0.006) | (-0.007) | (-0.008) |
| C2 degree encoder, X mixer |    1.000 |    0.999 |    0.985 |    0.901 |    0.998 |    0.991 |
| C3 QAOA preparation        |    0.544 |    0.273 |    0.348 |    0.094 |    0.717 |    0.315 |
| C4 two repetitions         |    1.000 |    0.999 |    0.967 |    0.872 |    0.997 |    0.990 |
| C5 Y mixer                 |    1.000 |    0.998 |    0.928 |    0.865 |    0.999 |    0.992 |
| C6 non-equivariant         |    0.123 |    0.143 |    0.064 |    0.044 | (-0.007) |    0.001 |

#### One-repetition X-mixer circuit at (n=14)

C2 makes every tested target strongly accessible.

The first three cycle counts reach:

$$
R^2_{C_3}=1.000,\qquad R^2_{C_4}=0.999,\qquad R^2_{C_5}=0.985.
$$

Six-cycle count reaches:

$$
R^2_{C_6}=0.901.
$$

Diamond count and girth are also near exact:

$$
R^2_D=0.998,\qquad R^2_{\text{girth}}=0.991.
$$

These scores are stronger than several canonical QuIC values reported elsewhere, particularly for (C_5) and (C_6). They should not be combined with those experiments because E18 uses the unnormalized uniform cubic rotation:

$$
R_X(8.625).
$$

The result shows that this alternative uniform preparation produces highly target-aligned cubic geometry.

#### QAOA preparation at (n=14)

The QAOA-style circuit is weaker for every target:

$$
R^2_{C_3}=0.544,\qquad R^2_{C_4}=0.273,\qquad R^2_{C_5}=0.348,\qquad R^2_{C_6}=0.094.
$$

Diamonds remain moderately accessible:

$$
R^2_D=0.717.
$$

Girth reaches:

$$
R^2_{\text{girth}}=0.315.
$$

The result indicates that the C2 preparation is important, especially for the deeper cycle targets.

However, only:

$$
10.51%
$$

of the median C3 probability mass lies in the first 1,000 coordinates. The QAOA comparison is therefore not a clean full-representation test at (n=14).

A full-vector or normalized-head-plus-mass rerun is needed before attributing the entire performance difference to the initial state.

#### Circuit depth at (n=14)

| Target   | C2, one repetition | C4, two repetitions | Difference |
| -------- | -----------------: | ------------------: | ---------: |
| (C_3)    |              1.000 |               1.000 |      0.000 |
| (C_4)    |              0.999 |               0.999 |      0.000 |
| (C_5)    |              0.985 |               0.967 |   (-0.018) |
| (C_6)    |              0.901 |               0.872 |   (-0.029) |
| Diamonds |              0.998 |               0.997 |   (-0.001) |
| Girth    |              0.991 |               0.990 |   (-0.001) |

Adding a second tied repetition provides no improvement.

Triangle and 4-cycle prediction are unchanged at displayed precision. The more difficult C5 and C6 targets become slightly weaker.

The result favors the shallower circuit within the tested tied-angle family:

$$
\boxed{\text{one repetition is sufficient for the tested cubic targets}}
$$

This is an ideal-probability representation result. It does not compare circuit cost under hardware noise, where the shallower circuit would also have a practical depth advantage.

#### Mixer axis at (n=14)

| Target   | C2, X mixer | C5, Y mixer | Difference |
| -------- | ----------: | ----------: | ---------: |
| (C_3)    |       1.000 |       1.000 |      0.000 |
| (C_4)    |       0.999 |       0.998 |   (-0.001) |
| (C_5)    |       0.985 |       0.928 |   (-0.057) |
| (C_6)    |       0.901 |       0.865 |   (-0.036) |
| Diamonds |       0.998 |       0.999 |   (+0.001) |
| Girth    |       0.991 |       0.992 |   (+0.001) |

The mixer axis has little effect on the shallowest targets.

Triangles, 4-cycles, diamonds, and girth remain near exact under both mixers.

The Y mixer is weaker for the deeper cycle counts:

$$
\Delta R^2_{C_5}=-0.057,\qquad\Delta R^2_{C_6}=-0.036.
$$

The structural geometry therefore does not require the X mixer in an absolute sense, but the X mixer exposes the finer cycle targets more effectively at the tested angle.

#### Non-equivariant circuit at (n=14)

C6 performs near the prediction floor:

$$
R^2_{C_3}=0.123,\qquad R^2_{C_4}=0.143,\qquad R^2_{C_5}=0.064,\qquad R^2_{C_6}=0.044.
$$

Diamond and girth prediction are approximately zero.

The weak results show that merely assigning heterogeneous rotations by qubit index does not reproduce the graph-aware circuit’s structural accessibility.

More importantly, C6 does not define a stable graph representation because its output depends on labeling.

#### Equivariance sensitivity

C2 and C6 are each tested on 100 graphs under one seeded random relabeling.

##### C2 degree encoder

| Census | Median cross-label (L_1) | Maximum cross-label (L_1) |
| ------ | -----------------------: | ------------------------: |
| (n=8)  |    (5.410\times10^{-16}) |     (1.030\times10^{-15}) |
| (n=14) |    (5.591\times10^{-16}) |     (7.649\times10^{-16}) |

##### C6 index encoder

| Census | Median cross-label (L_1) | Maximum cross-label (L_1) |
| ------ | -----------------------: | ------------------------: |
| (n=8)  |                   0.1118 |                    0.1720 |
| (n=14) |                  0.05234 |                   0.08335 |

The degree-encoded circuit remains invariant at the floating-point floor.

The non-equivariant circuit moves substantially:

$$
L_{1,\text{median}}=0.1118
$$

at (n=8), and:

$$
L_{1,\text{median}}=0.05234
$$

at (n=14).

Sorting does not repair a non-equivariant circuit. It removes coordinate permutations only when relabeling acts by consistently permuting the circuit and its output basis.

When the vertex labels alter the rotation assigned to each structural role, the probability multiset itself changes.

The experiment therefore measures the cost of abandoning permutation equivariance:

$$
\boxed{\text{sorting quotients coordinate labels, not label-dependent circuit parameters}}
$$

#### Cross-circuit interpretation

The screen identifies three broad levels of behavior.

##### Graph-blind circuits

C0 and C1 produce one readout across each census and remain at the prediction floor.

##### Equivariant graph-dependent circuits

C2 through C5 distinguish every graph.

Among these:

* C2 provides the strongest overall cubic results;
* C4 shows no benefit from a second tied repetition;
* C5 shows that the structural signal survives a change in mixer axis;
* C3 shows that the initial preparation strongly affects target accessibility.

##### Non-equivariant circuit

C6 also distinguishes every canonically labeled graph, but its output changes substantially under relabeling and supports little structural decoding.

This demonstrates that census-level distinctness is not enough. A useful graph representation must also respect graph isomorphism and organize the desired structural targets.

#### Relationship to E19

E19 maps the angle sensitivity of the same implemented circuit family.

Its nominal-center values reproduce the principal E18 scores, including:

$$
R^2_{C_3}=1.000,\qquad R^2_{C_5}=0.985,\qquad R^2_D=0.998
$$

for C2 at (n=14), and:

$$
R^2_{C_3}=0.770,\qquad R^2_{\kappa}=0.573
$$

at (n=8).

E18 supplies the circuit-family comparison at one fixed schedule. E19 shows how those contrasts change along the three angle axes.

Both experiments use the same unnormalized degree encoder and should be interpreted together as characterization of that alternative circuit family.

#### What the experiment establishes

The completed results establish that:

1. **Preparation-only and phase-only circuits are graph blind.**

   Both collapse each complete census to one readout and remain at the prediction floor.

2. **A noncommuting mixer is required to convert graph-dependent phases into probability information.**

3. **Several graph-dependent circuit constructions distinguish every graph in both tested censuses.**

4. **The one-repetition degree-encoded X-mixer circuit provides the strongest overall cubic decodability.**

   It reaches at least (0.985) on triangles, 4-cycles, 5-cycles, diamonds, and girth.

5. **A second tied repetition does not improve the tested cubic targets.**

   C5 and C6 accessibility decline slightly.

6. **The Y mixer preserves most of the structural signal.**

   Its largest losses occur for 5- and 6-cycle counts.

7. **The degree-dependent preparation is important.**

   QAOA-style preparation is substantially weaker at both graph orders.

8. **Permutation equivariance is operationally necessary.**

   The degree-encoded circuit remains invariant near (10^{-15}), while the index-encoded circuit changes by approximately (10^{-1}) under relabeling.

9. **Distinctness and useful graph representation are different properties.**

   C6 distinguishes all canonically labeled graphs but is label dependent and weakly aligned with the tested targets.

The experiment provides a coherent screen of preparation, depth, mixer axis, graph blindness, and equivariance within one circuit family.

#### Necessary qualifications

The primary qualification is the encoder mismatch.

C2 is labeled canonical in the notebook, but the implemented rotation is:

$$
R_X(\alpha d_i)
$$

rather than:

$$
R_X\left(\alpha\frac{d_i}{\Delta}\right).
$$

The numerical values should not be presented as results for the canonical QuIC circuit.

The mismatch is especially significant on the cubic census, where the implemented uniform angle is:

$$
8.625
$$

instead of:

$$
2.875.
$$

The circuit screen must be rerun with maximum-degree normalization before it can establish the same conclusions for canonical QuIC.

The (n=14) models use only the first 1,000 probability coordinates. Retained mass differs substantially across circuits, particularly for C3:

$$
m_{1000,\text{C3}}=0.1051.
$$

The raw-head comparison therefore confounds circuit information with probability concentration.

A cleaner cross-circuit screen would use one of the following:

* complete vectors;
* normalized top-1,000 heads with retained mass appended;
* or circuit-specific depths selected to retain comparable mass.

The ridge fits produce repeated ill-conditioned-matrix warnings. E10 showed that the useful QuIC directions often require near-zero regularization and can be sensitive to inner-fold selection.

No fold standard deviations are printed in the notebook’s final matrix, even though they are stored internally. Differences of a few hundredths should therefore remain descriptive.

No paired significance tests compare the circuits.

C6 is decoded using one canonical graph labeling. Its (R^2) values do not describe a graph invariant and could change under another labeling convention.

The fingerprint count uses vectors rounded to 12 decimal places. It establishes no observed collisions at that resolution, not exact symbolic injectivity.

The experiment evaluates only one angle schedule. E19 provides one-dimensional angle transects but not a full joint optimization.

The two graph orders use different graph families and target lists. Their circuit rankings should not be interpreted as pure graph-order effects.

All results use ideal statevector probabilities. They do not establish finite-shot or hardware-accessible performance.

Finally, the notebook title calls the study a six-circuit screen, but seven circuits are evaluated after adding C6. The title and accompanying documentation should be corrected.

#### Overall assessment

E18 is a useful circuit-family screen with two clear control results.

First, C0 and C1 establish that graph-dependent diagonal phases do not affect the sorted probability readout without a noncommuting layer. Second, the C6 relabeling test demonstrates that sorting does not rescue a circuit whose parameters depend on arbitrary vertex indices.

Within the implemented equivariant family, the one-repetition X-mixer circuit provides the strongest overall cubic results. Additional tied depth does not improve the tested targets, while a Y mixer preserves most of the shallow structure but weakens the finer cycle coordinates. QAOA-style preparation is substantially weaker.

The screen also exposes an important methodological distinction. Every graph-dependent circuit produces distinct readouts for every graph, but their predictive geometry differs dramatically. Injectivity, target accessibility, and permutation invariance are separate requirements.

The current notebook does not evaluate canonical QuIC because its degree encoder omits maximum-degree normalization. Its results instead characterize the same unnormalized circuit family mapped in E19.

The appropriate central claim is:

> Within an unnormalized degree-encoded circuit family, graph-dependent phases become structurally informative only after a noncommuting mixer, and the one-repetition X-mixer construction provides the strongest overall cubic decodability among the tested circuits. A second tied repetition offers no advantage, a Y mixer preserves most shallow structure but weakens longer-cycle accessibility, and QAOA-style preparation is substantially weaker. The degree-encoded circuits remain invariant to relabeling at the floating-point floor, whereas an index-encoded control changes by approximately (10^{-1}), demonstrating that sorting does not repair non-equivariant circuit parameters. Because the implemented encoder is (R_X(\alpha d_i)) rather than (R_X(\alpha d_i/\Delta)), the experiment characterizes an alternative circuit family and must be rerun before supporting canonical QuIC claims.



### E18 - Circuit Family Screen

#### Experimental design

E18 compares seven quantum graph circuits constructed from a common gate family.

The analysis uses two complete graph censuses:

* **11,117 connected graphs at (n=8)**;
* **509 connected cubic graphs at (n=14)**.

Each circuit produces a descending-sorted Born-probability vector. The decoder uses:

* the complete 256-dimensional vector at (n=8);
* the first 1,000 coordinates of the 16,384-dimensional vector at (n=14).

The tested circuits are:

1. **C0 — preparation-only control**

   A uniform graph-independent (R_X) preparation with no edge gate and no mixer.

2. **C1 — phase-only control**

   The same uniform preparation followed by graph-edge (R_{ZZ}) gates, with no mixer.

3. **C2 — canonical QuIC**

   A normalized degree-dependent (R_X) preparation followed by one graph-edge (R_{ZZ}) layer and one uniform (R_X) mixer.

4. **C3 — QAOA-style preparation**

   A (|+\rangle^{\otimes n}) preparation followed by one graph-edge (R_{ZZ}) layer and one uniform (R_X) mixer.

5. **C4 — two-repetition QuIC**

   The C2 entangler–mixer block is repeated twice with tied angles.

6. **C5 — Y-mixer QuIC**

   The C2 circuit is retained, but its final (R_X) mixer is replaced by an (R_Y) mixer.

7. **C6 — non-equivariant index encoder**

   The normalized degree encoder is replaced by an index-dependent rotation that deliberately changes under vertex relabeling.

The circuit angles are fixed throughout:

$$
\alpha=2.875,\qquad\gamma=2.0,\qquad\beta=0.1.
$$

No circuit-angle optimization is performed.

The target sets are:

##### (n=8)

* degree variance;
* triangle count;
* 4-cycle count;
* vertex connectivity.

##### (n=14)

* triangle count;
* 4-cycle count;
* 5-cycle count;
* 6-cycle count;
* diamond count;
* girth.

Diamond count is certified through the cubic identity:

$$
\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).
$$

All targets are decoded using five shuffled outer folds and the standing ridge grid:

$$
\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2}.
$$

The experiment is structured as a set of controlled contrasts:

* C0 and C1 test graph blindness;
* C2 versus C3 tests the initial preparation;
* C2 versus C4 tests tied-angle circuit depth;
* C2 versus C5 tests the mixer axis;
* C2 versus C6 tests permutation equivariance.

#### Correction relative to the original E18 run

The original E18 notebook implemented the degree encoder as:

$$
R_X(\alpha d_i).
$$

The canonical QuIC encoder is:

$$
R_X\left(\alpha\frac{d_i}{\Delta}\right),
$$

where (\Delta) is the maximum degree of the graph.

The corrected notebook applies maximum-degree normalization in C2, C4, and C5.

On the cubic census, the original circuit applied:

$$
R_X(8.625)
$$

to every qubit, while the corrected circuit applies:

$$
R_X(2.875).
$$

The following arms are unchanged by the correction:

* C0 and C1, which use the flat encoder;
* C3, which uses no degree encoder;
* C6, which uses the index encoder;
* all graph-blindness conclusions;
* all distinct-readout counts;
* the C6 relabeling-sensitivity results.

The numerical decoder rows for C2, C4, and C5 change substantially. The original E18 result should therefore be replaced rather than combined with the corrected run.

#### Target and census validation

The notebook enumerates:

$$
11{,}117
$$

connected unlabeled graphs at (n=8), and:

$$
509
$$

connected cubic graphs at (n=14).

For the cubic census, it verifies:

$$
\text{tr}(A^3)=6C_3,
$$

$$
\text{tr}(A^4)=8C_4+15n,
$$

and:

$$
\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).
$$

All identities hold exactly.

#### Canonical-encoder correctness gate

The corrected C2 row is compared with the independently recorded E2 full-vector results.

| Target   | Corrected E18 | E2 reference | Absolute difference |
| -------- | ------------: | -----------: | ------------------: |
| (C_3)    |         1.000 |        1.000 |               0.000 |
| (C_4)    |         0.998 |        0.998 |               0.000 |
| (C_5)    |         0.928 |        0.928 |               0.000 |
| (C_6)    |         0.484 |        0.485 |               0.001 |
| Diamonds |         0.993 |        0.993 |               0.000 |
| Girth    |         0.993 |        0.993 |               0.000 |

The worst discrepancy is:

$$
0.001.
$$

The corrected top-1,000 C2 representation therefore reproduces the independent canonical QuIC record.

This gate distinguishes the corrected encoder from the original unnormalized circuit, whose cubic scores included:

$$
R^2_{C_5}=0.985,\qquad R^2_{C_6}=0.901.
$$

Those inflated values do not belong to canonical QuIC.

#### Graph-blindness controls

The graph-blindness test compares each control circuit across 50 additional graphs at each graph order.

| Census | C0 preparation only |        C1 phase only |
| ------ | ------------------: | -------------------: |
| (n=8)  |               0.000 | (5.99\times10^{-16}) |
| (n=14) |               0.000 | (5.65\times10^{-17}) |

Both circuits satisfy:

$$
L_1<10^{-12}.
$$

The full-census fingerprint counts confirm the collapse:

| Census | C0 distinct readouts | C1 distinct readouts |
| ------ | -------------------: | -------------------: |
| (n=8)  |             1/11,117 |             1/11,117 |
| (n=14) |                1/509 |                1/509 |

C0 is graph blind because it contains no graph-dependent gate.

C1 contains graph-dependent diagonal phases, but those phases do not change computational-basis probabilities. The statevector phases depend on the graph, while the Born-probability vector does not.

Sorting is therefore not required to make C1 probability blind. The graph dependence has already disappeared when amplitudes are converted to probabilities.

The controls reproduce the E9 mechanism:

$$
\boxed{\text{graph-dependent phase requires a noncommuting layer to affect measurement probabilities}}
$$

#### Readout distinctness

The complete sorted vectors are rounded to 12 decimal places and hashed.

##### (n=8)

| Circuit             | Distinct readouts | Census size |
| ------------------- | ----------------: | ----------: |
| C0 preparation only |                 1 |      11,117 |
| C1 phase only       |                 1 |      11,117 |
| C2 canonical QuIC   |            11,117 |      11,117 |
| C3 QAOA preparation |            11,117 |      11,117 |
| C4 two repetitions  |            11,117 |      11,117 |
| C5 Y mixer          |            11,117 |      11,117 |
| C6 non-equivariant  |            11,117 |      11,117 |

##### (n=14)

| Circuit             | Distinct readouts | Census size |
| ------------------- | ----------------: | ----------: |
| C0 preparation only |                 1 |         509 |
| C1 phase only       |                 1 |         509 |
| C2 canonical QuIC   |               509 |         509 |
| C3 QAOA preparation |               509 |         509 |
| C4 two repetitions  |               509 |         509 |
| C5 Y mixer          |               509 |         509 |
| C6 non-equivariant  |               509 |         509 |

Every graph-dependent circuit produces a distinct rounded readout for every census graph.

For C2 through C5, this is evidence of census-level injectivity for several equivariant circuit constructions.

The C6 result has a different interpretation. It separates the canonically labeled census graphs but does not define an isomorphism-invariant graph representation.

The result also reinforces the distinction:

$$
\boxed{\text{readout distinctness}\neq\text{target-aligned geometry}}
$$

C2 through C6 have identical distinctness counts but very different decoder results.

#### Retained probability mass

At (n=8), the complete probability vector has only 256 entries. Every model therefore uses the full distribution:

$$
m_{1000}=1.
$$

At (n=14), the first 1,000 of 16,384 probabilities are retained.

| Circuit             | Median retained mass at (n=14) |
| ------------------- | -----------------------------: |
| C0 preparation only |                         1.0000 |
| C1 phase only       |                         1.0000 |
| C2 canonical QuIC   |                         1.0000 |
| C3 QAOA preparation |                         0.1051 |
| C4 two repetitions  |                         1.0000 |
| C5 Y mixer          |                         0.9999 |
| C6 non-equivariant  |                         0.9544 |

The corrected C2, C4, and C5 distributions are much more concentrated than their unnormalized counterparts.

The original reported medians were:

| Circuit | Original unnormalized | Corrected normalized |
| ------- | --------------------: | -------------------: |
| C2      |                0.9218 |               1.0000 |
| C4      |                0.9268 |               1.0000 |
| C5      |                0.8959 |               0.9999 |

The top-1,000 decoder therefore retains essentially the complete reported mass for the three normalized QuIC circuits.

C3 remains highly diffuse:

$$
m_{1000}=0.1051.
$$

The C2–C3 comparison at (n=14) is consequently confounded by unequal truncation. Only approximately 10.5% of the QAOA probability mass is presented to its decoder.

The C2–C4 and C2–C5 contrasts are substantially cleaner because all three retain essentially their complete mass at the reported precision.

#### Circuit-by-target results at (n=8)

| Circuit             | Degree variance |    (C_3) |    (C_4) | Connectivity |
| ------------------- | --------------: | -------: | -------: | -----------: |
| C0 preparation only |        (-0.001) | (-0.001) | (-0.001) |     (-0.000) |
| C1 phase only       |        (-0.001) | (-0.001) | (-0.001) |     (-0.000) |
| C2 canonical QuIC   |           0.055 |    0.007 |    0.018 |        0.123 |
| C3 QAOA preparation |           0.009 |    0.114 |    0.105 |        0.061 |
| C4 two repetitions  |           0.039 |    0.006 |    0.013 |        0.079 |
| C5 Y mixer          |           0.124 |    0.022 |    0.038 |        0.004 |
| C6 non-equivariant  |           0.037 | (-0.000) |    0.000 |        0.132 |

Because the complete distribution is used, the (n=8) circuit comparisons are not affected by unequal retained mass.

#### Canonical QuIC on the mixed-degree census

The corrected C2 circuit performs near the prediction floor for all four targets:

$$
R^2_{\text{degree variance}}=0.055,\qquad R^2_{C_3}=0.007,\qquad R^2_{C_4}=0.018,\qquad R^2_{\kappa}=0.123.
$$

The largest score is only:

$$
0.123.
$$

The correction therefore removes the strong mixed-degree results reported by the original unnormalized run.

| Target          | Original C2 | Corrected C2 |   Change |
| --------------- | ----------: | -----------: | -------: |
| Degree variance |       0.283 |        0.055 | (-0.228) |
| (C_3)           |       0.770 |        0.007 | (-0.763) |
| (C_4)           |       0.807 |        0.018 | (-0.789) |
| Connectivity    |       0.573 |        0.123 | (-0.450) |

The original strong cycle scores were properties of the unnormalized degree rotation, not canonical QuIC.

The corrected result agrees with E21, which independently found that canonical QuIC remains near the prediction floor on the complete mixed-degree (n=8) census.

#### QAOA preparation at (n=8)

C3 produces:

$$
R^2_{C_3}=0.114,\qquad R^2_{C_4}=0.105.
$$

These scores remain modest, but both exceed canonical QuIC.

The corresponding differences are:

$$
\Delta R^2_{C_3}=-0.107,\qquad\Delta R^2_{C_4}=-0.087
$$

when defined as C2 minus C3.

Canonical QuIC performs better on degree variance and connectivity:

$$
0.055>0.009,\qquad0.123>0.061.
$$

Thus, the normalized degree encoder exposes some degree-related and connectivity variation but does not create the strong cycle geometry observed on regular graphs.

#### Depth at (n=8)

Adding a second tied repetition changes the scores as follows:

| Target          | C2, one repetition | C4, two repetitions | Difference |
| --------------- | -----------------: | ------------------: | ---------: |
| Degree variance |              0.055 |               0.039 |   (-0.016) |
| (C_3)           |              0.007 |               0.006 |   (-0.001) |
| (C_4)           |              0.018 |               0.013 |   (-0.005) |
| Connectivity    |              0.123 |               0.079 |   (-0.044) |

The second repetition does not improve any tested target on the mixed-degree census.

#### Mixer axis at (n=8)

Replacing the X mixer with a Y mixer produces:

| Target          | C2, X mixer | C5, Y mixer | Difference |
| --------------- | ----------: | ----------: | ---------: |
| Degree variance |       0.055 |       0.124 |   (+0.069) |
| (C_3)           |       0.007 |       0.022 |   (+0.015) |
| (C_4)           |       0.018 |       0.038 |   (+0.020) |
| Connectivity    |       0.123 |       0.004 |   (-0.119) |

The Y mixer improves degree variance and the two cycle scores, but all three remain weak.

Connectivity nearly disappears.

The effect of the mixer axis is therefore strongly target dependent.

#### Circuit-by-target results at (n=14)

| Circuit             |    (C_3) |    (C_4) |    (C_5) |    (C_6) | Diamonds |    Girth |
| ------------------- | -------: | -------: | -------: | -------: | -------: | -------: |
| C0 preparation only | (-0.003) | (-0.008) | (-0.013) | (-0.006) | (-0.007) | (-0.008) |
| C1 phase only       | (-0.003) | (-0.008) | (-0.013) | (-0.006) | (-0.007) | (-0.008) |
| C2 canonical QuIC   |    1.000 |    0.998 |    0.928 |    0.484 |    0.993 |    0.993 |
| C3 QAOA preparation |    0.544 |    0.273 |    0.348 |    0.094 |    0.717 |    0.315 |
| C4 two repetitions  |    1.000 |    1.000 |    0.960 |    0.461 |    0.998 |    0.992 |
| C5 Y mixer          |    1.000 |    0.997 |    0.951 |    0.698 |    0.998 |    0.991 |
| C6 non-equivariant  |    0.123 |    0.143 |    0.064 |    0.044 | (-0.007) |    0.001 |

#### Canonical QuIC on the cubic census

C2 reproduces the established canonical hierarchy:

$$
R^2_{C_3}=1.000,\qquad R^2_{C_4}=0.998,\qquad R^2_{C_5}=0.928,\qquad R^2_{C_6}=0.484.
$$

Diamond count and girth are near exact:

$$
R^2_D=0.993,\qquad R^2_{\text{girth}}=0.993.
$$

This row is independently validated by the E2 record and should replace the original E18 C2 values.

#### QAOA preparation at (n=14)

C3 is weaker for every target:

| Target   | C2 canonical QuIC | C3 QAOA | Difference |
| -------- | ----------------: | ------: | ---------: |
| (C_3)    |             1.000 |   0.544 |   (+0.456) |
| (C_4)    |             0.998 |   0.273 |   (+0.725) |
| (C_5)    |             0.928 |   0.348 |   (+0.580) |
| (C_6)    |             0.484 |   0.094 |   (+0.390) |
| Diamonds |             0.993 |   0.717 |   (+0.276) |
| Girth    |             0.993 |   0.315 |   (+0.678) |

The normalized QuIC preparation produces substantially stronger cubic structural accessibility.

The comparison is not fully controlled because the first 1,000 QAOA probabilities contain only:

$$
10.51%
$$

of the median total mass.

A full-vector or normalized-head comparison is required before attributing the entire difference to circuit preparation.

#### Depth at (n=14)

| Target   | C2, one repetition | C4, two repetitions | Difference |
| -------- | -----------------: | ------------------: | ---------: |
| (C_3)    |              1.000 |               1.000 |      0.000 |
| (C_4)    |              0.998 |               1.000 |   (+0.002) |
| (C_5)    |              0.928 |               0.960 |   (+0.032) |
| (C_6)    |              0.484 |               0.461 |   (-0.023) |
| Diamonds |              0.993 |               0.998 |   (+0.005) |
| Girth    |              0.993 |               0.992 |   (-0.001) |

The corrected result differs from the original E18 depth conclusion.

A second tied repetition improves:

* 4-cycle count slightly;
* 5-cycle count by (0.032);
* diamond count slightly.

It weakens:

* 6-cycle count by (0.023);
* girth negligibly.

The additional repetition therefore provides selective rather than general improvement.

The clearest gain is for 5-cycles:

$$
0.928\rightarrow0.960.
$$

The one-repetition circuit remains simpler and nearly saturates most targets, but the corrected experiment does not support the claim that additional depth offers no benefit.

#### Mixer axis at (n=14)

| Target   | C2, X mixer | C5, Y mixer | Difference |
| -------- | ----------: | ----------: | ---------: |
| (C_3)    |       1.000 |       1.000 |      0.000 |
| (C_4)    |       0.998 |       0.997 |   (-0.001) |
| (C_5)    |       0.928 |       0.951 |   (+0.023) |
| (C_6)    |       0.484 |       0.698 |   (+0.214) |
| Diamonds |       0.993 |       0.998 |   (+0.005) |
| Girth    |       0.993 |       0.991 |   (-0.002) |

The Y mixer preserves the saturated triangle, 4-cycle, diamond, and girth results.

It also improves both deeper cycle targets:

$$
C_5:\ 0.928\rightarrow0.951,
$$

and:

$$
C_6:\ 0.484\rightarrow0.698.
$$

The C6 increase is substantial:

$$
\Delta R^2=+0.214.
$$

This reverses the conclusion from the invalid unnormalized run, where the Y mixer appeared weaker for C5 and C6.

The corrected experiment shows that the structural signal does not depend uniquely on the X mixer and that the Y mixer exposes longer-cycle information more effectively at the fixed angle.

#### Comparison of the equivariant cubic circuits

| Circuit                   | (C_3) | (C_4) | (C_5) | (C_6) | Diamonds | Girth |
| ------------------------- | ----: | ----: | ----: | ----: | -------: | ----: |
| C2 one-repetition X mixer | 1.000 | 0.998 | 0.928 | 0.484 |    0.993 | 0.993 |
| C4 two-repetition X mixer | 1.000 | 1.000 | 0.960 | 0.461 |    0.998 | 0.992 |
| C5 one-repetition Y mixer | 1.000 | 0.997 | 0.951 | 0.698 |    0.998 | 0.991 |

No circuit dominates every target.

* C2 has the strongest displayed girth result.
* C4 has the strongest 4-cycle and 5-cycle results.
* C5 has the strongest 6-cycle result.
* C4 and C5 tie on diamonds at displayed precision.
* All three are exact on triangles.

The corrected screen therefore supports a target-specific circuit-design conclusion rather than a universal preference for C2.

The canonical C2 circuit remains the simplest common reference and reproduces the paper’s established hierarchy. C4 and C5 demonstrate that deeper-cycle accessibility can be redistributed by changing depth or mixer axis.

#### Effect of the encoder correction on the cubic circuits

| Circuit and target | Original unnormalized | Corrected normalized |   Change |
| ------------------ | --------------------: | -------------------: | -------: |
| C2, (C_5)          |                 0.985 |                0.928 | (-0.057) |
| C2, (C_6)          |                 0.901 |                0.484 | (-0.417) |
| C4, (C_5)          |                 0.967 |                0.960 | (-0.007) |
| C4, (C_6)          |                 0.872 |                0.461 | (-0.411) |
| C5, (C_5)          |                 0.928 |                0.951 | (+0.023) |
| C5, (C_6)          |                 0.865 |                0.698 | (-0.167) |

The correction has its largest effect on 6-cycle prediction.

The unnormalized encoder made C2 and C4 appear dramatically stronger on C6 than their canonical versions.

It also changed the relative ranking of the mixer axes. Under the corrected encoder, the Y mixer is clearly strongest for C6.

This demonstrates that the encoder scale is not a superficial implementation detail. It changes both absolute target accessibility and the conclusions drawn from circuit comparisons.

#### Non-equivariant circuit

C6 performs weakly on both censuses.

At (n=14):

$$
R^2_{C_3}=0.123,\qquad R^2_{C_4}=0.143,\qquad R^2_{C_5}=0.064,\qquad R^2_{C_6}=0.044.
$$

Diamond and girth prediction are at the floor.

At (n=8), the strongest C6 score is:

$$
R^2_{\kappa}=0.132.
$$

The index encoder therefore does not reproduce the target geometry of the equivariant circuits, even when evaluated under one canonical labeling.

#### Equivariance sensitivity

C2 and C6 are each evaluated under random vertex relabelings of 100 graphs.

##### Canonical QuIC

| Census | Median cross-label (L_1) | Maximum cross-label (L_1) |
| ------ | -----------------------: | ------------------------: |
| (n=8)  |    (5.488\times10^{-16}) |     (1.393\times10^{-15}) |
| (n=14) |    (3.226\times10^{-16}) |     (9.636\times10^{-16}) |

##### Non-equivariant encoder

| Census | Median cross-label (L_1) | Maximum cross-label (L_1) |
| ------ | -----------------------: | ------------------------: |
| (n=8)  |                   0.1118 |                    0.1720 |
| (n=14) |                  0.05234 |                   0.08335 |

Canonical QuIC remains invariant at the floating-point floor.

The index-encoded circuit changes substantially under relabeling.

Sorting therefore removes coordinate labels only when the circuit itself transforms equivariantly:

$$
\boxed{\text{sorting quotients output coordinates but does not repair label-dependent circuit parameters}}
$$

#### Relationship to E21

The corrected E18 results align with E21.

Both experiments find that canonical QuIC:

* nearly solves triangle and 4-cycle counts on cubic graphs;
* strongly decodes 5-cycles, diamonds, and girth;
* has weaker cubic 6-cycle accessibility;
* collapses on the complete mixed-degree (n=8) census.

E21 additionally shows that strong structural accessibility returns on a complete 4-regular census.

Together, the experiments support the interpretation that the organized QuIC geometry is associated with regular graph families rather than with the presence of an explicit degree encoder alone.

#### Consequence for E19

E19 maps the original unnormalized E18 circuit family.

Its nominal C2 center contains:

$$
R^2_{C_5}=0.985,\qquad R^2_{C_6}=0.901,
$$

which matches the invalid original E18 row rather than the corrected canonical row:

$$
R^2_{C_5}=0.928,\qquad R^2_{C_6}=0.484.
$$

E19 therefore remains an angle map of the unnormalized circuit and cannot be cited as a robustness analysis of canonical QuIC.

A normalized E19 rerun is required before making canonical angle-robustness claims.

#### What the experiment establishes

The corrected results establish that:

1. **The notebook now evaluates the canonical normalized QuIC encoder.**

   The C2 cubic row reproduces the independent E2 record to a worst discrepancy of (0.001).

2. **Preparation-only and phase-only circuits are graph blind.**

   Both collapse each census to one readout and remain at the prediction floor.

3. **A noncommuting mixer is required to convert graph-dependent phases into probability differences.**

4. **Every graph-dependent circuit produces distinct rounded readouts across both complete censuses.**

5. **Canonical QuIC is strongly target aligned on cubic graphs but weak on the complete mixed-degree census.**

6. **The original strong mixed-degree results were artifacts of the unnormalized encoder.**

7. **A second tied repetition selectively improves cubic 5-cycle prediction.**

   It raises (R^2) from (0.928) to (0.960).

8. **A Y mixer substantially improves cubic 6-cycle prediction.**

   It raises (R^2) from (0.484) to (0.698).

9. **No tested equivariant circuit dominates every target.**

10. **Permutation equivariance is operationally necessary.**

    Canonical QuIC remains invariant near (10^{-15}), while the index encoder changes by approximately (10^{-1}).

11. **Distinctness, target accessibility, and isomorphism invariance remain separate representation properties.**

E18 therefore provides a controlled screen of graph blindness, preparation, depth, mixer axis, and equivariance for the canonical circuit family.

#### Necessary qualifications

The (n=14) analysis uses the first 1,000 probabilities rather than the complete vectors.

This is unlikely to materially affect C2, C4, or C5 because their reported median retained masses are approximately one. It materially affects C3, whose median retained mass is only:

$$
0.1051.
$$

The QAOA comparison should therefore not be interpreted as a pure preparation ablation at (n=14).

The retained masses are printed to four decimal places. Values reported as:

$$
1.0000
$$

should not be interpreted as mathematically exact unit mass.

The fingerprint count uses 12-decimal rounded vectors. It establishes no observed collision at that resolution, not exact symbolic injectivity.

C6 is evaluated on the canonical census labeling. Its decoder scores are not graph-invariant quantities and may change under another labeling convention.

The ridge fits emit repeated ill-conditioned-matrix warnings.

E10 showed that QuIC probe results can depend on extremely small regularization values and low-singular-value feature directions.

The notebook stores fold standard deviations internally but does not print them in the final result matrix.

No paired statistical tests compare C2, C4, and C5. Differences of a few thousandths should be treated as descriptive ties.

The larger C5 and C6 differences are more substantively meaningful, but they remain results from one fixed angle schedule.

The screen evaluates tied-angle depth only. It does not test whether independently chosen angles at the second repetition improve the circuit further.

Only X and Y single-qubit mixers are compared. No second entangler family is evaluated.

The two graph orders use different graph families and target sets. Their differences cannot be attributed to graph order alone.

All results use exact statevector probabilities. They do not establish finite-shot or hardware-accessible circuit rankings.

Finally, the notebook title still calls the experiment a six-circuit screen even though seven circuits are evaluated. The title and saved artifact documentation should be corrected.

#### Overall assessment

The corrected E18 run changes the scientific interpretation of the circuit screen.

Canonical QuIC reproduces the established cubic hierarchy and collapses on the complete mixed-degree census. The strong mixed-degree cycle results in the original notebook were caused by omitting maximum-degree normalization.

The corrected depth and mixer comparisons are also different.

A second tied repetition improves 5-cycle prediction from:

$$
0.928
$$

to:

$$
0.960,
$$

while the Y mixer improves 6-cycle prediction from:

$$
0.484
$$

to:

$$
0.698.
$$

Neither modification dominates the canonical circuit universally. Instead, depth and mixer axis redistribute which deeper structural coordinates are most linearly accessible.

The graph-blindness and equivariance controls remain clean. Preparation-only and phase-only circuits collapse to one readout, canonical QuIC is invariant under relabeling at the floating-point floor, and the index-encoded control moves by approximately (10^{-1}).

The appropriate central claim is:

> Within the canonical maximum-degree-normalized circuit family, graph-dependent phases become observable only after a noncommuting mixer, and every tested graph-dependent circuit produces distinct readouts across the complete (n=8) and cubic (n=14) censuses. Canonical one-repetition QuIC reproduces the established cubic hierarchy but remains near the prediction floor on the complete mixed-degree census. Circuit modifications redistribute the deeper structural signal: a second tied repetition improves 5-cycle accessibility, while a Y mixer substantially improves 6-cycle accessibility. The equivariant circuits remain invariant under relabeling at the floating-point floor, whereas an index-encoded control changes by approximately (10^{-1}), confirming that sorting does not repair non-equivariant circuit parameters.


### E19 - Angle Map

#### Experimental design

E19 maps how structural decodability changes as the three circuit angles vary.

The experiment uses two complete graph censuses:

* **11,117 connected graphs at (n=8)**;
* **509 connected cubic graphs at (n=14)**.

For each graph-dependent circuit, the experiment evaluates three one-dimensional transects through the nominal center:

$$
(\alpha,\gamma,\beta)=(2.875,2.0,0.1),
$$

where:

* (\alpha) controls the encoder scale;
* (\gamma) controls the edge-entangler angle;
* (\beta) controls the mixer angle.

Only one angle changes along each transect. The other two remain fixed at their nominal values.

The tested ranges are:

$$
\alpha\in[0,\pi],\qquad\gamma\in[0,\pi],\qquad\beta\in[0,\pi/2].
$$

Each grid contains the nominal value in addition to an evenly spaced eight-point grid.

The experiment therefore produces a cross-shaped local map rather than a complete three-dimensional angle cube. It measures sensitivity to each angle independently but does not evaluate interactions between simultaneous angle changes.

The probability representation is truncated to its first:

$$
k=1000
$$

sorted entries. At (n=8), this includes the complete 256-dimensional distribution. At (n=14), it retains the first 1,000 of 16,384 probabilities.

The target sets are intentionally narrow.

##### (n=8)

* triangle count;
* vertex connectivity.

##### (n=14)

* triangle count;
* 5-cycle count;
* diamond count.

The diamond target is verified through the cubic identity:

$$
\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).
$$

All readouts are evaluated using the standing five-fold ridge protocol:

$$
\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2}.
$$

The experiment reports decodability across the angle transects. It does not train or optimize the circuit angles.

#### Circuit family

Seven circuit configurations are included.

##### C0 - Preparation only

The circuit applies a uniform flat (R_X) preparation without graph-dependent edge gates or a mixer.

This is a graph-blind control.

##### C1 - Phase only

The circuit starts from the flat preparation and applies graph-dependent diagonal (R_{ZZ}) gates without a mixer.

Because the input is a computational-basis product state in this implementation, the edge gates change only phases and leave the sorted probability distribution graph independent.

##### C2 - Nominal QuIC family

The circuit uses:

* degree-scaled (R_X) preparation;
* graph-edge (R_{ZZ}) gates;
* a uniform (R_X) mixer;
* one repetition.

##### C3 - QAOA-style preparation

The circuit begins in:

$$
|+\rangle^{\otimes n},
$$

then applies the edge entangler and an (R_X) mixer.

It has no encoder-angle parameter.

##### C4 - Two-repetition QuIC

The C2 edge and mixer blocks are repeated twice, with the same tied values of (\gamma) and (\beta) in both repetitions.

##### C5 - Y-mixer circuit

The circuit retains the degree encoder and edge entangler but replaces the final (R_X) mixer with an (R_Y) mixer.

##### C6 - Non-equivariant encoder

The circuit encodes qubit index rather than a graph-invariant vertex attribute:

$$
\theta_i=\alpha\frac{i+1}{n}.
$$

This circuit depends on the chosen vertex ordering and is not permutation equivariant.

#### Encoder implemented by the notebook

The notebook describes C2, C4, and C5 as degree-encoded circuits. The implementation applies:

$$
R_X(\alpha d_i)
$$

to vertex (i).

It does not apply the canonical normalized degree encoder:

$$
R_X\left(\alpha\frac{d_i}{\Delta}\right).
$$

This distinction is immaterial to whether the notebook consistently maps its own E18 circuit family, but it is material to comparison with the canonical QuIC representation used in E1, E2, E6, E7, E9, E13, and E16 / E17.

On the cubic (n=14) census, the implemented center applies:

$$
R_X(2.875\times3)=R_X(8.625)
$$

to every qubit rather than:

$$
R_X(2.875).
$$

On the heterogeneous (n=8) census, both the absolute scale and the degree dependence differ from canonical QuIC.

The E19 angle map must therefore be interpreted as a map of the **unnormalized E18 circuit family**, not as a parameter-robustness audit of the canonical QuIC object.

#### Canonical-center scores

The nominal C2 center produces:

| Census | Target       | Nominal-center (R^2) |
| ------ | ------------ | -------------------: |
| (n=8)  | Triangles    |                0.770 |
| (n=8)  | Connectivity |                0.573 |
| (n=14) | Triangles    |                1.000 |
| (n=14) | 5-cycles     |                0.985 |
| (n=14) | Diamonds     |                0.998 |

The notebook was intended to compare these scores against a stored E18 artifact with a tolerance of:

$$
10^{-9}.
$$

That artifact was not mounted during the run. The automated identity assertion was therefore skipped.

The scores were printed for manual comparison and match the values recorded in the notebook’s E18 discussion, but the E18 identity gate did not execute successfully in this run.

The nominal (n=14) 5-cycle value also differs from the canonical QuIC truncation result reported in E13:

$$
0.985\quad\text{in E19 versus}\quad0.928\quad\text{for canonical QuIC at }k=1000.
$$

This difference is consistent with the encoder mismatch.

#### Graph-blind controls

Both graph-blind controls remain at the constant-predictor floor.

| Census | Circuit             | Configurations checked |    Best observed (R^2) |
| ------ | ------------------- | ---------------------: | ---------------------: |
| (n=8)  | C0 preparation only |                      1 |    approximately 0.000 |
| (n=8)  | C1 phase only       |                      9 |    approximately 0.000 |
| (n=14) | C0 preparation only |                      1 | approximately (-0.003) |
| (n=14) | C1 phase only       |                      9 | approximately (-0.003) |

C1 remains graph blind across all nine tested entangler angles.

This validates the basic phase-to-probability mechanism: diagonal edge phases alone do not create graph-dependent measurement probabilities in this preparation.

A mixer or another noncommuting operation is required to convert the phase differences into observable probability differences.

#### (n=14) canonical-family angle map

The (n=14) cubic census provides the cleaner angle analysis because every graph has the same degree sequence and every qubit receives the same implemented encoder rotation.

##### Per-axis maxima

| Axis               |  Triangle peak |   5-cycle peak |   Diamond peak |
| ------------------ | -------------: | -------------: | -------------: |
| Encoder (\alpha)   | 1.000 at 0.898 | 0.987 at 1.795 | 0.999 at 0.898 |
| Entangler (\gamma) | 1.000 at 1.346 | 0.985 at 2.000 | 0.998 at 1.795 |
| Mixer (\beta)      | 1.000 at 0.224 | 0.985 at 0.224 | 0.998 at 0.100 |

The nominal center obtains:

$$
R^2_{C_3}=1.000,\qquad R^2_{C_5}=0.985,\qquad R^2_D=0.998.
$$

The best values found along the individual transects are:

$$
1.000,\qquad0.987,\qquad0.999.
$$

The differences between the nominal center and the per-axis maxima are therefore no more than:

$$
0.002.
$$

Within the resolution of the tested grid, the nominal schedule is not a narrowly tuned optimum. It lies on a broad region of near-maximal decodability for all three targets.

Triangle count is particularly insensitive. It reaches:

$$
R^2=1.000
$$

at multiple interior values on all three axes.

Diamond count is similarly stable, with peak values between:

$$
0.998\quad\text{and}\quad0.999.
$$

Five-cycle count is the most angle-sensitive of the three targets, but its nominal score remains within (0.002) of every transect maximum.

#### Endpoint behavior on the cubic census

For C2 at (n=14), the graph-dependent readout collapses at the expected graph-blind endpoints.

##### Zero encoder

At:

$$
\alpha=0,
$$

the initial state is:

$$
|0\rangle^{\otimes n}.
$$

The edge gates contribute only phases to this computational-basis state, and the uniform mixer produces the same sorted distribution for every cubic graph.

##### Encoder endpoint at (\pi)

Under the implemented unnormalized encoder:

$$
R_X(\pi d_i)=R_X(3\pi)
$$

on every cubic vertex.

This prepares the same computational-basis state up to phase on every graph. The subsequent sorted readout is graph independent.

This endpoint collapse depends on the unnormalized integer-degree formula. It would not follow generally from the normalized encoder:

$$
R_X\left(\pi\frac{d_i}{\Delta}\right)
$$

on heterogeneous graphs.

##### Zero entangler

At:

$$
\gamma=0,
$$

the circuit contains no graph-dependent edge operation. The encoder and mixer are identical across all cubic graphs, so the readout collapses.

##### Zero mixer

At:

$$
\beta=0,
$$

the edge gates modify only phases. The probabilities remain graph independent, reproducing the mechanism established in E9.

These endpoint controls support the conclusion that the interior cubic signal requires all three components:

* a nontrivial preparation;
* graph-dependent phase accumulation;
* noncommuting phase-to-probability conversion.

#### Mixer-angle behavior

The nominal mixer angle is:

$$
\beta=0.1.
$$

The per-axis summary shows that the maximum triangle and C5 scores occur at the nearby tested value:

$$
\beta=0.224,
$$

while diamonds peak at the nominal value.

The notebook’s recorded curve interpretation reports that the three targets remain strong through the small- and intermediate-mixer region, while C5 declines first at larger mixer angles.

At:

$$
\beta=\pi/2,
$$

the reported C5 score falls to approximately:

$$
R^2=0.448.
$$

Triangle and diamond accessibility persist longer.

This supports a target-dependent robustness ordering:

$$
\text{triangles and diamonds are more mixer robust than 5-cycles}.
$$

The result is consistent with the earlier characterization of C5 as a finer probability-shape statistic whose accessibility depends on more detailed rank structure.

The complete numeric pointwise curves are stored in the external E19 pickle rather than printed in the notebook output. The attached notebook therefore supports the reported extrema and recorded endpoint value, but it does not provide a complete independent table of every intermediate score.

#### Alternative circuits at (n=14)

##### QAOA-style preparation

| Axis               |  Triangle peak |   5-cycle peak |   Diamond peak |
| ------------------ | -------------: | -------------: | -------------: |
| Encoder (\alpha)   | 0.544 at 0.000 | 0.348 at 0.000 | 0.717 at 0.000 |
| Entangler (\gamma) | 0.986 at 2.693 | 0.512 at 2.693 | 0.940 at 1.346 |
| Mixer (\beta)      | 0.717 at 0.449 | 0.607 at 0.898 | 0.717 at 0.100 |

The QAOA circuit has no encoder. Its reported (\alpha) transect is therefore constant by construction.

The printed “peak at 0.000” is only the first member of a set of tied values and should not be interpreted as an encoder optimum.

The QAOA-style circuit can make triangle count nearly exact:

$$
R^2=0.986
$$

at:

$$
\gamma=2.693.
$$

It also carries substantial diamond information:

$$
R^2=0.940.
$$

Its best 5-cycle score is much lower:

$$
R^2=0.607.
$$

Thus, the QAOA preparation captures coarse motif and spectral-adjacent structure but does not reproduce the strong C5 accessibility of C2.

##### Two-repetition circuit

| Axis               |  Triangle peak |   5-cycle peak |   Diamond peak |
| ------------------ | -------------: | -------------: | -------------: |
| Encoder (\alpha)   | 1.000 at 0.898 | 0.967 at 2.875 | 1.000 at 3.142 |
| Entangler (\gamma) | 1.000 at 0.898 | 0.975 at 1.795 | 0.998 at 0.898 |
| Mixer (\beta)      | 1.000 at 0.100 | 0.967 at 0.100 | 0.997 at 0.100 |

The two-repetition circuit remains highly informative, but it does not improve upon the one-repetition C2 circuit for 5-cycles.

Its maximum C5 score is:

$$
R^2=0.975,
$$

compared with:

$$
R^2=0.987
$$

for the C2 transects.

Triangle and diamond prediction remain near exact.

The additional repetition therefore preserves the shallow structure but does not provide a clear advantage for the harder C5 target.

##### Y-mixer circuit

| Axis               |  Triangle peak |   5-cycle peak |   Diamond peak |
| ------------------ | -------------: | -------------: | -------------: |
| Encoder (\alpha)   | 1.000 at 0.898 | 0.952 at 1.346 | 0.999 at 2.693 |
| Entangler (\gamma) | 1.000 at 0.449 | 0.945 at 1.346 | 0.999 at 2.000 |
| Mixer (\beta)      | 1.000 at 0.100 | 0.950 at 0.224 | 0.999 at 0.100 |

Replacing the X mixer with a Y mixer preserves strong structural accessibility.

Triangles remain exact, diamonds remain near exact, and C5 peaks between:

$$
0.945\quad\text{and}\quad0.952.
$$

The Y mixer is therefore viable but consistently weaker than the C2 X-mixer circuit on C5.

The result indicates that the structural signal does not depend uniquely on one mixer axis, although the chosen noncommuting rotation affects the strength of the finer cycle coordinate.

##### Non-equivariant encoder

| Axis               |  Triangle peak |   5-cycle peak |   Diamond peak |
| ------------------ | -------------: | -------------: | -------------: |
| Encoder (\alpha)   | 0.916 at 0.449 | 0.127 at 2.244 | 0.214 at 1.795 |
| Entangler (\gamma) | 0.537 at 0.449 | 0.158 at 0.449 | 0.142 at 2.693 |
| Mixer (\beta)      | 0.242 at 1.346 | 0.075 at 1.346 | 0.077 at 1.571 |

The index-based encoder retains some triangle accessibility but performs poorly on C5 and diamonds.

Its best values are:

$$
R^2_{C_5}=0.158,\qquad R^2_D=0.214.
$$

The result supports the importance of an equivariant graph-dependent preparation for the deeper structural targets.

However, C6 is not a valid invariant graph representation. Its output can change under vertex relabeling because qubit angles are assigned by index.

Its results should therefore be treated as a symmetry-breaking control rather than as a competitive representation baseline.

#### Circuit comparison at (n=14)

The best value observed for each circuit across all three transects is:

| Circuit                   | Best triangle (R^2) | Best C5 (R^2) | Best diamond (R^2) |
| ------------------------- | ------------------: | ------------: | -----------------: |
| C2 one-repetition X mixer |               1.000 |         0.987 |              0.999 |
| C3 QAOA preparation       |               0.986 |         0.607 |              0.940 |
| C4 two repetitions        |               1.000 |         0.975 |              1.000 |
| C5 Y mixer                |               1.000 |         0.952 |              0.999 |
| C6 non-equivariant        |               0.916 |         0.158 |              0.214 |

Several circuit constructions can make triangles and diamonds almost perfectly accessible.

Five-cycle count is more discriminating.

The ranking for the strongest observed C5 score is:

$$
\text{C2}=0.987>\text{C4}=0.975>\text{C5}=0.952>\text{C3}=0.607>\text{C6}=0.158.
$$

The one-repetition X-mixer circuit remains the strongest tested construction for the finer C5 coordinate.

The differences between C2, C4, and C5 are modest compared with their separation from the QAOA and non-equivariant circuits. The broad conclusion is therefore that:

* degree-dependent preparation plus a noncommuting mixer produces the strongest C5 accessibility;
* an additional repetition is unnecessary;
* replacing the mixer axis weakens but does not destroy the signal;
* removing equivariant preparation substantially degrades it.

#### (n=8) angle-map results

The (n=8) census is degree heterogeneous. Under the implemented unnormalized encoder, the initial product-state probabilities already encode the degree multiset.

The angle map must therefore distinguish:

* topology transmitted through the edge gates;
* graph information already present in the degree-dependent preparation.

##### C2 nominal circuit

| Axis               |  Triangle peak | Connectivity peak |
| ------------------ | -------------: | ----------------: |
| Encoder (\alpha)   | 0.770 at 2.875 |    0.573 at 2.875 |
| Entangler (\gamma) | 0.885 at 0.000 |    0.810 at 3.142 |
| Mixer (\beta)      | 0.846 at 0.000 |    0.840 at 0.000 |

The nominal center obtains:

$$
R^2_{C_3}=0.770,\qquad R^2_{\kappa}=0.573.
$$

Both targets can be decoded more strongly at an endpoint where one graph-processing component is absent.

At:

$$
\beta=0,
$$

the mixer is absent, but the degree-dependent preparation still varies among graphs. The resulting scores are:

$$
R^2_{C_3}=0.846,\qquad R^2_{\kappa}=0.840.
$$

At:

$$
\gamma=0,
$$

the edge entangler is absent, yet triangle count reaches:

$$
R^2=0.885.
$$

These results show that much of the (n=8) performance comes directly from the degree encoder rather than from topology converted through entangler–mixer interference.

The zero-mixer collapse established in E9 applies to cubic graphs with uniform preparation. It does not apply to a heterogeneous census whose vertex rotations already encode degree.

##### QAOA-style preparation

| Axis               |  Triangle peak | Connectivity peak |
| ------------------ | -------------: | ----------------: |
| Encoder (\alpha)   | 0.114 at 0.000 |    0.061 at 0.000 |
| Entangler (\gamma) | 0.981 at 0.449 |    0.778 at 0.449 |
| Mixer (\beta)      | 0.450 at 1.571 |    0.290 at 1.571 |

The (\alpha) transect is constant because the circuit has no encoder.

The QAOA circuit attains the highest triangle score observed in the complete (n=8) map:

$$
R^2=0.981
$$

at:

$$
\gamma=0.449.
$$

It also reaches:

$$
R^2=0.778
$$

for connectivity at the same entangler angle.

The result shows that the heterogeneous census can support strong target accessibility without degree encoding, but only at selected entangler values.

Because the peak is selected after evaluating the grid and no fold uncertainty is reported, it should be treated as a descriptive angle-map maximum rather than a validated tuned model.

##### Two-repetition circuit

| Axis               |  Triangle peak | Connectivity peak |
| ------------------ | -------------: | ----------------: |
| Encoder (\alpha)   | 0.722 at 2.875 |    0.626 at 2.875 |
| Entangler (\gamma) | 0.909 at 0.000 |    0.818 at 3.142 |
| Mixer (\beta)      | 0.846 at 0.000 |    0.840 at 0.000 |

The two-repetition circuit closely reproduces the endpoint behavior of C2.

Its strongest connectivity score is:

$$
R^2=0.840
$$

at zero mixer, identical to the C2 peak at displayed precision.

The second repetition therefore does not produce a clear general advantage on the heterogeneous census.

##### Y-mixer circuit

| Axis               |  Triangle peak | Connectivity peak |
| ------------------ | -------------: | ----------------: |
| Encoder (\alpha)   | 0.761 at 2.875 |    0.582 at 2.875 |
| Entangler (\gamma) | 0.846 at 0.000 |    0.839 at 3.142 |
| Mixer (\beta)      | 0.846 at 0.000 |    0.840 at 0.000 |

The Y-mixer results are also dominated by the degree-encoder endpoints.

The maxima at:

$$
\beta=0
$$

are identical to C2 and C4 because the mixer type is irrelevant when its angle is zero.

##### Non-equivariant encoder

| Axis               |  Triangle peak | Connectivity peak |
| ------------------ | -------------: | ----------------: |
| Encoder (\alpha)   | 0.254 at 0.898 |    0.323 at 0.898 |
| Entangler (\gamma) | 0.781 at 0.449 |    0.564 at 0.449 |
| Mixer (\beta)      | 0.140 at 0.449 |    0.132 at 0.100 |

The index encoder is weaker than the graph-aware circuits on both targets.

As at (n=14), it is not permutation invariant and should be interpreted only as a symmetry-breaking control.

#### Circuit comparison at (n=8)

The best value observed for each circuit is:

| Circuit                   | Best triangle (R^2) | Best connectivity (R^2) |
| ------------------------- | ------------------: | ----------------------: |
| C2 one-repetition X mixer |               0.885 |                   0.840 |
| C3 QAOA preparation       |               0.981 |                   0.778 |
| C4 two repetitions        |               0.909 |                   0.840 |
| C5 Y mixer                |               0.846 |                   0.840 |
| C6 non-equivariant        |               0.781 |                   0.564 |

No single circuit dominates both targets.

The QAOA-style preparation provides the strongest triangle result, while the degree-encoded circuits provide the strongest connectivity result.

However, the connectivity maxima for C2, C4, and C5 occur at:

$$
\beta=0
$$

or at another boundary where the readout is strongly determined by degree encoding.

The (n=8) map therefore characterizes a mixture of degree-sequence accessibility and topology accessibility rather than a pure graph-circuit hierarchy.

#### Angle sensitivity and target dependence

The angle maxima differ across:

* graph orders;
* targets;
* circuit constructions;
* and circuit axes.

There is no universal best angle schedule.

The cleanest robustness result belongs to the implemented C2 circuit on cubic graphs. Its nominal center lies within (0.002) of the best observed score for every target and every axis.

By contrast, the heterogeneous (n=8) targets often peak at boundary values:

$$
\gamma=0,\qquad\gamma=\pi,\qquad\beta=0.
$$

Those maxima frequently reflect information already present in the unnormalized degree preparation.

Five-cycle count is the most useful target for distinguishing circuit constructions at (n=14). Triangles and diamonds are nearly saturated by several alternatives, while C5 degrades substantially when the preparation or equivariance structure changes.

#### What the experiment establishes

The completed angle map establishes that:

1. **The nominal E18 C2 schedule is not narrowly tuned on the cubic census.**

   Its triangle, C5, and diamond scores are within (0.002) of the best values found along all three one-dimensional transects.

2. **The cubic structural signal disappears at graph-blind endpoints.**

   Removing the encoder, entangler, or mixer collapses the one-repetition cubic readout under the implemented circuit family.

3. **Triangle and diamond accessibility is robust across several circuit constructions.**

   C2, C4, and C5 all reach approximately exact prediction.

4. **Five-cycle count is more circuit selective.**

   C2 reaches (0.987), compared with (0.975) for two repetitions, (0.952) for a Y mixer, (0.607) for QAOA preparation, and (0.158) for the non-equivariant circuit.

5. **Additional depth does not improve the best cubic C5 result.**

   The one-repetition C2 circuit remains strongest.

6. **The Y mixer retains most, but not all, of the structural accessibility of the X mixer.**

7. **The non-equivariant encoder performs poorly on deeper structural targets.**

8. **The heterogeneous-census results contain a large degree-encoding component.**

   Several (n=8) targets peak when the edge entangler or mixer is absent.

The angle map therefore supports robustness of the implemented cubic circuit while showing that target accessibility is jointly determined by preparation, equivariance, mixer choice, and graph family.

#### Necessary qualifications

The implemented “degree” encoder is:

$$
R_X(\alpha d_i),
$$

not the canonical QuIC encoder:

$$
R_X\left(\alpha\frac{d_i}{\Delta}\right).
$$

This is the principal qualification.

E19 should not be used to claim that the canonical QuIC angles are robust until the experiment is repeated with maximum-degree normalization.

The mismatch also explains why the nominal C5 score does not reproduce E13’s canonical (k=1000) value.

The E18 artifact was not mounted, so the nominal-center identity gate was skipped. The printed values match the notebook’s recorded E18 column manually, but no machine assertion completed.

The notebook saves the complete angle curves to an external pickle:

$$
\texttt{/kaggle/working/e19_angle_map.pkl}.
$$

That artifact is not included with the attached notebook. The visible output contains only the canonical values and per-axis extrema.

Consequently, detailed claims about:

* plateau widths;
* monotonicity;
* local slopes;
* and every intermediate angle

cannot be independently reconstructed from the attachment alone.

The QAOA circuit has no encoder. Its (\alpha) transect is constant, and the reported peak at zero is arbitrary.

The (n=8) zero-entangler and zero-mixer configurations are not graph blind because the degree-dependent preparation remains graph dependent. They should not be described as endpoint collapses.

The angle maps use one-dimensional transects. A circuit may respond differently when two or three angles change simultaneously.

The best values are selected from approximately nine tested settings per axis without a held-out angle-selection stage. They are descriptive maxima, not unbiased estimates of optimized performance.

No fold standard deviations or paired significance tests are printed for the angle curves. Differences of a few thousandths should not be interpreted as meaningful rankings.

The ridge fits repeatedly emit ill-conditioned-matrix warnings. E10 showed that QuIC probe results rely on extremely small regularization values and can be sensitive to inner-fold selection, particularly for weaker targets.

The non-equivariant circuit depends on the nauty-provided vertex ordering. Its results do not define an isomorphism-invariant graph representation.

The two graph orders also use different graph families and different targets. Differences between their angle maps cannot be attributed to graph order alone.

Finally, all results use exact statevector probabilities. The map characterizes ideal representational accessibility, not finite-shot or hardware-accessible performance.

#### Overall assessment

E19 provides a useful circuit-family and parameter-sensitivity map, but it does not map the canonical QuIC object.

For the implemented unnormalized encoder, the cubic result is strong. The nominal one-repetition X-mixer schedule lies on a broad high-performing region: triangles remain exact, diamond count remains near exact, and C5 remains within (0.002) of the best value observed along any individual angle axis.

The alternative-circuit results clarify which design choices matter. Additional depth provides no C5 advantage. A Y mixer retains strong but slightly weaker accessibility. QAOA preparation preserves triangles and diamonds but loses much of the C5 signal. The non-equivariant encoder performs poorly on the deeper targets.

The heterogeneous (n=8) map has a different interpretation. Degree-dependent preparation alone predicts substantial triangle and connectivity variation, so several maxima occur with no mixer or no entangler. Those results do not isolate topology transmitted through the quantum graph circuit.

The appropriate central claim for the current notebook is:

> For the unnormalized E18 circuit family, the nominal one-repetition X-mixer schedule lies on a broad high-decodability region of the complete cubic (n=14) census: triangle and diamond prediction remains near exact and 5-cycle prediction stays within (0.002) of the best value observed along each one-dimensional angle transect. Alternative preparations, mixer axes, and additional depth preserve shallow structure but generally reduce 5-cycle accessibility, while a non-equivariant encoder performs poorly. On the heterogeneous (n=8) census, several maxima occur without entanglement or mixing because the unnormalized degree preparation already carries substantial graph information. The experiment must be repeated with the normalized encoder (R_X(\alpha d_i/\Delta)) before it can support a canonical QuIC angle-robustness claim.

### E19 - One-Dimensional Angle Map

#### Experimental design

E19 maps the sensitivity of QuIC and four related circuit families to their three continuous angle parameters.

The experiment uses two complete graph censuses:

* **11,117 connected graphs at (n=8)**;
* **509 connected cubic graphs at (n=14)**.

The canonical angle schedule is:

$$\alpha=2.875,\qquad\gamma=2.0,\qquad\beta=0.1.$$

For the canonical degree encoder:

$$R_X\left(\alpha\frac{d_i}{\Delta}\right),$$

where (d_i) is the degree of vertex (i) and (\Delta) is the maximum degree of the graph.

The entangler and mixer are:

$$R_{ZZ}(\gamma),\qquad R_X(\beta),$$

except in circuit families that replace the preparation or mixer.

E19 varies one angle at a time while holding the other two at their canonical values.

The sampled grids are:

$$\alpha\in{0,0.449,0.898,1.346,1.795,2.244,2.693,2.875,\pi},$$

$$\gamma\in{0,0.449,0.898,1.346,1.795,2.0,2.244,2.693,\pi},$$

and:

$$\beta\in{0,0.1,0.224,0.449,0.673,0.898,1.122,1.346,\pi/2}.$$

Each axis therefore contains nine points, including the canonical center exactly.

The experiment is a set of one-dimensional transects, not a joint search over the three-dimensional angle cube.

#### Circuit families

Five graph-dependent circuits are mapped.

1. **C2 — canonical QuIC**

   Normalized degree preparation, one entangler layer, and one X-mixer layer.

2. **C3 — QAOA-style preparation**

   Uniform (|+\rangle^{\otimes n}) preparation, one entangler layer, and one X-mixer layer.

3. **C4 — two-repetition QuIC**

   Normalized degree preparation followed by two tied entangler–X-mixer repetitions.

4. **C5 — Y-mixer QuIC**

   Normalized degree preparation, one entangler layer, and one Y-mixer layer.

5. **C6 — non-equivariant index encoder**

   Index-dependent preparation followed by one entangler and one X mixer.

Two graph-blind controls are evaluated separately:

* C0 preparation only;
* C1 phase only.

#### Targets and readout depths

At (n=8), the targets are:

* triangle count;
* vertex connectivity.

At (n=14), the targets are:

* triangle count;
* 5-cycle count;
* diamond count.

The complete 256-dimensional sorted probability vector is used at (n=8).

At (n=14), the first:

$$k=1000$$

sorted probabilities are retained.

The decoder uses:

* five shuffled outer folds;
* fixed seed zero;
* `RidgeCV`;
* inner five-fold cross-validation;
* regularization grid:

$$\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2}.$$

The reported value at every angle is the mean outer-fold (R^2).

#### Correction relative to the original E19 run

The original notebook implemented the degree encoder as:

$$R_X(\alpha d_i),$$

rather than:

$$R_X\left(\alpha\frac{d_i}{\Delta}\right).$$

The corrected notebook applies maximum-degree normalization consistently in:

* C2 canonical QuIC;
* C4 two-repetition QuIC;
* C5 Y-mixer QuIC.

The following circuit families are unchanged by the correction:

* C3 QAOA preparation, which has no degree encoder;
* C6 index encoding;
* C0 and C1 controls.

On the cubic census:

$$d_i=\Delta=3,$$

so the corrected realized preparation angle is:

$$\alpha.$$

The original notebook instead applied:

$$3\alpha.$$

This changes both the canonical center and the interpretation of the alpha axis.

For example, the original cubic C2 triangle and diamond maxima occurred at:

$$\alpha=0.898.$$

The corrected maxima occur at:

$$\alpha=2.693.$$

The relationship:

$$3(0.898)\approx2.693$$

is the direct signature of the missing normalization.

#### Effect of the correction at the canonical center

The canonical C2 values change as follows.

##### Mixed-degree (n=8) census

| Target       | Original unnormalized center | Corrected normalized center |   Change |
| ------------ | ---------------------------: | --------------------------: | -------: |
| (C_3)        |                        0.770 |                       0.007 | (-0.763) |
| Connectivity |                        0.573 |                       0.123 | (-0.450) |

The strong mixed-degree result in the original E19 run was therefore an artifact of the unnormalized degree rotations.

##### Cubic (n=14) census

| Target   | Original unnormalized center | Corrected normalized center |   Change |
| -------- | ---------------------------: | --------------------------: | -------: |
| (C_3)    |                        1.000 |                       1.000 |    0.000 |
| (C_5)    |                        0.985 |                       0.928 | (-0.057) |
| Diamonds |                        0.998 |                       0.993 | (-0.005) |

Normalization has little effect on the saturated triangle and diamond results but materially reduces canonical 5-cycle accessibility.

The corrected center reproduces the established E2 and corrected E18 record:

$$R^2_{C_3}=1.000,\qquad R^2_{C_5}=0.928,\qquad R^2_D=0.993.$$

#### Validation gates

The corrected notebook reconstructs both complete censuses:

$$11{,}117$$

connected graphs at (n=8), and:

$$509$$

connected cubic graphs at (n=14).

For the cubic census, it verifies:

$$\text{tr}(A^3)=6C_3,$$

$$\text{tr}(A^4)=8C_4+15n,$$

and:

$$\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).$$

The diamond target is therefore independently certified.

The notebook does not apply the corresponding fifth-trace identity to certify (C_5) directly. Its canonical-center agreement with E2 supplies an external consistency check for that target.

The independent E2 gate passes exactly at displayed precision:

| Target   | Corrected center | E2 record | Difference |
| -------- | ---------------: | --------: | ---------: |
| (C_3)    |            1.000 |     1.000 |      0.000 |
| (C_5)    |            0.928 |     0.928 |      0.000 |
| Diamonds |            0.993 |     0.993 |      0.000 |

The notebook also contains a factory-equivalence gate against the corrected E18 artifact.

That artifact was not mounted during the recorded run, so the automated E18 gate was skipped. The final notebook prose incorrectly instructs the reader to confirm that both gates passed.

Only the E2 gate executed.

The printed canonical-center values nevertheless match corrected E18 to displayed precision.

#### Graph-blind controls

C0 and C1 remain at the constant-predictor floor.

| Census | Circuit             | Best score across tested configurations |
| ------ | ------------------- | --------------------------------------: |
| (n=8)  | C0 preparation only |                     approximately 0.000 |
| (n=8)  | C1 phase only       |                     approximately 0.000 |
| (n=14) | C0 preparation only |                                (-0.003) |
| (n=14) | C1 phase only       |                                (-0.003) |

C1 remains graph blind throughout its complete gamma transect.

The graph-dependent (R_{ZZ}) phases do not alter computational-basis probabilities until a noncommuting operation converts phase information into amplitude information.

This reproduces the mechanism established in E9 and E18.

#### Canonical QuIC on cubic graphs

The sampled C2 extrema are:

| Axis  | Target   | Canonical center | Best sampled score | Best sampled angle |
| ----- | -------- | ---------------: | -----------------: | -----------------: |
| Alpha | (C_3)    |            1.000 |              1.000 |              2.693 |
| Alpha | (C_5)    |            0.928 |              0.987 |              2.244 |
| Alpha | Diamonds |            0.993 |              0.999 |              2.693 |
| Gamma | (C_3)    |            1.000 |              1.000 |              1.346 |
| Gamma | (C_5)    |            0.928 |              0.971 |              1.795 |
| Gamma | Diamonds |            0.993 |              1.000 |              2.244 |
| Beta  | (C_3)    |            1.000 |              1.000 |              0.224 |
| Beta  | (C_5)    |            0.928 |              0.979 |              0.449 |
| Beta  | Diamonds |            0.993 |              1.000 |              0.224 |

The canonical schedule is already at or near the best sampled value for:

* triangles;
* diamonds.

Five-cycle count has meaningful angle headroom.

The largest sampled C5 improvement is:

$$0.987-0.928=0.059,$$

obtained by changing:

$$\alpha:2.875\rightarrow2.244.$$

Changing beta produces:

$$0.928\rightarrow0.979,$$

and changing gamma produces:

$$0.928\rightarrow0.971.$$

Thus, the canonical C5 score is not an architectural ceiling.

#### Cubic triangle and diamond stability

Triangle count is exactly decoded at the canonical center and at several reported one-axis extrema.

Diamond count remains between approximately:

$$0.993\quad\text{and}\quad1.000$$

at the center and best sampled points.

The map therefore shows that the central cubic C3 and diamond conclusions are not consequences of one uniquely tuned triple.

The experiment does not establish a broad plateau because it prints only the extrema rather than the complete curve table, and the nine-point grids are coarse.

The defensible statement is that the canonical center lies close to the best sampled one-axis values.

#### Cubic 5-cycle sensitivity

C5 is more angle sensitive than C3 or diamonds.

Every one-dimensional C2 transect contains a sampled setting that materially improves upon the canonical score.

This supports two conclusions.

1. The weaker canonical C5 score is partly schedule dependent.

2. The hierarchy:

$$C_3>D>C_5$$

at the canonical center should not be interpreted as a fixed ordering over all parameter settings.

C5 remains highly accessible, but its linear alignment with the sorted representation changes more strongly with the angle schedule.

#### Requirement for both entanglement and mixing on cubic graphs

On the regular cubic census, the normalized degree encoder reduces to one uniform rotation.

If:

$$\gamma=0,$$

the circuit contains no graph-dependent operation.

If:

$$\beta=0,$$

the graph-dependent entanglers modify only phases, leaving the sorted Born probabilities graph independent.

Thus, the cubic topology signal requires:

* nonzero graph-dependent phase accumulation;
* and a noncommuting mixer.

The strong sampled values occur away from these graph-blind boundaries.

This connects the global map to E9’s local beta-expansion analysis.

#### Canonical QuIC on the mixed-degree census

The corrected canonical center is weak:

$$R^2_{C_3}=0.007,\qquad R^2_{\text{connectivity}}=0.123.$$

The best sampled C2 values are:

| Axis  | Target       | Canonical center | Best sampled score | Best sampled angle |
| ----- | ------------ | ---------------: | -----------------: | -----------------: |
| Alpha | (C_3)        |            0.007 |              0.243 |              (\pi) |
| Alpha | Connectivity |            0.123 |              0.602 |              2.244 |
| Gamma | (C_3)        |            0.007 |              0.404 |              0.000 |
| Gamma | Connectivity |            0.123 |              0.438 |              (\pi) |
| Beta  | (C_3)        |            0.007 |              0.410 |              0.000 |
| Beta  | Connectivity |            0.123 |              0.517 |              0.000 |

The maxima initially appear to show that angle changes substantially improve the heterogeneous result.

Several of the largest scores, however, occur at settings that remove the topology-sensitive part of the circuit.

#### Degree-only endpoints at (n=8)

At:

$$\beta=0,$$

the entangler changes phases but no later noncommuting operation converts those phases into probabilities.

The sorted probabilities depend on the normalized degree preparation but not on edge arrangement beyond the degree sequence.

For C2, C4, and C5, the beta-zero representation therefore reduces to the same degree-sequence-derived probability multiset.

All three circuits consequently report the same beta-zero maxima:

$$R^2_{C_3}=0.410,\qquad R^2_{\text{connectivity}}=0.517.$$

Similarly, for C2 at:

$$\gamma=0,$$

the representation is produced only by degree-dependent single-qubit rotations and the X mixer. It contains no edge-entangling topology.

Its triangle score reaches:

$$0.404.$$

These values do not demonstrate improved topology encoding.

They show that degree sequence alone is correlated with triangles and connectivity across the complete mixed-degree census.

The correct interpretation is:

> Moving away from the canonical center can expose stronger degree-sequence baselines, but E19 does not show that canonical QuIC can recover a regular-like topological hierarchy on the heterogeneous census.

#### Connectivity at nonzero entanglement

The best C2 connectivity score is:

$$0.602$$

at:

$$\alpha=2.244,$$

with canonical gamma and beta retained.

This configuration includes both entanglement and mixing and therefore cannot be reduced to the beta-zero degree-only baseline.

However, the experiment does not compare the score against a degree-sequence-only classical baseline or condition on degree sequence.

The result shows angle sensitivity but does not isolate topology beyond degrees.

#### QAOA-style preparation

C3 has no encoder.

Its alpha transect therefore evaluates the same circuit nine times.

The reported alpha “peak” at zero is an arbitrary first occurrence of a complete tie and has no scientific interpretation.

The meaningful QAOA axes are gamma and beta.

##### Mixed-degree (n=8)

| Axis  | Target       | Corrected E18 center | Best sampled score | Best sampled angle |
| ----- | ------------ | -------------------: | -----------------: | -----------------: |
| Gamma | (C_3)        |                0.114 |              0.981 |              0.449 |
| Gamma | Connectivity |                0.061 |              0.778 |              0.449 |
| Beta  | (C_3)        |                0.114 |              0.450 |            (\pi/2) |
| Beta  | Connectivity |                0.061 |              0.290 |            (\pi/2) |

A single gamma setting:

$$\gamma=0.449$$

raises both targets dramatically.

Because the QAOA preparation contains no degree encoder, this result cannot be explained by direct degree-sequence amplitudes in the same manner as C2’s beta-zero endpoint.

The weak QAOA row in E18 is therefore highly schedule specific.

##### Cubic (n=14)

| Axis  | Target   | Corrected E18 center | Best sampled score | Best sampled angle |
| ----- | -------- | -------------------: | -----------------: | -----------------: |
| Gamma | (C_3)    |                0.544 |              0.986 |              2.693 |
| Gamma | (C_5)    |                0.348 |              0.512 |              2.693 |
| Gamma | Diamonds |                0.717 |              0.940 |              1.346 |
| Beta  | (C_3)    |                0.544 |              0.717 |              0.449 |
| Beta  | (C_5)    |                0.348 |              0.607 |              0.898 |
| Beta  | Diamonds |                0.717 |              0.717 |              0.100 |

Angle variation narrows the gap between QAOA preparation and canonical QuIC, especially for triangles and diamonds.

Even at its best sampled one-axis values, QAOA remains weaker for C5 and diamonds than the normalized QuIC variants.

The target extrema also occur at different settings, so the table does not describe one jointly optimal QAOA circuit.

#### Two-repetition QuIC

##### Cubic (n=14)

| Axis  | Target   | Corrected E18 center | Best sampled score | Best sampled angle |
| ----- | -------- | -------------------: | -----------------: | -----------------: |
| Alpha | (C_3)    |                1.000 |              1.000 |              2.875 |
| Alpha | (C_5)    |                0.960 |              0.960 |              2.875 |
| Alpha | Diamonds |                0.998 |              1.000 |              (\pi) |
| Gamma | (C_3)    |                1.000 |              1.000 |              2.244 |
| Gamma | (C_5)    |                0.960 |              0.963 |              1.795 |
| Gamma | Diamonds |                0.998 |              1.000 |              0.898 |
| Beta  | (C_3)    |                1.000 |              1.000 |              0.100 |
| Beta  | (C_5)    |                0.960 |              0.977 |              0.449 |
| Beta  | Diamonds |                0.998 |              0.999 |              0.449 |

The corrected E18 center is already close to the best sampled points.

The largest improvement is:

$$0.960\rightarrow0.977$$

for C5 under beta variation.

The two-repetition circuit is therefore less sensitive than canonical C2 on the mapped C5 transects, although the experiment does not provide a formal sensitivity statistic.

##### Mixed-degree (n=8)

The best sampled results are:

| Axis  |          (C_3) |   Connectivity |
| ----- | -------------: | -------------: |
| Alpha | 0.313 at 0.000 | 0.567 at 2.244 |
| Gamma | 0.305 at 0.000 | 0.467 at 0.000 |
| Beta  | 0.410 at 0.000 | 0.517 at 0.000 |

The alpha-zero C4 circuit is not graph blind.

After the first mixer creates a superposition, the second entangler can convert graph topology into a later probability effect.

Nevertheless, the strongest beta-zero values are again the shared degree-only baseline.

No regular-like mixed-degree hierarchy is recovered.

#### Y-mixer QuIC

##### Cubic (n=14)

| Axis  | Target   | Corrected E18 center | Best sampled score | Best sampled angle |
| ----- | -------- | -------------------: | -----------------: | -----------------: |
| Alpha | (C_3)    |                1.000 |              1.000 |              2.875 |
| Alpha | (C_5)    |                0.951 |              0.951 |              2.875 |
| Alpha | Diamonds |                0.998 |              0.999 |              1.795 |
| Gamma | (C_3)    |                1.000 |              1.000 |              0.449 |
| Gamma | (C_5)    |                0.951 |              0.961 |              1.346 |
| Gamma | Diamonds |                0.998 |              1.000 |              0.449 |
| Beta  | (C_3)    |                1.000 |              1.000 |              0.224 |
| Beta  | (C_5)    |                0.951 |              0.988 |              0.898 |
| Beta  | Diamonds |                0.998 |              1.000 |              0.449 |

The Y mixer produces the strongest sampled C5 value among the mapped equivariant circuits:

$$R^2_{C_5}=0.988.$$

This slightly exceeds the best sampled C2 value:

$$0.987.$$

It occurs at:

$$\beta=0.898,$$

not at the canonical Y-mixer center.

The corrected E18 conclusion that mixer axis redistributes deeper structural accessibility is therefore strengthened.

##### Mixed-degree (n=8)

The best values are:

| Axis  |          (C_3) |   Connectivity |
| ----- | -------------: | -------------: |
| Alpha | 0.375 at 0.898 | 0.598 at 2.244 |
| Gamma | 0.274 at 0.449 | 0.428 at 0.000 |
| Beta  | 0.410 at 0.000 | 0.517 at 0.000 |

As with C2 and C4, the beta-zero maximum is the normalized degree-only representation rather than a topology-sensitive Y-mixer circuit.

#### Non-equivariant index encoder

C6 is unchanged from the original E19 run.

##### Mixed-degree (n=8)

Its strongest sampled values are:

$$R^2_{C_3}=0.781,\qquad R^2_{\text{connectivity}}=0.564,$$

both at:

$$\gamma=0.449.$$

##### Cubic (n=14)

Its strongest sampled values across the separate transects are:

$$R^2_{C_3}=0.916,$$

$$R^2_{C_5}=0.158,$$

and:

$$R^2_D=0.214.$$

The C3 result shows that a label-dependent coordinate system can be highly predictive under one fixed canonical census labeling.

It does not define a graph invariant.

E18 showed that C6 changes substantially under vertex relabeling. Its angle-map scores therefore cannot be treated as valid unlabeled-graph representation performance.

The circuit remains useful only as a negative equivariance control.

#### Best sampled one-axis values by circuit

The following table takes the maximum over all three separate transects.

The entries in one row generally occur at different angle settings and do not describe one jointly realizable circuit.

##### Cubic (n=14)

| Circuit             | Best sampled (C_3) | Best sampled (C_5) | Best sampled diamonds |
| ------------------- | -----------------: | -----------------: | --------------------: |
| C2 canonical QuIC   |              1.000 |              0.987 |                 1.000 |
| C3 QAOA preparation |              0.986 |              0.607 |                 0.940 |
| C4 two repetitions  |              1.000 |              0.977 |                 1.000 |
| C5 Y mixer          |              1.000 |              0.988 |                 1.000 |
| C6 non-equivariant  |              0.916 |              0.158 |                 0.214 |

The three equivariant QuIC variants are essentially tied on triangles and diamonds at their best sampled points.

C2 and C5 are also effectively tied on C5:

$$0.987\quad\text{versus}\quad0.988.$$

Circuit architecture comparisons based only on the canonical E18 column are therefore schedule dependent.

The QAOA-style circuit remains weaker overall, but angle adjustment substantially reduces its apparent deficit.

#### Relationship to E18

E18 compares circuit families at one fixed angle schedule.

E19 shows that several E18 rankings are not invariant to the angle choice.

The most important examples are:

* QAOA C3 at (n=14): (0.544\rightarrow0.986);
* QAOA diamonds at (n=14): (0.717\rightarrow0.940);
* QAOA C3 at (n=8): (0.114\rightarrow0.981);
* Y-mixer C5 at (n=14): (0.951\rightarrow0.988);
* canonical C2 C5 at (n=14): (0.928\rightarrow0.987).

E18 remains the controlled canonical-schedule comparison.

E19 shows that its absolute and relative scores should not be interpreted as architecture ceilings.

#### Relationship to E9

E9 studies the local emergence of graph information as beta moves away from zero.

On a regular graph family, beta zero removes the only mechanism that converts graph-dependent phases into probabilities.

E19 extends that local mechanism across a coarse global beta transect.

The cubic results are consistent with:

$$\beta=0\Longrightarrow\text{graph-blind sorted probabilities}.$$

The mixed-degree result is different.

At beta zero, the normalized degree encoder already creates graph-dependent amplitudes through the degree sequence. The representation is not topology sensitive, but it is not graph blind.

E19 therefore clarifies that the beta-zero collapse is exact on regular families and becomes a degree-sequence baseline on heterogeneous families.

#### Relationship to E21 and E23

E21 showed that canonical sorted QuIC is strong on regular cubic and 4-regular censuses but weak on the complete mixed-degree census.

E23 showed that sorting removes useful heterogeneous degree-role information while strongly aligning regular-graph structure.

E19 does not overturn those conclusions.

Although selected n8 angles produce higher scores, many of the strongest values arise when entanglement or mixing is removed and the readout depends primarily on degree sequence.

The angle map therefore does not demonstrate that parameter tuning restores the regular-graph topology geometry on heterogeneous graphs.

#### What the experiment establishes

The completed results establish that:

1. **The corrected E19 map uses the canonical maximum-degree-normalized encoder.**

2. **The canonical cubic center reproduces the independent E2 record.**

3. **Preparation-only and phase-only controls remain at the prediction floor throughout their tested configurations.**

4. **Cubic triangle and diamond accessibility are not tied to one exact angle triple.**

   The canonical center is already near the best sampled one-axis values.

5. **Cubic 5-cycle accessibility is more angle sensitive.**

   Canonical C2 improves from (0.928) to as high as (0.987).

6. **The Y-mixer circuit reaches the strongest sampled C5 score.**

   Its maximum is (0.988).

7. **The two-repetition circuit is already close to its sampled maxima at the corrected E18 center.**

8. **The weak canonical QAOA results are strongly angle dependent.**

   QAOA can reach (0.986) on cubic triangles and (0.981) on mixed-degree triangles.

9. **Fixed-angle architecture rankings are not architecture ceilings.**

10. **Several mixed-degree maxima are degree-sequence-only endpoints.**

    They do not establish improved topological encoding.

11. **The non-equivariant circuit can achieve strong scores under a fixed labeling but remains invalid as an unlabeled-graph representation.**

12. **The original unnormalized E19 results should be replaced completely.**

E19 therefore supports angle sensitivity and schedule-dependent structural accessibility, not angle optimization or a universal robustness claim.

#### Necessary qualifications

The experiment varies only one angle at a time.

It does not search the complete:

$$\alpha\times\gamma\times\beta$$

parameter space.

The best joint schedule may differ substantially from every reported transect maximum.

Conversely, target-specific maxima from different axes cannot be combined into one circuit.

The grids contain only nine points per axis.

The experiment cannot determine:

* exact optima;
* peak widths;
* derivatives;
* or broad robustness plateaus.

Several maxima occur at grid boundaries, including:

* C2 n8 triangle at (alpha=\pi);
* QAOA n8 beta maxima at (beta=\pi/2).

These should be interpreted as lower bounds on the best value within a larger parameter domain, not as established global maxima.

The scanned ranges do not cover complete gate periodicities.

The notebook evaluates:

$$5\times3\times9=135$$

mapped circuit configurations per census.

The reported maxima are selected using the same outer folds used to score them.

They are therefore exploratory test-set maxima.

No independent graph split or nested angle-selection loop evaluates the generalization of a selected angle.

The numerical maxima are expected to be optimistically biased.

No correction is applied for the large number of:

* circuits;
* axes;
* angles;
* and targets.

No fold-level standard deviations, confidence intervals, or paired comparisons are printed.

Differences of a few thousandths should be treated as ties.

The QAOA alpha transect is redundant because the QAOA circuit has no encoder and ignores alpha entirely.

Its reported alpha maxima are arbitrary tie-breaking artifacts.

The final notebook prose says that both canonical-center gates passed, but the E18 artifact was absent and the factory-equivalence assertion was skipped.

Only the independent E2 gate executed.

The n14 C5 target is not independently certified through the fifth adjacency trace in this notebook.

The decoder uses a 1,000-dimensional feature matrix for only 509 cubic graphs.

Repeated ill-conditioned-matrix warnings occur throughout the run.

The ridge grid extends to:

$$10^{-14},$$

and the features are not standardized.

E10 showed that some QuIC probe results are sensitive to weak regularization and low-singular-value directions.

The largest qualitative effects are unlikely to be explained by numerical instability alone, but fine architecture and angle differences require caution.

The experiment maps only:

* C3 and connectivity at (n=8);
* C3, C5, and diamonds at (n=14).

It does not map:

* C4;
* C6;
* girth;
* spectral gap;
* or metric targets.

The angle conclusions should not be generalized to the entire structural hierarchy.

The graph families and target sets differ between the two orders.

Differences between (n=8) and (n=14) cannot be attributed to graph order alone.

On the mixed-degree census, the degree encoder allows graph-dependent probabilities even without an entangling contribution.

Angle-map improvements must therefore be separated from genuine topology-sensitive improvements.

No classical degree-sequence baseline is included.

All results use exact statevector probabilities.

Finite-shot recovery may change both the preferred angles and the relative circuit rankings.

Finally, the experiment does not evaluate computational cost, trainable optimization, barren plateaus, or hardware robustness.

The words “peak” and “best” refer only to the sampled one-dimensional grid.

#### Overall assessment

The corrected E19 run supplies the angle analysis that the original unnormalized notebook could not support.

For cubic graphs, canonical QuIC remains extremely strong around the fixed schedule.

Triangles and diamonds are already saturated, while C5 has meaningful one-axis headroom:

$$0.928\rightarrow0.987.$$

The alternative circuits are also more competitive after angle variation than their fixed E18 rows suggest.

QAOA reaches:

$$R^2_{C_3}=0.986,\qquad R^2_D=0.940,$$

and the Y-mixer circuit reaches:

$$R^2_{C_5}=0.988.$$

Thus, the paper should not present the canonical E18 rankings as fundamental architecture rankings.

The mixed-degree results require a different interpretation.

Canonical C2 remains weak at the corrected center, and several large apparent gains occur at beta or gamma zero. Those endpoints remove topology-sensitive interference and expose degree-sequence correlations instead. Angle changes can improve target prediction, but E19 does not show that they restore the regular-graph structural geometry.

The appropriate central claim is:

> Under the corrected maximum-degree-normalized encoder, QuIC’s cubic triangle and diamond accessibility remains saturated across multiple sampled one-axis settings, while 5-cycle accessibility is more schedule dependent and improves from (0.928) to approximately (0.987). Angle variation also substantially strengthens alternative circuits, including QAOA-style preparation and the Y-mixer family, showing that fixed-angle circuit rankings are not architecture ceilings. On the complete mixed-degree census, however, several of the strongest scores occur at degree-sequence-only endpoints where entanglement is not converted into probability structure. E19 therefore establishes schedule-dependent structural accessibility and near-center cubic stability, but not global angle robustness, joint optimization, or recovery of heterogeneous topology encoding.


### E20 - Exact Partition Audit

#### Experimental design

E20 attempts to certify whether the sorted QuIC readout induces a discrete partition on the complete connected graph census at:

* **11,117 graphs at (n=8)**.

A discrete partition means that every graph forms a singleton readout class:

$$
\mathbf p(G)=\mathbf p(H)\Longrightarrow G=H
$$

within the enumerated unlabeled census.

The experiment is stronger than a rounded-vector collision count. It uses three numerical routes:

1. **Primary Qiskit statevector implementation**

   The circuit is constructed in Qiskit and evaluated in double precision.

2. **Independent gate-level implementation**

   The same circuit is reconstructed without Qiskit using explicit dense (R_X) matrices, diagonal (R_{ZZ}) phases, and tensor contractions.

3. **Extended-precision implementation**

   The closest candidate graph pairs are recomputed using 32-decimal-digit `mpmath` arithmetic.

The complete connected census is generated using:

$$
\texttt{nauty-geng -c 8}.
$$

For each graph, the complete sorted probability vector has dimension:

$$
2^8=256.
$$

The experiment then computes:

* 12-decimal rounded fingerprints for all readouts;
* an exhaustive all-graph nearest-neighbor search;
* an independent implementation comparison;
* extended-precision separations for the 100 closest candidate pairs.

The intended canonical degree encoder is:

$$
R_X\left(2.875\frac{d_i}{\Delta}\right),
$$

where (d_i) is the vertex degree and (\Delta) is the graph’s maximum degree.

The notebook does not implement that encoder. It instead applies:

$$
R_X(2.875d_i).
$$

This is a materially different circuit. For example, a degree-7 vertex receives:

$$
2.875\times7=20.125
$$

radians rather than the canonical maximum rotation:

$$
2.875.
$$

The current run therefore audits an **unnormalized degree encoder**, not the canonical QuIC representation used in the preceding experiments.

#### Census validation

The enumeration returns exactly:

$$
11{,}117
$$

connected unlabeled graphs, matching the known complete (n=8) census size expected by the notebook.

Each graph is converted from graph6 format into an (8\times8) adjacency matrix using a consistent sorted node order.

#### Rounded-readout distinctness

Every graph produces a distinct 12-decimal rounded fingerprint:

$$
11{,}117/11{,}117.
$$

No multi-graph readout class is observed under the implemented circuit.

Because two exactly equal floating-point arrays would necessarily have the same rounded fingerprint, the result rules out literal equality among the computed Qiskit vectors.

It also shows that the minimum observed separation is not confined below the 12-decimal fingerprint resolution.

#### Nearest-neighbor separation

The notebook compares each graph with every other graph in chunked all-pairs passes and retains its nearest readout neighbor.

The resulting candidate nearest-neighbor distribution is:

| Statistic      | Sorted-readout (L_1) distance |
| -------------- | ----------------------------: |
| Minimum        |          (3.263\times10^{-3}) |
| 1st percentile |          (7.513\times10^{-3}) |
| Median         |          (3.300\times10^{-2}) |

The closest candidate pair is:

$$
(2960,4805),
$$

with separation:

$$
L_1=3.263\times10^{-3}.
$$

This is a large numerical margin relative to ordinary double-precision error.

However, the all-pairs distances are not actually computed in float64. Before the search, the Qiskit vectors are converted to:

$$
\texttt{float32}.
$$

The search is exhaustive over graph pairs but approximate in numerical precision.

The reported value should therefore be described as the exhaustive **float32 nearest-neighbor result**, not the exact float64 nearest-neighbor distance.

Given that the minimum is approximately (10^{-3}), float32 rounding is unlikely to explain the observed separation. It nevertheless prevents the current computation from serving as a formally exact float64 nearest-neighbor certificate.

#### Independent implementation agreement

The gate-level implementation agrees with the Qiskit implementation on all 11,117 graphs.

The worst sorted-vector discrepancy is:

$$
L_1=8.044\times10^{-16}.
$$

The prespecified tolerance is:

$$
10^{-12}.
$$

Thus:

$$
8.044\times10^{-16}<10^{-12}.
$$

This confirms that the computed readouts are not specific to Qiskit’s statevector-construction path.

The comparison is particularly useful because the second implementation independently applies:

* single-qubit (R_X) gates;
* edgewise diagonal (R_{ZZ}) phases;
* the final mixer;
* Born-probability conversion;
* descending sorting.

The two implementations nevertheless share the same unnormalized encoder formula. Their agreement validates the implemented circuit, not the intended canonical circuit.

#### Extended-precision separation

The 100 closest candidate pairs from the float32 nearest-neighbor pass are recomputed using 32-decimal-digit arithmetic.

All 100 pairs remain distinct.

The smallest extended-precision separation is:

$$
L_1=3.263\times10^{-3},
$$

again occurring for pair:

$$
(2960,4805).
$$

The certification floor is:

$$
10^{-20},
$$

and the observed minimum satisfies:

$$
3.263\times10^{-3}>10^{-20}.
$$

The closest tested pairs are therefore genuinely separated under the implemented circuit and are not products of float64 cancellation or simulator noise.

The extended-precision result is much stronger than necessary for these particular pairs because the observed gaps are already approximately 13 orders of magnitude above the certification floor.

#### Relationship to E16 / E17

E16 / E17 evaluated the canonical normalized degree encoder and reported a candidate minimum (n=8) separation of:

$$
2.159\times10^{-5}.
$$

E20 reports:

$$
3.263\times10^{-3},
$$

which is approximately:

$$
151
$$

times larger.

This is not a consistency check between the two experiments.

The earlier notebook uses:

$$
R_X\left(2.875\frac{d_i}{\Delta}\right),
$$

while E20 uses:

$$
R_X(2.875d_i).
$$

The large change in the readout-separation scale is therefore consistent with the circuit having changed.

The nearest-neighbor procedures also differ:

* E16 / E17 uses a local candidate window after sorting graphs by their largest probability;
* E20 performs an exhaustive graph-pair search, but in float32.

The two reported minima cannot be treated as independent estimates of the same quantity.

#### What the experiment establishes

The completed run establishes that:

1. **The unnormalized degree-encoder readout is injective on the complete connected (n=8) census at the tested parameters.**

   All 11,117 computed readouts have distinct 12-decimal fingerprints.

2. **The observed separations are not Qiskit-specific.**

   An independent gate-level implementation agrees on every graph with worst discrepancy:

   $$
   8.044\times10^{-16}.
   $$

3. **The closest tested pairs remain separated at extended precision.**

   All 100 candidate nearest-neighbor pairs remain distinct at 32 decimal digits.

4. **The minimum observed candidate separation is numerically large.**

   The smallest float32 and extended-precision distance is approximately:

   $$
   3.263\times10^{-3}.
   $$

5. **The run does not certify the canonical QuIC partition.**

   The implemented vertex rotation omits normalization by maximum degree.

The appropriate conclusion is therefore specific to the circuit that was actually executed.

#### Necessary qualifications

The principal qualification is the encoder mismatch.

The code labels:

$$
2.875
$$

as the maximum encoding rotation, but multiplies it directly by vertex degree. The implemented maximum rotation can therefore substantially exceed (2.875).

The notebook must be rerun with:

$$
\theta_i=2.875\frac{d_i}{\Delta}
$$

before E20 can be used as a certification of the canonical QuIC object.

The independent Qiskit and gate-level implementations do not detect this issue because both use the same incorrect formula.

The nearest-neighbor search converts the readout matrix to float32. It is exhaustive over graph pairs but not exact in the original float64 coordinates.

A strict certification should compute the candidate ordering and distances in float64, even if smaller chunks are required to control memory.

Only the 100 pairs selected by the float32 pass are evaluated at extended precision. If float32 rounding changes the nearest-neighbor ordering, the true closest float64 pair may not appear in that set.

The large observed minimum makes such a failure unlikely to alter the qualitative conclusion for this alternative circuit, but the current procedure does not mathematically exclude it.

The extended-precision implementation constructs its angles from Python floating-point values. It therefore evaluates high-precision arithmetic at the binary-float approximations of:

$$
2.875,\quad2.0,\quad0.1,
$$

rather than constructing those decimal values directly at arbitrary precision.

For a strict real-parameter audit, the angles should be initialized from decimal strings.

The rounded fingerprint test uses 12-decimal coordinate rounding. It is a strong census-level collision test but not a symbolic equality proof.

The experiment establishes injectivity only for:

* connected unlabeled graphs;
* (n=8);
* the tested circuit angles;
* one circuit repetition;
* the implemented sorted readout.

It does not imply injectivity at other graph orders or parameter settings.

Finally, injectivity of ideal statevector readouts does not imply finite-shot distinguishability. E7S shows that much smaller structural and cospectral differences can remain below multinomial sampling noise even when they are numerically genuine.

#### Overall assessment

The numerical audit is methodologically strong in outline:

* complete census enumeration;
* all-graph collision testing;
* exhaustive candidate search;
* an independent circuit implementation;
* and extended-precision verification of the closest pairs.

The run also produces an unambiguous result for the circuit that was executed. Every connected (n=8) graph receives a distinct sorted readout, the two implementations agree near machine precision, and the closest tested pair remains separated by approximately:

$$
3.263\times10^{-3}
$$

at 32-decimal-digit precision.

The result cannot yet serve its intended role in the QuIC paper because the encoder differs from the canonical object. The omission of maximum-degree normalization changes the circuit and explains why the separation scale does not reproduce E16 / E17.

The appropriate central claim for the current notebook is:

> Under an unnormalized degree encoder (R_X(2.875d_i)), the sorted QuIC readout is injective on the complete connected (n=8) graph census: all 11,117 graphs have distinct computed vectors, an independent gate-level implementation agrees with Qiskit to a worst-case (L_1) error of (8.044\times10^{-16}), and the 100 closest candidate pairs remain separated at 32-decimal-digit precision. Because the implemented encoder omits normalization by maximum degree, this run does not yet certify the canonical QuIC partition and must be repeated with (R_X(2.875d_i/\Delta)).

### E20 - Exact Partition Audit

#### Experimental design

E20 tests whether the canonical sorted QuIC readout induces a discrete partition on the complete connected graph census at:

* **11,117 graphs at (n=8)**.

A discrete partition means that no two distinct unlabeled census graphs receive the same readout:

$$
\mathbf p(G)=\mathbf p(H)\Longrightarrow G=H.
$$

Each graph is represented by its complete descending-sorted Born-probability vector:

$$
\mathbf p(G)\in\mathbb R^{256}.
$$

The circuit uses the canonical QuIC configuration:

* normalized degree encoder;
* edgewise (R_{ZZ}) entanglers;
* uniform (R_X) mixer;
* one entangler–mixer repetition.

The locked angles are:

$$
\alpha=2.875,\qquad\gamma=2.0,\qquad\beta=0.1.
$$

The vertex encoder is:

$$
R_X\left(2.875\frac{d_i}{\Delta}\right),
$$

where (d_i) is the degree of vertex (i) and (\Delta) is the maximum degree of the graph.

The audit uses three independent numerical routes.

1. **Primary Qiskit statevector implementation**

   The complete readout is computed in float64 using Qiskit.

2. **Independent gate-level implementation**

   The same circuit is reconstructed without Qiskit using explicit dense (R_X) gates, diagonal (R_{ZZ}) phases, and tensor contractions.

3. **Extended-precision implementation**

   The closest candidate graph pairs are recomputed with 32-decimal-digit `mpmath` arithmetic.

The experiment then performs:

* complete-census rounded-fingerprint counting;
* an exhaustive all-graph nearest-neighbor search;
* an all-graph independent-implementation comparison;
* extended-precision verification of the 100 closest candidate pairs.

#### Correction relative to the earlier E20 run

The original E20 notebook mistakenly implemented:

$$
R_X(2.875d_i)
$$

rather than:

$$
R_X\left(2.875\frac{d_i}{\Delta}\right).
$$

The corrected notebook applies maximum-degree normalization consistently in:

* the Qiskit implementation;
* the independent gate-level implementation;
* the extended-precision implementation.

The earlier unnormalized run therefore audited a different circuit and should be replaced by the current results.

The correction changes the separation scale substantially.

The earlier minimum was approximately:

$$
3.263\times10^{-3}.
$$

The corrected minimum is approximately:

$$
2.159\times10^{-5}.
$$

The unnormalized circuit therefore produced a closest-pair separation approximately:

$$
151
$$

times larger.

The partition verdict remains unchanged, but the geometry is materially different.

#### Census validation

The complete census is generated using:

$$
\texttt{nauty-geng -c 8}.
$$

The enumeration returns exactly:

$$
11{,}117
$$

connected unlabeled graphs.

Each graph is reconstructed from graph6 format as an (8\times8) adjacency matrix using a consistent sorted node order.

#### Rounded-readout distinctness

Every graph receives a distinct 12-decimal rounded fingerprint:

$$
11{,}117/11{,}117.
$$

No multi-graph collision class is observed.

Because two identical computed float64 vectors would necessarily produce the same rounded fingerprint, this result rules out literal equality among the stored primary readouts.

It also places the observed distinctions well above ordinary coordinate-level floating-point noise. At least one coordinate differs at the 12-decimal rounding scale for every graph pair.

#### Exhaustive nearest-neighbor search

The experiment compares every graph against every other graph in chunked all-pairs passes.

For each graph, it retains the nearest other readout under sorted-vector (L_1) distance.

The resulting nearest-neighbor distribution is:

| Statistic      | Sorted-readout (L_1) distance |
| -------------- | ----------------------------: |
| Minimum        |          (2.162\times10^{-5}) |
| 1st percentile |          (8.395\times10^{-4}) |
| Median         |          (3.116\times10^{-2}) |

The exhaustive candidate search therefore finds no near-collision remotely close to float64 precision.

The minimum candidate separation is approximately:

$$
2.2\times10^{-5}.
$$

This is more than ten orders of magnitude above ordinary double-precision roundoff.

The nearest-neighbor search is exhaustive over all graph pairs, unlike the local-window candidate search used in E16 / E17.

However, the readouts are converted to float32 before the all-pairs distance calculation. The search is therefore exhaustive in pair coverage but approximate in coordinate precision.

The reported:

$$
2.162\times10^{-5}
$$

value is the minimum found under the exhaustive float32 distance pass, not an exact float64 all-pairs minimum.

#### Independent implementation agreement

The gate-level implementation is evaluated on all 11,117 graphs.

The worst discrepancy from the Qiskit readout is:

$$
L_1=1.209\times10^{-15}.
$$

The prespecified tolerance is:

$$
10^{-12}.
$$

Thus:

$$
1.209\times10^{-15}<10^{-12}.
$$

The two implementations agree approximately three orders of magnitude more tightly than required.

This rules out the possibility that the distinct partition arises from one simulator’s:

* qubit ordering;
* gate convention;
* statevector construction;
* or probability-extraction path.

The second implementation independently reconstructs:

* every normalized degree rotation;
* every graph-edge (R_{ZZ}) phase;
* the final mixer;
* the Born probabilities;
* the descending sort.

The complete-census agreement therefore provides a strong implementation-level validation of the corrected circuit.

#### Extended-precision certification

The 100 closest candidate pairs identified by the exhaustive search are recomputed at:

$$
32
$$

decimal digits of working precision.

All 100 pairs remain separated.

The smallest extended-precision separation is:

$$
L_1=2.159\times10^{-5},
$$

for census members:

$$
(10{,}975,11{,}041).
$$

The certification floor is:

$$
10^{-20}.
$$

The observed minimum satisfies:

$$
2.159\times10^{-5}>10^{-20}.
$$

The smallest tested separation is therefore approximately:

$$
2.2\times10^{15}
$$

times larger than the certification floor.

The float32 candidate distance and extended-precision result differ by only approximately:

$$
0.14%.
$$

This indicates that float32 quantization changes the reported gap only slightly for the closest identified pair.

#### Relationship to E16 / E17

E16 / E17 reported a candidate minimum (n=8) separation of:

$$
2.159\times10^{-5}.
$$

The corrected E20 extended-precision result is:

$$
2.159\times10^{-5}.
$$

The agreement is exact at the displayed precision.

The two experiments use the same canonical normalized degree encoder.

Their nearest-neighbor procedures differ:

* E16 / E17 searches a local candidate window after sorting graphs by the leading probability;
* E20 performs an exhaustive float32 all-pairs search and then recomputes the closest candidates at extended precision.

E20 therefore upgrades the earlier candidate result.

The earlier local search happened to identify the same separation scale and apparently the same closest pair, while the exhaustive audit provides substantially stronger evidence that no smaller pair was missed by the local heuristic.

The notebook’s final markdown comment states that the E16 / E17 result used an unnormalized encoder. That statement is inconsistent with the matching separation and with the earlier canonical implementation record. It should be removed from the notebook documentation.

#### Partition verdict

The notebook declares:

$$
\boxed{\text{DISCRETE}}
$$

for the complete connected (n=8) census.

The verdict is supported by three numerical legs:

1. **Complete-census distinctness**

   $$
   11{,}117/11{,}117
   $$

   rounded readouts are unique.

2. **Independent implementation agreement**

   $$
   L_{1,\max}=1.209\times10^{-15}.
   $$

3. **Extended-precision separation**

   $$
   L_{1,\min}=2.159\times10^{-5}
   $$

   among the 100 closest candidate pairs.

Together, these results provide a strong finite-census numerical certificate that the canonical sorted QuIC readout is injective on the complete connected (n=8) census at the tested parameters.

#### What the experiment establishes

The corrected results establish that:

1. **The canonical normalized QuIC readout distinguishes every connected unlabeled graph at (n=8).**

   All 11,117 graphs receive distinct computed vectors.

2. **The partition result is not simulator specific.**

   An independent gate-level implementation agrees with Qiskit on every graph to worst-case (L_1) error:

   $$
   1.209\times10^{-15}.
   $$

3. **The closest identified readouts remain genuinely separated at extended precision.**

   All 100 candidate pairs remain distinct at 32 decimal digits.

4. **The minimum identified separation is approximately (2.16\times10^{-5}).**

5. **The exhaustive audit reproduces the earlier E16 / E17 separation scale.**

6. **Maximum-degree normalization materially affects the geometry.**

   The corrected nearest separation is approximately 151 times smaller than in the invalid unnormalized run.

7. **The correction changes the separation margin but not the census-level injectivity verdict.**

E20 therefore supplies the strongest numerical partition audit for the canonical QuIC object at (n=8).

#### Necessary qualifications

The result is a numerical finite-census certificate, not a symbolic injectivity theorem.

It establishes distinctness for:

* connected unlabeled graphs;
* exactly eight vertices;
* the canonical fixed angles;
* one circuit repetition;
* ideal statevector probabilities;
* descending-sorted readout vectors.

It does not prove injectivity for arbitrary graph orders or parameter values.

The nearest-neighbor search uses float32 coordinates.

Although it compares every pair, the candidate ranking and reported primary distances are not computed directly in float64. A stricter audit would retain float64 throughout the chunked search.

Only the 100 closest float32-selected candidate pairs are recomputed at extended precision.

If float32 rounding changed the ordering enough to exclude the true closest float64 pair from that set, the extended-precision minimum would not be globally certified.

The following evidence makes that concern small in practice:

* every 12-decimal fingerprint is unique;
* the nearest observed gap is approximately (10^{-5});
* the independent implementations agree near (10^{-15});
* the exhaustive result reproduces the independent E16 / E17 candidate minimum.

Nevertheless, the mathematically strict statement is that E20 certifies the selected nearest candidates rather than every pair at arbitrary precision.

The extended-precision implementation constructs its angles from Python floating-point values. It therefore evaluates high-precision arithmetic at the binary-float approximations of:

$$
2.875,\qquad2.0,\qquad0.1.
$$

A stricter arbitrary-precision audit would initialize the parameters from decimal strings.

The normalized encoder angle is also calculated in ordinary floating-point arithmetic before conversion to `mpmath`.

The rounded-fingerprint count uses coordinate-wise rounding to 12 decimal places. It is not a symbolic equality test.

The word “exact” in the notebook’s nearest-neighbor comments refers to exhaustive pair coverage, not exact arithmetic.

The experiment evaluates ideal probability vectors. It does not establish that all 11,117 graphs are distinguishable at finite shot counts.

E7S shows that much smaller structural distinctions can remain below sampling noise even when they are genuine in the exact probability representation.

Finally, injectivity does not imply useful global geometry. E16 / E17 and E21 show that the complete mixed-degree (n=8) census is only weakly organized by the tested graph invariants despite having distinct readouts for every graph.

#### Overall assessment

The corrected E20 run successfully performs the intended partition audit.

All three numerical routes now implement the canonical encoder:

$$
R_X\left(2.875\frac{d_i}{\Delta}\right).
$$

Every connected unlabeled (n=8) graph receives a distinct sorted QuIC readout. The independent gate-level implementation agrees with Qiskit to a worst-case discrepancy of:

$$
1.209\times10^{-15}.
$$

The exhaustive nearest-neighbor pass identifies a minimum candidate distance of:

$$
2.162\times10^{-5},
$$

and extended-precision recomputation gives:

$$
2.159\times10^{-5}.
$$

This exactly reproduces the earlier E16 / E17 separation scale while replacing its local candidate search with an exhaustive census-wide pass.

The correction also demonstrates why the invalid original E20 result could not be retained. Removing maximum-degree normalization enlarged the closest separation by approximately a factor of 151. The partition remained discrete, but the circuit geometry changed substantially.

The appropriate central claim is:

> Using the canonical maximum-degree-normalized encoder, the descending-sorted QuIC probability vector is numerically injective on the complete connected (n=8) graph census. All 11,117 graphs have distinct computed readouts, an independent gate-level implementation agrees with Qiskit to a worst-case (L_1) discrepancy of (1.209\times10^{-15}), and the 100 closest exhaustive-search candidates remain separated at 32-decimal-digit precision. The minimum identified separation is (2.159\times10^{-5}), reproducing the earlier E16 / E17 candidate value while providing a substantially stronger census-wide audit.


### E21 - Regularity Transfer

#### Experimental design

E21 tests whether QuIC’s cycle-decoding results are specific to cubic graphs or transfer to a different regular graph family.

The experiment uses three complete connected graph censuses:

* **509 connected 3-regular graphs at (n=14)**;
* **1,544 connected 4-regular graphs at (n=12)**;
* **11,117 connected graphs at (n=8)**, containing mixed degree sequences and regularities.

The two regular censuses provide the primary transfer comparison.

On every regular graph, the canonical normalized encoder:

$$
R_X\left(2.875\frac{d_i}{\Delta}\right)
$$

reduces to the same uniform rotation:

$$
R_X(2.875),
$$

because every vertex satisfies:

$$
d_i=\Delta.
$$

The cubic and 4-regular circuits therefore use the same initial product state. Their difference arises from the graph topology and regularity rather than from a change in the encoder values.

The mixed-degree (n=8) census provides an off-regularity comparison. On those graphs, the encoder uses genuinely heterogeneous rotations determined by each graph’s relative degree profile.

Two circuits are evaluated.

1. **QuIC**

   * normalized degree encoder;
   * edgewise (R_{ZZ}(2.0)) entanglers;
   * uniform (R_X(0.1)) mixer;
   * one entangler–mixer repetition.

2. **QAOA-style baseline**

   * (|+\rangle^{\otimes n}) preparation;
   * edgewise (R_{ZZ}(2.0)) entanglers;
   * uniform (R_X(0.1)) mixer.

Both circuits are decoded from their complete descending-sorted Born-probability vectors.

The representation dimensions are:

$$
2^8=256,\qquad2^{12}=4{,}096,\qquad2^{14}=16{,}384.
$$

Using complete vectors removes the unequal retained-mass issue that affected the truncated cross-circuit comparison in E18.

The targets are:

* triangle count ((C_3));
* 4-cycle count ((C_4));
* 5-cycle count ((C_5));
* 6-cycle count ((C_6));
* induced diamond count.

Each target is decoded using five shuffled outer folds and the standing nested ridge protocol:

$$
\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2}.
$$

The experiment asks two distinct questions.

1. Does the strong QuIC cycle accessibility observed on cubic graphs persist on a complete census of graphs with a different regularity?
2. Does QuIC retain an advantage over the same QAOA-style baseline across the regular and mixed-degree censuses?

#### Target definitions and certification

Cycle counts are computed directly by enumerating simple cycles through length six.

The triangle identity is verified on every graph:

$$
\text{tr}(A^3)=6C_3.
$$

For the cubic census, the notebook additionally verifies:

$$
\text{tr}(A^4)=8C_4+15n,
$$

$$
\text{tr}(A^5)=10C_5+10\text{tr}(A^3),
$$

and:

$$
\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).
$$

For the 4-regular census, it verifies:

$$
\text{tr}(A^4)=8C_4+28n,
$$

and:

$$
\text{tr}(A^5)=10C_5+90C_3.
$$

The 4-regular 6-cycle count is obtained directly from cycle enumeration. The notebook does not use a closed sixth-trace identity to certify that target.

For cubic graphs, diamonds are counted using the edge-hinge identity. For the 4-regular and mixed-degree censuses, the notebook uses an induced-diamond count that excludes (K_4) subgraphs by requiring the two common neighbors of the diamond spine to be nonadjacent.

#### Canonical-encoder correctness gate

The cubic QuIC row is compared with the independently recorded E2 results.

| Target | E21 QuIC | E2 reference | Absolute difference |
| ------ | -------: | -----------: | ------------------: |
| (C_3)  |    1.000 |        1.000 |               0.000 |
| (C_4)  |    0.998 |        0.998 |               0.000 |
| (C_5)  |    0.928 |        0.928 |               0.000 |
| (C_6)  |    0.485 |        0.485 |               0.000 |

All four values reproduce the E2 record at displayed precision.

This is an important validation because E18 and E19 accidentally used the unnormalized encoder:

$$
R_X(\alpha d_i).
$$

E21 instead uses:

$$
R_X\left(\alpha\frac{d_i}{\Delta}\right),
$$

and lands exactly on the canonical cubic results.

The transfer analysis can therefore be interpreted as a test of the canonical QuIC representation.

#### Complete results

| Census              | Circuit | (C_3) | (C_4) | (C_5) | (C_6) | Diamonds |
| ------------------- | ------- | ----: | ----: | ----: | ----: | -------: |
| (n=14), 3-regular   | QuIC    | 1.000 | 0.998 | 0.928 | 0.485 |    0.993 |
| (n=14), 3-regular   | QAOA    | 0.877 | 0.869 | 0.734 | 0.715 |    0.994 |
| (n=12), 4-regular   | QuIC    | 1.000 | 0.999 | 0.787 | 0.922 |    0.935 |
| (n=12), 4-regular   | QAOA    | 0.978 | 0.851 | 0.778 | 0.852 |    0.824 |
| (n=8), mixed degree | QuIC    | 0.007 | 0.018 | 0.025 | 0.031 |    0.002 |
| (n=8), mixed degree | QAOA    | 0.114 | 0.105 | 0.097 | 0.087 |    0.069 |

The corresponding QuIC-minus-QAOA differences are:

| Census              |    (C_3) |    (C_4) |    (C_5) |    (C_6) | Diamonds |
| ------------------- | -------: | -------: | -------: | -------: | -------: |
| (n=14), 3-regular   | (+0.123) | (+0.129) | (+0.194) | (-0.230) | (-0.001) |
| (n=12), 4-regular   | (+0.022) | (+0.148) | (+0.009) | (+0.070) | (+0.111) |
| (n=8), mixed degree | (-0.106) | (-0.086) | (-0.072) | (-0.056) | (-0.067) |

#### Transfer from 3-regular to 4-regular graphs

QuIC remains strongly predictive across the complete 4-regular census.

The 4-regular results are:

$$
R^2_{C_3}=1.000,\qquad R^2_{C_4}=0.999,\qquad R^2_{C_5}=0.787,\qquad R^2_{C_6}=0.922,\qquad R^2_D=0.935.
$$

All five targets remain substantially decodable.

This establishes that the canonical QuIC cycle signal is not confined to cubic graphs.

The strongest transfer occurs for the first two cycle counts.

##### Triangle count

Triangle count remains exact:

$$
1.000\rightarrow1.000.
$$

##### Four-cycle count

Four-cycle count also remains essentially exact:

$$
0.998\rightarrow0.999.
$$

These two results provide the cleanest evidence for cross-regularity stability.

##### Five-cycle count

Five-cycle accessibility remains strong but declines:

$$
0.928\rightarrow0.787.
$$

The difference is:

$$
-0.141.
$$

The 5-cycle layer therefore transfers qualitatively but not at the same strength.

##### Six-cycle count

Six-cycle accessibility changes in the opposite direction:

$$
0.485\rightarrow0.922.
$$

The improvement is:

$$
+0.437.
$$

The cubic result had suggested that 6-cycle information was the weakest tested cycle layer. That ordering does not persist on the 4-regular census.

##### Diamond count

Diamond prediction remains strong:

$$
0.993\rightarrow0.935.
$$

The decline is modest relative to the complete score range:

$$
-0.058.
$$

The broad conclusion is therefore stronger than cubic specificity but weaker than exact profile invariance.

> QuIC’s general cycle and diamond accessibility transfers to 4-regular graphs, but the relative strengths of the deeper targets change substantially.

#### The hierarchy does not transfer unchanged

The cubic sequence is:

$$
C_3\approx C_4>C_5>C_6.
$$

The 4-regular sequence is:

$$
C_3\approx C_4>D>C_6>C_5.
$$

The first two layers are stable, but the deeper ordering changes.

In particular:

* (C_5) becomes weaker;
* (C_6) becomes much stronger;
* diamonds remain strongly accessible.

E21 therefore does not establish one universal cycle-depth law shared by all regular graphs.

It establishes a more limited but useful result:

$$
\boxed{\text{strong cycle accessibility transfers across regularities, while the deeper target ordering is family dependent}}
$$

This distinction matters for the paper’s central characterization.

The cubic hierarchy remains a real property of the cubic censuses. E21 shows that it is embedded within a broader regular-graph phenomenon rather than defining the only possible regular-graph profile.

#### Mixed-degree census

QuIC falls to the prediction floor on the complete connected (n=8) census.

The scores are:

$$
R^2\in[0.002,0.031].
$$

The best target is 6-cycle count:

$$
R^2_{C_6}=0.031.
$$

Triangle, 4-cycle, 5-cycle, and diamond prediction are likewise negligible.

This collapse occurs despite:

* use of the complete 256-dimensional probability vector;
* explicit normalized degree encoding;
* over 11,000 training examples across the census.

The result cannot be attributed to truncating the probability tail or to an unusually small graph sample.

The same canonical circuit that nearly solves the first two cycle targets on both regular censuses provides essentially no linear accessibility on the mixed-degree census.

The contrast is large:

| Target   | 3-regular QuIC | 4-regular QuIC | Mixed-degree QuIC |
| -------- | -------------: | -------------: | ----------------: |
| (C_3)    |          1.000 |          1.000 |             0.007 |
| (C_4)    |          0.998 |          0.999 |             0.018 |
| (C_5)    |          0.928 |          0.787 |             0.025 |
| (C_6)    |          0.485 |          0.922 |             0.031 |
| Diamonds |          0.993 |          0.935 |             0.002 |

The experiment therefore reproduces the off-regularity failure under a substantially broader census than the four fixed-degree-sequence strata in E6.

The two experiments answer complementary questions:

* E6 holds graph order fixed at (n=14) and varies nonregular degree sequences;
* E21 uses exhaustive regular censuses and a complete mixed-degree census across graph orders.

Together they provide stronger evidence that the regular graph manifold is central to the observed QuIC geometry.

#### Why regularity matters to the encoder

On either regular census:

$$
\frac{d_i}{\Delta}=1
$$

for every vertex.

The canonical degree encoder therefore becomes uniform:

$$
R_X(2.875)^{\otimes n}.
$$

All graph-dependent information must then be introduced by the edge-entangler pattern and converted into probabilities by the mixer.

On the mixed-degree census, the encoder varies across vertices:

$$
R_X\left(2.875\frac{d_i}{\Delta}\right).
$$

The circuit must simultaneously represent:

* degree-role variation;
* edge topology;
* cycle structure;
* and graph-to-graph changes in the normalization scale (\Delta).

The result is consistent with the interpretation that uniform preparation creates a cleaner topology-only interference geometry, while heterogeneous local rotations entangle degree variation with the structural coordinates.

E21 does not prove that mechanism directly. It shows that the empirical distinction aligns sharply with regularity.

#### QuIC versus QAOA on the cubic census

On cubic graphs, QuIC is stronger for:

* triangles;
* 4-cycles;
* 5-cycles.

The margins are:

$$
+0.123,\qquad+0.129,\qquad+0.194.
$$

QAOA is stronger for 6-cycles:

$$
0.715>0.485.
$$

Diamond prediction is effectively tied:

$$
0.994\quad\text{versus}\quad0.993.
$$

The comparison shows that QuIC’s main cubic advantage lies in the first three cycle layers, especially (C_5).

It does not dominate the baseline on every invariant.

#### QuIC versus QAOA on the 4-regular census

QuIC exceeds QAOA on all five 4-regular targets.

| Target   |  QuIC |  QAOA | Difference |
| -------- | ----: | ----: | ---------: |
| (C_3)    | 1.000 | 0.978 |   (+0.022) |
| (C_4)    | 0.999 | 0.851 |   (+0.148) |
| (C_5)    | 0.787 | 0.778 |   (+0.009) |
| (C_6)    | 0.922 | 0.852 |   (+0.070) |
| Diamonds | 0.935 | 0.824 |   (+0.111) |

The largest differences occur for:

* 4-cycles;
* diamonds;
* 6-cycles.

The C5 difference is only:

$$
+0.009.
$$

QuIC and QAOA therefore provide nearly identical 5-cycle accessibility on this census.

The 4-regular experiment gives QuIC its broadest baseline advantage, but the magnitude remains target dependent.

#### QuIC versus QAOA on the mixed-degree census

QAOA exceeds QuIC on every mixed-degree target.

The QAOA scores remain modest:

$$
R^2\in[0.069,0.114].
$$

They are nevertheless consistently above the QuIC scores.

The differences range from:

$$
-0.056
$$

to:

$$
-0.106.
$$

QAOA’s uniform (|+\rangle^{\otimes n}) preparation appears more robust than QuIC’s heterogeneous degree-dependent preparation on this complete census, although neither circuit provides strong prediction.

This result reinforces the conclusion that QuIC’s degree encoder does not automatically help outside regular families.

#### Regularity transfer is not unique to QuIC

QAOA also performs substantially better on the two regular censuses than on the mixed-degree census.

For example:

$$
R^2_{C_3}=0.877\quad\text{and}\quad0.978
$$

on the regular censuses, compared with:

$$
R^2_{C_3}=0.114
$$

at (n=8).

Similarly, QAOA’s 4-cycle score is:

$$
0.869\quad\text{and}\quad0.851
$$

on the regular censuses, compared with:

$$
0.105
$$

on the mixed-degree census.

The regularity effect is therefore not unique to QuIC.

Both graph-dependent phase-and-mixer circuits produce much stronger cycle-aligned geometry on the regular censuses.

QuIC often provides the stronger representation within that regime, particularly for cubic (C_3)–(C_5) and 4-regular (C_4), (C_6), and diamonds.

The correct interpretation is comparative rather than exclusive:

> Regularity supports strong structural accessibility for both tested quantum circuit families, while QuIC changes which targets are most directly exposed.

#### What the experiment establishes

The completed results establish that:

1. **The notebook uses the correct canonical normalized QuIC encoder.**

   The cubic results exactly reproduce the independent E2 record.

2. **QuIC’s structural accessibility transfers from 3-regular to 4-regular graphs.**

   All five tested targets remain strongly decodable on the complete 4-regular census.

3. **Triangle and 4-cycle accessibility are the most stable cross-regularity results.**

   Both remain essentially exact.

4. **The deeper target profile is not universal.**

   Five-cycle prediction declines, while 6-cycle prediction becomes substantially stronger on the 4-regular census.

5. **Diamond accessibility also transfers.**

   It remains above (0.93) at both regularities.

6. **QuIC collapses on the complete mixed-degree (n=8) census.**

   Every target remains near the prediction floor despite full-vector decoding.

7. **The off-regularity collapse is not a truncation artifact.**

   The complete probability vectors are used for all circuits and graph orders.

8. **QuIC exceeds QAOA on all five 4-regular targets and on the first three cubic cycle targets.**

9. **QuIC does not universally dominate QAOA.**

   QAOA is stronger for cubic (C_6) and for every target on the mixed-degree census.

10. **Regularity also benefits the QAOA baseline.**

    The transfer effect is broader than the QuIC encoder alone.

E21 therefore extends the cubic result into a regular-graph characterization while rejecting a universal target-ordering claim.

#### Necessary qualifications

The three censuses differ in graph order as well as regularity.

The regular comparison uses:

* 3-regular graphs at (n=14);
* 4-regular graphs at (n=12).

The mixed-degree comparison uses:

* all connected graphs at (n=8).

The experiment therefore does not isolate regularity as the only changed variable.

The fixed-order E6 experiments provide the complementary control showing off-regularity degradation at (n=14).

The complete (n=8) census is a mixed census rather than a census containing only nonregular graphs. It includes graphs with many different degree sequences and also includes some regular graphs.

Its near-zero aggregate score demonstrates failure across the complete heterogeneous collection, not failure on every individual regularity stratum within that collection.

A stricter transfer design would compare:

* 3-regular and 4-regular graphs at the same order;
* or multiple regularities across several common graph orders.

The census sizes also differ substantially:

$$
509,\qquad1{,}544,\qquad11{,}117.
$$

The larger mixed-degree sample does not rescue QuIC performance, but sample size remains another difference among the experiments.

The 4-regular (C_6) target is computed directly but not certified through a closed trace identity in the notebook.

The induced-diamond routine is mathematically designed to exclude (K_4) subgraphs, but the notebook does not execute a separate brute-force assertion over all four-vertex subsets during this run.

The final output reports mean outer-fold (R^2) values but does not print the stored fold standard deviations.

No paired statistical tests compare:

* regularities;
* circuits;
* or target-specific score differences.

Small differences such as the 4-regular C5 margin of:

$$
0.009
$$

should therefore be treated as descriptive ties.

The full-vector models operate in strongly high-dimensional regimes. E10 showed that QuIC ridge probes can rely on very small regularization values and low-variance feature directions.

E21 does not repeat the shuffled-target or solver-agreement audits for the new 4-regular census.

The experiment evaluates linear accessibility rather than information content in the strict sense. A low ridge score does not prove that the mixed-degree vectors contain no cycle information.

The QAOA and QuIC circuits are compared at one shared fixed angle schedule. The schedule may favor one circuit differently across graph families.

All results use exact ideal probabilities. They do not establish finite-shot or hardware-accessible transfer.

Finally, the transfer result concerns one regular graph order per regularity. It supports a regular-graph hypothesis but does not yet establish a general theorem across all (d)-regular graph families.

#### Overall assessment

E21 supplies the missing regularity-transfer experiment.

The canonical QuIC circuit reproduces the established cubic results exactly and remains strongly informative on the complete 4-regular (n=12) census:

$$
R^2=1.000,\quad0.999,\quad0.787,\quad0.922,\quad0.935
$$

for triangles, 4-cycles, 5-cycles, 6-cycles, and diamonds.

The result rules out the narrow interpretation that QuIC’s structural accessibility is a peculiarity of cubic graphs.

The transfer is not an exact replication of the cubic hierarchy. Triangle and 4-cycle prediction remain saturated, but C5 becomes weaker and C6 becomes substantially stronger. The broader regular-graph phenomenon is stable cycle accessibility, not one universal ordering of cycle lengths.

The complete mixed-degree (n=8) census provides the sharp contrast. QuIC remains near the prediction floor for every target despite full-vector decoding and more than 11,000 graph examples.

The QAOA baseline sharpens the conclusion. It also benefits strongly from regularity, showing that the effect is not unique to QuIC. QuIC nevertheless provides the stronger representation for the first three cubic cycle targets and for every tested 4-regular target.

The appropriate central claim is:

> QuIC’s strong structural accessibility transfers beyond cubic graphs to the complete connected 4-regular (n=12) census. Triangle and 4-cycle counts remain essentially exact, while 5-cycle, 6-cycle, and diamond counts remain strongly decodable, although their relative ordering changes across regularities. The same canonical circuit collapses on the complete mixed-degree (n=8) census even under full-vector decoding. Regularity therefore appears to support the organized probability geometry, but it does not impose one universal cycle hierarchy. A QAOA-style baseline shows the same broad regularity dependence, while QuIC provides stronger target-specific accessibility within the regular regime.


### E22 - Readout Geometry and Partial Spectral Complementarity Audit

#### Experimental scope

E22 studies two related properties of the QuIC representation across three complete graph censuses.

1. **Similarity geometry**

   Does distance between readout vectors track distance between graph structures?

2. **Classical complementarity**

   Does a circuit representation improve prediction after a nonlinear spectral model has already explained the target?

The experiment uses:

| Census | Graph family            | Graphs | Readout dimension |
| ------ | ----------------------- | -----: | ----------------: |
| (n=14) | Connected cubic         |    509 |            16,384 |
| (n=12) | Connected 4-regular     |  1,544 |             4,096 |
| (n=8)  | Connected heterogeneous | 11,117 |               256 |

The shared producer successfully completed all three censuses.

E22A completed its full three-census similarity analysis.

E22B completed:

* all five targets at (n=14);
* all five targets at (n=12).

It did not complete:

* any reported (n=8) target;
* its stated E11 validation cell;
* artifact persistence;
* or the final results cell.

The available E22B record is therefore the supplied runtime log rather than a saved result artifact.

---

#### Shared circuit representations

The producer computes two descending-sorted exact Born-probability vectors.

##### QuIC

The canonical normalized degree encoder is:

$$R_X\left(2.875\frac{d_i}{\Delta}\right).$$

It is followed by:

* one edgewise $$R_{ZZ}(2.0)$$ layer;
* one uniform $$R_X(0.1)$$ mixer;
* one repetition.

##### QAOA-style baseline

The second circuit begins from:

$$|+\rangle^{\otimes n},$$

followed by the same:

* edgewise $$R_{ZZ}(2.0)$$ layer;
* uniform $$R_X(0.1)$$ mixer.

Both circuits retain the complete sorted probability vector.

The producer stores the readouts as float32 matrices after constructing them through Qiskit statevectors.

---

#### Targets

The shared target set is:

* triangle count $$C_3$$;
* 4-cycle count $$C_4$$;
* 5-cycle count $$C_5$$;
* 6-cycle count $$C_6$$;
* diamond count.

For the cubic census, diamond count is the edge-hinge count:

$$D=#{uv\in E:|N(u)\cap N(v)|=2}.$$

For the noncubic censuses, the producer counts induced diamonds by requiring the two common neighbors of the spine edge to be nonadjacent.

---

#### Target certification

The cubic census satisfies:

$$\text{tr}(A^3)=6C_3,$$

$$\text{tr}(A^4)=8C_4+15n,$$

$$\text{tr}(A^5)=10C_5+10\text{tr}(A^3),$$

and:

$$\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).$$

The 4-regular census satisfies:

$$\text{tr}(A^3)=6C_3,$$

$$\text{tr}(A^4)=8C_4+28n,$$

and:

$$\text{tr}(A^5)=10C_5+90C_3.$$

The 4-regular $$C_6$$ target is counted directly and is not trace certified in this notebook.

The producer’s heterogeneous certification string says that no trace certification is performed. The code nevertheless verifies:

$$\text{tr}(A^3)=6C_3$$

for every census, including (n=8). The printed description is therefore slightly stale.

---

#### Canonical QuIC correctness gate

The producer verifies the cubic QuIC representation against the independent E2 record.

| Target  | E22 producer | E2 record | Difference |
| ------- | -----------: | --------: | ---------: |
| $$C_3$$ |        1.000 |     1.000 |      0.000 |
| $$C_4$$ |        0.998 |     0.998 |      0.000 |
| $$C_5$$ |        0.926 |     0.928 |   (-0.002) |
| $$C_6$$ |        0.489 |     0.485 |   (+0.004) |

The gate passes.

The shared readouts therefore use the corrected canonical normalized encoder rather than the invalid unnormalized circuit from the original E18–E20 runs.

---

## E22A - Similarity Geometry

#### Primary structural distance

E22A defines its primary graph distance as the Euclidean distance between complete sorted adjacency spectra:

$$d_{\text{spec}}(G,H)=|\lambda(G)-\lambda(H)|_2.$$

The readout distance used in the global analysis is:

$$d_{\text{readout}}(G,H)=|\mathbf p(G)-\mathbf p(H)|_1.$$

For each census, 6,000 graph pairs are sampled with replacement. Self-pairs are removed.

The primary statistic is the Spearman correlation:

$$\rho_{\text{spec}}=\rho_{\text{S}}\left(d_{\text{readout}},d_{\text{spec}}\right).$$

This measures monotone agreement with **spectral geometry**. It is not a general graph-edit or combinatorial similarity metric.

---

#### Global spectral-distance fidelity

| Census              | QuIC spectral $$\rho$$ | QAOA spectral $$\rho$$ |
| ------------------- | ---------------------: | ---------------------: |
| (n=14) cubic        |                  0.641 |                  0.560 |
| (n=12) 4-regular    |                  0.768 |                  0.677 |
| (n=8) heterogeneous |                  0.065 |                  0.207 |

The regular censuses show moderate to strong global monotone alignment between readout and spectral distances.

QuIC exceeds QAOA on both regular families:

$$0.641>0.560,$$

and:

$$0.768>0.677.$$

The heterogeneous census behaves differently.

QuIC’s spectral-distance correlation falls to:

$$0.065.$$

QAOA remains weak but reaches:

$$0.207.$$

The principal E22A result is therefore a regularity-dependent spectral geometry:

> QuIC globally tracks adjacency-spectrum distance on regular graph families but not on the complete heterogeneous census.

This agrees with E21’s regularity-transfer result for supervised structural accessibility.

It also shows that the regularity dependence is not exclusive to QuIC. QAOA’s spectral geometry weakens substantially at (n=8), although less completely.

---

#### Secondary target-distance correlations

For each target $$t$$, E22A computes:

$$d_t(G,H)=|t(G)-t(H)|,$$

and reports:

$$\rho_t=\rho_{\text{S}}\left(d_{\text{readout}},d_t\right).$$

##### QuIC

| Census              | $$C_3$$ | $$C_5$$ | Diamonds |
| ------------------- | ------: | ------: | -------: |
| (n=14) cubic        |   0.907 |   0.093 |    0.452 |
| (n=12) 4-regular    |   0.903 |   0.429 |    0.578 |
| (n=8) heterogeneous |   0.034 |   0.070 |    0.028 |

##### QAOA

| Census              | $$C_3$$ | $$C_5$$ | Diamonds |
| ------------------- | ------: | ------: | -------: |
| (n=14) cubic        |   0.463 |   0.206 |    0.783 |
| (n=12) 4-regular    |   0.691 |   0.344 |    0.674 |
| (n=8) heterogeneous |   0.075 |   0.055 |    0.016 |

---

#### QuIC target geometry

QuIC’s regular-graph geometry is dominated by triangle differences:

$$\rho_{C_3}=0.907\quad\text{at }n=14,$$

and:

$$\rho_{C_3}=0.903\quad\text{at }n=12.$$

This reproduces the strong triangle ordering observed in E16 and E17.

Five-cycle distance is much less aligned on the cubic census:

$$\rho_{C_5}=0.093.$$

It becomes more visible on the 4-regular census:

$$\rho_{C_5}=0.429.$$

Diamond-distance alignment is intermediate:

$$0.452\quad\text{and}\quad0.578.$$

On the heterogeneous census, all three target correlations are approximately zero.

This is consistent with the weak mixed-degree decodability found in E18, E21, and E23.

---

#### QAOA target geometry

QAOA has a different structural orientation.

On the cubic census, its strongest reported target-distance alignment is diamonds:

$$\rho_D=0.783.$$

This exceeds its triangle correlation:

$$\rho_{C_3}=0.463.$$

The same ordering appears at (n=12):

$$\rho_D=0.674,\qquad\rho_{C_3}=0.691,$$

with the two values much closer.

QAOA’s global geometry is therefore more diamond aligned than QuIC’s on the cubic family, even though the partial E22B residual analysis suggests that QuIC adds more predictive diamond information beyond the tested classical baseline.

These results are not contradictory.

Pairwise-distance correlation measures global geometric ordering. Residual prediction measures whether a fitted model extracts target variation missed by another fitted model.

---

#### What the valid E22A global analysis establishes

The completed global-distance analysis establishes that:

1. **QuIC readout distance moderately tracks spectral distance on cubic graphs.**

2. **The alignment becomes stronger on the complete 4-regular census.**

3. **QuIC’s spectral-distance geometry collapses on the heterogeneous census.**

4. **QAOA shows the same broad regularity dependence, but retains a weak heterogeneous spectral correlation.**

5. **QuIC’s regular-graph geometry is strongly aligned with triangle differences.**

6. **QAOA’s cubic geometry is more strongly aligned with diamond differences.**

7. **Neither circuit’s heterogeneous geometry is meaningfully aligned with the three tested target distances.**

These are global monotone-geometry statements. They do not establish nearest-neighbor preservation.

---

## E22A Local-Fidelity Audit

#### Intended local statistic

E22A attempts to measure local geometry using the overlap between:

* the ten nearest spectral neighbors;
* the ten nearest readout neighbors.

For each query graph:

$$O_{10}(G)=\frac{|N_{10}^{\text{spec}}(G)\cap N_{10}^{\text{readout}}(G)|}{10}.$$

The notebook reports:

| Census              | QuIC reported overlap | QAOA reported overlap |
| ------------------- | --------------------: | --------------------: |
| (n=14) cubic        |                 0.272 |                 0.299 |
| (n=12) 4-regular    |                 0.200 |                 0.215 |
| (n=8) heterogeneous |                 0.112 |                 0.105 |

These values are not valid because the self-match exclusion is implemented incorrectly.

---

#### Self-indexing bug

The query graphs are selected through:

```python
query_indices = rng.choice(census_size, size=..., replace=False)
```

The distance matrix row at local position $$i$$ therefore corresponds to global graph index:

$$\texttt{query_indices}[i].$$

The nearest-neighbor function instead excludes:

```python
start + local_index
```

which is the query’s local row position, not its global graph index.

The correct exclusion is:

```python
query_indices[start + local_index]
```

or an explicitly supplied global self-index array.

As written, the true zero-distance self-match remains in almost every neighbor list.

For the exact sampled queries:

* 507 of 509 cubic queries retain their self-match;
* all 1,000 4-regular queries retain their self-match;
* all 1,000 heterogeneous queries retain their self-match.

Because the self graph appears in both the spectral and readout neighbor lists, it contributes an automatic overlap of:

$$\frac{1}{10}=0.1$$

for almost every query.

This is particularly consequential at (n=8), where the reported values are only:

$$0.112\quad\text{and}\quad0.105.$$

Almost the entire reported heterogeneous overlap can be explained by the erroneous shared self-match.

The function also excludes an unrelated reference graph whose global index happens to equal the query row position. Removing the self-match afterward is therefore not equivalent to simply subtracting 0.1 from the reported means.

---

#### Local metric inconsistency

The global analysis uses readout $$L_1$$ distance.

The local function calls `scipy.spatial.distance.cdist` without specifying a metric, so it uses Euclidean distance:

$$L_2.$$

This is not necessarily wrong, but it means the global and local analyses do not measure the same readout geometry.

The notebook describes the two as complementary global and local views without emphasizing the metric change.

A corrected rerun should either:

* use $$L_1$$ for both;
* or explicitly present the local $$L_2$$ analysis as a different metric.

---

#### Status of the coarse-versus-local claim

The notebook proposes the interpretation:

> Moderate global Spearman correlation combined with low local overlap means the representation preserves coarse ordering while scrambling fine neighborhoods.

That interpretation may ultimately be correct.

The current local outputs cannot support it.

The local-neighbor analysis must be rerun with correct self-index exclusion before any fine-neighborhood conclusion is included in the paper.

---

## E22B - Partial Complementarity Analysis

#### Intended question

E22B asks whether QuIC or QAOA adds predictive information after a nonlinear spectral model has already explained the target.

The spectral feature bank contains:

1. all adjacency eigenvalues except the largest;
2. trace moments:

$$\text{tr}(A^k),\qquad k=3,\ldots,8.$$

For regular censuses, the largest eigenvalue is constant and can be omitted without information loss.

The circuit residual stage uses the first:

$$k=1000$$

sorted probabilities.

---

#### Intended two-stage protocol

Within each outer fold:

1. fit a classical spectral model;
2. obtain cross-fitted classical residuals on the outer-training set;
3. train a ridge probe from the circuit readout to those residuals;
4. predict the residual on the outer-test set;
5. add the residual prediction to the classical prediction.

For classical prediction $$\widehat y_{\text{classical}}$$ and circuit residual prediction $$\widehat r_{\text{circuit}}$$:

$$\widehat y_{\text{combined}}=\widehat y_{\text{classical}}+\widehat r_{\text{circuit}}.$$

The complementarity statistic is:

$$\Delta R^2=R^2_{\text{combined}}-R^2_{\text{classical}}.$$

A positive value means that the circuit residual stage improves the selected classical prediction under that evaluation procedure.

---

#### Classical models

The notebook evaluates:

* RBF kernel ridge;
* ExtraTrees regression.

The RBF hyperparameters are selected inside the training data over:

$$\alpha\in{10^{-6},\ldots,10^2},$$

and:

$$\gamma\in{10^{-3},\ldots,10^1}.$$

ExtraTrees uses:

* 300 trees;
* default tree depth;
* default minimum leaf size.

This is not the exact E11 nonlinear protocol.

E11 used:

* a narrower RBF alpha grid;
* three-fold rather than five-fold RBF grid selection;
* a tuned ExtraTrees grid over depth and minimum leaf size.

E22B should therefore be described as an E11-inspired spectral-residual analysis, not an exact reuse of E11.

---

#### Completed partial results

The supplied log contains complete result rows for:

* five targets at (n=14);
* five targets at (n=12).

No completed (n=8) result is available.

The main printed columns are:

* an oracle-selected classical score;
* QuIC’s reported delta over the selected model;
* QAOA’s reported delta over the selected model;
* QuIC’s separately computed delta over RBF.

##### (n=14) cubic

| Target   | Reported classical |          QuIC delta |          QAOA delta | QuIC-over-RBF delta |
| -------- | -----------------: | ------------------: | ------------------: | ------------------: |
| $$C_3$$  |              1.000 | approximately 0.000 | approximately 0.000 | approximately 0.000 |
| $$C_4$$  |              1.000 |               0.000 | approximately 0.000 |               0.000 |
| $$C_5$$  |              1.000 |               0.000 |               0.000 |               0.000 |
| $$C_6$$  |              0.991 |               0.003 |               0.001 |               0.003 |
| Diamonds |              0.874 |               0.073 |               0.041 |               0.072 |

##### (n=12) 4-regular

| Target   | Reported classical |          QuIC delta |          QAOA delta | QuIC-over-RBF delta |
| -------- | -----------------: | ------------------: | ------------------: | ------------------: |
| $$C_3$$  |              1.000 | approximately 0.000 | approximately 0.000 | approximately 0.000 |
| $$C_4$$  |              1.000 |               0.000 |               0.000 |               0.000 |
| $$C_5$$  |              1.000 |               0.000 |               0.000 |               0.000 |
| $$C_6$$  |              0.971 |               0.019 |               0.007 |               0.019 |
| Diamonds |              0.770 |               0.076 |               0.032 |               0.093 |

---

#### Exact spectral targets

The classical score is exactly one at displayed precision for:

$$C_3,\qquad C_4,\qquad C_5$$

on both regular censuses.

This is expected.

The spectral feature bank explicitly contains the required trace moments.

For cubic graphs:

$$C_3=\frac{\text{tr}(A^3)}{6},$$

$$C_4=\frac{\text{tr}(A^4)-15n}{8},$$

and:

$$C_5=\frac{\text{tr}(A^5)-10\text{tr}(A^3)}{10}.$$

For 4-regular graphs:

$$C_4=\frac{\text{tr}(A^4)-28n}{8},$$

and:

$$C_5=\frac{\text{tr}(A^5)-90C_3}{10}.$$

There is no residual information for either circuit to add after these exact moments are included.

The zero deltas are therefore a useful machinery control rather than evidence that the circuits lack those quantities.

---

#### Cubic $$C_6$$ and diamond split

For cubic graphs:

$$\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).$$

The spectrum determines:

$$C_6+D,$$

but does not generally determine the split between the two quantities.

The partial E22B results reflect this structure.

The nonlinear classical baseline nearly solves $$C_6$$:

$$R^2_{\text{classical}}=0.991.$$

Only a small residual remains:

$$\Delta R^2_{\text{QuIC}}=0.003.$$

Diamond count leaves substantially more room:

$$R^2_{\text{classical}}=0.874.$$

The reported QuIC residual increases the mean score by:

$$0.073.$$

The corresponding QAOA increase is:

$$0.041.$$

Under the separately fixed RBF baseline, QuIC’s delta is:

$$0.072.$$

This is the cleanest completed E22B result.

---

#### Four-regular results

The same broad pattern appears at (n=12).

The nonlinear spectral models nearly solve $$C_6$$:

$$R^2_{\text{classical}}=0.971.$$

QuIC adds:

$$0.019,$$

while QAOA adds:

$$0.007.$$

Diamond count leaves more unexplained variation:

$$R^2_{\text{classical}}=0.770.$$

The reported deltas are:

$$\Delta R^2_{\text{QuIC}}=0.076,$$

and:

$$\Delta R^2_{\text{QAOA}}=0.032.$$

Against the fixed RBF baseline, QuIC adds:

$$0.093.$$

The repeated result across two regular families is descriptive evidence that diamond variation contains a circuit-accessible component not captured by the tested RBF spectral model.

---

#### QuIC versus QAOA

For the two nonsaturated targets, QuIC has the larger reported residual gain on both censuses.

| Census | Target   | QuIC delta | QAOA delta |
| ------ | -------- | ---------: | ---------: |
| (n=14) | $$C_6$$  |      0.003 |      0.001 |
| (n=14) | Diamonds |      0.073 |      0.041 |
| (n=12) | $$C_6$$  |      0.019 |      0.007 |
| (n=12) | Diamonds |      0.076 |      0.032 |

The diamond difference is consistent:

$$0.073>0.041,$$

and:

$$0.076>0.032.$$

This suggests that QuIC’s residual diamond coordinate is stronger than QAOA’s under the tested setup.

The result remains descriptive because:

* no fold-level standard deviations are printed;
* no paired test is performed;
* and the selected-baseline procedure uses outer-test outcomes.

---

## Critical E22B Protocol Audit

#### Outer-test model-selection leakage

The notebook documentation says that the stronger classical model is selected by training cross-validation.

The code instead computes both models’ outer-test scores:

```python
rbf_test = r2_score(y_test, rbf.predict(X_test))
trees_test = r2_score(y_test, trees.predict(X_test))
classical_test = max(rbf_test, trees_test)
strong_fitter = fit_rbf if rbf_test >= trees_test else fit_extra_trees
```

The held-out test targets are therefore used to decide:

* which model becomes the classical baseline;
* which model generates the training residuals;
* which model supplies the test prediction used in the combined estimator.

This violates the intended outer-fold separation.

The reported `classical_r2`, `quic_delta`, and `qaoa_delta` columns are not clean held-out model-selection results.

The classical score is an oracle maximum over two test-evaluated models.

The residual model is also conditioned on which classical arm happened to score better on the test fold.

These columns can be reported descriptively, but they should not be used as the paper’s definitive complementarity estimates.

A corrected run should select the classical arm using only:

* inner training-fold performance;
* or a prespecified fixed baseline.

---

#### RBF-specific QuIC column is cleaner

The `quic_rbf_delta` column does not use the oracle model choice.

It always uses the RBF fitter.

Its hyperparameters are selected from training data, and its training residuals are cross fitted.

The completed RBF-specific QuIC deltas are therefore the most defensible E22B outputs:

| Census           | $$C_6$$ | Diamonds |
| ---------------- | ------: | -------: |
| (n=14) cubic     |   0.003 |    0.072 |
| (n=12) 4-regular |   0.019 |    0.093 |

These results support a limited statement:

> QuIC improves diamond prediction beyond the particular training-selected RBF spectral model on both completed regular censuses.

The corresponding RBF-alone scores were not printed in the supplied log, so the final combined RBF scores cannot be reconstructed from the available record.

---

#### The stated E11 gate did not execute

The notebook places its E11 validation in a later cell.

Because the long main grid stopped before that cell, the gate did not run.

The notebook therefore did not produce the claimed:

```text
E11 correctness gate PASSED
```

message.

The observed cubic diamond value:

$$\Delta R^2_{\text{QuIC over RBF}}=0.072$$

can be compared with the E11 value:

$$0.099.$$

The difference is:

$$0.027.$$

That lies within the notebook’s loose tolerance of:

$$0.05.$$

However, the two notebooks do not use identical RBF grids or inner validation protocols.

The result should not be described as an exact E11 reproduction.

It is directionally consistent with E11.

---

#### Incomplete regularity comparison

E22B was designed to compare:

* cubic graphs;
* 4-regular graphs;
* heterogeneous graphs.

The heterogeneous stage did not produce a completed target row.

Consequently, E22B cannot answer its intended transfer question:

> Does circuit complementarity beyond nonlinear spectral models survive outside regular graph families?

E22A shows that the heterogeneous distance geometry is weak.

E21 shows that heterogeneous supervised decodability is weak.

Those results do not substitute for the missing E22B residual analysis.

No (n=8) complementarity claim should be inferred.

---

#### No saved partial artifact

The persistence cell occurs after the complete three-census loop.

Because execution stopped during the loop, no completed E22B pickle was written.

The supplied console log is the only record of the partial results.

The per-fold values and fitted predictions are unavailable.

This prevents:

* fold-level uncertainty analysis;
* paired error bootstrapping;
* reconstruction of RBF-alone scores;
* or recovery of partially completed unprinted (n=8) work.

---

#### What the completed E22 results establish

The valid completed outputs establish that:

1. **The shared producer uses canonical normalized QuIC readouts.**

2. **QuIC’s global readout distance moderately tracks spectral distance on cubic and 4-regular censuses.**

3. **That global spectral geometry nearly disappears on the complete heterogeneous census.**

4. **QuIC’s regular-graph distance geometry is especially aligned with triangle differences.**

5. **QAOA’s cubic distance geometry is strongly aligned with diamond differences.**

6. **The E22A local-neighborhood values are invalid because self-matches were not correctly removed.**

7. **The nonlinear spectral feature bank exactly saturates $$C_3$$, $$C_4$$, and $$C_5$$ on both regular censuses.**

8. **Little residual room remains for $$C_6$$.**

9. **Diamond count retains a repeatable QuIC-accessible RBF residual.**

   The completed deltas are:

   $$0.072\quad\text{at }n=14,$$

   and:

   $$0.093\quad\text{at }n=12.$$

10. **The oracle-selected descriptive rows show larger QuIC than QAOA diamond gains on both regular censuses.**

11. **E22B does not provide a heterogeneous complementarity result.**

12. **E22B’s primary selected-baseline columns are affected by outer-test model-selection leakage.**

E22 therefore supplies a valid global geometry result and partial regular-family complementarity evidence, but not a complete local-geometry or three-census complementarity audit.

---

#### Necessary qualifications

The primary E22A metric is adjacency-spectrum distance.

Calling it “structural distance” without qualification is too broad.

Cospectral nonisomorphic graphs have zero spectral distance regardless of potentially substantial combinatorial differences.

The analysis measures alignment with spectral geometry.

The global Spearman results use one sample of approximately 6,000 pairs per census.

No:

* confidence interval;
* repeated pair sample;
* or permutation null

is reported.

Pairs are sampled with replacement, so some graph pairs may appear more than once.

This is unlikely to change the large qualitative regular-versus-heterogeneous contrast, but the observations are not all independent.

The target-distance correlations contain many tied distances, especially for integer motif counts.

Spearman correlation handles ties, but its effective resolution differs among targets.

The readout matrices are stored as float32.

The large global correlations are unlikely to depend on this precision choice, but very small distance distinctions may be altered.

The E22A local analysis uses Euclidean readout distance rather than the global $$L_1$$ metric and contains the more serious self-index bug.

It should be discarded until rerun.

The E22B spectral feature bank contains redundant information:

* reduced eigenvalues;
* trace moments computed from the same spectrum.

This is intentional for nonlinear modeling but should not be described as combining independent classical information sources.

For regular graphs, the trace features directly encode several targets. Their perfect results are algebraic rather than learned discoveries.

The E22B oracle baseline is selected separately within every outer test fold.

This makes its baseline scores optimistic and invalidates a strict held-out interpretation of the corresponding deltas.

The separately fixed RBF QuIC deltas avoid that particular model-selection leak but still use an E22-specific RBF grid rather than the exact E11 model.

No clean RBF-specific QAOA column is recorded.

The QuIC-versus-QAOA residual comparison therefore relies on the leaky selected-baseline columns.

No inference or uncertainty estimate accompanies the complementarity differences.

The 4-regular diamond target is induced diamond count, while the cubic implementation uses the hinge identity. These coincide in the relevant cubic family but the computational definitions differ.

The (n=8) target counts are direct counts, and its diamond statistic can have different distributional behavior from the regular censuses.

All circuit results use ideal complete probability vectors.

E22 does not test whether the reported global geometry or residual diamond coordinate survives finite-shot sampling.

Finally, similarity correlation and supervised complementarity answer different questions.

A target can have strong pairwise distance alignment but weak residual predictive gain, or the reverse.

---

#### Overall assessment

E22A supplies a useful global geometry result.

QuIC’s readout distance tracks adjacency-spectrum distance at:

$$\rho=0.641$$

on cubic graphs and:

$$\rho=0.768$$

on 4-regular graphs, but only:

$$\rho=0.065$$

on the heterogeneous census.

Its distance geometry is strongly triangle aligned on both regular families.

QAOA shows weaker regular spectral alignment but stronger cubic diamond-distance alignment.

The intended local-neighborhood result is not usable. An indexing error retains the zero-distance query graph in nearly every neighbor set and automatically contributes approximately 0.1 overlap.

E22B provides a partial but coherent regular-family pattern.

The spectral feature bank algebraically solves $$C_3$$ through $$C_5$$, nearly solves $$C_6$$, and leaves diamond count as the principal unresolved target.

Against a fixed RBF spectral model, QuIC adds:

$$\Delta R^2=0.072$$

for cubic diamonds and:

$$\Delta R^2=0.093$$

for 4-regular diamonds.

Those are the strongest defensible E22B outputs.

The broader selected-baseline columns are contaminated by outer-test model selection, and the notebook did not reach (n=8), its validation gate, or persistence.

The appropriate central claim is:

> QuIC’s full readout geometry globally tracks adjacency-spectrum distance on complete cubic and 4-regular censuses but not on the complete heterogeneous census, with particularly strong alignment to triangle differences on the regular families. The attempted local-neighborhood analysis is invalid because self-matches were not correctly excluded. In the partial complementarity run, spectral trace features exactly determine triangles through 5-cycles and nearly determine 6-cycles, while diamond count retains a repeatable QuIC-accessible residual beyond the tested RBF spectral model: (0.072) at (n=14) and (0.093) at (n=12). The run does not establish heterogeneous complementarity, and its oracle-selected classical comparison must be corrected before QuIC-versus-QAOA residual claims are treated as definitive.

### E23 - Invariantization by Sorting

#### Experimental design

E23 compares four ways of converting the same canonical QuIC circuit into a graph representation.

The experiment uses two complete graph censuses:

* **509 connected cubic graphs at (n=14)**;
* **11,117 connected graphs at (n=8)**.

The circuit uses the corrected canonical encoder:

$$R_X\left(2.875\frac{d_i}{\Delta}\right),$$

followed by:

* edgewise (R_{ZZ}(2.0)) entanglers;
* a uniform (R_X(0.1)) mixer;
* one entangler–mixer repetition.

For each graph, the circuit first produces the raw computational-basis probability vector:

$$\mathbf p(G)\in\mathbb R^{2^n}.$$

The four readout constructions are:

1. **Canonical raw**

   The graph is placed in a nauty canonical labeling before the circuit is built. The unsorted probability vector is then retained with its computational-basis coordinates.

2. **Random-label raw**

   Each graph is independently relabeled before the circuit is built. The raw probability coordinates are retained without alignment across graphs.

   Five independently seeded relabeling replicates are evaluated.

3. **Hamming-weight pooling**

   Raw probabilities are aggregated over basis states with equal Hamming weight:

   $$h_w(G)=\sum_{z:,|z|=w}p_G(z),\qquad w=0,\ldots,n.$$

   This produces an invariant vector of dimension:

   $$n+1.$$

4. **Descending sort**

   The full probability vector is sorted:

   $$\mathbf q(G)=\text{sort}_{\downarrow}\mathbf p(G).$$

   The experiment evaluates:

   * the complete sorted vector;
   * the first 100 probabilities;
   * the first 1,000 probabilities.

At (n=8), the complete vector has only 256 entries, so the 1,000-coordinate arm is identical to the full representation.

#### Targets

The cubic census uses:

* triangle count;
* 4-cycle count;
* 5-cycle count;
* diamond count;
* girth.

The complete heterogeneous census uses:

* triangle count;
* 4-cycle count;
* vertex connectivity;
* Wiener index.

Each target is decoded using five shuffled outer folds and the standing nested ridge grid:

$$\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2}.$$

The experiment also evaluates:

* 12-decimal rounded distinctness;
* sampled pairwise-distance correlations with canonical raw;
* mean random-label performance across five relabeling replicates.

#### Information content versus linear accessibility

Canonical raw and sorted full are not equal representations, but sorted full is a deterministic many-to-one function of canonical raw:

$$\mathbf q(G)=\text{sort}*{\downarrow}\mathbf p*{\text{canon}}(G).$$

Sorting discards the association between probabilities and computational-basis strings.

It therefore cannot increase information in an unrestricted information-theoretic sense.

It can, however, increase performance under a restricted decoder. Sorting is nonlinear, while the downstream probe is linear. The transformation can reorganize information into coordinates that are substantially easier for ridge regression to use.

This distinction is essential to interpreting E23.

Canonical raw is an information-preserving reference, but it is not an upper bound on linear (R^2).

#### Census construction and completion

Both representation banks complete successfully:

| Census          | Graphs | Raw-vector dimension | Targets                              |
| --------------- | -----: | -------------------: | ------------------------------------ |
| Cubic (n=14)    |    509 |               16,384 | (C_3), (C_4), (C_5), diamonds, girth |
| Connected (n=8) | 11,117 |                  256 | (C_3), (C_4), connectivity, Wiener   |

No code cell terminates with an error.

The corrected canonical encoder is used consistently in every arm.

The sorted cubic results reproduce the established canonical QuIC record:

$$R^2_{C_3}=1.000,\qquad R^2_{C_4}=0.998,\qquad R^2_{C_5}=0.928,$$

$$R^2_D=0.993,\qquad R^2_{\text{girth}}=0.993.$$

The sorted heterogeneous results also reproduce the corrected E18 and E21 values:

$$R^2_{C_3}=0.007,\qquad R^2_{C_4}=0.018,\qquad R^2_{\kappa}=0.123.$$

These cross-experiment matches provide a strong implementation check.

#### Distinctness

Every representation is distinct on every graph at 12-decimal rounding precision.

| Census          | Canonical raw |   Sorted full | Hamming pooling | Random-label replicate 0 |
| --------------- | ------------: | ------------: | --------------: | -----------------------: |
| Cubic (n=14)    |       509/509 |       509/509 |         509/509 |                  509/509 |
| Connected (n=8) | 11,117/11,117 | 11,117/11,117 |   11,117/11,117 |            11,117/11,117 |

The Hamming-weight result contradicts the notebook’s anticipated collision-collapse story.

Even the nine-dimensional (n=8) Hamming representation distinguishes all 11,117 graphs at the tested numerical precision.

This is not mathematically paradoxical. A low-dimensional continuous representation can assign distinct values to arbitrarily many members of a finite set.

The result establishes:

$$\boxed{\text{low dimension does not imply finite-census collisions}}$$

Hamming pooling may still discard useful geometry or make targets less linearly accessible, but it does not collapse either tested census into repeated vectors.

Distinctness alone therefore does not distinguish the invariantization methods.

#### Cubic decodability results

| Target   | Canonical raw | Sorted full | Sorted 100 | Sorted 1,000 | Hamming pooling | Random-label mean |
| -------- | ------------: | ----------: | ---------: | -----------: | --------------: | ----------------: |
| (C_3)    |         0.990 |       1.000 |      1.000 |        1.000 |           1.000 |             0.986 |
| (C_4)    |         0.344 |       0.998 |      0.993 |        0.998 |           1.000 |          (-0.011) |
| (C_5)    |         0.158 |       0.928 |      0.272 |        0.928 |           0.750 |          (-0.013) |
| Diamonds |         0.573 |       0.993 |      0.990 |        0.993 |           1.000 |             0.240 |
| Girth    |         0.313 |       0.993 |      0.987 |        0.993 |           0.385 |             0.112 |

Sorting produces large improvements over canonical raw for four of the five cubic targets.

| Target   | Sorted minus canonical raw |
| -------- | -------------------------: |
| (C_3)    |                   (+0.010) |
| (C_4)    |                   (+0.654) |
| (C_5)    |                   (+0.770) |
| Diamonds |                   (+0.420) |
| Girth    |                   (+0.680) |

The full sorted representation therefore does not merely retain canonical-raw linear accessibility. It creates a much more target-aligned coordinate system.

#### Canonical raw on cubic graphs

Canonical raw remains nearly exact for triangle count:

$$R^2_{C_3}=0.990.$$

Its performance is much weaker for:

$$R^2_{C_4}=0.344,$$

$$R^2_{C_5}=0.158,$$

$$R^2_D=0.573,$$

and:

$$R^2_{\text{girth}}=0.313.$$

Canonical graph labeling makes the raw vector invariant, but the computational-basis coordinates are not necessarily structurally aligned across different graphs.

A basis state with a particular binary index refers to vertices selected by the canonical labeling. Canonical vertex identities can change discontinuously as graph structure changes.

Canonicalization therefore solves label invariance without necessarily producing a smooth or linearly useful cross-graph coordinate system.

#### Sorting on cubic graphs

Sorting removes bitstring identities and retains only the probability order statistics.

The resulting representation nearly solves every tested cubic target.

The strongest improvements occur for:

* 4-cycles;
* 5-cycles;
* girth.

The result supports a rank-geometry interpretation:

> On cubic graphs, the structural signal is more consistently organized by probability magnitude than by canonical computational-basis identity.

Sorting acts as a nonlinear alignment mechanism. Large probabilities with related structural roles are placed into corresponding ranks even when their associated bitstrings differ among graphs.

This is stronger than a claim that sorting preserves the raw geometry. It shows that sorting replaces the raw coordinate geometry with a much more linearly target-aligned one.

#### Hamming pooling on cubic graphs

Hamming-weight pooling performs substantially better than the notebook’s anticipated “destructive averaging” baseline.

It reaches:

$$R^2_{C_3}=1.000,\qquad R^2_{C_4}=1.000,\qquad R^2_D=1.000.$$

It also reaches:

$$R^2_{C_5}=0.750.$$

Its main failure is girth:

$$R^2_{\text{girth}}=0.385.$$

The comparison with sorting is:

| Target   | Sorted full | Hamming pooling | Sorted minus Hamming |
| -------- | ----------: | --------------: | -------------------: |
| (C_3)    |       1.000 |           1.000 |                0.000 |
| (C_4)    |       0.998 |           1.000 |             (-0.002) |
| (C_5)    |       0.928 |           0.750 |             (+0.178) |
| Diamonds |       0.993 |           1.000 |             (-0.007) |
| Girth    |       0.993 |           0.385 |             (+0.608) |

Sorting is not necessary for triangles, 4-cycles, or diamonds under this decoder.

Its clearest advantage appears for:

* 5-cycles;
* girth.

The proper conclusion is therefore target specific.

Hamming pooling preserves substantial shallow and local motif information but loses much of the finer structure needed for girth and part of the 5-cycle signal.

#### Random-label raw on cubic graphs

Random relabeling preserves triangle accessibility:

$$R^2_{C_3}=0.986.$$

It destroys most accessibility for:

$$C_4,\qquad C_5,$$

where the mean scores are approximately zero.

Diamond count retains a modest signal:

$$R^2_D=0.240,$$

and girth remains weak:

$$R^2_{\text{girth}}=0.112.$$

The result shows that unaligned raw coordinates are unusable for several deeper targets.

It does not show that random-label raw is universally at the floor.

Triangle count remains nearly exact, indicating that some structural directions are encoded through permutation-insensitive aggregate behavior even before explicit invariantization.

The notebook computes standard deviations across the five random-label replicates but does not print them. Its prose claim of “large replicate spread” is therefore not supported by the visible record.

#### Sorted-head depth on cubic graphs

The first 100 sorted probabilities are sufficient for:

$$C_3,\qquad C_4,\qquad D,\qquad\text{girth}.$$

The corresponding scores are:

$$1.000,\qquad0.993,\qquad0.990,\qquad0.987.$$

Five-cycle count behaves differently:

$$R^2_{C_5}=0.272\quad\text{at }k=100,$$

and:

$$R^2_{C_5}=0.928\quad\text{at }k=1000.$$

This reproduces the rank-depth hierarchy established in E7 and E13.

The shallow head already carries triangles, 4-cycles, diamonds, and girth, while 5-cycle accessibility requires substantially deeper probability ranks.

#### Heterogeneous-census decodability results

| Target       | Canonical raw | Sorted full | Sorted 100 | Sorted 1,000 | Hamming pooling | Random-label mean |
| ------------ | ------------: | ----------: | ---------: | -----------: | --------------: | ----------------: |
| (C_3)        |         0.273 |       0.007 |      0.007 |        0.007 |           0.117 |             0.110 |
| (C_4)        |         0.217 |       0.018 |      0.018 |        0.018 |           0.183 |             0.177 |
| Connectivity |         0.778 |       0.123 |      0.092 |        0.123 |           0.353 |             0.346 |
| Wiener index |         0.314 |       0.000 |      0.000 |        0.000 |           0.191 |             0.171 |

The heterogeneous result reverses the cubic ordering.

Canonical raw is strongest for every target.

Sorting loses most of the canonical-raw linear accessibility:

| Target       | Sorted minus canonical raw |
| ------------ | -------------------------: |
| (C_3)        |                   (-0.266) |
| (C_4)        |                   (-0.199) |
| Connectivity |                   (-0.655) |
| Wiener index |                   (-0.314) |

The complete sorted vector remains near the prediction floor.

This agrees with E18 and E21: canonical sorted QuIC does not produce a useful global cycle geometry on the complete mixed-degree census.

#### Canonical raw on heterogeneous graphs

Canonical raw retains moderate information for:

* triangles;
* 4-cycles;
* Wiener index.

It is particularly strong for connectivity:

$$R^2_{\kappa}=0.778.$$

This shows that the canonical probability vector contains linearly accessible heterogeneous-graph information that sorting removes.

The result is not inconsistent with sorted-vector injectivity.

Every sorted vector remains distinct, but distinctness does not guarantee target alignment.

The raw bitstring identities appear to carry information about degree roles and connectivity that is lost when probabilities are reduced to their ordered multiset.

#### Hamming pooling on heterogeneous graphs

Hamming pooling exceeds sorting for every tested target:

| Target       | Sorted full | Hamming pooling |
| ------------ | ----------: | --------------: |
| (C_3)        |       0.007 |           0.117 |
| (C_4)        |       0.018 |           0.183 |
| Connectivity |       0.123 |           0.353 |
| Wiener index |       0.000 |           0.191 |

The Hamming representation remains weaker than canonical raw, but it preserves considerably more of the useful heterogeneous-graph signal than sorting.

This directly contradicts the notebook’s expected ordering:

$$\text{canonical raw}\approx\text{sorted}\gg\text{Hamming}.$$

The observed heterogeneous ordering is:

$$\text{canonical raw}>\text{Hamming}\approx\text{random label}>\text{sorted}.$$

The result suggests that total excitation-weight structure tracks degree heterogeneity, connectivity, and distance-related variation more effectively than rank statistics do.

#### Random-label raw on heterogeneous graphs

Random-label raw closely tracks Hamming pooling:

$$R^2_{C_3}=0.110,$$

$$R^2_{C_4}=0.177,$$

$$R^2_{\kappa}=0.346,$$

$$R^2_{\text{Wiener}}=0.171.$$

The raw coordinates are not aligned across graphs, but graph-level aggregate effects remain visible.

The similarity between random-label raw and Hamming pooling suggests that a substantial portion of their usable signal may arise from permutation-insensitive or approximately aggregate distributional structure.

This is a descriptive interpretation. The notebook does not decompose the random-label representation into invariant and non-invariant components.

#### The proposed invariantization ratio

The notebook defines:

$$\eta_y=\frac{R^2_{\text{sorted},y}}{R^2_{\text{canonical},y}}.$$

The reported values are:

##### Cubic census

| Target   | (\eta_y) |
| -------- | -------: |
| (C_3)    |    1.010 |
| (C_4)    |    2.904 |
| (C_5)    |    5.866 |
| Diamonds |    1.731 |
| Girth    |    3.175 |

##### Heterogeneous census

| Target       | (\eta_y) |
| ------------ | -------: |
| (C_3)        |    0.027 |
| (C_4)        |    0.085 |
| Connectivity |    0.158 |
| Wiener index |    0.001 |

These values cannot be interpreted as the fraction of information or geometry preserved by sorting.

A preservation fraction should not generally exceed one, while the cubic ratios reach:

$$5.866.$$

The ratio instead compares linear-probe performance in two different coordinate systems.

A more accurate name is:

$$\text{relative linear accessibility ratio}.$$

Even under that name, the ratio can become unstable when the denominator is small or negative. Differences in (R^2) are easier to interpret.

E23 should not call (\eta_y) the “cost of invariantization.”

#### Pairwise geometry

The experiment samples 4,000 graph pairs and computes the Spearman correlation between each arm’s pairwise (L_1) distances and canonical-raw pairwise distances.

| Census          | Sorted full | Hamming pooling | Random-label replicate 0 |
| --------------- | ----------: | --------------: | -----------------------: |
| Cubic (n=14)    |       0.128 |           0.098 |                 (-0.007) |
| Connected (n=8) |       0.474 |           0.862 |                    0.485 |

The cubic sorted representation has only weak correlation with canonical-raw geometry:

$$\rho=0.128.$$

The sorted representation therefore does not preserve most of the canonical pairwise-distance ordering.

Its near-perfect target decoding arises despite this large geometric reorganization.

At (n=8), sorting preserves a moderate amount of the canonical distance ordering:

$$\rho=0.474.$$

Hamming pooling preserves much more:

$$\rho=0.862.$$

Random-label replicate zero also slightly exceeds sorting:

$$0.485>0.474.$$

The geometry results reject the notebook’s intended interpretation that sorting closely tracks canonical raw while Hamming pooling destroys its geometry.

The more accurate conclusion is:

> Sorting creates a different geometry whose usefulness is highly graph-family and target dependent.

#### Reconciling decodability and geometry

The cubic results show:

* weak global geometric correlation with canonical raw;
* much stronger linear decoding after sorting.

These findings are compatible.

A representation can substantially change global pairwise distances while aligning a small number of target-relevant directions.

Sorting appears to suppress basis-state identity and concentrate recurring structural probability patterns into comparable ranks.

The result is not geometric preservation. It is geometric reorganization.

On the heterogeneous census, that same reorganization removes useful degree-role and connectivity information, causing sorted decoding to collapse.

E23 therefore identifies regularity as a boundary condition for the usefulness of the sorted quotient.

#### Relationship to E16, E20, and E21

E16 and corrected E20 establish that sorted QuIC is:

* permutation invariant;
* numerically injective on the complete connected (n=8) census;
* numerically injective on the cubic (n=14) census.

E23 adds that injectivity does not determine the quality of the representation geometry.

At (n=8):

* sorted QuIC distinguishes every graph;
* yet it predicts none of the tested targets well.

At (n=14):

* sorted QuIC distinguishes every graph;
* and its rank geometry nearly solves the tested structural targets.

E21 showed that the strong sorted geometry transfers to 4-regular graphs but not to the mixed-degree census.

E23 clarifies the mechanism empirically:

* canonical raw retains heterogeneous degree-role information;
* sorting removes coordinate identities;
* the removal is beneficial on regular graphs and destructive on heterogeneous graphs.

#### What the experiment establishes

The completed results establish that:

1. **All four readout constructions distinguish every graph in both tested censuses at 12-decimal precision.**

   Hamming pooling does not produce the expected finite-census collisions.

2. **Sorting substantially improves linear structural accessibility on cubic graphs.**

   It raises (C_4), (C_5), diamond, and girth scores by approximately (0.42) to (0.77) relative to canonical raw.

3. **The cubic gain is not caused by preserving canonical-raw pairwise geometry.**

   The sampled distance correlation is only (0.128).

4. **Sorting acts as a nonlinear target-aligning transformation.**

5. **Hamming pooling retains substantial cubic information.**

   It exactly predicts triangles, 4-cycles, and diamonds and reaches (0.750) on 5-cycles.

6. **Sorting’s clearest cubic advantages over Hamming pooling are 5-cycle count and girth.**

7. **The first 100 sorted probabilities already carry triangles, 4-cycles, diamonds, and girth.**

   Five-cycle accessibility requires a deeper head.

8. **Sorting sharply degrades linear accessibility on the heterogeneous census.**

   Canonical raw is stronger on every tested target.

9. **Hamming pooling and random-label raw both outperform sorting on the heterogeneous census.**

10. **Sorted-vector injectivity and target-aligned geometry are separate properties.**

11. **The proposed (\eta_y) ratio is not a cost or preservation fraction.**

12. **Sorting is effective within the regular-graph regime but is not a universally superior invariantization method.**

#### Necessary qualifications

Canonical raw is obtained through an external classical graph-canonicalization procedure.

E23 does not measure the runtime, memory, or scaling cost of nauty canonicalization relative to sorting.

No empirical efficiency claim is supported.

Sorting itself operates on a vector of size:

$$2^n,$$

and therefore also inherits the exponential readout dimension.

The experiment compares representational geometry, not end-to-end computational efficiency.

The notebook prose states that canonicalization was verified under relabeling, but no explicit relabel-and-assert validation cell appears in the recorded run.

The correctness of canonical raw relies on the behavior of `nauty-labelg` and the deterministic graph6 conversion.

Sorted and Hamming-weight readouts are invariant because a vertex relabeling induces a qubit permutation, and both probability sorting and Hamming-weight aggregation remove that permutation. This relies on the underlying circuit being permutation equivariant.

The distinctness test uses 12-decimal rounded fingerprints. It establishes no observed numerical collisions, not symbolic injectivity.

The random-label results are means across only five relabeling replicates.

The notebook calculates replicate standard deviations but does not print or persist them in the visible summary table. Claims about large or small replicate variation cannot be verified from the attached output.

The canonical, sorted, and random raw feature spaces are highly dimensional relative to the cubic sample size:

$$509\text{ graphs versus }16{,}384\text{ features}.$$

The ridge fits emit many ill-conditioned-matrix warnings.

E10 showed that some QuIC probes depend on low-variance directions and extremely weak regularization. E23 does not repeat the independent solver and shuffled-target audits.

The large qualitative contrasts are unlikely to be explained entirely by numerical variation, but exact values should retain the established ridge-probe qualification.

The geometry analysis uses only 4,000 randomly sampled graph pairs.

It estimates global distance-order preservation but does not provide uncertainty intervals or repeat the sample under multiple seeds.

Spearman correlation with canonical raw is only one geometry criterion. A low value does not imply that all local or target-specific neighborhoods are lost.

The target sets differ between the two censuses. Cross-census comparisons are therefore partly target dependent.

The graph orders also differ:

* cubic regular graphs at (n=14);
* heterogeneous connected graphs at (n=8).

E6 provides the same-order evidence that nonregularity degrades the sorted hierarchy at (n=14), while E21 provides transfer to another regular census.

Hamming pooling’s perfect distinctness should not be generalized beyond these finite censuses or parameters.

The experiment evaluates ideal statevector probabilities. It does not establish whether the invariantization contrasts survive finite-shot sampling.

Finally, “sorting is necessary” is not supported.

Hamming pooling equals or exceeds sorting on several cubic targets and outperforms it on every heterogeneous target.

The supported conclusion is that sorting is particularly effective for selected regular-graph structural coordinates.

#### Overall assessment

E23 is scientifically useful, but it does not support the story written into its final notebook cell.

Sorting is not a nearly free invariant quotient that preserves most of canonical-raw geometry. On the cubic census, its pairwise-distance correlation with canonical raw is only:

$$0.128.$$

Instead, sorting performs a strong nonlinear reorganization.

That reorganization raises 5-cycle prediction from:

$$0.158$$

to:

$$0.928,$$

and girth prediction from:

$$0.313$$

to:

$$0.993.$$

It also raises 4-cycle and diamond accessibility substantially.

Hamming-weight pooling proves stronger than anticipated. It remains collision free on both censuses and exactly predicts cubic triangles, 4-cycles, and diamonds. Sorting’s clearest advantages over this natural linear invariant are the deeper 5-cycle signal and girth.

The heterogeneous census provides the critical counterexample. Canonical raw retains substantial connectivity and metric information, while sorting collapses nearly to the prediction floor. Hamming pooling and even randomly relabeled raw vectors preserve more linear accessibility.

The experiment therefore strengthens a narrower and more interesting interpretation:

> Sorting is not simply an inexpensive substitute for canonical labeling. It is a nonlinear rank transform that discards basis-state identities and constructs a new probability geometry. On regular cubic graphs, that geometry strongly aligns with cycle, diamond, and girth structure, particularly for deeper rank-dependent targets. On the heterogeneous census, the same quotient removes useful degree-role and connectivity information and performs worse than canonical raw or Hamming-weight pooling. Sorting is therefore a powerful regular-graph structural readout, not a universally information-preserving invariantization procedure.


### E24 - Folklore 2-WL Baseline

#### Experimental design

E24 compares QuIC with folklore 2-dimensional Weisfeiler–Leman refinement on the exact adjacency-cospectral graph classes identified at:

* **(n=18)**;
* **471 exact cospectral groups**;
* **958 total members**.

The experiment has three components.

1. **E24 producer**

   Computes folklore 2-WL representations for all 958 members of the exact cospectral groups and carries forward the existing QuIC representations from E14.

2. **E24a ranking**

   Compares QuIC and folklore 2-WL on held-out ranking of:

   * Wiener index;
   * automorphism-group order.

3. **E24b witnesses**

   Compares their ability to:

   * distinguish the six exact cospectral diamond and 6-cycle witnesses;
   * rank the diamond direction under leave-one-witness-out evaluation.

The experiment addresses a narrower question than whether QuIC contains information beyond the adjacency spectrum.

E14 already established that the relevant graph properties vary within exact adjacency-cospectral classes. E24 asks whether that non-spectral structure is also accessible to a strong classical higher-order refinement.

#### Input data

The producer reuses the validated E14 artifact.

The complete connected cubic census contains:

$$41{,}301$$

graphs, from which the exact spectral partition contains:

$$471\text{ groups and }958\text{ members}.$$

Full QuIC probability vectors are available for:

$$906=625\text{ qualifying members}+281\text{ control members}.$$

These members cover:

$$445$$

of the 471 exact cospectral groups.

The qualifying set contains every group varying in:

* diamond count;
* Wiener index;
* automorphism-group order.

Consequently, QuIC is available for every member used in the E24 ranking and witness experiments, although it is not available for all 471 groups in the census-wide expressivity table.

The QuIC representation used by E24 is the first:

$$k=100$$

coordinates of the canonical descending-sorted probability vector.

#### Integrity checks

The producer repeats the E14 validation gates.

The stored graph invariants satisfy:

$$\text{tr}(A^3)=6C_3,$$

$$\text{tr}(A^4)=8C_4+15n,$$

$$\text{tr}(A^5)=10C_5+10\text{tr}(A^3),$$

and:

$$\text{tr}(A^6)=87n+6C_3+96C_4+12(C_6+D).$$

The 471 exact cospectral groups are independently reconstructed from integer trace tuples and match the E14 record.

The varying-group sets are also reproduced:

| Invariant    | Varying exact cospectral groups |    |    |
| ------------ | ------------------------------: | -- | -- |
| Diamonds     |                               6 |    |    |
| 6-cycles     |                               6 |    |    |
| 7-cycles     |                              18 |    |    |
| Wiener index |                             283 |    |    |
| Radius       |                              75 |    |    |
| Diameter     |                              53 |    |    |
| $$\log_2     |                   \text{Aut}(G) | $$ | 90 |

All 958 cospectral members are reconstructed from their graph6 strings.

The full graph-invariant suite is recomputed for the 906 members represented in the E14 artifact and matches the stored values.

Three QuIC vectors are independently rebuilt through Qiskit. Their worst coordinate discrepancy is below:

$$10^{-12}.$$

The folklore 2-WL analysis therefore operates on the same validated graph classes and targets as E14 and E14N.

#### Folklore 2-WL construction

The representation is folklore 2-WL on ordered vertex pairs.

The initial pair colors distinguish:

* diagonal pairs;
* edges;
* nonedges.

For each ordered pair ((u,v)), one refinement round replaces its color with a content-addressed digest of:

* its previous color;
* the sorted multiset of color pairs:

$${(c(u,w),c(w,v)):w\in V}.$$

The implementation uses 128-bit BLAKE2b digests rather than Python’s process-dependent `hash()` function.

Every graph is refined synchronously. A common structural signature therefore receives the same digest across different graphs.

Two graph representations are retained.

1. **Stable folklore 2-WL**

   Uses only the histogram from the final refining round.

2. **Cumulative folklore 2-WL**

   Concatenates the normalized color histograms from every stored refinement round.

The cumulative representation preserves the path by which the stable partition is reached rather than retaining only the final partition.

#### Refinement behavior

The full 958-member refinement stabilizes after round four.

| Round | Global distinct colors |
| ----: | ---------------------: |
|     0 |                      3 |
|     1 |                      8 |
|     2 |                  1,497 |
|     3 |                250,232 |
|     4 |                262,375 |

The next refinement produces no increase in the number of color classes, so round four is retained as the stable representation.

The complete sparse representation contains:

$$639{,}485$$

nonzero member-round entries.

No pair of members within one exact cospectral group has the same cumulative folklore 2-WL fingerprint.

The producer therefore finds:

$$0$$

within-group cumulative ties.

Because there are no ties, the planned 256-bit recheck has no candidate collisions to reevaluate.

#### Census-level expressivity

| Representation           | Exact cospectral groups fully separated | Groups evaluated |
| ------------------------ | --------------------------------------: | ---------------: |
| Stable folklore 2-WL     |                                     471 |              471 |
| Cumulative folklore 2-WL |                                     471 |              471 |
| QuIC top-100             |                                     445 |              445 |

Both folklore 2-WL representations distinguish every member within every one of the 471 exact cospectral groups.

QuIC also distinguishes every evaluated group using only its first 100 probabilities.

The coverage differs.

Folklore 2-WL is evaluated on:

$$471/471$$

groups.

QuIC is evaluated on:

$$445/471$$

groups because full QuIC vectors were not produced for the remaining 26 groups.

The result therefore establishes perfect separation for each representation over its available coverage. It does not establish a complete 471-group QuIC comparison.

Among the 445 commonly covered groups, both QuIC and folklore 2-WL fully separate every group.

#### Expressivity does not imply inductive ranking

The stable folklore 2-WL histogram distinguishes every cospectral group, but this does not mean that its color coordinates transfer across unrelated groups.

At stabilization, many colors describe highly graph-specific structural signatures. A final-round color appearing only in a held-out graph has no corresponding coefficient in a model whose vocabulary was constructed from training graphs.

E24a therefore builds the folklore 2-WL feature vocabulary from the training partition only.

Test-only colors are discarded and receive implicit weight zero.

This inductive protocol separates two questions:

* whether the representation distinguishes graphs when both are available;
* whether shared coordinates support a ranking rule that transfers to unseen cospectral groups.

The stable and cumulative representations behave very differently under this distinction.

#### Held-out ranking protocol

The ranking targets are:

* Wiener index across 283 varying exact cospectral groups;
* $$\log_2|\text{Aut}(G)|$$ across 90 varying exact cospectral groups.

Every relevant member has both:

* a QuIC top-100 vector;
* folklore 2-WL histogram blocks.

Four representations are compared:

1. QuIC top-100;
2. stable folklore 2-WL;
3. cumulative folklore 2-WL;
4. QuIC top-100 concatenated with cumulative folklore 2-WL.

The deterministic group partition from E14N is reused.

| Target       |   Partition 0 | Partition 1 |           |           |
| ------------ | ------------: | ----------: | --------- | --------- |
| Wiener index |    131 groups |  152 groups |           |           |
| $$\log_2     | \text{Aut}(G) |          $$ | 40 groups | 50 groups |

Both directions are evaluated:

* train on partition 0 and test on partition 1;
* train on partition 1 and test on partition 0.

No graph from a test cospectral group appears in the corresponding training set.

#### Ranking model

For each unequal-target pair ((G_i,G_j)), the feature is the representation difference:

$$\mathbf x_{ij}=\phi(G_i)-\phi(G_j).$$

The label is:

$$y_{ij}=\text{sign}(t(G_i)-t(G_j)).$$

The model is:

* intercept-free logistic regression;
* (L_2) regularization;
* dual-form `liblinear`;
* fixed (C=1);
* both pair orientations included.

For concatenation, QuIC and folklore 2-WL are independently scaled by their training-set pairwise root-mean-square block energies.

The same scaling procedure is also applied to each standalone representation.

The primary score is group-balanced accuracy:

$$A_{\text{group}}=\frac{1}{|\mathcal G_{\text{test}}|}\sum_{g\in\mathcal G_{\text{test}}}A_g.$$

Each exact cospectral group therefore receives equal weight.

The null permutes target assignments within each held-out group while keeping the fitted decision margins fixed.

Each direction uses:

$$100{,}000$$

permutation draws.

The add-one resolution is:

$$\frac{1}{100{,}001}\approx10^{-5}.$$

The two directional values are summarized by:

$$p_{\text{Bonferroni}}=2\min(p_A,p_B).$$

This is an omnibus test for evidence in at least one direction. It is not, by itself, a test of replication across both directions.

#### Null calibration

The fixed-margin permutation procedure is tested on synthetic group data.

* Perfectly aligned margins reach the permutation floor.
* Independent noise produces approximately uniform (p)-values.

The validation passes the notebook’s prespecified tolerances.

#### Wiener-index ranking

| Representation            | Train 0, test 1 | Permutation (p) | Train 1, test 0 | Permutation (p) | Bonferroni (p) |
| ------------------------- | --------------: | --------------: | --------------: | --------------: | -------------: |
| QuIC top-100              |           0.533 |          0.2070 |           0.551 |          0.1237 |         0.2473 |
| Stable folklore 2-WL      |           0.000 |          1.0000 |           0.000 |          1.0000 |         1.0000 |
| Cumulative folklore 2-WL  |           0.817 |       (<0.0001) |           0.837 |       (<0.0001) |      (<0.0001) |
| QuIC plus cumulative 2-WL |           0.800 |       (<0.0001) |           0.830 |       (<0.0001) |      (<0.0001) |

Cumulative folklore 2-WL strongly ranks Wiener index in both directions.

Its group-balanced accuracies are:

$$0.817\quad\text{and}\quad0.837.$$

Both results lie far beyond their within-group permutation nulls.

QuIC performs only modestly above chance:

$$0.533\quad\text{and}\quad0.551,$$

and neither direction is significant under the E24 model configuration.

The concatenated representation also ranks Wiener index strongly, but it does not improve upon cumulative folklore 2-WL:

$$0.800<0.817,$$

and:

$$0.830<0.837.$$

The primary classical baseline is therefore substantially stronger than QuIC on this target.

#### Stable folklore 2-WL on Wiener index

Stable folklore 2-WL obtains:

$$0.000$$

in both directions.

This should not be interpreted as inverse ranking.

The scoring rule treats a zero decision margin as a failure. Under the inductive vocabulary, final-round colors are sufficiently graph specific that the held-out stable histograms provide no usable shared coordinates to the trained model.

The result therefore means:

> The stable histogram is maximally discriminative when graphs are compared directly, but its final color identities do not support transferable ranking under the train-only vocabulary.

The cumulative representation succeeds because the earlier refinement rounds retain shared structural coordinates across graph groups.

#### Wiener error overlap

A group is counted as correct in the overlap table only when every unequal pair in that group is correctly ranked.

| Outcome                               | Groups |
| ------------------------------------- | -----: |
| QuIC and cumulative 2-WL both correct |    131 |
| QuIC only                             |     18 |
| Cumulative 2-WL only                  |    100 |
| Neither                               |     34 |

The categories sum to:

$$283$$

Wiener-varying groups.

QuIC and cumulative folklore 2-WL do not make identical errors.

QuIC uniquely solves 18 groups, while cumulative folklore 2-WL uniquely solves 100.

The concatenated model correctly handles 102 groups belonging to one of the two exclusive-success categories.

This demonstrates representational complementarity at the level of individual groups.

It does not demonstrate an aggregate concatenation advantage. The concatenated mean accuracy remains slightly below cumulative folklore 2-WL.

#### Wiener aggregate comparison

Combining each group’s held-out result across the two split directions gives:

| Representation            | Mean group-balanced accuracy |
| ------------------------- | ---------------------------: |
| QuIC                      |                        0.541 |
| Cumulative folklore 2-WL  |                        0.827 |
| QuIC plus cumulative 2-WL |                        0.814 |

The bootstrap interval for:

$$T_{\text{QuIC}}-T_{\text{2WL}}$$

is:

$$[-0.352,-0.218].$$

The interval lies entirely below zero.

Cumulative folklore 2-WL therefore has a clear aggregate advantage over QuIC under the E24 ranking protocol.

The bootstrap interval for:

$$T_{\text{concat}}-\max(T_{\text{QuIC}},T_{\text{2WL}})$$

is:

$$[-0.042,0.015].$$

This interval contains zero.

The experiment provides no evidence that simple concatenation improves upon the stronger cumulative folklore 2-WL baseline.

#### Automorphism-order ranking

| Representation            | Train 0, test 1 | Permutation (p) | Train 1, test 0 | Permutation (p) | Bonferroni (p) |
| ------------------------- | --------------: | --------------: | --------------: | --------------: | -------------: |
| QuIC top-100              |           0.660 |          0.0144 |           0.425 |          0.8392 |         0.0288 |
| Stable folklore 2-WL      |           0.000 |          1.0000 |           0.000 |          1.0000 |         1.0000 |
| Cumulative folklore 2-WL  |           0.700 |          0.0030 |           0.604 |          0.0956 |         0.0061 |
| QuIC plus cumulative 2-WL |           0.700 |          0.0027 |           0.629 |          0.0519 |         0.0054 |

The automorphism result is split asymmetric for every informative representation.

##### QuIC

One direction reaches:

$$A_{\text{group}}=0.660,\qquad p=0.0144.$$

The reverse direction falls below chance:

$$A_{\text{group}}=0.425,\qquad p=0.8392.$$

The Bonferroni omnibus value is:

$$p=0.0288.$$

This establishes evidence in one prespecified direction, not replication across both halves.

##### Cumulative folklore 2-WL

One direction reaches:

$$A_{\text{group}}=0.700,\qquad p=0.0030.$$

The reverse direction reaches:

$$A_{\text{group}}=0.604,\qquad p=0.0956.$$

The reverse effect is positive but does not meet a conventional (0.05) threshold.

##### Concatenated representation

The concatenated model obtains:

$$0.700,\qquad p=0.0027$$

in one direction and:

$$0.629,\qquad p=0.0519$$

in the other.

The reverse value narrowly misses (0.05), but it remains nonsignificant under that threshold.

The notebook’s `same_direction_replication` flag checks only whether both observed accuracies exceed their null means. That condition is not sufficient to establish inferential replication.

The appropriate conclusion is that cumulative folklore 2-WL and the concatenated representation show strong one-direction evidence with weaker reverse-direction support.

#### Automorphism error overlap

| Outcome                               | Groups |
| ------------------------------------- | -----: |
| QuIC and cumulative 2-WL both correct |     38 |
| QuIC only                             |     12 |
| Cumulative 2-WL only                  |     20 |
| Neither                               |     20 |

The categories sum to:

$$90$$

automorphism-varying groups.

The concatenated representation recovers 19 groups from the two exclusive-success categories.

As with Wiener index, the overlap shows that QuIC and folklore 2-WL are not structurally identical.

#### Automorphism aggregate comparison

| Representation            | Mean group-balanced accuracy |
| ------------------------- | ---------------------------: |
| QuIC                      |                        0.556 |
| Cumulative folklore 2-WL  |                        0.657 |
| QuIC plus cumulative 2-WL |                        0.669 |

The bootstrap interval for:

$$T_{\text{QuIC}}-T_{\text{2WL}}$$

is:

$$[-0.220,0.022].$$

The interval includes zero.

The experiment therefore does not establish a reliable aggregate difference between QuIC and cumulative folklore 2-WL for automorphism order.

The concatenated model has the highest point estimate:

$$0.669.$$

However, the interval for:

$$T_{\text{concat}}-\max(T_{\text{QuIC}},T_{\text{2WL}})$$

is:

$$[-0.033,0.056].$$

This interval also includes zero.

The point estimate is compatible with complementarity, but the experiment does not establish that concatenation improves aggregate held-out ranking.

#### Diamond and 6-cycle witnesses

E24b evaluates the six exact adjacency-cospectral pairs that exchange one diamond for one 6-cycle.

Within each pair:

$$|\Delta D|=1,\qquad\Delta C_6=-\Delta D.$$

Because the complete spectrum fixes:

$$C_6+D,$$

diamond ranking and 6-cycle ranking are the same directional problem with reversed labels.

All six witness pairs are distinguished by:

* stable folklore 2-WL;
* cumulative folklore 2-WL;
* QuIC top-100.

| Representation           | Witness pairs separated |
| ------------------------ | ----------------------: |
| Stable folklore 2-WL     |                     6/6 |
| Cumulative folklore 2-WL |                     6/6 |
| QuIC top-100             |                     6/6 |

The direct witnesses are therefore not difficult for folklore 2-WL.

They establish information beyond the adjacency spectrum, but not information beyond this higher-order classical representation.

#### Leave-one-witness-out diamond ranking

For each of the six witness pairs:

1. five pairs are used to train the antisymmetric ranker;
2. the sixth pair is held out;
3. the model predicts which member carries the diamond.

The folklore 2-WL vocabulary is rebuilt from the five training witnesses in each fold.

The exact null enumerates all:

$$2^6=64$$

possible assignments of diamond directions across the six groups.

Unlike E14’s add-one permutation value, E24b reports the exhaustive tail frequency directly.

| Representation            | Correct witnesses | Exact null mean | Exact (p) |
| ------------------------- | ----------------: | --------------: | --------: |
| QuIC top-100              |               6/6 |             3.0 |   0.03125 |
| Cumulative folklore 2-WL  |               6/6 |             3.0 |   0.03125 |
| QuIC plus cumulative 2-WL |               6/6 |             3.0 |   0.03125 |

Every representation correctly ranks all six held-out witness pairs.

The exact tail contains two of the 64 possible direction assignments, giving:

$$p=\frac{2}{64}=0.03125.$$

The result is stronger numerically than the conservative E14 add-one value:

$$p=\frac{3}{65}=0.0462,$$

but it represents the same six-pair evidence.

Cumulative folklore 2-WL exactly matches QuIC on the direct diamond witness task.

Concatenation cannot improve on the saturated:

$$6/6$$

result.

#### Relationship to E3C

E3C found the same distinction on the (n=14) and (n=16) cubic censuses:

* final stable folklore 2-WL histograms were highly discriminative;
* stable-only linear decoding was weak;
* cumulative refinement histories supported strong structural decoding.

E24 extends that result to the exact cospectral residue at (n=18).

The final stable partition identifies every graph, but its graph-specific color coordinates transfer poorly.

The cumulative refinement path provides the reusable structural features.

This distinction is central to interpreting folklore 2-WL:

$$\boxed{\text{stable expressivity}\neq\text{inductive structural accessibility}}$$

#### Relationship to E14 and E14N

E14 established that QuIC ranks:

* the six diamond and 6-cycle witnesses;
* Wiener index;
* automorphism-group order

within exact adjacency-cospectral classes.

E14N supplied a cleaner deterministic split-null confirmation for Wiener index and one-direction confirmation for automorphism order.

E24 shows that those properties are also accessible to folklore 2-WL.

The strongest comparison is Wiener index.

Under the E24 protocol:

$$T_{\text{2WL}}=0.827>T_{\text{QuIC}}=0.541.$$

For automorphism order, the two representations are less clearly separated:

$$T_{\text{2WL}}=0.657,\qquad T_{\text{QuIC}}=0.556,$$

with a bootstrap interval that includes zero.

On the six diamond witnesses, both methods obtain:

$$6/6.$$

The appropriate conclusion is therefore:

> QuIC’s non-spectral residue is structurally meaningful, but it is not inaccessible to a strong higher-order classical refinement.

#### Difference from the E14N QuIC protocol

E24 describes its ranker as the E14N ranker generalized to arbitrary representations. The implementation is not identical.

E14N scales the QuIC pair-difference matrix using the root mean square across all matrix entries:

$$s_{\text{E14N}}=\sqrt{\text{mean}*{i,j}(X*{ij}^2)}.$$

E24 scales each representation block using the root mean square of pairwise row energies:

$$s_{\text{E24}}=\sqrt{\text{mean}_i|X_i|_2^2}.$$

For a 100-dimensional QuIC block:

$$s_{\text{E24}}=\sqrt{100},s_{\text{E14N}}=10s_{\text{E14N}}.$$

E24 therefore divides the QuIC differences by a scale ten times larger.

Because the logistic model retains the fixed value:

$$C=1,$$

this changes the effective regularization strength.

E24 also uses dual-form `liblinear`, while E14N used the default logistic-regression solver.

These differences explain why E24 does not reproduce the E14N QuIC values.

For Wiener index, E14N reported approximately:

$$0.603\quad\text{and}\quad0.607,$$

while E24 reports:

$$0.533\quad\text{and}\quad0.551.$$

For automorphism order, E14N reported:

$$0.740\quad\text{and}\quad0.517,$$

while E24 reports:

$$0.660\quad\text{and}\quad0.425.$$

The E24 QuIC row is valid within the common E24 model and scaling protocol. It should not replace the E14N result or be described as an exact replication.

A stricter comparison would either:

* preserve the E14N QuIC preprocessing for the QuIC-only arm;
* select (C) separately within each training partition;
* or prespecify representation-specific regularization after scale normalization.

#### What the experiment establishes

The completed results establish that:

1. **Folklore 2-WL separates every exact adjacency-cospectral group at (n=18).**

   Both stable and cumulative histograms distinguish all 471 groups.

2. **QuIC top-100 separates all 445 exact cospectral groups for which it was computed.**

3. **All three tested representations separate all six diamond and 6-cycle witness pairs.**

4. **Cumulative folklore 2-WL ranks the diamond direction in all six leave-one-witness-out folds.**

   It exactly matches QuIC at (6/6), with exhaustive (p=0.03125).

5. **Cumulative folklore 2-WL strongly ranks Wiener index in both deterministic split directions.**

   Its group-balanced accuracies are (0.817) and (0.837).

6. **Cumulative folklore 2-WL substantially exceeds QuIC on Wiener index under the E24 protocol.**

   The bootstrap interval for the aggregate difference lies entirely below zero from the QuIC perspective.

7. **Automorphism-order ranking is split asymmetric.**

   Cumulative folklore 2-WL and the concatenated representation are strong in one direction but do not independently reject the reverse-direction null at (0.05).

8. **Stable folklore 2-WL is expressively complete but inductively unusable under the train-only final-color vocabulary.**

9. **QuIC and cumulative folklore 2-WL have nonidentical error sets.**

   Each uniquely solves some groups.

10. **Simple concatenation does not establish an aggregate improvement over cumulative folklore 2-WL.**

11. **QuIC’s exact-cospectral residue is not beyond folklore 2-WL.**

E24 therefore provides a strong classical explanation for much of the functional structure found in E14.

#### Necessary qualifications

The folklore 2-WL analysis covers only the 958 members of exact adjacency-cospectral groups, not the full 41,301-graph census.

The statement:

$$471/471$$

therefore refers to the exact cospectral partition, not all cubic graphs at (n=18).

QuIC expressivity is evaluated on only 445 of the 471 groups. The remaining 26 groups do not have stored QuIC vectors.

The folklore 2-WL colors are represented by 128-bit cryptographic digests rather than exact symbolic identifiers.

No within-group cumulative ties occur, so the planned 256-bit recheck is not exercised on any pair. The collision probability is negligible, but the result remains hash based.

The refinement depth is determined from stabilization across all 958 graphs.

Although the ranking vocabulary is train only, the decision to retain rounds zero through four was informed by the complete producer set. A fully inductive implementation could fix the number of refinement rounds before constructing the train/test split.

The stable folklore 2-WL score of zero should not be interpreted as poor expressivity or systematic reverse ordering.

Test-only stable colors are discarded, and exact zero margins are counted as failures. The notebook does not separately report the fraction of test pairs receiving zero margins.

The group-balanced permutation values printed as (0.0000) are rounded to four decimal places. With 100,000 draws, they should be reported as below the displayed resolution rather than as exact zero.

The Bonferroni statistic:

$$2\min(p_A,p_B)$$

tests whether at least one direction is significant after considering both. It does not establish two-direction replication.

This distinction is especially important for automorphism order.

The overlap table defines a group as correct only when its accuracy is exactly one. A multi-member group with most, but not all, pairs correctly ranked is placed in the incorrect category.

The overlap counts are therefore stricter than the mean group-balanced accuracies.

The bootstrap resamples fixed held-out group accuracies. It does not refit the representations or models within each bootstrap draw.

The E24 ranker changes both scaling and solver relative to E14N. The QuIC-only results are therefore not an exact protocol replication.

The train-only block-energy normalization is reasonable for concatenation, but applying one fixed (C) after representation-dependent scaling does not guarantee equivalent regularization across representations.

The random-number seeds for the permutation and bootstrap procedures include Python’s built-in `hash()` function. Unless `PYTHONHASHSEED` is fixed, exact sampled values may vary across processes.

The cumulative folklore 2-WL feature space is much larger than the QuIC top-100 space. E24 evaluates structural accessibility, not equal dimensionality, runtime, memory, or computational cost.

The producer computes folklore 2-WL on graphs with only 18 vertices. Its practical cost at larger graph orders is not evaluated.

The six-witness result remains based on only six independent cospectral classes. The exhaustive null makes the inference exact for those classes but does not increase their number.

Finally, all QuIC results use ideal probabilities. The comparison does not address finite-shot accessibility.

#### Overall assessment

E24 supplies the strongest classical baseline for the exact-cospectral results.

Folklore 2-WL separates every one of the 471 exact cospectral groups. Its cumulative refinement history also provides strong functional coordinates.

On Wiener index, cumulative folklore 2-WL reaches:

$$0.817\quad\text{and}\quad0.837$$

across the two deterministic split directions, compared with:

$$0.533\quad\text{and}\quad0.551$$

for QuIC under the E24 ranking configuration.

The aggregate bootstrap interval confirms a substantial classical advantage on this target.

On automorphism order, cumulative folklore 2-WL is strong in one direction and positive but nonsignificant in the reverse direction. QuIC is likewise split asymmetric. Neither representation has a clearly established aggregate advantage after group-level bootstrapping.

On the six direct diamond and 6-cycle witnesses, cumulative folklore 2-WL exactly matches QuIC:

$$6/6,\qquad p=0.03125.$$

Stable folklore 2-WL provides an important negative result of a different kind. It distinguishes every graph but obtains zero ranking accuracy under the inductive train-only vocabulary. The cumulative path, rather than the final partition alone, carries transferable structural information.

QuIC retains exclusive successes on both ranking targets, showing that the two representations are not identical. Simple concatenation, however, does not significantly improve upon the stronger standalone method.

The appropriate central claim is:

> Folklore 2-WL fully separates all 471 exact adjacency-cospectral classes at (n=18) and functionally recovers the same non-spectral graph properties identified by QuIC. Its cumulative refinement history ranks Wiener index substantially better than QuIC under the common E24 protocol, provides one-direction evidence for automorphism-group order, and matches QuIC’s perfect 6-of-6 ranking of the direct diamond and 6-cycle witnesses. Stable final histograms remain fully discriminative but fail to transfer under an inductive vocabulary, showing that the reusable signal lies in the refinement trajectory rather than stable expressivity alone. QuIC’s non-spectral residue is therefore structurally meaningful but not beyond folklore 2-WL.



### E24C - Protocol-Matched Folklore 2-WL Ranking

#### Experimental design

E24C reruns the E24 exact-cospectral ranking comparison under the precise evaluation protocol used by E14N.

The purpose is to remove a methodological difference in the original E24a ranking notebook.

E24a changed two elements of the QuIC evaluation relative to E14N:

* entrywise root-mean-square scaling was replaced with block-energy scaling;
* the default `lbfgs` logistic solver was replaced with dual-form `liblinear`.

Under that altered protocol, QuIC’s Wiener-index accuracies declined from approximately:

$$0.603\quad\text{and}\quad0.607$$

in E14N to:

$$0.533\quad\text{and}\quad0.551$$

in E24a.

That left open the possibility that part of the apparent folklore 2-WL advantage resulted from evaluating QuIC under a different preprocessing and optimization pipeline.

E24C eliminates that objection by evaluating all primary representations through one common protocol:

* the deterministic E14N group split;
* QuIC depth (k=100);
* train-only entrywise root-mean-square scaling;
* intercept-free logistic regression;
* the default `lbfgs` solver;
* fixed regularization (C=1);
* group-balanced held-out accuracy;
* within-test-group target permutation;
* 100,000 null draws;
* Bonferroni correction over the two split directions.

The primary representations are:

1. QuIC top-100;
2. cumulative folklore 2-WL;
3. stable folklore 2-WL.

Concatenation is deliberately excluded from the primary comparison because E14N does not define a natural scaling rule for combining a 100-dimensional dense QuIC block with a very high-dimensional sparse folklore 2-WL block.

#### Input data

E24C loads the validated E24 producer artifact containing the exact adjacency-cospectral partition of the complete connected cubic census at:

* **(n=18)**;
* **471 exact cospectral groups**;
* **958 total members**.

The ranking targets are:

* Wiener index;
* $$\log_2|\text{Aut}(G)|.$$

The varying classes contain:

| Target       | Varying groups | Members | QuIC coverage |     |          |
| ------------ | -------------: | ------: | ------------: | --- | -------- |
| Wiener index |            283 |     579 |      Complete |     |          |
| $$\log_2     |  \text{Aut}(G) |      $$ |            90 | 183 | Complete |

Every member used in either ranking experiment has:

* a QuIC top-100 vector;
* a stable folklore 2-WL representation;
* a cumulative folklore 2-WL representation.

The folklore 2-WL producer stabilized after round four.

E24C does not recompute the circuits or folklore 2-WL refinement from graph6. It inherits the validated representation artifact from E24 and applies additional metadata, coverage, and group-count gates.

#### Representations

##### QuIC

The QuIC arm uses the first 100 coordinates of the complete descending-sorted canonical QuIC probability vector:

$$\phi_{\text{QuIC}}(G)=\mathbf p_{1:100}(G).$$

##### Stable folklore 2-WL

The stable representation uses only the final refinement-round histogram.

The feature vocabulary is constructed from the training groups only. Colors appearing exclusively in held-out groups are discarded.

##### Cumulative folklore 2-WL

The cumulative representation concatenates normalized color histograms from every refinement round through stabilization.

Its train-only vocabulary includes the round index as part of every color key, preventing colors from different rounds from sharing a coordinate.

#### Deterministic split

The E14N content-addressed partition is reused exactly.

Each varying exact-cospectral group is assigned to partition zero or one using a SHA-256 digest of the sorted graph6 strings of its members.

| Target       |   Partition 0 | Partition 1 |           |           |
| ------------ | ------------: | ----------: | --------- | --------- |
| Wiener index |    131 groups |  152 groups |           |           |
| $$\log_2     | \text{Aut}(G) |          $$ | 40 groups | 50 groups |

Both directions are evaluated:

* **Direction A:** train on partition 0 and test on partition 1;
* **Direction B:** train on partition 1 and test on partition 0.

No member of a held-out exact-cospectral group enters the corresponding model fit or folklore 2-WL vocabulary.

#### Pairwise ranking construction

For every unequal-target pair ((G_i,G_j)) within a training group, the representation difference is:

$$\mathbf x_{ij}=\phi(G_i)-\phi(G_j).$$

The label is:

$$y_{ij}=\text{sign}\left(t(G_i)-t(G_j)\right).$$

Both orientations are included:

$$(\mathbf x_{ij},y_{ij})\quad\text{and}\quad(-\mathbf x_{ij},-y_{ij}).$$

This enforces an antisymmetric ranking model.

The logistic regression has:

* no intercept;
* fixed (C=1);
* maximum 5,000 iterations;
* default `lbfgs` optimization.

#### E14N entrywise scaling

Every representation is scaled using the E14N formula.

For an (m\times d) training difference matrix (X), the scale is:

$$s=\sqrt{\frac{1}{md}\sum_{i=1}^{m}\sum_{j=1}^{d}X_{ij}^2}.$$

The model receives:

$$X/s.$$

The same formula is applied to:

* the dense 100-dimensional QuIC matrix;
* the sparse stable folklore 2-WL matrix;
* the sparse cumulative folklore 2-WL matrix.

This reproduces E14N’s QuIC preprocessing and gives all primary arms identical evaluation code.

#### Primary statistic

The primary statistic is group-balanced held-out accuracy:

$$A_{\text{group}}=\frac{1}{|\mathcal G_{\text{test}}|}\sum_{g\in\mathcal G_{\text{test}}}\frac{\text{correct unequal pairs in }g}{\text{unequal pairs in }g}.$$

Each exact-cospectral group receives equal weight, regardless of its number of unequal-target pairs.

Raw pooled pair accuracy is also computed but is not the primary comparison.

#### Within-test-group permutation null

The fitted decision margins remain fixed while target values are permuted within each held-out cospectral group.

For two-member groups, the null reverses the target direction with equal probability.

For larger groups, the complete target-value assignment is permuted among the members. This preserves:

* the target multiset;
* target ties;
* transitivity of the target ordering;
* the number and structure of within-group comparisons.

The one-sided add-one value is:

$$p=\frac{1+#{A_{\text{null}}\ge A_{\text{observed}}}}{100{,}001}.$$

The minimum attainable value is:

$$\frac{1}{100{,}001}\approx10^{-5}.$$

E24C replaces Python’s process-dependent string hash with a stable cryptographic seed. Observed accuracies are unaffected, while the exact Monte Carlo null draws may differ slightly from E14N.

#### Null validation

The permutation implementation is tested using synthetic grouped data.

A perfectly aligned model reaches:

$$A_{\text{group}}=1$$

and the minimum attainable permutation value.

Independent random margins produce approximately uniform null values across 300 synthetic experiments.

All calibration assertions pass.

#### QuIC reproduction gate

Before any classical comparison is interpreted, the QuIC arm is required to reproduce E14N’s recorded group-balanced accuracies within:

$$0.003.$$

| Target       | Direction     | E24C QuIC | E14N reference | Absolute difference |       |        |
| ------------ | ------------- | --------: | -------------: | ------------------: | ----- | ------ |
| Wiener index | A             |     0.603 |          0.603 |              0.0003 |       |        |
| Wiener index | B             |     0.607 |          0.607 |              0.0001 |       |        |
| $$\log_2     | \text{Aut}(G) |        $$ |              A |               0.740 | 0.740 | 0.0000 |
| $$\log_2     | \text{Aut}(G) |        $$ |              B |               0.517 | 0.517 | 0.0003 |

Every gate passes.

The associated QuIC permutation results are:

| Target       |       Direction A |       Direction B | Bonferroni omnibus |                   |            |
| ------------ | ----------------: | ----------------: | -----------------: | ----------------- | ---------- |
| Wiener index | 0.603, (p=0.0049) | 0.607, (p=0.0066) |         (p=0.0098) |                   |            |
| $$\log_2     |     \text{Aut}(G) |                $$ |  0.740, (p=0.0004) | 0.517, (p=0.4284) | (p=0.0008) |

The small differences from E14N’s reported permutation values arise from the corrected stable null seeds, not from a change in the fitted QuIC models.

The successful gate establishes that the E24C QuIC arm is an adequate reproduction of the recorded E14N ranking result.

#### Wiener-index ranking

| Representation           | Direction A accuracy | Direction A (p) | Direction B accuracy | Direction B (p) | Bonferroni omnibus |
| ------------------------ | -------------------: | --------------: | -------------------: | --------------: | -----------------: |
| QuIC top-100             |                0.603 |          0.0049 |                0.607 |          0.0066 |             0.0098 |
| Cumulative folklore 2-WL |                0.904 |       (<0.0001) |                0.878 |       (<0.0001) |          (<0.0001) |
| Stable folklore 2-WL     |                0.000 |          1.0000 |                0.000 |          1.0000 |             1.0000 |

Cumulative folklore 2-WL strongly ranks Wiener index in both directions.

Its held-out group-balanced accuracies are:

$$0.904\quad\text{and}\quad0.878.$$

QuIC also confirms in both directions:

$$0.603\quad\text{and}\quad0.607.$$

The directional cumulative-2-WL advantages are:

$$0.904-0.603=0.301,$$

and:

$$0.878-0.607=0.271.$$

The classical advantage therefore remains large after the QuIC evaluation is restored to the E14N protocol.

#### Aggregate Wiener comparison

Combining the held-out group accuracies across both deterministic split directions gives:

| Representation           | Mean group-balanced accuracy |
| ------------------------ | ---------------------------: |
| QuIC                     |                        0.605 |
| Cumulative folklore 2-WL |                        0.892 |

The aggregate difference is:

$$T_{\text{2WL}}-T_{\text{QuIC}}=0.287.$$

A 10,000-resample group bootstrap gives:

$$95%\ \text{CI}=[0.223,0.348].$$

The complete interval lies above zero.

The protocol-matched experiment therefore supports the direct comparative claim:

> Under the E14N ranking protocol, cumulative folklore 2-WL outperforms QuIC on Wiener-index ranking across exact adjacency-cospectral classes.

This conclusion is no longer attributable to the altered QuIC scaling or solver used in E24a.

#### Relationship to the original E24a Wiener comparison

The original E24a aggregate values were approximately:

$$T_{\text{QuIC}}=0.541,\qquad T_{\text{2WL}}=0.827.$$

The protocol-matched values are:

$$T_{\text{QuIC}}=0.605,\qquad T_{\text{2WL}}=0.892.$$

Matching E14N improves both representations.

The aggregate gap is almost unchanged:

$$0.827-0.541=0.286,$$

compared with:

$$0.892-0.605=0.287.$$

Thus, the original preprocessing change lowered both representations but did not create the observed Wiener gap.

E24C converts that descriptive robustness into a clean protocol-controlled comparison.

#### Wiener error overlap

A group is counted as correct in the overlap analysis only when every unequal pair in the group is correctly ranked.

| Outcome                               | Groups |
| ------------------------------------- | -----: |
| QuIC and cumulative 2-WL both correct |    157 |
| QuIC only                             |     12 |
| Cumulative 2-WL only                  |     93 |
| Neither                               |     21 |

The categories sum to:

$$157+12+93+21=283.$$

Cumulative folklore 2-WL uniquely solves substantially more groups:

$$93>12.$$

QuIC nevertheless has 12 exclusive successes.

The representations therefore do not implement identical structural rules, even though cumulative folklore 2-WL is much stronger in aggregate.

#### Stable folklore 2-WL on Wiener index

Stable folklore 2-WL obtains zero group-balanced accuracy in both directions.

This is not evidence of reverse Wiener ordering.

The stable final-round colors are sufficiently graph specific that held-out groups often contain no colors present in the train-only stable vocabulary.

The resulting feature differences receive zero decision margins, and E24C counts zero margins as failures.

Stable folklore 2-WL remains fully discriminative when graphs are directly compared in the complete producer representation. Its failure here concerns inductive coordinate transfer.

The result reinforces the distinction:

$$\boxed{\text{stable expressivity}\neq\text{inductive ranking accessibility}}$$

The transferable Wiener signal lies in the cumulative refinement history rather than in the final stable histogram alone.

#### Automorphism-order ranking

| Representation           | Direction A accuracy | Direction A (p) | Direction B accuracy | Direction B (p) |   Bonferroni omnibus |
| ------------------------ | -------------------: | --------------: | -------------------: | --------------: | -------------------: |
| QuIC top-100             |                0.740 |          0.0004 |                0.517 |          0.4284 |               0.0008 |
| Cumulative folklore 2-WL |                0.780 |       (<0.0001) |                0.554 |          0.2516 | approximately 0.0001 |
| Stable folklore 2-WL     |                0.000 |          1.0000 |                0.000 |          1.0000 |               1.0000 |

Both informative representations are strongly split asymmetric.

##### QuIC

Direction A reaches:

$$A_{\text{group}}=0.740,\qquad p=0.0004.$$

Direction B is near the null:

$$A_{\text{group}}=0.517,\qquad p=0.4284.$$

##### Cumulative folklore 2-WL

Direction A reaches:

$$A_{\text{group}}=0.780,\qquad p<0.0001.$$

Direction B reaches:

$$A_{\text{group}}=0.554,\qquad p=0.2516.$$

Cumulative folklore 2-WL is numerically stronger in both directions, but neither representation independently confirms the reverse split.

The Bonferroni omnibus values establish that each representation has an effect in at least one prespecified direction.

They do not establish two-direction replication.

#### Aggregate automorphism comparison

| Representation           | Mean group-balanced accuracy |
| ------------------------ | ---------------------------: |
| QuIC                     |                        0.641 |
| Cumulative folklore 2-WL |                        0.680 |

The aggregate difference is:

$$T_{\text{2WL}}-T_{\text{QuIC}}=0.039.$$

The group-bootstrap interval is:

$$95%\ \text{CI}=[-0.072,0.144].$$

The interval includes zero.

E24C therefore does not establish that cumulative folklore 2-WL outperforms QuIC on automorphism-order ranking.

The supported conclusion is narrower:

* both representations contain a strong automorphism-ordering direction in one split;
* both fail to confirm that direction in the reverse split;
* their aggregate difference is unresolved.

#### Relationship to the original E24a automorphism comparison

The original E24a aggregate values were approximately:

$$T_{\text{QuIC}}=0.556,\qquad T_{\text{2WL}}=0.657.$$

The protocol-matched values are:

$$T_{\text{QuIC}}=0.641,\qquad T_{\text{2WL}}=0.680.$$

The QuIC score increases more substantially than the folklore 2-WL score.

The apparent aggregate gap therefore shrinks from approximately:

$$0.101$$

to:

$$0.039.$$

This shows that protocol matching matters materially for the automorphism comparison.

The original E24a notebook was sufficient to show that cumulative folklore 2-WL carries automorphism information. It was not sufficient to support a clean claim of superiority over QuIC.

E24C resolves that issue in favor of no established aggregate difference.

#### Automorphism error overlap

| Outcome                               | Groups |
| ------------------------------------- | -----: |
| QuIC and cumulative 2-WL both correct |     46 |
| QuIC only                             |     11 |
| Cumulative 2-WL only                  |     14 |
| Neither                               |     19 |

The categories sum to:

$$46+11+14+19=90.$$

The exclusive-success counts are close:

$$11\quad\text{versus}\quad14.$$

This is consistent with the bootstrap result: cumulative folklore 2-WL has a slightly higher point estimate, but neither representation clearly dominates the other across the complete set of varying groups.

#### Secondary concatenation

A QuIC-plus-cumulative-2-WL representation is evaluated secondarily using block-energy normalization rather than E14N entrywise scaling.

The observed accuracies are:

| Target       |   Direction A | Direction B |       |       |
| ------------ | ------------: | ----------: | ----- | ----- |
| Wiener index |         0.800 |       0.830 |       |       |
| $$\log_2     | \text{Aut}(G) |          $$ | 0.700 | 0.629 |

For Wiener index, concatenation remains weaker than cumulative folklore 2-WL alone:

$$0.800<0.904,$$

and:

$$0.830<0.878.$$

For automorphism order, the concatenated point estimates lie between or near the standalone results.

Because the block balancing is not protocol matched, this arm is appropriately excluded from the primary comparison.

E24C does not establish a concatenation advantage.

#### What the experiment establishes

The completed results establish that:

1. **The QuIC ranking arm reproduces E14N’s recorded group-balanced accuracies.**

   Every reproduction gate passes within the prespecified tolerance.

2. **The original E24 QuIC degradation was caused by its altered evaluation protocol.**

3. **Cumulative folklore 2-WL strongly ranks Wiener index in both deterministic split directions.**

   Its accuracies are (0.904) and (0.878).

4. **QuIC also confirms Wiener ranking in both directions.**

   Its accuracies are (0.603) and (0.607).

5. **Cumulative folklore 2-WL substantially outperforms QuIC on Wiener index under the common E14N protocol.**

   The aggregate advantage is (0.287), with bootstrap interval ([0.223,0.348]).

6. **The protocol-matched Wiener gap is almost identical to the original E24a aggregate gap.**

   The earlier protocol did not create the classical advantage.

7. **The automorphism comparison remains split asymmetric for both representations.**

8. **Cumulative folklore 2-WL does not establish an aggregate automorphism advantage over QuIC.**

   The bootstrap interval includes zero.

9. **Stable folklore 2-WL remains expressively discriminative but inductively unusable under the train-only final-color vocabulary.**

10. **QuIC and cumulative folklore 2-WL have nonidentical error sets on both targets.**

11. **Simple concatenation does not improve the Wiener result and remains outside the protocol-matched primary analysis.**

E24C closes the principal methodological gap in E24 and supports a target-specific comparison rather than a universal classical dominance claim.

#### Necessary qualifications

E24C is protocol matched to E14N, but the common entrywise scaling is not dimension neutral.

For the scaling:

$$s^2=\frac{1}{md}\sum_{i,j}X_{ij}^2,$$

the average squared norm of a scaled training row is:

$$\frac{1}{m}\sum_{i=1}^{m}\left|\frac{X_i}{s}\right|_2^2=d.$$

Thus, the average scaled row norm grows as:

$$\sqrt d.$$

QuIC has:

$$d=100,$$

while cumulative folklore 2-WL has a much larger train-vocabulary dimension.

With the same fixed:

$$C=1,$$

the resulting regularization is not representation-capacity matched. The high-dimensional folklore 2-WL arm receives much larger scaled row norms and therefore effectively weaker regularization.

This does not invalidate the claim:

> cumulative folklore 2-WL outperforms QuIC under the exact E14N protocol.

It does limit stronger claims that cumulative folklore 2-WL is intrinsically superior under all fair capacity-matched comparisons.

A dimension-neutral comparison would require:

* training-only selection of (C) separately for each representation;
* row-energy normalization;
* or another prespecified regularization-matching rule.

The QuIC reproduction gate compares the recorded three-decimal group-balanced accuracies rather than complete model margins or coefficient vectors.

The tolerance is:

$$0.003.$$

The successful gate establishes reproduction of the recorded E14N outcomes, not bitwise identity of every intermediate object.

E24C reuses the E24 producer artifact. It checks group counts, member counts, target coverage, and QuIC availability but does not rerun the producer’s graph-invariant and Qiskit validation suite.

The integrity of the representation layer therefore inherits the completed E24 producer audit.

The folklore 2-WL train vocabulary is split specific, but the stabilization round was determined from the full 958-member producer set.

This uses test graphs to determine how many target-free refinement rounds are retained. It does not use Wiener or automorphism labels, but a fully inductive pipeline could fix the refinement depth before examining the complete producer set.

The stable folklore 2-WL score of zero depends on:

* dropping held-out colors absent from the train vocabulary;
* and counting zero margins as failures.

It should not be interpreted as zero graph-distinguishing power.

Permutation values displayed as (0.0000) are rounded. With 100,000 draws, they should be reported as below the displayed resolution rather than as literal zero.

The statistic:

$$2\min(p_A,p_B)$$

is a Bonferroni omnibus value for evidence in at least one of two directions.

It does not establish replication across both directions.

Wiener index independently succeeds in both directions. Automorphism order does not.

The fixed-margin permutation test conditions on the fitted model. It does not retrain the model after each held-out target permutation.

This is valid for the conditional test because held-out target values do not enter training, but it does not measure uncertainty from alternative training-group compositions.

The bootstrap resamples fixed held-out group accuracies and does not refit the representation or ranking model.

Its interval describes variation across the observed held-out groups, not full pipeline uncertainty.

The overlap analysis calls a group correct only when every unequal-target pair is correctly ranked.

This is stricter than the continuous group-balanced statistic and can classify a mostly correct multi-member group as unsuccessful.

No correction is applied across:

* two targets;
* three primary representations;
* and the aggregate bootstrap comparisons.

The primary Wiener comparison was motivated in advance, but secondary inferential statements should remain descriptive.

Cumulative folklore 2-WL has much greater feature dimension and construction cost than QuIC top-100.

E24C does not compare:

* representation runtime;
* memory;
* feature dimension;
* sample complexity;
* or hardware acquisition cost.

The experiment concerns structural accessibility, not resource-matched efficiency.

The secondary concatenation uses a different scaling rule and should not enter the primary protocol-matched table.

Finally, the experiment concerns:

* connected cubic graphs;
* (n=18);
* exact adjacency-cospectral classes;
* one deterministic split;
* and two target invariants.

It does not establish the same ranking relationship on arbitrary graph families.

#### Overall assessment

E24C performs the needed correction to the original E24 ranking comparison.

The QuIC arm now reproduces E14N:

$$0.603/0.607$$

for Wiener index and:

$$0.740/0.517$$

for automorphism order.

Under that matched protocol, cumulative folklore 2-WL reaches:

$$0.904/0.878$$

for Wiener index.

Its aggregate advantage over QuIC is:

$$0.287,$$

with:

$$95%\ \text{CI}=[0.223,0.348].$$

The classical advantage is therefore large, replicated across both split directions, and no longer attributable to a degraded QuIC evaluation.

The automorphism result is different.

Cumulative folklore 2-WL reaches:

$$0.780/0.554,$$

compared with:

$$0.740/0.517$$

for QuIC.

Both representations are strong in one direction and null in the reverse direction. Their aggregate difference is only:

$$0.039,$$

with an interval spanning zero.

The appropriate central claim is:

> Under the exact E14N ranking protocol, cumulative folklore 2-WL substantially outperforms QuIC on Wiener-index ordering within exact adjacency-cospectral classes. It reaches group-balanced accuracies of (0.904) and (0.878), compared with (0.603) and (0.607) for QuIC, and its aggregate advantage has a group-bootstrap interval of ([0.223,0.348]). The automorphism-order comparison remains unresolved: cumulative folklore 2-WL has a slightly higher point estimate, but both representations are split asymmetric and the aggregate difference is compatible with zero. E24C therefore establishes a strong classical advantage for global metric geometry, not universal dominance over QuIC’s non-spectral residue.



### E25 - Degree-Typed Structural Decodability

#### Experimental design

E25 asks what structural information dominates QuIC’s geometry after leaving the regular-graph manifold.

The experiment reuses the four fixed-degree-sequence strata produced in E6:

| Stratum         | Locked degree sequence | Graphs | Edges |
| --------------- | ---------------------- | -----: | ----: |
| S1 near regular | $$(4,4,3^{10},2,2)$$   |    400 |    21 |
| S2 bimodal      | $$(4^7,2^7)$$          |    400 |    21 |
| S3 skewed       | $$(5,5,4,4,3^6,2^4)$$  |    400 |    22 |
| S4 hub          | $$(6,4,4,3^8,2,2,2)$$  |    400 |    22 |

Every comparison is performed within one stratum.

The degree multiset is therefore constant across all 400 graphs in that stratum. Any variation in degree-typed structure arises from how vertices of the fixed degree classes are connected, not from variation in:

* the number of vertices of each degree;
* the total number of edges;
* or the degree sequence itself.

The central question is whether the off-regular QuIC representation is organized primarily by:

* ordinary cycle totals;
* or degree-conditioned topology such as assortative and disassortative edge mixing.

#### Representation inherited from E6

E25 does not run a new circuit.

It consumes the exact sorted probability vectors stored by the E6 producer and retains the first:

$$k=1000$$

coordinates.

The resulting feature matrix has shape:

$$400\times1000$$

within every stratum.

The E6 representation uses the **flat encoder**:

$$R_X(2.875)^{\otimes14},$$

followed by:

* edgewise $$R_{ZZ}(2.0)$$ entanglers;
* a uniform $$R_X(0.1)$$ mixer;
* one entangler–mixer repetition.

Degrees are not supplied to the circuit as node features.

This distinction is important. High decodability of degree-mixing statistics cannot be attributed to directly rotating each vertex according to its degree. It must emerge from the interaction between:

* the common flat initial state;
* the graph’s edge pattern;
* and the sorted probability readout.

#### Degree-typed target families

E25 constructs three target families from each graph.

##### Joint-degree edge counts

For degree classes $$a\le b$$:

$$M_{ab}=#{uv\in E:{\deg u,\deg v}={a,b}}.$$

These counts form the joint-degree or degree-mixing matrix.

They distinguish, for example:

* low-degree to low-degree edges;
* low-degree to high-degree edges;
* and high-degree to high-degree edges.

##### Degree-typed triangles

For degree classes $$a\le b\le c$$:

$$T_{abc}=#{\text{triangles whose vertex-degree multiset is }(a,b,c)}.$$

The typed counts partition the ordinary triangle total:

$$C_3=\sum_{a\le b\le c}T_{abc}.$$

##### Degree-typed induced 4-cycles

Each chordless 4-cycle is typed by the cyclic order of its vertex degrees.

The degree ring is canonicalized over its eight dihedral symmetries:

* four rotations;
* two orientations.

The degrees are not simply sorted, because sorting would discard whether two degree classes occur:

* adjacent on the cycle;
* or opposite one another.

The typed counts partition the induced 4-cycle total:

$$C_4^{\text{induced}}=\sum_{\tau}C_{4,\tau}^{\text{induced}}.$$

This is not the same target as the producer’s ordinary 4-cycle count, which includes 4-cycles contained in chorded four-vertex subgraphs.

#### Typed-feature inventory

Every observed typed column varies within its stratum. No constant typed column is dropped.

| Stratum         | Varying edge types | Varying triangle types | Varying induced-C4 types |
| --------------- | -----------------: | ---------------------: | -----------------------: |
| S1 near regular |                  6 |                      7 |                       14 |
| S2 bimodal      |                  3 |                      3 |                        5 |
| S3 skewed       |                 10 |                     17 |                       44 |
| S4 hub          |                  9 |                     14 |                       29 |

The number of columns should not be interpreted as the number of independent structural degrees of freedom.

For every degree class $$a$$ with $$n_a$$ vertices:

$$2M_{aa}+\sum_{b\ne a}M_{ab}=an_a.$$

Because the degree sequence is fixed, the right-hand side is constant.

The edge-type columns are therefore linearly constrained.

Their maximum unconstrained dimensions are approximately:

| Stratum | Edge-type columns | Degree-class constraints | Maximum free dimensions |
| ------- | ----------------: | -----------------------: | ----------------------: |
| S1      |                 6 |                        3 |                       3 |
| S2      |                 3 |                        2 |                       1 |
| S3      |                10 |                        4 |                       6 |
| S4      |                 9 |                        4 |                       5 |

In S2, for example, the three nearly perfectly decoded edge counts describe only one independent mixing coordinate.

#### Integrity gates

The notebook verifies for all 1,600 graphs that:

* each adjacency matrix has the locked degree sequence;
* each stored probability vector has dimension $$2^{14}=16{,}384$$;
* each probability vector is descending sorted;
* each vector sums to one;
* the stored triangle and 4-cycle targets satisfy their trace identities.

The identities are:

$$\text{tr}(A^3)=6C_3,$$

and:

$$\text{tr}(A^4)=8C_4+2\sum_i d_i^2-\sum_i d_i.$$

The typed-triangle rows are also verified to sum exactly to the stored triangle totals for every graph:

$$\sum_{a,b,c}T_{abc}=C_3.$$

The typed induced-4-cycle rows are verified to sum to their computed induced-cycle totals for every graph.

The induced-cycle implementation is additionally compared with brute-force four-vertex-subset enumeration on 60 graphs distributed across the four strata.

#### Linear decodability protocol

Each target is predicted from the same top-1,000 QuIC head.

The notebook uses:

* five shuffled outer folds;
* fixed seed zero;
* per-outer-fold standardization;
* ridge regression;
* regularization grid:

$$\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2}.$$

Predictions are assembled out of fold, and one global out-of-fold score is computed:

$$R^2_{\text{OOF}}=1-\frac{\sum_i(y_i-\widehat y_i)^2}{\sum_i(y_i-\overline y)^2}.$$

A synthetic null target produces:

$$R^2=-0.150,$$

while a target constructed as a linear combination of QuIC coordinates produces:

$$R^2=0.988.$$

The calibration supports the basic functioning of the probe.

#### Total-count decodability

The direct cycle-total scores are:

| Stratum         | $$C_3$$ | Producer $$C_4$$ |  $$C_5$$ | Induced $$C_4$$ total |
| --------------- | ------: | ---------------: | -------: | --------------------: |
| S1 near regular |   0.707 |            0.370 | (-0.115) |                 0.424 |
| S2 bimodal      |   0.957 |         (-0.603) | (-0.409) |                 0.155 |
| S3 skewed       |   0.148 |         (-0.008) | (-0.141) |                 0.023 |
| S4 hub          |   0.622 |            0.125 |    0.005 |                 0.294 |

The mean across $$C_3$$, producer $$C_4$$, and $$C_5$$ is:

| Stratum         | Mean cycle-total $$R^2$$ |
| --------------- | -----------------------: |
| S1 near regular |                    0.321 |
| S2 bimodal      |                 (-0.018) |
| S3 skewed       |      approximately 0.000 |
| S4 hub          |                    0.250 |

The ordinary cycle totals are therefore highly stratum dependent.

Triangle count remains accessible in S1, S2, and S4, while 4- and 5-cycle totals are generally weak.

#### Q1 - Joint-degree edge decodability

The joint-degree edge counts are nearly perfectly decodable in every stratum.

| Stratum         | Mean $$M_{ab}$$ $$R^2$$ | Minimum typed $$R^2$$ | Maximum typed $$R^2$$ | Mean cycle-total $$R^2$$ |
| --------------- | ----------------------: | --------------------: | --------------------: | -----------------------: |
| S1 near regular |                   0.983 |                  0.96 |                  1.00 |                    0.321 |
| S2 bimodal      |                   0.998 |    approximately 1.00 |    approximately 1.00 |                 (-0.018) |
| S3 skewed       |                   0.954 |                  0.86 |                  0.99 |      approximately 0.000 |
| S4 hub          |                   0.976 |                  0.94 |                  0.99 |                    0.250 |

Every stratum shows the same large separation:

$$\text{mean }R^2(M_{ab})\gg\text{mean }R^2(C_3,C_4,C_5).$$

The contrast is largest in S2 and S3.

##### S1 near regular

The six edge-type scores range from:

$$0.96\text{ to }1.00.$$

The strongest coordinate is $$M_{24}$$ at approximately one.

##### S2 bimodal

All three edge types are effectively exact:

$$R^2_{22}\approx R^2_{24}\approx R^2_{44}\approx1.$$

Because the degree sequence is fixed, these three counts are constrained to one free mixing coordinate. The result establishes near-perfect recovery of that coordinate rather than three independent discoveries.

##### S3 skewed

Ten degree-pair types are evaluated.

Even the weakest types remain strongly predictable:

$$R^2_{55}=0.86,\qquad R^2_{25}=0.90.$$

Most other pair types lie between:

$$0.96\text{ and }0.99.$$

##### S4 hub

All nine varying degree-pair types score between:

$$0.94\text{ and }0.99.$$

Edges incident to the degree-six hub remain strongly accessible, including:

$$R^2_{26}=0.97,\qquad R^2_{36}=0.96,\qquad R^2_{46}=0.94.$$

#### Interpretation of Q1

Q1 is strongly supported.

The flat-encoder sorted QuIC representation exposes how fixed degree classes connect to one another much more directly than it exposes ordinary cycle totals.

This result is not caused by degree-sequence leakage.

Within each stratum:

* every graph has the same degree sequence;
* every graph uses the same flat initial rotation;
* every graph has the same number of edges.

The varying object is the assignment of edges among degree classes.

The strongest supported interpretation is:

> Off the regular manifold, the dominant sorted QuIC geometry tracks joint-degree topology rather than untyped cycle totals.

This helps explain why the regular-graph cycle hierarchy does not transfer cleanly to E6.

On a regular graph, all edges have the same degree type. The joint-degree matrix collapses to one constant entry and cannot compete with cycle structure.

On a nonregular graph, degree mixing becomes a large source of structural variation, and QuIC organizes that variation very strongly.

#### Q2 - Degree-typed triangles

The mean typed-triangle scores are:

| Stratum         | Mean typed-triangle $$R^2$$ | Direct $$C_3$$ $$R^2$$ | Typed-minus-total |
| --------------- | --------------------------: | ---------------------: | ----------------: |
| S1 near regular |                       0.486 |                  0.707 |          (-0.221) |
| S2 bimodal      |                       0.845 |                  0.957 |          (-0.112) |
| S3 skewed       |                       0.187 |                  0.148 |          (+0.039) |
| S4 hub          |                       0.322 |                  0.622 |          (-0.300) |

Typed triangles do not generally outperform total triangle count.

Only S3 has a positive mean difference, and that difference is small:

$$0.187-0.148=0.039.$$

The individual typed targets vary widely.

##### S1 near regular

The all-degree-three triangle type is highly accessible:

$$R^2_{333}=0.96.$$

Mixed low-degree types can be weak or negative:

$$R^2_{223}=-0.24.$$

##### S2 bimodal

The triangle types are all substantially accessible:

$$R^2_{224}=0.61,$$

$$R^2_{244}=0.94,$$

$$R^2_{444}=0.99.$$

The total triangle count remains stronger than their mean.

##### S3 skewed

Many low-degree triangle types are at or below the prediction floor.

The strongest types involve higher-degree vertices, including:

$$R^2_{335}=0.57,$$

$$R^2_{355}=0.56.$$

##### S4 hub

Triangle types involving the hub are among the strongest:

$$R^2_{336}=0.71,$$

$$R^2_{446}=0.71.$$

Several low-degree types remain weak or negative.

#### Interpretation of Q2

Q2 is not supported as a general statement.

QuIC does encode selected degree-typed triangle structures, especially types involving high-degree vertices. However, decomposing triangles by degree does not generally make the family easier to decode than the total triangle count.

The triangle results therefore do not explain the off-regular failure through a universal hidden typed-cycle hierarchy.

They support a narrower observation:

> Degree typing reveals which triangle configurations are accessible, but total triangle count is usually at least as predictable as the average typed component.

#### Degree-typed induced 4-cycles

The mean decodability of individual induced-4-cycle types is:

| Stratum         | Varying induced-C4 types | Mean typed $$R^2$$ |
| --------------- | -----------------------: | -----------------: |
| S1 near regular |                       14 |              0.102 |
| S2 bimodal      |                        5 |           (-0.118) |
| S3 skewed       |                       44 |           (-0.014) |
| S4 hub          |                       29 |              0.050 |

Unlike joint-degree edge counts, degree-typed induced 4-cycles are generally weak.

The large number of cycle types in S3 and S4 does not produce strong average accessibility.

Many of these targets are sparse count variables with limited within-stratum support. Their negative out-of-fold scores indicate that the ridge model often performs worse than the global mean predictor.

The contrast is sharp:

$$\text{edge degree mixing is highly accessible, while degree-typed induced 4-cycles are not.}$$

#### Q3 - Cancellation test

Q3 tests whether weak direct prediction of a total arises because separately accessible typed components cancel when the total is modeled directly.

Each typed column is decoded separately under the same outer folds. Their aligned out-of-fold predictions are then summed and compared with direct prediction of the corresponding total.

##### Triangle totals

| Stratum         | Direct $$C_3$$ | Sum of typed predictions |     Lift |
| --------------- | -------------: | -----------------------: | -------: |
| S1 near regular |          0.707 |                    0.711 | (+0.004) |
| S2 bimodal      |          0.957 |                    0.950 | (-0.007) |
| S3 skewed       |          0.148 |                    0.129 | (-0.020) |
| S4 hub          |          0.622 |                    0.623 | (+0.001) |

The summed typed prediction provides no meaningful triangle improvement.

All differences lie between:

$$-0.020\text{ and }+0.004.$$

##### Induced 4-cycle totals

| Stratum         | Direct induced $$C_4$$ | Sum of typed predictions |                Lift |
| --------------- | ---------------------: | -----------------------: | ------------------: |
| S1 near regular |                  0.424 |                    0.422 |            (-0.002) |
| S2 bimodal      |                  0.155 |                    0.354 |            (+0.199) |
| S3 skewed       |                  0.023 |                    0.023 | approximately 0.000 |
| S4 hub          |                  0.294 |                    0.294 | approximately 0.000 |

Only S2 shows a substantial positive lift:

$$0.354-0.155=0.199.$$

The other three strata show no improvement.

#### Interpretation of Q3

The proposed cancellation mechanism is not generally supported.

For triangles, separate typed regressions reconstruct essentially the same score as direct total regression.

For induced 4-cycles, only the bimodal stratum shows the predicted behavior.

Even in S2, the result is not a pure proof of cancellation. Each typed model selects and regularizes its coefficients separately before the predictions are summed. The improvement can arise from:

* target decomposition;
* component-specific regularization;
* or a genuine cancellation structure.

The valid conclusion is:

> Typed decomposition materially improves induced-4-cycle reconstruction in the bimodal stratum, but cancellation is not a general explanation for weak cycle-total decoding.

#### Q4 - Principal-component alignment

E25 standardizes the 1,000 QuIC coordinates and performs PCA within each stratum.

For each of the first five components, it measures alignment with:

1. the joint-degree edge-count block $${M_{ab}}$$;
2. the cycle-total block $${C_3,C_4,C_5}$$.

Two alignment statistics are reported:

* in-sample multiple-regression $$R^2$$ from the complete block;
* the largest absolute correlation with any single target column.

The first five standardized-head PCs explain:

| Stratum         | Variance explained by first five PCs |
| --------------- | -----------------------------------: |
| S1 near regular |                                67.6% |
| S2 bimodal      |                                70.9% |
| S3 skewed       |                                73.2% |
| S4 hub          |                                72.1% |

The variance-weighted block alignments are:

| Stratum         | Degree-mixing block $$R^2$$ | Cycle-total block $$R^2$$ |
| --------------- | --------------------------: | ------------------------: |
| S1 near regular |                       0.556 |                     0.046 |
| S2 bimodal      |                       0.469 |                     0.421 |
| S3 skewed       |                       0.661 |                     0.052 |
| S4 hub          |                       0.635 |                     0.057 |

#### S1 principal components

The first component explains:

$$23.1%$$

of standardized-head variance.

Its degree-mixing block alignment is:

$$R^2=0.814,$$

with best single-type correlation:

$$|r|=0.886.$$

The corresponding cycle-total values are only:

$$R^2=0.016,\qquad |r|=0.113.$$

The second component also favors degree mixing:

$$R^2_{\text{mix}}=0.607,\qquad R^2_{\text{cycle}}=0.065.$$

#### S2 principal components

S2 is the important exception to a simple degree-mixing-only story.

PC1 explains:

$$40.9%$$

of the standardized variance and is strongly aligned with degree mixing:

$$R^2_{\text{mix}}=0.757.$$

However, it also aligns with the cycle-total block:

$$R^2_{\text{cycle}}=0.541.$$

PC2 is more strongly cycle aligned:

$$R^2_{\text{cycle}}=0.596,$$

compared with:

$$R^2_{\text{mix}}=0.082.$$

The five-PC weighted summaries are therefore close:

$$0.469\text{ versus }0.421.$$

S2 contains a joint degree-mixing and cycle-total geometry rather than a clean dominance of one block.

#### S3 principal components

All first five components align more strongly with the degree-mixing block.

The variance-weighted values are:

$$R^2_{\text{mix}}=0.661,$$

and:

$$R^2_{\text{cycle}}=0.052.$$

The first component alone has:

$$R^2_{\text{mix}}=0.734,$$

compared with:

$$R^2_{\text{cycle}}=0.064.$$

#### S4 principal components

The degree-mixing block again dominates:

$$R^2_{\text{mix}}=0.635,$$

compared with:

$$R^2_{\text{cycle}}=0.057.$$

PC2 and PC3 have particularly strong mixing alignments:

$$0.828\quad\text{and}\quad0.778.$$

#### Interpretation of Q4

Q4 is strongly supported in S1, S3, and S4.

The leading standardized-head directions are much better explained by joint-degree mixing than by the three ordinary cycle totals.

S2 remains mixed. Its dominant component contains both degree-mixing and cycle information, and its second component favors cycle totals.

The dimension-fair single-column correlations support the main block result. The degree-mixing advantage is not solely caused by fitting more predictor columns in the multiple-regression comparison.

The appropriate conclusion is:

> Degree mixing dominates the leading standardized QuIC directions in three of four nonregular strata, while the bimodal stratum contains a more entangled degree-mixing and cycle-total geometry.

#### Relationship to E6

E6 showed that ordinary structural targets degrade sharply after leaving the regular manifold.

The flat-encoder aggregate results were weak for:

* 4-cycles;
* 5-cycles;
* 6-cycles;
* girth;
* diameter;
* and several metric targets.

E25 shows that the representation is not generally structure free.

Instead, it carries an exceptionally strong description of how degree classes connect.

This reframes the E6 result.

The regular graph hierarchy does not simply disappear because QuIC loses structural information. The dominant structural axis changes.

On regular graphs:

* every vertex has one degree;
* every edge has the same degree-pair type;
* degree mixing is constant;
* cycle structure becomes the principal varying signal.

On fixed-degree-sequence nonregular graphs:

* the degree multiset remains fixed;
* the edge-type mixing pattern varies;
* that mixing pattern dominates the sorted representation.

E25 therefore supplies a plausible representation-level explanation for regularity dependence.

#### Relationship to E6D

E6D applied the normalized degree encoder to the same four strata and found weaker ordinary-target decoding than the flat encoder.

E25 makes that result less paradoxical.

The flat encoder already captures degree mixing through topology. Explicit degree-dependent rotations need not reveal a new clean structural coordinate; they can instead alter or disrupt the interference geometry that made degree mixing accessible.

E25 does not directly decode the typed targets from E6D’s degree-encoded vectors, so this remains an interpretation rather than a tested comparison.

A direct flat-versus-degree-encoded typed-target audit would be required to determine whether E6D preserves, strengthens, or destroys the near-perfect $$M_{ab}$$ accessibility.

#### What the experiment establishes

The completed results establish that:

1. **The flat-encoder E6 representation contains highly accessible degree-mixing structure.**

2. **Joint-degree edge counts are nearly perfectly decodable in every stratum.**

   Mean typed scores range from:

   $$0.954\text{ to }0.998.$$

3. **The result cannot be attributed to variation in degree sequence.**

   Every comparison occurs within a fixed-degree-sequence stratum.

4. **The result cannot be attributed to direct degree encoding.**

   E6 uses the same flat initial rotation on every vertex.

5. **Joint-degree edge counts are much more accessible than ordinary cycle totals.**

6. **Degree-typed triangles do not generally outperform total triangle count.**

7. **Degree-typed induced 4-cycles are mostly weakly decodable.**

8. **The cancellation hypothesis receives only isolated support.**

   A substantial lift appears only for induced 4-cycles in S2.

9. **The leading standardized QuIC PCs align predominantly with degree mixing in S1, S3, and S4.**

10. **S2 contains both degree-mixing and cycle-total structure.**

11. **The regularity effect can be interpreted as a change in the dominant structural coordinates rather than a complete loss of structure.**

E25 therefore supports a degree-mixing explanation for QuIC’s off-regular geometry, but not a broad hidden typed-cycle hierarchy.

#### Necessary qualifications

The E25 probe is not identical to the original E6 probe.

E6 used:

* raw QuIC coordinates;
* explicit outer-fold fitting;
* `RidgeCV(cv=5)` inside each outer training fold;
* mean test-fold $$R^2$$.

E25 uses:

* standardized QuIC coordinates;
* `RidgeCV` with its default internal generalized cross-validation behavior;
* `cross_val_predict`;
* one pooled out-of-fold $$R^2$$.

These choices can materially change high-dimensional QuIC results.

E25’s within-notebook typed-versus-total comparisons are controlled because every target uses the same E25 procedure. Its numerical scores should not be described as direct reproductions of E6 or compared cell by cell with E6’s published values.

A paper-facing version should rerun the principal E25 targets under the exact E6 protocol.

The notebook states that the typed-versus-total comparison is invariant to the choice of head depth and regularization grid because both sides use the same settings.

That is too strong.

Using the same settings makes the comparison controlled, but different targets can respond differently to:

* truncation depth;
* standardization;
* alpha selection;
* and feature dimension.

The result is demonstrated at:

$$k=1000,$$

not proven invariant to other depths.

The near-perfect edge-type scores are not statistically independent.

Fixed degree sequences impose linear constraints on the $$M_{ab}$$ columns. Mean typed $$R^2$$ therefore counts several redundant descriptions of a lower-dimensional mixing space.

The S2 result is the clearest case: three nearly exact edge counts describe only one free coordinate.

A cleaner block-level result would predict an independent basis of the joint-degree matrix or report multivariate reconstruction error after removing the fixed stub constraints.

The mean typed-triangle and typed-cycle scores also average targets with different:

* variances;
* count ranges;
* sparsity;
* and frequencies.

A mean over typed columns is descriptive rather than a formally balanced family statistic.

No target-distribution table is printed.

The PCA block regressions are in sample.

They do not use held-out graphs or adjusted $$R^2$$. The degree-mixing block also contains more columns than the three-variable cycle block in most strata.

The best-single-column correlations reduce but do not eliminate this concern.

PCA is applied after standardizing every QuIC rank coordinate to unit variance.

The reported components are therefore leading components of the correlation-standardized head, not leading variance directions of the natural raw probability representation.

The phrase “high-variance QuIC PCs” should be qualified accordingly.

The first-five-PC weighted summaries normalize within the first five components. They do not measure alignment over the remaining approximately 27%–32% of standardized variance.

The Q3 summed prediction uses separately fitted and separately regularized models for every typed column.

A lift can reflect component-specific regularization rather than literal cancellation in a common linear model.

A more direct cancellation analysis would jointly fit the typed vector or analytically decompose one common coefficient model.

The induced-4-cycle typing is validated against brute-force enumeration on 60 graphs rather than all 1,600 graphs. Row-wise reconciliation is checked for every graph, but that only confirms consistency with the typed counter’s own total.

The all-4-cycle robustness variant is defined but not executed.

The notebook therefore establishes results for chordless 4-cycles only.

The producer’s $$C_4$$ target includes all 4-cycles, while the typed total in Q3 contains induced 4-cycles. These targets should remain clearly distinguished.

E25 does not compare QuIC with:

* the adjacency spectrum;
* trace moments;
* folklore 2-WL;
* direct graph statistics;
* or a simple model trained on alternative representations.

The experiment shows that degree mixing is linearly accessible from QuIC. It does not show that this information is uniquely quantum, non-spectral, or difficult for classical methods.

The four strata are sampled sets of 400 degree-preserving-switch graphs, not exhaustive fixed-degree-sequence censuses.

The sampling and deduplication procedure can influence the distribution of mixing patterns.

No confidence intervals, permutation tests, or paired inferential comparisons are reported across the many typed targets.

Finally, all representations use exact ideal probabilities. The finite-shot accessibility of the degree-mixing coordinates is unknown.

#### Overall assessment

E25 provides a strong explanation for the apparent loss of QuIC’s cycle hierarchy outside regular graphs.

The flat-encoder representation does not become unstructured. It becomes organized around a different structural object.

Across four fixed-degree-sequence strata, joint-degree edge counts are decoded with mean scores between:

$$0.954\quad\text{and}\quad0.998.$$

The corresponding ordinary cycle-total means range only from approximately:

$$-0.018\quad\text{to}\quad0.321.$$

The leading standardized QuIC directions also align far more strongly with degree mixing than with cycle totals in S1, S3, and S4. The bimodal stratum contains a mixed geometry but still yields effectively exact recovery of its single independent edge-mixing coordinate.

The typed-cycle diagnostics are weaker.

Typed triangles usually underperform total triangle count. Degree-typed induced 4-cycles remain near the prediction floor. Summing typed predictions provides a substantial improvement only for induced 4-cycles in the bimodal stratum.

The experiment therefore supports a specific structural interpretation rather than a general typed-motif claim:

> On fixed-degree-sequence nonregular graphs, the flat-encoder sorted QuIC representation is dominated by joint-degree mixing. Edge counts between degree classes are nearly perfectly linearly accessible despite degrees never being supplied to the circuit, while ordinary and degree-typed cycle counts are much less consistently decoded. The leading standardized representation directions likewise align primarily with degree mixing in three of four strata. Regularity does not merely strengthen QuIC; it removes degree-mixing variation, allowing cycle structure to become the dominant geometry.



### E25R - E6-Protocol Confirmation of Degree-Typed Decodability

#### Experimental purpose

E25R reruns the essential E25 targets using the ridge-probe protocol established in E6.

The original E25 analysis differed from E6 in four consequential ways:

| Component         | Original E25                   | E6 protocol                           |
| ----------------- | ------------------------------ | ------------------------------------- |
| QuIC coordinates  | Standardized within fold       | Raw                                   |
| Ridge selection   | Generalized cross-validation   | Inner five-fold cross-validation      |
| Outer evaluation  | One pooled out-of-fold $$R^2$$ | Mean of five test-fold $$R^2$$ values |
| Fitting procedure | `cross_val_predict`            | Explicit outer-fold loop              |

E10 showed that high-dimensional QuIC probes can depend materially on:

* coordinate scaling;
* very small ridge penalties;
* inner-fold construction;
* and the definition of the reported $$R^2$$.

E25R therefore asks which E25 findings remain when the typed targets are evaluated through the same probe used for the E6 results they are intended to explain.

The rerun includes:

1. ordinary cycle totals $$C_3,C_4,C_5$$;
2. joint-degree edge counts $$M_{ab}$$;
3. degree-typed triangle counts $$T_{abc}$$.

It intentionally does not rerun:

* degree-typed induced 4-cycles;
* the typed-component cancellation experiment;
* the principal-component alignment analysis.

Those E25 components remain exploratory under their original standardized pooled probe.

#### Relationship to the exact E6 implementation

The actual E6 consumer confirms the following settings:

$$\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2},$$

with:

* five shuffled outer folds;
* outer seed zero;
* inner `RidgeCV(cv=5)`;
* raw QuIC coordinates;
* mean outer-fold test $$R^2$$;
* standard deviation across the five test folds.

E25R uses those same settings.

The notebook header states that the alpha grid and fold arrangement still require confirmation. That warning is stale: direct inspection of the E6 consumer confirms that E25R uses the correct values.

Two differences remain.

First, E6 uses the complete:

$$16{,}384$$

dimensional QuIC vector, whereas E25R retains:

$$k=1000$$

coordinates.

Second, E6 explicitly guards against a target becoming constant within an individual training or test fold. E25R checks only whether the complete target vector is nonconstant.

No E25R row returns a `NaN`, so the omitted exact-constant-fold guard does not appear to change the completed results. It remains a code-level difference, particularly relevant to sparse typed-triangle targets.

E25R should therefore be described as:

> the E6 ridge-probe protocol applied to the E25 top-1,000 representations,

rather than a completely identical reproduction of every E6 analysis detail.

#### Exact reproduction of the E6 total-target rows

Despite using only the first 1,000 probabilities, E25R reproduces the complete-vector E6 results for $$C_3,C_4,C_5$$ to three decimal places in all four strata.

| Stratum         | Target  | E25R top-1,000 | E6 full vector |
| --------------- | ------- | -------------: | -------------: |
| S1 near regular | $$C_3$$ |          0.449 |          0.449 |
| S1 near regular | $$C_4$$ |          0.095 |          0.095 |
| S1 near regular | $$C_5$$ |       (-0.017) |       (-0.017) |
| S2 bimodal      | $$C_3$$ |          0.991 |          0.991 |
| S2 bimodal      | $$C_4$$ |          0.295 |          0.295 |
| S2 bimodal      | $$C_5$$ |          0.284 |          0.284 |
| S3 skewed       | $$C_3$$ |       (-0.047) |       (-0.047) |
| S3 skewed       | $$C_4$$ |       (-0.018) |       (-0.018) |
| S3 skewed       | $$C_5$$ |       (-0.019) |       (-0.019) |
| S4 hub          | $$C_3$$ |          0.378 |          0.378 |
| S4 hub          | $$C_4$$ |       (-0.034) |       (-0.034) |
| S4 hub          | $$C_5$$ |       (-0.050) |       (-0.050) |

The fold standard deviations also reproduce to displayed precision except for a rounding difference of approximately 0.001 on S4 triangle count.

This provides a strong empirical gate that:

* the graph ordering is consistent;
* the outer splits match;
* the alpha grid matches;
* the top-1,000 head is sufficient to reproduce the three relevant E6 total rows.

It does not prove that every typed target would be unchanged under the full vector.

#### Graph strata

The experiment uses the four fixed-degree-sequence strata from E6.

| Stratum         | Locked degree sequence | Graphs |
| --------------- | ---------------------- | -----: |
| S1 near regular | $$(4,4,3^{10},2,2)$$   |    400 |
| S2 bimodal      | $$(4^7,2^7)$$          |    400 |
| S3 skewed       | $$(5,5,4,4,3^6,2^4)$$  |    400 |
| S4 hub          | $$(6,4,4,3^8,2,2,2)$$  |    400 |

Every comparison occurs within one stratum.

Consequently, the following quantities are fixed:

* number of vertices;
* number of edges;
* degree multiset;
* number of vertices in each degree class.

The experiment measures topology within a fixed degree sequence rather than learning differences among degree sequences.

#### Circuit representation

E25R reuses the E6 exact probability vectors.

The E6 producer uses the flat encoder:

$$R_X(2.875)^{\otimes14},$$

followed by:

* one graph-edge $$R_{ZZ}(2.0)$$ layer;
* one uniform $$R_X(0.1)$$ mixer;
* one repetition.

Vertex degree is not supplied to the circuit.

The analyzed feature vector is:

$$\phi(G)=\mathbf p_{1:1000}(G),$$

where $$\mathbf p(G)$$ is the descending-sorted exact Born-probability vector.

The result therefore concerns topology-induced degree-role information rather than direct degree-feature encoding.

#### Target definitions

##### Joint-degree edge counts

For degree classes $$a\le b$$:

$$M_{ab}=#{uv\in E:{\deg u,\deg v}={a,b}}.$$

These counts describe how the fixed degree classes connect.

##### Degree-typed triangles

For degree classes $$a\le b\le c$$:

$$T_{abc}=#{\text{triangles whose degree multiset is }(a,b,c)}.$$

The typed counts reconcile exactly to the total triangle count:

$$C_3=\sum_{a\le b\le c}T_{abc}.$$

The numbers of varying typed targets are:

| Stratum         | Edge types $$M_{ab}$$ | Triangle types $$T_{abc}$$ |
| --------------- | --------------------: | -------------------------: |
| S1 near regular |                     6 |                          7 |
| S2 bimodal      |                     3 |                          3 |
| S3 skewed       |                    10 |                         17 |
| S4 hub          |                     9 |                         14 |

No observed typed column is constant across its complete stratum.

#### Validation gates

For all 1,600 graph records, E25R verifies:

* the locked degree sequence;
* vector dimension $$2^{14}$$;
* descending sortedness;
* probability normalization;
* the triangle trace identity;
* the 4-cycle trace identity.

The identities are:

$$\text{tr}(A^3)=6C_3,$$

and:

$$\text{tr}(A^4)=8C_4+2\sum_i d_i^2-\sum_i d_i.$$

Typed triangles are reconciled to $$C_3$$ for every graph during matrix construction.

The edge-count and triangle-count functions are additionally spot checked on 15 graphs per stratum.

The gate is not fully identical to the original E6 gate. E25R does not independently assert:

* that the producer metadata specifies flat encoding;
* uniqueness of all graph6 strings;
* or agreement with an independently rebuilt circuit vector.

The original E6 consumer performed those checks on the same producer artifact. E25R inherits that validated source rather than reproducing its entire integrity suite.

#### Probe calibration

The E6-style raw-coordinate probe obtains:

$$R^2=-0.024$$

on an independent Gaussian target and:

$$R^2=1.000$$

on a target constructed as a linear combination of QuIC coordinates.

The original E25 pooled probe obtains:

$$R^2=-0.150$$

and:

$$R^2=0.988$$

on the same two calibration targets.

Both probes pass the notebook’s broad calibration criteria.

The constructed signal is only a software sanity check. It does not validate generalization on graph invariants, because the target is explicitly generated from the input features.

#### Cycle-total results under the E6 probe

| Stratum         |  $$C_3$$ |  $$C_4$$ |  $$C_5$$ |     Mean |
| --------------- | -------: | -------: | -------: | -------: |
| S1 near regular |    0.449 |    0.095 | (-0.017) |    0.176 |
| S2 bimodal      |    0.991 |    0.295 |    0.284 |    0.524 |
| S3 skewed       | (-0.047) | (-0.018) | (-0.019) | (-0.028) |
| S4 hub          |    0.378 | (-0.034) | (-0.050) |    0.098 |

The cycle geometry remains highly stratum dependent.

##### S1 near regular

Triangle count is moderately accessible:

$$R^2_{C_3}=0.449.$$

Four- and 5-cycle counts are weak:

$$R^2_{C_4}=0.095,\qquad R^2_{C_5}=-0.017.$$

Triangle prediction is also unstable across folds:

$$0.449\pm0.714.$$

The large fold standard deviation indicates that its apparent moderate mean does not transfer uniformly across all graph partitions.

##### S2 bimodal

Triangle count is almost exact:

$$R^2_{C_3}=0.991.$$

Unlike the original E25 pooled results, both deeper cycle totals are positively decoded:

$$R^2_{C_4}=0.295,\qquad R^2_{C_5}=0.284.$$

These are moderate rather than strong scores, but they overturn the pooled-probe result that placed both targets below zero.

##### S3 skewed

All three total cycle targets remain at the prediction floor.

##### S4 hub

Triangle count retains a moderate signal:

$$R^2_{C_3}=0.378.$$

Four- and 5-cycle counts remain below zero.

#### Effect of the probe correction on cycle totals

| Stratum | Target  | E6-probe result | Original pooled result |   Change |
| ------- | ------- | --------------: | ---------------------: | -------: |
| S1      | $$C_3$$ |           0.449 |                  0.707 | (-0.258) |
| S1      | $$C_4$$ |           0.095 |                  0.370 | (-0.275) |
| S1      | $$C_5$$ |        (-0.017) |               (-0.115) | (+0.098) |
| S2      | $$C_3$$ |           0.991 |                  0.957 | (+0.034) |
| S2      | $$C_4$$ |           0.295 |               (-0.603) | (+0.898) |
| S2      | $$C_5$$ |           0.284 |               (-0.409) | (+0.693) |
| S3      | $$C_3$$ |        (-0.047) |                  0.148 | (-0.195) |
| S3      | $$C_4$$ |        (-0.018) |               (-0.008) | (-0.010) |
| S3      | $$C_5$$ |        (-0.019) |               (-0.141) | (+0.122) |
| S4      | $$C_3$$ |           0.378 |                  0.622 | (-0.244) |
| S4      | $$C_4$$ |        (-0.034) |                  0.125 | (-0.159) |
| S4      | $$C_5$$ |        (-0.050) |                  0.005 | (-0.055) |

The changes are not uniform.

The most consequential difference is S2:

$$C_4:-0.603\rightarrow0.295,$$

and:

$$C_5:-0.409\rightarrow0.284.$$

The original E25 statement that cycle totals are weak in every nonregular stratum therefore requires revision.

The supported result is:

> Cycle totals remain weak in the near-regular, skewed, and hub strata, while the bimodal stratum retains nearly exact triangle information and moderate 4- and 5-cycle accessibility.

#### Joint-degree edge decodability

The joint-degree edge counts remain the strongest result.

| Stratum         | Number of types | Mean $$R^2$$ | Minimum | Maximum | Mean cycle-total $$R^2$$ |
| --------------- | --------------: | -----------: | ------: | ------: | -----------------------: |
| S1 near regular |               6 |        1.000 |   1.000 |   1.000 |                    0.176 |
| S2 bimodal      |               3 |        1.000 |   1.000 |   1.000 |                    0.524 |
| S3 skewed       |              10 |        0.962 |   0.887 |   1.000 |                 (-0.028) |
| S4 hub          |               9 |        0.990 |   0.966 |   0.999 |                    0.098 |

The result is stronger under the E6 protocol than under the original pooled probe.

##### S1 near regular

Every degree-pair target is decoded with:

$$R^2=1.000,$$

and zero fold variation at the printed precision.

##### S2 bimodal

All three counts are also exactly decoded:

$$R^2_{22}=R^2_{24}=R^2_{44}=1.000.$$

Because the degree sequence is fixed, these three counts represent only one independent degree-mixing coordinate.

##### S3 skewed

All ten edge types remain strongly accessible.

The weakest values are:

$$R^2_{25}=0.887,$$

$$R^2_{55}=0.892,$$

and:

$$R^2_{22}=0.904.$$

The other seven targets lie between:

$$0.974\text{ and }1.000.$$

##### S4 hub

All nine edge types score between:

$$0.966\text{ and }0.999.$$

Edges incident to the degree-six hub remain strongly decoded:

$$R^2_{26}=0.984,$$

$$R^2_{36}=0.991,$$

$$R^2_{46}=0.966.$$

#### Structural interpretation of the edge results

The degree sequence is fixed within each stratum.

Thus, QuIC is not merely recovering:

* the number of degree-two vertices;
* the number of degree-four vertices;
* or the degree histogram.

It is recovering how those degree classes are connected.

For every degree class $$a$$:

$$2M_{aa}+\sum_{b\ne a}M_{ab}=an_a,$$

where $$n_a$$ is fixed within the stratum.

The edge-type columns are consequently redundant.

Their maximum independent dimensions are:

| Stratum | Reported edge types | Maximum free dimensions |
| ------- | ------------------: | ----------------------: |
| S1      |                   6 |                       3 |
| S2      |                   3 |                       1 |
| S3      |                  10 |                       6 |
| S4      |                   9 |                       5 |

The result should not be described as 28 independent exact predictions.

It establishes nearly exact reconstruction of the lower-dimensional joint-degree mixing state.

The principal E25 conclusion therefore survives and becomes stronger:

$$\boxed{\text{the off-regular QuIC geometry is strongly organized by degree mixing}}$$

#### Degree-typed triangle results

The family summaries are:

| Stratum         | Number of types | Mean typed $$R^2$$ | Median typed $$R^2$$ | Direct $$C_3$$ |
| --------------- | --------------: | -----------------: | -------------------: | -------------: |
| S1 near regular |               7 |           (-1.470) |                0.244 |          0.449 |
| S2 bimodal      |               3 |              0.979 |                0.993 |          0.991 |
| S3 skewed       |              17 |              0.063 |                0.093 |       (-0.047) |
| S4 hub          |              14 |              0.189 |                0.065 |          0.378 |

The arithmetic mean is not reliable in S1.

One sparse target produces:

$$R^2_{234}=-13.190\pm27.545.$$

That single row drives the seven-type mean from a broadly mixed result to:

$$-1.470.$$

The median:

$$0.244$$

is more representative of the typical S1 typed target, although neither statistic accounts for differences in target variance or prevalence.

#### S1 typed triangles

Three high-degree triangle types are strongly decoded:

$$R^2_{333}=0.940,$$

$$R^2_{334}=0.895,$$

$$R^2_{344}=0.877.$$

The remaining degree-two-containing types range from weak to catastrophically unstable.

The direct total triangle score is:

$$0.449.$$

The E6-probe result therefore reveals a strong subset of triangle structure but does not support a meaningful all-type average.

#### S2 typed triangles

All three types are highly accessible:

$$R^2_{224}=0.945,$$

$$R^2_{244}=0.993,$$

$$R^2_{444}=1.000.$$

Their mean is:

$$0.979,$$

compared with:

$$R^2_{C_3}=0.991$$

for total triangles.

Degree typing does not outperform the total, but it shows that each component of the bimodal triangle count is separately recoverable.

#### S3 typed triangles

The total triangle score is below zero:

$$R^2_{C_3}=-0.047.$$

Several typed components nevertheless retain positive accessibility.

The strongest include:

$$R^2_{335}=0.443,$$

$$R^2_{345}=0.379,$$

$$R^2_{355}=0.366,$$

$$R^2_{455}=0.336.$$

Many other types remain at or below the prediction floor.

One target is highly unstable:

$$R^2_{333}=-0.950\pm2.130.$$

S3 therefore provides the clearest evidence that selected typed components may be accessible even when their total is not.

This is not evidence that the whole typed-triangle family is strongly decoded.

#### S4 typed triangles

The strongest types are concentrated around higher-degree vertices and the hub:

$$R^2_{446}=0.708,$$

$$R^2_{336}=0.630,$$

$$R^2_{346}=0.536,$$

$$R^2_{344}=0.524.$$

The direct total triangle score is:

$$0.378.$$

Several low-degree types remain weak or negative.

The family mean is lower than the total:

$$0.189<0.378.$$

#### Effect of protocol choice on typed triangles

The original pooled-probe family means were:

| Stratum         | Original pooled mean | E6-probe mean |
| --------------- | -------------------: | ------------: |
| S1 near regular |                0.486 |      (-1.470) |
| S2 bimodal      |                0.845 |         0.979 |
| S3 skewed       |                0.187 |         0.063 |
| S4 hub          |                0.322 |         0.189 |

The changes are large and target dependent.

The S1 reversal is dominated by one sparse, unstable target rather than by uniform degradation across all seven types.

The appropriate lesson is not that one probe is universally more pessimistic. It is that averaging raw $$R^2$$ values across heterogeneous typed-count targets is highly unstable.

A paper-facing typed-triangle analysis should report:

* individual target results;
* target support and variance;
* fold variability;
* or a variance-weighted multivariate measure.

It should not use the unqualified arithmetic mean as its principal statistic.

#### Does degree typing improve triangle prediction?

The answer remains no as a general claim.

| Stratum | Direct $$C_3$$ | Mean typed triangles | Median typed triangles |
| ------- | -------------: | -------------------: | ---------------------: |
| S1      |          0.449 |             (-1.470) |                  0.244 |
| S2      |          0.991 |                0.979 |                  0.993 |
| S3      |       (-0.047) |                0.063 |                  0.093 |
| S4      |          0.378 |                0.189 |                  0.065 |

Only S3 has typed-family central tendencies above the direct total.

Even there, the absolute values remain modest.

E25R supports a component-level statement:

> Selected degree-typed triangles, particularly configurations involving higher-degree vertices, remain linearly accessible when the corresponding total triangle count is weak.

It does not support a universal hidden typed-triangle hierarchy.

#### What survives from E25

##### Strongly confirmed

The joint-degree edge result survives completely.

Under the E6 protocol:

$$\text{mean }R^2(M_{ab})\in[0.962,1.000].$$

This is the strongest and cleanest E25 result.

##### Confirmed with revision

Ordinary cycle totals remain much weaker than degree mixing, but S2 must be treated separately.

Its mean total-cycle score is:

$$0.524,$$

rather than the near-zero value produced by the original pooled probe.

##### Partially supported

Selected typed triangles remain accessible, particularly:

* all three S2 types;
* high-degree S1 types;
* several S3 and S4 high-degree configurations.

##### Not confirmed as a family-level claim

Mean typed-triangle performance is probe sensitive and can be dominated by sparse pathological targets.

##### Not rerun

E25R does not validate under the E6 protocol:

* degree-typed induced 4-cycle results;
* the S2 cancellation result;
* principal-component alignment with degree mixing.

Those results remain part of the original E25 exploratory analysis and should not be presented as protocol-matched confirmations.

#### Relationship to E6

E6 found that ordinary QuIC target accessibility weakens after leaving regular graph families.

E25R shows that this does not reflect a complete loss of structural information.

The same representation that performs poorly on many ordinary cycle totals reconstructs degree mixing almost exactly.

The contrast is especially strong in S3:

$$\text{mean }R^2(M_{ab})=0.962,$$

while:

$$\text{mean }R^2(C_3,C_4,C_5)=-0.028.$$

In S4:

$$\text{mean }R^2(M_{ab})=0.990,$$

while:

$$\text{mean }R^2(C_3,C_4,C_5)=0.098.$$

The regularity interpretation is therefore strengthened.

On a regular graph family, joint-degree mixing is constant because every edge has the same endpoint-degree type.

Once degree mixing is removed as a source of variation, cycle structure becomes the dominant accessible geometry.

On nonregular fixed-degree-sequence strata, variation in how degree classes connect becomes a leading structural coordinate.

#### What the experiment establishes

The completed results establish that:

1. **The E6 raw-coordinate nested-ridge protocol has been applied to the essential E25 targets.**

2. **The top-1,000 total-cycle rows reproduce the full-vector E6 rows to three decimal places.**

3. **Joint-degree edge counts remain nearly perfectly decodable in every stratum.**

4. **The edge result is stronger under the E6 probe than under the original E25 probe.**

5. **The edge result cannot be explained by degree-sequence variation or explicit degree encoding.**

6. **Ordinary cycle accessibility remains stratum dependent.**

7. **S2 retains substantially more cycle information than the original pooled analysis indicated.**

8. **Selected typed triangles remain accessible even when the corresponding total is weak.**

9. **Typed-triangle family means are unstable and should not be headline statistics.**

10. **The broad claim that degree-typed triangles outperform total triangles is not supported.**

11. **The induced-cycle, cancellation, and PCA portions of E25 remain unconfirmed under the E6 probe.**

E25R therefore confirms the degree-mixing explanation while narrowing the typed-motif interpretation.

#### Necessary qualifications

E25R uses only the first 1,000 probabilities, while the E6 QuIC column uses the complete 16,384-dimensional vector.

The exact reproduction of $$C_3,C_4,C_5$$ strongly reduces concern for those totals. It does not establish that the full-vector and top-1,000 typed-target results are identical.

The E25R implementation omits E6’s fold-level exact-constant-target guard.

No completed target returns `NaN`, but rare typed targets can have extremely small variance in individual folds and produce very large negative $$R^2$$ values.

The S1 $$T_{234}$$ result is the clearest example:

$$-13.190\pm27.545.$$

This is a property of the unstable normalized-error statistic on a sparse target, not evidence of a meaningful strong inverse relationship.

The notebook does not print:

* the frequency of each typed motif;
* target variances;
* the number of nonzero graphs;
* or fold-specific target ranges.

Those quantities are necessary to interpret the pathological typed rows responsibly.

The edge-count targets are linearly dependent under the fixed degree-sequence constraints.

Averaging their $$R^2$$ values overcounts a lower-dimensional joint-degree mixing space.

A stronger block-level audit would:

* choose an independent basis of the joint-degree matrix;
* predict all independent coordinates jointly;
* or reconstruct the complete constrained matrix and report multivariate error.

The perfect S1 and S2 edge results use 1,000 QuIC features for 400 graphs with ridge penalties extending to:

$$10^{-14}.$$

The design is high dimensional and potentially ill conditioned.

E6 emitted repeated linear-algebra warnings under the same protocol. E25R suppresses those warnings.

The exact cross-fold results are compelling, but an independent dual or singular-value solver check would further strengthen the perfect-decoding claim.

No shuffled-target audit is performed separately for each typed target.

The generic Gaussian null passes, but rare count distributions can behave differently from a continuous synthetic null.

The typed-target comparisons include many implicit tests without multiple-comparison correction.

No confidence intervals or formal paired tests compare:

* degree-mixing targets;
* typed triangles;
* and total cycles.

The mean across targets gives equal weight to motifs with very different prevalence and variance.

No spectral, folklore 2-WL, or elementary classical baseline is included.

Joint-degree edge counts are simple classical graph statistics. E25R establishes accessibility from QuIC, not uniqueness, computational advantage, or non-spectrality.

The representation uses exact ideal probabilities.

The finite-shot recovery of degree-mixing information is unknown.

The four strata contain sampled sets of 400 graphs rather than exhaustive fixed-degree-sequence censuses.

Finally, E25R does not rerun the full E25 study. It is a targeted confirmation of the central degree-mixing result and selected triangle diagnostics.

#### Overall assessment

E25R validates the most important E25 conclusion under the paper’s established E6 probe.

Joint-degree edge mixing is reconstructed almost perfectly:

$$R^2=1.000$$

throughout S1 and S2,

$$\text{mean }R^2=0.962$$

in S3, and:

$$\text{mean }R^2=0.990$$

in S4.

This remains true despite:

* fixed degree sequences;
* a flat circuit encoder;
* and weak ordinary cycle decoding in most strata.

The result strongly supports the interpretation that QuIC’s off-regular geometry is organized around how degree classes connect.

The cycle-total correction is important.

S1, S3, and S4 remain weak, but S2 now has:

$$R^2_{C_3}=0.991,\qquad R^2_{C_4}=0.295,\qquad R^2_{C_5}=0.284.$$

The bimodal stratum therefore carries both near-perfect degree-mixing information and moderate cycle information.

The typed-triangle results are more limited.

S2’s three typed triangles are almost exactly decoded, and selected high-degree types remain accessible in the other strata. However, family averages are probe sensitive and can be destroyed by one sparse target with enormous fold instability.

The appropriate central claim is:

> Under the exact E6 raw-coordinate nested-ridge probe, the flat-encoder sorted QuIC representation nearly perfectly recovers joint-degree edge mixing within all four fixed-degree-sequence strata. Mean edge-type scores range from (0.962) to (1.000), while ordinary cycle totals remain much weaker outside the bimodal family. Selected degree-typed triangles are also accessible, particularly configurations involving higher-degree vertices, but their family-level averages are unstable and do not generally exceed total triangle prediction. E25R therefore confirms that QuIC’s off-regular geometry is dominated by degree mixing, while narrowing the broader typed-cycle interpretation.


### E26 - Degree-Sector Sorting Ablation

#### Experimental design

E26 tests whether QuIC’s weak cycle decodability on nonregular graphs is caused primarily by the final global sorting operation.

The experiment reuses the four fixed-degree-sequence strata generated in E6:

| Stratum         | Locked degree sequence | Graphs |
| --------------- | ---------------------- | -----: |
| S1 near regular | $$(4,4,3^{10},2,2)$$   |    400 |
| S2 bimodal      | $$(4^7,2^7)$$          |    400 |
| S3 skewed       | $$(5,5,4,4,3^6,2^4)$$  |    400 |
| S4 hub          | $$(6,4,4,3^8,2,2,2)$$  |    400 |

Every comparison is performed within one stratum.

The degree sequence is therefore fixed across the 400 graphs in each analysis. The experiment varies how the same ideal circuit probabilities are converted into a permutation-invariant graph representation.

The circuit is the E6 flat-encoder circuit:

* uniform vertex preparation;
* edgewise entanglement;
* one uniform mixer;
* one repetition.

The angles are:

$$\theta_{\text{enc}}=2.875,\qquad\theta_{\text{ent}}=2.0,\qquad\theta_{\text{mix}}=0.1.$$

Every vertex receives the same initial rotation:

$$R_X(2.875).$$

The circuit does not explicitly encode vertex degree.

The targets are:

* triangle count;
* 4-cycle count;
* 5-cycle count;
* 6-cycle count.

#### Representation constructions

For graph $$G$$, let:

$$\mathbf p_G=(p_G(z))_{z\in{0,1}^{14}}$$

denote the unsorted ideal Born-probability vector.

Each basis state is assigned a degree-occupancy signature.

Let the distinct degree classes of the graph be:

$$d_1<d_2<\cdots<d_m,$$

and let:

$$V_{d_j}={i:\deg(i)=d_j}.$$

For bitstring $$z$$, define:

$$\kappa_G(z)=\left(\sum_{i\in V_{d_1}}z_i,\ldots,\sum_{i\in V_{d_m}}z_i\right).$$

The signature records how many excited qubits occur in each vertex-degree class.

E26 compares four readouts.

##### R0 - Global sorting

R0 is the ordinary QuIC readout:

$$R_0(G)=\text{sort}_{\downarrow}{p_G(z):z\in{0,1}^{14}}.$$

It retains the complete probability multiset but discards every association between a probability and its originating bitstring or degree-occupancy sector.

Its dimension is:

$$2^{14}=16{,}384.$$

##### R2 - Degree-sector mass

For each occupancy signature $$\kappa$$:

$$h_{\kappa}(G)=\sum_{z:\kappa_G(z)=\kappa}p_G(z).$$

The sector masses are concatenated in lexicographic signature order.

The representation dimensions are:

| Stratum         | Degree-class sizes | Number of sectors |
| --------------- | -----------------: | ----------------: |
| S1 near regular |           2, 10, 2 |                99 |
| S2 bimodal      |               7, 7 |                64 |
| S3 skewed       |         4, 6, 2, 2 |               315 |
| S4 hub          |         3, 8, 2, 1 |               216 |

R2 discards all probability variation within each sector.

##### R3 - Degree-sector sorting

R3 sorts probabilities within each degree-occupancy sector and concatenates the sorted sectors in lexicographic signature order:

$$R_3(G)=\mathop{\Vert}*{\kappa}\text{sort}*{\downarrow}{p_G(z):\kappa_G(z)=\kappa}.$$

R3 has the same dimension as R0:

$$16{,}384.$$

R0 and R3 contain the same complete probability multiset.

Their difference is that R3 preserves the degree-occupancy sector associated with each probability before discarding within-sector bitstring identities.

##### R3-random - Random sector assignment

The control randomly permutes the complete probability vector before assigning the values to the fixed sector blocks and sorting within those blocks.

It preserves:

* the global probability multiset;
* the number of sectors;
* the size of every sector;
* the final representation dimension.

It destroys the actual relationship between probabilities and degree-occupancy sectors.

#### What the R3 versus R0 contrast tests

R3 and R0 use:

* the same circuit;
* the same graph;
* the same exact probability values;
* the same feature dimension.

A positive R3-minus-R0 result shows that degree-occupancy membership supplies useful alignment that is lost under global sorting.

It does not show that the circuit failed to encode the information.

It also does not isolate sorting without adding information. R3 uses the graph’s degree partition during readout, whereas R0 uses only the probability multiset.

R3 is therefore an explicitly degree-conditioned invariant readout rather than a neutral reordering of R0.

The defensible interpretation is:

> R3 tests whether attaching coarse degree-role labels to probability ranks improves structural accessibility.

A positive result is evidence that global sorting discarded useful degree-role association. It is not automatically evidence that sorting is the sole architectural bottleneck.

#### Validation controls

The E6 producer artifact contains:

* 400 graphs in each stratum;
* the locked degree sequence for each stratum;
* adjacency matrices;
* exact globally sorted QuIC vectors;
* cycle-count targets.

All stratum sizes and degree sequences match the producer record.

The unsorted circuit probabilities are regenerated from each adjacency matrix using the flat E6 circuit.

For five graphs per stratum, the rebuilt R0 vector matches the stored producer vector within:

$$10^{-9}.$$

The degree-sector cardinalities satisfy:

$$|{z:\kappa_G(z)=\kappa}|=\prod_j\binom{|V_{d_j}|}{\kappa_j}.$$

The cardinalities sum to:

$$2^{14}=16{,}384.$$

For five graphs per stratum and 20 random vertex relabelings per graph, R2 and R3 remain invariant at the numerical floor.

| Stratum         | Worst R2 relabeling deviation | Worst R3 relabeling deviation |
| --------------- | ----------------------------: | ----------------------------: |
| S1 near regular |         $$1.2\times10^{-15}$$ |         $$1.2\times10^{-15}$$ |
| S2 bimodal      |         $$1.1\times10^{-15}$$ |         $$1.1\times10^{-15}$$ |
| S3 skewed       |         $$1.0\times10^{-15}$$ |         $$1.0\times10^{-15}$$ |
| S4 hub          |         $$1.0\times10^{-15}$$ |         $$1.0\times10^{-15}$$ |

These checks support the correctness of:

* the qubit-to-vertex convention;
* degree-class construction;
* sector ordering;
* within-sector sorting;
* relabeling invariance.

The R0-equals-producer and probability-conservation checks are performed on the sampled control graphs rather than asserted separately on all 1,600 graphs.

#### Decoding protocol

Every representation is evaluated with the same within-E26 protocol:

* five shuffled outer folds;
* fixed seed zero;
* train-only standardization;
* ridge regression;
* regularization grid:

$$\alpha_{\text{ridge}}\in{10^{-8},10^{-6},10^{-4},10^{-2},1,10^2}.$$

The notebook records:

* mean outer-fold $$R^2$$;
* outer-fold standard deviation;
* pooled out-of-fold $$R^2$$;
* out-of-fold predictions.

The primary displayed table uses mean outer-fold $$R^2$$.

#### Complete decoding results

| Stratum         | Target  | R0 global sort | R2 sector mass | R3 sector sort | R3-random |
| --------------- | ------- | -------------: | -------------: | -------------: | --------: |
| S1 near regular | $$C_3$$ |          0.911 |          0.986 |          0.115 |  (-1.859) |
| S1 near regular | $$C_4$$ |          0.634 |          0.484 |          0.711 |  (-1.668) |
| S1 near regular | $$C_5$$ |          0.281 |          0.074 |          0.214 |  (-3.683) |
| S1 near regular | $$C_6$$ |       (-0.162) |          0.068 |          0.089 |  (-1.549) |
| S2 bimodal      | $$C_3$$ |          0.980 |          0.999 |          0.978 |  (-0.172) |
| S2 bimodal      | $$C_4$$ |          0.735 |          0.934 |          0.918 |  (-1.616) |
| S2 bimodal      | $$C_5$$ |          0.748 |          0.484 |          0.837 |  (-1.617) |
| S2 bimodal      | $$C_6$$ |          0.016 |          0.598 |          0.563 |  (-1.723) |
| S3 skewed       | $$C_3$$ |          0.056 |          0.065 |          0.431 | (-34.973) |
| S3 skewed       | $$C_4$$ |       (-0.319) |       (-0.010) |       (-0.138) | (-15.766) |
| S3 skewed       | $$C_5$$ |       (-0.293) |       (-0.054) |       (-0.051) | (-59.249) |
| S3 skewed       | $$C_6$$ |       (-0.469) |       (-0.081) |       (-0.081) |  (-9.155) |
| S4 hub          | $$C_3$$ |          0.606 |       (-1.035) |          0.510 | (-34.447) |
| S4 hub          | $$C_4$$ |          0.106 |          0.129 |          0.169 |  (-2.178) |
| S4 hub          | $$C_5$$ |       (-0.226) |       (-0.030) |       (-0.136) |  (-8.972) |
| S4 hub          | $$C_6$$ |       (-0.180) |       (-0.035) |       (-0.189) |  (-8.730) |

The mean across the four targets is:

| Stratum         | R0 global sort | R2 sector mass | R3 sector sort |
| --------------- | -------------: | -------------: | -------------: |
| S1 near regular |          0.416 |          0.403 |          0.282 |
| S2 bimodal      |          0.620 |          0.754 |          0.824 |
| S3 skewed       |       (-0.256) |       (-0.020) |          0.040 |
| S4 hub          |          0.077 |       (-0.243) |          0.089 |

These unweighted target means are descriptive only. Negative $$R^2$$ values and differences in target variance make them unsuitable as formal aggregate statistics.

#### S1 near-regular results

The globally sorted representation remains strongest overall in S1.

##### Triangle count

R0 reaches:

$$R^2_{C_3}=0.911.$$

Sector masses improve this to:

$$R^2_{C_3}=0.986.$$

R3, however, falls sharply to:

$$R^2_{C_3}=0.115.$$

Degree-sector sorting therefore destroys most of the triangle accessibility present in the globally sorted vector.

The result shows that preserving more side information does not necessarily produce a better linear coordinate system.

##### Four-cycle count

R3 improves the mean fold score from:

$$0.634$$

to:

$$0.711.$$

The gain is modest.

##### Five-cycle count

R3 is weaker than R0:

$$0.214<0.281.$$

##### Six-cycle count

R0 is below the prediction floor:

$$R^2_{C_6}=-0.162.$$

R3 raises the score to:

$$0.089.$$

The absolute result remains weak, but the paired improvement is the only S1 sector-sorting contrast whose bootstrap interval lies entirely above zero.

The S1 result does not support a general global-sorting bottleneck.

#### S2 bimodal results

S2 provides the strongest support for degree-sector preservation.

##### Triangle count

All three meaningful representations nearly solve the target:

$$R^2_{C_3}=0.980,\qquad0.999,\qquad0.978.$$

R2 is numerically strongest, but the target is saturated across the representations.

##### Four-cycle count

R0 reaches:

$$0.735.$$

R2 and R3 increase this to:

$$0.934\quad\text{and}\quad0.918.$$

The degree-sector mass alone therefore carries nearly all of the accessible 4-cycle signal.

##### Five-cycle count

R3 improves over R0:

$$0.837>0.748.$$

R2 is substantially weaker:

$$0.484.$$

The distinction indicates that within-sector probability shape carries useful C5 information that is lost when each sector is reduced to one mass.

##### Six-cycle count

R0 is essentially at the floor:

$$R^2_{C_6}=0.016.$$

R2 and R3 recover substantial signal:

$$R^2_{C_6}=0.598\quad\text{and}\quad0.563.$$

The large point improvement is the clearest apparent restoration of a deeper cycle target.

Its bootstrap interval is wide and crosses zero, however, so the paired uncertainty analysis does not establish the improvement as bounded away from zero under the notebook’s resampling procedure.

S2 nevertheless provides the most coherent descriptive evidence that degree-conditioned readout restores cycle accessibility.

#### S3 skewed results

R0 performs at or below the prediction floor on every target.

##### Triangle count

R3 raises triangle prediction from:

$$0.056$$

to:

$$0.431.$$

This is the strongest substantive S3 recovery.

R2 remains near the floor:

$$0.065.$$

The improvement therefore depends on within-sector probability shape rather than sector mass alone.

##### Four-cycle count

R3 remains below zero:

$$R^2_{C_4}=-0.138.$$

It is less negative than R0:

$$-0.319,$$

but the target is not usefully decoded.

##### Five- and six-cycle counts

R3 improves the scores relative to R0:

$$-0.293\rightarrow-0.051,$$

and:

$$-0.469\rightarrow-0.081.$$

The paired bootstrap intervals for these differences exclude zero.

The final R3 scores nevertheless remain negative.

The correct interpretation is therefore:

> Sector sorting significantly reduces prediction error relative to global sorting for S3 C5 and C6, but it does not recover useful positive decodability.

A positive difference between two negative $$R^2$$ values is not restoration of the target.

#### S4 hub results

S4 provides little support for the sector-sorting hypothesis.

##### Triangle count

R0 remains stronger:

$$0.606>0.510.$$

R2 fails badly:

$$R^2_{C_3}=-1.035.$$

The within-sector probability shape restores much of the information lost by the mass-only representation, but it does not outperform global sorting.

##### Four-cycle count

R3 modestly improves the mean score:

$$0.106\rightarrow0.169.$$

The paired interval includes zero.

##### Five- and six-cycle counts

All representations remain at or below the prediction floor.

None of the S4 R3-minus-R0 intervals excludes zero.

The hub stratum therefore does not show that global sorting is the off-regularity bottleneck.

#### Paired R3-minus-R0 analysis

The notebook performs a paired graph-level bootstrap on the out-of-fold squared errors.

For each bootstrap sample, it computes the difference between the two representations’ pooled resampled $$R^2$$ values.

The resulting means and 95% intervals are:

| Stratum         | Target  | Bootstrap $$\Delta_{\text{sector}}$$ |    95% interval |
| --------------- | ------- | -----------------------------------: | --------------: |
| S1 near regular | $$C_3$$ |                             (-0.573) | [-1.664, 0.022] |
| S1 near regular | $$C_4$$ |                             (+0.069) | [-0.025, 0.152] |
| S1 near regular | $$C_5$$ |                             (-0.067) | [-0.269, 0.098] |
| S1 near regular | $$C_6$$ |                             (+0.249) |  [0.051, 0.422] |
| S2 bimodal      | $$C_3$$ |                             (-0.001) | [-0.015, 0.020] |
| S2 bimodal      | $$C_4$$ |                             (+0.150) |  [0.010, 0.385] |
| S2 bimodal      | $$C_5$$ |                             (+0.091) |  [0.035, 0.162] |
| S2 bimodal      | $$C_6$$ |                             (+0.475) | [-0.361, 1.822] |
| S3 skewed       | $$C_3$$ |                             (+0.363) |  [0.222, 0.508] |
| S3 skewed       | $$C_4$$ |                             (+0.189) | [-0.137, 0.441] |
| S3 skewed       | $$C_5$$ |                             (+0.247) |  [0.068, 0.427] |
| S3 skewed       | $$C_6$$ |                             (+0.386) |  [0.146, 0.640] |
| S4 hub          | $$C_3$$ |                             (-0.083) | [-0.268, 0.060] |
| S4 hub          | $$C_4$$ |                             (+0.028) | [-0.335, 0.280] |
| S4 hub          | $$C_5$$ |                             (+0.114) | [-0.103, 0.323] |
| S4 hub          | $$C_6$$ |                             (-0.026) | [-0.340, 0.212] |

Six of the sixteen intervals lie entirely above zero:

* S1 C6;
* S2 C4;
* S2 C5;
* S3 C3;
* S3 C5;
* S3 C6.

These six cells do not all represent strong final prediction.

Only the following have positive and substantively useful R3 scores:

* S2 C4;
* S2 C5;
* S3 C3.

S1 C6 remains weak, while S3 C5 and C6 remain below zero.

The experiment therefore supports selective degree-sector gains, not a general recovery of the cycle hierarchy.

#### Why the bootstrap differences do not equal the table differences

The displayed decoding table reports:

$$\text{mean of five test-fold }R^2\text{ values}.$$

The paired bootstrap operates on the assembled out-of-fold predictions and computes resampled pooled $$R^2$$ differences.

These are different estimands.

For example, the S1 triangle table difference is:

$$0.115-0.911=-0.796,$$

while the mean bootstrap difference is:

$$-0.573.$$

The discrepancy is expected from the different fold-weighting and resampling definitions.

The table and bootstrap values should not be subtracted or combined as though they were the same statistic.

#### Sector mass versus within-sector shape

R2 isolates aggregate probability assigned to each degree-occupancy sector.

R3 additionally preserves the ranked probability shape inside every sector.

Their comparison reveals several distinct regimes.

##### Mass-dominated targets

R2 is at least as strong as R3 for:

* S1 triangles;
* S2 triangles;
* S2 4-cycles;
* S2 6-cycles.

For these targets, aggregate sector occupation carries most or all of the useful degree-conditioned signal.

##### Shape-dependent targets

R3 substantially exceeds R2 for:

* S1 4-cycles;
* S2 5-cycles;
* S3 triangles;
* S4 triangles.

The largest difference occurs for S4 triangles:

$$0.510-(-1.035)=1.545.$$

This does not mean R3 exceeds global sorting in S4. It shows that reducing each sector to one mass destroys information that is retained by the within-sector rank profile.

##### Weak in both forms

Neither sector mass nor sector shape usefully decodes:

* S3 C4–C6;
* S4 C5–C6.

Degree-sector conditioning does not generally restore the deeper cycle hierarchy in the most irregular strata.

#### Random-sector control

R3-random performs poorly in every cell and catastrophically in several S3 and S4 cells.

The R3-minus-random bootstrap intervals are positive for all sixteen targets.

This confirms that independently randomizing the relationship between probabilities and sector blocks destroys cross-graph predictive alignment.

It does not by itself prove that the R3 advantage is specifically caused by meaningful degree roles.

The control has three important limitations.

First, every graph receives a different random probability permutation.

The resulting coordinate system is graph specific rather than aligned across the dataset.

Second, the random seed depends on the graph’s position in the stored enumeration:

$$\text{seed}=20250717+\text{graph index}.$$

R3-random is therefore not a representation defined solely by the graph.

Third, R3-random is not subjected to the relabeling-invariance tests used for R2 and R3.

Its extremely negative scores are consequently best interpreted as a destructive sanity check:

> Arbitrary graph-specific reassignment of probability values to sector blocks destroys decodability.

They should not be used as quantitative evidence that the full R3-minus-random difference measures degree-role information.

A cleaner control would require a prespecified, consistently aligned alternative partition rather than a different random assignment for every graph.

#### Does E26 identify global sorting as the bottleneck?

Not generally.

The evidence differs by stratum.

##### S1 near regular

Global sorting remains stronger on triangles and C5. R3 provides only a modest C4 improvement and a weak positive C6 result.

##### S2 bimodal

Degree-sector information clearly helps. R2 or R3 improves C4, C5, and C6, and R3 provides the strongest average target profile.

##### S3 skewed

R3 substantially recovers triangle information and reduces error for C5 and C6, but the deeper-cycle scores remain below zero.

##### S4 hub

R3 provides no robust improvement over R0.

The broad claim:

$$\boxed{\text{global sorting causes the off-regularity failure}}$$

is therefore not supported.

The narrower supported claim is:

$$\boxed{\text{global sorting discards useful degree-sector association for selected targets and degree sequences}}$$

The usefulness of that association depends strongly on the degree-sequence family.

#### Relationship to E25

E25 showed that the globally sorted flat-encoder representation already decodes joint-degree edge-mixing counts with near-perfect accuracy across all four strata.

E26 shows that explicitly preserving degree-occupancy sectors does not generally restore ordinary cycle prediction.

These findings are compatible.

The off-regular representation can be strongly organized by degree mixing while its cycle information remains difficult to expose.

E26 further indicates that:

* some cycle information is recoverable by sector masses;
* some requires within-sector shape;
* and some remains inaccessible even after degree-sector labels are retained.

The combined interpretation is:

> The nonregular QuIC geometry is dominated by degree-conditioned topology, but the failure of the ordinary cycle hierarchy cannot be attributed solely to the final global sort.

#### Relationship to E23

E23 showed that global sorting can radically reorganize the raw probability geometry.

On regular cubic graphs, sorting greatly improves cycle and girth accessibility relative to canonical raw coordinates.

On the heterogeneous complete census, sorting removes useful degree-role and connectivity information.

E26 refines the second result by introducing an intermediate quotient.

R3 removes exact bitstring identities but preserves coarse degree-role occupancy.

Its selective improvements show that some of the information lost by global sorting can be recovered without returning to a fully canonical raw basis.

The recovery is incomplete and family dependent.

Thus, the three readout levels can be viewed as:

1. canonical raw coordinates retain exact basis-state identity;
2. degree-sector sorting retains coarse degree-role identity;
3. global sorting retains only probability rank.

E26 shows that the middle level can help, but it does not uniformly dominate either endpoint.

#### Decision on the deferred degree-encoded arm

The notebook states that the normalized degree-encoded arm should be added if R3 materially improves over R0.

That condition is met.

Positive paired intervals occur for:

* S2 C4;
* S2 C5;
* S3 C3;
* and several weaker cells.

The degree-encoded follow-up is therefore triggered by the notebook’s own decision rule.

That follow-up would distinguish two possibilities.

1. **Topology-induced degree roles**

   The flat circuit already creates probability sectors associated with vertex-degree classes, and preserving those sectors exposes additional structure.

2. **Explicitly encoded degree roles**

   Degree-dependent initial rotations may strengthen, weaken, or reorganize the same sector information.

Without the degree-encoded arm, E26 characterizes only the flat-encoder circuit.

#### What the experiment establishes

The completed results establish that:

1. **Degree-sector mass and degree-sector sorting define numerically permutation-invariant readouts.**

2. **The unsorted E6 circuit can be regenerated consistently with the stored globally sorted representation.**

3. **Preserving degree-sector membership improves selected cycle targets.**

4. **The strongest broad improvement occurs in the bimodal stratum.**

   R2 or R3 strongly improves C4 and C6, while R3 improves C5.

5. **Sector sorting substantially recovers triangle prediction in the skewed stratum.**

   The score rises from (0.056) to (0.431).

6. **Several positive error reductions do not yield useful final prediction.**

   S3 C5 and C6 remain below zero.

7. **The near-regular and hub strata do not show a general R3 advantage.**

8. **Sector masses alone carry substantial information for several S1 and S2 targets.**

9. **Within-sector rank shape is important for selected targets, particularly S2 C5 and S3 C3.**

10. **Random graph-specific sector reassignment destroys predictive alignment.**

11. **Global sorting is not established as the general cause of off-regularity failure.**

12. **The result triggers the planned degree-encoded follow-up arm.**

E26 therefore provides evidence for selective information loss under global sorting but not a universal architectural bottleneck.

#### Necessary qualifications

The E26 decoder does not reproduce the exact E6 analysis protocol.

E26 uses:

* complete 16,384-dimensional vectors;
* train-only feature standardization;
* a reduced ridge grid beginning at (10^{-8});
* explicit shuffled inner folds;
* mean fold and pooled out-of-fold statistics.

The original E6 analyses used different truncation, scaling, regularization, and reporting choices.

E26 is internally controlled because every representation uses the same protocol. Its R0 scores should not be presented as direct reproductions of the published E6 values.

The strongest paper-facing contrasts should be rerun under the exact E6 probe protocol or clearly identified as a separate full-vector standardized ablation.

The complete R0 and R3 matrices have:

$$16{,}384\text{ features and }400\text{ graphs}.$$

The standardized design matrices are therefore severely rank deficient.

The notebook suppresses linear-algebra warnings. High-dimensional ridge results may be sensitive to:

* scaling;
* regularization range;
* inner-fold construction;
* numerical solver;
* and low-variance directions.

E10 showed that such sensitivity is real for QuIC probes.

The R0-equals-producer gate is applied to five graphs per stratum rather than all 1,600 graphs.

The relabeling test also uses five graphs per stratum and 20 permutations per graph.

These are strong spot checks but not exhaustive validation.

R3 is not merely R0 with less destructive sorting.

It incorporates graph-derived degree-class information into the readout.

Its gains demonstrate value from this hybrid degree-conditioned quotient, not a free recovery from the probability multiset alone.

R2 and R3 have different dimensions:

* R2 has 64–315 features;
* R3 has 16,384 features.

Their raw scores do not isolate information content from feature dimension and regularization behavior.

The paired bootstrap resamples fixed out-of-fold errors.

It does not:

* refit the model;
* regenerate the folds;
* or repeat hyperparameter selection.

Its intervals describe graph-level variation under the fitted cross-validation procedure, not full pipeline uncertainty.

The bootstrap seeds use Python’s built-in `hash()` function.

Unless `PYTHONHASHSEED` is fixed, the exact bootstrap intervals may vary across Python processes.

The random-sector control also depends on graph enumeration index and uses a different random assignment for every graph.

It is not a stable graph representation and is not a clean matched null.

No multiple-comparison correction is applied across:

$$4\text{ strata}\times4\text{ targets}=16$$

R3-minus-R0 intervals.

At a nominal 95% level, some positive intervals could occur by chance across the family.

The S2 C6 point difference is large, but its interval is extremely broad:

$$[-0.361,1.822].$$

It should remain descriptive.

The target means across strata average positive and negative $$R^2$$ values without accounting for target variance. They are useful summaries but not inferential statistics.

The experiment evaluates only:

* one graph order;
* four sampled degree sequences;
* a flat encoder;
* one circuit repetition;
* one fixed angle schedule;
* exact ideal probabilities.

The four strata are sampled graph families rather than exhaustive fixed-degree-sequence censuses.

No finite-shot experiment tests whether degree-sector readouts are operationally recoverable.

Finally, the degree-encoded arm is absent even though the notebook’s decision rule is met.

The current experiment should be described as the flat-encoder phase of the ablation rather than the completed sorting-mechanism study.

#### Overall assessment

E26 rules out a simple explanation for QuIC’s off-regularity behavior.

Global sorting does discard useful degree-conditioned information in some settings. The clearest examples are:

* S2 4-cycles;
* S2 5-cycles;
* S3 triangles.

Degree-sector masses also recover substantial S2 C6 information descriptively.

However, the effect is not general.

R3 sharply degrades near-regular triangle prediction, leaves most hub-stratum results unchanged, and does not produce positive C5 or C6 prediction in the skewed and hub strata.

The random-sector control confirms that arbitrary graph-specific reassignment destroys alignment, but it is too destructive and insufficiently matched to quantify the value of genuine degree sectors.

The strongest interpretation is therefore selective:

> Preserving degree-occupancy sectors before sorting can recover structural coordinates that are erased by the global probability quotient, particularly in the bimodal degree family and for skewed-stratum triangles. The effect is not universal: sector sorting can also degrade strong targets and does not restore the deeper cycle hierarchy in the most irregular strata. Global sorting is therefore one source of off-regular information loss, but it is not the general architectural bottleneck.

By the notebook’s own decision rule, the normalized degree-encoded arm should be run before E26 is treated as complete.



### E26R - Protocol-Matched Confirmation of Degree-Sector Readouts

#### Experimental purpose

E26R reruns four decisive E26 representation comparisons under the exact ridge-probe protocol used in E6.

The original E26 comparison was internally controlled, but its decoder differed from E6 in several ways:

* feature standardization;
* a truncated ridge grid;
* shuffled inner folds;
* and a different evaluation implementation.

Those changes materially altered the R0 globally sorted baseline relative to the established E6 results.

E26R therefore evaluates four selected stratum-target cells using:

* raw representation coordinates with no standardization;
* explicit five-fold outer fitting;
* inner five-fold `RidgeCV`;
* the complete E6 ridge grid;
* mean outer-fold test $$R^2$$ as the primary score;
* and the complete 16,384-dimensional probability representations.

The four selected cells are:

| Stratum         | Target  | Intended role                    |
| --------------- | ------- | -------------------------------- |
| S2 bimodal      | $$C_4$$ | Positive sector contrast         |
| S2 bimodal      | $$C_5$$ | Positive sector contrast         |
| S3 skewed       | $$C_3$$ | Positive sector contrast         |
| S1 near regular | $$C_3$$ | Intended negative counterexample |

The last cell does not remain a negative counterexample under the matched protocol.

#### Graph families

The experiment reuses three of the four fixed-degree-sequence E6 strata:

| Stratum         | Locked degree sequence | Graphs |
| --------------- | ---------------------- | -----: |
| S1 near regular | $$(4,4,3^{10},2,2)$$   |    400 |
| S2 bimodal      | $$(4^7,2^7)$$          |    400 |
| S3 skewed       | $$(5,5,4,4,3^6,2^4)$$  |    400 |

The S4 hub stratum is not evaluated in E26R.

Every comparison occurs within one fixed degree sequence. Variation in the readouts and targets therefore reflects topology within the degree class rather than differences in the degree multiset.

#### Circuit and probability representations

E26R regenerates the unsorted ideal probabilities from the E6 flat-encoder circuit:

$$R_X(2.875)^{\otimes14},$$

followed by:

* one edgewise $$R_{ZZ}(2.0)$$ layer;
* one uniform $$R_X(0.1)$$ mixer;
* one repetition.

The complete probability vector has dimension:

$$2^{14}=16{,}384.$$

The circuit does not directly encode vertex degree.

#### Degree-occupancy sectors

Let the graph’s distinct degree classes be:

$$d_1<d_2<\cdots<d_m.$$

For each basis state $$z\in{0,1}^{14}$$, define its degree-occupancy signature:

$$\kappa_G(z)=\left(\sum_{i:\deg(i)=d_1}z_i,\ldots,\sum_{i:\deg(i)=d_m}z_i\right).$$

The signature records how many excited qubits belong to each degree class.

E26R compares four representations.

##### R0 - Global probability sorting

$$R_0(G)=\text{sort}_{\downarrow}{p_G(z):z\in{0,1}^{14}}.$$

R0 retains the complete probability multiset but removes all bitstring and degree-sector identities.

##### R2 - Degree-sector masses

$$R_2(G)*\kappa=\sum*{z:\kappa_G(z)=\kappa}p_G(z).$$

R2 retains only the total probability mass assigned to each degree-occupancy sector.

Its dimensions are:

| Stratum         | R2 dimension |
| --------------- | -----------: |
| S1 near regular |           99 |
| S2 bimodal      |           64 |
| S3 skewed       |          315 |

##### R3 - Within-sector probability sorting

$$R_3(G)=\mathop{\Vert}*{\kappa}\text{sort}*{\downarrow}{p_G(z):\kappa_G(z)=\kappa}.$$

R3 retains the complete probability multiset and the degree-occupancy sector of each probability, while discarding exact bitstring identity within each sector.

Its dimension is:

$$16{,}384.$$

##### R3-random - Random sector reassignment

The complete probability vector is randomly permuted before values are assigned to the sector blocks and sorted within those blocks.

This destroys the genuine relationship between probabilities and degree sectors while retaining:

* the complete probability multiset;
* the number of sector blocks;
* sector-block sizes;
* and total representation dimension.

#### Exact E6 decoder protocol

For each outer fold, E26R fits:

$$\widehat f=\text{RidgeCV}\left(\alpha\in{10^{-14},10^{-13},\ldots,10^2},\text{cv}=5\right)$$

using the raw representation coordinates.

The primary reported score is:

$$\overline{R^2}=\frac{1}{5}\sum_{j=1}^{5}R_j^2.$$

The outer folds use:

* five shuffled partitions;
* seed zero.

No feature standardization is applied.

This matches the actual E6 decoder protocol.

#### Representation validation

For every graph used in E26R, the notebook regenerates the unsorted circuit probabilities and verifies:

$$\max_i|R_0(G)*i-\mathbf p*{\text{E6}}(G)_i|<10^{-9}.$$

The gate is applied to all:

$$3\times400=1{,}200$$

graphs in the three evaluated strata.

Every regenerated globally sorted vector therefore agrees with the E6 producer artifact.

E26R does not rerun the full E26 sector-cardinality and relabeling-invariance suite. Those properties are inherited from E26 rather than independently reestablished here.

#### Reproduction of the E6 R0 baseline

The R0 values exactly reproduce the established E6 results for the four selected cells:

| Stratum         | Target  |  E26R R0 | Recorded E6 |
| --------------- | ------- | -------: | ----------: |
| S2 bimodal      | $$C_4$$ |    0.295 |       0.295 |
| S2 bimodal      | $$C_5$$ |    0.284 |       0.284 |
| S3 skewed       | $$C_3$$ | (-0.047) |    (-0.047) |
| S1 near regular | $$C_3$$ |    0.449 |       0.449 |

This confirms that E26R’s globally sorted arm is directly comparable with the E6 off-regularity record.

The reproduction is verified by comparison with the recorded E6 values, although the notebook does not encode those values as a hard assertion.

#### Complete protocol-matched results

| Stratum         | Target  |   R0 global sort | R2 sector mass | R3 sector sort |        R3-random |
| --------------- | ------- | ---------------: | -------------: | -------------: | ---------------: |
| S2 bimodal      | $$C_4$$ |    0.295 ± 0.137 |  0.783 ± 0.053 |  0.345 ± 0.151 | (-0.066) ± 0.057 |
| S2 bimodal      | $$C_5$$ |    0.284 ± 0.135 |  0.463 ± 0.064 |  0.306 ± 0.102 | (-0.014) ± 0.014 |
| S3 skewed       | $$C_3$$ | (-0.047) ± 0.042 |  0.807 ± 0.025 |  0.632 ± 0.206 | (-0.027) ± 0.016 |
| S1 near regular | $$C_3$$ |    0.449 ± 0.714 |  0.987 ± 0.004 |  0.962 ± 0.066 | (-0.016) ± 0.020 |

The central result is not simply that R3 improves upon R0.

In every selected cell:

$$R_2>R_3.$$

The sector-mass representation is therefore the strongest tested readout across all four confirmations.

#### S2 bimodal 4-cycle prediction

The globally sorted baseline reaches:

$$R^2_{R0}=0.295.$$

Degree-sector sorting raises the score only modestly:

$$R^2_{R3}=0.345.$$

The sector-mass representation produces a much larger result:

$$R^2_{R2}=0.783.$$

The mean-fold improvements are:

$$R^2_{R3}-R^2_{R0}=0.050,$$

and:

$$R^2_{R2}-R^2_{R0}=0.488.$$

The paired bootstrap, computed from the assembled out-of-fold predictions, gives:

| Contrast           | Bootstrap mean |   95% interval |
| ------------------ | -------------: | -------------: |
| R3 minus R0        |       (+0.049) | [0.011, 0.086] |
| R2 minus R0        |       (+0.452) | [0.363, 0.549] |
| R3 minus R3-random |       (+0.421) | [0.302, 0.523] |

Both genuine sector readouts improve upon global sorting.

The substantially larger R2 result shows that aggregate probability allocation among degree sectors carries most of the restored C4 signal.

Within-sector probability shape adds little beyond those masses and may dilute their linear accessibility.

#### S2 bimodal 5-cycle prediction

The globally sorted baseline is:

$$R^2_{R0}=0.284.$$

R3 reaches:

$$R^2_{R3}=0.306,$$

while R2 reaches:

$$R^2_{R2}=0.463.$$

The mean-fold differences are:

$$R^2_{R3}-R^2_{R0}=0.022,$$

and:

$$R^2_{R2}-R^2_{R0}=0.179.$$

The paired bootstrap results are:

| Contrast           | Bootstrap mean |    95% interval |
| ------------------ | -------------: | --------------: |
| R3 minus R0        |       (+0.022) | [-0.038, 0.083] |
| R2 minus R0        |       (+0.164) |  [0.086, 0.247] |
| R3 minus R3-random |       (+0.328) |  [0.217, 0.425] |

The R3-minus-R0 interval includes zero.

E26R therefore does not confirm that preserving within-sector rank shape improves S2 C5 over global sorting.

Sector masses do improve the target:

$$0.284\rightarrow0.463,$$

with a positive paired interval.

The original E26 interpretation—that within-sector shape was particularly important for S2 C5—is not supported under the E6 probe.

#### S3 skewed triangle prediction

The globally sorted representation is below the prediction floor:

$$R^2_{R0}=-0.047.$$

Both sector readouts recover substantial triangle information:

$$R^2_{R2}=0.807,$$

and:

$$R^2_{R3}=0.632.$$

The corresponding mean-fold changes are:

$$R^2_{R2}-R^2_{R0}=0.854,$$

and:

$$R^2_{R3}-R^2_{R0}=0.679.$$

The paired bootstrap gives:

| Contrast           | Bootstrap mean |   95% interval |
| ------------------ | -------------: | -------------: |
| R3 minus R0        |       (+0.682) | [0.508, 0.803] |
| R2 minus R0        |       (+0.841) | [0.793, 0.889] |
| R3 minus R3-random |       (+0.665) | [0.492, 0.790] |

This is the strongest evidence that global sorting removes useful degree-conditioned structure.

However, the stronger R2 result again indicates that sector probability mass, not within-sector rank shape, is the principal recovered coordinate.

#### S1 near-regular triangle prediction

S1 was selected as the negative counterexample because the original E26 probe produced:

$$R^2_{R0}=0.911,$$

and:

$$R^2_{R3}=0.115.$$

Under the E6 protocol, that result reverses.

The matched scores are:

$$R^2_{R0}=0.449,$$

$$R^2_{R2}=0.987,$$

and:

$$R^2_{R3}=0.962.$$

The paired bootstrap results are:

| Contrast           | Bootstrap mean |   95% interval |
| ------------------ | -------------: | -------------: |
| R3 minus R0        |       (+0.421) | [0.132, 0.840] |
| R2 minus R0        |       (+0.435) | [0.127, 0.886] |
| R3 minus R3-random |       (+0.988) | [0.932, 1.027] |

The intended negative control is therefore a strong positive result.

Both degree-sector readouts nearly solve triangle count, while global sorting is only moderately predictive and highly unstable across folds:

$$0.449\pm0.714.$$

This is the most consequential correction to the original E26 interpretation.

The notebook’s final prose still anticipates “a near-zero negative counterexample.” That expectation is stale and contradicted by the completed output.

#### Comparison with the original E26 results

| Stratum | Target  | Representation | Original E26 |     E26R |
| ------- | ------- | -------------- | -----------: | -------: |
| S2      | $$C_4$$ | R0             |        0.735 |    0.295 |
| S2      | $$C_4$$ | R2             |        0.934 |    0.783 |
| S2      | $$C_4$$ | R3             |        0.918 |    0.345 |
| S2      | $$C_5$$ | R0             |        0.748 |    0.284 |
| S2      | $$C_5$$ | R2             |        0.484 |    0.463 |
| S2      | $$C_5$$ | R3             |        0.837 |    0.306 |
| S3      | $$C_3$$ | R0             |        0.056 | (-0.047) |
| S3      | $$C_3$$ | R2             |        0.065 |    0.807 |
| S3      | $$C_3$$ | R3             |        0.431 |    0.632 |
| S1      | $$C_3$$ | R0             |        0.911 |    0.449 |
| S1      | $$C_3$$ | R2             |        0.986 |    0.987 |
| S1      | $$C_3$$ | R3             |        0.115 |    0.962 |

The protocol correction affects the representations differently.

Most notably:

* S1 R3 rises from (0.115) to (0.962);
* S3 R2 rises from (0.065) to (0.807);
* S2 R3 C5 falls from (0.837) to (0.306).

The original E26 representation rankings were therefore strongly probe dependent.

The robust pattern in E26R is not that R3 restores all four selected targets. It is that R2 sector mass is consistently strong.

#### Sector mass versus within-sector shape

Across all four cells:

| Stratum and target | R2 sector mass | R3 sector sort | R2 minus R3 |
| ------------------ | -------------: | -------------: | ----------: |
| S2 $$C_4$$         |          0.783 |          0.345 |    (+0.438) |
| S2 $$C_5$$         |          0.463 |          0.306 |    (+0.157) |
| S3 $$C_3$$         |          0.807 |          0.632 |    (+0.175) |
| S1 $$C_3$$         |          0.987 |          0.962 |    (+0.025) |

Sector mass equals or exceeds sector sorting everywhere.

The result suggests that the structural signal is concentrated in:

$$\left{\sum_{z:\kappa_G(z)=\kappa}p_G(z)\right}_{\kappa},$$

rather than in the detailed distribution of probability ranks within each sector.

R3 retains all information present in R2 in an unrestricted information-theoretic sense, because each sector mass can be recovered by summing its R3 block.

Nevertheless, a single linear ridge probe does not automatically perform those block sums efficiently in a 16,384-dimensional feature space.

R2 explicitly performs that aggregation before regression and produces a much more accessible coordinate system.

The R2 advantage can therefore reflect both:

* genuine concentration of the signal in sector masses;
* and improved inductive bias from an explicit low-dimensional aggregation.

#### Does E26R establish a sorting bottleneck?

E26R supplies evidence that global sorting removes useful degree-sector association in the four selected cells.

R3 improves upon R0 with an interval excluding zero for:

* S2 C4;
* S3 C3;
* S1 C3.

It does not do so for S2 C5.

R2 improves upon R0 with a positive interval in all four cells.

The strongest supported statement is therefore:

> Global sorting discards degree-sector membership that is useful for selected cycle targets, while coarse sector masses provide the most consistently accessible replacement coordinates.

This is stronger than the original E26 conclusion for S1 and S3.

It is weaker than a universal bottleneck claim because:

* only four of the original sixteen cells are rerun;
* one R3 contrast is unresolved;
* the S4 stratum is absent;
* and R2/R3 use graph-derived degree information not present in R0.

E26R does not establish that global sorting is the sole cause of QuIC’s off-regularity behavior.

#### Relationship to E25R

E25R showed that the globally sorted E6 representation nearly perfectly recovers joint-degree edge-mixing counts.

E26R shows that degree-sector probability masses also strongly recover selected cycle totals.

These are related but distinct degree-conditioned structures.

E25R concerns the graph statistic:

$$M_{ab}=#{\text{edges connecting degree classes }a\text{ and }b}.$$

E26R concerns the circuit readout:

$$h_\kappa=\sum_{z:\kappa_G(z)=\kappa}p_G(z).$$

The combined evidence suggests that the off-regular representation contains a strong degree-role organization at multiple levels:

* edge mixing is present in the globally sorted probability geometry;
* degree-sector mass retains additional cycle information that global sorting partially obscures.

The result supports a degree-conditioned explanation of off-regular structure, but it does not show that the sector masses are equivalent to edge-mixing counts.

#### Random-sector control

R3 substantially outperforms R3-random in all four cells.

The paired intervals are entirely positive.

This confirms that arbitrary graph-specific probability reassignment to the sector blocks destroys useful alignment.

The control remains imperfect.

Each graph receives a different random assignment based on:

$$20250717+\text{graph index}.$$

The resulting representation is:

* dependent on dataset enumeration;
* not a stable graph function;
* and not aligned consistently across graphs.

Its negative scores are therefore best interpreted as a destructive sanity check.

They do not quantify how much of R3’s performance is specifically attributable to semantically meaningful degree sectors.

#### What the experiment establishes

The completed results establish that:

1. **The globally sorted R0 arm reproduces the exact E6 values for all four selected cells.**

2. **The E26 representation comparison is highly sensitive to the decoder protocol.**

3. **The intended S1 negative counterexample reverses under the E6 probe.**

   R3 reaches (0.962) and R2 reaches (0.987), compared with (0.449) for R0.

4. **Sector masses improve upon global sorting in all four selected cells.**

5. **Sector sorting improves upon global sorting in three of the four selected cells.**

6. **The S2 C5 sector-sorting gain is not bounded away from zero.**

7. **Sector mass is stronger than sector sorting in every selected cell.**

8. **The principal restored signal appears to lie in aggregate degree-sector probability allocation.**

9. **Global sorting removes useful degree-sector association for selected targets.**

10. **The four-cell result does not establish a universal sorting bottleneck.**

11. **The random-sector control confirms that arbitrary graph-specific block assignment destroys decodability, but it is not a clean matched null.**

12. **The original E26 S1 counterexample and within-sector-shape interpretation should be replaced.**

E26R therefore strengthens the degree-sector readout hypothesis while shifting its mechanism from within-sector rank shape to sector mass.

#### Necessary qualifications

E26R evaluates only four cells selected after inspection of the original E26 results.

The cells are not an unbiased sample of:

$$4\text{ strata}\times4\text{ targets}=16$$

possible comparisons.

The bootstrap intervals should therefore not be interpreted as confirmatory familywise inference over the complete E26 grid.

A full protocol-matched rerun of all sixteen cells is required for a general statement about how often R2 or R3 improves upon global sorting.

The S1 cell was selected as a negative counterexample but reversed under the matched protocol. This reduces concern that only positive results were retained, but it does not remove the post-selection issue.

The primary table reports mean outer-fold $$R^2$$.

The paired bootstrap instead resamples the assembled out-of-fold errors and computes pooled $$R^2$$ differences.

These are different estimands.

Consequently, the bootstrap mean does not exactly equal the difference between the two displayed mean-fold scores.

The bootstrap resamples fixed out-of-fold predictions.

It does not refit:

* the ridge model;
* the inner regularization selection;
* or the outer folds.

Its intervals describe graph-level variation conditional on the completed cross-validation procedure.

R2 and R3 are not capacity matched.

R2 has between 64 and 315 coordinates, while R3 has 16,384 coordinates.

The same fixed ridge grid may regularize those spaces differently.

The stronger R2 results may partly reflect a better inductive bias and lower-dimensional feature space rather than strictly greater information content.

R3 contains enough information to reconstruct R2 through block summation, but that operation is not directly imposed on the linear decoder.

R2 and R3 also incorporate the graph’s degree partition into the readout.

They are hybrid graph-and-circuit constructions, not transformations of the probability multiset alone.

Their improvement over R0 does not prove that the quantum circuit independently learned degree classes.

The notebook suppresses linear-algebra warnings.

R0 and R3 use 16,384 features for only 400 graphs, with ridge penalties extending to:

$$10^{-14}.$$

E10 showed that such high-dimensional QuIC probes can depend on low-variance directions and weak regularization.

The R0 reproduction gate strongly supports implementation consistency, but an independent dual or singular-value solver check would strengthen the large R3 results.

E26R verifies R0 against the producer vector for every evaluated graph.

It does not rerun:

* all sector-cardinality assertions;
* probability conservation by sector;
* or permutation-invariance tests.

Those checks are inherited from E26.

The random-sector control remains dependent on graph enumeration index.

Stable cryptographic seeds correct the bootstrap reproducibility issue but do not correct the construction of R3-random itself.

No correction is applied for the multiple selected representation-target contrasts.

The experiment uses:

* exact statevector probabilities;
* one flat-encoder circuit;
* one graph order;
* and three sampled degree-sequence strata.

The S4 hub family is absent.

No finite-shot experiment evaluates whether the sector-mass coordinates can be recovered operationally.

The normalized degree-encoded arm also remains untested.

Finally, E26R does not compare the sector representations with simple classical baselines derived directly from:

* degree mixing;
* cycle counts;
* the adjacency spectrum;
* or folklore 2-WL.

The experiment establishes structural accessibility, not quantum advantage.

#### Overall assessment

E26R provides the required protocol correction and changes the mechanism suggested by E26.

The globally sorted arm reproduces the E6 baselines exactly.

Under that matched decoder:

* S2 C4 improves from (0.295) to (0.783) using sector mass;
* S2 C5 improves from (0.284) to (0.463);
* S3 C3 improves from (-0.047) to (0.807);
* S1 C3 improves from (0.449) to (0.987).

Degree-sector sorting also improves three cells, but it is consistently weaker than the low-dimensional mass representation and provides no confirmed advantage for S2 C5.

The intended S1 negative counterexample disappears. Rather than showing that sector preservation damages near-regular triangles, the matched result shows that degree-sector masses and ranks almost completely recover them.

The appropriate central claim is:

> Under the exact E6 raw-coordinate nested-ridge protocol, degree-occupancy sector readouts recover substantial structural information that is obscured by global probability sorting. Sector masses improve all four selected targets, raising S2 4-cycle prediction from (0.295) to (0.783), S3 triangle prediction from (-0.047) to (0.807), and near-regular triangle prediction from (0.449) to (0.987). Within-sector sorting also improves three cells but is uniformly weaker than sector mass and does not significantly improve S2 5-cycles. E26R therefore identifies aggregate degree-sector probability allocation—not within-sector rank shape—as the most consistent restored coordinate, while leaving a full sixteen-cell confirmation necessary before global sorting is declared the general off-regularity bottleneck.

### E27 - Conditional Structure Audit

#### Experimental purpose

E27 asks whether the degree-mixing structure identified in E25R is genuinely distinct from the ordinary cycle signal or merely another parameterization of it.

Within each fixed-degree-sequence stratum, joint-degree edge counts and cycle counts can covary. Consequently, near-perfect prediction of the degree-mixing matrix does not by itself establish that QuIC contains a separate degree-mixing coordinate.

E27 evaluates three conditional questions.

1. **Mixing after cycles**

   Residualize the independent degree-mixing basis on:

   $${C_3,C_4,C_5,C_6},$$

   then ask whether QuIC predicts the remaining mixing residual.

2. **Cycles after mixing**

   Residualize each cycle count on the degree-mixing basis, then ask whether QuIC predicts the remaining cycle residual.

3. **Mixing after spectrum**

   Residualize the mixing basis on the complete 14-eigenvalue adjacency spectrum, then ask whether QuIC predicts the remaining residual.

The intended interpretations are:

* mixing that survives cycle residualization is not merely a linear cycle proxy;
* cycle information that survives mixing residualization is not fully mediated by linear degree mixing;
* mixing that survives spectral residualization is not linearly recoverable from the raw eigenvalue coordinates.

The final point must be stated carefully. The implemented spectral nuisance model is linear in the eigenvalues and does not remove arbitrary nonlinear spectral functions.

#### Graph families

The experiment reuses all four E6 fixed-degree-sequence strata.

| Stratum         | Locked degree sequence | Graphs |
| --------------- | ---------------------- | -----: |
| S1 near regular | $$(4,4,3^{10},2,2)$$   |    400 |
| S2 bimodal      | $$(4^7,2^7)$$          |    400 |
| S3 skewed       | $$(5,5,4,4,3^6,2^4)$$  |    400 |
| S4 hub          | $$(6,4,4,3^8,2,2,2)$$  |    400 |

Every analysis is performed within one stratum.

The following quantities are therefore constant:

* graph order;
* number of edges;
* degree multiset;
* number of vertices in each degree class.

The varying structural object is how those fixed degree classes are connected.

#### QuIC representation

E27 reuses the exact sorted probability vectors generated by the E6 flat-encoder circuit.

The circuit uses:

$$R_X(2.875)^{\otimes14},$$

followed by:

* one graph-edge $$R_{ZZ}(2.0)$$ layer;
* one uniform $$R_X(0.1)$$ mixer;
* one repetition.

Degrees are not supplied directly to the circuit.

The feature vector is the first:

$$k=1000$$

coordinates of the complete descending-sorted Born-probability vector.

The second-stage QuIC decoder uses the E6 protocol confirmed in E25R:

* raw QuIC coordinates;
* five shuffled outer folds;
* outer seed zero;
* inner five-fold `RidgeCV`;
* ridge grid:

$$\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2};$$

* mean outer-fold test $$R^2$$.

E6 used the complete 16,384-dimensional vector, while E27 uses the top-1,000 head. E25R showed that this head reproduces the relevant E6 cycle and degree-mixing results to displayed precision.

#### Data and target validation

All 1,600 graph records pass the notebook’s integrity gates.

For every graph, E27 verifies:

* the locked stratum degree sequence;
* exact-vector dimension $$2^{14}$$;
* descending sortedness;
* unit probability mass;
* triangle trace consistency;
* 4-cycle trace consistency.

The trace identities are:

$$\text{tr}(A^3)=6C_3,$$

and:

$$\text{tr}(A^4)=8C_4+2\sum_i d_i^2-\sum_i d_i.$$

All executed cells complete without error.

#### Joint-degree mixing representation

For degree classes $$a\le b$$, define:

$$M_{ab}=#{uv\in E:{\deg u,\deg v}={a,b}}.$$

The observed edge-type matrices have:

| Stratum         | Raw $$M_{ab}$$ columns |
| --------------- | ---------------------: |
| S1 near regular |                      6 |
| S2 bimodal      |                      3 |
| S3 skewed       |                     10 |
| S4 hub          |                      9 |

Within a fixed degree sequence, these columns satisfy the stub constraints:

$$2M_{aa}+\sum_{b\ne a}M_{ab}=an_a.$$

The centered edge-count matrix is reduced through singular-value decomposition.

Singular values smaller than:

$$10^{-8}s_{\max}$$

are discarded.

The resulting ranks are:

| Stratum         | Raw columns | Retained mixing rank |
| --------------- | ----------: | -------------------: |
| S1 near regular |           6 |                    3 |
| S2 bimodal      |           3 |                    1 |
| S3 skewed       |          10 |                    6 |
| S4 hub          |           9 |                    5 |

These ranks match the expected maximum dimensions after imposing the fixed-stub constraints.

The retained SVD scores provide a nonredundant coordinate system for the joint-degree mixing state.

#### Cross-fitted residualization

Residualization occurs inside each E6 outer fold.

For a target $$Y$$ and nuisance bank $$Z$$:

1. nuisance models are fitted on inner partitions of the outer-training set;
2. out-of-fold nuisance predictions produce honest residuals for the outer-training graphs;
3. one nuisance model is fitted on the complete outer-training set;
4. that model produces residuals for the outer-test graphs;
5. the QuIC ridge model is fitted to the outer-training residuals;
6. the model predicts the independently residualized outer-test targets.

The nuisance model is:

* train-only standardization;
* ridge regression;
* generalized cross-validation over:

$$\alpha_{\text{nuisance}}\in{10^{-6},10^{-5.5},\ldots,10^6}.$$

The nuisance model never observes the second-stage outer-test targets during fitting.

This is a valid leakage-controlled two-stage construction for the particular nuisance model being used.

#### Calibration

The two-stage implementation is tested using synthetic targets.

##### Pure nuisance

A target generated almost entirely from the cycle nuisance bank yields:

$$R^2=-0.017$$

after residualization and QuIC decoding.

This is consistent with successful nuisance removal.

##### QuIC-linear signal

A target constructed as a linear combination of QuIC coordinates yields:

$$R^2=1.000.$$

##### Combined nuisance and QuIC signal

A target containing both nuisance and QuIC-linear components yields:

$$R^2=0.977$$

after nuisance residualization.

The calibration shows that the software can:

* remove a synthetic linear nuisance;
* retain a separately encoded QuIC component;
* and decode that surviving component.

It does not establish that the real graph relationships are linear or fully removed by the nuisance models.

#### Raw degree-mixing decodability

The pooled degree-mixing scores reproduce the E25R result in independent-basis form.

| Stratum         | Mixing rank | Raw pooled mixing $$R^2$$ |
| --------------- | ----------: | ------------------------: |
| S1 near regular |           3 |             1.000 ± 0.000 |
| S2 bimodal      |           1 |             1.000 ± 0.000 |
| S3 skewed       |           6 |             0.972 ± 0.005 |
| S4 hub          |           5 |             0.991 ± 0.002 |

The scores are variance weighted across the retained mixing coordinates rather than arithmetic means over redundant $$M_{ab}$$ columns.

The result confirms that the lower-dimensional joint-degree mixing state is itself almost perfectly accessible from QuIC.

#### Mixing after cycle residualization

| Stratum         | Raw mixing $$R^2$$ | Mixing residualized on $$C_3$$–$$C_6$$ | Fold SD |   Change |
| --------------- | -----------------: | -------------------------------------: | ------: | -------: |
| S1 near regular |              1.000 |                                  0.983 |   0.013 | (-0.017) |
| S2 bimodal      |              1.000 |                                  0.583 |   0.071 | (-0.417) |
| S3 skewed       |              0.972 |                                  0.934 |   0.012 | (-0.038) |
| S4 hub          |              0.991 |                                  0.944 |   0.012 | (-0.047) |

Residual mixing remains strongly decodable in every stratum.

##### S1 near regular

The score remains effectively saturated:

$$1.000\rightarrow0.983.$$

The mixing state is therefore not explained by a linear combination of the four cycle totals.

##### S2 bimodal

The score falls substantially:

$$1.000\rightarrow0.583.$$

S2 has only one independent mixing coordinate. Ordinary cycles explain or align with a meaningful portion of that coordinate, but a substantial residual remains accessible.

This is evidence of overlap rather than equivalence.

##### S3 skewed

Residual mixing remains:

$$R^2=0.934.$$

The four cycle totals explain little of the QuIC-accessible degree-mixing geometry.

##### S4 hub

Residual mixing remains:

$$R^2=0.944.$$

As in S1 and S3, degree mixing survives almost intact after linear cycle removal.

#### Interpretation of mixing after cycles

The strongest conclusion from E27 is:

$$\boxed{\text{degree mixing is not merely the ordinary cycle signal under another parameterization}}$$

This conclusion is particularly strong in:

* S1;
* S3;
* S4.

S2 contains substantially more mixing-cycle overlap but still retains a clearly decodable residual coordinate.

The result is conditional on linear ridge nuisance removal. It does not rule out nonlinear relationships between degree mixing and the cycle bank.

#### Mixing after spectral residualization

| Stratum         | Raw mixing $$R^2$$ | Mixing residualized on spectrum | Fold SD |   Change |
| --------------- | -----------------: | ------------------------------: | ------: | -------: |
| S1 near regular |              1.000 |                           0.964 |   0.010 | (-0.036) |
| S2 bimodal      |              1.000 |                           0.667 |   0.080 | (-0.333) |
| S3 skewed       |              0.972 |                           0.932 |   0.009 | (-0.040) |
| S4 hub          |              0.991 |                           0.951 |   0.009 | (-0.040) |

The mixing residual remains highly decodable after linear regression on the 14 adjacency eigenvalues.

The same pattern appears after conditioning jointly on cycles and spectrum:

| Stratum         | Mixing residualized on cycles and spectrum |
| --------------- | -----------------------------------------: |
| S1 near regular |                              0.962 ± 0.011 |
| S2 bimodal      |                              0.649 ± 0.071 |
| S3 skewed       |                              0.917 ± 0.010 |
| S4 hub          |                              0.928 ± 0.014 |

The result supports the limited statement:

> Degree mixing is not exhausted by a linear readout of the raw adjacency eigenvalues.

It does not establish a non-spectral coordinate in the unrestricted sense.

#### Why the spectral result is not a full non-spectral test

The complete spectrum determines nonlinear power sums:

$$\text{tr}(A^k)=\sum_i\lambda_i^k.$$

Within a fixed degree sequence, for example:

$$C_3=\frac{1}{6}\sum_i\lambda_i^3,$$

and:

$$C_4=\frac{1}{8}\left(\sum_i\lambda_i^4-2\sum_i d_i^2+\sum_i d_i\right).$$

A linear ridge model on the raw eigenvalue vector does not automatically represent these polynomial functions.

Consequently, high residual mixing after linear spectral regression can still contain information that is a nonlinear function of the spectrum.

The E27 output does not support the claim:

$$\boxed{\text{degree mixing is non-spectral}}$$

It supports:

$$\boxed{\text{degree mixing is not linearly recoverable from the raw eigenvalue coordinates}}$$

A stronger audit would cross-fit nuisance models using:

* spectral power sums;
* polynomial spectral features;
* RBF kernel regression;
* or the nonlinear spectral models used in E11.

The direct exact-cospectral analyses in E14 remain the cleaner evidence of information beyond the adjacency spectrum.

#### Cycle totals before and after mixing residualization

##### S1 near regular

| Target  | Raw $$R^2$$ | Residual after mixing | Fold SD |
| ------- | ----------: | --------------------: | ------: |
| $$C_3$$ |       0.449 |                 0.565 |   0.463 |
| $$C_4$$ |       0.095 |                 0.096 |   0.047 |
| $$C_5$$ |    (-0.017) |              (-0.013) |   0.060 |
| $$C_6$$ |    (-0.021) |              (-0.019) |   0.010 |

Triangle prediction survives and numerically improves after removing linear mixing dependence:

$$0.449\rightarrow0.565.$$

This can occur when degree mixing acts as a suppressor or nuisance for a separate triangle direction.

The large fold variability remains:

$$0.565\pm0.463.$$

Four-cycle prediction is weak but unchanged. Five- and 6-cycle prediction remain at the floor.

##### S2 bimodal

| Target  | Raw $$R^2$$ | Residual after mixing | Fold SD |
| ------- | ----------: | --------------------: | ------: |
| $$C_3$$ |       0.991 |                 0.988 |   0.003 |
| $$C_4$$ |       0.295 |                 0.184 |   0.145 |
| $$C_5$$ |       0.284 |                 0.185 |   0.122 |
| $$C_6$$ |       0.296 |                 0.261 |   0.117 |

Triangle accessibility is essentially unchanged:

$$0.991\rightarrow0.988.$$

The deeper cycle scores decline but remain positive:

$$C_4:0.295\rightarrow0.184,$$

$$C_5:0.284\rightarrow0.185,$$

$$C_6:0.296\rightarrow0.261.$$

S2 therefore contains both:

* a degree-mixing channel;
* cycle information not fully mediated by that channel.

The overlap is strongest for C4 and C5.

##### S3 skewed

| Target  | Raw $$R^2$$ | Residual after mixing | Fold SD |
| ------- | ----------: | --------------------: | ------: |
| $$C_3$$ |    (-0.047) |              (-0.017) |   0.013 |
| $$C_4$$ |    (-0.018) |              (-0.037) |   0.019 |
| $$C_5$$ |    (-0.019) |              (-0.018) |   0.019 |
| $$C_6$$ |    (-0.023) |              (-0.019) |   0.023 |

All cycle targets are at the prediction floor before residualization and remain there afterward.

This does not show that the cycle signal is mediated by mixing.

There is no positive cycle signal to mediate.

The correct S3 conclusion is:

> QuIC contains a strong degree-mixing coordinate but no demonstrated ordinary cycle coordinate under the tested probe.

##### S4 hub

| Target  | Raw $$R^2$$ | Residual after mixing | Fold SD |
| ------- | ----------: | --------------------: | ------: |
| $$C_3$$ |       0.378 |                 0.303 |   0.280 |
| $$C_4$$ |    (-0.034) |              (-0.009) |   0.008 |
| $$C_5$$ |    (-0.050) |              (-0.032) |   0.047 |
| $$C_6$$ |    (-0.038) |              (-0.021) |   0.021 |

Triangle count retains a moderate residual signal:

$$0.378\rightarrow0.303.$$

The deeper cycles remain at the prediction floor.

S4 therefore contains:

* an almost perfectly accessible degree-mixing coordinate;
* a weaker but distinct triangle coordinate;
* no demonstrated C4–C6 channel.

#### Why the notebook’s cycle-mediation flags are misleading

The notebook computes the unweighted mean of the four residual cycle scores and declares a stratum “cycle mediated by mixing” when that mean is below:

$$0.10.$$

This produces:

* `True` for S3;
* `True` for S4.

Neither flag supports its intended interpretation.

##### S3

All four raw cycle scores were already approximately zero.

The residual mean cannot establish mediation of a signal that was absent before conditioning.

##### S4

Triangle count remains positively decoded at:

$$R^2=0.303.$$

Averaging it with three null deeper-cycle targets reduces the mean to:

$$0.060$$

and incorrectly labels the entire cycle family as mediated.

Cycle targets are individually meaningful and must be interpreted separately.

The notebook’s mean-based mediation flag should not appear in the paper.

#### Per-stratum conditional interpretation

| Stratum         | Degree mixing after cycles | Cycle channel after mixing               | Supported interpretation                             |
| --------------- | -------------------------: | ---------------------------------------- | ---------------------------------------------------- |
| S1 near regular |                      0.983 | Triangle survives; deeper cycles weak    | Distinct mixing and triangle channels                |
| S2 bimodal      |                      0.583 | C3 nearly exact; C4–C6 remain positive   | Overlapping but distinct mixing and cycle channels   |
| S3 skewed       |                      0.934 | All cycle targets at floor               | Strong mixing channel; no demonstrated cycle channel |
| S4 hub          |                      0.944 | C3 remains 0.303; deeper cycles at floor | Strong mixing channel plus weaker triangle channel   |

The results do not support one universal off-regular mechanism.

The common feature is the degree-mixing coordinate.

The cycle channel varies substantially by degree-sequence family.

#### Matched structural witnesses

E27 identifies exact-integer graph pairs of two types.

1. Graphs with identical:

   $$(C_3,C_4,C_5,C_6)$$

   but different joint-degree edge counts.

2. Graphs with identical joint-degree edge counts but different cycle totals.

The largest displayed differences are:

| Stratum         | Equal cycles: maximum displayed $$M_{ab}$$ $$L_1$$ gap | Equal mixing: maximum displayed cycle $$L_1$$ gap |
| --------------- | -----------------------------------------------------: | ------------------------------------------------: |
| S1 near regular |                                                     16 |                                                24 |
| S2 bimodal      |                                                      4 |                                                34 |
| S3 skewed       |                                                     22 |                                                26 |
| S4 hub          |                                                     14 |                                                30 |

These witnesses demonstrate that, within each sampled stratum:

* cycle totals do not determine degree mixing;
* degree mixing does not determine cycle totals.

The search is more complete than the notebook description suggests.

The code examines every pair inside every exact-equality bucket and retains the largest gap. It is exhaustive over the observed equality classes, although it is not a search beyond the 400 sampled graphs in each stratum.

The witnesses illustrate structural non-equivalence. They do not independently establish that QuIC has learned two statistically independent channels.

#### Relationship to E25R

E25R established that the flat-encoder sorted QuIC representation nearly perfectly reconstructs joint-degree mixing.

E27 strengthens that result.

After linear removal of:

* all four ordinary cycle totals;
* the complete raw eigenvalue vector;
* or both together,

the residual mixing state remains strongly decodable.

The combined result supports:

> QuIC’s off-regular geometry contains a robust degree-mixing coordinate that is not merely the linearly predictable component of ordinary cycle counts or raw adjacency eigenvalues.

E27 also narrows the cycle interpretation.

* S2 retains separate cycle and mixing channels.
* S1 and S4 retain triangle information beyond mixing.
* S3 shows only the mixing channel.

#### Relationship to E26R

E26R showed that degree-occupancy sector masses recover selected cycle targets hidden by global probability sorting.

E27 analyzes a different object:

* E26R uses probability mass assigned to degree-occupancy sectors;
* E27 uses graph-level edge counts between vertex-degree classes.

Both findings indicate strong degree-conditioned organization, but they should not be conflated.

The E27 results do not show that the mixing basis and sector-mass representation are equivalent or interchangeable.

#### What the experiment establishes

The completed results establish that:

1. **The independent joint-degree mixing state remains nearly perfectly accessible under the E6 probe.**

2. **Mixing remains strongly decodable after linear removal of ordinary cycle counts.**

   The residual scores range from:

   $$0.583\text{ to }0.983.$$

3. **S1, S3, and S4 lose very little mixing accessibility after cycle residualization.**

4. **S2 exhibits substantial mixing-cycle overlap but retains a strong independent residual coordinate.**

5. **Mixing remains strongly decodable after linear regression on the raw adjacency eigenvalues.**

6. **This establishes a beyond-linear-spectrum result, not unrestricted non-spectrality.**

7. **Triangle information survives mixing residualization in S1, S2, and S4.**

8. **S2 also retains positive residual C4, C5, and C6 accessibility.**

9. **S3 contains no demonstrated ordinary cycle channel before or after conditioning.**

10. **The notebook’s mean cycle-mediation flags are not scientifically reliable.**

11. **Exact matched pairs demonstrate that degree mixing and cycle totals do not determine one another within any sampled stratum.**

12. **The common off-regular coordinate is degree mixing, while the independent cycle channel is family dependent.**

E27 therefore strengthens the degree-mixing explanation while rejecting a simple one-channel account of every nonregular stratum.

#### Necessary qualifications

The notebook calls itself an “independence” audit.

The implemented procedure establishes conditional linear accessibility after ridge residualization. It does not prove statistical independence.

Both nuisance relationships may be nonlinear.

A high residual score means that QuIC predicts what remains after the selected ridge nuisance model. It does not establish that the residual is independent of the nuisance variables.

The spectrum audit is especially limited.

Linear regression on raw eigenvalues does not remove nonlinear spectral functions such as:

$$\sum_i\lambda_i^k.$$

The result must not be described as proving that degree mixing is non-spectral.

The mixing basis is constructed once using all 400 target graphs before outer cross-validation.

The SVD therefore uses the held-out mixing targets to determine:

* centering;
* basis orientation;
* and retained singular directions.

If the final statistic were exactly invariant to orthogonal rotation, this would be largely harmless.

The implementation is not exactly rotation invariant because:

* each mixing coordinate receives its own nuisance model;
* each coordinate receives its own selected ridge penalty;
* and coordinates can be skipped separately when residual variance is small.

A stricter audit would either:

* derive an independent basis analytically from the stub constraints;
* or fit the SVD on each outer-training set and project the held-out edge-count vectors using the training basis.

The notebook states that per-coordinate mixing results are reported.

They are not.

The implementation returns only the pooled variance-weighted score and fold standard deviation.

Consequently, a high pooled result does not show that every retained mixing direction is decoded. The result can be dominated by the highest-variance SVD coordinates.

This is particularly relevant to:

* the six-dimensional S3 basis;
* the five-dimensional S4 basis.

The pooled statistic is also not strictly rotation invariant under coordinate-specific regularization selection.

The nuisance-removal strength is not reported.

E27 provides the residual decoder $$R^2$$ but does not report:

* nuisance-model $$R^2$$;
* residual variance as a fraction of original variance;
* residual-nuisance correlation;
* or target variance remaining after conditioning.

A residual target can be highly predictable while representing either a large or a very small fraction of the original structural variation.

The drop:

$$1.000\rightarrow0.583$$

in S2 cannot be interpreted as 41.7% of mixing being cycle mediated.

The raw and residual $$R^2$$ values use different target variances and are not decomposable in that manner.

Cross-fitted residuals for the outer-training set are produced by inner-fold models, while outer-test residuals are produced by a nuisance model fitted on the complete outer-training set.

This is a defensible cross-fitting construction, but the two sets of residuals are generated by models trained on different sample sizes and may have different noise distributions.

No permutation test, bootstrap interval, or repeated outer split is used for the conditional scores.

The fold standard deviations summarize only five fixed graph folds.

S1 triangle residual prediction is particularly unstable:

$$0.565\pm0.463.$$

The cycle nuisance bank contains only:

$$C_3,C_4,C_5,C_6.$$

It does not condition on:

* girth;
* diamonds;
* degree-conditioned motifs;
* longer cycles;
* graph distances;
* or other structural variables that may covary with mixing.

The full-spectrum bank contains 14 highly constrained coordinates.

The eigenvalues have:

* zero trace;
* fixed squared sum within each fixed-edge stratum;
* and other nonlinear relationships.

The nuisance regression does not explicitly account for these constraints.

The matched-pair witnesses come from sampled 400-graph strata rather than exhaustive fixed-degree-sequence censuses.

They establish existence within those samples, not universal independence over the complete graph families.

The persisted artifact is incorrectly named:

$$\texttt{e26_conditional_audit.pkl}.$$

The notebook text also refers to E26 where E27 is intended.

These stale labels should be corrected before the experiment is incorporated into the master record.

Finally, all QuIC representations use exact ideal probabilities.

The finite-shot recoverability of the conditional mixing residual is unknown.

#### Overall assessment

E27 provides strong evidence that degree mixing is a genuine and unusually dominant coordinate of QuIC’s off-regular geometry.

After linear residualization on all four ordinary cycle totals, degree mixing remains decodable at:

$$0.983,\quad0.583,\quad0.934,\quad0.944$$

across S1 through S4.

After linear residualization on the raw adjacency eigenvalues, it remains at:

$$0.964,\quad0.667,\quad0.932,\quad0.951.$$

The S2 reduction shows meaningful overlap among degree mixing, cycles, and spectral structure. It does not collapse the mixing coordinate. In the other three strata, the residual mixing score remains close to the raw result.

The reverse audit shows that the cycle channel is family dependent.

* S2 retains triangles and moderate deeper-cycle residuals.
* S1 and S4 retain separate triangle information.
* S3 has no positive ordinary cycle signal to begin with.

The notebook’s broad “cycle mediated” flags should therefore be discarded.

The appropriate central claim is:

> Under leakage-controlled cross-fitted linear residualization, QuIC’s joint-degree mixing coordinate remains strongly decodable after removing ordinary cycle counts, with residual scores from (0.583) to (0.983), and after removing linearly accessible adjacency-spectrum information, with scores from (0.667) to (0.964). The reverse analysis shows that S2 retains distinct cycle and mixing channels, S1 and S4 retain triangle information beyond mixing, and S3 exhibits only the mixing channel under the tested probe. E27 therefore establishes a robust degree-mixing coordinate that is not merely a linear cycle or raw-eigenvalue proxy, but it does not prove statistical independence or unrestricted non-spectrality.


### E28-P0 - Finite-Shot Runtime Pilot

#### Experimental purpose

E28 was designed to test whether degree-conditioned aggregation reduces QuIC’s finite-shot requirements.

It compares three empirical readouts constructed from independently multinomial-sampled circuit outcomes:

* **R0:** globally sorted frequencies;
* **R2:** degree-sector probability masses;
* **R3:** probabilities sorted within degree sectors.

The planned shot ladder was:

$$S\in{2^{10},2^{12},2^{14},2^{16},2^{18},2^{20}},$$

with:

$$12$$

sampling replicates per budget.

The targets were:

* joint-degree mixing in all four E6 strata;
* S1 triangle count;
* S2 4-, 5-, and 6-cycle counts;
* S3 triangle count.

#### Validation and exact ceilings

The setup phase completed successfully.

The notebook verified:

* all four fixed degree sequences;
* the E6 graph records and cycle identities;
* reconstruction of the unsorted circuit probabilities;
* agreement between the re-sorted reconstructed probabilities and the stored E6 vectors;
* correct degree-sector dimensions;
* numerical permutation invariance of R2 and R3;
* the frozen E6 decoder calibration.

The exact-probability ceilings were:

| Stratum         | Readout | Mixing | Selected cycle targets                |
| --------------- | ------- | -----: | ------------------------------------- |
| S1 near regular | R0      |  1.000 | $$C_3=0.449$$                         |
|                 | R2      |  1.000 | $$C_3=0.987$$                         |
|                 | R3      |  1.000 | $$C_3=0.961$$                         |
| S2 bimodal      | R0      |  1.000 | $$C_4=0.295,\ C_5=0.284,\ C_6=0.296$$ |
|                 | R2      |  1.000 | $$C_4=0.783,\ C_5=0.463,\ C_6=0.539$$ |
|                 | R3      |  1.000 | $$C_4=0.345,\ C_5=0.306,\ C_6=0.340$$ |
| S3 skewed       | R0      |  0.972 | $$C_3=-0.047$$                        |
|                 | R2      |  1.000 | $$C_3=0.807$$                         |
|                 | R3      |  1.000 | $$C_3=0.631$$                         |
| S4 hub          | R0      |  0.991 | —                                     |
|                 | R2      |  1.000 | —                                     |
|                 | R3      |  0.998 | —                                     |

These ceilings reproduce the protocol-matched E26R pattern: R2 is the strongest cycle readout in every selected cell.

#### Runtime failure

The finite-shot sweep did not complete.

The log confirms that all 12 replicates finished for:

$$2^{10}$$

and:

$$2^{12}$$

shots.

The notebook then entered the:

$$2^{14}$$

budget and was terminated when the execution environment reached its 12-hour compute-protection limit.

The approximate runtime was:

* setup and exact ceilings: 22 minutes;
* complete $$2^{10}$$ budget: approximately four hours;
* complete $$2^{12}$$ budget: approximately four additional hours;
* four planned budgets still remaining.

The dominant expense was not multinomial sampling. It was the repeated nested ridge evaluation across:

$$6\text{ budgets}\times12\text{ replicates}\times27\text{ decoder calls},$$

with hundreds of outer and inner ridge fits per replicate.

The monolithic design would have required approximately 24 hours rather than fitting within one protected session.

#### Lost partial results

Although the log confirms that the first two budgets completed, the notebook timed out before reaching the cells that:

* collapsed replicate values into means and standard deviations;
* computed recovery thresholds;
* printed the finite-shot curves;
* or saved the result artifact.

The completed low-shot values existed only in the terminated process memory.

Consequently, no numerical finite-shot recovery result can be reported from this run.

In particular, E28-P0 does **not** establish:

* that R2 recovers degree mixing at low shot counts;
* that R2 is more sample efficient than R0;
* how R3 compares with R2 under sampling;
* or any shots-to-recovery threshold.

#### Minimal result

E28-P0 establishes only that:

1. the finite-shot implementation and representation gates pass;
2. the exact ceilings reproduce the prior degree-sector result;
3. each complete budget requires approximately four hours under the full nested E6 probe;
4. the original six-budget, three-readout notebook cannot finish within the 12-hour compute limit;
5. the finite-shot experiment must be distributed and checkpointed.

#### Revised execution plan

The current run is retained as **E28-P0 — Finite-Shot Runtime Pilot**.

The replacement design will divide the work into:

* a bounded low-shot R0/R2/R3 comparison;
* a full R2 recovery sweep;
* a matched R0 recovery sweep;
* and a lightweight synthesis notebook.

Each worker will save after every replicate and use keyed seeds so that R0 and R2 are evaluated on identical empirical samples.

A full high-shot R3 sweep is no longer planned unless the low-shot audit shows that R3 materially exceeds R2. The existing exact ceilings consistently favor R2, making the full R3 curve a poor use of the protected compute budget.

#### Overall assessment

E28-P0 is a computational failure, not a negative scientific result.

The notebook passed its setup and exact-representation checks, but the finite-shot sweep was too expensive for the execution environment. It completed the first two shot budgets and then timed out during the third before any sampled results were summarized or persisted.

The appropriate record is:

> E28-P0 validated the finite-shot implementation and reproduced the protocol-matched exact ceilings, but the monolithic sweep exceeded the environment’s 12-hour compute-protection limit. Complete 12-replicate runs finished at (2^{10}) and (2^{12}) shots, but the process was terminated during the (2^{14}) budget before curve statistics or artifacts were saved. No finite-shot recovery claim is therefore made from this run. The experiment will be replaced by checkpointed R2 and R0 worker sweeps, with R3 restricted to a low-shot screening comparison.


### E29A - Circuit-by-Readout Structural Screen

#### Experimental purpose

E29A tests whether the degree-conditioned probability structure identified in E25R and E26R is specific to the flat QuIC circuit or appears across a broader family of shallow graph-phase circuits.

The experiment separates two design choices:

1. **Circuit architecture**

   How the graph-dependent Born distribution is produced.

2. **Invariant readout**

   How that probability distribution is reduced to a graph representation.

Five circuit families are evaluated using three invariant readouts on the four fixed-degree-sequence graph strata from E6.

The primary hypotheses are:

* **General circuit hypothesis:** degree-sector masses reconstruct joint-degree mixing across multiple graph-phase circuits;
* **Degree-conditioning hypothesis:** degree-sector masses outperform the coarser Hamming-weight marginal;
* **Architecture-interaction hypothesis:** the benefit of degree-sector readout depends on circuit preparation and mixer choice.

#### Shared E29P producer

All E29X experiments use the E29P producer.

E29P computes every circuit statevector once and saves a common artifact for each:

$$\text{circuit}\times\text{stratum}$$

combination.

Every artifact uses the same:

* graph ordering;
* adjacency matrices;
* degree-sector construction;
* qubit convention;
* angle schedule;
* numerical precision;
* cycle targets;
* joint-degree mixing basis;
* and adjacency spectra.

This shared producer prevents E29A, E29B, E29C, and E29D from silently comparing representations generated under different conventions.

#### Graph families

The experiment uses four sampled fixed-degree-sequence strata at:

$$n=14.$$

| Stratum         | Locked degree sequence | Graphs | Independent mixing rank |
| --------------- | ---------------------- | -----: | ----------------------: |
| S1 near regular | $$(4,4,3^{10},2,2)$$   |    400 |                       3 |
| S2 bimodal      | $$(4^7,2^7)$$          |    400 |                       1 |
| S3 skewed       | $$(5,5,4,4,3^6,2^4)$$  |    400 |                       6 |
| S4 hub          | $$(6,4,4,3^8,2,2,2)$$  |    400 |                       5 |

Every comparison occurs within one stratum.

The following quantities are therefore fixed:

* graph order;
* edge count;
* degree multiset;
* number of vertices in every degree class.

The joint-degree mixing targets measure how those fixed degree classes connect rather than differences among degree sequences.

#### Circuit bank

All circuits use the same graph-phase angle:

$$\gamma=2.0,$$

and the same mixer magnitude when applicable:

$$\beta=0.1.$$

No circuit or angle is selected using target performance.

##### F-X - Flat QuIC reference

Every qubit receives:

$$R_X(2.875).$$

This is followed by:

* graph-edge $$R_{ZZ}(2.0)$$ gates;
* a uniform $$R_X(0.1)$$ mixer.

F-X is the E6 reference circuit.

##### D-X - Normalized degree encoder

The preparation is:

$$R_X\left(2.875\frac{d_i}{\Delta}\right),$$

followed by the same:

* graph-edge $$R_{ZZ}(2.0)$$ layer;
* uniform X mixer.

##### H-X - QAOA-style preparation

The circuit begins from:

$$|+\rangle^{\otimes14},$$

followed by:

* graph-edge $$R_{ZZ}(2.0)$$ gates;
* a uniform $$R_X(0.1)$$ mixer.

##### F-Y - Mixer-axis ablation

The preparation and graph-phase layer match F-X, but the final mixer is:

$$R_Y(0.1).$$

##### H-H - IQP-style circuit

The circuit is:

$$H^{\otimes14}\rightarrow U_{ZZ}(2.0)\rightarrow H^{\otimes14}.$$

This circuit is included as a structurally different graph-phase architecture.

#### Graph-blind controls

The producer also evaluates two controls.

1. **No-edge control**

   Flat preparation and X mixer without graph-edge gates.

2. **No-mixer control**

   Flat preparation and graph-edge phases without a final noncommuting mixer.

The globally sorted readout is constant across graphs within every stratum to numerical precision:

$$\max_j\operatorname{SD}_G R_0(G)_j\le2.11\times10^{-15}.$$

This confirms that graph-dependent phase gates do not alter computational-basis probabilities without a later noncommuting operation.

The producer stores and checks only the globally sorted control readout. It does not directly store or assert constancy of the R1 and R2 control representations.

#### Invariant readouts

Let:

$$p_G(z)=|\langle z|\psi_G\rangle|^2$$

be the exact Born probability of basis state $$z$$.

E29A compares three readouts.

##### R0 - Global sorting

$$R_0(G)=\operatorname{sort}_{\downarrow}{p_G(z)}.$$

E29A retains the first:

$$k=1000$$

probabilities.

R0 removes:

* bitstring identity;
* Hamming-weight identity;
* degree-sector identity.

##### R1 - Hamming-weight marginal

For Hamming weight $$w$$:

$$R_1(G)*w=\sum*{z:|z|=w}p_G(z).$$

Its dimension is:

$$15.$$

R1 retains total excitation count but discards which degree classes contain those excitations.

##### R2 - Degree-sector mass

Let the graph’s distinct degree classes be:

$$d_1<\cdots<d_m.$$

For bitstring $$z$$, define the degree-occupancy signature:

$$\kappa_G(z)=\left(\sum_{i:\deg(i)=d_1}z_i,\ldots,\sum_{i:\deg(i)=d_m}z_i\right).$$

The sector mass is:

$$R_2(G)*\kappa=\sum*{z:\kappa_G(z)=\kappa}p_G(z).$$

Its dimensions are:

| Stratum         | R2 dimension |
| --------------- | -----------: |
| S1 near regular |           99 |
| S2 bimodal      |           64 |
| S3 skewed       |          315 |
| S4 hub          |          216 |

R2 refines R1 because Hamming weight is the sum of the degree-class occupancies:

$$|z|=\sum_j\kappa_j(z).$$

R1 can therefore be reconstructed by summing appropriate R2 sectors.

R2 is not a circuit-only representation. It uses the graph’s degree partition during readout and is properly understood as a hybrid graph-conditioned Born marginal.

#### Shared targets

##### Independent joint-degree mixing basis

For degree classes $$a\le b$$:

$$M_{ab}=#{uv\in E:{\deg u,\deg v}={a,b}}.$$

The raw edge-count columns obey fixed-stub constraints:

$$2M_{aa}+\sum_{b\ne a}M_{ab}=an_a.$$

E29P centers the joint-degree count matrix and applies singular-value decomposition.

Singular values below:

$$10^{-8}s_{\max}$$

are discarded.

The retained SVD scores form the nonredundant mixing target used in E29A.

##### Cycle totals

The scalar targets are:

$$C_3,\qquad C_4,\qquad C_5,\qquad C_6.$$

The producer verifies the triangle and 4-cycle trace identities:

$$\operatorname{tr}(A^3)=6C_3,$$

and:

$$\operatorname{tr}(A^4)=8C_4+2\sum_i d_i^2-\sum_i d_i.$$

C5 and C6 are inherited from the gated E6 artifact but are not independently trace certified in E29P or E29A.

#### Producer validation

The completed producer validates:

* all four degree sequences;
* exact probability-vector dimension $$2^{14}$$;
* probability normalization;
* R1 and R2 unit mass;
* degree-sector counts;
* sector cardinalities against binomial products;
* normalized degree-encoder angles;
* graph-blind R0 controls;
* F-X global sorting against the stored E6 vector for every graph.

The F-X gate requires:

$$|R_0^{\text{E29P}}(G)-R_0^{\text{E6}}(G)|_\infty<10^{-12}.$$

All 1,600 F-X vectors pass.

#### Validation defects

Two producer validation statements are weaker than their descriptions.

##### E26R comparison was not implemented

The producer loads the E26R artifact and reports:

> compared to E26R pkl — see assertion

However, the code contains no numerical comparison or assertion between the new F-X R2 values and E26R.

The purported direct E26R gate did not occur.

F-X R2 is instead supported by:

* reconstruction from the same unsorted probabilities as the validated R0 vector;
* correct sector dimensions;
* unit-mass checks;
* and consistency of the downstream E29A results with E26R.

It should not be described as bitwise reproduced from the E26R artifact.

##### Relabeling check sorts the R2 coordinates

The permutation self-test compares:

$$\operatorname{sort}(R_2(G))$$

with:

$$\operatorname{sort}(R_2(\pi G)).$$

This verifies invariance of the sector-mass multiset but is weaker than verifying coordinatewise equality under the canonical sector ordering.

Because sectors are constructed from increasing degree classes and mixed-radix occupancy signatures, coordinatewise invariance is expected. The implemented assertion does not prove it directly.

#### Frozen E6 decoder

Every circuit, readout, stratum, and target uses the same decoder:

* raw features;
* five shuffled outer folds;
* outer seed zero;
* inner five-fold `RidgeCV`;
* ridge grid:

$$\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2};$$

* mean outer-fold test $$R^2$$;
* outer-fold standard deviation.

The synthetic calibration produces:

$$R^2_{\text{null}}=-0.005,$$

and:

$$R^2_{\text{linear}}=1.000.$$

The basic decoder mechanics pass.

#### Mixing reconstruction by circuit and readout

##### Per-stratum results

| Circuit | Stratum |     R0 global sort | R1 Hamming mass | R2 degree-sector mass |
| ------- | ------- | -----------------: | --------------: | --------------------: |
| F-X     | S1      |               1.00 |            0.61 |                  1.00 |
| F-X     | S2      |               1.00 |            1.00 |                  1.00 |
| F-X     | S3      |               0.97 |            0.32 |                  1.00 |
| F-X     | S4      |               0.99 |            0.39 |                  1.00 |
| D-X     | S1      |               0.98 |            0.97 |                  1.00 |
| D-X     | S2      |               1.00 |            1.00 |                  1.00 |
| D-X     | S3      |               0.36 |            0.68 |                  0.99 |
| D-X     | S4      |               0.24 |            0.94 |                  1.00 |
| H-X     | S1      |               0.08 |            0.61 |                  1.00 |
| H-X     | S2      |               0.55 |            1.00 |                  1.00 |
| H-X     | S3      |               0.12 |            0.47 |                  1.00 |
| H-X     | S4      |               0.09 |            0.38 |                  1.00 |
| F-Y     | S1      |               1.00 |            0.71 |                  1.00 |
| F-Y     | S2      |               1.00 |            1.00 |                  1.00 |
| F-Y     | S3      |               0.98 |            0.45 |                  1.00 |
| F-Y     | S4      |               0.99 |            0.41 |                  1.00 |
| H-H     | S1      |            (-0.02) |            0.08 |                  0.23 |
| H-H     | S2      | approximately 0.00 |            0.12 |                  0.51 |
| H-H     | S3      | approximately 0.00 |            0.04 |                  0.17 |
| H-H     | S4      |            (-0.01) |            0.05 |                  0.14 |

##### Mean over strata

| Circuit |  Mean R0 | Mean R1 | Mean R2 |
| ------- | -------: | ------: | ------: |
| F-X     |    0.991 |   0.583 |   1.000 |
| D-X     |    0.642 |   0.897 |   0.997 |
| H-X     |    0.212 |   0.612 |   0.999 |
| F-Y     |    0.991 |   0.641 |   1.000 |
| H-H     | (-0.007) |   0.072 |   0.265 |

#### Generality of degree-mixing reconstruction

R2 reconstructs the independent joint-degree mixing state almost perfectly for:

* F-X;
* D-X;
* H-X;
* F-Y.

This includes circuits with:

* flat preparation;
* normalized degree preparation;
* Hadamard preparation;
* X mixing;
* Y mixing.

The result is therefore not specific to the flat QuIC preparation or X mixer.

The H-H circuit is a clear exception.

Its R2 mixing score ranges only from:

$$0.14\text{ to }0.51.$$

The strict hypothesis that degree-sector masses reconstruct degree mixing across every shallow graph-phase circuit is rejected.

The supported result is narrower:

> Degree-sector masses almost perfectly reconstruct joint-degree mixing across the four preparation–phase–small-mixer circuits, but not for the H-H interference architecture.

#### What global sorting retains

R0 behaves very differently across the circuit bank.

F-X and F-Y retain near-perfect mixing information after global sorting:

$$\overline{R^2}_{R0}=0.991.$$

D-X retains mixing in S1 and S2 but degrades sharply in the more irregular strata:

$$R^2=0.36\quad\text{in S3},$$

and:

$$R^2=0.24\quad\text{in S4}.$$

H-X global sorting largely removes the mixing coordinate:

$$\overline{R^2}_{R0}=0.212.$$

Yet its R2 representation reconstructs mixing almost perfectly.

Thus, the same circuit distribution can contain strong degree-conditioned information that becomes inaccessible after global rank sorting.

The effect is architecture dependent.

#### Does Hamming weight explain the R2 result?

R1 performs strongly in selected cases.

In the bimodal stratum:

$$R^2_{R1}=1.00$$

for F-X, D-X, H-X, and F-Y.

This is unsurprising because S2 has only one independent degree-mixing coordinate, and the excitation-weight distribution can align strongly with it.

Outside S2, R1 is generally weaker than R2.

The mean R2-minus-R1 gains are approximately:

| Circuit | Mean mixing gain |
| ------- | ---------------: |
| F-X     |         (+0.417) |
| D-X     |         (+0.100) |
| H-X     |         (+0.387) |
| F-Y     |         (+0.359) |
| H-H     |         (+0.193) |

Degree conditioning therefore adds information beyond total Hamming weight for every circuit on average.

The gain is smallest for D-X because its degree-dependent preparation already makes the coarse Hamming distribution highly informative.

#### Cycle-family screen

E29A summarizes cycle gains through:

$$\Delta_{\text{cycle}}=\frac{1}{16}\sum_{s=1}^{4}\sum_{k=3}^{6}\left[R^2_{R2}(C_k)-R^2_{R0}(C_k)\right].$$

| Circuit | Descriptive $$\Delta_{\text{cycle}}$$ |
| ------- | ------------------------------------: |
| F-X     |                              (+0.219) |
| D-X     |                              (+0.100) |
| H-X     |                              (+0.248) |
| F-Y     |                              (+0.276) |
| H-H     |                              (+0.240) |

Every circuit has a positive mean R2-minus-R0 cycle contrast.

This does not mean every circuit has strong absolute R2 cycle prediction.

A positive contrast can arise because:

* R2 is strong;
* R0 is weak;
* or both representations remain below zero but R2 is less poor.

The H-H result is the clearest reason not to interpret the family average as absolute structural accessibility.

#### Notebook bootstrap screen

The notebook reports the following numbers of cycle cells flagged after its bootstrap and Holm procedure:

| Circuit | R2 over R0 | R2 over R1 |
| ------- | ---------: | ---------: |
| F-X     |      13/16 |       9/16 |
| D-X     |       6/16 |       6/16 |
| H-X     |      11/16 |       8/16 |
| F-Y     |      16/16 |      14/16 |
| H-H     |      15/16 |      14/16 |

The largest and most consistent screen occurs for F-Y.

R2 exceeds R0 in all 16 F-Y cycle cells and exceeds R1 in 14.

The smallest family-wide benefit occurs for D-X.

This supports an architecture interaction at the descriptive level:

* explicit degree preparation reduces the additional benefit of degree-sector marginalization;
* changing the F-X mixer from X to Y increases the average R2 gain;
* Hadamard preparation makes global sorting weak while preserving a strong R2 coordinate under H-X.

#### Important bootstrap qualification

The notebook labels:

$$\Pr_{\text{bootstrap}}(\Delta\le0)$$

as a one-sided bootstrap p-value and applies Holm correction to those values.

The bootstrap samples are drawn from the empirical data without imposing a null-centered distribution.

The resulting fraction is useful as a bootstrap sign-stability measure, but it is not a conventional hypothesis-test p-value generated under:

$$H_0:\Delta=0.$$

The Holm-adjusted counts should therefore be reported as:

* bootstrap/Holm screen flags;
* or robust positive-direction cells under the empirical resampling procedure.

They should not be presented as formal familywise-error-controlled hypothesis tests.

The percentile intervals remain useful descriptive uncertainty summaries.

The bootstrap statistic also uses pooled out-of-fold squared errors and a globally centered target sum of squares, whereas the headline table uses mean test-fold $$R^2$$.

The bootstrap differences and the displayed mean-fold differences are related but are not the same estimand.

#### Circuit interaction

The descriptive cycle contrast changes with architecture:

$$\Delta_{\text{cycle}}^{F-X}=0.219,$$

$$\Delta_{\text{cycle}}^{D-X}=0.100,$$

$$\Delta_{\text{cycle}}^{H-X}=0.248,$$

$$\Delta_{\text{cycle}}^{F-Y}=0.276.$$

Relative to F-X:

* normalized degree preparation reduces the average gain by (0.119);
* Hadamard preparation increases it by (0.029);
* Y mixing increases it by (0.057).

No direct paired cross-circuit test evaluates these differences.

The values therefore support architecture-dependent readout effects descriptively, not a formal causal ranking of preparation and mixer choices.

#### Concentration diagnostics

##### Effective degree sectors

| Circuit |   S1 |   S2 |    S3 |    S4 |
| ------- | ---: | ---: | ----: | ----: |
| F-X     |  2.0 |  2.7 |   2.6 |   2.2 |
| D-X     | 18.4 |  8.2 |  44.6 |  46.5 |
| H-X     | 53.6 | 28.7 | 165.6 | 117.5 |
| F-Y     |  2.3 |  2.3 |   2.4 |   2.4 |
| H-H     | 27.0 | 15.8 |  84.1 |  59.8 |

##### Mean inverse participation ratio

| Circuit |     S1 |     S2 |     S3 |     S4 |
| ------- | -----: | -----: | -----: | -----: |
| F-X     | 0.7021 | 0.4927 | 0.5884 | 0.6714 |
| D-X     | 0.0050 | 0.0071 | 0.0011 | 0.0004 |
| H-X     | 0.0001 | 0.0001 | 0.0001 | 0.0001 |
| F-Y     | 0.6072 | 0.5462 | 0.6299 | 0.6186 |
| H-H     | 0.0003 | 0.0003 | 0.0003 | 0.0003 |

F-X and F-Y produce highly concentrated distributions occupying approximately two effective degree sectors.

D-X, H-X, and H-H are much more diffuse.

Diffuseness does not explain the H-H failure by itself.

H-X is at least as diffuse as H-H and nevertheless obtains:

$$\overline{R^2}_{R2,\text{mixing}}=0.999.$$

The H-H weakness therefore reflects its interference architecture or the structural organization of its probabilities, not merely high entropy.

There is also no simple monotone relationship between concentration and cycle gain.

* F-Y is concentrated and has the largest mean cycle contrast.
* H-X is extremely diffuse and also has a large contrast.
* D-X is intermediate in concentration and has the smallest contrast.

#### Relationship to E25R

E25R established that F-X global sorting and degree-sector structure expose joint-degree mixing.

E29A extends the result beyond F-X.

Near-perfect R2 reconstruction appears under:

* normalized degree preparation;
* Hadamard preparation;
* X mixing;
* Y mixing.

The degree-mixing coordinate is therefore reusable across a broad circuit subset rather than unique to the original flat QuIC circuit.

The H-H exception prevents a universal claim.

#### Relationship to E26R

E26R showed that F-X degree-sector masses improve selected cycle targets relative to global sorting.

E29A generalizes that comparison across five circuit architectures.

The result confirms that sector marginalization can improve cycle accessibility beyond F-X, especially for:

* F-Y;
* H-X;
* and selected H-H contrasts.

The screen also shows that R2’s benefit depends on circuit architecture and cannot be treated as a readout-only constant.

#### What the experiment establishes

The completed results establish that:

1. **The E29P producer successfully generated all five circuit families across all four strata.**

2. **F-X globally sorted vectors reproduce the E6 producer for every graph.**

3. **Degree-sector masses almost perfectly reconstruct joint-degree mixing for F-X, D-X, H-X, and F-Y.**

4. **The result is not specific to flat preparation, degree preparation, Hadamard preparation, X mixing, or Y mixing.**

5. **H-H is a clear exception.**

   Its mean R2 mixing score is only (0.265).

6. **Global sorting preserves mixing for F-X and F-Y but loses much of it for D-X and H-X in irregular strata.**

7. **Degree conditioning adds beyond Hamming-weight marginalization in every circuit on average.**

8. **R2 improves the descriptive mean cycle score over R0 for every circuit.**

9. **The magnitude and breadth of the gain depend on circuit architecture.**

10. **F-Y produces the broadest positive R2 cycle screen.**

11. **D-X produces the smallest mean cycle gain despite near-perfect R2 mixing recovery.**

12. **Probability diffuseness alone does not explain circuit success or failure.**

13. **The producer’s claimed direct E26R R2 assertion was not actually implemented.**

14. **The notebook’s bootstrap/Holm values are robustness-screen quantities rather than formal null p-values.**

E29A therefore supports a reusable degree-conditioned readout mechanism across several shallow graph-phase circuits, with architecture-specific accessibility and one important counterexample.

#### Necessary qualifications

R2 incorporates graph-derived degree labels at readout time.

It is a hybrid graph-conditioned representation and should not be described as information obtained from the circuit probabilities alone.

The graph families have fixed degree sequences, so the result is not trivial degree-histogram decoding. Nevertheless, the readout is explicitly told which vertices belong to each degree class.

The mixing target basis is computed by SVD on all 400 graphs before outer cross-validation.

This uses held-out target data to determine:

* centering;
* basis orientation;
* retained rank.

The pooled reconstruction score is not guaranteed to be invariant to that orientation because every coordinate receives a separately selected ridge model.

A stricter implementation would:

* derive an independent mixing basis analytically from the stub constraints;
* or fit the SVD on each outer-training fold and project held-out graphs through the training basis.

The mixing score is variance weighted across the retained SVD coordinates.

A value near one does not prove that every independent mixing direction is equally well decoded.

Per-coordinate scores are described in the notebook introduction but are not printed or persisted in the final compact result object.

R0, R1, and R2 are not dimension or capacity matched.

Their dimensions are approximately:

$$1000,\qquad15,\qquad64\text{--}315.$$

The same ridge grid can regularize those spaces differently.

R2’s advantage reflects both:

* retained degree-sector information;
* and an explicit low-dimensional aggregation with a favorable inductive bias.

The R0 head is truncated to 1,000 probabilities.

A deeper globally sorted head could alter selected comparisons.

The producer stores up to 4,096 values, but E29A does not test head sensitivity.

The graph-blind controls verify only R0 constancy.

R1 and R2 constancy is expected analytically for those flat controls within fixed-degree-sequence strata but is not directly asserted.

The R2 permutation test compares sorted sector masses rather than coordinate-aligned sector vectors.

The direct E26R value-match check is absent despite the producer’s printed statement.

The cycle-family average combines positive and negative $$R^2$$ values and gives equal weight to targets with different variances.

It is descriptive only.

The bootstrap resamples fixed out-of-fold errors and does not refit:

* the outer models;
* inner ridge selection;
* or the mixing basis.

Its uncertainty is conditional on the completed cross-validation pipeline.

The bootstrap random generator is shared sequentially across all cells. The procedure is reproducible, but cells do not use independently named content-addressed seeds.

No formal test compares:

* circuit preparations;
* mixer axes;
* or concentration statistics.

The H_general, H_degree, and H_interaction conclusions remain screen-level conclusions.

The experiment uses:

* exact ideal probabilities;
* one graph order;
* four sampled degree sequences;
* one fixed angle schedule;
* one circuit layer.

No finite-shot experiment evaluates R2 recovery.

Finally, the analysis establishes structural accessibility, not quantum advantage. Degree-sector masses, degree mixing, Hamming-weight marginals, and the graph degree partition are all efficiently available classical objects.

#### Overall assessment

E29A provides strong evidence that degree-conditioned Born marginals are not unique to the flat QuIC circuit.

For F-X, D-X, H-X, and F-Y, R2 reconstructs the independent joint-degree mixing state with mean scores between:

$$0.997\quad\text{and}\quad1.000.$$

This remains true even when global sorting performs poorly.

The H-X result is particularly informative:

$$\overline{R^2}_{R0}=0.212,$$

but:

$$\overline{R^2}_{R2}=0.999.$$

Thus, the graph-phase circuit contains degree-conditioned structure that global rank sorting nearly erases.

H-H breaks the universal version of the claim:

$$\overline{R^2}_{R2}=0.265.$$

The readout mechanism therefore generalizes across several preparation–phase–mixer circuits but not across every shallow interference architecture.

Cycle accessibility also improves under R2, but the strength of the improvement is architecture dependent. F-Y has the largest descriptive family gain:

$$\Delta_{\text{cycle}}=0.276,$$

while D-X has the smallest:

$$0.100.$$

The appropriate central claim is:

> Degree-sector Born marginals are a reusable structural readout across several shallow graph-phase circuits rather than a QuIC-specific artifact. They nearly perfectly reconstruct joint-degree mixing under flat, normalized-degree, and Hadamard preparations with either X or Y mixing, even when global sorting discards that information. The H-H circuit is a clear exception, showing that the effect is broad but not universal. Degree-sector masses also improve cycle accessibility across the circuit bank, with the magnitude depending on preparation and mixer architecture. These results identify degree-conditioned marginalization as a general readout mechanism, while leaving its strongest inference conditional on a graph-supplied degree partition, a globally constructed mixing basis, and ideal exact probabilities.


### E29B - Circuit-General Conditional Linear Structure Audit

#### Experimental purpose

E29B tests whether the degree-mixing structure identified in E27 and E29A remains accessible after removing ordinary cycle or spectral variation.

The experiment extends the E27 conditional audit across:

* five shallow graph-phase circuits;
* three invariant readouts;
* four fixed-degree-sequence graph strata.

It evaluates three questions.

1. **Mixing after cycles**

   Can a circuit readout predict the component of joint-degree mixing that remains after linear regression on:

   $${C_3,C_4,C_5,C_6}?$$

2. **Mixing after spectrum**

   Can the readout predict the component of joint-degree mixing that remains after linear regression on the complete adjacency spectrum?

3. **Cycles after mixing**

   Can the readout predict cycle-count variation remaining after linear regression on the independent joint-degree mixing basis?

These are cross-fitted conditional linear-accessibility tests.

They do not establish statistical independence or unrestricted non-spectrality.

#### Shared E29P producer

E29B consumes the shared E29P artifacts used by the complete E29X series.

The producer supplies identical:

* graph ordering;
* circuit definitions;
* readout definitions;
* cycle targets;
* adjacency spectra;
* and joint-degree mixing coordinates.

E29B loads all five circuit families successfully and verifies that every circuit artifact uses the same graph order as the gated E6 dataset.

For every one of the 1,600 graphs, it also reasserts:

$$\text{tr}(A^3)=6C_3,$$

and:

$$\text{tr}(A^4)=8C_4+2\sum_i d_i^2-\sum_i d_i.$$

All notebook cells complete without error, and the result artifact:

```text
e29b_conditional_audit.pkl
```

is written successfully.

#### Graph strata

The experiment uses four sampled fixed-degree-sequence families at:

$$n=14.$$

| Stratum         | Locked degree sequence | Graphs | Mixing rank |
| --------------- | ---------------------- | -----: | ----------: |
| S1 near regular | $$(4,4,3^{10},2,2)$$   |    400 |           3 |
| S2 bimodal      | $$(4^7,2^7)$$          |    400 |           1 |
| S3 skewed       | $$(5,5,4,4,3^6,2^4)$$  |    400 |           6 |
| S4 hub          | $$(6,4,4,3^8,2,2,2)$$  |    400 |           5 |

All comparisons occur within one fixed degree sequence.

The degree-mixing target therefore describes how fixed degree classes connect rather than differences among degree histograms.

#### Circuit bank

The five circuit families are:

| Circuit | Preparation                                | Graph phase     | Final transformation |
| ------- | ------------------------------------------ | --------------- | -------------------- |
| F-X     | Flat $$R_X(2.875)$$                        | $$R_{ZZ}(2.0)$$ | $$R_X(0.1)$$         |
| D-X     | Normalized degree $$R_X(2.875d_i/\Delta)$$ | $$R_{ZZ}(2.0)$$ | $$R_X(0.1)$$         |
| H-X     | $$H^{\otimes14}$$                          | $$R_{ZZ}(2.0)$$ | $$R_X(0.1)$$         |
| F-Y     | Flat $$R_X(2.875)$$                        | $$R_{ZZ}(2.0)$$ | $$R_Y(0.1)$$         |
| H-H     | $$H^{\otimes14}$$                          | $$R_{ZZ}(2.0)$$ | $$H^{\otimes14}$$    |

F-X is the original flat QuIC circuit.

H-H is an IQP-style interference architecture and serves as the principal architectural counterexample.

#### Readouts

##### R0 - Global sorting

$$R_0(G)=\text{sort}_{\downarrow}{p_G(z)}.$$

The first:

$$k=1000$$

probabilities are retained.

R0 is evaluated for every non-flat circuit. The F-X R0 analysis is omitted because the corresponding conditional audit was already performed in E27.

##### R1 - Hamming-weight marginal

$$R_1(G)*w=\sum*{z:|z|=w}p_G(z).$$

R1 has dimension:

$$15.$$

It retains total excitation number but discards the degrees of the excited vertices.

##### R2 - Degree-sector mass

For degree classes $$d_1<\cdots<d_m$$, define:

$$\kappa_G(z)=\left(\sum_{i:\deg(i)=d_1}z_i,\ldots,\sum_{i:\deg(i)=d_m}z_i\right).$$

The sector-mass readout is:

$$R_2(G)*\kappa=\sum*{z:\kappa_G(z)=\kappa}p_G(z).$$

Its dimension ranges from:

$$64\text{ to }315$$

across the four strata.

R2 is the primary readout.

It uses the graph’s degree partition during aggregation and is therefore a hybrid graph-conditioned circuit readout.

#### Independent mixing basis

For degree classes $$a\le b$$:

$$M_{ab}=#{uv\in E:{\deg u,\deg v}={a,b}}.$$

The raw joint-degree counts satisfy the fixed-stub constraints:

$$2M_{aa}+\sum_{b\ne a}M_{ab}=an_a.$$

E29P centers the raw edge-count matrix and retains its numerical SVD rank.

The resulting mixing ranks are:

$$3,\quad1,\quad6,\quad5$$

for S1 through S4.

E29B predicts these nonredundant mixing coordinates rather than averaging over the linearly dependent raw edge-count columns.

#### Cross-fitted conditional protocol

Conditional residualization occurs inside every E6 outer fold.

For target $$Y$$ and nuisance bank $$Z$$:

1. split the outer-training set into five inner folds;
2. fit the nuisance model without each inner prediction fold;
3. construct cross-fitted residuals for the outer-training graphs;
4. fit one nuisance model on the complete outer-training set;
5. construct residuals for the outer-test graphs;
6. train the circuit-readout ridge probe on the training residuals;
7. evaluate it on the independently residualized test targets.

The nuisance model is:

* train-only standardization;
* ridge regression;
* regularization grid:

$$\alpha_{\text{nuisance}}\in{10^{-6},10^{-5.5},\ldots,10^6}.$$

The second-stage readout probe uses the E6 configuration:

* raw readout coordinates;
* five shuffled outer folds;
* seed zero;
* inner five-fold `RidgeCV`;
* grid:

$$\alpha_{\text{readout}}\in{10^{-14},10^{-13},\ldots,10^2}.$$

For multivariate mixing, squared errors and target sums of squares are pooled across retained coordinates inside each outer fold.

#### Calibration

A synthetic target generated entirely from the nuisance bank gives:

$$R^2=-0.033$$

after residualization and decoding.

A target generated linearly from the tested features gives:

$$R^2=1.000.$$

The calibration supports the basic implementation of:

* cross-fitted nuisance removal;
* second-stage feature decoding;
* and outer-test isolation.

It does not establish that the real graph relationships are fully linear.

---

## B1 - Degree Mixing After Cycle Residualization

#### R2 results by circuit and stratum

| Circuit |   S1 |   S2 |   S3 |   S4 |  Mean |
| ------- | ---: | ---: | ---: | ---: | ----: |
| F-X     | 0.99 | 0.68 | 0.96 | 0.96 | 0.896 |
| D-X     | 0.98 | 0.72 | 0.95 | 0.93 | 0.895 |
| H-X     | 0.99 | 0.76 | 0.96 | 0.96 | 0.915 |
| F-Y     | 0.99 | 0.77 | 0.97 | 0.96 | 0.923 |
| H-H     | 0.21 | 0.32 | 0.15 | 0.11 | 0.199 |

The four preparation–phase–mixer circuits retain strong residual mixing scores:

$$0.895\text{ to }0.923.$$

H-H remains much weaker:

$$R^2=0.199$$

on average.

#### Cross-circuit generality

The result is remarkably stable across:

* flat preparation;
* normalized degree preparation;
* Hadamard preparation;
* X mixing;
* Y mixing.

For F-X, D-X, H-X, and F-Y, cycle residualization removes little of the accessible mixing coordinate in S1, S3, and S4.

The principal exception is S2.

Its residual values range from:

$$0.68\text{ to }0.77.$$

S2 has only one independent joint-degree mixing coordinate. It therefore exhibits substantially greater overlap between:

* degree mixing;
* ordinary cycle totals;
* and the circuit readout.

Even in S2, the residual mixing coordinate remains strongly predictable.

#### Supported interpretation

The result supports:

> Across four shallow preparation–phase–mixer circuits, degree-sector masses retain a strong joint-degree mixing coordinate after cross-fitted linear removal of triangle through 6-cycle counts.

It does not prove that degree mixing is statistically independent of cycles.

---

## B2 - Degree Mixing After Spectral Residualization

#### R2 results by circuit and stratum

| Circuit |   S1 |   S2 |   S3 |   S4 |  Mean |
| ------- | ---: | ---: | ---: | ---: | ----: |
| F-X     | 0.98 | 0.75 | 0.96 | 0.97 | 0.915 |
| D-X     | 0.97 | 0.84 | 0.95 | 0.95 | 0.930 |
| H-X     | 0.97 | 0.76 | 0.96 | 0.96 | 0.913 |
| F-Y     | 0.98 | 0.82 | 0.96 | 0.96 | 0.930 |
| H-H     | 0.20 | 0.33 | 0.15 | 0.13 | 0.202 |

The same four circuits retain strong residual mixing scores after regression on the complete raw adjacency eigenvalue vector:

$$0.913\text{ to }0.930.$$

H-H again remains weak.

The result is highly consistent with B1.

#### Spectral interpretation

E29B supports the statement:

> The degree-mixing coordinate exposed by R2 is not exhausted by a linear ridge readout of the raw adjacency eigenvalues.

It does not establish unrestricted non-spectrality.

The complete spectrum determines nonlinear quantities such as:

$$\text{tr}(A^k)=\sum_i\lambda_i^k.$$

A linear model on the raw eigenvalues does not automatically remove polynomial or other nonlinear spectral functions.

A stronger spectral nuisance audit would require cross-fitted models using:

* trace powers;
* polynomial spectral features;
* RBF kernel regression;
* or the nonlinear spectral models used in E11.

E29B also conditions on cycles and spectrum separately. It does not test a joint nuisance bank containing both.

---

## Readout Dependence of Conditional Mixing

#### Mean residual scores

| Circuit | Readout | Mixing after cycles | Mixing after spectrum |
| ------- | ------- | ------------------: | --------------------: |
| F-X     | R1      |               0.460 |                 0.450 |
| F-X     | R2      |               0.896 |                 0.915 |
| D-X     | R0      |               0.510 |                 0.488 |
| D-X     | R1      |               0.763 |                 0.790 |
| D-X     | R2      |               0.895 |                 0.930 |
| H-X     | R0      |               0.138 |                 0.115 |
| H-X     | R1      |               0.518 |                 0.485 |
| H-X     | R2      |               0.915 |                 0.913 |
| F-Y     | R0      |               0.873 |                 0.890 |
| F-Y     | R1      |               0.543 |                 0.533 |
| F-Y     | R2      |               0.923 |                 0.930 |
| H-H     | R0      |            (-0.008) |              (-0.015) |
| H-H     | R1      |               0.060 |                 0.073 |
| H-H     | R2      |               0.199 |                 0.202 |

#### Degree sectors versus Hamming weight

R2 substantially exceeds R1 for:

* F-X;
* H-X;
* F-Y.

For H-X, for example:

$$R^2_{\text{mix}|\text{cycles}}:0.518\rightarrow0.915,$$

and:

$$R^2_{\text{mix}|\text{spectrum}}:0.485\rightarrow0.913.$$

The surviving conditional structure therefore requires more than total excitation number.

D-X is different.

Its Hamming-weight marginal already retains:

$$0.763$$

after cycle removal and:

$$0.790$$

after spectral removal.

The normalized degree encoder appears to move substantial degree-conditioned information into the coarse Hamming-weight distribution.

R2 remains stronger, but its incremental advantage is smaller.

#### Global sorting

Global sorting preserves conditional mixing unevenly across architectures.

##### F-Y

F-Y R0 retains strong residual mixing:

$$0.873\quad\text{and}\quad0.890.$$

Its probability ranks preserve most of the degree-mixing channel even without explicit sector labels.

##### D-X

D-X R0 is intermediate:

$$0.510\quad\text{and}\quad0.488.$$

Some conditional mixing survives global sorting, but much less than under R1 or R2.

##### H-X

H-X R0 is weak:

$$0.138\quad\text{and}\quad0.115.$$

The H-X circuit contains an almost perfectly accessible R2 mixing coordinate, but global sorting nearly erases it.

This is the strongest evidence that readout quotient and circuit architecture interact.

##### H-H

All three H-H readouts remain weak.

Degree-sector aggregation improves H-H relative to R0 and R1, but it does not reveal the strong mixing coordinate seen in the other four circuits.

---

## B3 - Cycle Counts After Mixing Residualization

The notebook reports the mean residual cycle score across:

$$4\text{ strata}\times4\text{ targets}=16$$

cells for R2.

| Circuit | Mean residual cycle $$R^2$$ |
| ------- | --------------------------: |
| F-X     |                       0.347 |
| D-X     |                       0.066 |
| H-X     |                       0.300 |
| F-Y     |                       0.480 |
| H-H     |                       0.341 |

#### F-X and H-X

F-X and H-X retain moderate average cycle accessibility after linear removal of joint-degree mixing:

$$0.347$$

and:

$$0.300.$$

Their sector masses therefore contain cycle information not reducible to the tested linear mixing basis.

#### F-Y

F-Y has the strongest residual cycle result:

$$R^2=0.480.$$

This suggests that the Y-mixer sector masses retain the richest higher-order cycle channel among the tested circuits.

This is an aggregate descriptive comparison. No direct cross-circuit test establishes that F-Y is statistically superior.

#### D-X

D-X falls to:

$$R^2=0.066.$$

This suggests that much of the cycle accessibility in D-X sector masses overlaps with the degree-mixing basis.

The result is compatible with the E29A observation that D-X has:

* highly informative R1 and R2 degree-conditioned marginals;
* but the smallest average R2-over-R0 cycle gain among the four primary circuits.

The notebook labels D-X as “cycle mediated by mixing.”

That wording is too strong.

The reported value is an unweighted mean over 16 heterogeneous target cells. It does not establish that every cycle or stratum collapses after conditioning.

#### H-H

H-H has an aggregate residual cycle score of:

$$0.341.$$

Its raw and conditional degree-mixing scores are weak, so the value cannot represent a strong cycle channel mediated through mixing.

The notebook display does not print the H-H target-by-target raw and residual cycle rows. The aggregate alone is insufficient to determine:

* which targets contribute;
* whether the corresponding raw scores are positive;
* or whether a small number of cells dominate the mean.

The completed result artifact contains the detailed B3 values, but those values are not exposed in the submitted notebook output.

#### Limits of the aggregate B3 statistic

The mean combines:

* four different cycle lengths;
* four degree-sequence strata;
* positive and negative $$R^2$$ values;
* targets with different variances and count ranges.

It should be treated as a screening statistic rather than a mediation test.

A paper-facing B3 analysis should report the complete:

$$\text{circuit}\times\text{stratum}\times\text{cycle}$$

table before making target-specific claims.

---

## Audit of the Notebook Interpretation Flags

E29B converts its continuous results into three binary flags using fixed thresholds of:

$$0.10.$$

The flags are not robust enough for paper use.

#### Mixing-survives-cycles flag

The flag requires:

$$R^2_{\text{raw mixing}}-R^2_{\text{residual mixing}}<0.10.$$

The aggregate differences are approximately:

| Circuit | Raw minus residual |
| ------- | -----------------: |
| F-X     |              0.104 |
| D-X     |              0.102 |
| H-X     |              0.084 |
| F-Y     |              0.077 |

The threshold marks only H-X and F-Y as passing.

This creates an artificial distinction between:

$$0.102$$

and:

$$0.084.$$

All four residual scores remain near or above:

$$0.895.$$

The continuous results support the same substantive conclusion for all four circuits.

The binary flag should be discarded.

#### Mixing-is-spectral flag

This flag is triggered when the residual mixing score after spectral regression falls below:

$$0.10.$$

No R2 representation meets that criterion.

The flag name is nevertheless too broad because the nuisance model removes only linearly accessible raw-eigenvalue information.

#### Cycle-mediated-by-mixing flag

Only D-X is marked because its 16-cell mean residual cycle score is:

$$0.066.$$

As in E27, averaging a strong target with several weak targets can produce a misleading family-level classification.

Mediation should be evaluated separately for each cycle and stratum.

---

## Relationship to E27

E27 found that the F-X globally sorted readout retains a strong degree-mixing coordinate after linear cycle and spectral residualization.

E29B extends the conditional result to degree-sector masses across multiple circuits.

For F-X, D-X, H-X, and F-Y:

$$R^2_{\text{mix}|\text{cycles}}\in[0.895,0.923],$$

and:

$$R^2_{\text{mix}|\text{spectrum}}\in[0.913,0.930].$$

The degree-mixing channel is therefore not unique to:

* flat preparation;
* X mixing;
* or global rank sorting.

The H-H result shows that it is not universal across every shallow graph-phase architecture.

## Relationship to E29A

E29A established that R2 almost perfectly reconstructs raw degree mixing under four circuits.

E29B shows that the result survives linear removal of ordinary cycles and raw spectral coordinates.

It also clarifies why R2 matters most for H-X.

E29A found:

$$R^2_{\text{raw mixing}}=0.999$$

for H-X R2 but only:

$$0.212$$

for H-X R0.

E29B finds the same separation after conditioning:

$$0.915\text{ versus }0.138$$

after cycle removal.

Thus, H-X contains a strong conditional degree-mixing channel that global sorting nearly eliminates.

---

## What the Experiment Establishes

The completed results establish that:

1. **E29B completed all five circuits, all applicable readouts, and all four strata.**

2. **The cross-fitted conditional machinery passes its synthetic calibration.**

3. **R2 degree-sector masses retain strong mixing accessibility after linear cycle removal for F-X, D-X, H-X, and F-Y.**

4. **The same four circuits retain strong mixing accessibility after linear raw-spectrum removal.**

5. **H-H remains a clear architectural exception.**

6. **S2 consistently exhibits the greatest overlap between mixing, cycles, and spectrum.**

7. **R2 retains substantially more conditional mixing information than R1 for F-X, H-X, and F-Y.**

8. **D-X moves unusually large conditional mixing information into the Hamming-weight marginal.**

9. **Global sorting preserves conditional mixing for F-Y, partially preserves it for D-X, and nearly erases it for H-X.**

10. **F-X, H-X, and F-Y retain aggregate cycle information beyond linear degree mixing.**

11. **D-X has little aggregate residual cycle accessibility after mixing removal.**

12. **The notebook’s binary threshold flags overstate distinctions among nearly identical strong R2 results.**

13. **The experiment demonstrates conditional linear separation, not statistical independence or unrestricted non-spectrality.**

E29B therefore supports a circuit-general degree-mixing channel whose visibility depends strongly on the readout quotient.

---

## Necessary Qualifications

The nuisance models are linear ridge regressions.

Residual mixing after cycle removal can still contain nonlinear functions of:

$$C_3,C_4,C_5,C_6.$$

Residual mixing after spectral removal can still contain nonlinear spectral functions.

The phrases “independent of cycles” and “not spectral” exceed the implemented analysis.

Raw and residual $$R^2$$ values use different target variances.

A decline from:

$$1.000\rightarrow0.68$$

does not mean that cycles explain 32% of the original mixing information.

The scores are not additively decomposable mediation fractions.

The joint-degree mixing basis is constructed through SVD using all 400 graphs before outer cross-validation.

This exposes held-out mixing targets when determining:

* centering;
* basis orientation;
* and numerical rank.

A stricter implementation would derive the independent basis analytically or fit the SVD inside each outer-training fold.

The notebook describes its pooled multivariate score as rotation invariant.

Strict rotation invariance is not guaranteed because:

* each target coordinate receives a separately selected ridge penalty;
* each coordinate receives a separate nuisance model;
* and low-variance coordinates can be skipped separately.

The score is variance weighted and may be dominated by the leading mixing directions.

Per-coordinate conditional mixing scores are not printed.

R2 uses the graph’s degree partition at readout time.

It is not information extracted from an unlabeled probability multiset alone.

R0, R1, and R2 differ substantially in dimension:

$$1000,\qquad15,\qquad64\text{--}315.$$

The same ridge grid does not capacity match these feature spaces.

The strong R2 results reflect both:

* retained degree-sector semantics;
* and an explicit low-dimensional aggregation.

The B3 display reports only circuit-level averages.

Target-specific cycle-mediation claims cannot be audited from the printed notebook output without the persisted result artifact.

The interpretation thresholds:

$$0.10$$

are arbitrary and create unstable binary distinctions.

No:

* bootstrap interval;
* permutation test;
* repeated outer split;
* or direct cross-circuit comparison

is performed for the conditional scores.

Fold standard deviations are saved for B1 and B2 but are not printed in the submitted output.

The experiment inherits the known producer qualifications:

* the mixing SVD is global;
* the R2 relabeling test compares sorted sector masses rather than coordinate-aligned vectors;
* the claimed direct E26R R2 assertion was not implemented.

All readouts use exact ideal probabilities.

Finite-shot recovery of the residual degree-mixing coordinate is unknown.

Finally, the experiment covers:

* one graph order;
* four sampled degree sequences;
* one fixed angle schedule;
* and one shallow circuit layer.

It establishes accessibility, not quantum advantage.

---

## Overall Assessment

E29B provides a coherent extension of E27 across a circuit bank.

For F-X, D-X, H-X, and F-Y, degree-sector masses retain almost all of their predictive strength after linear cycle or spectral residualization:

$$R^2_{\text{mix}|\text{cycles}}=0.895\text{--}0.923,$$

and:

$$R^2_{\text{mix}|\text{spectrum}}=0.913\text{--}0.930.$$

The result is particularly strong for H-X.

Its globally sorted readout retains almost no conditional mixing geometry:

$$0.138\quad\text{after cycles},$$

while its degree-sector marginal reaches:

$$0.915.$$

The circuit distribution therefore contains a strong structural channel that global probability sorting nearly erases.

D-X behaves differently.

Its Hamming-weight marginal already retains substantial conditional mixing, and its average cycle residual after mixing removal falls to:

$$0.066.$$

This suggests that normalized degree preparation concentrates much of its R2 cycle accessibility in the joint-degree mixing channel.

F-Y retains the strongest average residual cycle score:

$$0.480,$$

suggesting a richer higher-order channel beyond the mixing basis.

H-H remains the counterexample: its degree-mixing signal is weak both before and after conditioning.

The appropriate central claim is:

> Degree-sector Born marginals expose a circuit-general joint-degree mixing coordinate across flat, normalized-degree, and Hadamard preparations with X or Y mixing. After cross-fitted linear removal of ordinary cycles, residual mixing scores remain between (0.895) and (0.923), and after removal of linearly accessible raw-spectrum information they remain between (0.913) and (0.930). Global sorting preserves this conditional channel for F-Y, partially preserves it for D-X, and nearly destroys it for H-X. The H-H architecture is a clear exception. E29B therefore establishes a robust, readout-dependent conditional mixing coordinate, but not statistical independence, unrestricted non-spectrality, or universal behavior across circuit architectures.


### E29C - Classical Location and Incremental Value of Degree-Sector Readout

#### Experimental purpose

E29C locates the degree-sector probability readout relative to elementary classical graph summaries.

The experiment does not test quantum advantage.

It asks two narrower questions.

1. **Incremental target value**

   Does the degree-sector readout improve cycle prediction after joint-degree mixing and the complete adjacency spectrum have already been supplied?

2. **Reverse reconstruction**

   How accurately can the degree-sector probability vector itself be reconstructed from joint-degree mixing and the spectrum?

The experiment extends these questions across the five E29 circuit families and four fixed-degree-sequence graph strata.

#### Execution status

E29C completed successfully.

It:

* loaded all five circuit families;
* evaluated all four strata;
* evaluated all four cycle targets;
* generated the incremental-value heatmap;
* completed the reverse reconstruction audit;
* saved the result artifact:

```text
e29c_classical_location.pkl
```

No cell terminated with an exception.

The cycle-model cell emitted 860 singular-matrix warnings from scikit-learn’s ridge solver. These warnings and one catastrophic fitted result require substantial qualification of the aggregate conclusions.

---

## Shared E29P producer

E29C uses the shared E29P artifacts employed throughout the E29X series.

The producer fixes:

* graph ordering;
* circuit angles;
* qubit convention;
* degree-sector construction;
* cycle targets;
* joint-degree mixing coordinates;
* adjacency spectra;
* and exact Born probabilities.

The four graph strata are:

| Stratum         | Locked degree sequence | Graphs | Mixing rank |
| --------------- | ---------------------- | -----: | ----------: |
| S1 near regular | $$(4,4,3^{10},2,2)$$   |    400 |           3 |
| S2 bimodal      | $$(4^7,2^7)$$          |    400 |           1 |
| S3 skewed       | $$(5,5,4,4,3^6,2^4)$$  |    400 |           6 |
| S4 hub          | $$(6,4,4,3^8,2,2,2)$$  |    400 |           5 |

Every analysis occurs within one fixed degree sequence.

#### Circuit bank

The five circuits are:

| Circuit | Preparation                                | Graph phase     | Final transformation |
| ------- | ------------------------------------------ | --------------- | -------------------- |
| F-X     | Flat $$R_X(2.875)$$                        | $$R_{ZZ}(2.0)$$ | $$R_X(0.1)$$         |
| D-X     | Normalized degree $$R_X(2.875d_i/\Delta)$$ | $$R_{ZZ}(2.0)$$ | $$R_X(0.1)$$         |
| H-X     | $$H^{\otimes14}$$                          | $$R_{ZZ}(2.0)$$ | $$R_X(0.1)$$         |
| F-Y     | Flat $$R_X(2.875)$$                        | $$R_{ZZ}(2.0)$$ | $$R_Y(0.1)$$         |
| H-H     | $$H^{\otimes14}$$                          | $$R_{ZZ}(2.0)$$ | $$H^{\otimes14}$$    |

#### Degree-sector readout

For degree classes:

$$d_1<\cdots<d_m,$$

define the occupancy signature of basis state $$z$$ as:

$$\kappa_G(z)=\left(\sum_{i:\deg(i)=d_1}z_i,\ldots,\sum_{i:\deg(i)=d_m}z_i\right).$$

The R2 coordinate for sector $$\kappa$$ is:

$$R_2(G)*\kappa=\sum*{z:\kappa_G(z)=\kappa}p_G(z).$$

The R2 dimensions are:

| Stratum | R2 dimension |
| ------- | -----------: |
| S1      |           99 |
| S2      |           64 |
| S3      |          315 |
| S4      |          216 |

R2 is a hybrid graph-conditioned circuit readout because the graph’s degree partition is supplied during aggregation.

---

## Classical feature banks

E29C uses three circuit-independent classical banks.

##### Joint-degree mixing

For degree classes $$a\le b$$:

$$M_{ab}=#{uv\in E:{\deg u,\deg v}={a,b}}.$$

The linearly dependent raw counts are reduced to the producer’s SVD mixing basis.

##### Adjacency spectrum

The spectral bank contains the complete sorted adjacency spectrum:

$$\lambda(G)=(\lambda_1,\ldots,\lambda_{14}).$$

Trace moments are intentionally omitted because they are deterministic power sums of the complete spectrum.

This avoids duplicating the same graph information, although a linear model on the raw eigenvalues does not automatically reconstruct nonlinear power sums.

##### Combined classical bank

The primary classical reference is:

$$X_{\text{classical}}(G)=\left[M(G),\lambda(G)\right].$$

Its dimensions are:

| Stratum | Mixing dimensions | Spectrum dimensions | Combined dimensions |
| ------- | ----------------: | ------------------: | ------------------: |
| S1      |                 3 |                  14 |                  17 |
| S2      |                 1 |                  14 |                  15 |
| S3      |                 6 |                  14 |                  20 |
| S4      |                 5 |                  14 |                  19 |

Cumulative folklore 2-WL is not included.

E29C therefore locates R2 relative only to:

* joint-degree mixing;
* and the raw complete spectrum.

---

## Prediction protocol

Every feature bank is evaluated through one common standardized ridge pipeline.

The protocol uses:

* five shuffled outer graph folds;
* outer seed zero;
* train-only `StandardScaler`;
* inner five-fold `RidgeCV`;
* regularization grid:

$$\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2};$$

* mean outer-fold test $$R^2$$.

The targets are:

$$C_3,\qquad C_4,\qquad C_5,\qquad C_6.$$

The five target models are:

1. mixing alone;
2. spectrum alone;
3. mixing plus spectrum;
4. R2 alone;
5. mixing plus spectrum plus R2.

The primary incremental statistic is:

$$\Delta R^2_{\text{inc}}=R^2(M+\lambda+R2)-R^2(M+\lambda).$$

A positive value means that the concatenated model predicts the target better than the mixing-plus-spectrum model under the tested ridge procedure.

It does not automatically mean that R2 supplies graph information outside the linear span of the classical bank.

#### Calibration

The standardized decoder produces:

$$R^2_{\text{null}}=-0.005,$$

and:

$$R^2_{\text{linear}}=1.000.$$

The basic implementation passes its synthetic calibration.

---

## Classical cycle baseline

The mixing-plus-spectrum model is circuit independent.

| Stratum         | $$C_3$$ | $$C_4$$ | $$C_5$$ | $$C_6$$ |
| --------------- | ------: | ------: | ------: | ------: |
| S1 near regular |   0.990 |   0.968 |   0.719 |   0.670 |
| S2 bimodal      |   0.987 |   0.963 |   0.611 |   0.666 |
| S3 skewed       |   0.990 |   0.965 |   0.688 |   0.630 |
| S4 hub          |   0.988 |   0.964 |   0.595 |   0.620 |

The classical bank nearly saturates C3 and C4 in all four strata.

It also provides moderate to strong prediction for C5 and C6.

The available residual room is therefore concentrated primarily in the longer-cycle targets.

These scores should not be described as algebraic recovery from the spectrum.

The model is linear in:

* raw eigenvalues;
* and the mixing coordinates.

Its strong finite-census performance can use correlations specific to the sampled strata.

---

## Complete incremental results

The R2-over-classical increments are:

| Stratum and target |      F-X |      D-X |      H-X |      F-Y |      H-H |
| ------------------ | -------: | -------: | -------: | -------: | -------: |
| S1 $$C_3$$         | (+0.007) | (-0.061) | (-0.001) | (+0.009) | (-0.004) |
| S1 $$C_4$$         | (-0.004) | (-0.002) | (-0.003) | (-0.010) | (-0.005) |
| S1 $$C_5$$         | (+0.202) | (-0.106) | (+0.171) | (+0.159) | (-0.010) |
| S1 $$C_6$$         | (-0.036) | (+0.040) | (-0.001) | (-0.004) | (+0.084) |
| S2 $$C_3$$         | (+0.013) | (+0.008) | (+0.006) | (+0.013) | (-0.002) |
| S2 $$C_4$$         | (+0.013) | (+0.009) | (+0.014) | (+0.015) | (-0.007) |
| S2 $$C_5$$         | (+0.294) | (+0.305) | (+0.307) | (+0.304) | (+0.005) |
| S2 $$C_6$$         | (+0.147) | (+0.176) | (+0.088) | (+0.118) | (+0.074) |
| S3 $$C_3$$         | (-0.007) | (-0.005) | (-0.004) | (-0.009) | (-0.031) |
| S3 $$C_4$$         | (-0.023) | (-0.021) | (-0.011) | (-0.030) | (-0.074) |
| S3 $$C_5$$         | (-0.051) | (-0.034) | (-0.009) | (-0.064) | (-0.109) |
| S3 $$C_6$$         | (-0.065) | (-0.037) | (-0.030) | (-0.075) | (+0.009) |
| S4 $$C_3$$         | (-0.005) | (-0.003) | (-0.002) | (-2.394) | (-0.015) |
| S4 $$C_4$$         | (-0.018) | (-0.010) | (-0.007) | (-0.016) | (-0.072) |
| S4 $$C_5$$         | (-0.011) | (+0.018) | (+0.035) | (+0.045) | (-0.030) |
| S4 $$C_6$$         | (-0.053) | (-0.053) | (-0.015) | (-0.053) | (+0.031) |

The result is highly structured.

* S2 C5 is positive for all four primary circuits.
* S2 C6 is also consistently positive.
* S1 C5 improves for F-X, H-X, and F-Y but not D-X or H-H.
* Nearly every S3 increment is negative.
* Nearly every S4 increment is negligible or negative.
* F-Y S4 C3 is catastrophically unstable.

---

## Circuit-level summaries

| Circuit | Mean increment |       Median increment | Positive cells | R2 reconstructed from $$M+\lambda$$ |
| ------- | -------------: | ---------------------: | -------------: | ----------------------------------: |
| F-X     |       (+0.025) |               (-0.006) |           6/16 |                               0.999 |
| D-X     |       (+0.014) |               (-0.004) |           6/16 |                               0.702 |
| H-X     |       (+0.034) | approximately (-0.002) |           6/16 |                               0.794 |
| F-Y     |       (-0.124) | approximately (-0.007) |           7/16 |                               0.998 |
| H-H     |       (-0.010) |               (-0.006) |           5/16 |                               0.177 |

The median increment is nonpositive for every circuit.

The small positive means for F-X, D-X, and H-X are driven by a limited number of larger C5 and C6 gains.

There is no broad circuit-wide incremental advantage.

#### F-Y outlier

The reported F-Y mean is dominated by one cell:

$$\Delta R^2_{\text{inc}}=-2.394$$

for S4 C3.

The classical model scores:

$$R^2(M+\lambda)=0.988,$$

and R2 alone scores:

$$R^2(R2)=0.853.$$

After concatenation, the score collapses to:

$$R^2(M+\lambda+R2)=-1.406.$$

Removing this single displayed cell changes F-Y’s mean increment from:

$$-0.124$$

to approximately:

$$+0.027.$$

The reported circuit mean is therefore not a stable representation summary.

The cell is best treated as a numerical or regularization failure, not evidence that R2 contains strongly adversarial C3 information.

---

## S2 deeper-cycle result

The most repeatable positive pattern occurs in the bimodal stratum.

##### C5

| Circuit | Classical | R2 alone | Combined | Increment |
| ------- | --------: | -------: | -------: | --------: |
| F-X     |     0.611 |    0.468 |    0.905 |  (+0.294) |
| D-X     |     0.611 |    0.592 |    0.916 |  (+0.305) |
| H-X     |     0.611 |    0.472 |    0.918 |  (+0.307) |
| F-Y     |     0.611 |    0.739 |    0.916 |  (+0.304) |
| H-H     |     0.611 |    0.163 |    0.617 |  (+0.005) |

The four preparation–phase–small-mixer circuits all raise S2 C5 prediction from:

$$0.611$$

to approximately:

$$0.905\text{--}0.918.$$

H-H does not reproduce the result.

##### C6

| Circuit | Classical | R2 alone | Combined | Increment |
| ------- | --------: | -------: | -------: | --------: |
| F-X     |     0.666 |    0.594 |    0.813 |  (+0.147) |
| D-X     |     0.666 |    0.654 |    0.842 |  (+0.176) |
| H-X     |     0.666 |    0.526 |    0.754 |  (+0.088) |
| F-Y     |     0.666 |    0.580 |    0.784 |  (+0.118) |
| H-H     |     0.666 |    0.353 |    0.740 |  (+0.074) |

S2 C6 also improves under every circuit.

The primary four circuits produce gains from:

$$0.088\text{ to }0.176.$$

This is weaker than the C5 result but more general across the complete circuit bank.

#### Interpretation

S2 has only one independent degree-mixing coordinate.

E29B showed unusually strong overlap among:

* mixing;
* cycles;
* and spectrum

in this stratum.

E29C now shows that the R2 coordinate system can substantially improve regularized prediction of the deeper cycles beyond the direct mixing-plus-spectrum feature bank.

This is the strongest positive result in E29C.

It still does not prove that R2 contains classically unavailable information because the incremental model is not based on an orthogonal R2 residual.

---

## S1 C5 result

S1 C5 provides a secondary positive pattern.

| Circuit | Classical | R2 alone | Combined | Increment |
| ------- | --------: | -------: | -------: | --------: |
| F-X     |     0.719 |    0.097 |    0.921 |  (+0.202) |
| D-X     |     0.719 |    0.114 |    0.613 |  (-0.106) |
| H-X     |     0.719 |    0.141 |    0.891 |  (+0.171) |
| F-Y     |     0.719 |    0.166 |    0.879 |  (+0.159) |
| H-H     |     0.719 | (-0.006) |    0.709 |  (-0.010) |

F-X, H-X, and F-Y improve substantially.

D-X becomes worse, and H-H remains unchanged.

The result therefore depends on circuit architecture and is not a universal property of degree-sector marginalization.

---

## S3 and S4

The incremental result is predominantly negative in the skewed and hub strata.

#### S3

Across all circuits and targets, nearly every increment is below zero.

The mixing-plus-spectrum baseline already scores:

$$0.990,\quad0.965,\quad0.688,\quad0.630$$

for C3 through C6.

Adding R2 generally reduces held-out performance.

This does not imply that R2 lacks structural information.

E29A and E29B show that R2 strongly carries degree mixing under four circuits. The S3 result instead indicates that the R2 coordinate system does not improve these cycle predictions beyond the tested classical ridge model.

#### S4

Most S4 increments are also near zero or negative.

The only recurring positive values are small C5 gains for D-X, H-X, and F-Y.

The F-Y C3 failure prevents meaningful aggregation without a numerical correction.

---

## Reverse reconstruction of R2

E29C predicts each circuit’s entire R2 vector from:

* mixing;
* spectrum;
* and their combination.

The displayed mixing-plus-spectrum reconstruction scores are:

| Circuit |   S1 |   S2 |   S3 |   S4 |  Mean |
| ------- | ---: | ---: | ---: | ---: | ----: |
| F-X     | 1.00 | 1.00 | 1.00 | 1.00 | 0.999 |
| D-X     | 0.94 | 0.84 | 0.61 | 0.41 | 0.702 |
| H-X     | 0.89 | 0.92 | 0.61 | 0.76 | 0.794 |
| F-Y     | 1.00 | 1.00 | 1.00 | 1.00 | 0.998 |
| H-H     | 0.24 | 0.27 | 0.09 | 0.11 | 0.177 |

#### F-X and F-Y

The sector-mass vectors are almost perfectly reconstructed from joint-degree mixing and the raw spectrum.

The mean pooled scores are:

$$0.999$$

and:

$$0.998.$$

Under this linear standardized probe, the two R2 representations lie almost entirely on a classically described manifold.

This is the clearest E29C result.

#### D-X

D-X is strongly reconstructible in S1 and S2 but only partially reconstructible in the more irregular strata:

$$0.61\quad\text{and}\quad0.41.$$

The normalized degree encoder therefore produces substantial sector-mass variation not linearly explained by the tested classical bank.

#### H-X

H-X is partially reconstructible throughout the four strata:

$$0.61\text{--}0.92.$$

The graph-phase distribution contains additional sector structure beyond the direct linear mixing-plus-spectrum model.

#### H-H

H-H is only weakly reconstructed:

$$0.09\text{--}0.27.$$

Most of its sector-mass variance lies outside the tested linear classical feature bank.

However, H-H produces essentially no average incremental cycle benefit:

$$\overline{\Delta R^2_{\text{inc}}}=-0.010.$$

Thus, structure unexplained by mixing and spectrum is not automatically useful for the tested cycle targets.

---

## Classical reconstruction does not predict incremental value

The reverse and forward results do not follow a simple ordering.

##### Nearly complete classical reconstruction with positive target gains

F-X and F-Y R2 are almost perfectly reconstructed from:

$$M+\lambda.$$

Nevertheless, they produce substantial S2 C5 gains and selected S1 C5 gains.

##### Partial classical reconstruction with small average gains

D-X and H-X contain much more R2 variation unexplained by the classical bank.

Their average increments are only:

$$0.014$$

and:

$$0.034.$$

##### Low classical reconstruction without target gain

H-H contains the largest unexplained R2 component but has:

$$\overline{\Delta R^2_{\text{inc}}}=-0.010.$$

The amount of R2 variance outside the tested classical bank is therefore poorly aligned with incremental cycle prediction.

The supported interpretation is:

> Classical reconstructibility and cycle usefulness are separate properties. A circuit can produce classically unexplained degree-sector structure that is irrelevant to the tested cycles, while a nearly classically reconstructible representation can improve a regularized cycle model through a more favorable coordinate system.

---

## Why concatenation does not establish new information

The notebook interprets a positive increment as R2 carrying cycle-aligned structure not supplied by mixing and spectrum.

That wording is too strong.

Suppose R2 is a linear transformation of the classical bank:

$$R2\approx X_{\text{classical}}B.$$

Then concatenating:

$$[X_{\text{classical}},R2]$$

may add little or no new linear information.

It can nevertheless improve ridge prediction because:

* the coordinates are standardized separately;
* duplicated or transformed directions change the ridge penalty geometry;
* the expanded representation changes effective regularization;
* inner cross-validation can select a different penalty;
* and small R2 residual directions can be highly target aligned.

The near-perfect reverse reconstruction of F-X and F-Y demonstrates that this issue is not hypothetical.

Their positive increments cannot be interpreted directly as evidence of graph information beyond mixing and spectrum.

A cleaner incremental-information test would:

1. cross-fit R2 from the classical bank;
2. form the residual sector representation:

$$R2_\perp=R2-\widehat{R2}(M,\lambda);$$

3. add only $$R2_\perp$$ to the classical cycle model;
4. evaluate the target gain on held-out graphs.

Alternatively, the classical and R2 feature spaces could be explicitly orthogonalized within each outer-training fold.

E29C does not perform this test.

Its increment is a **regularized coordinate-addition statistic**, not an information decomposition.

---

## Numerical stability audit

The cycle-model cell emits:

$$860$$

warnings of the form:

```text
Singular matrix in solving dual problem. Using least-squares solution instead.
```

The notebook suppresses `LinAlgWarning`, but scikit-learn emits these events as `UserWarning`, so the fallback remains active.

The warnings indicate that many inner ridge fits encounter singular or near-singular systems.

The risk is highest for the concatenated models because they combine:

* constrained mixing coordinates;
* the complete spectrum;
* 64–315 R2 coordinates;
* only 400 graphs;
* and ridge penalties as small as $$10^{-14}$$.

The F-Y S4 C3 collapse is consistent with this instability.

E29C saves no fold-level standard deviations for the cycle models. The code calls the decoder but retains only its mean score.

Consequently, the notebook cannot show whether:

* the positive S2 gains occur consistently across folds;
* the negative values are concentrated in one split;
* or the F-Y failure arises from one catastrophic fold.

The incremental results should remain exploratory until independently reproduced with:

* a numerically stable SVD or dual solver;
* a less extreme minimum ridge penalty;
* fold-level scores;
* and preferably residualized R2 features.

---

## Relationship to E29A

E29A showed that R2 almost perfectly reconstructs joint-degree mixing for:

* F-X;
* D-X;
* H-X;
* F-Y.

E29C asks whether R2 contributes cycle prediction beyond directly supplying mixing and spectrum.

The answer is mostly no.

The incremental gains are:

* concentrated in S2 C5 and C6;
* partially present in S1 C5;
* absent or negative across most S3 and S4 cells.

Thus, the strong degree-mixing accessibility in E29A does not translate into a broad cycle advantage beyond the classical banks.

## Relationship to E29B

E29B showed that R2 retains a degree-mixing coordinate after linear cycle or spectrum residualization.

E29C studies the reverse direction:

> Does R2 improve cycle prediction after mixing and spectrum are supplied directly?

The results are compatible.

R2 can strongly encode residual mixing while adding little to cycle prediction.

The conditional mixing coordinate and the incremental cycle coordinate are not the same structural object.

## What the experiment establishes

The completed results establish that:

1. **E29C completed all circuits, strata, and cycle targets and saved its artifact.**

2. **Mixing plus the complete raw spectrum nearly saturates C3 and C4 in every stratum.**

3. **The principal residual prediction opportunity lies in C5 and C6.**

4. **R2 does not provide a broad incremental cycle advantage.**

   Every circuit has a nonpositive median increment.

5. **The strongest repeatable gain occurs for S2 C5.**

   The four primary circuits improve by approximately (0.294)–(0.307).

6. **S2 C6 also improves across the complete circuit bank.**

7. **S1 C5 improves under F-X, H-X, and F-Y but not D-X or H-H.**

8. **R2 generally does not improve S3 or S4 cycle prediction.**

9. **F-X and F-Y R2 are almost perfectly reconstructed from mixing and spectrum.**

10. **D-X and H-X R2 are only partially reconstructed, especially in irregular strata.**

11. **H-H R2 is mostly unexplained by the tested classical bank but provides no average cycle gain.**

12. **Classical reconstruction gap is not a proxy for target usefulness.**

13. **Positive concatenation increments do not prove new information beyond the classical feature span.**

14. **The cycle analysis is numerically unstable under the current ridge grid.**

15. **The F-Y aggregate is invalidated by one catastrophic S4 C3 fit.**

E29C therefore locates the main R2 benefit as a target- and stratum-specific coordinate effect rather than broad information beyond mixing and spectrum.

---

## Necessary qualifications

The primary increment is based on feature concatenation rather than orthogonal residualization.

It cannot distinguish:

* new information;
* a better coordinate parameterization;
* altered regularization;
* duplicated directions;
* or preconditioning effects.

The reverse reconstruction uses pooled multivariate $$R^2$$ across R2 coordinates.

Sector coordinates with greater variance contribute more heavily.

Near-perfect pooled reconstruction does not prove that every degree sector is individually reconstructed.

Conversely, low pooled reconstruction can be driven by many low-amplitude sector directions that are irrelevant to cycle prediction.

The mixing basis is constructed globally by SVD over all 400 graphs before outer cross-validation.

This uses held-out feature information to determine:

* centering;
* rank;
* and basis orientation.

A stricter implementation would derive an analytical independent mixing basis or fit it within each outer-training fold.

The complete spectrum is supplied as 14 raw eigenvalues.

The model is linear and does not remove arbitrary nonlinear spectral functions.

E29C therefore does not locate R2 relative to the complete algebra of spectral invariants.

The five models are not capacity matched.

Their feature dimensions range from:

* 15–20 classical coordinates;
* 64–315 R2 coordinates;
* to as many as 335 concatenated coordinates.

The same ridge grid can impose very different effective regularization across these spaces.

The minimum penalty:

$$10^{-14}$$

is too close to an unregularized fit for several highly collinear standardized designs.

The 860 solver warnings and F-Y failure confirm that this is not merely theoretical.

No fold-level standard deviations, confidence intervals, permutation tests, or paired bootstrap comparisons are reported for the incremental values.

The experiment evaluates:

$$5\times4\times4=80$$

incremental cells without correction for multiplicity.

The means across 16 cells assign equal weight to:

* four different cycle lengths;
* four different graph strata;
* positive and negative $$R^2$$ values;
* and targets with different variances.

They are descriptive only.

The R2-only scores use a standardized probe and should not be compared numerically with the raw-coordinate E29A or E29B values.

The producer’s prior qualifications remain:

* R2 uses graph-supplied degree classes;
* the mixing SVD is global;
* the R2 relabeling test is weaker than a coordinatewise test;
* and the claimed direct E26R R2 assertion was not implemented.

Cumulative folklore 2-WL is absent.

The experiment therefore does not place R2 relative to the strongest higher-order classical representation used elsewhere in the paper.

All results use exact ideal probabilities.

No finite-shot analysis tests whether the relevant R2 coordinates can be recovered operationally.

Finally, the experiment covers:

* one graph order;
* four sampled degree sequences;
* one fixed angle schedule;
* and one shallow circuit layer.

It establishes finite-family linear accessibility rather than universal representation structure.

---

## Overall assessment

E29C is primarily a negative localization result.

The classical bank of joint-degree mixing and raw adjacency eigenvalues already predicts:

$$C_3\approx0.99,$$

$$C_4\approx0.96,$$

and C5–C6 at approximately:

$$0.60\text{--}0.72$$

across the four strata.

Adding R2 does not produce a general improvement.

Every circuit has a nonpositive median increment, and most S3 and S4 cells become slightly worse.

The clear positive exception is the bimodal stratum.

For S2 C5, the four principal circuits improve the classical score from:

$$0.611$$

to approximately:

$$0.905\text{--}0.918.$$

S2 C6 also improves across the circuit bank.

The reverse audit places F-X and F-Y R2 almost entirely within the linear mixing-plus-spectrum manifold:

$$R^2_{\text{reconstruct}}\approx1.$$

D-X and H-X contain more unexplained sector structure, while H-H is mostly unreconstructed.

That unexplained variation does not predict incremental cycle value.

The appropriate central claim is:

> Degree-sector Born marginals do not provide a broad cycle-prediction advantage beyond joint-degree mixing and the raw adjacency spectrum. Incremental gains are concentrated in the bimodal family, where R2 raises C5 prediction from (0.611) to approximately (0.91) under four preparation–phase–mixer circuits and also improves C6. F-X and F-Y sector vectors are themselves almost perfectly reconstructed from mixing and spectrum, while H-H is largely unreconstructed but provides no average cycle gain. E29C therefore shows that classical unexplained variance and target usefulness are distinct, and that positive R2 concatenation gains can reflect a favorable regularized coordinate system rather than new information outside the classical feature span. The current incremental results remain exploratory because the concatenated fits emit extensive singular-matrix warnings and include one catastrophic F-Y failure.


### E29D - Cross-Circuit Geometry and Complementarity Audit

#### Experimental purpose

E29D asks whether the degree-sector representations produced by different E29 circuit families are:

* geometrically redundant;
* structurally distinct but predictively equivalent;
* or genuinely complementary.

The experiment evaluates circuit relationships at three levels.

1. **Representation geometry**

   Compare the complete degree-sector mass matrices using linear centered-kernel alignment, pairwise-distance ordering, and concentration diagnostics.

2. **Prediction-error geometry**

   Compare independently generated out-of-fold residuals and graph-level squared errors under the frozen E6 ridge probe.

3. **Nested prediction stacking**

   Combine circuit-specific base predictions using a nonnegative meta-model and compare the stacked predictor with the strongest standalone circuit.

The first two analyses completed and provide usable descriptive results.

The stacking analysis also completed computationally, but two implementation defects invalidate its reported gains. E29D therefore does not provide a valid final test of predictive complementarity.

#### Execution status

The notebook completed all cells without an exception.

It successfully:

* loaded all five E29P circuit families;
* gated graph ordering and trace identities;
* computed representation-level geometry;
* generated out-of-fold predictions;
* computed prediction-error comparisons;
* executed the proposed nested stacking procedure;
* saved `e29d_complementarity.pkl`;
* saved `e29d_stacking_gain.png`.

Completion of the code does not imply validity of every statistic. The stacking implementation requires correction before its outputs can be interpreted.

---

## Shared E29P producer

E29D uses the common E29P artifacts employed by E29A–E29C.

The producer supplies identical:

* graph ordering;
* degree-sector definitions;
* circuit parameters;
* probability conventions;
* cycle targets;
* joint-degree mixing coordinates;
* and concentration diagnostics.

The experiment uses the four fixed-degree-sequence strata at:

$$n=14.$$

| Stratum         | Locked degree sequence | Graphs | Mixing rank |
| --------------- | ---------------------- | -----: | ----------: |
| S1 near regular | $$(4,4,3^{10},2,2)$$   |    400 |           3 |
| S2 bimodal      | $$(4^7,2^7)$$          |    400 |           1 |
| S3 skewed       | $$(5,5,4,4,3^6,2^4)$$  |    400 |           6 |
| S4 hub          | $$(6,4,4,3^8,2,2,2)$$  |    400 |           5 |

Every comparison occurs within one fixed degree sequence.

#### Circuit bank

The five available circuits are:

| Circuit | Preparation                                | Graph phase     | Final transformation |
| ------- | ------------------------------------------ | --------------- | -------------------- |
| F-X     | Flat $$R_X(2.875)$$                        | $$R_{ZZ}(2.0)$$ | $$R_X(0.1)$$         |
| D-X     | Normalized degree $$R_X(2.875d_i/\Delta)$$ | $$R_{ZZ}(2.0)$$ | $$R_X(0.1)$$         |
| H-X     | $$H^{\otimes14}$$                          | $$R_{ZZ}(2.0)$$ | $$R_X(0.1)$$         |
| F-Y     | Flat $$R_X(2.875)$$                        | $$R_{ZZ}(2.0)$$ | $$R_Y(0.1)$$         |
| H-H     | $$H^{\otimes14}$$                          | $$R_{ZZ}(2.0)$$ | $$H^{\otimes14}$$    |

The primary pairwise analyses compare F-X with:

* D-X;
* H-X;
* F-Y.

H-H is included only in the all-circuit stacking configuration.

#### Degree-sector readout

For degree classes:

$$d_1<\cdots<d_m,$$

the occupancy signature of basis state $$z$$ is:

$$\kappa_G(z)=\left(\sum_{i:\deg(i)=d_1}z_i,\ldots,\sum_{i:\deg(i)=d_m}z_i\right).$$

The R2 representation is:

$$R_2(G)*\kappa=\sum*{z:\kappa_G(z)=\kappa}p_G(z).$$

Its dimension ranges from:

$$64\text{ to }315$$

across the four strata.

R2 is a graph-conditioned circuit readout because the degree partition is explicitly supplied during aggregation.

---

## Validation gates

For every circuit and stratum, E29D verifies that graph ordering matches the E6 dataset.

For every one of the 1,600 graphs, it also reasserts:

$$\text{tr}(A^3)=6C_3,$$

and:

$$\text{tr}(A^4)=8C_4+2\sum_i d_i^2-\sum_i d_i.$$

All five circuit artifacts are present for every stratum.

The notebook does not independently revalidate:

* circuit probabilities;
* R2 normalization;
* sector cardinalities;
* or permutation invariance.

Those checks are inherited from the E29P producer.

---

# Representation-Level Geometry

#### Metrics

For each principal circuit pair and stratum, E29D computes four quantities.

##### Linear centered-kernel alignment

For centered representation matrices $$X$$ and $$Y$$:

$$\text{CKA}(X,Y)=\frac{|Y^\top X|_F^2}{|X^\top X|_F|Y^\top Y|_F}.$$

High CKA indicates that the two feature matrices span similarly organized linear variation across graphs.

##### Pairwise-distance correlation

For 4,000 sampled graph pairs, E29D computes each circuit’s R2 Manhattan distance:

$$d_{R2}(G,H)=|R_2(G)-R_2(H)|_1,$$

and reports the Spearman correlation between the two circuits’ distance vectors.

This measures agreement in coarse pairwise graph ordering.

##### Sector entropy

For R2 sector masses:

$$H_{\text{sector}}(G)=-\sum_\kappa R_2(G)*\kappa\log R_2(G)*\kappa.$$

##### Effective sector count

$$K_{\text{sector}}(G)=\exp(H_{\text{sector}}(G)).$$

Because effective sector count is a deterministic transform of sector entropy, the two reported correlations are largely redundant.

---

## Complete representation-geometry results

| Circuit pair | Stratum |   CKA | L1-distance Spearman | Sector-entropy correlation |
| ------------ | ------- | ----: | -------------------: | -------------------------: |
| F-X vs D-X   | S1      | 0.359 |                0.873 |                      0.957 |
| F-X vs D-X   | S2      | 0.898 |                0.749 |                   (-0.099) |
| F-X vs D-X   | S3      | 0.249 |                0.439 |                      0.074 |
| F-X vs D-X   | S4      | 0.281 |                0.574 |                   (-0.548) |
| F-X vs H-X   | S1      | 0.606 |                0.728 |                      0.773 |
| F-X vs H-X   | S2      | 0.922 |                0.824 |                      0.996 |
| F-X vs H-X   | S3      | 0.454 |                0.594 |                      0.205 |
| F-X vs H-X   | S4      | 0.636 |                0.701 |                      0.748 |
| F-X vs F-Y   | S1      | 0.647 |                0.665 |                   (-0.514) |
| F-X vs F-Y   | S2      | 0.998 |                0.863 |                      0.999 |
| F-X vs F-Y   | S3      | 0.611 |                0.772 |                   (-0.478) |
| F-X vs F-Y   | S4      | 0.675 |                0.780 |                   (-0.010) |

The unweighted means across strata are:

| Circuit pair | Mean CKA | Mean distance Spearman | Mean entropy correlation |
| ------------ | -------: | ---------------------: | -----------------------: |
| F-X vs D-X   |    0.447 |                  0.659 |                    0.096 |
| F-X vs H-X   |    0.655 |                  0.712 |                    0.681 |
| F-X vs F-Y   |    0.733 |                  0.770 |      approximately 0.000 |

---

## F-X versus D-X

F-X and D-X exhibit the weakest linear alignment of the three principal pairs.

Outside S2, CKA ranges only from:

$$0.249\text{ to }0.359.$$

The pairwise-distance correlation is nevertheless moderate or strong:

$$0.439\text{ to }0.873.$$

This combination indicates that the two circuits can preserve similar coarse graph-distance ordering while expressing that ordering through different feature directions.

S1 is the clearest example:

$$\text{CKA}=0.359,$$

but:

$$\rho_{\text{distance}}=0.873.$$

The concentration geometry also changes sharply by stratum.

In S1, sector entropy is strongly aligned:

$$r=0.957.$$

In S4, it is anticorrelated:

$$r=-0.548.$$

Graphs that produce a relatively diffuse F-X sector distribution can therefore produce a relatively concentrated D-X distribution, or conversely, within the hub stratum.

Normalized degree preparation materially reorganizes the representation even when some coarse graph-distance ordering survives.

---

## F-X versus H-X

F-X and H-X have intermediate representation alignment.

Their CKA values range from:

$$0.454\text{ to }0.922,$$

and their distance correlations range from:

$$0.594\text{ to }0.824.$$

S2 is again the most aligned stratum:

$$\text{CKA}=0.922,$$

$$\rho_{\text{distance}}=0.824,$$

$$r_{\text{entropy}}=0.996.$$

The skewed stratum is substantially less aligned:

$$\text{CKA}=0.454,$$

and:

$$r_{\text{entropy}}=0.205.$$

Hadamard preparation preserves a recognizable version of the F-X graph geometry but changes it substantially in the more compositionally complex degree sequences.

---

## F-X versus F-Y

F-X and F-Y have the strongest overall representation alignment.

Their average values are:

$$\overline{\text{CKA}}=0.733,$$

and:

$$\overline{\rho}_{\text{distance}}=0.770.$$

In S2, the linear geometries are nearly identical:

$$\text{CKA}=0.998.$$

Changing the mixer from X to Y therefore leaves the dominant bimodal degree-sector geometry almost unchanged.

The concentration results are more complicated.

Despite moderate-to-high CKA and distance agreement, entropy correlations are:

$$-0.514$$

in S1 and:

$$-0.478$$

in S3.

Thus, two circuits can organize intergraph distances similarly while reversing which individual graphs produce the more concentrated sector distributions.

Because F-X and F-Y both occupy only approximately two effective sectors on average, the entropy variation may be narrow. No diagnostic range or uncertainty interval is reported, so these negative correlations should remain descriptive.

---

## Representation-Level Interpretation

The three circuit modifications produce different forms of geometry.

* **D-X** most strongly changes the feature orientation and concentration ordering.
* **H-X** retains a moderate version of the F-X geometry.
* **F-Y** preserves the strongest global feature and distance geometry but can reverse graph-level concentration rankings.
* **S2** is consistently the most aligned stratum across all three circuit pairs.

The representation-level result supports:

> The E29 circuit families are neither identical nor wholly unrelated. They often preserve similar coarse graph-distance ordering while reorganizing feature directions and probability concentration in architecture- and degree-sequence-dependent ways.

Representation non-equivalence alone does not establish useful predictive complementarity.

---

# Prediction-Level Error Geometry

#### Frozen decoder

Out-of-fold predictions are generated using the E6 probe:

* raw R2 features;
* five shuffled outer folds;
* seed zero;
* inner five-fold `RidgeCV`;
* regularization grid:

$$\alpha_{\text{ridge}}\in{10^{-14},10^{-13},\ldots,10^2}.$$

The synthetic calibration gives:

$$R^2_{\text{null}}=-0.005,$$

and:

$$R^2_{\text{linear}}=1.000.$$

The decoder implementation matches the E29A R2 decoder in code structure, although E29D does not perform a direct numerical equality assertion against the saved E29A predictions.

#### Error metrics

For scalar targets, the notebook computes the correlation between signed residuals:

$$r_{\text{residual}}=\text{corr}(y-\widehat y_A,y-\widehat y_B).$$

For every target, it computes per-graph squared error:

$$e_i^{(c)}=|y_i-\widehat y_i^{(c)}|_2^2,$$

and the correlation:

$$r_{\text{SE}}=\text{corr}(e^{(A)},e^{(B)}).$$

Low correlations indicate that the two circuits tend to fail on different graphs or in different directions.

---

## Complete prediction-level results

| Circuit pair | Target  | Residual correlation | Squared-error correlation |
| ------------ | ------- | -------------------: | ------------------------: |
| F-X vs D-X   | Mixing  |                0.313 |                     0.509 |
| F-X vs D-X   | $$C_3$$ |             (-0.150) |                     0.402 |
| F-X vs D-X   | $$C_4$$ |                0.547 |                     0.544 |
| F-X vs D-X   | $$C_5$$ |                0.839 |                     0.719 |
| F-X vs D-X   | $$C_6$$ |                0.883 |                     0.822 |
| F-X vs H-X   | Mixing  |                0.010 |                     0.287 |
| F-X vs H-X   | $$C_3$$ |             (-0.047) |                     0.250 |
| F-X vs H-X   | $$C_4$$ |                0.463 |                     0.495 |
| F-X vs H-X   | $$C_5$$ |                0.810 |                     0.642 |
| F-X vs H-X   | $$C_6$$ |                0.856 |                     0.784 |
| F-X vs F-Y   | Mixing  |                0.038 |                     0.531 |
| F-X vs F-Y   | $$C_3$$ |                0.223 |                     0.551 |
| F-X vs F-Y   | $$C_4$$ |                0.550 |                     0.467 |
| F-X vs F-Y   | $$C_5$$ |                0.890 |                     0.825 |
| F-X vs F-Y   | $$C_6$$ |                0.930 |                     0.905 |

#### Mixing residual-correlation caveat

The mixing target is multivariate in S1, S3, and S4.

The code computes signed residual correlation only when the target has one column.

Consequently, the displayed mixing residual correlations:

$$0.313,\quad0.010,\quad0.038$$

come only from S2, whose mixing rank is one.

They are not four-stratum mixing summaries.

The squared-error correlations do include all four strata.

---

## Triangle errors

Triangle residuals are weakly correlated or anticorrelated:

$$-0.150,\quad-0.047,\quad0.223.$$

The squared-error correlations are also low to moderate:

$$0.250\text{ to }0.551.$$

This is the strongest prediction-level evidence that the circuits make meaningfully different errors.

In particular, F-X versus H-X has:

$$r_{\text{SE}}=0.250.$$

The two representations tend to identify different graphs as easy or difficult for triangle prediction.

This is a necessary condition for useful ensemble complementarity, but not sufficient evidence that an ensemble improves held-out prediction.

---

## Four-cycle errors

C4 occupies an intermediate regime.

Residual correlations range from:

$$0.463\text{ to }0.550,$$

and squared-error correlations range from:

$$0.467\text{ to }0.544.$$

The circuits are neither fully redundant nor strongly independent on this target.

---

## Five- and six-cycle errors

C5 and C6 errors are highly aligned.

For C5:

$$r_{\text{residual}}=0.810\text{--}0.890,$$

and:

$$r_{\text{SE}}=0.642\text{--}0.825.$$

For C6:

$$r_{\text{residual}}=0.856\text{--}0.930,$$

and:

$$r_{\text{SE}}=0.784\text{--}0.905.$$

The different circuits therefore tend to make similar longer-cycle errors.

This suggests limited ensemble opportunity for C5 and C6, even though their raw R2 representations are not identical.

---

## Median-error discordance

The notebook attempts to count graphs that one circuit predicts successfully while the other misses.

For each circuit separately, “success” is defined as squared error below that circuit’s own median.

The reported directional counts are always equal.

For example:

```text id="6t1lps"
exclusive F-X:376 D-X:376
```

for F-X versus D-X on C3.

This equality is forced by the definition.

Within each stratum, both below-median sets contain the same number of graphs. Therefore:

$$|A\setminus B|=|B\setminus A|.$$

The counts cannot identify which circuit has more exclusive successes.

They measure only disagreement between the two median-error rankings.

The total discordant graph counts are:

| Pair       | Mixing | $$C_3$$ | $$C_4$$ | $$C_5$$ | $$C_6$$ |
| ---------- | -----: | ------: | ------: | ------: | ------: |
| F-X vs D-X |    760 |     752 |     588 |     446 |     382 |
| F-X vs H-X |    700 |     780 |     620 |     468 |     388 |
| F-X vs F-Y |    738 |     782 |     546 |     350 |     298 |

Out of 1,600 graphs, the corresponding C3 discordance rates are approximately:

$$47%\text{--}49%.$$

The C6 discordance rates fall to approximately:

$$19%\text{--}24%.$$

This supports the residual-correlation result:

* triangle difficulty rankings differ substantially;
* longer-cycle difficulty rankings are much more similar.

The notebook stores a mean paired squared-error difference that could identify the lower-error circuit, but it does not print that statistic in the completed output.

---

# Nested Stacking Audit

#### Intended model

The notebook intends to fit a nonnegative meta-model:

$$\widehat y_{\text{stack}}=\sum_c w_c\widehat y_c,$$

where each base prediction is generated out of fold inside the outer-training set.

The tested configurations are:

* F-X plus H-X;
* F-X plus F-Y;
* F-X plus D-X;
* all five circuits.

The design correctly avoids concatenating the raw circuit feature matrices.

It also correctly constructs inner out-of-fold base predictions for the outer-training graphs.

However, the meta-model and evaluation contain two decisive implementation errors.

---

## Stacking defect 1 - Centered target with uncentered base predictions

The code computes the outer-training target mean:

$$\overline y_{\text{train}},$$

then solves:

$$\min_{w\ge0}|\widehat Y_{\text{base}}w-(y-\overline y_{\text{train}})|_2^2.$$

It predicts:

$$\widehat y_{\text{stack}}=\widehat Y_{\text{base,test}}w+\overline y_{\text{train}}.$$

The base predictions are not centered.

Each base predictor already contains its own fitted target mean or intercept. The meta-model therefore tries to explain a centered target using uncentered predictions.

For positive count targets, nonnegative least squares can respond by shrinking the weights toward zero. The resulting predictor approaches the training mean:

$$\widehat y_{\text{stack}}\approx\overline y_{\text{train}}.$$

This is exactly the pattern in the outputs.

The cycle stacks return scores close to zero despite standalone scores as high as:

$$0.993.$$

The appropriate centered implementation would be:

$$\widetilde Y_{\text{base}}=\widehat Y_{\text{base}}-\overline{\widehat Y}_{\text{base,train}},$$

followed by:

$$\min_{w\ge0}|\widetilde Y_{\text{base,train}}w-(y-\overline y_{\text{train}})|_2^2,$$

and:

$$\widehat y_{\text{stack}}=(\widehat Y_{\text{base,test}}-\overline{\widehat Y}*{\text{base,train}})w+\overline y*{\text{train}}.$$

An alternative is a positive linear regression with an independently fitted intercept.

Without this correction, the cycle-stacking results do not measure complementarity.

---

## Stacking defect 2 - Inconsistent R² denominators

The stacked model accumulates its target sum of squares separately within every outer test fold:

$$\text{SST}*{\text{stack}}=\sum_f\sum*{i\in f}(y_i-\overline y_f)^2.$$

The standalone comparator uses one mean per complete stratum:

$$\text{SST}*{\text{standalone}}=\sum_s\sum*{i\in s}(y_i-\overline y_s)^2.$$

These denominators are not equal.

The reported gain:

$$R^2_{\text{stack}}-R^2_{\text{standalone}}$$

therefore subtracts scores defined using different baselines.

Even with a corrected meta-model, the displayed gain would not be a valid like-for-like comparison.

Both stacked and standalone predictions must be evaluated using the identical:

* graph set;
* pooled prediction vector;
* and target-centering convention.

---

## Reported stacking outputs

The notebook reports:

| Target  | Least-negative configuration |     Stacked $$R^2$$ | Reported best standalone |       Reported gain |
| ------- | ---------------------------- | ------------------: | -----------------------: | ------------------: |
| Mixing  | F-X plus D-X                 |               0.999 |                    1.000 | approximately 0.000 |
| $$C_3$$ | F-X plus H-X                 |               0.171 |                    0.704 |            (-0.533) |
| $$C_4$$ | F-X plus D-X                 |               0.036 |                    0.426 |            (-0.390) |
| $$C_5$$ | F-X plus D-X                 | approximately 0.000 |                    0.231 |            (-0.231) |
| $$C_6$$ | F-X plus H-X                 |            (-0.004) |                    0.231 |            (-0.234) |

The all-circuit stacks are similarly poor.

These numbers must not be interpreted as evidence that:

* circuit stacking is harmful;
* one circuit subsumes all others;
* the circuits are predictively redundant;
* or the low triangle residual correlations fail to produce ensemble value.

The test is invalid because of the centering and denominator defects.

The mixing stack remains near one because the SVD mixing coordinates are centered around zero and standalone prediction is already saturated. That result does not validate the stacking implementation for noncentered cycle-count targets.

---

## What a corrected stacking rerun should do

A corrected analysis should:

1. generate inner out-of-fold base predictions exactly as E29D already does;

2. center every base-prediction column using only the outer-training graphs;

3. center the outer-training target;

4. fit nonnegative weights to those centered quantities;

5. apply the training base means to center the outer-test base predictions;

6. restore the outer-training target mean;

7. evaluate stacked and standalone predictions under exactly the same pooled $$R^2$$ definition;

8. print fold-level weights and gains;

9. compare the stack with the best base circuit on each outer fold or through one fixed pooled metric;

10. preferably repeat the outer partition or bootstrap the held-out graph errors.

The corrected test may still show no stacking benefit, particularly for C5 and C6 where the error correlations are high.

The current notebook cannot answer that question.

---

# Relationship to E29A

E29A showed that several circuits achieve similar aggregate structural scores under R2.

E29D demonstrates that similar aggregate performance does not imply identical representation geometry.

In particular:

* F-X and D-X have low CKA outside S2;
* F-X and H-X have distinct triangle error patterns;
* F-X and F-Y preserve similar distance geometry but can reverse concentration ordering.

E29D therefore supplies a useful geometric decomposition of the E29A screen.

# Relationship to E29B

E29B showed that F-X, D-X, H-X, and F-Y all retain strong conditional degree-mixing coordinates under R2.

E29D shows that those strong conditional scores can arise from representations with substantially different feature orientation and concentration geometry.

The common degree-mixing channel is therefore not represented identically across the circuit families.

# Relationship to E29C

E29C found that R2 provides only limited incremental cycle prediction beyond joint-degree mixing and the spectrum.

E29D’s high C5 and C6 residual correlations are consistent with that result.

The circuits tend to fail on the same longer-cycle graphs, leaving little obvious circuit-to-circuit complementarity.

Triangle errors are much less aligned, but the failed stacking implementation prevents a direct test of whether those differences produce usable predictive gain.

---

# What the Experiment Establishes

The valid completed analyses establish that:

1. **E29D completed and saved its representation and prediction-level results.**

2. **F-X and F-Y have the strongest overall R2 geometry alignment.**

3. **F-X and D-X have the weakest linear feature alignment outside S2.**

4. **Coarse pairwise-distance ordering can remain similar even when linear CKA is low.**

5. **S2 is the most consistently aligned stratum across all principal circuit pairs.**

6. **Probability-concentration ordering can differ sharply despite similar global representation geometry.**

7. **Triangle residuals and graph-level errors differ substantially across circuits.**

8. **C4 errors show intermediate similarity.**

9. **C5 and C6 errors are strongly correlated across circuit families.**

10. **The reported exclusive-success counts are nondirectional median-ranking discordance counts.**

11. **The mixing residual correlations are based only on the rank-one S2 target.**

12. **The nested stacking result is invalid because the base predictions were not centered while the target was centered.**

13. **The stacked and standalone R² values also use inconsistent denominators.**

14. **E29D therefore does not establish either predictive complementarity or predictive redundancy.**

The experiment supports representation non-equivalence and target-dependent error alignment, but its decisive ensemble test must be rerun.

---

# Necessary Qualifications

The CKA and pairwise-distance analyses are descriptive.

No:

* repeated pair sample;
* confidence interval;
* permutation test;
* or graph-level bootstrap

is reported.

The distance correlations use 4,000 randomly sampled pairs per comparison.

Different circuit-pair and stratum cells consume different sequential draws from one random generator. Their point estimates are not computed on one universal pair sample.

Graph-pair observations are also dependent because the same graph can occur in many pairs.

Sector entropy and effective sector count are deterministically related:

$$K_{\text{sector}}=\exp(H_{\text{sector}}).$$

Reporting both correlations adds little independent evidence.

The entropy correlations may be unstable when the range of entropy values is narrow. This is particularly relevant to F-X and F-Y, whose average effective sector counts are close to two.

Prediction residual correlations are averaged equally across strata rather than weighted by target variance or graph difficulty.

For mixing, the signed residual correlation silently excludes the multivariate S1, S3, and S4 targets.

The squared-error correlation remains available across all strata but compresses direction and target-coordinate information into one nonnegative scalar per graph.

The median-error discordance threshold is circuit specific.

A graph can be called a “success” for a generally weak circuit and a “failure” for a stronger circuit because each is judged relative to its own median.

The E29D decoder is code-equivalent to the E29A R2 decoder, but no direct bitwise prediction gate is implemented.

The notebook suppresses `LinAlgWarning` while using high-dimensional ridge models and penalties down to:

$$10^{-14}.$$

E10 showed that QuIC-family probe results can depend on low-variance directions and weak regularization.

The stacking configuration named “all” includes H-H, but H-H is absent from the pairwise representation and prediction analyses.

No H-H-specific geometry or error comparison is available.

The experiment uses:

* exact ideal probabilities;
* one graph order;
* four sampled degree sequences;
* one fixed angle schedule;
* and one shallow layer.

Finally, R2 incorporates graph-supplied degree classes. E29D compares hybrid graph-conditioned circuit readouts rather than unlabeled probability vectors alone.

---

# Overall Assessment

E29D’s valid results show that the E29 circuit families expose related but nonidentical degree-sector geometries.

F-X and F-Y have the strongest feature and distance alignment, including nearly identical S2 geometry:

$$\text{CKA}=0.998.$$

F-X and D-X preserve some common pairwise-distance ordering while using substantially different linear coordinates in S1, S3, and S4.

At the prediction level, the clearest circuit differences occur for triangles.

Triangle residual correlations range from:

$$-0.150\text{ to }0.223,$$

and approximately half of the graphs fall on opposite sides of the two circuits’ median-error rankings.

For C5 and C6, residual and squared-error correlations are high, indicating much greater redundancy.

The notebook’s intended decisive result—the nested stack—is not usable.

It regresses a centered target on uncentered base predictions and then compares stacked and standalone R² values computed with different denominators. The near-zero cycle stacks are therefore artifacts of the implementation rather than evidence against complementarity.

The appropriate central claim is:

> Degree-sector representations from the E29 circuit bank exhibit architecture-dependent but partially shared graph geometry. F-X and F-Y are most closely aligned, while normalized-degree and Hadamard preparations reorganize the representation more strongly outside the bimodal stratum. Circuit prediction errors differ most for triangles and become increasingly aligned for 5- and 6-cycles, identifying C3 as the strongest candidate for useful cross-circuit complementarity. However, E29D’s nested stacking test is invalid because it fits centered targets to uncentered base predictions and compares R² scores with inconsistent denominators. E29D therefore establishes representation non-equivalence and target-dependent error discordance, but it does not determine whether circuit combinations outperform the best standalone representation.
