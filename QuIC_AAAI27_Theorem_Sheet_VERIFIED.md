# QuIC AAAI-27 Theorem Sheet

**Status:** Draft for author verification. Do not describe this file as author-verified until every checkbox in Section 10 is completed.

**Purpose:** This is the only mathematical source that should be uploaded to the main-paper writing project, together with the main-paper writing packet and current manuscript. It contains the permitted theorem statements, notation, coefficient conventions, proof skeletons, and scope restrictions for the seven-page AAAI paper. It deliberately excludes the all-orders, replica, repeated-layer, finite-angle-head, and injectivity programs.

**Canonical source:** QuIC_Formalism_Reproducible_Calculations (2).ipynb, especially Sections 1–4 and Appendix B. Numerical values below were cross-checked against the stored notebook outputs.

---

## 1. Circuit, state, and readout conventions

Let \(G=(V,E)\) be a simple undirected graph with \(n=|V|\) and \(m=|E|\). The one-repetition circuit is

\[
|\psi_G(\beta)\rangle=
R_X(\beta)^{\otimes n}
\left[\prod_{uv\in E}R_{ZZ}^{(u,v)}(\gamma)\right]
\left[\bigotimes_{v\in V}R_X(\eta_v)\right]|0^n\rangle,
\]

with

\[
R_X(\theta)=e^{-i\theta X/2},
\qquad
R_{ZZ}(\gamma)=e^{-i\gamma Z\otimes Z/2}.
\]

For the regular-graph theory, use the uniform encoder \(\eta_v=\eta\). For the canonical experiments,

\[
\eta=2.875,\qquad \gamma=2.0,\qquad \beta=0.1.
\]

Define the labeled Born probabilities, sorted feature map, and purity by

\[
p_G(x;\beta)=|\langle x|\psi_G(\beta)\rangle|^2,
\qquad
\Phi_{\mathrm{QuIC}}(G)=p_G(\beta)^\downarrow,
\]

\[
M_2(G;\beta)=\sum_{x\in\{0,1\}^n}p_G(x;\beta)^2.
\]

Here \(p_G^\downarrow\) denotes descending sorting. The derivative convention in the central theorem is

\[
M_2''(G;0)=
\left.\frac{\partial^2}{\partial\beta^2}M_2(G;\beta)\right|_{\beta=0}.
\]

All theorem statements concern exact noiseless probabilities. The central motif theorem is infinitesimal at \(\beta=0\), even though the census experiments use \(\beta=0.1\).

---

## 2. Lemma: cut phase and exact mixer interference

For \(x\in\{0,1\}^n\), let \(z_v=(-1)^{x_v}\), and let \(c_G(x)\) be the number of edges crossing the cut represented by \(x\). Then

\[
\prod_{uv\in E}e^{-i\gamma z_uz_v/2}
=e^{-i\gamma m/2}e^{i\gamma c_G(x)}.
\]

Thus the commuting \(ZZ\) layer encodes a complex phase landscape over graph cuts. It does not, by itself, make this graph dependence visible in computational-basis probabilities.

Let \(\phi_G(x)\) be the complete pre-mixer amplitude, including the product-state encoder and cut phase. The exact mixer action is

\[
\boxed{
\psi_G(x;\beta)
=\cos^n(\beta/2)
\sum_{S\subseteq V}
[-i\tan(\beta/2)]^{|S|}
\phi_G(x\oplus S).
}
\]

**Permitted interpretation:** the mixer interferes cuts separated by Hamming flips, so order \(r\) in the mixer expansion involves configurations rooted at at most \(r\) flipped vertices and their incident edges.

**Do not claim:** that the commuting \(ZZ\) gates alone compute the final graph representation, or that the hypercube-walk observation is an independent headline theorem.

---

## 3. Proposition: boundary-sector transform

For \(F\subseteq E\), let \(\partial F\subseteq V\) be its odd-degree boundary and let \(\triangle\) denote symmetric difference. Define

\[
\mathcal Z^{\boldsymbol\eta}_{G,T}(q)
=\sum_{F\subseteq E}q^{|F|}
\exp\!\left(i\sum_{v\in T\triangle\partial F}\eta_v\right).
\]

Under the normalized Walsh convention used in the formalism notebook,

\[
\boxed{
\widehat g_G(T)=2^{-n}
\left(\cos\frac\gamma2\right)^m
e^{-\frac i2\sum_v\eta_v}
\mathcal Z^{\boldsymbol\eta}_{G,T}
\left(-i\tan\frac\gamma2\right).
}
\]

For the pure cut phase with a uniform encoder factored away, define

\[
Z_{G,T}(z)=\sum_{F\subseteq E:\,\partial F=T}z^{|F|}.
\]

Then

\[
\widehat f_G(T)=e^{i\gamma m/2}
\cos(\gamma/2)^m
Z_{G,T}(-i\tan(\gamma/2)).
\]

For a simple cubic graph, an even subgraph is a vertex-disjoint cycle packing, giving

\[
[z^3]Z_{G,\varnothing}=C_3,\qquad
[z^4]Z_{G,\varnothing}=C_4,\qquad
[z^5]Z_{G,\varnothing}=C_5,
\]

\[
\boxed{
[z^6]Z_{G,\varnothing}
=C_6+\binom{C_3}{2}-D_\diamond.
}
\]

Here \(C_\ell\) counts simple \(\ell\)-cycles and \(D_\diamond\) is the pair-incidence diamond count defined in Section 5.

**Role in the paper:** this proposition explains why cycles and diamonds are natural algebraic carriers rather than post-hoc regression targets.

**Scope:** the general Ising/cut-polynomial correspondence is not claimed as novel. The contribution is the use of the encoder-bearing transform to characterize the measured feature map.

---

## 4. Proposition: distributional meaning of sorting

Define

\[
\nu_G=\frac1{2^n}\sum_x\delta_{2^n p_G(x)}.
\]

For graphs \(G,H\) of the same order,

\[
\boxed{
\min_{\sigma\in S_{2^n}}
\|p_G-\sigma p_H\|_1
=\|p_G^\downarrow-p_H^\downarrow\|_1
=W_1(\nu_G,\nu_H).
}
\]

**Proof skeleton:** monotone matching minimizes the sum of absolute differences in one dimension. Applying it to equally weighted atoms \(2^np_G(x)\) and \(2^np_H(x)\) cancels the empirical factor \(2^{-n}\).

**Permitted interpretation:** sorting is the empirical quantile representation of the Born-value distribution and implements optimal matching under arbitrary permutations of probability coordinates.

**Mandatory qualification:** coordinate permutations form \(S_{2^n}\), which is much larger than the vertex-relabeling action. Sorting is a coarse invariantization and is not proved complete or injective.

---

## 5. Central theorem: exact cubic closure of the second purity derivative

### 5.1 Pair-incidence notation

For an unordered vertex pair \(i<j\), define

\[
a_{ij}=\mathbf 1[ij\in E],
\qquad
\kappa_{ij}=|N(i)\cap N(j)|.
\]

Let

\[
N_{a,k}(G)=
\#\{\{i,j\}:a_{ij}=a,\ \kappa_{ij}=k\}.
\]

For a \(d\)-regular graph, the exact pair-adjacency/codegree reduction is

\[
M_2''(G;0)=B_{n,d}+\sum_{a,k}N_{a,k}(G)F_{a,k}^{(n,d)},
\]

where \(B_{n,d}\) is graph-independent at fixed \(n,d,\eta,\gamma\), and \(F_{a,k}^{(n,d)}\) is the exact local pair kernel. For cubic graphs abbreviate \(F_{a,k}^{(n,3)}\) by \(F_{a,k}\), and define

\[
v_a=F_{a,1}-F_{a,0},
\]

\[
\delta_0=F_{0,2}-2F_{0,1}+F_{0,0},
\qquad
\delta_1=F_{1,2}-2F_{1,1}+F_{1,0}.
\]

Define the pair-incidence diamond count by

\[
\boxed{
D_\diamond(G)=\sum_k\binom{k}{2}N_{1,k}(G).
}
\]

This counts a diamond through its adjacent root pair and two common neighbors. It is not restricted to induced diamonds; a \(K_4\) contributes once for each of its six edges. Throughout the paper, \(C_4\) counts all simple four-cycles, including chorded ones.

### 5.2 Algebraic third-difference lemma

For every simple cubic graph and all real encoder and entangler angles,

\[
\boxed{
F_{0,3}-3F_{0,2}+3F_{0,1}-F_{0,0}=0.
}
\]

Equivalently, for \(k\in\{0,1,2,3\}\),

\[
F_{0,k}=F_{0,0}+kv_0+\binom{k}{2}\delta_0.
\]

**Approved proof skeleton:**

1. Put \(c=\cos(\eta/2)\), \(s=\sin(\eta/2)\), \(r=c^2\), \(u=s^2\), and \(L=r^2+u^2\).
2. For nonadjacent roots, expand the three terms in the exact pair kernel. Every common-neighbor contribution lies in the span of three geometric sequences \(b_1^k,b_2^k,b_3^k\), with \(b_2=\overline b_1\) and \(b_3\in\mathbb R\).
3. The combined weights are
   \[
   \Gamma_1=\kappa P_+^6,\qquad
   \Gamma_2=\kappa P_-^6,\qquad
   \Gamma_3=2\kappa(P_+P_-)^3,
   \]
   where \(\kappa=2ru(r-u)^2/L^2\).
4. Since the third difference of \(b^k\) is \((b-1)^3\), substitution cancels the Laurent denominators and leaves the exact aligned/anti-aligned cancellation \(1+1-2=0\).
5. Apparent singularities at isolated zeros of the intermediate carriers are removable because the original local kernel is a continuous trigonometric polynomial.

The full carrier algebra belongs in Appendix~\(\ref{app:M2-proof}\). The main paper must retain the statement and the \(1+1-2\) cancellation mechanism.

### 5.3 Motif-closure theorem

**Theorem (cubic second-purity motif closure).** Let \(G\) be a simple cubic graph on \(n\) vertices, with uniform encoder angle \(\eta\), entangler angle \(\gamma\), and the circuit defined in Section 1. Then

\[
\boxed{
M_2''(G;0)=A_n
+b_3C_3(G)
+b_4C_4(G)
+b_DD_\diamond(G),
}
\]

where

\[
b_3=3(v_1-v_0),\qquad
b_4=2\delta_0,\qquad
b_D=\delta_1-\delta_0,
\]

and

\[
A_n=B_{n,3}
+\left[\binom n2-\frac{3n}{2}\right]F_{0,0}
+\frac{3n}{2}F_{1,0}
+3nv_0.
\]

The reduction uses

\[
\sum_k kN_{1,k}=3C_3,\qquad
\sum_{a,k}\binom{k}{2}N_{a,k}=2C_4,\qquad
\sum_k\binom{k}{2}N_{1,k}=D_\diamond.
\]

At \(\eta=2.875,\gamma=2.0,n=14\), the coefficients in the \(M_2''(0)\) convention are

\[
\boxed{
b_3=3.730451849553312\times10^{-5},
}
\]

\[
\boxed{
b_4=3.343689464196942\times10^{-8},
\qquad
b_D=3.991027080346710\times10^{-8}.
}
\]

Thus \(b_4\) and \(b_D\) are nonzero but approximately three orders of magnitude below \(b_3\) at this setting.

### 5.4 Coefficient convention lock

| Expansion | Coefficient of motif \(X\) |
|---|---:|
| \(M_2''(0)\) | \(b_X\) |
| coefficient \([\beta^2]M_2(\beta)\) | \(b_X/2\) |
| coefficient of \(t^2\), \(t=\tan(\beta/2)\) | \(2b_X\) |

Every manuscript equation and numerical coefficient must name its convention.

### 5.5 Scope lock

This theorem identifies the first graph-dependent purity curvature on fixed-order cubic families. It does **not** assert that the second-order term controls the magnitude at \(\beta=0.1\).

For the triangular prism minus \(K_{3,3}\), the verified expansion begins

\[
\Delta M_2(\beta)
=4.9351508856\times10^{-5}\beta^2
+5.6148736330\times10^{-3}\beta^3
+O(\beta^4).
\]

At \(\beta=0.1\), the cubic contribution is about \(11.4\) times the quadratic contribution. The correct language is **structural motif closure**, not a claim that the theorem quantitatively explains the complete canonical-angle spectrum.

---

## 6. Corollary: explicit separation from ordinary 1-WL

On fixed-order regular graphs, ordinary 1-WL assigns the same constant color to every vertex at every refinement round. Let \(G,H\) be same-order simple cubic graphs. If

\[
b_3\Delta C_3+b_4\Delta C_4+b_D\Delta D_\diamond\ne0,
\]

then \(M_2''(G;0)\ne M_2''(H;0)\). Because the zeroth- and first-order purity terms are common-mode on the fixed-order regular family and \(M_2\) is analytic in \(\beta\), the purities differ for all sufficiently small nonzero \(\beta\). Unequal purities imply unequal probability multisets and hence unequal sorted QuIC representations.

**Explicit witness:** the triangular prism and \(K_{3,3}\) are both cubic on six vertices and ordinary 1-WL equivalent. Their motif counts are

\[
(C_3,C_4,D_\diamond)_{\mathrm{prism}}=(2,3,0),
\]

\[
(C_3,C_4,D_\diamond)_{K_{3,3}}=(0,9,0).
\]

At \(\eta=2.875,\gamma=2.0\), the stored direct calculation gives

\[
M_2''(\mathrm{prism};0)-M_2''(K_{3,3};0)
=9.870301771109\times10^{-5}.
\]

**Permitted claim:** QuIC explicitly separates regular graph pairs that ordinary 1-WL collapses.

**Prohibited claim:** QuIC dominates 1-WL, 2-WL, or the \(k\)-WL hierarchy in general.

---

## 7. Corollary: adjacency-cospectral diamond separation

For a simple cubic graph,

\[
\operatorname{tr}(A^3)=6C_3,
\]

\[
\operatorname{tr}(A^4)=15n+8C_4,
\]

\[
\boxed{
\operatorname{tr}(A^6)
=87n+6C_3+96C_4+12(C_6+D_\diamond).
}
\]

Therefore adjacency-cospectral cubic graphs of the same order have equal \(C_3\), equal \(C_4\), and equal \(C_6+D_\diamond\).

If adjacency-cospectral cubic graphs \(G,H\) satisfy \(D_\diamond(G)\ne D_\diamond(H)\) and \(b_D(\eta,\gamma,n)\ne0\), then

\[
\boxed{
M_2''(G;0)-M_2''(H;0)
=b_D\bigl(D_\diamond(G)-D_\diamond(H)\bigr)\ne0.
}
\]

Their sorted Born representations consequently differ for all sufficiently small nonzero mixer angles. Since the spectrum fixes \(C_6+D_\diamond\),

\[
\Delta C_6=-\Delta D_\diamond.
\]

E14 provides six independent finite-angle witnesses at \(n=18,\beta=0.1\); it is empirical confirmation at the operating point, not part of the local analytic corollary.

**Permitted claim:** the ideal QuIC representation is strictly beyond adjacency-spectrum equivalence on explicit cubic pairs.

**Prohibited claim:** quantum advantage, universal cospectral separation, or superiority over classical computation.

---

## 8. Approved theorem ordering

1. Circuit and feature-map definition.
2. Cut-phase and mixer-interference lemma.
3. Boundary-sector proposition.
4. Sorting/quantile proposition.
5. Cubic motif-closure theorem, including the cancellation idea.
6. Ordinary 1-WL corollary.
7. Adjacency-cospectral diamond corollary.
8. E14 finite-angle witnesses.

Only the motif closure should be called the **central theorem**.

---

## 9. Material excluded from the AAAI main-paper theory

Do not introduce:

- replica partition functions for all moments;
- all-orders rooted-incidence locality as a formal theorem;
- higher-order purity carrier classifications;
- repeated circuits as space-time boundary polynomials;
- finite-angle head-separation certificates;
- generic-collision or measure-zero parameter dichotomies;
- universal or generic sorted-spectrum injectivity;
- finite-shot \(C_5\) or \(C_6\) decoders inferred from defect layers;
- a general irregular-graph theorem;
- a general comparison with \(k\)-WL.

These are deferred foundational-theory directions or supplementary context.
