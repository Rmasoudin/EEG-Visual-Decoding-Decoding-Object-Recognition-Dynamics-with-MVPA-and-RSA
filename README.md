# EEG-Visual-Decoding-Decoding-Object-Recognition-Dynamics-with-MVPA-and-RSA

Overview

This repository documents an advanced cognitive neuroscience project focused on analyzing Electroencephalography (EEG) data to decode the neural dynamics of visual object recognition, specifically distinguishing between face and dollhouse stimuli. The analysis employs a comprehensive multi-method approach, including traditional event-related potentials (ERP), time-frequency analysis, and state-of-the-art machine learning techniques like Multivariate Pattern Analysis (MVPA) and Representational Similarity Analysis (RSA) with deep neural network models (CORnet-S).

The goal is to provide insights into when and where visual category information emerges in the brain, and how these neural representations relate to computational models of the ventral visual stream.

Experimental Paradigm

The data originates from a Rapid Serial Visual Presentation (RSVP) experiment:

Stimuli: 18 images across two categories: faces (marked by trigger 496) and dollhouses (marked by trigger 436).

Presentation: Each stimulus was presented for 100 ms with a 200 ms Inter-Stimulus Interval (ISI).

EEG Acquisition: 64-channel EEG (10-10 system), sampled at 1000 Hz. Reference electrode: Fz.

Core Analysis Methods

The project utilizes five primary analytical modules to explore the data:

1. Preprocessing and Data Preparation

All raw EEG data must undergo a rigorous preprocessing pipeline before advanced analysis.

Epoching: Data is segmented (epoched) around stimulus onset, typically from -500 ms to +1500 ms.

Filtering: Application of online or offline filters (e.g., 0.1 Hz high-pass and 100 Hz low-pass) to remove drift and high-frequency noise.

Artifact Correction: Steps such as Independent Component Analysis (ICA) are applied to identify and remove artifacts (e.g., eye blinks, muscle movements).

Baseline Correction: Correction applied to normalize the signal based on the pre-stimulus period.

2. Event-Related Potentials (ERP) Analysis

The ERP analysis module focuses on the average temporal waveform evoked by the two categories.

Plotting: Generation of grand-average ERP plots for face vs. dollhouse stimuli.

Statistics: Execution of statistical comparisons (e.g., permutation tests or cluster-based statistics) to identify and interpret time points and electrodes showing significant differences between the two conditions.

3. Time-Frequency Analysis (TFA)

This method explores oscillatory activity in the EEG signal, analyzing how power changes across different frequency bands over time.

Transformation: Use of methods like wavelet or short-time Fourier transforms to generate time-frequency maps.

Comparison: Categorical comparison of time-frequency maps to discuss the role of different neural oscillations (e.g., alpha, beta, gamma) in perception and recognition.

4. Multivariate Pattern Analysis (MVPA)

MVPA uses machine learning classifiers to decode stimulus category from the spatio-temporal patterns of EEG activity. This allows for detection of subtle, distributed information often missed by ERP analysis.

Temporal MVPA: Classifier trained at each time point across all channels to map the temporal dynamics of information emergence.

Spatial MVPA: Classifier trained across the spatial pattern of electrodes, often aggregated over a specific time window.

Cross-Temporal Generalization (Optional): Training the classifier at one time point and testing its performance at all other time points to reveal the temporal stability of the neural code.

5. Representational Dissimilarity Matrix (RDM) and RSA

This module compares the neural representation structure to external models, specifically Deep Neural Networks (DNNs).

RDM Computation: Calculation of the Representational Dissimilarity Matrix (RDM) by computing the dissimilarity (e.g., 1 - correlation) between activation patterns for all stimulus pairs across time and/or channels.

Representational Similarity Analysis (RSA): Comparison (correlation) between the EEG-derived RDMs and model-derived RDMs (e.g., from different visual layers of the CORnet-S model, like V1, V2, V4, and IT).

Interpretation: Determining which visual layers of the CORnet-S model best correlate with the observed EEG dynamics, thus linking the temporal evolution of brain activity to the hierarchical structure of the ventral visual pathway.

📜 License

This repository is provided for research and academic use.
Please acknowledge this work appropriately if it informs your analyses
