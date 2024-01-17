# trashcan80
place to dump some of my miscellaneous trs-80 related stuff

## trs804kb

This is my backlate work for @jaycrutti's TRS-80 Model 4 keyboard [replacement](https://www.jaycrutti.com/hardware-projects/tandy-trs-80-model-4-replacement-keyboard) using modern mechanical keyswitches.

## trs804p-gotek

This is a 3D printed faceplate and sled to put a Gotek floppy emulator inside the modem compartment of a TRS-80 model 4P. Uses one of those "0.91 inch 128x32" OLED i2c displays for more info. [FlashFloppy](https://github.com/keirf/flashfloppy) is my Gotek firmware of choice.

I have my model 4p configured to see this as a third floppy drive (DS2). The Trs80s can support 4 floppy drives, but the DS2 signal is not broken out to the floppy connector on the 4P mainboard (at least on my machine). The components are there, they just didn't put in the traces. 

My toggle switch swaps the DS2 and DS0 lines so that you can boot from the emulator if you so choose. To make this neater, I rerouted the DS0 signal on the mainboard so it runs down one one of the unused wires of the floppy cable instead of the one it's supposed to use. The DS2 signal is also isolated at the connector on the Gotek. The switch selects which signal should go to the real floppy drive and then sends it back up the correct line, so the real drive can remain jumpered to DS0. 
