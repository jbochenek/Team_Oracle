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
1. [Analysis](#DATA-ANALYSIS)
1. [Vizualization](#DATA-VISUALIZATION)
1. [Final Report](#FINAL-REPORT)
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
## MAIN DATASET


---

# DATA ACQUISITION
## MAIN DATASETS

---

# DATA PRE-PROCESSING
## MAIN DATASETS

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

# DATA ANALYSIS & VISUALIZATION
## MAIN DATASETS

---


# FINAL REPORTS
- [Launch Report](https://drive.google.com/file/d/15KfQaU8OuMD9S-bvT8gHdp_dhFoZs9ZB/view?usp=sharing)
- [Pitch Presentation](https://docs.google.com/presentation/d/1YLyuNzaK5g3q05XDbT2ZW4Gx-scvFxnpfSup-AL45Us/edit?usp=sharing)
- [Data Acquisition, Pre-Processing, & Exporatory Data Analysis Report](https://drive.google.com/file/d/16kYkAiHrbIjpaxFCZT3rHyijl3tWc5kv/view?usp=sharing)
- [Predictive Modeling Report](https://drive.google.com/file/d/1Inl7djEvG7uKzIGU2E6CleqAmWnowzpZ/view?usp=sharing)
- [Final Presentation]()

---

# RESPONSIBILITY SUMMARY

Jenni Bochenek: Launch report, Data acquisition and Preprocessing/Exploratory Data Analysis report

Joe Larson: Outline and steps to accomplish the project, coding format and some unit testing

Yifan Yang: Pitch Presentation

Shibo Yao: Final Presentation

All: Data acquisition, preprocessing, applying ML model, Model evaluation and final report.

