# EEG Seizure Pattern Analysis

**Dataset:** CHB-MIT Scalp EEG Database (PhysioNet, version 1.0.0)  
**Research question:** How do time- and frequency-domain features of scalp EEG vary across annotated seizure and non-seizure periods in selected recordings?

In this project, I explored signal patterns in selected scalp EEG recordings from one subject. The analysis examines signal amplitude, variability, and frequency-band power across annotated seizure and non-seizure periods. The resulting data are organized for visualization in Tableau.

## 1. Selected recordings and data

The analysis uses eight recordings from subject CHB01:

- `chb01_01.edf`
- `chb01_03.edf`
- `chb01_04.edf`
- `chb01_15.edf`
- `chb01_16.edf`
- `chb01_18.edf`
- `chb01_21.edf`
- `chb01_26.edf`

The selected recordings cover approximately 7.6 hours. The recordings contain 23 EEG channels and use a 256 Hz sampling rate. Seizure timing is taken from the subject summary provided with the dataset.

The full CHB-MIT dataset is larger; this project uses only the selected recordings listed above.

## 2. Preprocessing and feature extraction

We apply a 1–40 Hz Butterworth band-pass filter and divide the recordings into non-overlapping 2-second windows.

For each channel and window, we calculate:
- mean and standard deviation of amplitude;
- root mean square (RMS);
- line length, a simple measure of signal variation;
- relative band power for delta, theta, alpha, beta, and 30–40 Hz bands;
- spectral entropy.

The seizure label is based on overlap with the annotated seizure intervals. The 30–40 Hz feature represents only this portion of the conventional gamma band.

## 3. Tableau visualization

The window-level feature data and seizure event intervals are prepared for use in Tableau. The dashboard supports exploration of signal patterns over time, across EEG channels, and by frequency band.

**Tableau dashboard:** [EEG Seizure Analysis — Signal Patterns](https://public.tableau.com/views/EEG_Seizure_Analysis_Dashboard/EEGSignalAnalysisSeizurePatterns?:language=en-US&publish=yes)

The dashboard is intended for descriptive exploration. The project does not report predictive performance as evidence of seizure detection.

<img width="1101" height="700" alt="image" src="https://github.com/user-attachments/assets/1abd9b0b-6ef5-415b-926d-9266d9c3243a" />

## 4. Limitations

- The analysis uses eight selected recordings from one subject, not the full CHB-MIT dataset.
- The observations are channel-window measurements and are not independent subjects or independent seizure events.
- A single subject does not support conclusions about performance across individuals.
- The extracted features describe selected signal characteristics and do not establish reliable seizure biomarkers.

This work is an independent exploratory analysis of a publicly available EEG dataset. It is intended to examine signal patterns and support visualization.

## 5. Files

- `data/tableau_exports/` — Tableau-ready data tables and recording notes.

## 6. Dataset citation

Shoeb, A. H. (2009). *Application of Machine Learning to Epileptic Seizure Onset Detection* [PhD thesis, Massachusetts Institute of Technology]. The CHB-MIT Scalp EEG Database is available via PhysioNet: [https://doi.org/10.13026/C2K01R](https://doi.org/10.13026/C2K01R).

Database acknowledgement: Children’s Hospital Boston and the Massachusetts Institute of Technology. Cite the dataset and comply with its Open Data Commons Attribution License v1.0.
