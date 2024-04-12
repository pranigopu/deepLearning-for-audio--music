# Musical key & tempo recognition

**WARNING**: Parts of the code may reference local files and folders that have not been included in this folder to save space for the submission.

## Code files
- `Functions.ipynb` (contains necessary functions & imports for all)
- `MusicalKeyClassification.ipynb` (task 1)
- `MusicalTempoClassification.ipynb` (task 2)
- `CombiningInferences.ipynb` (task 3)
- `CaseStudy.ipynb` (case study)

For importing `.ipynb` files, I had installed the module `import_ipynb`. You can do so by running the following in your Jupyter Notebook:

```
!pip install import_ipynb
```

## Datasets
- Key dataset: https://github.com/GiantSteps/giantsteps-key-dataset (KEY)
- Tempo dataset: https://github.com/GiantSteps/giantsteps-tempo-dataset

The CSV file with annotations for the key dataset is already present in this directory as `musicalKeyClassification.csv`. Annotations for tempo recognition is also present in the folder `annotationsForMusicalTempoClassification`.

## Trained model weights

Load the following weights using the function `load_model(<model>, <file name>)` defined in `Functions.ipynb`. Remember that the model passed as the argument has to be of the same architecture as the one whose weights you are trying to load.

The file names (with self-explanatory names) are:

- `musicalKeyClassificationTrainedModelWeights.npy`
- `musicalTempoClassificationTrainedModelWeights.npy`

## Case study
- "Ambient Life" by Pranav Gopalkrishna
    - File type: MP3
    - Duration: 5 minutes 26 seconds
    - MuseScore link: https://musescore.com/user/31737238/scores/8251148?share=copy_link

## Regenerating spectrograms & melspectrograms
If the spectrograms and melspectrograms have not already been stored, you will have to generate them. You will be prompted to do so if you run the appropriate code. Be warned that upon generating the spectrograms and melspectrograms, the files to store their values will be generated, and these files (especially for spectrograms) can be quite large. If you do not want these files to be generated, alter the appropriate code in `Functions.ipynb`.

## Downloading the audio for training and testing
As mentioned in the report, the data for the 2 tasks was taken from the following:

**TASK 1**:

- Dataset name: GiantSteps Key Set
- GitHub URL: https://github.com/GiantSteps/giantsteps-key-dataset

**TASK 2**:

- Dataset name: GiantSteps Tempo Set
- GitHub URL: https://github.com/GiantSteps/giantsteps-tempo-dataset

---

I obtained the data for each task as follows:

- Cloned the respective dataset's GitHub repository on my own system
- Ran the Bash script `audio_dl.sh` present in the respective repository's directory
- Upon running the above, I obtained a folder "audio" in which were the relevant MP3 audio files

**NOTE**: When running `audio_dl.sh`, I faced a strange issue wherein though the right audio files were being downloaded, the Bash script did not recognise it for some reason and executed its failure-to-download condition, which involved removing the created MP3 file. To prevent this removal, I simply commented the line `rm "$audiofilename"` in the Bash script. I did not try to learn the cause of this issue, so I cannot say why this issue occurred.

## Special references & acknowledgements

Help in figuring out how to process audio data and train neural networks (including CNN and RNN):

"Deep Learning (for Audio) with Python" (YouTube playlist) by "Valerio Velardo - The Sound of AI": <br>
https://www.youtube.com/playlist?list=PL-wATfeyAMNrtbkCNsLcpoAyBBRJZVlnf
