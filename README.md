# Project definition
A device that works with TTGO v1 storing the information it receives from various sensors, and sending the data via LoRa to a raspberry server that has nodered. 
![ProjectWithNoCase](https://github.com/Ariadna2002/FLora-Comunica2/blob/main/Images/ProjectWithNoCase.jpeg)

This project is composed of two "blocks", the first one a pcb with 3 sensors connected to a TTGO, and the second one a Lilygo connected to a raspberry. Both are transreceivers, since the TTGO sends the information it collects from the sensors and sends it to the lilygo board, but also receives information from it to use its actuators, which in our case is a led that can be turned off remotely from the nodered GUI. The green led just indicates if the Nodered is on.

This repository contains all the information needed to make both transreceivers.

# Materials
To carry out this project we have used the following materials:

## Components of the transmitter:

· 2 Leds 

· [Fire sensor - KY-026](https://hobbyking.com/es_es/keyes-flame-sensor-module-for-arduino.html?wrh_pdp=7&countrycode=ES&gclid=Cj0KCQiA3rKQBhCNARIsACUEW_a4FJTaPsVnPIupxuU-vIrrFga68_RIqFARL68YgrhCmGbWckRRJigaAnNfEALw_wcB)

· [Temperature/humidity/pressure sensor - GY-BMEP280](https://es.aliexpress.com/item/1005003089223378.html?gatewayAdapt=glo2esp&_randl_currency=EUR&_randl_shipto=ES&src=google&aff_fcid=63d0ffc3a82642d5a0fcf167d65251ed-1645005589147-05136-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=63d0ffc3a82642d5a0fcf167d65251ed-1645005589147-05136-UneMJZVf&terminal_id=974d9b7ff4e5452b8d3eb89935d3f2a6)

· [Gas sensor](https://www.smart-prototyping.com/MQ-9-carbon-monoxide,-combustible-gas-sensor-detection-alarm-module.html)

· ESP32 TTGO

## Receiver:

· ESP32 Lilygo TTGO

· Raspberry Pi 4

## Softwares:

· Programation: [Arduino IDE](https://www.arduino.cc/)
· PCB Designs: [Proteus](https://componentsearchengine.com/library/proteus?gclid=Cj0KCQiA3rKQBhCNARIsACUEW_aY6RcRdgSPUMMehsdv-Bzp3LncFmYT_sYbc0FBilARIvG0W2LUSLcaAgRlEALw_wcB)
· 3D designs: [Tinkercad](https://www.tinkercad.com/dashboard)


# Connections of the transmitter
![Image1](https://github.com/Ariadna2002/FLora-Comunica2/blob/main/Schematic.png)

# Procedure 

## Configuration of the Server in raspberry

First of all, to start with the work we must have installed "Mosquitto Broker" in our raspberry. Here is a [tutorial](https://www.luisllamas.es/como-instalar-mosquitto-el-broker-mqtt/) for that. The installation and programming of nodered is a must, if we don't have the programming part done the receiver will not receive any data because it wont be connected to the raspberry (by MQTT) and will give us a failed message when we try the program in the ttgo. 

To install nodered, enter these 2 commands in the raspberry terminal:
```
- bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)
```
and 
```
- npm install node-red-dashboard
```
Once we have installed, we have to enter in the google browser the ip of the raspberry and the port, this will allow us to access nodered. Our configuration for everything to work is the following.
![Captura de pantalla 2022-02-16 131329](https://user-images.githubusercontent.com/99401726/154263679-7e6f2584-875b-4944-b4a6-73cab04c53bf.png)

Every node must be also configured. 

## Assembly of the transmitter

Following the diagram in the connection section, we will connect all the sensors to the ttgo, and we will insert the program of [LoraSender](https://github.com/Ariadna2002/FLora-Comunica2/tree/main/LoRaSender) which is divided in 4 parts, but in the arduino must be entered in the same program, but in different tabs.


# Procedure

1-The first thing we must do is the installation and programming in NodeRed because if we don't have the programming part done the receiver will not receive any data because it wont be connected to the raspberry (by MQTT) and will give us a failed message. To do this we will follow the steps in the "NodeRed" folder.

2-Secondly, we must make the connections as shown in the image of "connections". For the program to work it must detect the BMEP280 sensor.

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

# PCB 
