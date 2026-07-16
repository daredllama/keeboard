# Keyboard Build Journal

## Entry 1 — Figuring out hardware and layout
**Date: 7/11/2026**

Started planning out the layout for the keyboard. I really didn't want a bulky keybaord,
but at the same time, I wanted to maintain most of the function that I would have on 
a conventional laptop. So, I settled with a 75% layout, I used the reference picture below.

<img width="2820" height="1216" alt="image" src="https://github.com/user-attachments/assets/cf011115-c34f-4406-9dbf-3eaefff0556b" />

## Entry 2 — Deciding how to light this thing up
**Date: 7/12/2026**

Went back and forth between per-key RGB, underglow, and a "backlit"
middle-ground option. Landed on full backlit — one LED under every single
switch (~79-84 depending on final key count). I realized the switches
I've got already have that clear/translucent housing built for exactly this. I also realized this was gonna be a tedious task.

<img width="1072" height="868" alt="Screenshot 2026-07-12 103644" src="https://github.com/user-attachments/assets/ce4a9b97-b546-4f9b-9801-ac147b74afd2" />

## Entry 3 — Building the LED chain in the schematic
**Date: 7/12/2026**

Got the SK6812 schematic block down: VDD/GND, a 100nF decoupling cap per
LED, DIN/DOUT chained through. Added a ~500Ω resistor on just the first
LED's DIN (protects against voltage spikes, only needed once at the start
of the chain). Copy-pasted that pattern like 79 times.

<img width="1984" height="508" alt="Screenshot 2026-07-12 105447" src="https://github.com/user-attachments/assets/d239e748-8b3a-4eed-8764-6a8a2b2dc997" />


## Entry 4 — Rotary encoder + OLED wiring
**Date: 7/13/2026**

Wired up the EC11 encoder (A/B/C for rotation, S1/S2 for the click).
Spent a while figuring out OLED options — I wanted I looong screen put apparently
4 pin OLEDs don't come in 256x32, so I had to settle for a 128x64 display, which gave
a me a bit more surface area.

<img width="1914" height="1436" alt="Screenshot 2026-07-12 114551" src="https://github.com/user-attachments/assets/b9ca4746-b45f-4dbc-a704-5cd8d2f9a81a" />


## Entry 5 — Locking in the matrix and pin map
**Date: 7/13/2026**

Finalized the switch matrix at 15 columns × 6 rows — 79 switch positions
total, including the encoder's click. Assigned every single GPIO on the
Pico (all 26, no spares left) across the matrix, encoder, LED, and OLED.
Also worked out all the stab sizes and key widths based on the F75 layout
I'm copying.

<img width="882" height="960" alt="Screenshot 2026-07-12 122729" src="https://github.com/user-attachments/assets/2aeb5a57-0ac4-441e-b19c-583192a04c88" />


## Entry 6 — Where do I put LEDs?
**Date: 7/14/2026**

Originally when I made my previous hackpad, I put the LEDS in between the swithes,
which I soon figured out was not viable for this build.
So I solved it by going reverse-mount (LED on the back of the board, shining
through a cutout). Little did I know how tedious wiring all the caps and LEDS was going to be. I quite litereally spent the ENTIRE
day wiring this. Sigh.

<img width="1272" height="1292" alt="Screenshot 2026-07-12 221359" src="https://github.com/user-attachments/assets/5a7916c9-fc81-495a-a6f4-c34d461911a5" />


## Entry 7 — Plate and case stuff
**Date: 7/14/2026**

Decided to do some CAD (I am most comfortable w/ this). Learned
about the different keyboard mounting styles (tray, top, bottom,
sandwich, gasket, etc.) and went with sandwich mount — simple to design.
I made it very cool and sleek looking.

<img width="1330" height="626" alt="Screenshot 2026-07-15 225540" src="https://github.com/user-attachments/assets/3ad53654-7a8f-4b94-bd76-ed3eae14e9b9" />


## Entry 8 — Getting the firmware going (RMK)
**Date: 7/15/2026**

Decided to do this one in RMK instead of QMK since I've already done a QMK
board before (ZePad) and wanted to try something new. Since I'm kinda unfamiliar with this,
I use a lot of placeholders for things I will come to later. Also wrote in the other files.

## Entry 9 — Getting ready for assembly
**Date: 7/15/2026**

Finalized all of the rest of the files which included finding the prices for 
the BOM and also writing the README and JOURNAL.

Total Hours: prolly 20ish.
