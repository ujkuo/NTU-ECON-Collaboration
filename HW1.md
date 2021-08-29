# HW1

[![hackmd-github-sync-badge](https://hackmd.io/I5CpqKyjQ-6MdT3L03N0mw/badge)](https://hackmd.io/I5CpqKyjQ-6MdT3L03N0mw)


<style>
p{
line-height:1.7em;
}
.markdown-body >*{
font-family: Georgia;
}
</style>

$$
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




<!-- -------1-1----------------- -->

1. Let $f$ be a function from $\rn$ to $\rm$, and $A\subset \rn$ and $B\subset \rm$. Define $f^{-1}(B)=\set{a\in\rn}{f(a)\in B}$. Show that for any subsets $A_{1}, A_{2}$ of $\rn$ and $B_{1}, B_{2}$ of $\rm$.
   * $f\left(A_{1} \cap A_{2}\right) \subseteq f\left(A_{1}\right) \cap f\left(A_{2}\right)$ 
    
   :::info
   solution by 陳家威:
   Assume $b \in f(A_1 \cap A_2)$, 
   $$
   \begin{align}
   \implies &\exists a \in A_1 \cap A_2 \st f(a)=b \\
   \implies &\exists a \in A_1 \st f(a)=b \qtext{and} \\
   &\exists a \in A_2 \st f(a)=b\\
   \implies & b=f(a)\in f(A_1) \qtext{and}\\
   & b=f(a)\in f(A_2) \\
   \color{red}{{}^*\implies} &b \in f(A_1) \cap f(A_2)
   \end{align}
   $$
   Since an element $b$ in $f(A_1 \cap A_2)$ is also in  $f(A_1) \cap f(A_2)$, we conclude that 
   $$f(A_1 \cap A_2) \subseteq f(A_1) \cap f(A_2)
   $$
   This is the ***choose-an-element*** method.
   ::: 
      :::warning
   Notice that the other direction,  $f\left(A_{1} \cap A_{2}\right) \supseteq f\left(A_{1}\right) \cap f\left(A_{2}\right)$, is not generally true. Consider $A_1=\{0\}, A_2=\{1\}$ and $f(x)=0$ for all $x\in \mathbb{R}$. We have LHS$=\emptyset$ but RHS$=\{0\}$.
   
   This can be observed in the proof at the last step ($\color{red}{{}^*\implies}$), where 
   $$
   \begin{align}
       b\in f(A_1) \cap f(A_2)
       \implies& b=f(a_1)\in f(A_1) \qtext{and} b=f(a_2)\in f(A_2)\\
       \;\not\!\!\!\implies& b=f(a)\in f(A_1) \qtext{and} b=f(a)\in f(A_2)
    \end{align}
   $$
   
   Only when the function is one-to-one(a.k.a injective), as *HW2-1* suggests, will $b=f(a_1)=f(a_2)=f(a)$, and ${}^*\implies$ becomes ${}^*\iff$
    :::
   
   <!--1-2 ------------------------ -->
   
   * $f^{-1}\left(B_{1} \cup B_{2}\right)=f^{-1}\left(B_{1}\right) \cup f^{-1}\left(B_{2}\right)$
    :::info
    solution by 陳家威:
    We first note a trivial fact. By definition
    $$
    f^{-1}(B)=\set{a\in\rn}{f(a)\in B}
    $$
    If we can find $a\in\rn$ such that $f(a)\in B$, we immediately know (by definition), that $a\in f^{-1}(B)$. Therefore, 
    $$
    f(a) \in B \iff a\in f^{-1}(B)
    $$
    
    We then proceed to our proof. 
    Assume $a \in f^{-1}(B_1 \cup B_2)$, 
    $$
    \begin{align}
    a & \in f^{-1}(B_1 \cup B_2)  \\ 
    &\iff f(a)\in B_1 \cup B_2 \\
    &\iff f(a)\in B_1 \qtext{or} f(a) \in B_2\\
    &\iff a\in f^{-1}(B_1) \qtext{or} a\in f^{-1}(B_2) \\
    &\iff a \in f^{-1}(B_1) \cup f^{-1}(B_2)
    \end{align}
    $$
    The ***if and only if*** condition ensures that $f^{-1}(B_1 \cup B_2) \subseteq f^{-1}(B_1) \cup f^{-1}(B_2)$ and $f^{-1}(B_1) \cup f^{-1}(B_2) \subseteq f^{-1}(B_1 \cup B_2)$. Therefore proves the equallity of two sets.
    :::
    
    <!--1-3 ------------------------ -->
   * $f^{-1}\left(B_{1} \cap B_{2}\right)=f^{-1}\left(B_{1}\right) \cap f^{-1}\left(B_{2}\right)$
   :::info
   solution by 陳家威:
   We follow the same logic as HW1-2, since $f(a) \in B \iff a\in f^{-1}(B)$ holds.
   
   Assume $a \in f^{-1}(B_1 \cap B_2)$, 
    $$
    \begin{align}
    & a \in f^{-1}(B_1 \cap B_2)   \\ 
    &\iff f(a)\in B_1 \cap B_2 \\
    &\iff f(a)\in B_1 \qtext{and} f(a) \in B_2\\
    &\iff a\in f^{-1}(B_1) \qtext{and} a\in f^{-1}(B_2) \\
    &\iff a \in f^{-1}(B_1) \cap f^{-1}(B_2)
    \end{align}
    $$
   :::
   
   <!--1-4 ------------------------ -->
   * $A_{1} \subseteq f^{-1}\left(f\left(A_{1}\right)\right)$
   
   :::warning
    Notice that $A_1 \supseteq f^{-1}\left(f\left(A_{1}\right)\right)$ is not generally true. Consider $A_1=\{0\}$ and $f(x)=0$ for all $x\in \mathbb{R}$. We have LHS$=\{0\}$ but RHS$=f^{-1}\left(\{0\}\right)=\mathbb{R}$.
   :::
   
   :::info
   solution by 陳家威:
   Same procedure as above. We first pick an element from  $A_1$. Assume $a \in A_1$:
   $$
   a \in A_1 \implies \exists b \in f(A_1) \st f(a)=b
   $$
   (trivial by taking $b$ as $a$ itself)
   Note, however, the definition for $f^{-1}(f(A_1))$ (which is an preimage):
   $$
   f^{-1}(f(A_1))=\set{\alpha \in \rn}{\exists \beta \in f(A_1) \st f(\alpha)=\beta}
   $$

    The definition straightforwardly guarantees that $a \in f^{-1}(f(A_1))$. Thus $A_{1} \subseteq f^{-1}\left(f\left(A_{1}\right)\right)$
   :::
   
   <!--1-5 ------------------------ -->
   * $f\left(f^{-1}\left(B_{1}\right)\right) \subseteq B_{1}$.
   
   :::warning
   Notice that $f\left(f^{-1}\left(B_{1}\right)\right) \supseteq B_{1}$ is not generally true. Consider $B_1=\{0,1\}$ and $f(x)=0$ for all $x\in \mathbb{R}$. We have LHS$=f(\mathbb{R})=\{0\}$ but RHS$=\{0,1\}$.
   :::
  
   :::info
   solution by 陳家威: 
   (Proof is already provided by the instructor in the video.)
   Assume $b \in f(f^{-1}(B_1))$. By its definition:
   $$
   f(f^{-1}(B_1))=\set{\beta \in \rm}{\exists \alpha \in f^{-1}(B_1) \st f(\alpha) = \beta}
   $$
   we get $b \in f(f^{-1}(B_1)) \iff \exists a \in f^{-1}(B_1) \st f(a) = b$
   But (recall HW 1-2) 
   $$
   a \in f^{-1}(B_1) \iff f(a)\in B_1
   $$
   We obtain that $b=f(a)\in B_1$, which completes our proof.
   :::
   
   
   <!--2-1 ------------------------ -->
   
2. Let $f$ be a function from $\rn$ to $\rm$, and $f$ is one-to-one on $\rn$.
   *  $f(A_{1}\cap A_{2})=f(A_{1})\cap f(A_{2})$ for all subsets $A_{1}$ and $A_{2}$ in $\rn$.
   :::info
   solution by 羅偉駿:
   Take $a_0\in f(A_{1})\cap f(A_{2})$
   
   \begin{align}
   \iff &a_0 \in \set{a}{\exists x \in A_{1}, \text{ s.t. } f(x) = a} \qtext{and} \\
   &a_0 \in \set{a}{\exists x \in A_{2}, \text{ s.t. } f(x) = a} \\
   \iff &\exists x_1 \text{ s.t. }f(x_1) = a_0  \qtext{and}\\ 
   &\exists x_2 \text{ s.t. }f(x_2) = a_0 \\
   \end{align}
   
   because of <span style="color:red">one-to-one</span>,
   \begin{align}
   &\color{red}{{}\iff} \exists x_1  = x_2 \in A_1 \cap A_2 \text{ s.t. } f(x_1) = a_0 \\
   &\iff a_{0} \in  \set{a}{\exists x \in A_{1}\cap A_{2}, \text{ s.t. } f(x) = a} \\
   \end{align}
   
   Therefore,
   $$
   a_0 \in f(A_{1}\cap A_{2})
   $$
   
   :::
   
   <!--2-2 ------------------------ -->
   
   * $f^{-1}(f(A))=A$ for every subset $A$ in $\rn$.
   :::info
   solution by 羅偉駿:
   Take $a_1 \in f^{-1}(f(A))$
   \begin{align}
   &\iff a_{1} \in  \set{a}{f(a) \in f(A)} \\
   &\iff f(a_1) \in f(A)  \\
   &\iff f(a_1) \in \set{a}{\exists x \in A , \text{ s.t. } f(x) = a} \\
   &\iff \exists x \in A , \text{ s.t. } f(x) = f(a_1)
   \end{align}
   Because of one-to-one,
   \begin{align}
   &\iff \exists x \in A , \text{ s.t. } x = a_1 \\
   &\iff a_1 \in A
   \end{align}
   Therefore,
   $$
   f^{-1}(f(A)) = A
   $$
   :::

   
   <!--3-1 ------------------------ -->
   
3. Find the domain and range of following functions.
   * For all $x$ in $[-3,3$), $F(x)=(x+1)^{2}.$
   :::info
   solution by 鄭宗弘:   $D(F)=[-3,3),\ R(F)=[0,16)$
   :::
   
   <!--3-2 ------------------------ -->
   * For all $x$ in $\mathbb{R}$, $F(x) = 2^{x}.$
   :::info
   solution by 鄭宗弘: $D(F)=\mathbb{R},\ R(F)=\mathbb{R}^+$
   :::
   
   <!--4-1 ------------------------ -->
   
4. The functions $F$ and $G$ are defined as follows. Verify that $R(F)\subseteq D(G)$, and find the domain and range of $(G\circ F)(x).$  Find a formula for $(G\circ F)(x).$ $F(x)=x^{2}-2, x\in \mathbb{R}$; $G(x) = -x + 1, x\in \mathbb{R}.$
   :::info
   solution by 鄭宗弘: 
   $R(F)=[-2,\infty)\subseteq\mathbb{R}=D(G)$
   $(G\circ F)(x)=G(F(x))=-F(x)+1=-(x^2-2)+1=-x^2+3$
   Hence, $D(G\circ F)=\mathbb{R},\ R(G\circ F)=(-\infty,3]$.
   :::
   
   <!--5-1 ------------------------ -->
   
   
5. Consider $F(x)=x^{2}-2, x\in \mathbb{R}$; $G(x)=-x+1, x\in \mathbb{R}$. Check whether each of the two functions is a one-to-one function.
   :::info
   solution by 鄭宗弘:
   $F$ is clearly not one-to-one, to be more direct, $F(1)=F(-1)$.
   $G$ is one-to-one: We want to show that $G(x_1)=G(x_2)\implies x_1=x_2$
   Say there is $x_1,x_2\in\mathbb{R}$ with $G(x_1)=G(x_2)$.    We obtain that $-x_1+1=-x_2+1$, and so $x_1=x_2$. Done!
   :::
   


