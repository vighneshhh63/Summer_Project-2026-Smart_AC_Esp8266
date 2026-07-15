# ☀️ Summer Project: Alexa Voice-Controlled Smart AC (ESP8266)

During my summer break, instead of just scrolling through social media, I decided to build something practical. I converted my old, non-smart Panasonic AC into a voice-controlled Smart AC using a NodeMCU (ESP8266), an IR Transmitter, and Sinric Pro connected with Amazon Alexa.

## 🛠️ Hardware Stack ( Sustainable)
* **NodeMCU (ESP8266)** - The brain of the project (with built-in Wi-Fi).
* **IR Transmitter (940nm LED)** - To mimic the physical remote's signals.
* **3.7V Lithium-ion Battery** - Reclaimed from old tech to power the setup portably.
* **SPST Toggle Switch** - A physical master switch to save battery when the AC isn't needed.

## 🔌 Circuit Connection
* **IR LED:** Signal Pin connected to `D2 (GPIO 4)`, GND to NodeMCU `GND`.
* **Power Setup:** Battery (+) -> Switch -> NodeMCU `VIN` (using the internal voltage regulator to step down the battery voltage safely).
* **Ground:** Battery (-) -> NodeMCU `GND`.

* THIS DEVICE HAS 1 TO 2 METERS RANGE AS OF NOW. USING MORE POWERFULL COMPONENTS CAN HELP IN INCREASING ITS RANGE!

## 💻 Tech Stack & Reverse Engineering
* **Language:** C++ (Arduino IDE)
* **The Hardest Part:** Reverse-engineering the massive **439-bit raw IR data** of the Panasonic AC remote. I captured the raw pulses using an IR receiver first, then mapped them to the sending protocol.
* **Cloud Integration:** Used the **SinricPro** SDK to bridge the local ESP8266 to AWS IoT, making it fully compatible with Alexa Smart Home commands.

---

