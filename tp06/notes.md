- ex3: to avoid using loops consider using matrix multiplication for ex 3
- ex5: Sum = 1 => blurred, sum = 0 => will have edges (approximation of 2nd derivative?)

    $$ \nabla^2{f(x,y) = \sum_{-\infty}^{\infty}{ \sum_{-\infty}^{\infty}{c_{?m}*f(x-n, y-m) }}} $$

- bonus: scipy correlate 2d

## Delta Function

- Theme 7
- P. 25 / (or 35)

### Special Signals

Continuous Delta Function

\begin{equation*}
    \delta(t) = \begin{cases}
        \infty & t = 0 \\
        0 & t \neq 0
    \end{cases}
    \\ \int_{-\infty}^{\infty}{\delta(t)dt} = 1
\end{equation*}

### Superpositions baisis of delta-funbctions

$$
    x(n) = \sum_{k=-\infty}^{\infty}{x(k)\delta(n-k)}
$$


