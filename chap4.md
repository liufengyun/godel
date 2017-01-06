# Representing Functions

## Robinson Arithmetic

The first order theory _Robinson Arithmetic_. The language
$\mathcal{L}(A) = \{0, S, +, \cdot \}$ where

1. $0$ is a constant symbol
2. $S$ is a unary function symbol
3. $+$ and $\cdot$ are binary function symbols

The axioms of the theory are as follows:

1. $\forall x. Sx \neq 0$
2. $\forall x \exists y (x \neq 0 \to Sy = x)$
3. $\forall x \forall y (Sx = Sy \to x = y)$
4. $\forall x. x + 0 = x$
5. $\forall x \forall y (x + Sy = S(x + y))$
6. $\forall x. x \cdot 0 = 0$
7. $\forall x \forall y (x \cdot Sy = (x \cdot y) + x)$


\begin{example}
The standard model of Robinson Arithmetic is $\langle \mathbb{N}, 0, S, +, \cdot \rangle$.
\end{example}


\begin{example}
A non standard model of Robinson arithmetic $\mathcal{M}$ in which:

\begin{enumerate}
\item $S^\mathcal{M}$ admits a fixed point
\item $\cdot^\mathcal{M}$ is not commutative
\end{enumerate}
\end{example}


\begin{notation}
For any integer $n$, we write $n$ for the $\mathcal{L}_A$-term $\underbrace{S \dots S}_n 0$.
\end{notation}


\begin{example}
$\texttt{Rob.} \vdash_c \forall x (0 + x = k \to x = k)$
\end{example}


\begin{example}
$\texttt{Rob.} \vdash_c \forall x \forall y (Sy + x = k \to S(y + x) = k$.
\end{example}


## Representable Functions

\begin{definition}

Let $f : \mathbb{N}^n \to \mathbb{N}$ and $\phi(x_0, \dots, x_n)$ be
any $\mathcal{L}_A$-formula whose free variables are among $x_0, \dots, x_n$.
$\phi(x_0, \dots, x_n)$ represents the function $f$ if for all $i_i,
\dots, i_n \in \mathbb{N}$:
\[
\forall x_0 f(i_1, \dots, i_n) = x_0 \longleftrightarrow \texttt{Rob.} \vdash_c \phi(x_0, \dots, i_n).
\]

\end{definition}

Note: The variables $i_1, i_n$ on the left and right mean different things. On
the left, they are integers. On the right they are formula in \texttt{Rob}
that correspond to the integer. Strictly, a conversion function is in need on
the right. The abuse of symbols is justified for simplicity of presentation.


\begin{definition}

Let $A \subseteq \mathbb{N}^n$ and $\phi(x_1, \dots, x_n)$ be any
$\mathcal{L}_A$-formula whose free variables are among $x_1, \dots,
x_n$.  $\phi(x_1, \dots, x_n)$ represents the set $A$ if for all $i_1,
\dots, i_n \in \mathbb{N}$ we have:
\[
(i_1, \dots, i_n) \in A \longleftrightarrow \texttt{Rob.} \vdash_c \phi(i_1, \dots, i_n).
\]

\end{definition}


\begin{proposition}
For any $A \subseteq \mathbb{N}^n$, $A$ is representable if and only if
$\mathcal{X}_A$ is representable.
\end{proposition}


\begin{example}
The constant function $f(i_1, \dots, i_n) = k$ is represented by $x_0 = k$.
\end{example}


\begin{example}
The projection $\pi_j^n$ is represented by $x_0 = i_j$.
\end{example}


\begin{example}
The successor $S: \mathbb{N} \to \mathbb{N}$ is represented by $x_0 = Sx_1$.
\end{example}


\begin{example}
The addition $+ : \mathbb{N}^2 \to \mathbb{N}$ is represented by $x_0 = x_1 + x_2$.
\end{example}


\begin{example}
The multiplication $\cdot : \mathbb{N}^2 \to \mathbb{N}$ is represented by $x_0 = x_1 \cdot x_2$.
\end{example}


\begin{lemma}
The set of representable functions is closed under composition.
\end{lemma}


\begin{example}
\hfill
\begin{enumerate}
\item for all non-zero integer $i$: $Rob. \vdash_c i \neq 0$.
\item for all integers $i \neq j$: $Rob. \vdash_c i \neq j$.
\end{enumerate}
\end{example}


\begin{notation}
\hfill

(1) We write $x \le z$ to mean $\exists y \; y + x = z$. \\
(2) We write $x < z$ to abbreviate $\exists y (y + x = z \land x \neq z)$.
\end{notation}


\begin{example}
$Rob. \vdash_c \forall x \; \neg x < 0$.
\end{example}


\begin{example}
$Rob. \vdash_c \forall x [x \le n \longleftrightarrow x = 0 \lor x = S0 \lor \dots \lor x = n]$.
\end{example}


\begin{example}
$Rob. \vdash_c \forall x (x \le n \lor n \le x)$.
\end{example}


\begin{lemma}
Let $A \subseteq \mathbb{N}^{n + 1}$ be representable. If the following function
$f : \mathbb{N}^n \to \mathbb{N}$ is total, then $f$ is representable:
\[
f(i_1, \dots, i_n) = \mu k \; (k, i_1, \dots, i_n) \in A.
\]
\end{lemma}


\begin{theorem}[Chinese Remainder Theorem]
Suppose $n_0, n_1, \dots, n_k$ are positive integers which are pairwise co-prime.
Then, for any given sequence of integers $a_0, a_1, \dots, a_k$ there exists an
integer $x$ solving the system of simultaneous congruences:
\begin{equation*}
\begin{cases}
x & \equiv \quad a_0 \quad mod \; n_0 \\
x & \equiv \quad a_1 \quad mod \; n_1 \\
  & \vdots \\
x & \equiv \quad a_k \quad mod \; n_k.
\end{cases}
\end{equation*}
\end{theorem}


\begin{lemma}[Godel $\beta$-function]
There exists some function $\beta$ which is both representable and primitive
recursive such that for all $k \in \mathbb{N}$ and every sequence
$n_0, \dots, n_k$ there exists $a, b \in \mathbb{N}$ such that
\begin{equation*}
\begin{cases}
\beta(0, a, b) & = n_0 \\
\beta(1, a, b) & = n_1 \\
               & \vdots \\
\beta(k, a, b) & = n_k \\
\end{cases}
\end{equation*}
\end{lemma}


\begin{lemma}

If both functions $g : \mathbb{N}^p \to \mathbb{N}$ and $h :
\mathbb{N}^{p + 2} \to \mathbb{N}$ are both representable,
then the following function is also representable:
\begin{equation*}
\begin{cases}
f(\vec{x}, 0) & = g(\vec{x}) \\
f(\vec{x}, y + 1) & = h(\vec{x}, y, f(\vec{x}, y))
\end{cases}
\end{equation*}
\end{lemma}

*Proof idea:* Godel $\beta$-function is used to code the sequence:
\begin{equation*}
\begin{cases}
f(\vec{x}, 0) & = g(\vec{x}) \\
f(\vec{x}, 1) & = h(\vec{x}, 0, f(\vec{x}, 0)  \\
f(\vec{x}, 2) & = h(\vec{x}, 1, f(\vec{x}, 1)) \\
              & \vdots                       \\
f(\vec{x}, y + 1) & = h(\vec{x}, y, f(\vec{x}, y)) \\
\end{cases}
\end{equation*}

The formula that represents the function is as follows:

\begin{equation*}
\exists a \exists b \forall i \le y + 1 \exists y \exists z
\left(
\begin{array}{c}
i = 0 \to \phi_g(y, \vec{x}) \\
\land \\
\phi_\beta(y, i, a, b) \\
\land \\
\phi_h(z, \vec{x}, i, y) \\
\land \\
\phi_\beta(z, Si, a, b) \\
\land \\
\phi_\beta(x_0, y + 1, a b) \\
\end{array}
\right)
\end{equation*}

It's obvious the proof has to do induction on the depth of recursion $y + 1$. \qed.

\begin{theorem}
All total recursive functions are representable.
\end{theorem}
