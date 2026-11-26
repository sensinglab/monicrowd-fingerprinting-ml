# MoniCrowd Fingerprinting and Machine Learning Toolkit

**Wi-Fi Information Element Analysis, Device Fingerprinting, and Machine Learning for Crowd Monitoring**

---

## Overview

This repository provides research tools developed and adapted within the **MoniCrowd project** for Wi-Fi device fingerprinting and machine-learning-based device counting under MAC address randomization.

The toolkit supports the analysis of Wi-Fi probe requests, the construction and evaluation of device fingerprints, the preparation of experimental datasets, and the investigation of machine learning methods for estimating active Wi-Fi device populations.

A central motivation is that MAC address randomization makes direct address-based counting unreliable. Although fingerprinting can improve the association of probe requests with physical devices, fingerprint fragmentation and collisions can still introduce substantial counting errors.

The toolkit supports research into both **fingerprint construction** and **learning-based count estimation**, including approaches that compensate for residual fingerprinting errors without requiring reliable identification of individual devices.

---

## Main Components

### 1. Information Element Analysis and Fingerprinting

The **Information Elements Automatic Analyser (IEAA)** supports the development of rule-based Wi-Fi device fingerprints by examining structural and content characteristics of Information Elements (IEs) extracted from probe requests.

Its functionality includes:

- Identification and analysis of standard and vendor-specific IEs.
- Bit-level evaluation of IE content stability.
- Analysis of variations within and across physical devices.
- Threshold-based selection of characteristics for fingerprint construction.
- Evaluation of fingerprint fragmentation, collisions, and device-counting errors.

The IEAA and associated fingerprinting tools are located in the [`Fingerprint/`](Fingerprint/) directory.

### 2. Machine Learning and Device Counting

The repository also contains experimental machine learning implementations for analysing fingerprint-derived observations and investigating device-count estimation.

The available research code covers neural-network-based approaches and other learning methods, including regression and clustering experiments.

The broader research investigates how machine learning can complement rule-based fingerprinting by estimating the number of active devices from imperfect observations, rather than assuming a one-to-one correspondence between fingerprints and physical devices.

Individual implementations and experimental configurations are maintained in their respective directories.

### 3. Dataset Preparation and Crowd-Scenario Construction

The toolkit includes utilities for processing captured Wi-Fi traffic and preparing data for experimental evaluation.

These tools support:

- Processing recorded probe-request traces.
- Converting captured observations into structured datasets.
- Combining traces from independently captured devices.
- Constructing crowd scenarios with configurable device populations and temporal characteristics.
- Preparing observations for fingerprinting and machine learning experiments.

Constructed scenarios can reuse recorded device traces while preserving their original IE content and transmission characteristics, enabling controlled experiments with known device-count ground truth.

---

## Repository Organization

The repository includes the following research components and utilities:

| Directory or tool | Purpose |
|---|---|
| `Fingerprint/` | Information Element analysis, IEAA, and fingerprinting experiments |
| `NN/` | Neural network experiments |
| `CNN/` | Convolutional neural network experiments |
| `RandomForestRegression/` | Random forest regression experiments |
| `SVR/` | Support vector regression experiments |
| `DBSCAN/` | Density-based clustering experiments |
| `pcapDistributionOrchestrator.py` | Construction of crowd scenarios from recorded device traces |
| `datasetToCSV.py` | Dataset conversion and preparation |
| `datasetToCSV_detailed.py` | Detailed dataset conversion and preparation |

Some components originate from different stages of the research and may use different experimental configurations or dependencies.

---

## Research Workflow

The tools support a research workflow that combines experimental data preparation, fingerprinting, and learning-based device-count estimation.

```text
Controlled Wi-Fi Probe-Request Captures
                  |
                  v
      Dataset Preparation
                  |
                  v
   Information Element Analysis
               (IEAA)
                  |
                  v
      Fingerprint Construction
                  |
                  v
   Traffic and Fingerprint Features
                  |
                  v
       Machine Learning Models
                  |
                  v
     Estimated Active Wi-Fi Devices
```

The diagram illustrates the main research workflow rather than a single executable application.

In the MoniCrowd sensing architecture, fingerprinting and machine-learning inference can operate locally at the edge, with only aggregate device-count estimates transmitted to the central monitoring platform.

---

## Experimental Data

The MoniCrowd research uses controlled, device-labeled Wi-Fi probe-request captures and constructed crowd scenarios.

Controlled captures provide ground truth for investigating IE stability, fingerprint construction, fragmentation, and collisions.

Constructed crowd scenarios support the evaluation of device-counting methods under configurable population sizes and arrival patterns while reusing recorded transmission behavior.

The datasets are maintained separately from this source-code repository:

- **MoniCrowd dataset:** controlled Wi-Fi probe-request captures and associated metadata.
- **Training and test datasets:** constructed crowd scenarios used in machine learning experiments.

Dataset references, experimental configurations, and methodological details are provided in the associated research publications.

---

## Privacy Considerations

MoniCrowd research investigates privacy-preserving approaches to passive Wi-Fi crowd monitoring.

The proposed sensing architecture performs device-level processing locally, allowing aggregate counts to be transmitted without forwarding individual probe-request observations to the central monitoring platform.

However, captured probe requests and experimental datasets may contain device-level identifiers or other potentially identifying information. Appropriate pseudonymization, access controls, and data-retention practices remain necessary.

Fingerprinting and machine learning are used to support device-count estimation, not to reconstruct persistent identities of individual users.

**Device counting and human occupancy estimation are distinct tasks.** Converting estimated device populations into estimates of people requires additional calibration.

---

## Relationship to the MoniCrowd Project

This toolkit is part of the broader **MoniCrowd** research ecosystem.

The complete MoniCrowd architecture includes sensing devices, edge processing, communication infrastructure, backend services, visualization, and complementary sensing and calibration components.

This repository focuses on the research tools associated with Wi-Fi fingerprinting, experimental data processing, and machine learning.

The toolkit supports the offline development and evaluation of fingerprinting rules and machine learning models. Selected fingerprinting rules and trained ML models are incorporated into the operational [crowd-sensor](https://github.com/sensinglab/crowd-sensor), enabling local device-count estimation without executing the experimental analysis, model training, or threshold optimization procedures during normal operation.

For the overall architecture and related components, see:

- **MoniCrowd:** https://github.com/sensinglab/monicrowd
- **Project website:** https://monicrowd.sensinglab.eu

---

## Research and Reproducibility

The tools in this repository support research on:

- Wi-Fi probe-request analysis under MAC address randomization.
- Information Element stability and fingerprint construction.
- Fingerprint fragmentation and collision analysis.
- Machine-learning-based estimation of active-device populations.
- Evaluation across controlled crowd scenarios and device populations.

Different directories may correspond to different experimental studies. Users should consult the relevant source code, configuration files, datasets, and publications to identify the procedures associated with a particular experiment.

---

## Contact

For information about the MoniCrowd project:

**SensingLab**

Website: https://monicrowd.sensinglab.eu

Email: info@sensinglab.eu
