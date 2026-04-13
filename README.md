# Gene-Enhanced AMDGT for Drug–Disease Association Prediction

## Overview
This project presents an enhanced version of the AMDGT (Attention-aware Multi-modal Dual Graph Transformer) model for predicting drug–disease associations.

The proposed improvement incorporates **sample-specific gene representations** into the fusion stage, enabling the model to better capture biological interactions between drugs, diseases, and genes. This leads to improved predictive performance and better generalization across datasets.

---

## Key Contribution
- Introduced **gene-aware fusion mechanism**
- Used **sample-specific gene embeddings** instead of global aggregation
- Improved performance on benchmark datasets (C and F)
- Maintained fair evaluation using unchanged datasets

---

## Requirements
- Python 3.9.13  
- PyTorch 1.10.0  
- DGL 0.9.0  
- NumPy 1.23.1  
- NetworkX 2.8.4  
- Scikit-learn 0.24.2  
- CUDA Toolkit (optional, CPU supported)

---

## Dataset
The project uses standard benchmark datasets:
- **C-dataset**
- **F-dataset**
- B-dataset

Each dataset contains:
- Drug–Disease associations  
- Drug–Protein interactions  
- Disease–Protein interactions  
- Feature embeddings for drugs, diseases, and proteins  

Note:  
Datasets are used **without modification**. Any performance improvement comes solely from model enhancements.

---

## Model Architecture

The framework consists of:

1. **Similarity Network Construction**
   - Drug similarity (fingerprint + GIP)
   - Disease similarity (phenotype + GIP)

2. **Graph Transformer (GT)**
   - Extracts similarity-based features

3. **Heterogeneous Graph Transformer (HGT)**
   - Captures structural relationships among drugs, diseases, and proteins

4. **Gene-Aware Fusion (Proposed)**
   - Combines drug–disease interaction with **sample-specific gene embeddings**

H = (H_r ⊙ H_d) + H_g

5. **Prediction Module**
- MLP for final classification

---

## Visualization

- ROC Curves (C, F, B datasets)
- Precision-Recall (PR) Curves

These demonstrate improved discrimination capability of the proposed model.

---

## Project Structure

<pre>
AMDGT/
│
├── data/                  # Dataset files
├── model/                 # Model architecture
├── data_preprocess.py     # Data preprocessing
├── metric.py              # Evaluation metrics
├── train_DDA.py           # Training script
└── README.md
</pre>

## Usage

### 1. Clone the repository

```bash
git clone https://github.com/your-username/AMDGT.git
cd AMDGT
```

### 2. Install dependencies

```bash
pip install torch dgl numpy networkx scikit-learn
```

### 3. Run training (C-dataset)

```bash
python train_DDA.py --dataset C-dataset
```

### 4. Run training (F-dataset)

```bash
python train_DDA.py --dataset F-dataset
```
