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
