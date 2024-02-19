# Paper presentation
As a part of the deep learning for audio and music course, we students have to present a paper of our choice (either live or in video, with a live Q & A in either case). My chosen paper is "Piano Skills Assessment" by Paritosh Parmar, Jaiden Reddy and Brendan Morris. I chose this paper due to the following reasons:

- My experience in piano assessment (as a student)
- The relevance of such an application (ex. personal performance evaluation to help self-improvement)
- The interesting complexity of the problem of automating musical evaluation

CHOSEN PAPER LINK: https://arxiv.org/abs/2101.04884

---

# Notes on the chosen paper
## Driving questions
- Can a computer assess piano player's skill level?
- Visual analysis or auditory analysis? What about both?
- How to sample shorter clips to best reflect player performance
    - **CONTEXT**: Long videos are difficult for CNNs to process

## Key considerations for data & training
- Dataset <br> **NOTE**: _The dataset contains visual and auditory data_
    - Feature selection w.r.t. method of evaluation
    - Data collection method
    - Mitigation of small dataset size (as data collection method led to small dataset)
    - Sampling schemes (both were used and compared to each other)
        - Uniform
        - Contiguous
     
**NOTE**: Sampling schemes relate to how clips must be sampled from longer videos to best reflect the player's performance. Relevant quote from the paper: <br> _"Since current CNNs have difficulty processing long [video] videos, how can shorter clips be sampled to best reflect the players skill level?"_

- Training <br> **NOTE**: _Consider the data representation and CNN structure used for each branch_
    - Branches
        - Visual branch
        - Aural branch <br> **CONCEPTS TO LEARN**: _Averaging function_
        - Multimodal branch <br> **CONCEPTS TO LEARN**: _Cross-modality contamination_
    - Objective function
        - Difference from usual classification problems
        - Defining distance component of the objective function
     
### Dataset details
Relevant quote: <br> _"In this paper, automated determination of piano playing skill level based on a 10 point scale using a new multimodal PIano Skills Assessment (PISA) dataset (Fig. 1) that accounts for both visual and auditory evidence."_

2 key attributes in PISA dataset: (1) player skill and (2) music difficulty

---

**QUESTION 1**: How are the above attributes measured?

**ANSWER 1**: <br> (1) _"The primary evaluation of player skill is through the technique required for the most difficult song they are able to play. In this way, song level generally indicates player skill."_ The technique is graded based on skill-level as defined in the syllabus by Music Teachers National Association (MTNA). (2) _"The methodology for determining the song level (SL) of difficulty of a piano piece utilized multiple syllabi. A 10 point grading system was used for piece difficulty."_ As with player skill, music difficulty was graded based on the skill-level as defined in various syllabi; cross referrencing was done as needed.

---

**QUESTION 2**: How was the training and testing data acquired and annotated?

**ANSWER 2**: <br> (1) Acquiring the data: _"We had to rely on a trained pianist to collect videos from YouTube, analyze them, and determine each player’s skill level (as described above). As such, scaling up the dataset is difficult. We collected a total of 61 total piano performances."_ <br> (2) Annotating the data: _"For each piano performance, we provide the following annotations: 1) player skill level; 2) song difficulty level; 3) name of the song; 4) a bounding box around the pianist’s hands"_ <br> (3) Delineating the testing and training data: _"Out of the 61 total piano performances, we use 31 (516 samples) as our training set and 30 (476 samples) as our test set. Note that no overlap exists between train and test sets."_

---

**QUESTION 3** (follow-up of previous): How was the small dataset size mitagated?

**ANSWER 3**: <br> _"To mitigate small dataset size, we create multiple unique, non-overlapping samples, each of size of 160 frames. In this way, we have a total of 992 unique samples."_ Hence, they divide the videos into small, equally-sized clips; the model is to be trained not on whole videos but on clips. This would be necessary in any case (even for a larger dataset), since CNNs have difficulty processing long videos (however, for larger datasets, we may only take a few clips per video, rather than use the whole video).

<br>

**QUESTION 3.i**: How are the samples taken?

**ANSWER 3.i**: <br> Samples are taken in 2 different ways (leading to 2 different use-cases): (a) contiguous sampling scheme and (b) uniformly distributed sampling scheme. <br> A sampling scheme is a detailed description of what data will be obtained and how this will be done. Each performance - measured in frames - is divided into small, equally-sized segments (equally-sized means having the same number of frames). A sample is the set of segments considered as a whole (i.e. as a single input for the CNN). Sampling scheme, thus, defines the method by which the segments are picked for each sample. <br> (a) Contiguous sampling scheme is wherein each sample gets a set of contiguous segments. <br> (b) Uniformly distributed sampling scheme is wherein each sample gets uniformly-spaced segments from across the performance video.

> REFERENCE: (To understand what a sample scheme is) https://itl.nist.gov/div898/handbook/ppc/section3/ppc332.htm

**NOTE**: _The 2 different use-cases based on the 2 different sampling schemes are both explored and compared to each other in experimentation._

### Training details


#### Unimodal approach

## Key considerations for experimentation
**Questions for experiments**:

- Is it possible to determine the pianist’s skill level using machine learning/computer vision?
- What is the better sampling strategy: contiguous or uniform distribution?
- Is a multimodal assessment better than a unimodal asssessment?
    - Hence, the paper involves both unimodal and multimodal approaches
