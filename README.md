# Development of a Multi-Point Flow Monitoring System for Accurate Pipeline Leakage Detection

> A low-cost embedded multi-point flow monitoring system for pipeline leakage detection using differential flow analysis and physical flow verification.

<p align="center">
  <img src="Images/Hardware_Setup.jpg" alt="Laboratory Hardware Setup" width="800">
</p>

<p align="center">

![Publication](https://img.shields.io/badge/Publication-IEEE%20Xplore-blue)
![Indexing](https://img.shields.io/badge/Scopus-Indexed-orange)
![ESP32](https://img.shields.io/badge/ESP32-Embedded%20Controller-red)
![Arduino](https://img.shields.io/badge/Arduino-IDE-00979D)
![NodeJS](https://img.shields.io/badge/Node.js-Backend-green)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-darkgreen)
![IoT](https://img.shields.io/badge/IoT-Web%20Monitoring-blue)
![License](https://img.shields.io/badge/License-MIT-success)

</p>

---

## 📖 Overview

Pipeline leakage can cause significant water loss, operational inefficiency, equipment damage, and financial losses. Conventional approaches based on pressure monitoring or inlet–outlet flow comparison may generate false alarms during transient hydraulic conditions such as pump switching and rapid valve operation.

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
- Low-cost laboratory-scale implementation
- No dependence on continuous cloud connectivity for detection

---

## 🏗️ System Architecture

The system uses three flow measurement points:

1. **Inlet Flow Sensor** — measures incoming pipeline flow.
2. **Outlet Flow Sensor** — measures outgoing pipeline flow.
3. **Intermediate Flow Sensor** — measures physically diverted flow through the leakage branch.

The ESP32 processes the sensor pulse signals and performs leakage verification locally.

<p align="center">
  <img src="Images/Block_Diagram.png" alt="System Architecture" width="850">
</p>

### Hardware Components

| Component | Quantity | Purpose |
|---|---:|---|
| ESP32 Development Board | 1 | Embedded controller |
| YFS201 Flow Sensor | 2 | Inlet and outlet measurement |
| YFS401 Flow Sensor | 1 | Intermediate flow verification |
| PVC Pipeline | 1 | Experimental pipeline |
| PVC Tee Joint | Multiple | Leakage branch connection |
| Flexible Tubing | As required | Water circulation |
| Water Pump | 1 | Continuous water circulation |
| Buzzer | 1 | Leakage alarm |
| 12 V DC Adapter | 1 | Power supply |

### Software Stack

| Technology | Purpose |
|---|---|
| Arduino IDE | ESP32 firmware development |
| Embedded C | Leakage detection algorithm |
| Node.js | Backend server |
| MongoDB | Data and event storage |
| HTML / CSS / JavaScript | Web dashboard |
| Wi-Fi | Wireless communication |

---

## ⚙️ Working Principle

The system uses a **two-stage leakage verification strategy**.

### 1. Flow Measurement

Three turbine flow sensors continuously generate pulse signals proportional to the measured flow.

```text
                 Pipeline
                    │
                    ▼
              Inlet Sensor
                    │
                    │
                    ├──────────────► Outlet Sensor
                    │
                    │
                    └────► Leakage Branch
                              │
                              ▼
                       Intermediate Sensor
```

### 2. Primary Flow Deviation

The ESP32 calculates the inlet–outlet flow deviation:

```text
ΔP = Pin − Pout
```

If the deviation remains within the predefined tolerance, the system continues normal monitoring.

### 3. Physical Verification

When the deviation exceeds the threshold, leakage is not immediately declared.

The intermediate sensor is checked to determine whether the measured diverted flow corresponds to the observed inlet–outlet imbalance:

```text
|(Pin − Pout) − Pmid| ≤ ε
```

Where:

- `Pin` = inlet sensor pulse count
- `Pout` = outlet sensor pulse count
- `Pmid` = intermediate sensor pulse count
- `ε` = verification tolerance

Leakage is confirmed only when the physical flow measurement satisfies the verification condition.

### 4. Alarm

After leakage confirmation:

```text
Leakage Confirmed
       │
       ├──► Activate Buzzer
       ├──► Log Event
       └──► Update Dashboard
```

The ESP32 performs the primary leakage decision locally, while the dashboard provides supervisory monitoring.

---

## 🔁 Detection Algorithm

<p align="center">
  <img src="Images/Flowchart.png" alt="Leakage Detection Flowchart" width="800">
</p>

The detection sequence is:

```text
                 START
                   │
                   ▼
          Read Sensor Pulses
                   │
                   ▼
       Calculate Inlet–Outlet
             Difference
                   │
                   ▼
       Difference > Threshold?
             │          │
            NO         YES
             │          │
             │          ▼
             │   Read Intermediate
             │       Flow Sensor
             │          │
             │          ▼
             │   Does Physical Flow
             │   Match the Deviation?
             │        │       │
             │       NO      YES
             │        │       │
             │        ▼       ▼
             │    Ignore   Confirm
             │   Transient Leakage
             │        │       │
             └────────┘       ▼
                        Activate Alarm
                              │
                              ▼
                       Update Dashboard
```

---

## 📷 Hardware Setup

The system was implemented using a laboratory-scale PVC pipeline with three flow measurement points.

<p align="center">
  <img src="Images/Hardware_Setup.jpg" alt="Laboratory Hardware Setup" width="800">
</p>

The setup consists of:

- Two YFS201 flow sensors
- One YFS401 flow sensor
- ESP32 development board
- PVC pipeline and leakage branch
- Water pump
- Buzzer
- Regulated power supply

The intermediate flow sensor provides physical measurement of diverted flow for leakage verification.

---

## 🌐 Web Dashboard

The system includes a Node.js-based web dashboard for supervisory monitoring.

<p align="center">
  <img src="Results/Dashboard.png" alt="Web Dashboard" width="850">
</p>

The dashboard provides:

- Inlet flow monitoring
- Outlet flow monitoring
- Intermediate flow monitoring
- Leakage status
- Historical event logging

The dashboard is intended for monitoring and visualization. The primary leakage detection and alarm logic are executed by the ESP32.

---

## 🧪 Experimental Validation

The system was evaluated using a laboratory-scale PVC pipeline under three operating conditions.

### Normal Flow

- Continuous water circulation
- No intentional leakage
- Stable inlet–outlet flow balance

### Induced Leakage

- Controlled leakage introduced through the intermediate branch
- Diverted flow measured using the intermediate sensor
- Leakage evaluated using dual-stage verification

### Transient Flow Disturbances

- Pump switching
- Rapid valve operation
- Temporary hydraulic imbalance

These tests evaluated both leakage detection and rejection of transient disturbances.

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

> **Note:** These performance values are based on laboratory-scale experimental trials and should not be interpreted as industrial-scale validation.

---

## 🔬 Multi-Point Verification

A conventional two-point flow monitoring system primarily observes the difference between inlet and outlet flow.

The proposed system introduces an additional physical measurement point:

```text
Conventional Approach

Inlet ─────────────────► Outlet
          │
          ▼
    Flow Difference
          │
          ▼
   Possible Leakage


Proposed Approach

Inlet ─────────────────► Outlet
          │
          ▼
    Flow Difference
          │
          ▼
Intermediate Flow Sensor
          │
          ▼
 Physical Verification
          │
          ▼
    Confirm / Reject
```

The additional measurement point provides physical evidence of diverted flow before a leakage event is confirmed.

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

---

## 📁 Repository Contents

### Images

The `Images/` directory contains the main visual documentation:

- `Block_Diagram.png` — system architecture
- `Flowchart.png` — leakage detection algorithm
- `Hardware_Setup.jpg` — laboratory prototype

### Results

The `Results/` directory contains the experimental evidence:

- `Experimental_Data.xlsx` — experimental dataset
- `Performance_Graphs.pdf` — performance analysis
- `Result_Graph.png` — summarized experimental results
- `Dashboard.png` — web monitoring interface

### Publication

The `Publication/` directory contains information related to the published research work.

---

## 🚀 Getting Started

### Hardware

The experimental system can be assembled using the components listed in the **Hardware Components** section.

The block diagram, flowchart, and hardware setup are available in the `Images/` directory.

### Embedded System

The ESP32 performs:

- Flow pulse acquisition
- Flow deviation calculation
- Leakage verification
- Alarm control
- Communication with the monitoring system

### Monitoring System

The monitoring interface uses:

- Node.js
- MongoDB
- HTML
- CSS
- JavaScript
- Wi-Fi communication

> The current repository is organized primarily as a project, research, and results showcase. Source implementation files are not included.

---

## 🧪 Basic Testing Procedure

### Test 1 — Normal Operation

1. Start the water pump.
2. Allow the system to reach stable flow.
3. Observe inlet and outlet readings.
4. Verify that the intermediate flow remains negligible.

**Expected Result:** No leakage alarm.

### Test 2 — Leakage Simulation

1. Open the controlled leakage branch.
2. Observe the intermediate sensor.
3. Monitor the inlet–outlet deviation.
4. Observe the leakage indication.

**Expected Result:** Leakage is confirmed and the alarm is activated.

### Test 3 — Transient Disturbance

1. Start or stop the pump, or operate the valve rapidly.
2. Observe the temporary flow imbalance.
3. Monitor the leakage decision.

**Expected Result:** No confirmed leakage under the tested transient conditions.

---

## 📄 Publication

This work was published at the:

**International Conference on Smart Electronic Devices and Intelligent Systems (ICSEDIS 2026)**

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

My primary contributions to the project included:

- Hardware assembly and system integration
- Experimental setup and testing
- Data collection and validation
- Technical documentation
- Research paper preparation and writing

---

## 🔮 Future Scope

Potential extensions of the system include:

- Integration with industrial SCADA systems
- Adaptive threshold optimization
- Industrial communication protocols such as Modbus TCP, MQTT, and OPC UA
- Cloud-based analytics and remote diagnostics
- SMS, email, or messaging-based alerts
- AI/ML-based leakage classification
- Large-scale pipeline deployment
- Mobile-based monitoring

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
