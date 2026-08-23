# Mini Room Monitor

A compact Arduino-based room monitoring system that measures **temperature, humidity, and gas sensor readings** and displays the collected information locally using an LED matrix display.

The project combines simple environmental sensors with an Arduino UNO and a custom web dashboard. Sensor data can be viewed locally through the dashboard, while an AI model connected through **OpenRouter** can be used to interpret the collected readings.

---

## Introduction

The **Mini Room Monitor** is a low-cost environmental monitoring project built using an **Arduino UNO**, **DHT22**, **MQ-135 gas sensor**, and a **MAX7219 LED matrix display**.

The system continuously collects environmental data and provides a simple way to observe the conditions of a room.

The Arduino handles the sensor readings and local display, while a computer-based local server can receive the data and present it through a custom HTML dashboard.

An AI model can also be connected through OpenRouter to analyze the sensor readings and provide a more understandable interpretation of the environment.

---

## Features

- 🌡️ **Temperature monitoring**
- 💧 **Humidity monitoring**
- 🧪 **MQ-135 gas sensor readings**
- 📊 **Gas sensor values displayed individually**
- 🔢 **MAX7219 LED matrix display**
- 🖥️ **Custom local web dashboard**
- 🤖 **AI-assisted sensor interpretation**
- 🔌 **Arduino UNO based system**
- 📡 **Serial communication between Arduino and computer**
- 💾 **Simple and low-cost hardware**
- 🧩 **Modular sensor-based design**

---

## Hardware Used

- Arduino UNO
- DHT22 Temperature & Humidity Sensor
- MQ-135 Gas Sensor
- MAX7219 8×8 LED Matrix Display
- Breadboard
- Jumper Wires
- USB Cable
- Computer for the local dashboard and AI integration

---

## Software Used

- Arduino IDE
- C++ / Arduino
- HTML
- CSS
- JavaScript
- Local server
- OpenRouter API
- AI model through OpenRouter

---

## Sensors

### DHT22

The DHT22 is used to measure:

- Temperature
- Relative Humidity

The readings are periodically collected by the Arduino and sent to the connected system.

### MQ-135

The MQ-135 is a general-purpose gas sensor commonly used for detecting changes in the concentration of several gases.

Depending on the sensor's configuration and calibration, it can respond to gases including:

- Ammonia (NH₃)
- Nitrogen oxides (NOx)
- Alcohol vapors
- Benzene
- Smoke
- Carbon dioxide (CO₂)

> **Note:** The MQ-135 is not a laboratory-grade gas analyzer. Its raw analog output is affected by sensor calibration, temperature, humidity, warm-up time, and other environmental factors. The project therefore treats the MQ-135 output primarily as a gas-response reading rather than an exact concentration measurement.

---

## Display

A **MAX7219 8×8 LED matrix** is used as the local display.

The matrix can display sensor information directly from the Arduino, allowing basic readings to be viewed without opening the web dashboard.

---

## System Architecture

```text
                ┌──────────────────────┐
                │      Arduino UNO     │
                └──────────┬───────────┘
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
          DHT22         MQ-135       MAX7219
       Temp/Humidity    Gas Sensor    LED Matrix
             │             │
             └──────┬──────┘
                    │
                    ▼
              Serial Data
                    │
                    ▼
          ┌───────────────────┐
          │   Local Server    │
          └─────────┬─────────┘
                    │
                    ▼
          ┌───────────────────┐
          │  Web Dashboard    │
          └─────────┬─────────┘
                    │
                    ▼
          ┌───────────────────┐
          │ AI Interpretation │
          │   OpenRouter      │
          └───────────────────┘
