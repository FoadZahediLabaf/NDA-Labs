# Network Data Analysis

A collection of Python notebooks applying data analysis and machine learning to network measurements, traffic classification, device identification, and optical-network performance.

Developed for the **Network Data Analysis** course at **Politecnico di Milano**.

**Python · NumPy · Pandas · scikit-learn · XGBoost · Matplotlib · Jupyter**

## Overview

The repository brings together six coursework topics involving different forms of network data.

The notebooks cover data loading, preprocessing, feature extraction, statistical analysis, model training, and evaluation. Each notebook contains the workflow for its corresponding problem.

## Projects

| Project | Main Focus | Notebook |
|---|---|---|
| Active Measurements | Network probing, measurement statistics, and visualization | [Open notebook](Active_Measurements/Active_Measurements.ipynb) |
| Application Flow Identification | Traffic-feature classification with logistic regression and XGBoost | [Open notebook](Application_flow_identification/Application_flow_identification.ipynb) |
| MAC De-randomization | Probe-request grouping and device-identification evaluation | [Open notebook](MAC_De-randomization/MAC_De-randomization.ipynb) |
| QoT Estimation | Optical-network regression and input-uncertainty analysis | [Open notebook](QoT_Estimation/QoT_estimation_v2026.ipynb) |
| Traffic Prediction | Network traffic prediction coursework | [Open notebook](Traffic_prediction/Traffic_prediction.ipynb) |
| Website Fingerprinting | Website classification from traffic features | [Open notebook](Website_Fingerprinting/Website_Fingerprinting.ipynb) |

## 1. Active Measurements

Analysis of network behavior using active measurements and external network information.

The notebook includes:

- Loading server information.
- Resolving network addresses.
- Collecting and processing measurements.
- Statistical summaries and visualizations.
- Geographical information processing.

Libraries include Pandas, NumPy, Matplotlib, Requests, GeoPy, and PythonPing.

Some cells perform live network measurements, so outputs can vary with connectivity, endpoint availability, and execution permissions.

## 2. Application Flow Identification

Classification of application traffic using features extracted from network flows.

The workflow includes:

- Dataset preparation and feature selection.
- Exploration of feature distributions.
- A stratified training/test split.
- Feature standardization.
- Hyperparameter evaluation.
- Logistic regression and XGBoost classification.
- Accuracy, precision, recall, F1-score, and confusion matrices.

The saved evaluation covers three application classes: **Skype**, **Dropbox**, and **Google**.

## 3. MAC De-randomization

Investigation of device identification when MAC addresses are randomized.

The notebook processes probe-request observations, groups related records, and evaluates how well the resulting groups correspond to device identities.

The analysis includes similarity-based grouping and clustering evaluation using V-measure.

## 4. Quality of Transmission Estimation

Prediction of optical-network Signal-to-Noise Ratio using network-related features.

The notebook compares:

- A linear-regression baseline.
- A multilayer perceptron implemented with `MLPRegressor`.

It also examines feature selection, prediction-error distributions, and the effect of uncertain fiber span lengths on the required safety margin.

### Recorded Test Results

The saved outputs for the corresponding full-feature experiment report:

| Model | Test R² | Test MSE |
|---|---:|---:|
| Linear Regression | 0.901 | 0.443 |
| Neural Network | 0.974 | 0.114 |

These values refer to the dataset split and settings used in the notebook. The predictions are expressed in dB, so the squared-error metric has units of dB².

The notebook also evaluates reduced-feature models and uncertainty levels of 5%, 10%, and 15% of the maximum span length.

## 5. Traffic Prediction

The traffic prediction notebook contains the coursework analysis for this topic.

Its data-loading cells, methodology, and saved outputs are available in:

```text
Traffic_prediction/Traffic_prediction.ipynb
```

## 6. Website Fingerprinting

Classification of websites using features extracted from network traffic traces.

The notebook includes:

- Traffic trace processing.
- Feature extraction and preprocessing.
- Label encoding and feature scaling.
- K-nearest-neighbor classification.
- Accuracy and confusion-matrix analysis.

## Repository Structure

```text
NDA-Labs/
├── Active_Measurements/
│   └── Active_Measurements.ipynb
├── Application_flow_identification/
│   └── Application_flow_identification.ipynb
├── MAC_De-randomization/
│   └── MAC_De-randomization.ipynb
├── QoT_Estimation/
│   ├── QoT_estimation_v2026.ipynb
│   ├── SNR_dataset_0.2dB_per_km.txt
│   └── SNR_dataset_0.25dB_per_km.txt
├── Traffic_prediction/
│   └── Traffic_prediction.ipynb
└── Website_Fingerprinting/
    └── Website_Fingerprinting.ipynb
```

## Getting Started

### Local Jupyter Environment

```bash
git clone https://github.com/FoadZahediLabaf/NDA-Labs.git
cd NDA-Labs

python3 -m venv .venv
source .venv/bin/activate

python -m pip install jupyter numpy pandas matplotlib scikit-learn xgboost
jupyter notebook
```

On Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

The command above installs the common analysis libraries. Individual notebooks may require additional dependencies.

For active measurements:

```bash
python -m pip install requests geopy pythonping
```

The website fingerprinting notebook also includes a Seaborn installation cell.

### Google Colab

The notebooks can also be opened in Google Colab.

Upload or connect the required datasets, adjust file paths where necessary, and follow the notebook's dependency and execution cells.

## Data and Execution

The notebooks use different datasets and working-directory assumptions.

Before running one:

1. Inspect its imports and data-loading cells.
2. Identify the required files and expected directory structure.
3. Supply any external coursework data.
4. Set the notebook's working directory or update its input paths.
5. Run the cells in order.

The QoT directory includes the two SNR text files used by its notebook. Other notebooks reference inputs that are not bundled as a complete dataset collection.

## Evaluation

The notebooks use metrics appropriate to their tasks:

| Task | Evaluation |
|---|---|
| Classification | Accuracy, precision, recall, F1-score, confusion matrices |
| Regression | R², mean squared error, maximum error |
| Device grouping | V-measure |
| Network measurements | Statistical summaries and visualizations |

Saved outputs document previous executions. Reproducing a result requires the corresponding input data, preprocessing, model settings, and library environment.

## Author and Academic Context

**Foad Zahedi Labaf**

MSc student in Computer Science and Engineering at Politecnico di Milano.

The exercises and notebook scaffolding originate from the course. The repository contains my implemented coursework solutions and analyses.

## Copyright

© 2026 Foad Zahedi Labaf. All rights reserved.

Third-party materials remain subject to their original licenses and terms.
