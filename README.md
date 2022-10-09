# Arcus

This is an EPICS IOC for the Arcus stepper motor controller and driver: 
- [single-axis ACE-SDE](https://www.arcus-technology.com/products/single-axis-motion-controller/1-axis-usb-controller-plus-driver) and 
- [two-axis PMX-2ED-SA](https://www.arcus-technology.com/products/multi-axis-motion-controller/2-axis-usb-controller-plus-driver/)

# Required Modules
- [asyn](https://github.com/epics-modules/asyn)
- [stream](https://github.com/epics-modules/stream)

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
  that driver chip might fail.

# Control Pannel with MEDM
<center>
    <img src="https://github.com/WeiLi-Alpha/Arcus/blob/main/Manual/Motor_ACE-ADE_Full.png" height="600"/><img src="https://github.com/WeiLi-Alpha/Arcus/blob/main/Manual/Motor_PMX-2ED-SA_Full.png" height="600"/></center>

