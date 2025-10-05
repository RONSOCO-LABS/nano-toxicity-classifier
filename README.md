# Nanotoxicology Machine Learning Classification Project

## 📋 Paper Information
**Title:** "Machine Learning-Based Prediction of Metal Nanoparticle Toxicity in Human Cell Lines: A Preliminary Contribution to the Development of Nanotoxicology in Peru"

**Team:**
- Leonardo Joaquín Camarena Trujillo - leonardo.camarena@unmsm.edu.pe
- Luis David Yauri Martinez - luis.yauri1@unmsm.edu.pe
- Jannina Romero Mori - jannina.romero@unmsm.edu.pe
- Nhikori Mirella Tovar Porras - nhikori.tovar@unmsm.edu.pe
- Juan Carlos Mondalgo Tapia - juan.mondalgo1@unmsm.edu.pe

---

## 📖 Project Overview

This project implements a comprehensive machine learning workflow for nanotoxicology classification, comparing the effects of outlier treatment and SMOTE balancing across multiple algorithms. The study systematically evaluates 4 experimental configurations using 6 different machine learning models.

## 🗂️ Project Structure

```
├── README.md
├── dataset_input/
│   ├── HaHa-Manual.csv
│   └── MeOX-IIIB.xlsx
├── dataset_output/
│   ├── 01_combined_data.csv
│   ├── 02_human_species.csv
│   ├── 03_human_species_filtered.csv
│   ├── dataset_outliers_treated.csv
│   └── dataset_outliers_untreated.csv
├── notebooks/
│   ├── preprocessing-of-the-datasets.ipynb
│   └── machine-learning-workflow.ipynb
└── results/
    ├── experiment_1/
    ├── experiment_2/
    ├── experiment_3/
    └── experiment_4/
```

## 📥 Data sources used for the initial dataset

The following sources were used to compile the initial dataset employed in this project:

- Structured Nanotoxicity Datasets with Physicochemical and Toxicological Attributes of Metal Oxide Nanoparticles
  - https://zenodo.org/records/15385143

- Meta-analyzed datasets for toxicity classification of metal oxide nanoparticles
  - https://zenodo.org/records/15300193

## 🚀 Reproduction Instructions

### Requirements

- Recommended / tested Python version: **3.10.0**.

- Verify your Python version before creating the virtual environment:

  ```powershell
  python --version
  ```

### Step 1: Initial Setup
1. **Clone/Download the repository**
2. **Ensure initial datasets are in place:**
   - Place `HaHa-Manual.csv` in `dataset_input/`
   - Place `MeOX-IIIB.xlsx` in `dataset_input/`

### Step 2: Environment Setup

#### Local Virtual Environment

1. **Create virtual environment:**
    ```bash
    python -m venv nanotox-env
    ```
2. **Activate environment:**
    ```bash
    # Windows
    nanotox-env\Scripts\activate

    # macOS/Linux
    source nanotox-env/bin/activate
    ```

3. **Install required dependencies (desde `requirements.txt`):**
    ```bash
    pip install -r requirements.txt
    ```

### Step 3: Data Preprocessing

1. **Execute preprocessing notebook:**
   - Open and run `notebooks/preprocessing-of-the-datasets.ipynb`
   - This will generate the processed datasets in `dataset_output/`:
     - `dataset_outliers_treated.csv`
     - `dataset_outliers_untreated.csv`

### Step 4: Machine Learning Experiments

1. **Run the main ML workflow:**
   - Execute `notebooks/machine-learning-workflow.ipynb`
   - This notebook contains the complete 4-experiment framework:
     - **Experiment 1:** Outliers treated with SMOTE
     - **Experiment 2:** Outliers treated without SMOTE
     - **Experiment 3:** Outliers untreated with SMOTE
     - **Experiment 4:** Outliers untreated without SMOTE

## 📊 Expected Outputs

After execution, you will obtain:

### 1. Model Performance Results
- Comprehensive comparison of 6 ML algorithms:
  - Logistic Regression
  - Decision Tree
  - Random Forest
  - XGBoost
  - LightGBM
  - Support Vector Machine (SVM)

### 2. Visualization Outputs
- ROC curves comparison for best models
- Class distribution analysis
- Experimental results comparison tables

### 3. Model Persistence
- Best trained models saved as `.pkl` files
- Results exported as CSV files

## �🔬 Experimental Framework

The project implements a **2×2 factorial design**:

| Experiment | Outlier Treatment | SMOTE Balancing | Dataset |
|------------|------------------|-----------------|---------|
| Experiment 1 | ✅ Treated | ✅ Applied | `dataset_outliers_treated.csv` |
| Experiment 2 | ✅ Treated | ❌ Not Applied | `dataset_outliers_treated.csv` |
| Experiment 3 | ❌ Not Treated | ✅ Applied | `dataset_outliers_untreated.csv` |
| Experiment 3 | ❌ Not Treated | ❌ Not Applied | `dataset_outliers_untreated.csv` |

## 🎯 Key Features

- **Systematic Experimental Design:** 4 controlled experiments evaluating preprocessing combinations
- **Comprehensive Model Evaluation:** 6 state-of-the-art ML algorithms with hyperparameter optimization
- **Robust Validation:** Stratified K-fold cross-validation with performance metrics
- **Reproducible Results:** Fixed random seeds and standardized evaluation protocols

## 📈 Main results

Below is a summary of the best-performing models for each experiment with the main metrics (AUC, Accuracy, Precision, Recall and F1-score). The metrics correspond to the aggregated evaluation used in the study (stratified validation and selection of the best model per experiment).

| Experiment | Model | AUC | Accuracy | Precision | Recall | F1-score |
|------------|:-----:|----:|--------:|---------:|------:|---:|
| EXP1: Outliers treated with SMOTE | XGBoost | 0.960 | 0.879 | 0.885 | 0.878 | 0.881 |
| EXP2: Outliers treated without SMOTE | XGBoost | 0.963 | 0.912 | 0.910 | 0.912 | 0.911 |
| EXP3: Outliers untreated with SMOTE | LightGBM | 0.957 | 0.919 | 0.919 | 0.919 | 0.919 |
| EXP4: Outliers untreated without SMOTE | XGBoost | 0.962 | 0.914 | 0.913 | 0.914 | 0.913 |

For detailed results, ROC curves and saved models please check the notebook `notebooks/machine-learning-workflow.ipynb`, the CSV files in `results/` and the serialized models in the `results/experiment_*` folders.

## 📚 Academic Use Guidelines & Disclaimer

### ✅ Permitted uses
- Research and academic purposes
- Educational activities and coursework
- Scientific publications and citations
- Non-commercial research collaboration
- Thesis and dissertation projects

### ⚠️ Restrictions & contact
- Commercial use requires explicit written permission
- Redistribution must include this license notice
- Modifications should be clearly documented
- Original authorship must be acknowledged

**Contact for permissions:**
- Luis David Yauri Martinez — luis.yauri1@unmsm.edu.pe

---

### ℹ️ Disclaimer

This project is part of an academic research study on nanotoxicology classification using machine learning techniques. All data and methodologies are intended for educational and research purposes only.

The models and results presented in this project are for academic research purposes. Clinical or regulatory decisions should not be based solely on these computational predictions without proper experimental validation.

## 📄 License

This project is licensed under the **MIT License**. See the full license in [LICENSE.md](./LICENSE.md).