# Quantum Metrology Engine: Ideal State Estimation & Noise Dynamics Simulator

An advanced NumPy/SciPy-based computational simulation framework designed to evaluate parameter-estimation sensitivity, benchmark multi-particle probe architectures, and calculate Quantum Fisher Information (QFI) bounds under ideal and open-system numerical conditions.

The framework implements quantum state-vector and density-matrix representations, unitary parameter encoding, Kraus quantum channels, and generalized mixed-state QFI calculations.

---

## Research Disclaimer & Quantum-Inspired Classical Methodology

**Important Note for Reviewers & Engineers:**

This repository implements a classical numerical simulation of quantum-metrology models. It evaluates theoretical sensitivity scaling, quantum-state evolution, entanglement, and environmental decoherence through explicit state-vector and density-matrix calculations.

Certain computational structures are also discussed through algorithmic analogies to post-silicon electro-optical hardware telemetry and Multi-Layer Perceptron (MLP) architectures.

These analogies describe mathematical and computational similarities only. They do not establish physical equivalence between neural-network operations and quantum-mechanical processes.

The framework does not implement a physical quantum computer or execute quantum circuits on quantum hardware.

---

## 1. Set-Theoretic Foundations: Cantor's Diagonal Argument & State Space Cardinality

The mathematical motivation examines classical and quantum configuration spaces using set theory and Cantor's Diagonalization Theorem.

### 1.1 Classical Configuration Space

For a finite classical register containing \(N\) binary switches, the number of possible configurations is:

$$
|S_{\mathrm{classical}}| = 2^N
$$

For the set of all countably infinite binary sequences, define:

$$
S_{\mathrm{binary}} = \{0,1\}^{\mathbb{N}}
$$

Each infinite binary sequence corresponds to a subset of the natural numbers. Therefore, the configuration space is in bijective correspondence with the power set of the natural numbers:

$$
S_{\mathrm{binary}} \cong \mathcal{P}(\mathbb{N})
$$

Its cardinality is:

$$
|S_{\mathrm{binary}}| = 2^{\aleph_0} = \mathfrak{c}
$$

Here, \(\aleph_0\) denotes the cardinality of the natural numbers, while \(\mathfrak{c}\) denotes the cardinality of the continuum.

The real numbers have the same cardinality:

$$
|\mathbb{R}| = \mathfrak{c} = 2^{\aleph_0}
$$

For every finite integer \(N \geq 1\):

$$
|\mathbb{R}^N| = \mathfrak{c}
$$

Therefore, the space of all countably infinite binary configurations and a finite-dimensional continuous real parameter space have the same cardinality.

### 1.2 Quantum Hilbert-Space Structure

For a register of \(N\) two-level quantum systems (qubits), the composite Hilbert space is:

$$
\mathcal{H}_N = (\mathbb{C}^2)^{\otimes N}
$$

Its complex dimension is:

$$
\dim_{\mathbb{C}}(\mathcal{H}_N) = 2^N
$$

The normalized pure-state space, after identifying physically equivalent global phases, is the complex projective space:

$$
\mathbb{CP}^{2^N-1}
$$

For every finite \(N \geq 1\), the cardinality of this pure-state space is:

$$
|\mathbb{CP}^{2^N-1}| = \mathfrak{c}
$$

Although the Hilbert-space dimension grows exponentially with the number of qubits, the cardinality of the pure-state space remains equal to the continuum for every finite register.

Entanglement changes the structure of quantum correlations and the available state configurations. It does not, by itself, increase the cardinality of a finite-dimensional quantum state space beyond the continuum.

### 1.3 Cantor's Diagonalization Theorem

For any set \(S\), Cantor's theorem establishes that its power set has strictly greater cardinality:

$$
|\mathcal{P}(S)| = 2^{|S|} > |S|
$$

In particular:

$$
2^{\aleph_0} > \aleph_0
$$

and:

$$
2^{\mathfrak{c}} > \mathfrak{c}
$$

However, these results do not establish that the physical state space of a finite-dimensional quantum register has cardinality \(2^{\mathfrak{c}}\).

Such a conclusion would require an independent mathematical proof that the physical quantum state space is in bijective correspondence with the power set of the continuum.

### 1.4 Mathematical Conclusion

The relevant distinction is between cardinality and mathematical structure.

Quantum computational and informational properties must instead be evaluated through:

- Hilbert-space dimensionality.
- Superposition and interference.
- Entanglement and non-classical correlations.
- Measurement statistics.
- State-space geometry.
- Computational representation complexity.

This distinction provides a mathematically consistent foundation for comparing classical information-processing architectures with quantum systems.

---

## 2. Quantum Mechanical Foundational Principles

The engine implements mathematical postulates of non-relativistic quantum mechanics to model idealized quantum-state evolution and measurement.

### 2.1 The State Vector and Hilbert Space

An isolated quantum system is represented by a normalized complex state vector \(|\psi\rangle\) in a complex Hilbert space \(\mathcal{H}\).

The normalization condition is:

$$
\langle\psi|\psi\rangle = 1
$$

For mixed quantum states, the density-matrix representation is used. A valid density matrix satisfies:

$$
\rho = \rho^\dagger
$$

### 2.2 Linear Operators and Physical Observables

Physical observables are represented by linear Hermitian operators:

$$
\hat{O} = \hat{O}^\dagger
$$

According to the spectral theorem, an observable satisfies the eigenvalue equation:

$$
\hat{O}|\phi_n\rangle = \lambda_n|\phi_n\rangle
$$

The corresponding eigenvalues are real:

$$
\lambda_n \in \mathbb{R}
$$

These eigenvalues represent the possible outcomes of measurements of the corresponding observable.

### 2.3 Quantum Measurement and Projection

For a measurement associated with a non-degenerate normalized eigenstate \(|\phi_n\rangle\), the corresponding projection operator is:

$$
\hat{P}_n = |\phi_n\rangle\langle\phi_n|
$$

For a degenerate measurement outcome, the projection operator must project onto the entire corresponding eigenspace.

For a projective measurement, the probability of obtaining outcome \(n\) is:

$$
P(n) = \operatorname{Tr}(\rho\hat{P}_n)
$$

For a pure state:

$$
P(n) = |\langle\phi_n|\psi\rangle|^2
$$

The normalized post-measurement state, conditional on obtaining outcome \(n\) with nonzero probability, is:

$$
\rho_n =
\frac{\hat{P}_n\rho\hat{P}_n}
{\operatorname{Tr}(\rho\hat{P}_n)}
$$

Measurement therefore updates the state according to the measurement outcome and the associated measurement model.

---

## 3. Theoretical & Mathematical Analogy Matrix

The computational architecture can be discussed through mathematical analogies to quantum-state processing.

These correspondences are conceptual and do not imply that classical neural-network operations are physically equivalent to quantum operations.

### 3.1 Ingestion Layer

Raw classical features and processing parameters are mapped into numerical representations corresponding to quantum-state vectors or density matrices:

$$
|\psi\rangle \in \mathcal{H}
$$

or:

$$
\rho \in \mathcal{L}(\mathcal{H})
$$

Here, \(\mathcal{L}(\mathcal{H})\) denotes the space of linear operators acting on the Hilbert space.

### 3.2 Hidden Layer

Linear algebraic transformations can be represented abstractly as linear operators:

$$
|\psi'\rangle = \hat{A}|\psi\rangle
$$

A general linear transformation is not necessarily unitary or physically realizable as a closed-system quantum evolution.

### 3.3 Non-Linear Activation: ReLU

The ReLU activation function is:

$$
\operatorname{ReLU}(x) = \max(0,x)
$$

It acts as a nonlinear numerical truncation operation on real-valued components.

This can be discussed as an algorithmic analogy to filtering or projection, but ReLU is not itself a quantum projection operator.

A quantum projection operator must satisfy:

$$
\hat{P}^2 = \hat{P}
$$

and, for an orthogonal projection:

$$
\hat{P}^\dagger = \hat{P}
$$

### 3.4 Structural Extraction Layer

In quantum mechanics, measurement statistics are obtained from observable operators and the Born rule:

$$
\langle\hat{O}\rangle = \operatorname{Tr}(\rho\hat{O})
$$

The measurement outcomes are associated with the eigenvalues of the observable.

In a classical neural network, the corresponding output layer instead produces numerical predictions according to its implemented activation and output functions.

---

## 4. Architectural Implementation of Time-Variant Dynamics

The engine models continuous temporal evolution governed by a time-independent system Hamiltonian \(\hat{H}\) through two equivalent mathematical representations.

### 4.1 Schrödinger Framework

For a time-independent Hamiltonian, the unitary time-evolution operator is:

$$
\hat{U}(t) =
\exp\left(-\frac{i}{\hbar}\hat{H}t\right)
$$

The operator satisfies the unitarity conditions:

$$
\hat{U}^\dagger(t)\hat{U}(t) = \mathbf{I}
$$

$$
\hat{U}(t)\hat{U}^\dagger(t) = \mathbf{I}
$$

The state vector evolves according to:

$$
|\psi(t)\rangle = \hat{U}(t)|\psi(0)\rangle
$$

The density matrix evolves according to:

$$
\rho(t) =
\hat{U}(t)\rho_0\hat{U}^\dagger(t)
$$

### 4.2 Heisenberg Framework

In the Heisenberg picture, the reference state remains fixed while observables evolve continuously:

$$
\hat{G}(t) =
\hat{U}^\dagger(t)\hat{G}_0\hat{U}(t)
$$

The corresponding Heisenberg equation of motion is:

$$
\frac{d\hat{G}(t)}{dt}
=
\frac{i}{\hbar}[\hat{H},\hat{G}(t)]
+
\left(\frac{\partial\hat{G}}{\partial t}\right)_{\mathrm{explicit}}
$$

The commutator is defined as:

$$
[\hat{A},\hat{B}] = \hat{A}\hat{B} - \hat{B}\hat{A}
$$

### 4.3 Automated Formal Verification

The Schrödinger and Heisenberg pictures must produce identical expectation values:

$$
\operatorname{Tr}[\rho(t)\hat{G}_0]
=
\operatorname{Tr}[\rho_0\hat{G}(t)]
$$

The numerical verification discrepancy is evaluated as:

$$
\epsilon_{\mathrm{verification}}
=
\left|
\operatorname{Tr}[\rho(t)\hat{G}_0]
-
\operatorname{Tr}[\rho_0\hat{G}(t)]
\right|
$$

Under ideal unitary evolution, this discrepancy should approach numerical precision, subject to the stability and conditioning of the numerical implementation.

---

## 5. Open Quantum Systems & Amplitude-Damping Kraus Channel

Physical quantum systems interact with their environments. Environmental coupling can cause decoherence, energy relaxation, and transitions between quantum states.

The framework uses density matrices and completely positive trace-preserving quantum channels to represent non-unitary state evolution.

### 5.1 The Density Matrix Formalism

A mixed quantum state can be represented as a convex combination of pure-state projectors:

$$
\rho = \sum_i p_i|\psi_i\rangle\langle\psi_i|
$$

where:

$$
p_i \geq 0
$$

and:

$$
\sum_i p_i = 1
$$

The density matrix must satisfy three fundamental physical constraints.

**Unit trace:**

$$
\operatorname{Tr}(\rho) = 1
$$

**Hermiticity:**

$$
\rho = \rho^\dagger
$$

**Positive semidefiniteness:**

$$
\langle\phi|\rho|\phi\rangle \geq 0
$$

for every state vector \(|\phi\rangle\).

### 5.2 Lindblad Master Equation

Under the Markovian approximation, the time evolution of a general open quantum system can be described by the Lindblad master equation:

$$
\frac{d\rho}{dt}
=
-\frac{i}{\hbar}[\hat{H},\rho]
+
\mathcal{D}(\rho)
$$

The dissipator is:

$$
\mathcal{D}(\rho)
=
\sum_k
\left(
\hat{L}_k\rho\hat{L}_k^\dagger
-
\frac{1}{2}
\left\{
\hat{L}_k^\dagger\hat{L}_k,\rho
\right\}
\right)
$$

The anticommutator is defined as:

$$
\{A,B\} = AB + BA
$$

The operators \(\hat{L}_k\) describe environmental interaction and dissipative channels.

Their units must be consistent with the time units and rate conventions used in the implementation. In the convention above, the Lindblad operators have units consistent with inverse square root of time.

### 5.3 The Kraus Operator Representation

A completely positive trace-preserving quantum channel is represented by:

$$
\rho_{\mathrm{out}}
=
\mathcal{E}(\rho_{\mathrm{in}})
=
\sum_k E_k\rho_{\mathrm{in}}E_k^\dagger
$$

The Kraus operators must satisfy the completeness relation:

$$
\sum_k E_k^\dagger E_k = \mathbf{I}
$$

This condition guarantees trace preservation.

For a discrete numerical simulation, the completeness relation should be verified at every integration step within an appropriate numerical tolerance.

The Kraus representation is a finite-time quantum-channel description. It is not itself identical to the differential Lindblad master equation, although suitable Kraus maps can represent its finite-time evolution.

### 5.4 Single-Qubit Amplitude-Damping Channel

For a single-qubit amplitude-damping channel with damping probability \(p\), the Kraus operators are:

$$
E_0 =
\begin{pmatrix}
1 & 0 \\
0 & \sqrt{1-p}
\end{pmatrix}
$$

$$
E_1 =
\begin{pmatrix}
0 & \sqrt{p} \\
0 & 0
\end{pmatrix}
$$

where:

$$
0 \leq p \leq 1
$$

Here, the computational basis is taken to be \(\{|0\rangle,|1\rangle\}\), with \(|0\rangle\) the ground state and \(|1\rangle\) the excited state.

The completeness relation becomes:

$$
E_0^\dagger E_0 + E_1^\dagger E_1
=
\mathbf{I}
$$

For independent amplitude-damping channels acting on \(N\) qubits, the global Kraus operators are constructed from tensor products of the corresponding local Kraus operators.

For a local damping channel acting on each qubit, the global operators can be represented as:

$$
E_{\boldsymbol{k}}
=
E_{k_1}\otimes E_{k_2}\otimes\cdots\otimes E_{k_N}
$$

where each index \(k_j\) identifies a local Kraus operator.

### 5.5 Generalized Mixed-State QFI Solver

The framework evaluates parameter-estimation sensitivity using the Quantum Fisher Information (QFI) and the Symmetric Logarithmic Derivative (SLD).

The SLD is defined by:

$$
\frac{\partial\rho_\theta}{\partial\theta}
=
\frac{1}{2}
\left(
L_\theta\rho_\theta
+
\rho_\theta L_\theta
\right)
$$

The Quantum Fisher Information is:

$$
F_Q =
\operatorname{Tr}(\rho_\theta L_\theta^2)
$$

For the spectral decomposition:

$$
\rho_\theta =
\sum_m p_m|\phi_m\rangle\langle\phi_m|
$$

the SLD matrix elements are:

$$
(L_\theta)_{mn}
=
\frac{
2\langle\phi_m|
\partial_\theta\rho_\theta
|\phi_n\rangle
}{
p_m+p_n
}
$$

for eigenvalue pairs satisfying:

$$
p_m+p_n>0
$$

When both eigenvalues are zero, the corresponding SLD component can be set to zero because it does not contribute to the QFI.

The spectral QFI expression is:

$$
F_Q =
\sum_{\substack{m,n\\p_m+p_n>0}}
\frac{
2\left|
\langle\phi_m|
\partial_\theta\rho_\theta
|\phi_n\rangle
\right|^2
}{
p_m+p_n
}
$$

The parameter derivative must be calculated from the complete parameter-dependent evolution.

For a parameter-independent Kraus channel:

$$
\rho_{\mathrm{out}}(\theta)
=
\sum_k E_k
\rho_{\mathrm{in}}(\theta)
E_k^\dagger
$$

the derivative is:

$$
\frac{\partial\rho_{\mathrm{out}}}{\partial\theta}
=
\sum_k E_k
\frac{\partial\rho_{\mathrm{in}}}{\partial\theta}
E_k^\dagger
$$

If the Kraus operators themselves depend on \(\theta\), the full product rule must be applied:

$$
\begin{aligned}
\frac{\partial\rho_{\mathrm{out}}}{\partial\theta}
=
\sum_k \bigg[
&
\frac{\partial E_k}{\partial\theta}
\rho_{\mathrm{in}}E_k^\dagger
\\
&+
E_k
\frac{\partial\rho_{\mathrm{in}}}{\partial\theta}
E_k^\dagger
\\
&+
E_k\rho_{\mathrm{in}}
\frac{\partial E_k^\dagger}{\partial\theta}
\bigg]
\end{aligned}
$$

For unitary parameter encoding with:

$$
U_\theta = e^{-i\theta G}
$$

where \(G\) is a Hermitian generator, the derivative of the encoded state is:

$$
\frac{\partial\rho_\theta}{\partial\theta}
=
-i[G,\rho_\theta]
$$

This formulation avoids assuming that a general noisy evolution can always be described by a single effective unitary generator.

---

## 6. System Execution & Real-World Output Analysis

The framework produces numerical telemetry benchmarks for parameter-estimation sensitivity across discrete simulation time steps.

The following values are the reported benchmark outputs supplied with this documentation. Their numerical equivalence and physical interpretation require independent verification against the executable implementation.

### 6.1 Reported Simulation Output

```text
==============================================================================
     QUANTUM METROLOGY ENGINE: DUAL KRAUS ADJOINT LOCKED MAP
==============================================================================
[+] Active Channels (N): 3 | Hilbert Dimension: 8
[+] Operational Sequence: [Evolution] -> [Parameter Encoding] -> [Kraus Noise]
------------------------------------------------------------------------------
[✓] N=1 Analytical Check at p=0.25:
    Numerical Engine QFI: 0.750000 | Analytical Theory: 0.750000
    Validation Discrepancy Delta: 5.55e-16
------------------------------------------------------------------------------

[ TIME STEP 4 | t = 0.60s | p_damping = 0.0695 ]

 ▪ Product State (|+>^N):
   -> Schrödinger Picture QFI | Ideal: 3.00000 | Noisy: 2.79159
   -> Heisenberg Picture QFI  | Ideal: 3.00000 | Noisy: 2.63902
   [Verification] Ideal picture equivalency delta: 4.441e-16
   [Verification] Noisy picture equivalency delta: 1.526e-01
   [Diagnostics] Reported QFI degradation: 6.95%

 ▪ Entangled GHZ State:
   -> Schrödinger Picture QFI | Ideal: 7.72056 | Noisy: 6.85215
   -> Heisenberg Picture QFI  | Ideal: 7.72056 | Noisy: 6.72649
   [Verification] Ideal picture equivalency delta: 7.105e-15
   [Verification] Noisy picture equivalency delta: 1.257e-01
   [Diagnostics] Reported QFI degradation: 11.25%

==============================================================================
[+] Simulation Complete. Rendering Analytical Graphs...
==============================================================================
```

### 6.2 Generated Analytical Visualization

The simulation is configured to export an analytical visualization of the information-degradation curves.

[Quantum Metrology Framework Analysis](https://github.com/GenaTab1993/Quantum_Metrology_Engine/blob/main/quantum_metrology_dual_adjoint_analysis.png) ([View raw image](https://github.com/GenaTab1993/Quantum_Metrology_Engine/raw/main/quantum_metrology_dual_adjoint_analysis.png))

The expected output filename is:

`quantum_metrology_dual_adjoint_analysis.png`

The image must exist in the repository at the referenced relative path for GitHub to display it.

### 6.3 Non-Commutativity and Numerical Verification

A non-zero discrepancy between the Schrödinger and Heisenberg calculations under noisy evolution requires investigation.

For a quantum channel \(\mathcal{E}\), the corresponding adjoint channel is defined by:

$$
\mathcal{E}^{*}(A)
=
\sum_k E_k^\dagger A E_k
$$

It satisfies the duality relation:

$$
\operatorname{Tr}[A\mathcal{E}(\rho)]
=
\operatorname{Tr}[\mathcal{E}^{*}(A)\rho]
$$

For the same physical parameter-encoding protocol and the same quantum channel, both pictures must reproduce the same expectation values and the same QFI.

A discrepancy between two reported noisy QFI values does not, by itself, prove a physical non-commutativity effect.

It may instead indicate differences in:

- The ordering of unitary evolution and noise.
- The parameter-encoding convention.
- The derivative calculation.
- The adjoint-channel implementation.
- The effective generator used in the QFI calculation.
- Numerical truncation or eigenvalue thresholds.

The noisy-picture discrepancies reported in Section 6.1 should therefore be treated as unresolved numerical diagnostics until the two implementations are verified against the same mathematical channel composition.

---

## 7. Performance Benchmarks & Complexity Profile

### 7.1 Quantitative Matrix Benchmark Summary

**Product Probe Configuration**

The reported ideal QFI is:

$$
F_Q^{\mathrm{ideal}} = 3.00000
$$

The reported noisy QFI is:

$$
F_Q^{\mathrm{noisy}} = 2.79159
$$

The relative information loss, calculated from these values, is:

$$
\Delta F_Q =
\frac{
F_Q^{\mathrm{ideal}}-F_Q^{\mathrm{noisy}}
}{
F_Q^{\mathrm{ideal}}
}
\times 100\%
$$

**Entangled GHZ Probe Configuration**

For a standard three-qubit GHZ probe under the generator:

$$
\hat{G}
=
\frac{1}{2}
\sum_{j=1}^{N}\hat{\sigma}_z^{(j)}
$$

the ideal pure-state QFI is expected to satisfy:

$$
F_Q = N^2
$$

For \(N=3\):

$$
F_Q = 9
$$

The reported ideal value of \(7.72056\) differs from this standard benchmark.

This difference requires examination of the implemented generator normalization, probe preparation, and parameter-encoding convention before the result can be described as standard Heisenberg-limit scaling.

The reported noisy value is:

$$
F_Q^{\mathrm{noisy}} = 6.85215
$$

The reported degradation percentage should be interpreted as a comparison against the reported ideal value, not automatically against the theoretical \(N^2\) benchmark.

### 7.2 Classical Numerical Complexity

For an \(N\)-qubit register, the Hilbert-space dimension is:

$$
d = 2^N
$$

A dense state vector requires memory proportional to:

$$
\mathcal{O}(2^N)
$$

A dense density matrix requires memory proportional to:

$$
\mathcal{O}(4^N)
$$

Dense matrix multiplication and full matrix diagonalization can require computational work proportional to:

$$
\mathcal{O}(d^3)
=
\mathcal{O}(8^N)
$$

These estimates describe dense classical numerical representations. Actual costs depend on matrix structure, sparsity, numerical algorithms, and implementation details.

### 7.3 Native Quantum Hardware Considerations

A physical quantum processor does not generally guarantee constant-time execution.

Its operational cost depends on:

- Circuit depth.
- Gate connectivity and topology.
- Number of measurements and repetitions.
- Gate and measurement error rates.
- Quantum error-correction overhead.
- State-preparation and readout procedures.

Consequently, the classical simulation complexity and physical quantum-hardware execution cost must be evaluated separately.

---

## 8. Setup & Deployment Instructions

### 8.1 Workstation Dependencies

The simulation requires Python and the following scientific computing libraries:

```bash
pip install numpy scipy matplotlib
```

### 8.2 Core Script Execution

Save the main framework script as:

`quantum_metrology.py`

Run the simulation from the working directory:

```bash
python quantum_metrology.py
```

### 8.3 Expected Execution Outputs

Upon successful execution, the script is expected to:

1. Initialize the multi-qubit numerical simulation.
2. Execute ideal and noisy state-evolution calculations.
3. Evaluate the mixed-state Quantum Fisher Information.
4. Perform the single-qubit analytical calibration check.
5. Generate the numerical telemetry logs.
6. Export the analytical visualization:

`quantum_metrology_dual_adjoint_analysis.png`

The visualization is exported to the active working directory.

---

## 9. Scientific Validation Scope & Limitations

The framework is intended as a classical numerical environment for exploring quantum-metrology equations and open-system dynamics.

The following validation stages are important for a complete scientific audit:

- Verification of state normalization and density-matrix positivity.
- Verification of Kraus completeness and trace preservation.
- Comparison of analytical and numerical single-qubit QFI.
- Verification of Schrödinger-Heisenberg expectation-value equivalence.
- Verification of QFI equivalence for identical noisy quantum channels.
- Independent confirmation of the GHZ ideal-QFI benchmark.
- Numerical stability testing across time steps and damping parameters.
- Reproducibility of the exported simulation results.

Reported numerical discrepancies must remain documented until their causes have been identified and resolved.

The distinction between mathematical analogy, numerical simulation, and physical quantum-hardware implementation must be maintained throughout the project.

---

**Developer/Physicist:** Genady Tabachnik  
**Validation Domain:** Post-Silicon Electro-Optical Integration & Open Quantum Systems Simulation  
**Documentation Status:** Revised Theoretical Specification; Numerical Benchmark Equivalence Pending Verification.

---

## License

This project is licensed under the MIT License.
