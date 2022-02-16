# Project definition
A device that works with TTGO v1 storing the information it receives from various sensors, and sending the data via LoRa to a raspberry server that has nodered. 

# Procedure
To make easier the process of making this project, we have divided it in different parts. 

## Materials
To carry out this project we have used the following materials:

### Sensors:

· KY-026 fire sensor

· GY-BMEP280 temperature/humidity/pressure sensor

· Flying Fish gas sensor

### Modules:

· ESP32 Lilygo TTGO

· ESP32 TTGO

### Computer used to see the information:

· Raspberry Pi 4

### Software used for programming:

· Arduino IDE

### A part:

· 2 LEDS

· PCB

· 3D Printer


## Connections

https://github.com/Ariadna2002/FLora-Comunica2/blob/main/Schematic.png

## Steps

1-The first thing we must do is the installation and programming in NodeRed because if we do not have the programming part done the receiver will not receive any data because it will not be connected to the raspberry (by MQTT) and will give us a failed message. To do this we will follow the steps in the "NodeRed" folder.

2-Secondly, we must make the connections found in the attached "Schematic" file above. For the program to work it must detect the BMEP280 sensor.

3-The third thing to do is to load the "LoRaSender" program in our TTGO with the connections already made.

4-The fourth step is to load the "LoRaReceiver" program in our Lilygo TTGO. To do this we must create four files in our Arduino IDE and paste the programs attached above with the exact names.
To do this, in our Arduino IDE we will find an arrow at the top right, just below the serial monitor icon (a magnifying glass), and click "New tab". Then we will write the names as they are in the previously shared files.

For example:
We create a new file as just explained, name it "Sender.h" and paste the "Sender.h" file to it. 
It's as simple as that.

Finally, we adapted the "LoRaReceiver" program with our:

-Wifi name (ssid)

-Password

-The IP address of the raspberry that we are using (mqtt_server)

These are the steps to be followed only for the complete operation of the project. If you would like to add a PCB and a 3D design of a housing for this project, we have left the files for you to download. 
