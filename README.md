# guitar-chord-recognition
Project primarily focuses on following tasks : 
* Feature extraction of chroma features from an audio data set corresponding to chords of an acoustic guitar
* Implementation and comparison of different machine learning models on the extracted chroma features 
* Live chord recognition on an acoustic guitar 

## Project Scope

### Chords
Training data is composed of 200 audio clips corresponding to following ten chords recorded on an acoustic guitar:
* a
* am
* bm
* c
* d
* dm
* e
* em
* f
* g

*The data is made publicly available by INTELSIG Laboratory, University of Liège, Departement EECS. Further details can be found under references,*

### Chroma Features
The projects considers 3 types of chroma features namely:
* STFT : Short-time Fourier transform
* CQT :Constant-Q transform
* CENS : Chroma Energy Normalized

*Library used for extracting the above features :* [LibROSA](https://librosa.github.io/librosa/)

### Implemented Classification Models
Following classification models were used in this project:
* Logistic Regression
* K-nearest neighbor
* SVM
* kernel SVM
* Naive Bayes
* Decision Tree
* Random Forest

## Getting Started

### Conda setup
```shell
# create conda environment
$ conda env create -f requirement.yml

# activate conda environment
$ conda activate guitar_chord_recognition
```
### Project setup
* Unzip all contents from jim2012Chords.zip\Guitar_Only to data/ChordAudioDataset. (See **References** section at end of this document for data download link)
* Create Chroma features for the given audio data set
```shell
# create all 3 type of chroma feature
python extract_features.py

# pass chroma feature type as argument to create specific feature data
python extract_features.py {chroma_type}
```

* Train and save classification Models
```shell
# Classification model as argument (Default chroma_type = "cqt")
python train_and_save_model.py {classification_model}

# Classification model and chroma feature type as arguments
python train_and_save_model.py {classification_model} {chroma_type}
```

### Check model performance 
```shell
# Classification model as argument (Default chroma_type = "cqt")
python check_model_performance.py {classification_model}

# Classification model and chroma feature type as arguments
python check_model_performance.py {classification_model} {chroma_type}
```

### Live guitar chord recognition
```shell
# Record and predict guitar chord (Default chroma_type="cqt"& model="kernel_svm")
python predict_chord.py

# Predict using specified classification model or chroma feature type
python predict_chord.py {classification_model}
python predict_chord.py {chroma_type}

# Predict using both classification model and chroma feature type
python predict_chord.py {classification_model} {chroma_type}
```

Note: *Please refer the argument section for possible values of {classification_model} and {chroma_type}*

### Program parameters:
*Classification model arguments*:

Classification Model  | Argument
--------------------- | ---------------------
Logistic Regression   | logistic
K-nearest neighbor    | knn
SVM                   | svm
kernel SVM            | kernel_svm
Naive Bayes           | naive_bayes
Decision Tree         | decision_tree
Random Forest         | random_forest

*Chroma feature arguments*:

Chroma Feature               | Argument
---------------------        | ---------------------
Short-time Fourier transform | stft
Constant-Q transform         | cqt
Chroma Energy Normalized     | cens

## Sample Execution
```shell
# detect guitar chord
(guitar_chord_recognition) $>python predict_chord.py
recording starts in 3 seconds...
recording starts in 2 seconds...
recording starts in 1 seconds...
Start playing the chord. recording now...
Recording completed. Recording save path : data/recording\test_audio_c170b4c1-0a2f-4d06-9e79-0efc589ad617.wav
recorded audio : data/recording\test_audio_c170b4c1-0a2f-4d06-9e79-0efc589ad617.wav
CHORD PLAYED : f
```

## Conclusion
Please refer to: 
* [model-comparison-results](result/model-comparision-results.md)
* [test-summary](result/test-summary.md)

## References
* [NEURAL NETWORKS FOR MUSICAL CHORDS RECOGNITION](references/jim2012_08_p_osmalskyj.pdf)
* Guitar Chord Audio data set: http://www.montefiore.ulg.ac.be/services/acous/STSI/file/jim2012Chords.zip
* Urban Sound Classification
  * http://aqibsaeed.github.io/2016-09-03-urban-sound-classification-part-1/
  * http://aqibsaeed.github.io/2016-09-24-urban-sound-classification-part-2/
* LibROSA
  * https://librosa.github.io/









    
