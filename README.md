Quick Setup Guide
1. Hardware Connections
• Connect potentiometer:
o One side → 3.3V
o Other side → GND
o Middle (wiper) → GPIO 4 (or your chosen ADC pin)
• (Optional) Connect LED:
o GPIO → resistor → LED → GND
________________________________________
2. Upload ESP32 Code
• Open Arduino IDE
• Select ESP32-C3 board
• Select correct COM port
• Upload the sketch
 The ESP32 will:
• Read the potentiometer
• Convert it to frequency
• Send values via Serial (115200 baud)
________________________________________
3. Run Processing 4 Sketch
• Open Processing 4
• Run this line first to find port:
println(Serial.list());
• Find your ESP32 (e.g. "COM8")
• Set correct index:
myPort = new Serial(this, Serial.list()[INDEX], 115200);
________________________________________
4. Important
•  Close Arduino Serial Monitor before running Processing 4
•  Baud rate must be 115200
________________________________________
5. Use the System
• Turn the potentiometer
• Watch:
o Frequency change in real time
o Wave compress and expand
o Rotating vector speed change
________________________________________
Result
You now have a real-time frequency visualizer controlled by a physical knob.
Rotating_vector_spinning_lancet_that_generates_a_sine_wave
 Real-Time Frequency & Wave Visualization System
Working Principle
The system is based on the fundamental relationship:
f = 1 / T
• The potentiometer adjusts an analog voltage.
• The ESP32 reads this value and maps it to a frequency range.
• This frequency is sent via serial communication to Processing.
• Processing uses this value to:
o Rotate a vector (phasor)
o Generate a sine wave in real time
________________________________________
Visualization Concept
The project uses a rotating vector (phasor) to generate a sine wave:
• The horizontal projection of the rotating vector forms the waveform.
• As frequency increases:
o The vector rotates faster
o The waveform becomes more compressed
• As frequency decreases:
o The rotation slows down
o The waveform expands
Conclusion
The system successfully links physical input (potentiometer) with mathematical behavior (waveform generation), creating an intuitive and interactive way to understand frequency and time-based signals.
________________________________________

Port index (IMPORTANT)
Step 1 — Print ports
Run this:
println(Serial.list());
You will see something like:

[0] "COM3"
[1] "COM8"
[2] "COM11"
Step 2 — Find your ESP32
 Look for:
"COM8" (in my case}
In this example:
COM8 = index 1
Step 3 — Use the INDEX (not the port number)
myPort = new Serial(this, Serial.list()[1], 115200);
 NOT [8]
 USE [1]
