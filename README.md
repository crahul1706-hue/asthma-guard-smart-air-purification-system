# asthma-guard-smart-air-purification-system
# 🌬️ Asthma Guard – Smart Air Purification System

**ESP32-Based Wearable Air Purification, Environmental Monitoring and Early Warning System**

## 📌 Project Overview

Asthma Guard is an embedded systems and IoT project designed to monitor surrounding air conditions and deliver filtered air toward the user's breathing zone.

The proposed wearable system combines environmental sensors, HEPA filtration, coaxial fans, an ESP32 microcontroller, and a real-time web dashboard.

The system reads environmental sensor values, evaluates them against configurable thresholds, controls the fan driver when gas or dust readings exceed the configured limits, and activates a buzzer when a warning condition is detected.

A future enhancement is wireless notification to designated family members or caregivers when environmental conditions become unfavorable.

**Project status:** Physical prototype developed; firmware integration and testing in progress.

## 🎯 Objectives

- Monitor surrounding environmental conditions.
- Measure temperature and relative humidity.
- Read gas-related values using an MQ-135 sensor.
- Monitor dust-sensor output using a GP2Y1010 optical dust sensor.
- Control coaxial fans through an external driver circuit.
- Direct filtered air toward the user's breathing zone.
- Generate audible warnings when configured thresholds are exceeded.
- Display live sensor readings through an ESP32-hosted web dashboard.
- Develop a wearable, portable air-purification system.


## 🛠️ Hardware Components

| Component                            | Purpose                                                   |
| ------------------------------------ | --------------------------------------------------------- |
| ESP32 development board              | Sensor acquisition, processing, and web server            |
| DHT22 sensor                         | Temperature and humidity measurement                      |
| MQ-135 sensor                        | Gas-related analog readings                               |
| GP2Y1010 optical dust sensor         | Dust-related optical measurements                         |
| Coaxial fans                         | Airflow generation                                        |
| HEPA filters                         | Removal of airborne particles passing through the filters |
| IRLZ44N or compatible driver circuit | Fan power switching, subject to circuit verification      |
| Buzzer                               | Audible warning                                           |
| Battery and power circuit            | Portable power supply                                     |
| Wearable enclosure                   | Mechanical support for the assembly                       |


## ⚙️ Working Principle

### 1. Environmental Monitoring

The sensors collect temperature, humidity, gas-related readings, and dust-sensor measurements from the surrounding environment.

### 2. Data Processing

The ESP32 reads the sensor values periodically and compares them with configurable thresholds.

### 3. Air Purification

When the configured gas or dust threshold is exceeded, the firmware activates the fan driver. The fans are intended to direct air through the filtration assembly and toward the user's breathing zone.

### 4. Warning System

The buzzer activates when a configured warning condition is detected, including excessive gas-related readings, dust readings, temperature, or humidity outside the selected range.

### 5. Real-Time Dashboard

The ESP32 hosts a local web dashboard that displays sensor readings, the overall environmental status, warning details, and fan state.

### 6. Periodic Monitoring

The firmware samples the sensors approximately every four seconds and updates the dashboard with the latest readings.

## 🔌 Circuit Pin Configuration

| Component                   | ESP32 GPIO |
| --------------------------- | ---------- |
| DHT22 data                  | GPIO 4     |
| MQ-135 analog output        | GPIO 35    |
| GP2Y1010 analog output (Vo) | GPIO 34    |
| GP2Y1010 LED control        | GPIO 25    |
| Fan driver control          | GPIO 18    |
| Buzzer                      | GPIO 23    |

**Important:** GPIO 18 uses active-low fan control in the recovered design. Verify the actual driver circuit before connecting the fan. Never power a fan directly from an ESP32 GPIO.

## 💻 Software and Technologies

- Arduino IDE
- ESP32 Arduino Core
- Embedded C/C++
- Wi-Fi communication
- HTTP web server using `WebServer.h`
- JSON-based sensor data API
- HTML, CSS, and JavaScript dashboard
- DHT sensor library by Adafruit

## 📊 Web Dashboard and API

After the ESP32 connects to Wi-Fi, the IP address is printed in the Serial Monitor.

Open that IP address in a browser connected to the same local network to access the dashboard.

The firmware provides these endpoints:

| Endpoint    | Function                                   |
| ----------- | ------------------------------------------ |
| `/`         | Displays the live monitoring dashboard     |
| `/api/data` | Returns the latest sensor readings as JSON |

The API provides fields for temperature, humidity, raw MQ-135 ADC readings, dust-sensor voltage, voltage rise above baseline, overall status, fan state, and warning details.

## 🚀 How to Run the Project

1. Install Arduino IDE.
2. Install ESP32 board support.
3. Install the required DHT sensor library.
4. Open `AsthmaGuard.ino`.
5. Replace the Wi-Fi placeholders with your local Wi-Fi credentials.
6. Check the pin assignments and verify the sensor and fan-driver wiring.
7. Select the appropriate ESP32 board and port.
8. Upload the firmware.
9. Open Serial Monitor at **115200 baud**.
10. Open the IP address printed in the Serial Monitor to view the dashboard.

## 🧪 Testing and Calibration

The following tasks are required to validate the prototype:

- Verify DHT22 temperature and humidity readings.
- Check the MQ-135 sensor response and establish a calibration procedure.
- Verify GP2Y1010 timing, analog output, and clean-air baseline.
- Calibrate the gas and dust warning thresholds.
- Verify the fan driver's active-low behavior.
- Test buzzer operation under warning conditions.
- Check dashboard updates and recovery after Wi-Fi disconnection.
- Measure filtration performance and airflow near the breathing zone.
- Record actual readings and experimental results.

The MQ-135 output is a raw ADC value, not a calibrated gas concentration. The current firmware reports GP2Y1010 voltage and baseline voltage rise, not validated dust concentration in mg/m³.

## 🔬 Development Status

-  Project concept and system architecture defined
-  Physical prototype photographs documented
-  ESP32 dashboard structure implemented in firmware
-  Sensor interfaces defined in firmware
-  Fan and buzzer control logic implemented
-  Verify all sensors on the physical hardware
-  Calibrate gas and dust readings
-  Validate fan and filtration performance
-  Implement mobile notifications to designated contacts
-  Complete experimental testing and documentation

## 🔮 Future Enhancements

- Mobile application for remote monitoring
- Wireless notifications to selected emergency contacts
- Historical air-quality data logging
- Automatic fan-speed adjustment
- Battery-life optimization
- Filter replacement reminders
- Improved wearable enclosure and comfort
- Validated airflow and filtration testing

## ⚠️ Safety and Limitations

Asthma Guard is an experimental engineering prototype, not a certified medical or respiratory protective device.

The sensor thresholds are configurable prototype values and are not clinically validated asthma-risk thresholds. Environmental readings alone cannot diagnose or reliably predict an asthma attack.

HEPA filtration effectiveness depends on filter specification, sealing, airflow, and operating conditions. The proposed directed-airflow barrier requires testing and has not been established as protective.

The device must not replace prescribed asthma treatment, approved respiratory protection, or medical assistance.

## 👨‍💻 Project Information

- **Project:** Asthma Guard – Smart Air Purification System
- **Domain:** Embedded Systems, IoT, Wearable Technology
- **Controller:** ESP32
- **Programming:** Arduino C/C++
- **Sensors:** DHT22, MQ-135, GP2Y1010
- **Core functions:** Environmental monitoring, fan control, buzzer alerts, web dashboard
- **Status:** Prototype 

## 📄 License

This project is intended for educational and research purposes. A suitable open-source license can be added when selected.

