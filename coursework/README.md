# Module coursework for deep learning for audio and music

## Instructions
1. Apply two different deep learning methods to the audio, to infer two different aspects (e.g. to infer the pitch and the instrument in music, or the species and the start/end times in animal sound, or a source-separation mask and a gender in speech).
    - It is acceptable to use some existing code and/or pretrained models from other sources, but you must implement and train at least one of the methods yourself, and the majority of the overall implementation should be your own work. Describe all this in your written report.
    - You can use any publicly available (or available on the school/c4dm servers) training/validation/testing data that you wish, not just the audio file; these datasets must be clearly stated in the report.
    - To encourage reproducibility your code we require you in also submit a Jupyter notebook, that includes the output of each cell (code) that you have used to produce your report.
2. Explore empirically how to combine the two different inferences. This could be through explicitly creating a single deep learning model that aims to infer both aspects, but it could be through other approaches such as pre-training, language modelling, or postprocessing outputs. In your report, describe the approach(es) you explore and discuss the outcomes, comparing them against the other outcomes you have obtained.
3. Pick an audio file that will be the case study for your coursework. You might pick a music recording, an urban or wildlife soundscape, a radio clip containing music and speech, or something else.
    - Inspect the performance of the models in (1) and (2) when applied to your selected audio file, perhaps under different variants of your models. Critically discuss (in your written report) the models and what they infer.
    - You are going to apply at least two different deep learning methods to it, and discuss their performance - so, the audio file needs to have enough content & complexity to it that you can clearly see what an algorithm gets right/wrong. It is also helpful if the audio is Creative Commons licensed because that means you can republish it (e.g. blog about it), but that's not essential.
    - One source of copyleft music is: https://www.jamendo.com/

Submission format: 1500-word report PDF. Please also submit a copy of the audio file used as the case study, as well as your code which includes a Jupyter notebook with cell outputs. Please put this all into one ZIP file, named as follows:

`coursework_{yourname}.zip`

You will be assessed on: the suitability of the deep learning applied, the discussion/reflection of the detailed results from the case study audio, and generally on the quality of the written report.

_Please feel free to blog publicly about your work in progress, if you like, or to share code publicly (e.g. on Github)._
