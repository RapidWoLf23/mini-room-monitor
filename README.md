# Mini Room Monitor

A compact Arduino-based room monitoring system that measures temperature, humidity, and gas sensor values using multiple sensors and displays the readings on a MAX7219 LED matrix.

The project also provides a local web dashboard for viewing the sensor readings in a more convenient interface. An AI model accessed through OpenRouter can be connected to the local dashboard to interpret and present the sensor data.

---

## Introduction

The Mini Room Monitor is a simple embedded-system project designed to monitor basic environmental conditions inside a room.

The system uses an Arduino Uno as the main controller and collects data from:

- DHT22 temperature and humidity sensor
- MQ-135 gas sensor
- MAX7219 8×8 LED matrix display

The sensor readings are processed by the Arduino and displayed locally on the LED matrix. The readings can also be sent to a computer through serial communication, where a locally hosted web dashboard can display the information.

The project combines basic electronics, sensor interfacing, Arduino programming, serial communication, web development, and AI-assisted data interpretation.

---

## Features

- 🌡️ Temperature monitoring using DHT22
- 💧 Relative humidity monitoring using DHT22
- 🧪 MQ-135 gas sensor monitoring
- 📊 Displays sensor readings on a MAX7219 LED matrix
- 💻 Local web-based monitoring dashboard
- 🔌 Arduino Uno based system
- 📡 Serial communication between Arduino and computer
- 🤖 Optional AI-assisted interpretation through OpenRouter
- 📦 Simple and low-cost hardware setup
- 🛠️ Designed as an educational electronics and IoT-style project

---

## Hardware Used

| Component | Purpose |
|---|---|
| Arduino Uno | Main microcontroller |
| DHT22 | Temperature and humidity measurement |
| MQ-135 | Gas sensing |
| MAX7219 8×8 LED Matrix | Displays sensor information |
| Breadboard | Circuit prototyping |
| Jumper Wires | Electrical connections |
| USB Cable | Arduino power and serial communication |

---

## Gas Sensor

The MQ-135 is a general-purpose gas sensor commonly used for detecting changes associated with several gases and air contaminants.

Depending on the sensor configuration and calibration, it can respond to gases such as:

- Ammonia (NH₃)
- Nitrogen oxides (NOx)
- Alcohol vapors
- Benzene
- Smoke
- Carbon dioxide (CO₂)

The MQ-135 provides an analog sensor output. The value produced by the sensor is affected by the concentration of gases as well as environmental conditions.

**Important:** The raw MQ-135 analog value is not directly equivalent to a precise gas concentration in ppm. Proper calibration and gas-specific characterization are required for accurate quantitative measurements.

---

## System Architecture

```text
              ┌────────────────────┐
              │    DHT22 Sensor    │
              │ Temperature/Humid. │
              └─────────┬──────────┘
                        │
                        │
              ┌─────────▼──────────┐
              │                    │
              │    Arduino Uno     │
              │                    │
              └──────┬───────┬─────┘
                     │       │
             ┌───────┘       └─────────┐
             │                         │
      ┌──────▼──────┐           ┌──────▼──────┐
      │   MQ-135    │           │   MAX7219    │
      │ Gas Sensor  │           │  LED Matrix  │
      └─────────────┘           └──────────────┘
                     │
                     │ USB / Serial
                     ▼
              ┌────────────────┐
              │ Local Computer │
              │ Web Dashboard  │
              └───────┬────────┘
                      │
                      ▼
              ┌────────────────┐
              │ Optional AI    │
              │ Interpretation │
              └────────────────┘
