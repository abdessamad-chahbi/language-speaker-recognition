# 🗣️ Automatic Language & Speaker Recognition

**MFCC Feature Extraction + GMM Modeling**

## 📌 Overview

This project implements a system capable of automatically identifying both the **language** and the **speaker** from an audio sample. It leverages **MFCC (Mel-Frequency Cepstral Coefficients)** for feature extraction and **Gaussian Mixture Models (GMM)** for classification.

The system supports **5 Languages**:  
🇲🇦 **Arabic** | 🇬🇧 English | 🇫🇷 French | 🇯🇵 Japanese | 🇪🇸 Spanish  
and multiple speakers (male & female).

This work is structured in **two major parts**:

1. **Language Recognition**
2. **Speaker Recognition**

---

## 📘 Table of Contents

- Project summary  
- Highlights   
- Methodology 
- Experimental Results  
- Tech Stack  
- System Architecture 
- Future Improvements

---

## 🧩 Project summary

This project implements an audio classification pipeline based on **MFCCs and GMMs**. It contains two complementary modules:

- **Part I — Language Recognition:** classify audio into one of five languages (Arabic, English, French, Japanese, Spanish) using MFCCs + GMMs.  
- **Part II — Speaker Recognition:** reorganize MFCC feature files per speaker, then train per‑speaker GMMs to identify speakers.

## ✨ Highlights

- Feature extraction using MFCC (python_speech_features / librosa).  
- GMM classifiers tested with multiple component sizes (8, 16, 32, 64, 128).  
- Separate workflows for language classification and speaker identification.  
- Model persistence with joblib for later scoring.  
- Evaluation with accuracy, confusion matrices and score comparisons across GMM sizes.

---

## 🧠 Methodology (high level)

1. Preprocess audio → compute MFCC feature vectors per file.  
2. For language recognition (Part I):
   - Aggregate MFCCs for each language.
   - Train GMM models per language with different numbers of components.
   - Score test files against each language GMM and assign the language with highest likelihood.  
3. For speaker recognition (Part II):
   - Reorganize MFCCs by language → gender → speaker_id → train/test.
   - Train a GMM per speaker (varying components) and identify the best model per speaker.
   - Score test audio to find the most likely speaker model.  
4. Evaluate using accuracy and confusion matrix; analyze effect of GMM components on performance.

---

## ✅ Experimental Results

📌 Increasing the number of Gaussian components generally **improves performance**  
📌 Speaker recognition is more challenging → intra-speaker variability must be considered  

✔ High language classification accuracy  
✔ Robust speaker recognition using trained GMMs  
✔ Saved models for later deployment using `.joblib`  

---

## 🛠️ Tech Stack

| Category          | Tools                             |
| ----------------- | --------------------------------- |
| Programming       | Python                            |
| Speech Processing | MFCC, python_speech_features      |
| ML                | Gaussian Mixture Models (Sklearn) |
| Storage           | Joblib                            |
| Data Handling     | NumPy, Pandas                     |
| Visualization     | Matplotlib                        |
| Development       | Jupyter Notebook                  |

---

## 📊 System Architecture

```
Audio Input → MFCC Extraction → GMM Language Models → Predicted Language
                             ↓
                      GMM Speaker Models → Predicted Speaker
```

---

## 🚀 Future Improvements

* Add **HMM / GMM-UBM** for speaker modeling
* Expand dataset with more speakers & languages
* Integrate real-time microphone input
* Deploy as a GUI or Web Application
* Experiment with **Deep Learning-based embeddings (x-vectors, wav2vec2.0)**

---
