# -T-BOX-
基于车载 T-BOX 设计要求，搭建了一个可运行的“通信子模块 Demo”，实现传感器数据采集、电源与接口电路搭建、数据打包处理与 MQTT 上行通讯，用于模拟车载终端对云平台的上报流程
# T-BOX Communication Module Demo (ESP32-C3)

This project implements a minimal T-BOX communication module demo using ESP32-C3.  
It simulates a vehicle terminal uploading sensor data to a cloud MQTT server through 
UART acquisition → data framing → JSON packaging → MQTT uplink.

This repository aims to demonstrate hardware debugging ability, embedded C development,
communication protocol design, and engineering documentation ability.

---

## ✨ Features
- UART-based sensor acquisition (Rx/Tx)
- Data frame parsing & CRC check
- JSON packaging (heartbeat/status/sensor data)
- MQTT client uplink to local Mosquitto server
- Oscilloscope/serial-based debugging
- Reusable modular firmware design

---

## 📡 Hardware Setup

| Module | Description |
|--------|-------------|
| ESP32-C3 DevKit | Main MCU; WiFi MQTT client |
| UART Sensor (e.g. PM2.5 / Temp Sensor) | Provides raw data frames |
| DC-DC 5V→3.3V | Power supply module |
| USB-to-UART tool | Serial debugging |
| Breadboard & Dupont wires | Wiring test environment |

See hardware/wiring_diagram.md for wiring.

---

## 📁 Repository Structure

firmware/ # ESP-IDF source code
hardware/ # Hardware wiring & module description
docs/ # Protocol + debugging notes

yaml
复制代码

---

## 🧪 How to Run

1. Install ESP-IDF (latest recommended)
2. Configure WiFi + MQTT broker in `mqtt_upload.c`
3. Compile & flash:
idf.py set-target esp32c3
idf.py build
idf.py flash monitor

markdown
复制代码
4. Start Mosquitto:
mosquitto -v

csharp
复制代码
5. Observe JSON frames on topic:
tbox/data/upload

yaml
复制代码

---

## 📝 License
MIT License
