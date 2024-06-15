# Suicidal Text Detection

Suicidal text detection is a critical task that aims to identify and classify text content that indicates suicidal ideation or poses a risk of self-harm.
In this project we have used jupyter notebook and used a language which is python .
Libraries used:- Numpy, Pandas, Seaborn, nltk , Streamlit etc.
we have used some algorithm to check precision score and create a webpage using Streamlit Library.

## Project Directory Structure
```
├── data_preprocessing.ipynb
├── data_cleaning.ipynb
├── eda.ipynb
├── word2vec.ipynb
├── models_logit.ipynb
├── models_cnn.ipynb
├── models_lstm.ipynb
├── models_bert.ipynb
├── models_electra.ipynb
├── infer.ipynb
├── chatbot.ipynb
├── Data
│   ├── suicide_detection.csv
│   ├── suicide_detection_full_clean.csv
│   ├── suicide_detection_final_clean.csv
│   └── ...
├── Models
│   └── ...
└── …
```
This project is built on Python 3 and scripts were originally hosted on Google Colab. Required packages are installed individually in each `.ipynb` file.

## 1. Data Collection
The [Suicide and Depression Detection dataset](https://www.kaggle.com/nikhileswarkomati/suicide-watch) is obtained from Kaggle and stored as `Data/suicide_detection.csv`. The dataset was scraped from Reddit and consists of 232,074 rows equally distributed between 2 classes - suicide and non-suicide.

## 2. Text Preprocessing
Run `data_preprocessing.ipynb` to perform text preprocessing and generate `Data/suicide_detection_full_clean.csv`.
> Note: Spelling correction requires a long processing time.

## 3. Data Cleaning
Run `data_cleaning.ipynb` to clean data and generate `Data/suicide_detection_final_clean.csv`. This is the final dataset which will be used for the project and will be split into train:test:val sets with the ratio of 8:1:1. The final dataset is left with 174,436 rows with a class distribution of approximately 4:6 for suicide and non-suicide.

## 4. Exploratory Data Analysis (EDA)
Run `eda.ipynb` to gain more insights of both the original dataset and the cleaned dataset. EDA on the original dataset helped to determine steps for text preprocessing and data cleaning, while insights gained on the cleaned train data helped us to better build our representations and models.

## 5. Representation Learning
Run `word2vec.ipynb` to pre-train custom Word2Vec embeddings from our cleaned dataset and to generate `Data/vocab.txt` and `Data/embedding_word2vec.txt`. In our project, we have also experimented with pre-trained Twitter GloVe embeddings retrieved [here](https://nlp.stanford.edu/projects/glove/), which was downloaded and stored as `Data/glove_twitter_27B_200d.txt`.

## 6. Model Building & Evaluation
There are 5 models built for this project - Logistic Regression (Logit), Convolutional Neural Network (CNN), Long Short-term Memory Network (LSTM), BERT, and ELECTRA. These models are stored separately into different notebooks with the format `models_[model name].ipynb`. The trained models are stored in the `Models/` folder.
> Note: Different variations were built for each model to find the best hyperparameters by testing empirically.

## 7. Model Selection
The best variation of the aforementioned models can be seen in the table below. Although BERT and ELECTRA have rather comparable performances, **ELECTRA** is selected as the best performing model with our prioritisation on F1 score, as well as insights into the model architecture. Run `infer.ipynb` to predict whether input text has suicidal intent or not using the selected ELECTRA model.

| Best Model | Accuracy | Recall | Precision | F1 Score |
|:---:|:---:|:---:|:---:|:---:|
| Logit | 0.9111 | 0.8870 | 0.8832 | 0.8851 |
| CNN | 0.9285 | 0.9013 | 0.9125 | 0.9069 |
| LSTM | 0.9260 | 0.8649 | 0.9386 | 0.9003 |
| BERT | 0.9757 | 0.9669 | **0.9701** | 0.9685 |
| **ELECTRA** | **0.9792** | **0.9788** | 0.9677 | **0.9732** |


![image](https://github.com/aniket-singh8299/SUICIDAL-TEXT--DETECTION/assets/89138903/596f0d8e-5b7f-4337-8c59-5903c6478031)

