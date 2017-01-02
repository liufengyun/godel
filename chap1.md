# Towards Turing Machines

## Deterministic Finite Automata

\begin{definition}[Deterministic Finite Automaton]

A \textit{deterministic finite automaton} (DFA) is a 5-tuple $(Q,
\Sigma, \delta, q_0, F)$, where

\begin{enumerate}
\item $Q$ is a finite set called the states,
\item $\Sigma$ is a finite set called the alphabet,
\item $\delta: Q \times \Sigma \longrightarrow Q$ is the transition function,
\item $q_0 \in Q$ is the initial state, and
\item $F \subseteq Q$ is the set of accepting states.
\end{enumerate}

\end{definition}

Some notations:

- $\Sigma^{<\omega}$ (or $\Sigma^*$): the set of finite words on $\Sigma$
- $\epsilon$: the empty sequence

\begin{definition}[DFA Accepts a Word]

A DFA $\mathcal{A} = (Q, \Sigma, \delta, q_0, F)$ on an alphabet $\Sigma$
accepts the word $w \in \Sigma^{<\omega}$ if and only if

\begin{itemize}
\item either $w = \epsilon$ and $q_0 \in F$, or
\item $w = \langle a_0, \dots, a_n \rangle$ with each $a_i \in \Sigma$,
  and there is a sequence of states $r_0, \dots, r_{n + 1}$ such that:

  \begin{itemize}
  \item $r_0 = q_0$
  \item $\forall i < n$, $\delta(r_i, a_i) = r_{i + 1}$
  \item $r_{n + 1} \in F$.
  \end{itemize}
\end{itemize}

\end{definition}

\begin{definition}[DFA Accepts a Language]
Given any DFA $\mathcal{A}$, $\mathcal{L(A)}$ denotes the language accepted by $\mathcal{A}$:

\[
\mathcal{L(A)} = \{ w \in \Sigma^{<\omega} : w \text{ is accepted by } \mathcal{A}  \}.
\]

\end{definition}

\begin{definition}[Regular Language]

Any language recognized by some deterministic finite automata (DFA) is
called regular.

\end{definition}

## Nondeterministic Finite Automata

Some conventions:

- Given any alphabet $\Sigma$, $\epsilon \notin \Sigma$
- $\Sigma_\epsilon = \Sigma \cup \{ \epsilon \}$

\begin{definition}[Nondeterministic Finite Automaton]

A nondeterministic finite automaton (NFA) is a 5-tuple $(Q, \Sigma,
\delta, q_0, F)$, where:

\begin{enumerate}
\item $Q$ is a finite set of states,
\item $\Sigma$ is a finite alphabet,
\item $\delta : Q \times \Sigma_{\epsilon} \longrightarrow \mathcal{P}(Q)$ is the transition function,
\item $q_0 \in Q$ is the initial state, and
\item $F \subseteq Q$ is the set of accepting states.
\end{enumerate}

\end{definition}

\begin{definition}[NFA accepts a Word]

Let $\mathcal{N} = (Q, \Sigma, \delta, q_0, F)$ be an NFA and $w \in
\Sigma^{<\omega}$. We say that $mathcal{N}$ accepts $w$ if and only if

\begin{itemize}
\item either $w = \epsilon$ and $q_0 \in F$, or
\item $w = \langle a_0, \dots, a_n \rangle$  with each $a_i \in \Sigma_\epsilon$,
and there is a sequence of states $r_0, \dots, r_{n + 1}$ such that

\begin{itemize}
\item $r_0 = q_0$,
\item $\forall i < n$, $r_{i + 1} \in \delta(r_i, a_i)$,
\item $r_{n + 1} \in F$.
\end{itemize}

\end{itemize}

\end{definition}

\begin{proposition}[Equivalence of NFA and DFA]

Every NFA has an equivalent DFA, i.e. given any NFA $mathcal{N}$ there
exists some DFA $\mathcal{D}$ such that

\[
\mathcal{L(N)} = \mathcal{L(D)}.
\]

\end{proposition}

\begin{definition}[Union, Intersection, Complement, Concatenation, Star]

Let $A$ and $B$ be languages. We define the regular operations union,
concatenation and star as follows:

\begin{itemize}
\item Union: $A \cup B = \{ x \mid x \in A \text{ or } x \in B \}$.
\item Intersection: $A \cap B = \{ x \mid x \in A \text{ and } x \in B \}$.
\item Complement: $\bar{A} = \{ x \mid x \notin A \}$.
\item Concatenation: $A \circ B = \{ xy \mid x \in A \text{ and } y \in B \}$.
\item Star: $A^* = \{ x_1x_2 \dots x_k \mid k \ge 0 \text{ and } \forall x_i \in A \}$.
\end{itemize}

\end{definition}

\begin{theorem}[Closure under Regular Operations]

Regular languages are closed under union, intersection, complement, concatenation and star.

\end{theorem}


## Regular Expressions

\begin{definition}

We say that $R$ is a regular expression if $R$ is one of the following form:

\begin{enumerate}

\item $a$ where $a \in \Sigma$
\item $\epsilon$ the empty string
\item $\oslash$ the empty regular expression
\item $R_1 \cup R_2$
\item $R_1 \circ R_2$
\item $R_1^*$

\end{enumerate}

\end{definition}




\begin{definition}

Let R be a regular expression. We define by induction its associated language
$L(R)$ as follows:

\begin{enumerate}

\item $L(a) = \{ a \}$
\item $L(\epsilon) = \{ \epsilon \}$
\item $\L(\oslash) = \oslash$
\item $L(R_1 \cup R_2) = L(R_1) \cup L(R_2)$
\item $L(R_1 \circ R_2) = L(R_1) \circ L(R_2)$
\item $L(R_1^*) = L(R_1)^*$

\end{enumerate}

\end{definition}

Note:

- $L(R \circ \oslash) = L(\oslash \circ R) = L(\oslash) = \oslash$
- $L(\oslash^*) = L(\oslash)^* = \{ \epsilon \}$


\begin{theorem}[Relation of Regular Language and Regular Expression]

A language $L$ is regular if and only if there exists a regular
expression $R$ such that $L = L(R)$.

\end{theorem}

The proof of the theorem depends on *Generalized-NFA*, the transitions
of which are labelled with regular expressions. The idea is to reduce
any DFA into a 2-state Generalized-NFA.

\begin{example}
Transform a 2-state DFA into a Generalized-NFA in steps.
\end{example}

\begin{example}[$0^*1(0\cup1)$]
Transform a 3-state DFA into a Generalized-NFA in steps.
\end{example}

## Non-Regular Languages

\begin{theorem}[Pumping Lemma]

If $A$ is a regular language, then there is a number $p$ (the pumping
length) where, if $s$ is any sequence in $A$ of length at least $p$,
then $s$ may be divided into three pieces, $s = xyz$, satisfying the
following conditions:

\begin{enumerate}
\item $\forall i \ge 0$, $xy^iz \in A$,
\item $\lvert y \rvert > 0$,
\item $\lvert xy \rvert \le p$.
\end{enumerate}

\end{theorem}



\begin{example}
The language $\{ 0^m1^m \mid n \in \mathbb{N} \}$ is not regular.
\end{example}

## Pushdown Automata

\begin{definition}[Pushdown Automaton]

A pushdown automaton (PDA) is a 6-tuple $(Q, \Sigma, \Gamma, \delta,
q_0, F)$, where $Q$, $\Sigma$, $\Gamma$ and $F$ are all finite sets, and:

\begin{enumerate}
\item $Q$ is the set of states,
\item $\Sigma$ is the input alphabet,
\item $\Gamma$ is the stack alphabet,
\item $\delta : Q \times \Sigma_\epsilon \times \Gamma_\epsilon \longrightarrow \mathcal(P)(Q \times \Gamma_\epsilon$ is the transition function,
\item $q_0 \in Q$ is the initial state, and
\item $F \subseteq Q$ is the set of accepting states.
\end{enumerate}

\end{definition}

\begin{definition}[PDA Accepts a Word]

A pushdown automaton $\mathcal{M} = (Q, \Sigma, \Gamma, \delta, q_0,
F)$ accepts input $w = \langle w_1w_2 \dots w_m \rangle$, where each
$w_i \in \Sigma_\epsilon$ and there exists a sequence of states
$r_0, r_1, \dots, r_m \in Q$ and a sequence of stack states
$s_0, s_1, \dots, s_m \in \Gamma^*$ such that:

\begin{enumerate}

\item $r_0 = q_0$ and $s_0 = \epsilon$,

\item $\forall i < m$, $(r_{i + 1}, b) \in \delta(r_i, w_{i + 1}, a)$, where
$s_i = at$ and $s_{i + 1} = bt$ for some $a, b \in \Gamma_\epsilon$ and $t \in \Gamma^*$.

\item $r_m \in F$.

\end{enumerate}

\end{definition}


\begin{example}

\hfill

(1) The language $\{ 0^m1^m \mid m \in \mathbb{N} \}$ is recognized by a PDA.

(2) The language $\{ 0^i1^j2^k \mid i, j, k \ge 0 \land (i = j \lor i = k) \}$
is recognized by a PDA, however it's \textbf{NOT} recognizable by a
\textit{deterministic PDA}.
\end{example}


## Context-Free Grammar

\begin{definition}

A context-free grammar is a 4-tuple $(V, \Sigma, R, S)$, where

\begin{enumerate}

\item $V$ is a finite set whose elements are called \textit{variables},

\item $\Sigma$ is a finite set disjoint from $V$ whose elements are
called \textit{terminals},

\item $R$ is a finite set of rules of the form $(\xi, u)$ where $\xi \in V$
and $u \in (V \cup \Sigma)^*$,

\item $S \in V$ is the initial variable.

\end{enumerate}

\end{definition}

Notations:

- $uAv \Rightarrow uwv$ ($uAv$ yields $uwv$) if $u, v \in (V \cup \Sigma)^*$ and $(A, w) \in R$.
- $u \Rightarrow^* v$ if $u = v$ or there exists a sequence $u_1, \dots, u_k$ such that $u \Rightarrow u_1 \Rightarrow \dots \Rightarrow u_k \Rightarrow v$.
- The language generated by a grammar is $\{ w \in \Sigma^* \mid S \Rightarrow^* w \}$.


\begin{example}

The language $\{ 0^n\sharp 1^n \mid n \in \mathcal{N} \}$ is generated by
the following grammar:

\begin{enumerate}
\item $S \longrightarrow 0S1$
\item $S \longrightarrow B$
\item $B \longrightarrow \sharp$

\end{enumerate}

\end{example}


\begin{theorem}[Equivalence of PDA and Context-Free Grammar]

A language is recognized by a PDA if and only if it is context-free.

\end{theorem}


Facts:

1. The class of context-free languages is closed under _union_,
_concatenation_, and _star_, but NOT under _intersection_ or
_complement_.
1. Let $C$ be a context-free language and $R$ be a regular language,
   then $C \cap R$ is context free.

The class of deterministic context-free languages (DCFL) is closed
under _complementation_, but NOT closed under the following operations:

1. Union
1. Intersection
1. Concatenation
1. Star
1. Reversal

Any CFL whose complement is not a CFL is not DCFL.


\begin{definition}[Pumping Lemma for Context-Free Languages]

If $A$ is a context-free language, then there is a number $p$ (the
pumping length) where, if $s$ is any sequence in $A$ of length at
least $p$, then $s$ may be divided into five pieces, $s = vwxyz$,
satisfying the following conditions:

\begin{enumerate}

\item $\forall i \ge 0$, $vw^ixy^iz \in A$
\item $\lvert wy \rvert > 0$,
\item $\lvert wxy \rvert \le p$.

\end{enumerate}

\end{definition}


\begin{example}
The language $\{ a^nb^nc^b \mid n \in \mathbb{N} \}$ is not context-free.
\end{example}
