# Quantum Machine Learning for Sleep Apnea Detection

## 📌 Project Overview
Sleep apnea is a serious medical condition characterized by repeated interruptions in breathing during sleep, which can lead to cardiovascular disease, stroke, and chronic fatigue if left untreated.  
The standard diagnostic method, **Polysomnography (PSG)**, is accurate but expensive, intrusive, and time-consuming.

This project explores a **Quantum Machine Learning (QML)** approach for automated detection of sleep apnea using **EEG (Electroencephalogram) signals**.  
By combining classical signal processing with quantum machine learning, we aim to build a smarter, faster, and potentially more accurate method for detection.

---

## ⚙️ How It Works
### Input
- EEG signals from the **PhysioNet MIT-BIH Polysomnographic Database (SLPDB)**.
- Specifically, signals from the **C3-O1 EEG channel** sampled at 100–250 Hz.

### Processing Pipeline
1. **Data Preprocessing**
   - Noise removal and filtering of EEG signals.  
   - Segmentation into 30-second windows.  
   - Frequency-domain transformation (FFT) into brainwave bands: Delta, Theta, Alpha, Beta, Gamma.  

2. **Feature Extraction**
   - Statistical features: mean, standard deviation, skewness, kurtosis, RMS.  
   - Bandpower features: Delta, Theta, Alpha, Beta, Gamma.  
   - Ratios and peak frequencies.  

3. **Feature Selection**
   - Implemented with **Quantum Approximate Optimization Algorithm (QAOA)** to identify the most relevant features.  

4. **Classification Models**
   - **Classical Machine Learning**: Support Vector Machine (SVM) with RBF kernel.  
   - **Quantum Machine Learning**: Quantum Support Vector Machine (QSVM) using:
     - Qiskit (Quantum Kernel Estimation with ZZFeatureMap).  
     - PennyLane (AngleEmbedding + entanglement layers).  

5. **Output**
   - Binary classification: **Apnea** vs. **Normal sleep segment**.  

---

## 🖥️ How to Run
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name

---
### 📂 Dataset

- **Source**: [MIT-BIH Polysomnographic Database (SLPDB) on PhysioNet](https://www.physionet.org/content/slpdb/)  

#### Contents
- `.dat` → raw EEG and physiological signals  
- `.hea` → header info (signal labels, sampling rate, calibration)  
- `.st` → annotations (sleep stages & apnea events)  

⚠️ The dataset is **too large** to be stored in this repository.  

To download, run:
```bash
wget -r -N -c -np https://physionet.org/files/slpdb/1.0.0/
