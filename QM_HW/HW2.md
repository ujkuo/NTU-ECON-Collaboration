# HW2


<style>
p{
line-height:1.7em;
}
.markdown-body >*{
font-family: Georgia;
}
</style>

$$
    %一些我定的command%
                %粗體%
    \newcommand{\b}[1]{\mathbf{#1}}
                %Real Number%
    \newcommand{\r}{\mathbb{R}}
                %R^n%
    \newcommand{\rn}{\mathbb{R}^n}
                %R^m%
    \newcommand{\rm}{\mathbb{R}^m}
                %N%
    \newcommand{\n}{\mathbb{N}}
                %epsilon%
    \newcommand{\e}{\epsilon}
    \newcommand{\ve}{\varepsilon}
                %such that 縮寫，加空格%
    \newcommand{\st}{\quad \text{s.t.} \quad}
                %前後空格的文字%
    \newcommand{\qtext}[1]{\quad \text{#1} \quad}
                %把{A|B}變成 \set{A}{B}%
    \newcommand{\set}[2]{ \left\{ #1 \mid #2 \right\}}
$$


<!-- -------1-1-------------------->
1. Find two converging subsequences of the following sequence.
   * $\{1,-1,1,-1,1,-1,\cdots\}$
   :::info
   solution by 鄭宗弘: 
   Let $\{a_n\}$ represents the presented sequence.
   Then $\{a_{2k-1}\}\to 1$ and $\{a_{2k}\}\to -1$.
   :::

<!-- -------2-1-------------------->
2. Suppose $\{x_n\}$ and $\{y_n\}$ are sequences of real numbers, and $\lim_{n\to \infty}x_{n}=x$ and $\lim_{n\to \infty}y_{n}=y$. Then prove the following results. You need to use "$\epsilon$-$N$" language.

    * $\lim_{n\to \infty}(x_n+y_n)=x+y$
   :::info
   solution by Yu-Chieh Kuo:
   Consider
   \begin{align}
   |(x_n+b_n) - (x+y)| & = |(x_n-x) + (y_n-y)|\\
                      & \leq |(x_n-x)| + |(y_n-y)| \ (\text{By triangle inequality})
   \end{align}
   Since $\lim_{n\to \infty}x_{n}=x$ and $\lim_{n\to \infty}y_{n}=y$, \
   \begin{align}
   \text{for any} \ \e >0, \ \exists N_1, N_2 \in \n \st & n \geq N_1 \implies |x_n-x| < \frac{\e}{2} \\
   & n \geq N_2 \implies |y_n-y| < \frac{\e}{2}
   \end{align}
   Let $N = \max \{N_1, N_2\}$, then we have
   \begin{equation}
   \forall n \geq N \implies |(x_n-x) + (y_n-y)| \leq |(x_n-x)| + |(y_n-y)| < \frac{\e}{2} + \frac{\e}{2} = \e \quad \square
   \end{equation} 
   :::
    <!-- -------2-2-------------------->


    * $\lim_{n\to \infty}(x_ny_n)=xy$
    
   :::info
   solution by Yu-Chieh Kuo:
   Notice that
   \begin{align}
   |x_ny_n -xy| & = |x_ny_n -xy_n +xy_n -xy| \\
                & \leq |x_n-x||y_n| + |y_n-y||x|
   \end{align}
   Choose $C>0$ big enough $\st |y_n| \leq C$, we have $\forall n \in \n \qtext{and} |x| \leq C$. We have
   \begin{equation}
   |x_n-x||y_n| + |y_n-y||x| \leq C|x_n-x| + C|y_n-y|
   \end{equation}
   Therefore, $\forall \e >0 \ \exists N \in \n \st n\geq N \implies |x_n-x|<\frac{\e}{2C} \qtext{and} |y_n-y|<\frac{\e}{2C}$
   $\therefore |x_ny_n - xy| < C\frac{\e}{2C} +C\frac{\e}{2C} = \e$

   :::
   
    <!-- -------2-3----------------- --> 

    * $\lim_{n\to \infty}(\frac1{x_n})=\frac1x$ if $x_n\neq 0$ for all $n$.
   :::info
   solution by 鄭宗弘: 
   Since $x_n\to x$, for $n$ big enough, say $n>M$ for some $M\in\mathbb{N}$, we have $d(x_n,x)<\frac{|x|}2\Rightarrow |x_n|>\frac{|x|}2$.
   Hence, for $n>M$, we have
   $$|\frac1{x_n}-\frac1x|=|\frac{x-x_n}{xx_n}|<|\frac{2}{x^2}||x_n-x|
   $$
   For every $\epsilon>0$, take $N(\epsilon)>M$ be some integer such that $|x_n-x|<|\frac{x^2}{2}|\epsilon$.
   Then, for $n>N(\epsilon)$, it is easy to see that $|\frac1{x_n}-\frac1x|<\epsilon$. Done!
   :::
   
   
<!-- -------3-1----------------- -->
3. Suppose $\{\b{x_k}\}$ and $\{ \b{y_k} \}$ are sequences in $\rn$, and $\{ \beta_k \}$ is a sequence of real numbers (in $\mathbb{R}^1$) and $\b{x_k} \to \b{x}$ and $\b{y_k} \to \b{y}$, and $\beta_k \to \beta$. Show that 
    * $\lim_{k \to \infty} \b{x_k}+\b{y_k}=\b{x}+\b{y}$

   :::info
   solution by 謝秉儒:
   \begin{align}
   \qtext{for} i=1,\dots,n & \qquad  x_{ki} \rightarrow  x_{i},y_{ki}\rightarrow y_i \qtext{-by Thm.9}\\
   & \implies x_{ki}+y_{ki} \rightarrow x_i+y_i \qtext{-by Q2}\\
   & \implies x_k+y_k \rightarrow x+y \qtext{-by Thm.9}
   \end{align}
   :::

    <!-- -------3-2----------------- -->
    * $\lim_{k \to \infty} \b{x_k}\cdot\b{y_k}=\b{x}\cdot\b{y}$

   :::info
   solution by 謝秉儒:
       Similar to Q3.1
   \begin{align}
   \qtext{for} i=1,\dots,n & \qquad  x_{ki} \rightarrow  x_{i},y_{ki}\rightarrow y_i \qtext{-by Thm.9}\\
   & \implies x_{ki} \cdot y_{ki} \rightarrow x_i \cdot y_i \qtext{-by Q2}\\
   & \implies x_k \cdot y_k \rightarrow x \cdot y \qtext{-by Thm.9}
   \end{align}
   
   ---
   Alternative solution by 陳家威
   The question can be written as
   $$
   \begin{align}
   \lim_{k \to \infty}\b{x}_k\cdot\b{y}_k
   &=\lim_{k \to \infty}\sum_{i=1}^n{x_{ik}y_{ik}} \xrightarrow{?} \sum_{i=1}^n {x_i y_i}
   \end{align}
   $$
   Like usual, we first examine the distance between the two element:
   $$
   \begin{align}
   \left| 
       \sum_{i=1}^n {x_{ik}y_{ik}}-\sum_{i=1}^n {x_{i}y_{i}} 
   \right| &=
   \left|
       \sum_{i=1}^n {(x_{ik}y_{ik}-x_{i}y_{i})}
   \right| &\\
   &\le \sum_{i=1}^n {\Bigg| x_{ik}y_{ik}-x_{i}y_{i} \Bigg|} &\text{by triangle ineq.} 
   \end{align}
   $$
   
   We know from Thrm9., since $\{\b{x}_k\}\to \b{x}$, $\{x_{ik}\} \to x_i$, and so does $\{y_{ik}\} \to y_i$. Applying Q2-2, we know $\lim_{k\to \infty}(x_{ik}y_{ik})=x_iy_i$, which means for each $i$, 
   $$
   \forall \e>0\qtext{,}\exists N_i \st |x_{ik}y_{ik}-x_{i}y_{i}|<\frac{\e}{n} \qtext{when} k>N_i
   $$
   
   Therefore, $\forall \e>0$
   $$
   \begin{align}
      \left| 
      \sum_{i=1}^n {x_{ik}y_{ik}}-\sum_{i=1}^n {x_{i}y_{i}} 
    \right| &\le
   \sum_{i=1}^n {\Bigg| x_{ik}y_{ik}-x_{i}y_{i} \Bigg|}\le n\times\frac{\e}{n}=\e \\ \\
   \forall k >\max\{N_1, N_2,\cdots,N_n\}&
   \end{align}
   $$
   which completes our proof of $\lim_{k \to \infty} \b{x_k}\cdot\b{y_k}=\b{x}\cdot\b{y}$
   :::
   


    <!-- -------3-3----------------- -->
    * $\lim_{k \to \infty} \beta_k\b{x_k}=\beta\b{x}$

   :::info
   solution by 謝秉儒:
   \begin{align}
   \qtext{for} i=1,\dots,n & \qquad  \beta_{k} \cdot x_{ki} \rightarrow \beta \cdot x_i \qtext{-by Q2}\\
   & \implies \beta_k \cdot x_k \rightarrow \beta\cdot x \qtext{-by Thm.9}
   \end{align}
   :::

<!-- -------4----------------- -->
4. Suppose $\{ x_n \}$, $\{ y_n \}$, and $\{ z_n \}$ are convergent sequences of real numbers. Let $x_n \to a$, $y_n \to a$, and $x_n \le z_n \le y_n$ for all $n$. Then $z_n \to a$.
    :::warning
    This is called the squeeze theorem, or the sandwich theorem.
    :::
    :::info
    solution by 謝秉儒:
    We know that $\forall\epsilon>0$, we can find $N_1(\epsilon),N_2(\epsilon)$ such that $n>N_1(\epsilon)\implies|x_n-a|<\epsilon$, and $n>N_2(\epsilon)\implies|y_n-a|<\epsilon$ 
    Let $N(\epsilon)=\max\{N_1(\frac\epsilon5),N_2(\frac\epsilon5)\}$. We have
    \begin{align}
    |z_{n}-a| & = |z_n + x_n -x_n +y_n-y_n -a| \leq |x_n-z_n|+|x_n-y_n|+|y_n-a|\\
    & \leq 2|x_n-y_n|+|y_n-a| \leq 2(|x_n-a|+|y_n-a|)+|y_n-a|\\
    & <2(\frac{\e}{5}+\frac{\e}{5})+\frac\e5 = \e
    \end{align}
    By definition, we then have $z_n\to a$.
    :::
    
<!-- -------5----------------- -->
5. Given nonempty subsets $S$ and $T$ of $\mathbb{R}^1$ such that $s \le t$ for every $s \in S$ and every $t \in T$. Then
$$
\inf S \le \inf T
$$

    :::info
    solution by 鄭宗弘:
    By assumption, $s \leq t$, $\forall s \in S$ and $\forall t \in T$. Hence, $\inf S \leq t$ , $\forall t \in T$.
    Therefore $\inf S$ is a lower bound for $T$.
    By the definition of $\inf T$, we have $\inf T \ge \inf S$.

    :::
    :::warning
    In fact, the statement can be stronger
    $$ \sup S\leq\inf T
    $$
    The following is a proof.
    By assumption, for any $s\in S$, we have $s\leq t$ for all $t\in T$. Hence, every $s\in S$ is a lower bound of $T$ and so $s\leq \inf T$ for all $s\in S$. Therefore, $\inf T$ is an upper bound of $S$. In conclusion, $\sup S\leq \inf T$ .
    :::

<!-- -------6----------------- -->
6. Let $(\textbf{S},d)$ be a metric space. A sequence $\{x_n\}_{n=1}^\infty$ in $\textbf{S}$ is convergent if and only if every subsequence of $\{x_n\}_{n=1}^\infty$ is convergent. 
    :::info
    solution by 邴國榮:
    $(\Rightarrow)$
    Let $\{x_n\}_{n=1}^\infty$ in $\textbf{S}$ converges to $\b{p}$, then $\forall \epsilon > 0$, $\exists N(\epsilon) \in \mathbb{N}$ such that $d(x_n,p) < \epsilon$ whenever $n > N$.
    Now consider a subsequence $\{x_{n_k}\}$ of $\{x_n\}_{n=1}^\infty$, it satisfies that ${n_k} \geq k$. 
    For every $\epsilon>0$, it suffices to find $K(\epsilon)$ such that $k>K(\epsilon)\implies d(x_{n_k},p)<\epsilon$
    Let $K(\e)=N(\e)$, we then have
    \begin{align}
    k>K(\e)\implies n_k\geq k>N(\e)\implies d(x_{n_k},p) < \epsilon
    \end{align} 
    By definition, $x_{n_k}\to p$. Done!

    
    $(\Leftarrow)$
    Assume that every subsequence of $\{x_n\}_{n=1}^\infty$ in $\textbf{S}$ converges to $\b{p}$. By definition, since $\{x_n\}_{n=1}^\infty$ is a subsequence of itself, then $\{x_n\}_{n=1}^\infty$ also converges to $\b{p}$.
    :::
    
    ::: warning
    $$
    \forall \e>0, \;\exists N \st d(x_\color{red}k, p) \le \e  \qtext{if} k>N
    $$
    Since $n_k>k$, we also get
    $$
    \forall \e>0, \;\exists N \st d(x_\color{red}{n_k}, p) \le \e  \qtext{if} \color{red}{n_k>k}>N
    $$
    Which can be further written as
            $$
    \forall \e>0, \;\exists k>N \st d(x_{n_k}, p) \le \e  \qtext{if} n_k>k
    $$
    Thus shows that ${x_{n_k}}$ converges.
    :::

<!-- -------7----------------- -->
7. Show that the sup and inf of a set are uniquely determined whenever they exist. 

    :::info
    solution by 鄭宗弘:
    For a set $S$, we shall prove that if $u_1,u_2$ are both supremum of $S$, then $u_1=u_2$.
    Say $u_1,u_2$ are both supremum of $S$, then by definition of supremum, $u_1,u_2\in U(S)$.
    $u_1$ is supremum and $u_2\in U(S)$, by definition of supreum, we have $u_1\leq u_2$. Similarly, $u_2\leq u_1$.
    Therefore, $u_1=u_2$ and so sup is unique.
    Similar argument proves that inf is also unique.
    :::
    
<!-- -------8-a----------------- -->
8. Find the supremum, infimum, maximum, and minimum of the set $X$ in each of the following cases:

    (a) $X=\set{x\in \mathbb{R}}{x=\frac{1}{n}, \quad n=1,2,\cdots}$
    
    :::info
    solution by 陳家威 & Lecture Note:
    (Just an insight) $X=\left\{ 1, \frac{1}{2}, \frac{1}{3}, \cdots  \right\}=\{x_n|n\in\mathbb{N}\}$, where $x_n=\frac1n$.
    
    * max:
        Since $\max{X}=X \cap U(X)$, we first find $U(X)$
        The upper bound, which is defined by
        $$
        U(X)=\set{u \in \r}{ u \ge x ,\quad\forall x \in X}
        $$
        (The result if obvious, but I'll still provide a more careful elaboration.) Note that $x_k$ is decreasing, because
        $$
        \frac{1}{n}-\frac{1}{n+1}=\frac{1}{n(n+1)}>0
        $$
        We know $u\ge x_1=1$. Rewrite the upper bound
        $$
        U(X)=\set{u \in \r}{ u \ge 1}
        $$
        Now, since $\max{X}=X \cap U(X)$, apparantly $\max{X}=1$.
    * sup:
        By **Theorem 1**, if $\max X$ exists, then $\sup X=\max X = 1$
    * min:
        Since $\min{X} = X \cap L(X)$, where
        $L(X)=\set{\ell \in \r}{\ell \le x , \quad \forall x \in X}$. But since $x_k \to 0$ and $x_k$ is decreasing, we get
        $$
        L(X)=\set{\ell \in \r}{\ell \le 0}
        $$
        Now, since $\min X = X \cap L(X)$, there is no intersection, in other words, $X \cap L(X)=\emptyset$. That is, there is no $\min X$
    * inf: 
        There is, however, an infimin $\inf X = 0$.
    :::
    <!-- -------8-b----------------- -->
    (b) $X=\set{x \in \mathbb{R}}{x=1-\frac{1}{n}, \quad n=1,2,\cdots}$
    
    :::info
    solution by 陳家威:
    (Just an insight) $X=\left\{ 0, \frac{1}{2}, \frac{2}{3}, \cdots \right\}$.
    
    The sequence is a simple manipulation (a linear transfrom) of that of (a) ($X_\text{(b)} =1-X_\text{(a)}$), therefore we can easily get:
    * max: (doesn't exist)
    * inf: $0$
    * min: $0$
    * sup: $1$
    :::
    
<!-- -------9----------------- -->
9. For $\{ x_n \}$ in $\mathbb{R}$ with $x_n = n$. Use Definition 9 to show that this sequence does not converge. 
    ::: success
    Negation of convergence(divergence)
    

    $$
    \begin{array}
    ,& &\text{convergence}&&\\
    \exists p \in R ,& \forall \e>0 ,& \exists N \in \n ,&\forall n>N ,& d(x_n, p)<e \\
    &&\text{not convergence}&&\\
    \forall p \in R ,& \exists \e>0 ,& \forall N \in \n ,& \exists n>N ,& d(x_n, p)>\e
    \end{array}
    $$
    直觀文字：(對任何一個點$p$，存在一個半徑$\e$，使得不管從哪一項($N$)作為起點，都可以找到一個在他後面的點($n>N$)，他跟$p$點的距離大於$\e$)
    :::
    :::info
    solution by 鄭宗弘: For any $p\in\mathbb{R}$, take $\epsilon=1$. Then for any $N\in\mathbb{N}$, choose $n=\max\{floor(p)+2,N+1\}$. We have $n>N$ but $d(x_n,p)>\epsilon$.
    Hence, the negation of the sequence converges is proven.
    :::