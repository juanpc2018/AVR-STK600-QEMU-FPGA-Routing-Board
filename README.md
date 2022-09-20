## AVR STK600 QEMU FPGA Routing Board idea

i iknow there is a Software that emulates AVR, 
loads the compiled image file from Atmel Studio 7 / MPLAB Studio or Arduino IDE,
and emulates wires, resistors, leds, switches, etc...
cannot remember the name of that software.
BUT...
100% virtual defeats the purpose of AVR.
its like a contradiction, a paradox. <>

it would be nice if AVR emulator can have Real I/o
using Parallel port pcie cards,
or Serial ports i/o,
also for emulating Analog I/o a soundcard driver,
so emulated AVR interact with real Protoboard, wires, Leds, Switches.
or a Custom i/o pcie/usb board with exact same impedances, frequencies, speeds.
too crazy?
cant get my head around this...
the proper way to develop AVR is using the STK600 developer board, "a Super Arduino 2560",
has a stable, configurable PLL or DDS Clock Generator,
inputs for standard XO leads, different ways to program the IC, jtag, i2c, usb, etc...
all i/o pins,
basic switches & leds.
a PCIe board that connects directly to STK600 ?
The idea of STK600 is able to change/swap differnt AVR IC models,
with the same circuit connected, to find the best AVR IC for that code.
Arduino board is fixed, cannot change IC, needs to rewire the whole circuit to change form 328 to 2560,
STK600 can change IC without affecting the circuit connected.
AVR emulator + PCIe to STK600 board eliminates the Plug n Remove, Plug n Remove.
Basically thats the problem & strengh of STK600,
some Avr IC boards do Not connect directly, need a Routing board in-between like a sandwitch, and some rounting boards have lower frequency, crosstalk interferences.
because the routing is too complex.
also PCIe to QFTP48 32/64/68 male socket.
for the next step in development,
when test board is printed by pcbway or the other.
to Test the pcb circuit board without soldering the Avr ic.
practical use, time saving, money saving without affecting workflow/development.
connected to the development process, a chain link, Not a separated, isolated ecosystem.


This project can be divided in several ways...

using real AVR or Not.

a way to implement this could be:

A) large PCIe Board or PCB rack mount chasis,
that has all AVR ICs or QEMU
+ large & fast FPGA to handle all the i/o routing, FIFO buffering.

B) an Universal programable routing board for STK600,
with an FPGA to handle all the routing & FIFO.
maybe configurable via dip switches, 

Active Routing instead of Passive Routing.

C) instead of FPGA, HCMOS analog switches.

instead of swapping the routing board and IC board, just the IC board, 
and dip switch the Routing board.

D) using mini relays.


Mini Relays = $$$, more energy consumption, wears, but will guarantee signal integrity.
CMOS Analog Switches = cheaper, noiseless, low power, does Not wear as fast,
but the problem is that AVR has 100 i/o pins.
Highfrequency loss vs. Ron war... would require dual path approach with very low ROn path, and very low Capacitance path in parallel.
double path would require double the components, double the routing, perfect phase alginment of every path, because high speed digital signals require phase alignment.

Just ideas... 

https://www.analog.com/en/analog-dialogue/articles/wideband-cmos-switches.html

https://www.maximintegrated.com/en/design/technical-documents/app-notes/5/5299.html

https://www.analog.com/en/technical-articles/cmos-switches-offer-high-performance-in-low-power-wideband-applications.html


https://
g i t l a b
.com/qemu-project/qemu/-/issues/1181
