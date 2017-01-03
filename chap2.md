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


## Universal Turing Machine

Encoding of Turing machine:

- $C : A \longrightarrow \{0, 1\}^{[8]}$
- $c(a_0\dots a_p) = C(a_0)\dots C(a_p)$
- Code of $\mathcal{M}$: $^\ulcorner \mathcal{M}^\urcorner = c(\mathcal{M})$.

\begin{definition}[Universal Turing Machine]

There exists a Turing machine $\mathcal{u}$ such that on each input of the form
$vw \in \{0, 1\}^*$:

\begin{center}

if $v = ^\ulcorner\mathcal{M}^\urcorner$ for some Turing machine $\mathcal{M}$,
then $\mathcal{u}$ works as $\mathcal{M}$ on input $w$.

\end{center}

\end{definition}


## The Halting Problem

\begin{proposition}

The following language is Turing recognizable but not decidable:
\[
\{  ^\ulcorner \mathcal{M}^\urcorner w \in \{0, 1\}^* \mid \mathcal{M} \text{ is a TM accepts } w  \}
\]

\end{proposition}

__Proof:__ Suppose there is a decider $\mathcal{D}$ decides the
language. We construct a new TM $\mathcal{H}$ based on $\mathcal{D}$
for the given input $w$:

1. if $\mathcal{D}$ accepts $ww$, $\mathcal{H}$ doesn't terminate
2. if $\mathcal{D}$ rejects $ww$, $\mathcal{H}$ accepts $w$

Now the question is: does $\mathcal{H}$ accept $^\ulcorner \mathcal{H}^\urcorner$?
If $\mathcal{H}$ accepts $^\ulcorner \mathcal{H}^\urcorner$, then
$\mathcal{D}$ rejects $^\ulcorner \mathcal{H}^\urcorner$$^\ulcorner
\mathcal{H}^\urcorner$, which in turn implies
$\mathcal{H}$ doesn't accept $^\ulcorner \mathcal{H}^\urcorner$, a contradiction.

On the other hand, If it doesn't accept, then according to the
definition it doesn't terminate. If $\mathcal{H}$ doesn't terminate
on $^\ulcorner \mathcal{H}^\urcorner$, then $\mathcal{D}$ accepts
$^\ulcorner \mathcal{H}^\urcorner$$^\ulcorner
\mathcal{H}^\urcorner$. According to the definition of the set, then
it means $\mathcal{H}$ accepts $^\ulcorner \mathcal{H}^\urcorner$, a
contradiction. \qed

\begin{proposition}

The following language is Turing recognizable but not decidable:
\[
\{ ^\ulcorner \mathcal{M} ^\urcorner \in \{0, 1\}^* \mid \mathcal{M}(\epsilon) \downarrow \}.
\]


\end{proposition}

**Proof Idea**: Suppose there exists a decider for the language, then
we can use it to create a general decider for any Turing machine on
any input.

Given a decider $\mathcal{D}$ for the language, and input $^\ulcorner
\mathcal{M}^\urcorner w$, the general decider $\mathcal{G}$ works as
follows:

- It changes the TM description $^\ulcorner \mathcal{M}^\urcorner$ to
$^\ulcorner \mathcal{M}^{\prime\urcorner}$, which when started will first write
$w$ on the tape and return to the initial state.
- Run the decider $\mathcal{D}$ on $^\ulcorner\mathcal{M}^{\prime\urcorner}$:
    - if it accepts, then $\mathcal{G}$ accepts $^\ulcorner\mathcal{M}^\urcorner w$
    - otherwise, it rejects.   \qed.


\begin{corollary}

The following languages are not recursively enumerable:

\begin{itemize}
\item $\{0, 1\}^* \backslash \{ ^\ulcorner \mathcal{M}^\urcorner w \in \{0, 1\}^* \mid \mathcal{M}(w) \downarrow^{acc.} \}$
\item $\{0, 1\}^* \backslash \{ ^\ulcorner \mathcal{M}^\urcorner \in \{0, 1\}^* \mid \mathcal{M}(\epsilon) \downarrow \}$
\item $ \{ ^\ulcorner \mathcal{M}^\urcorner w \in \{0, 1\}^* \mid \mathcal{M}(w) \downarrow^{rej.} \text{ or  } \mathcal{M}(w) \uparrow \}$
\item $ \{ ^\ulcorner \mathcal{M}^\urcorner w \in \{0, 1\}^* \mid \mathcal{M}(\epsilon) \uparrow \}$
\end{itemize}

\end{corollary}



## Turing Machine with Oracle

\begin{definition}[Oracle]
\hfill

(1) An \textbf{oracle} is any subset $\mathbb{O} \subseteq \mathbb{N}$

(2) An \textbf{oracle-compatible-Turing machine} (o-c-TM) is a 2-tape Turing
machine similar to any 2-tape Turing machine except that it only
reads but never writes on tape \textcircled{\small 2}:
\[
\mathcal{O} = (Q, \Sigma, \Gamma, \delta, q_0, q_{acc.}, q_{rej.})
\]

(3) An oracle-compatible-Turing machine $\mathcal{O}$ equipped with
the oracle $\mathbb{O}$, on input word $w \in \Sigma^*$ (in short \textbf{an
oracle TM} $\mathcal{O}^\mathbb{O}$ on word $w \in \Sigma^*$) is the TM
whose initial configuration is:
\[
(q_0w, q_0\mathcal{X}_\mathbb{O})
\]
where $\mathcal{X}_\mathbb{O} \in \{0, 1\}^\omega$ is the infinite word
\[
\mathcal{X}_\mathbb{O}(0)\mathcal{X}_\mathbb{O}(1)\dots\mathcal{X}_\mathbb{O}(n)\dots
\]
defined by
\[
\mathcal{X}_\mathbb{O}(n) = \left\{
  \begin{array}{rl}
    1 & \text{if } n \in \mathbb{O}, \\
    0 & \text{if } n \notin \mathbb{O}. \\
  \end{array} \right.
\]


\end{definition}


\begin{example}

Let $\mathbb{O} \subseteq \mathbb{N}$ be the set of all the codes of
Turing machines that halt on the mpty input:
\[
\mathbb{O} = \{ \overline{1\ulcorner\mathcal{M}\urcorner}^2 \in \mathbb{N} \mid \mathcal{M}(\epsilon) \downarrow \}
\]

Then we can construct an machine $\mathcal{O}^\mathbb{O}$ that decides the language by using the oracle:
\[
\{ \ulcorner\mathcal{M}\urcorner \in \{0, 1\}^* \mid \mathcal{M}(\epsilon) \downarrow \}
\]

\end{example}


\begin{notation}
\hfill

\begin{enumerate}

\item The mapping $f: \{0, 1\}^* \iff \mathbb{N}$ is a bijection
\item Given any language $L \subseteq \{0, 1\}^*$, we write $\mathbb{O}_L \subseteq \mathbb{N}$ for the set:
\[
\mathbb{O}_L = \{ \ulcorner w \urcorner \in \mathbb{N} \mid w \in L \} = \{ k \in \mathbb{N} \mid \ulcorner k \urcorner \in L \}.
\]
\item Given any subset $\mathbb{O} \subseteq \mathbb{N}$, we write $\mathcal{L}_{(\mathbb{O})} \subseteq \{0, 1\}^*$ for the language:
\[
\mathcal{L}_{(\mathbb{O})} = \{ w \in \{0, 1\}^* \mid \ulcorner w \urcorner \in \mathbb{O} \} = \{ \ulcorner k \urcorner \in \{0, 1\}^* \mid k \in \mathbb{O} \}.
\]

\end{enumerate}

In another word, $\mathbb{O}_L$ is the oracle associated with the
language $L$, and $\mathcal{L}_{(\mathbb{O})}$ is the language associated
with the oracle $\mathbb{O}$.
\end{notation}


\begin{proposition}

Given any recursive language $L \subseteq \{0, 1\}^*$, and any oracle
Turing machine $\mathcal{O}^{\mathbb{O}_L}$:

\begin{itemize}

\item $\mathcal{L}(\mathcal{O}^{\mathbb{O}_L})$ is recursively enumerable,
\item if $\mathcal{O}^{\mathbb{O}_L}$ is an oracle decider, then
$\mathcal{L}(\mathcal{O}^{\mathbb{O}_L})$ is recursive.

\end{itemize}

\end{proposition}



\begin{definition}[Turing Reducibility]

Given any $A, B \subseteq \mathbb{N}$, $A$ is \textit{Turing-reducible} to $B$,
denoted $A \le_T B$ if there exists an o-c-TM $\mathcal{O}^B$ which on empty
tape computes $\mathcal{X}_A$.

\end{definition}


\begin{proposition}
\hfill

Given any $A, B \subseteq \mathbb{N}$, the following are equivalent:

(1) $A$ is Turing reducible to $B$

(2) for every o-c-TM $\mathcal{M}$, there exists an o-c-TM $\mathcal{N}$ such
that $\mathcal{L}(\mathcal{M}^A) = \mathcal{L}(\mathcal{N}^B)$. Moreover, in
case $\mathcal{M}^A$ is an oracle decider, we may ensure that $\mathcal{N}^B$
be one too.

\end{proposition}



\begin{notation}
Given any $A, B \subseteq \mathbb{N}$, we write:

\begin{enumerate}
\item $A \le_T B$ if $A$ is Turing reducible to $B$.
\item $A \equiv_T B$ if $A \le_T B$ and $B \le_T A$.
\item $A <_T B$ if $A \le_T B$ and $B \nleq_T A$.
\end{enumerate}

\end{notation}


\begin{example}
Given any language $L \subseteq \{0, 1\}^*$:

\begin{enumerate}
\item $\mathbb{O}_L \equiv_T \mathbb{O}_{\overline{L}} = \mathbb{N} \backslash \mathbb{O}_L$.
\item $\oslash \le_T \mathbb{O}_L$.
\item $L$ is recursive $\iff$ $\mathbb{O}_L \equiv_T \oslash$.
\item $L$ is not recursive $\iff$ $\oslash <_T \mathbb{O}_L$.
\item $\mathbb{O}_L \equiv_T \mathbb{O}_{\mathcal{L}_({\mathbb{O}_L})}$ holds
since we have $\mathbb{O}_L = \mathbb{O}_{\mathcal{L}_({\mathbb{O}_L})}$.
\end{enumerate}

\end{example}


The following equivalence class is called a __Turing degree__:
$$
[A]_{\equiv_T} = \{ B \subseteq \mathbb{N} \mid B \equiv_T A \}
$$
The ordering on oracles induces an ordering $\mathbb{TD}$ on the set of all Turing degrees.


\begin{example}[Facts of Turing Degrees]
\hfill

(1) Given any $d \in \mathbb{TD}$, $card(d) = \mathfrak{N}_0$.

(2) Given any set $A \subseteq \mathbb{N}$ the set is countable: $\{ B \subseteq \mathbb{N} \mid B \le_T A \}$.

(3) Given any $d \in \mathbb{TD}$, $card\{e \in \mathbb{TD} \mid e \le d \} \le \aleph_0$.

(4) Given any $d \in \mathbb{TD}$, $card\{e \in \mathbb{TD} \mid d \le e \} \le 2^{\aleph_0}$.

\end{example}


\begin{proposition}
\hfill

(1) \{ $\mathcal{L}_{(\mathbb{O})} \subseteq \{0, 1\}^* \mid
\mathbb{O} \le_T \oslash $ \} is the class \textit{Rec.} of all
recursive languages.

(2) $\{ L \subseteq \{0, 1\}^* \mid \mathbb{O}_L \le_T \mathbb{H}_{alt} \} \supsetneq \mathcal{R}.\mathcal{E}.$

(3) $\{ \mathcal{L}_{(\mathbb{O})} \subseteq \{0, 1\}^* \mid \mathbb{O} \le_T \mathbb{H}_{alt} \} \supsetneq \mathcal{R}.\mathcal{E}.$

Where $\mathbb{H}_{alt}$ stands for the set of codes of Turing machines that halt on the empty input:
\[
\mathbb{H}_{alt} = \mathbb{O}_{\{ \ulcorner \mathcal{M} \urcorner \in \{0, 1\}^* \mid \mathcal{M}(\epsilon) \downarrow \}}
= \{ \ulcorner \mathcal{M} \urcorner \in \mathbb{N} \mid \mathcal{M}(\epsilon) \downarrow \}
\]

\end{proposition}



\begin{definition}[Jump Operator]

Given any subset $A \subset \mathbb{N}$, the \textit{jump} of $A$, denoted $A'$, is
\[
A' = \mathbb{O}_{\{\ulcorner \mathcal{M} \urcorner \in \{0, 1\}^* \mid \mathcal{M} \text{ an o-c-TM}, \mathcal{M}^A(\epsilon)\downarrow  \}}
= \{ \ulcorner \mathcal{M} \urcorner \in \mathbb{N} \mid \mathcal{M}^A(\epsilon) \downarrow \}
\]

\end{definition}


\begin{example}
$\mathcal{H}_{alt} \equiv_T \oslash'$.
\end{example}

\begin{proposition}
For every $A \subseteq \mathbb{N}$ the set
\[
A^\dag = \{ \alpha_2(\ulcorner \mathcal{M} \urcorner, \ulcorner w \urcorner) \in \mathbb{N} \mid M^A(w) \downarrow \}
\]
satisfies
\[
A' \equiv_T A^\dag.
\]
\end{proposition}


\begin{proposition}
For every $A \subseteq \mathbb{N}$, $A <_T A'$.
\end{proposition}


\begin{corollary}
The following strict ordering between jumps is satisfied:
\[
\oslash <_T \oslash' <_T \oslash'' <_T \dots
\]
\end{corollary}
