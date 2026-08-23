# Mini Room Monitor

A low-cost Arduino-based environmental monitoring system that measures room temperature, humidity, and gas-sensor response using a DHT22 and MQ-135.

The project combines an Arduino UNO-based sensor system with a MAX7219 LED matrix, a local web dashboard, and optional AI-powered interpretation through OpenRouter.

The Arduino collects the sensor readings and sends them to a local computer through serial communication. The local server processes the incoming data and provides it to a custom web dashboard, where the current environmental readings can be viewed in a more convenient interface.

An AI model connected through OpenRouter can additionally interpret the sensor readings and provide a human-readable explanation of the current room conditions.

---

## Features

- 🌡️ Real-time temperature monitoring
- 💧 Real-time humidity monitoring
- 🧪 MQ-135 gas sensor monitoring
- 📊 Individual gas-related sensor information
- 🔢 MAX7219 8×8 LED matrix display
- 🔌 Arduino UNO-based hardware
- 💻 Serial communication between Arduino and computer
- 🌐 Custom local web dashboard
- 🤖 AI-powered environmental interpretation using OpenRouter
- 📱 Browser-based dashboard interface
- 📡 Local server for handling sensor data
- 🧩 Modular hardware and software architecture
- 💾 Low-cost and educational design

---

## Project Overview

The Mini Room Monitor is designed as a small environmental monitoring system for observing basic conditions inside a room.

The Arduino UNO acts as the main controller. It reads data from the DHT22 temperature and humidity sensor and the MQ-135 gas sensor.

The collected readings are also shown locally using a MAX7219 LED matrix display.

For a more detailed view, the Arduino sends the readings through USB serial communication to a computer running the project's local server.

The server receives the sensor data and makes it available to a custom HTML-based dashboard.

The dashboard provides a visual representation of the current readings and can send the sensor information to an AI model through OpenRouter for additional interpretation.

---

## System Architecture

```text
                 ┌──────────────────────┐
                 │      Arduino UNO     │
                 │     Main Controller  │
                 └──────────┬───────────┘
                            │
             ┌──────────────┼──────────────┐
             │              │              │
             ▼              ▼              ▼
          DHT22           MQ-135        MAX7219
       Temperature &     Gas Sensor      LED Matrix
         Humidity
             │              │
             └───────┬──────┘
                     │
                     ▼
               Sensor Readings
                     │
                     ▼
              USB Serial Data
                     │
                     ▼
            ┌──────────────────┐
            │   Local Server   │
            └────────┬─────────┘
                     │
                     ▼
            ┌──────────────────┐
            │   Web Dashboard  │
            │ HTML / CSS / JS  │
            └────────┬─────────┘
                     │
                     ▼
            ┌──────────────────┐
            │   OpenRouter AI  │
            │   Interpretation │
            └──────────────────┘
