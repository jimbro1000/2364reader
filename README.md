# 2364 Masked Rom Adapter for EPROM programmer

You can't re-program a masked rom but you can still
read it. This adapts the pin positions of old 2364
masked roms to use the same pin positions as a 27C64
so that a regular EPROM programmer can easily read
the contents of the masked ROM.

The 2364 and pin compatible masked roms were common in
the 80s era of 8-bit home computers (Commodore VIC-20,
Commodore 64, Tandy CoCos, etc). Before attempting to
use this adapter make sure that the rom **is** pin
compatible. If incompatible, at best you will create
a corrupted ROM image, at worst you could damage the
ROM. Most programmers will protect themselves from
damage but do not assume this is the case.

## Why do you need it?

While masked roms are generally robust they do fail,
this adapter provides a simple way to read the rom
image using an eprom programmer. In practical terms
this is a way to verify a real rom against a known
rom image. Or maybe to generate a new rom image where
one doesn't exist.

Some modern recreations of old 8-bit computers have
opted to use 27/28C64s instead of the original masked
roms in the name of avoiding unobtainable parts. This
adapter can also be used to fit original roms. If a
larger capacity eprom is used (eg. 27C256) this 
adapater will not really help.

## BOM

| Position | Component                                | Quantity |
|:---------|:-----------------------------------------|:--------:|
| U1       | 24 pin dip socket 15mm wide              | 1        |
| U2       | 1x14 pin 2.54mm pitch male header        | 2        |
| JP1      | 1x3 pin 2.54mm pitch male header         | 1        |
| JP1      | 2.54mm jumper                            | 1        |

note: it is highly recommended to use round (turned) pin headers for
U2 instead of the bulkier square pin versions as these are kinder to
sockets

## Assembly

1. Fit two rows of pins to the bottom of the board in
the longer rows (14 pins each)

2. Trim the pin ends on the top of the board to allow
clean fitting of a socket

3. Fit a 24 pin socket on the top of the board

4. Fit a row of 3 pins to the board at JP1

5. Use a jumper on JP1 on the 8k side

## Usage

1. Move the jumper to the 8k side of JP1

2. Fit your 2364 masked rom in the socket

3. Place the board and rom in your eprom reader/programmer

4. Set the programmer to use a 27C64

5. Read the rom as normal

### Reading a 2332 rom (4K bytes/32K bits)

While I intended the jumper to gracefully handle A12
addressing when reading a 2332 but in the current
design it gives unexpected results. Until fixed the
steps for reading a 2332 are the same as for the 8K 2364. 
The end result is that the upper 4K are read as $FF
instead of repeating the image.

A change to the board has been made to circumvent the 
problem but is not tested.

#### Ignore until fixed:

1. Move the jumper to the 4k side of the board

2. Fit your 2332 masked rom in the socket

3. Proceed as normal for a 2364 from step 3

Note: The image read from the rom will show as an 8k image, 
but the image repeats after the first 4k. Trim the image at
the 4k mark to convert the result into the correct 4k size.
