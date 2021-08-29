# HW5


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
1. Show $(0,1]$ is neither open nor closed.
::: info
solution by 羅偉駿：
Not open:
Take $1 \in (0,1]$.
$\forall \epsilon > 0, B(1,\epsilon) \not\subset (0,1]$;  for example, $1+\frac{\epsilon}{2}>1 \notin (0,1]$.
So $(0,1]$ is not open.
\
Not closed:
Take $0 \in (0,1]^c$.
$\forall \epsilon > 0, B(0,\epsilon) \not\subset (0,1]^c$; for example, $0+\frac{\epsilon}{2}>1 \in (0,1]$.
Since $(0,1]^c$ is not open, $(0,1]$ is not closed.
:::
<!---------- 2 ---------->
2. Show that the finite union of closed sets is closed.
::: info
solution by 羅偉駿：
We know that the finite intersection of open sets is open.
Given $G_i$ is open, $\forall i \in [1,n]$.
\begin{align*}
    &\implies \bigcap_{i=1}^n G_i \text{ is open.} \\
    &\implies [\bigcap_{i=1}^n G_i]^c \text{ is closed.} \\
    &\implies \bigcup_{i=1}^n G_i^c \text{ is closed.}
\end{align*}
Hence, the finite union of closed sets is closed.
:::
<!---------- 3 ---------->
3. If S and T are subsets of $\rn$, show that $\mathrm{int}S\cap\mathrm{int}T = \mathrm{int}{(S\cap T)}$ and $\mathrm{int}S\cup\mathrm{int}T \subset \mathrm{int}{(S\cup T)}$
::: info
solution by 羅偉駿：
First, show that $\mathrm{int}S\cap\mathrm{int}T = \mathrm{int}{(S\cap T)}$.
$(\subset):$
Let $x \in \mathrm{int}S\cap\mathrm{int}T$
$\implies \exists \epsilon_s > 0, \text{s.t. } B(x,\epsilon_s) \subset S$ and $\exists \epsilon_t > 0, \text{s.t. } B(x,\epsilon_t) \subset T$
Let $\epsilon = \min\{\epsilon_s, \epsilon_t\}.$
$\implies B(x,\epsilon) \subset S \cap T$
$\implies x \in \mathrm{int}(S \cap T)$
Hence, $\mathrm{int}S\cap\mathrm{int}T \subset \mathrm{int}{(S\cap T)}$.
\
$(\supset):$
Let $x \in \mathrm{int}(S \cap T)$
$\implies \exists \epsilon >0, \text{s.t. }B(x,\epsilon) \subset S \cap T$
$\implies \exists \epsilon >0, \text{s.t. }B(x,\epsilon) \subset S$ and $B(x,\epsilon) \subset T$
$\implies x \in \mathrm{int}S \cap \mathrm{int}T$
\
Second, show that $\mathrm{int}S\cup\mathrm{int}T \subset \mathrm{int}{(S\cup T)}.$
Let $x \in \mathrm{int}S\cup\mathrm{int}T.$
If $x \in \mathrm{int}S$, $\exists \epsilon >0, \text{s.t. }B(x,\epsilon) \subset S \subset S \cup T$.
If $x \in \mathrm{int}T$, $\exists \epsilon >0, \text{s.t. }B(x,\epsilon) \subset T \subset S \cup T$.
$\implies x \in \mathrm{int}{(S\cup T)}$
Hence, $\mathrm{int}S\cup\mathrm{int}T \subset \mathrm{int}{(S\cup T)}.$



:::
<!---------- 4 ---------->
4. Show that $S=\set{(y_1, y_2)\in \r^2}{P_1 y_1 + P_2 y_2 < I}$ is not closed.

:::info
solution by Yu-Chieh Kuo:

The statement is equivalent to show that $S^C=\set{(y_1, y_2)\in \r^2}{P_1y_1+P_2y_2\geq I}$ is not open.
Consider $y=(y_1, y_2) \in S^C \st P_1y_1+P_2y_2 = I$, and we have
$$
\begin{align}
& \forall \e > 0 \ \exists \ (y_1-\frac{\e}{2}, y_2) \in \mathcal{B}((y_1,y_2), \e) \\
\implies & P_1(y_1 - \frac{\e}{2})+P_2y_2 < P_1y_1+P_2y_2=I \notin S^C
\end{align}
$$
Since $\mathcal{B}((y_1,y_2),\e) \notin S^C$, $S^C$ is not open. $\iff S$ is not closed.

:::


<!---------- 5 ---------->
5. Show that $(0,1)$ is open in $\r$.
(Hint: Find $\delta$ just as Exercise 1. Notice that this is in $\r^1$, so begin with $|z-x|$ instead of $\lVert z-x \rVert$)

:::info
solution by Yu-Chieh Kuo:

Let $x \in (0,1)$ and consider $r = \frac{\min (x, 1-x)}{2}$, which leads to that $\mathcal{B}(x,r) \subseteq (0,1)$.
Thus, we show that $(0, 1)$ is open in $\mathbb{R}$.

:::


<!---------- 6 ---------->
6. Show that the set of all integers is closed.
(Hint. First think about what is the complement of the set of all integers. Then use Theorem 1.23 in Sundaram.)

:::info
solution by Yu-Chieh Kuo:
Since $\mathbb{Z}^C= \bigcup _{n\in \mathbb{Z}}(n, n+1)$, we have that $\r \backslash \mathbb{Z}$ is the union of open intervals, which is also an open set.
Therefore, since $\mathbb{Z}^C$ is open, we show that the set of all integers is closed.

:::
    
:::success
*Theorem 1.23 in Sundaram* (Also Theorem 1 in Lecture note 5)

Let A be an arbitrary index set. Suppose for each $\alpha \in A$, $G_\alpha$ is an open set. Then $\bigcup_{\alpha \in A} G_\alpha$ is also open. That is, the arbitrary union of open sets is open.

:::

<!---------- 7 ---------->
7. Suppose $S_1$ and $S_2$ are convex sets in $\rn$, then $S_1+S_2$ is convex.

::: info
solution by 謝秉儒：
$$
\forall S_{11},S_{12} \in S_1 \ , \pi_1 \in [0,1] \quad \pi_1 \cdot S_{11}+(1-\pi_1)\cdot S_{12} \in S_1\\
\forall S_{21},S_{22} \in S_2 \ , \pi_2 \in [0,1] \quad \pi_2 \cdot S_{21}+(1-\pi_2)\cdot S_{22} \in S_2\\
\therefore \forall a,b \in S_1+ S_2 , \text{we can find }a=s_1'+s_2',b=s_1''+s_2'' \\ \text{where } s_1',s_1'' \in S_1\text{ and }s_2'',s_2'' \in S_2 \\
\text{Therefore, for }\pi_3\in [0,1] \\
\begin{align}
\pi_3 \cdot a+(1-\pi_3)\cdot b & =\pi_3 \cdot (s_1'+s_2') & + (1-\pi_3)\cdot s_1''+s_2''\\
& =\pi_3 \cdot s_1'+(1-\pi_3)\cdot s_1'' & +\pi_3 \cdot s_2'+(1-\pi_3)\cdot s_2''\\
 & \quad \in S_1 & \in S_2
\end{align}
$$

:::
<!---------- 8 ---------->
8. $S=\set[:]{(x,y)}{-1<x<1, y=0}$. Is S a closed set in $\r^2$? Is it bounded? Is it compact?

::: info
solution by 謝秉儒：
Not closed:
$\{(-1+\frac{1}{n},0)\}_{n=1}^{\infty} \rightarrow (-1,0), \text{but} (-1,0) \notin S$
\
Bounded:
For $r\geq1, \ S \in \mathcal{B}((0,0),r)$
\
Not compact:
Because $S$ is not closed, so $S$ is not compact.
:::

<!---------- 9 ---------->
9. $S=\set[:]{(x,y)}{x+y=1}$. Is $S$ a closed set in $\r^2$? Is it bounded? Is it compact?

::: info
solution by 謝秉儒：
Closed:
Define $S^c=S_1:\{(x,y)|x+y<1\} \cup S_2:\{(x,y)|x+y>1\}$
To show S is closed, we should claim $S_1$ and $S_2$ is open.
$\forall (x_1,y_1) \in S_1,$ we need to find a $r$ such that $B((x_1,y_1),r) \subset S_1$
By Distance of Point From a Line in $\mathbb{R}^2$
$d= \frac{|x_1+y_1-1|}{\sqrt{2}}$
$\forall r<d, B((x_1,y_1),r)\subset S_1$
Use the same method to show $S_2$ open.
$\Longrightarrow S$ is closed
\
Not Bounded:
$\forall r\in \mathbb{R},\ \exists s\in S \st s \notin B(0,r)$
$s=(r+1,-r) \quad \because |(r+1,-r),0|=\sqrt{2r^2+2r+1}>r$
\
Not compact:
Because $S$ is not bounded, so $S$ is not compact
:::

<!---------- 10 ---------->
10. The arbitrary union of open sets is open. 

:::info
solution by 邴國榮:
(Proof is already provided by the instructor in the video.)
Let $\textbf{I}$ be an arbitrary index set.
Suppose $x$ is in the union of open sets, that is: $$x \in \bigcup_{i=I} G_i$$ Means that for some $i$, $$x \in G_i \implies \exists r_i > 0, \ \text{such that }B(x, r_i) \subset G_i \subset \bigcup_{i=I} G_i$$ Give $r=\min \{r_i\}$ where $i \in \mathbf{I}$
$$\exists r > 0, \ \text{such that }B(x, r) \subset \bigcup_{i=I} G_i$$
:::
<!---------- 11 ---------->
11. $(\textbf{Sundram q27})$ Let $A = [-1,0)$ and $B = (0, 1]$. Examine whether each of the following statements is true or false.
    (a) $A \cup B$ is compact
    (b) $A+B=\set[:]{x+y}{x \in A, y \in B}$ is compact
    \(c\) $A \cap B$ is compact
    
    $(\textbf{Sundram q32})$ Let $A = \{1,1/2,1/3,...,1/n,...\} \cup \{0\}$. Is $A$ closed? Is it compact?

:::info
(Sundram q27)
solution by 邴國榮:
Use $Theorem\ 5$:$$\text{A set}\ S \subset \rn \text{ is compact} \iff S \text{ is closed and bounded}$$ (a)
$A \cup B=[-1,1]-\{0\}$ is not closed
(b)
$A+B=\set[:]{x+y}{x \in A, y \in B} = (-1,1)$ is not closed
\(c\)
$A \cap B = \phi$ is bounded
Since $\phi^c$ = $\mathbb{R}$ is open, means that $A \cap B$ is closed
Thus, $\textbf{(a) and (b)}$ are not compact, but $\textbf{(c)}$ is
:::
:::info
(Sundram q32)
solution by 邴國榮:
$A = \{1,1/2,1/3,...,1/n,...\} \cup \{0\} \implies A \in [0,1]$
That is, A is bounded in [0,1], and $A^c = \{x\in\mathbb{R}^1 \mid x \notin [0,1]\}$
The definiton of $A^c$ shows that it is open. That is, $A$ is closed (By $Definition\ 3$).
Thus by $Theorem\ 5$, $A = \{1,1/2,1/3,...,1/n,...\} \cup \{0\}$ is compact.
:::
    
<!---------- 12 ---------->
12. A set S is closed if and only if $S=\overline{S}$.
:::info
solution by 邴國榮:
By $Definition\ 7$, it shows that $S \subset \bar{S}$ holds  for all sets.
And by $Theorem\ 3$, a set $S \subset \rn$ is closed $\iff$ it contains all its adherent points. That is, $S \subset \rn$ is closed $\iff S \supset \bar{S}$
Thus, $S \subset \rn$ is closd $\iff S = \bar{S}$ 
:::

<!---------- 13 ---------->
13. If $A$ is open and $B$ is closed, then $A−B$ is open and $B−A$ is closed.

::: info
solution by 陳家威:
$A$ is open $\iff$ $A^c$ is closed.
$B$ is closed $\iff$ $B^c$ is open.

By thrm 1 in L5, *the intersection of a finite collection of open set is open*, and by thrm 2 in L5, *the intersection any collection of closed set is closed.*

Therfore :
$A\cap B^C=\text{open }\cap\text{ open}$ is open; 
$B\cap A^C=\text{closed }\cap\text{ closed}$ is closed.

>Note that $A-B=A\cap B^C$ (in A but not in B), and $B-A=B\cap A^C$ (in B but not in A)
:::
<!---------- 14 ---------->
14. If $x$ is an accumulation point of S, then every $n$-ball $B(x,r)$ contains infinitely many points of S.
:::info
Solution by 陳家威:
>Idea:If we can construct an infinite sequence, where every element is smaller than the given radius, then we prove there contains infinetely many points within $S$.

##### Construction of Sequence
For each $n \in \n$, we pick a point $x_n$ that is inside the ball $B(x,\frac{1}{n})$. By the definition of $x$ being an accumulation point, $B(x, r)\cap S-\{x\}\neq \emptyset \quad (\forall r>0)$, so $x_n$ must exist. Note that $x_n$ must satisfy $d(x, x_n)<\frac{1}{n}$.

We then prove the statement with help of the sequence $\{x_n\}_{n=1}^\infty$. 

##### Proof the Statement
For any r, we choose an index number $k$ such that $r>\frac{1}{k}$. It is obvious that the element $x_k$ must be inside $B(x, \frac{1}{k})$ according to our procedure of construction. We then know that $\{x_n\}_{n=k}^\infty \in B(x, r)\cap S-\{x\}$, hence prove that there contains infinitely many points of S.
:::
<!---------- 15 ---------->
15. Suppose $(S_\alpha)_{\alpha \in A}$ is a collection of convex sets in $\rn$. Then $\bigcap_{\alpha \in A} S_\alpha$ is also convex.

:::info
Let $x,y \in \bigcap_{\alpha \in A}$. We then know that
$$
x \in S_\alpha \quad \forall \alpha \in A \\
y \in S_\alpha \quad \forall \alpha \in A \\
$$
Let $z = \pi x + (1-\pi) y$. Since $S_\alpha$ is convex, we know by definition $z \in S_\alpha, \ \forall \alpha$. Thus $z = \pi x + (1-\pi) y \in \bigcap_{\alpha \in A}$, which proves that $\bigcap_{\alpha \in A}$ is convex.
:::
<!---------- 16 ---------->
16. $L_f(\overline{v})$ is a convex set for every $\overline{v}$ if and only if $f(\theta x^a + (1-\theta)x^b) \le \max\{f(x^a), f(x^b)\}$ for all $x^a$ and $x^b$ and for all $\theta \in [0,1]$.

:::info
($\implies$)
Pick $x_a, x_b$ in $L_f(\bar{v})=\set{x}{f(x) \le \bar{v}}$, we know that $f(x_a) \le \bar{v}$ and $f(x_b) \le \bar{v}$. Since $L_f(\bar{v})$ is convex, $\theta x_a + (1-\theta) x_b \in L_f(\bar{v})$ and $f (\theta x_a + (1-\theta) x_b ) \le \bar{v}$.
Let $\bar{v} = \max\{f(x_a), f(x_b)\}$, we then get
$$
f (\theta x_a + (1-\theta) x_b ) \le \max\{f(x_a), f(x_b)\}
$$

($\impliedby$)
Pick $x_a, x_b \in L_f(\bar{v})$, then $f(x_a) \le \bar{v}$ and $f(x_b) \le \bar{v}$. Consequently, $\max\{f(x_a), f(x_b)\} \le \bar{v}$. Hence

$$
f (\theta x_a + (1-\theta) x_b ) \le \max\{f(x_a), f(x_b)\} \le \bar{v}
$$
:::
