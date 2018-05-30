# Speaker_Verification
implementation of generalized end-to-end loss for speaker verification

### Explanation
- This code is implementation of generalized end-to-end loss for speaker verification (https://arxiv.org/abs/1710.10467)
- This paper improved previous work (End-to-End Text-Dependent Speaker Verification, https://arxiv.org/abs/1509.08062)

### Speaker Verification
- Speaker verification task is 1-1 check for the specific enrolled voice and the new voice. This task needs higher accuracy than speaker identification which is N-1 check for N enrolled voices and a new voice. 
- There are two types of speaker verification. 1) Text dependent speaker verification (TD-SV). 2) Text independent speaker verification (TI-SV). The former uses text specific utterances for enrollment and verification, whereas the latter uses text independent utterances.
- Each forward step in this paper, similarity matrix of utterances are calculated and the integrated loss is used for objective function.
(Section 2.1)

### Data
- I cannot obtain proper speaker verifiaction dataset. (The authors of the paper used their own Google dataset.)
- For implementation, I used VTCK public dataset(CSTR VCTK Corpus 
, http://homepages.inf.ed.ac.uk/jyamagis/page3/page58/page58.html) and noise added VTCK dataset(Noisy speech database for training speech enhancement algorithms and TTS models, https://datashare.is.ed.ac.uk/handle/10283/1942)
- VCTK dataset includes speech data uttered by 109 native speakers of English with various accents. 
- For TD-SV, I used the first audio file of each speaker which says "Call Stella". Each training and test data, I added random noise which is extracted from noise added VTCK dataset. 
- For TD-SI, I used random selected utterances from each speaker. Blank of raw audio files are trimmed and then slicing is performed.  

### Files
configuration.py
- argument parsing
data_preprocess.py
- extract noise and perform STFT for raw audio. For each raw audio, voice activity detection is performed by using librosa library.
utils.py
- containing various functions for training and test.
model.py
- containing train and test function. Train fucntion draws graph, starts training and saves the model and history. Test function load variables and test performance with test dataset.
main.py
- When this file is implemented, training or test begins.


### Results
Loss


Equal Error Rate.











