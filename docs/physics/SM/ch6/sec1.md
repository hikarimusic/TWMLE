## 1. What system are we talking about?

* We have **N identical, non-interacting particles** (a simple ideal gas).
* They are in a box of volume **V** and together have a fixed total energy **E**.
* That's exactly what a **microcanonical ensemble** is: N, V, E are fixed.

Quantum mechanically, each particle can sit in some **energy level**.
Because there are so many very closely spaced levels, we group them into **"cells"**:

* Cell *i* contains **gᵢ** almost-equal energy levels, all around energy **εᵢ**.
* **nᵢ** is the number of particles in cell *i*.

So:

* Total number of particles: \(\sum_i n_i = N\)
* Total energy:      \(\sum_i n_i \varepsilon_i = E\)

---

## 2. Distributions vs microstates

Two important ideas:

* A **distribution** \(\{n_i\}\) just tells you *how many* particles are in each cell.
* A **microstate** tells you **exactly which level each particle occupies**.

For a given distribution \(\{n_i\}\), there are many possible microstates.
Call that number **W[{nᵢ}]**.

The **total number of allowed microstates** with the given N, V, E is

\[
\Omega(N,V,E) = \sum_{\{n_i\}}' W[\{n_i\}]
\]

(the sum runs over all distributions that satisfy the N and E constraints).

Because different cells are independent, the number of microstates factorizes:

\[
W[\{n_i\}] = \prod_i w(i),
\]

where **w(i)** is the number of microstates inside cell *i*.

So the whole problem becomes:
**How many ways can we put nᵢ particles into gᵢ levels in cell i, depending on the statistics?**

---

## 3. Counting microstates for different statistics

Think "balls into boxes".

### (a) Bosons – Bose–Einstein (BE)

* Particles are **indistinguishable**.
* Any number of particles can occupy the **same level**.

This is "n identical balls into g boxes, no limit per box".
The number of ways is

\[
w_{BE}(i) = \frac{(n_i + g_i - 1)!}{n_i!\,(g_i-1)!}.
\]

So for the whole system:

\[
W_{BE}[\{n_i\}] = \prod_i \frac{(n_i + g_i - 1)!}{n_i!\,(g_i-1)!}.
\]

---

### (b) Fermions – Fermi–Dirac (FD)

* Particles are **indistinguishable**.
* **At most one particle per level** (Pauli principle).

So in cell i we just choose **which nᵢ of the gᵢ levels are occupied**:

\[
w_{FD}(i) = \frac{g_i!}{n_i!\,(g_i - n_i)!}.
\]

So:

\[
W_{FD}[\{n_i\}] = \prod_i \frac{g_i!}{n_i!\,(g_i - n_i)!}.
\]

---

### (c) Classical particles – Maxwell–Boltzmann (MB)

* Particles are treated as **distinguishable** (classical).
* No restriction on how many particles per level.

Naively: each of the nᵢ particles can choose any of the gᵢ levels → \(g_i^{n_i}\) ways.
But this **overcounts** because swapping two identical particles doesn't make a new physical state, so we divide by \(n_i!\) (Gibbs correction):

\[
w_{MB}(i) = \frac{g_i^{n_i}}{n_i!},
\]

so

\[
W_{MB}[\{n_i\}] = \prod_i \frac{g_i^{n_i}}{n_i!}.
\]

---

## 4. Entropy and "most probable" distribution

The **entropy** of the gas in the microcanonical ensemble is

\[
S(N,V,E) = k \ln \Omega(N,V,E) = k \ln \Big[\sum_{\{n_i\}} W[\{n_i\}] \Big].
\]

For a macroscopic system, one distribution \(\{n_i^*\}\) overwhelmingly dominates this sum: the **most probable distribution** (the one with the largest W). Then

\[
S \approx k \ln W[\{n_i^*\}].
\]

So the problem becomes:

> Find the set \(\{n_i^*\}\) that maximizes \(W[\{n_i\}]\)
> subject to \(\sum_i n_i = N\) and \(\sum_i n_i \varepsilon_i = E\).

They do this by:

1. Taking \(\ln W\) (logs turn products into sums).
2. Using Stirling's approximation: \(\ln x! \approx x \ln x - x\) (valid for large x).
3. Introducing Lagrange multipliers **α** and **β** to enforce the constraints.

To treat BE, FD, and MB at once, they introduce a parameter **a**:

* a = −1 → Bose–Einstein
* a = +1 → Fermi–Dirac
* a → 0 → Maxwell–Boltzmann

After the math, maximizing \(\ln W\) gives

\[
\ln\left(\frac{g_i}{n_i^*} - a\right) - \alpha - \beta \varepsilon_i = 0.
\]

Solving for \(n_i^*\):

\[
n_i^* = \frac{g_i}{e^{\alpha + \beta \varepsilon_i} + a}.
\]

This is the **general occupation formula**:

* **Bosons (BE)**: \(a = -1\) ⇒ \(n_i^* = \dfrac{g_i}{e^{\alpha + \beta \varepsilon_i} - 1}\)
* **Fermions (FD)**: \(a = +1\) ⇒ \(n_i^* = \dfrac{g_i}{e^{\alpha + \beta \varepsilon_i} + 1}\)
* **Classical (MB)**: \(a \to 0\) ⇒ \(n_i^* = g_i e^{-\alpha - \beta \varepsilon_i}\)

These are the familiar **Bose-Einstein, Fermi-Dirac, and Maxwell-Boltzmann distributions**.

Physically, \(n_i^*/g_i\) is the **most probable number of particles per single-particle level** at energy εᵢ.

---

## 5. Connecting α and β to thermodynamics

From earlier in the book, they identify

\[
\beta = \frac{1}{kT}, \quad \alpha = -\frac{\mu}{kT},
\]

where **T** is temperature and **μ** is chemical potential.

So the distributions become the usual forms:

* FD: \(n_i^* = \dfrac{g_i}{e^{(\varepsilon_i - \mu)/kT} + 1}\)
* BE: \(n_i^* = \dfrac{g_i}{e^{(\varepsilon_i - \mu)/kT} - 1}\)
* MB: \(n_i^* = g_i e^{-(\varepsilon_i - \mu)/kT}\)

---

## 6. Entropy and pressure

They plug \(n_i^*\) back into the expression for \(\ln W\), and after simplifying get

\[
\frac{S}{k} \approx \sum_i \Big[ n_i^* \ln\Big( \frac{g_i}{n_i^*} - a \Big) + \frac{g_i}{a} \ln\Big(1 - a \frac{n_i^*}{g_i}\Big) \Big].
\]

This can be rewritten as

\[
\frac{S}{k} = \alpha N + \beta E + \frac{1}{a}\sum_i g_i \ln\Big(1 + a e^{-\alpha - \beta \varepsilon_i}\Big).
\]

Using thermodynamics, the combination on the right is related to **PV / kT**, so they arrive at

\[
PV = \frac{kT}{a} \sum_i g_i \ln\Big(1 + a e^{-\alpha - \beta \varepsilon_i}\Big).
\]

This is a **general expression for the pressure** of the gas in terms of the microscopic levels and statistics.

---

## 7. Classical limit → ideal gas law

For the Maxwell–Boltzmann limit (a → 0):

* Use \(\ln(1 + a x) \approx a x\).
* Then

\[
PV = kT \sum_i g_i e^{-\alpha - \beta \varepsilon_i}
= kT \sum_i n_i^*
= NkT.
\]

So you recover the **ideal gas law**

\[
PV = NkT,
\]

which is independent of the details of the energy levels.
