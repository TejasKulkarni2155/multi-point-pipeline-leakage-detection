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

Pipeline leakage can cause significant water loss, operational inefficiency, equipment damage, and financial losses. Conventional approaches based on pressure monitoring or inlet–outlet flow comparison may generate false alarms during transient hydraulic conditions such as pump switching and rapid valve operation.

This project presents a **multi-point flow monitoring system** that combines differential flow measurement with **physical verification of diverted flow**. Three turbine flow sensors are connected to an ESP32, which performs leakage detection locally. A Node.js-based web dashboard provides real-time monitoring and event logging.

The system was experimentally evaluated under normal flow, induced leakage, and transient operating conditions.

### Key Results

| Metric | Result |
|---|---:|
| Experimental Trials | **50** |
| Detection Accuracy | **98%** |
| Precision | **100%** |
| Recall / Sensitivity | **95%** |
| Specificity | **100%** |
| False Positives | **0** |

---

## 🎯 Objectives

- Develop a multi-point flow monitoring system using three turbine flow sensors.
- Detect leakage through inlet–outlet flow deviation.
- Physically verify diverted flow using an intermediate sensor.
- Reduce false alarms during transient hydraulic conditions.
- Perform real-time leakage decisions locally using an ESP32.
- Provide web-based monitoring and historical event logging.

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
- Operation independent of continuous cloud connectivity

---

## 🏗️ System Architecture

The system uses three flow measurement points:

1. **Inlet Flow Sensor** — measures incoming pipeline flow.
2. **Outlet Flow Sensor** — measures outgoing pipeline flow.
3. **Intermediate Flow Sensor** — measures physically diverted flow through the leakage branch.

The ESP32 processes the sensor pulse signals and performs leakage verification locally. When leakage is confirmed, the system activates the buzzer and updates the monitoring system.

<p align="center">
  <img src="Images/Block_Diagram.png" alt="System Architecture" width="850">
</p>

### Hardware

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

The leakage detection process uses a two-stage verification strategy.

### 1. Flow Measurement

The three turbine flow sensors continuously generate pulse signals proportional to the measured flow.

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
