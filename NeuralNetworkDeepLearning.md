## Using neural nets to recognize handwritten digits

- Human primary visual cortex (V1) has 140 million neurons with 10s of billions of connections between them.

#### Perceptron

- **Perceptron** : A perceptron takes several binary inputs x1, x2, ...xn and produces a single binary output.  The neuron's output, 0 or 1, is determined by whether the weighted sum ∑jwjxj is less than or greater than some threshold value.
  - This is the basic mathematical model used. Its a devixe that makes decisions by weightin up evidence.
- The neuron's output, 0 or 1, is determined by whether the weighted sum ∑jwjxj is less than or greater than some threshold value. This can be simplified as follows:
  1.  write ∑jwjxj as a dot product, w⋅x≡∑jwjxj, where w and x are vectors whose components are the weights and inputs, respectively
  2.  move the threshold to the other side of the inequality, and to replace it by what's known as the perceptron's bias, b≡−threshold
- Bias is a measure of how easy it is to get the perveptron to fire.
- NAND gate is universal for computation and can be used to build any logical funcitons.
- **The devise with such perceptrons can automatically tune the weights and biases of a notwoek of artificial neurons**.

#### Sigmoid 

-  A small change in the weights or bias of any single perceptron in the network can sometimes cause the output of that perceptron to completely flip, say from 0 to 1.
- This problem can be overcome by inroducing a new type of artificial neuron called a sigmoid neuron.
- Unlike a perceptron sigmoid outputs values between [0, 1].
- However, perceptrons and sigmoid have similar characteristics. When z=w⋅x+b is large and positive, the output from the sigmoid neuron is approximately 1, just as it would have been for a perceptron
- The smoothnes of sigmoid is very important as small changes Δwj in the weights and Δb in the bias will produce a small change Δoutput in the output from the neuron

#### Architecture of a neural network

1. Input layer
2. Output Layer
3. Hidden Layer.

- The recurrent neural networks are more similar to how our brain works than feed forward network.
- For a network prediction with 10 classes it is natural to select just 4 output neurons to encode the 0 classes as binary. However, empirical results show that the NN with 10 output classes tend to perform better.
