# Talking Plant with ESP32 and Home-Assistant

This DIY talking plant solution measures the level of moisture in the oil and sends you a message through Alexa reminding you to water it when the soil is dry

⚡️ COMPONENTS AND SUPPLIES
--------------------------

<img align="right" src="https://github.com/isbkch/esp32-aws-weather-station/blob/master/docs/esp-32.jpg?raw=true" style="max-width:100%;" height="200">

*   [ESP32 Board](https://amzn.to/3jmCpqx)
*   [HC-SR501](https://www.amazon.ca/gp/product/B07KBWVJMP) PIR Sensor Infrared IR
*   [5 LiPo Batteries And Charger](https://www.amazon.ca/gp/product/B0795F139D)
*   [Solder Kit](https://www.amazon.ca/-/fr/gp/product/B01N46T138/)
*   [Silicone Soldering Pad](https://www.amazon.ca/gp/product/B082NBS3PH/)
*   [Helping Hands for soldering](https://www.amazon.ca/gp/product/B002PIA6Z4)
*   [Breadboard](https://amzn.to/2Ei40tP) - [Jumper Wires](https://amzn.to/2Ehh2ru) - [Male to Male Jumper Wires + Tweezer](https://amzn.to/3jcf9eX)

🚀APPS
------

*   [VSCode](https://code.visualstudio.com/)
*   [Fritzing](https://fritzing.org/)
*   [PlatformIO](https://platformio.org/)
*   [Home Assistant](https://www.home-assistant.io/)

📦 Libraries
=====
*   [PubSubClient](https://www.arduinolibraries.info/libraries/pub-sub-client)
*   [Wire](https://github.com/espressif/arduino-esp32/tree/master/libraries/Wire)
*   [WiFi](https://github.com/espressif/arduino-esp32/tree/master/libraries/WiFi)

Hardware Overview: HC-SR501 PIR Sensor Infrared IR
----------------------

<img align="right" src="https://github.com/MecaHumArduino/esp32-talking-plant/blob/main/doc/images/HC-SR501.jpg?raw=true">

The HC-SR501 PIR motion sensor is a $2 sensor that is used to detect movement from humans or pets.
**How PIR Motion Sensor Works**
All objects with a temperature above Absolute Zero emit heat energy in the form of infrared radiation, including human bodies. The hotter an object is, the more radiation it emits.
For most of our Arduino projects that need to detect when a person has left or entered the area, or has approached, HC-SR501 PIR sensors are a great choice. They are low power and low cost, pretty rugged, have a wide lens range, easy to interface with and are insanely popular among hobbyists.

HC-SR501 PIR sensor has three output pins VCC, Output and Ground as shown in the diagram below. It has a built-in voltage regulator so it can be powered by any DC voltage from 4.5 to 12 volts, typically 5V is used. Other than this, there are a couple options you have with your PIR. Let’s check them out.

<img align="center" src="https://github.com/MecaHumArduino/esp32-talking-plant/blob/main/doc/images/PIR-Sensor-Pinout-with-Jumper-Setting-Sensitivity-Time-Adjustment-BISS0001-IC-Labeling-Diagram.png?raw=true">

There are two potentiometers on the board to adjust a couple of parameters:

Sensitivity– This sets the maximum distance that motion can be detected. It ranges from 3 meters to approximately 7 meters. The topology of your room can affect the actual range you achieve.
Time– This sets how long that the output will remain HIGH after detection. At minimum it is 3 seconds, at maximum it is 300 seconds or 5 minutes.



The MPU-6050 is a serious little piece of motion processing tech! By combining both a 3-Axis accelerometer and a 3-Axis gyroscope on a single chip, the MPU-6050 is capable of processing complex 9-axis MotionFusion algorithms, the MPU-6050 does away with the cross-axis alignment problems that can creep up on discrete parts.

Hardware Overview: SW-420 Vibration Sensor
----------------------

<img align="center" src="https://github.com/MecaHumArduino/esp32-smart-cube/blob/main/doc/img/SW-420-sensor.jpeg?raw=true" height="300">

This Vibration Sensor Module consists of an SW-420 Vibration Sensor, resistors, capacitor, potentiometer, comparator LM393 IC, Power, and status LED in an integrated circuit. It is useful for a variety of shocks triggering, theft alarm, smart car, an earthquake alarm, motorcycle alarm, etc.

Hardware Overview: LiPo Battery
-----------------
<img align="right" src="https://images-na.ssl-images-amazon.com/images/I/31jNdqR1-yL._AC_.jpg" style="max-width:100%;" height="150">

A Lithium Polymer battery, or more correctly Lithium-ion Polymer battery (abbreviated as **LiPo**, **LIP**, **Li-poly**, **lithium-poly** and others), is a rechargeable battery of lithium-ion technology using a polymer electrolyte instead of a liquid electrolyte. High conductivity semisolid (gel) polymers form this electrolyte. These batteries provide higher specific energy than other lithium battery types and are used in applications where weight is a critical feature, such as mobile devices, radio-controlled aircraft and some electric vehicles.

I had purchased this set of [5 batteries with a charger](https://www.amazon.ca/gp/product/B0795F139D) from Amazon for under $15 and been using them for a [previous project](https://github.com/MecaHumArduino/wemos-water-leak-sensor) without a problem, so that shall be my go to battery for this project as well.

3D PRINTED CASE
---------------
No one likes wires hanging around, and so I went ahead looking for a 3D case I can use for this project and luckily found [this one on Thingiverse](https://www.thingiverse.com/thing:2550726) so that's what I'll be using

Schematic Diagram
-----------------

Wire the **MPU6050** and the **SW-420** to the [**ESP32**](https://amzn.to/3jmCpqx) development board as shown in the following schematic diagram.

<img align="center" src="https://github.com/MecaHumArduino/esp32-smart-cube/blob/main/doc/img/wiring-diagram.png?raw=true" style="max-width:100%;" height="600">


Make sure you have installed an MQTT broker in your HomeAssistant setup beforehand. You can start here: https://www.home-assistant.io/docs/mqtt/broker#run-your-own

Finally
--------
All contribution to this project is appreciated
