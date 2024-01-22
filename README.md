# Deep learning (DL)
A record of my work in the deep learning course of my master's. Technically, deep learning is a part of ML, but ML basics were covered in a separate previous course.

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

## Conceptual map
- `NN`: Neural network
    - `NN.base.1`: Basic terminology
        - Observation & its representation as a vector
        - Target (generally real-valued and not a vector)
        - Neuron
        - Layer
    - `NN.base.2`: Key aspects of NN
        - Architecture (_how the NN uses its parameters to compute predictions_)
        - Training (_the process of finding parameters for the NN_)
        - Generalisation (_ability to make accurate predications about new observations_)
    - `NN.base.3`: Success criteria
        - Flexibility
        - Efficiency

**NOTES ON FLEXIBILITY & EFFICIENCY**:<br>Flexibility is essentially generalisability; generalisation can often be improved by task-specific architectures. Efficiency is with respect to computation, time and hardware usage.
