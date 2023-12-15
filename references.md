---
layout: default
---

## References

This project was inspired by several recent (i.e. past 5 years) advances in using machine learning, specifically deep learning, techniques to solve forward and inverse problems involving ordinary and partial differential equations which can be highly nonlinear. These techniques can be broadly categorized into the following:

[Physics-Informed Neural Networks (PINNs)](https://www.sciencedirect.com/science/article/abs/pii/S0021999118307125), which utilize both the experimental data and the physical constraints of the model in the regularizer.

[Neural Operators (NOs)](https://arxiv.org/abs/2108.08481), which are provably universal approximators for nonlinear, continuous operator solutions to families of partial differential equations. Work that builds upon this is the [Fourier Neural Operator (FNO)](https://arxiv.org/abs/2010.08895), introduced to solve various PDEs including Navier-Stokes, being several orders of magnitude faster than classical solvers. 

These two techniques are combined in [Physics-Informed Neural Operators (PINOs)](https://arxiv.org/abs/2111.03794), which use both training data and physical constraints to learn the solution operator of a given family of parametric partial differential equations (PDEs).

In the data section we referenced a recent (2023) paper by Li et al. proposing [Geometry-Informed Neural Operators (GINOs)](https://arxiv.org/abs/2309.00583), which leverage graph and Fourier architectures to learn the solution operator for irregular geometries.

Additionally, this project references the seminal work from Kurt Hornik, Maxwell Stinchcombe, and Halbert White on the [Universal Approximation Theorem](https://www.sciencedirect.com/science/article/abs/pii/0893608089900208?via=ihub).

We also modified/adapted code from the following repositories:

[Navier-Stokes-Numerical-Solution-Using-FDM-FVM-LBM-Solver-Python-Scripting](https://github.com/rjwalia/Navier-Stokes-Numerical-Solution-Using-FDM-FVM-LBM-Solver-Python-Scripting/blob/main/2D%20Laplace%20Equation.py)
