# NLP Homework 01 — Kamyar Goodarzi

A clean, reproducible implementation of **Natural Language Processing Homework 01**.  
The project covers practical NLP workflows including web scraping, Persian text preprocessing, TF-IDF based recommendation, and Persian news classification.

---

## Project Summary

This repository contains the completed notebook, generated outputs, and trained model artifacts for four NLP tasks:

1. **Job Data Extraction** using Selenium and BeautifulSoup  
2. **Persian Text Cleaning** using Regex and Hazm  
3. **Movie Recommendation** using TF-IDF and Cosine Similarity  
4. **Persian News Classification** using TF-IDF and LinearSVC  

The main implementation is available in:

```text
HW_NLP_01_KamyarGoodarzi.ipynb
```

---

## Repository Structure

```text
.
├── HW_NLP_01_KamyarGoodarzi.ipynb
├── models/
│   └── task4_persian_news_tfidf_linearsvc_pipeline.joblib
├── outputs/
│   ├── task1_jobinja_jobs.csv
│   ├── task2_cleaned_persian_texts.csv
│   ├── task2_top10_words.csv
│   ├── task3_movie_recommendations_The_Dark_Knight.csv
│   ├── task4_class_distribution.csv
│   ├── task4_classification_report.csv
│   ├── task4_classification_report.txt
│   ├── task4_cleaned_news_dataset.csv
│   ├── task4_confusion_matrix.jpg
│   ├── task4_confusion_matrix.png
│   ├── task4_confusion_matrix_normalized.csv
│   ├── task4_confusion_matrix_raw.csv
│   ├── task4_error_analysis.txt
│   ├── task4_label_names.json
│   ├── task4_test_predictions.csv
│   └── task4_training_metadata.json
├── .gitignore
└── README.md
```

---

## Task 1 — Web Scraping with Selenium and BeautifulSoup

The first task implements a web scraping workflow for extracting job listing information from paginated pages.

Extracted fields:

- Job title
- Company name
- City/location
- Page number
- Listing URL

Generated artifact:

```text
outputs/task1_jobinja_jobs.csv
```

> Note: The current generated CSV keeps the expected output schema. If the target website blocks automation, changes its HTML structure, or returns no listings during execution, the output file may contain only headers.

---

## Task 2 — Persian Text Cleaning with Regex and Hazm

This task builds a Persian preprocessing pipeline for cleaning noisy text.

The pipeline includes:

- Regex-based noise removal
- Repeated-character correction
- Persian normalization with Hazm
- Tokenization
- Stopword removal
- Preservation of negation words such as `نه`, `نیست`, `نمی`, and `نبود`
- Top-word frequency analysis

Generated artifacts:

```text
outputs/task2_cleaned_persian_texts.csv
outputs/task2_top10_words.csv
```

The cleaned text output contains **8 records**.

Top frequent words after preprocessing are saved in `task2_top10_words.csv`.

---

## Task 3 — Content-Based Movie Recommendation

This task implements a recommendation system using movie descriptions.

Main steps:

- Load movie titles and overviews
- Remove missing overviews
- Convert overviews into TF-IDF vectors
- Compute cosine similarity
- Return the five most similar movies for a selected movie title

Generated artifact:

```text
outputs/task3_movie_recommendations_The_Dark_Knight.csv
```

Example recommendation query:

```text
The Dark Knight
```

Generated recommendations:

- The Dark Knight Rises
- Batman Returns
- Batman: The Dark Knight Returns, Part 2
- Batman Forever
- Batman

---

## Task 4 — Persian News Classification

This task trains a Persian news classification model using TF-IDF features and a linear support vector classifier.

Model configuration:

- Model: `LinearSVC`
- Vectorizer: `TfidfVectorizer`
- N-gram range: `(1, 2)`
- Maximum features: `30000`
- Total samples: `1975`
- Training samples: `1580`
- Test samples: `395`
- Classes:
  - `صفحه نخست`
  - `عصرايران دو`

Generated artifacts:

```text
models/task4_persian_news_tfidf_linearsvc_pipeline.joblib
outputs/task4_classification_report.csv
outputs/task4_classification_report.txt
outputs/task4_confusion_matrix.png
outputs/task4_confusion_matrix.jpg
outputs/task4_confusion_matrix_raw.csv
outputs/task4_confusion_matrix_normalized.csv
outputs/task4_error_analysis.txt
outputs/task4_test_predictions.csv
outputs/task4_training_metadata.json
```

Classification report:

```text
precision    recall  f1-score   support

   صفحه نخست       0.94      0.94      0.94       200
 عصرايران دو       0.93      0.93      0.93       195

    accuracy                           0.93       395
   macro avg       0.93      0.93      0.93       395
weighted avg       0.93      0.93      0.93       395
```

Error analysis summary:

```text
Most confused pair:
The model most frequently classified "صفحه نخست" as "عصرايران دو".

Number of such errors:
13

Possible reason:
These two topics probably share overlapping vocabulary and similar news context. In Persian news, categories such as politics, economy, society, and international affairs often contain common words related to government, institutions, sanctions, prices, decisions, and public events.

Because this model is based on TF-IDF features, it mainly learns word-frequency patterns rather than deep semantic meaning. Therefore, when two topics use similar words, the classifier may confuse them.
```

---

## How to Run

1. Clone the repository:

```bash
git clone <repository-url>
cd NLP-Homework-01-Kamyar-Goodarzi
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
.venv\Scripts\activate
```

3. Install the required Python packages:

```bash
pip install pandas numpy matplotlib scikit-learn beautifulsoup4 selenium hazm joblib jupyter
```

4. Open the notebook:

```bash
jupyter notebook HW_NLP_01_KamyarGoodarzi.ipynb
```

5. Run the cells in order.

---

## Notes

- The `outputs/` directory contains generated CSV files, plots, reports, and prediction results.
- The `models/` directory contains reusable trained model artifacts.
- Dataset files may need to be downloaded separately depending on the execution environment.
- Selenium-based scraping may require a compatible browser and WebDriver.
- Results may vary slightly depending on package versions, dataset versions, and website availability.

---

## Author

**Kamyar Goodarzi**  
Natural Language Processing — Homework 01
