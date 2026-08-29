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

### Project at a Glance

| Category | Details |
|---|---|
| Application | Pipeline leakage detection |
| Controller | ESP32 |
| Flow Sensors | 2 × YFS201 + 1 × YFS401 |
| Detection | Multi-point differential flow |
| Verification | Physical diverted-flow measurement |
| Alarm | Audible buzzer |
| Monitoring | Node.js web dashboard |
| Database | MongoDB |
| Communication | Wi-Fi |
| Validation | 50 laboratory-scale trials |

---

## 🎯 Objectives

- Develop a multi-point flow monitoring system using three turbine flow sensors.
- Detect leakage through inlet–outlet flow deviation.
- Physically verify diverted flow using an intermediate flow sensor.
- Reduce false alarms during transient hydraulic conditions.
- Perform real-time leakage decisions locally using an ESP32.
- Provide web-based monitoring and historical event logging.

---

## ✨ Key Features

- Three-point flow measurement
- Dual-stage leakage verification
- ESP32-based local decision making
- Physical diverted-flow verification
- Real-time leakage indication and audible alarm
- Wi-Fi communication
- Web-based monitoring dashboard
- Historical event logging
- Low-cost laboratory-scale implementation
- Detection without dependence on continuous cloud connectivity

---

## 🏗️ System Architecture

The system uses three flow measurement points: an **inlet sensor**, an **outlet sensor**, and an **intermediate sensor** connected to a leakage branch. The ESP32 processes sensor pulses and performs leakage verification locally.

<p align="center">
  <img src="Images/Block_Diagram.png" alt="System Architecture" width="850">
</p>

### Hardware

| Component | Qty. | Purpose |
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

### Software

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

The system uses a **two-stage verification strategy**.

### Stage 1 — Flow Deviation

The ESP32 continuously reads the inlet and outlet sensors and calculates:

```text
ΔP = Pin − Pout
```

If the deviation remains within the predefined tolerance, normal monitoring continues.

### Stage 2 — Physical Verification

When the deviation exceeds the threshold, leakage is not immediately declared. The intermediate sensor verifies whether the measured diverted flow corresponds to the observed imbalance.

```text
|(Pin − Pout) − Pmid| ≤ ε
```

Where:

- `Pin` = inlet sensor pulse count
- `Pout` = outlet sensor pulse count
- `Pmid` = intermediate sensor pulse count
- `ε` = verification tolerance

If the verification condition is satisfied, leakage is confirmed.

### Response

After confirmation, the system:

- Activates the buzzer
- Logs the leakage event
- Updates the dashboard

The primary leakage decision is performed locally by the ESP32.

---

## 🔁 Detection Algorithm

<p align="center">
  <img src="Images/Flowchart.png" alt="Leakage Detection Flowchart" width="800">
</p>

The algorithm follows this sequence:

```text
Read Sensors
     ↓
Calculate Inlet–Outlet Difference
     ↓
Difference > Threshold?
     ↓ Yes
Read Intermediate Sensor
     ↓
Physical Flow Matches Difference?
     ↓ Yes
Confirm Leakage
     ↓
Activate Alarm + Log Event + Update Dashboard
```

A deviation that is not physically verified by the intermediate sensor is not treated as a confirmed leakage event.

---

## 📷 Hardware Setup

The system was implemented using a laboratory-scale PVC pipeline with three flow measurement points.

<p align="center">
  <img src="Images/Hardware_Setup.jpg" alt="Laboratory Hardware Setup" width="800">
</p>

The setup includes:

- Two YFS201 flow sensors
- One YFS401 flow sensor
- ESP32 development board
- PVC pipeline and leakage branch
- Water pump
- Buzzer
- Regulated power supply

---

## 🌐 Web Dashboard

The Node.js-based dashboard provides supervisory monitoring and event visualization.

<p align="center">
  <img src="Results/Dashboard.png" alt="Web Dashboard" width="850">
</p>

It displays:

- Inlet flow
- Outlet flow
- Intermediate flow
- Leakage status
- Historical events

The primary leakage detection and alarm logic are executed by the ESP32.

---

## 🧪 Experimental Validation

The system was evaluated using a laboratory-scale PVC pipeline under three operating conditions:

| Condition | Description |
|---|---|
| **Normal Flow** | Continuous circulation without intentional leakage |
| **Induced Leakage** | Controlled leakage through the intermediate branch |
| **Transient Disturbances** | Pump switching and rapid valve operation |

These tests evaluated leakage detection and rejection of transient flow disturbances.

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

> **Note:** These performance values are based on laboratory-scale experiments and should not be interpreted as industrial-scale validation.

---

## 🔬 Multi-Point Verification

A conventional two-point flow monitoring system primarily observes the difference between inlet and outlet flow. The proposed architecture adds an intermediate measurement point to provide physical verification of diverted flow.

```text
Conventional:
Inlet ─────────────► Outlet
          │
          ▼
    Flow Difference
          │
          ▼
   Possible Leakage


Proposed:
Inlet ─────────────► Outlet
          │
          ▼
    Flow Difference
          │
          ▼
Intermediate Sensor
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
├── Documentation/
│   ├── Project_Report.pdf
│   └── Presentation.pptx
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

## 🚀 Getting Started

### Hardware

Assemble the pipeline using the components listed above. Install the two YFS201 sensors at the inlet and outlet and connect the YFS401 sensor to the intermediate leakage branch.

Connect the sensors and buzzer to the ESP32 and provide the required regulated power supply.

### ESP32

The ESP32 performs:

- Flow pulse acquisition
- Flow deviation calculation
- Leakage verification
- Alarm control
- Communication with the monitoring system

### Dashboard

The monitoring system uses Node.js and MongoDB.

```bash
npm install
npm start
```

The dashboard is configured to run at:

```text
http://localhost:3000
```

> Source implementation files are not included in the current repository structure. This repository is organized as a project documentation, results, and research showcase.

---

## 🧪 Basic Testing

### Normal Operation

1. Start the water pump.
2. Allow stable flow to develop.
3. Observe the three flow readings.

**Expected:** No leakage alarm.

### Leakage Simulation

1. Open the controlled leakage branch.
2. Observe the intermediate sensor.
3. Monitor the leakage indication.

**Expected:** Leakage is confirmed and the alarm is activated.

### Transient Disturbance

1. Start or stop the pump, or operate the valve rapidly.
2. Observe the temporary flow imbalance.
3. Monitor the leakage decision.

**Expected:** No confirmed leakage under the tested transient conditions.

---

## 📄 Project Documentation

Detailed methodology, mathematical modeling, experimental procedures, analysis, and discussion are available in:

- `Documentation/Project_Report.pdf`
- `Documentation/Presentation.pptx`

Additional experimental data and performance graphs are available in `Results/`.

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

- Integration with industrial SCADA systems
- Adaptive threshold optimization
- Modbus TCP, MQTT, and OPC UA support
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
