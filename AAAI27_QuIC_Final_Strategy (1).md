# AAAI-27 QuIC Final Submission Strategy

## 1. Executive decision

This paper will be a **theoretical characterization of a frozen quantum graph feature map**, supported by exhaustive and carefully controlled experiments. It will not present QuIC as a new circuit, a complete graph invariant, a superior replacement for classical graph learning, or a demonstrated quantum advantage.

The acceptance-oriented paper is built around one central mathematical result:

\[
M_2''(0)=A_n+b_3C_3+b_4C_4+b_DD_{\diamond}
\]

for cubic graphs, together with its consequences for regular graphs and adjacency-cospectral graphs. The exact cut/boundary transform explains where the motif structure originates. Exhaustive cubic censuses then show that the full sorted representation exhibits the same structural hierarchy and makes it accessible to simple downstream models.

Everything in the manuscript must support one of three questions:

| Level | Question | Primary evidence |
|---|---|---|
| Structural content | What graph information is present in the ideal feature map? | Boundary transform, purity theorem, cospectral witnesses |
| Linear accessibility | What information can a simple downstream learner recover? | Representation geometry, ridge probes, rank truncation, 2-WL controls |
| Statistical accessibility | What information survives finite measurement, and how does readout choice affect recovery? | E15 global-sorting curves; E29F-HX degree-sector comparison in the supplement |

This distinction is the paper's bridge to AI. QuIC is the mathematical specimen; the AI contribution is a characterization of the **structural inductive bias and downstream accessibility of a graph representation**.

## 2. Paper thesis

### One-sentence thesis

> A shallow phase-encoded quantum circuit defines a training-free graph feature map whose weak-mixer Born readout has an identifiable combinatorial inductive bias: on regular graphs, short-cycle and rooted-incidence structure appears in a predictable hierarchy and includes a diamond-sensitive component beyond the adjacency spectrum. Its finer globally sorted motif content is increasingly costly to recover from finite measurements, while structure-aware aggregation can make other low-dimensional graph signals substantially more accessible.

### Short thesis for the introduction

Hybrid quantum-classical graph learning can treat a quantum circuit as a fixed feature extractor, but graph discrimination alone does not reveal which information the representation exposes to a downstream learner. We characterize that information for QuIC. The graph first becomes a complex landscape over Boolean cuts; the local mixer interferes nearby cuts; and the sorted Born probabilities form a permutation-invariant graph representation. For cubic graphs, an exact weak-mixer purity expansion identifies triangles, four-cycles, and diamonds as low-order carriers. Complete graph censuses show that these same quantities organize the representation geometry and its linear decodability, while higher-order WL and finite-shot controls delimit the result.

### What the paper is fundamentally claiming

1. **Mechanism:** The circuit is not adequately characterized as merely “computing a cut function.” The commuting \(ZZ\) layer encodes the cut-phase landscape, while the noncommuting mixer converts local differences of that landscape into measurable probability variation.
2. **Exact combinatorial theorem:** For cubic graphs, the second derivative of output purity closes exactly on \(C_3\), \(C_4\), and \(D_\diamond\).
3. **Formal consequences:** The theorem yields explicit separation from 1-WL on regular graphs and from the adjacency spectrum on cospectral cubic pairs with different diamond counts.
4. **Representation-learning consequence:** The full sorted feature vector organizes graph space hierarchically by the same short-cycle structure and makes it linearly accessible.
5. **Scope:** Higher-order WL remains a strong or stronger classical representation in the tested cubic regime. Fine motif information in the global sorted readout is expensive to recover, but supplementary irregular-graph results show that finite-shot accessibility depends strongly on readout design.

## 3. Primary contribution hierarchy

The paper should advertise exactly three contributions.

### Contribution 1: Exact representation mechanism

We derive an exact mathematical account of how the circuit transforms graph structure into a sorted measurement representation:

- \(R_{ZZ}\) gates encode the graph's complex cut-phase function;
- Walsh coefficients are boundary-sector/cycle-space weight enumerators;
- the \(R_X\) mixer interferes cuts related by Hamming flips;
- the sorted probability vector is a canonical distributional readout rather than an arbitrary implementation trick.

This contribution prevents the paper from being dismissed as a routine statement that commuting \(ZZ\) gates encode a cut objective.

### Contribution 2: Cubic motif theorem and spectral separation

We prove the exact second-purity derivative formula and derive:

- a separation corollary for regular graphs collapsed by 1-WL;
- a separation corollary for adjacency-cospectral cubic graphs with unequal diamond count;
- explicit connection to the six \(n=18\) diamond/\(C_6\) exchange witnesses.

This is the paper's sharpest mathematical novelty and its technical climax.

### Contribution 3: Exhaustive characterization of accessibility

Across all connected cubic graphs at \(n=14\) and \(n=16\), we show that:

- global geometry is dominated by triangles;
- four-cycles organize variation conditional on triangles;
- five-cycles organize residual variation after fixing triangles and four-cycles;
- simple linear probes recover the same hierarchy;
- structural information occurs at progressively deeper ranks in the sorted vector;
- stronger classical and finite-shot controls distinguish information content from practical accessibility and show that accessibility depends on the invariant readout applied to circuit measurements.

This contribution makes the theory relevant to representation learning rather than leaving it as a circuit identity.

## 4. Required AI positioning

AI relevance must be explicit in the title, abstract, first paragraph, experimental questions, and conclusion. It must not be confined to related work or a speculative applications paragraph.

### Required conceptual framing

The circuit is a **fixed graph feature map** used by a downstream learner:

\[
G \longmapsto \Phi_{\mathrm{QuIC}}(G)
\longmapsto f_w\!\left(\Phi_{\mathrm{QuIC}}(G)\right).
\]

The manuscript evaluates the feature map at three increasingly practical levels:

\[
\text{information contained}
\not\equiv
\text{information linearly accessible}
\not\equiv
\text{information statistically accessible}.
\]

This distinction is central. Injectivity or pairwise graph separation does not ensure that a transferable learner can extract a useful target, and ideal decodability does not ensure that the target survives finite sampling.

### Required terminology

Prefer:

- quantum graph feature map;
- frozen or training-free representation;
- structural inductive bias;
- representation geometry;
- linear accessibility or linear decodability;
- statistical or finite-shot accessibility;
- permutation-invariant sorted probability representation;
- boundary-sector polynomial;
- weak-mixer response;
- controlled comparison with folklore 2-WL.

Avoid making “quantum graph invariant” the only description. It emphasizes discrimination but undercommunicates the representation-learning contribution.

### CFI positioning

CFI is prior context, not a new AAAI contribution. The paper should contain one concise statement:

> Although folklore 2-WL is stronger on the cubic-census prediction tasks studied here, prior QuIC experiments distinguish CFI pairs not separated by the corresponding WL test [QCE citation]. We therefore do not infer a general expressive ordering from the present comparison.

Do not introduce new CFI formalism, rerun the CFI study, claim formal incomparability, or include CFI in the contribution list or abstract.

## 5. Main-paper mathematical content

### 5.1 Definitions that must appear

The main paper must define:

1. The QuIC circuit and the fixed canonical angles used experimentally.
2. The labeled probability vector \(p_G\) and sorted feature map \(\Phi(G)=p_G^\downarrow\).
3. Cut size \(c_G(x)\), spin variables \(z_v=(-1)^{x_v}\), and output purity \(M_2(G)=\sum_xp_G(x)^2\).
4. Boundary \(\partial F\) and the boundary-sector polynomial
   \[
   Z_{G,T}(z)=\sum_{F\subseteq E:\,\partial F=T}z^{|F|}.
   \]
5. The precise graph domain of each theorem, especially cubic regular graphs.

These definitions allow a non-quantum graph-learning reviewer to understand every central result without reconstructing circuit conventions from the supplement.

### 5.2 Lemma: cut phase and hypercube interference

Include the cut identity

\[
\prod_{uv\in E}e^{-i\gamma z_uz_v/2}
=e^{-i\gamma|E|/2}e^{i\gamma c_G(x)}
\]

and the mixer identity

\[
\psi_G(x;\beta)
=\cos^n(\beta/2)
\sum_{S\subseteq V}
[-i\tan(\beta/2)]^{|S|}
\phi_G(x\oplus S).
\]

Role in the paper: these equations explain why the graph becomes a phase landscape over Boolean cuts and why mixer order corresponds to the number of flipped roots. They support the motif theorem without creating a separate all-orders theory branch.

Do not promote the hypercube interpretation as an independent headline theorem. The fact that the product \(X\)-mixer is a walk on the Boolean hypercube is explanatory structure, not the principal novelty.

### 5.3 Proposition: boundary-sector transform

State the exact Walsh/boundary relation under the paper's normalization and show the relevant low-order closed-sector coefficients:

\[
[z^3]Z_{G,\varnothing}=C_3,\qquad
[z^4]Z_{G,\varnothing}=C_4,\qquad
[z^5]Z_{G,\varnothing}=C_5,
\]

\[
[z^6]Z_{G,\varnothing}
=C_6+\binom{C_3}{2}-D_\diamond.
\]

Role in the paper: this is the bridge from circuit algebra to classical combinatorial quantities and establishes why short cycles and diamonds are natural carriers rather than post-hoc regression targets.

Only a proof sketch and the essential expansion belong in the main paper. Full normalization algebra and coefficient checks belong in the supplement.

### 5.4 Proposition: distributional meaning of sorting

Define the empirical Born-value measure

\[
\nu_G=\frac{1}{2^n}\sum_x\delta_{2^np_G(x)}.
\]

State that \(p_G^\downarrow\) is its empirical quantile representation and, for equal graph order,

\[
\min_{\sigma\in S_{2^n}}
\|p_G-\sigma p_H\|_1
=\|p_G^\downarrow-p_H^\downarrow\|_1
=W_1(\nu_G,\nu_H).
\]

Role in the paper: this defuses the objection that sorting is ad hoc and explains why the experiments study a distribution of probability masses rather than labeled outcomes.

This result receives one proposition and one interpretive paragraph. Do not expand it into general \(W_q\), moment reconstruction, quotient-group theory, or replica partition functions in the main paper.

### 5.5 Central theorem: cubic second-purity motif closure

State the theorem with:

- all angle and graph assumptions;
- the exact formula
  \[
  M_2''(0)=A_n+b_3C_3+b_4C_4+b_DD_\diamond;
  \]
- explicit coefficient definitions, or sufficiently explicit closed forms to make the theorem independently checkable;
- the third-difference cancellation responsible for eliminating other cubic incidence configurations;
- a concise proof in the main paper.

The proof cannot be deferred entirely to supplementary material. AAAI reviewers are not obligated to read it, and this theorem carries the paper.

### 5.6 Corollaries that must immediately follow

#### Corollary A: separation from 1-WL

For same-order regular graphs, ordinary 1-WL gives the same constant coloring. When the theorem's motif combination differs and its angle coefficient is nonzero, the QuIC purity—and therefore the sorted Born multiset—differs for sufficiently small nonzero mixer angle.

Present an explicit witness such as the triangular prism and \(K_{3,3}\). Scope the claim to explicit separation, not general superiority over the WL hierarchy.

#### Corollary B: adjacency-cospectral diamond separation

For adjacency-cospectral cubic graphs, the spectrum fixes the lower spectral quantities appearing in the theorem. If \(D_\diamond(G)\ne D_\diamond(H)\) and \(b_D\ne0\), then

\[
M_2''(G;0)-M_2''(H;0)
=b_D\bigl(D_\diamond(G)-D_\diamond(H)\bigr)\ne0.
\]

Consequently the sorted Born distributions differ for sufficiently small nonzero \(\beta\).

This is the technical climax. It must be stated as a theorem consequence before the empirical witnesses are introduced.

### 5.7 Mathematical material excluded from the main paper

The following must not be promoted in the main text:

- replica complex-Ising partition characterization of all \(M_q\);
- all-orders rooted-incidence locality;
- first-\(2^n\)-moments reconstruction of the sorted vector;
- a general \(S_n\) versus \(S_{2^n}\) quotient theory;
- interval-certified head ordering through \(n\le32\);
- triple-defect formulas as theorems for \(C_5\) or \(C_6\);
- universal or generic injectivity of the sorted representation;
- repeated-circuit space-time boundary polynomials.

These results either add proof surface without strengthening the central acceptance claim or remain insufficiently closed. Some may appear in the supplement as optional derivations, but none should enter the abstract, contribution list, or central narrative.

## 6. Main-paper experimental content

The experiments are not an omnibus benchmark. Each block must answer a question created by the theory.

### Experimental Question 1: Does the ideal representation exhibit the predicted motif hierarchy?

#### Main evidence: E1

Include:

- complete connected cubic censuses: \(509\) graphs at \(n=14\) and \(4{,}060\) at \(n=16\);
- global triangle-dominated geometry;
- within-\(C_3\) four-cycle organization;
- within-\((C_3,C_4)\) five-cycle organization;
- replication across both graph orders;
- effective rank near three as supporting evidence of low-dimensional organization.

The main paper should show one consolidated figure or table, not every stratum. Full stratum results belong in the supplement.

Why required: E1 is the population-level validation that the motif hierarchy organizes the complete feature space rather than a selected set of examples.

### Experimental Question 2: Is the hierarchy accessible to a downstream learner and localized in the sorted distribution?

#### Main evidence: E2 and E7

Include:

- full-vector ridge results for \(C_3,C_4,C_5\), with \(C_6\) reported cautiously;
- a compact truncation result showing approximate depth progression:
  - \(C_3\): extreme head;
  - \(C_4\): roughly first \(10^2\) probabilities;
  - \(C_5\): several hundred;
  - \(C_6\): approximately \(10^3\) and less stable;
- the fact that the useful absolute head grows much more slowly than the ambient \(2^n\) vector over the two tested orders.

Do not call the representation polynomial-size or use the truncation result as a runtime advantage. The statement is rank localization of information, not efficient state preparation or readout.

Why required: the AI claim concerns what a downstream model can access, not merely what an exact invariant contains.

### Experimental Question 3: Does the theorem identify information beyond the adjacency spectrum?

#### Main evidence: E14

Include:

- the six \(n=18\) exact cospectral diamond/\(C_6\) exchange pairs;
- exact or high-precision QuIC separation;
- direct linkage to Corollary B;
- selection-corrected significance only if space permits and the protocol is stated accurately.

Present these as theorem-backed witnesses, not as a large statistical benchmark or evidence of universal cospectral separation.

Why required: this is the empirical realization of the sharpest formal novelty and prevents the cycle hierarchy from being dismissed as spectral re-expression.

### Experimental Question 4: How does the feature map compare with a strong classical structural representation?

#### Main evidence: E3C, compact form

Include one compact comparison showing:

- ordinary 1-WL collapses on the fixed-order cubic censuses;
- folklore 2-WL distinguishes all tested census graphs and cospectral pairs;
- cumulative 2-WL nearly saturates short-cycle prediction and is stronger on \(C_6\) and diameter;
- QuIC is competitive on shorter cycles and stronger on the tested girth probe;
- final 2-WL discrimination and transferable linear accessibility are not identical.

Do not describe 2-WL as a defeated baseline. Do not infer a universal expressive ordering.

Why required: a weak constant-feature GNN comparison would make the paper appear to avoid the appropriate classical control. The strong 2-WL result increases credibility.

#### E24C placement

The full protocol-matched Wiener-ranking comparison belongs in the supplement. The main paper may mention in one sentence that the matched functional comparison also favors 2-WL on Wiener ranking. Wiener prediction is not part of the central short-cycle theorem, so a full main-text treatment would divert the narrative.

### Experimental Question 5: Is the ideal information statistically accessible?

#### Main evidence: E15

Include one compact curve, panel, or table showing that:

- triangle recovery becomes reliable only at millions of shots;
- four-cycle, diamond, and deeper-cycle signals are substantially harder;
- exact-statevector cospectral distances can be comparable to finite-sampling variation.

Frame this as a statistical-accessibility characterization, not as a failed hardware demonstration.

Why required: without this control, a reviewer may reasonably interpret ideal linear decodability as an implicit practical claim. The result precisely scopes the contribution.

#### Required supplementary counterpoint: E29F-HX

E29F-HX does not replace E15 because it uses irregular graphs, an H-X circuit, an analytical joint-degree mixing target, and alternative pooled readouts. It changes the interpretation of E15 from a universal shot barrier to a readout-specific result.

The supplement must report that, across four fixed-degree-sequence strata containing 400 graphs each:

- degree-sector mass aggregation (R2) has exact linear-probe ceilings of approximately \(0.999\)–\(1.000\) for the analytical joint-degree mixing coordinates;
- at \(2^{16}\) shots, R2 reaches \(R^2\approx0.845\)–\(0.963\) across the four strata;
- R2 reaches 90% of its exact ceiling at approximately \(2^{14.6}\)–\(2^{17.1}\) shots;
- R2 exceeds global sorting (R0) and Hamming-weight pooling (R1) in every paired stratum/budget comparison, with bootstrap intervals excluding zero;
- R1's failure despite occasionally high exact ceilings shows that the gain is not explained by generic aggregation or lower dimension alone.

The main paper may contain one discussion sentence:

> The finite-shot limitation is not uniform across readouts: supplementary experiments on four irregular graph strata show that degree-sector aggregation recovers analytical joint-degree mixing at 90% of its exact ceiling using approximately \(2^{14.6}\)–\(2^{17.1}\) shots, while global sorting and Hamming pooling remain substantially weaker.

Do not present this as general sample efficiency, cycle recovery, or validation of the cubic motif theorem. The target and readout are intentionally aligned, making this a readout-mechanism result.

### Optional main-text mechanism check: E9

If space permits, include a small inset or sentence confirming:

- collapse at \(\beta=0\);
- agreement with the analytic first derivative;
- emergence of graph-dependent triangle structure at second order.

If space is tight, move the full E9 results to the supplement. The main theorem and exact algebra already establish the mechanism; E9 is confirmatory rather than load-bearing.

## 7. Main-paper material that must not appear

The main paper must not contain:

1. **A claim that QuIC is newly introduced here.** Cite the QCE paper and state that this work newly characterizes its representation.
2. **Hardware or CFI results presented as new AAAI evidence.** They belong to the prior QCE contribution.
3. **A universal injectivity or completeness claim** for globally sorted probabilities.
4. **A general “beyond \(k\)-WL” or “incomparable to WL” claim.** Only explicit prior CFI evidence and current family-specific comparisons are supportable.
5. **“Beyond classical” language.** Diamond separation is beyond the adjacency spectrum, not beyond classical computation or classical graph invariants.
6. **A quantum-advantage claim**, including implicit runtime, memory, or sample-complexity advantage.
7. **A claim that the complete feature vector is compact or polynomial-size.** Rank localization is not ambient-size reduction.
8. **A claim that sorting is only a harmless removal of vertex labels.** Global sorting quotients over all outcome permutations and can both expose and destroy structure.
9. **A claim that finite-\(\beta\) probabilities exactly decode motifs** merely because their Taylor coefficients do.
10. **A claim that the regular-graph hierarchy transfers generally to irregular graphs.** The existing irregular results show strong degree and joint-degree effects.
11. **A large GNN benchmark table.** The paper is a theoretical feature-map characterization, not an application benchmark.
12. **Protocol-sensitive residual claims** from the broader E29 family or invalid/superseded experimental runs. E29F-HX is an exception only for its validated finite-shot readout comparison.
13. **An abstract that lists every formal viewpoint and every limitation.** The abstract should communicate one mechanism, one theorem, and one validation arc.

## 8. Supplementary material

The supplement must make the paper independently auditable without becoming a second paper.

### 8.1 Required mathematical supplement

Include:

- complete derivation of the degree-weighted Walsh/boundary transform;
- normalization and sign conventions;
- full proof of the cubic \(M_2''(0)\) formula;
- the algebraic third-difference lemma and carrier table;
- explicit coefficient formulas and numerical values at canonical angles;
- proof details for both separation corollaries;
- full derivation of the two-defect adjacency/codegree census if referenced;
- reproducible symbolic and numerical assertions from the formalism notebook.

The main paper must still contain enough proof to validate the theorem. The supplement supplies completeness, not the only evidence.

### 8.2 Required experimental supplement

Include:

- graph-generation and census-verification procedures;
- canonical angle configuration and exact circuit conventions;
- complete E1 stratum tables, Mantel statistics, PCA results, and replication details;
- full E2 fold-level ridge results and target definitions;
- complete E7 truncation curves;
- E9 perturbative validation;
- exact E14 graph identifiers, structural invariants, precision audit, and significance calculation;
- complete E3C folklore 2-WL definition, vocabulary construction, dimensions, and all target results;
- complete E24C protocol-matched functional comparison;
- full E15 shot curves, estimators, repetitions, and uncertainty;
- a required E29F-HX readout section containing exact ceilings, raw recovery curves, matched-shot absolute \(R^2\), paired R2-R0 and R2-R1 intervals, sector dimensions, target ranks, ridge diagnostics, and the H-X architecture-transfer qualification;
- one concise irregular-graph scope section synthesizing E21/E25/E26 with E29F-HX: degree and joint-degree structure dominate the irregular regime, while degree-conditioned readout can make that dominant channel statistically accessible;
- collision and relabeling sanity checks from E16/E17/E20 only as empirical diagnostics, never as proof of completeness.

### 8.3 Claim-to-run index

Create a one-page table with:

| Manuscript claim/figure | Canonical experiment | Script/notebook cell | Output artifact | Status |
|---|---|---|---|---|

Only validated canonical runs should appear. The full E1–E30 research record may remain available as a scientific log, but it is not the reader-facing navigation document.

### 8.4 Optional supplementary theory

Only include these if already polished and they do not delay the paper:

- general \(W_q\) sorted-distance identity;
- Born Fourier autocorrelation identity;
- first-derivative formula for arbitrary degree;
- regular-graph common-mode result for \(M_2'(0)\);
- defect-layer ordering at the specifically tested \(n=14,16\) settings;
- computationally verified triple-defect formulas explicitly labeled as conjectural or finite checks.

Do not allow optional material to blur the status of proved versus computationally observed results.

## 9. Deferred to later papers

The following are coherent future projects and should be protected from being consumed as side remarks here.

### 9.1 General theory of the sorted Born representation

- replica partition functions for all probability moments;
- full quotient/optimal-transport geometry;
- analytic collision dichotomy;
- classification or counterexamples for sorted injectivity;
- multi-angle completeness questions;
- repeated-layer space-time boundary polynomials.

Potential paper: a mathematical-physics or quantum-information treatment of Born spectra as graph invariants.

### 9.2 Higher-order motif calculus

- rigorous all-orders rooted-incidence locality;
- completed third-order carrier calculation;
- exact triple-defect recovery of \(C_5\) and \(C_6\);
- arbitrary-degree, degree-colored motif expansions;
- formal relationship, if any, to levels of the WL hierarchy.

Potential paper: a general perturbative motif calculus for phase-encoded graph circuits.

### 9.3 Irregular-graph and readout design

- analytical joint-degree mixing basis;
- sector-mass and sector-sorted representations;
- readout quotient design;
- angle and mixer choices that suppress degree dominance;
- theory explaining why degree-sector masses isolate joint-degree mixing;
- transfer of the finite-shot advantage to additional circuits, graph orders, and non-mixing targets.

Potential paper: structured readout and circuit design for irregular quantum graph representations.

### 9.4 Applied hybrid learning

- quantum kernels built from the representation;
- molecular or attributed-graph feature extraction;
- comparisons under matched feature dimension and sample budget;
- end-to-end hybrid learning tasks;
- hardware-aware feature selection.

Potential paper: QuIC-Mol or a general hybrid quantum-classical graph-learning application.

## 10. Detailed seven-page paper outline

The target is seven technical pages, with proofs and key controls visible in the main paper.

### Section 1 — Introduction and contribution statement (approximately 0.9 page)

#### Purpose

Establish the AI problem before introducing quantum mechanics.

#### Required content

1. Fixed quantum circuits are used as feature maps in hybrid learning, but discrimination alone does not characterize their inductive bias.
2. Graph representation theory evaluates both distinguishing power and accessibility of structural information, commonly using WL and spectral comparisons.
3. QuIC provides a controlled specimen: shallow, training-free, permutation-invariant, and already introduced/evaluated in prior QCE work.
4. State the present question: what combinatorial information does its sorted Born representation encode, and what is accessible to downstream models?
5. Give exactly three contribution bullets matching Section 3 of this strategy.

#### Why required

This section determines whether the paper is read as theoretical AI or as a quantum circuit paper with an attached ML motivation.

#### Must not include

- extensive NISQ promises;
- claims of practical quantum advantage;
- CFI as a new contribution;
- a long catalog of experiments;
- universal injectivity language.

### Section 2 — Quantum graph feature map and readout (approximately 0.85 page)

#### Purpose

Define the object in AI-readable terms and give sorting a principled interpretation.

#### Required content

1. Circuit definition and angle conventions.
2. Definition of \(p_G\) and \(\Phi(G)=p_G^\downarrow\).
3. Relabeling invariance statement.
4. Born-value measure and one-dimensional sorted-distance proposition.
5. A small pipeline schematic:
   \[
   G\rightarrow\text{phase-encoded circuit}\rightarrow\Phi(G)\rightarrow\text{downstream learner}.
   \]

#### Why required

Reviewers must understand that the paper studies a graph representation consumed by ordinary learning algorithms, not merely a quantum state.

#### Must not include

- full quotient-group theory;
- moment reconstruction;
- a claim that global sorting is lossless;
- storage-efficiency claims.

### Section 3 — From cut phases to incidence structure (approximately 1.1 pages)

#### Purpose

Explain the mechanism that connects the graph to the motif theorem.

#### Required content

1. Exact cut-phase identity.
2. Boundary-sector transform and selected low-order coefficients.
3. Exact mixer/hypercube identity.
4. Short explanation: order in mixer angle corresponds to flipped-root incidence complexity.

#### Why required

Without this section, the purity theorem appears as an isolated calculation and the experiments appear post-hoc. With it, the theorem and hierarchy follow from a common mechanism.

#### Must not include

- replica partition functions;
- all-orders theorem;
- repeated-layer formalism;
- broad novelty claims for the Ising mapping itself.

### Section 4 — Cubic motif theorem and consequences (approximately 1.55 pages)

#### Purpose

Deliver the paper's main technical contribution.

#### Required content

1. Definition of purity and derivative convention.
2. Central theorem with exact assumptions and coefficients.
3. Proof structure, including the cancellation lemma.
4. 1-WL separation corollary with explicit witness.
5. adjacency-cospectral diamond corollary.
6. A short note distinguishing infinitesimal theorem from finite-\(\beta\) experimental behavior.

#### Why required

This section supplies the formal novelty that distinguishes the paper from both the QCE introduction of QuIC and known cut/Ising formulations.

#### Must not include

- unproved third-order motif claims;
- extrapolation to arbitrary degree sequences;
- “beyond classical” language;
- universal cospectral separation.

### Section 5 — Exhaustive representation characterization (approximately 1.55 pages)

#### Purpose

Show that the theorem's structural quantities organize the full feature map and are accessible to a learner across complete graph populations.

#### Required content

1. Census sizes, circuit configuration, and evaluation protocol.
2. Consolidated E1 hierarchy result across \(n=14,16\).
3. E2 linear-probe table for \(C_3,C_4,C_5\), with cautious \(C_6\).
4. Compact E7 rank-localization curve or table.
5. One sentence or inset from E9 if space permits.

#### Why required

The theorem concerns one low-order scalar observable. This section demonstrates that the complete sorted vector exhibits a broader, replicated representation geometry relevant to downstream learning.

#### Must not include

- every stratum;
- large GNN tables;
- unstable nonlinear probes;
- claims that correlation alone proves encoding;
- dimension-efficiency claims.

### Section 6 — Controlled boundaries: spectrum, 2-WL, and shots (approximately 0.75 page)

#### Purpose

Answer the three most predictable reviewer objections in a single compact section.

#### Required content

1. E14 theorem-backed cospectral witnesses.
2. One compact E3C 2-WL comparison.
3. One compact E15 finite-shot result.
4. One sentence pointing to the supplementary E29F-HX result as evidence that statistical accessibility is readout-dependent.
5. The single prior-QCE CFI sentence.

#### Why required

This section establishes that the contribution is neither merely spectral nor presented against weak classical baselines, while preventing ideal-statevector results from being mistaken for immediate practical efficiency.

#### Must not include

- a formal incomparability claim;
- the full E24C Wiener analysis;
- hardware results from QCE;
- multiple pages of negative experiments.

### Section 7 — Discussion, limitations, and conclusion (approximately 0.3 page)

#### Purpose

State exactly what has been learned about the feature map and close without reopening the research program.

#### Required content

1. Reiterate structural content versus linear and statistical accessibility.
2. State regular/cubic scope.
3. State that sorted completeness and general WL ordering remain open.
4. Identify higher-order motif calculus and irregular readout design as future work in one sentence.

#### Why required

The paper's honesty is a strength only if the scope is explicit and concise. A long limitations section would overwhelm the positive contribution.

## 11. Planned visual and table inventory

The main paper should contain no more than three principal visual objects.

### Figure 1: Feature-map mechanism

A compact pipeline showing:

\[
G
\rightarrow
\text{cut phases}
\rightarrow
\text{hypercube mixing}
\rightarrow
\text{sorted Born distribution}
\rightarrow
\text{linear readout}.
\]

Annotate the three accessibility levels: contained, linearly accessible, statistically accessible.

Purpose: communicates both the mechanism and AI relevance before the theorem.

### Figure 2: Exhaustive hierarchy and rank localization

Combine the most legible E1 hierarchy result with E7 truncation behavior across \(n=14,16\).

Purpose: visually connects motif order with representation geometry and probability rank.

### Table 1 or Figure 3: Controlled comparison

Compactly report:

- QuIC linear accessibility;
- folklore 2-WL comparison;
- exact cospectral witness result;
- finite-shot transition or limitation.

If this becomes too dense, keep the linear-probe/2-WL table and present finite shots as a small inset in Figure 2 or a concise textual result.

## 12. Claim discipline

### Claims that may be made directly

- The circuit's \(ZZ\) layer encodes the graph cut phase exactly.
- The stated boundary transform and low-order sector coefficients are exact.
- The mixer identity is exact.
- The sorted vector is permutation invariant and has the stated distributional/optimal-matching interpretation.
- The cubic \(M_2''(0)\) closure is exact under its stated assumptions.
- The theorem yields explicit 1-WL and adjacency-cospectral separation witnesses.
- The complete \(n=14,16\) cubic censuses exhibit the reported hierarchy.
- The reported linear probes quantify accessibility under their stated protocol.
- Folklore 2-WL is stronger on specified targets and separates all tested census graphs.
- Finite-shot recovery becomes substantially harder for deeper motifs.

### Claims that require qualifying language

- “QuIC separates graphs beyond \(k\)-WL” must refer to prior tested CFI instances and cite QCE.
- “The representation contains \(C_5\) or \(C_6\)” should be empirical unless tied to a proved coefficient.
- “Useful head” means empirically sufficient sorted ranks at tested orders, not polynomial end-to-end complexity.
- “Beyond spectrum” means beyond adjacency-spectrum equivalence on explicit witnesses.
- “Shallow” refers to circuit depth, not measurement or classical postprocessing cost.
- “Training-free” describes feature construction, not absence of a trained downstream probe.

### Claims prohibited in this submission

- universal completeness or injectivity of sorted probabilities;
- general dominance over 1-WL, 2-WL, or \(k\)-WL;
- formal incomparability with the WL hierarchy;
- quantum computational advantage;
- practical sample efficiency for deep motifs;
- general irregular-graph motif hierarchy;
- exact finite-\(\beta\) motif decoding from infinitesimal derivatives;
- novelty of the general Ising or QAOA cut mapping.

## 13. Reproducibility and supplement strategy

The reader-facing reproducibility package should consist of:

1. a cleaned formalism notebook containing only canonical derivations and assertions;
2. scripts or notebooks for the main experiments;
3. immutable graph identifiers or generation instructions for each census and witness set;
4. a claim-to-run index;
5. environment/package versions and deterministic seeds;
6. a short README that reproduces main figures and tables in manuscript order.

The full exploratory E1–E30 record can remain as the scientific log. It should not be the only navigation layer and need not be reproduced verbatim in the paper supplement.

## 14. Final-week execution order

No new broad experiment or theory project should begin. Work in this order:

1. **Freeze claims and notation.** Fix the circuit convention, angle notation, graph domain, and exact status of every statement.
2. **Write Section 4 first.** Complete the central theorem, proof, and two corollaries before prose polishing elsewhere.
3. **Write Sections 2–3.** Add only the formal machinery required to make Section 4 inevitable and understandable.
4. **Build the consolidated empirical artifacts.** Produce the E1/E2/E7 figure and compact E14/2-WL/shot comparison from canonical runs.
5. **Write Section 1 around the feature-map accessibility problem.** Do not begin from NISQ motivation.
6. **Write the scope section and CFI sentence.** Verify that no global WL or injectivity claim remains.
7. **Build the claim-to-run index and clean supplement.** Separate proved, certified, and empirical statements visibly.
8. **Perform an adversarial claim audit.** Search for “injective,” “complete,” “advantage,” “beyond WL,” “efficient,” “compact,” “incomparable,” and “general.” Check every occurrence.
9. **Perform a self-overlap audit against QCE.** Ensure that QuIC introduction, CFI, and hardware are cited as prior work rather than presented as new.
10. **Final page-budget pass.** Cut optional formalism before compressing the central theorem or controls.

## 15. Go/no-go criteria for each optional item

An optional item enters the main paper only if all four conditions hold:

1. it directly supports the thesis;
2. it is completely proved or experimentally canonical;
3. it replaces rather than merely adds to existing exposition;
4. it can be understood by a graph-learning reviewer without a new conceptual branch.

Under this rule:

- hypercube identity: **main paper**;
- sorting/quantile proposition: **main paper**;
- replica theorem: **deferred**;
- all-orders locality: **deferred**;
- \(n\le32\) interval head: **deferred unless certification is immediate and costs no writing time**;
- triple-defect \(C_5/C_6\) closure: **deferred**;
- E29F-HX finite-shot readout comparison: **required supplement with one main-text sentence**;
- remaining E29/E30 residual and circuit-family analyses: **supplement or deferred**;
- full E24C: **supplement**;
- new application benchmark: **deferred**.

## 16. Acceptance-oriented abstract

**Recommended title:**

> Characterizing the Structural Inductive Bias of a Quantum Graph Feature Map

**Abstract:**

> Hybrid quantum-classical graph learning uses quantum circuits as feature maps, yet graph discrimination alone does not reveal which structural information their outputs expose to downstream models. We characterize the structural inductive bias of a shallow, training-free quantum graph feature map. We show that its commuting \(ZZ\) layer produces a complex cut-phase function whose Walsh coefficients are boundary-sector weight enumerators, while local mixing exposes rooted incidence structure. For cubic graphs, we derive an exact expression for the second derivative of output purity as an affine function of triangle, four-cycle, and diamond counts. This yields formal separations from 1-WL on regular graphs and from the adjacency spectrum on explicit cospectral pairs. Complete censuses of connected cubic graphs on 14 and 16 vertices reveal a replicated hierarchy in both representation geometry and linear accessibility, with short-cycle information concentrated at progressively deeper probability ranks. Comparisons with folklore 2-WL and finite-shot sampling distinguish structural information contained by the ideal representation from information accessible to downstream models and finite measurements.

## 17. Final decision statement

The paper succeeds if a reviewer can answer the following after reading only the abstract, Figure 1, the central theorem, and the primary results table:

1. **Why is this AI?** It characterizes the inductive bias and accessibility of a graph feature map used by downstream learners.
2. **What is mathematically new?** An exact mechanism-to-motif characterization culminating in cubic purity closure and diamond-sensitive cospectral separation.
3. **Why believe it matters beyond selected examples?** The hierarchy replicates over complete connected cubic censuses at two orders.
4. **Were appropriate controls used?** Yes: adjacency spectra, folklore 2-WL, exact cospectral witnesses, finite-shot sampling, and a structure-aware readout counterpoint showing that statistical accessibility is not uniform.
5. **What is not being claimed?** Universal completeness, WL dominance, quantum advantage, general irregular transfer, or practical access to every ideal feature.

No additional scientific breadth is required for this submission. The acceptance-maximizing task is now to execute this narrow argument cleanly, prove the central result visibly, and prevent optional material from obscuring it.
