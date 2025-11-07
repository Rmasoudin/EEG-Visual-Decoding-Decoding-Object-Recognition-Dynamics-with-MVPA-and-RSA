# EEG-Visual-Decoding-Decoding-Object-Recognition-Dynamics-with-MVPA-and-RSA

Decoding Object Recognition Dynamics with MVPA and RSA

This project investigates how the human brain encodes and processes visual information through **non-invasive EEG recordings**.  
It focuses on understanding **object recognition dynamics** in the **ventral visual stream** by analyzing event-related potentials (ERP), oscillatory activity (TFA), and multivariate representational patterns (MVPA/RSA).

---

## 📘 Overview

The project analyzes **scalp EEG data** recorded during a **Rapid Serial Visual Presentation (RSVP)** paradigm.  
By combining **time-domain**, **frequency-domain**, and **multivariate analyses**, the goal is to characterize how neural representations of object categories (Faces vs Dollhouses) evolve over time and relate to the hierarchical visual features extracted by deep neural networks such as **CORnet-S**.

This repository includes:
- End-to-end **EEG preprocessing** (filtering, ICA artifact correction, epoching)  
- **ERP analysis** and statistical testing (cluster-based permutation tests)  
- **Time–Frequency Analysis (TFA)** for oscillatory characterization  
- **Multivariate Pattern Analysis (MVPA)** for time-resolved and spatial decoding  
- **Representational Similarity Analysis (RSA)** linking EEG activity to DNN layers (V1, V2, V4, IT)

---

## 🧩 Experimental Paradigm and Data Description

The analysis uses EEG data collected during a **Rapid Serial Visual Presentation (RSVP)** experiment.

**EEG Acquisition**
- 64-channel EEG using the international 10–10 system  
- Sampling Rate: **1000 Hz**  
- Online Reference: **Fz electrode**

**Stimuli and Conditions**
- 18 images across two categories:  
  - **Faces** (Trigger 496)  
  - **Dollhouses** (Trigger 436)  
- Presentation: 100 ms per image  
- Inter-Stimulus Interval (ISI): 200 ms  

**Epoching and Time Window**
- Epochs extracted from **−500 ms to +1500 ms** relative to stimulus onset  
- Baseline correction applied using the pre-stimulus interval (−500–0 ms)

---

## ⚙️ Pipeline Overview

The repository is structured into modular analysis stages.  
Each stage can be executed independently or combined for full-pipeline processing.

---

### 1️⃣ Signal Preprocessing and Artifact Correction

**Objective:**  
Prepare raw EEG data for reliable ERP and MVPA analysis.

**Steps:**
1. **Filtering**  
   - Apply high-pass (0.1 Hz) and low-pass (100 Hz) filters to remove slow drift and high-frequency noise.  
2. **Epoching & Baseline Correction**  
   - Segment continuous EEG into epochs (−500 to +1500 ms) per trial.  
   - Apply baseline correction using the pre-stimulus interval.  
3. **Artifact Correction (ICA)**  
   - Use Independent Component Analysis to remove ocular (EOG) and muscular (EMG) artifacts.  
4. **Bad Channel Interpolation**  
   - Detect and interpolate flat or noisy channels as necessary.  

---

### 2️⃣ Event-Related Potential (ERP) Analysis

**Objective:**  
Quantify the average time-locked neural response and identify category-selective effects.

**Methods:**
- **ERP Computation**  
  - Compute grand-average ERPs for each condition (Faces vs Dollhouses) across trials.  
- **Visualization**  
  - Plot ERP waveforms across representative electrodes (e.g., occipital and temporal regions).  
- **Statistical Comparison**  
  - Use **cluster-based permutation tests** to detect significant time–channel clusters differentiating categories.

---

### 3️⃣ Time–Frequency Analysis (TFA)

**Objective:**  
Characterize oscillatory dynamics associated with visual processing.

**Steps:**
1. **Time–Frequency Decomposition**  
   - Use **Morlet wavelets** or **Short-Time Fourier Transform** to compute power spectra over time.  
2. **Frequency Bands**  
   - Analyze alpha (8–12 Hz), beta (13–30 Hz), and gamma (30–80 Hz) bands.  
3. **Comparison Across Conditions**  
   - Compute difference maps (Faces − Dollhouses) to identify category-related oscillatory modulations.  

---

### 4️⃣ Multivariate Pattern Analysis (MVPA)

**Objective:**  
Decode visual categories from distributed spatiotemporal EEG patterns using machine learning.

**Steps:**
1. **Temporal Decoding**  
   - Train a classifier (e.g., SVM) at each time point across all electrodes.  
   - Assess dynamic onset and duration of category information.  
2. **Spatial Decoding**  
   - Train a classifier on spatial patterns averaged over specific time windows (e.g., P1, N170, P300).  
3. **Cross-Temporal Generalization**  
   - Train at time *t₁* and test at time *t₂* to assess the temporal stability of neural representations.  

---

### 5️⃣ Representational Geometry and RSA

**Objective:**  
Relate EEG representational structure to computational models of vision.

**Steps:**
1. **RDM Construction**  
   - Compute pairwise dissimilarities (1 − correlation) between multichannel EEG responses for all stimuli.  
2. **Model RDMs**  
   - Derive visual layer representations from **CORnet-S** (V1, V2, V4, IT).  
3. **Representational Similarity Analysis (RSA)**  
   - Correlate time-resolved EEG RDMs with model RDMs to identify when each visual layer best aligns with neural dynamics.  
4. **Interpretation**  
   - Examine the temporal evolution of hierarchical visual representation across the ventral stream.  

---

## 🧮 Tools and Dependencies
- **EEG:** `EEGLAB`
- **Python:** `mne`, `numpy`, `scipy`, `scikit-learn`, `matplotlib`, `seaborn`, `pandas`  
- **Machine Learning:** `scikit-learn` for SVM-based decoding  
- **Visualization:** Matplotlib / Seaborn for ERP, TFA, and decoding plots  

---

## 📊 Example Outputs

- Grand-average **ERP plots** for Face vs Dollhouse stimuli  
- **Time–Frequency maps** showing power changes across conditions  
- **Decoding accuracy curves** over time with significance thresholds  
- **Cross-temporal generalization matrices**  
- **RSA time courses** showing correlations with DNN layers  

---


## 📜 License

This repository is provided for research and academic use.  
Please acknowledge this work appropriately if it informs your analyses.

---

> *“The dynamics of neural representations reveal not just what we see — but when and how the brain recognizes it.”*
