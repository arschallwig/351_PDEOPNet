---
layout: default
---

## Data

# (Regular) PINN

Interestingly, we did not have to collect nor generate any data for the physics-informed neural network. Instead, we just enforced constant Dirichlet boundary conditions along the unit square's edges (representing a metal plate), and then randomly sampled various collocation points along the plate's surface where we enforced the physics-informed loss term of our objective function. Note that all the non-boundary points had zero initial conditions. An advantage of PINNs, as we've discussed, is that they require less training data due to the physics-informed loss guiding the solution approximation. 

# Fourier PINN
<!---
You can talk about in the first cell of data prep section of the new ipynb that I exported, I made it so we can custom choose like plate size and temp range and number of sampling points and such 
So you can talk about like our ability to programmatically build out new simulations 
--->

The Fourier PINN was very similar

# Neural Operator

Since neural operators are a continuous function-to-function mapping, and images are essentially functions of two-dimensional space (x and y), we can think of the neural operator as a continuous image-to-image mapping. Hence, we had images (of the same dimension) as input and output. Specifically, the images we generated are 64x64, with the heat intensity values at each pixel ranging from continuous values between -1 and 1. We generated this data by modifying the following code [CITATION] which solves the Laplace equation (which is just the steady state heat equation). We iterated it 2000 times to generate 2000 training pairs of images. The inputs were generated with (uniformly) randomly selected boundary conditions between -1 and 1, and zero initial conditions for all non-boundary points on the plate surface. In each iteration, we then solved the Laplace equation to get the steady state heat solution for our random initial state, and this image would be the corresponding output of the training pair. We found that solving for the steady state outputs did not take very long (especially compared to using Finite-Difference or Finite-Element methods, which would be necessary to see the time-evolution or non-steady state solutions), so most of the time was spent uploading them to Google Drive, so our group members could access the training pairs using the Colab files.

Before we decided to generate our own (synthetic) data, we found a dataset online which was generated for a paper [CITATION] which uses different machine learning techniques to solve essentially the same problem as us; finding the steady state solution to the heat equation, in their case for the purpose of studying heat conduction transfer. However, their dataset had varying geometries (e.g., rectangles, triangles, other shapes); this made sense for them as they used a convolutional neural network, and convolutional filters are translationally-invariant, meaning the network could better adapt to different plate geometries. Based on our understanding of neural operators (and PINNs), however, we didn't think our network(s) would generalize well to this training scheme, as they probably wouldn't capture wider-range space dependencies in the domain without some modification. This paper [CITATION] proposes a graph neural operator to account for varying geometries, and this could definitely be a next step in this project given more time.
