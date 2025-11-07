# EEG-Visual-Decoding-Decoding-Object-Recognition-Dynamics-with-MVPA-and-RSA

📘 Overview

The project investigates non-invasive electrophysiological recordings obtained from the scalp during a rapid visual processing task.
By analyzing time-domain (ERP), frequency-domain (TFA), and multivariate patterns (MVPA/RSA), the goal is to understand how the ventral visual stream encodes object categories and how this neural activity relates to the hierarchical features learned by deep neural networks like CORnet-S.

This repository includes:

End-to-end EEG preprocessing (filtering, artifact correction, epoching).

ERP analysis with statistical comparison (cluster-based permutation tests).

Time-Frequency Analysis (TFA) to characterize neural oscillations.

Multivariate Pattern Analysis (MVPA) for time-resolved and spatial decoding.

Representational Similarity Analysis (RSA) to link EEG dynamics to CNN visual layers (V1, V2, V4, IT).

Experimental Paradigm and Data Description

The analysis uses data recorded during a Rapid Serial Visual Presentation (RSVP) experiment.

Electrophysiological Data: 64-channel EEG (10-10 system).

Sampling Rate: 1000 Hz.

Stimuli: 18 images across two categories: Faces (Trigger 496) and Dollhouses (Trigger 436).

Epoching: Extracted time windows from -500 ms to +1500 ms relative to stimulus onset.

Presentation Details: 100 ms duration per stimulus with a 200 ms Inter-Stimulus Interval (ISI).

Reference: Fz electrode used as the online reference.

⚙️ Pipeline Overview

The repository is structured into modular stages, designed for a complete analysis of the EEG data.

1️⃣ Signal Preprocessing and Artifact Correction

Objective:
Prepare raw EEG signals for reliable statistical and multivariate analysis.
Steps:
Filtering
Apply required online or offline filters (e.g., 0.1 Hz high-pass and 100 Hz low-pass) to remove drift and line noise.
Epoching and Baseline Correction
Segment continuous data into trials (epochs) from -500 ms to +1500 ms.
Apply baseline correction using the pre-stimulus period.
Artifact Correction (ICA)
Use Independent Component Analysis (ICA) to identify and remove ocular (EOG) and muscular (EMG) artifacts.
Bad Channel Interpolation
Identify and interpolate noisy or flat channels if necessary.

2️⃣ Event-Related Potential (ERP) Analysis

Objective:
Quantify the average time-locked neural response and identify significant differences between categories.
Steps:
ERP Plotting
Compute and plot grand-average ERPs for Face vs. Dollhouse stimuli across key scalp regions.
Statistical Comparison
Conduct statistical tests (e.g., cluster-based permutation tests) to highlight time periods and electrodes with significant categorical differences.

3️⃣ Time-Frequency Analysis (TFA)

Objective:
Analyze power changes across different frequency bands (oscillations) over time.
Steps:
Time-Frequency Transformation
Use wavelet or short-time Fourier transforms to compute power maps (Time x Frequency) for each category.
Comparison and Interpretation
Compare TFA maps across faces and dollhouses. Discuss observed effects in context of established neural oscillations (e.g., alpha, beta, gamma) and their role in perception.

4️⃣ Multivariate Pattern Analysis (MVPA)

Objective:
Decode stimulus category from the full spatio-temporal pattern of EEG activity using machine learning.
Steps:
Temporal MVPA
Train and test an SVM/classifier at each individual time point across all channels to map the dynamic onset and duration of decoding accuracy.
Spatial MVPA
Train a classifier using electrode patterns, often aggregated over specific time windows (e.g., P1, N170, P300).
Cross-Temporal Generalization (Optional)
Train at time $t_1$ and test at time $t_2$ to assess the stability and evolution of the neural code over time.

5️⃣ Representational Dissimilarity Matrix (RDM) and RSA

Objective:
Compare the structure of the neural representation geometry with theoretical and computational models.
Steps:
RDM Construction
Compute the Representational Dissimilarity Matrix (RDM) by calculating the dissimilarity (e.g., 1 minus correlation) between the multi-channel EEG patterns for every pair of stimuli.
Representational Similarity Analysis (RSA)
Correlate the time-resolved EEG RDMs with model RDMs derived from features of different visual layers of the CORnet-S deep neural network (V1, V2, V4, IT).
Interpretation
Determine which DNN layers best predict the human EEG representation structure over time, linking neural dynamics to hierarchical visual processing.

🧮 Tools and Dependencies

Python: MNE (for core EEG processing), scikit-learn (for MVPA classification), numpy, scipy, matplotlib/seaborn (for visualization). Specialized toolboxes may be used for RSA and time-frequency analysis.

📜 License

This repository is provided for research and academic use.
Please acknowledge this work appropriately if it informs your analyses.
