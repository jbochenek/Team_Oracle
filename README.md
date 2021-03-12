# Team_Oracle
Drexel Winter 2021 DSCI 592 Team Oracle
# TEAM ORACLE
## Capstone Project for DSCI 592, Winter 2021, team Oracle
### Introduction


[Whole Project on Google Drive](https://drive.google.com/drive/folders/10-42_ifui6hlObPWvMMivdQwEFf6Vh43?usp=sharing)

[Instructions on Mirroring Project and Running Code](https://docs.google.com/document/d/1ysa7SlRrU_gzBxPbzbzn_VbI47uG09an0JxQ1BUjOps/edit?usp=sharing)

---

# Table of Contents
1. [Team Members](#TEAM-MEMBERS)
1. [Datasets](#EXPLANATION-OF-DATASETS)
1. [Acquisition](#DATA-ACQUISITION)
1. [Pre-Processing](#DATA-PRE-PROCESSING)
1. [Vizualization](#DATA-VISUALIZATION)
1. [Analysis](#DATA-ANALYSIS)
1. [Final Reports](#FINAL-REPORTS)
1. [Responsibilities](#RESPONSIBILITY-SUMMARY)

---
# TEAM MEMBERS

### Jennifer Bochenek
- Education 
  - B.S. in Psychology with concentrations in Psychobiology of Addiction and Clinical Psychology, and a minor in Biology from Purdue University (May 2011)
  - M.S. in Psychology from New Mexico Highlands University, thesis topic on *Sensation Seeking and Sleep Quality: Activity as a pre-requisit for high quality sleep* (December 2012)
- Occupation
  - Research Associate at Educational Testing Service
- Skills
  - R, Python, Java, SQL, Unix
  - SPSS, Orange, Weka, Tableau
  - Data collection/acquisition, management and cleaning; descriptive and inferential statistics; machine learning; data visualization; paper writing


### Yifan Yang
- Education
  - B.S. in Statistics and minor in Computer Science from Virginia Tech
- Occupation
  - Student, formerly IT for a POS company
- Skills
  - SQL, Unix, Java, Python, R
  - R-Studio, Python 
  - Descriptive, infernetial, non-parametric and other advanced statistics, machine learning, data visualization
  
  
### Shibo Yao
- Education
  - B.S. in Software Engineering
- Occupation
  - Student, formerly assistant industry analyst for a consulting company
- Skills
  - Python, Java, R, SQL
  - Eclipse, Pycharm, Rstudio
  - Data acquisition, pre-processing, analysis, and interpretation

### Joe Larson
- Education
  - Penn State
  - Electrical Engineering 
  - MBA
  - Master of Expert Systems
- Occupation
  - Manager at a GSE
- Skills
  - R, Python
  - Google Colaboratory
  - Management

For our team we have split out the research areas/topics and each team member is responsible for acquisition, cleaning, merging (if needed) of data for their topic, and analysis of said data, which all contribute to the final dataset and report. We will also be rotating who is the team facilitator for meetings on a weekly basis.

---

# EXPLANATION OF DATASETS
The data for this project comes from Kaggle. It is part of their ongoing process to provide a dataset for use in NLP analysis. The data is part of a posted competition called “Natural Language Processing with Disaster Tweets”, with the stated purpose to “predict which Tweets are about real disasters and which ones are not”. We chose this dataset because the topic was of interest and the data was not pre-cleaned, so this would make it a challenge. The data from Kaggle is a selection of tweets from Twitter that were then tagged by humans for if they were about real tweets or not. Additionally, humans tagged keywords concerning what disaster type the tweet could be concerning. These keywords were present regardless of real vs not disaster status. The interesting part is that neither the keyword nor the tweet have been preprocessed nor cleaned, which makes it perfect for our purposes. 

---

# DATA ACQUISITION
The dataset was downloaded directly from Kaggle. In order to do so, we made a team on Kaggle and joined the competition. There are two files, a training dataset, and a test dataset. Both were downloaded as a CSV and transferred to the group’s google documents folder.

---

# DATA PRE-PROCESSING
As stated previously, there is extensive data pre-processing that has to be done. There are 5 columns in the original dataset: ID, Location, Keyword, Text, and Target. Location and Keyword both had missing data (Location: 2533 in training, 1105 in test, Keyword: 61 null in training, 26 null in test), but text and target were never null.  There are 7,613 tweets in the training set and 3,263 in the test set. Location is the location of the tweeter’s account that is set in their settings, some of them are non-locations. We decided to not use the location data as a result. 

The biggest challenge was in cleaning the text data and creating additional variables to use in the machine learning algorithms. In order to do so in an organized manner, we created a data flow table that describes the order that the steps should be done in and how they concern the variables that are being altered. Table 1 below shows that process, with the description of the step, what variable is being used, what variable is being created, alongside which members of the team were responsible for each step. Many of the same steps were also used on the keyword variable, as sensible. The final resultant dataset contained 91 variables.

|     | Description                                                                                                                                                      | In Variable                                      | Out Variable                                                                                                                                                                                                     | Responsibility | Notes/Progress                                 |
|-----|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|------------------------------------------------|
| 1.  | Change text to lower charters                                                                                                                                    | [‘text’]                                         | [‘text_to_lower’]                                                                                                                                                                                                | Joe            | Done                                           |
| 2.  | Remove encoding errors (otherwise would artificially inflate the char count)                                                                                     | [‘text_lower’]                                   | [‘text_remove_encoding_error’]                                                                                                                                                                                   | Jenni          | Done                                           |
| 3.  | Count of total char Count of hashtags (#)  Count of urls Count of words Count of punctuation  Count of unique words (non-repeated)  Count of average word length | [‘text_remove_encoding_error’]                   | ['text_count_total_char'] ['text_count_hashtags'] ['text_count_urls'] ['text_count_words'] ['text_count_punctuation'] ['text_count_unique_words'] ['text_mean_words_length']                                     | Jenni/ Joe     | Done                                           |
| 4.  | Separate hashtags into new column                                                                                                                                | [‘text_remove_encoding_errors’]                  | [‘text_hashtags’]                                                                                                                                                                                                | Jenni          | Done                                           |
| 5.  | Edit typos, slang, and informal language                                                                                                                         | [text_remove_encoding_errors']                   | [‘text_informal_language’]                                                                                                                                                                                       | Jenni          | Done                                           |
| 6.  | Remove URLs                                                                                                                                                      | [‘text_informal_language’]                       | [‘text_url_removed’]                                                                                                                                                                                             | Joe            | Done                                           |
| 7.  | Do we want/need to redo counts here?                                                                                                                             | [‘text_informal_language’]                       | ['text_count_total_char'] ['clean_text_count_hashtags'] ['clean_text_count_urls'] ['clean_text_count_words'] ['clean_text_count_punctuation'] ['clean_text_count_unique_words'] ['clean_text_mean_words_length'] | Joe            | Done                                           |
| 8.  | Determine reading level, comprehension level, grade level of text?                                                                                               | [‘text_informal_language’]                        |                                                                                                                                                                                                                  | Y&S            | decided not to do based on not being impactful |
| 9.  | Tokenize                                                                                                                                                         | [‘text_url_removed’]                             | ['text_token']                                                                                                                                                                                                   | Joe            | Done                                           |
| 10. | Sentiment                                                                                                                                                        | df_train Full dataframe                          | ['text_affect_dict'] ['text_top_affect'] ['text_affect_freq'] ['text_raw_emotion’]                                                                                                                             | Jenni          | Done Use NRCLex                                |
| 11. | Higher level sentiment analysis                                                                                                                                  | df_train Full dataframe                          | ['all_negative'] ['all_positive'] ['anger'] [‘disgust’] [‘fear’] [‘sadness’] [‘anticipation’] [‘joy’] [‘surprise’] [‘trust’]                                                                                     | Jenni          | Done                                           |
| 12. | Remove punctuation                                                                                                                                               | [‘text_url_removed’]                             | [‘text_remove_punctuations’]                                                                                                                                                                                     | Joe            | Done                                           |
| 13. | Named Entity Recognition POS Tagging                                                                                                                             | [‘text_token’] [‘text_pos_tag’]                  | [‘text_ner_tag’] [‘text_ner_tag’]                                                                                                                                                                                | Y&S            | Done                                           |
| 14. | Remove Stopwords (remember to add stands for retweet to Stopwords list)                                                                                          | [‘text_token’]                                   | [‘text_token_remove_stopwords’]                                                                                                                                                                                  | Yifan& Shibo   | Done                                           |
| 15. | Stem words Lemmatize words                                                                                                                                       | [‘text_token_remove_stopwords’] [‘text_pos_tag’] | [‘text_stem’]   [‘text_clean_lemma’]                                                                                                                                                                             | Y&S            | Done                                           |
| 16. | TF TF-IDF                                                                                                                                                        | [‘text_lemma’]                                   | [‘text_tf’] [‘text_tfidf’]                                                                                                                                                                                       | Jenni          | See doing tf-idf with scikitlearn link below   |
| 17. | Word2Vec                                                                                                                                                         | [‘text_token’]                                   | [‘text_vec’]                                                                                                                                                                                                     | Jenni          | Use Gensim                                     |

---

# DATA VISUALIZATION
### Tweet Histograms
![Tweet Histograms](images/histogramstext.png?raw=true "Tweet Histograms")

### Keyword Histograms
![Keywords Histograms](images/histogramskeyword.png?raw=true "Keywords Histograms")

### Pair Plot by Target
![Pair Plot by Target](images/pairplotcountstarget.png?raw=true "Pair Plot of Count Variables by Target")

### Correlation Matrix
![Correlations](images/correlation.png?raw=true "Correlation Matrix")

### Wordcloud for Tweets
![Tweet Wordcloud](images/text.png?raw=true "Tweet Wordcloud")

### Wordcloud for Tweets with non-real Disasters
![Non-Real Disaster Tweets](images/target0.png?raw=true "Non-Real Disaster Tweets")

### Wordcloud for Tweets with real Disasters
![Real Disaster Tweets](images/target1.png?raw=true "Real Disaster Tweets")

### Wordcloud for Keywords
![Keyword Wordcloud](images/keyword.png?raw=true "Keyword Wordcloud")

---

# DATA ANALYSIS

### Feature Importance

### Naive Bayes
- Accuracy: 0.803
- Recall: 0.69
- F1: 0.75
- Pecision: 0.82

### Support Vector Machines
Before Optimization
SVC(random_state = 23)
- Accuracy: 0.629
- Recall: 0.397
- F1: 0.479
- Pecision: 0.604


After Optimization
SVC(C=0.5, class_weight = None, gamma = 0.001, kernel='linear', random_state = 23)
- Accuracy: 0.804
- Recall: 0.668
- F1: 0.746
- Pecision: 0.845

### BERT
- Accuracy: 0.831
- Recall: 0.766
- F1: 0.796
- Pecision: 0.827

### K-Nearest Neighbor
Before Optimization
- Accuracy: 0.718
- Recall: 0.718
- F1: 0.717
- Pecision: 0.716

After Optimization
- Accuracy: 0.727
- Recall: 0.727
- F1: 0.727
- Pecision: 0.728

### Gradient Boosting
Before Optimization
- Accuracy: 0.691
- Recall: 0.691
- F1: 0.692
- Pecision: 0.694

After Optimization
- Accuracy: 0.718
- Recall: 0.718
- F1: 0.717
- Pecision: 0.717


### Model Comparison

|           | Naive Bayes | SVC   | BERT  | KNN   | Gradient Boosting |
|-----------|-------------|-------|-------|-------|-------------------|
| Accuracy  | 0.802       | 0.804 | 0.831 | 0.727 | 0.718             |
| Recall    | 0.691       | 0.668 | 0.766 | 0.727 | 0.718             |
| F1        | 0.754       | 0.746 | 0.796 | 0.727 | 0.717             |
| Precision | 0.823       | 0.845 | 0.827 | 0.728 | 0.717             |

---

# FINAL REPORTS
- [Launch Report](https://drive.google.com/file/d/15KfQaU8OuMD9S-bvT8gHdp_dhFoZs9ZB/view?usp=sharing)
- [Pitch Presentation](https://docs.google.com/presentation/d/1YLyuNzaK5g3q05XDbT2ZW4Gx-scvFxnpfSup-AL45Us/edit?usp=sharing)
- [Data Acquisition, Pre-Processing, & Exporatory Data Analysis Report](https://drive.google.com/file/d/16kYkAiHrbIjpaxFCZT3rHyijl3tWc5kv/view?usp=sharing)
- [Predictive Modeling Report](https://drive.google.com/file/d/1Inl7djEvG7uKzIGU2E6CleqAmWnowzpZ/view?usp=sharing)
- [Final Presentation](https://docs.google.com/presentation/d/1QJsjxDM95MamnSZxHz2pd1UeU-9BH0K3FH1eWrgYLLs/edit?usp=sharing)

---

# RESPONSIBILITY SUMMARY

Jenni Bochenek: Launch report, Data acquisition and Preprocessing/Exploratory Data Analysis report

Joe Larson: Outline and steps to accomplish the project, coding format and some unit testing

Yifan Yang: Pitch Presentation

Shibo Yao: Final Presentation

All: Data acquisition, preprocessing, applying ML model, Model evaluation and final report.

