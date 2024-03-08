# Topics for audio & music

- Audio representation
    - Raw waveform
    - Frequency axis graph representations <br> _Representations as graphs wherein one axis is frequency_
        - Spectogram
            - Decomposition of frequencies using **Fourier transform** (FT)
            - Types
                - Complex spectogram
                - Magnitude spectogram
            - Mel scale & melspectogram
                - Uses log scale for pitch measurement
        - Constant Q-transform
        - Chromograph
            - Merges information across octaves

**NOTE: More on audio representation strategies**:

- Extreme minimal computation $\implies$ Raw waveform
- Extreme maximal computation $\implies$ Pre-trained embeddings
- Visual representation $\implies$ Spectograms
- Data normalisation

- Audio file representation
    - Sequence of frames <br> _Raw audio divided into frames_ <br> **NOTE**: Hop = Step, Size = Length = Width (i.e. they are interchangeable here)
        - Window vs. frame
        - Sample rate (i.e. number of samples per second)
            - Measured in Hertz
            - Sample rate = $n \implies$ 1 sample every $\frac{1}{n}$-th of a second
        - Window length (also "frame length")
            - Measured in samples or time (ex. seconds)
        - Hop length
            - Measured in samples or time (ex. seconds)
        - Window type
    - Sequence of frames as a spectogram <br> _... extends from "Sequence of frames"_
        - Frame representation in spectogram
            - 1 frame = 1 column in spectogram
            - Use of windows for spectogram
                - Significance of window type
                - Significance of window  length
        - Spectogram bin
        - Spectral resolution (i.e. bandwidth of spectogram bin)

**KEY TOPICS THAT EXTEND FROM THE ABOVE**:

- Fast Fourier transform (FFT)
- Spectral leakage
- Why use melspectogram?
    - Adjusts for human perception w.r.t. amplitude & pitch
    - Reduces dimensions while retaining most relevant info w.r.t. human perception
    - Allows vertical transpositions (linear scale does not)
- Tradeoff between frequency resolution (FR) vs. time resolution (TR)
    - More frames $\implies$ Less FR (_shorter time frames make it harder to discern frequencies_)
    - More FR $\implies$ Fewer frames

**NOTE**: Processing audio for deep learning often requires converting audio to images (especially when using CNNs).

## Formulas
- Sample rate = $\frac{1}{\text{Time interval after which a new sample is taken}}$
    - Measured in samples per second or Hertz
- Frame length = Samples per frame OR Time length of a frame
- Hop length <br> = Samples per hop OR Time length of a hop <br> = $\frac{1}{\text{Overlap between windows perr hop}}$
    - Determines frame rate <br> _i.e. hop length decides how many frames measured per second; this is independent of frame length_
- Frame rate <br> = Frames per second <br> = $\frac{\text{Sample rate}}{\text{Hop length}}$
- Spectral resolution <br> = Bandwidth of a spectogram bin <br> = Range of frequencies considered as one class
- Audio file length = Total frames $\times$ Hop length

Synonyms:

- Hop size = Hop length = Step size = Step length
- Frame size = Frame length = Window size = Window length
