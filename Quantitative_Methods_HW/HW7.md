# HW7
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
                %grad%
    \newcommand{\grad}{\nabla}
                %Hessian%
    \newcommand{\ddf}{\mathcal{D}^2 f}
                %partial%
    \newcommand{\p}{\partial}
    \newcommand{\pdv}[3][{}]{\frac{\p^ #1 #2}{\p #3^ #1}}
    \newcommand{\ppdv}[3]{\frac{\p^2 #1}{\p #2 \p #3}}
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
                %前後空格的文字%
    \newcommand{\qtext}[1]{\quad \text{#1} \quad}
                %epsilon%
    \newcommand{\set}[2]{ \left\{ #1 \mid #2 \right\}}
$$

# Lecture 7-2 (Optimization)

1. Let $D=[0,1]$. Describe the set $f(D)$ in each of the following cases, identify $\sup{f(D)}$, and answer whether or not $\max{f(D)}$ exists.

    * $f(x) = 1+x$ for all $x \in D$

    * $f(x) = 1$ if $x<\frac{1}{2}$ and $f(x) = 2x$ otherwise.

:::info
solution by 邴國榮:
* $f(x) = 1+x$ for all $x \in D$
$f(D)=[1,2] \implies U(f(D)) = \set{u \in \mathbb{R}}{u \geq 2} \implies Sup(f(D))=2$
by definition, $U(f(D)) \cap f(D) = 2$, thus $\max{f(D)} = 2$

* $f(x) = 1$ if $x<\frac{1}{2}$ and $f(x) = 2x$ otherwise.
in $D = [0,1],$
$$f(x) = \begin{cases}
    1 & \text{where} \  x \in [0,\frac{1}{2}) \\
    2x & \text{where} \  x \in [\frac{1}{2},1]
    \end{cases}$$ then $U(f(D)) = \set{u \in \mathbb{R}}{u \geq 2} \implies Sup(f(D))=2$
by definition, $U(f(D)) \cap f(D) = 2$, thus $\max{f(D)} = 2$
:::

2. Read Sundaram subsection 2.3.1 to 2.3.5, and 2.3.7. For each optimization problem, answer the same questions as in Example.

    ::: success
    [Reading Material](http://docshare02.docshare.tips/files/19163/191639836.pdf)

    Start from Page 87 of the PDF file.
    :::
    
# Lecture 7 -- Derivatives

1. Assume $f$ and $g$ are real-valued functions defined on $(a,b)$ and differentiable at c. Apply Theorem 1 to show
    
    <!-------- 1-a ----------->
    (a) $f + g$ is differnentiable at c and its derivative of c equals $f'(c) + g'(c)$. 
    :::info
    Solution by 羅偉駿：
    Since f, g are differentiable at c,
    $$
    f'(c) = \lim_{x\to c} \frac{f(x)-f(c)}{x-c}, g'(c) = \lim_{x\to c} \frac{g(x)-g(c)}{x-c}.
    $$
    Let $h(x) = f(x) + g(x)$, then
    $$
    \begin{align*}
        h'(c) 
        &= \lim_{x\to c} \frac{h(x)-h(c)}{x-c} \\
        &= \lim_{x\to c} \frac{f(x)+g(x)-f(c)-g(c)}{x-c} \\
        &= \lim_{x\to c} \frac{f(x)-f(c)}{x-c} + lim_{x\to c} \frac{g(x)-g(c)}{x-c} \\
        &= f'(c) + g'(c)
    \end{align*}
    $$
    
    :::
    <!-------- 1-b ----------->
    (b) $fg$ is differnentiable at c and its derivative of c equals $f(c)g'(c) + f'(c)g(c)$.
    :::info
    Solution by 羅偉駿：
    Since f, g are differentiable at c,
    $$
    f'(c) = \lim_{x\to c} \frac{f(x)-f(c)}{x-c}, g'(c) = \lim_{x\to c} \frac{g(x)-g(c)}{x-c}.
    $$
    Let $h(x) = f(x)g(x)$, then
    $$
    \begin{align*}
        h'(c) 
        &= \lim_{x\to c} \frac{h(x)-h(c)}{x-c} \\
        &= \lim_{x\to c} \frac{f(x)g(x)-f(c)g(c)}{x-c} \\
        &= \lim_{x\to c} [g(c)\frac{f(x)-f(c)}{x-c} + f(c)\frac{g(x)-g(c)}{x-c}] \\
        &= g(c) \lim_{x\to c}\frac{f(x)-f(c)}{x-c} + f(c) \lim_{x\to c}\frac{g(x)-g(c)}{x-c} \\
        &= g(c)f'(c)+f(c)g'(c)
    \end{align*}
    $$
    :::
2. Sundaram Q57, Q63 on page 73
    
    <!-------- 2-i ----------->
    (i) Let $f:\r^2 \to \r$ be defined by $f(0,0) =0$ and for $(x,y) \neq (0,0)$, 
    $$ 
    f(x,y) = {xy(x^2-y^2) \over x^2+y^2}
    $$
    Show that the cross-partials $\ppdv{f}{x}{y}$ and $\ppdv{f}{y}{x}$ exist at all $(x,y)\in \r^2$, but that these partials are not continuous at $(0,0)$. Show also that
    $$
    \ppdv{f}{x}{y}(0,0) \neq \ppdv{f}{y}{x}(0,0)
    $$
    :::info
    Solution by 陳家威, and I appreciate 鄭宗弘 for pointing out my mistake.
    
    We first find the derivatives of $f(x,y)$ where $(x,y) \neq (0,0)$. By basic calculus:
    $$
    \begin{align}
    \pdv{f}{x}(x,y) &= f_x(x,y) =
    { {x^4y + 4x^2y^3 - y^5}  \over {(x^2 + y^2)^2 } } \\
    \pdv{f}{y}(x,y) &= f_y(x,y) = 
    { {x^5 - 4x^3y^2 - xy^4}  \over {(x^2 + y^2)^2 } }
    \end{align}
    $$
    Here I denote $f_x$ with $\pdv{f}{x}$ . And its cross-partial derivatives
    $$
    \begin{align}
    f_{xy}(x,y) &= \pdv{}{x}f_y =
    { {x^6 + 9 x^4 y^2 - 9 x^2 y^4 - y^6} \over {(x^2 + y^2)^3} } \\
    f_{yx}(x,y) &= \pdv{}{y}f_x = 
    { {x^6 + 9 x^4 y^2 - 9 x^2 y^4 - y^6} \over {(x^2 + y^2)^3} }
    \end{align}
    $$
    At first sight the two cross-partial derivatives look exactly the same. However, the symmetry breaks when we construct two sequences that converge into $(0,0)$.
    
    Let us construct a sequence $P_n=(\frac{1}{n} , \frac{1}{n} k) \in \r^+ \times \r^+$, where $k \in R/ \{ 0 \}$. This is basically just a sequence with slope $k$ that converges to $0$ : $P_n \to (0,0)$. Clearly we observe that, for each point $P_n$ , $y_n = k x_n$, therefore the second derivative is
    $$
    \begin{align}
    f_{xy}(P_n)&= 
    { x^6 + 9 x^4 (kx)^2 - 9 x^2 (kx)^4 - (kx)^6 \over  { ( x^2 + (kx)^2 )^3  }  } \\
    &=
    { 1 + 9 k^2 - 9 k^4 - k^6 \over { ( 1 + k^2 )^3 } } =g(k)
    \end{align}
    $$
    This means that for each sequence $\{P_n\}$ that converges to $(0,0)$, the cross-partial derivative $f_{xy}$ depends on the slope $k$ you choose to approach with. 
    
    Recall the condition for a function to be continuous : 
    $$
    \lim_{n \to \infty} f_{xy}(P_n) = f_{xy}(\lim_{n \to \infty} P_n)
    $$
    Since $\lim_{n \to \infty} f_{xy}(P_n)$ is not the same for each $k$ in the first place, the condition is definitely unsatisfied, therefore $f_{xy}$ is not continuous at $(0,0)$.
    
    ##### Show that$\ppdv{f}{x}{y}(0,0) \neq \ppdv{f}{y}{x}(0,0)$
    We then proceed to see the cross-partial derivative at $(0,0)$ from different order. In order to do that, we must first evaluate the first partial derivative at $(0,0)$
    $$
    \begin{align}
    f_x(0,0) &= \lim_{h \to 0} \frac{f(h,0) - f(0,0)}{ h } = \lim_{h \to 0}\frac{0-0}{h}=0 \\
    f_y(0,0) &= \lim_{h \to 0} \frac{f(0,h) - f(0,0)}{ h } = \lim_{h \to 0}\frac{0-0}{h}=0
    \end{align}
    $$
    and thus the cross-partial derivatives
    $$
    \begin{align}
    f_{xy}(0,0) &= \pdv{}{x}f_y(0,0) = \lim_{h \to 0} \frac{f_y(h,0)-f_y(0,0)}{h} = \lim_{h \to 0} { { \frac{h^5}{h^4} - 0 } \over  h  } = 1 \\
    f_{yx}(0,0) &= \pdv{}{y}f_x(0,0) = \lim_{h \to 0} \frac{f_x(0,h)-f_x(0,0)}{h} = \lim_{h \to 0} { { -\frac{h^5}{h^4} - 0 } \over  h  } = -1
    \end{align}
    $$
    We see that $\ppdv{f}{x}{y}(0,0) = 1 \neq \ppdv{f}{y}{x}(0,0) = -1$ . That is, the hessian matrix will not be symmetric at $(0,0)$.
    :::
    
    <!-------- 2-ii ----------->
    (ii) Find the hessians $D^2 f$ of each of the following functions. Evaluate the hessians at the specified points, and examine the hessian is positive definite, negative definite, positive semidefinite, negative semidefinite, or indefinite:
    
    <!-------- 2-ii-a ----------->
    (a) $f: \r^2 \to \r, f(x) = x_1^2+\sqrt{x_2}$ , at $x=(1,1)$
    ::: info
    $\ddf = \begin{bmatrix} 2 & 0 \\ 0 & -\frac{1}{4} x_2^{3/2}\end{bmatrix}_{(1,1)} = \begin{bmatrix} 2 & 0 \\ 0 & -\frac{1}{4} \end{bmatrix}$
    
    The eignvalues are obviously $2, -\frac{1}{4} \implies$ indefinite
    :::

    <!-------- 2-ii-b ----------->
    (b) $f: \r^2 \to \r, f(x) = (x_1 x_2)^{1/2}$ , at an arbitrary point $x \in \r^2_{++}$
    ::: info
    $$
    \begin{align}
    f_1 &= \frac{1}{2} x_2 (x_1 x_2)^{-1/2} \\
    f_2 &= \frac{1}{2} x_1 (x_1 x_2)^{-1/2} \\ \hline
    f_{11} &= -\frac{1}{4} x_2^2 (x_1 x_2)^{-3/2} \\
    f_{22} &= -\frac{1}{4} x_1^2 (x_1 x_2)^{-3/2} \\
    f_{12} &= f_{21} = \frac{1}{4}(x_1 x_2)^{-1/2}
    \end{align}
    $$
    $$
    \ddf = \begin{bmatrix}
    f_{11} & f_{12} \\
    f_{21} & f_{22}
    \end{bmatrix}
    $$
    Principle minor of 1^st^ order: $f_{11}<0, f_{22}<0$
    Principle minor of 2^nd^ order: $f_{11} f_{22} - f_{12} f_{21} = \frac{1}{16(x_1 x_2)}- \frac{1}{16(x_1 x_2)}=0$
    $\implies$ negative semidefinite
    :::

    <!-------- 2-ii-c ----------->
    \(c\) $f: \r^2 \to \r, f(x) = (x_1 x_2)^2$ , at an arbitrary point $x \in \r^2_{++}$
    
    :::info
    $$
    \ddf=\begin{bmatrix}
    2x^2 & 4 x_1 x_2 \\
    4 x_1 x_2 & 2x_1^2
    \end{bmatrix}
    $$
    Principle minor of 1^st^ order: $f_{11}>0, f_{22}>0$
    Principle minor of 2^nd^ order: $f_{11} f_{22} - f_{12} f_{21}=-12 x_1^2 x_2^2 < 0$
    $\implies$ indefinite
    
    :::

    <!-------- 2-ii-d ----------->
    (d) $f: \r^3_+ \to \r, f(x) = \sqrt{x} + \sqrt{x_2} + \sqrt{x_3}$ , at $x=(2,2,2)$
    :::info
    $$
    \ddf = \begin{bmatrix}
    -\frac{1}{4} x_1^{-3/2} & 0 & 0 \\
    0 & -\frac{1}{4} x_2^{-3/2} & 0 \\
    0 & 0 & -\frac{1}{4} x_3^{-3/2}
    \end{bmatrix}
    $$
    Eigenvalues are all $<0 \implies$ negative definite
    :::

    <!-------- 2-ii-e ----------->
    (e) $f: \r^3_+ \to \r, f(x) = \sqrt{x_1 x_2 x_3}$ , at $x=(2,2,2)$
    
    :::info
    Solution by 陳家威 
    $$
    \newcommand{\xxx}{x_1 x_2 x_3}
    \begin{matrix}
    & f_1 = \frac{x_2 x_3}{2\sqrt{\xxx}}
    & f_2 = \frac{x_1 x_3}{2\sqrt{\xxx}} 
    & f_3 = \frac{x_1 x_2}{2\sqrt{\xxx}}
    \end{matrix}
    $$

    $$
    \begin{align}
    f_{11} &= - \frac{ x_2^2 x_3^2}{4 (\xxx)^{3/2}} &\qquad f_{12} &=\frac{x_3}{2 (\xxx)^{1/2}} - \frac{\xxx^2}{4(\xxx)^{3/2}} \\
     &= - \frac{(\xxx)^2 / x_1^2 }{4 (\xxx)^{3/2}}  &   &= \frac{x_3}{2 (\xxx)^{1/2}} - \frac{x_3(\xxx)}{4(\xxx)^{3/2}} \\
     &= - \frac{(\xxx)^{1/2}}{4 x_1^2} & & = \frac{x_3}{2 (\xxx)^{1/2}} - \frac{x_3}{4(\xxx)^{1/2}} \\
     &= -\frac{f}{4x_1^2} & & =\frac{x_3}{f}
    \end{align}
    $$
        *By symmetry, because doing $x_1$ is the same as doing $x_2, x_3$, we can simply calculate the results for one and interchange the indicies to obtain the others*:
    $$
    f_{ii} = -\frac{f}{4x_i^2} \qquad f_{ij} = \frac{x_k}{f}
    \newcommand{\fii}[1]{\frac{-f}{4x_{#1}^2}}
    \newcommand{\fij}[1]{\frac{x_{#1}}{f}}
    $$
    Hence the Hessian matrix
    $$
    \ddf = 
    \begin{bmatrix}
    f_{11} & f_{12} & f_{13} \\
    f_{21} & f_{22} & f_{23} \\
    f_{31} & f_{32} & f_{33}
    \end{bmatrix} = 
    \begin{bmatrix}
    \fii{1} & \fij{3} & \fij{2} \\
    \fij{3} & \fii{2} & \fij{1} \\
    \fij{2} & \fij{1} & \fii{3}
    \end{bmatrix}
    $$
    >To this point, you can just plug in $(x_1, x_2, x_3)=(2,2,2)$ and get a matrix with only numbers, which is 
    >$$
    \begin{bmatrix}
        -\frac{\sqrt{2}}{8} & \frac{\sqrt{2}}{8}  & \frac{\sqrt{2}}{8} \\
        \frac{\sqrt{2}}{8} & -\frac{\sqrt{2}}{8}  &\frac{\sqrt{2}}{8} \\
        \frac{\sqrt{2}}{8} & \frac{\sqrt{2}}{8}  & -\frac{\sqrt{2}}{8} \\
    \end{bmatrix}
    >$$
    > but I prefer analyzing the general behavior of the Hessian matrix when $\xxx > 0$, because I like symmetry :blush: .


    ***Principle minor of order 1***:
    $f_{11}=\fii{1} < 0 \qtext{,} f_{22} = \fii{2}< 0 \qtext{,} f_{33} = \fii{3} < 0$
    
    ***Principle minor of order 2***:
    $$
    \begin{align}
    \det \left (\begin{matrix}
    f_{11} & f_{12} \\
    f_{21} & f_{22}
    \end{matrix} \right) &= 
    f_{11}f_{22} - f_{12}f_{21} =\frac{f^2}{16 (x_1^2 x_2^2)}-\frac{x_3^2}{16(\xxx)} \\
    &=\frac{\xxx}{16 (x_1^2 x_2^2)} - \frac{x_3^2}{16(\xxx)} = 0
    \end{align}
    $$
    By symmetry, all determinants of principle minors of order 2 are $=0$.

    ***Principle minor of order 3***
    $$\det(\ddf)=( f_{11} f_{22} f_{33} + f_{12} f_{23} f_{13} + f_{13} f_{21} f_{32} ) - ( f_{13} f_{22} f_{31} + f_{23} f_{32} f_{11} + f_{12} f_{21} f_{33} )$$
    
    Before brute-forcing the equation, notice (1) Because the function is well-behaved at $(2,2,2)$ , we know $f_{ij} = f_{ji}$, and (2) due to symmetry, any permutation that preserves the order of the index does not affect the valuation, for example, by interchanging $(1,2,3) \to (2,3,1) \to (3,1,2)$, the value $f_{13} f_{22} f_{31} \to f_{21} f_{33} f_{12} \to f_{32} f_{11} f_{23}$ remains the same.
    
    Therefore we can simplify the det to
    $$
    \begin{align}
    \det(\ddf) &= f_{11} f_{22} f_{33} + 2 (f_{12} f_{23} f_{13}) - 3 (f_{13} f_{22} f_{13})\\
    &= - \frac{f^3}{64 (\xxx)^2} + 2 \fij{3} \fij{1} \fij{2} -3 \fij{2} \left (\fii{2} \right) \fij{2} \\
    & = \frac{1}{16f} = \frac{1}{16\sqrt{\xxx}} >0
    \end{align}
    $$
    Thus, the Hessian matrix for $f(x)=\sqrt{\xxx}$ is indefinite for all points such that $\xxx>0$.

    :::

    <!-------- 2-ii-f ----------->
    (f) $f: \r^3_+ \to \r, f(x) = x_1 x_2 + x_2 x_3 + x_3 x_1$ , at $x=(1,1,1)$

    :::info
    $$
    \ddf = \begin{bmatrix}
    0 & 1 & 1 \\
    1 & 0 & 1 \\
    1 & 1 & 0
    \end{bmatrix}, \text{and } \det(\ddf - \lambda I) = (-\lambda ^3 + 1 + 1) - 3\lambda = 0 \\
    \iff \lambda = 2, -1, -1 \implies f \text{ is indefinite.}
    $$
    :::


    <!-------- 2-ii-g ----------->
    (g) $f: \r^3_+ \to \r, f(x) = ax_1 + bx_2 + cx_3$ , for some constants $a, b, c \in \r$, at $x=(2,2,2)$
    
    :::info
    $$
    \ddf = \begin{bmatrix}
    0 & 0 & 0 \\
    0 & 0 & 0 \\
    0 & 0 & 0
    \end{bmatrix}, \text{and } \lambda = 0 \implies     f \text{ is either positive or negative semi-definite.}
    $$
    :::

<!-------- 3 ----------->
3. Simon and Blume 14.7 on page 312
    A firm has the Cobb-Douglas production function $y=10 x_1^{1/3} x_2^{1/2} x_3^{1/6}$. Currently, it is using the input bundle $(27,16,64)$.
    (a) How much is it producing?
    (b) Use differntials to approximate its new output when $x_1$ increases to $27.1$, $x_2$ decreases to $15.7$ and $x_3$ remains the same.
    \(c\) Use a calculator to compare your answer in part b with the actual output.
    (d) Do b and c for $\Delta x_1 = \Delta x_2 = 0.2$ and $\Delta x_3 = -0.4$.
    
:::info
solution by 邴國榮:
(a)
$y=10 \cdot 27^{1/3} \cdot 16^{1/2} \cdot 64^{1/6} = 10 \cdot 3 \cdot 4 \cdot 2 = 240$
(b)
linear approximation of $y=10 x_1^{1/3} x_2^{1/2} x_3^{1/6} \approx$
$$y^* + \frac{10}{3} x_1^{-2/3} x_2^{1/2} x_3^{1/6} \cdot 0.1 + 5 x_1^{1/3} x_2^{-1/2} x_3^{1/6} \cdot (-0.3) + \frac{5}{3} x_1^{1/3} x_2^{1/2} x_3^{-5/6} \cdot 0$$ $$=240 - \frac{211}{108} \approx 238.0463$$
$(c)$
by calculator, $y=10 \cdot 27.1^{1/3} \cdot 15.7^{1/2} \cdot 64^{1/6} \approx 238.0325$
(d)
$\Delta x_1 = 0.2, \Delta x_2 = 0.2, \Delta x_3 = -0.4$, then the production by linear approximation: $$y^* + \frac{10}{3} x_1^{-2/3} x_2^{1/2} x_3^{1/6} \cdot 0.2 + 5 x_1^{1/3} x_2^{-1/2} x_3^{1/6} \cdot 0.2 + \frac{5}{3} x_1^{1/3} x_2^{1/2} x_3^{-5/6} \cdot (-0.4)$$ $$=240 + \frac{199}{108} \approx 241.8426$$
where the value is $y=10 \cdot 27.2^{1/3} \cdot 16.2^{1/2} \cdot 63.6^{1/6} \approx 241.8373$
:::
    
<!-------- 4 ----------->
4. Simon and Blume Read subsection 15.4: application: comparative statics (p360–364, work on exercises 15.26-15.32).
    :::warning
    These exercises depend strongly on the contents and equations in the subsection mentioned above, so I neglected this part.
    
    :::
    
    :::info
    solutions by Yu-Chieh Kuo and 陳家威
    **15.26:** 
    Cobe-Douglus Utility gives that $U = x_i^\alpha y_i^\alpha$, $\alpha > 0$.
    Since a monotonic transformation on an utility function preserves the same preference, and $\frac{d}{dx}\ln x = \frac{1}{x}$ is also a monototic transformation. Thus,
    $$
    U' = \ln(U) = \alpha \ln (x_i) + (1 - \alpha)\ln y_i = \alpha u(x_i) + (1 - \alpha)u(y_i)
    $$
    is also a  Cobb-Douglus Utility.
    
    **15.27:**
    Given $$
    \begin{cases}
    px_1 + qy_1 & = pe_1 & \text{(42)} \\
    x_1 + x_2 & = e_1 & \text{(45)} \\
    y_1 + y_2 & = e_2 & \text{(46)}
    \end{cases}
    $$, by substitute $(e_1 - x_2, e_2 - y_2)$ for $(x_1, y_1)$, we have 
    $$
    \begin{equation}
    p(e_1 - x_2) + q(e_2 - y_2) = pe_1 \implies px_2 + qy_2 = qe_2
    \end{equation}
    $$
    
    **15.28:**
    Given
    $$
    \begin{cases}
    \frac{\alpha}{1-\alpha}u_1'(x_1) - pu_1'(y_1) & = 0 & \text{(a)} \\
    px_1 + y_1 - p & = 0 & \text{(b)} \\
    \frac{\alpha}{1-\alpha}u_2'(x_2) - pu_2'(y_2) & = 0 & \text{(c)} \\
    x_1 + x_2 - 1 & = 0 & \text{(d)} \\
    y_1 + y_2 - 1 & = 0 & \text{(e)}
    \end{cases}
    $$,
    (a) and (b) imply $\frac{u_1'(x_1)}{u_1'(y_1)} = \frac{u_2'(x_2)}{u_2'(y_2)} = \frac{p(1-\alpha)}{\alpha}$ denoted by (f). If we restrict $u_i'(x)$ to be in the form of $ax^{k-1}, \ k \neq 1$, that is, $u_i(x) \propto \ln x$ or $u_i(x)$ is homogeneous of degree $k, \ k \neq 0, 1$.
    Therefore, deriving from (f)
    $$
    \begin{cases}
    \frac{u_1'(x_1)}{u_1'(y_1)} & = \frac{(\frac{x_1}{y_1})^{k-1} u_1'(y_1)}{u_1'(y_1)}  & = (\frac{x_1}{y_1})^{k-1} & \text{(g)} \\
    \frac{u_2'(x_2)}{u_2'(y_2)} & = \frac{(\frac{x_2}{y_2})^{k-1} u_2'(y_2)}{u_2'(y_2)}  & = (\frac{x_2}{y_2})^{k-1} & \text{(h)} \\
    \frac{u_1'(x_1)}{u_1'(y_1)} & = \frac{u_2'(x_2)}{u_2'(y_2)}  & = \frac{p(1-\alpha)}{\alpha} & \text{(f).}
    \end{cases}
    $$
    (f), (g), (h) imply $\frac{x_1}{y_1} = \frac{x_2}{y_2} = \frac{1-x_1}{1-y_1} \implies (x_1, x_2) = (y_1, y_2)$. Plug $(x_1, x_2) = (y_1, y_2)$ into (a), we have
    
    $$
    \begin{equation}
    \frac{u_1'(x_1)}{u_1'(y_1)} = \frac{u_2'(x_2)}{u_2'(y_2)} = 1 = \frac{p(1-\alpha)}{\alpha} \implies p = \frac{\alpha}{1-\alpha} \\
    px_1 + y_1 - p = px_1 + x_1 - p = 0 \implies x_1 = \frac{p}{1+p} = \alpha = y_1 \\
    x_1 + x_2 = 1 \implies x_2 = 1 - x_1 = 1 - \alpha = y_2
    \end{equation}
    $$
    
    **15.29:**
    Let $A = \begin{bmatrix}
    -r_1(\alpha) & r_1(\alpha) & -(1-\alpha) \\
    \alpha & 1-\alpha & -(1-\alpha)^2 \\
    r_2(1-\alpha) & -r_2(1-\alpha) & \dfrac{-(1-\alpha)^2}{\alpha}
    \end{bmatrix}$, we can derive $\det A = -(1-\alpha)R_2 + \frac{(1-\alpha)^2}{\alpha}R_1 \equiv D$, where $R_1 \equiv r_1(\alpha) > 0$ and $R_2 \equiv r_2(1-\alpha) > 0$.
    Crammer's rule gives us that 
    $$
    \begin{cases}
    dx_1 & = \frac{-R_2(1-R_1)(1-\alpha)^2}{D}de_2 \\
    dy_1 & = \frac{(1-\alpha)R_2[R_1(1-\alpha) + \alpha]}{D}de_2 \\
    dp & = \frac{R_1 R_2}{D}de_2.
    \end{cases}
    $$
    Besides, the Implict Function Theorem tells us that, when given only one (exogeneous) variable $e_2$, every variable can be written as a function of $e_2$. Therefore, we have
    $$
    \begin{cases}
    \pdv{x_1}{e_2} & = \frac{-R_2(1-R_1)(1-\alpha)^2}{D} \\
    \pdv{y_1}{e_2} & = \frac{(1-\alpha)R_2[R_1(1-\alpha) + \alpha]}{D} \\
    \pdv{x_2}{e_2} & = \frac{R_2(1-R_1)(1-\alpha)^2}{D} \\
    \pdv{y_2}{e_2} & = 1 - \frac{(1-\alpha)R_2[R_1(1-\alpha) + \alpha]}{D} \\
    \pdv{p}{e_2} & = \frac{R_1R_2}{D}
    \end{cases}
    $$
    
    **15.30:**
    Given $u_1(z) = u_2(z) = \ln z$ and $\alpha = \frac{1}{2}$, we derive that $R_1 = R_2 = D = 1$
    $\implies \pdv{x_1}{e_2} = \pdv{x_2}{e_2} = 0, \ \pdv{y_1}{e_2} = \pdv{y_2}{e_2} = \frac{1}{2} > 0, \text{ and} \pdv{p}{e_2} = 1 > 0$
    
    :::
