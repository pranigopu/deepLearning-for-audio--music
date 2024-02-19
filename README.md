# Deep learning for music & audio
A record of my work in the deep learning (DL) for audio and music course of my master's. Technically, deep learning is a part of ML, but ML basics were covered in a separate previous course.

## ML to DL
### Broad areas of ML
- Supervised learning (covered in ML course)
- Unsupervised learning (covered in ML course)
- Reinforcement learning (basics covered in "AI in Games" course)

Some extra notes in RL...

- RL studies sequential decision-making under uncertainty
- In RL, agent tries to learn the sequence that maximises cumulative reward
- In RL, the goal is implicit in the reward structure

### Neural network (NN) & the focus of DL
- NN is at its core a function that maps inputs to outputs based on parameters
- NN (beyond a single-layer) is a composition of functions
- DL studies certain types of NN's; NN's wherein the composition of functions is "deep enough"

Hence, we begin by discussing NN's.

## Programming support topics

- `pytorch`: PyTorch library for handling vectors & matrices as tensors
    - `pytorch.tensor`: Tensor
        - Tensor ranks
            - Rank 0: Floating point number
            - Rank 1: Array or vector
            - Rank 2: Matrix or vector of vectors
            - Rank 3: Matrix of matrices
        - Matrix multiplication with tensors (_how is it done?_)
        - Broadcasting
        - Memory management
            - Assignment only assigns new names & does not create copies
                - Hence, using assignment, different identifiers can be made to refer to the same memory
                - Assignment does not by itself duplicate data
            - In-place assignments can be done in the following ways (given tensors `X` and `Y`):
                - `Y += X`
                - `Y[:] = Y + X`
                - **NOTE**: `Y = Y + X` is not in-place & creates a new memory location for `Y`
        - Converting tensors to other Python datatypes (ex. NumPy array, float, etc.)
- Generator functions in Python
    - Keyword `yield` used to mark the point from where the function must continue in the next call
    - Local variables for the next call and execution resumes from `yield`

## Conceptual map
- `NN`: Neural network
    - `NN.base.1`: Basic terminology
        - Observation & its representation as a vector
        - Target (generally real-valued & not a vector)
        - Neuron
        - Layer
    - `NN.base.2`: Key aspects of NN
        - Architecture (_how the NN uses its parameters to compute predictions_)
        - Training (_the process of finding parameters for the NN_)
        - Generalisation (_ability to make accurate predications about new observations_)
    - `NN.base.3`: Success criteria
        - Flexibility
        - Efficiency
    - `NN.MoL`: The mathematics of learning
        - `NN.MoL.Norm`: Norm (L1, L2, etc.)
            - Definition & basic properties
            - L2 norm a.k.a. Euclidean distance
            - Relation between norm & distance (especially with respect to vectors)<br> _Distance here refers to the formal mathematical definition of distance_ <br> **CONSIDER**: Given vectors $X$ and $Y$, norm of $X-Y$ is some type of distance between $X$ & $Y$
            - Use of norms for comparing vectors of all observed & predicted targets<br> _... relates to cost function_
        - `NN.MoL.CF`: Cost function
            - Cost function as a measure of distance between observed and predicted targets
            - Cost function as a function in terms of NN parameters<br> _... relates to gradient descent_
        - `NN.MoL.GD`: Gradient descent (with respect to cost function)<br> _... extends from cost function, i.e._ `NN.MoL.CF`

**NOTES ON FLEXIBILITY & EFFICIENCY**:<br>Flexibility is essentially generalisability; generalisation can often be improved by task-specific architectures. Efficiency is with respect to computation, time and hardware usage.
