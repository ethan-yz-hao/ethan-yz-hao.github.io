---
title: "Agent-Based Modeling Demo - Schelling's Segregation Model"
excerpt: "The classic Schelling's segregation model (Spring 2022) aiming to introduce the agent-based modeling method.<br/><img src='/images/portfolio-3-50.gif' width='400'>"
collection: portfolio
---

Schelling's segregation model is an agent-based model developed by economist Thomas Schelling in 1971. It does not include outside factors that place pressure on agents to segregate and demonstrate that having people with "mild" in-group preference towards their own group could still lead to a highly segregated society via de facto segregation.

## Modeling
Python Package Used: mesa

### Initial Status
Simplify a city into a N × N gird, with each white block represents one household with no inhabitant (accounts for 10% of the grid). Assume that the city has 2 types of households with the same number, represented by two colors (red and blue). Randomly generate the above two types of households in the grid as the initial state of the model.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-3-grid.jpg){: width="200"} | 
|:--:|
| *grid* |

### Agent Behavior
For every household in the grid, there is only one rule: when the proportion of the same type of household in the surrounding 8 households falls below a certain threshold, the household will "move" and randomly go to any empty block in the grid. The higher the threshold, the less tolerant the households are to households who are different from them, and the more likely they are to "move". For households on the boundary of the grid, we assume that they can "see the households on the other side of the boundary". For the households in the lower right corner of the figure below, they can see all the households in the black boxed line.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-3-grid_frame.jpg){: width="200"} | 
|:--:|
| *behavior* |

### Execution Sequence
Next, the sequence of the households' actions is determined by randomly order all the households, and the households check the threshold then move in that order. After completing a round, a new order is generated.

### Terminating Criterion
Finally, the model requires an terminating criterion. By recording the number of households in the model that does not exceed the threshold, i.e., the number of households in the "happy" state, we can calculate the proportion of "happy" households in the grid (Happy Ratio). When the proportion of "happy" households reaches 100%, i.e., all households are "happy", the model is terminated.

## Result

### 50%
We started our analysis with a threshold of 50%, which seems to be a very tolerant society, after all, it has the same proportion of the two types of households in the grid, but it can be seen that the model gradually converges after a certain period of time, eventually forming a clear dividing line.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-3-50.gif){: width="300"} | 
|:--:|
| *50%* |

### 30%
By lowering the threshold to 30%, it can be found that segregation still emerged. We can calculate the "mean similarity" of the model using the proportion of the same type of household in the surrounding 8 households and averaging for all the households in the grid. "The "mean similarity" with 30% threshold converges to nearly 70%, which means that on average, 70% of the households around each household are the same, and segregation is still evident.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-3-30.gif){: width="300"} | 
|:--:|
| *30%* |

### 20%
There is no significant segregation until the threshold drops to 20%, at which point the "mean similarity" is close to 50%, the same proportion as the two types of households in the grid.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-3-20.gif){: width="300"} | 
|:--:|
| *20%* |

### 80%
Interestingly, if we increase the threshold to 80%, the "mean similarity" also drops to 50%. In this case, the percentage of "happy" households is very low, and all households are constantly "moving".

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-3-80.gif){: width="300"} | 
|:--:|
| *80%* |

## Conclusion
Among the various "emergence" phenomena, the "phase transition" - the qualitative change of the system - is one of the most amazing and important ones. In Schelling's segregation model, there is also a "phase transition" when the threshold gradually increases and the "mean similarity" first increases and then decreases. The convergence rate of the model also gradually decreases with the model starting from static convergence to dynamic equilibrium. As the model can still converge when the threshold is 65%, but cannot converge when it reaches 70%, the critical state of the model is between 65% and 70%.

Agent Based Model (ABM) is often used to study such "emergence" phenomena in complex systems. Schelling's segregation model is a classical ABM used to analyze the complex system of urban population distribution, which was proposed in 1971 and marked the move from theoretical to application of the Agent Based Modeling and Simulation (ABMS) method.