<h1>BlindNav: Smart Assistive Navigation </h1>
Empowering Independence Through Intelligent Obstacle Detection & Real-Time Feedback.
<br> </br>
<img width="1480" height="2100" alt="final stick design" src="https://github.com/user-attachments/assets/d8645a04-a5bb-4fb4-9df3-0c92f85af765" />


<h1>CAD</h1>
<div style="display: flex; align-items: flex-start; gap: 10px; ">
    <img
src="<img width="553" height="801" alt="3d stick design" src="https://github.com/user-attachments/assets/c5c4fe16-a121-431c-be8e-3e0cf2b6f1bf" />" width="45%" alt="3d stick design">
    <img
src="<img width="400" height="700" alt="3d stick design (transparent)" src="https://github.com/user-attachments/assets/db94706c-37aa-40ac-8b90-eb9a05495142" />" width="45%" alt="Internal 3d stick design">
</div>








<h1>PCB</h1>

<h1>Wiring Diagram</h1>
<img width="500" height="700" alt="Wiring Diagram" src="https://github.com/user-attachments/assets/6689b45c-7df5-4b0f-b640-5c3a435fc7cb" />


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
