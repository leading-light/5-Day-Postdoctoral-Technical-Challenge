📄 README.md
# 🩺 Pneumonia Detection using CNN (PneumoniaMNIST)

This project implements a complete deep learning pipeline for pneumonia classification using the PneumoniaMNIST dataset from MedMNIST.

The implementation includes:

- Reproducible training setup
- Dataset normalization (mean/std computation)
- Data augmentation
- Custom CNN architecture
- Learning rate scheduling
- Early stopping
- Comprehensive evaluation metrics
- ROC curve visualization
- Failure case analysis
- Export of outputs for downstream tasks (Task 2)

---

## 📊 Dataset

Dataset: **PneumoniaMNIST**  
Source: MedMNIST  
Image size: 28×28 grayscale  
Classes:
- 0 → Normal
- 1 → Pneumonia

The dataset is automatically downloaded via:

```python
from medmnist import PneumoniaMNIST
🧠 Model Architecture

A lightweight CNN optimized for 28×28 grayscale images:

3 Convolutional blocks:

Conv2D + BatchNorm + ReLU + MaxPool

Fully connected layer (256 units)

Dropout (0.5)

Output layer (2 classes)

Weight initialization:

He initialization (Conv layers)

Xavier initialization (Linear layers)

⚙️ Training Configuration

Optimizer: Adam

Learning rate: 1e-3

Weight decay: 1e-4

Scheduler: ReduceLROnPlateau

Early stopping patience: 7 epochs

Batch size: 64

Epochs: 30

Loss function: CrossEntropyLoss

📈 Evaluation Metrics

The model is evaluated on the test set using:

Accuracy

Precision

Recall

F1-score

ROC-AUC

Confusion analysis

ROC Curve visualization

Misclassified sample visualization

📂 Output Files (for Task 2 integration)

After evaluation, the following files are saved:

task1_output/
│
├── test_predictions.csv
└── misclassified_images.npz
test_predictions.csv

Contains:

image_index

true label

predicted label

pneumonia probability

misclassified_images.npz

Contains:

images (numpy array)

labels

preds

probs

These files are designed for downstream medical report generation tasks.

🚀 How to Run

Install dependencies:

pip install -r requirements.txt

Run the notebook:

Task1_CNN_Pneumonia.ipynb

The dataset will download automatically.

💻 Hardware

CPU compatible

GPU optional (automatically detected)