Correct way (IMPORTANT)
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

