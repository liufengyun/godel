# \godel's Second Incompleteness Theorem

## Peano Arithmetic and $I\Sigma_1^0$

**Peano Arithmetic** = **Robinson Arithmetic** + **induction**

1. $\forall x. Sx \neq 0$
2. $\forall x \exists y (x \neq 0 \to Sy = x)$
3. $\forall x \forall y (Sx = Sy \to x = y)$
4. $\forall x. x + 0 = x$
5. $\forall x \forall y (x + Sy = S(x + y))$
6. $\forall x. x \cdot 0 = 0$
7. $\forall x \forall y (x \cdot Sy = (x \cdot y) + x)$

**axiom schema (induction)** $((\phi_{[0/x_0]} \land \forall x_0 (\phi
  \to \phi_{[Sx_0/x_0]})) \to \forall x_0 \phi$.


\begin{example}
In Robinson arithemtic, we cannot prove addition is commutative. We can prove it
in Peano arithmetic.
\end{example}


\begin{example}
Any two terms are comparable in Peano arithmetic.
\end{example}


\begin{example}
Addition is associative in Peano arithemtic.
\end{example}


\begin{example}
Multiplication is commutative in Peano arithmetic.
\end{example}

\begin{example}
Multiplication distributes over addition in Peano arithmetic.
\end{example}

\begin{example}
Multiplication is associative in Peano arithemtic.
\end{example}


\begin{proposition}
The theory $Rob. + I\Sigma_0^1$ proves that:

\begin{enumerate}
\item addition is commutative and associative
\item multiplication is commutative and associative
\item multiplication distributes over addition
\end{enumerate}

\end{proposition}
