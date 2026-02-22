# Task 2: Medical Report Generation using Visual Language Model (BLIP)

## Overview

This project implements automated medical report generation from chest X-ray images using a Vision-Language Model (VLM). 

The system integrates:
- A CNN classifier from Task 1 (pneumonia detection)
- A pre-trained BLIP image-captioning model
- Prompt conditioning using CNN prediction confidence

The final output is a structured radiology-style report generated for misclassified test images.

---

## Model Used

We use:

- **BLIP Image Captioning Model**
  - Model: `Salesforce/blip-image-captioning-base`
  - Framework: PyTorch
  - Execution device: CPU-only

Reference:
Li et al., *BLIP: Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation*, 2022.

---

## Project Structure
project/
│
├── task1_output/
│ ├── test_predictions.csv
│ └── misclassified_images.npz
│
├── task2_output/
│ └── generated_reports.csv
│
├── task2_notebook.ipynb
├── README.md
├── requirements.txt
└── DESCRIPTION.md


---

## Installation

This project runs in a Python 3.11 CPU environment.

Install dependencies:

```bash
pip install -r requirements.txt

How It Works

Load misclassified images from Task 1.

Convert grayscale arrays to PIL images.

Use CNN prediction probability to condition the prompt.

Generate a structured radiology-style report using BLIP.

Save results into task2_output/generated_reports.csv.

Output

Generated CSV file contains:

Image index

True label

CNN prediction

CNN probability

Generated report text

Notes

This implementation is CPU-compatible.

BLIP is a general vision-language model and not clinically validated.

Generated reports are for research purposes only.