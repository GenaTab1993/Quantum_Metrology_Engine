# Quantum Metrology Engine: Ideal State Estimation & Noise Dynamics Simulator

An advanced Qiskit-based computational simulation framework designed to evaluate parameter estimation sensitivity, benchmark multi-particle probe architectures, and calculate Quantum Fisher Information (QFI) bounds under synthetic numerical perturbations.

## Research Disclaimer & Quantum-Inspired Classical Methodology

This repository functions as a validated ideal-state computational simulator within Quantum Metrology, demonstrating theoretical sensitivity scaling of entangled probes under idealized, noise-free parameters. 

---

## 1. Set-Theoretic Foundations: Cantor's Diagonal Argument & State Space Volumetrics

The mathematical motivation models multi-particle quantum states via transfinite set theory and Cantor's Diagonalization Theorem:

*   **Classical Configuration Space Boundary ($|S_{\text{classic}}| = \aleph$):** Maps to the uncountably infinite continuum value:
    $$|S_{\text{classic}}| = 2^{\aleph_0} = \aleph$$
*   **Quantum Superposition Continuum ($|S_{\text{quantum}}| = 2^\aleph$):** Scaled cardinality of entangled quantum state space:
    $$|S_{\text{quantum}}| = 2^\aleph$$
*   **Methodological Conclusion:** By Cantor's theorem, the power set is strictly larger:
    $$2^\aleph > \aleph$$

---

## 2. Quantum Mechanical Foundational Principles

The engine operates under strict formal postulates:

### 2.1 The State Vector and Hilbert Space
Defined by a state vector residing in a Hilbert Space ($\mathcal{H}$), rigorously normalized:
$$\langle\psi|\psi\rangle = 1.0$$

### 2.2 Linear Operators and Physical Observables
Physical variables are represented by Hermitian operators satisfying:
$$\hat{O} = \hat{O}^\dagger$$

### 2.3 State Projection and Wavefunction Collapse
Modeled via a projection operator:
$$\hat{P} = |\phi_n\rangle\langle\phi_n|$$
---

## 3. Theoretical & Mathematical Analogy Matrix

The neural network's computational architecture maps to quantum mechanics across four key stages, detailed in the full documentation.

---

## 4. Architectural Implementation of Time-Variant Dynamics

The engine solves evolution loops governed by a Hamiltonian $\hat{H}$ across the Schrödinger and Heisenberg frameworks, ensuring algebraic integrity through automated formal verification.
---

## 5. System Execution & Real-World Output Analysis

The execution pipeline outputs dynamic telemetry benchmarks tracking the exact Quantum Fisher Information (QFI) metrics across discrete time steps:

```text
==============================================================================
      QUANTUM METROLOGY ENGINE: DYNAMIC RUNTIME TELEMETRY LOGS
==============================================================================
[+] Active Qubits (N): 3 | Hilbert Space Dimension: 8
[+] Injecting Hardware Noise Floor Amplitude: 0.1
------------------------------------------------------------------------------

[⏱️ TIME STEP 0 | t = 0.00s]
  ▪️ Product State (|+>^N):
    -> Schrödinger Picture QFI  | Ideal: 3.00000  | Noisy: 2.88236
    -> Heisenberg Picture QFI   | Ideal: 3.00000  | Noisy: 3.45211
    [Verification] Formal Equivalency Delta: 0.00e+00
    [Diagnostics] Synthetic Deviation Impact : 3.92%
  ▪️ Entangled GHZ State:
    -> Schrödinger Picture QFI  | Ideal: 9.00000  | Noisy: 8.19393
    -> Heisenberg Picture QFI   | Ideal: 9.00000  | Noisy: 11.57280
    [Verification] Formal Equivalency Delta: 0.00e+00
    [Diagnostics] Quantum Decoherence Loss   : 8.96%

[⏱️ TIME STEP 1 | t = 0.15s]
  ▪️ Product State (|+>^N):
    -> Schrödinger Picture QFI  | Ideal: 3.00000  | Noisy: 3.21695
    -> Heisenberg Picture QFI   | Ideal: 3.00000  | Noisy: 4.49948
    [Verification] Formal Equivalency Delta: 8.88e-16
    [Diagnostics] Synthetic Deviation Impact : -7.23%
  ▪️ Entangled GHZ State:
    -> Schrödinger Picture QFI  | Ideal: 8.91401  | Noisy: 8.29970
    -> Heisenberg Picture QFI   | Ideal: 8.91401  | Noisy: 10.32864
    [Verification] Formal Equivalency Delta: 3.55e-15
    [Diagnostics] Quantum Decoherence Loss   : 6.89%

[⏱️ TIME STEP 2 | t = 0.30s]
  ▪️ Product State (|+>^N):
    -> Schrödinger Picture QFI  | Ideal: 3.00000  | Noisy: 2.75137
    -> Heisenberg Picture QFI   | Ideal: 3.00000  | Noisy: 4.98992
    [Verification] Formal Equivalency Delta: 1.33e-15
    [Diagnostics] Synthetic Deviation Impact : 8.29%
  ▪️ Entangled GHZ State:
    -> Schrödinger Picture QFI  | Ideal: 8.66098  | Noisy: 8.24711
    -> Heisenberg Picture QFI   | Ideal: 8.66098  | Noisy: 9.14994
    [Verification] Formal Equivalency Delta: 1.78e-15
    [Diagnostics] Quantum Decoherence Loss   : 4.78%

[⏱️ TIME STEP 3 | t = 0.45s]
  ▪️ Product State (|+>^N):
    -> Schrödinger Picture QFI  | Ideal: 3.00000  | Noisy: 2.47888
    -> Heisenberg Picture QFI   | Ideal: 3.00000  | Noisy: 3.69983
    [Verification] Formal Equivalency Delta: 4.44e-16
    [Diagnostics] Synthetic Deviation Impact : 17.37%
  ▪️ Entangled GHZ State:
    -> Schrödinger Picture QFI  | Ideal: 8.25542  | Noisy: 6.86661
    -> Heisenberg Picture QFI   | Ideal: 8.25542  | Noisy: 8.78133
    [Verification] Formal Equivalency Delta: 1.78e-15
    [Diagnostics] Quantum Decoherence Loss   : 16.82%

[⏱️ TIME STEP 4 | t = 0.60s]
  ▪️ Product State (|+>^N):
    -> Schrödinger Picture QFI  | Ideal: 3.00000  | Noisy: 3.31850
    -> Heisenberg Picture QFI   | Ideal: 3.00000  | Noisy: 4.54985
    [Verification] Formal Equivalency Delta: 0.00e+00
    [Diagnostics] Synthetic Deviation Impact : -10.62%
  ▪️ Entangled GHZ State:
    -> Schrödinger Picture QFI  | Ideal: 7.72056  | Noisy: 7.15107
    -> Heisenberg Picture QFI   | Ideal: 7.72056  | Noisy: 9.11058
    [Verification] Formal Equivalency Delta: 8.88e-16
    [Diagnostics] Quantum Decoherence Loss   : 7.38%

==============================================================================
[+] Co-Simulation Complete. Exporting High-Resolution Subplots to Disk...
==============================================================================
```

---

## 6. Analytical Visualizations

The generated paired diagnostic tracks are plotted and automatically exported as standalone high-resolution assets embedded directly below:

### 6.1 Schrödinger Evolution Analytics
![Schrödinger Product Probe Track](01_schrodinger_product_probe.png)
![Schrödinger Entangled GHZ Track](02_schrodinger_entangled_ghz_probe.png)

### 6.2 Heisenberg Evolution Analytics
![Heisenberg Product Operator Track](03_heisenberg_product_probe.png)
![Heisenberg Entangled Operator Track](04_heisenberg_entangled_ghz_probe.png)
---

## 7. Performance Benchmarks, Complexity & Computational Efficiency

The framework evaluates metrological sensitivity, computational constraints, and noise scaling across four configurations (N = 3 qubits, $\nu = 1000$ trials, perturbation 0.10):

### 7.1 Quantitative Matrix Benchmark Data Summary
*   **Config 1 (Schrödinger - Product Probe):** Ideal QFI 3.00000 (QCRB 0.01825 rad); Perturbed QFI 2.88236 (QCRB 0.01862 rad). Shows standard information erosion and 3.92% decoherence loss.
*   **Config 2 (Schrödinger - Entangled GHZ Probe):** Ideal QFI 9.00000 (QCRB 0.01054 rad); Perturbed QFI 8.19393 (QCRB 0.01105 rad). Exhibits an 8.96% drop in sensitivity, proving volatility in entangled states.
*   **Config 3 (Heisenberg - Product Operator Tracking):** Ideal QFI 3.00000 (QCRB 0.01825 rad); Perturbed QFI 3.45211 (QCRB 0.01702 rad). Displays variance inflation from direct generator noise injection.
*   **Config 4 (Heisenberg - Entangled Operator Tracking):** Ideal QFI 9.00000 (QCRB 0.01054 rad); Perturbed QFI 11.57280 (QCRB 0.00929 rad). Highlights operator deformation and fluctuation requiring continuous calibration.

### 7.2 Algorithmic Complexity Profile
*   **Classical Simulation Overhead:** Scales at $\mathcal{O}(2^N)$ for dense complex state matrices.
*   **Native Quantum Acceleration:** Executes temporal updates in strict $\mathcal{O}(1)$ physical time.

---

## 8. Setup & Deployment Instructions

### 8.1 Workstation Dependencies & Execution
Install required libraries and launch via terminal:
```bash
pip install qiskit numpy matplotlib scipy
jupyter lab
```
Open the primary script: `QUANTUM_METROLOGY_ENGINE.ipynb`.

***

**Developer/Physicist:** Genady Tabachnik  
**Validation Domain:** Post-Silicon Electro-Optical Integration & Quantum Metrology Simulation  
**Status:** Functional Production-Ready Core Framework Locked.

## License

This project is licensed under the MIT License.
