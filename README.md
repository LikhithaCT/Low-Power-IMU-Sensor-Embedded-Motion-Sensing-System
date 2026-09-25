# Low Power IMU Sensor for Wearable Devices

A low-power, interrupt-driven motion sensing system designed for wearable and battery-operated applications using an MPU6050 6-axis IMU and Arduino Uno.

## 📌 Overview

Wearable devices such as AR/VR headsets, fitness trackers, smart glasses, and gesture-controlled systems require continuous motion sensing while maintaining low power consumption.

Traditional systems continuously poll IMU data, keeping the microcontroller active even when there is no movement. This project addresses this problem using an interrupt-driven architecture.

The MPU6050 continuously monitors motion using its internal motion detection capability. When motion exceeds the configured threshold, the MPU6050 generates an interrupt that wakes the Arduino Uno from low-power sleep mode.

During active motion, accelerometer and gyroscope data are acquired through I²C and visualized using the Arduino Serial Plotter.

## 🎯 Objectives

- Design a low-power IMU-based motion sensing system.
- Implement interrupt-driven wake-up functionality.
- Keep the microcontroller in low-power sleep mode during inactivity.
- Acquire real-time accelerometer and gyroscope data.
- Reduce unnecessary processing and energy consumption.
- Demonstrate the suitability of the approach for wearable applications.

## 🏗️ System Architecture

```text
                  ┌─────────────────┐
                  │    MPU6050      │
                  │    6-Axis IMU   │
                  └────────┬────────┘
                           │
                     Motion Detection
                           │
                         INT
                           │
                           ▼
                  ┌─────────────────┐
                  │   Arduino Uno   │
                  │                 │
                  │  Sleep / Wake   │
                  │    Control      │
                  └────────┬────────┘
                           │
                          I²C
                           │
                           ▼
                  ┌─────────────────┐
                  │ Real-Time Data  │
                  │   Processing    │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │ Serial Plotter  │
                  │ AcX AcY AcZ     │
                  │ GyX GyY GyZ     │
                  └─────────────────┘
