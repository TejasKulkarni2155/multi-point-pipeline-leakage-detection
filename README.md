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

> **Publication:** International Conference on Smart Electronic Devices and Intelligent Systems (ICSEDIS 2026) | IEEE Xplore | Scopus Indexed | DOI: 10.1109/ICSEDIS68157.2026.11518189 :contentReference[oaicite:4]{index=4}
