---
layout: default
---

## References

This project was inspired by several recent (i.e. past 5 years) advances in using machine learning, specifically deep learning, techniques to solve forward and inverse problems involving ordinary and partial differential equations which can be highly nonlinear. These techniques can be broadly categorized into the following:

Physics-Informed Neural Networks (PINNs), introduced in the following paper: https://www.sciencedirect.com/science/article/abs/pii/S0021999118307125

Neural Operators (NOs), introduced in the following paper: https://arxiv.org/abs/2108.08481. Work that builds upon this is the Fourier Neural Operator (FNO), introduced to solve various PDEs including Navier-Stokes, being several orders of magnitude faster than classical solvers: https://arxiv.org/abs/2010.08895. 

These two techniques are combined in Physics-Informed Neural Operators (PINOs), which use both training data and physical constraints to learn the solution operator of a given family of parametric partial differential equations (PDEs): https://arxiv.org/abs/2111.03794
