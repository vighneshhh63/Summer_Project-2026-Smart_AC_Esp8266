AFTER COMPLETING HARDWARE AND CODDING STUFF THESE IMPORTANT STEPS ARE FOLLOWED FOR SETTING UP THE NODEMCU WITH ALEXA AND AC.

Phase 1: Flashing the Code to the NodeMCU
Before disconnecting the microcontroller from your laptop, you had to upload the code and verify its connection using these exact steps:
Connect the Board: You connected the NodeMCU ESP8266 to your computer using a high-quality Micro-USB data cable.
Configure Arduino IDE Settings:
Board: You went to Tools > Board > ESP8266 Boards and selected NodeMCU 1.0 (ESP12-E Module).
Port: You went to Tools > Port and selected the active COM port (e.g., COM3 or COM4).
Upload Speed: Set to 115200 for a stable flash.
Upload the Code: You clicked the Upload button (Right Arrow icon).
Monitor the Boot:
You opened the Serial Monitor (Ctrl + Shift + M).
Set the Baud Rate to 115200.
You pressed the physical RST (Reset) button on the NodeMCU.
You verified that the NodeMCU successfully printed:
Wi-Fi Connection Established Successfully!

Phase 2: Setting Up the Sinric Pro Cloud Portal
Sinric Pro acts as the secure bridge between your local NodeMCU and Amazon's Alexa servers. Here is how you configured the portal:
1. Account & Room Creation
You signed up / logged into the Sinric Pro Portal (portal.sinric.pro).
(Optional) You created a Room (e.g., "Bedroom") to keep your smart devices organized.

2. Device Creation Settings
You went to the Devices tab on the left menu and clicked Add Device.
You entered the following settings:
Device Name: AC (This is the exact name Alexa will use).
Description: Voice Controlled Old AC.
Device Type: Selected Switch (since we are triggering a simple ON command for now).
Room: Selected your room (e.g., "Bedroom").
You clicked Next and then Save.

3. Copying Secure Keys & Device IDs
Once the device was created, Sinric Pro generated unique credentials. You copied these three critical parameters directly into your code:
APP Key: Found in Credentials on the left sidebar.
APP Secret: Found in Credentials on the left sidebar.
Device ID: Found directly on your newly created "AC" device card.

Phase 3: Linking Sinric Pro to Amazon Alexa
This is the magic step that allows you to control the NodeMCU using your voice. You set this up via the Alexa Smartphone App:
1. Enabling the Sinric Pro Skill
You opened the Amazon Alexa App on your phone.
Tapped on More (bottom right) and selected Skills & Games.
Searched for "Sinric Pro" in the search bar.
Tapped Enable to Use.

2. Account Linking (OAuth)
After enabling the skill, a web page opened inside the Alexa app asking for your Sinric Pro credentials.
You logged in using your Sinric Pro email and password.
You authorized Amazon Alexa to access your Sinric Pro devices.
Once linked, you received a confirmation message: "Sinric Pro has been successfully linked."

3. Device Discovery & Smart Home Setup
Back in the Alexa App, a prompt appeared: "Discovering Devices..." (If it didn't, you simply said, "Alexa, discover my devices").
Alexa scanned the cloud and found your virtual device named "AC".
You assigned the "AC" device to your virtual Bedroom group inside the Alexa App.

Phase 4: Hardware Assembly & Portability Setup
Once the software and cloud integrations were fully tested on USB power, you transitioned the device into a standalone, battery-powered unit:
The Battery Hookup: You took your rechargeable 3.7V Li-ion battery.
Wiring the Master Switch:
You soldered/connected the Battery Positive (+ / Red wire) to one terminal of your physical SPST slide switch.
You connected the other terminal of the switch to the VIN pin of the NodeMCU.
This slide switch acts as a physical vacation cut-off to save battery power.
The Common Ground: You connected the Battery Negative (- / Black wire) directly to the GND pin of the NodeMCU.
IR LED Mounting: You ensured the IR Transmitter LED was pointing directly at your AC's receiver window, with its positive leg on D2 and negative on GND.

Phase 5: The Final Test RunYou flipped the physical slide switch ON.The NodeMCU booted up, connected to your home Wi-Fi automatically, and established a handshake with the Sinric Pro cloud server (turning the dashboard indicator green/online).You gave the voice command: "Alexa, turn ON the AC."Alexa sent the signal to Sinric Pro $\rightarrow$ Sinric Pro pushed a callback to your NodeMCU $\rightarrow$ NodeMCU instantly blasted the 439-bit raw IR array $\rightarrow$ The AC beeped and turned on! ❄️🎉
