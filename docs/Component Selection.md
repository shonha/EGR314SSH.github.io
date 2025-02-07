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
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/PIC16F1503.jpg" width="200" height="200">

* $0.99
* [Link to Product](https://www.digikey.com/en/products/detail/microchip-technology/PIC16F1503-I-SL/2772041)

|Pros               |Cons                      |
|-------------------|--------------------------|
|Fast Shipping      |Can't communicate over UART|

2. PIC16F18326-I/SL
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/PIC16F1503.jpg" width="200" height="200">

* $1.39
* [Link to Product](https://www.digikey.com/en/products/detail/microchip-technology/PIC16F18326-I-SL/6098362)

|Pros               |Cons                      |
|-------------------|--------------------------|
|Has UART and SPI compatibility|small programming size (24kB) compared to 128 kB used in class|
|Functions with MPX labs ||

3. PIC18F14Q20T-I/SS
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/150%7EC04-072%7ESS%7E20.jpg" width="200" height="200">

* $1.06
* [Link to Product](https://www.digikey.com/en/products/detail/microchip-technology/PIC16F1823-I-ST/2258581)

|Pros               |Cons                      |
|-------------------|--------------------------|
|UART and SPI compatibility|compatibility issues|


**Choice:** Option 2 PIC16F18326-I/SL

**Rationale:** I chose this specific microcontroller because it can communicate with UART and use an SPI to effectively control my stepper motor driver. It also has the necessary pins for the entire subsystem, leaving out extra pins for debugging purposes. It also works with MPX labs and the snap programmer. It also needs around 2.3V -5.5V to power which works perfectly with the switching regulator. The max current for GPIO pins are 50 mA and about 250 mA for the entire package. A 24kB programming memory should also get the job done.

### Motor Driver
1. DRV8434SRGER
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/MDOP1.jpg" width="200" height="200">

* $3.13
* [Link to Product](https://www.digikey.com/en/products/detail/texas-instruments/DRV8434SRGER/13627140)

|Pros               |Cons                      |
|-------------------|--------------------------|
|can communicate with SPI     |hard to solder/almost impossible|

2. DRV8434SPWPR
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/MDOP2.jpg" width="200" height="200">

* $3.21
* [Link to Product](https://www.digikey.com/en/products/detail/texas-instruments/DRV8434SPWPR/15857251)

|Pros               |Cons                      |
|-------------------|--------------------------|
|several half bridges|bigger than other options|


3. DRV8889QPWPRQ1
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/MDOP3.jpg" width="200" height="200">

* $4.17
* [Link to Product](https://www.digikey.com/en/products/detail/texas-instruments/DRV8889QPWPRQ1/11615769)

|Pros               |Cons                      |
|-------------------|--------------------------|
|can communicate with SPI|expensive option|

**Choice:** Option 3 DRV8889QPWPRQ1

**Rationale:** I chose option 3 because it is able to support a 5V stepper motor. It is also compatible with my PIC I chose after doing some research. Although it is the most expensive option, it also has good thermal padding and operating temperatures.
### Stepper Motor
1. MIKROE-1530
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/SMOP1.jpg" width="200" height="200">

* $9.60
* [Link to Product](https://www.digikey.com/en/products/detail/mikroelektronika/MIKROE-1530/5724295)

|Pros               |Cons                      |
|-------------------|--------------------------|
|cheap/affordable     |unipolar|

2. QSH4218-51-10-049
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/SMOP2.jpg" width="200" height="200">

* $67.78
* [Link to Product](https://www.digikey.com/en/products/detail/analog-devices-inc-maxim-integrated/QSH4218-51-10-049/4843427)

|Pros               |Cons                      |
|-------------------|--------------------------|
|bipolar/hybrid|super expensive|


3. 42M100B1B
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/SMOP3.jpg" width="200" height="200">

* $37.73
* [Link to Product](https://www.digikey.com/en/products/detail/portescap/42M100B1B/417819)

|Pros               |Cons                      |
|-------------------|--------------------------|
|bipolar/hybrid|no datasheet and hard to wire|

**Choice:** Option 1 MIKROE-1530

**Rationale:**  I chose option 1 because it is by far the cheapest out of all the options as stepper motors are really expensive. It does not have bipolar capabilities but can still be used for bidirectional control. 
### 5V Power Supply

1. SWI3-5-N-MUB
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/PSOP1.jpg" width="200" height="200">

* $4.90
* [Link to Product](https://www.digikey.com/en/products/detail/cui-inc/SWI3-5-N-MUB/7784529)

|Pros               |Cons                      |
|-------------------|--------------------------|
|cheapest option     |low current output|

2. QSH4218-51-10-049
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/PSOP2.jpg" width="200" height="200">

* $6.75
* [Link to Product](https://www.digikey.com/en/products/detail/tri-mag-llc/L6R06H-050/7682614)

|Pros               |Cons                      |
|-------------------|--------------------------|
|smallest charging block|low current output|


3. 42M100B1B
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/PSOP3.jpg" width="200" height="200">

* $6.82
* [Link to Product](https://www.digikey.com/en/products/detail/tri-mag-llc/L6R12-050U/7682629)

|Pros               |Cons                      |
|-------------------|--------------------------|
|high current potential|most expensive option|


**Choice:** Option 3 L6R12-050U

**Rationale:**  I chose option 3 because it supplies the highest current which will be needed for my stepper motor. It also has a USB power jack, making it convenient to carry around. It is the most expensive option but only about thirty more cents.

### 3.3V Switching Regulator

1. TLV61048DBVR
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/VROP1.jpg" width="200" height="200">

* $0.63
* [Link to Product](https://www.digikey.com/en/products/detail/texas-instruments/TLV61048DBVR/10715594)

|Pros               |Cons                      |
|-------------------|--------------------------|
|cheapest option     |6 pin configuration|

2. TLV61046ADBVR
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/VROP2.jpg" width="200" height="200">

* $1.09
* [Link to Product](https://www.digikey.com/en/products/detail/texas-instruments/TLV61046ADBVR/8133008)

|Pros               |Cons                      |
|-------------------|--------------------------|
|adjustable regulator|6 pin configuration|


3. MCP1603T-330I/OS
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/VROP3.jpg" width="200" height="200">

* $1.32
* [Link to Product](https://www.digikey.com/en/products/detail/microchip-technology/MCP1603T-330I-OS/1098431)

|Pros               |Cons                      |
|-------------------|--------------------------|
|buck regulator|smaller input voltage range|
|5 pin configuration||


**Choice:** Option 3 MCP1603T-330I/OS

**Rationale:**  I decided on option 3 because it has a similar pin configuration as the 3.3V regulator we designed in class. It is also a buck regulator, having a higher efficiency than most regulators. It does have a smaller input voltage range but my stepper motor is only using 5V.

