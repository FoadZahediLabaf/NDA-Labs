# Network Data Analysis

Python notebooks exploring network measurements, traffic classification, device identification, optical-network regression, and traffic forecasting.

Developed for the **Network Data Analysis** course at **Politecnico di Milano**.

**Python · NumPy · Pandas · scikit-learn · XGBoost · TensorFlow/Keras · Matplotlib · Jupyter**

## Overview

The repository contains six coursework notebooks. Each addresses a networking problem through data preparation, feature extraction, statistical analysis, machine learning, or experimental evaluation.

The notebooks include source code and saved outputs from earlier executions. Their datasets, dependencies, and execution environments differ.

## Projects

| Project | Main Focus | Notebook |
|---|---|---|
| Active Measurements | ICMP measurements, IP geolocation, and the relationship between RTT and distance | [Open notebook](Active_Measurements/Active_Measurements.ipynb) |
| Application Flow Identification | Three-class traffic classification using logistic regression and XGBoost | [Open notebook](Application_flow_identification/Application_flow_identification.ipynb) |
| MAC De-randomization | Online probe-request clustering and device-count estimation | [Open notebook](MAC_De-randomization/MAC_De-randomization.ipynb) |
| QoT Estimation | Optical-path SNR regression, modulation margins, and span-length uncertainty | [Open notebook](QoT_Estimation/QoT_estimation_v2026.ipynb) |
| Traffic Prediction | ANN and LSTM forecasting with a capacity-provisioning cost experiment | [Open notebook](Traffic_prediction/Traffic_prediction.ipynb) |
| Website Fingerprinting | Packet-trace features, cumulative representations, and k-NN classification | [Open notebook](Website_Fingerprinting/Website_Fingerprinting.ipynb) |

## 1. Active Measurements

The notebook generates a list of Debian mirror hostnames and studies the relationship between geographical distance and network round-trip time.

Its workflow includes DNS resolution, IP geolocation, repeated ICMP probes, average RTT filtering, geodesic distance calculation, and a linear RTT-distance fit.

This experiment performs live network requests. Results depend on the execution host, network conditions, target availability, and permissions for ICMP probing.

## 2. Application Flow Identification

Classification of **Skype**, **Dropbox**, and **Google** traffic using traffic-flow features.

The notebook implements data cleaning, feature-distribution plots, stratified train/test splitting, cross-validation for hyperparameter evaluation, and model comparison. Logistic regression uses standardized features; XGBoost uses unscaled features.

Evaluation includes accuracy, weighted precision/recall/F1, classification reports, and confusion matrices.

## 3. MAC De-randomization

Probe requests are processed in timestamp order and assigned to clusters according to a minimum number of matching features.

The notebook compares feature-match thresholds on the lecture dataset, applies the selected threshold to challenge subsets containing different numbers of devices, and estimates the number of device clusters in an unlabeled dataset.

Evaluation includes V-measure, majority-label disagreement, and the number of clusters produced.

## 4. Quality of Transmission Estimation

Prediction of optical-path SNR using features describing fiber spans, path length, and interference conditions.

The notebook compares linear regression with a multilayer perceptron. It explores SGD and Adam optimization, feature selection, modulation-format margins, and the effect of uncertain span lengths on prediction accuracy.

Evaluation uses regression metrics and prediction-error distributions, with additional analysis of input uncertainty and modulation decisions.

## 5. Traffic Prediction

Forecasting hourly telecom traffic for spatial cells in Milan using November–December 2013 data.

The notebook compares:

- A feed-forward artificial neural network using calendar and lagged-traffic features.
- An LSTM using sequences of past traffic observations.

The workflow includes hourly aggregation, feature preparation, chronological train/test splitting, normalization, and a temporal gap in the LSTM split.

Evaluation includes MSE, MAE, R², prediction plots, and an over-/under-provisioning cost experiment with different cost weights.

## 6. Website Fingerprinting

Classification of websites from captured TCP/443 traffic.

The notebook collects traces with `tcpdump` and `curl`, extracts packet fields with `tshark`, and compares two feature representations:

- Bidirectional packet-size, volume, and inter-arrival-time statistics.
- An interpolated representation of cumulative signed packet sizes.

It compares k-NN settings, plots confusion matrices, and evaluates the selected statistical-feature classifier on a separately collected follow-up capture set. The notebook notes that this follow-up was collected a few hours after the original captures.

The capture cells assume a Linux-style environment, including `apt-get` and the `eth0` interface.

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

## Environment Setup

### Common Analysis Libraries

```bash
git clone https://github.com/FoadZahediLabaf/NDA-Labs.git
cd NDA-Labs
python3 -m venv .venv
source .venv/bin/activate
python -m pip install jupyter numpy pandas matplotlib scikit-learn xgboost
jupyter notebook
```

On Windows PowerShell, activate the environment with:

```powershell
.venv\Scripts\Activate.ps1
```

### Notebook-Specific Requirements

| Notebook | Additional requirements |
|---|---|
| Active Measurements | `requests`, `geopy`, `pythonping`; network access and ICMP permissions |
| Traffic Prediction | TensorFlow/Keras; model plotting uses `plot_model` and its visualization dependencies |
| Website Fingerprinting | `tcpdump`, `tshark`, `curl`, packet-capture permissions, and an appropriate network interface; its setup cell also installs Seaborn |

For active measurements:

```bash
python -m pip install requests geopy pythonping
```

For traffic prediction, install TensorFlow in a supported Python environment. The repository does not pin a complete shared dependency environment.

## Data Requirements

| Notebook | Input location or generation |
|---|---|
| Active Measurements | Creates `servers.csv` in its first cell and collects live measurements |
| Application Flow Identification | Requires external `22_apps_flow_features.csv` |
| MAC De-randomization | References `/content/lecture_dataset`, `/content/challenge_dataset`, and `/content/MAC_derand_unlabelled-challenge.csv` |
| QoT Estimation | Includes two SNR text files; the current code loads `SNR_dataset_0.25dB_per_km.txt` |
| Traffic Prediction | Requires external `dataset/short_milan_processed_2013-MM-DD.txt` files |
| Website Fingerprinting | Generates `csv_captures/` and `csv_captures_day2/` through its capture cells |

Set the working directory and input paths for the notebook being used. For QoT, run with the `QoT_Estimation` directory as the working directory or update the dataset paths.

Google Colab can be used where the notebook's dependencies, input files, and network capabilities are available.

## Execution Notes

Saved outputs reflect earlier executions and can vary with data, configuration, and execution conditions. Each notebook has its own setup requirements.

Two initialization issues need attention before a fresh Run All:

- **Application Flow Identification:** call `create_dataset(DATASET_FILE, APP_NAMES)` and assign its return value to `homework_dataset_file` before the feature-distribution cell.
- **QoT Estimation:** the standalone `new_y = np.array(new_snr_values)` cell appears before `new_snr_values` is loaded; the following cell already performs this initialization in the correct order.

## Academic Context

The exercises and notebook scaffolding originate from the course. This repository contains my implemented coursework solutions and analyses.

## Author

**Foad Zahedi Labaf**

## Copyright

© 2026 Foad Zahedi Labaf. All rights reserved.

Third-party materials remain subject to their original licenses and terms.
