---
layout: default
---

## Results
Below, we will present and discuss our results for the three major model architectures that were explained in [methods](./methods.md). Because each architecture has its own strengths and weaknesses, our results suggest that certain methods are best suited for certain scenarios. By exploring these results and drawing more general conclusions, we help to clarify the variable effectiveness and future use cases of each of these model architectures.  

### PINN

We trained and tested our PINN model on three different scenarios. In all three cases, the learning rate was held constant at `5e-4`. A table describing those three scenarios is below:

| Simulation | num_sample_points | border_coordinates | temp_range | epochs | k |
|:-----------|:------------------|:-------------------|:-----------|:-------|:--|
| 1          | 2000              | [-1,1]             | [-1,1]     | 3000   | 1 |
| 2          | 2000              | [-1,1]             | [-1,1]     | 2000   | 2 |
| 3          | 8000              | [-5,5]             | [-3,3]     | 2000   | 2 |

The train and test results from simulation 1 are below:

![Validation Loss for PINN, Simulation 1](/assets/imgs/PINN_1_Validation.png) ![Final State for PINN, Simulation 1](/assets/imgs/PINN_1_Heat.png)

The top plot demonstrates the validation loss over our 3000 epochs of training for simulation 1. As we can see it succesfully converges, suggesting a strong model fit was achieved. The bottom plot depicts the final state of the hot plate system. We have successfully captured the radiant heat eminating from the bottom, hot edge of the plate, suggesting we have accurately modeled the dynamics of our system. Importantly, the edges have maintained their constant temperature, as enforced by our boundary loss, and the sample points distributed throughout the plate now respect the heat equation. 

The train and test results from simulation 2 are below:

![Validation Loss for PINN, Simulation 2](/assets/imgs/PINN_2_Validation.png) ![Final State for PINN, Simulation 2](/assets/imgs/PINN_2_Heat.png)

Similarly, the validation loss depicted in the top plot suggests convergence over our training time for simulation 2. Notably there are slight spikes in the validation loss once the model approaches convergence. While it is difficult to pinpoint the exact reason for this in such a deep model, we believe it may appear as an artifact of training, where gradients briefly "explode" for certain points. For example, these spikes could occur between training epochs, resulting in a significant shift in gradient, and thus loss, as the model moves from propagating the last point of the previous epoch to the first point of the new epoch.  Importantly, the bottom plot's depiction of the final state of the Helmholtz-modified hot plate system is consistent with our expected results, suggesting we have again accurately modeled our system. 

The train and test results from simulation 3 are below:

![Validation Loss for PINN, Simulation 3](/assets/imgs/PINN_3_Validation.png) ![Final State for PINN, Simulation 3](/assets/imgs/PINN_3_Heat.png)

Again, the validation loss in the top plot suggests that we have achieved convergence over our training time for simulation 3. However, we see an odd, periodic banding effect across the plate. We believe this is likely due to model underfitting, a limitation of the basic PINN architecture. Rather than spreading evenly throughout the space, we see a periodic shape that, while sourcing from the bottom of the plate, is not wholly accurate to the expected output of the Helmholtz system. 

Overall, our PINN has provided solid output for our heat and Helmholtz scenarios. While it has some fitting issues with a larger system region and Helmholtz constant, it overall performs well for being a relatively simple architecture. Thus, we conclude that the PINN is well-suited for simple systems where initial conditions are consistent and there are not too many high-frequency elements in the system. While the model must be re-trained for different system initial conditions, once trained it can provide accurate and consistent outputs at smaller scales.  

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

![Validation Loss for FPINN, Simulation 2](/assets/imgs/FPINN_2_Validation.png) ![Final State for FPINN, Simulation 2](/assets/imgs/FPINN_2_Heat.png)

Again, the validation loss converges, after a slight plateau for the first several hundred epochs. While this could look like convergence if we did not train past 500 epochs, this suggests that in this region we had not yet fit our model fully. Thus, it was important that we continued to expand the number of training epochs to where we steady decline as shown in the plot above. Again, the final state is consistent with the Helmholtz system and mirror the output of the PINN on scenario 2. 

The train and test results from simulation 3 are below:

![Validation Loss for FPINN, Simulation 3](/assets/imgs/FPINN_3_Validation.png) ![Final State for FPINN, Simulation 3](/assets/imgs/FPINN_3_Heat.png)

The valiation loss converges after demonstrating a slight plateau effect, much as occurred in simulation 2. Yet again, we trained past this plateau to the full 3000 epochs as set in our testing strategy. The system appears to reach a more consistent state than our PINN for simulation 3. We see there is a more progressive gradient in "heat" over the plate, and there are no significant oscillatory effects as with the PINN. This suggests that the FPINN can more accurately capture and interpret the high-frequency dynamics of the Helmholtz equation.  

While suffering from the same initial conditions limitation as the PINN, the FPINN appears to perform well at capturing and representing high-frequency system dynamics. In the Helmholtz equation model, it accurately captures and "smoothes" out the high-frequency terms in the system which arise from the squared constant in the equation. Again, the FPINN is trained dependent on initial conditions and would need to be retrained for structurally-different initial conditions, but the emphasis of high-frequency components in the model allows us to achieve consistently competitive results despite a smaller architecture. 

### FNO

### Conclusion

While all models have their strengths and weaknesses, the three models differ largely in their complexity, ability to capture high-frequency dynamics, and robustness to initial system conditions. The PINN is a simple model, but is not particularly strong at capturing high-frequency system dynamics, and is fully dependent on system initial conditions. The FPINN is similarly simple and dependent on initial conditions, but can capture high-frequency dynamics very well. Finally the FNO, though complex, is the most generalizable, allowing it to capture high-frequency dynamics and be robust to system initial conditions. Thus, if enough compute resources are available, we suggest that the Fourier Neural Operator model is the most for learning the dynamics of partial differential equations. Although it can be difficult to train, its generalizability with continued focus on frequency-domain learning, allows it to most accurately, and most consistently, model differential equations. 
