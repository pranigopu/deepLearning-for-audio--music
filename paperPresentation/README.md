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
- Visual analysis or auditory analysis?
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
- Training <br> **NOTE**: _Consider the data representation and CNN structure used for each branch_
    - Branches
        - Visual branch
        - Aural branch <br> **CONCEPTS TO LEARN**: _Averaging function_
        - Multimodal branch <br> **CONCEPTS TO LEARN**: _Cross-modality contamination_
    - Objective function
        - Difference from usual classification problems
        - Defining distance component of the objective function
## Key considerations for experimentation
- Questions for experiments
    - Is it possible to determine the pianist’s skill level using machine learning/computer vision?
    - What is the better sampling strategy: contiguous or uniform distribution?
    - Is a multimodal assessment better than a unimodal asssessment?
