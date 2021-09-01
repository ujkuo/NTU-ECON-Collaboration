# HW3

<style>
p{
line-height:1.7em;
}
.markdown-body >*{
font-family: Georgia;
}
img[alt="mid"]{
max-width:60%;
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

<!-- -------1----------------- -->
1. Let $\{x_n\}$ and $\{y_n\}$ be two bounded sequences in $\r^1$. Let $\{y_n\}$ be that $x_n \leq y_n$ for all n. Prove that
    \begin{equation}
    \liminf_{n \to \infty} x_n \leq \liminf_{n \to \infty} y_n
    \end{equation}
    and
    \begin{equation}
    \limsup_{n \to \infty} x_n \leq \limsup_{n \to \infty} y_n
    \end{equation}
    
    :::warning
    Be careful when refering to the ***comparison property*** in Lecture 2. The following compares the two scenerios:
    ![mid](https://i.imgur.com/0uiWcbk.png)
    In this homework it is the bottom case; not all "x"s are smaller than all "y"s. Only true on same n.
    A visualization is like the image below:
    ![](https://i.imgur.com/MwcvcwO.png)
    
    Clearly, $x_{100}>y_1$, but for the same n, $x_n \le y_n$.
    
    :::
    
    :::info
    solution(a) by 羅偉駿:
    
    Let $a_n^x = \inf\{x_n, x_{n+1},...\} \text{ and } a_n^y = \inf\{y_n, y_{n+1},...\}$
    Goal: $\lim_{n \to \infty} a_n^x \leq \lim_{n \to \infty} a_n^y$ $\implies$ Goal: $\forall n\in\mathbb{N},a_n^x \leq a_n^y$
    Because of the definition of inf, 
    $$\forall n\in\mathbb{N},\forall i\in\mathbb{N}\cup\{0\}, a_n^x \leq x_{n+i}$$
    Since $x_n \leq y_n$ for all $n\in\mathbb{N}$,
    $$
   \forall n\in\mathbb{N},\forall i\in\mathbb{N}\cup\{0\},a_n^x \leq y_{n+i} \\
    \implies \forall n\in\mathbb{N}, a_n^x \in L(\{y_n, y_{n+1},...\}) \\
    \implies \forall n\in\mathbb{N}, a_n^x \leq \inf\{y_n, y_{n+1},...\} = a_n^y
    $$
    According to Theorem 1.8 in Sundaram, $$\lim_{n \to \infty} a_n^x \leq \lim_{n \to \infty} a_n^y$$
    Therefore,
    $$\liminf_{n \to \infty} x_n \leq \liminf_{n \to \infty} y_n.$$
    
    :::
    
    :::info
    solution(b) by 羅偉駿:
        Let $a_n^x = \sup\{x_n, x_{n+1},...\} \text{ and } a_n^y = \sup\{y_n, y_{n+1},...\}$
    Goal: $\lim_{n \to \infty} a_n^x \leq \lim_{n \to \infty} a_n^y$ $\implies$ Goal: $\forall n\in\mathbb{N} ,a_n^x \leq a_n^y$
    Because of the definition of sup, 
    $$\forall n\in\mathbb{N}\forall i\in\mathbb{N}\cup\{0\}, a_n^y \geq y_{n+i}$$
    Since $x_n \leq y_n$ for all $n\in\mathbb{N}$,
    $$
    \forall n\in\mathbb{N},\forall i\in\mathbb{N}\cup\{0\},a_n^y \geq x_{n+i} \\
    \implies \forall n\in\mathbb{N}, a_n^y \in U(\{x_n, x_{n+1},...\}) \\
    \implies \forall n\in\mathbb{N}, a_n^y \geq \sup\{x_n, x_{n+1},...\} = a_n^x
    $$
    According to Theorem 1.8 in Sundaram, $$\lim_{n \to \infty} a_n^x \leq \lim_{n \to \infty} a_n^y$$
    Therefore,
    $$\limsup_{n \to \infty} x_n \leq \limsup_{n \to \infty} y_n.$$
    :::

<!-- -------2----------------- -->
2. Let $\{x_n\}$ and $\{y_n\}$ be two bounded sequences in $\r^1$. Show that
    \begin{equation}
    \liminf_{n \to \infty} (x_n+y_n) \geq \liminf_{n \to \infty} x_n + \liminf_{n \to \infty} y_n
    \end{equation}

    :::info
    solution:
    As the first problem, it suffices to show that for all $n\in \mathbb{N}$, $\inf\{x_n+y_n,x_{n+1}+y_{n+1},\cdots\}\geq \inf\{x_n,x_{n+1},\cdots\}+\inf\{y_n,y_{n+1},\cdots\}$.
    For all $i\in \mathbb{N}\cup\{0\}$,
    $$
    x_{n+i}+y_{n+i}\geq \inf\{x_n,x_{n+1},\cdots\}+\inf\{y_n,y_{n+1},\cdots\}
    $$
    Hence, $\inf\{x_n,x_{n+1},\cdots\}+\inf\{y_n,y_{n+1},\cdots\}$ is a lower bound of $\{x_n+y_n,x_{n+1}+y_{n+1},\cdots\}$. Therefore, $\inf\{x_n+y_n,x_{n+1}+y_{n+1},\cdots\}\geq \inf\{x_n,x_{n+1},\cdots\}+\inf\{y_n,y_{n+1},\cdots\}$ is proven. And so the proposition is proven.
    :::

<!-- -------3----------------- -->
3. Find the $\limsup$ and the $\liminf$
    - $x_k = (-1)^k, \ k=1,2, \ldots$
    - $x_k = (-1)^k + \frac{1}{k}, \ k=1,2, \ldots$

    :::info
    solution:
    Both has $\limsup=1$, and $\liminf=-1$ trivially. However, we would give a proof about why these sequences have no other limits.
    :::

    :::success
    We would like to take the first sequence as example. Suppose $p\in \mathbb{R}$ is a limit point of $\{x_k\}$. There is a subsequence $\{x_{k(n)}\}_n\to p$. Notice that one of $\{n\in\mathbb{N}|k(n) \text{ is odd}\}$ and $\{n\in\mathbb{N}|k(n) \text{ is even}\}$ is infinite.
    If the former is infinite, say $\{n\in\mathbb{N}|k(n) \text{ is odd}\}=\{n_1,n_2,n_3,\cdots\}$ with $n_1<n_2<n_3<\cdots$.
    Then $\{x_{k(n_t)}\}_t$ is a subsequence for both $\{x_{2k-1}\}$ and $\{x_{k(n)}\}$. Noticing that both sequence are convergent, and so the limit of subsequence meets the limit of the two. Hence, the limit of the two sequences must also meet each other. Therefore, $p=-1$.
    If the latter is infinite, then $p=1$ similarly.
    We can do the same trick to the second sequence.
    :::