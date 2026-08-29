# Development of a Multi-Point Flow Monitoring System for Accurate Pipeline Leakage Detection

> A low-cost embedded multi-point flow monitoring system for pipeline leakage detection using differential flow analysis and physical flow verification.

<p align="center">
  <img src="Images/Block_Diagram.png" alt="System Architecture" width="850">
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

Pipeline leakage can cause significant water loss, operational inefficiency, equipment damage, and financial losses. Conventional approaches based on pressure monitoring or inlet–outlet flow comparison can produce false alarms during transient hydraulic conditions such as pump switching and rapid valve operation.

This project presents a **multi-point flow monitoring system** that combines differential flow measurement with **physical verification of diverted flow**. Three turbine flow sensors are connected to an ESP32, which performs leakage detection locally. A Node.js-based web dashboard provides real-time monitoring and event logging.

The system was experimentally evaluated under normal flow, induced leakage, and transient operating conditions.

### Key Results

| Metric               |   Result |
| -------------------- | -------: |
| Experimental Trials  |   **50** |
| Detection Accuracy   |  **98%** |
| Precision            | **100%** |
| Recall / Sensitivity |  **95%** |
| Specificity          | **100%** |
| False Positives      |    **0** |

---

## 🎯 Objectives

* Develop a multi-point flow monitoring system using three turbine flow sensors.
* Detect leakage through inlet–outlet flow deviation.
* Physically verify diverted flow using an intermediate sensor.
* Reduce false alarms during transient hydraulic conditions.
* Perform real-time leakage decisions locally using an ESP32.
* Provide web-based monitoring and historical event logging.

---

## ✨ Key Features

* Three-point flow measurement
* Dual-stage leakage verification
* ESP32-based local decision making
* Physical diverted-flow verification
* Real-time leakage indication
* Audible alarm
* Wi-Fi communication
* Node.js monitoring dashboard
* MongoDB event logging
* Operation independent of continuous cloud connectivity
* Low-cost laboratory-scale implementation

---

## 🏗️ System Architecture

The system uses three flow measurement points:

1. **Inlet sensor** — measures incoming pipeline flow.
2. **Outlet sensor** — measures outgoing pipeline flow.
3. **Intermediate sensor** — measures physically diverted flow through the leakage branch.

The ESP32 processes the sensor pulse signals and performs the leakage verification locally. When leakage is confirmed, the system activates the buzzer and sends monitoring information to the web dashboard.

<p align="center">
  <img src="Images/Block_Diagram.png" alt="System Architecture" width="850">
</p>

### Hardware Components

| Component               |        Qty. | Purpose                        |
| ----------------------- | ----------: | ------------------------------ |
| ESP32 Development Board |           1 | Embedded controller            |
| YFS201 Flow Sensor      |           2 | Inlet and outlet measurement   |
| YFS401 Flow Sensor      |           1 | Intermediate flow verification |
| PVC Pipeline            |           1 | Experimental pipeline          |
| PVC Tee Joint           |    Multiple | Leakage branch connection      |
| Flexible Tubing         | As required | Water circulation              |
| Water Pump              |           1 | Continuous water circulation   |
| Buzzer                  |           1 | Leakage alarm                  |
| 12 V DC Adapter         |           1 | Power supply                   |

### Software Stack

| Technology              | Purpose                     |
| ----------------------- | --------------------------- |
| Arduino IDE             | ESP32 firmware development  |
| Embedded C              | Leakage detection algorithm |
| Node.js                 | Backend server              |
| MongoDB                 | Data and event storage      |
| HTML / CSS / JavaScript | Web dashboard               |
| Wi-Fi                   | Wireless communication      |

---

## ⚙️ How It Works

The leakage detection process uses two stages.

### 1. Measure Flow

The three turbine flow sensors generate pulse signals proportional to the measured flow.

```text
Inlet Flow ───────► Sensor 1
                         │
Pipeline ────────────────┼──────► Sensor 2 ───────► Outlet
                         │
                         └──────► Leakage Branch
                                      │
                                   Sensor 3
```

### 2. Detect Flow Deviation

The ESP32 calculates the difference between inlet and outlet pulse counts:

```text
ΔP = Pin − Pout
```

If the deviation remains within the predefined tolerance, the system continues normal monitoring.

### 3. Verify the Leakage

If the deviation exceeds the threshold, the system does **not immediately declare leakage**.

Instead, the intermediate sensor is checked to determine whether the measured diverted flow corresponds to the inlet–outlet imbalance.

```text
|(Pin − Pout) − Pmid| ≤ ε
```

where:

* `Pin` = inlet sensor pulse count
* `Pout` = outlet sensor pulse count
* `Pmid` = intermediate sensor pulse count
* `ε` = verification tolerance

Leakage is confirmed only when the physical flow measurement satisfies the verification condition.

### 4. Respond to Confirmed Leakage

When leakage is confirmed:

```text
Leakage Confirmed
       │
       ├──► Activate Buzzer
       │
       ├──► Log Event
       │
       └──► Update Dashboard
```

The ESP32 performs the detection locally, while the dashboard acts as a supervisory monitoring interface.

---

## 🔁 Detection Logic

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

## 🌐 Web Dashboard

The monitoring dashboard provides a supervisory view of system operation.

<p align="center">
  <img src="Images/Dashboard.png" alt="Web Dashboard" width="850">
</p>

### Dashboard Displays

* Inlet flow
* Outlet flow
* Intermediate flow
* Leakage status
* Historical events

The dashboard is not responsible for the primary leakage decision. Detection and alarm logic remain on the ESP32, allowing the embedded system to continue its monitoring function even if network connectivity is unavailable.

---

## 🧪 Experimental Validation

The system was tested using a laboratory-scale PVC pipeline and three flow sensors.

### Test Conditions

**Normal Flow**

* Continuous water circulation
* No intentional leakage
* Stable inlet–outlet flow balance

**Induced Leakage**

* Controlled leakage introduced through the intermediate branch
* Diverted flow measured using the intermediate sensor
* Leakage evaluated using dual-stage verification

**Transient Flow Disturbances**

* Pump switching
* Rapid valve operation
* Temporary hydraulic imbalance

These conditions were selected to evaluate both leakage detection and rejection of transient disturbances.

---

## 📊 Experimental Results

A total of **50 experimental trials** were conducted.

| Test Category          | Trials |
| ---------------------- | -----: |
| Normal Flow            |     20 |
| Leak Condition         |     20 |
| Transient Flow Changes |     10 |
| **Total**              | **50** |

### Classification Results

| Parameter           | Result |
| ------------------- | -----: |
| True Positive (TP)  |     19 |
| False Negative (FN) |      1 |
| True Negative (TN)  |     30 |
| False Positive (FP) |      0 |

### Performance Metrics

| Metric                   |   Result |
| ------------------------ | -------: |
| **Accuracy**             |  **98%** |
| **Precision**            | **100%** |
| **Recall / Sensitivity** |  **95%** |
| **Specificity**          | **100%** |
| **False Positive Rate**  |   **0%** |

The experiments showed that the system correctly identified most induced leakage events while producing no false-positive detections in the tested transient conditions.

<p align="center">
  <img src="Images/Result_Graph.png" alt="Experimental Results" width="800">
</p>

> **Note:** These performance values represent the reported laboratory-scale experimental trials and should not be interpreted as industrial-scale validation.

---

## 🔬 Why Multi-Point Verification?

A conventional two-point system can identify a difference between inlet and outlet flow, but that difference does not by itself establish the physical cause.

The proposed architecture adds an intermediate measurement point:

```text
Conventional:

Inlet ─────────────────► Outlet
          Difference
             ↓
       Possible Leakage


Proposed:

Inlet ─────────────────► Outlet
          Difference
             │
             ▼
     Intermediate Flow
       Verification
             │
             ▼
     Confirm / Reject
```

This provides a second physical measurement before declaring a leakage event and was specifically evaluated for transient operating conditions.

---

## 📂 Repository Structure

```text
multi-point-pipeline-leakage-detection/
│
├── Documentation/
│   ├── Project_Report.pdf
│   ├── Presentation.pptx
│   └── README.md
│
├── Hardware/
│   ├── Circuit_Diagram.png
│   ├── Pin_Connections.pdf
│   ├── Bill_of_Materials.xlsx
│   └── README.md
│
├── Images/
│   ├── Block_Diagram.png
│   ├── Prototype.jpg
│   ├── Dashboard.png
│   └── Result_Graph.png
│
├── Publication/
│   └── README.md
│
├── Results/
│   ├── Experimental_Data.xlsx
│   ├── Performance_Graphs.pdf
│   └── README.md
│
├── Software/
│   ├── ESP32_Firmware/
│   ├── Dashboard/
│   └── README.md
│
├── LICENSE
└── README.md
```

---

## 🚀 Getting Started

### Hardware Setup

1. Assemble the PVC pipeline.
2. Install the two YFS201 sensors at the inlet and outlet.
3. Connect the YFS401 sensor to the intermediate branch.
4. Connect the three sensors to the ESP32.
5. Connect the buzzer.
6. Power the system using the required regulated DC supply.

### ESP32 Firmware

1. Install Arduino IDE.
2. Install the ESP32 board package.
3. Open the ESP32 firmware.
4. Configure the Wi-Fi credentials.
5. Upload the firmware to the ESP32.

### Dashboard

Install the required Node.js dependencies:

```bash
npm install
```

Start MongoDB and run the application:

```bash
npm start
```

The dashboard is configured to run at:

```text
http://localhost:3000
```

---

## 🧪 Basic Testing

### Normal Operation

Start the pump and observe the three flow readings.

**Expected:** No leakage alarm.

### Leakage Simulation

Open the controlled leakage branch and observe the intermediate sensor.

**Expected:** Diverted flow is detected and the leakage alarm is activated.

### Transient Disturbance

Perform a pump start/stop operation or rapid valve operation.

**Expected:** Temporary flow imbalance should not result in a confirmed leakage alarm under the tested conditions.

---

## 📷 Prototype

<p align="center">
  <img src="Images/Prototype.jpg" alt="Laboratory Prototype" width="750">
</p>

The laboratory prototype consists of a PVC pipeline, three turbine flow sensors, an ESP32 controller, pump, leakage branch, and alarm system.

---

## 📄 Publication

This work was published at the:

**International Conference on Smart Electronic Devices and Intelligent Systems (ICSEDIS 2026)**

| Item      | Details                            |
| --------- | ---------------------------------- |
| Publisher | IEEE                               |
| Indexing  | IEEE Xplore, Scopus                |
| DOI       | 10.1109/ICSEDIS68157.2026.11518189 |
| ISBN      | 979-8-3315-8824-3                  |

The publisher-formatted IEEE paper is not included in this repository.

---

## 👨‍💻 My Contribution

My primary contributions to the project included:

* Hardware assembly and system integration
* Experimental setup and testing
* Data collection and validation
* Technical documentation
* Research paper preparation and writing

---

## 🔮 Future Scope

Potential extensions of the system include:

* Integration with industrial SCADA systems
* Adaptive threshold optimization
* Industrial communication protocols such as Modbus TCP, MQTT, and OPC UA
* Cloud-based analytics and remote diagnostics
* SMS, email, or messaging-based alerts
* AI/ML-based leakage classification
* Large-scale pipeline deployment
* Mobile-based monitoring

These are proposed extensions and were not part of the reported experimental validation.

---

## 👥 Authors

| Name                    | Role               |
| ----------------------- | ------------------ |
| **Praveen V. Pol**      | Guide              |
| **Vikas J. Nandeshwar** | Student Researcher |
| **Tejas R. Kulkarni**   | Student Researcher |
| **Sejal M. Mankawade**  | Student Researcher |
| **Aditya V. Kulsange**  | Student Researcher |
| **Samadhan S. Kendre**  | Student Researcher |

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

See [`LICENSE`](LICENSE) for the complete license terms.

---
