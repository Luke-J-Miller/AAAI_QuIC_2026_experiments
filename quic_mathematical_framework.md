# Mathematical Framework for QuIC

## 1. Circuit definition

Let \(G=(V,E)\) be a simple undirected graph with \(n=|V|\), \(m=|E|\), vertex degrees \(d_i\), and maximum degree \(\Delta\). For one circuit repetition, define

\[
U_G(\boldsymbol{\alpha},\gamma,\beta)
=
U_M(\beta)\,
U_E(G,\gamma)\,
U_D(G,\boldsymbol{\alpha}),
\]

where

\[
U_D(G,\boldsymbol{\alpha})
=
\bigotimes_{i=1}^{n}R_X(\alpha_i),
\qquad
\alpha_i=\theta_{\mathrm{enc}}\frac{d_i}{\Delta},
\]

\[
U_E(G,\gamma)
=
\prod_{(i,j)\in E}R_{ZZ}^{(i,j)}(\gamma),
\]

and

\[
U_M(\beta)
=
\bigotimes_{i=1}^{n}R_X(\beta).
\]

The circuit state and measured distribution are

\[
|\psi_G\rangle
=
U_G|0^n\rangle,
\qquad
p_G(y)
=
|\langle y|\psi_G\rangle|^2.
\]

The QuIC representation is the descendingly sorted probability vector

\[
q_G=\operatorname{sort}_{\downarrow}\{p_G(y):y\in\{0,1\}^n\}.
\]

For the cubic-graph experiments, \(d_i=\Delta=3\), so every encoder angle is identical:

\[
\alpha_i=\theta_{\mathrm{enc}}.
\]

Thus, within the cubic census, all graph dependence enters through the \(R_{ZZ}\) interaction pattern and its subsequent interference under the mixer.

---

## 2. The entangler is a cut-phase operator

For \(x\in\{0,1\}^n\), define

\[
z_i(x)=(-1)^{x_i}
\]

and let

\[
S_x=\{i:x_i=1\}.
\]

Write

\[
c_G(x)=|\delta_G(S_x)|
\]

for the number of edges crossing the cut induced by \(x\).

For an edge \((i,j)\),

\[
z_i(x)z_j(x)
=
\begin{cases}
+1,&x_i=x_j,\\
-1,&x_i\neq x_j.
\end{cases}
\]

Hence

\[
\sum_{(i,j)\in E}z_i(x)z_j(x)
=
m-2c_G(x).
\]

Using the Qiskit convention

\[
R_{ZZ}^{(i,j)}(\gamma)
=
\exp\left(-\frac{i\gamma}{2}Z_iZ_j\right),
\]

the complete entangling layer acts diagonally:

\[
U_E(G,\gamma)|x\rangle
=
\exp\left[
-\frac{i\gamma}{2}
\sum_{(i,j)\in E}z_i(x)z_j(x)
\right]|x\rangle.
\]

Substituting the cut identity gives

\[
U_E(G,\gamma)|x\rangle
=
e^{-i\gamma m/2}
e^{i\gamma c_G(x)}
|x\rangle.
\]

The factor \(e^{-i\gamma m/2}\) is global. Therefore, up to global phase,

\[
\boxed{
U_E(G,\gamma)|x\rangle
=
e^{i\gamma c_G(x)}|x\rangle.
}
\]

The entangler encodes the complete graph cut function into computational-basis phases.

---

## 3. QuIC as a transform of the cut landscape

After the degree encoder,

\[
|\phi_G\rangle
=
U_D|0^n\rangle
=
\sum_x w_G(x)|x\rangle,
\]

where

\[
w_G(x)
=
\prod_{i=1}^{n}
\cos\left(\frac{\alpha_i}{2}\right)^{1-x_i}
\left[
-i\sin\left(\frac{\alpha_i}{2}\right)
\right]^{x_i}.
\]

After the entangler, omitting its global phase,

\[
|\eta_G\rangle
=
\sum_x
w_G(x)e^{i\gamma c_G(x)}|x\rangle.
\]

The mixer matrix element depends only on Hamming distance:

\[
\langle y|U_M(\beta)|x\rangle
=
\cos\left(\frac{\beta}{2}\right)^{n-d_H(x,y)}
\left[
-i\sin\left(\frac{\beta}{2}\right)
\right]^{d_H(x,y)}.
\]

Define

\[
K_\beta(y,x)
=
\cos\left(\frac{\beta}{2}\right)^{n-d_H(x,y)}
\left[
-i\sin\left(\frac{\beta}{2}\right)
\right]^{d_H(x,y)}.
\]

Then

\[
\boxed{
\psi_G(y)
=
\sum_x
K_\beta(y,x)\,
w_G(x)\,
e^{i\gamma c_G(x)}.
}
\]

Thus QuIC applies a translation-invariant transform on the Boolean hypercube to the complex signal

\[
f_G(x)=w_G(x)e^{i\gamma c_G(x)}.
\]

Symbolically,

\[
\psi_G
=
\mathcal T_\beta
\left[
w_Ge^{i\gamma c_G}
\right].
\]

The circuit therefore performs the following operations:

1. Represent every vertex subset \(S_x\) as a Boolean-cube point.
2. assign that point the graph cut value \(c_G(x)\);
3. encode the cut value as a phase;
4. mix neighboring Boolean-cube points;
5. measure the resulting interference pattern;
6. sort the probabilities to remove dependence on vertex labels.

The resulting object is appropriately described as an **unlabeled cut-phase interference spectrum**.

---

## 4. Permutation equivariance and graph invariance

Let \(\pi\in S_n\) be a permutation of the vertices, and let \(P_\pi\) be the corresponding qubit-permutation unitary:

\[
P_\pi|x_1,\ldots,x_n\rangle
=
|x_{\pi^{-1}(1)},\ldots,x_{\pi^{-1}(n)}\rangle.
\]

The degree encoder is equivariant because vertex degrees permute with the graph:

\[
U_D(\pi G)
=
P_\pi U_D(G)P_\pi^\dagger.
\]

The entangling layer is equivariant because the edge set transforms as

\[
E(\pi G)=\{(\pi(i),\pi(j)):(i,j)\in E(G)\},
\]

giving

\[
U_E(\pi G)
=
P_\pi U_E(G)P_\pi^\dagger.
\]

The uniform mixer commutes with every qubit permutation:

\[
P_\pi U_M(\beta)P_\pi^\dagger
=
U_M(\beta).
\]

Therefore,

\[
U_{\pi G}
=
P_\pi U_G P_\pi^\dagger.
\]

Since \(P_\pi|0^n\rangle=|0^n\rangle\),

\[
|\psi_{\pi G}\rangle
=
P_\pi|\psi_G\rangle.
\]

Consequently,

\[
p_{\pi G}(\pi y)=p_G(y).
\]

The unsorted distribution is permutation equivariant, and sorting removes the induced output permutation:

\[
\boxed{
q_{\pi G}=q_G.
}
\]

This proves graph-isomorphism invariance of the QuIC representation.

---

## 5. The labeled cut function determines the graph

The cut function is itself a complete labeled representation.

For a singleton set,

\[
c_G(\{i\})=d_i.
\]

For two vertices,

\[
c_G(\{i,j\})
=
d_i+d_j-2A_{ij},
\]

because an edge \((i,j)\), when present, is counted in both singleton cuts but does not cross the joint cut.

Therefore,

\[
\boxed{
A_{ij}
=
\frac{
c_G(\{i\})+c_G(\{j\})-c_G(\{i,j\})
}{2}.
}
\]

Thus the complete labeled cut landscape determines the adjacency matrix exactly.

This does **not** prove that the measured and sorted QuIC representation is injective. It establishes only that the signal supplied to the phase transform contains the complete labeled graph.

---

## 6. Irrational phase encoding as an anti-aliasing condition

Cut values are integers. Consider the phase map

\[
k\longmapsto e^{i\gamma k},
\qquad
k\in\mathbb Z.
\]

Suppose two distinct cut values \(k\neq \ell\) receive the same phase:

\[
e^{i\gamma k}=e^{i\gamma \ell}.
\]

Then

\[
\gamma(k-\ell)=2\pi r
\]

for some \(r\in\mathbb Z\), implying

\[
\frac{\gamma}{\pi}
=
\frac{2r}{k-\ell}
\in\mathbb Q.
\]

Therefore,

\[
\boxed{
\gamma\notin\pi\mathbb Q
\quad\Longrightarrow\quad
k\neq\ell
\implies
e^{i\gamma k}\neq e^{i\gamma\ell}.
}
\]

The condition is sufficient, though not necessary for a fixed finite cut range. It prevents exact periodic aliasing between distinct integer cut values for graphs of arbitrary size.

If

\[
\gamma=\pi\frac{a}{b},
\]

the phase map has a finite period in \(k\), and sufficiently separated cut values necessarily alias.

The irrational-angle condition is only a **local anti-aliasing condition on the phase encoding**. It does not rule out:

- cancellation between multiple basis amplitudes;
- distinct statevectors with equal Born probabilities;
- equal probability vectors up to coordinate permutation;
- finite-precision numerical aliases;
- operational indistinguishability under finite shots or hardware noise.

Moreover, irrational rotations are represented only approximately in floating-point arithmetic and physical control systems.

---

## 7. Boundary-resolved Fourier expansion

Let

\[
\chi_T(x)
=
\prod_{i\in T}z_i(x)
=
(-1)^{\sum_{i\in T}x_i}
\]

be the Walsh character indexed by \(T\subseteq V\). For a function \(f:\{0,1\}^n\to\mathbb C\), use the normalized transform

\[
\widehat f(T)
=
2^{-n}\sum_x f(x)\chi_T(x).
\]

Define the pure cut-phase function

\[
f_G(x)=e^{i\gamma c_G(x)}.
\]

From the cut identity,

\[
f_G(x)
=
e^{i\gamma m/2}
\prod_{(i,j)\in E}
e^{-i\gamma z_i(x)z_j(x)/2}.
\]

Each edge factor expands as

\[
e^{-i\gamma z_iz_j/2}
=
\cos\left(\frac{\gamma}{2}\right)
-
i\sin\left(\frac{\gamma}{2}\right)z_iz_j.
\]

Expanding the product over edges gives

\[
f_G(x)
=
e^{i\gamma m/2}
\sum_{F\subseteq E}
\cos\left(\frac{\gamma}{2}\right)^{m-|F|}
\left[
-i\sin\left(\frac{\gamma}{2}\right)
\right]^{|F|}
\prod_{(i,j)\in F}z_i(x)z_j(x).
\]

For an edge subset \(F\subseteq E\), define its odd boundary

\[
\partial F
=
\{v\in V:\deg_F(v)\equiv1\pmod2\}.
\]

Because

\[
\prod_{(i,j)\in F}z_iz_j
=
\prod_{v\in V}z_v^{\deg_F(v)}
=
\prod_{v\in\partial F}z_v
=
\chi_{\partial F}(x),
\]

the Walsh coefficient is

\[
\boxed{
\widehat f_G(T)
=
e^{i\gamma m/2}
\sum_{\substack{F\subseteq E\\\partial F=T}}
\cos\left(\frac{\gamma}{2}\right)^{m-|F|}
\left[
-i\sin\left(\frac{\gamma}{2}\right)
\right]^{|F|}.
}
\]

When \(\cos(\gamma/2)\neq0\), define

\[
Z_{G,T}(z)
=
\sum_{\substack{F\subseteq E\\\partial F=T}}
z^{|F|}.
\]

Then

\[
\boxed{
\widehat f_G(T)
=
e^{i\gamma m/2}
\cos\left(\frac{\gamma}{2}\right)^m
Z_{G,T}
\left(
-i\tan\frac{\gamma}{2}
\right).
}
\]

The polynomial \(Z_{G,T}\) is the generating function of edge subsets with odd boundary \(T\).

This is the central structural theorem.

### Important qualification

At the canonical value \(\gamma=2\),

\[
\left|\tan\frac{\gamma}{2}\right|
=
\tan(1)
\approx1.557.
\]

Therefore, the polynomial is not being evaluated in a small-\(\gamma\) regime. Increasing edge order is not suppressed by powers of \(\tan(\gamma/2)\). The expansion describes:

- which structures occur;
- the boundary sector in which they occur;
- the earliest edge order at which they can occur.

It does not, by itself, order their numerical influence at the canonical angle.

---

## 8. Closed and open boundary sectors

### 8.1 Closed sector

When

\[
T=\varnothing,
\]

the condition \(\partial F=\varnothing\) requires every selected degree to be even. Such an \(F\) is an even subgraph.

In a cubic graph,

\[
\deg_F(v)\in\{0,1,2,3\},
\]

so evenness implies

\[
\deg_F(v)\in\{0,2\}.
\]

Every nontrivial connected component of \(F\) is therefore a cycle. Because a cubic graph cannot support degree four in \(F\), these cycles are vertex-disjoint.

Thus, for cubic graphs,

\[
Z_{G,\varnothing}(z)
\]

is the generating polynomial for vertex-disjoint unions of cycles.

### 8.2 Open sectors

When

\[
T\neq\varnothing,
\]

the edge sets are \(T\)-joins: subgraphs whose odd-degree vertices are exactly \(T\). These sectors contain paths, collections of paths, cycles attached to paths, and more complicated boundary-conditioned structures.

The closed sector represents cycle structure. The open sectors represent how the graph connects specified boundary vertices.

---

## 9. Exact low-order closed-sector coefficients on cubic graphs

Let \(C_k(G)\) denote the number of simple \(k\)-cycles.

For three, four, and five selected edges, the only possible nonempty even subgraph is a single cycle of the corresponding length. Therefore,

\[
\boxed{
[z^3]Z_{G,\varnothing}(z)=C_3,
}
\]

\[
\boxed{
[z^4]Z_{G,\varnothing}(z)=C_4,
}
\]

and

\[
\boxed{
[z^5]Z_{G,\varnothing}(z)=C_5.
}
\]

This establishes the exact structural ordering

\[
C_3,\quad C_4,\quad C_5
\]

in the low-order closed sector.

It does not prove that these coefficients dominate the fixed-angle measured distribution. The empirical stratification results show that they do dominate the observed geometry:

\[
C_3
\rightarrow
C_4\mid C_3
\rightarrow
C_5\mid(C_3,C_4).
\]

The theory identifies the available hierarchy; the experiments establish its finite-angle prominence.

---

## 10. Sixth-order closed sector and diamonds

At six edges, an even subgraph of a simple cubic graph is either:

1. a single 6-cycle; or
2. a union of two vertex-disjoint triangles.

Let \(D(G)\) denote the number of unordered pairs of triangles sharing an edge. Equivalently, \(D\) counts diamond subgraphs \(K_4-e\).

Two distinct triangles in a cubic graph cannot share exactly one vertex: that vertex would require four incident triangle edges. They are therefore either vertex-disjoint or share an edge.

The number of vertex-disjoint triangle pairs is

\[
\binom{C_3}{2}-D.
\]

Hence

\[
\boxed{
[z^6]Z_{G,\varnothing}(z)
=
C_6+\binom{C_3}{2}-D.
}
\]

After conditioning on \(C_3\), the new sixth-order closed-sector quantity is

\[
\boxed{
Q_6=C_6-D.
}
\]

This is the first order at which the closed cut expansion separates two structures through a nontrivial signed combination.

---

## 11. Adjacency spectral moments on cubic graphs

Adjacency spectral moments count closed walks:

\[
\operatorname{tr}(A^k)
=
\sum_{i=1}^{n}\lambda_i^k
=
\#\{\text{closed walks of length }k\}.
\]

For a simple cubic graph,

\[
\boxed{
\operatorname{tr}(A^2)=3n,
}
\]

\[
\boxed{
\operatorname{tr}(A^3)=6C_3,
}
\]

\[
\boxed{
\operatorname{tr}(A^4)=15n+8C_4,
}
\]

\[
\boxed{
\operatorname{tr}(A^5)=60C_3+10C_5,
}
\]

and

\[
\boxed{
\operatorname{tr}(A^6)
=
87n+6C_3+96C_4+12C_6+12D.
}
\]

Consequently,

\[
C_3=\frac{\operatorname{tr}(A^3)}{6},
\]

\[
C_4=
\frac{\operatorname{tr}(A^4)-15n}{8},
\]

and

\[
C_5
=
\frac{
\operatorname{tr}(A^5)-10\operatorname{tr}(A^3)
}{10}.
\]

Thus \(C_3,C_4,\) and \(C_5\) are adjacency-spectral invariants within the cubic census. Their strong accessibility from QuIC is therefore consistent with the observed spectral backbone.

### Derivation of the fourth moment

For a general simple graph,

\[
\operatorname{tr}(A^4)
=
2m
+
4\sum_v\binom{d_v}{2}
+
8C_4.
\]

For a cubic graph,

\[
2m=3n,
\qquad
4\sum_v\binom{3}{2}=12n,
\]

giving

\[
\operatorname{tr}(A^4)=15n+8C_4.
\]

### Derivation of the fifth moment

A closed 5-walk has one of three quotient supports:

- a 5-cycle;
- a triangle;
- a triangle with one pendant edge.

A 5-cycle contributes \(10C_5\). The two triangle-based quotient classes jointly contribute \(60C_3\) in a cubic graph, yielding

\[
\operatorname{tr}(A^5)=10C_5+60C_3.
\]

---

## 12. Derivation of the sixth spectral moment

A closed 6-walk is a homomorphism from \(C_6\) into \(G\). Grouping these homomorphisms by their kernel partition produces the following quotient supports.

| Quotient support | Kernel multiplicity | Injective homomorphisms into a cubic graph |
|---|---:|---:|
| \(C_6\) | \(1\) | \(12C_6\) |
| \(C_4\) with a pendant edge | \(6\) | \(8C_4-4D\) |
| Two triangles sharing one vertex | \(3\) | \(0\) |
| \(C_4\) | \(6\) | \(8C_4\) |
| \(P_4\) | \(3\) | \(12n-6C_3\) |
| Diamond \(K_4-e\) | \(9\) | \(4D\) |
| \(K_{1,3}\) | \(2\) | \(6n\) |
| \(P_3\) | \(6\) | \(6n\) |
| \(C_3\) | \(4\) | \(6C_3\) |
| \(K_2\) | \(1\) | \(3n\) |

Summing gives

\[
\begin{aligned}
\operatorname{tr}(A^6)
={}&12C_6
+6(8C_4-4D)
+6(8C_4)\\
&+3(12n-6C_3)
+9(4D)
+2(6n)\\
&+6(6n)
+4(6C_3)
+3n,
\end{aligned}
\]

which simplifies to

\[
\operatorname{tr}(A^6)
=
87n+6C_3+96C_4+12C_6+12D.
\]

---

## 13. The diamond sign split

Remove the lower-order cubic terms from the sixth spectral moment:

\[
S_6
=
\frac{
\operatorname{tr}(A^6)-87n-6C_3-96C_4
}{12}.
\]

Then

\[
\boxed{
S_6=C_6+D.
}
\]

By contrast, after removing the fixed triangle-pair term from the sixth closed-sector coefficient,

\[
Q_6
=
[z^6]Z_{G,\varnothing}
-
\binom{C_3}{2},
\]

we obtain

\[
\boxed{
Q_6=C_6-D.
}
\]

Therefore, the spectral and cut-sector expansions expose complementary linear combinations:

\[
S_6=C_6+D,
\qquad
Q_6=C_6-D.
\]

Jointly,

\[
\boxed{
C_6=\frac{S_6+Q_6}{2},
}
\]

and

\[
\boxed{
D=\frac{S_6-Q_6}{2}.
}
\]

This is the sharpest exact distinction between the two representations:

> The adjacency spectrum aggregates 6-cycles and diamonds with the same sign, whereas the sixth-order closed cut sector separates them with opposite signs.

The qualification is that QuIC evaluates the complete generating polynomial at a fixed complex argument and then applies mixing, Born measurement, and sorting. The coefficient’s existence does not guarantee clean fixed-angle decodability. The residual diamond experiment tests whether this distinction survives the complete readout.

---

## 14. Open sectors encode graph distance

For any even vertex set \(T\), define

\[
\tau_G(T)
=
\min\{|F|:\partial F=T\},
\]

the minimum cardinality of a \(T\)-join.

By definition of \(Z_{G,T}\),

\[
\boxed{
\operatorname{val}Z_{G,T}
=
\tau_G(T),
}
\]

where \(\operatorname{val}\) is the smallest exponent having a nonzero coefficient.

For a two-vertex boundary

\[
T=\{u,v\},
\]

every \(T\)-join contains a \(u\)-to-\(v\) path, so

\[
|F|\geq d_G(u,v).
\]

A shortest \(u\)-to-\(v\) path itself has odd boundary \(\{u,v\}\), giving equality:

\[
\boxed{
\operatorname{val}Z_{G,\{u,v\}}
=
d_G(u,v).
}
\]

Moreover,

\[
[z^{d_G(u,v)}]Z_{G,\{u,v\}}
\]

equals the number of shortest \(u\)-to-\(v\) paths.

Thus the complete collection of two-boundary sector polynomials contains the graph distance matrix in its lowest-degree terms. In particular, it structurally contains information determining

\[
W(G)
=
\sum_{\{u,v\}}d_G(u,v),
\]

the Wiener index, and

\[
\operatorname{rad}(G)
=
\min_u\max_v d_G(u,v),
\]

the radius.

This gives a direct theoretical explanation for the empirical association of the non-spectral QuIC residue with Wiener index and radius.

Again, fixed-angle evaluation and sorting need not preserve all such information. The theorem identifies what is present in the boundary-resolved cut transform before those subsequent quotients.

---

## 15. The mixer exposes finite differences of the cut landscape

Let

\[
\phi_G(x)
=
w_G(x)e^{i\gamma c_G(x)}
\]

be the amplitude immediately before the mixer. Since

\[
U_M(\beta)
=
\exp\left(
-\frac{i\beta}{2}\sum_iX_i
\right),
\]

a small-\(\beta\) expansion gives

\[
\psi_G(y;\beta)
=
\phi_G(y)
-
\frac{i\beta}{2}
\sum_i
\phi_G(y\oplus e_i)
+
O(\beta^2).
\]

Therefore,

\[
p_G(y;\beta)
=
|\phi_G(y)|^2
+
\beta
\sum_i
\operatorname{Im}
\left[
\overline{\phi_G(y)}
\phi_G(y\oplus e_i)
\right]
+
O(\beta^2).
\]

The relative phase in the first correction is

\[
\overline{\phi_G(y)}
\phi_G(y\oplus e_i)
=
\overline{w_G(y)}
w_G(y\oplus e_i)
e^{i\gamma\Delta_i c_G(y)},
\]

where

\[
\Delta_i c_G(y)
=
c_G(y\oplus e_i)-c_G(y).
\]

Using \(z_i=(-1)^{y_i}\),

\[
\boxed{
\Delta_i c_G(y)
=
z_i
\sum_{j\in N(i)}z_j.
}
\]

For cubic graphs,

\[
\Delta_i c_G(y)\in\{-3,-1,1,3\}.
\]

At \(\beta=0\),

\[
p_G(y;0)=|w_G(y)|^2.
\]

Within the cubic census, this depends only on Hamming weight and is graph-independent. All graph discrimination in the measured probabilities therefore appears at positive order in \(\beta\), through finite differences and correlations of the cut landscape.

Higher powers of \(\beta\) involve simultaneous flips of multiple vertices and therefore probe increasingly extended cut correlations.

---

## 16. The mixer does not suppress Fourier sectors by magnitude

The mixer kernel is a Boolean convolution. Its Walsh multiplier is

\[
\widehat K_\beta(T)
=
\left[
\cos\left(\frac{\beta}{2}\right)
-
i\sin\left(\frac{\beta}{2}\right)
\right]^{n-|T|}
\left[
\cos\left(\frac{\beta}{2}\right)
+
i\sin\left(\frac{\beta}{2}\right)
\right]^{|T|}.
\]

Therefore,

\[
\boxed{
\widehat K_\beta(T)
=
e^{-i\beta(n-2|T|)/2}.
}
\]

Its magnitude is

\[
|\widehat K_\beta(T)|=1
\]

for every \(T\). The mixer does not attenuate high-\(|T|\) boundary sectors in the Walsh basis.

The correct distinction is:

- in the computational basis, transitions over Hamming distance \(r\) scale as
  \[
  \left|\tan\frac{\beta}{2}\right|^r;
  \]
- in the Walsh basis, all sectors retain their magnitude but acquire \(|T|\)-dependent phases.

At the canonical value \(\beta=0.1\),

\[
\tan(\beta/2)\approx0.05,
\]

so long Hamming-distance transitions are strongly suppressed in the direct basis. This motivates a small-\(\beta\) analysis of the measured statistics, but not a Fourier-magnitude suppression argument.

---

## 17. Balanced-mixer interpretation

At

\[
\beta=\frac{\pi}{2},
\]

the kernel is

\[
K_{\pi/2}(y,x)
=
2^{-n/2}(-i)^{d_H(x,y)}.
\]

Using

\[
(-i)^{d_H(x,y)}
=
(-i)^{|x|+|y|}
(-1)^{x\cdot y},
\]

one obtains

\[
\psi_G(y)
=
2^{-n/2}
(-i)^{|y|}
\sum_x
(-i)^{|x|}
w_G(x)e^{i\gamma c_G(x)}
(-1)^{x\cdot y}.
\]

Thus, up to local phase factors, the balanced mixer computes a Walsh transform of the cut-phase signal. The probabilities are its power spectrum:

\[
p_G(y)
=
\left|
\widehat{\widetilde f_G}(y)
\right|^2
\]

for

\[
\widetilde f_G(x)
=
(-i)^{|x|}
w_G(x)e^{i\gamma c_G(x)}.
\]

The canonical circuit uses \(\beta=0.1\), not \(\pi/2\), so this is an interpretive special case rather than the exact canonical readout.

---

## 18. Probability moments and the sorted representation

Let

\[
N=2^n
\]

and write the unsorted probabilities as

\[
p_1,\ldots,p_N.
\]

Define the power sums

\[
M_r(G)
=
\sum_{j=1}^{N}p_j^r.
\]

The first \(N\) power sums determine the elementary symmetric polynomials through Newton’s identities. These determine the polynomial

\[
P_G(t)
=
\prod_{j=1}^{N}(t-p_j).
\]

The roots of \(P_G\), including multiplicities, are exactly the probability multiset. Therefore,

\[
\boxed{
\{M_1,\ldots,M_N\}
\quad\text{determines}\quad
q_G.
}
\]

Conversely, \(q_G\) determines every \(M_r\). The full sorted vector and the complete probability-moment sequence are therefore equivalent descriptions of the measured probability multiset.

Low-order moments are compressed symmetric summaries. The empirical moment ladder shows:

- purity \(M_2\) almost completely determines \(C_3\);
- moments through approximately \(M_5\) recover \(C_4\);
- \(C_5\) is not recoverable from the tested low-order moments but is linearly accessible from the full vector.

This indicates that progressively finer structural information resides beyond the lowest symmetric summaries.

---

## 19. Replica-partition formulation of probability moments

For integer \(r\),

\[
M_r(G)
=
\sum_y|\psi_G(y)|^{2r}.
\]

Expanding \(\psi_G(y)\) and its conjugate introduces \(r\) forward replicas and \(r\) conjugate replicas:

\[
M_r(G)
=
\sum_{\substack{
x^{(1)},\ldots,x^{(r)}\\
\bar x^{(1)},\ldots,\bar x^{(r)}
}}
\mathcal W_{\mathrm{local}}
\prod_{(i,j)\in E}
\mathcal W_{\mathrm{edge}}
\left(
\mathbf s_i,\mathbf s_j
\right),
\]

where each replicated vertex state is

\[
\mathbf s_i
=
\left(
z_i^{(1)},\ldots,z_i^{(r)},
\bar z_i^{(1)},\ldots,\bar z_i^{(r)}
\right).
\]

The edge factor is

\[
\mathcal W_{\mathrm{edge}}
=
\exp\left[
-\frac{i\gamma}{2}
\sum_{a=1}^{r}z_i^{(a)}z_j^{(a)}
+
\frac{i\gamma}{2}
\sum_{a=1}^{r}\bar z_i^{(a)}\bar z_j^{(a)}
\right].
\]

All encoder, mixer, and output-summation terms enter through local vertex factors. Consequently, \(M_r(G)\) is exactly the partition function of a finite-state replicated spin model on \(G\).

Expanding its edge interactions produces a finite sum indexed by graph-supported interaction patterns. This provides the formal route

\[
\text{cut-phase circuit}
\longrightarrow
\text{replica partition function}
\longrightarrow
\text{subgraph contributions}
\longrightarrow
\text{probability moments}.
\]

At the canonical \(\gamma\), this is a structural expansion rather than a convergent low-order perturbation.

---

## 20. Why regular graphs isolate cycle structure

Let \(T\) be a tree with \(e\) edges, and let \(G\) be \(d\)-regular. Then

\[
\boxed{
\operatorname{hom}(T,G)=n\,d^e.
}
\]

To prove this, root \(T\). The root has \(n\) possible images. Once a parent image is chosen, each child has exactly \(d\) possible adjacent images. Homomorphisms permit collisions among nonadjacent vertices, so no further correction is needed.

Thus all tree homomorphism counts are identical across graphs with fixed \(n\) and \(d\).

More generally, if a connected unicyclic pattern consists of a cycle \(C_\ell\) with rooted trees attached, each attached tree edge contributes a factor \(d\). Its homomorphism count is therefore proportional to

\[
\operatorname{hom}(C_\ell,G)
=
\operatorname{tr}(A^\ell).
\]

This explains why a regular-graph census suppresses degree and tree variation and exposes cyclic structure.

The exact closed-sector expansion gives the clean sequence \(C_3,C_4,C_5\). The broader measured statistics may also receive open-sector and multicyclic contributions, so the observed hierarchy remains an empirical statement about dominance, not an assertion that no other structures occur.

---

## 21. Why the dominant geometry is spectral

The cut-phase expansion and adjacency spectral moments both respond first to short closed structures.

On cubic graphs,

\[
C_3,\ C_4,\ C_5
\]

are completely determined by

\[
\operatorname{tr}(A^3),\
\operatorname{tr}(A^4),\
\operatorname{tr}(A^5).
\]

Therefore, the following empirical observations are mathematically consistent:

- the first principal component of QuIC is strongly predictable from the spectrum;
- triangles, 4-cycles, and 5-cycles are strongly linearly decodable;
- low-order probability moments recover the earliest motifs;
- the global QuIC geometry follows short-cycle variation.

The appropriate interpretation is not that QuIC accidentally reproduces the spectrum. Both representations are responding to the same low-order closed structures.

---

## 22. Why QuIC can retain non-spectral information

The adjacency spectrum aggregates closed walks solely by length:

\[
\operatorname{tr}(A^k).
\]

The boundary-sector expansion retains a finer organization:

\[
F\longmapsto\partial F.
\]

It distinguishes:

- closed even subgraphs;
- pair-boundary paths and joins;
- higher-order \(T\)-join sectors;
- how cycles and paths attach to specified boundaries;
- different signed combinations of multicyclic structures.

The sixth-order diamond split gives one exact example:

\[
\text{spectrum: }C_6+D,
\qquad
\text{closed cut sector: }C_6-D.
\]

The pair-boundary valuation gives another:

\[
\operatorname{val}Z_{G,\{u,v\}}
=
d_G(u,v).
\]

This supports the interpretation:

> The dominant QuIC geometry follows low-order closed structures that are also visible spectrally, while its finer residue can contain boundary-resolved path and incidence information that adjacency eigenvalues aggregate away.

The empirical separation of cospectral graphs and the observed Wiener-index and radius associations are consistent with this mechanism.

---

## 23. Constant-feature message-passing collapse on regular graphs

Consider a message-passing GNN of the form

\[
h_v^{(0)}=h_0
\]

for every vertex, with updates

\[
h_v^{(\ell+1)}
=
\Phi_\ell
\left(
h_v^{(\ell)},
\operatorname{AGG}
\left\{
\Psi_\ell
\left(
h_v^{(\ell)},h_u^{(\ell)}
\right)
:
u\in N(v)
\right\}
\right).
\]

Suppose \(G\) is \(d\)-regular. By induction, all vertices have the same representation at every layer.

At layer zero this holds by assumption. If

\[
h_v^{(\ell)}=h^{(\ell)}
\]

for every \(v\), then each vertex receives the same multiset of \(d\) identical messages. Therefore,

\[
h_v^{(\ell+1)}=h^{(\ell+1)}
\]

for every \(v\), independently of the graph’s adjacency arrangement.

With sum pooling,

\[
h_G
=
\sum_vh_v^{(L)}
=
n\,h^{(L)}.
\]

Thus, for fixed \(n\) and \(d\),

\[
\boxed{
h_G
\text{ is identical for every graph in the census.}
}
\]

This proves the collapse of constant-feature GIN and GCN on the cubic datasets. Random node features and Laplacian positional encodings break the hypothesis and therefore need not collapse.

---

## 24. What is not proved: injectivity after measurement and sorting

The complete pipeline is

\[
G
\longmapsto
|\psi_G\rangle
\longmapsto
p_G
\longmapsto
q_G.
\]

Each arrow after the statevector introduces a quotient.

### Born-map aliasing

Distinct statevectors can have identical measurement probabilities. If

\[
|\psi_H\rangle
=
D|\psi_G\rangle
\]

for a diagonal unitary \(D\), then

\[
|\psi_H(y)|^2=|\psi_G(y)|^2
\]

for every \(y\). Global phase is only the simplest case; coordinate-dependent phases are also erased.

Thus

\[
|\psi_G\rangle\neq|\psi_H\rangle
\]

does not imply

\[
p_G\neq p_H.
\]

### Sorting aliasing

Even when

\[
p_G\neq p_H
\]

as labeled vectors, the sorted representations may coincide if there exists a permutation

\[
\sigma\in S_{2^n}
\]

such that

\[
p_G(y)=p_H(\sigma(y))
\]

for every \(y\).

Therefore, measured injectivity would require proving that, for every pair of nonisomorphic graphs \(G,H\) and every output permutation \(\sigma\), there exists some \(y\) satisfying

\[
|\psi_G(y)|^2
\neq
|\psi_H(\sigma(y))|^2.
\]

This is a uniform anti-aliasing theorem over graph pairs, interference patterns, Born measurement, and arbitrary output permutations. It is not implied by the cut function’s completeness, irrational phase encoding, or statevector-level distinguishability.

The paper should not claim injectivity.

A suitable statement is:

> Across thousands of experimental configurations and millions of evaluated graph instances, we observed no collisions in the sorted QuIC representation under our stated numerical criterion. This provides strong empirical evidence of discriminative capacity, but we do not claim injectivity.

The collision criterion and numerical tolerance should be specified. Exact equality in floating-point arithmetic is not an adequate operational definition.

A corresponding limitations statement is:

> Proving injectivity of the measured representation would require a uniform anti-aliasing result over all nonisomorphic graph pairs, ruling out both phase-equivalent Born distributions and permutation-equivalent probability spectra. Choosing \(\pi\)-irrational rotation angles prevents direct periodic aliasing of distinct integer cut values, but it does not exclude graph-pair-specific interference aliases after mixing, measurement, and sorting.

---

# Recommended formal statement stack

## Proposition 1: Cut-phase identity

For every \(x\in\{0,1\}^n\),

\[
U_E(G,\gamma)|x\rangle
=
e^{-i\gamma m/2}
e^{i\gamma c_G(x)}
|x\rangle.
\]

## Proposition 2: Permutation equivariance

For every vertex permutation \(\pi\),

\[
p_{\pi G}(\pi y)=p_G(y),
\]

and therefore

\[
q_{\pi G}=q_G.
\]

## Proposition 3: Cut-function completeness

The labeled cut function determines the adjacency matrix through

\[
A_{ij}
=
\frac{
c_G(\{i\})+c_G(\{j\})-c_G(\{i,j\})
}{2}.
\]

This proposition should not be linked to a claim of measured injectivity.

## Theorem 4: Boundary-resolved Fourier expansion

For every \(T\subseteq V\),

\[
\widehat f_G(T)
=
e^{i\gamma m/2}
\sum_{\partial F=T}
\cos\left(\frac{\gamma}{2}\right)^{m-|F|}
\left[
-i\sin\left(\frac{\gamma}{2}\right)
\right]^{|F|}.
\]

Equivalently,

\[
\widehat f_G(T)
=
e^{i\gamma m/2}
\cos\left(\frac{\gamma}{2}\right)^m
Z_{G,T}
\left(
-i\tan\frac{\gamma}{2}
\right).
\]

## Corollary 5: Cubic closed-sector coefficients

\[
[z^3]Z_{G,\varnothing}=C_3,
\qquad
[z^4]Z_{G,\varnothing}=C_4,
\qquad
[z^5]Z_{G,\varnothing}=C_5,
\]

and

\[
[z^6]Z_{G,\varnothing}
=
C_6+\binom{C_3}{2}-D.
\]

## Corollary 6: Diamond sign split

\[
Q_6=C_6-D,
\qquad
S_6=C_6+D.
\]

Thus the closed cut sector and adjacency spectrum expose complementary sixth-order combinations.

## Corollary 7: Distance valuation

For every pair \(u,v\),

\[
\operatorname{val}Z_{G,\{u,v\}}
=
d_G(u,v).
\]

## Proposition 8: Constant-feature MPNN collapse

Every permutation-invariant message-passing network initialized with uniform node features produces the same graph embedding for all fixed-\(n\), fixed-\(d\) regular graphs.

---

# Connection between theory and experiments

The mathematical and empirical claims should be paired as follows.

| Mathematical structure | Empirical result |
|---|---|
| Closed-sector coefficients begin with \(C_3,C_4,C_5\) | Triangle–square–pentagon stratified hierarchy |
| \(C_3,C_4,C_5\) are cubic spectral invariants | Dominant spectral PCA component and strong linear probes |
| Probability moments are symmetric compressions of the sorted vector | Purity recovers triangles; additional moments recover \(C_4\); full vector needed for \(C_5\) |
| Sixth cut coefficient contains \(C_6-D\) while spectrum contains \(C_6+D\) | Diamond spectral-residual probe |
| Two-boundary sectors encode pairwise distances | Wiener index and radius appear in the non-spectral residue |
| Constant-feature MPNNs collapse on regular graphs | Exact GIN/GCN representation collapse |
| Born measurement and sorting introduce unresolved aliases | No injectivity claim; empirical noncollision statement |
| Small \(\beta\) exposes finite differences of the cut landscape | Canonical readout emphasizes structured local interference without requiring a small-\(\gamma\) argument |

## Central theoretical claim

> QuIC converts the complete graph cut function into a permutation-invariant quantum interference spectrum. The boundary-resolved Fourier expansion shows that its closed sectors organize cycle structure, while its open sectors encode path and \(T\)-join structure. On cubic graphs, the first closed-sector coefficients are exactly the triangle, square, and pentagon counts, and the sixth coefficient separates 6-cycles and diamonds through a combination complementary to the adjacency spectrum. The experiments show that this structural organization remains visible after fixed-angle mixing, Born measurement, and probability sorting.
