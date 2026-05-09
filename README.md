# pancancer_reproduction_hcai

Reproduction of:

Crawford, Chikina, Greene (2024)  
*Optimizer's dilemma: optimization strongly influences model selection in transcriptomic prediction*

---

## 📁 Overview

This repository contains my reproduction of the paper using the provided codebase:
https://github.com/greenelab/pancancer-evaluation

---

## ⚙️ Setup

```bash
conda env create -f environment.yml
conda activate pc-eval

## 📊 Data Access

⚠️ Large data files (e.g., `.tsv.gz`, expression matrices) are **not included in this repository** due to GitHub file size limitations.

The required data can be obtained using the provided preprocessing notebook:

```bash
cd 00_process_data
jupyter notebook download_data.ipynb

Due to computational constraints, I have run:

50 genes used (instead of 84)
2 cross-validation folds (instead of 4×2)
Reduced hyperparameter search

cd 01_stratified_classification

python run_stratified_lasso_penalty.py \
    --genes top_50 \
    --num_folds 2 \
    --results_dir ../results

python run_stratified_lasso_penalty.py \
    --genes top_50 \
    --sgd \
    --num_folds 2 \
    --results_dir ../results_sgd_small

📈 Results
Main finding reproduced:
liblinear and SGD show similar predictive performance
Differences due to:
smaller dataset
reduced CV folds
limited compute

Figures comparing results are in:
figures/
