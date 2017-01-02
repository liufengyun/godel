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
