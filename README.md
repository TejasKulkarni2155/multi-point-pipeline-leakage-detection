<!-- ========================================================= -->
<!--                  PROJECT HEADER                           -->
<!-- ========================================================= -->

<p align="center">
  <img src="Images/Block_Diagram.png" alt="System Architecture" width="900">
</p>

<h1 align="center">
Development of a Multi-Point Flow Monitoring System for Accurate Pipeline Leakage Detection
</h1>

<p align="center">
A Low-Cost Embedded Multi-Point Flow Monitoring System for Accurate Pipeline Leakage Detection Using Physical Flow Verification
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

# 📖 Overview

Pipeline leakage remains one of the major causes of water loss, operational inefficiency, equipment damage, and financial loss in industrial and municipal pipeline systems. Conventional leak detection techniques generally depend on pressure monitoring or two-point flow comparison. While these approaches are relatively simple, they often generate false alarms during transient hydraulic events such as pump start-up, pump shut-down, and rapid valve operation.

This project presents a **Multi-Point Flow Monitoring System** that improves leakage detection reliability using three turbine flow sensors and an ESP32 microcontroller. Instead of relying only on inlet–outlet flow imbalance, the proposed architecture introduces **physical verification of diverted flow** using an intermediate flow sensor. The embedded controller performs all leakage detection locally, while a web-based dashboard provides real-time monitoring, visualization, and event logging.

The system was experimentally validated on a laboratory-scale prototype under normal flow, induced leakage, and transient operating conditions. Experimental evaluation achieved **98% detection accuracy**, **100% precision**, and **zero false-positive detections** during transient hydraulic disturbances. The work was published in the **2026 International Conference on Smart Electronic Devices and Intelligent Systems (ICSEDIS)** and indexed in **IEEE Xplore** and **Scopus**. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

---

# 🎯 Problem Statement

Traditional pipeline leakage detection systems frequently generate false alarms because they rely solely on pressure variations or inlet–outlet flow imbalance. During transient conditions such as pump switching or valve actuation, temporary hydraulic disturbances can resemble actual leakage, reducing the reliability of conventional monitoring systems.

The challenge addressed in this project is to develop a **low-cost, embedded, real-time leakage detection system** capable of distinguishing genuine leakage events from temporary hydraulic disturbances through physical flow verification while maintaining high detection accuracy and minimal computational complexity. :contentReference[oaicite:2]{index=2}

---

# 🎯 Objectives

- Develop a multi-point flow monitoring system using three turbine flow sensors.
- Detect minor pipeline leakage through inlet–outlet differential pulse analysis.
- Physically verify diverted flow using an intermediate flow sensor.
- Minimize false alarms during transient operating conditions.
- Perform real-time embedded decision making using an ESP32 microcontroller.
- Provide IoT-based monitoring, visualization, and event logging through a web dashboard.
- Develop a scalable and computationally efficient architecture suitable for industrial pipeline monitoring. :contentReference[oaicite:3]{index=3}

---

# ✨ Key Features

- Multi-point flow monitoring architecture
- Three turbine flow sensors
- ESP32-based embedded controller
- Dual-stage leakage verification
- Physical diverted flow confirmation
- Near real-time leakage detection
- Zero false-positive detection during transient conditions
- Embedded decision making without cloud dependency
- Web-based monitoring dashboard
- Historical event logging
- Audible leakage alarm
- Low-cost hardware implementation
- Scalable monitoring architecture
- Industrial instrumentation application

---

# 🌟 Highlights

| Feature | Description |
|----------|-------------|
| **Detection Method** | Multi-Point Differential Flow Monitoring |
| **Verification Method** | Physical Flow Verification |
| **Controller** | ESP32 |
| **Monitoring** | Real-Time IoT Dashboard |
| **Communication** | Wi-Fi |
| **Database** | MongoDB |
| **Backend** | Node.js |
| **Programming** | Embedded C (Arduino) |
| **Detection Accuracy** | **98%** |
| **Precision** | **100%** |
| **Specificity** | **100%** |
| **False Positives** | **0** |
| **Publication** | IEEE Xplore |
| **Indexing** | Scopus |

---

> **Publication:** International Conference on Smart Electronic Devices and Intelligent Systems (ICSEDIS 2026) | IEEE Xplore | Scopus Indexed | DOI: 10.1109/ICSEDIS68157.2026.11518189 
---

# 🏗 System Architecture

The proposed system employs a **multi-point flow monitoring architecture** consisting of three turbine flow sensors, an ESP32 microcontroller, an audible alarm, and an IoT-based monitoring dashboard.

Unlike conventional two-point flow comparison methods, the proposed architecture introduces an **intermediate verification point** to physically measure diverted flow before confirming leakage. This additional verification stage significantly improves detection reliability by distinguishing actual leakage from temporary hydraulic disturbances.

<p align="center">
  <img src="Images/Block_Diagram.png" width="850" alt="System Architecture">
</p>

### System Components

- **Inlet Flow Sensor (YFS201)** measures the incoming water flow.
- **Outlet Flow Sensor (YFS201)** measures the outgoing water flow.
- **Intermediate Flow Sensor (YFS401)** measures physically diverted water caused by leakage.
- **ESP32** performs embedded pulse processing and leakage verification.
- **Buzzer** provides immediate audible leakage indication.
- **Node.js Dashboard** displays real-time monitoring data.
- **MongoDB** stores historical flow records and leakage events.

The architecture enables reliable leakage confirmation without relying solely on inferred pressure variations or cloud-based processing. :contentReference[oaicite:0]{index=0}

---

# ⚙ Hardware Components

| Component | Quantity | Purpose |
|-----------|---------:|---------|
| ESP32 Development Board | 1 | Main embedded controller |
| YFS201 Flow Sensor | 2 | Inlet and outlet flow measurement |
| YFS401 Flow Sensor | 1 | Intermediate leakage verification |
| PVC Pipeline | 1 | Experimental pipeline setup |
| PVC Tee Joint | Multiple | Intermediate branch connection |
| Flexible Tubing | As Required | Water circulation |
| Water Pump | 1 | Continuous water circulation |
| Buzzer | 1 | Leakage alarm indication |
| 12V DC Adapter | 1 | Power supply |
| Connecting Wires | As Required | Electrical connections |

---

# 💻 Software Stack

| Software | Purpose |
|-----------|---------|
| Arduino IDE | ESP32 firmware development |
| Embedded C | Leakage detection algorithm |
| Node.js | Backend server |
| MongoDB | Database |
| HTML | Dashboard interface |
| CSS | Dashboard styling |
| JavaScript | Dashboard interaction |
| Wi-Fi | Wireless communication |

---

# 🔄 Working Principle

The leakage detection algorithm follows a dual-stage verification strategy.

### Step 1 – Flow Measurement

Three turbine flow sensors continuously generate pulse signals proportional to the water flow.

- Inlet Flow
- Outlet Flow
- Intermediate Branch Flow

---

### Step 2 – Primary Deviation Detection

The ESP32 continuously calculates the difference between inlet and outlet pulse counts.

```
ΔP = Pin − Pout
```

If the calculated deviation remains within the predefined tolerance, the system continues normal monitoring.

---

### Step 3 – Leakage Verification

When the deviation exceeds the allowable threshold, the system **does not immediately declare leakage**.

Instead, it compares the measured diverted flow with the calculated flow imbalance using the intermediate flow sensor.

Only when both values agree within the verification tolerance is leakage confirmed.

This dual-stage verification significantly reduces false alarms generated by transient hydraulic disturbances. :contentReference[oaicite:1]{index=1}

---

### Step 4 – Alarm Generation

After successful verification:

- Leakage is confirmed.
- Buzzer is activated.
- Event is logged.
- Dashboard is updated.

---

### Step 5 – Real-Time Monitoring

The Node.js web application displays:

- Inlet Flow
- Outlet Flow
- Intermediate Flow
- Leakage Status
- Historical Events

The dashboard is intended for monitoring and logging only.

The ESP32 independently performs all safety-critical decision making, allowing the system to continue operating even if the dashboard or network becomes unavailable. :contentReference[oaicite:2]{index=2}

---

# 🔁 Detection Algorithm

```text
                 Start
                   │
                   ▼
      Read Flow Sensor Pulses
                   │
                   ▼
      Calculate Inlet–Outlet Difference
                   │
                   ▼
     Is Difference > Threshold?
            │             │
           No             Yes
            │              │
            ▼              ▼
 Continue Monitoring   Read Intermediate Sensor
                           │
                           ▼
     Does Physical Flow Match Deviation?
                │                 │
               No                 Yes
                │                  │
                ▼                  ▼
      Ignore Transient      Confirm Leakage
                │                  │
                ▼                  ▼
          Continue         Activate Alarm
                │                  │
                └──────────► Update Dashboard
```

---

# 🌐 Dashboard Features

The web-based dashboard provides a supervisory interface for monitoring system operation.

### Features

- Real-time pulse monitoring
- Leakage status indication
- Historical event logging
- Secure login authentication
- Session management
- MongoDB data storage

<p align="center">
  <img src="Images/Dashboard.png" width="850" alt="Dashboard">
</p>

The dashboard operates independently of the embedded detection logic, ensuring that loss of network connectivity does not affect leakage detection or alarm generation. :contentReference[oaicite:3]{index=3}

---
---

# 📐 Mathematical Model

The proposed leakage detection system employs a **dual-stage verification model** that combines differential pulse analysis with physical flow verification.

### 1️⃣ Primary Flow Deviation

The primary flow deviation is calculated as:

<p align="center">

ΔP = Pin − Pout

</p>

Where:

| Symbol | Description |
|---------|-------------|
| **Pin** | Pulse count measured by the inlet flow sensor |
| **Pout** | Pulse count measured by the outlet flow sensor |
| **ΔP** | Difference between inlet and outlet pulse counts |

If the calculated deviation exceeds the predefined threshold, the system proceeds to the verification stage.

---

### 2️⃣ Leakage Verification Condition

Leakage is confirmed only when the measured intermediate flow corresponds to the calculated inlet–outlet imbalance.

<p align="center">

|(Pin − Pout) − Pmid| ≤ ε

</p>

Where:

| Symbol | Description |
|---------|-------------|
| **Pmid** | Intermediate flow sensor pulse count |
| **ε** | Verification tolerance |

This verification stage distinguishes actual leakage from temporary hydraulic disturbances.

---

### 3️⃣ Verification Tolerance

The verification tolerance is defined as:

<p align="center">

ε = kσn + ec,max

</p>

Where:

| Parameter | Description |
|-----------|-------------|
| **σn** | Standard deviation of measurement noise |
| **k** | Scaling factor |
| **ec,max** | Maximum transient deviation observed experimentally |

The tolerance band improves system robustness while maintaining sensitivity to genuine leakage events. :contentReference[oaicite:1]{index=1}

---

# 🧪 Experimental Setup

The proposed system was experimentally validated using a laboratory-scale PVC pipeline.

### Experimental Hardware

- ESP32 Development Board
- Two YFS201 Flow Sensors
- One YFS401 Flow Sensor
- PVC Pipeline
- Water Pump
- Buzzer
- Web Dashboard
- MongoDB Database

---

### Test Conditions

Three operating conditions were investigated.

### ✅ Normal Flow

- Continuous water circulation
- No intentional leakage
- Stable inlet–outlet flow balance

---

### ✅ Induced Leakage

- Controlled leakage introduced
- Intermediate sensor measured diverted flow
- Leakage confirmed through dual-stage verification

---

### ✅ Transient Flow Disturbances

- Pump switching
- Rapid valve operations
- Temporary hydraulic imbalance

These tests evaluated the system's capability to reject false alarms under dynamic operating conditions. :contentReference[oaicite:2]{index=2}

---

# 📊 Experimental Results

## Normal Operation

Under normal operating conditions:

- Inlet and outlet pulse counts remained nearly equal.
- Intermediate sensor detected negligible flow.
- No leakage alarms were generated.

---

## Induced Leakage

During controlled leakage tests:

- Significant inlet–outlet deviation was observed.
- Intermediate sensor measured diverted flow.
- Leakage was correctly identified.

---

## Transient Disturbances

During pump start-stop cycles and rapid valve operations:

- Temporary pulse imbalance occurred.
- Intermediate sensor did not verify diverted flow.
- No false alarms were generated.

This demonstrates the effectiveness of the proposed dual-stage verification mechanism. :contentReference[oaicite:3]{index=3}

---

# 📈 Performance Evaluation

A total of **50 experimental trials** were conducted.

| Test Category | Number of Tests |
|---------------|----------------:|
| Normal Flow | 20 |
| Leak Condition | 20 |
| Transient Flow Changes | 10 |
| **Total** | **50** |

---

## Classification Results

| Parameter | Value |
|-----------|------:|
| True Positive (TP) | 19 |
| False Negative (FN) | 1 |
| True Negative (TN) | 30 |
| False Positive (FP) | 0 |

---

## Performance Metrics

| Metric | Result |
|---------|--------|
| **Accuracy** | **98%** |
| **Precision** | **100%** |
| **Recall (Sensitivity)** | **95%** |
| **Specificity** | **100%** |
| **False Positive Rate** | **0%** |

These results demonstrate reliable leakage detection while maintaining complete immunity to false alarms during transient hydraulic events. :contentReference[oaicite:4]{index=4}

---

# 📉 Comparative Analysis

The proposed architecture was compared with conventional pipeline leakage detection methods.

| Method | Physical Verification | False Alarm Rejection | Cloud Dependency |
|---------|----------------------|-----------------------|------------------|
| Pressure-Based | ✖ | Moderate | Often Required |
| Acoustic/Vibration | ✖ | Moderate | Sometimes Required |
| AI / Model-Based | ✖ | High | Required |
| Conventional Two-Point Flow Comparison | ✖ | Low | Optional |
| **Proposed Multi-Point Flow Monitoring** | ✔ | **High** | **Not Required** |

The proposed system achieves reliable leakage confirmation through direct physical flow verification while maintaining low computational complexity and eliminating dependence on continuous cloud connectivity. :contentReference[oaicite:5]{index=5}

---

# 💡 Key Outcomes

- Successfully developed a multi-point pipeline monitoring system.
- Achieved **98% detection accuracy**.
- Eliminated false-positive detections during transient flow disturbances.
- Verified leakage through physical flow measurement.
- Implemented real-time embedded decision making using ESP32.
- Enabled remote monitoring through a Node.js dashboard.
- Demonstrated a scalable, low-cost architecture suitable for industrial monitoring applications. :contentReference[oaicite:6]{index=6}

---
---

# 📂 Repository Structure

```text
multi-point-pipeline-leakage-detection
│
├── 📁 Documentation
│   ├── Project_Report.pdf
│   ├── Presentation.pptx
│   └── README.md
│
├── 📁 Hardware
│   ├── Circuit_Diagram.png
│   ├── Pin_Connections.pdf
│   ├── Bill_of_Materials.xlsx
│   └── README.md
│
├── 📁 Images
│   ├── Block_Diagram.png
│   ├── Prototype.jpg
│   ├── Dashboard.png
│   └── Result_Graph.png
│
├── 📁 Publication
│   └── README.md
│
├── 📁 Results
│   ├── Experimental_Data.xlsx
│   ├── Performance_Graphs.pdf
│   └── README.md
│
├── 📁 Software
│   ├── ESP32_Firmware
│   ├── Dashboard
│   └── README.md
│
├── LICENSE
└── README.md
```

---

# 🚀 Getting Started

## Hardware Setup

1. Assemble the PVC pipeline.
2. Install the inlet YFS201 flow sensor.
3. Install the outlet YFS201 flow sensor.
4. Connect the YFS401 sensor to the intermediate branch.
5. Connect all three sensors to the ESP32 GPIO pins.
6. Connect the buzzer.
7. Power the system using a regulated DC supply.

---

## Software Setup

### ESP32 Firmware

1. Install Arduino IDE.
2. Install ESP32 Board Package.
3. Open the firmware.
4. Configure Wi-Fi credentials.
5. Upload the code.

---

### Dashboard

1. Install Node.js.
2. Install MongoDB.
3. Run

```bash
npm install
```

4. Start MongoDB.

5. Run

```bash
npm start
```

6. Open

```text
http://localhost:3000
```

*(Update this URL if your project uses a different port.)*

---

# 🧪 How to Test the System

### Test 1 — Normal Operation

- Start the pump.
- Observe inlet and outlet readings.
- Intermediate sensor should remain inactive.
- No alarm should be generated.

Expected Result:

✅ Normal Operation

---

### Test 2 — Leakage Simulation

- Open the leakage branch.
- Observe intermediate sensor.
- Buzzer should activate.
- Dashboard should display leakage.

Expected Result:

✅ Leakage Detected

---

### Test 3 — Valve Disturbance

- Quickly operate the control valve.
- Observe temporary pulse imbalance.

Expected Result:

✅ No False Alarm

---

# 📷 Prototype Gallery

## Laboratory Prototype

<p align="center">
<img src="Images/Prototype.jpg" width="750">
</p>

The laboratory-scale prototype consists of three turbine flow sensors mounted on a PVC pipeline with an ESP32-based embedded controller. The intermediate branch physically measures diverted flow for leakage verification, enabling reliable experimental validation of the proposed architecture. :contentReference[oaicite:0]{index=0}

---

# 🌐 Web Dashboard

<p align="center">
<img src="Images/Dashboard.png" width="850">
</p>

The Node.js dashboard provides real-time visualization of:

- Inlet Flow
- Outlet Flow
- Intermediate Flow
- Leakage Status
- Historical Event Logs

The dashboard is intended for supervisory monitoring only. All safety-critical leakage detection decisions are executed locally by the ESP32 microcontroller, ensuring continued operation even if network connectivity is lost. :contentReference[oaicite:1]{index=1} :contentReference[oaicite:2]{index=2}

---

# 📄 Publication

This work has been published in an international IEEE conference.

| Item | Details |
|------|---------|
| Conference | International Conference on Smart Electronic Devices and Intelligent Systems (ICSEDIS 2026) |
| Publisher | IEEE |
| Indexing | IEEE Xplore, Scopus |
| DOI | 10.1109/ICSEDIS68157.2026.11518189 |
| ISBN | 979-8-3315-8824-3 |

> **Copyright Notice**
>
> The publisher-formatted IEEE paper is **not included** in this repository.
> Please access the publication through IEEE Xplore using the DOI. :contentReference[oaicite:3]{index=3}

---

# 👨‍💻 My Contribution

My primary contributions to this project include:

- Hardware assembly and system integration
- Experimental setup and testing
- Data collection and validation
- Technical documentation
- Research paper preparation and writing

---

# 💼 Skills Demonstrated

This project demonstrates practical experience in:

- Embedded Systems
- Instrumentation Engineering
- Industrial Automation
- Flow Measurement
- Sensor Integration
- ESP32 Programming
- IoT Systems
- Node.js Development
- MongoDB
- Experimental Validation
- Data Analysis
- Engineering Documentation

---
---

# 🚀 Future Scope

The proposed system establishes a robust foundation for low-cost pipeline leakage detection. Future enhancements can further improve its scalability, intelligence, and industrial applicability.

## Potential Improvements

- Integration with industrial SCADA systems.
- Adaptive threshold optimization based on operating conditions.
- AI/ML-based leakage prediction and classification.
- Cloud-based analytics and remote diagnostics.
- Industrial communication protocol support (Modbus TCP, MQTT, OPC UA).
- SMS, Email, and Telegram alert notifications.
- GPS-based leak localization for long-distance pipelines.
- Deployment on large-scale industrial water distribution networks.
- Mobile application for remote monitoring.
- Digital Twin integration for predictive maintenance.

---

# 📚 References

This work was developed by referring to published research in pipeline leakage detection, embedded systems, and industrial instrumentation.

Key references are available in the published conference paper.

---

# 👥 Authors

| Name | Role |
|------|------|
| **Praveen V. Pol** | Guide |
| **Vikas J. Nandeshwar** | Student Researcher |
| **Tejas R. Kulkarni** | Student Researcher |
| **Sejal M. Mankawade** | Student Researcher |
| **Aditya V. Kulsange** | Student Researcher |
| **Samadhan S. Kendre** | Student Researcher |

---

# 👨‍💻 About Me

Hi, I'm **Tejas R. Kulkarni**, an undergraduate student pursuing **B.Tech in Instrumentation & Control Engineering** at **Vishwakarma Institute of Technology, Pune**.

My primary interests include:

- Industrial Automation
- Embedded Systems
- Instrumentation
- Industrial IoT
- Process Control
- Control Systems
- Industrial Communication
- Measurement Systems

I enjoy developing practical engineering solutions that combine hardware, embedded software, and real-world experimentation.

---

# 🤝 Acknowledgements

I would like to express my sincere gratitude to:

- Vishwakarma Institute of Technology (VIT), Pune
- Department of Instrumentation & Control Engineering
- Our project guide for continuous guidance and support
- All project team members for their valuable contributions

Their support and encouragement made this work possible.

---

# 📄 Citation

If you use this work in your research, project, or academic work, please cite:

```text
P. V. Pol, V. J. Nandeshwar, T. R. Kulkarni,
S. M. Mankawade, A. V. Kulsange, and
S. S. Kendre,

"Development of a Multi-Point Flow Monitoring
System for Accurate Pipeline Leakage Detection,"

Proceedings of the International Conference on
Smart Electronic Devices and Intelligent Systems
(ICSEDIS 2026),

IEEE Xplore,

DOI:
10.1109/ICSEDIS68157.2026.11518189
```

---

## BibTeX

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

# 📜 License

This project is licensed under the **MIT License**.

You are free to:

- Use
- Modify
- Distribute
- Learn from

this project under the terms of the MIT License.

See the **LICENSE** file for complete details.

---
