\underline{\textsc{DFA and NFA}}

- **Deterministic Finite Automaton**: A \textit{deterministic finite automaton} (DFA) is a 5-tuple $(Q, \Sigma, \delta, q_0, F)$
- **Equivalence DFA & NFA**: Let $Q' = \mathcal{P}(Q)$, $F' = \{ S \subseteq Q \mid S \cap F \neq \oslash \}$,
$\delta'(S, a) = \{ q' \in Q \mid \exists q \in S q \xrightarrow{\epsilon^*a\epsilon^*} q' \}$
and $q'_0 = \{ q_0 \}$.
- **Closure**: Regular languages are closed under *union*, *intersection*, *complement*, *concatenation* and *star*.
- **Regular Expression = Regular Language**: The proof depends on *Generalized-NFA*, the transitions
of which are labelled with regular expressions. The idea is to reduce
any DFA into a 2-state Generalized-NFA.
- **Pumping Lemma**: $\exists p = \lvert s \rvert$, such that $s = xyz$, (1) $\forall i \ge 0$, $xy^iz \in A$; (2) $\lvert y \rvert > 0$; (3) $\lvert xy \rvert \le p$.

\underline{\textsc{PDA}}

- **Pushdown Automaton**: A pushdown automaton (PDA) is a 6-tuple $(Q, \Sigma, \Gamma, \delta, q_0, F)$.
- **Context-Free Grammar**: A context-free grammar is a 4-tuple $(V, \Sigma, R, S)$. V - variables, R - rules, S - start variable, $\Sigma$ - terminals.
- **PDA = CFG**: $CFG \Rightarrow PDA$: Put the start variable $S$ on stack, non-deterministically expand rules. $PDA \Rightarrow CFG$:
      1. Construct an equivalent P such that:
          - P has a single accepting state
          - It empties stack before accepting
          - Each transition either pushes a symbol or pops one, but never both
      2. Now construct the grammar as follows:
          - $V = \{ A_{pq} \mid p, q \in Q \}$
          - the start variable is $A_{q_0, q_{acc}}$
          - $A_{pq} \to aA_{rs}b$ if $(r, t) \in \delta(p, a, \epsilon)$ and $(q, \epsilon) \in \delta(s, b, t)$
          - $A_{pq} \to A_{pr}A_{rq}$ if $p, q, r \in Q$
          - $A_{pp} \to \epsilon$ for each $p \in Q$

- The class of context-free languages is closed under _union_,
_concatenation_, and _star_, but NOT under _intersection_ or
_complement_.
- Let $C$ be a context-free language and $R$ be a regular language,
   then $C \cap R$ is context free.
- **Pumping Lemma**: $\exists p = \lvert s \rvert$, such that $s = vwxyz$, (1) $\forall i \ge 0$, $vw^ixy^iz \in A$, (2) $\lvert wy \rvert > 0$, (3) $\lvert wxy \rvert \le p$.
- The language $\{ a^nb^nc^b \mid n \in \mathbb{N} \}$ is not context-free.

\underline{\textsc{Turing Machines}}

- **Deterministic Turing Machine**: A deterministic Turing Machine is a 7-tuple $(Q, \Sigma, \Gamma, \delta, q_0, q_{acc.}, q_{rej.})$.
- **Configuration**: $q_0w$, $w_0q_{acc.}w_1$, $w_0q_{rej.}w_1$.
- **The Halting Problem**: $\{  ^\ulcorner \mathcal{M}^\urcorner w \in \{0, 1\}^* \mid \mathcal{M} \text{ is a TM accepts } w  \}$. Construct $\mathcal{H}$ based on $\mathcal{D}$ for the given input $w$:

    1. if $\mathcal{D}$ accepts $ww$, $\mathcal{H}$ rejects $w$
    2. if $\mathcal{D}$ rejects $ww$, $\mathcal{H}$ accepts $w$

    Now the question is: does $\mathcal{H}$ accept $^\ulcorner \mathcal{H}^\urcorner$?

\begin{multicols}{2}

\textbf{Decidable}

$A_{DFA} = \{ \langle B, w \rangle \mid B \text{ is a DFA accepts } w  \}$ \\
$A_{NFA} = \{ \langle B, w \rangle \mid B \text{ is a NFA accepts } w  \}$ \\
$A_{REX} = \{ \langle R, w \rangle \mid R \text{ is a regular expression generates } w  \}$ \\
$E_{DFA} = \{ \langle A \rangle \mid A \text{ is a DFA and } \mathcal{L}(A) = \oslash  \}$ \\
$EQ_{DFA} = \{ \langle A, B \rangle \mid A, B \text{ are DFAs and } \mathcal{L}(A) = \mathcal{L}(B)  \}$ \\
$A_{CFG} = \{ \langle G, w \rangle \mid G \text{ is a CFG generates } w  \}$ \\
$E_{CFG} = \{ \langle G \rangle \mid G \text{ is a CFG and } \mathcal{L}(G) = \oslash  \}$ \\
Every context-free language is decidable \\

\textbf{Undecidable}

$A_{TM} = \{ \langle M, w \rangle \mid M \text{ is a TM and } M \text{ accepts } w  \}$ \\
$E_{TM} = \{ \langle M \rangle \mid M \text{ is a TM and } \mathcal{L}(M) = \oslash  \}$ \\
$EQ_{TM} = \{ \langle M_1, M_2 \rangle \mid M_1, M_2 \text{ are TMs and } \mathcal{L}(M_1) = \mathcal{L}(M_2)  \}$ \\
$REGULAR_{TM} = \{ \langle M \rangle \mid M \text{ is a TM and } \mathcal{L}(M) \text{ is  a regular language }  \}$

\end{multicols}


\underline{\textsc{Recursive Functions}}

\begin{proposition}[Closed under bounded quantification]

The set of all primitive recursive predicates is closed under bounded
quantification, i.e. if $A \subseteq \mathbb{N}^{p + 1}$ is primitive
recursive, then the following two sets as well:

(1) $\{ (\vec{x}, z) \mid \exists t \le z (\vec{x}, t) \in A \}$
(2) $\{ (\vec{x}, z) \mid \forall t \le z (\vec{x}, t) \in A \}$

\end{proposition}

\underline{\textsc{Representing Functions}}

Let $A \subseteq \mathbb{N}^n$ and $\phi(x_1, \dots, x_n)$ be any
$\mathcal{L}_A$-formula whose free variables are among $x_1, \dots,
x_n$.  $\phi(x_1, \dots, x_n)$ represents the set $A$ if for all $i_1,
\dots, i_n \in \mathbb{N}$ we have:
$(i_1, \dots, i_n) \in A \Longrightarrow \texttt{Rob.} \vdash_c \phi(i_1, \dots, i_n)$ and
$(i_1, \dots, i_n) \notin A \Longrightarrow \texttt{Rob.} \vdash_c \neg \phi(i_1, \dots, i_n)$


\underline{\textsc{\godel's First Incompleteness Theorem}}

\begin{lemma}

For all primitive recursive functions $h : \mathbb{N}^{n + p + 1} \to \mathbb{N},
g : \mathbb{N}^n \to \mathbb{N}, k_1, \dots, k_p : \mathbb{N} \to \mathbb{N}$,
such that every integer $y > 0$: $\bigwedge_{0 < i \le p} k_i(y) < y$, the function $f : \mathbb{N}^{n + 1} \to \mathbb{N}$ defined by:
\begin{enumerate}
\item $f(\vec{x}, 0) = g(\vec{x})$
\item $f(\vec{x}, y + 1) = h(f(\vec{x}, k_1(y)), \dots, f(\vec{x}, k_p(y)), \vec{x}, y, f(\vec{x}, y))$
\end{enumerate}

is also primitive recursive.
\end{lemma}

\begin{proposition}
Given any theory $T$, $\{ \ulcorner \psi \urcorner \mid \psi \in T \} \text{ is recursive } \Longrightarrow \{ \ulcorner \phi \urcorner \mid T \vdash_c \phi \} \text{ is recursively enumerable }$.
\end{proposition}

\begin{theorem}
Let $T \supseteq Rob.$ be any theory, $T$ is consistent $\Longleftrightarrow$ $T$ is undecidable.
\end{theorem}

*Proof idea*: The idea is similar to the proof of undecidability of
the halting problem. Suppose $T$ is decidable, then the following set
$\mathcal{C}$ is decidable as well:
$\mathcal{C} = \{ \ulcorner H \urcorner \mid T \vdash_c \neg H(\ulcorner H \urcorner) \}$

Note that in the above $H$ contains one free variable. As $\mathcal{C}$ is
decidable, there exists one formula $\phi(x_0)$ in Robinson arithemtic
represents it, i.e.:

$k \in \mathcal{C} \quad \Longleftrightarrow \quad Rob. \vdash_c \phi(k) \quad  \Longleftrightarrow \quad T \vdash_c \phi(k)$.
Now we have: $T \vdash_c \phi(\ulcorner \phi \urcorner) \quad  \Longleftrightarrow \quad \ulcorner \phi \urcorner \in \mathcal{C} \quad \Longleftrightarrow \quad T \vdash_c \neg \phi(\ulcorner \phi \urcorner)$.


\underline{\textsc{\godel's Second Incompleteness Theorem}}

\begin{definition}[$\Delta_0^0$-formula]
The set of $\Delta_0^0$-formula is the least that:
(1) contains all atomic formulas: $t_0 = t_1$
(2) is closed under conjunction, disjunction and negation
(3) is closed under bounded quantification:
$\phi \in \Delta_0^0 \text{ and } t \text{ is a term } \longrightarrow \forall x < t. \phi \text{ and } \exists x < t. \phi \text{ are both in } \Delta_0^0$.
\end{definition}

\begin{proposition}

Given any $n \in \mathbb{N}$ and any $\Sigma_1^0$-formula $\phi =
\exists x_0 \dots x_n \psi$ where $\psi \in \Delta_0^0$, then there
exists some $\Delta^0_0$-formula $\psi'$ such that:
\[
Rob. \vdash_c \exists x_0 \dots x_n \psi \longleftrightarrow \exists x \psi'.
\]
\end{proposition}
$$
diag(n) =
\begin{cases}
\ulcorner \phi_{[\ulcorner \phi \urcorner / x_0]} \urcorner  & \text{ if } n = \ulcorner \phi \urcorner \in \mathcal{F}_{\checkmark x_0 !free} \\
0 & \text{ otherwise }
\end{cases}
$$
$$
Rob. \vdash_c \forall x_0 (diag(n) = x_0 \longleftrightarrow \phi_{diag}(x_0, n)).
$$
$$
\Xi(x_0) = \exists x_1 \exists x_2 (\phi_{proof_T}(x_1, x_2) \land \phi_{diag}(x_2, x_0))
$$

\begin{proposition}
For every integer $n$ we have
$\mathbb{N} \models \Xi(n) \quad \Longleftrightarrow \quad Rob. \vdash_c \Xi(n)$.
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
$\exists \phi (\exists x_0 \phi_{proof_T}(x_0, \ulcorner \phi \urcorner) \land \exists x_0 \phi_{proof_T}(x_0, \ulcorner \neg \phi \urcorner) )$.

\end{proposition}

\begin{lemma}
Let $\phi$ be any closed $\Sigma_1^0$-formula, then we have
$Rob. + I\Sigma_1^0 \vdash_c \phi \longrightarrow \exists x_1 \phi_{proof_{Rob.}} (x_1, \ulcorner \phi \urcorner)$.
\end{lemma}

\begin{lemma}
Let $\phi$ be any closed $\Sigma_1^0$-formula, then we have
$Rob. + I\Sigma_1^0 \vdash_c \phi  \quad  \Longleftrightarrow \quad Rob. + I\Sigma_1^0 \vdash_c \exists x_1 \phi_{proof_{Rob.}} (x_1, \ulcorner \phi \urcorner)$.
\end{lemma}

\begin{proposition}
Let $\phi$ be any closed $\Sigma_1^0$-formula:$\mathbb{N} \models \phi \longleftrightarrow \exists x_1 \phi_{proof_{Rob.}}(x_1, \ulcorner \phi \urcorner)$.
\end{proposition}

\begin{lemma}
Let $t_{[x_1, \dots, x_n]}$ be any $\mathcal{L}_A$-term (where $\mathcal{L}_A = \{ 0, S, +, \cdot \}$):
$Rob. + I\Sigma^0_1 \vdash_c
\forall x_1 \dots x_{n + 1} (t_{[x_1, \dots, x_n]} = x_{n + 1} \longrightarrow \exists x_0 (x_0, \ulcorner t_{[x_1, \dots, x_n]} = x_{n + 1} \urcorner))$
\end{lemma}

\begin{lemma}
The set of all formula $\phi$ that satisfy
$Rob. + I\Sigma^0_1 \vdash_c
\forall x_1 \dots x_{n + 1} (\phi_{[x_1, \dots, x_n]} \longrightarrow \exists x_0 (x_0, \ulcorner \phi_{[x_1, \dots, x_n]} \urcorner))$
is closed under conjunction, disjunction, existential quantification and bounded universal quantification.
\end{lemma}
