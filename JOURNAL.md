# JOURNAL.md

---

title: "quartz58"
author: "tim"
description: "My attempt at a dream keyboard"
created_at: "2025-07-15"

---

**Total Time Spent**:

## ~May-July 14: Research

**Time Spent**: ~8 hours

- Researched split keyboards, specifically Lily58 and Corne layouts.
- What I wanted in a keyboard/use, if I wanted a track pad, rotatory knob, leds etc.
- At the same time learned about, how to use and created a layout on Ergogen, and starting on the pcb. (although later this was just used for key layout due to the amount of custom parts being used)
- Came up with a list and created a google doc to document everything found and what needs to be worked on.
- Compared and contrasted if I wanted a oled or nice!view epaper screen, with RGB to figure out battery life (just decided to go with nice!view and per key RGB and potentially 4000-2000mAh battery to also add weight)
- Also decided to go with MX switch footprint instead of choc, due to mx's superior sound and I'm not ready to commit fully to choc switches
- Found more specific parts such as the TPS65 Touchpad, ANO rotary wheel and comparing that to models such as the cirque track pad, and conventional knobs
  ![LAYOUT IN ERGOGEN](IMGS/ergogenlayoutv1.png)
- Created onshape to continue to mess with the layout and the dimensions of the new parts
  ![SEEING IF TPS65 CAN FIT](IMGS/beginningOfOnshape.png)

**NOTE**: I started doing early planning, and researching part on and off throughout march, early july due to other commitments, but majority of design and firmware development is happening in July (from now on).

## July 15: True Beginning

**Time Spent**: ~2 hours

- Created Github repo
- Uploaded all my documents here and started writing the journal

## July 17:

**Time Spent**: ~6 hours

- simplifed ergogen config to remove the PCB stuff
- TRRS conundrum
  - When deciding what to do with this keyboard I wanted a fallback just incase if there wasn't any batteries installed or I was using a normal promicro instead of a nicenano or their equivalents for them to keep working. Although when doing the schematic for the pcb I realized this is going to be a pretty difficult decision to make as I was already running out of pins, additionally there can be dangers if I do have this TRRS port to connect the two for them to fight on voltage
  - Additionally with its compatibility with zmk
  - Ultimately I decided to veto it for now and if I were to have one of the above problems I would just connect each separately to the computer.
- ANO Directional Navigation and Scroll Wheel Rotary Encoder
  - Found the white version of this encoder at digikey with the part number TSWB3NCB111LFS
  - Found datasheet for it, so I can later create my custom pcb for it
- TPS65 Trackpad
  - Found the datasheet for it, so I can later create a custom symbol for it
- THUS to conclude today, completed simple stuff of the schematic, although I would still need to create the custom symbols for the ANO encoder and TPS65 ENCODER
  ![progress on schematic so far](IMGS/schematic2025-07-17.png)
