<!-- ========================================================= -->
<!--                        PROJECT BANNER                     -->
<!-- ========================================================= -->

<p align="center">
  <img src="Images/prototype.jpg" alt="Prototype" width="900"/>
</p>

<h1 align="center">
Development of a Multi-Point Flow Monitoring System for Accurate Pipeline Leakage Detection
</h1>

<p align="center">

![ESP32](https://img.shields.io/badge/ESP32-Embedded-blue)

![Arduino](https://img.shields.io/badge/Arduino-IDE-00979D)

![IoT](https://img.shields.io/badge/IoT-Enabled-success)

![IEEE](https://img.shields.io/badge/Published-IEEE%20Xplore-blue)

![Scopus](https://img.shields.io/badge/Indexed-Scopus-orange)

</p>

---

# Abstract

Pipeline leakage is one of the major causes of water loss, operational inefficiency, economic damage, and safety risks in industrial and municipal pipeline networks. Conventional leak detection methods primarily rely on two-point flow comparison or pressure-based monitoring, which often generate false alarms during transient operating conditions such as pump start-up, pump shut-down, or rapid valve actuation.

This project presents a **Multi-Point Flow Monitoring System** that improves leakage detection reliability using three turbine flow sensors and an ESP32 microcontroller. Instead of relying solely on inlet–outlet flow imbalance, the proposed architecture introduces an intermediate verification point that physically measures diverted flow before confirming leakage. This dual-stage verification significantly reduces false-positive detections while maintaining high sensitivity to genuine leakage events.

The embedded controller performs all decision-making locally for real-time operation, while a web-based monitoring dashboard provides remote visualization, event logging, and supervisory monitoring. Experimental validation demonstrated **98% leakage detection accuracy**, **100% precision**, and **zero false-positive detections** during transient flow disturbances.

---

# Technologies Used

| Category | Technologies |
|-----------|--------------|
| Microcontroller | ESP32 |
| Sensors | YFS201 Flow Sensor, YFS401 Flow Sensor |
| Programming | Embedded C / Arduino |
| Dashboard | Node.js |
| Database | MongoDB |
| Communication | Wi-Fi |
| Domain | Instrumentation & Control Engineering |

---
