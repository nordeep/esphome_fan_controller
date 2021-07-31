# esphome_fan_controller
ESPHome PWM FAN controller

## Goal
1. Control the fan speed by fan PWM.
2. Ability to turn off the fan.
3. Read RPM data from the fan.
## Warning!
Be careful while connect PSU +12V and GND to MOSFET. 
## Notes
Common PWN FAN doesn't stop on 0% PWM signal and still running on minimum RPM. It is possible to control the fan speed not by fan PWM, but by PWM of power. In that case the fan can stop, but RPM data from the fan is messed up.
We will start/stop the fan with a MOSFET and set the speed with the FAN PWM input signal.
