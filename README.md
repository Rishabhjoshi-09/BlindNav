# BlindNav
BlindNav is a smart assistive device designed to help visually impaired individuals navigate their surroundings safely and independently. Built around an ESP32 microcontroller, it combines multiple sensors and feedback systems into a lightweight, rechargeable walking stick that responds to real-world conditions in real time.

The device uses ultrasonic sensors positioned at both ground and head level to detect obstacles across multiple angles. When an obstacle is detected, the stick responds with different vibration patterns - fast pulses for close-range threats and slower pulses for distant ones- giving the user intuitive, immediate awareness without requiring sight or complex interpretation.

A water detection sensor at the base of the stick identifies puddles and wet surfaces before the user steps into them, preventing slips and falls. Combined with a speaker and microphone, BlindNav also delivers voice feedback such as "Obstacle ahead" or "Water Detected", making alerts accessible even in loud environments where vibration alone may not be enough.

For EMERGENCIES, a dedicated SOS button allows the user to instantly send a distress signal along with their live GPS location to a trusted contact or caregiver. This feature addresses one of the most critical gaps in current assistive technology - the ability to call for help without a phone. A volume control system lets users adjust audio feeeback to their environment.

Night safety is handled through automatic LED activation in low-light conditions, making the user more visible to vehicles and pedestrians. All components are powered by a rechargeable lithium battery with an onboard module, eliminating the need for disposable batteries and making the device practical for daily use.

BlindNav is designed to be affordable, user-friendly, and built for real-life conditions rather than controlled environments. Every feature prioritizes practical usability - ergonomic form factor to the multi-modal alert system. The goal is to build a fully functional device that meaningfully improves safety, confidence, and independence for visually impaired users in everyday situations.

<img width="740" height="1058" alt="final stick design" src="https://github.com/user-attachments/assets/d8645a04-a5bb-4fb4-9df3-0c92f85af765" />

<br><br>
Features

| Feature | Description |
| ------- | ----------- |
| 🦯 Dual Obstacle Detection | Ultrasonic sensors at ground and head level |
| 📳 Smart vibration Feedback | Fast = Close, Slow = Far - distance understood instantely |
| 💧 Water / Puddle Detection | Sensor at base alerts before user step into water |
| 🆘 Emergency SOS Button | One press sends GPS location alert to family |
| 📍 GPS Tracking | Live location sharing for emergencies |
| 💡 Night Visibility LED | Auto-activates in low light via LDR sensor |
