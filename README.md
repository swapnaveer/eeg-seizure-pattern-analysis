# EEG Seizure Pattern Analysis

## Overview

An exploratory analysis of publicly available CHB-MIT scalp EEG recordings, examining signal characteristics across annotated seizure and non-seizure periods. The analysis was used to prepare Tableau-ready data for an interactive dashboard showing EEG patterns over time, across channels, and by frequency band.

**Tableau dashboard:** [EEG Seizure Analysis — Signal Patterns](https://public.tableau.com/views/EEG_Seizure_Analysis_Dashboard/EEGSignalAnalysisSeizurePatterns?:language=en-US&publish=yes)

<img width="1101" height="700" alt="image" src="https://github.com/user-attachments/assets/62751f53-9293-41c2-bf0b-61ca0804779c" />


## Dataset and scope

- Dataset: [CHB-MIT Scalp EEG Database on PhysioNet](https://physionet.org/content/chbmit/1.0.0/)
- Subject: CHB01 (one subject)
- Recordings analyzed: eight selected recordings — chb01_01, chb01_03, chb01_04, chb01_15, chb01_16, chb01_18, chb01_21, and chb01_26
- Total recording duration: approximately 7.6 hours
- Sampling frequency: 256 Hz
- EEG channels: 23
- Windowing: non-overlapping 2-second windows
- Annotated seizure events: 7

## Analysis

The EEG recordings were filtered using a 1–40 Hz Butterworth band-pass filter and divided into non-overlapping 2-second windows. The feature set included:

- Signal mean, standard deviation, RMS, and line length
- Relative delta, theta, alpha, beta, and 30–40 Hz band power
- Spectral entropy

The resulting features and seizure annotations were organized into Tableau-ready files to support time-based and channel-based exploration.

## Dashboard

The Tableau dashboard provides an interactive way to examine signal patterns over time, across EEG channels, and by frequency band, with seizure and non-seizure periods represented using the available annotations.

## Repository contents

- `data/tableau_exports/eeg_window_features_tableau.csv` — compact Tableau-ready window-level feature table.
- `data/tableau_exports/seizure_events_tableau.csv` — annotated seizure event intervals.
- `data/tableau_exports/recording_coverage.csv` — recording coverage details.
- `data/tableau_exports/README_analysis_notes.txt` — dataset and feature-generation notes.
- `docs/EEG_Seizure_Analysis_CHBMIT_original_notebook.ipynb` — an earlier notebook artifact. It documents a smaller two-recording analysis and is included as supplementary material; it is not the exact eight-recording export pipeline used to create the Tableau-ready files.

## Important limitations

This is a descriptive, exploratory analysis of eight selected recordings from one subject, not the full CHB-MIT dataset. The 2-second channel-window observations are not independent subjects or independent seizure events. The analysis does not establish a validated seizure detector, clinical performance, or generalization to other individuals. No predictive performance claim should be inferred from the dashboard.

Raw EDF recordings are not included in this repository. Download the dataset from PhysioNet and review its terms before use.

## Data source and citation

Shoeb, A. (2009). Application of Machine Learning to Epileptic Seizure Onset Detection and Treatment. Massachusetts Institute of Technology. [CHB-MIT Scalp EEG Database, PhysioNet](https://physionet.org/content/chbmit/1.0.0/). DOI: [10.13026/C2K01R](https://doi.org/10.13026/C2K01R).

The dataset is distributed under the Open Data Commons Attribution License v1.0. Consult the dataset page for current terms and citation requirements.

