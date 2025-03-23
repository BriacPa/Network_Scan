# Wi-Fi Scanner with OLED Display (ESP32)

This project implements a Wi-Fi scanner using an ESP32, with results displayed on an OLED screen (SH1106, 128x64 pixels). It uses the `U8g2lib` library for drawing on the OLED display, the `WiFi.h` library for scanning Wi-Fi networks, and the `esp_wifi.h` library to access the Wi-Fi functionality of the ESP32.

## Features

- **Wi-Fi Scan**: Scan for available Wi-Fi networks and display their details (SSID, RSSI, Encryption Type, Channel, MAC Address).
- **Progress Bar**: Displays a progress bar on the screen that updates every second while displaying network information.
- **Non-blocking Scan**: The scan is done asynchronously, and the display updates with available network information.

## Hardware Requirements

- **ESP32** development board (e.g., ESP32 DevKit V1).
- **OLED Display (SH1106)**: 128x64 resolution, I2C interface.
- **Wires**: Connect the I2C SDA and SCL pins to the corresponding pins on your ESP32.

### Pin Configuration:

- **SDA**: Pin 21 (can be changed in the code if necessary).
- **SCL**: Pin 22 (can be changed in the code if necessary).

## Libraries Used

- [Wire.h](https://www.arduino.cc/en/Reference/Wire): I2C communication library.
- [U8g2lib](https://github.com/olikraus/U8g2_Arduino): Graphics library for the OLED display.
- [WiFi.h](https://github.com/espressif/arduino-esp32/tree/master/libraries/WiFi): Wi-Fi library for the ESP32.
- [esp_wifi.h](https://github.com/espressif/arduino-esp32/blob/master/libraries/WiFi/src/esp_wifi.h): ESP32 Wi-Fi management functions.

## Setup

### 1. Install the Libraries

To use this project, you'll need to install the following libraries:

1. **U8g2lib**:
    - Open Arduino IDE, go to **Sketch** → **Include Library** → **Manage Libraries**.
    - Search for **U8g2lib** and install it.

2. **WiFi**:
    - This is part of the ESP32 core libraries. Ensure you have the latest ESP32 board package installed in your Arduino IDE.

### 2. Wiring the Display

1. **SDA Pin**: Connect to GPIO 21 of the ESP32.
2. **SCL Pin**: Connect to GPIO 22 of the ESP32.
3. **VCC and GND**: Connect to 3.3V and GND of the ESP32, respectively.

### 3. Upload the Code

1. Open the code in the Arduino IDE.
2. Select the correct ESP32 board and port from the **Tools** menu.
3. Upload the sketch to the ESP32.

## Usage

1. After the ESP32 starts, it will immediately begin scanning for available Wi-Fi networks.
2. The display will show a list of available Wi-Fi networks along with their signal strength (RSSI), encryption type, channel, and MAC address.
3. The progress bar will update each second as the information is displayed.
4. If no networks are found, the display will show "No Networks".

## Code Explanation

### Core Logic:

- **Wi-Fi Scanning**: The `performWiFiScan()` function scans for available networks. It saves the networks into a vector and prevents duplicates using a `std::set`.
- **Display Update**: Every second, the display is updated to show the current network's details and the progress bar.
  
### Helper Functions:

- `encryptionTypeToString()`: Converts the encryption type (e.g., WPA2, WPA3) to a human-readable string.
- `performWiFiScan()`: Handles the scanning process, saving networks to a vector, and updates the display with available networks.

## Troubleshooting

1. **No Networks Found**: Ensure your ESP32 is within range of Wi-Fi networks and there is no interference from other devices.
2. **OLED Display Not Working**: Check your wiring for the correct SDA and SCL pins. Make sure your OLED display is properly connected to the ESP32.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
