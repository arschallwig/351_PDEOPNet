---
layout: default
---


#### PDENets is a collection of Physics-Informed Neural Networks (PINN) trained to solve key families of Partial Differential Equations (PDE) including the heat equation and Helmholtz equation. <!--- TODO list any more PDEs here (or update this current listing if need-be --> 

Systems defined by PDEs can be seen all around us. Whether in the diffusion of heat or quantum mechanics, physicists, engineers, mathematicians, and more rely on PDEs to model and understand the world.

As the systems that we study become more complex, the solutions to those systems become increasingly intractable, and simulations become increasingly intensive. A necessary supplement to the traditional numerical methods that have previously driven scientic computing are the new, data-driven methods heralded by machine learning. By leveraging large amounts of training data, machine learning models can approximate solutions to partial differential equations and capture system dynamics all at drastically increased speeds. 

PINNs are a cutting-edge class of machine learning models that unite the data-driven approach to modeling that is central to machine learning with the differential equations that are key in many scientific disciplines. Rather than learning from mass amounts of data alone, PINNs supplement this data and guide the learning process by enforcing a differential loss on the model. This means that, in addition to learning features from the data, the model will also adhere to the functional relationship defined by differential equations. 

PDENets is a collection of networks implemented to solve several important families of PDEs. We specifically implement and focus on the performance of general PINNs, Fourier PINNs, and Neural Operators (NO). In doing so, we explore questions regarding variable basis representation, system property analysis, and data processing. In our results, we draw conclusions regarding the strengths and weaknesses of these models, and what they are variably best suited for. For more on our project, please visit the links below:

[1. Overview](./overview.md)

[2. Data](./data.md)

[3. Methods](./methods.md)

[4. Results](./results.md)

[5. Project Progress Report](./project_progress_report.md)

[6. References](./references.md)
