# Aqua-Sense-AI
The Pipe-Pulse Acoustic Leak Detector is a cutting-edge IoT solution designed by Electro-Tech for non-invasive water monitoring. Built on the ESP8266, it uses an analog microphone and a custom "Water Logic" algorithm to identify the specific sound frequencies of flowing water while ignoring background noise. It's a smart, safe build.
1. Project Concept: Acoustic Water Intelligence
The Aqua-Save Leak Detector is an IoT safety system based on the ESP8266 (NodeMCU). Unlike traditional water sensors that need to get wet to work, this system uses "Acoustic Intelligence." It monitors the specific sound frequencies and patterns created by water flowing through pipes or dripping onto surfaces. By using an analog microphone (MIC_PIN A0), the device "listens" for the vibration of water. This allows for non-invasive monitoring, meaning you can strap the sensor to the outside of a pipe or place it near a water tank to detect hidden leaks before they cause serious damage.

2. The "Water Logic" Algorithm
The most advanced part of this code is how it distinguishes between a loud noise (like a door slamming) and actual water flow.

Baseline Calibration: When the device starts, it samples 100 noise readings to calculate a baseline_noise level. This allows it to "ignore" the natural silence or static of the room.

Continuous Flow Detection: The code uses a continuous_sound_count variable. Instead of triggering an alarm for a single loud spike, it requires the sound to persist for a specific number of cycles (15+ cycles).

Filtering: If a noise is sudden and short, the counter resets. If the sound is constant—like a burst pipe or a tap left open—the counter climbs, confirming the presence of water flow rather than random background noise.

3. Hardware Interfacing & Safety Features
The physical build is designed for high-visibility alerts:

The Buzzer (D8): If the "Water Logic" confirms a leak, a physical buzzer sounds to alert anyone nearby.

The ESP8266 Hub: The NodeMCU manages the WiFi connection and handles the heavy lifting of processing analog signals into digital logic.

Power Management: The code includes ESP.wdtFeed() and yield() commands. These ensure the "Watchdog Timer" doesn't reset the chip during heavy WiFi tasks, keeping the leak monitor online 24/7 without crashing.

4. Telegram IoT Integration
The system is fully connected to the cloud, giving you a remote "ear" on your property.

Real-time Reporting: Every 25 seconds, the device sends a telemetry report to your Telegram Bot, showing the current "Score" (noise level) and "Flow Counter."

Remote Commands: You can talk back to the device. Sending /stop mutes the buzzer for 10 seconds if you are currently fixing the leak. Sending /status gives you an instant health check, and /reset allows you to reboot the system remotely if it needs a fresh calibration.

5. Technical Calibration for "Electro-Tech"
To make this project successful, the SENSITIVITY_THRESHOLD is key. In the code, it is set to 4. This acts as a "noise gate." If your environment is naturally noisy (like a laundry room), you can increase this number. If it is a very quiet basement, you can decrease it to detect even the smallest pinhole leaks. By combining analog signal processing with a custom software filter, this "Electro-Tech" build provides a professional-grade solution for home automation and resource protection.
