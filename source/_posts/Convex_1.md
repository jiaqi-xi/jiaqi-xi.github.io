---
title: "Convex Optimization(1): Mathematical Backgrounds"
date: 2021-03-26 15:46:00
tags:
	- Convex Optimization
	- Math
categories: 
	- Course Notes
keywords: “Convex Optimization, Math, Course Notes”
cover: https://tva1.sinaimg.cn/large/008eGmZEgy1goxdwelyb7j31900u0kjl.jpg
top_img: https://tva1.sinaimg.cn/large/008eGmZEgy1goxdwelyb7j31900u0kjl.jpg

---

I am taking *Convex Optimization* this semester (2021 Spring). Here is the first chapter of my course notes. The notes are based on my understanding of the course materials provided by Prof. Zhouchen Lin. The notes only offer concise definition and formulas with few proofs and examples. 

# Convex Optimization Notes

Table of Contents:

<!-- toc -->

## Mathematical Backgrounds

### Topology in $\mathbb{R}^n$

-   open, closed, bounded, compact

    -   **Open**: $\forall x\in \mathcal{C}, \exist\epsilon>0, B_{\epsilon}(x)\subseteq C$
    -   Closed: $\mathcal{C}^c$ is open
    -   Bounded: $\exist R>0,\|x\|<R,\forall x\in \mathcal{C}$
    -   Compact: bounded+closed

-   Interior, closure, boundary

    -   **Interior**: $\mathcal{C}^\circ = \{x\mid \exist \epsilon>0, B_{\epsilon}(x)\subseteq \mathcal{C}\}$

        Interior = points that satisfy openness, so interior of open set $\mathcal{C}$ = $\mathcal{C}$ itself.

    -   Closure: $\overline{\mathcal{C}} = \left((\mathcal{C}^c)^\circ\right)^c$

    -   Boundary: $\partial \mathcal{C} = \overline{\mathcal{C}} \backslash \mathcal{C}^\circ$

### Analysis

-   **Accumulation point**

    -   **Def 1**: $\forall \epsilon>0, \exist x\in \{x_k\}, x\in B_\epsilon(x^*)$
    -   Def 2: $x^*$ is a limit of a subsequence

-   Bolzano-Weierstrass theorem

    Any **bounded** sequence in $\mathbb{R}^n$ contains **a convergent subsequence**.

    *Proof. Bounded so we can divide the range in half. There always exists one of the halves that has infinite number of points in it.*

-   Convergence rate

    *When number of operations is infinite, try convergence rate to estimate an optimization algorithm.*

    -   Q-linear

        Assume $x_k\to x^{*}$, then define sequence of **errors**: $e_k = x_k-x^{*}$.

        Sequence $\{x_k\}$ Q-linearly converges to $x^{*}$ with **rate $r$ and rate constant $C$** if
        $$
        \lim_{k\to \infty}\frac{\|e_{k+1}\|}{\|e_k\|^r} = C,C<\infty
        $$

        -   Linear: $r=1, 0<C<1$

            Sublinear: $r=1, C=1$

            Superlinear: $r=1, C=0$

        -   Quadratic: $r=2$

    -   R-linear

        *When* $\lim_{k\to \infty}\frac{\|e_{k+1}\|}{\|e_k\|^r}$ *does not exist, try R-linear definition.*

        Sequence $\{x_k\}$ R-linearly converges to $x^{*}$ when $\|x_k-x^{*}\|\le e_k, \{e_k\}$ converges to $0$ Q-linearly.

-   Continuity

    $x \in \text{dom} f, \forall \epsilon>0, \exist \delta\Rightarrow y\in \text{dom} f, \|\mathbf{y}-\mathbf{x}\|_{2} \leq \delta \Rightarrow\|f(\mathbf{y})-f(\mathbf{x})\|_{2} \leq \varepsilon$

-   Minimum vs Minimal point $x^*$

    -   Minimum: min for all point x
    -   Minimal: min for sufficiently small $\epsilon>0$, $\forall x \in B_\epsilon (x^*)\cup \text{dom} f$

-   Closedness

    -   For each $\alpha \in \mathbb{R}, \{\mathbf{x} \in \operatorname{dom} f \mid f(\mathbf{x}) \leq \alpha\}$ is closed
    -   $\operatorname{epi} f=\left\{(\mathbf{x}, t) \in \mathbb{R}^{n+1} \mid \mathbf{x} \in \operatorname{dom} f, f(\mathbf{x}) \leq t\right\}$ Is closed

    -   Continuous + closed domain = closed function

        Continuous + open domain = closed iff $f\to \infty$ along every sequence converging to a boundary point of domain
### Derivative

If $f:\mathbb{R}^n\to\mathbb{R}^m$, $Df(x)= \mathbf{J}_{m\times n}$ when for all choices of sequence $\{z\}\subset \text{dom} f$, 
$$
\lim _{\mathbf{z} \in \operatorname{dom} f, \mathbf{z} \neq \mathbf{x}, \mathbf{z} \rightarrow \mathbf{x}} \frac{\|f(\mathbf{z})-f(\mathbf{x})-\mathbf{J}(\mathbf{z}-\mathbf{x})\|_{2}}{\|\mathbf{z}-\mathbf{x}\|_{2}}=0
$$
Let $z = x+te_i$ and let $t\to 0$, we have $i$-th column $\frac{\partial f(\mathbf{x})}{\partial x_{i}}$, so
$$
\mathbf{J}=\frac{\partial f(\mathbf{x})}{\partial \mathbf{x}^{T}}=\left(\frac{\partial f_{i}(\mathbf{x})}{\partial x_{j}}\right), 1\le i\le m, 1\le j\le n.
$$

-   Gradient

    1.  If $f:\mathbb{R}^n\to\mathbb{R}$, then $Df(x)$ is a $1\times n$ row vector. We call its **transpose** the gradient of the function:
        $$
        \nabla f(\mathbf{x})=D f(\mathbf{x})^{\top}
        $$
        First-order approximation can thus be:  $f(\mathbf{x})+\langle\nabla f(\mathbf{x}), \mathbf{z}-\mathbf{x}\rangle$.

        Note that **only when $f$ is real-value** will gradient be different from derivative.

        -   Why define gradient?

            Because we normally view a vector as a column vector.

    2.  If $f(\mathbf{X})$ here $\mathbf{X}$ is a matrix, then define $\frac{\partial f}{\partial \mathbf{X}} \triangleq\left(\frac{\partial f(\mathbf{X})}{\partial X_{i j}}\right)$

        More on [matrix calculus](http://www.matrixcalculus.org/).

-   First-order Approximation

    An alternative method of **finding the derivative is by deriving a first-order approximation**:
    $$
    f(\mathbf{z}) = f(\mathbf{x})+Df(\mathbf{x})(\mathbf{z}-\mathbf{x})
    $$
    *Example*: $f(\mathbf{X})=\log \operatorname{det} \mathbf{X}, \text{dom} f = \mathbb{S}^n_{++}$

    Let $\mathbf{Z}$ be close to $\mathbf{X}, \Delta\mathbf{X} = \mathbf{Z}-\mathbf{X}, \lambda_i$ be the $i$-th eigenvalue of $\mathbf{X}^{-1 / 2} \Delta \mathbf{X X}^{-1 / 2}$. Since $\Delta\mathbf{X}$ is close to 0, $\lambda_i$ are also small.

    Lemma: 
    $$
    \text{det}\mathbf{A}\mathbf{B} = \text{det}\mathbf{B}\mathbf{A},\text{tr}\mathbf{A}\mathbf{B} = \text{tr}\mathbf{B}\mathbf{A}\\
     \text{det}\mathbf{A} = \prod_{i=1}^n \lambda_i(\mathbf{A}), \text{tr}\mathbf{A} = \sum_{i=1}^n \lambda_i(\mathbf{A}),\\
     \langle\mathbf{A},\mathbf{B}\rangle = \text{tr}\mathbf{A}^\top\mathbf{B}
    $$
    *(Why $\text{det}\mathbf{A} = \prod_{i=1}^n \lambda_i(\mathbf{A})$? Because $\lambda_i$ = multiple of the basis of eigenvector, $\text{det}$ = multiple of volume)*
    $$
    \begin{aligned} \log \operatorname{det} \mathbf{Z} &=\log \operatorname{det}(\mathbf{X}+\Delta \mathbf{X}) \\ &=\log \operatorname{det}\left(\mathbf{X}^{1 / 2}\left(\mathbf{I}+\mathbf{X}^{-1 / 2} \Delta \mathbf{X} \mathbf{X}^{-1 / 2}\right) \mathbf{X}^{1 / 2}\right) \\ &=\log \operatorname{det} \mathbf{X}+\log \operatorname{det}\left(\mathbf{I}+\mathbf{X}^{-1 / 2} \Delta \mathbf{X} \mathbf{X}^{-1 / 2}\right) \\ &=\log \operatorname{det} \mathbf{X}+\sum_{i=1}^{n} \log \left(1+\lambda_{i}\right) \approx \log \operatorname{det} \mathbf{X}+\sum_{i=1}^{n} \lambda_{i} \\ &=\log \operatorname{det} \mathbf{X}+\operatorname{tr}\left(\mathbf{X}^{-1 / 2} \Delta \mathbf{X X}^{-1 / 2}\right) \\ &=\log \operatorname{det} \mathbf{X}+\operatorname{tr}\left(\mathbf{X}^{-1} \Delta \mathbf{X}\right) \\ &=\log \operatorname{det} \mathbf{X}+\operatorname{tr}\left(\mathbf{X}^{-1}(\mathbf{Z}-\mathbf{X})\right) \end{aligned}
    $$
    Since $\langle \mathbf{A},\mathbf{B}\rangle=\text{tr}(\mathbf{A}^T\mathbf{B})$, $\nabla f(\mathbf{X}) = \mathbf{X}^{-1}$.	$\blacksquare$

-   Chain rule
    $$
    D h(\mathbf{x})=D g(f(\mathbf{x})) D f(\mathbf{x})
    $$
    Remember to take transpose when $f$ is real-valued.

    -   Affine function: $f: \mathbb{R}^{n} \rightarrow \mathbb{R}^m, g: \mathbb{R}^p \rightarrow \mathbb{R}^m, g(\mathbf{x}) = f(\mathbf{Ax+b}), \mathbf{A}\in \mathbb{R^{n\times p}}, \mathbf{b}\in \mathbb{R}^n$
        $$
        D g(\mathbf{x})=D f(\mathbf{Ax+b}) \mathbf{A}\\
        \nabla g(\mathbf{x})=\mathbf{A}^\top\nabla f(\mathbf{Ax+b})
        $$

-   **Understand derivative as a mapping**

    Derivative is basically a mapping of $\Delta x \to \Delta f(x)$. Therefore, chain rule is actually successional mappings.

    Consider $f(\mathbf{x}) = \log \text{det} (\mathbf{F}_0+x_1\mathbf{F}_1+\cdots x_n\mathbf{F}_n)$, if we fix $\mathbf{x}_{-I}$, then we have 2 mappings:

    1.  $x_i \to \mathbf{F}_0+x_1\mathbf{F}_1+\cdots x_n\mathbf{F}_n$

        Mapping of derivative $\mathbb{R}\to \mathbb{R}^{n\times n}$: $x_k\to x_k\mathbf{F}_k$

        Here, $\mathbf{F}_k$ is both the matrix of the mapping and the derivative.

    2.  $\mathbf{M} \to \log \text{det} \mathbf{M}$

        Mapping of derivative $\mathbb{R}^{n\times n}\to \mathbb{R}$: $\mathbf{N} \to \text{tr}(\mathbf{N} \cdot \nabla \log \text{det} \mathbf{N})$

        Here, the derivative size is supposed to be $1\times(n\times n)$, so the mapping matrix cannot be written down. However, we can write out the above mapping.

    By chain rule, **combining these two mappings** and we will have:
    $$
    \frac{\partial f(\mathbf{x})}{x_i} = \text{tr}(\mathbf{F_i}\cdot \nabla \log \text{det}\mathbf{N}) = \text{tr}(\mathbf{F}^{-1}\mathbf{F_i}), \\\mathbf{F}=\mathbf{F}_{0}+x_{1} \mathbf{F}_{1}+\cdots+x_{n} \mathbf{F}_{n}\\
    \Rightarrow \nabla f(\mathbf{x})=\left[\begin{array}{c}\operatorname{tr}\left(\mathbf{F}^{-1} \mathbf{F}_{1}\right) \\ \vdots \\ \operatorname{tr}\left(\mathbf{F}^{-1} \mathbf{F}_{n}\right)\end{array}\right]
    $$

    -   Why we know the second mapping to be $\mathbf{N} \to \text{tr}(\mathbf{N} \cdot \nabla \log \text{det} \mathbf{N})$?

        Back to how we compute the gradient of $f(\mathbf{X})=\log \operatorname{det} \mathbf{X}, \text{dom} f = \mathbb{S}^n_{++}$. We know by first-order approximation that
        $$
        f(\mathbf{z}) = f(\mathbf{x})+Df(\mathbf{x})(\mathbf{z}-\mathbf{x}) = f(\mathbf{x})+ \langle \nabla f(\mathbf{x}), \mathbf{z}-\mathbf{x}\rangle =f(\mathbf{x})+\text{tr}((\mathbf{z}-\mathbf{x})\nabla f(\mathbf{x}))
        $$
        Hence, the derivative is actually a mapping from $\mathbf{z}-\mathbf{x}$ to $f(\mathbf{z}) - f(\mathbf{x}) = \text{tr}((\mathbf{z}-\mathbf{x})\nabla f(\mathbf{x}))$.

### Second derivative

If $f:\mathbb{R}^n\to \mathbb{R}$, then $Df(\mathbf{x}): \mathbb{R}^n\to \mathbb{R}^n$, and $D^2f(\mathbf{x}):\mathbb{R}^n\to \mathbb{R}^{n\times n}$.
$$
D^{2} f(\mathbf{x})=\nabla^{2} f(\mathbf{x})=\frac{\partial(D f(\mathbf{x}))^{T}}{\partial \mathbf{x}^{T}}=\left(\frac{\partial^{2} f(\mathbf{x})}{\partial x_{i} \partial x_{j}}\right)=\mathbf{H}
$$

-   Second-order approximation

    It needs to satisfy:
    $$
    \lim _{\mathbf{z} \in \operatorname{dom} f, \mathbf{z} \neq \mathbf{x}, \mathbf{z} \rightarrow \mathbf{x}} \frac{|f(\mathbf{z})-\hat{f}(\mathbf{z})|}{\|\mathbf{z}-\mathbf{x}\|_{2}^{2}}=0
    $$

    So we have:
    $$
    \hat{f}(\mathbf{z})=f(\mathbf{x})+\nabla f(\mathbf{x})^{\top}(\mathbf{z}-\mathbf{x})+(1 / 2)(\mathbf{z}-\mathbf{x})^{\top} \nabla^{2} f(\mathbf{x})(\mathbf{z}-\mathbf{x}) \\
    =f(\mathbf{x})+D f(\mathbf{x})(\mathbf{z}-\mathbf{x})+\frac{1}{2}\left\langle D^{2} f(\mathbf{x})(\mathbf{z}-\mathbf{x}), \mathbf{z}-\mathbf{x}\right\rangle
    $$

-   Chain rule for second derivative

    -   Scalar function: $f: \mathbb{R}^{n} \rightarrow \mathbb{R}, g: \mathbb{R} \rightarrow \mathbb{R}, h(\mathbf{x}) = g(f(\mathbf{x}))$
        $$
        \nabla^{2} h(\mathbf{x})=g^{\prime}(f(\mathbf{x})) \nabla^{2} f(\mathbf{x})+g^{\prime \prime}(f(\mathbf{x})) \nabla f(\mathbf{x}) \nabla f(\mathbf{x})^{T}
        $$

    -   Affine function: $f: \mathbb{R}^{n} \rightarrow \mathbb{R}, g: \mathbb{R}^m \rightarrow \mathbb{R}, g(\mathbf{x}) = f(\mathbf{Ax+b}), \mathbf{A}\in \mathbb{R^{n\times m}}, \mathbf{b}\in \mathbb{R}^n$
        $$
        \nabla^{2} g(\mathbf{x})=\mathbf{A}^{\top} \nabla^{2} f(\mathbf{A} \mathbf{x}+\mathbf{b}) \mathbf{A}
        $$

### Neural Network

-   Back Propagation

    The error function and layer computation can be written like:
    $$
    \begin{array}{l}e(\mathbf{w}, \mathbf{v}, \mathbf{y})=V\left(\mathbf{y}, \mathbf{x}_{o}\right) \\ x_{i}=\sigma\left(\sum_{j \in \mathrm{pa}(i)} w_{i j} x_{j}\right) = \sigma(a_i)\\
    \frac{\partial V}{\partial w_{i j}}=\frac{\partial V}{\partial a_{i}} \frac{\partial a_{i}}{\partial w_{i j}}=\delta_{i} x_{j}\end{array}
    $$
    
-   Automatic differentiation

    ![image-20210322101810039](https://tva1.sinaimg.cn/large/008eGmZEly1gosgtd742sj315i0eywjb.jpg)

-   Reparameterization trick

    **Case: Parameter of sampling distribution**

    Motivation: How to compute the gradient of $L(\theta)=\mathbb{E}_{z \sim p_{\theta}(z)}[f(z)]$? After sampling $z$, we no longer have $\theta$ in the expression, so back propagation cannot work.

    (Note that no $\theta$ in density function $f(z)$)

    1.  Choose a non-parameterized distribution $q(\epsilon)$ (e.g. standard normal distribution, uniform...) and sample an instance $\epsilon$
    2.  Generate a sample of $z$ by $z=g_\theta(\epsilon)$. The choice of $g_\theta$ should make $z\sim p_\theta(z)$

    Now we have $L(\theta)=\mathbb{E}_{\varepsilon \sim q(\varepsilon)}\left[\tilde{f}_{\theta}(\varepsilon)\right],\tilde{f}_{\theta} = f(g_\theta)$, the sampling will not wipe out $\theta$, then:
    $$
    \frac{\partial L(\theta)}{\partial \theta}=\frac{\partial}{\partial \theta} \mathbb{E}_{\varepsilon \sim q(\varepsilon)}\left[\tilde{f}_{\theta}(\varepsilon)\right]=\mathbb{E}_{\varepsilon \sim q(\varepsilon)}\left[\frac{\partial}{\partial \theta} \tilde{f}_{\theta}(\varepsilon)\right]=\mathbb{E}_{\varepsilon \sim q(\varepsilon)}\left[\frac{\partial f}{\partial g} \frac{\partial g_{\theta}(\varepsilon)}{\partial \theta}\right]
    $$
    ![image-20210323164239610](https://tva1.sinaimg.cn/large/008eGmZEly1gotxjst0wrj30vw0dijt2.jpg)

    *Example: Normal distribution*

    Since we know that $\mathcal{N}\left(z ; \mu, \sigma^{2}\right)=\sigma \mathcal{N}(\varepsilon ; 0,1)+\mu$, we sample $z = \sigma\varepsilon+\mu$ and
    $$
    \mathbb{E}_{z \sim \mathcal{N}\left(z ; \mu, \sigma^{2}\right)}[f(z)]=\mathbb{E}_{\varepsilon \sim \mathcal{N}(\varepsilon ; 0,1)}[f(\sigma \varepsilon+\mu)].
    $$

-   Gumbel-Softmax Trick

    **Case: Taking max**

    Motivation: How to compute the gradient of $L(\theta)=\underset{i}{\operatorname{argmax}}\left\{x_{i}(\theta) \mid i=1, \cdots, K\right\}$?

    Choose $x_i$ deterministically $\to$ Choose (Sample) $x_i$ according to $\pi_{i}=\frac{\exp x_{i}}{\sum_{k=1}^{K} \exp x_{k}}$.

    Since $\mathbf{\pi}$ is a probability distribution, we cannot simply take $\arg\max_i(\pi _i)$ as the result. Instead, we need to add some randomness:
    $$
    z =\text{onehot}\left( \arg\max_i[g_i+\log \pi_i] \right) =\text{onehot}\left( \arg\max_ix_i'\right), g_i\sim \text{Gumbel}(0,1)\\ G\sim -\log(-\log(U)),U\sim \text{Unif}[0,1]
    $$
    Since $\arg\max$ is not differentiable, we use softmax to approximate it:
    $$
    \pi_{\tau, i}^{\prime}=\frac{\exp \left(x_{i}^{\prime} / \tau\right)}{\sum_{k=1}^{K} \exp \left(x_{k}^{\prime} / \tau\right)}
    $$
    Here, $\tau$ is a hyper-parameter called temperature. The smaller $\tau$ is, the closer the softmax approximates one-hot vector.

### Linear Algebra

-   **Symmetric eigenvalue decomposition** (EVD)

    $\mathbf{A}\in \mathbb{S}^n$ Is a real symmetric $n\times n$ matrix, then $\mathbf{A} = \mathbf{Q} \mathbf{\Lambda} \mathbf{Q}^{\top}$. $\mathbf{Q}$ Is orthonormal set of eigenvectors satisfies $\mathbf{Q}^\top \mathbf{Q} =\mathbf{I}$, $\mathbf{\Lambda}=\text{diag}(\lambda_1,\cdots,\lambda_n)$.
    $$
    \operatorname{det} \mathbf{A}=\prod_{i=1}^{n} \lambda_{i}, \operatorname{tr} \mathbf{A}=\sum_{i=1}^{n} \lambda_{i},\|\mathbf{A}\|_{2}={\max|\lambda|},\|\mathbf{A}\|_{F}=\left(\sum_{i=1}^{n} \lambda_{i}^{2}\right)^{1 / 2}
    $$

-   Definiteness

    By definition, the largest and smallest eigenvalues satisfy
    $$
    \lambda_{\max }(\mathbf{A})=\sup _{x \neq 0} \frac{\mathbf{x}^{\top} \mathbf{A} \mathbf{x}}{\mathbf{x}^{\top} \mathbf{x}}, \quad \lambda_{\min }(\mathbf{A})=\inf _{\mathbf{x} \neq 0} \frac{\mathbf{x}^{\top} \mathbf{A} \mathbf{x}}{\mathbf{x}^{\top} \mathbf{x}}\\
    \lambda_{\min }(\mathbf{A})\mathbf{x}^{\top} \mathbf{x}\le\mathbf{x}^{\top} \mathbf{A} \mathbf{x} \le \lambda_{\max }\mathbf{x}^{\top} \mathbf{x}
    $$
    For $\mathbf{A}\in \mathbb{S}^n$, **positive definite** $\mathbf{A} \succ \mathbf{0}$: $\forall \mathbf{x}\ne \mathbf{0}, \mathbf{x}^\top\mathbf{A}\mathbf{x}>0$ $\Leftrightarrow \lambda_\min(\mathbf{A})>0$.
    
-   Symmetric squareroot
    $$
    \mathbf{A}^{1 / 2}=\mathbf{Q} \operatorname{diag}\left(\lambda_{1}^{1 / 2}, \ldots, \lambda_{n}^{1 / 2}\right) \mathbf{Q}^{\top}
    $$
    $\mathbf{A}^{1 / 2}$ Is the unique symmetric positive semidefinite solution of $\mathbf{X}^2 = \mathbf{A}$.

-   SVD

    $\mathbf{A}\in \mathbb{S}^{m\times n}$ Can be factored as $\mathbf{A}=\mathbf{U}\mathbf{\Sigma}\mathbf{V}^\top, \mathbf{\Sigma}=\text{diag}\{\sigma_1,\cdots,\sigma_r\}$.

    $\sigma_i$ of a symmetric matrix = |$\lambda_i\ne 0$|, sorted into descending order

-   Condition number

    Condition number is a measure for the sensitivity of the out-data with respect to perturbations in in-data. 

    For $\mathbf{Ax=b}$, adding perturbations to become $\mathbf{A(x+\delta x)=b+\delta b}$. Since $\|\mathbf{b}\|\le \lambda_\max\|\mathbf{x}\|, \|\delta \mathbf{b}\|\ge \lambda_\min\| \delta\mathbf{x}\|$, we have:
    $$
    {\|\delta \mathbf{x}\| \over \|\mathbf{x}\|} \leq \kappa(\mathbf{A}) {\|\delta \mathbf{b}\| \over
    \|\mathbf{b}\|}
    $$
    Nonsingular (invertible) matrix $\mathbf{A}\in \mathbb{R}^{n\times n}$ has condition number:
    $$
    \operatorname{cond}(\mathbf{A})=\|\mathbf{A}\|_{2}\left\|\mathbf{A}^{-1}\right\|_{2}=\sigma_{\max }(\mathbf{A}) / \sigma_{\min }(\mathbf{A})
    $$

-   Pseudo-inverse
    $$
    \mathbf{A}^{\dagger}=\mathbf{V} \boldsymbol{\Sigma}^{-1} \mathbf{U}^{\top} \in \mathbb{R}^{n \times m}
    $$

-   Adjoint operator

    Given linear operator: $\mathcal{A}:\mathbb{R}^m\to \mathbb{R}^n$, its adjoint operator $\mathcal{A}^*$ satisfies:
    $$
    \left\langle\mathcal{A}^{*}(\mathbf{x}), \mathbf{y}\right\rangle=\langle\mathbf{x}, \mathcal{A}(\mathbf{y})\rangle, \quad \forall \mathbf{x} \in \mathbb{R}^{n}, \mathbf{y} \in \mathbb{R}^{m}
    $$
    *Example*: If $\mathcal{A}^{}(\mathbf{x}) =\mathbf{Ax}$, then $\mathcal{A}^{*}(\mathbf{x}) =\mathbf{A}^\top \mathbf{x}$.

-   Von Neumann trace theorem

    Suppose $\mathbf{A,B}\in \mathbb{R}^{m\times n}$, then:
    $$
    |\langle\mathbf{A}, \mathbf{B}\rangle| \leq \sum_{i=1}^{\min (m, n)} \sigma_{i}(\mathbf{A}) \sigma_{i}(\mathbf{B})
    $$
    When they are both p.s.d. matrices, we have:
    $$
    \sum_{i=1}^{n} \sigma_{i}(\mathbf{A}) \sigma_{n-i+1}(\mathbf{B}) \leq \operatorname{tr}(\mathbf{A B}) \leq \sum_{i=1}^{n} \sigma_{i}(\mathbf{A}) \sigma_{i}(\mathbf{B})
    $$

### Norms

$f:\mathbb{R}^n\to \mathbb{R}$ Is called norm if $f$ is nonnegative, definite($f(\mathbf{x} )=0 \Leftrightarrow \mathbf{x=0}$), homogeneous($f(t\mathbf{x} )=|t|f(\mathbf{x} )$), and satisfies triangle inequality($f(\mathbf{x+y} )\le f(\mathbf{x} )+f(\mathbf{y} )$).

-   Inner product
    $$
    \langle\mathbf{x}, \mathbf{y}\rangle = \mathbf{x}^\top \mathbf{y} \\
    \langle\mathbf{X}, \mathbf{Y}\rangle = \text{tr}\left(\mathbf{X}^\top \mathbf{Y}\right)\\
    $$

-   Unit balls

    If we have a norm $\|\cdot\|$, then the ball is $\mathcal{B} = \{\mathbf{x}\in \mathbb{R}^n\mid \|\mathbf{x}\|\le 1\}$. It is symmetric about the origin, convex, closed, bounded and has nonempty interior.

    If we have a ball $\mathcal{C}$ that satisfies the above properties, it is a unit ball of the norm $\|\mathbf{x}\| = \left(\sup \{t\ge 0\mid t\mathbf{x}\in \mathcal{C}\}\right)^{-1}$.

-   Quadratic norm

    For $\mathbf{P}\in \mathbb{S}_{++}^n$, $\|\mathbf{x}\|_P = (\mathbf{x}^\top \mathbf{P}\mathbf{x})^{1/2} = \|\mathbf{P}^{1/2}\mathbf{x}\|_2$. Its unit ball is an ellipsoid.

-   Equivalence of norms
    $$
    \alpha \|\mathbf{x}\|_a\le \|\mathbf{x}\|_b\le \beta \|\mathbf{x}\|_a, \forall \mathbf{x}\in \mathbb{R}^n
    $$
    This means $\|\cdot\|_a$ and $\|\cdot\|_b$ are equivalent, i.e. they define the same set of open subsets and convergent sequences.

-   Operator/induced norms

    We can induce an operator norm of $\mathbf{X}\in \mathbb{R}^{m\times n}$ with $\|\cdot\|_a$ on $\mathbb{R}^m$ and $\|\cdot\|_b$ on $\mathbb{R}^n$:
    $$
    \|\mathbf{X}\|_{a,b} = \sup \{\|\mathbf{Xu}\|_a\mid \|\mathbf{u}\|_b\le 1\}
    $$

-   Matrix norms
    $$
    \|\mathbf{X}\|_F = \left(\text{tr}\left(\mathbf{X}^\top \mathbf{X}\right)\right)^{1/2}\\
    
    {\displaystyle \|\mathbf{X}\|_{1}=\max _{j}\sum _{i}|x_{ij}|}\\
    
    {\displaystyle \|\mathbf{X}\|_{2}=\sigma _{\max }(\mathbf{X})}\\
    
     \|\mathbf{X}\|_{\infty} = \max_i\sum_{j}|x_{ij}|
    $$

-   Nuclear norm
    $$
    \|\mathbf{A}\|_* = \sum_i\sigma_i(\mathbf{A})\\
    \|\mathbf{X}\|_* = \max_{\mathbf{U}^\top \mathbf{U}=\mathbf{I}\\\mathbf{V}^\top \mathbf{V}=\mathbf{I}} \text{tr}(\mathbf{U}^\top\mathbf{X}\mathbf{V})
    $$
    First, we can prove $\|\mathbf{X}\|_* \ge \text{tr}(\mathbf{U}^\top\mathbf{X}\mathbf{V})$ by Von Neumann trace theorem:
    $$
    \text{tr}(\mathbf{U}^\top\mathbf{X}\mathbf{V}) = \langle \mathbf{X}, \mathbf{U}\mathbf{V}^\top\rangle \le \sum_i\sigma_i(\mathbf{X})\sigma_i(\mathbf{U}\mathbf{I}\mathbf{V}^\top) = \sum_i\sigma_i(\mathbf{X}) = \|\mathbf{X}\|_*
    $$
    Next, when $\mathbf{X}=\mathbf{U}_x\mathbf{\Sigma}_x\mathbf{V}_x^\top$, then take $\mathbf{U}=\mathbf{U}_x, \mathbf{V}=\mathbf{V}_x$, we have the equality:
    $$
    \langle \mathbf{X}, \mathbf{U}\mathbf{V}^\top\rangle =\text{tr}(\mathbf{U}_x^\top\mathbf{X}\mathbf{V}_x) =\text{tr}(\mathbf{\Sigma}_x)= \|\mathbf{X}\|_*
    $$

-   $(p,q)$-norm
    $$
    \|\mathbf{A}\|_{p, q}=\left(\sum_{i=1}^{n}\left\|\mathbf{A}_{i}\right\|_{p}^{q}\right)^{\frac{1}{q}}, \quad  p,q\ge 1
    $$

-   Dual norm

    For norm $\|\cdot\|$, its dual norm is:
    $$
    \|\mathbf{z}\|^* = \sup\{\mathbf{z}^\top \mathbf{x}\mid \|\mathbf{x}\|\le 1\}
    $$
    *Example*:

    -   $\|z\|_2\Leftrightarrow \|z\|_2$: $\|z\|_2^* = \sup_x\{\langle z,x\rangle\mid \|x\|_2\le 1\}$. By Cauchy-Schwartz inequality, $\langle z,x\rangle\le \|x\|_2\|z\|_2\le \|z\|_2$. When $x = \frac{z}{\|z\|_2}$, $\langle z,x\rangle= \|z\|_2$. Hence, $\|z\|_2^* = \|z\|_2$.

    -   $\|z\|_p\Leftrightarrow \|z\|_q$: $\|z\|_p^* = \sup_x\{\langle z,x\rangle\mid \|x\|_p\le 1\},$ by Holder inequality, $\langle z,x\rangle\le \|z\|_q\|x\|_p,\frac{1}{p}+\frac{1}{q}=1$.

    -   $\|z\|_1\Leftrightarrow \|z\|_\infty$: $|\sum_i z_ix_i|\le \sum_i|z_i||x_i|\le \left(\sum_i|x_i|\right) \max_i |z_i| = \|x\|_1\|z\|_\infty$, let $x_i = \text{sgn}(z_i), i=\arg\max_i|z_i|$





