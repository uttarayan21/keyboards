
## Corne 
Board: [petejohanson/crkbd][corne-pcb]  
Firmware: [haobogu/rmk][rmk]  
Model: [printables/void/crkbd][corne-3d-model]  
Keycaps: [kprepublic/xda-v2-gentleman-blank][xda-v2-gentleman-blank]  
Youtube: [youtube/EIGA/wireless-corne-keyboard-perfected][wireless-corne]  

#### Required
Note: This was taken from a stackskb.com listing of a wired corne kit and adapted to be a wireless kit   
Possibly more items will be needed.

- 1x PCB Set (left and right half of PCB)                   (we printed them)
- 2x Top Plates                                             (we printed them)
- 2x nice!nano compatible boards (supermini nrf52840)       (bought from robotkits.co.in)
- 2x nice!view displays                                     (bought from beekeeb.com) (60$ oof)
- 2x 600mah single cell lipo battery                        (bought from robu.in)
- 10x 8mm Brass Standoffs                                   (bought from robu.in)
- 20x 5mm screws                                            (bought from robu.in)
- 2x 2-pin SPST Switch (?)                                  (bought from robu.in)
- 45x SOD-123 Diodes (1N4148W)                              (bought from robu.in)

Other things that you'll need but not part of the keyboard  

Soldering Iron: Pinecil v2 / Fnirsi HS-02 (or any soldering iron you have)

### Planning
- pcb:
    We need to export the corne kicad files as gerber first.  
    To do so first install kicad  
    for macos you can just do  
    ```sh
    brew install --cask kicad
    ```
    for windows you'll have to manually install by navigating to the website  
    and for linux use whatever package manager your distro comes with.
    In kicad open the file `corne-ultralight.kicad_pro` file  
    Then click on the pcb editor  
    On the pcb editor click on the plot button ( the one that looks like a printer with legs )  
    Then click on Plot and then on Generate Drill files  
    This should make a gerbers folder on that same directory.  
    Zip it up and send it for printing.  
- hotswap sockets:
    I have an old sofle v2 that I bought but it turned out terrible.  
    I'll harvest that pcb for the diodes and hotswap sockets.  
    I don't have a desoldering pump so I'll just try to use desoldering wicks to get rid of all the connections  
- firmware:
    Right now I plan on using [rmk][rmk] which is a rust library for building keyboard firmware to have absolute control over what's going on in the keyboards.
    I have some usual generic keymaps that I always program in
    capslock -> control
    left control -> fn(1)
    command <-> option (only on macos)
    I'm using a nrf52840 which should be supported by this.
    I'm also using a nice!view display so I'll probably have to write some animations / apps for the display.

### Ordering parts
- pcb: I am ordering from robu.in since I am from india and its cheapest option available
    robu.in needs a gerber zip file (same as jlcpcb).

- case:
    ~~For the case you can get all the stl files from the links above.
    I used the 600mah battery and 6 column ones.
    For materials I used black abs at standard quality and 20% infill~~
    Update: I got a 3d printer and printed them myself.

### Steps
Align the diodes to the board with the line on the diode facing the same direction as the arrow on the pcb
![diode](../assets/corne/diode.jpeg)
![diode-pcb](../assets/corne/pcb-diode.jpeg)
You can use through hole sod123 diodes or you can use smd diodes.  
Soldering smd diodes are harder than through hole diodes so you may want to go with that if you don't have experience soldering surface mount components.  

Next you solder the microcontroller into the pcb.

Next you mount your switches to the plate (FR4 / Acrylic / 3D Printed).
And then solder the switches to the pcb.
It is important to mount the switches to the plate first since once soldered you can't mount the plate without desoldering.

![plate](../assets/corne/plate.jpeg)

Then you just solder the battery wires to the red-black terminals and put it inside of the case and you have your keyboard.
(Note: To mount it you need m2 screws they are self tapping screws so you don't need heat set threaded inserts for it)
![keyboard](../assets/corne/final.jpeg)

And it was so fun and easy that I built 2 of them.
![keyboards](../assets/corne/final2.jpeg)


[corne-pcb]: https://github.com/petejohanson/crkbd/tree/board/corne-ultralight
[corne-3d-model]: https://www.printables.com/model/347524-corne-keyboard-case-5-and-6-columns
[xda-v2-gentleman-blank]:  https://kprepublic.com/products/xda-v2-gentleman-blank-set-thick-pbt-for-keyboard-gh60-poker-87-tkl-104-ansi-xd64-bm60-xd68-bm65-bm68-dark-grey-black-yellow
[wireless-corne]: https://www.youtube.com/watch?v=YlZPnh9cbQU
[rmk]: https://github.com/HaoboGu/rmk



