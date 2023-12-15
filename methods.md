---
layout: default
---

## Methods
On this page we will discuss the major machine learning methods employed to analyze partial differential equations. The three architectures that we analyze represent a progression in difficulty. In architecture, implementation, and analysis, each successive architecture becomes more complex, but leverages key techniques to better capture, characterize, and represent our desired systems.

The first architecture is a simple Physics-Informed Neural Network (PINN). The core of this architecture is a multi-layer perceptron (MLP) that learns system final conditions based on initial conditions. 

We follow this with the more complicated Fourier Physics-Informed Neural Network (FPINN), which leverages a Fourier learning layer to learn in multiple bases and capture more nuanced dynamics of the system. 

Finally, we conclude with a Physics-Informed Neural Operator (PINO) which unites techniques from the FPINN and a new training cycle to capture generalizable differential operators. 

More details on all three models is presented below. By developing these three models, we have a strong baseline to compare and discuss model shortcomings and effectiveness.  

### PINN

The Physics-Informed Nerual Network (PINN) was implemented in PyTorch, based on the [original paper](https://arxiv.org/abs/1711.10561) and corresponding [TensorFlow implementation](https://github.com/314arhaam/heat-pinn/blob/main/codes/heatman.ipynb). Beyond transitioning to PyTorch, our implementation introduced several novel features, including a new way to customize training scenarios, a modified model architecture, and new loss function. The training scenario customization is discussed in full on our [data](./data.md) page. 

The PINN architecture is a multi-layer perceptron (MLP), meaning that all activations are fully connected. Each fully-connected layer is followed by a tanh activation function, which maps each activation to the range $$\alpha \in (-1, 1)$$. The architecture contains seven fully-connected layers, each with 20 activations. This architecture is depicted visually below:

![PINN Diagram](/assets/imgs/MLP_diagram.png)

To train our model, we used two loss terms to enforce boundary conditions and differential loss. Our differential loss was altered from the original paper and implementation, seeking to solve the Helmholtz equation in addition to the heat equation. The two loss functions are below, where $$u$$ is the scalar output of the network.

$$\mathcal{L}_{boundary} = \text{mean}((x - \hat{x})^{2}) $$

$$\mathcal{L}_{PDE} = \text{mean}((\frac{\partial^2 u}{\partial x} + \frac{\partial^2 u}{\partial y} + k^2 \cdot u)^2) $$


### Fourier PINN

### PINO
