# Deep learning for music & audio
A record of my work in the deep learning (DL) for audio and music course of my master's. Technically, deep learning is a part of ML, but ML basics were covered in a separate previous course.

## Use of DL in audio & music
- Uncover features in audio representations (ex. image recognition on spectograms of audio files)
- Classify audio or parts of audio
- Musical analysis

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
