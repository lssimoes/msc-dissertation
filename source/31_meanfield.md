
## Model 1 {#sec:models:model1}
<!-- A Mean Field society model -->

In our first model we are interested in studying the distribution of opinions in a society discussing one issue, the $\zeitgeist$. A possible strategy is to take a society of the agents developed in [@sec:entropicdynamics], recognize relevant information describing the model and proceed with Statistical Mechanics calculations. At some point the calculation might become intractable and one must transition to approximate results and/or computational methods. In this section we develop a Mean Field approach to an specific canonical ensemble of social agents in a noisy society. The work follows closely [@Simoes2018].

To look for the relevant information that describes the model we first look at the Update [@eq:upstudent; @eq:upc]. For simplicity we consider that the description of our "moral space" $\mathbb{R}^K$ is already one that renders the "moral dimensions" independent from one another, and we assume that $\mathbf{C}_n =  \gamma^2_n \mathbb1$. We also assume that, for a certain timescale, the evolution of $\gamma$ is frozen. Hence, the update mechanism is going to be led only by:

$$ \student_{n+1} = \student_n - \nabla_{\student_n} \gamma^2 \log\left[\varepsilon + \left(1 - 2\varepsilon\right) \Phi\left( \tfrac{\sigma h_n}{\gamma} \right)\right] $$ {#eq:upstudentfinal}

Under those circumstances, we assume the term inside the differentiation is relevant and sufficient information to describe the evolution of our system, and we can consider that our society of agents $\{ \studenti \}$ can be described totally by one specific Hamiltonian $\hamiltonian$:

$$  \hamiltonian =  - \gamma^2 \sum_{\langle i,j \rangle} \log \left[ \varepsilon + \left(1 - 2\varepsilon\right) \Phi \left( \frac1\gamma \left( \sigma_i h_j + \sigma_j h_i \right) \right) \right] = \sum_{\langle i,j \rangle} V_{ij} $$ {#eq:hamiltonian1}

\newpage

We can study this society using entropic inference, which lead us to the following canonical (Boltzmann) probability distribution:

<!-- We also suppose that the mean value of this quantity $\left\langle \hamiltonian \right\rangle$ is conserved throughout the configuration evolution of the society, that is, $\hamiltonian$ remains close to some fixed value $E$ of energy but has the possibility of oscillating to higher/lower energy values depending on some "temperature" parameter (which can also be seen as a "social pressure"). In a Maximum Entropy framework, we can say that the probability distribution describing this society with this information paradigm is given by the canonical (Boltzmann) distribution: -->

$$P_B(\{ \student_i \}) = \frac{1}{Z_B} \exp \left( - \beta \hamiltonian\left( \{ \student_i \} \right)\ \right)$$ {#eq:canonicaldistribution}

This description, however, is rather complex depending on the kind of applications we want to follow. A common procedure to simplify our model is to consider a mean field approximation, which projects our solution (the probability distribution $P_B$, which depends on the whole set $\{\student_i\}$ all at once) into a a parametric family of separable probability distributions $P_0 = \Pi_i P_i(\student_i)$ much simpler to work with.

In that case, we do not wish to choose a separable distribution indiscriminately; we want to pick as close as possible the specific $P_0$ which best approximates $P_B$ given the constraints we have assigned to it. That is a calculation we can do maximizing the entropy $S$ (or minimizing the Kullback-Leibler divergence), as follows:

\begin{align}
      S[P_0 || P_B] &= - \iint \left( \prod_{i=1}^N \mathrm{d}\student_i \right) P_0 \log \left( \frac{P_0}{P_B} \right) \\
      &= - \iint \left( \prod_i \mathrm{d}\student_i \right) P_0 \left[ \log \left( Z_B \right) + \beta \hamiltonian+ \log \left(\Pi_i P_i \right) \right] \\
     &= \left\langle \log Z_B  - \beta \hamiltonian- \sum_i \log P_i \right\rangle_{P_0}
\end{align}

We want to find $P_0$ so that variations of $S$ equals to zero, $\delta S = 0$. Usual functional calculus arguments lead to:

$$ \delta S = \int \mathrm{d} J_j\ \delta P_j \left[ \log Z_B + \log P_j + 1 + \beta \sum_{i \in \partial j} \int \mathrm{d}\student_i P_i V_{ij} \right] $$

The desired result can only be obtained for any variation $\delta P_j$ if the term in brackets $\left[ \cdots \right]$ is identically zero itself. We get the following:

$$ P_j(\student_j) = \frac{1}{Z_j} \exp \left( - \beta \sum_{i \in \partial j} \int \mathrm{d}\student_i P_i V_{ij} \right)$$ {#eq:meanfieldexact}

where $Z_j$ is the new partition function/normalization of the model.

\newpage

Inserting back $V_{ij}$ ([@eq:hamiltonian1]):

$$ P_j(\student_j) = \frac{1}{Z_j} \exp \left( \beta \gamma^2 \sum_{i \in \partial j} \int \mathrm{d}\student_i P_i \log \left[ \varepsilon + \left(1 - 2\varepsilon\right) \mathlarger{\Phi} \left( \frac{\sigma_i h_j + \sigma_j h_i}{\gamma} \right) \right] \right) $$ {#eq:meanfieldexact2}

Unfortunately, due to the rather complex form of the potential $V_{ij}$, the integral in [@eq:meanfieldexact2] is intractable. In that case, instead of selecting the best mean field probability distribution family, we are going to choose an approximation with a similar functional form.

Let us consider the fact that in a mean field model agent $j$ does not interact directly with another agent $i$, but only with an external effective field. With that in mind we can approximate the integral over $i$ in [@eq:meanfieldexact2] to $\log\left[ \varepsilon + \left(1 - 2\varepsilon\right) \mathlarger{\Phi} \left( \frac{r h_j + \sigma_j m}{\gamma} \right)\right]$. The sum over neighbors $\partial j$ becomes an effective number of neighbors for agent $j$ that can also be approximated to a constant value $\nu$ throughout society. Although people have different number of peers depending on their sociability, we expect them to have similar values nonetheless.

Taking the logarithm out of the exponential, one obtains:

$$ P_j(\student_j) = \frac{1}{Z_j} \left[ \varepsilon + \left(1 - 2\varepsilon\right) \Phi \left( \frac1\gamma \left( r h_j + m \sigma_j \right) \right) \right]^{\beta \nu \gamma^2} $$

Now one has to interpret the meaning of parameters $m$ and $r$ to proceed. One can see them as parameters that describe the overall behavior of the society, such that one agent $i$ receives signals from its neighbors irrespective of label $i$. In fact, remembering they came from the integral in [@eq:meanfieldexact2], we can see them as expected values over the distribution $P_{\mathrm{MF}}(\student)$

We can represent this self-consistently with the following set of equations to be obeyed:

\begin{align}
    m &= \int \mathrm{d}\student\ h(\student) P_{\mathrm{MF}}(\student) \\
    r &= \int \mathrm{d}\student\ \sign h(\student) P_{\mathrm{MF}}(\student)
\end{align}

And our final mean field probability distribution becomes:

$$ P_{\mathrm{MF}}(\student) = \frac{1}{Z} \left[ \varepsilon + \left(1 - 2\varepsilon\right) \Phi \left( \frac{r}\gamma h(\student) + \frac{m}{\gamma} \sign h(\student) \right) \right]^{\beta \nu \gamma^2} $$ {#eq:meanfieldfinal}

This result does not mean that all the agents are identical, but that they draw their moral vector from the same probability distribution (being held constant parameters $\beta, \varepsilon, \gamma$).

We can also rewrite our order parameters

\begin{align}
    m &= \int \mathrm{d}\student_i h_i P_i = \frac{1}{Z_i} \int \mathrm{d}\student_i h_i \left[ \varepsilon + \left(1 - 2\varepsilon\right)  \Phi \left( \frac1\gamma \left( r h_i + \sigma_i m \right) \right) \right]^{\beta \nu \gamma^2} \\
    \nonumber &= \frac{1}{Z_i} \frac{1}{\sqrt{K}} \int \mathrm{d}\student_i\ \zeitgeist \cdot \student_i \left[ \varepsilon + \left(1 - 2\varepsilon\right)  \Phi \left( \frac1\gamma \left( r \frac{\zeitgeist \cdot \student_i}{\sqrt{K}} + \mathrm{sign} \left( \zeitgeist \cdot \student_i \right)  m \right) \right) \right]^{\beta \nu \gamma^2}
\end{align}

\begin{align}
    r &= \int \mathrm{d}\student_i \sigma_i P_i = \frac{1}{Z_i} \int \mathrm{d}\student_i \sigma_i \left[ \varepsilon + \left(1 - 2\varepsilon\right)  \Phi \left( \frac1\gamma \left( r h_i + \sigma_i m \right) \right) \right]^{\beta \nu \gamma^2} \\
    \nonumber &= \frac{1}{Z_i} \int \mathrm{d}\student_i\ \mathrm{sign} \left( \zeitgeist \cdot \student_i \right) \left[ \varepsilon + \left(1 - 2\varepsilon\right)  \Phi \left( \frac1\gamma \left( r \frac{\zeitgeist \cdot \student_i}{\sqrt{K}} + \mathrm{sign} \left( \zeitgeist \cdot \student_i \right)  m \right) \right) \right]^{\beta \nu \gamma^2}
\end{align}

Since we can always rotate the coordinate system to a given orientation, we choose one in which $\zeitgeist = |\zeitgeist| \hat{\mathrm{e}}_5$, so that $\zeitgeist \cdot \student_i = \sqrt{K} \cos\theta$ and all the other angular integrals are trivial besides the one in $\theta$:

\begin{align}
    \nonumber m &= \frac{1}{\zeta} \int_0^\pi \mathrm{d}\theta \sin^3 \theta \cos\theta\ B(\theta| \varepsilon, \gamma, m, r, \beta\nu)  \\
    r &= \frac{1}{\zeta} \int_0^\pi \mathrm{d}\theta \sin^3 \theta\ \mathrm{sign} \left( \cos\theta \right)\ B(\theta| \varepsilon, \gamma, m, r, \beta\nu) \label{eq:mfeqs} \\
    \nonumber \zeta &= \hspace{4mm}\int_0^\pi \mathrm{d}\theta \sin^3 \theta\ B(\theta| \varepsilon, \gamma, m, r, \beta\nu)
\end{align}

where we implicitly defined the function $B(\theta) \equiv B(\theta| \varepsilon, \gamma, m, r, \beta\nu)$ :

$$ B(\theta) = \left[ \varepsilon + \left(1 - 2\varepsilon\right)  \Phi \left( \frac1\gamma \left( r\cos\theta + \mathrm{sign} \left( \cos\theta \right)  m \right) \right) \right]^{\beta \nu \gamma^2} $$ {#eq:bfunction}

We now proceed to the numerical determination of values of $(m, r, \zeta)$ for each set of parameters $(\varepsilon, \gamma, \beta\nu)$ by integrating [@eq:mfeqs]. We present this in [@sec:results:model1].

\newpage
