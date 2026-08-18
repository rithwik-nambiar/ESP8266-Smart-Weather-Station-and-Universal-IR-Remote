# ESP8266 Smart Weather Station & Universal IR Remote Hub 🌦️📡

A high-performance desktop companion built on the **ESP8266**. This project features an intelligent context-switching system that toggles between network-heavy tasks (Weather/NTP) and timing-critical hardware tasks (IR Cloning).

## 📸 Interface Preview

| 1. Dashboard Mode | 2. IR Control Mode | 3. Naming Signal |
| :--- | :--- | :--- |
| ![Dashboard](images/dashboard.jpg) | ![IR Mode](images/ir_mode.jpg) | ![Keyboard](images/keyboard.jpg) |
| *Real-time Weather & NTP Clock* | *Cloning & hardware control* | *Custom HMI Touch Keyboard* |

## 🚀 Key Features
* **Auto Resource Management:** The system deactivates the WiFi during IR capture to eliminate CPU interrupts, ensuring microsecond precision for decoding IR signals from any device.
* **On-Screen Keyboard:** A custom-coded QWERTY touch interface allows for naming captured IR signals directly on the device.
* **Non-Volatile Storage (SPIFFS):** Uses the ESP8266's internal Flash memory to store captured signals, ensuring data persists after a reboot.
* **Dynamic Weather Engine:** Fetches live data (Temp, Humidity, Conditions) from OpenWeatherMap API with 10-minute refresh intervals and NTP time sync.

## 🛠️ Components Used :
1. **Microcontroller:** ESP8266 (NodeMCU)
2. **Display:** 2.4" TFT LCD (ILI9341) using `TFT_eSPI` library.
3. **Peripherals:** IR Receiver,2N2222 Transistor, IR Transmitter LED
4. **Logic:** REST API integration, JSON parsing, SPIFFS File Management.

## 🔧 Installation & Setup
1.  **Hardware:** Connect components as per the code's defined GPIO pins.
2.  **Credentials** Enter your WiFi credentials and OpenWeatherMap API Key.
3.  **Calibration:** On first boot, the system triggers a touch calibration. Results are saved to `/touch.cal` in SPIFFS.

## 🔌 Hardware Connections & Pinout

This project uses a 2N2222A NPN transistor as a high-current switch to drive the IR LED for maximum range without damaging the ESP8266 GPIO pins.

| Component | Pin Name | ESP8266 Pin |
| :--- | :--- | :--- |
| **TFT Display** | VCC / LED | **3V3** |
| | GND | **GND** |
| | CS | **D8 (GPIO 15)** |
| | DC / RS | **D3 (GPIO 0)** |
| | SDI (MOSI) | **D7 (GPIO 13)** |
| | SCK (CLK) | **D5 (GPIO 14)** |
| **IR Receiver** | Data Out | **D4 (GPIO 2)** |
| | VCC / GND | **3V3 / GND** |
| **IR Transmitter**| **Base** | **D1 (GPIO 5)** |
| **(2N2222A)** | **Emitter** | **GND** |
| | **Collector** | **IR LED (-)** |
| **IR LED** | Anode (+) | **3V3** |

## 📄 License
This project is licensed under the **MIT License**.

---
**Developed by [Rithwik Nambiar](https://github.com/rithwik-nambiar)** *Aspiring Embedded Systems Engineer*
