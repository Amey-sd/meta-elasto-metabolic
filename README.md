# Meta-Elasto Metabolic Risk Assessment

An AI-driven diagnostic framework that utilizes high-frequency tissue vibrations (Elastography) combined with clinical metadata to assess metabolic and cardiovascular disease risks non-invasively.

## 🚀 Project Overview

Traditionally, assessing metabolic risk requires invasive blood tests and laboratory analysis. This project explores a **non-invasive alternative** by analyzing biological vibration signatures. Using data from a special sensor (Elastograph) recorded at 2,000Hz across 18 frequency channels, we use Deep Learning to extract "biological fingerprints" that correlate with medical risk factors.

### Key Objectives:
*   **Signal Discovery:** Identify vibration patterns in muscle and tissue that indicate metabolic stress.
*   **Multi-Modal Fusion:** Combine raw time-series sensor data with clinical metadata (Age, Sex, BMI, and Anatomical Location).
*   **Unsupervised Clustering:** Group patients into natural biological phenotypes using Deep Encoders and K-Means.

## 🧠 Model Architecture

The core of this repository is a **Multi-Modal Feature Encoder** designed to process heterogeneous data:

1.  **Signal Branch (1D-CNN):** A 1D Convolutional Neural Network that processes 18 channels of frequency data ($F1$ to $F18$). It acts as a set of trainable filters to detect the "texture" of tissue vibrations.
2.  **Context Branch (MLP):** A Multi-Layer Perceptron that processes clinical variables:
    *   Age
    *   Sex
    *   Waist Circumference
3.  **The Fusion Layer:** Merges the outputs of both branches into an 80-dimensional **Latent Vector** (the digital fingerprint).

## 📊 Methodology & Results

### Risk Scoring (Ground Truth)
We validate our AI's natural groupings against a **Medical Gold Standard** score (0-5), where one point is assigned for each clinical symptom:
*   High Fasting Glucose
*   High Triglycerides
*   High Blood Pressure
*   Low HDL Cholesterol
*   Central Obesity (Waist Circumference)

### Performance Highlights
*   **Clustering Alignment:** Achieved **80.74% accuracy** in aligning unsupervised AI clusters with medical risk scores (CNN+MLP folder).
*   **Healthy Population Precision:** The model identifies healthy/low-risk individuals with **88% precision**, making it an excellent negative screening tool.
*   **Visualization:** Utilizes PCA (Principal Component Analysis) to map the biological similarity between patients in a 2D space.

## 🛠️ Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Amey-sd/meta-elasto-metabolic.git
   ```
2. Install dependencies:
   ```bash
   pip install requirements.txt
   ```

## 💻 Usage

The pipeline is designed to process raw `.csv` files containing frequency signals.

## 📈 Future Work
*   **Signal Filtering:** Implementing bandpass filters (10Hz-450Hz) to further reduce sensor noise.
*   **Longitudinal Tracking:** Analyzing how a single patient's vibration signature moves across the PCA map after treatment.
*   **Cardiovascular Focus:** Isolating vascular-only risk factors to improve metabolic screening.

---
**Contributors:** [Amey-sd](https://github.com/Amey-sd)  
**Project Context:** Developed as part of the Meta-Elasto study focusing on non-invasive metabolic biomarkers which is a part of EPF Semester Project under clients from [Ultrasonic Lab, University of Granada](https://investiga.ugr.es/laboratorio-singular/ultrasonics-lab/).