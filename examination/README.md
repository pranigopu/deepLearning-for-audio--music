# ECS7013P: Deep Learning for Audio and Music (Final Exam)

- **Student name**: Pranav Narendra Gopalkrishna
- **Student number**: 231052045

## Question 1

### Part a

Tanh and ReLU can lead to vanishing gradient, however leaky ReLU does not.

### Part b

> REFERENCE USED: https://wandb.ai/ayush-thakur/dl-question-bank/reports/What-s-the-Optimal-Batch-Size-to-Train-a-Neural-Network---VmlldzoyMDkyNDU

#### (i)

The most likely parameter being modified is batch size, since the rate of descent in each graph is roughly equal and the only noticeable difference is the fluctuations or random oscillations in the loss curve.

#### (ii)

Figure C represents the smallest magnitude of the hyperparameter (i.e. the smallest batch size, leading to the most random fluctuations).

#### (iii)

The batch size for figure B should be smaller than for figure A, leading to more random oscillations or noise, which gives the model a higher chance of leaving a local minimum to reach a more optimised state (i.e. a lower local minimum), especially when the cost function is non-convex.

### Part c

> REFERENCES USED: https://www.cs.toronto.edu/~wenjie/papers/nips16/top.pdf

#### (i)

The entire input to the neural network, since each neuron's output of the previous layer maps to each neuron of the next layer.

#### (ii)

A 5 by 5 section of the spectrogram.

#### (iii)

A 1 by 7 section of the spectrogram (i.e. a set of frequencies from one time stamp).

#### (iv)

The entire spectrogram along with the layer outputs.

#### (v)

The part of the input to the autoencoder; the part cannot be determined easily since the latent space is opaque.

### Part d

ReLU ensures that if $z$ is greater than or equal to 0, it remains unchanged, whereas if it is negative, it is set as 0. Now, a sigmoid function is defined such that all values greater than zero result in a sigmoid value above 0.5 while 0 results in a sigmoid value of exactly 0.5. Hence, by applying ReLU then applying sigmoid, we are ensuring that the output of the sigmoid is greater than or equal to 0.5. Hence, if we classify the inputs such that the $\hat{y} \geq 0.5$ is classified as a bird sound, every value of $z$ will be classified as a bird sound.

A simple fix to this problem is to remove the "equal to" part, i.e. to classify $\hat{y} > 0.5$ as bird sounds rather than $\hat{y} \geq 0.5$. In such a case, if $z > 0$, we get a bird sound classification, and if $z \leq 0$ we get a non-bird sound classification.

---

## Question 2

### Part a

I would use softmax activation for each class output. It would predict the likelihood of the input's genre belonging to the corresponding class.

### Part b

> REFERENCE USED: https://gombru.github.io/2018/05/23/cross_entropy_loss/

Loss function I would use is categorical cross-entropy.

Let us define some notation:

- $CCE$ = Categorical cross-entropy loss
- $k$ = Higest index of the available categories (where indices start from 0)
- $t_i$ = The one-hot encoding of the $i$-th category
- $s$ = Vector of outputs from the final layer before softmax
- $f(s)_i$ = Softmax value for the $i$-th category

We define categorical cross-entropy loss as:

$\displaystyle CCE = \sum_{i=0}^{k} t_i \log(f(s)_i)$

### Part c

Scalar output for the whole batch would involve averaging the categorical cross-entropy loss for each output within the mini-batch. Hence, if the mini-batch size is $b$, we have the following formula (using the same notation as part b):

$\displaystyle CCE_\text{mini-batch} = \frac{1}{b} \sum_{h=0}^{b} \sum_{i=0}^{k} t_i \log(f(s_h)_i)$

Here:

- $CCE_\text{mini-batch}$ = Average categorical cross-entropy loss for the whole mini-batch
- $s_h$ is the vector of outputs from the final layer before softmax for the $h$-th item in the mini-batch


### Part d

#### (i)

Potential hyperparameters to tune:

- **Learning rate**: Suitability of the learning rate is often dependent on the overall nature of the training data. For example, data with higher magnitudes may require a lower learning rate due to the risk of gradient explosion.
- **Batch size**: A higher batch size results in more coarse steps that aggregate a set of data points. This may be more required in larger datasets, but for smaller training data, we can afford to use smaller batch sizes.

#### (ii)

The early layers of a genre classifier (usually convolutional and pooling layers) deal with or extract the more fine-grained features of the input. Such features (e.g. timbre, distortion, acoustic qualities, etc.) may be generalisable across any kind of audio input and may not need additional training once trained on a sufficiently large and representative dataset. In particular, the extracted features may be low-level enough to helpfully progress music classification, despite the fact that they were intended to extract music vs. non-music features.

#### (iii)

Freezing the early layers may be unhelpful in the following cases:

- The layers were previously trained only on a narrow objective (binary classification) and hence may not be tuned to handle a broader objective which may require different features or a wider range of features
- The layers were insufficiently trained and could use more fine-tuning for better performance

### Part e

The activation and loss function used were chosen based on the problem being a multi-class classification. For a multi-label classification (where one input can be assigned to multiple labels), the activation function (softmax) estimates the probability of a given label being present in the input as opposed to the other labels, i.e. in a mutually exclusive way. However, we want to estimate the probability of a given label being present at all, regardless of the other labels; in other words, we want to check for the presence of each label independent of the presence of other labels. Softmax clearly does not achieve this. Individual sigmoids for each label would be an appropriate solution.

As for the loss function, categorical cross-entropy loss gives the distance between the actual (ground truth) label of the input and the estimated labels; in other words, it considers only one target value and gives the distance of the overall predictions with respect to that one target value. However, in multi-label classification, there may be multiple target labels associated with one input, which categorical cross-entropy cannot account for. Individual binary cross-entropy losses for each label would be an appropriate solution.

---

## Question 3

### Part a

#### (i)

A learning rate that is too large can prevent the cost function from converging or at least converging more steadily due to each gradient descent always overshooting the optimum (due to the large learning rate); if the learning rate is too large, it can even make the gradients explode. Hence, looking at the cost curve, a non-converging, i.e. highly oscillating or diverging (upward-moving) cost curve is a sign that the learning rate is too high.

#### (ii)

A learning rate that is too small may converge very slowly or may get stuck in a local minimum and plateau (i.e. not change across iterations). Hence, looking at the cost curve, a plateauing cost curve (especially at a relatively high cost value) is a sign that the learning rate is too low.

### Part b

No answer.

### Part c

What is overfitting? How does splitting a dataset into train, validation, and test sets
help identify overfitting? What considerations need to be taken into account when
splitting the data? Explain your answer carefully
Overfitting is a situation that occurs as a result of training a model, wherein the model's weights become fine-tuned to specific variations in the training data that are not common in general (i.e. when considering all the potential data from the given domain). In such a case, the model may lose its generalisability, since it gives excess importance to specific factors that are uncommon and/or irrelevant in general.

Splitting the data into validation and test sets gives as a control, i.e. data that is not considered by the model during training, which means the model cannot fine-tune with respect to them. Hence, if we see that a model is far more accurate for the training data than for the validation and test sets, we may infer (given certain considerations) that the model has overfitted, especially if the performance is poor for the validation and test sets.

Since the validation and test sets must serve as a control, it must be as representative of the data from the domain in question as possible. Hence, we have the following considerations:

- The validation and test sets must be sufficiently large (to include a sufficiently diverse range of data points)
- The data must be randomly shuffled before splitting to prevent selectivity during training.

### Part d

The purpose of a deep neural network is to estimate arbitrarily complex, non-convex, non-linear functions. A purely linear layer within a neural network does not add any complexity - mathematically - to the model, since the linear layer essentially produces a linear combination of the inputs that could have as well been achieved (with lesser computational complexity) by altering the weights of the non-linear layers.

### Part e

#### (i)

1. **Noise augmentation**: Creating new data by adding standard normal noise to each "Madonna present" input.
2. **Pitch-shifting**: Creating new data by shifting the pitch of the "Madonna present" inputs.
3. **Time-stretching**: Creating new data by stretching (i.e. lengthening) the time of the "Madonna present" inputs.

#### (ii)

Without $\alpha$ and $\beta$, the logistic loss function does not account for the possibility of the model overestimating "Madonna absent" labels due to the greater size and variation in the "Madonna absent" data. Using $\alpha$ and $\beta$, we can weight each element (the "Madonna present" element, i.e. $y\log(\hat{y})$, and "Madonna absent" elements, i.e. $(1-y)\log(1-\hat{y})$ of the loss function) to account for this potential overestimation.

Given that there are 10 times as many "Madonna absent" signals, reasonable values for $\alpha$ and $\beta$ may be 10 and 1; the most suitable values would depend on how well the model is able to generalise "Madonna present" signals, but in general, $\alpha > \beta$.

---

## Question 4

### Part a

| Layer | Spatial output dimensions|
| --- | --- |
| Input layer | $(M, M)$ |
| Convolutional layer | $(M + 4 - 5 + 1, M + 4 - 5 + 1) = (M, M)$|
| Max pooling layer | $(\frac{M - 1}{2},\frac{M - 1}{2})$ |
| Parallel convolutional layers | $(\frac{M - 1}{2} - 2, \frac{M - 1}{2} - 2)$ |

**NOTE**: Consider division as integer division (i.e. rounding to the lowest integer).

### Part b

**Input layer**:

0 parameters.

**Convolutional layer**:

Doubling the channels, we get $1 \times 2 = 2$ channels.

$2$ channels/filters of $5 \times 5$ kernels $\implies 2 \times 5 \times 5 = 50$ parameters.

Adding bias, we get $51$ parameters.

**Max pooling layer**:

0 parameters.

**Parallel convolutional layers**:

Doubling the channels, we get $2 \times 2 = 4$ channels (parallel convolutional layers means neither comes first).

$2$ layers with $4$ channels/filters of $5 \times 5$ kernels $\implies 2 \times 4 \times 5 \times 5 = 200$ parameters.

Adding 2 biases (1 for each layer), we get $202$ parameters.

There are 2 dimensions, so the multivariate Gaussian has 2 means and 2 standard deviations, leading to $202 + 2 + 2 = 206$ parameters.

### Part c

| Layer | Spatial output dimensions|
| --- | --- |
| Input layer | $(1, 28, 28)$ |
| Convolutional layer | $(2, 28 + 4 - 5 + 1, 28 + 4 - 5 + 1) = (2, 28, 28)$|
| Max pooling layer | $(2, \frac{28 - 1}{2},\frac{28 - 1}{2}) = (2, 13, 13)$ |
| Parallel convolutional layers | $(4, 11, 11)$ |

**NOTE**: Consider division as integer division (i.e. rounding to the lowest integer).

Hence, the shape of the latent space is $4 \times 11 \times 11$.

- The 1st dimension represents the number of channels (i.e. the number of filters/features extracted)
- The 2nd dimension corresponds to the width of the input
- The 2nd dimension corresponds to the height of the input

"Corresponds" in this context means the respective dimension was reduced in size to some representation within the latent space.

### Part d

The points on the latent space represent abstractions of the given images. We observe disconnected elements (e.g. lines, squiggles, etc.) that are reassembled in some way to get the final output. Such a representation is caused by feature extraction through the convolutional layers, which filter/extract some abstract attributes or aspects of the input (e.g. horizontal line segments, curved segments, etc.). Max pooling reduces the dimensionality and removes noise in the results of the convolution by keeping only the most significant values of each filtering, which is why we get relatively distinct, relatively well-defined abstracted elements when decoding points on the latent space.

There are a few possible improvements, depending on the cause of the reduction of quality in the reconstructed input:

1. Smaller max pooling kernel size
2. Reducing convolutional layers

Reducing the max pooling kernel size ensures that significant but relatively less significant values in a small area are still retained. In other words, it ensures that the filtered values are processed at a higher resolution.

Reducing convolutional layers reduces the maximum level of abstraction at which features are extracted. Each feature extraction (especially when combined with max pooling) introduces a level of abstraction that causes some amount of information loss. Fewer layers could ensure that enough information is retained for a higher quality reconstruction. However, reducing layers beyond a certain point can defeat the point of an autoencoder (i.e. finding a more efficient representation for the given image).
