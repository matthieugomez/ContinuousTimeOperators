[![Build Status](https://travis-ci.org/matthieugomez/InfinitesimalGenerators.jl.svg?branch=master)](https://travis-ci.org/matthieugomez/InfinitesimalGenerators.jl)




## Create Infinitesimal Generators
- `generator(x, μx, σx)` returns the infinitesimal generator 𝔸 associated with the Markov process x: <br>
	<img src="img/dx.png" height ="30%" width = "30%">: <br> <img src="img/generator.png" height ="60%" width = "60%"> <br clear="all" />
-  `generator(x, μx, σx, μM, σM)` returns the tilted infinitesimal generator 𝔸 associated with the multiplicative functional M: <br>
	<img src="img/dM.png" height ="40%" width = "40%">: <br> <img src="img/generator_tilted.png" height ="80%" width = "80%"> <br clear="all" />

## General Tools
For an infinitesimal generator 𝔸:
- `principal_eigenvalue(𝔸)` returns a the principal eigenvalue of the matrix `𝔸`, its left eigenvector, and its right eigenvector
- `feynman_kac_backward(𝔸,  t, ψ, f, V)` returns the solution of the PDE `u_t(x, t) + 𝔸 u  - V(x, t) u + f(x, t) = 0` with `u(x, T) = ψ(x)`

## Convenience Functions
In addition, the package provides the following convenience functions, which simply apply the tools above to particular generators:
- `stationary_distribution(x, μx, σx)` returns the stationary distribution of `x`
- `hansen_scheinkman_decomposition(x, μx, σx, μM, σM)` returns the [Hansen-Scheinkman decomposition](https://www.nber.org/papers/w12650) of `M`
- `feynman_kac_forward(x, μx, σx; t, ψ, f, V)`	returns <img src="img/feynman_kac.png" height ="60%" width = "60%">
- `feynman_kac_forward(x, μx, σx, μM, σM; t, ψ)` returns  <img src="img/feynman_kac_tilded.png" height ="22%" width = "22%">


## Related Packages
- This package relies [BandedMatrices.jl](https://github.com/JuliaMatrices/BandedMatrices.jl) to represent infinitesimal generators efficiently. The principal eigenvalue of infinitesimal generators is found using [KrylovKit.jl](https://github.com/Jutho/KrylovKit.jl)
- This package is related to [DiffEqOperators.jl](https://github.com/JuliaDiffEq/DiffEqOperators.jl), which contains more general tools to solve differential equations.