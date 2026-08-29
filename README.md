# Development of a Multi-Point Flow Monitoring System for Accurate Pipeline Leakage Detection

> A low-cost embedded multi-point flow monitoring system for pipeline leakage detection using differential flow analysis and physical flow verification.

<p align="center">
  <img src="https://img.shields.io/badge/Publication-IEEE%20Xplore-blue">
  <img src="https://img.shields.io/badge/Indexing-Scopus-Indexed-orange">
  <img src="https://img.shields.io/badge/ESP32-Embedded%20Controller-red">
  <img src="https://img.shields.io/badge/Arduino-IDE-00979D">
  <img src="https://img.shields.io/badge/Node.js-Backend-green">
  <img src="https://img.shields.io/badge/MongoDB-Database-darkgreen">
  <img src="https://img.shields.io/badge/IoT-Web%20Monitoring-blue">
  <img src="https://img.shields.io/badge/License-MIT-success">
</p>

---

## 📖 Overview

Pipeline leakage can cause water loss, operational inefficiency, equipment damage, and financial losses. Conventional approaches based on pressure monitoring or inlet–outlet flow comparison may generate false alarms during transient hydraulic conditions such as pump switching and rapid valve operation.

This project presents a **Multi-Point Flow Monitoring System** that combines differential flow measurement with **physical verification of diverted flow**. Three turbine flow sensors are connected to an ESP32, which performs leakage detection locally. A Node.js-based web dashboard provides real-time monitoring and event logging.

The system was experimentally evaluated under normal flow, induced leakage, and transient operating conditions using a laboratory-scale pipeline prototype.

### Key Results

| Metric | Result |
|---|---:|
| Experimental Trials | **50** |
| Detection Accuracy | **98%** |
| Precision | **100%** |
| Recall / Sensitivity | **95%** |
| Specificity | **100%** |
| False Positive Rate | **0%** |

---

## 🎯 Objectives

- Develop a multi-point flow monitoring system using three turbine flow sensors.
- Detect leakage through inlet–outlet flow deviation.
- Physically verify diverted flow using an intermediate flow sensor.
- Reduce false alarms during transient hydraulic conditions.
- Perform real-time leakage decisions locally using an ESP32.
- Provide web-based monitoring and event logging.

---

## ✨ Key Features

- Three-point flow measurement
- Dual-stage leakage verification
- ESP32-based local decision making
- Physical diverted-flow verification
- Real-time leakage indication
- Audible leakage alarm
- Wi-Fi communication
- Web-based monitoring dashboard
- Historical event logging
- No continuous cloud dependency for leakage detection

---

## 🏗️ System Architecture

The system uses three flow measurement points:

| Measurement Point | Sensor | Purpose |
|---|---|---|
| Inlet | YFS201 | Incoming pipeline flow |
| Outlet | YFS201 | Outgoing pipeline flow |
| Intermediate | YFS401 | Diverted-flow verification |

The ESP32 processes sensor pulse signals and performs the primary leakage verification locally.

<p align="center">
  <img src="Images/Block_Diagram.png" alt="System Architecture" width="850">
</p>

### Hardware Components

| Component | Qty. | Purpose |
|---|---:|---|
| ESP32 Development Board | 1 | Embedded controller |
| YFS201 Flow Sensor | 2 | Inlet and outlet measurement |
| YFS401 Flow Sensor | 1 | Intermediate verification |
| PVC Pipeline | 1 | Experimental pipeline |
| PVC Tee Joint | Multiple | Leakage branch |
| Flexible Tubing | As required | Water circulation |
| Water Pump | 1 | Water circulation |
| Buzzer | 1 | Leakage alarm |
| 12 V DC Adapter | 1 | Power supply |

### Software Stack

| Technology | Purpose |
|---|---|
| Arduino IDE / Embedded C | ESP32 firmware and detection algorithm |
| Node.js | Backend server |
| MongoDB | Data and event storage |
| HTML / CSS / JavaScript | Web dashboard |
| Wi-Fi | Communication |

---

## ⚙️ Working Principle

The system uses a **two-stage leakage verification strategy**.

### Stage 1 — Flow Deviation

The three flow sensors generate pulse signals proportional to the measured flow. The ESP32 calculates:

```text
ΔP = Pin − Pout
```

If the deviation remains within the predefined tolerance, normal monitoring continues.

### Stage 2 — Physical Verification

When the deviation exceeds the threshold, leakage is not immediately declared. The intermediate sensor is checked to determine whether the measured diverted flow corresponds to the observed imbalance:

```text
|(Pin − Pout) − Pmid| ≤ ε
```

Where:

- `Pin` = inlet sensor pulse count
- `Pout` = outlet sensor pulse count
- `Pmid` = intermediate sensor pulse count
- `ε` = verification tolerance

Leakage is confirmed only when the physical flow measurement satisfies the verification condition.

### Alarm Response

After confirmation, the system activates the buzzer, records the event, and updates the dashboard. The primary leakage decision is performed locally by the ESP32.

---

## 🔁 Detection Algorithm

<p align="center">
  <img src="Images/Flowchart.png" alt="Leakage Detection Flowchart" width="800">
</p>

The detection sequence is:

1. Read flow sensor pulses.
2. Calculate the inlet–outlet deviation.
3. Compare the deviation with the threshold.
4. If the threshold is exceeded, read the intermediate flow.
5. Compare the physical diverted flow with the calculated deviation.
6. Confirm leakage only when the verification condition is satisfied.
7. Activate the alarm and update the monitoring system.

---

## 📷 Hardware Setup

The laboratory prototype uses a PVC pipeline with three flow measurement points.

The setup includes two YFS201 sensors, one YFS401 sensor, an ESP32, PVC pipeline and leakage branch, water pump, buzzer, and regulated power supply.

The intermediate flow sensor provides physical measurement of diverted flow for leakage verification.

---

## 🌐 Web Dashboard

The Node.js-based dashboard provides a supervisory interface for monitoring the system.

<p align="center">
  <img src="Results/Dashboard.png" alt="Web Dashboard" width="850">
</p>

It displays:

- Inlet flow
- Outlet flow
- Intermediate flow
- Leakage status
- Historical event logging

The dashboard is used for monitoring and visualization. Leakage detection and alarm decisions are performed by the ESP32.

---

## 🧪 Experimental Validation

The system was evaluated under three operating conditions:

### Normal Flow

- Continuous water circulation
- No intentional leakage
- Stable inlet–outlet flow balance

### Induced Leakage

- Controlled leakage through the intermediate branch
- Diverted flow measured using the intermediate sensor
- Leakage evaluated using dual-stage verification

### Transient Flow Disturbances

- Pump switching
- Rapid valve operation
- Temporary hydraulic imbalance

---

## 📊 Experimental Results

A total of **50 experimental trials** were conducted.

| Test Category | Trials |
|---|---:|
| Normal Flow | 20 |
| Leak Condition | 20 |
| Transient Flow Changes | 10 |
| **Total** | **50** |

### Classification Results

| Parameter | Result |
|---|---:|
| True Positive (TP) | 19 |
| False Negative (FN) | 1 |
| True Negative (TN) | 30 |
| False Positive (FP) | 0 |

### Performance Metrics

| Metric | Result |
|---|---:|
| **Accuracy** | **98%** |
| **Precision** | **100%** |
| **Recall / Sensitivity** | **95%** |
| **Specificity** | **100%** |
| **False Positive Rate** | **0%** |

<p align="center">
  <img src="Results/Result_Graph.png" alt="Experimental Results" width="800">
</p>

The results indicate that the system correctly identified most induced leakage events while producing no false-positive detections during the tested transient conditions.

> **Note:** These results are based on laboratory-scale experimental trials and should not be interpreted as industrial-scale validation.

---

## 📂 Repository Structure

```text
multi-point-pipeline-leakage-detection/
│
├── Images/
│   ├── Block_Diagram.png
│   ├── Flowchart.png
│   └── Hardware_Setup.jpg
│
├── Publication/
│   └── README.md
│
├── Results/
│   ├── Experimental_Data.xlsx
│   ├── Performance_Graphs.pdf
│   ├── Result_Graph.png
│   └── Dashboard.png
│
├── LICENSE
└── README.md
```

### Repository Contents

| Directory / File | Contents |
|---|---|
| `Images/` | Block diagram, flowchart, hardware setup |
| `Results/` | Experimental data, graphs, dashboard |
| `Publication/` | Publication information |
| `LICENSE` | MIT License |
| `README.md` | Project overview and technical summary |

Detailed experimental data and performance graphs are available in the `Results/` directory.

---

## 🚀 Getting Started

Assemble the pipeline using the listed components, with the two YFS201 sensors at the inlet and outlet and the YFS401 sensor at the intermediate branch.

Connect the sensors and buzzer to the ESP32 and provide the required regulated power supply.

The ESP32 performs:

- Flow pulse acquisition
- Flow deviation calculation
- Leakage verification
- Alarm control
- Communication with the monitoring system

The monitoring interface uses Node.js, MongoDB, HTML, CSS, JavaScript, and Wi-Fi communication.

> Source implementation files are not included in the current repository. The repository is organized as a project, research, and results showcase.

---

## 📄 Publication

This work was published at the **International Conference on Smart Electronic Devices and Intelligent Systems (ICSEDIS 2026)**.

| Item | Details |
|---|---|
| Conference | ICSEDIS 2026 |
| Publisher | IEEE |
| Indexing | IEEE Xplore, Scopus |
| DOI | 10.1109/ICSEDIS68157.2026.11518189 |
| ISBN | 979-8-3315-8824-3 |

The publisher-formatted IEEE paper is not included in this repository.

---

## 👨‍💻 My Contribution

My primary contributions included:

- Hardware assembly and system integration
- Experimental setup and testing
- Data collection and validation
- Technical documentation
- Research paper preparation and writing

---

## 🔮 Future Scope

Potential extensions include:

- Industrial SCADA integration
- Adaptive threshold optimization
- Modbus TCP, MQTT, or OPC UA communication
- Cloud-based analytics and remote alerts
- AI/ML-based leakage classification
- Large-scale pipeline deployment

These are proposed future extensions and were not part of the reported experimental validation.

---

## 👥 Authors

| Name | Role |
|---|---|
| **Praveen V. Pol** | Guide |
| **Vikas J. Nandeshwar** | Student Researcher |
| **Tejas R. Kulkarni** | Student Researcher |
| **Sejal M. Mankawade** | Student Researcher |
| **Aditya V. Kulsange** | Student Researcher |
| **Samadhan S. Kendre** | Student Researcher |

---

## 📚 Citation

If you use this work in your research or project, please cite:

```bibtex
@inproceedings{Kulkarni2026PipelineLeakage,
  title={Development of a Multi-Point Flow Monitoring System for Accurate Pipeline Leakage Detection},
  author={Pol, Praveen V. and Nandeshwar, Vikas J. and Kulkarni, Tejas R. and Mankawade, Sejal M. and Kulsange, Aditya V. and Kendre, Samadhan S.},
  booktitle={International Conference on Smart Electronic Devices and Intelligent Systems (ICSEDIS)},
  year={2026},
  publisher={IEEE},
  doi={10.1109/ICSEDIS68157.2026.11518189}
}
```

---

## 📜 License

This project is licensed under the **MIT License**.

See [`LICENSE`](LICENSE) for complete license terms.
