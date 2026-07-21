# QuIC AAAI-27 Main-Paper Writing Packet

## 0. Operating instruction for the writing model

You are writing only the seven-page AAAI-27 main paper. You are not writing the supplement, a journal version, or a comprehensive account of the QuIC research program.

This packet is intentionally information-limited. Treat the omission of an experiment, theorem, or interpretation as deliberate. Do not request, infer, or invent additional results. When a supporting detail belongs in the supplement, use the exact appendix placeholder defined in this packet and continue writing the main argument.

If a fact required for a proof or numerical statement is absent, insert a visible author query such as:

> `[AUTHOR CHECK: insert exact coefficient/proof step from verified formalism]`

Do not complete missing mathematics from analogy or general knowledge.

## 1. Acceptance objective

The optimization target is **acceptance to AAAI-27**.

The desired review outcome is three reviewers who all understand and accept the same narrow paper, even if none regards it as the definitive theory of quantum graph representations. Three weak accepts are preferable to one or two strong accepts offset by a reviewer who cannot identify the AI contribution, misunderstands the theorem, or believes the paper overclaims.

Use the following decision rule:

> Include a concept only if it is the central contribution or directly resolves a predictable reviewer objection. If a detail increases specialist sophistication but creates a new conceptual branch, omit it or refer to the supplement.

### Expected reviewer mix

Write simultaneously for:

1. a general machine-learning or representation-learning reviewer;
2. a graph-learning or graph-theory reviewer familiar with WL and spectral methods;
3. a quantum-computing reviewer familiar with shallow circuits and QAOA-style encodings.

No reviewer should need to adopt another reviewer’s vocabulary to understand the paper.

### Writing consequences

- State the AI problem before the quantum mechanism.
- Use one central theorem, not a collection of equally weighted formal objects.
- Define every quantum quantity needed by a non-quantum reviewer.
- State every graph-theoretic comparison narrowly and literally.
- Prefer one precise claim over several adjacent observations.
- Put the strongest classical control in the main paper.
- Treat limitations as scope, not as the paper’s final message.
- Never make the abstract a catalog of formal viewpoints or negative qualifications.

## 2. The paper being written

### Recommended title

> **Characterizing the Structural Inductive Bias of a Quantum Graph Feature Map**

### One-sentence thesis

> A shallow phase-encoded quantum circuit defines a training-free graph feature map whose weak-mixer Born readout has an identifiable combinatorial inductive bias: on regular graphs, short-cycle and rooted-incidence structure appears in a predictable hierarchy and includes a diamond-sensitive component beyond the adjacency spectrum, while downstream and finite-shot experiments distinguish information contained by the ideal representation from information practically accessible through a chosen readout.

### AI framing

The object is a fixed feature map used by an ordinary downstream learner:

\[
G\longmapsto \Phi_{\mathrm{QuIC}}(G)
\longmapsto f_w\!\left(\Phi_{\mathrm{QuIC}}(G)\right).
\]

The paper distinguishes:

\[
\text{information contained}
\not\equiv
\text{information linearly accessible}
\not\equiv
\text{information statistically accessible}.
\]

This is the central connection to AI. The contribution is not merely that the circuit distinguishes graphs. It characterizes the structural inductive bias of a graph representation and the accessibility of its content to downstream models.

### Exactly three contribution claims

1. **Exact representation mechanism.** The circuit transforms graph structure into a sorted measurement representation through a cut-phase encoding, a boundary-sector transform, and local interference between Hamming-neighboring cuts.
2. **Cubic motif theorem.** The second mixer derivative of output purity closes exactly on triangles, four-cycles, and diamonds, yielding explicit separation from ordinary 1-WL and from adjacency-spectrum equivalence.
3. **Exhaustive accessibility characterization.** Complete cubic censuses exhibit the predicted short-cycle hierarchy in representation geometry, linear probes, and probability rank, with folklore 2-WL and finite-shot sampling providing strong scope controls.

Do not add a fourth contribution.

## 3. Authority and evidence rules

For main-paper drafting:

- this packet controls the permitted claims, evidence, terminology, and narrative;
- author-verified theorem text controls exact mathematical details;
- the current manuscript controls already-fixed notation and LaTeX conventions;
- the QCE paper is prior work and must be cited when QuIC, hardware, or CFI is discussed;
- no experimental archive or additional formalism is available during this stage.

If this packet and a draft conflict, flag the conflict. Do not silently choose the more ambitious claim.

## 4. Main mathematical content

### 4.1 Circuit and feature-map definition

The ideal one-repetition circuit is

\[
|\psi_G\rangle=
R_X(\beta)^{\otimes n}
\left[\prod_{uv\in E}R_{ZZ}^{(u,v)}(\gamma)\right]
\left[\bigotimes_iR_X(\eta_i)\right]|0^n\rangle.
\]

For the regular-graph experiments,

\[
\eta=2.875,\qquad \gamma=2.0,\qquad \beta=0.1.
\]

Let \(p_G\) be the labeled Born probability vector. The graph feature map is

\[
\Phi_{\mathrm{QuIC}}(G)=p_G^\downarrow,
\]

the probabilities arranged in descending order.

### 4.2 Cut phase

For \(z_v=(-1)^{x_v}\) and cut size \(c_G(x)\),

\[
\prod_{uv\in E}e^{-i\gamma z_uz_v/2}
=e^{-i\gamma|E|/2}e^{i\gamma c_G(x)}.
\]

The graph-dependent phase is \(e^{i\gamma c_G(x)}\), while the complete pre-mixer amplitude is

\[
\phi_G(x)=a_\eta(x)e^{i\gamma c_G(x)},
\]

where \(a_\eta(x)\) is the product-state encoder amplitude.

Do not describe the complete circuit as merely “computing a cut function.” The cut phase is the encoded landscape; measurable graph information appears only after noncommuting mixing and Born measurement.

### 4.3 Mixer interference

The exact mixer expansion is

\[
\psi_G(x;\beta)
=\cos^n(\beta/2)
\sum_{S\subseteq V}
[-i\tan(\beta/2)]^{|S|}
\phi_G(x\oplus S).
\]

Interpretation: the mixer interferes cuts separated by Hamming flips. Mixer order therefore indexes the number of flipped roots and motivates the emergence of rooted incidence structure.

Do not promote the Boolean-hypercube interpretation as a second main theorem.

### 4.4 Boundary-sector transform

Define the unweighted boundary-sector polynomial

\[
Z_{G,T}(z)=\sum_{F\subseteq E:\,\partial F=T}z^{|F|}.
\]

The actual encoder-bearing Walsh coefficients form an encoder-weighted boundary-sector transform. The unweighted polynomial isolates the underlying cycle-space combinatorics. For simple cubic graphs,

\[
[z^3]Z_{G,\varnothing}=C_3,
\qquad
[z^4]Z_{G,\varnothing}=C_4,
\qquad
[z^5]Z_{G,\varnothing}=C_5,
\]

\[
[z^6]Z_{G,\varnothing}
=C_6+\binom{C_3}{2}-D_\diamond.
\]

Use these identities to explain why cycles and diamonds are natural carriers. Do not claim novelty for the general Ising or cut-polynomial connection.

For the complete derivation, write:

> `Appendix~\ref{app:boundary-transform} gives the weighted boundary-sector derivation and normalization conventions.`

### 4.5 Distributional interpretation of sorting

Define

\[
\nu_G=\frac{1}{2^n}\sum_x\delta_{2^np_G(x)}.
\]

For graphs of equal order,

\[
\min_{\sigma\in S_{2^n}}
\|p_G-\sigma p_H\|_1
=\|p_G^\downarrow-p_H^\downarrow\|_1
=W_1(\nu_G,\nu_H).
\]

This gives sorting a canonical distributional interpretation. It does not make sorting lossless or prove graph completeness.

For the short proof, write:

> `See Appendix~\ref{app:sorting} for the rearrangement/optimal-matching proof.`

### 4.6 Central theorem

Define

\[
M_2(G;\beta)=\sum_xp_G(x;\beta)^2,
\qquad
M_2''(G;0)=
\left.\frac{\partial^2}{\partial\beta^2}M_2(G;\beta)\right|_{\beta=0}.
\]

For simple cubic graphs under the verified theorem assumptions,

\[
\boxed{
M_2''(G;0)
=A_n+b_3C_3(G)+b_4C_4(G)+b_DD_\diamond(G)
}.
\]

At the canonical \(n=14\), \(\eta=2.875\), \(\gamma=2.0\) setting,

| Motif | Coefficient |
|---|---:|
| \(C_3\) | \(3.73045185\times10^{-5}\) |
| \(C_4\) | \(3.34368946\times10^{-8}\) |
| \(D_\diamond\) | \(3.99102708\times10^{-8}\) |

The main paper must include the theorem’s assumptions, explicit coefficient definitions, and the essential third-difference cancellation. Do not fabricate missing coefficient algebra. Insert an author check if the verified theorem extract has not been provided.

For complete carrier algebra, write:

> `The full carrier enumeration and coefficient calculation appear in Appendix~\ref{app:M2-proof}.`

### 4.7 Corollary: ordinary 1-WL separation

For same-order regular graphs, ordinary 1-WL with uniform initialization produces the same constant coloring. The purity argument additionally uses

\[
M_2(G;0)=M_2(H;0),
\qquad
M_2'(G;0)=M_2'(H;0).
\]

If the theorem’s motif combination differs and the relevant coefficient is nonzero, the sorted Born distributions differ for sufficiently small nonzero \(\beta\).

Use the triangular prism and \(K_{3,3}\) as the explicit witness. Claim explicit separation, not general superiority over the WL hierarchy.

### 4.8 Corollary: adjacency-cospectral diamond separation

For adjacency-cospectral cubic graphs, the spectrum fixes the lower spectral quantities entering the theorem. If

\[
D_\diamond(G)\ne D_\diamond(H),
\]

then

\[
M_2''(G;0)-M_2''(H;0)
=b_D[D_\diamond(G)-D_\diamond(H)]\ne0.
\]

The theorem gives local separation for sufficiently small nonzero mixer angle. Separation at the experimental value \(\beta=0.1\) is established separately by exact/high-precision computation.

For proof and witness details, write:

> `See Appendix~\ref{app:cospectral-proof} for the spectral identities and Appendix~\ref{app:E14} for the finite-angle witnesses.`

## 5. Main experimental evidence

Only the following experiments may appear as main-paper evidence.

### 5.1 E1: exhaustive representation geometry

Complete connected cubic censuses:

- \(509\) graphs at \(n=14\);
- \(4{,}060\) graphs at \(n=16\).

Global Mantel correlations between QuIC \(L_1\) geometry and motif differences:

| Quantity | \(n=14\) | \(n=16\) |
|---|---:|---:|
| \(C_3\) | 0.903 | 0.900 |
| \(C_4\) | 0.290 | 0.303 |
| \(C_5\) | 0.109 | 0.079 |
| random control | 0.005 | -0.007 |

After fixing triangle count, sufficiently populated strata have \(C_4\) correlations of 0.898–0.968 at \(n=14\) and 0.853–0.964 at \(n=16\). Within the largest \(n=16\) fixed-triangle strata, PC1 explains 53.6%–54.7% of variance and has \(|\rho(\mathrm{PC1},C_4)|=0.978\)–0.985. After fixing \((C_3,C_4)\), all 16 qualifying \(n=14\) strata and all 43 qualifying \(n=16\) strata exhibit positive \(C_5\) organization.

Permitted claim:

> Across the exhaustive connected cubic censuses at \(n=14\) and \(n=16\), QuIC geometry is organized hierarchically by short-cycle structure: triangles dominate globally, four-cycles define the leading direction after conditioning on triangles, and five-cycles organize the remaining geometry after conditioning on both.

Qualification: this establishes metric organization, not causal encoding or a unique invariant coordinate.

Supplement reference:

> `Complete stratum definitions, Mantel tests, and PCA results appear in Appendix~\ref{app:E1}.`

### 5.2 E2: linear accessibility

Nested ridge probes on exact full sorted vectors give:

| Target | \(n=14\) \(R^2\) | \(n=16\) \(R^2\) |
|---|---:|---:|
| \(C_3\) | \(1.000\pm0.000\) | \(1.000\pm0.000\) |
| \(C_4\) | \(0.998\pm0.002\) | \(1.000\pm0.000\) |
| \(C_5\) | \(0.928\pm0.092\) | \(0.982\pm0.015\) |
| \(C_6\) | \(0.485\pm0.326\) | \(0.642\pm0.122\) |

Permitted claim:

> Simple held-out linear probes recover the geometric hierarchy: triangles and four-cycles are essentially exact, five-cycles remain strongly accessible, and six-cycles form a weaker and less stable layer.

Qualification: these are high-dimensional exact-vector probes, not measurement-efficiency or computational-advantage results.

Supplement reference:

> `Full fold-level results, target definitions, and ridge diagnostics appear in Appendix~\ref{app:E2}.`

### 5.3 E7: rank localization

| Target | Practical head location | Representative result |
|---|---|---|
| \(C_3\) | first 25 | \(R^2=1.000\) at both orders |
| \(C_4\) | approximately first 100 | \(R^2=0.993/0.996\) |
| \(C_5\) | several hundred | \(R^2=0.927/0.981\) at \(k=400\) |
| \(C_6\) | approximately first 1,000 | \(R^2=0.484/0.640\) |

Permitted claim:

> Structural information is rank stratified within the tested sorted distributions.

Qualification: this does not make the complete representation polynomial-size or efficiently measurable.

Supplement reference:

> `Complete truncation curves and cutoff qualifications appear in Appendix~\ref{app:E7}.`

### 5.4 E14: exact cospectral witnesses

The complete connected cubic \(n=18\) census contains \(41{,}301\) graphs. Six exact adjacency-cospectral witness pairs exchange one diamond for one six-cycle.

- QuIC ranks the diamond count correctly in all six pairs.
- The first 100 sorted probabilities suffice.
- The selection-corrected sign-flip result is \(p=0.0462\).
- Separations were checked with exact/high-precision supporting audits.

Permitted claim:

> Six exact adjacency-cospectral cubic witness pairs realize the theorem’s diamond term at \(\beta=0.1\): each pair exchanges one diamond for one six-cycle, and QuIC ranks all six correctly using the first 100 probabilities.

Qualification: this is an explicit witness set, not universal cospectral separation and not “beyond classical” computation.

Supplement reference:

> `Graph identifiers, precision checks, and the selection protocol appear in Appendix~\ref{app:E14}.`

### 5.5 E3C: folklore 2-WL control

Folklore 2-WL on ordered vertex pairs:

- distinguishes all 509 \(n=14\) and all 4,060 \(n=16\) census graphs;
- separates every tested adjacency-cospectral pair;
- nearly saturates short-cycle prediction;
- substantially exceeds QuIC on \(C_6\) and diameter;
- remains weaker than QuIC on the tested girth probe.

Compact results:

| Target | 2-WL \(n=14/16\) | QuIC \(n=14/16\) |
|---|---:|---:|
| \(C_3\) | 0.998 / 1.000 | 1.000 / 1.000 |
| \(C_4\) | 0.993 / 0.999 | 0.998 / 1.000 |
| \(C_5\) | 0.917 / 0.993 | 0.928 / 0.982 |
| \(C_6\) | 0.879 / 0.983 | 0.485 / 0.642 |
| girth | 0.787 / 0.844 | 0.993 / 0.999 |

Required qualification: the synchronized 2-WL vocabulary is target-free but constructed over the complete census and is therefore transductive. It is also high-dimensional and sparse. Do not infer a computational-efficiency ordering from feature dimension.

Supplement reference:

> `The folklore 2-WL update, synchronized-vocabulary construction, dimensions, and complete target table appear in Appendix~\ref{app:E3C}.`

### 5.6 E15: finite-shot accessibility of global sorting

Independent multinomial training and test realizations show:

- triangle recovery reaches 90% of the exact-vector score at approximately \(3.1\times10^6\) shots per graph;
- at \(2^{24}\) shots, \(C_3\) reaches approximately 0.994, \(C_4\) approximately 0.67–0.68, girth approximately 0.89, diamonds approximately 0.59, and \(C_6\) approximately 0.14;
- \(C_5\) remains at the prediction floor;
- exact cospectral-mate distances remain comparable to repeat-sampling variation.

Permitted claim:

> The ideal hierarchy is also a hierarchy of measurement difficulty under global sorting: triangles require millions of shots for reliable recovery, while deeper motif and cospectral signals remain substantially harder.

Qualification: this is ideal multinomial sampling, not hardware execution or a universal shot barrier.

Supplement reference:

> `The complete shot ladder, estimators, replicate design, and uncertainty appear in Appendix~\ref{app:E15}.`

### 5.7 Supplement-only readout counterpoint

The main paper may use exactly one sentence:

> Degree-conditioned aggregation can expose irregular-graph structure that is poorly accessible through global sorting or Hamming pooling; see Appendix~\ref{app:E29-HX}.

Do not provide E29-HX numbers, architecture details, or additional interpretation in the main paper. Do not turn this sentence into a fourth contribution.

### 5.8 Prior CFI context

Use at most one sentence, citing the QCE paper:

> Although folklore 2-WL is stronger on the cubic-census prediction tasks studied here, prior QuIC experiments distinguish CFI pairs not separated by the corresponding WL test~\cite{QCE_QUIC}; we therefore do not infer a general expressive ordering.

CFI is prior evidence, not a new AAAI experiment.

## 6. Main-paper structure and page budget

### Section 1: Introduction and contributions — approximately 0.9 page

Must accomplish:

- establish the feature-map accessibility problem;
- distinguish discrimination, linear accessibility, and statistical accessibility;
- cite prior QuIC/QCE rather than reintroducing the circuit as new;
- state exactly three contributions.

### Section 2: Quantum graph feature map and sorted readout — approximately 0.85 page

Must contain:

- circuit and representation definitions;
- permutation-invariant readout;
- compact distributional interpretation of sorting;
- the graph-to-feature-to-learner pipeline.

### Section 3: From cut phases to incidence structure — approximately 1.1 pages

Must contain:

- cut identity;
- weighted boundary-transform interpretation;
- selected unweighted sector coefficients;
- mixer interference identity.

### Section 4: Cubic motif theorem and consequences — approximately 1.55 pages

Must contain:

- purity definition;
- central theorem and essential proof structure;
- ordinary 1-WL corollary;
- adjacency-cospectral diamond corollary;
- local-theorem versus finite-angle distinction.

### Section 5: Exhaustive representation characterization — approximately 1.55 pages

Must contain:

- E1 hierarchy;
- E2 linear accessibility;
- E7 rank localization;
- one consolidated figure and one compact table.

### Section 6: Controlled boundaries — approximately 0.75 page

Must contain:

- E14 witnesses;
- compact E3C comparison;
- compact E15 result;
- one E29-HX appendix sentence;
- one prior-CFI sentence.

### Section 7: Discussion and conclusion — approximately 0.3 page

Must reiterate:

- what structure is present;
- what is linearly accessible;
- what is costly under global sorting;
- regular/cubic scope;
- no universal completeness or WL ordering.

## 7. Planned assets

### Figure 1: feature-map mechanism

\[
G
\rightarrow
\text{cut phases}
\rightarrow
\text{local interference}
\rightarrow
\text{sorted Born representation}
\rightarrow
\text{linear readout}.
\]

Annotate contained, linearly accessible, and statistically accessible information.

### Figure 2: hierarchy and rank localization

Combine E1 conditional geometry with E7 truncation depth across \(n=14,16\).

### Table 1: controlled representation comparison

Combine the compact QuIC and folklore 2-WL results. Present E14 and E15 as small adjacent results or textual callouts if another table would exceed the page budget.

## 8. Prohibited claims and content

Do not include:

- universal completeness or injectivity of globally sorted probabilities;
- general dominance over 1-WL, 2-WL, or \(k\)-WL;
- formal incomparability with the WL hierarchy;
- quantum computational advantage;
- runtime, memory, storage, or sample-complexity advantage;
- practical sample efficiency for deep motifs;
- a general irregular-graph hierarchy;
- exact finite-\(\beta\) motif decoding inferred only from derivatives at zero;
- novelty of the general Ising/QAOA cut mapping;
- a statement that sorting merely removes vertex labels without additional information loss;
- QCE hardware or CFI results as new evidence;
- any additional experiment, theorem, circuit family, angle study, application, or residual analysis not included in this packet.

If tempted to add omitted content, insert an appendix placeholder only if one is defined below. Otherwise omit it.

## 9. Appendix-reference contract

Use these labels exactly so the supplement can be written later without changing the main manuscript.

| Label | Main-paper purpose |
|---|---|
| `app:boundary-transform` | weighted boundary-sector derivation and normalization |
| `app:sorting` | sorted-distance/quantile proof |
| `app:M2-proof` | full purity carrier enumeration and coefficient algebra |
| `app:cospectral-proof` | spectral identities used by the diamond corollary |
| `app:E1` | full hierarchy strata and PCA |
| `app:E2` | complete ridge protocol and fold results |
| `app:E7` | complete truncation curves |
| `app:E9` | optional perturbative mechanism check |
| `app:E14` | witness identifiers, precision, and significance |
| `app:E3C` | full folklore 2-WL construction and results |
| `app:E15` | complete finite-shot protocol and curves |
| `app:E24C` | protocol-matched Wiener ranking, if mentioned |
| `app:E29-HX` | readout capabilities beyond global sorting |
| `app:irregular` | irregular-graph scope synthesis |
| `app:numerics` | precision, relabeling, and finite-census diagnostics |

Do not write appendix content during the main-paper stage. The placeholders are promises of support, not invitations to expand the main paper.

## 10. Acceptance-oriented abstract

> Hybrid quantum-classical graph learning uses quantum circuits as feature maps, yet graph discrimination alone does not reveal which structural information their outputs expose to downstream models. We characterize the structural inductive bias of a shallow, training-free quantum graph feature map. We show that its commuting \(ZZ\) layer produces a complex cut-phase function whose Walsh coefficients admit a boundary-sector characterization, while local mixing exposes rooted incidence structure. For cubic graphs, we derive an exact expression for the second derivative of output purity as an affine function of triangle, four-cycle, and diamond counts. This yields formal separations from 1-WL on regular graphs and from the adjacency spectrum on explicit cospectral pairs. Complete censuses of connected cubic graphs on 14 and 16 vertices reveal a replicated hierarchy in both representation geometry and linear accessibility, with short-cycle information concentrated at progressively deeper probability ranks. Comparisons with folklore 2-WL and finite-shot sampling distinguish structural information contained by the ideal representation from information accessible to downstream models and finite measurements.

## 11. Final instruction

Build one narrow chain:

\[
\text{feature-map question}
\rightarrow
\text{exact mechanism}
\rightarrow
\text{cubic theorem}
\rightarrow
\text{exhaustive accessibility}
\rightarrow
\text{controlled boundaries}.
\]

The manuscript is successful when three different AAAI reviewers can independently state the same contribution after reading the abstract, Figure 1, the central theorem, and the main results table. Do not trade that shared understanding for additional technical breadth.
