# ESPHome-Remote-Thermostat
A remote to control a Generic Thermostat in Home Assistant. Screen features 3 seperate pages that cycle when the rotary encoder is pressed to customize the way information displayed.

Screen 1 - top of the screen shows the thermostat or room name, under that in a large readable font is the current temperature reading from the sendor and under that is a smaller font showing the value the temperature is set to.

Screen 2 - Just for fun. This screen features the bongo cat gif and has small readouts of the current temperature and set temperature on the left side of the display.

Screen 3 - This screen features an animated background that changes when the heating device is turned on and has a readout of the set tempurature and current temperature.

Hardware Required -
Node MCU, Rotary Encoder, 128X64 OLED SSD1306, and a Home Assistant Server

Hardware Setup - pins listed are for a generic Node MCU V3, check your pinout!

Rotary encoder

gnd: G

+: VIN

sw: D4

dt: D7

clk: D6



OLED

VCC: 3V

GND: G 

SCL: D2

SDA: D1


Home Assistant Configuration-
Sensors that need to be added to sensor.yaml

 - platform: template
   sensors:
    set_temp_office:
      value_template: "{{states.climate.desk_heater.attributes.temperature}}" #set to your generic thermostat
 - platform: template
   sensors:
    hvac_mode:
      value_template: "{{state_attr('climate.desk_heater', 'hvac_action')}}" #set to your generic thermostat
      
Files that need to be added to Home Assistant for ESPHome to use-

add these folders to config/esphome: "_fonts" "_icons"

then upload the files from the corresponding folders in the repo. make sure to keep the file structure intact.

ESPHome configuration-
Just add a new device, copy remote_thermostat.yaml and edit it as needed.
