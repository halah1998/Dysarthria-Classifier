<p align="center">
  <img width="550" src="https://user-images.githubusercontent.com/49031258/122465135-b89f9c00-cf85-11eb-9e3b-b123e2dcae44.jpg">
</p>

Dysarthria is a motor speech disorder that arises from weakness or paralysis of muscles in the face, lips, tongue, and throat. It is caused by neurological damage and is often one of the first symptoms of numerous common neurological disorders. For instance, Dysarthria affects 70-100% of people with Parkinson’s disease, 30% of people with ALS (Lou Gehrig's disease), and 20% of people with Cerebral Palsy. 

Diagnosis of these disorders require MRI and CT scans, blood and urine tests, and EEG or electromyography tests. These tests are very expensive and may be inaccessible for some patients. For our final project at the AI4Good Lab, we decided to build a machine learning tool that is capable of detecting a patient's underlying cause of Dysarthria by classifying audio input as being indicative of Parkinson's disease, ALS, or Cerebral Palsy. The best part is that this tool is free and accessible for all!

Refer to `notebook.ipynb` for an in-depth review of the data collection, data visualization, and machine learning model.

# Command Line Usage
To classify your own audio files from the command line, please follow these instructions.  
1. Record yourself sustaining the /a/ vowel sound for 5 seconds. 
2. Convert the audio file to .wav format.
3. Download this repository and navigate into it from the command line using ```cd```.
4. On the command line, type the command ``` python3 main.py -i <path_to_audio_file> ```
5. For a reminder of the usage, you can type ``` python3 main.py -h ```

# File explorer
` ` ` feature_extraction.ipynb ` ` ` 

Contains the code for extracting sound features relevant to dysarthria diagnosis from audio files.

 ` ` ` smote.py ` ` `

Contains two functions, `smote_binary` and `smote_multiclass`, that oversample or undersample a dataframe using the SMOTE technique and one-hot encode it.

` ` ` performance_report.py ` ` `

Contains an eponymous function that generates a CSV file with various performance metrics and graphs for easy comparison of models.

` ` ` logistic_regression.py ` ` `

Contains a function that fits a logistic regression model for each of the specified n classes (default is 1) and returns the necessary parameters for `performance_report`.


# Database
**Parkinson's Disease:**
A variety of datasets were used in this project. We collected three datasets (totaling 6439 PD patients and 192 healthy controls) for PD including, UCI Machine Learning Repository's [Parkinson's Disease Classification Data Set](https://archive.ics.uci.edu/ml/datasets/Parkinson%27s+Disease+Classification)(188 patients with PD (107 men and 81 women) with ages ranging from 33 to 87), UCI's [Parkinson Speech Dataset with Multiple Types of Sound Recordings](https://archive.ics.uci.edu/ml/datasets/Parkinson+Speech+Dataset+with++Multiple+Types+of+Sound+Recordings#) dataset(20 Parkinson's Disease (PD) patients and 20 healthy subjects), UCI's [Parkinsons Data Set ](https://archive.ics.uci.edu/ml/datasets/parkinsons)(8 control, 23 with PD). All Parkinson's datasets had aucustic features extracted and documented in csv files. 

**Amyotrophic Lateral Sclerosis:**
For the second cause of Dysarthria we focused on ALS and used publicly accessible voice data that was collected in Republican Research and Clinical Center of Neurology and Neurosurgery (Minsk, Belarus). This data included a total of  54 speaker rocordings, with 39 healthy controls (23 males, 16 females) and 15 ALS patients. The ALS patients showed signs of bulbar dysfunction (6 males, 9 females). Ages for the healthy group averaged at 41.9 years and with the ALS patients at 57.7. Participants were asked to pronounce sustained vowel /a/ at a comfortable pitch and loudness in one constant breath. Voice signals were recorded using a smartphone. Average duration of the samples is 4.1 s. Linear regression was applied to the data to account for the age difference in the the mean ages of the participants from the control and those with ALS. The dataset can be found in another implementation [ALS Dataset](https://github.com/Mak-Sim/Troparion/tree/master/SPA2019).

We used our feature extraction function to collect the acoustical features listed below. 

**Cerebral Palsy:**
For the third cause we focused on CP and used the **Universal Access Speech Technology Corpus (UASpeech)**. A restricted dataset that is easily accessible through request. We cannot redistribute it due to a confidentiality agreement. However, it can be requested from their [website](http://isle.illinois.edu/sst/data/UASpeech/index.html). The dataset includes audiovisual isolated-word recordings of talkers with spastic dysarthria, predominanty caused by cerebral palsy. The particpants were promted to read isolated words as well as letters. We extracted the letter \a\. Therefore, it is important to note that there is slight inconsistencies in the lengths of the pronounciation of the phonotation \a\ across the diseases. The participant age ranged from 18 to 58 years of age, averaging at 38. There were 13 male participants and 4 female particpant. 

We used our feature extraction function to collect the acoustical features listed below. 

**Datasets were augmented using our smote function to train the model on a fair distribution of healthy controls, PD patients, ALS patients, and CP patients. We trained the model on an augmented 200 set, 400 set, and 6000 set. All produced high recall, acuracies, and low false negative. 
**

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
Special thanks to our TA, Nadia Blostein, for her invaluable guidance and clever insights throughout the program !  
Thank you to our team mentors Ainaz, Disha and Isabelle for sharing their expertise and weekly consulting meetings !  
Thank you to the AI4Good Lab team for creating this opportunity in the first place !

# References
[SMOTE technique](https://machinelearningmastery.com/smote-oversampling-for-imbalanced-classification/)

[Parkinson's Disease Detection Article](https://www.researchgate.net/publication/347520593_Parkinson%27s_Disease_Detection_from_Voice_and_Speech_Data_Using_Machine_Learning)

[ALS Bulbar Detection Article](https://www.bsuir.by/m/12_100229_1_139167.pdf)
