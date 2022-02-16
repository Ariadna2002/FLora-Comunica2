# Project definition
A device that works with TTGO v1 storing the information it receives from various sensors, and sending the data via LoRa to a raspberry server that has nodered. 

# Procedure
To make easier the process of making this project, we have divided it in different parts. 

## Materials
To carry out this project we have used the following materials:

### Sensors:

· [Fire sensor - KY-026](https://hobbyking.com/es_es/keyes-flame-sensor-module-for-arduino.html?wrh_pdp=7&countrycode=ES&gclid=Cj0KCQiA3rKQBhCNARIsACUEW_a4FJTaPsVnPIupxuU-vIrrFga68_RIqFARL68YgrhCmGbWckRRJigaAnNfEALw_wcB)

· [Temperature/humidity/pressure sensor - GY-BMEP280](https://es.aliexpress.com/item/1005003089223378.html?gatewayAdapt=glo2esp&_randl_currency=EUR&_randl_shipto=ES&src=google&aff_fcid=63d0ffc3a82642d5a0fcf167d65251ed-1645005589147-05136-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=63d0ffc3a82642d5a0fcf167d65251ed-1645005589147-05136-UneMJZVf&terminal_id=974d9b7ff4e5452b8d3eb89935d3f2a6)

· [Gas sensor](https://www.smart-prototyping.com/MQ-9-carbon-monoxide,-combustible-gas-sensor-detection-alarm-module.html)

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

![Image1](https://github.com/Ariadna2002/FLora-Comunica2/blob/main/Schematic.png)

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
