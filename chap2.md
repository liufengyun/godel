# Turing Machines


## Deterministic Turing Machines

\begin{definition}[Deterministic Turing Machine]

A deterministic Turing Machine is a 7-tuple $(Q, \Sigma, \Gamma,
\delta, q_0, q_{acc.}, q_{rej.}))$ where $Q, \Sigma, \Gamma$ are
all finite sets and

\begin{enumerate}

\item $Q$ is the set of states,
\item $\Sigma$ is the alphabet not containing the blank symbol, $\sqcup$,
\item $\Gamma$ is the tape alphabet where $\sqcup \in \Gamma$ and $\Sigma \subseteq \Gamma$,
\item $\delta : Q \times \Gamma \longrightarrow Q \times \Gamma \times \{ L, R \} $ is the transition function
\item $q_0$ is the initial state
\item $q_{acc.}$ is the accepting state
\item $q_{rej.}$ is the rejecting state

\end{enumerate}

\end{definition}


A _configuration_ of a Turing machine is a snapshot: it consists of
the actual constrol state ($q$), the position of the head and what is
written on the tape ($w$).

We write $w_0qw_1$ to say that:

- the tape content is $w_0w_1\sqcup\sqcup\dots$
- the head is positioned on the first letter of $w_1\sqcup\sqcup\dots$
- the actual control state is q

The __initial configuration__ on input $w \in \Sigma^{< \omega}$ is $q_0w$.

An __halting configuration__ is either:

- an _accepting configuration_ of the form $w_0q_{acc.}w_1$, or
- a _rejecting configuration_ of the form $w_0q_{rej.}w_1$.

Given two configurations $C$ and $C'$, we write __$C \Rightarrow C'$__
($C$ yields $C'$ in one step) if there exists $a, b, c \in \Gamma$, and
$u, v \in \Gamma^*$ such that either:

- $C = uaq_ibv, C' = uq_jacv$ and $\delta(q_i, b) = (q_j, c, L)$, or
- $C = uaq_ibv, C' = uacq_jv$ and $\delta(q_i, b) = (q_j, c, R)$

\begin{definition}[A TM Accepts a Word]

A Turing machine accepts input $w$ if there is a sequence of
configurations $C_0, \dots, C_k$ such that:

\begin{enumerate}
\item $C_0 = q_0w$
\item $\forall i < k, C_i \Rightarrow C_{i + 1}$
\item $C_k$ is an accepting configuration
\end{enumerate}

\end{definition}

\begin{definition}{Language Recognized by a TM}
The set of all words accepted by a TM $\mathcal{M}$ is the language it recognizes:

\[
\mathcal{L(M)} = \{ w \in \Sigma^* \mid \mathcal{M} \text{ accepts } w \}.
\]

\end{definition}


\begin{example}

A Turing machine that recognizes $\{ w\bar{w} \mid w \in \{0, 1\}^*
\}$ -- where $\bar{w}$ is the mirror of $w$ (e.g. $\overline{001011} = 110100$).

\end{example}


\begin{definition}[Turing Recognizable Languages]

A language $L$ is Turing recognizable if there exists a TM
$\mathcal{M}$ such that

\[
L = \mathcal{L(M)}
\]

\end{definition}



\begin{proposition}[Equivalence to TM with bi-infinite Tapes]

Turing machines with bi-infinite tapes are equivalent to Turing machines.

\end{proposition}




\begin{proposition}[Equivalence to 2-stack Pushdown Automata]

2-stack Pushdown automata are equivalent to Turing machines.

\end{proposition}




\begin{definition}[Decider]

A decider is a TM that halts on all inputs.

\end{definition}




\begin{definition}[Turing-Decidable Languages]

A language is Turing decidable if and only if there exists a decider that
recognizes it.

\end{definition}

Convention of termiology:

- Turing recognizable = recursively enumerable
- Decidable = recursive



\begin{example}

The language $\{ a^nb^nc^n \mid n \in w \}$ is decidable.

\end{example}


\begin{definition}

A $k$-tape TM is the same as a TM expcept that is composed of $k$
tapes: $\textcircled{\small 1}, \dots, \textcircled{\small k}$, with $k$ independent heads
so that the transition function becomes:

\[
\delta : Q \times \Gamma^{k} \longrightarrow Q \times \Gamma^k \times \{ L, R \}^k
\]

\end{definition}

Note that a configuration of a $k$-tape Turing machine is of the form:
$$
(u_1qv_1, u_2qv_2, \dots, u_kq_vk).
$$


\begin{proposition}[Equivalence to multi-tape TMs]

Given any TM there exists:

\begin{enumerate}
\item an equivalent TM with a bi-infinite tape
\item a multi-tape TM
\item a multi-tape with bi-infinite tapes TM.
\end{enumerate}

\end{proposition}



\begin{theorem}
Every multi-tape TM has an equivalent single tape TM.
\end{theorem}


## Non-Deterministic Turing Machines

\begin{definition}[Non-Deterministic Turing Machines]

A non-deterministic TM (NTM) is the same as a deterministic TM except
for the transition function which is of the form:
\[
\delta: Q \times \Gamma \longrightarrow \mathcal{P}(Q \times \Gamma \times \{L, R\}).
\]

\end{definition}



\begin{theorem}[Equivalence to Deterministic Turing Machines]

For every NTM there exists a deterministic TM that recognizes the same language.

\end{theorem}


\begin{proposition}

\hfill

Recursive languages are closed under
(1) union
(2) intersection,
(3) concatenation
(4) star
(5) complementation.

Recursively recursive languages are closed under
(1) union
(4) intersection
(2) concatenation
(3) star.

\end{proposition}


\begin{definition}

An enumerator is a TM. We say that it enumerates a language $L$ if the
result of its computation (possibly infinite) is of the form:
\[
w_0 \sqcup w_1 \sqcup \dots \sqcup w_n \sqcup w_{n + 1} \sqcup \dots
\]
where $L = \{ w_i \mid i \in \mathbb{N} \}$.

\end{definition}

We say that a language $L$ is _recursively enumerable_ if there is an
enumerator that enumerates $L$.



\begin{theorem}[Turing Recognizable is Recursively Enumerable]

A language is Turing Recognizable if and only if it is recursively enumerable.

\end{theorem}



\begin{proposition}[Turing Decidable and Ordered Enumeration]

A language $L$ is Turing decidable if and only if there exists an
enumerator that enumerates the words of $L$ in an ordering.

\end{proposition}



## The Concept of Algorithm

\begin{definition}[Coding]

A coding is a rule for converting a piece of information into another
object. Given any non-empty sets $E, F$, a coding is a one-to-one total
function:
\[
c : E \xrightarrow{1-1} F.
\]

\end{definition}


\begin{example}
$E = \{0, 1\}$ and $F = \mathcal{N}$ and $c : E \xrightarrow{1-1} F$ is a coding
from binary numbers to integers.
\end{example}


\begin{notation}
Given any Turing machine $\mathcal{M}$, we write

\begin{itemize}
\item $\mathcal{M}(w) \downarrow$ to say that the machine $\mathcal{M}$ stops on input $w$

\begin{itemize}
\item $\mathcal{M}(w) \downarrow^{acc.}$ means that $\mathcal{M}$ stops in an accpeting configuration, and
\item $\mathcal{M}(w) \downarrow^{rej.}$ means that $\mathcal{M}$ stops in an rejecting configuration
\end{itemize}

\item $\mathcal{M}(w) \uparrow$ to say that the machine $\mathcal{M}$ never stops on input $w$.


\end{itemize}

\end{notation}



\begin{definition}[Turing Computable]

Given any two non-empty finite sets $A, B$, a partial function $f : A^*
\rightarrow B^*$ is Turing computable if and only if there exists a Turing
machine $\mathcal{M}_f such that$:

\begin{itemize}
\item on input $w \notin dom(f): \mathcal{M}_f(w) \uparrow$
\item on input $w \in dom(f): \mathcal{M}_f(w) \downarrow^{acc.}$ with the word ``$f(w)$" on its tape.
\end{itemize}

\end{definition}



\begin{remarks}
\hfill

(1) Given any finite alphabet $\Sigma$, and any TM $\mathcal{M}$ whose
alphabet is $\Sigma$, there exists a \textit{Turing computable} coding:
$c : \Sigma^* \longrightarrow \{0, 1, \sqcup\}^*$ and a TM $\mathcal{M}_c$
with tape alphabet $\{ 0, 1, \sqcup \}$ such that $\mathcal{M}$ accepts $w$
if and only if $\mathcal{M}_c$ accepts $c(w)$.

(2) Every regular language is decidable because a DFA is nothing but a
deterministic TM that always goes right.

(3) Every context-free language is decidable.

\end{remarks}
