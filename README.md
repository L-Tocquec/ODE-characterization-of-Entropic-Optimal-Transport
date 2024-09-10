# **Discrete Optimal Transport**

This notebook is dedicated to the framework of discrete optimal transport, particularly focusing on discrete entropic optimal transport and its convergence towards the original problem.

## Overview

We start by defining two discrete sets \(\mathcal{X}\) and \(\mathcal{Y}\) with cardinalities \(N\) and \(M\), respectively. We also define two measures:

\[
\mu = \sum_{x \in \mathcal{X}} \mu_x \delta_x
\]
\[
\nu = \sum_{y \in \mathcal{Y}} \nu_y \delta_y
\]

where \((\mu_x)_x\) and \((\nu_y)_y\) are weights, and \(\delta_z\) denotes a Dirac mass.

The optimal transport problem and its entropic version are defined as follows:

### Optimal Transport Problem

\[
OT(\mu, \nu) = \inf_{\gamma \in \mathcal{P}} \langle c, \gamma \rangle
\]

### Entropic Optimal Transport Problem

\[
EOT_\epsilon(\mu, \nu) = \inf_{\gamma \in \mathcal{P}} \left(\epsilon \langle c, \gamma \rangle + H(\gamma)\right)
\]

where \(\mathcal{P} \stackrel{\text{def}}{=} \{ z \in \mathbb{R}^{NM} \mid A^t z + b = 0; \; z \succeq 0 \}\) and \(H\) is the Shannon entropy. Moreover:

\[
A^t = \begin{bmatrix}
\mathbb{1}_M^t & 0_M^t & \cdots & 0_M^t \\
0_M^t & \mathbb{1}_M^t & \cdots & 0_M^t \\
\vdots & \vdots & \ddots & \vdots \\
0_M^t & 0_M^t & \cdots & \mathbb{1}_M^t \\
\hline
I_M & I_M & \cdots & I_M
\end{bmatrix} \in \mathbb{R}^{(M+N) \times MN}
\]

and:

\[
b = - \begin{pmatrix}
\mu_{x_1} \\
\vdots \\
\mu_{x_N} \\
\nu_{y_1} \\
\vdots \\
\nu_{y_M}
\end{pmatrix} \in \mathbb{R}^{M+N}
\]

The entropic optimal transport problem admits a unique solution (due to strict convexity and coercivity) that converges to one of the original solutions \(\gamma^*\) as \(\epsilon \to +\infty\).

### Dual Problems

We can also define the dual problems:

\[
\inf_{\psi \in \mathbb{R}^{N+M}} \langle b, \psi \rangle \quad \text{subject to} \quad A \psi \preceq c
\]

\[
\inf_{\psi \in \mathbb{R}^{N+M}} \left( \langle b, \psi \rangle + \sum_{x \in \mathcal{X}, y \in \mathcal{Y}} e^{A_{xy} \psi - \epsilon c_{xy}} \right)
\]

Again, the entropic dual problem has a unique solution \(\psi_\epsilon\) such that \(\psi_\epsilon / \epsilon\) converges to a solution \(\psi^*\) of the original dual problem.
