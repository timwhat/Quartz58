# JOURNAL.md

---

title: "quartz58"
author: "tim"
description: "attempt at a next to no compromises keyboard"
created_at: "2025-07-15"

---

**Total Time Spent**: 97.75 hours

## ~May-July 14: Research

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

**Time Spent**: 8 hours

## July 15: True Beginning

- Created Github repo
- Uploaded all my documents here and started writing the journal

**Time Spent**: 1.5 hours

## July 17: Progress & Decisions

#### Ergogen Config

- Simplified the Ergogen configuration to focus solely on the key layout, removing PCB-specific elements.

#### TRRS Conundrum

- Considered adding a TRRS port as a fallback for situations without batteries or when using a Pro Micro instead of a Nice!Nano (or equivalents).
- Faced challenges with limited pin availability and potential voltage conflicts if both sides are connected.
- Evaluated compatibility with ZMK firmware.
- Ultimately decided **not** to include the TRRS port for now. If issues arise, each half will be connected separately to the computer.

#### ANO Directional Navigation & Scroll Wheel Rotary Encoder

- Spent significant time searching for pre-made schematic symbols and footprints.
- Discovered the white version of the encoder (TSWB3NCB111LFS) available on Digi-Key.
- Located the data sheet, enabling future creation of a custom PCB footprint.

#### TPS65 Trackpad

- Found the data sheet, which will help in creating a custom symbol for schematic integration.

#### Schematic Progress

- Completed basic schematic elements.
- Next steps: create custom symbols for the ANO encoder and TPS65 trackpad.

![Progress on schematic so far](IMGS/schematic2025-07-17.png)

**Time Spent**: 6 hours

## July 18: DOWN THE RABBIT HOLE

### ANO Directional Navigation and Scroll Wheel Rotary Encoder

- After realizing that the TSWB3NCB111LFS encoder is not in stock anywhere, I decided to contact the creators of the soflePLUS2, which features this encoder.
- Reached out to them on Instagram; they mentioned being based in Malaysia, with their supplier in China—making shipping to Canada quite expensive.
- For now, I'll use the glossy Adafruit encoder, even though it may not match the color scheme.

### Schematic

- Learned how to create symbols in KiCad and completed basic symbols for the trackpad and encoder.
- Refined more of the schematic and started assigning footprints.

| ![TPS65 footprint](IMGS/TPS65_footprint.png) | ![ANO encoder footprint](IMGS/ANO_encoder_footprint.png) |
| :------------------------------------------: | :------------------------------------------------------: |

![Progress on schematic so far v2](IMGS/schematic20250718.png)

**Time Spent**: 4.5 hours

## July 19

#### Custom Choc + MX hotswap

- Due to my indecision I decided to make sure that I could use both choc and MX switches on these pcbs.
- After tons of googling I couldn't find what I was looking for, although I could find it in one of the keyboards that I am using for inspo, the sofle plus 2.
- They just layered it on top of each other so you could just chose and they had the LED at the bottom still.
- So I decided to take the same approach and just layer two hotswap footprints on top of each other to achieve this, by following a guide on the kicad forms, which was just copying text from one file to another

![Cursed hotswap footprint](IMGS/MX_Choc_Hotswap.png)

- I then cleaned it up with some of the overlays stacking.
- I do plan on making it more polished with the outlines and looks more complete, but since it doesn't effect anything else right now, only asthenics I'll worry it about it later.

#### Starting PCB Laying out

- I first did all the basic stuff just assigning footprints, however I didn't for my trackpad and encoder as im making those later and I'll just insert it later.
- I then spent an hour just attempting to layout the switches according to the ergogen, then I figured out that I could just use the ergogen one, import it into mine, change the footprint to my type of switch
- I also roughly placed some of the components such as diodes and leds to get here

![PCB so far](IMGS/schematic20250720.png)

- Although when doing this I ran into a problem where my thumb key was a bit too close to each other so I had to go back to ergo gen and fix that, then import it back and align it by stacking a nearby switch to not ruin the other progress I've made

![minor overlap :((](IMGS/thumbKeyBeingTooClose.png)
![fixing the thumb key in ergogen](IMGS/fixingThumbKey.png)

- So far my thoughts are that I might be way in over my head due to only ~10 days being left and still so much todo (CAD and zmk) and the goals I want to achieve with this keyboard, but I think I got this!!

**Time Spent**: 5.5 hours

## July 23

- I had to take a break to focus on finishing my summer school, and today I just took the final exam and now I'm back, hopefully I can finish this in time

#### ANO Encoder Update

- After reviewing the encoders data sheet I realized I had wired the encoder wrong and I can't integrate SW1 into the matrix
- So I just used one of the middle pins on the nice nano

| ![new MCU and ANO Encoder wiring](IMGS/anoEncoderWiringPt2.png) | ![ANO encoder wiring data sheet](IMGS/anoEncoderWiring.png) |
| :-------------------------------------------------------------: | :---------------------------------------------------------: |

- Tomorrow I will make the pcb for this ANO Encoder

#### General Planning/PCB

- Figured that instead of just placing each led and diode one by one, which is repetitive and might lead to mistakes I will just instead just do it in ergo gen and change the footprints and assign them like what I did for the switches
- I might also do this for the MCU placement n stuff
- As I'm mixing 19.05mm with 1mm stuff which makes it tricky to make it all consistent
- which I started doing today, I also minimized the perimeter of the pcb to allow for

**Time Spent**: 1.5 hours

## July 24

#### General PCB Stuff

- Readjusted my thumb key again to make it perfect with the references of onshape
- I decided I liked the look of a smaller pcb that minimizes the area instead of the normal lily58 so I changed that in ergogen (taking wayy longer than I thought bc ergogen isn't as easy to use as onshape)
- Also I put in the leds in ergogen so I can remove me manually placing it which could lead to mistakes, I didn't do this with the diodes like I planned but I want to place them fancy later to efficiently use up the space
- This lead me to basically restarting the pcb

| ![redoing the thumb key again](IMGS/redoingThumbKey.png) | ![pcb update](IMGS/schematic20250725.png) |
| :------------------------------------------------------: | :---------------------------------------: |

- I also found side mounting of the buttons and switches that I will be using!
  - The SSSS and panasonic one, used on the typeractive keyboards

| ![SSSS811101 footprint](IMGS/SSSS811101footprint.png) | ![Panasonic push button footprint](IMGS/EVQPUfootprint.png) | ![Changing the footprint](IMGS/changingFootprintForSWandButton.png) |
| :---------------------------------------------------: | :---------------------------------------------------------: | :-----------------------------------------------------------------: |

#### CAD more scafolding

- I added in the components into the cad with the keys in a sketch to plan out where everything's gonna go
  - Although I am still missing the acrylic cover I'm gonna make to cover the mcu and display

![cad updates](IMGS/cad20250725.png)

**Time Spent**: 4.5 hours

## July 26

#### ANO Encoder

- Today I made significancy more progress on this encoder
- Made the footprint, which took a while as I've never done before and there wasn't one available online (THANK YOU DIGIKEY FOR THE AMAZING KICAD FOOTPRINT GUIDE)
  - Some notes about this footprint is that it took a surprisingly long time and a pain to make and line up with the schematic although after some time I made it work
- I ALSO FOUND THE GREAT FH12 FFC cable connectors to connect the trackpad and encoder daughterboard to their respective halves after tons of time searching
  - It also took sometime finding the footprint but luckly it was in the kicad footprints library :DD
- Also planned more out of this daughterboard pcb layout and dimensions in onshape

| ![ANO Encoder Schematic Updates ](IMGS/anoEncoderWiringPt3.png) | ![ANO Encoder Footprint With FH12 Connector](IMGS/anoEncoderWiringPt4.png) | ![PCB size and perimeter decided](IMGS/cad20250727.png) |
| :-------------------------------------------------------------: | :------------------------------------------------------------------------: | ------------------------------------------------------- |

#### General PCB

- Realized that the spacing between the center of the led and the center of the switch was 5.08 mm not the 4.5 I eyeballed by looking it up in the Keyboard Atelier discord
  - Making me change that entire thing in ergogen, then transferring it backk to kicad
- With that change and having the numbers on each of the components messed up I decided to renumber them in the schematic and then Kicad
  - Then I went through it all and make sure each switch and led lined up with its counterpart in the schematic which was wayy too tedious
  - At this point I settled on the leds going in a zig-zag pattern for wiring for simplicity and shorter run lengths
- I also started placing all of the diodes on one of the halves manually so I can have more space for fancy wiring and their traces for the switches

![PCB updates](IMGS/pcb20250727.png)

**Time Spent**: 6.5 hours

## July 27

- First thoughts, I might not be able to finish on time because of all the trouble I'm having with the pcb and other responsibility now also popping up in the next few days :/

#### General PCB

- In the morning I realized that the via's can't really be ontop of the pads so I changed each of them so they would be atleast 0.4mm away
- Continued routing this pcb and ran checks
  - This is where I got 1k+ errors due to my hacked together switch and sketch stuff, making me spend some time fixing that
  - First with the switches I switched some of the holes to edge cuts and changing some of the settings and tweaking the overrides, along with the leds

| ![PCB updates and less errors](IMGS/pcb20250728.png) | ![MX Choc Hotswap fix](IMGS/MX_Choc_HotswapPt2.png) | ![Overriding the error with the led pads being too close to the edge cut](IMGS/overideLED.png) |
| :--------------------------------------------------: | :-------------------------------------------------: | ---------------------------------------------------------------------------------------------- |

#### ANO Encoder

- Created the general shape of the breakout board first in onshape then moving it to kicad
- I might need to rotate it so that the 7 and 5 pins are away from the right edge as that would be where they would be most visible as they poke out a bit more then the others

![updates to ano encoder](IMGS/anoEncoderWiringPt5.png)

- Final thoughts for today, I think I need to finish the left side entirely tomorrow and I might be able to also start on the CAD and finish that within a day due to my experience
- I also might need to do a bare bones zmk config without the fancy online key editing just for this project to be submittable on time

**Time Spent**: 7 hours

## July 28

- Not sure why but I'm just having trouble focusing on this :// might be the amount of sleep I'm getting but I will try and get this done by hopefully end of 30th to leave the 31st for any last minute
- Also summer school has started once again which may become a problem in the next few days

#### ANO Encoder

- FINALLY SHOULD'VE HAD THIS 4 DAYS AGO
- Created daughter board footprint along with lining it up on the pcb with the connectors, also created a cutout so that the fpc connector can be passed through
- Also I rotated and rerouted the daughter board so it would work better

| ![New Daughter Board](IMGS/anoEncoderWiringPt6.png) | ![With new footprint of daughter board and wiring](IMGS/anoEncoderWiringPt7.png) | ![Integration](IMGS/pcb20250729.png) |
| :-------------------------------------------------: | :------------------------------------------------------------------------------: | ------------------------------------ |

#### General PCB

- Worked on routing so the left side is basically done and should be much faster to route the other with a blue print basically
- Got the errors down a bit more although they are minor and can be fixed relatively quickly
- Although I realized that this doesn't have the 0.5 fillets which I might add back with the help of ergogen
- Made the pcb exportable by fixing all of the outline errors with the mx switches and ano encoder

| ![Pcb with number of errors left](IMGS/pcb20250729pt2.png) | ![CAD in kicad](IMGS/cad20250727.png) | ![CAD in onshape with mates](IMGS/cad20250729pt2.png) |
| :--------------------------------------------------------: | :-----------------------------------: | :---------------------------------------------------: |

- Also looking back on this pcb after developing more of the cad I might move the mcu along with the displays slightly
  - Additionally I need to figure out the mounting holes for the acrilic cover
- In the CAD this is also what I am planning so far

  - Thicker bezzels (~7mm or less)
    - Accommodate a ball catch mechanism like in the rd75
    - and to house a gasket mounting system
      - This will also most likely be a poron foam strips thing in the front and back mounted to the plate
      - Although this might be ditched and reduced to just a plate isolating system due to time and wanting the keyboard to be relatively thin

  **Time Spent**: 7 hours

## July 29

#### ANO ENCODER

- Redid polarity of the encoder to work with the type A ffc cable
- Also slightly reduced the size of the daughter board

| ![Ano](IMGS/anoEncoderWiringPt8.png) | ![Closeup of connector on daughter board](IMGS/anoEncoderWiringPt9.png) | ![Closeup of connector on pcb](IMGS/anoEncoderWiringPt10.png) |
| :----------------------------------: | :---------------------------------------------------------------------: | :-----------------------------------------------------------: |

#### General PCB

- Updates to pcb by editing ergogen then importing into kicad to have the .5 fillet on the pcb so its smoother

#### CAD

- Worked on CAD, added the plate, top case, and bottom case so far
- I also added the supporting such as the headers for the mcu, and adding in the ano encoder with the nice!view display
- Additionally I laid out where the ball catch mechanisms are suppose to go along with the poron gaskets
- I spent a bit too long on figuring out how to create the case in the way I wanted due to all of the variables, although I figured it out in the end with a bunch of sketches

https://cad.onshape.com/documents/873cec737929b1b06537c433/w/1c9e733c7d397ada1b99a04d/e/52e5a88970633a5c0f63818b

| ![CAD so far](IMGS/cad20250730.png) | ![Part studio of case currently with some sketches shown](IMGS/cad20250730Pt2.png) | ![hitbox for ball catch mechanism](IMGS/cad20250730pt3.png) |
| :---------------------------------: | :--------------------------------------------------------------------------------: | :---------------------------------------------------------: |

**Time Spent**: 8 hours

## July 30: LOWKEY REALLY BEHIND

#### CAD and PCB Stuff

- Worked a bit on placement of the trackpad and creating a bounding box, starting on a case for that
- Also rearranged a bit of the mcu with the display so they would all fit correctly above the switch
  - Additionally I made sure the usbc wouldnt stick past the pcb so I made it 0.2mm away from the edge to play it safe

| ![additions of precise mcu and display placement](IMGS/cad20250731.png) | ![track pad bounding box starting on case](IMGS/cad20250731pt2.png) |
| :---------------------------------------------------------------------: | :-----------------------------------------------------------------: |

before and after!

| ![before, eyeballed placeholder placement of mcu and displays](IMGS/pcb20250731pt2.png) | ![now done above the switch (mcu and display placement)](IMGS/pcb20250731.png) |
| :-------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------: |

#### MONUMENTAL ZMK RUN

- I first imported the standard lily58 zmk config
  - Customized to fit my pins, added my own shield and the encoder with its 4 buttons
- When working on it I realized that I needed to make the numbering consistent so I make the go from 0 on the left and +1 as it got to the right cols
- Swaped around the cs and rgb pins to high frequency ones because of reading through the docs it recommended that
- So then I was ready to compile and it just wouldn't work so I used github co-pilot to help me understand the errors along with a friend, and then many iterations later...
- After commenting out the cs nice!view and trackpad stuff it compiled!!!
  https://github.com/timwhat/zmk-config-quartz58/tree/main
- So if I have any time remaining for this I will continue to make these features work and add additional features such as cool rgb affects, If not I will work on it while I wait for my parts to ship

| ![File Structure](IMGS/zmk20250731.png) | ![how many commits it took)](IMGS/zmk20250731Pt2.png) |
| :-------------------------------------: | :---------------------------------------------------: |

**Time Spent**: 7.5 hours

## July 31: Basically done

- Will write more in a few hours to document what's been done but completed wiring on both sides of pcb
  - I will clean up the wiring on the right side as it was really rushed to get it in by the deadline (making the traces look nicer with some pcb pattern)

#### CAD and PCB Stuff

- Completely finished routing everything
  - While doing this I made some changes to schematic to make routing some of the traces easier
- Created Gerber files for quote
- Created TPS65 Mount along with other minor stand offs
- Continuously refined case
  - Added Magsafe for tenting support and gaskets for visuals

![CAD](IMGS/cad20250801.png)
![pcb](IMGS/pcb20250801.png)
![schematic](IMGS/schematic20250801.png)
| ![magsafe mount](IMGS/cad20250801pt2.png) | ![pcb](IMGS/cad20250801pt3.png) |
| :--------------------------: | :--------------------------: |

- Wrote BOM list
- Completed README requirements

- My Next Steps
  - Rename the files in the kicad to match conventions
  - Continue to polish the pcb traces and silkscreens (currently **FULLY** working this is just for asthenic)
  - Continue to refine case if any ideas or thoughts for improvements pop up
  - Complete ZMK as it compiles and test on the real keyboard once received

**Time Spent**: 11 hours

## August 1st

- Today I just caught up on school work and fixing my sleep schedule, and trying to get unburnt out from this
- I also updated the gerbers as I switched JST footprints so they are through hole and I could source it to typeractive

![pcb](IMGS/pcb20250801pt2.png)

**Time Spent**: 0.25 hours

## August 2nd

- Woke up to a slack message and my rereview being rejected sadly :/
  - Due to this not qualifying for a 10 point project despite my nativity thinking it would and only checking with other highway members and not a reviewer.
- I had to rethink what I wanted out of this keyboard, as I can not afford the difference in its current state
- Basically entire day until late evening I started working on this

#### PCB - SK6812 Mini Power Problem

- I also realized that for the LEDS, I felt like them having such thin traces felt wrong so I decided to dive deeper
- After looking through its [datasheet by Adafruit](https://cdn-shop.adafruit.com/product-files/4960/4960_SK6812MINI-E_REV02_EN.pdf), it takes 1mA as static, 12mA per RGB so 37mA total at 3.7V, 29 LEDs per side, resulting in 1.073A per side.
- Going into [digikey trace calculator](https://www.digikey.ca/en/resources/conversion-calculators/conversion-calculator-pcb-trace-width) it says the min trace with in external layers, in air would be 0.34mm, so I decided to go with .45mm trace widths to be save **IF ANYONES READING THIS PLEASE CHECK IF THIS IS CORRECT**
  ![pcb](IMGS/tracecalc20250803.png)
- Then I made sure the led's used their own nets, and then I set them to this new .45mm trace witdth
- This is where I ended this part for the night I will figure out this routing tomorrow morning

![pcb](IMGS/pcb20250803.png)

#### BOM Update

- Decided to ditch the encoder and trackpad cover for now among other items that I will save up for and purchase my self at a later date
- Also switched the battery from 2000mAh to the 750mAh one from typeractive because they come with the jst 2.0mm connector so I dont have to buy that + slightly lighter and I don't want
- Also optimized everything to save on shipping so I switched around the connectors to use mouser and yea! I'll hopfully have more progress tomorrow as I am less busy

**Time Spent**: 2.5 hours

## August 3rd

#### PCB

- After spending a afternoon jumping down the rabithole of powering these sk6812mini's looking in various discord servers I found out you also need level shifters and capacitors for these leds are 5v
- Since by board doesnt really have room for this + this would add tons of complexity I finally made the call to ditch them, they will prob be present in the next revisions of this board
- Also I found leds such as the sk6805 which does work at 3.3v, but they are wayyy too small and difficult to solder for my experience so yea
- Thus now that I didn't need the LED's, instead of having to choose to use the mx or choc sockets in a switch location I remembered that I saw a board that used both
  - Since I couldn't find a footprint for this I decided to repeat what I did with the og mxchoc hs footprint and just make it again but the choc socket this time would be on the bottom
  - Also I had to turn some of the holes into edge cuts so they wouldn't produce a warning where the two holes were too close

![pcb](IMGS/pcb20250804.png)

- So after removing the LED's and changing the footprint I routed everything on both sides which took some amount of time and I added a inverted thing to make it look cool

![pcb](IMGS/pcb20250804pt3.png)

- I also added this pattern which I might change to like a grid later on before ordering

![pcb](IMGS/pcb20250804pt2.png)

- After that I updated gerbers and got a jlcpcb quote again so its up to date
- Considering cleaning up more of the traces to make this pcb perfect but, everything currently works!!

#### BOM

- Changed some stuff around for formatting and switched the 10 pin fpc cable to 6cm as that place better fit that.

**Time Spent**: 4.5 hours

## August 4th: Getting ready for review

#### Display

- For the display I realized that having only one pointing point with 1 screw was going to be unreliable due to it being able to rotate the cover while it is there, so I added another hole in the pcb!

![adding the additional hole](IMGS/pcb20250804pt4.png)

- I then added that to the CAD and switched this display cover so that it was 3d printable as the polycarbonate version was out of my price range as now I'm working under the 6 point.

![new display cover](IMGS/cad20250805pt2.png)

- Although it wasn't until half a day later in the late evening i realized that these hole locations are not the most great.... So I re aranged them again for the 5th time, also requiring to edit the encoder's pcb and foot print to get this perfect

| ![before](IMGS/cad20250805pt3.png) | ![after!](IMGS/cad20250805pt4.png) |
| :--------------------------------: | :--------------------------------: |

- When updating the pcb however the edge cuts would just not line up no matter what even with cords, so this is where I called it for the night on this.

![I am in pain](IMGS/pcb20250805.png)

#### Power Switch and RST Button

- Due to me having a 3D printer and probably wayyy more time to iterate on this cut out to get this absolutely perfect
- I for now settled on this, as anything else currently, due to the gasket mounting would make this extremely complex and it would have to go up and down with the pcb n' stuff

![switch and button cutout](IMGS/cad20250805pt5.png)

- Eventually when I have the components I want to make something like this as I feel as though it'll be much easier to prodotype this

#### Magsafe and Battery Mount

- I decided to cad out basic models of these components so then they can go in their corresponding cutout for alignment!

![base with additions](IMGS/cad20250804pt4.png)

#### General CAD and Exploded View Experimentation

- I took this time to finally recolor the pcb white, so it matches what it would look like in real life.
- I also started to create a exploded view of the keyboard to show its complexity and to easier explain components, as now there is a really nice visual aid
  - To further help I may use Onshape Render Studio to create nice renders of this keyboard

![exploded view](IMGS/cad20250805pt6.png)

- As for a while I won't be using this keyboard with the encoder as I don't have the funds I also created a version of the keyboard sides without the addons! I will later add them into their own assembly and nessary electronics n stuff!

![partstudio](IMGS/cad20250805pt7.png)

**Time Spent**: 5.5 hours

## August 5th

- Today I started off just by looking through the stuff and adding the oled screen to see if everything would fit correctly.
  - Espically as, I know I am extremely indecisive so I wanted this to also work really well with choc switches if I ever decide to switch to them later.

![with choc testing](IMGS/cad20250805pt8.png)

- When I did this it worked perfectly althought, I might in real life need to trim some of the actual header to make it fit due to the combination of the thumb key placement, the tolderances of copper to outside, causing the daughterboard to be this big, and inability to move the display up
- Although I did move the display .475mm closer, which I didnt before as I had traces running inbetween the pins, additionally I couldnt move it any more up due to the boundaries of the pads

![pad spacing](IMGS/pcb20250805pt2.png)

- But after when looking this over in the CAD the headers would overlap soooo I had to move them back :/

Them headers touching
![headers touching](IMGS/cad20250805pt9.png)

Not Touching/Fixed
![fixed!](IMGS/cad20250805pt10.png)

- Working on the daughterboard it just wouldn't remove the self-intersect wrror on the edge cuts, it as ocurring between two arcs so i tried to add a straight line inbetween, and still no luck, I have a theory that i was related to it being connected to another arc so the combonation of these two was causing a error later down the line
- Hours later I finally solved it, it was a combination of this being really complex, with two arcs interspeting and the entire thing not being complete soo I just connected everything (this was really painful to go back and fourth on the onshape and kicad to figure this out)
- This part is a expansion on yesterday so not that indepth
- Because I basically redid the shape of the daughterboard I updated the acording footprint and their location on the pcb so they were still good with the hole locations for the fpc cable pass through, below is it being unaligned and fixed!

![it being fixed!!!](IMGS/pcb20250805pt3.png)
| ![realigning the hole](IMGS/pcb20250805pt5.png) | ![rearanging the connector](IMGS/pcb20250805pt4.png) | ![it being fixed!!!](IMGS/pcb20250806pt6.png) |
| :---------------------------------------------: | :-------------------------------------------------: | :--------------------------------------------: |

- I also created little indents in the bottom case so my 8.0mmx1.5mm rubber feet can fit snug and are more difficult to remove
- While I was at it I also added a 0.1mm indent for my magsafe just as a visual indicator of where it is

![it being fixed!!!](IMGS/cad20250806.png)

- While looking around the case I found out that some of the fillets were not really lining up between the bottom case and the top case so I decided instead of using the fillet tool that I would just manually do it as I had much more control with the sketch
- thus creating a much better fillet n stuff
- And then when there were places where this wasn't possible I just added a .8 fillet along with a .2 on the insides

![before](IMGS/cad20250806pt2.png)
![it being fixed!!!](IMGS/cad20250806.png)

- Getting me here, the basically complete CAD!

![full cad!](IMGS/cad20250806pt3.png)

ALSO my excuse for getting it so close to the deadline is because of summer school (I am in pain.)
and onshape while updating one of my context's decided to crashout on me :/ but I fixed it pretty quickly resulting in the picture above!

![why](IMGS/cad20250806pt4.png)

**Time Spent**: 6.5 hours

## August 15th: Comin back!

#### Grant and BOM stuff

- I got my project approved for the 10 point! even though I was told to resub as a 6 point due to only being a keyboard, so I messaged my reviewer to confirm, and to see if I can alocate everything to fit under the grant!
- I am also preparing everything to order in the typeractive cart and aliexpress, although when looking it over I saw that the 750mAh battery from typeractive was unable to be shipped to Canada where I live so I'll be prob switching that to a ali alternative, which I'm also confirming with alex (reason why I didn't work on this a day before was because I had a few back to back deadlines on summer school :/ but now I'm free for a dayishhh)
- Over the next day I will update the BOM to match these changes, but if I get reduced back to a 6 pointer I'll revert it!

- I since I'm not getting the batteries anymore from typeractive the shipping is basically $15 so I switchign it so that I'm getting the MX sockets from here instead, I'll also ask tomorrow if this is allowedd with my reviewer

| ![](IMGS/bom20250816.png) | ![](IMGS/bom20250816pt2.png) |
| :-----------------------: | :--------------------------: |

#### PCB

- Here I was kindof annoyed with the over doing of the silkscreen around the MCU so I just got rid of it in the footprint, and I make the font better on the nice!vew footprint
  - But before I order I might change it so that the silkscreen for the pins on the otherside so its more visible for future reference
- I also did some minor trace cleaning up

| ![](IMGS/pcb20250816.png) | ![](IMGS/pcb20250816pt2.png) | ![](IMGS/pcb20250816pt3.png) |
| :-----------------------: | :--------------------------: | :--------------------------: |

**Time Spent**: 1 hours

## August 16th: is this what overthinking feels like

#### In-decision abt PCB

- When I was looking at the battery connector I was a bit conflicted after looking at more boards, and i decided to rotate it 90 degrees since then it would be easier to fit a bigger battery
- I was also considering having it be able to be mounted under the MCU if I ever go with a slim build with the extra pcbs, but I just stuck with it being under, sicne its gonna be really conflicting with the display n stuff, routing wires around that, and if I had any regrets I'll just fix it in the next iteration

![](IMGS/pcb20250817pt2.png)

- Added another hole for the trackpad so it would be stronger which I should've done from the start, and in CAD
  | ![](IMGS/pcb20250817.png) | ![](IMGS/cad20250817.png) |
  | :-----------------------: | :----------------------: |

- I added some silk screen n stuff for the name, revision of this keyboard, date, and my github user in a small empty space on the pcb!
- I also figured out how to change the color in the pcb 3d viewer, so I changed the color to white, and silkscreen to black
- I ALSO ALSO learned about the hatch fill pattern and now my pcb looks a bit cooler!!
- Additionally I just optimized the routing a bit more so it looked a bit nicer

| ![](IMGS/pcb20250817pt3.png) | ![](IMGS/pcb20250817pt4.png) |
| :--------------------------: | :--------------------------: |

#### BOM update (hopefully final)

- I changed my BOM to use some generic aliexpress vendor for the battery, I wanted to keep it high so its like set and forget so I went for a 2000mAh one with 2.0mm jst headers
- And then I rearranged and updated the prices of the stuff on the BOM ready to update my reviewer to look over the changes I made to make sure its goodd!

**Time Spent**: 3 hours

## August 21:

- Summer school recently finished! !
- Started ordering stuff first from aliexpress as those would take the longest to come

![](IMGS/bom20250822.png)

**Time Spent**: .25 hours

## August 22:

#### CAD (prep for better renders and cad practices)

- Found out that I got the magnet thickness wrong and placement so I corrected that and now the rings more towards the center of the keyboard
- I then went hunting for better switches and keycaps to use in the CAD, so I settled on the SA profile keycaps and some nice HD switches, although they do take some rendering time so I might change it back
- I also changed the color of these switches and keycaps to make them match the keyboard by making a copy of them and importing them into another onshape document

![](IMGS/cad20250823.png)

- I also then changed it so that each part of the keyboard is its own assembly so its easier to edit n stuff
- So I seperated the MAIN into top, plate, bottom, and electronics with case parts
- but I still kept the original main since its gonna take a while to transfer the contexts, so I will finish this up in the coming days to make sure its perfect

![](IMGS/cad20250823pt2.png)
![](IMGS/cad20250823pt3.png)
![](IMGS/cad20250823pt4.png)
![](IMGS/cad20250823pt5.png)
![](IMGS/cad20250823pt6.png)

- while doing this I also found some minor issues with the extrusion distances, but I resolved them

**Time Spent**: 2.5 hours

## August 22:

#### BOM

- When I was getting ready to order everything else, something felt wrong about the typeractive and mouser order as they were wayyy to expensive
- As when I was first creating the BOM I was rushing, and when I did more reaserch I found it was WAYYY cheaper to buy from aliexpress, and with enough time I found everything on there
  - As one of the problems was the Mill Max Sockets, but with the power of a reddit post I found them, in addition to the ones for the displays
- Also descovered a cheaper way to ship on jlcpcb, but it takes a few days longer, which I can deal with
- Thus, I removed the typeractive order with alternatives on ali, in addition to adding in the switches and keycaps that I got since it can fit in the grant budget now

![](IMGS/bom20250823.png)

#### PCB

- I moved the FFC and FPC connectors a 1mm down so if the Choc sockets are installed it won't be a pain to install that

![](IMGS/pcb20250823pt3.png)

- I also minorly improved the routing
- AND I got the correct footprint for the RST buttons so they have holes for stability

| Before                    | After                        |
| ------------------------- | ---------------------------- |
| ![](IMGS/pcb20250823.png) | ![](IMGS/pcb20250823pt2.png) |

**Time Spent**: 2.5 hours (so far)
