# Simple and Multilayer Perceptron

The Perceptron is one of the first neural network models and the starting point for understanding basic concepts of supervised learning.

The network topology of a neuron shows that each input is multiplied by its synaptic weight, and then _h_ is calculated as $h = \sum_{j=1}^M w_jx_j$. Thus, the sign of _h_ is evaluated through the activation function, which will assess the sign of _h_. If it is positive, the output will be 1, and if it is negative, -1.

<image
src="/images/simplePerceptron.png"
alt="Simple Perceptron"
caption="**Figure 1**: Simple Perceptron">

To update the synaptic weights, the obtained output is subtracted from the desired output for the input pattern being evaluated. If the error for the pattern is non-zero, each weight coefficient wi is updated as:

$\Delta w_j(k) = \eta · x_j · (y_{desired} − y_{obtained}) $

$w_j(k) = w_j(k − 1) + \Delta w_j(k)$

The parameter $\eta$ is the learning rate. When it is smaller, it takes more iterations to converge to a possible solution, as it determines how much the synaptic weights are modified (i.e., how much the discriminating plane rotates).

<details>

  <summary> 1. Simple Perceptron </summary>

  Perceptrons were trained to solve AND and OR logic functions with 2 and 4 inputs. In the implementation, the learning rates and their influence on convergence to the solution were analyzed. The error evolution can be seen as the network adjusts its synaptic weights.

  <image
  src="/images/output_AND_2inputs.png"
  alt="Training result for AND with 2 inputs"
  caption="**Figure 1.1.1**: Training result for AND with 2 inputs">

  <image
  src="/images/error_AND_2inputs.png"
  alt="Global error evolution for AND with 2 inputs"
  caption="**Figure 1.1.2**: Perceptron error evolution during training">

  <image
  src="/images/weights_OR_4in.png"
  alt="Synaptic weights evolution for OR with 4 inputs"
  caption="**Figure 1.1.3**: Synaptic weights evolution for OR with 4 inputs">

  It is noted that this topology finds a solution only for linearly separable problems. If not, the simple perceptron will be unable to find a solution with zero total error.

  ## Capacity 

  The capacity gives an idea of how many random patterns a perceptron in a neural network of a certain size can be expected to learn. Training a simple model with patterns of different sizes, it is evaluated whether the perceptron could learn without errors. As the number of patterns increases, the capacity is observed to change, reflecting the perceptron's effectiveness in classifying the patterns. The results show the relationship between the pattern size and the perceptron’s performance.
  
  <image
  src="/images/capacity_perceptron.png"
  alt="Simple perceptron capacity"
  caption="**Figure 1.1.4**: Simple perceptron capacity for N = 40">

  It is important to note that in all cases, when training a network with _N_ inputs, the simple perceptron can learn up to _2N_ patterns.
  
</details>

<details>
  
  <summary> 2. Multilayer Perceptron </summary>
    
  For problems that are **not** linearly separable, such as the XOR logic function, a multilayer perceptron was trained.
    
  Using the backpropagation algorithm, it was demonstrated how this network can learn more complex relationships. The multilayer perceptron has hidden layers that allow the data to be transformed in a way that enables correct classification.

  <image
  src="/images/multilayerTopology.png"
  alt="Multilayer perceptron topology"
  caption="**Figure 1.2.1**: Multilayer perceptron topology">

  To visualize the effect of changing synaptic weights, two random weights were chosen, and a graph was made by slightly varying their values to explore the solution space, obtaining the minima and identifying in which region those synaptic weights can vary without affecting the global error.
  
  <image
  src="/images/error_XOR_3D.png"
  alt="Error map by varying two synaptic weights"
  caption="**Figure 1.2.2**: Error map by varying two synaptic weights">
  
  <image
  src="/images/error_XOR.png"
  alt="Error map by varying two synaptic weights in 2D"
  caption="**Figure 1.2.3**: Error map by varying two synaptic weights in 2D">

</details>

## Code and Other Topics Studied

This development and more can be found in the file [`perceptron.ipynb`](../perceptron.ipynb), where other practical examples are also analyzed:
  - Implementation of a network with backpropagation to learn a continuous function. Minibatch analysis.
  - Optimization through a genetic algorithm. Mutation, crossover, and population size analysis.
