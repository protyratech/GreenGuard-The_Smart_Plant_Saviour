# 🌱 GreenGuard — The Smart Plant Saviour

An IoT-powered automatic irrigation system that monitors soil moisture, temperature, and humidity in real time. It automatically controls a water pump using a relay module to maintain healthy plant growth while conserving water.

## 🚀 Features

- 🌱 Real-time soil moisture monitoring
- 🌡️ Temperature and humidity measurement
- 💧 Automatic water pump control
- 📟 OLED live data display
- ☁️ IoT cloud monitoring support
- 🌾 Smart agriculture application

## 🛠️ Hardware Components

| Component | Quantity |
|---|---|
| Arduino UNO R4 WiFi | 1 |
| OLED SSD1306 Display | 1 |
| DHT11 Sensor | 1 |
| Soil Moisture Sensor | 1 |
| Relay Module | 1 |
| DC Water Pump | 1 |
| Breadboard | 1 |

## Description

### 🔧 1. Physical Assembly

#### Step 1 – Prepare Breadboard & Power

- Place the Arduino UNO R4 WiFi on your workbench and connect the USB Type-C cable for programming.
- Place the OLED display, DHT11 sensor, and Soil Moisture sensor on the breadboard.
- Connect all common grounds (GND) together.
- Connect all positive (VCC/5V) lines together.

---

#### Step 2 – Hook Up Sensors

##### 🌱 Soil Moisture Sensor (Capacitive Type)

- VCC → 5V
- GND → GND
- AO (Analog Output) → A0

##### 🌡️ DHT11 Sensor

- VCC → 5V
- GND → GND
- DATA → D2

##### 📟 OLED Display (SSD1306, I²C)

- SDA → Arduino SDA
- SCL → Arduino SCL
- VCC → 5V
- GND → GND

---

#### Step 3 – Connect the Relay Module

- Relay VCC → 5V (Arduino UNO R4 WiFi)
- Relay GND → GND (Arduino UNO R4 WiFi)
- Relay IN → D3 (Arduino UNO R4 WiFi)

---

#### Step 4 – Connect the Pump & Power

- Use a separate power supply for the pump (match the pump’s rated voltage, e.g., 5V to 12V).
- Connect the pump negative (−) → Pump power supply negative (−).
- Connect the pump power supply negative (−) to Arduino UNO R4 WiFi GND (common ground).
- Connect pump positive (+) → Relay COM terminal.
- Connect the pump power supply positive (+) → Relay NO terminal.

---

#### Step 5 – Safety Checks

- Verify the relay rating is equal to or higher than your pump current.
- For mains/AC pumps, use a proper AC-rated relay or SSR and ensure full electrical isolation.
- Insulate all exposed terminals with heat-shrink or electrical tape.

---

### 💻 2. Software / Uploading Code

1. Open Arduino IDE and select **Arduino UNO R4 WiFi** as your board.

2. Install required libraries (if not already installed):

    - **WiFiS3**
    - **PubSubClient**
    - **DHT Sensor Library**
    - **Adafruit GFX**
    - **Adafruit SSD1306**

3. Paste the final Arduino code.

4. Update your WiFi SSID and password, as well as your ThingsBoard token.

5. Upload the sketch.

6. Open Serial Monitor (**9600 baud**) to check debug messages.

---

### 🌱 3. Calibrate Soil Sensor & Set Threshold

1. Place the sensor in dry air.
   - Analog value ≈ 1023

2. Place the sensor in wet soil.
   - Analog value ≈ 300–400
  
3. Choose a suitable moisture threshold.
    - Example: Dry Soil = 950, Wet Soil = 300, Threshold ≈ 600–700

4. Update this line in the code:
   - const int moistureThreshold = XXX;

5. Re-upload the sketch.

---

### 💧 4. Verify Pump Control

- Open the Serial Monitor and observe the soil moisture value.
- Remove the sensor from the soil (simulate dry soil).
- Pump turns ON using relay.
- Insert the sensor into moist soil.
- Pump turns OFF using relay.
- Use a multimeter to confirm relay NO/COM switching.

---

### 📟 5. OLED Display

- The OLED displays:
   - Soil Moisture
   - Temperature (°C)
   - Humidity (%)
   - Raw Value
   - Pump Status (ON/OFF)

---

### 🛠️ 6. Troubleshooting Checklist
| Problem | Solution |
|---|---|
| Relay clicks, but pump doesn't run | Check pump power supply connection |
| Pump runs unexpectedly | Adjust moistureThreshold value |
| OLED blank | Check I²C wiring (SDA/SCL) and address (0x3C) |
| DHT shows NaN | Check wiring or pull-up resistor |

---

### ☁️ IoT Integration

GreenGuard uses the WiFi capability of the Arduino UNO R4 WiFi to transmit real-time sensor data to IoT cloud platforms.

The system can monitor and visualize:

- 🌱 Soil moisture level
- 🌡️ Temperature data
- 💧 Humidity level
- 🚰 Water pump status

Cloud integration enables:

- 📊 Real-time data visualization
- 📱 Remote monitoring
- 📈 Historical data analysis
- 🌾 Smart agriculture automation

Supported IoT platforms:

- ThingsBoard
- Arduino IoT Cloud
- Blynk

---

## 🔮 Future Improvements

- Mobile app monitoring
- AI-based plant health analysis
- Weather-based irrigation
- Solar-powered operation
- Large-scale agricultural deployment

---

## 📂 Repository Structure

```text
GreenGuard-The-Smart-Plant-Saviour/
│
├── Code/
│   └── GreenGuard-The Smart Plant Saviour.ino
│
├── Circuit_Diagram/
│   └── Circuit_Diagram.jpg
│
├── README.md
│
└── LICENSE
```

---

## 👨‍💻 Developed By

Developed by **Rajdip Dutta**  
at **Protyra Tech**

🌱 Smart Agriculture | IoT | Embedded Systems | Electronics Innovation

---

## 📜 License

© 2026 Protyra Tech. All rights reserved.
