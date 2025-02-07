---
title: Component Selection
---
## Role and Responsibilities

I am responsible for the actuator and using a PIC. This will be done using a stepper motor to control the rotational movement of the solar panel so it can face the sun. I will communicate using a Serial Protocol Interface (SPI) along with a stepper motor driver. To communicate with the daisy chain, I will communicate over UART to receive data from the optical sensor, allowing the stepper motor to rotate based on where the sun is facing.  The microcontroller will be powered using a 3.3V switching buck regulator and a 5V power supply to power the 5V stepper motor.

## MCC Configuration

<img src ="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/MCC%20CONFIG.png">

I chose a 14 pin PIC as my main microcontroller as my subsystem will initially only need about 6 pins to work effectively. Two pins are designated to RX and TX pins so I can communicate to the daisy chain network. 4 pins are designated to the stepper motor driver, focusing on SCK, SDI, SDO, and SS. We have a clock, serial input, serial output, and slave select that will connect to the stepper motor driver. Other pins are free of use and can be used for debugging purposes.

## Major Components Selection

### PIC Microcontroller
1. PIC16F1503-I/SL


### Motor Driver

### Stepper Motor

### 5V Power Supply

### 3.3V Voltage Regulator
