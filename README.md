# QuIC Characterization

This repository contains the theory, experiments, and artifacts for a study targeting AAAI 2027, built around **QuIC**, a fixed, training-free quantum graph embedding.

QuIC is the object introduced in the IEEE QCE 2026 paper (*QuIC: A Training-Free Quantum Graph Embedding with Large-Scale Hardware Validation*, arXiv:2604.18841). This study asks a different question about the same object: not whether it runs on hardware, but what structural information it encodes, how that information is organized, and how much of it goes beyond classical spectral information.

The work now has two threads.

**Characterizing QuIC itself.** The bulk of the completed experiments — the cycle-count hierarchy, linear decodability, the spectral backbone and its non-spectral residue, the GNN and 2-WL baselines, the cospectral audits — establish what this one fixed circuit encodes and how.

**Generalizing beyond QuIC.** A single fixed circuit is a hard sell to an AI-focused venue on its own: the natural reviewer question is why the community should care what one handcrafted quantum feature map happens to encode. The project's current direction addresses that head-on by reframing the contribution around the *sorted measurement readout* as a general invariant quotient of label-equivariant quantum graph circuits, not QuIC specifically. That reframing is being tested empirically — screening a small family of circuit variants (phase-only and preparation-only controls, QAOA-style preparation, deeper repetitions, alternative mixers) across parameter settings and readout depths, to see which structural signals are QuIC-specific, which are architecture-level, and which are properties of sorting itself.

## Where to look

- **[QuIC Project State](./QuIC_Project_State.md)** — start here. The object definition, the mathematical framework, why the paper's framing has changed, what's proved versus measured, and the current experiment queue for both threads.
- **[QuIC Experimental Results](./QuIC_Experimental_Results.md)** — the full per-experiment write-ups: design, results, what each establishes, and its qualifications, for every experiment run so far.

Both documents are living records and are updated as the project moves.
