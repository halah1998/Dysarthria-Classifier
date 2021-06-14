# Goal 
Build a tool to diagnose motor speech disorders caused by conditions such as Parkinson’s and ALS from user audio input.

# How to use

# Code breakdown
`smote_binary(df)` returns an augmented dataframe using the SMOTE technique, as well as its row count.

`smote_multiclass_encoded(df)` returns an augmented dataframe using SMOTE, its row count, and one-hot encodes the classes.

`performance_report(model, X, y, X_test, y_test, y_pred, model_label)` creates a CSV file with various performance metrics and graphs for easy comparison.

`logreg_pred(url)` fits a logistic regression model and returns the necessary parameters for `performance_report`.

`feature_extraction.ipynb` contains the code for extracting sound features relevant to dysarthria diagnosis from audio files.

# Database
**Parkinson's Disease:**
A variety of datasets were used in this project. We collected three datasets for PD including, ... . All Parkinson's datasets had aucustic features extracted and documented in csv files. 

**Amyotrophic Lateral Sclerosis:**
For the second cause of Dysarthria we focused on ALS and used publicly accessible voice data that was collected in Republican Research and Clinical Center of Neurology and Neurosurgery (Minsk, Belarus). This data included a total of  54 speaker rocordings, with 39 healthy controls (23 males, 16 females) and 15 ALS patients. The ALS patients showed signs of bulbar dysfunction (6 males, 9 females). Ages for the healthy group averaged at 41.9 years and with the ALS patients at 57.7. Participants were asked to pronounce sustained vowel /a/ at a comfortable pitch and loudness in one constant breath. Voice signals were recorded using a smartphone. Average duration of the samples is 4.1 s. Linear regression was applied to the data to account for the age difference in the the mean ages of the participants from the control and those with ALS. The dataset can be found in another implementation [ALS Dataset](https://github.com/Mak-Sim/Troparion/tree/master/SPA2019).

We used our feature extraction function to collect the acoustical features listed below. 

**Cerebral Palsy:**
For the third cause we focused on CP and used the **Universal Access Speech Technology Corpus (UASpeech)**. A restricted dataset that is easily accessible through request. We cannot redistribute it due to a confidentiality agreement. However, it can be requested from their [website](http://isle.illinois.edu/sst/data/UASpeech/index.html). The dataset includes audiovisual isolated-word recordings of talkers with spastic dysarthria, predominanty caused by cerebral palsy. The particpants were promted to read isolated words as well as letters. We extracted the letter \a\. Therefore, it is important to note that there is slight inconsistencies in the lengths of the pronounciation of the phonotation \a\ across the diseases. The participant age ranged from 18 to 58 years of age, averaging at 38. There were 13 male participants and 4 female particpant. 

We used our feature extraction function to collect the acoustical features listed below. 

# Acoustical Features
The folowing acoustical features were extracted:

Jitter::local
Jitter::ABS local
Jitter::RAP
Jitter::PPQ5
Jitter::DDP
Shimmer::local
Shimmer::APQ3
Shimmer::APQ5
Shimmer::APQ11
Shimmer:dB
HNR
DFA
Median Fundamental Frequency

# Team
Chloe Pappas, <chloeoliviapappas@gmail.com>  
Hala Hassan, <halahassan13@gmail.com>  
Nadia Enhaili, <nadia.enhaili@gmail.com>  
Ritu Ataliya, <atal2950@mylaurier.ca>  
Jiayue Yang, <jiayue.yang@mail.mcgill.ca>  
Kamun Karl Itaj, <kamun.karl-itaj@hotmail.ca>  

# Acknowledgements


 
# References
[SMOTE technique](https://machinelearningmastery.com/smote-oversampling-for-imbalanced-classification/)

[Parkinson's Disease Detection Article](https://www.researchgate.net/publication/347520593_Parkinson%27s_Disease_Detection_from_Voice_and_Speech_Data_Using_Machine_Learning)

[ALS Bulbar Detection Article](https://www.bsuir.by/m/12_100229_1_139167.pdf)
