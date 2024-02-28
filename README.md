# Deep learning for music & audio
A record of my work in the deep learning (DL) for audio and music course of my master's. Technically, deep learning is a part of ML, but ML basics were covered in a separate previous course.

## Use of DL in audio & music
- Uncover features in audio representations (ex. image recognition on spectograms of audio files)
- Classify audio or parts of audio
- Musical analysis

---
To explore further, check the following:

- [DL focused part](https://github.com/pranigopu/deepLearning--for--audio-music/blob/17d6660862f79616c63c2bab18adaf260f166f57/deepLearning.md)
- [Audio & music focused part](https://github.com/pranigopu/deepLearning--for--audio-music/blob/8ab6c0c51e767763230fa5ebdd09658122a2302a/audioAndMusic.md)

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
