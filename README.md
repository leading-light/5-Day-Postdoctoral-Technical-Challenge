Automated Medical Report Generation using BLIP

This project implements an automated pipeline to generate structured radiology reports from medical images. It utilizes the Salesforce BLIP (Bootstrapping Language-Image Pre-training) model to interpret image features and condition them on classification probabilities to produce human-readable clinical findings.
📋 Overview

In this task, we bridge the gap between computer vision and clinical documentation. By taking misclassified or high-uncertainty images from a CNN classifier, we use a VLM to generate a detailed report. This serves as an "AI Second Opinion" or a draft for radiologists, focusing on:

    Findings: Descriptive analysis of the image features.

    Impression: The clinical conclusion based on the combined visual and statistical data.

🛠️ Tech Stack

    Model: Salesforce/blip-image-captioning-base

    Framework: PyTorch & Hugging Face Transformers

    Language: Python 3.11

    Environment: CPU-optimized for accessibility.

📂 Project Structure
Plaintext

.
├── task1_output/           # Input data from previous classification task
│   ├── test_predictions.csv 
│   └── misclassified_images.npz 
├── task2_output/           # Generated results
│   └── generated_reports.csv # Final CSV with text reports
├── report_generator.py     # Main generation script
└── requirements.txt        # Dependencies

🚀 Installation & Setup

    Clone the repository:
    Bash

    git clone https://github.com/your-username/medical-report-gen.git
    cd medical-report-gen

    Install requirements:
    Bash

    pip install torch torchvision transformers pillow matplotlib pandas numpy

⚙️ How it Works

The script follows a 4-step logic:

    Model Loading: Loads the BLIP processor and model in 8-bit or standard precision (CPU safe).

    Data Ingestion: Loads misclassified images and their associated CNN probabilities.

    Conditioned Prompting: Instead of simple captioning, the model is fed a prompt: "This X-ray has a pneumonia probability of [X]. Generate a structured report."

    Decoding: Converts the model's tensor outputs into a natural language string.

📊 Sample Output

The script generates a CSV and a visualization of the images. A sample output looks like this:

    Image Index 0: Label=Pneumonia, CNN Prob=0.85

    Report: "Findings: There is increased opacity in the lower lobes. Impression: Findings are consistent with bacterial pneumonia."

⚠️ Limitations & Disclaimer

    This tool is for research purposes only.

    The reports generated are based on a base-model VLM and should not be used for actual clinical diagnosis without expert verification.
