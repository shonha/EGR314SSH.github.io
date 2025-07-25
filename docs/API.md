---
Title: API
---
## Team Bytes
| Byte | Function |
|----|-------|
| AZ | Start |
| YB | Stop  |

| Unique ID | Byte |
|-----|-----|
|Shon Ha| h |
|Maximus Mathews|m|
|Rohan Fernandez|f|
|Shelton Larance|l|

## Messages Sent
### Message Type 2 (Light Readings from Optical Sensor)

<b><i>Received and Forwarded to MQTT</i></b>

|               | Byte 1-2   | Byte 3-6   | Byte 7-8   | Byte 9-12 |
|---------------|------------|------------|------------|-----------|
| Variable Name | sensor_one | L1_Reading | sensor_two | L2_Reading | 
| Variable Type | char       | char       | char       | char       | 
| Min Value     | S1         | 0000          | S2         | 0000          |
| Max Value     | S1         | 9999       | S2         | 9999       | 
| Example       | S1         | 3567       | S2         | 2343       | 

## Messages Received
### Message Type 1 (Wifi Toggle - Auto/Manual)

<b><i>Used to toggle stepper motor functionality from automatic (state 0) to manual (state 1).</i></b>

|               | Byte 1      | Byte 2 |
|---------------|-------------|--------|
| Variable Name | mode | mode_toggle |  
| Variable Type | char    |  char | 
| Min Value     | M           |   0|
| Max Value     | M           |   1|
| Example       | M           |   1|

### Message Type 2 (Optical Sensor Readings)

<b><i>Used to determine where the stepper motor will rotate, facing the solar panel towards the highest light level detected by the optical sensors. Bytes 1-2 act as an identifier, allowing the stepper motor to determine which way to face once all four readings have been sent.</i></b>

|               | Byte 1-2   | Byte 3-6   | Byte 7-8   | Byte 9-12 |
|---------------|------------|------------|------------|-----------|
| Variable Name | sensor_one | L1_Reading | sensor_two | L2_Reading | 
| Variable Type | char       | char       | char       | char       | 
| Min Value     | S1         | 0000          | S2         | 0000          |
| Max Value     | S1         | 9999       | S2         | 9999       | 
| Example       | S1         | 3567       | S2         | 2343       | 

### Message Type 4 (Button - digital signal)

<b><i>Used to manually control stepper motors from left to right. It has two states (0) and (1) to determine if the button has been pressed.</i></b>

|               | Byte 1      | Byte 2       | Byte 3 | Byte 4 |
|---------------|-------------|--------------|--------|--------|
| Variable Name | left_button | button_left_toggle |right_buttom| button_right_toggle|
| Variable Type | char     | char    | char| char   |
| Min Value     | L           | 0            | R|0|
| Max Value     | L           | 1            |R|1|
| Example       | L           | 1            |R|0|

## Message Handling Process Flow
### Example Messages
|    | Message |
|-----|--------|
|Received| AZmhMOS13452S27865L1R0YB|
|Sent| AZhlS12313S28745YB |
### Messages Received

```mermaid
flowchart TD
    A[UART Message Received] --> B{Break down messages based upon message types}
    B --> |Message Type #4|K
    B --> |For Message Type #1| D{Read Message Type} -->|Automatic| G[State 0] 
    D -->|Manual| J[State 1]
    B -->|For Message Type #2| E{Compare two readings and store into array} -->|Highest Reading| H[Rotate Stepper motor towards direction]
    E-->|Lowest Readings|L[Trash messages]
    J -->  K{Control Motor with Two Buttons}
    K --> |Left Button| C[Turn Stepper Motor CW]
    K --> |Right Button| M[Turn Stepper Motor CCW]
```
