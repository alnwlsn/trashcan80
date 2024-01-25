# trashcan80
place to dump some of my miscellaneous trs-80 related stuff

## trs804kb

This is my backlate work for @jaycrutti's TRS-80 Model 4 keyboard [replacement](https://www.jaycrutti.com/hardware-projects/tandy-trs-80-model-4-replacement-keyboard) using modern mechanical keyswitches.

## trs804p-gotek

This is a 3D printed faceplate and sled to put a Gotek floppy emulator inside the modem compartment of a TRS-80 model 4P. Uses one of those "0.91 inch 128x32" OLED i2c displays for more info. [FlashFloppy](https://github.com/keirf/flashfloppy) is my Gotek firmware of choice.

I have my model 4p configured to see this as a third floppy drive (DS2). The Trs80s can support 4 floppy drives, but the DS2 signal is not broken out to the floppy connector on the 4P mainboard (at least on my machine). The components are there, they just didn't put in the traces. 

My toggle switch swaps the DS2 and DS0 lines so that you can boot from the emulator if you so choose. To make this neater, I rerouted the DS0 signal on the mainboard so it runs down one one of the unused wires of the floppy cable instead of the one it's supposed to use. The DS2 signal is also isolated at the connector on the Gotek. The switch selects which signal should go to the real floppy drive and then sends it back up the correct line, so the real drive can remain jumpered to DS0. 

- Tandy 6000 Keyboard circuitry explained: https://www.youtube.com/watch?v=PWalT-7FzVU

## 8inch-adapter-pcb
Single sided, CNC cut PCB for converting the 50 pin 8" floppy disk cable to the more common 34 pin cable. Based on this https://github.com/pski/fd50to34 and made so I could quickly cut one out and start using it. Intended for a Gotek floppy disk emulator with https://github.com/keirf/flashfloppy

It might only work with a Gotek. On that, you can assign pin 34 to Drive Ready, and pin 2 to Disk Changed. On a real 5" or 3.5" drive, pin 34 is usually Disk Changed (but you can sometimes jumper it to drive ready instead), and pin 2 is used to select the density or disk RPM. 

**Update** - After nearly a week of confusing symptoms, I discovered that in some cases, the 6000 really does care if the disk drive reports 1 or 2 sided media. The Xenix install floppies come on both types, and the install will fail if the wrong type is used (you will get HRDIOE). I isolated pin 10 on the 50 pin side - this should be connected to a switch or jumper to GND; if you want to report 2 sided media, close the switch. Otherwise, leave it open.

## ps2-keyboard
Converts a ps2 keyboard to one that works with a TRS-80 8-inch system. Made because I was getting impatient waiting to fix the broken keyboard I have. Runs on an Arduino pro micro, but similar things should work. Similar to this converter https://www.smbaker.com/tandy-1000-upgrades-ps2-tandy-keyboard-adapter but for the Tandy 6000 instead of the Tandy 1000, and made more lazily by using the Arduino framework. Uses this PS2 arduino library https://github.com/techpaul/PS2KeyAdvanced

Change the mapping how you wish; I have not checked it against the real tandy 6000 keyboard, but it seems to mostly work well anyways. 

## Misc Notes - tandy 6000
* installing 2nd bank of DRAM for 128K on z80 board (or how I learned to read the instructions)
  * Be sure to remove C81-C83, if not already removed. These are used as power bypass caps for 16K rams, but for 64K rams, an address signal is on those pins instead. If the caps are present, they stretch the signal out too much and it doesn't work, which is why they must be cut out. See model 12/16 technical bullitin #18.

## CCR-81
3D printed battery cover replacement for CCR-81 / CCR-81A Cassette Tape Recorder
