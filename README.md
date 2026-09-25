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

## 🔧 Hardware Used

### MPU6050

- 6-axis IMU
- 3-axis accelerometer
- 3-axis gyroscope
- Motion detection capability
- I²C communication
- Interrupt output

### Arduino Uno

- ATmega328P microcontroller
- 16 MHz clock
- I²C interface
- External interrupt
- Low-power sleep modes

## 💻 Software

-Arduino IDE
-Embedded C/C++
-I²C communication
-AVR sleep/power management
-Arduino Serial Monitor
-Arduino Serial Plotter

## ⚙️ Working Principle

-The MPU6050 is initialized and configured.
-Motion detection thresholds are configured.
-The Arduino configures the MPU6050 interrupt.
-During inactivity, the Arduino enters low-power sleep mode.
-The MPU6050 continues monitoring motion.
-When motion crosses the configured threshold, the MPU6050 generates an interrupt.
-The Arduino wakes up.
-Accelerometer and gyroscope data are read through I²C.
-The data is displayed using the Serial Plotter.
-After a predefined period of inactivity, the Arduino returns to sleep mode.

##🔌 Interface

-MPU6050 → Arduino Uno
-MPU6050	Arduino Uno
-VCC	5V
-GND	GND
-SDA	A4
-SCL	A5
-INT	Digital Pin 2

## 📊 Motion Data

The system acquires six motion parameters:

AcX – X-axis acceleration
AcY – Y-axis acceleration
AcZ – Z-axis acceleration
GyX – X-axis angular velocity
GyY – Y-axis angular velocity
GyZ – Z-axis angular velocity

These values are visualized as real-time waveforms using the Arduino Serial Plotter.

##🔋 Low-Power Technique

The main power-saving technique is event-driven operation.

Instead of continuously polling the IMU:

No Motion
    ↓
Arduino Sleep
    ↓
MPU6050 monitors motion
    ↓
Motion detected
    ↓
Interrupt generated
    ↓
Arduino wakes
    ↓
Read IMU data
    ↓
Process / Display data
    ↓
No motion timeout
    ↓
Arduino Sleep

Unused Arduino peripherals such as ADC, SPI and timers can also be disabled during sleep to reduce power consumption.

## 📈 Results

The implemented system demonstrates:

Motion-triggered wake-up
Real-time accelerometer and gyroscope data
Low-power operation during inactivity
Sleep/wake transitions
Real-time waveform visualization
Interrupt-driven motion detection

The project report documents wake-up latency below 100 ms and 20 Hz sampling during active periods under the reported test setup.

## 🚀 Applications
-Wearable devices
-Fitness trackers
-AR/VR motion tracking
-Robotics
-Drones and UAVs
-Gesture-controlled systems
-Portable electronics
-IoT devices

## 🔮 Future Scope

Possible improvements include:

Custom low-power RTL hardware
Sensor-fusion algorithms
Wireless connectivity
Additional sensors
Hardware acceleration for motion processing
Dedicated low-power MCU
Integration into a low-power SoC

The project report specifically identifies custom RTL implementation of filtering, motion classification and wake-up detection as a future direction toward a dedicated low-power SoC.

## 📚 Documentation

The complete project report and presentation are available in the docs/ directory.

##👩‍💻 Project Team
Likhitha CT
Sahana T S
Kruthika RG
Sahana A

Department of Electronics & Communication Engineering
Atria Institute of Technology, Bengaluru

## Project Type

Academic Mini Project
Visvesvaraya Technological University (VTU)

**Technologies:** `Arduino` `MPU6050` `Embedded C/C++` `I²C` `Interrupts` `Low-Power Design` `Wearable Systems`

