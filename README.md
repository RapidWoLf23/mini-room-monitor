# Mini Room Monitor

A simple Arduino-based room monitoring system that measures temperature, humidity, and air-quality-related gas sensor values using a DHT22 and MQ-135 sensor.

The project displays sensor readings on a MAX7219 LED matrix and also provides a local web dashboard for viewing the readings. An AI model can be connected through OpenRouter to provide a simple interpretation of the collected environmental data.

---

## Features

- 🌡️ Temperature monitoring using DHT22
- 💧 Relative humidity monitoring using DHT22
- 🧪 MQ-135 gas sensor monitoring
- 📊 Displays gas sensor readings without calculating an overall AQI
- 🔴 MAX7219 8×8 LED matrix display
- 💻 Local web-based dashboard
- 🤖 Optional AI-powered environmental interpretation using OpenRouter
- 🔌 Arduino UNO based hardware
- 📡 Sensor data can be transferred to the local dashboard through the connected computer
- 📁 Simple project structure suitable for learning and experimentation

---

## Introduction

The **Mini Room Monitor** is a small electronics and software project designed to monitor basic environmental conditions inside a room.

The Arduino reads temperature and humidity from the **DHT22 sensor** and obtains the analog output of the **MQ-135 gas sensor**. The readings are displayed locally using an **8×8 MAX7219 LED matrix**.

The sensor data can also be sent to a computer and displayed through a locally hosted web dashboard. The dashboard provides a more convenient way to view the readings and can optionally use an AI model through **OpenRouter** to interpret the collected environmental information.

The project is intended primarily for **educational and experimental purposes** rather than professional environmental measurement.

---

## Hardware Used

- Arduino UNO
- DHT22 temperature and humidity sensor
- MQ-135 gas sensor
- MAX7219 8×8 LED matrix module
- Breadboard
- Jumper wires
- USB cable
- Computer for the local dashboard

---

## Sensors

### DHT22

The DHT22 is used to measure:

- Temperature
- Relative humidity

The sensor provides digital temperature and humidity readings to the Arduino.

### MQ-135

The MQ-135 is a general-purpose gas sensor whose sensitivity can vary with different gases and environmental conditions.

It is commonly associated with sensitivity to gases such as:

- Ammonia (NH₃)
- Nitrogen oxides (NOx)
- Alcohol vapours
- Benzene
- Smoke
- Carbon dioxide (CO₂)

In this project, the MQ-135 is used to provide a **sensor reading representing the detected gas response**.

The project does **not** convert the MQ-135 reading into an overall AQI value or claim laboratory-grade gas concentration measurements.

> **Note:** The MQ-135 is not a calibrated multi-gas analyzer. Accurate concentration measurements require appropriate calibration, controlled conditions, and gas-specific characterization.

---

## Display

A **MAX7219 8×8 LED matrix** is used as the local display.

The Arduino can cycle through environmental readings such as:

- Temperature
- Humidity
- MQ-135 sensor value

This allows the project to provide basic information without requiring a computer or web dashboard.

---

## Web Dashboard

The project also includes a locally hosted web dashboard.

The dashboard provides a visual interface for viewing:

- Temperature
- Humidity
- MQ-135 gas sensor value
- Gas-related sensor information

The dashboard is designed to make the sensor readings easier to understand than viewing raw serial output.

The dashboard runs locally and does not require the Arduino itself to have Wi-Fi connectivity.

---

## AI Integration

The project can optionally use an AI model through **OpenRouter**.

The local dashboard can send the sensor readings to the configured AI service, which can then provide a human-readable interpretation of the current environmental conditions.

For example, the AI can help explain whether the current temperature, humidity, and sensor readings appear relatively normal or unusual.

### Important

The OpenRouter API key should **never be stored directly in the public GitHub repository**.

Use an environment variable or another secure configuration method when connecting the dashboard to OpenRouter.

Do not upload API keys, passwords, tokens, or other private credentials to GitHub.

---

## How It Works

The basic data flow is:

```text
DHT22 ───────────────┐
                     │
MQ-135 ──────────────┼──> Arduino UNO
                     │
MAX7219 LED Matrix <─┘
                     │
                     ▼
                Serial Data
                     │
                     ▼
             Local Web Server
                     │
                     ▼
               Web Dashboard
                     │
                     ▼
            Optional AI Analysis
                 (OpenRouter)
