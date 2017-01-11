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
characteristic function is primitive recursive.

\end{definition}

Note that if the characteristic function is *primitive recursive*,
then the set is *decidable*. A set is decidable doesn't mean its
characteristic function is primitive recursive, e.g. the following
set whose characteristic function depends on Ackermann's function:
$$
M = \{ n \mid A(n, n) \text{ divides } 3 \}
$$

In contrast, if a set is *recognizable*, then its characteristic function
is *recursive*. However, if the characteristic function is *recursive*, it doesn't
imply that the set is *recognizable*, as the characteristic function
may be not defined at the point $x$ while $x \in A$.

To summarize, we have the following:
\begin{equation*}
\begin{array}{lcl}
X_A \text{ primitive recursive } &  \Rightarrow & A \text{ decidable (recursive) } \\
X_A \text{ primitive recursive } & \nLeftarrow & A \text{ decidable (recursive) } \\
X_A \text{ recursive } &  \nRightarrow & A \text{ recognizable (recursively enumerable) } \\
X_A \text{ recursive } & \Leftarrow & A \text{ recognizable (recursively enumerable) }
\end{array}
\end{equation*}

\vspace{5mm}

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
f \text{ is Turing computable } \iff G_f = \{ (\vec{x}, f(\vec{x})) \mid \vec{x} \in dom_f \} \text{ is Turing Recognizable }.
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


## Bounded Minimisation and Bounded Quantification

\begin{proposition}[Bounded minimisation]

If $A \subseteq \mathbb{N}^{p+1}$ is primitive recursive, then $f :
\mathbb{N}^{p + 1} \to \mathbb{N}$ defined below is also primitive
recursive:
\begin{equation*}
f(\vec{x}, z) =
\begin{cases}
0 & \text{ if } \forall t \le z (\vec{x}, t) \in A \\
\text{the least } t \le z \text{ such that } (\vec{x}, t) \in A & otherwise.
\end{cases}
\end{equation*}
$f(\vec{x}, z)$ is denoted by $\mu t \le z (\vec{x}, t) \in A$.
\end{proposition}


\begin{proposition}[Closed under bounded quantification]

The set of all primitive recursive predicates is closed under bounded
quantification, i.e. if $A \subseteq \mathbb{N}^{p + 1}$ is primitive
recursive, then the following two sets as well:

\begin{enumerate}
\item $\{ (\vec{x}, z) \mid \exists t \le z (\vec{x}, t) \in A \}$
\item $\{ (\vec{x}, z) \mid \forall t \le z (\vec{x}, t) \in A \}$
\end{enumerate}

\end{proposition}


\begin{example}
\hfill
\begin{enumerate}
\item $\{ 2n \mid n \in \mathbb{N} \}$ is primitive recursive.
\item $[\frac{x}{y}]$ is primitive recursive.
\item $\{ (x, y) \mid y \text{ divides } x \}$ is primitive recursive.
\item $\{ x \in \mathbb{N} \mid x \text{ is a prime number } \}$ is primitive recursive.
\end{enumerate}

\end{example}


## Coding Sequences of Integers

\begin{proposition}

For every non-zero $p \in \mathbb{N}$ there exists primitive recursive functions
$\beta_p^1, \beta_p^2, \dots, \beta_p^p : \mathbb{N} \to \mathbb{N}$ and
$\alpha_p : \mathbb{N}^p \to \mathbb{N}$ such at:

\begin{itemize}
\item $\alpha_p : \mathbb{N}^p \longleftrightarrow \mathbb{N}$
\item $\alpha_p^{-1} = (\beta_p^1(x), \dots, \beta_p^p(x))$
\end{itemize}

\end{proposition}


\begin{example}
A different way of coding sequences of integers:
\begin{equation*}
\begin{cases}
c(\epsilon) & = \quad 1 \\
c(x_0, \dots, x_p) & = \quad \prod(0)^{x_0 + 1} \cdot \prod(1)^{x_1 + 1} \dots \prod(p)^{x_p + 1}
\end{cases}
\end{equation*}
\end{example}


## Partial Recursive Functions

\begin{definition}[composition]

Given $f_1, \dots, f_n$ are partial functions on $\mathbb{N}^p \to
\mathbb{N}$, the composition $h = g(f_1, \dots, f_n)$ is defined by:
\begin{equation*}
h(\vec{x}) =
\begin{cases}
undefined & \text{if } \vec{x} \notin \bigcap_{1 \le i \le n} dom_{f_i} \\
undefined & \text{if } (f_1(\vec{x}), \dots, f_n(\vec{x})) \notin dom_g \\
g(f_1(\vec{x}), \dots, f_n(\vec{x})) & otherwise
\end{cases}
\end{equation*}

\end{definition}


\begin{definition}[recursion]

Given partial functions $g : \mathbb{N}^p \to \mathbb{N}$ and $h :
\mathbb{N}^{p + 2} \to \mathbb{N}$, there exists a unique partial
function $f : \mathbb{N}^{p + 1} \to \mathbb{N}$ such that for all
$\vec{x} \in \mathbb{N}^p$ and $y \in \mathbb{N}$:
\begin{equation*}
f(\vec{x}, 0) =
\begin{cases}
undefined & \text{if } \vec{x} \notin dom_g \\
g(\vec{x}) & otherwise
\end{cases}
\end{equation*}
\begin{equation*}
f(\vec{x}, y + 1) =
\begin{cases}
undefined & \text{if } (\vec{x}, y) \notin dom_g \\
undefined & \text{if } (\vec{x}, y, f(\vec{x}, y)) \notin dom_h \\
h(\vec{x}, y, f(\vec{x}, y)) & otherwise
\end{cases}
\end{equation*}

\end{definition}


\begin{definition}[minimization]

Given partial function $f : \mathbb{N}^{p + 1} \to \mathbb{N}$, we define
the partial function $g : \mathbb{N}^p \to \mathbb{N}$ as follows:
\[
g(\vec{x}) \quad = \quad \mu y \; f(\vec{x}, y) = 0.
\]

Note that $g(\vec{x}) = y$ implies that:
\begin{enumerate}
\item $\forall z < y, f(\vec{x}, z)$ is defined!
\item $\forall z < y, f(\vec{x}, z) > 0$,
\item $f(\vec{x}, y) = 0$.
\end{enumerate}

If no such $y$ exists, then $g(\vec{x}) = 0$.

\end{definition}

\begin{definition}[partial recursive functions]

The set of partial recursive functions is the least that contains:

\begin{enumerate}
\item All constant functions $\mathbb{N}^p \to \mathbb{N}$
\item All projections $\pi_i^p$
\item The successor function $S(n) = n + 1$
\end{enumerate}

And is closed under:

\begin{enumerate}
\item composition
\item recursion
\item minimisation
\end{enumerate}

\end{definition}


\begin{lemma}
Every partial recursive function is Turing computable.
\end{lemma}

*Proof idea:* Induction on the definition of partial recursive functions.

\begin{lemma}
Every Turing computable partial function is partial recursive.
\end{lemma}

*Proof idea:* Define a recursive function $f : \mathbb{N}^2 \to
 \mathbb{N}$ that maps the encoding of initial configuration to the
 encoding of configuration after $n$ steps. This function is primitive
 recursive.

Then the partial recursive function computed by the TM is the minimisation
of computation steps leading to an accepting state:
$$
f(w) = \beta_4^4(f(\alpha_4(0, 0, w, 0), \mu n.accept(n)))
$$

\begin{corollary}
Every partial recursive function admits a construction that requires at most one minimisation.
\end{corollary}

\begin{theorem}
A function is partial recursive if and only if it is Turing computable.
\end{theorem}

Note that we define _recursive_ as _partial recursive_. Ackermann
function is not _primitive recursive_, but _partial recursive_ or
_recursive_. _Partial recursive_ is also called $\mu$-recursive, to
differentiate from $\lambda$-recursive.
