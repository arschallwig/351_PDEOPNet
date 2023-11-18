---
layout: default
---

## Project Progress Report (17 November 2023)

This page is the Project Progress Report for 17 November 2023. This page will discuss the state of the project as of that date. We will begin by describing the data used for our project and how it was attained. We will then present three plots of our data to help visualize key aspects of our progress. We will describe more generally what work we have done so far, and create a plan for the next weeks until the project due date. Finally, we will provide a brief reflection on what we have learned so far.  

$$a^2 + b^2 = c^2$$

$$\begin{aligned}
E = mc^2
\end{aligned}$$

### Data
As our model is solving differential equations, our data are samples of the systems defined by the differential equation. For our first PINN model, we are specifically attempting to model the heat equation, thus our data can be thought of as the initial and final states of a thermodynamic system. In our case, we are specifically training on a 2-dimensional model of heat transfer. Thus, for $N$ samples in space we have $d=3$ dimensions representing the $xy$ location and initial temperature, $T$ of the point sample. Thus, our input data, $D_{in}$ can be viewed as a second-degree tensor:

$$D_{in} = \begin{bmatrix} x_0 & y_0 & T_0 \\
                        x_1 & y_1 & T_1 \\
                        ... & ... & ... \\
                        x_N & y_N & T_N \end{bmatrix}$$

As we are attemping to solve the heat equation, our labels, or the targets for our prediction, is simply the end thermodynamic state of each point sample. This will take a similar shape as $D_{in}$ as we need $d=3$ dimensions to represent $xy$ location and final temperature. Thus, our labels $D_{l}$ are similarly a a second-degree tensor:

$$D_{l} = \begin{bmatrix} x_0 & y_0 & T_0 \\
                        x_1 & y_1 & T_1 \\
                        ... & ... & ... \\
                        x_N & y_N & T_N \end{bmatrix}$$

### Visualizations

### Work Completed
Prior to this week, our team spent a majority of our time reading the current literature surrounding PDEs, PINNs, and neural operators. Due to the largely conceptual nature of this field, we had to consult countless resources including published literature, articles, recorded lectures, and more to fully understand the space. We found that, in many ways, this is still a very cutting-edge disclipline, with several milestone pieces having been published in recent months. As such, this rapidly-developing field necessarily lends itself to new ideas and creativity in ways that more established fields of study may not.   

Given the nebulus and quickly-changing nature of our topic, we decided it was imperative to identify key deliverables for our project so we could avoid getting lost in the flux of new work. With this in mind, this week we solidified our final plans for the structure of our project, and delegated necessary tasks to each member. We began by establishing the key goals enumerated on the cover page of this website. We seek to:

1. Develop a PINN model to solve important families of PDEs
2. Modify this model to transform data and compare performance across multiple bases of representation
3. Attempt to generalize our model as a Neural Operator, allowing us to not just solve PDEs numerically, but capture the functional structure of a PDE solution in our network

With these goals in mind, we then delegated and began necessary tasks. Of primary importance was creating training data, developing the first baseline PINN model, and researching Neural Operators. 

### Plan for Completion

### Reflections on Learning
