# ESPHome PWM FAN controller
Common PWN FAN doesn't stop on 0% PWM signal and still running on minimum RPM. It is possible to control the fan speed not by fan PWM, but by PWM of DC input. In that case the fan can be stopped, but RPM data from the fan is messed up. 
We will start/stop the fan with a MOSFET and set the speed with the FAN PWM input signal.

## Goal
1. Control the fan speed by fan PWM.
2. Ability to turn off the fan.
3. Read RPM data from the fan.
## Warning!
Be careful while connect PSU +12V and GND to MOSFET. 
## Notes
## Hardware
1. Wemos D1 mini
2. 4-channel Logic Level Converter - Bi-Directional
3. IRF520 MOSFET module or similar
4. 12V PWM FAN (DeepCool UF140 in my case)
5. 12V DC PSU

## Schema
![Schema](https://raw.githubusercontent.com/nordeep/esphome_fan_controller/main/images/fanmaster.svg)

## Software
Tested on ESPHome v 1.20.1 
A little bit trick to stop PWM fan is set 100% level of PWM on output. That's why I do not use power_supply component. 
My fan has maximum 1200 RPM so I filtered out RPM above 1500.

## Issues
1. Have to set 100% of PWM on boot to prevent fan from rotating on boot.
2. Slight rotation occurs on device boot. Be careful!