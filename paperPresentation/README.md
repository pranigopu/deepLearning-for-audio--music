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

**QUESTION**: How are the above attributes measured?

**ANSWER**: <br> _"The primary evaluation of player skill is through the technique required for the most difficult song they are able to play. In this way, song level generally indicates player skill."_ The technique is graded based on skill-level as defined in the syllabus by Music Teachers National Association (MTNA). <br><br> _"The methodology for determining the song level (SL) of difficulty of a piano piece utilized multiple syllabi. A 10 point grading system was used for piece difficulty."_ As with player skill, music difficulty was graded based on the skill-level as defined in various syllabi; cross referrencing was done as needed.

---

**QUESTION**: How was the training (annotated) data acquired?

**ANSWER**: <br> _"We had to rely on a trained pianist to collect videos from YouTube, analyze them, and determine each player’s skill level (as described above). As such, scaling up the dataset is difficult. We collected a total of 61 total piano performances."_

---

**QUESTION** (follow-up of previous): How was the small dataset size mitagated?

**ANSWER**: <br>

## Key considerations for experimentation
- Questions for experiments
    - Is it possible to determine the pianist’s skill level using machine learning/computer vision?
    - What is the better sampling strategy: contiguous or uniform distribution?
    - Is a multimodal assessment better than a unimodal asssessment?
