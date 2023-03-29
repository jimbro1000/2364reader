# 2364 Masked Rom Adapter for EPROM programmer

You can't re-program a masked rom but you can still
read it. This adapts the pin positions of old 2364
masked roms to use the same pin positions as a 27C64
so that a regular EPROM programmer can easily read
the contents of the masked ROM

## Assembly

Fit two rows of pins to the bottom of the board in
the longer rows (14 pins each)

Trim the pin ends on the top of the board to allow
clean fitting of a socket

Fit a 24 pin socket on the top of the board

Fit a row of 3 pins to the board at JP1

Use a jumper on JP1 on the 8k side

## Usage

Move the jumper to the 8k side of JP1

Fit your 2364 masked rom in the socket

Place the board and rom in your eprom reader/programmer

Set the programmer to use a 27C64

Read the rom as normal

### Reading a 2332 rom

Move the jumper to the 4k side of the board

Fit your 2332 masked rom in the socket

Proceed as normal for a 2364

The image read from the rom will show as an 8k image, 
but the image repeats from the first 4k

