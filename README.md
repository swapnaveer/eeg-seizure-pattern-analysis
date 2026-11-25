# EEG Seizure Pattern Analysis

**Dataset:** CHB-MIT Scalp EEG Database (PhysioNet, version 1.0.0)  
**Primary question:** How do time- and frequency-domain features of scalp EEG vary across annotated seizure and non-seizure periods in selected recordings?

In this project, I explored signal patterns in selected scalp EEG recordings from one subject. The analysis examines signal amplitude, variability, and frequency-band power across annotated seizure and non-seizure periods. The resulting data are organized for visualization in Tableau.

This is an educational, exploratory analysis—not a clinical device, diagnostic tool, or validated seizure detector. It uses a limited subset of one subject's recordings. Results cannot establish generalization to other people, hospitals, recording systems, or clinical settings.

## Selected recordings and data

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

## Preprocessing and feature extraction

We apply a 1–40 Hz Butterworth band-pass filter and divide the recordings into non-overlapping 2-second windows.

For each channel and window, we calculate:
- mean and standard deviation of amplitude;
- root mean square (RMS);
- line length, a simple measure of signal variation;
- relative band power for delta, theta, alpha, beta, and 30–40 Hz bands;
- spectral entropy.

The seizure label is based on overlap with the annotated seizure intervals. The 30–40 Hz feature represents only this portion of the conventional gamma band.

## Tableau visualization

The window-level feature data and seizure event intervals are prepared for use in Tableau. The dashboard supports exploration of signal patterns over time, across EEG channels, and by frequency band.

**Tableau dashboard:** [EEG Seizure Analysis — Signal Patterns](https://public.tableau.com/views/EEG_Seizure_Analysis_Dashboard/EEGSignalAnalysisSeizurePatterns?:language=en-US&publish=yes)

<img width="1101" height="700" alt="image" src="https://github.com/user-attachments/assets/62751f53-9293-41c2-bf0b-61ca0804779c" />


## Dataset and scope
dda5017bb1767764c5d05da030080d5c7b2eadc5


## Files

- `data/tableau_exports/` — Tableau-ready data tables and recording notes.
- `docs/EEG_Seizure_Analysis_CHBMIT_Final.ipynb` — Jupyter notebook documenting the EEG preprocessing, feature extraction, exploratory analysis, and classification.


## Repository contents

- `data/tableau_exports/eeg_window_features_tableau.csv` — compact Tableau-ready window-level feature table.
- `data/tableau_exports/seizure_events_tableau.csv` — annotated seizure event intervals.
- `data/tableau_exports/recording_coverage.csv` — recording coverage details.
- `data/tableau_exports/README_analysis_notes.txt` — dataset and feature-generation notes.
- `docs/EEG_Seizure_Analysis_CHBMIT_Final.ipynb` — Jupyter notebook documenting the EEG preprocessing, feature extraction, exploratory analysis, and classification.

## Limitations

- The analysis uses eight selected recordings from one subject, not the full CHB-MIT dataset.
- The observations represent individual channel-window measurements and should not be treated as independent subjects or seizure events.
- The analysis is limited to one subject and does not establish whether the observed patterns apply to other individuals.
- The extracted features describe selected signal characteristics and do not establish reliable seizure biomarkers.

This work is an independent exploratory analysis of a publicly available EEG dataset. It is intended to examine signal patterns and support visualization.

## Data source and citation

Guttag, J. (2010). *CHB-MIT Scalp EEG Database* (version 1.0.0). PhysioNet. https://doi.org/10.13026/C2K01R

Shoeb, A. H. (2009). *Application of Machine Learning to Epileptic Seizure Onset Detection and Treatment* [PhD thesis, Massachusetts Institute of Technology].

The dataset is distributed under the Open Data Commons Attribution License v1.0. Refer to the [PhysioNet dataset page](https://physionet.org/content/chbmit/1.0.0/) for access and usage terms.
