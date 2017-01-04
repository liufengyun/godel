# Recursive Functions

## Primitive Recursive Functions


\begin{definition}
\hfill

\textbf{projection:} If $i$ is any integer such that $1 \le i \le p$ holds,
the $i^th$ projection $\pi_i^p$ is the function defined by
\[
\pi_i^p(x_1,\dots,x_p) = x_i
\]

\textbf{successor:} $S(n) = n + 1$ is the successor function.

\textbf{composition:} Given $f_1, \dots, f_n : \mathbb{N}^p \to \mathbb{N}$ and
$g : \mathbb{N}^n \to \mathbb{N}$, the composition $h = g(f_1,\dots,f_n)$ with
the type $h : \mathbb{N}^p \to \mathbb{N}$ is defined by:
\[
h(x_1,\dots,x_p) = g(f_1(x_1,\dots,x_p),\dots,f_n(x_1,\dots,x_p))
\]

\textbf{recursion:} Given $g: \mathbb{N}^p \to \mathbb{N}$ and
$h : \mathbb{N}^{p+2} \to \mathbb{N}$, there exists a unique
$f : \mathbb{N}^{p+1} \to \mathbb{N}$ such that for all $\vec{x} : \mathbb{N}^p$
and $y : \mathbb{N}$ satisfies:
\begin{enumerate}
\item $f(\vec{x}, 0) = g(\vec{x})$
\item $f(\vec{x}, y + 1) = h(\vec(x), y, f(\vec(x), y))$
\end{enumerate}

We say $f$ is defined by recursion on both $g$ and $h$.

\end{definition}


\begin{definition}[Primitive Recursive Functions]

The set of primitive recursive functions is the least set that contains:

\begin{enumerate}
\item All constant functions $\mathbb{N}^p \to \mathbb{N}$;
\item All projections $\pi_i^p$;
\item The successor function $S(n) = n + 1$.
\end{enumerate}

and is closed under

\begin{enumerate}
\item composition
\item recursion
\end{enumerate}

\end{definition}


\begin{example}
A list of primitive recursive functions:

\begin{enumerate}
\item Addition: $(x, y) \to x + y$
\item Multiplication: $(x, y) \to x \times y$
\item Exponentiation: $x \to n^x$
\item Factorial: $x \to x!$
\end{enumerate}

\end{example}


\begin{example}
The following function $\ominus$ is primitive recursive:

\begin{equation*}
x \ominus y =
  \begin{cases}
      x - y & \text{ if } x > y, \\
      0 & otherwise.
  \end{cases}
\end{equation*}

\end{example}



\begin{definition}[Primitive Recursive Sets]

A set $A \subseteq \mathbb{N}^p$ is primitive recursive if its
characteristic function is recursive.

\end{definition}


\begin{example}
Primitive recursive sets:

\begin{enumerate}
\item $\oslash$
\item $\mathbb{N}$
\item $\{ (x, y) \mid x < y \}$
\end{enumerate}

\end{example}


\begin{definition}[Partial and Total Functions]
\hfill

(1) $f : A \to \mathbb{N}$ is a partial function of $\mathbb{N}^p \to
\mathbb{N}$ if $A \subseteq \mathbb{N}^p$.

(2) $f : A \to \mathbb{N}$ is a total function of $\mathbb{N}^p \to
\mathbb{N}$ if $A = \mathbb{N}^p$.

\end{definition}


\begin{notation}

We write $f \in (A \subseteq \mathbb{N}^p) \to \mathbb{N}$ if $f : A
\to \mathbb{N}$ is a partial function of $\mathbb{N}^p \to \mathbb{N}$.

\end{notation}


\begin{definition}[Turing Computable Partial Functions]
A partical function $f : \mathbb{N}^p \to \mathbb{N}$ is Turing computable if
there exsits a TM $\mathcal{M}$ such that on input $\vec{x} = (x_1, \dots, x_p)$:

(1) if $f(\vec{x})$ is not defined, then $\mathcal{M}(\vec{x}) \uparrow$;

(2) otherwise, $\mathcal{M}(\vec{x}) \downarrow$ with $f(\vec{x})$ written on its tape.

\end{definition}


\begin{proposition}

Given any partial function $f : \mathbb{N}^p \to \mathbb{N}$,
\[
f \text{ is Turing computable } \iff G_f = \{ (\vec{x}, f(x)) \mid \vec{x} \in dom_f \} \text{ is Turing Recognizable }.
\]

\end{proposition}


\begin{corollary}

Given any function $f : \mathbb{N}^p \to \mathbb{N}$,
\[
f \text{ is both total and Turing computable } \Rightarrow G_f \text{ is recursive (decidable) }.
\]

\end{corollary}


\begin{remarks}
\hfill

(1) All primitive recursive functions are total and Turing computable

(2) All graphs of primitive recursive functions are recursive
\end{remarks}


## Variable Substituition

\begin{proposition}[Primitive Recursive Functions closed under Variable Substituition]

If $f: \mathbb{N}^p to \mathbb{N}$ is primitive recursive, then given any
$\delta : \{ 1,\dots,p \} \to \{1,\dots,p\}$, the function $g$ defined below
is also primitive recursive:
\[
g(x_1,\dots,x_p) = f(x_{\delta(1)},\dots,x_{\delta(p)})
\]

\end{proposition}


\begin{proposition}

If $A \subseteq \mathbb{N}^k$ is primitive recursive, and
$f_1,\dots,f_n : \mathbb{N}^k \to \mathbb{N}$ are primitive
recursive, then the following set is primitive recursive:
\[
\{ \vec{x} \in \mathbb{N}^p \mid (f_1(\vec{x}),\dots,f_n(\vec{x})) \in A \}
\]

\end{proposition}



\begin{example}

If $f, g : \mathbb{N}^p \to \mathbb{N}$ are primitive recursive, then
the following sets are also primitive recursive:

\begin{enumerate}
\item $\{ \vec{x} \mid f(\vec{x}) > g(\vec{x}) \}$
\item $\{ \vec{x} \mid f(\vec{x}) = g(\vec{x}) \}$
\item $\{ \vec{x} \mid f(\vec{x}) < g(\vec{x}) \}$
\end{enumerate}

\end{example}



\begin{proposition}

If $A, B \subseteq \mathbb{N}^p$ are primitive recursive, then
$A \cup B, A \cap B, A \backslash B, A \Delta B$ and $\mathbb{N}^p \backslash A$
are all primitive recursive.

\end{proposition}


\begin{proposition}[Case study]

If $f_1, \dots, f_{n+1} : \mathbb{N}^p \to \mathbb{N}$ and $A_1,
\dots, A_n \in \mathbb{N}^p$ are all primitive recursive, then $g :
\mathbb{N}^p \to \mathbb{N}$ is also primitive recursive:
\begin{equation*}
g(\vec{x}) =
  \begin{cases}
    f_1(\vec{x}) & \text{ if } \vec{x} \in A_1 \\
    f_2(\vec{x}) & \text{ if } \vec{x} \in A_2 \backslash A_1 \\
    f_3(\vec{x}) & \text{ if } \vec{x} \in A_3 \backslash (A_2 \cup A_1) \\
    \vdots & \vdots \\
    f_{n + 1}(\vec{x}) & \text{ if } \vec{x} \notin A_1 \cup \dots \cup A_n
  \end{cases}
\end{equation*}

\end{proposition}



\begin{corollary}
$sup(x_1,\dots,x_n)$ and $inf(x_1,\dots,x_n)$ are primitive recursive.
\end{corollary}


\begin{proposition}
$f : \mathbb{N}^{p+1} \to \mathbb{N}$ is primitive recursive, then
$g, h : \mathbb{N}^p \to \mathbb{N}$ below are primitive recursive:
\[
g(x_1,\dots,x_p) = \sum_{t = 0}^{t = y} f(x_1,\dots,x_p,t)
\]
\[
h(x_1,\dots,x_p) = \prod_{t = 0}^{t = y} f(x_1,\dots,x_p,t).
\]

\end{proposition}
