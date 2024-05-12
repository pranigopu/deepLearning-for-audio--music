# Deep learning topics w.r.t. audio & music

- ML = Machine learning
- DL = Deep learning

## Section list
- Relevance of DL (or ML in general) in audio & music
    - Recognition tasks
    - Generative tasks
- ML to DL
- Conceptual map

## Relevance of DL (or ML in general) in audio & music
### Recognition tasks
- Classification (binary, multiclass, multilabel)
- Detection
- Transcription

**Core problems in machine listening (recognition tasks)**:

- Sound event detection
- Sound scene recognition
- Source separation
- Noise level estimation
- Noise reduction

### Generative tasks (extra topic)
**NOTE**: Generative tasks can be handled in ways other than ML or DL, but here, we shall look at it w.r.t. how it is handled using DL.

**Why DL for generative music?**

- Better generalisation
- Feasible in more complex generative goals
- More flexible & adaptable

**5 dimensions of generative problem**:

1. Objective
    - Type (generative vs. conditional)
    - Destination (_how is music presented or made available?_)
    - Interaction mode & style
        - Human as audience
        - System as performer
        - System as instrument
    - Style & constraints
    - Quality & innovation
2. Representation (_not the same as musical features_)
    - Audio
        - MIDI formal
        - Piano roll representation
    - Symbolic
        - ABC notation
        - Sheet music
    - _Issues in representation_
        - Feature extraction
        - Expressiveness
3. Architecture
    - Feed forward neural network
    - Autoencoder
    - Recurrent neural network (RNN)
        - LSTM
    - Compound architecture
        - Adversarial neural network
        - Neurosymbolic
4. Challenges
    - Overfitting avoidance
        - Dropout
        - Data augmentation
        - Weight decay
        - Early stopping
    - _How to achieve output variablility/diversity?_
5. Strategy
    - _How to control the model after training?_
    - _How to control the generative process?_

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

---
Now, we shall look at convolutional neural networks (CNNs), which are used for their ability to extract broader features from data, thereby (1) facilitating the recognition of essentials (hence causal factors or foundational features) in the data and (2) improving generalisability of the model (ex. in classification problems) and efficiency.

**SOME ABBREVIATIONS FOR CNNs**:

- CL = Convolutional layer
- PL = Pooling layer

---

- Convolutional neural network (CNN)
    - Uses in audio
        - Classify spectogram
        - Classify each column of a spectogram
        - Classify each pixel of a spectogram
    - Invariance vs. equivariance <br> _Key concept to understand CNN's mathematical properties_
        - CLs always provide equivariance
        - PLs always provide invariance
        - CLs provide invariance in certain cases?
    - Receptive field (of a neuron w.r.t. a layer)

**REFERENCES**:

- Receptive field: https://www.baeldung.com/cs/cnn-receptive-field-size

---

- DL for source separation & enhancement
    - Applications
        - Speech enhancement
        - Karaoke
        - Music mixing, demixing & remixing
    - Autoencoders
        - Spectograms
        - Reconstruction
        - Masking
    - U-Net
    - Deep clustering
    - Raw waveform methods

## Formulas
### Receptive field
Given that the receptive field of a neuron present in some layer $L$ is $r_n$ for layer $n$, what is the receptive field of the neuron for layer $n-1$? _Note that_ $r_0$ _is the input layer; hence, the lower the layer, the further it is from the final feature layer_. The formula for this is:

$r_{n-1} = s_n r_n + (k_n - s_n)$

Here:

- $r_n$ = Receptive field of the neuron for layer $n$
- $r_{n-1}$ = Receptive field of the neuron for layer $n-1$
- $s_n$ = Stride used in layer $n$
- $k_n$ = Kernel size used in layer $n$ (assuming square kernel)
    - $k_n$ is the length of one side of the square

Now, we know that $r_L = 1$ (since $L$ is the layer where the neuron is). Hence, we can recursively apply the formula given to obtain the receptive field of the neuron for any layer $n$ (including $n = 0$), given that we know $s_L$ and $k_L$.
