---
title: Power Budget
---
<img src="https://raw.githubusercontent.com/shonha/EGR314SSH.github.io/refs/heads/main/images/POWERBUDGET.png" alt="Power Budget" style="border: 2px solid black;">

The motor driver maximum current is reliant on the stepper motor I am using, thats why it adds up to 0 mA. Using a 12V 2A Power Supply, it leaves room for other components as there is plenty of excess current if I needed to switch my stepper motor or microcontroller in case of emergencies. I must take into account though that since I am using a Daisy Chain Network, I need to consider the other subsystems that are being used by my team as we are all sharing a 9-12V external power supply, meaning this is only applicable when i'm using a barrel jack. After further testing, 2A was not efficient enough to power the entire team's daisy chain network which consisted of four boards. This could of possibly been a hardware issue so during the Innovation Showcase, each board was powered seperately using individual power supplies. 
