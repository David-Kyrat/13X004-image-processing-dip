- ex3: to avoid using loops consider using matrix multiplication for ex 3 ex5: Sum = 1 => blurred, sum = 0 => will have edges (approximation of 2nd derivative?)

    $$ \nabla^2{f(x,y) = \sum_{-\infty}^{\infty}{ \sum_{-\infty}^{\infty}{c_{?m}*f(x-n, y-m) }}} $$
- if its 0 we are taking edges
- if its 1 we have blurred

- bonus: scipy correlate 2d

## Delta Function

- Theme 7
- P. 25 / (or 35)
- P. 14 slides

### Special Signals

Continuous Delta Function

\begin{equation*}
    \delta(t) = \begin{cases}
        \infty & t = 0 \\
        0 & t \neq 0
    \end{cases}
    \\ \int_{-\infty}^{\infty}{\delta(t)dt} = 1
\end{equation*}

### Superpositions basis of delta-functions

$$
    x(n) = \sum_{k=-\infty}^{\infty}{x(k)\delta(n-k)}
$$

## back to tp

$$
    x(n) = \delta(n) + \delta(n-1) + \delta(n-4) \\ h(n) = \delta(n) + \delta(n-1) 
$$

    x = [1, 1, 0, 0, 1, ....]
        0           4
    h = [1, 1, ...]

convolve them

        x 1 1 0 0 1
    h   1 1    

Error in photo?
