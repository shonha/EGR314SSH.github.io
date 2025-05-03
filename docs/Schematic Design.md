---
title: Schematic Design
---

<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/PCBFINAL.png" style="display: block; margin: auto;" alt="PCB Final">
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/PCBFINAL2.png" style="display: block; margin: auto;" alt="PCB Final 2">

<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/SchematicDesign.png">

## PCB Design
### Top Layer

<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/PCBTOP.png">

### Bottom Layer

<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/PCBBOTTOM.png">


[FULL ZIP Download](https://github.com/shonha/EGR314SSH.github.io/blob/main/Cadence/EGR314MOTOR.zip)

[Schematic PDF](https://github.com/shonha/EGR314SSH.github.io/blob/main/Cadence/EGR314PDF.pdf)

[PCB PDF](https://github.com/shonha/EGR314SSH.github.io/blob/main/Cadence/EGR314PDFPCB.pdf)

[MPLAB Software](https://github.com/shonha/EGR314SSH.github.io/blob/main/MPLAB/Hardware_VerificationV1.zip)


## User Satisfaction

The functionality of the motor subsystem satisfies user needs because it essentially is the backbone of this project. The sensors, HMI, and MQTT all rely on the feedback control the motor receives as it controls the direction of the solar panel, being the spotlight of this project. We want to educate students K-6 on solar power and the benefits of sustainable energy practices. All other subsystems are essentially inputs for the motor as they analyze light levels, manual button controls, and mode toggling which all fall under the motor. The stepper motor brings the project to life. It also satisfies product requirements as it fits under a bi-directional motor requirement as the motor adjusts itself in a 360 based on real time sensor data received or if a certain button is toggled when in manual control. 

## Decision Making Process

Our team's design for the motor subsystem is centered around precision, reliability, and compatibility. Stepper motors are reliable in moving heavier loads such as solar panels due to its high torque output and are more precise than your average DC motor as it uses step sizes to move precisely. We selected a 12V stepper motor because of its ability to provide precise positioning and also due to its torque factor to ensure that it can actually spin a chassis with the solar panel attached to it. The DRV8889-Q1 was chosen due to its many advantages as an SPI motor driver. It features a nFAULT output system that allows me to determine what is faulting the motor driver along with its many CTRL registers that control speed, current, stalling, and positioning. 


## Version 2.0

If I were capable of designing another version for my current motor subsystem, there would be many changes I would make to improve the overall design along with adding more functionality. It was at first intended to have two stepper motors but the price of motor drivers was exceedingly expensive. One motor would offer the 360 rotation which it currently has but then the other motor would add its tilt functionality to the solar panel so it can adjust its positioning from day to night. If possible, I would also replace my motors with more expensive ones. During testing, my motor would be exceedingly hot after about five minutes of being connected to my board. This is due to how stepper motors operate, as it actually takes current for the motor to remain stationary. Outside of class, I would have also moved away from MPLAB and PIC microcontrollers entirely as it proved to be challenging attempting to program SPI and also using the snap programmer. Another addition would be the switch from SPI to PWM outside of class as attempting to figure out SPI with the datasheet was a tedious process. 

Some minor hardware changes include getting a smaller fuse holder as the one I initially chose took up a decent chunk of the board. Another important change that I learned is to never leave any pins floating, especially for IC chips as you never know what might need to be jumped. I experienced many difficulties soldering wires to small solder pads as I figured out along the way that some pins on my motor driver were actually really important for full functionality. I would have also loved to add an extra debugging button as it would be easier to debug certain things such as the manual control of my stepper motor. It would also be important to note that I should always double check the datasheet because sometimes my circuit wouldn’t function properly because I didn’t ground something, especially my motor driver’s thermal pad. Another important note to self, especially when designing a PCB, is to leave a safety margin for traces to the board outline as all of my pcb boards were faulty due to a trace being too close to the board outline, causing me to jump a wire from my barrel jack a jumper. 
