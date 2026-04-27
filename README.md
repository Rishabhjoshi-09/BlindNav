<h1>BlindNav : Smart Assistive Navigation </h1>
Empowering Independence Through Intelligent Obstacle Detection & Real-Time Feedback.
<br> </br>
<img width="1480" height="2100" alt="final stick design" src="https://github.com/user-attachments/assets/d8645a04-a5bb-4fb4-9df3-0c92f85af765" />


<br></br>
<h1>Why BlindNav ?</h1>

BlindNav is a smart assistive device designed to provide visually impaired individuals with a safer and more independent navigation experience. Unlike a tradition white cane, it uses electronics to detect hazards that are otherwise "invisible" to a standard stick.
* **Electronic Safety Net:**  It is an ESP32 powered "smart stick" that uses ultrasonic sensors to detect obstacles in real-time, acting as an extension of the user's senses.

* **Dual-level Protection:** While traditional canes only find obstacles at ground level, BlindNav detects both ground-level (puddle, staris) and head-level (signboards, tree branches) hazards.

* **Intelligent Feedback System:** It communicates with the user through two main ways:
    * **Haptics:** A vibration motor that changes speed based on how close an object is.
    * **Voice:** Audio alerts (via a speaker) that give specific warnings like "Water Detected".

* **Emergency Lifeline:** It features an integrated SOS button and GPS module. If the user is lost or in danger, one press sends their live location to a trusted contact.

* **Environmental Awareness:** It includes an LDR (Light Dependent Resistor) that atutomatically turns on Night Visibility LEDs, making the user visible to vehicles and pedestrians in low-light conditions. 



<h1>Features</h1>

| Feature | Description |
| ------- | ----------- |
| 🦯 Dual Obstacle Detection | Ultrasonic sensors at ground and head level |
| 📳 Smart vibration Feedback | Fast = Close, Slow = Far - distance understood instantely |
| 💧 Water / Puddle Detection | Sensor at base alerts before user step into water |
| 🆘 Emergency SOS Button | One press sends GPS location alert to family |
| 📍 GPS Tracking | Live location sharing for emergencies |
| 💡 Night Visibility LED | Auto-activates in low light via LDR sensor |



<h1>Components</h1>

| Component | Purpose|
| --------- | ------- |
| ESP 32 | Main microcontroller |
| HC-SR04 (x2) | Obstacle detection - front & head level |
| Vibration Motor | Haptic alert feedfack |
| Speaker | Audio Alerts |
| Water Sensor Module | Puddle detection at base |
| SOS Push Button | Emergency alert trigger |
| GPS Module (NEO-6M) | Location Tracking |
| Light Sensor (LDR) | Auto Night LED |
| Li-ion Battery + TP4056 | Rechargeable power |
| Microphone + DFPlayer | Voice Feedback |



<h1>CAD</h1>
<img width="900" height="600" alt="image" src="https://github.com/user-attachments/assets/f4eebef2-ef08-4568-9773-665c6cfdc4e1" />

<h1>PCB</h1>
<img width="900" height="500" alt="digital circuit diagram" src="https://github.com/user-attachments/assets/88d8b371-d5e0-44ac-9bad-9e6613cf7517" />





<h1>Wiring Diagram</h1>
<img width="500" height="700" alt="Wiring Diagram" src="https://github.com/user-attachments/assets/6689b45c-7df5-4b0f-b640-5c3a435fc7cb" />


<h1>BOM List</h1>
## Bill of Materials (BOM)

| Item | Purpose | Price (USD) | Source | Link |
|------|--------|-------------|--------|------|
| ESP32 | Main microcontroller | $7.30 | Amazon | https://amzn.in/d/0gHaoIyY |
| HC-SR04 Ultrasonic Sensor (x2) | Obstacle Detection (front & head level) | $2.98 | Amazon | https://amzn.in/d/0fAaNY3Y |
| Vibration Motor | Haptic alert feedback | $2.50 | Amazon | https://amzn.in/d/07rawmSD |
| Speaker | Audio Alerts | $2.32 | Amazon | https://amzn.in/d/0fhy9WFE |
| Water Sensor Module | Detects Puddles At Base | $1.80 | Amazon | https://amzn.in/d/0bwGx5IL |
| SOS Button | Emergency alert trigger | $0.50 | - | - |
| GPS Module (NEO-6M) | Location Tracking | $4.38 | Flipkart | https://dl.flipkart.com/s/_BzfAxNNNN |
| Light Sensor (LDR) | Auto Night LED Control | $1.60 | Amazon | https://amzn.in/d/0fZwNgjv |
| Li-ion Battery (18650) | Power Supply | $3.20 | Amazon | https://amzn.in/d/0aF3MQx7 |
| TP4056 Charging Module | Battery Charging & Protection | $0.58 | Amazon | https://amzn.in/d/00pfBEQN |
| Microphone Module | Sound Input | $2.00 | Amazon | https://amzn.in/d/07QyzQxp |
| DFPlayer Mini | Voice Feedback System | $4.23 | Amazon | https://amzn.in/d/08cgAzWu |
| Jumper Wires | Connections Between Components | $3.17 | Amazon | https://amzn.in/d/0gfPHjTL |
| PCB / Perfboard | Mounting components | $4.56 | Amazon | https://amzn.in/d/04OUba8y |
| Switch (Power) | Turn device ON/OFF | $1.03 | Amazon | https://amzn.in/d/0fJ4RrQx |
| Stick Body | Holds All Components | Owned/Custom | - | - |

| **Total Component Price** |  | **$42.15** |  |  |
| **Shipping Price**        |  | **$3.85**  |  |  |
| **TOTAL PRICE**           |  | **$46.00** |  |  |
<br><br>

<h1>How It Works</h1>

```cpp

loop() {
    distance_front = ultrasonic.read(FRONT_SENSOR);
    distance_head  = ultrasonic.read(HEAD_SENSOR);

    if (distance_front < 30 || distance_head < 30) {
        vibrate(FAST);   // close obstacle
    } else if (distance_front < 80) {
        vibrate(SLOW);   // farther obstacle
    }

    if (waterSensor.detected()) {
        alert("WATER");
    }

    if (sosButton.pressed()) {
        sendAlert(gps.getLocation());
    }
}
```

<h1> How To Use & Install </h1>

1. Hardware Assembly
   * Secure the ESP32 and sensors into the 3d printed handle.
   * Ensure the water sensor is mounted at the very tip of the cane.
   * Calibrate the head-level sensor to a 15' upward tilt.

2. Software Setup
   1) Clone this repository: git clone https://github.com/Rishabhjoshi09/BlindNav.git
   2) Open the .ino file in the Arduino IDE.
   3) Install necessary libraries (NewPing, TinyGPS++, etc.).
   4) Flash the code to your ESP32.

3. Operation
   * Power ON : Use the toggle switch on the handle.
   * Navigation : Walk normally; the stick will vibrate when obstacles are within 100cm.
   * SOS : Press and hold the red button for 3 seconds to send a location alert.
