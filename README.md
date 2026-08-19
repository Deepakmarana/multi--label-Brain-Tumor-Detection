# 🧠 Brain Tumor Classification using Hybrid ResNet–Transformer

A deep learning project for **brain tumor classification from T2-weighted MRI images** using a hybrid **ResNet-18 + Transformer** architecture.

The model combines **CNN-based local feature extraction** with **Transformer-based global context modeling** to improve classification of visually similar brain tumor patterns.

---

## 🚀 Key Features

* T2-weighted MRI brain tumor classification
* ResNet-18 for local feature extraction
* Transformer Encoder for global context modeling
* 49 visual tokens generated from a 7×7 feature map
* Positional encoding
* Multi-head self-attention
* Data augmentation
* AdamW optimizer
* OneCycleLR learning-rate scheduler
* Mixed-precision training
* Accuracy, Precision, Recall and F1-score evaluation

The proposed architecture uses ResNet-18 to generate a `512 × 7 × 7` feature map, which is converted into 49 tokens before Transformer processing.

---

## 🏗️ Architecture

```text
              T2-Weighted MRI
                     │
                     ▼
              Image Preprocessing
                     │
                     ▼
               Data Augmentation
                     │
                     ▼
                 ResNet-18
                     │
                     ▼
              Feature Map
               512 × 7 × 7
                     │
                     ▼
             Tokenization
               49 Tokens
                     │
                     ▼
          Positional Encoding
                     │
                     ▼
          Transformer Encoder
          ┌──────────┴──────────┐
          │                     │
       Self-Attention          FFN
          │                     │
          └──────────┬──────────┘
                     ▼
          Global Feature Modeling
                     │
                     ▼
          Classification Head
                     │
                     ▼
              Tumor Classes
```

The hybrid architecture is designed to combine the local feature strength of CNNs with the long-range dependency modeling capability of Transformers.

---

## 📂 Dataset

The project uses T2-weighted MRI images from a Kaggle dataset.

The selected categories are:

* Astrocytoma
* Carcinoma
* Ependymoma
* Glioblastoma
* Normal
* Oligodendroglioma
* Tuberculoma

Images are resized to **224 × 224 pixels** before training.

### Dataset Structure

```text
dataset/
├── Astrocytoma/
├── Carcinoma/
├── Ependymoma/
├── Glioblastoma/
├── Normal/
├── Oligodendroglioma/
└── Tuberculoma/
```

> The dataset itself is not included in this repository because of size and data-distribution considerations.

---

## ⚙️ Training Configuration

| Parameter       | Value                    |
| --------------- | ------------------------ |
| Backbone        | ResNet-18                |
| Transformer     | Transformer Encoder      |
| Input Size      | 224 × 224                |
| Optimizer       | AdamW                    |
| Scheduler       | OneCycleLR               |
| Batch Size      | 32                       |
| Epochs          | 50                       |
| Learning Rate   | 1 × 10⁻⁴                 |
| Loss            | BCE with Label Smoothing |
| Dropout         | 0.4                      |
| Mixed Precision | Yes                      |

These are the training settings reported for the research model.

---

## 📊 Results

The research model achieved approximately **98% training/validation accuracy** during training.

The reported test classification accuracy was:

### **96% Accuracy**

| Metric            |    Score |
| ----------------- | -------: |
| Accuracy          | **0.96** |
| Macro Precision   |     0.95 |
| Macro Recall      |     0.98 |
| Macro F1-Score    | **0.96** |
| Weighted F1-Score |     0.96 |

The reported test set contains **108 samples**.

---

## 🛠️ Technologies

* Python
* PyTorch
* Torchvision
* Deep Learning
* Computer Vision
* ResNet
* Vision Transformer
* Self-Attention
* AdamW
* OneCycleLR
* Mixed-Precision Training

---

## ▶️ Usage

### 1. Clone the repository

```bash
git clone https://github.com/<username>/<repository-name>.git
cd <repository-name>
```

### 2. Install dependencies

```bash
pip install torch torchvision tqdm numpy pandas scikit-learn matplotlib seaborn
```

### 3. Prepare the dataset

Place the MRI dataset according to the structure shown above.

### 4. Open the notebook

```text
notebooks/
└── Vit_Transformer_phase_1.ipynb
```

Run the notebook using **Jupyter Notebook** or **Google Colab**.

---

## 📈 Evaluation

The model is evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

The research evaluation shows strong diagonal performance in the confusion matrix, while Ependymoma and Oligodendroglioma showed comparatively more classification errors because of visual feature similarity.

---

## 📁 Repository Structure

```text
Brain-Tumor-Classification/
│
├── README.md
├── notebooks/
│   └── Vit_Transformer_phase_1.ipynb
│
├── models/
│   └── best_model.pth
│
├── results/
│   ├── confusion_matrix.png
│   └── training_curves.png
│
└── requirements.txt
```

---

## 🔬 Research

This project is based on the research work:

**"Hybrid CNN–Transformer Architecture for Multi-Label Brain Tumor Detection on T2-Weighted MRI"**

The research focuses on addressing the limitations of using CNNs or Transformers independently by combining their complementary strengths.

---

## 🔮 Future Work

* Train the complete Transformer architecture from scratch
* Implement the complete ResNet-18 + Transformer model
* Improve handling of class imbalance
* Add Grad-CAM and attention visualization
* Perform cross-dataset validation
* Develop a web-based inference application
* Compare CNN, ViT and Hybrid architectures

---

## 👨‍💻 Author


* **Marana Deepak**


---

## ⚠️ Disclaimer

This project is intended for **research and educational purposes only**.

It is **not a medical diagnostic system** and should not be used as a substitute for professional medical diagnosis.

---

## ⭐ Citation

If you use this project for research or academic work, please cite the associated research paper.

---
