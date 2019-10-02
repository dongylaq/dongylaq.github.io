# Topological Quantum Computation Reading Group -- Week 1

##Particle Quantum Statistics

### Path Integral and Time Evolution

Let the evolution of state is characterized by the following Schrodinger equation, $i\hbar\partial_t|\psi_t\rangle = H|\psi_t\rangle$. Then, we can define an evolution operator $U(t_2, t_1)$ such that $|\psi_{t_2}\rangle = U(t_2, t_1)|\psi_{t_1}\rangle$. The Schrodinger equation for that operator is $i\hbar\partial_tU(t, t_0) = HU(t, t_0),\ U(t_0, t_0) = \mathrm{id}$. An important observation is that the operator solutions of Schrodinger equation form a group such that $U(t_3, t_2) U(t_2, t_1) = U(t_3, t_1)$.

Write the propagator in terms of position representation $\{|x\rangle: x \in \mathbb{R}^d\}$, the matrix element of it has the following form, refered to path integral.

$$\displaystyle \langle x_f | U(t_f, t_i) | x_i \rangle = \mathcal{N} \sum_{\mathrm{path\ \{x(t) : t \in [t_i, t_f]\}\ connecting (t_i, x_i), (t_f, x_f)}} e^{i S[x(t)] / \hbar}$$

where $\mathcal{N}$ is a normalizer. The additivity of propagator in position representation becomes

$$\displaystyle \left\langle x_{f}\left|\hat{U}\left(t_{f}, t_{i}\right)\right| x_{i}\right\rangle=\int d x_{m}\left\langle x_{f}\left|\hat{U}\left(t_{f}, t_{m}\right)\right| x_{m}\right\rangle\left\langle x_{m}\left|\hat{U}\left(t_{m}, t_{i}\right)\right|  x_{i}\right\rangle$$



### Identical Particles and Configuration Space

Identical particles in quantum mechanics refer to an indistinguishbility, namely, we cannot label those particles and say, for example, specifically one occupies given position. 

>Example (Identical Particles, cf. p31)
>
>Suppose we have two identical particles in a system, there is no meaning to saying that particle one is at position $x_1$ and two is at position $x_2$, interns of ket language $|x_1, x_2\rangle$. We can only say there are particles at both $x_1$ and $x_2$.

For simplicity, we always assume particles cannot overlap, namely, $x_i \neq x_j,\ i \neq j$. Let's define configuration space of $N$ identical particles as $\mathcal{C} = (\mathbb{R}^{Nd} - \Delta) / S_N$, where $\Delta$ is the set that at least two particles occupy the same position and the modulus wrt permutation group $S_N$ stands for the indistinguishability. What we want to know is the equivalent classes, fundamental group, defined on configuration space and their representations to make consistency of composition of propagators.

Let's first rewrite the path integral wrt foundamental group $G$,
$$
\langle x_f | U(t_f, t_i) | x_i \rangle = \mathcal{N} \sum_{g \in G} \rho(g) \sum_{\mathrm{path}_{i\rightarrow f}\in g} e^{i S[\mathrm{path}_{i\rightarrow j}]/\hbar}\label{Eq:PIFG}
$$
where $\rho$ is a representation of $G$. Then, the composition of path integral requires the following identity.
$$
\begin{split}
\sum_{g \in G} \rho(g) \sum_{\mathrm{path}_{i\rightarrow f}\in g} e^{i S[\mathrm{path}_{i\rightarrow j}]/\hbar} &= \int d x_m \left( \sum_{g_1 \in G} \rho(g_1) \sum_{\mathrm{path}_{i\rightarrow m}\in g_1} e^{i S[\mathrm{path}_{i\rightarrow m}]/\hbar} \right)\left( \sum_{g_2 \in G} \rho(g_2) \sum_{\mathrm{path}_{m\rightarrow f}\in g_1} e^{i S[\mathrm{path}_{m\rightarrow j}]/\hbar} \right)\\
&= \int d x_m \sum_{g_1, g_2 \in G} \sum_{\mathrm{path}_{i\rightarrow m} \in g_1} \sum_{\mathrm{path}_{m\rightarrow j} \in g_2} \rho(g_1)\rho(g_2) e^{i S[\mathrm{path}_{i\rightarrow j}]/\hbar}\\
&= \int d x_m \sum_{g_1, g_2 \in G} \sum_{\mathrm{path}_{i\rightarrow m} \in g_1} \sum_{\mathrm{path}_{m\rightarrow j} \in g_2} \rho(g_1g_2) e^{i S[\mathrm{path}_{i\rightarrow j}]/\hbar}
\end{split}
$$
The last equality follows that composing two path segaments in class $g_1$ and $g_2$ results in a longer path in class $g_1 g_2$. That implies that $\rho(g_1 g_2) = \rho(g_1) \rho(g_2)$ which is nothing but the property of a representation.



#### Abelian Representation

Let's first consider the case of one dimensional representation, $\rho : G \rightarrow S^1$. This is called abelian because of the comutativity of complex numbers. We will talk about nonabelian situation in which the representation is matrices which are generally not commutative.

##### 3+1 Dimensions

In 3+1 D, the fundamental group through configuration space is the symmetric group $S_N$, which has *only two possible* 1D representations.

+ Trivial representation: $\rho(g) = 1, \forall g \in G$. This corresponds to bosons.
+ Alternating representation: $\rho(g) = 1\ \mathrm{or}\ -1$ depending on the even or odd number of exchanges. This corresponds to fermions.

##### 2+1 Dimensions

In 2+1 D, the group $G$ is the braid group $B_N$ whose 1D representation is described as $\rho(g) = e^{i \theta W(g)}$, where $\theta$ is a parameter and $W$ is the winding number of braid $g$.

> Definition (Winding Number)
>
> Winding number is a braid invariant, defined as $W = (\# \mathrm{overcrossing}) - (\# \mathrm{undercrossing})$. The convention of crossing is that the clockwise exchange from top view is positive, overcrossing.

Therefore, a clockwise exchange accumulates a phase of $e^{i \theta}$.

+ $\theta = 0$: Bosons.
+ $\theta = \pi$: Fermions.
+ Other value of $\theta$: **Anyons**, fractional statistics



#### Nonabelian Representation

In quantum mechanics, high dimensional representation corresponds to degeneracies. Suppose even for fixed set of position $x$, we have a system still remains a $M$-fold degenerate subspace spaned by $\{|n ; x\rangle : n = 1, \cdots, M \}$. Then, the system state in degenerate subspace can be expressed as a linear combination of those bases, $|\psi\rangle = \sum_n A_n | n; x \rangle$, which means the degenerate system can be characterized by a vector in $\mathbb{C}^M$. Now, the matrix element of propagator indeed depends with degeneracy label $n$, $[\langle x_f | U(t_f, t_i) | x_i \rangle]_{n, n^\prime} = \langle n; x_f | U(t_f, t_i) | n^\prime; x_i\rangle$. Thus, we now have a high dimensional representation of braid group, $\rho : G \rightarrow \mathrm{U}(M)$.

>Definition (Quantum Dimension)
>
>Let M be the size of Hilbert space and N be the number of particles in system. Then, the quantum dimension $d$ is defined as $M \sim d^N$, where $\sim$ means scaling.
