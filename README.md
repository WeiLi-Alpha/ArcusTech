# Arcus

This is an EPICS IOC for the Arcus stepper motor controller and driver: 
- [single-axis ACE-SDE](https://www.arcus-technology.com/products/single-axis-motion-controller/1-axis-usb-controller-plus-driver) and 
- [two-axis PMX-2ED-SA](https://www.arcus-technology.com/products/multi-axis-motion-controller/2-axis-usb-controller-plus-driver/)

# Required 
## Modules
- [asyn](https://github.com/epics-modules/asyn)
- [stream](https://github.com/epics-modules/stream)
- [calc](https://github.com/epics-modules/calc)
- [base 3.15.6](https://epics-controls.org/resources-and-support/base/series-3-15/3-15-6/)

## Hardwares
- [single-axis ACE-SDE](https://www.arcus-technology.com/products/single-axis-motion-controller/1-axis-usb-controller-plus-driver) and 
- [two-axis PMX-2ED-SA](https://www.arcus-technology.com/products/multi-axis-motion-controller/2-axis-usb-controller-plus-driver/)
- 12V or 24V power supply
- USB to RS485/422 cable
- [TM-STPP-23 Hybrid Stepper Motor (NEMA 23)](https://www.arcus-technology.com/products/stepper-motors/tm-stpp-23/)
- IDC 50 pin Cable Connector
- IDC50 2x25 Pins 0.1" Male Header Breakout Board

# Parameters Configuration
## 1. PPMM  

Pulses Per MilliMeter, used to convert the number of pulses in the 
controller to the unit of mm (or degree if rotation stage), need to 
be characterized for specified stepper and linear guide.
the distance of motion `L` (in the required engineering unit, e.g. mm);
- this value of `PPMM` should be `10000/L`.

## 2. LCA

Limit Correction Amount, in the unit of Pulses. When press the home 
limit button, the motor moves to the specified direction. After 
hitting the switch button, it reverses the direction by the amount 
defined by the LCA. 

## 3. Ratio

Ratio between motor pulses and encoder counts. This ratio depends 
on the motor type, microstepping, encoder resolution and decoding 
multiplier. Value must be in the range [0.001 , 999.999].

# Reference
Refer to the manual:
- [Arcus ACE-SDE Single Axis Controller-Driver Manual Rev 1.24.pdf](https://github.com/WeiLi-Alpha/Arcus/blob/main/Manual/Arcus%20ACE-SDE%20Single%20Axis%20Controller-Driver%20Manual%20Rev%201.24.pdf)
- [PMX-2ED-SA-Manual-Rev-1.18.pdf](https://github.com/WeiLi-Alpha/Arcus/blob/main/Manual/PMX-2ED-SA-Manual-Rev-1.18.pdf)

# Trouble shooting
Here is a list of the issues that occurred while testing the stepper motor.
## Stepper motor alternates its direction during/between motions
If the stepper motor alternates its direction during moving 
while it's expected to move in the same direction, the current 
pulses are not circulating as expected, the reason could be:
- The internal wire of the motor is broken  
  => one of the wires might be disconnected;
- The connection cable is broken   
  => one or two wires might be disconnected;
- The driver does not send the pulse sequence as expected  
  => one pair of outputs might fail.

Need to check with a multimeter:
- Measure the resistance between A-/A and B-/B to see 
  if it's close to zero (usually $\le 1 ~\Omega$). If it goes 
  to infinity, it's disconnected somewhere;
- The same diagnostic can be applied to the connection cable;
- Use the multimeter to measure the voltage of the outputs,
  if the voltage difference bwtween a pair of output is always zero,
  that driver chip might have failed.

## Encoder Ratio
To use stepper motor with encoders, one should properly setup the 
parameter `Ratio`. The procedures is as follows:
- properly connect the encoder cable from the stepper motor to the 
controller;
- turn off the encoder power stwitch, move the stepper motor by a 
number of steps N1, and read the encoder position N2, the ratio is
R=N1/N2;
- the value R should be a positive value in the range 0.001-999.99, 
if R is negative, one should try to switch the outputs of A <==> B 
and /A <==> /B.

# Control Pannel with MEDM
<center>
    <img src="https://github.com/WeiLi-Alpha/Arcus/blob/main/Manual/Motor_ACE-ADE_Full.png" height="600"/><img src="https://github.com/WeiLi-Alpha/Arcus/blob/main/Manual/Motor_PMX-2ED-SA_Full.png" height="600"/></center>

