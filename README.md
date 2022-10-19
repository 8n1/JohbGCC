# JohbGCC v1.3

<img src="https://i.imgur.com/3Hr0nyt.png" width="45%">
 
This board is based on the PhobGCC v1.2.3 board (https://github.com/PhobGCC/PhobGCC-HW).  
  
It is 100% compatible with the PhobGCC software but requires a custom teensy.h. (More info below).  

--- 
  
The Board was made with KiCad version 6.0.5.  
Gerber and assembly production files were created using the KiCad plugin "JLCPCB Tools"  (https://github.com/Bouni/kicad-jlcpcb-tools).  


# Changes

- **Rotated the stickbox into original position**  
- **Rotated the Teensy 180°**  
- **Optimized the board paneling for manufacturing**  
- **Added some labels to make it very fail proof and easier to build**  
- **Tried to make the board easier to desolder (More info below)**  

## Other changes 

- **Both hall sensors on the c stick have a decoupling capacitor now**  
- **Routed the 3.3V and filled the top layer with GND too**   


# PCB

<img src="https://i.imgur.com/g4hP3WU.png" width="35%">
<img src="https://i.imgur.com/ktDSMyN.png" width="35%">

# Schematic / PCB tracks

<img src="https://i.imgur.com/d2445L4.jpeg" width="35%">  
  
<img src="https://i.imgur.com/L9F4D3K.jpeg" width="35%">  
<img src="https://i.imgur.com/O0rBgKY.jpeg" width="35%">  


# Custom teensy.h
  
Before uploading the PhobGCC software to the Teensy you need to copy the teensy.h for this board ("Johb1_3Teensy4_0.h") into the "teensy" folder that comes with the Phob software and tell it to use it.   
  
The *teensy.h"* is the configuration file that tells the Phob software to what pins the buttons, triggers, hall sensors are connected to the Teensy.  
  
This board requires a custom one because I re-routed most of the board after rotating the Teensy and to keep tracks nice and short I switched the GPIO pins.  


## Adding the JohbGCC teensy.h 

**Step by step:**
1.  Download the PhobGCC software (https://github.com/PhobGCC/PhobGCC-SW/releases)
2.  Download the JohbGCC teensy.h (https://github.com/8n1/JohbGCC/blob/master/Johb1_3Teensy4_0.h) and put it into the "teensy" folder that is included in the PhobGCC software zip file.
3.  Edit the file "common/phobGCC.h" to use the added JohbGCC teensy.h by adding this line as shown in the picture below:  
```
#include "../teensy/Johb1_3Teensy4_0.h"             // For JohbGCC board 1.3.x with Teensy 4.0
```
<img src="https://i.imgur.com/XPowAlR.png" width="35%">

4.  Done. Upload it to the Teensy. 

This has been tested with PhobGCC software v0.27 (https://github.com/PhobGCC/PhobGCC-SW/releases/tag/v0.27).  
For earlier versions the steps were slightly different.  
   
This is the only thing necessary to use the JohbGCC board with the PhobGCC software.  

# Modified/cut rumble bracket

It is necessary to modify the rumble bracket because the pins of the hall sensor interfere with it.  
  
**THIS MUST BE DONE, otherwise the controller can't be closed without force which causes various issues because the hall sensor pins will get crushed.**  
    
<img src="https://i.imgur.com/KK5e1PM.jpeg" width="35%">   
  
The text I put there says that it would be also possible to make the hall sensor pins flat instead but I found it much easier to just cut out a small part of the rumble bracket like shown in the pictures below so I would always recommend doing that.   
   
**"L" rumble bracket:**  
<img src="https://i.imgur.com/on0dNwA.jpeg" width="35%">  
**Rumble bracket with integrated trigger guards:**  
<img src="https://i.imgur.com/FKIZuTK.jpeg" width="35%">  
More pictures before and after cutting:  
https://imgur.com/a/gytP62m  



# Making it easier to desolder

I wanted to make the holes for some parts like the L/R potentiometer and GCC cable not through hole plated to make it easier to desolder (as it is on a OEM GCC board) but I haven't looked into how to do this enough and misunderstood a option in KiCad ("connected layers only") so I didn't got exactly what I wanted:  
<img src="https://i.imgur.com/QW1Yvjd.jpeg" width="35%">   
<img src="https://i.imgur.com/aZqT88x.jpeg" width="35%">   
   
But that's not bad actually, part success!  
They are still through hole plated, what that option did was to only remove the solder ring on the side where it's not needed.

... 

After doing some research it looks like that KiCad doesn't has this exact option built in.   
But what you can do is take a smd pad and put a not trough hole plated hole (aka. mounting hole) in the middle of it. But this way this manufacturer specification limitation comes into play (this is from jlcpcb):  
<img src="https://i.imgur.com/IvkqlrO.jpeg" width="35%">   
  
(I want to try this out with the mounting pins of the potentiometers on the next board I make.)


# Pictures

**Hall sensor footprints on c stick**   
<img src="https://i.imgur.com/2u1yAVK.jpeg" width="35%">  
   
**Square indicators that show where the part/cable goes**   
<img src="https://i.imgur.com/6rwubeC.jpeg" width="35%">
  
**Labels that indicate hall sensor orientation**   
<img src="https://i.imgur.com/YzBJW9b.jpeg" width="35%">


## More pictures

**Board as it came from JLCPCB:**  
https://imgur.com/a/ONnHoDy

**Soldered board:**  
https://imgur.com/a/rvYWUjU


***

# This project is based on PhobGCC
More informations about the PhobGCC project can be found here:  
https://github.com/PhobGCC  

***

# License
Text and images are licensed under Creative Commons CC-BY-SA.  
[Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/ "Creative Commons Attribution-ShareAlike 4.0 International")  
![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)  
  
KiCad board files are licensed under the CERN Open Hardware License.   
[CERN Open Hardware Licence Version 2 - Strongly Reciprocal](https://spdx.org/licenses/CERN-OHL-S-2.0.html "CERN Open Hardware Licence Version 2 - Strongly Reciprocal")  
![Open source hardware logo](https://i0.wp.com/www.oshwa.org/wp-content/uploads/2014/03/oshw-logo-100-px.png)  


***

If you have any questions contact me on discord (add me as a friend or find me in the PhobGCC discord): johgi#5103 (Might take a day or two to respond!)   
