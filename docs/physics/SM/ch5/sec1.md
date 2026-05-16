## Introduction to Ensembles and the Density Matrix

We don't look at **one** quantum system, but an **ensemble**: a huge number \(\mathcal{N}\) of *identical* systems, all described by the same Hamiltonian (same physics), but not necessarily in the same quantum state.

For the **k-th** system, the wavefunction is \(\psi^k(t)\).

We choose some convenient orthonormal basis of states \(\{\phi_n\}\) (for example, energy eigenstates) and expand each wavefunction in that basis:

\[
\psi^k(t) = \sum_n a_n^{(k)}(t)\,\phi_n
\]

The numbers \(a_n^{(k)}(t)\) are the **probability amplitudes**:

* \(|a_n^{(k)}(t)|^2\) = probability that *system k* is in state \(\phi_n\) at time \(t\),
* and for each system \(k\),
  \[
  \sum_n |a_n^{(k)}(t)|^2 = 1.
  \]

So: each system has its own list of probabilities for being in each state.

### From Amplitudes to the Density Matrix

Now we don't want to track every single system separately. We want a **statistical description of the whole ensemble**.

We introduce the **density operator** \(\hat{\rho}(t)\). In the basis \(\{\phi_n\}\) its matrix elements are

\[
\rho_{mn}(t) = \frac{1}{\mathcal{N}}\sum_{k=1}^{\mathcal{N}} a_m^{(k)}(t)\,a_n^{(k)*}(t).
\]

Interpretation:

* **Diagonal elements** \(\rho_{nn}(t) =\) average of \(|a_n^{(k)}(t)|^2\) over all systems. → Probability that a *randomly chosen* system is in state \(\phi_n\) at time \(t\).

* **Off-diagonal elements** \(\rho_{mn}\) with \(m\neq n\) contain information about **coherence / quantum superposition** between states \(m\) and \(n\).

Normalization:

\[
\sum_n \rho_{nn}(t) = 1 \quad\Longleftrightarrow\quad \mathrm{Tr}(\hat{\rho})=1.
\]

So \(\rho\) is just a fancy way of saying: *"here are the probabilities (and coherences) for different quantum states in the ensemble."*

### Time Evolution of the Density Matrix

Each wavefunction obeys the Schrödinger equation

\[
\hat{H}\,\psi^k(t) = i\hbar\,\frac{\partial}{\partial t}\psi^k(t),
\]

and from that you can derive the equation of motion for \(\rho\):

\[
i\hbar\,\frac{d\hat{\rho}}{dt} = [\hat{H},\hat{\rho}]
\]

This is the **Liouville–von Neumann equation**. It's the quantum analog of the classical Liouville equation.

### Equilibrium (Stationary Ensemble)

If the ensemble is in equilibrium, its statistical properties don't change in time:

\[
\frac{d\hat{\rho}}{dt} = 0.
\]

From the equation of motion, that means

\[
[\hat{H},\hat{\rho}] = 0.
\]

So:

1. \(\hat{\rho}\) must be a function of \(\hat{H}\) (they commute).
2. They can be diagonalized in the **same basis**: take \(\phi_n\) as energy eigenstates
   \[
   \hat{H}\phi_n = E_n \phi_n.
   \]

In that basis,

\[
H_{mn} = E_n\delta_{mn},\qquad \rho_{mn} = \rho_n\,\delta_{mn}.
\]

So in equilibrium the density matrix is **diagonal in the energy basis**. The diagonal entries \(\rho_n\) are simply:

\[
\rho_n = \text{probability the system has energy }E_n.
\]

### Expectation Value of an Observable

Let \(\hat{G}\) be any physical quantity (operator). For the k-th system,

\[
G^{(k)} = \int \psi^{k*}\,\hat{G}\,\psi^k\,d\tau.
\]

The **ensemble average** is

\[
\langle G \rangle = \frac{1}{\mathcal{N}}\sum_{k=1}^{\mathcal{N}} G^{(k)}.
\]

If you rewrite this using the expansion coefficients and \(\rho\), you get the key formula

\[
\boxed{\langle G \rangle = \mathrm{Tr}(\hat{\rho}\,\hat{G})}.
\]

Special case: \(\hat{G} = \hat{I}\) (identity operator):

\[
\mathrm{Tr}(\hat{\rho}) = 1,
\]

which is exactly our normalization of probabilities.

Also, because the **trace is basis-independent**, the expectation value does not depend on which basis \(\{\phi_n\}\) you use.
