# Virtual Healthcare Assistant – Data Science & AI Project

## Project Overview
This project develops a Virtual Healthcare Assistant using Natural Language Processing (NLP) and Machine Learning. The system was designed to interpret patient symptom descriptions, handle both medical terminology and everyday language, and provide outputs that can guide users.  

The work followed the full data workflow: preparing and cleaning raw data, exploring patterns, building and evaluating an NLP model, and designing a prototype interface for end users.

## 🎥 Project Presentation
You can watch my project walkthrough here:  

[![Watch the presentation](https://img.youtube.com/vi/B0r3LW2G5iA/0.jpg)](https://youtu.be/B0r3LW2G5iA)

---

## Process

### 1. Data Preparation
The first stage focused on ensuring the dataset was ready for analysis:
- Missing numerical values were filled using means, categorical values with modes  
- Text was standardised (lowercasing, punctuation removal) to reduce errors in input  
- Duplicate rows were removed to avoid bias and redundancy  
- Underrepresented conditions were augmented using data generation techniques to reduce class imbalance  

These steps produced a dataset that was consistent and structured for model training.

### 2. Data Exploration
Exploratory Data Analysis (EDA) was carried out to understand distributions, biases, and relationships:
- Frequency counts of common vs rare conditions  
- Identification of overrepresented illnesses such as colds and flu  
- Visualisations (Matplotlib, Seaborn) to display class distributions and highlight imbalance  
- Comparison of dataset frequencies with public health data for representativeness  

EDA confirmed the need for balancing techniques and guided the choice of model evaluation metrics.

### 3. Model Development
A range of NLP approaches were considered, with **BioBERT** selected for its biomedical language pre-training:
- **Data split**: 85% training, 15% testing  
- **Tokenization**: text converted into numerical tokens of fixed length (128 tokens per input)  
- **Architecture**: classification layer added on top of BioBERT  
- **Training setup**:  
  - Optimiser: AdamW  
  - Learning rate: 5e-5  
  - Loss function: Cross-Entropy  
  - Batch processing across 3 epochs  

This approach allowed the model to interpret both precise medical terminology and informal symptom inputs.

### 4. Model Evaluation
Performance was assessed with standard classification metrics:
- **Accuracy**: overall proportion of correct predictions  
- **Precision and Recall**: reviewed per condition, highlighting imbalance  
- **F1 score**: used to balance precision and recall for skewed data  
- **Confusion matrix**: revealed frequent misclassification of rare conditions into common ones  

Key findings:
- Precision for “common cold” reached 0.80 but recall was low (0.10)  
- Rare conditions (e.g., migraine, stomach bug) had precision and recall below 0.20  
- The model tended to over-predict frequent labels, confirming dataset imbalance as a core issue  
- **Mitigation**: confidence thresholds introduced to trigger clarifying questions or deferrals instead of unreliable predictions  

### 5. User Interface Design
The technical model outputs were paired with a prototype design aimed at non-technical users:
- **Body diagram input**: tap to select affected area  
- **Dropdown menus**: pre-filled symptom choices to reduce typing and error  
- **Navigation**: large, simple buttons with recognisable icons  
- **Results**: condition displayed with plain-language explanation, likelihood score, and suggested actions  

Prototypes were created in **Axure RP**, following Human-Computer Interaction (HCI) principles such as progressive disclosure, recognition over recall, and accessibility guidelines.

---

## Key Outcomes
- Cleaned and balanced dataset suitable for NLP modelling  
- A BioBERT-based classifier trained and evaluated on symptom descriptions  
- Insights into the impact of dataset imbalance on healthcare prediction tasks  
- Quantitative results from accuracy, precision, recall, F1, and confusion matrix analysis  
- Safety mechanisms through confidence thresholds and clarifying questions  
- Prototype user interface showing how predictions can be presented clearly and accessibly  

---

## Repository Contents
- `001239369-X_Report.pdf` – Full project report with methodology and evaluation  
- `Cleaned_data_set.csv` – Processed dataset used for training and testing  
- `1_Data_cleaning_processing.ipynb` – Data cleaning notebook  
- `2_Data_Exploration_Analysis.ipynb` – Exploratory analysis notebook  
- `3_Model_Development.ipynb` – Model training and evaluation notebook  
- `train_data.csv` and `test_data.csv` – Partitioned datasets  

---

## Next Steps
- Apply oversampling (e.g., SMOTE) to improve classification of rare conditions  
- Extend evaluation using cross-validation to increase robustness  
- Deploy as a lightweight web application to demonstrate interactive use cases  


