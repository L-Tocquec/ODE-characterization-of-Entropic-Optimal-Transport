# **I - Discrete optimal transport**
This notebook is dedicated to discrete optimal transport framework and particularly to discrete entropic optimal transport and its convergence towards the original problem.

We start by defining two discrete sets $\mathcal{X}$ and $\mathcal{Y}$ of cardinals N and M. We also define two measures:

$\mu = \sum\limits_{x\in \mathcal{X}}\mu_x \delta_x$ and $\nu = \sum\limits_{y\in \mathcal{Y}}\nu_y \delta_y$ where $(\mu_x)_x$ and $(\nu_y)_y$ are weights and $\delta_z$ design a Dirac mass.
The optimal transport problem and its entropic version are defined as:
\begin{align}
  OT(\mu,\nu) &= \inf\limits_{\gamma\in \mathcal{P}} \langle c , \gamma \rangle \\
  EOT_\epsilon (\mu,\nu) &= \inf\limits_{\gamma \in \mathcal{P}} \epsilon \langle  c , \gamma \rangle + H(\gamma)
\end{align}

where $\mathcal{P}\stackrel{\text{def}}{=}\{z \in \mathbb{R}^{NM} \: | \: A^t z + b = 0 \: ;  \: z \succeq 0 \: \}$ and $H$ is the Shannon entropy. Moreover:

$A^t = \begin{bmatrix}
\begin{array}{c|c|c|c|c}
\mathbb{1}_M^t & 0_M^t & 0_M^t & \cdots & 0_M^t \\
0_M^t & \mathbb{1}_M^t & 0_M^t & \cdots & 0_M^t \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
0_M^t & 0_M^t & \cdots & 0_M^t & \mathbb{1}_M^t \\
\hline
I_M & I_M & \cdots & I_M & I_M
\end{array}
\end{bmatrix} \in \mathbb{R}^{(M+N)\times MN}
$

and:

$ b =  - \begin{pmatrix} \mu_{x_1} \\ \cdots \\ \mu_{x_N} \\ \nu_{y_1} \\ \cdots \\ \nu_{y_M} \end{pmatrix}  \in \mathbb{R}^{M+N}$


The entropic optimal transport admits a unique solution (strict convexity + coercivity) that converges towards one of the original solution $\gamma^*$ as $\epsilon$ goes to $+\infty$.

One can also define the dual problems:

\begin{align}
  &\inf\limits_{\psi \in \mathbb{R}^{N+M}} \langle b, \psi \rangle\quad \text{ s.t }\quad A\psi \preceq c \\
  &\inf\limits_{\psi \in \mathbb{R}^{N+M}} \langle b, \psi \rangle + \sum_{x\in \mathcal{X}, y \in \mathcal{Y}} e^{ A_{xy} \psi  - \epsilon c_{xy} }
\end{align}

Another time, the entropic dual admits an unique solution $\psi_\epsilon$ such that $\psi_\epsilon/\epsilon$ converges towards a solution $\psi^*$ of the original dual problem.
