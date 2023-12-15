---
layout: default
---

## Overview

Our goal in this project was to harness the power of learning based methods to solve different families of partial differential equations. While traditional numerical methods require complicated finite approximations, learning based methods can offer dramatically faster solutions - for example, models have been developed to solve the Navier Stokes equation 1000 times faster than normal solvers. For our specific use case, we decided to attempt to solve the heat equation as our first PDE family, since it has a closed form solution we could use to generate our own data and compare our model based solution to. The research in this field of learning based methods is cutting edge and constantly changing, and we decided to explore two of the most researched models - PINNs and neural operators. PINNs, or physics informed neural networks, are a branch of neural networks that introduce information about a physical process into the model training by adding a physics based term to the loss function. 
