# Network Data Analysis Coursework

This repository contains my Python notebooks and coursework solutions for the **Network Data Analysis** course at Politecnico di Milano.

The work focuses on applying data analysis and machine learning techniques to networking-related problems. The assignments cover data preprocessing, feature extraction, visualization, supervised learning, clustering, regression, and performance evaluation.

## Start here

| Project | Focus | Notebook |
|---|---|---|
| Optical-network QoT estimation | Neural-network regression, a linear baseline, and input uncertainty | [QoT estimation](QoT_Estimation/QoT_estimation_v2026.ipynb) |
| Application flow identification | Feature engineering, logistic regression, and XGBoost | [Flow classification](Application_flow_identification/Application_flow_identification.ipynb) |
| Traffic prediction | Network traffic prediction coursework | [Traffic prediction](Traffic_prediction/Traffic_prediction.ipynb) |
| MAC de-randomization | Grouping probe requests and device identification | [MAC analysis](MAC_De-randomization/MAC_De-randomization.ipynb) |
| Active measurements | Network measurement statistics and visualization | [Active measurements](Active_Measurements/Active_Measurements.ipynb) |
| Website fingerprinting | Traffic features and classification | [Website fingerprinting](Website_Fingerprinting/Website_Fingerprinting.ipynb) |

### Example result: QoT regression

Saved notebook outputs report **test R² = 0.974** for the neural-network model, compared with **0.901** for the linear-regression baseline in the corresponding experiment. These are results from that notebook's dataset split and configuration, separate from the private EDFA project. See the notebook's code and outputs for the experiment details and input-uncertainty analysis.

## Running the notebooks

Open the linked notebooks in Jupyter or Google Colab. Dependencies vary by notebook and include NumPy, Pandas, Matplotlib, scikit-learn, and XGBoost for flow classification.

Some notebooks require external coursework data and local input paths. The QoT folder includes two SNR text files; other required datasets may need to be supplied separately. Check the data-loading cells before running. This coursework collection does not have a single automated setup command.

## Repository Structure

```text
.
├── Active_Measurements/
├── Application_flow_identification/
├── MAC_De-randomization/
├── QoT_Estimation/
├── Traffic_prediction/
└── Website_Fingerprinting/
```

## Assignments

### Active Measurements

This assignment focuses on the analysis of network measurements collected through active probing. The code processes measurement data, extracts useful statistics, and visualizes network behavior in order to better understand performance-related characteristics.

Main topics covered:

- Active network measurements
- Data preprocessing
- Statistical analysis
- Visualization of network metrics

### Application Flow Identification

This assignment applies machine learning methods to classify application flows using traffic-level features. The workflow includes dataset cleaning, feature preparation, model training, and evaluation of classification performance.

Main topics covered:

- Network traffic flow analysis
- Feature extraction and preprocessing
- Supervised learning
- Multi-class classification
- Model evaluation

### MAC De-randomization

This assignment studies the problem of recognizing devices when MAC address randomization is used. The implemented solution follows a clustering-based approach to group similar probe requests and evaluate how accurately they can be associated with the same device.

Main topics covered:

- MAC address randomization
- Probe request analysis
- Similarity-based clustering
- Online grouping of observations
- Clustering performance evaluation

### QoT Estimation

This assignment focuses on Quality of Transmission estimation in optical networks. Machine learning models are trained to predict the Signal-to-Noise Ratio of lightpaths using network-related features. The final part studies how uncertainty in fiber span length affects prediction accuracy and the required safety margin.

Main topics covered:

- Optical network QoT estimation
- Feature engineering
- Neural network regression
- Linear regression baseline
- Prediction error analysis
- Safety margin evaluation
- Impact of uncertain input features

### Website Fingerprinting

This assignment explores traffic classification for website fingerprinting. The code analyzes network traffic traces and extracts features that can be used to identify traffic patterns through machine learning techniques.

Main topics covered:

- Network traffic analysis
- Website fingerprinting
- Feature extraction from traffic traces
- Classification workflow
- Performance evaluation

## Technologies Used

The assignments are implemented mainly in Python using Jupyter and Google Colab notebooks.

Main libraries used across the repository include:

- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- XGBoost (flow classification)

## Note

This repository contains coursework solutions. Notebook scaffolding and exercises originate from the course; the implemented solutions and analyses are my work.

The QoT directory contains SNR data files used by its notebook. Other course datasets and external material are not bundled as a complete runnable dataset collection.
