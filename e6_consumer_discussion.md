## E6 results — the guarded branch, and what the collapse teaches

**The consistency rows certify the run.** The moment column sits at exactly
+1.000 with zero fold variance on C3 and C4 in all four strata, as the
identities tr(A³) = 6·C3 and tr(A⁴) = 8·C4 + 2Σd² − Σd require (the second
pins C4 because Σd² is a stratum constant). The eigenvalue column sits at
+1.000 on spectral gap in all four strata, as any function of the spectrum
must. The integrity gates upstream passed, including the independent
flat-circuit recompute. Every number below is therefore a measurement of
the representation, not of a pipeline defect.

**The pre-registered C5 question is answered on the guarded branch: QuIC
does not beat the spectrum once the C5 identity breaks.** The spectrum
loses its identity off regularity and still linearly decodes C5 at 0.63 to
0.80 across strata (best spectral aggregate 0.712, always the moment
column), while the flat-encoded QuIC probe reaches 0.050 on aggregate and
exceeds 0.28 in no stratum. The loss is not specific to C5. The QuIC
column collapses across the board relative to its cubic-census values:
C3 at 0.443 against 1.000, C4 at 0.085 against 1.000, C5 at 0.050 against
0.982, C6 at 0.053 against 0.642, and Wiener at 0.191 on aggregate. The
concat column tracks the best spectral column almost everywhere (dConcat
between −0.13 and +0.12, median near −0.03), so on these strata the QuIC
block adds essentially nothing to the spectrum under a linear readout.

**The finding is a scope result, and the framework already contains its
mechanism.** Section 20 proves that on a fixed-degree regular census every
tree homomorphism count is the constant n·d^e, so tree and degree
variation are suppressed and cycle structure is the leading varying
content of the cut landscape. That suppression is exactly what these
strata remove. With the degree sequence fixed but the graph nonregular,
the cut landscape's leading variation is degree-arrangement structure
(which vertices of which degree sit adjacent to which), and cycle content
is no longer at the head of the signal that survives mixing, measurement,
and sorting. E6 therefore converts an implicit assumption into an explicit
claim boundary: the decodability results of E1/E2/E5/E7 characterize QuIC
on regular censuses, and the regular census is not incidental to them but
constitutive of them. The theory-to-experiment pairing table gains a row:
Section 20's homomorphism argument pairs with the E6 collapse as its
off-regularity confirmation.

**Three secondary observations, logged as observations.**
First, the collapse follows a max-degree gradient. The QuIC column is
healthiest in the two max-degree-4 strata (S2 decodes C3 at 0.991 and
holds 0.28 to 0.60 on C4/C5/C6/Wiener/gap; S1 is volatile), and it is
essentially dead in the max-degree-5 stratum (S3, no cell above 0.20) and
the max-degree-6 stratum (S4, C3 at 0.378 and little else). The flat
encoder angle 2.875 was tuned against Δ = 3; how far the working point
degrades with Δ is a parameter question this study deliberately does not
pursue.
Second, the only positive dConcat cells in the table are C5 in the two
near-cubic strata (S1 +0.061, S2 +0.118, aggregate +0.035), so QuIC
contributes a small complementary C5 signal precisely where its column
retains life. With five folds and fold sds of 0.03 to 0.05 on those cells,
this is suggestive and is claimed as nothing.
Third, S1 decodes C3 at 0.449 ± 0.714: some folds near-perfect, some at
total failure. The purity-tracks-triangles mechanism was observed at
leading mixer order on cubic graphs, and its off-regularity behavior is
evidently fold-sensitive in a way the framework does not yet explain. The
instability is lemma material and is recorded here for it.

**Limitations of the measurement itself.** The probes measure linear
inaccessibility, not absence: the E5 no-nonlinear-headroom result was
established on the cubic censuses only, so the correct sentence is that
this content is not linearly decodable from the flat-encoded
representation on these strata, with other readouts untested. The flat
encoder is itself a design choice, made so that E6 varies the graphs while
holding the representation identical to the object the cubic experiments
characterize (the canonical degree-proportional encoder reduces to
RX(2.875) on every qubit on cubic graphs, verified bit-identically). A
degree-proportional encoder on these strata is a different object that
injects per-vertex degree as a node feature; whether that injection
restores decodability is a one-line producer revert and a rerun,
