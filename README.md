

#  IoT-Based SOS Emergency Alert System for kids or senior citizens

###  Overview

This project is an **IoT-based emergency alert system** built using **C++ on ESP32** integrated with an **A9G GSM/GPS module**.
When the **SOS button** is pressed for a few seconds, the system automatically:

1. Fetches the **real-time GPS location**,
2. Sends it via **SMS with a Google Maps link**, and
3. Initiates an **emergency phone call** to a predefined contact.

It’s designed for **personal safety**, **elderly care**, or **vehicle emergency systems**, combining IoT connectivity with efficient power management.

---

###  Tech Stack

* **Language:** C++
* **Hardware:** ESP32 / Arduino Board, A9G GSM + GPS Module, SOS Push Button
* **Communication:** UART (Serial Communication), AT Commands
* **Libraries:** WiFi.h (for disabling Wi-Fi to save power)
* **Data Structures Used:**

  * **String Structure** – for GPS data parsing and SMS message formatting
  * **Queue Logic** – for managing incoming serial data efficiently

---

###  Features

*  **SOS Detection:** Detects long-press (5 seconds) on SOS button to trigger emergency mode.
*  **GPS Location Tracking:** Retrieves accurate coordinates from the A9G GPS module.
*  **SMS Alert:** Sends the location as a clickable **Google Maps link** to the emergency contact.
*  **Automatic Calling:** Makes an immediate call after sending the SMS alert.
*  **Power Optimization:** Disables Wi-Fi and Bluetooth, enabling low-power sleep mode when idle.
*  **Remote Command Support:** Responds to SMS commands like `"SEND LOCATION"` to return current coordinates.
*  **Error Handling:** Detects and reports GPS unavailability (sends fallback SMS if needed).

---

###  Circuit Connections

| Component     | ESP32 Pin        | Description                 |
| ------------- | ---------------- | --------------------------- |
| GSM/GPS (A9G) | D0 (RX), D1 (TX) | Serial communication        |
| SOS Button    | D3               | Input trigger for emergency |
| Sleep Control | D2               | Controls GSM sleep mode     |
| Power Supply  | 5V               | For module operation        |

---

###  Working Principle

1. The system continuously monitors the SOS button.
2. When pressed for **5 seconds**, it fetches GPS coordinates using the **AT+LOCATION** command.
3. Sends an **SMS** with the Google Maps link to the configured contact number.
4. Optionally, initiates a **call** to the same number for faster response.
5. Enters **sleep mode** when idle to conserve battery power.

---

###  Code Highlights

* **Serial Communication:** `Serial1` is used for GSM/GPS data exchange.
* **AT Commands:** Used for GPS activation, SMS sending, and call management.
* **Sleep Control:** `digitalWrite(SLEEP_PIN, HIGH)` enables GSM module sleep.
* **Error Handling:** Detects `"GPS NOT FIXED"` and sends fallback messages.

---

###  Setup Instructions

1. Connect hardware as shown in the above table.
2. Upload the code to your **ESP32** using Arduino IDE.
3. Replace `SOS_NUM` with your own emergency number:

   ```cpp
   String SOS_NUM = "+91xxxxxxxxxx";
   ```
4. Open Serial Monitor (115200 baud) to see real-time logs.
5. Press and hold the SOS button for 5 seconds to trigger the alert.

---



###  Author

**Sayan Mandal**
[LinkedIn](https://linkedin.com/in/iamsayanmandal)

---


