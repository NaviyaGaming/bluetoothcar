# bluetoothcar
# 🏎️ ESP32 6WD WiFi Robot

A powerful 6-wheel-drive remote-controlled robot built on a Yaboom metallic chassis. It features a custom ESP32 web server for zero-reload directional control and PWM speed adjustment over WiFi, driven by dual high-current BTS7960 motor drivers.

## ✨ Features
* **6-Wheel Drive:** High-traction metallic chassis with left and right tracks wired in parallel.
* **Custom Web Interface:** Touch-friendly, zero-latency D-Pad and speed slider served directly from the ESP32.
* **High-Current Handling:** Utilizes dual BTS7960 (43A) motor drivers to handle the stall current of 6 parallel motors.
* **Independent Power Regulation:** 12V system stepped down to a clean 5V via a dedicated buck converter for stable ESP32 logic.

## 🛠️ Hardware Requirements
* **Microcontroller:** ESP32 (38-pin NodeMCU)
* **Chassis:** Yaboom metallic 6-wheel structure (6x DC Motors)
* **Motor Drivers:** 2x BTS7960 43A High-Power Drivers
* **Power Supply:** 12V 4000mAh Li-Po Battery
* **Power Regulation:** 12V to 5V Buck Converter

## ⚡ Power & Wiring Architecture

### Power Distribution
The 12V battery acts as the primary power rail. It is wired **in parallel** to:
1. `Driver A` (Left Side BTS7960) `B+` and `B-`
2. `Driver B` (Right Side BTS7960) `B+` and `B-`
3. 12V-to-5V Buck Converter `IN+` and `IN-`

*Note: The Buck Converter's 5V `OUT+` goes to the ESP32 `5V/VIN` pin, and `OUT-` goes to the ESP32 `GND` pin.*

### Motor Wiring
* **Left Side:** All 3 left motors are wired in parallel to the outputs of Driver A.
* **Right Side:** All 3 right motors are wired in parallel to the outputs of Driver B. *(Handled via software inversion in the code).*

### ESP32 Pin Mapping

**left motor driver             ESP32**
**RPWM                          25**
**LPWM                          26**
**REN                           18**
**LEN                           21**
**  **
**right motor driver            ESP32**
**RPWM                          27**    
**LPWM                          14**
**REN                           13**
**LEN                           12**

## 🚀 Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/NaviyaGaming/bluetoothcar]
