# 📝 Automated IELTS Essay Grading (Multi-Criteria Prediction)

## 📌 Overview
This project implements an **Automated Essay Grading (AEG) system** for **IELTS Writing essays**.  
The system predicts scores for **four IELTS assessment criteria** based on the input essay text using **Natural Language Processing (NLP)** and **Machine Learning models**.

The task is formulated as a **multi-output regression problem**, where one essay produces four predicted scores simultaneously.

### IELTS Scoring Criteria
- **Task Achievement**
- **Coherence and Cohesion**
- **Lexical Resource**
- **Grammatical Range and Accuracy**

---

## 🧹 Data Preprocessing
Raw essay text is transformed into numerical features through the following steps:

1. **Lowercasing & Special Character Removal**  
   Convert all text to lowercase and remove special characters.

2. **Word Filtering**  
   - Remove very short words (less than 3 characters)  
   - Keep meaningful tokens only

3. **Remove Frequent Words**  
   Remove words that appear too frequently across the dataset and carry low discriminative power.

4. **Remove Rare Words**  
   Remove words that appear very rarely to reduce noise.

5. **TF-IDF Vectorization**  
   Convert cleaned text into a numerical representation using **TF-IDF**, producing a **high-dimensional sparse vector (~9000 features)**.

---

## 🔢 Feature Representation
- **Input**: Essay text  
- **Output**: Sparse numerical vector using TF-IDF  
- **Vector Dimension**: ~9000 features  

This representation captures the importance of words across essays while handling vocabulary sparsity.

---

## 🤖 Models Used
Several machine learning models are evaluated:

- **LightGBM**
- **XGBoost**
- **Random Forest**

### Model Characteristics
- **LightGBM**  
  Efficient with large feature spaces and handles imbalanced data well.

- **XGBoost**  
  Strong regularization and flexible hyperparameters, but sensitive to tuning.

- **Random Forest**  
  More robust to overfitting and requires less tuning, suitable for noisy data.

---

## 📊 Results
Model performance comparison:

| Model | KaggleScore |
|------|------|
| LightGBM | 0.6046 |
| XGBoost | 0.4768 |
| Random Forest | **0.2241** |

📌 **Random Forest** is selected as the **most robust model**, providing more stable predictions for high-dimensional TF-IDF features.

---

## 🎯 Prediction Output
For each essay, the model predicts **four scores**:

- Task Achievement  
- Coherence & Cohesion  
- Lexical Resource  
- Grammatical Range & Accuracy  

These scores can be directly mapped to IELTS band score components.

---

## 🛠 Tech Stack
- Python  
- Scikit-learn  
- LightGBM  
- XGBoost  
- Pandas, NumPy  
- NLP (TF-IDF)
