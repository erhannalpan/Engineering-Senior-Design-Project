## 📌 Introduction
This project implements a fully portable inside-out tracking system for Virtual Reality, capable of estimating real-time 6-Degree-of-Freedom (6-DoF) head pose without any external sensors. Using a Raspberry Pi Camera Module running ORB-SLAM3 and a BNO055 9-axis IMU, the system fuses positional and rotational data through a Kalman filter on a Raspberry Pi 5 (16 GB). Fused pose data is transmitted wirelessly to a PC using Wi-Fi (UDP), where it is visualized with a Python VTK 3D head model. The system is lightweight, battery-powered, and designed to deliver accurate, low-latency VR tracking within a fully self-contained hardware platform.

## ✨ Features
- Real-time 6-DoF head-pose estimation  
- ORB-SLAM3 visual odometry  
- IMU + camera Kalman fusion to reduce drift  
- Low-latency UDP wireless communication  
- Python VTK 3D head-pose visualization  
- Battery-powered, portable, and lightweight  
- Operates without external base stations  

## 🎯 Goals
- Provide accurate 6-DoF tracking using only onboard sensors  
- Maintain orientation error ≤ ±10° and positional error ≤ ±10 cm  
- Keep wireless latency below 20 ms and rendering latency below 200 ms  
- Achieve at least 4 hours of continuous operation on a single powerbank  
- Deliver a self-contained, easy-to-wear VR tracking solution  

## 🧩 Subsystems
**Sensor Suite Subsystem:**  
Includes the BNO055 IMU for rotational data and the Raspberry Pi Camera Module for visual odometry. ORB-SLAM3 extracts environmental features, while the IMU provides real-time inertial measurements.

**Sensor Fusion Subsystem:**  
A 9×9 Kalman Filter combines IMU and camera measurements to minimize drift, stabilize pose estimation, and maintain high-accuracy tracking during fast or slow movements.

**Processing Unit Subsystem:**  
A Raspberry Pi 5 (16 GB) runs image processing, SLAM, IMU handling, fusion algorithms, and UDP data transmission.

**Communication Subsystem:**  
Uses Wi-Fi (P2P) and UDP sockets to transmit fused pose data at low latency (~6 ms TCP test equivalent, UDP faster).

**Visualization Subsystem:**  
A Python VTK renderer displays real-time head orientation and position in 3D at ~32 FPS with total system delay ~200 ms.

## 📊 Test Results (Objective Measurements)
- **Orientation Accuracy:** ±0.1° to ±7° (within ±10° requirement)  
- **Positional Accuracy:** Within ±10 cm after fusion  
- **Wireless Latency:** ~6 ms (TCP test), UDP < 6 ms  
- **Rendering Latency:** ~200 ms average  
- **Frame Rate:** ~32 FPS  
- **Battery Lifespan:** 4.18–4.93 hours  
- **Power Consumption:** 11–15 W depending on load  

## 🧪 Testing Overview
Testing included IMU-only measurements, camera-only SLAM accuracy tests, fusion validation, UDP latency tests, TCP RTT estimation, rendering performance evaluation, and power subsystem stress tests. Translation tests across X/Y/Z axes and rotational tests across roll/pitch/yaw confirmed that fused outputs meet system-level accuracy requirements. Battery runtime tests using a Xiaomi 20000 mAh 3 Pro powerbank demonstrated over 4 hours of sustained usage. Communication tests verified stable, low-latency data transfer, and visualization tests achieved smooth rendering at ~32 FPS with acceptable delay. All subsystems successfully met or exceeded the defined requirements.



[![Demo Video](https://img.youtube.com/vi/4jYGMu5-sZk/0.jpg)](https://youtu.be/4jYGMu5-sZk)

