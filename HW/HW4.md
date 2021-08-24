# HW4

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
                % 2*2 矩陣懶人%
    \def \m[#1,#2,#3,#4]{\begin{bmatrix} #1 & #2 \\ #3 & #4 \end{bmatrix}}%
                % 垂直向量懶人%
    \def \vv[#1,#2]{\begin{bmatrix}#1 \\ #2\end{bmatrix}}%
                %粗體%
    \newcommand{\b}[1]{\mathbf{#1}}
                %Real Number%
    \newcommand{\r}{\mathbb{R}}
                %Quadratic Form%
    \newcommand{\xAx}[2][x]{  
        \mathbf{#1}^\mathrm{T} #2 \mathbf{#1} }
                %前後空格的文字%
    \newcommand{\qtext}[1]{\quad \text{#1} \quad}
                %把{A|B}變成 \set{A}{B}%
    \newcommand{\set}[2]{ \left\{ #1 \mid #2
    \right\}}
$$

Test command
$$
\b{x}, \r,
\xAx{C}, \xAx[q]{D}
$$
[Simon and Blume](http://www.repetitfind.ru/Literature/subjects/Blume-Mathematics-for-Economists.pdf)

1. (Simon and Blume p597, Q23.8) Find the general solution of the following systems of difference equations:

    ::: spoiler <span style="color:green">(A little sidenote, click and read first if you have no idea where to start)</span>
    ::: success
    solution by 陳家威：
    #### (A little sidenote)
    Before proceeding the questions, let us first construct a procedure and introduce some notations.
    
    A linear **system of difference equation** written in the form:
    \begin{cases}
    \begin{align}
        x_{n+1} &= a_1x_n+b_1y_n  \\
        y_{n+1} &= a_2x_n+b_2y_n
    \end{align}
    \end{cases}
    can be written in the matrix form
    $$
    \tag{1-a} \label{eq:rec_vec}
    \vv[x_{n+1}, y_{n+1}]=\m[a_1,b_1, a_2, b_2]\vv[x_n,y_n]
    $$
    Let $\b{X}_n\equiv\vv[x_n,y_n]$ and $A\equiv\m[a_1,b_1, a_2, b_2]$, we can write $\eqref{eq:rec_vec}$ as
    $$
    \tag{1-b} \label{eq:rec}
    \b{X}_{n+1}=A\b{X}_{n}
    $$
    However, we can recursively subsitude $\b{X}_n$ by $\eqref{eq:rec}$ with its previous term, whence we eventually get
    $$
    \begin{align}
    \b{X}_{n+1} &=A\b{X}_{n} \\
    &=A^2\b{X}_{n-1}\\
    &=A^3\b{X}_{n-2}=\cdots\\
    \tag{2} \label{eq:xnx1}
    &=A^n\b{X}_{1}
    \end{align}
    $$
    Our question now is: how can we calculate $A^n$ easily? The common workaround is to ***diagonalize*** $A$
    $$
    A=P \Lambda P^{-1} \qtext{where} \Lambda = \begin{bmatrix}\lambda_1 & 0 \\ 0 & \lambda_2 \end{bmatrix} %
    \newcommand{\plp}{\,\not{P} \Lambda \not {P^{-1}}}
    $$
    so that 
    $$
    \begin{align}
    A^n &=\overbrace{(P \Lambda \not{P^{-1}})(\plp)\cdots(\plp) \not{P} \Lambda P^{-1}}^n\\
    &= P \Lambda^n P^{-1} \\
    \tag{3}\label{eq:an}
    &= P \m[\lambda_1^n,0,0,\lambda_2^n] P^{-1}
    \end{align}
    $$
    With equation $\eqref{eq:an}$, equation $\eqref{eq:xnx1}$ becomes (after shifting one index)
    $$
    \b{X}_{n}=P\Lambda^n P^{-1} \b{X}_0
    $$
    or
    $$
    \tag{4}
    \vv[x_{n}, y_{n}]=P\Lambda^n P^{-1}\vv[x_0, y_0]
    $$
    The main goal of the following homeworks is to diagonalize the matrix $A$, by finding its eigenvalue.
    
    I will only show the detailed process for 1 and 2; the others I will just provide directly the eigenvalue and eigenvector.
    
    ##### The eigenvector representation-- an alternative form
    > I appreciate 曾玟銨 for suggesting the following. 
    
    Instead of expressing the solution as $\b{X}_{n}=A^n\b{X}_0$, there is another way without explicitly involving the given initial condition $\b{X}_0=\vv[x_0, y_0]$. That is, to express $\b{X}_{n}$ as linear combinations of ***distinct eigenvectors***
    $$
        \b{X}_n = c_1\b{v}_1\lambda_1^n+c_2\b{v}_2\lambda_2^n
    $$
    where $c_1, c_2$ are some coefficients determined by the initial condition $\b{X}_0$.
    
    *proof*:
    Since eigenvectors are distinct (in our case of interest), it spans the whole space and so does on $\b{X}_0$
    $$
        \b{X}_0=c_1\b{v}_1+c_2\b{v}_2
    $$
    Now, 
    $$
    \begin{align}
    \b{X}_1=A\b{X}_0&=A(c_1\b{v}_1+c_2\b{v}_2)\\
    &=c_1A\b{v}_1+c_2A\b{v}_2
    \end{align}
    $$
    However, $\b{v}_1, \b{v}_2$ are eigenvectors of $A$, so by definition we know $A\b{v}_{1}=\lambda_{1}\b{v}_{1}$ and $A\b{v}_{2}=\lambda_{2}\b{v}_{2}$. Hence
    $$
    \b{X}_1=c_1\lambda_1\b{v}_1+c_2\lambda_2\b{v}_2
    $$
    Continue the iteration, we'll eventually end up with 
    $$
    \b{X}_n = c_1\b{v}_1\lambda_1^n+c_2\b{v}_2\lambda_2^n
    $$
    Q.E.D
    :::

* 
    \begin{cases}
    \begin{align}
    x_{n+1} &= 3x_n  \\
    y_{n+1} &= x_n + 2 y_n
    \end{align}
    \end{cases}

    ::: info
    solution:
    $A=\m[3,0,1,2]$. We solve the eigenvalue by solving
    $$
    \det(A-\lambda I)=\det\left(\m[3-\lambda, 0, 1, 2-\lambda]\right)=0
    $$
    Which gives us $(\lambda-2)(\lambda-3)=0 \implies \lambda=2 \qtext{or} 3$
    
    Each eigenvalue corresponds to an eigenvector *(when distinct, or else you might want to find generalized eigenvectors and a [Jordan Form](https://en.wikipedia.org/wiki/Jordan_normal_form) instead)*
    
    When $\lambda = 2$:
    $$
    \begin{align}
    (A-2I)\b{v}_2 &= 0 \\
    \m[3-2, 0, 1, 2-2]\b{v}_2=\m[1,0,1,0]\vv[v_x, v_y] &= 0
    \end{align}
    $$
    One solution is $\b{v}_2 = \vv[v_x, v_y]=\vv[0,1]$. This will be our eigenvector for $\lambda=2$.
    
    When $\lambda=3$
    $$
    \begin{align}
    (A-3I)\b{v}_3 &= 0 \\
    \m[3-3, 0, 1, 2-3]\b{v}_3=\m[0,0,1,-1]\vv[v_x, v_y] &= 0
    \end{align}
    $$
    One solution is $\b{v}_3 = \vv[v_x, v_y]=\vv[1,1]$. This will be our eigenvector for $\lambda=3$.
    
    We can now decompose our matrix $A$
    $$
    \begin{align}
    A&=\begin{bmatrix}\b{v}_2 & \b{v}_3\end{bmatrix} \m[2,0,0,3] \begin{bmatrix}\b{v}_2 & \b{v}_3\end{bmatrix}^{-1} \\
    &=\m[0,1,1,1] \m[2,0,0,3] \m[0,1,1,1]^{-1} \\
    &=\m[0,1,1,1] \m[2,0,0,3] \m[-1,1,1,0]
    \end{align}
    $$
    
    Therefore we can get
    $$
    \begin{align}
    \b{X}_n &=A^n\b{X}_0 \\
    &=\m[3,0,1,2]^n\b{X}_0 \\
    &=\m[0,1,1,1] \m[2^n,0,0,3^n] \m[-1,1,1,0]\b{X}_0 \\
    &=
    \begin{bmatrix}
    3^n & 0 \\
    3^n - 2^n & 2^n
    \end{bmatrix} \b{X}_0
    \end{align}
    $$
    or, returning to its original form, 
    $$
    \begin{cases}
    \begin{align}
    x_n &=3^n x_0\\
    y_n &=(3^n-2^n)x_0 + 2^n y_0
    \end{align}
    \end{cases}
    $$
    *Eigenvector basis form (suggested by 曾玟銨):*
    Here provides an altrenative form, without explicitly having to express in terms of $x_0, y_0$
    $$
   \begin{align} \b{X}_n &=c_2\b{v}_2\lambda_2^n+c_3\b{v}_3\lambda_3^n\\
   &=c_2\vv[0,1]2^n + c_3\vv[1,1]3^n
   \end{align}
    $$
    where $c_2, c_3$ can be solved with initial value of $\b{X}_0$.
    This is true since 
    * Eigenvectors are independent and form a set of basis for $\b{X}_0$ (which means, $\b{X}_0=\sum_{i=0}^k c_i\b{v}_i$)
    * $A\b{v}_i=\lambda_i \b{v}_i$
    :::


    *
    \begin{cases}
    \begin{align}
    x_{n+1} &= y_n \\
    y_{n+1} &= -x_n+5y_n
    \end{align}
    \end{cases}
    
    :::info
    solution:
    $A=\m[0,1,-1,5]$, solving for the eigenvalue:
    $$
    \det(A-\lambda I)=\det\left(\m[0-\lambda, 1, -1, 5-\lambda]\right)=0
    $$
    Which gives us $\lambda^2-5\lambda+1=0\implies\lambda_\pm=\frac{1}{2}(5\pm\sqrt{21})$
    $$
    \newcommand{\lp}{\lambda_+}
    \newcommand{\lm}{\lambda_-}
    $$
    
    We then solve for eigen value.
    In the case $\lp$:
    $$
    \begin{align}
    (A- \lp I)\b{v}_+ &= 0 \\
    \m[0-\lp, 1, -1, 5-\lp]\b{v}_+=\m[-\lp, 1, -1, 5-\lp]\vv[v_x, v_y]&=0
    \end{align}
    $$
    One solution of $\b{v}_+$ is $\vv[v_x, v_y]=\vv[1, \lp]$. (*We only have to check for one row $[-\lp \quad 1]$ because v_+ is in the null space of $(A-\lambda I)$ and $(A-\lambda I)$ is singular.*
    
    In the case of $\lm$:
    $$
    \begin{align}
    (A- \lm I)\b{v}_- &= 0 \\
    \m[0-\lm, 1, -1, 5-\lm]\b{v}_+=\m[-\lm, 1, -1, 5-\lm]\vv[v_x, v_y]&=0
    \end{align}
    $$
    Which also get $\b{v}_- = \vv[1, \lm]$.
    
    We noe decompose $A$
    $$
    \begin{align}
    A&=\begin{bmatrix}\b{v}_+ & \b{v}_-\end{bmatrix}\m[\lp,0,0,\lm]\begin{bmatrix}\b{v}_+ & \b{v}_-\end{bmatrix}^{-1}\\ &=\m[1,1,\lp,\lm]\m[\lp,0,0,\lm]\m[1,1,\lp,\lm]^{-1} \\
    \end{align}
    $$
    And 
    $$
    \begin{align}
    A^n &=\m[1,1,\lp,\lm]\m[\lp^n,0,0,\lm^n]\m[1,1,\lp,\lm]^{-1} \\
    &= \m[1,1,\lp,\lm]\m[\lp^n,0,0,\lm^n]\m[\lm, -1, -\lp, 1]\frac{1}{\lm-\lp} \\
    &= \frac{1}{\sqrt{21}}\m[1,1,\lp,\lm]
    \begin{bmatrix}
    -\lp^n\lm & \lp^n \\
    \lp\lm^n & -\lm^n
    \end{bmatrix}\\
    &= \frac{1}{\sqrt{21}}
    \begin{bmatrix}
    -\lp^n\lm+\lp\lm^n & \lp^n-\lm^n \\
    -\lp^{n+1}\lm+\lp\lm^{n+1} & \lp^{n+1}-\lm^{n+1}
    \end{bmatrix}
    \end{align}
    $$
    $\lp\lm=1$, however *(product of two roots)* ,hence
    $$
    \begin{align}
    A^n &= \frac{1}{\sqrt{21}}
    \begin{bmatrix}
    -\lp^{n-1}+\lm^{n-1} & \lp^n-\lm^n \\
    -\lp^{n}+\lm^{n} & \lp^{n+1}-\lm^{n+1}
    \end{bmatrix}
    \end{align}
    $$
    Finally, since $\vv[x_n, y_n]=\b{X}_n=A^n\b{X}_0$, we get
    $$
    \begin{cases}
    \begin{align}
    x_{n} &= \frac{1}{\sqrt{21}}\left[(-\lp^{n-1}+\lm^{n-1})x_0 + (\lp^n-\lm^n)y_0 \right]\\
    y_{n} &= \frac{1}{\sqrt{21}}\left[(-\lp^{n}+\lm^{n})x_0 + (\lp^{n+1}-\lm^{n+1})y_0 \right]
    \end{align}
    \end{cases}
    $$
    where $\lambda_\pm=\frac{5 \pm \sqrt{21}}{2}$.
    
    Again, we provide the *eigenvector basis form*:
    $$
    \b{X}_n=c_+\vv[1,\lambda_+]\lambda_+^n + c_-\vv[1,\lambda_-]\lambda_-^n
    $$
    :::

    *
    \begin{cases}
    \begin{align}
    x_{n+1} &= x_n-y_n \\
    y_{n+1} &= 2x_n+4y_n
    \end{align}
    \end{cases}
    ::: info
    solution:
    $A=\m[1,-1,2,4]=\m[1,1,-1,-2]\m[2,0,0,3]\m[1,1,-1,-2]^{-1}$
    $A^n$ can then be derived:
    $$
    A^n = 
    \begin{bmatrix}
    2^{n+1}-3^n & 2^n-3^n \\
    2(3^n-2^n) & 2(3^n-2^{n-1})
    \end{bmatrix}
    $$
    Therefore
    \begin{cases}
    \begin{align}
    x_{n} &= (2^{n+1}-3^n)x_0 + (2^n-3^n)y_0 \\
    y_{n} &= 2(3^n-2^n)x_0 + 2(3^n-2^{n-1})y_0
    \end{align}
    \end{cases}
    
    *In eigenvector basis form*:
    $$
    \b{X}_n=c_1\vv[1,-1]2^n + c_2\vv[1,-2]3^n
    $$
    :::

    * 
    \begin{cases}
    \begin{align}
    x_{n+1} & = 3x_n - y_n \\
    y_{n+1} & = -x_n + 2y_n - z_n \\
    z_{n+1} & = -y_n +3z_n\\
    \end{align}
    \end{cases}
    :::info
    solution:
    $$
    \begin{align}
    A &=\begin{bmatrix}
    3  & -1 & 0  \\
    -1 &  2 & -1 \\
    0  & -1 & 3 
    \end{bmatrix}\\
    &=\begin{bmatrix}
     1 & -1 &  1\\
     2 & 0  & -1\\
     1 & 1  & 1  
     \end{bmatrix}
     \begin{bmatrix}
     1 & 0 & 0 \\
     0 & 3 & 0 \\
     0 & 0 & 4 
     \end{bmatrix}
     \begin{bmatrix}
     1 & -1 &  1\\
     2 & 0  & -1\\
     1 & 1  & 1     
     \end{bmatrix}^{-1}\\
     A^n &=\begin{bmatrix}
     1 & -1 &  1\\
     2 & 0  & -1\\
     1 & 1  & 1  
     \end{bmatrix}
     \begin{bmatrix}
     1 & 0 & 0 \\
     0 & 3^n & 0 \\
     0 & 0 & 4^n 
     \end{bmatrix}
     \begin{bmatrix}
     1 & -1 &  1\\
     2 & 0  & -1\\
     1 & 1  & 1     
     \end{bmatrix}^{-1}\\
     &=\frac{1}{6}\begin{bmatrix}
     2^{2n+1}+3^{n+1}+1 & -2(4^n-1) & 2^{2n+1}-3^{n+1}+1\\
     -2(4^n-1) & 2(4^n+2) & -2(4^n-1)\\
     2^{2n+1}-3^{n+1}+1 & -2(4^n-1) & 2^{2n+1}+3^{n+1}+1
     \end{bmatrix}
    \end{align}
    $$

    Here skip the process of substituding into $\b{X}_n=A^n\b{X}_0$. Just note that now $\b{X}_n \equiv\begin{bmatrix}x_n \\y_n \\z_n \end{bmatrix}$
     *In eigenvector basis form*:
     $$
     \b{X}_n=c_1\begin{bmatrix}1\\2\\1\end{bmatrix} 1^n +c_2 \begin{bmatrix}-1\\0\\1\end{bmatrix} 3^n+ c_3 \begin{bmatrix}1\\-1\\1\end{bmatrix} 4^n
     $$
    
    :::

    *
    \begin{cases}
    \begin{align}
    x_{n+1} & = 4x_n - 2y_n -2z_n \\
    y_{n+1} & = y_n \\
    z_{n+1} & = x_n + z_n\\
    \end{align}
    \end{cases}
    ::: info
    solution:
    $$
    \begin{align}
    A &= \begin{bmatrix}
    4 &  -2 & -2 \\
    0 &  1  & 0  \\
    1 &  0  & 1
    \end{bmatrix}\\
    &=\begin{bmatrix}
    0  & 1 & 2 \\
    -1 & 0 & 0 \\
    1  & 1 & 1
    \end{bmatrix}
    \begin{bmatrix}
    1 & 0 & 0\\
    0 & 2 & 0\\
    0 & 0 & 3
    \end{bmatrix}
    \begin{bmatrix}
    0  & 1 & 2 \\
    -1 & 0 & 0 \\
    1  & 1 & 1
    \end{bmatrix}^{-1}\\
    A^{n} &= \begin{bmatrix}
    0  & 1 & 2 \\
    -1 & 0 & 0 \\
    1  & 1 & 1
    \end{bmatrix}
    \begin{bmatrix}
    1 & 0 & 0\\
    0 & 2^n & 0\\
    0 & 0 & 3^n
    \end{bmatrix}
    \begin{bmatrix}
    0  & 1 & 2 \\
    -1 & 0 & 0 \\
    1  & 1 & 1
    \end{bmatrix}^{-1}\\
    &= \begin{bmatrix}
    2(3^n-2^{n-1}) & 2(2^n-3^n) & 2(2^n-3^n) \\
    0              &       1    &     0      \\
    3^n-2^n        & 2^{n+1}-3^n-1 & 2^{n+1}-3^n
    \end{bmatrix}
    \end{align}
    $$
    And $\b{X}_n=A^n\b{X}_0$
    
    *In eigenvector basis form*:
     $$         \b{X}_n=c_1\begin{bmatrix}0\\-1\\1\end{bmatrix} 1^n +c_2 \begin{bmatrix}1\\0\\1\end{bmatrix} 2^n+ c_3 \begin{bmatrix}2\\0\\1\end{bmatrix} 3^n
     $$
    :::

2.  (Simon and Blume 11.1-11.3)
    * If for some non-zero vector $\b{v}_1, \b{v}_2$, and scaler $r_1, r_2$ we have
    \begin{align}
    \tag{1} \b{v}_1=r_2\b{v}_2 \qtext{or} \b{v}_1-r_2 \b{v}_2=0\\
    \tag{2} \b{v}_2=r_1\b{v}_1 \qtext{or} r_1\b{v}_1-\b{v}_2=0
    \end{align}
    and
    $$
    \tag{3} 
    c_1\b{v}_1+c_2\b{v}_2=0 \text{ , } c_1 \text{ or }c_2\text{ nonzero}
    $$
    Show that if (1) or (2) holds then(3) holds, and, if (3) holds, then (1) or (2) holds.
    ::: info
    solution by 羅偉駿:
    $(1)(2) \implies (3)$: Let $c_1r_2 +c_2 = 0$
    \begin{align*}
    c_1v_1 + c_2v_2 &= c_1r_2v_2 + c_2v_2  \\
    &= (c_1r_2 +c_2)v_2 \\
    &= 0v_2 \\
    &= 0
    \end{align*}
    
    $(3) \implies (1)(2)$: Let $r_2 = -\frac{c_2}{c_1}$
    \begin{align*}
    &c_1v_1 + c_2v_2 =0 \implies  v_1 = -\frac{c_2}{c_1}v_2 \implies v_1 = r_2v_2
    \end{align*}
    :::
    
     * Which of the following pairs or triplets of vectors are linearly independent?
         (a) $(2,1), (1,2)$
         (b) $(2,1), (-4,-2)$
         \(c\) $(1,1,0), (0,1,1)$
         (d) $(1,1,0), (0,1,1), (1,0,1)$
    ::: info
    solution by 羅偉駿:
    (a) They're linear independent, since
        $$
        \begin{vmatrix}
        2  & 1  \\
        1  & 2 
        \end{vmatrix} = 3 ≠ 0 
        $$
    
    (b) They're linear dependent, since
        $$
        \begin{vmatrix}
        2  & -4  \\
        1  & -2 
        \end{vmatrix} = 0 
        $$
    
    \(c\) They're linear independent, since
        \begin{align*}
        &\text{Suppose  }
        a_1
        \begin{bmatrix}
        1  \\
        1  \\
        0
        \end{bmatrix}
        +a_2
        \begin{bmatrix}
        0  \\
        1  \\
        1
        \end{bmatrix} =
        \begin{bmatrix}
        a_1  \\
        a_1 + a_2  \\
        a_2
        \end{bmatrix} = 0 \\
        &\implies a_1 = 0, a_2 = 0 \\
        \end{align*}
    
    (d) They're linear independent, since
        $$
        \begin{vmatrix}
        1  & 0  & 1  \\
        1  & 1  & 0  \\
        0  & 1  & 1  \\
        \end{vmatrix} =
        \begin{vmatrix}
        1  & 0  \\
        1  & 1
        \end{vmatrix}
        +
        \begin{vmatrix}
        0  & 1  \\
        1  & 1
        \end{vmatrix} = 1 - (-1) = 2 \neq 0
        $$
    
    :::
    * Determine whether or not each of the following collections of vectors in $\r^4$ are linearly independent.
    (a) 
    $$
        v_1=\begin{bmatrix} 1 \\ 0 \\ 1 \\ 0 \end{bmatrix},\quad 
        v_2=\begin{bmatrix} 1 \\ 0 \\ 0 \\ 1 \end{bmatrix},\quad 
        v_3=\begin{bmatrix} 0 \\ 0 \\ 1 \\ 1 \end{bmatrix},\quad 
    $$
    (b)
    $$
        v_1=\begin{bmatrix} 1 \\ 0 \\ 1 \\ 0 \end{bmatrix},\quad 
        v_2=\begin{bmatrix} 1 \\ 0 \\ -1 \\ 0 \end{bmatrix},\quad 
        v_3=\begin{bmatrix} 1 \\ 0 \\ 0 \\ 0 \end{bmatrix},\quad 
    $$
    ::: info
    solution by 羅偉駿:
    (a) They're linear independent, since
    \begin{align*}
        &\text{Suppose  } a_1v_1 + a_2v_2 + a_3v_3 = 0 \\
        &\implies a_1\begin{bmatrix} 1 \\ 0 \\ 1 \\ 0 \end{bmatrix}+
        a_2\begin{bmatrix} 1 \\ 0 \\ 0 \\ 1 \end{bmatrix} + 
        a_3\begin{bmatrix} 0 \\ 0 \\ 1 \\ 1 \end{bmatrix}=0 \\
        &\implies \begin{bmatrix} a_1+a_2 \\ 0 \\ a_1+a_3 \\ a_2+a_3 \end{bmatrix} = 0 \\
        &\implies a_1 = a_2 = a_3 = 0 \\
    \end{align*}
    
    (b) They're linear dependent, since we can let $a_1 = a_2 = \frac{1}{2}, a_3 = -1$
    \begin{align*}
        &\text{Suppose  } a_1v_1 + a_2v_2 + a_3v_3 = 0 \\
        &\implies a_1\begin{bmatrix} 1 \\ 0 \\ 1 \\ 0 \end{bmatrix}+
        a_2\begin{bmatrix} 1 \\ 0 \\ -1 \\ 0 \end{bmatrix} + 
        a_3\begin{bmatrix} 1 \\ 0 \\ 0 \\ 0  \end{bmatrix}=0 \\
        &\implies \begin{bmatrix} a_1+a_2+a_3 \\ 0 \\ a_1-a_2 \\ 0 \end{bmatrix} = 0 \\
        &\implies a_1 = a_2, 2a_1 + a_3 = 0 \\
    \end{align*}
    :::
 
3. (邴國榮)(Sundaram p73 Q62) Examine the definiteness or semidefiniteness of the following quadratic forms:

\begin{align}
    \begin{bmatrix}
    0 & 0 & 1 \\
    0 & 1 & 0 \\
    1 & 0 & 0
    \end{bmatrix}
    &\qtext{,}
    \begin{bmatrix}
    1 & 2 & 3 \\
    2 & 4 & 6 \\
    3 & 6 & 0
    \end{bmatrix}\qtext{,}\\
    \begin{bmatrix}
    1 & 0 & 1 \\
    0 & 1 & 0 \\
    1 & 0 & 1
    \end{bmatrix}
    &\qtext{,}
    \begin{bmatrix}
    -1 &  2 & -1 \\
    2  & -4 & 2\\
    -1 &  2 & -1
    \end{bmatrix}
\end{align}
:::info
solution by 邴國榮:
Examine the definiteness or semidefiniteness by $\b{eigenvalues}$:

(1)
$$
\begin{vmatrix}
    0-\lambda  & 0  & 1  \\
    0  & 1-\lambda  & 0  \\
    1  & 0  & 0-\lambda  \\
\end{vmatrix} = \lambda^2(1-\lambda)-(1-\lambda)=(\lambda+1)(\lambda+1)^2=0 \\
\implies \lambda = 1\ or -1
$$ Thus the matrix is $\b{indefinite}$.

(2)
$$
\begin{vmatrix}
    1-\lambda  & 2  & 3  \\
    2  & 4-\lambda  & 6  \\
    3  & 6  & 0-\lambda  \\
\end{vmatrix} = -\lambda^3+5\lambda^2+45=0 \\
\implies \lambda = 0\ or\ \frac{5 \pm \sqrt{205}}{2}
$$ Thus the matrix is $\b{indefinite}$.

(3)
$$
\begin{vmatrix}
    1-\lambda  & 0  & 1  \\
    0  & 1-\lambda  & 0  \\
    1  & 0  & 1-\lambda  \\
\end{vmatrix} = (1-\lambda)^3-(1-\lambda) = [(1-\lambda)^2-1](1-\lambda) =0 \\
\implies \lambda = 0\ or\ 1\ or\ 2
$$ Thus the matrix is $\b{\text{positive semidefinite}}$.

(4)
$$
\begin{vmatrix}
    -1-\lambda  & 2  & -1  \\
    2  & -4-\lambda  & 2  \\
    1  & 2  & -1-\lambda  \\
\end{vmatrix} = -(\lambda^3+6\lambda^2+9\lambda+4)+9\lambda+4 = -\lambda^3-6\lambda^2 =0 \\
\implies \lambda = 0\ or\ -6
$$ Thus the matrix is $\b{\text{negative semidefinite}}$.
:::

4. (黃楚岳)Let 
$$A=
\begin{bmatrix} 
    1 & 0 & 0 & 0 \\
    -2& 3 & 0 & 0 \\
    0 & -4& 5 & 0 \\
    0 & 0 & -6& 7
\end{bmatrix}
$$
and $B=(I+A)^{-1}(I-A)$. Find $(I+B)^{-1}$

:::info
Solution by 黃楚岳：

$$
\begin{array}{lll}
I+B&=&(I+A)^{-1}(I+A)+(I+A)^{-1}(I-A)\\
&=&(I+A)^{-1}\left[(I+A)+(I-A)\right]\\
&=&(I+A)^{-1}2I\\
(I+B)^{-1}&=&\left[(I+A)^{-1}2I\right]^{-1}\\
&=&(2I)^{-1}\left[(I+A)^{-1}\right]^{-1}\\
&=&\frac{1}{2}(I+A)\\
&=&\begin{bmatrix}
1  & 0  & 0  & 0\\
-1 & 2  & 0  & 0\\
0  & -2 & 3  & 0\\
0  & 0  & -3 & 4
\end{bmatrix}
\end{array}
$$

:::

5. Determine whether the following collection of vectors in $\r^4$ are linearly independent.
$$
v_1=\begin{bmatrix} 1 \\ 0 \\ 1 \\ 0 \end{bmatrix},\quad 
v_2=\begin{bmatrix} 1 \\ 0 \\ 0 \\ 1 \end{bmatrix},\quad 
v_3=\begin{bmatrix} 0 \\ 0 \\ 1 \\ 1 \end{bmatrix},\quad 
$$

6. (謝秉儒)Suppose $a,b,c$ are real numbers.  Discuss the solution of the system of the equations in terms of $a,b,c$ for two cases: 
(a) one solution, 
(b) infinitely many solutions.
\begin{cases}
x+2y+az = 1\\
3x+4y+bz = -1\\
2x+10y+7z = c
\end{cases}
    ::: info
    solution:
    $$
    \begin{align}
    \begin{array}{ccc|c}
    1 & 2 & a & 1 \\
    3 & 4 & b & -1 \\
    2 & 10 & 7 & c \\
    \end{array}&
    \rightarrow
    \begin{array}{ccc|c}
    1 & 2 & a & 1 \\
    0 & -2 & b-3a & -4 \\
    0 & 6 & 7-2a & c-2 \\
    \end{array}&
    \rightarrow
    \begin{array}{ccc|c}
    1 & 2 & a & 1 \\
    0 & -2 & b-3a & -4 \\
    0 & 0 & 7-11a+3b & c-14 \\
    \end{array}
    \end{align} 
    $$
    (a) one solution
    \begin{cases}
    7-11a+3b \neq 0\\
    \end{cases}
    (b) infinitely many solutions
    \begin{cases}
    7-11a+3b = 0\\
    c-14 =0
    \end{cases}
    

7.(Yu-Chieh Kuo) Determine the definiteness of the following symmetric matrices.
    $$
    A= 
    \begin{bmatrix}
    -3 & 4 \\
     4 & -5
    \end{bmatrix}, \quad
    B=
    \begin{bmatrix}
    2 & 4 \\
    4 & 8
    \end{bmatrix}
    $$

:::info
$$
\begin{align}
\det(A_1) &=\det[-3]=-3<0 \\
\det(A) &=\det\m[-3,4,4,-5]=-1<0
\end{align}
$$
Thus $A$ is indefinite.

$$
\begin{align}
\det(B_1) &=\det[2]=2>0 \\
\det(B) &=\det\m[2,4,4,8]=0
\end{align}
$$
To this point we know it mustn't be positive definite. To see if it is positive semidefinite, we still need to examine the other principle submatirx
$$
\det(B_2)=\det[8]=8>0
$$
Thus B is positive semidefinite.
:::
