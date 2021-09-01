# HW6


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
                %Real Number%
    \newcommand{\r}{\mathbb{R}}
                %R^n%
    \newcommand{\rn}{\mathbb{R}^n}
                %N%
    \newcommand{\n}{\mathbb{N}}
                %epsilon%
    \newcommand{\e}{\epsilon}
    \newcommand{\z}{\mathbb{Z}}
    \newcommand{\ve}{\varepsilon}
                %such that 縮寫，加空格%
    \newcommand{\st}{\quad \text{s.t.} \quad}
                %前後空格的文字%
    \newcommand{\qtext}[1]{\quad \text{#1} \quad}
                %把{A|B}變成 \set{A}{B}%
    \newcommand{\set}[3][\mid]{ \left\{ #2 #1 #3 \right\}}
$$

<!---------- 1 ---------->
1. Prove that case of $f(c) < 0$ in Theorem 4.
    ::: info
    solution by 羅偉駿：
    Let $\epsilon = -\frac{f(c)}{2} > 0.$
    Since f is continuous at c,
    $$
    \exists \delta > 0 \text{ s.t. } \forall x \in S, \text{ if } x \in B(c,\delta), \text{ then } f(x) \in B(f(c), \epsilon).
    $$
    
    Let $r = \delta$, then $f(x) \in B(f(c), \epsilon).$
    $$
    \begin{align*}
        &\implies |f(x) - f(c)| < \epsilon \\
        &\implies f(x) < f(c) + \epsilon = f(c) - \frac{f(c)}{2} = \frac{1}{2} f(c) < 0
    \end{align*}
    $$

    :::

2. Suppose $f: \rn \to \r$ is a continuous function. Show that the set $A = \{x \in \rn | f(x) = 0 \}$ is a closed set.
    :::info
    solution by 陳家威：
    By theorem 2, if $f$ is continuous, then we have 
    $$
    \tag{1}
    f(\lim_{n\to\infty} x_n)=\lim_{n\to\infty} f(x_n)
    $$
    for all sequence $\{ x_n \}_{n=1}^\infty$ such that $x_n\in A \to x$.
    
    By definition of $x_n \in A$, $f(x_n)=0$, so $\lim_{n\to\infty}f(x_n)=0$, and since $x_n\to x$, $f(\lim_{n\to\infty} x_n)=f(x)$.
    
    Combining them to equation 1, we have
    $$
        f(x)=f(\lim_{n\to\infty} x_n)=\lim_{n\to\infty} f(x_n) = 0
    $$
    So $x$ is in A since $f(x)=0$. Since for all $x_n \in A$ and $x_n \to x \in A$, we conclude that A is closed by theorem 4 in L5.


    :::


3. Consider a function $f: \r^2 \to \r$ as follows:
    $$
    f(x_1, x_2) = \begin{cases}
    \frac{x_1x_2}{x_1^2 + x_2^2} & \text{if} (x_1, x_2) \neq (0,0) \\
    0 & \text{if} (x_1, x_2) = (0,0)
    \end{cases}
    $$
    Show that $f$ is not continuous at $(0,0)$.
    :::info
    solution by Yu-Chieh Kuo
    
    Consider $g: \r \to \r^2$ as $g(t) = (at, bt)$ , where $(a,b)$ are fixed. 
    Then $\lim _{t \to 0} f(g(t)) = \lim _{(x_1, x_2) \to (0,0)} f(x_1, x_2) = 0$, and $\lim _{t \to 0} f(g(t)) = \frac{ab}{a^2 + b^2}$.
    But $\frac{ab}{a^2 + b^2}$ is dependent on arbitrarily $(a,b)$ instead of being $0$ fixedly. Thus, we can say that $f$ is not continuous at $(0,0)$ since it's limit value is not fixed at $(0,0)$.


    :::
    

4. (Seperately Continuous Function) Consider a function $f : D \subset \r^2 \to \r$, and $D = [0,1] \times [0,1]$ (this means that $x_1 \in [0,1]$ and $x_2 \in [0,1]$.) The function is defined by
    $$
    f(x_1, x_2) = \begin{cases}
    \frac{2x_1}{x_2} & \text{if} \  x_1 \in [0,\frac{x_2}{2}], & x_2 \in (0,1] \\
    2 - \frac{2x_1}{x_2} & \text{if} \  x_1 \in (\frac{x_2}{2}, x_2], & x_2 \in (0,1] \\
    0 & \text{if} \  x_1 \in (x_2, 1], & x_2 \in (0,1] \\
    0 & \text{if} \  x_1 \in [0, 1], & x_2 = 0
    \end{cases}
    $$
- Show that for each fixed value of $x_2 \in [0,1]$, f is continuous as a function of $x_1$ on $[0,1]$.
    :::info
    solution


    :::
- Similarly, show that for each fixed value of $x_1 \in [0,1]$, $f$ is continuous as a function of $x_2$ on $[0,1]$.
    :::info
    solution


    :::
- Show that $f$ is not continuous at $(0,0)$.
    :::info
    solution by 邴國榮
    To show that $f$ is not continuous at $(0,0)$, set two sequences $\{x_{1,n}\}$ and $\{x_{2,n}\}$ where $x_{1,n} \in x_1, x_{2,n} \in x_2$, such that $(x_{1,n}, x_{2,n}) \to (0, 0)$, but $f(x_{1,n},x_{2,n}) \not\to f(0, 0) = 0$.
    Let $x_{1,n} = \frac{x_{2,n}}{4}$ and $x_{2,n} = \frac{1}{n}$, it is  trival that $(x_{1,n}, x_{2,n}) \to (0, 0)$, where $f(x_{1,n},x_{2,n}) \to \frac{1}{2} \text{but not} \ 0.$
    Thus, $f$ is not continuous at $(0,0)$.
    :::

5. Prove the intermediate value theorem (a very important theorem).
    :::info
    solution by Yu-Chieh Kuo
    
    WLOG, we may assume that $f(a) < f(b)$ and $c = 0$. By nested intervals theorem, we have the following cases:
    - Case 1: $f(\frac{a+b}{2}) = 0$, then we find that $x \in [a,b] \st f(x) = 0$.
    - Case 2: $f(\frac{a+b}{2}) < 0$, then let $a_1 = \frac{a+b}{2}, b_1 = b$, and $f(a_1) < 0 < f(b_1)$.
    - Case 3: $f(\frac{a+b}{2}) > 0$, then let $a_1 = a, b_1 = \frac{a+b}{2}$, and $f(a_1) < 0 < f(b_1)$.
    
    Repeating this procedure, we can obtain $[a_n, b_n] \ (n \in \mathbb{N})$ are nested intervals with $f(a_n) < 0 < f(b_n) \ (n \in \mathbb{N})$ and $b_{n+1} - a_{n+1} = \frac{b_n - a_n}{2}$.
    Therefore, $\bigcap _{n=1}^\infty [a_n, b_n] = \{ x \}$ for some $x$.
    Now we should check whether $f(x) = 0$. Assume $f(x)>0, \ \forall \e >0 \ \exists \delta > 0 \st f(\mathcal{B}(x, \delta)) \subseteq \mathcal{B}(f(x), \e)$, and $\mathcal{B}(x, \delta)$ is open. Note that $\mathcal{B}(f(x), \e) \notin \{ 0 \}$. When $\delta$ is sufficiently small, $f(x-\delta) \cdot f(x+\delta)$ should be negative but it contradicts as $f(x) > 0$. Thus, $f(x) = 0$ is proven.

    :::