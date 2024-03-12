# The Alpine Project

This is a fork of a fork of a fork.  :)
Will log my progress of this keyboard here.

After getting some small pains which could be an indication of the carpal tunnel syndrome I went down the rabbit hole of ergonomic keyboards (and mouse).
Profesionally I'm doing a lot of CAD work. Which involves a lot of switching of the hands between the mouse and keyboard.
In my spare time, I do some coding. 
After learning a lot about ergonomic keyboards it was time to get one myself. I did'nt find any commercial product which came close to my wish list. So someone with technical skills does, I decided to make my own.

My wishlist was:
- Dactyl manuform 5x6
- Trackball + Trackpointer
- Hot swap Khail
- RGB led per key
- Rotary Encoder
- Oled display
- USB C
- Silent switches
- Cool looking, but office acceptable :)

# Thought Process
At start I wanted to design my own. I want to learn more about freecad and parametric modelling. Yet, I was presurred by time, so decided to the [joshreve ](https://github.com/joshreve/dactyl-keyboard) generator to work. (The cadquery dependencies was breaking the code.) Instead of starting from scratch, I decided to base it upon an exsisting project. 
The Alpine project was the one which came as close as possible. I made many minor tweaks to design to get it perfect to my liking.
I dropped the wish of having a trackball implemented, as it was limited in usage from what I've learned from other users.

I have no experience in 3d printing, so I decided to outsource.
Next step, was uploading the stl files to treatstock.com to get it printed.
Decided to give the semi-transparent Nylon a go. Will see how it ends up. 

Well changing to a different keyboard alone might not be enough.
To improve my ergonomics and productivity I want to do the following steps:
- Learn to use an alternative kyboard layout.
- Adjust my workflow, so I'll need to switch between mouse and keyboard less often.


In my research I learned that the most common qwerty layout might not be the best suited for today's interaction with the pc.
Years ago I've learned about the colemak layout. One thing which held me back was the learning something alternative / going against the herd. Well, right now I am a bit older. I don't care about going against the herd. I just want to do stuff that fits me and makes me happy. :) 
From the experience of other dactyl manuform users I've heard they had to learn how to type again.
Well since learning something new is involved, why not make the switch to a colemak layout at the same time. 
Most of my work is carried out the office of my clients. They will provide me with an regular qwerty keyboard.
So, propably after this one is finished, I'll make a different keyboard for travelling.. (or a second one.)



Based upon the result if nol00p:

![nol00p-Dactyl](/media/nol00p-Dactyl.JPEG)


# Acknoledgement
**Special thanks to [j_oshreve](https://www.reddit.com/user/j_oshreve/) on Reddit** for all his work on https://github.com/joshreve/dactyl-keyboard. Without all his is doing this project would not have been possible. 

I would note this repo would gave me a great guide to get to a working product. https://github.com/OutstandingOof/ducktyl-manuform
And off course the original: https://github.com/nol00p/Alpine

I would also like to thank alonswartz of giving me the idea of incorporating a trackpointer, without the need to cut into the keycaps or have a large space between them.  https://github.com/alonswartz/trackpoint/blob/master/README.md

The creators of the awesome [MxLedbit](https://github.com/swanmatch/MxLEDBitPCB) pcb's.


# Required parts
* 3d printed parts for : 
  * case: both sides top and bottom
  * tray holder: both sides 
  * EC11 adapters
  * OLED clips
* Screws: wafer head M3 screws
* Screw inserts
* wires: 
  * I recommend single core insulated wire, for the connection to the controller.
  * For the daisy chain between mxledbit pcb's enamel wire can be used.
* Dupont connectors + crimping tool
* controllers: Elite C V4.0 x2
* oled screens: SSD1306 128x32 0,91" OLED Display x2
* ec11 rotary encoders x2
* Diodes (For the keypress of the encoder)
* [MxLedbit](https://github.com/swanmatch/MxLEDBitPCB) PCB (container) and it's components.
* Switches
* Keycaps



# The Build
## The case
All the 3D design and case generation was done thanks to the awesome work from j_oshreve at [dactyl-keyboard](https://github.com/joshreve/dactyl-keyboard)
(Image below is from the original noloop version)
![print](/media/Print.JPEG)

Since I do'nt own a 3d printer, I used the printstock.com service.
The first print was in transparent nylon. 
The result is okay'is. It looked kinda sloppy. Encountered the following problems:
* Dimensions where not accurate.
* I've made a mistake in the design such that it was impossible to mount the mxledbit pcb's. Without breaking away the hotswap socket holder from the prints.
* The Oled clip did'nt fit.
* Some area's printed too thin.

The seller sent me two cases. (As he acknowledged the prints where not the best).
One print was cleaned, the other was not. So After the printing goes the painfully long process of picking out all of the support material, beeing carefull not to break anything.
To give you an impression, Here is an image of noloop.

![print](/media/support.JPEG)

I decided to improve the design.
Which lead me down the path of improving the settings, the code and so on.
My improvements on the dactyl generator can be found in my fork. https://github.com/bosd/dactyl-keyboard

Short Summary of the changes:
* Changed position of OLED display
* Improved rim of OLED display (Will not show ugly borders)
* Changed hot swap holder to PCB holder
* Improved/fixed the [too thin to print](https://github.com/joshreve/dactyl-keyboard/discussions/92) problem area's.
* Fixed position of screw holes.

For the second print, I decided to use JLCPCB's print service.
The prints arrived in perfect condition.


For this build I forked the loligagger tray to have a mirror version so that the usb and trrs wouldn't get crossed. 
TODO: I went trough various versions of trays. Document which one I ended up using.

![tray](/media/tray.JPEG)
![tray2](/media/tray2.JPEG)


## Wiring 

The wiring is pretty straight forward, just take your time and use the right type of wires. I recommend single core wire. for the wiring I followed this basic dactyl schematic: 
![right](/media/dactyl_manuform_right_wire_diagram.png)
![left](/media/dactyl_manuform_left_wire_diagram.png)

I could have updated the image. But, I'm lazy and it still is a accurate representation of this version.
The Pro-micro has been exchanged to a Elite C. The wiring doesnt go to the socket directly but to the MXledbits. The colored wires go to the `C` connection. The white wires go to the `R` connection of the pcb.

The wiring of the other connections of the MXLedbit pcb's are straight forwared.
Connect all the + connections to each other with a daisy chain of enamel wire.
Do the same for the - connections.
The more challenging part is the DI, DO connection.
Connect the `B7` pin of the elite-c to the `DI` connection first mxledbit pcb.
Then chain them from `DO` to `DI` and so on. (See schematic on MXledbit repo.)


### The Oled screens
Connect GND to GND, VCC to VCC, SDA to pin 2 and SCL to pin 3.
See schematic below.

### Rotary Encoders
To add the rotary encoder, wire the two pins on one side into the matrix, just like any other switch (press the encoder acts like any other switch).
From the other side of the encoder (the one with 3 pins) connect the middle one to GND. The two outer pins of the other side have to be wired to the pins A2 and A3. more details below.
Tip: Use heatshrink on the 3 pins to prevent unwanted contact of these pins to each other.
![encoder](/media/encoder.jpeg)

### The Trackpointer
This is a WIP.
Bought an old IBM/Lenovo laptop keyboard with integrated trackpointer.
Will re-purpose that trackpointer on the dactyl.
Currently figuring out the circuit and mechanical placement.
I'm Looking at a place on the thumb cluster. As it is more accurate to control with a thumb as an index finger. Something similar to [this](https://www.reddit.com/r/ErgoMechKeyboards/comments/susgnh/thumbtackpoint_i_shall_never_move_my_hands_again/)

### The controller

The final part is to connect all those wires to the controller.
( I used dupont connectors to connect to the header of the controller, so future upgrade will be easier.)

Since there are not enough VCC and 5V connections on the controller pcb.
I've used an dupont header, connected on one end with a wire jumper to act as a potential distributor.
So multiple connectors can connect to the same potential.

![wiring](/media/wiring.jpg)

The end result is something like this

![wired](/media/wired.jpeg)

With some brown oem pudding keycaps for testing purposes.
![assemblytest](/media/assemblytest.jpg)

### Firmware
For sake of simplicity, I have opted to install the elite-c on both sides. This makes flashing much easier by not having to deal with different loaders on each sides.
I've made a configuration for the QMK firmware [here](https://github.com/bosd/Alpine/tree/main/alpine).
(It's still a WIP)