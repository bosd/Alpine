# The Alpine Project

This is a fork of a fork of a fork.  :)
Will log my progress of this keyboard here.

After getting some small pains which could be an indication of the carpal tunnel syndrome I went down the rabbit hole of ergonomic keyboards (and mouse).
Profesionally I'm doing a lot of CAD work. Which involves a lot of switching of the hands between the mouse and keyboard.
In my spare time, I do some coding. 
After learning a lot about ergonomic keyboards it was time to get one myself. I did'nt find any commercail product which came close to my wish list. So someone with technical skills does, I decided to make my own.

My wishlist was:
- Dactyl manuform 5x6
- Trackball + Trackpointer
- Hot swap Thail
- RGB led per key
- Rotary Encoder
- Oled display
- USB C
- Silent switches
- Cool looking, but office accetpable :)

At start I wanted to design my own. I want to learn more about freecad and parametric modelling. But was struggling to get the [joshreve ](https://github.com/joshreve/dactyl-keyboard)or the [wylderbyld ](https://github.com/bullwinkle3000/dactyl-keyboard) generator to work. (The cadquery dependencies was breaking the code.)  After some hours struggling with it, pressured by time I decided to go with something of the shelve. 
The Alpine project was the one which came as close as possible.
I dropped the wish of having a trackball implemented, as it was limited in usage from what I've learned from other users.


I have no experience in 3d printing, so I decided to outsource.
Next step, was uploading the stl files to treatstock.com to get it printed.
Decided to give the semi-transparent Nylon a go. Will see how it ends up. 

Well changing to a different keyboard alone might not be enough.
To improve my ergonomics and productivity I want to do the following steps:
- Learn to use an alternative kyboard layout.
- Adjust my workflow, so I'll need to switch between mouse and keyboard less often.


In my research I learned that the most common qwerty layout might not be the best suited for today's interaction with the pc.
Years ago I've learned about the colemak layout. One thing which held me back was the learning something alternative / going against the herd. Well, right now I am a bit older. I don't care about going againsst the herd. I just want to do stuff that fits me and makes me happy. :) 
From the experience of other dactyl manuform users I've heard they had to learn how to type again.
Well since learning something new is involved, why not make the switch to a colemak layout at the same time. 
Most of my work is carried out the office of my clients. They will provide me with an regular qwerty keyboard.
So, propably after this one is finished, I'll make a different keyboard for travelling..




Based upon the result if nol00p:

![Ptero-Dactyl](/media/Ptero-Dactyl.JPEG)


# Acknoledgement
**Special thanks to [u/j_oshreve](https://www.reddit.com/user/j_oshreve/) on Reddit** for all his work on https://github.com/joshreve/dactyl-keyboard. Without all his is doing this project would not have been possible. 

I would note this repo would gave me a great guide to get to a working product. https://github.com/OutstandingOof/ducktyl-manuform
And off course the original: https://github.com/nol00p/Alpine

I would also like to thank alonswartz of giving me the idea of incorporating a trackpointer, without the need to cut into the keycaps or have a large space between them.  https://github.com/alonswartz/trackpoint/blob/master/README.md

The creators of the awesome mxledbit pcb's https://github.com/swanmatch/MxLEDBitPCB


# Though Process
the aim of the build is to try to get as clean a result as possible with all the features fully integrated in the case design. both the LCD are fully integrated in the case. the trays on both sides are mirrored to avoid crossing the trrs and the usb. 

# requirements 
* 3d printed parts for : 
  * case: both sides top and bottom
  * tray holder: both sides 
  * ec11 adapters
  * LCD tray
* Screws: wafer head M3 screws
* Screw inserts
* wires: I recommend single core wire, it is much easier to work with
* controllers: Elite C x2
* oled screens: SSD1306 128x32 0,91" OLED Display x2
* ec11 rotary encoders x2 
* Kailh hot swap sockets
* diodes: 1N4148
* MxLedbit PCB (container)
* switches
* keycaps



# The Build
## The case
all the 3D design and case generation was done thanks to the awesome work from u/j_oshrev at https://github.com/joshreve/dactyl-keyboard
![print](/media/Print.JPEG)

After the printing goes the painfully long process of picking out all of the support material, beeing carefull not to break anything. 

![print](/media/support.JPEG)

once the case is cleaned up, get the rest od teh component printed and install the sockets. 

![print](/media/kit.JPEG)

for this build I forked the loligagger tray to have a mirror version so that the usb and trrs wouldn't get crossed 

![tray](/media/tray.JPEG)
![tray2](/media/tray2.JPEG)


## Wiring 

the wiring is pretty straigh forward, juste take your time and use the right type of wires. I recommand single core wire. for the wiring i follow this: 
![right](/media/dactyl_manuform_right_wire_diagram.png)
![left](/media/dactyl_manuform_left_wire_diagram.png)

this key here is to get the diode orientation right! the black line on the diodes should all be connected together to from the row. the idea is that the current would not go back in the switch when activated. 

### The oled screens
connect GND to GND, VCC to VCC, SDA to pin 2 and SCL to pin 3.

### Rotary Encoders
To add the rotary encoder, wire the two pins on one side into the matrix, just like any other switch (press the encoder acts like any other switch). f
From the other side of the encoder (the one with 3 pins) connect the middle one to GND. The two outer pins of the other side have to be wired to the pins A2 and A3. more details bellow.
![encoder](/media/encoder.jpeg)

### the controller

the final part is to connect all those wire to the controller. 

![wiring](/media/wiring.jpg)

the wiring for a Pro Micro controler is the exact same.

the end result is something like this

![wired](/media/wired.jpeg)

# The Code
For simplicity sake, I have opted to install the elite-c on both sides. This makes flashing much easier by not having to deal with different loaders on each sides.

note: all the oled management code is pulled from the lily58. I need to spend time (and get help) to figure out how to better use the screen and get a setup that I actully like.
