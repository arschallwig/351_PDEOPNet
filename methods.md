---
layout: default
---

## Methods
On this page we will discuss the major machine learning methods employed to analyze partial differential equations. The three architectures that we analyze represent a progression in difficulty. In architecture, implementation, and analysis, each successive architecture becomes more complex, but leverages key techniques to better capture, characterize, and represent our desired systems.

The first architecture is a simple Physics-Informed Neural Network (PINN). The core of this architecture is a multi-layer perceptron (MLP) that learns system final conditions based on initial conditions. 

We follow this with the more complicated Fourier Physics-Informed Neural Network (FPINN), which leverages a Fourier learning layer to learn in multiple bases and capture more nuanced elements of the system. 

Finally, we conclude with a Physics-Informed Neural Operator (PINO) which unites techniques from the FPINN and a new training cycle to capture generalizable differential operators. 

More details on all three models is presented below. By developing these three models, we have a strong baseline to compare and discuss model shortcomings and effectiveness.  

### PINN

### Fourier PINN

### PINO
