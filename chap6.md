# \godel's Second Incompleteness Theorem

## Peano Arithmetic and $I\Sigma_1^0$

**Peano Arithmetic** = **Robinson Arithmetic** + **induction**

1. $\forall x. Sx \neq 0$
2. $\forall x \exists y (x \neq 0 \to Sy = x)$
3. $\forall x \forall y (Sx = Sy \to x = y)$
4. $\forall x. x + 0 = x$
5. $\forall x \forall y (x + Sy = S(x + y))$
6. $\forall x. x \cdot 0 = 0$
7. $\forall x \forall y (x \cdot Sy = (x \cdot y) + x)$

**axiom schema (induction)** $((\phi_{[0/x_0]} \land \forall x_0 (\phi
  \to \phi_{[Sx_0/x_0]})) \to \forall x_0 \phi$.


\begin{example}
In Robinson arithemtic, we cannot prove addition is commutative. We can prove it
in Peano arithmetic.
\end{example}


\begin{example}
Any two terms are comparable in Peano arithmetic.
\end{example}


\begin{example}
Addition is associative in Peano arithemtic.
\end{example}


\begin{example}
Multiplication is commutative in Peano arithmetic.
\end{example}

\begin{example}
Multiplication distributes over addition in Peano arithmetic.
\end{example}

\begin{example}
Multiplication is associative in Peano arithemtic.
\end{example}


\begin{proposition}
The theory $Rob. + I\Sigma_0^1$ proves that:

\begin{enumerate}
\item addition is commutative and associative
\item multiplication is commutative and associative
\item multiplication distributes over addition
\end{enumerate}

\end{proposition}


## The Arithmetical Hierarchy

\begin{definition}[$\Delta_0^0$-formula]
The set of $\Delta_0^0$-formula is the least that:
\begin{enumerate}
\item contains all atomic formulas: $t_0 = t_1$
\item is closed under conjunction, disjunction and negation
\item is closed under bounded quantification:
\[
\phi \in \Delta_0^0 \text{ and } t \text{ is a term } \longrightarrow \forall x < t. \phi \text{ and } \exists x < t. \phi \text{ are both in } \Delta_0^0.
\]
\end{enumerate}
\end{definition}


\begin{definition}[Arithemtic Hierarchy]
The hierarchy of formula from arithmetic is defined by induction on $n \in \mathbb{N}$:

\begin{enumerate}
\item $\Sigma_0^0 = \Pi_0^0 = \Delta_0^0$
\item $\phi \in \Pi_n^0 \longrightarrow \exists x_1 \dots \exists x_k \phi \in \Sigma_{n + 1}^0$
\item $\phi \in \Sigma_n^0 \longrightarrow \forall x_1 \dots \forall x_k \phi \in \Pi_{n + 1}^0$
\item $\Delta_{n + 1}^0 = \Sigma_{n + 1}^0 \cap \Pi_{n + 1}^0$
\end{enumerate}
\end{definition}

\begin{remarks}
All the classes defined above are closed under finite conjunction and disjunction.
\end{remarks}


\begin{example}
\hfill

(1) $x_0 < S(x_2 \cdot Sx_1) \longrightarrow \forall y \le x_3 y + x_0 = x_3 \quad \in \Delta_0^0$ \\
(2) $\forall x \forall y (x \cdot Sy = (x \cdot y) + x) \quad \in \Pi_1^1$ \\
(3) $\forall x \exists y (x \neq 0 \longrightarrow Sy = x) \quad \in \Pi_2^0 $
\end{example}


\begin{proposition}

Given any $n \in \mathbb{N}$ and any $\Sigma_1^0$-formula $\phi =
\exists x_0 \dots x_n \psi$ where $\psi \in \Delta_0^0$, then there
exists some $\Delta^0_0$-formula $\psi'$ such that:
\[
Rob. \vdash_c \exists x_0 \dots x_n \psi \longleftrightarrow \exists x \psi'.
\]

\end{proposition}



\begin{proposition}

Given any $\Sigma_{n + 1}^0$ formula $\phi$ and $\Pi_{n + 1}^0$
formula $\theta$, there exists $\Sigma_{n + 1}^0$ formula $\phi'$ and
$\Pi_{n + 1}^0$ formula $\theta'$ such that:

\begin{itemize}
\item $Rob. \vdash_c \phi \longleftrightarrow \phi'$
\item $Rob. \vdash_c \theta \longleftrightarrow \theta'$
\end{itemize}

where $\phi'$ and $\theta'$ have alternating quantifiers of length 1.

\end{proposition}


\begin{proposition}
Given any term $t$ that does not contain the variable $z$, and any formula
$\psi$, then we have:

\begin{enumerate}
\item $\exists y \le t. \exists z. \psi \longleftrightarrow \exists z. \exists y \le x. \psi$
\item $\forall y \le t. \forall z. \psi \longleftrightarrow \forall z. \forall y \le x. \psi$
\end{enumerate}
\end{proposition}


\begin{proposition}
Given any term $t$ that does not contain the variable $z$, and any formula
$\psi$, then there exsits $\psi'$:

\begin{enumerate}
\item $\exists y \le t. \forall z. \psi \longleftrightarrow \forall z. \exists y \le x. \psi'$
\item $\forall y \le t. \exists z. \psi \longleftrightarrow \exists z. \forall y \le x. \psi'$
\end{enumerate}
\end{proposition}


\begin{theorem}
Every total recursive function is representable by some $\Sigma_1^0$ formula.
\end{theorem}


## A First Glance at \godel's Second Incompleteness Theorem

We consider the following primitive recursive function $diag :
\mathbb{N} \to \mathbb{N}$.
$$
diag(n) =
\begin{cases}
\ulcorner \phi_{[\ulcorner \phi \urcorner / x_0]} \urcorner  & \text{ if } n = \ulcorner \phi \urcorner \in \mathcal{F}_{\checkmark x_0 !free} \\
0 & \text{ otherwise }
\end{cases}
$$

together with any $\Sigma_1^0$-formula $\phi_{diag}(x_0, x_1)$
that represents $diag$. This means we have for all $n \in \mathbb{N}$:
$$
Rob. \vdash_c \forall x_0 (diag(n) = x_0 \longleftrightarrow \phi_{diag}(x_0, n)).
$$

We define the $\Sigma_1^0$-formula $\Xi(x_0)$ by
$$
\Xi(x_0) = \exists x_1 \exists x_2 (\phi_{proof_T}(x_1, x_2) \land \phi_{diag}(x_2, x_0))
$$


\begin{proposition}
For every integer $n$ we have
$$
\mathbb{N} \models \Xi(n) \quad \Longleftrightarrow \quad Rob. \vdash_c \Xi(n).
$$
\end{proposition}


\begin{proposition}
$Rob. \vdash_c \Xi_{[\ulcorner \neg \Xi \urcorner / x_0]} \longleftrightarrow \exists x_1 \phi_{proof_T}(x_1, \ulcorner \neg \Xi_{[\ulcorner \neg \Xi \urcorner / x_0]} \urcorner).$
\end{proposition}


\begin{proposition}
If $Rob. \supseteq T$ is consistent, then $T \not \vdash_c \neg \Xi_{[\ulcorner \neg \Xi \urcorner / x_0]}.$
\end{proposition}



\begin{proposition}
\begin{equation*}
\left[\begin{array}{c}
    Rob. \\
    \Xi_{[\ulcorner \neg \Xi \urcorner / x_0]} \longrightarrow \exists x_1 \phi_{proof_{Rob.}} (x_1, \ulcorner \Xi_{[\ulcorner \neg \Xi \urcorner / x_0]} \urcorner)
 \end{array}
 \right]
 \vdash_c
 \Xi_{[\ulcorner \neg \Xi \urcorner / x_0]} \longrightarrow \neg cons(T).
\end{equation*}

where $\neg const(T)$ stands for the formula:
\[
\exists \phi (\exists x_0 \phi_{proof_T}(x_0, \ulcorner \phi \urcorner) \land \exists x_0 \phi_{proof_T}(x_0, \ulcorner \neg \phi \urcorner) ).
\]

\end{proposition}


\begin{lemma}
Let $T \supseteq Rob.$ be any consistent recursive theory, if we have
$$
T \vdash_c \Xi_{[\ulcorner \neg \Xi \urcorner / x_0]} \longrightarrow \exists x_1 \phi_{proof_{Rob.}}(x_1, \ulcorner \Xi_{[\ulcorner \neg \Xi \urcorner / x_0]} \urcorner)
$$
then it's impossible to prove consistency of the theory inside the theory, i.e.:
$$
T \not \vdash_c const(T).
$$

\end{lemma}


## The Core of the Proof

\begin{lemma}
Let $\phi$ be any closed $\Sigma_1^0$-formula, then we have
$$
Rob. + I\Sigma_1^0 \vdash_c \phi \longrightarrow \exists x_1 \phi_{proof_{Rob.}} (x_1, \ulcorner \phi \urcorner).
$$
\end{lemma}

*Proof idea:* Lemma 187 and 188.

\begin{lemma}
Let $\phi$ be any closed $\Sigma_1^0$-formula, then we have
$$
Rob. + I\Sigma_1^0 \vdash_c \phi  \quad  \Longleftrightarrow \quad Rob. + I\Sigma_1^0 \vdash_c \exists x_1 \phi_{proof_{Rob.}} (x_1, \ulcorner \phi \urcorner).
$$
\end{lemma}

*Proof idea:*

- $\Leftarrow$: trivial, from existence of proof we can construct an actual proof in the standard model $\mathbb{N}$ by resorting to *soundness theorem*.
- $\Rightarrow$:
    - prove $\mathbb{N} \models \exists x_1 \phi_{proof_{Rob.}} (x_1, \ulcorner \phi \urcorner)$ by induction on the shape of $\phi$.
    - prove every model $\mathcal{M}$ of $Rob. + I\Sigma_1^0$ that $\mathcal{M} \models \exists x_1 \phi_{proof_{Rob.}} (x_1, \ulcorner \phi \urcorner)$
        - every model $\mathcal{M}$ is a final extension of a structure isomorphic to $\mathbb{N}$.
    - immediate by *completeness theorem*

Note that here the word *complete* in *completeness theorem*, which,
together with *soundness theorem* means that:

> There is a formal proof of s in T if and only if s is satisfied by every model of T.

It establishes the correspondancy between semantics of a langauge and
its proof system. \godel \ incompleteness theorem cares about whether
all theorems of a theory can be proved.

*Incompleteness* is also different from *undecidability* of a
theory. A theory can be undecidable, but all theorems are
provable. \godel \ proved that for any consistent recursive theory
which is stronger than Robinson arithemtic, there are some theorems
that escape any efforts of proof, either systematic or ad-hoc. That
means even God can't prove them, as proving them will result in
contradictions.

\begin{definition}[Final Extension]

Let $\mathcal{M}$ and $\mathcal{N}$ be two models of $Rob.$, such that
$\mathcal{M}$ is a substructure of $\mathcal{N}$.  $\mathcal{N}$ is a
final extension of $\mathcal{M}$ if and only if for every $a \in
\lvert \mathcal{M} \rvert$ and $b \in \lvert \mathcal{N} \rvert$ we
have:

\begin{enumerate}
\item $\mathcal{N} \models b \le a \quad \Longrightarrow \quad b \in \lvert \mathcal{M} \rvert$
\item $b \notin \lvert \mathcal{M} \rvert \quad \Longrightarrow \quad a \le b$.
\end{enumerate}
\end{definition}


\begin{lemma}

If $\mathcal{N}$ is a model of $Rob.$, then the substructure
$\mathcal{M}$ whose domain is
\[
\lvert \mathcal{M} \rvert = \{ n^{\mathcal{N}} \mid n \in \mathcal{N} \}
\]
is isomorphic to the standard model $\mathcal{N}$.
\end{lemma}



\begin{lemma}
Up to isomorphism, every model $\mathcal{N}$ of $Rob.$ is a final extension of
the standard model $\mathbb{N}$.
\end{lemma}


\begin{proposition}
Let $\phi$ be any closed $\Sigma_1^0$-formula:
\[
\mathbb{N} \models \phi \longleftrightarrow \exists x_1 \phi_{proof_{Rob.}}(x_1, \ulcorner \phi \urcorner).
\]
\end{proposition}


\begin{corollary}
If the Goldbach conjecture is neither provable nor disprovable, then it holds true in $\mathbb{N}$.
\end{corollary}


Note: The corollary above seems problematic to me. If Goldbach is
true, then by Lemma 185 it would be provable, a contradiction.


\begin{lemma}
Let $t_{[x_1, \dots, x_n]}$ be any $\mathcal{L}_A$-term (where $\mathcal{L}_A = \{ 0, S, +, \cdot \}$):
\[
Rob. + I\Sigma^0_1 \vdash_c
\forall x_1 \dots x_{n + 1} (t_{[x_1, \dots, x_n]} = x_{n + 1} \longrightarrow \exists x_0 (x_0, \ulcorner t_{[x_1, \dots, x_n]} = x_{n + 1} \urcorner))
\]
\end{lemma}


*Proof idea*: Induction on the height of the term $t_{[x_1, \dots, x_n]}$.


\begin{lemma}
The set of all formula $\phi$ that satisfy
\[
Rob. + I\Sigma^0_1 \vdash_c
\forall x_1 \dots x_{n + 1} (\phi_{[x_1, \dots, x_n]} \longrightarrow \exists x_0 (x_0, \ulcorner \phi_{[x_1, \dots, x_n]} \urcorner))
\]
is closed under

\begin{enumerate}
\item conjunction
\item disjunction
\item existential quantification
\item bounded universal quantification
\end{enumerate}
\end{lemma}



\begin{theorem}[\godel's second incompleteness theorem]
Let $T \supseteq Rob. + I\Sigma_1^0$ be any consistent recursive theory:
\[
T \not \vdash_c const(T)
\].
\end{theorem}
