# ESP32-RF-Signal-Scanner
This project is a portable RF signal strength scanner built around an ESP32 and the AD8317 RF Log Detector
ESP32 RF Signal Scanner (AD8317)
Overview

This project is a portable RF signal strength scanner built around an ESP32 and the AD8317 RF Log Detector.
It measures RF signal levels, converts them to:

📊 Raw ADC values
⚡ Voltage
📶 Signal Strength (0–10 scale)
📡 Approximate dBm

Results are displayed on a 128x64 SSD1306 OLED display, and a piezo buzzer provides audible feedback based on signal strength.

🧠 How It Works
The AD8317 outputs a voltage proportional to RF signal strength.
The ESP32 ADC reads this voltage.
The value is:
Smoothed using a moving average
Converted to voltage
Converted to approximate dBm

A potentiometer adjusts detection sensitivity (baseline range).
The OLED shows real-time data and signal bars.
A buzzer increases pitch as signal strength increases.

Hardware Used
🔹 Microcontroller
ESP32 (tested with XAIO / similar compact ESP32 boards)

🔹 RF Detector
AD8317 RF Logarithmic Detector

Typical Output Range: 0.33V – 1.65V
Approximate slope: −22 mV/dB

128x64 I2C OLED
I2C Address: 0x3C

🔹 Other Components
2x Boost Converters (9V & 5V outputs)
Potentiometer (sensitivity adjustment)
Piezo Buzzer
Battery + power switch
RF antenna (for AD8317 SMA input)

🔌 Wiring Guide
⚡ Power
Component	Connection
Boost Converter A (9V)	AD8317 VCC
Boost Converter B (5V)	ESP32 VCC
Power Switch	Controls main battery ground

📡 Signal Connections
Device	ESP32 Pin
AD8317 VOUT	GPIO2 (D0)
Potentiometer Wiper	GPIO3 (D1)
OLED SDA	GPIO21
OLED SCL	GPIO20
Buzzer +	GPIO8
All Grounds	Common GND

3.3V — Pot — GND
        |
       D1

       Display Information

The OLED shows:
Raw ADC value
Voltage
Baseline Range (Sensitivity)
Calculated dBm
Signal Strength (0–10)

📶 Visual signal bars
🔊 Audio Feedback

The buzzer:
Activates when signal strength > 0
Frequency increases from 500Hz → 2000Hz
Tone duration: 50ms

⚙️ Calibration Process
Power on device.
Turn OFF nearby RF sources.
Device automatically establishes baseline from 100 samples.
Adjust potentiometer to control sensitivity range.
Higher range = more sensitive detection.


Libraries Required
Install via Arduino Library Manager:
Adafruit GFX
Adafruit SSD1306
Also required:

Wire (built-in)
Arduino core for ESP32

🚀 Upload Settings
Board: ESP32 Dev Module (or equivalent)
Flash Speed: 80MHz
Partition Scheme: Default
Upload Speed: 921600 (recommended)

🛠 Features

✔ Moving average smoothing (20 samples)
✔ Adjustable sensitivity
✔ dBm approximation
✔ Visual signal meter
✔ Audible feedback
✔ Boot logo splash screen

⚠️ Notes

AD8317 requires stable 9V input.
Ensure common ground between all modules.
dBm values are approximate and may require calibration for precision work.
Avoid overdriving RF input beyond module limits.
