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


### Fourier PINN

### PINO

### Conclusion and Future Improvements
