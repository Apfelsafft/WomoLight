# WomoLight
Smart light control for Campers, RVs, Wohnmobile

**Features:**
- 8 opto-coupled inputs divided into 2 separated groups with green control LED
- 8 opto-coupled PWM outputs divided into 2 separated groups with red control LED
- lights are dimmable
- 12V power supply for ESP or USB supply (set by jumper)
- Each input provides 12v for a switch that can be used as input voltage
- Each output provides GND for a LED but 12v is switched (highside driver)
- each terminal can be utilized by screw terminal or solder tap.
- I2C connector for further expansion
- GasLevel connector for two WomoLin GasLevel Sensors


Based on an ESP32 this board can control up to 8 lights in a camper.
It provides input for 8 physical light switches so that you are able to use them as well and combine them with the outputs by your needs.
By default each input is linked to its respective output. IN1 toggles OUT1, IN2 toggles OUT2, etc...
If you like to have more control please delete the "on_state:" part in each binary_sensor input.

The board provides 8 opto coupled INPUTs and OUTPUTs by using I/O expander PCF8574 (input) and PCA9685 (output PWM).

As the board will be integrated into an Home Assistant instance in my camper the ESP32 will be programmed in YAML using ESPhome.
I guess the best way ist to install ESPhome in your Home Assistant instance, create a new ESP32 device and copy the relevant part (all below the captive_portal) into your newly created yaml file.

Make sure you define the wemos_d1_mini32 board.

In Home Assistant 8 lights will appear which are dimmable.
You also see 8 input devices, which represent your switches. They can be used for any type of automations.


**known bugs**
PCB:
- Address jumpers need to be soldered and used as there are no default pull-down resistors. 
- first batch of PCB has wrong AMS1117 (1.2V only) and no capacitors along the AMS1117.
- in general AMS1117 seems to be a bad choice as it get very hot using 12V input voltage
- screw terminals are not the best choice for camper installations
- driver FETs are not mechanically secured and can be stressed by vibrations
- no connectors for further I2C boards or UARTs

ESPhome:
- transition time for on/off is 1s. Could be reduced to "feel more responsive"


![3D Vorschau](/LichtsteuerungV1.jpg)
