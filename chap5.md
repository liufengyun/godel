# \godel's First Incompleteness Theorem

## \godel \ Numbers

\begin{definition}[\godel \ numbering of the $\mathcal{L}_A$-terms]
The \godel numbering of the terms from the language
$\mathcal{L}_A = \{ 0, S, +, \cdot \}$ is
\begin{equation*}
\begin{array}{lcl}
t = 0 & \rightsquigarrow & \ulcorner t \urcorner = \alpha_3(0, 0, 0) \\
t = x_n & \rightsquigarrow & \ulcorner t \urcorner = \alpha_3(n + 1, 0, 0) \\
t = St_0 & \rightsquigarrow & \ulcorner t \urcorner = \alpha_3(\ulcorner t_0 \urcorner, 0, 1) \\
t = t_0 + t_1 & \rightsquigarrow & \ulcorner t \urcorner = \alpha_3(\ulcorner t_0 \urcorner, \ulcorner t_1 \urcorner, 2) \\
t = t_0 \cdot t_1 & \rightsquigarrow & \ulcorner t \urcorner = \alpha_3(\ulcorner t_0 \urcorner, \ulcorner t_1 \urcorner, 3)
\end{array}
\end{equation*}

\end{definition}


\begin{lemma}

The set $\mathcal{T}$ of all codes of terms from $\mathcal{L}_A$ is primitive recursive:
\[
\mathcal{T} = \{ \ulcorner t \urcorner \mid t \text{ is a term from } \mathcal{L}_A \}
\]

\end{lemma}



\begin{lemma}

For all primitive recursive functions $h : \mathcal{N}^{n + p + 1} \to \mathbb{N},
g : \mathcal{N}^n \to \mathbb{N}, k_1, \dots, k_p : \mathcal{N} \to \mathcal{N}$,
such that every integer $y > 0$:
\[
\bigwedge_{0 < i \le p} k_i(y) < y
\]
the function $f : \mathcal{N}^{n + 1} \to \mathbb{N}$ defined by:
\begin{enumerate}
\item $f(\vec{x}, 0) = g(\vec{x})$
\item $f(\vec{x}, y + 1) = h(f(\vec{x}, k_1(y)), \dots, f(\vec{x}, k_p(y)), \vec{x}, y, f(\vec{x}, y))$
\end{enumerate}

is also primitive recursive.
\end{lemma}



\begin{definition}[\godel \ numbering of the $\mathcal{L}_A$-formula]
The \godel \ numbering of the $\mathcal{L}A$-formula is as follows:

\begin{equation*}
\begin{array}{lcl}
\phi = t_0 = t_1 & \rightsquigarrow & \ulcorner \phi \urcorner = \alpha_3(\ulcorner t_0 \urcorner, \ulcorner t_1 \urcorner, 4) \\
\phi = \neg \psi & \rightsquigarrow & \ulcorner \phi \urcorner = \alpha_3(\ulcorner \psi \urcorner, 0, 5) \\
\phi = \phi_0 \land \phi_1 & \rightsquigarrow & \ulcorner \phi \urcorner = \alpha_3(\ulcorner \phi_0 \urcorner, \ulcorner \phi_1 \urcorner, 6) \\
\phi = \phi_0 \lor \phi_1 & \rightsquigarrow & \ulcorner \phi \urcorner = \alpha_3(\ulcorner \phi_0 \urcorner, \ulcorner \phi_1 \urcorner, 7) \\
\phi = \phi_0 \to \phi_1 & \rightsquigarrow & \ulcorner \phi \urcorner = \alpha_3(\ulcorner \phi_0 \urcorner, \ulcorner \phi_1 \urcorner, 8) \\
\phi = \phi_0 \leftrightarrow \phi_1 & \rightsquigarrow & \ulcorner \phi \urcorner = \alpha_3(\ulcorner \phi_0 \urcorner, \ulcorner \phi_1 \urcorner, 9) \\
\phi = \forall x_n \psi & \rightsquigarrow & \ulcorner \phi \urcorner = \alpha_3(\ulcorner \psi \urcorner, n, 10) \\
\phi = \exists x_n \psi & \rightsquigarrow & \ulcorner \phi \urcorner = \alpha_3(\ulcorner \psi \urcorner, n, 11)
\end{array}
\end{equation*}



\begin{lemma}
The set of all codes of formula from $\mathcal{L}_A$ is primitive recursive:
\[
\{ \ulcorner \phi \urcorner \mid \phi \text{ is a formula from } \mathcal{L}_A  \}.
\]
\end{lemma}

\end{definition}


\begin{lemma}
The set of all codes of terms from $\mathcal{L}_A$ that contain the variable $x_n$ is primitive recursive:
\[
\mathcal{T}_{\checkmark x} = \{ (\ulcorner t \urcorner, n) \mid t \text{ is a term from } \mathcal{L}_A \text{ and } t \text{ contains } x_n  \}.
\]
\end{lemma}


\begin{lemma}
The set of all codes of terms from $\mathcal{L}_A$ that do not contain the variable $x_n$ is primitive recursive:
\[
\mathcal{T}_{\neg x} = \{ (\ulcorner t \urcorner, n) \mid t \text{ is a term from } \mathcal{L}_A \text{ and } t \text{ does not contain } x_n  \}.
\]
\end{lemma}


\begin{lemma}
The set of all codes of formula from $\mathcal{L}_A$ that contain the variable $x_n$ is primitive recursive:
\[
\mathcal{F}_{\checkmark x} = \{ (\ulcorner \phi \urcorner, n) \mid \phi \text{ is a formula from } \mathcal{L}_A \text{ and } \phi \text{ contains } x_n  \}.
\]
\end{lemma}


\begin{lemma}
The set of all codes of formula from $\mathcal{L}_A$ that do not contain the variable $x_n$ is primitive recursive:
\[
\mathcal{F}_{\neg x} = \{ (\ulcorner \phi \urcorner, n) \mid \phi \text{ is a formula from } \mathcal{L}_A \text{ and } \phi \text{ does not contain } x_n  \}.
\]
\end{lemma}


\begin{lemma}
The set of all codes of formula from $\mathcal{L}_A$ that contain the variable $x_n$ as free variable is primitive recursive:
\[
\mathcal{F}_{\checkmark x \ free} = \{ (\ulcorner \phi \urcorner, n) \mid \phi \text{ is a formula from } \mathcal{L}_A \text{ and } x_n \text{ is free in } \phi  \}.
\]
\end{lemma}


\begin{lemma}
The set of all codes of formula from $\mathcal{L}_A$ that contain the variable $x_n$ as bound variable is primitive recursive:
\[
\mathcal{F}_{\checkmark x \ bound} = \{ (\ulcorner \phi \urcorner, n) \mid \phi \text{ is a formula from } \mathcal{L}_A \text{ and } x_n \text{ is bound in } \phi \}.
\]
\end{lemma}


\begin{lemma}
The set of all codes of closed formula from $\mathcal{L}_A$ is primitive recursive:
\[
\mathcal{F}_{\checkmark closed} = \{ \ulcorner \phi \urcorner \mid \phi \text{ is a closed formula from } \mathcal{L}_A \}.
\]
\end{lemma}


\begin{lemma}
The function $S^\mathcal{T}_{ub.}(n_u, n_t, n) : \mathcal{N}^3 \to \mathcal{N}$ defined below is primitive recursive:
\begin{equation*}
s^\mathcal{T}_{ub.}(n_u, n_t, n) =
\begin{cases}
\ulcorner u_{[t/x_n]} \urcorner & \text{ if } n_u \in \mathcal{T}, n_t \in \mathcal{T} \text{ and } n_u = \ulcorner u \urcorner, n_t = \ulcorner t \urcorner \\
0 & otherwise
\end{cases}
\end{equation*}
\end{lemma}


\begin{lemma}
The function $S^\mathcal{F}_{ub.}(n_u, n_t, n) : \mathcal{N}^3 \to \mathcal{N}$ defined below is primitive recursive:
\begin{equation*}
s^\mathcal{F}_{ub.}(n_\phi, n_t, n) =
\begin{cases}
\ulcorner \phi_{[t/x_n]} \urcorner & \text{ if } n_\phi \in \mathcal{F}, n_t \in \mathcal{T} \text{ and } n_u = \ulcorner u \urcorner, n_t = \ulcorner t \urcorner \\
0 & otherwise
\end{cases}
\end{equation*}
\end{lemma}


\begin{definition}[coding and decoding sequences]
We define $\ulcorner \urcorner : \mathcal{N}^\omega \to \mathcal{N}$ as follows:
\begin{equation*}
\begin{cases}
\ulcorner \epsilon \urcorner & = 0 \\
\ulcorner x_0, \dots, x_p \urcorner & = \prod(0)^{x_0} \cdot \prod(1)^{x_1} \cdots \prod({p})^{x_p}
\end{cases}
\end{equation*}
where $\prod(i)$ enumerates the prime numbers.

We define $\llcorner \urcorner : \mathcal{N}^2 \to \mathcal{N}$ as follows:
\[
{_\llcorner n \urcorner}^i = \mu x \le n \; \prod(i)^{i + 1} \text{ does not divide } n.
\]
\end{definition}


\begin{definition}[\godel \ numbering of the $\mathcal{L}_A$-finite sets of formula]
The \godel \ numbering of any set $\Delta = \{ \phi_0, \phi_1, \dots, \phi_p \}$
of $\mathcal{L}_A$-formula is any integer of the form:
\begin{equation*}
\begin{cases}
\ulcorner \oslash \urcorner & = 1 \\
\ulcorner \Delta \urcorner & = \prod(i_0)^{\ulcorner \phi_0 \urcorner} \cdot \prod(i_1)^{\ulcorner \phi_1 \urcorner} \dots \prod(i_p)^{\ulcorner \phi_p \urcorner}
\end{cases}
\end{equation*}

We denote $\mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})}$ the set of codes of finite sets of formula:
\[
\mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} = \{ \Delta \mid \Delta \text{ is some finite set of } \mathcal{L}_A formula \}.
\]

\end{definition}


\begin{lemma}
The set $\mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})}$ of codes of finite sets of formula is primitive recursive.
\end{lemma}


\begin{lemma}

There exists two primitive recursive functions $\mathcal{R}_{em.} :
\mathcal{N}^2 \to \mathcal{N}$ and $\mathcal{A}_{dd.} : \mathcal{N}^2
\to \mathcal{N}$ such chat:
\begin{equation*}
\mathcal{A}_{dd.}(n, m) =
\begin{cases}
\ulcorner \Delta \cup \{\phi\} \urcorner & \text{ if } n = \ulcorner \phi \urcorner \in \mathcal{F} \text{ and } m = \ulcorner \Delta \urcorner \in \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} \\
0 & \text{ if } n \notin \mathcal{F} \text{ or } m \notin \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})}
\end{cases}
\end{equation*}

\begin{equation*}
\mathcal{R}_{em.}(n, m) =
\begin{cases}
\ulcorner \Delta \backslash \{\phi\} \urcorner & \text{ if } n = \ulcorner \phi \urcorner \in \mathcal{F} \text{ and } m = \ulcorner \Delta \urcorner \in \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} \\
0 & \text{ if } n \notin \mathcal{F} \text{ or } m \notin \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})}
\end{cases}
\end{equation*}


\end{lemma}


\begin{lemma}
The following set is primitive recursive:
\[
\mathcal{I}_{ns.} = \{ (\ulcorner \phi \urcorner, \ulcorner \Delta \urcorner) \in \mathcal{N}^2 \mid \ulcorner \phi \urcorner \in \mathcal{F}, \  \ulcorner \Delta \urcorner \in \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} \text{ and } \phi \in \Delta \}
\]
\end{lemma}


\begin{lemma}
The following set if primitive recursive:
\[
\mathcal{E}_{qu.} = \{ (\ulcorner \Gamma \urcorner, \ulcorner \Delta \urcorner) \in \mathcal{N}^2 \mid \ulcorner \Gamma \urcorner \in \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})}, \  \ulcorner \Delta \urcorner \in \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} \text{ and } \Gamma = \Delta \}
\]
\end{lemma}



\begin{lemma}
There exists a primitive recursive function $\mathcal{U}_{nion} : \mathcal{N}^2 \to \mathcal{N}$ such that:

\begin{equation*}
\mathcal{U}_{nion}(n, m) =
\begin{cases}
0 & \text{ if } n \notin \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} or m \notin \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} \\
\ulcorner \Gamma' \cup \Delta' \urcorner & \text{ if } n = \ulcorner \Gamma \urcorner \in \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} \text{ and } m = \ulcorner \Delta \urcorner \in \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} \text{ and } \ulcorner \Gamma' \cup \Delta' \urcorner \ \mathcal{E}_{qu.} \ \ulcorner \Gamma \cup \Delta \urcorner
\end{cases}
\end{equation*}
\end{lemma}


\begin{definition}[\godel \ numbering of the $\mathcal{L}_A$-sequents from sequent calculus]
The \godel \ numbering of any sequent $\Gamma \vdash \Delta$ is
\[
\ulcorner \Gamma \vdash \Delta \urcorner = \alpha_2(\ulcorner \Gamma \urcorner, \ulcorner \Delta \urcorner)
\]

We denote $SQ$ the set of codes of finite sets of formula:
\[
SQ = \{ \ulcorner \Gamma \vdash \Delta \urcorner \mid \Gamma, \Delta \in \mathcal{C}_{\mathcal{P}_{\small fin.}(\mathcal{F})} \}
\]

Given any integer $n$ we use the notation $^l n$ for $\beta_2^1(n)$ and $^r n$ for $\beta_2^2(n)$. This way,
\[
n = \ulcorner \Gamma \vdash \Delta \urcorner \quad \longrightarrow \quad {^l n = \ulcorner \Gamma \urcorner} \text{ and } {^r n = \ulcorner \Delta \urcorner}
\]
\end{definition}


\begin{lemma}
The set $SQ$ of codes of sequents of sequent calculus is primitive recursive.
\end{lemma}


\begin{definition}[\godel \ numbering of the axioms of sequent calculus]
\[
AX = \{ \alpha_2(2^{\ulcorner \phi \urcorner}, 2^{\ulcorner \phi \urcorner}) \mid \ulcorner \phi \urcorner \in \mathcal{F} \}
\]
\end{definition}


\begin{lemma}
The set $AX$ of codes of axioms of sequent calculus is primitive recursive.
\end{lemma}


## Coding the Proofs


\begin{figure}
\center \textbf{Sequent Calculus}
\begin{framed}
Axioms \\

\infax[ax]
{ \phi \vdash \phi }

\hrulefill

Logical Rules \\

\begin{multicols}{3}

\infrule[$\land_{l1}$]
{  \Gamma, \phi \vdash \Delta }
{  \Gamma, \phi \land \psi \vdash \Delta }

\infrule[$\land_{l2}$]
{  \Gamma, \psi \vdash \Delta }
{  \Gamma, \phi \land \psi \vdash \Delta }

\infrule[$\land_r$]
{  \Gamma \vdash \phi, \Delta \andalso \Gamma \vdash \psi, \Delta }
{  \Gamma \vdash  \phi \land \psi, \Delta }

\end{multicols}

\begin{multicols}{3}

\infrule[$\lor_l$]
{  \Gamma, \phi \vdash \Delta \andalso \Gamma, \psi \vdash \Delta }
{  \Gamma, \phi \lor \psi \vdash  \Delta }

\infrule[$\lor_{r1}$]
{  \Gamma \vdash \phi, \Delta }
{  \Gamma \vdash \phi \lor \psi, \Delta }

\infrule[$\lor_{r2}$]
{  \Gamma \vdash \psi, \Delta }
{  \Gamma \vdash \phi \lor \psi, \Delta }

\end{multicols}

\begin{multicols}{2}

\infrule[$\to_l$]
{ \Gamma \vdash \phi, \Delta \andalso \Gamma, \psi \vdash \Delta }
{ \Gamma, \phi \to \psi \vdash \Delta }

\infrule[$\to_r$]
{ \Gamma, \phi \vdash \psi, \Delta }
{ \Gamma \vdash \phi \to \psi, \Delta }

\end{multicols}

\begin{multicols}{2}
\infrule[$\neg_l$]
{ \Gamma \vdash \phi, \Delta }
{ \Gamma \neg \phi \vdash \Delta }

\infrule[$\neg_r$]
{ \Gamma, \phi \vdash \Delta }
{ \Gamma \vdash \neg \phi, \Delta }

\end{multicols}

\begin{multicols}{2}

\infrule[$\forall_l$]
{ \Gamma, \phi_{[t/x]} \vdash \Delta }
{ \Gamma, \forall x \phi \vdash \Delta }

\infrule[$\forall_r$]
{ \Gamma \vdash \phi_{[y/x]}, \Delta }
{ \Gamma \vdash \forall x \phi, \Delta }

\end{multicols}

\begin{multicols}{2}

\infrule[$\exists_r$]
{ \Gamma, \phi_{[y/x]} \vdash \Delta }
{ \Gamma, \exists x \phi \vdash \Delta }

\infrule[$\exists_r$]
{ \Gamma \vdash \phi_{[t/x]}, \Delta }
{ \Gamma \vdash \exists x \phi, \Delta }

\end{multicols}

\begin{multicols}{2}

\infrule[Ref]
{ \Gamma, t = t \vdash \Delta }
{ \Gamma \vdash \Delta }

\infrule[Rep]
{ \Gamma, t = s, \phi_{[s/x]}, \phi_{[t/x]} \vdash \Delta }
{ \Gamma, s = t, \phi_{[t/x]} \vdash \Delta }

\end{multicols}

\hrulefill

Structural Rules

\begin{multicols}{4}

\infrule[$wkn_l$]
{ \Gamma \vdash \Delta }
{ \Gamma, \phi \vdash \Delta }

\infrule[$wkn_r$]
{ \Gamma \vdash \Delta }
{ \Gamma \vdash \phi, \Delta }

\infrule[$ctr_l$]
{ \Gamma, \phi, \phi \vdash \Delta }
{ \Gamma, \phi \vdash \Delta }

\infrule[$ctr_r$]
{ \Gamma \vdash \phi, \phi, \Delta }
{ \Gamma \vdash \phi, \Delta }

\end{multicols}

\hrulefill

Cut Rule

\infrule[cut]
{ \Gamma \vdash \phi, \Delta \andalso \Gamma', \phi \vdash \Delta' }
{ \Gamma, \Gamma' \vdash \Delta, \Delta' }

\end{framed}
\end{figure}
