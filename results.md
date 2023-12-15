---
layout: default
---

## Results
Below, we will present and discuss our results for the three major model architectures that were explained in [methods](./methods.md). Because each architecture has its own strengths and weaknesses, our results suggest that certain methods are best suited for certain scenarios. By exploring these results and drawing more general conclusions, we help to clarify the variable effectiveness and future of each of these model architectures.  

### PINN

We trained and tested our PINN model on three different scenarios. In all three cases, the learning rate was held constant at `5e-4`

| Simulation | num_sample_points | border_coordinates | temp_range | epochs | k |
|:-----------|:------------------|:-------------------|:-----------|:-------|:--|
| 1          | 2000              | [-1,1]             | [-1,1]     | 3000   | 1 |
| 2          | 2000              | [-1,1]             | [-1,1]     | 2000   | 2 |
| 3          | 8000              | [-5,5]             | [-3,3]     | 2000   | 2 |

The train and test results from simulation 1 are below:

![Validation Loss for PINN, Simulation 1](/assets/imgs/PINN_1_Validation.png) ![Final State for PINN, Simulation 1](/assets/imgs/PINN_1_Heat.png)

The top plot demonstrates the validation loss over our 3000 epochs of training for simulation 1. As we can see it succesfully converges, suggesting a strong model fit was achieved. The bottom plot depicts the final state of the hot plate system. We have successfully captured the radiant heat eminating from the bottom, hot edge of the plate, suggesting we have accurately modeled our system. 

The train and test results from simulation 2 are below:

![Validation Loss for PINN, Simulation 2](/assets/imgs/PINN_2_Validation.png) ![Final State for PINN, Simulation 2](/assets/imgs/PINN_2_Heat.png)

Similarly, the validation loss depicted in the top plot suggests convergence over our training time for simulation 2. Additionally, the bottom plot's depiction of the final state of the Helmholtz-modified hot plate system is consistent with our expected results, suggesting we have again accurately modeled our system. 

The train and test results from simulation 3 are below:

![Validation Loss for PINN, Simulation 3](/assets/imgs/PINN_3_Validation.png) ![Final State for PINN, Simulation 3](/assets/imgs/PINN_3_Heat.png)

Again, the validation loss in the top plot suggests that we have achieved convergence over our training time for simulation 3. However, we see an odd, periodic banding effect across the plate. We believe this is likely due to model underfitting, a limitation of the basic PINN architecture.

From both our own experience of training the PINN and our reading of the literature, it seems that PINNs are "finicky" and difficult to optimize, which is a trade-off since they also require less data.

### Fourier PINN

For direct comparison with our PINN, we trained and tested our FPINN model on the same three different scenarios. In all three cases, the learning rate was held constant at `5e-4`. Note that simulation 3 for the FPINN was trained over 3000 epochs versus the 2000 epochs trained for simulation 3 for the PINN. 

| Simulation | num_sample_points | border_coordinates | temp_range | epochs | k |
|:-----------|:------------------|:-------------------|:-----------|:-------|:--|
| 1          | 2000              | [-1,1]             | [-1,1]     | 3000   | 1 |
| 2          | 2000              | [-1,1]             | [-1,1]     | 2000   | 2 |
| 3          | 8000              | [-5,5]             | [-3,3]     | 3000   | 2 |

The train and test results from simulation 1 are below:

![Validation Loss for FPINN, Simulation 1](/assets/imgs/FPINN_1_Validation.png) ![Final State for FPINN, Simulation 1](/assets/imgs/FPINN_1_Heat.png)

Just as with the PINN implementation for simulation 1, we see a similar level and rate of convergence in the top plot, which shows the validation loss over the 3000 epochs of training for our FPINN. The bottom plot again depicts the final state of the hot plate system, which captures the expected radiant heat dynamics, and is consistent with the PINN model output. 

The train and test results from simulation 2 are below:

TODO comment on how these look

![Validation Loss for FPINN, Simulation 2](/assets/imgs/FPINN_2_Validation.png) ![Final State for FPINN, Simulation 2](/assets/imgs/FPINN_2_Heat.png)

The train and test results from simulation 3 are below:

![Validation Loss for FPINN, Simulation 3](/assets/imgs/FPINN_3_Validation.png) ![Final State for FPINN, Simulation 3](/assets/imgs/FPINN_3_Heat.png)

TODO comment on how these look

TODO provide general thoughts on effectiveness of FPINN

### PINO

### Conclusion and Future Improvements

TODO reiterate general thoughts on effectiveness of each model
