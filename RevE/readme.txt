Guide for BLE Blaster Rev E shield

Please see the BLE Blaster Rev E Guide PDF file to see where each of the following features lies on the board.

SW Switch:

The SW Switch, which was a simple push button in the schematic and BOM, has been replaced on the boards with a slide switch. When the switch is pushed to the right (towards the BLE module) the module will be awake. When it is pushed to the left (away from the BLE module) it will be asleep.

High Powered FETs:

There are four high power FETs on the left hand side of the board. They take power from the FET Power Input screw terminals, and switch the positive power input to GND. Eaceh of the four output screw terminal blocks has to output terminals - a positive (unswiched) and a return (switched). The positive terminals are all connected together, and are also connected to the FET Power Input + input terminal. The terminals labeled 5, 6, 9, and 10 (on the silk screen) are switched to GND by the FETs, and are controlled by Arduino digital pins with the number given by the label. All of these pins are hardware PWM outputs on both Arduinos and chipKITs, so you can use this to do LED dimming or motor speed control, etc. There are through hole spots for BEMF diodes (D9, D9, D10 and D11) to be soldered in, but they are not populated by default. They would be used if any of the FET outputs had an inductive load like a relay or motor attached. 

Prototyping Area:

There are a few holes for prototyping circuits. There are some GND, 5V (if available), and 3.3V holes allong the bottom edge of the prototyping area.

3.3V Power LED (Green):

When lit, this LED indicates the presense of 3.3V on the board.

Connection LED (Red):

This LED is controlled by the BLE module, and has different meanings depending on the mode the BLE module is in. See BLE module datasheet for more information.

UART Connector:

This connector contains GND, 3.3V, TX, RX, CTS and RTS, and is pinned out for the MCP2200 module. It allows a direction connection to the BLE module should you want to communicate with it directly from a PC rather than going through a chipKIT or Arduino board.

Wakeup Button, Reset Button:

These are push buttons used by the BLE module. See the BLE module datasheet for more information.

System Mode Selection Jumpers:

This is a block of 9 pins. The left hand colum of 3 pins is all connected to +3.3V, the right hand column to GND, and the center column is connected to the P2_0, P2_4, and EAN pins of the BLE module. You would place jumpers across these pins to set the logic levels of thes three BLE module pins on boot to enter special firmware programming modes, for example. Note that no jumpers need to be connected to run normally, as the BLE module handles pull ups/pull downs appropriately for these three I/O pins.

Reset Enable Jumper:

Normally this jumper is not connected. But if you want to control the BLE module's reset pin from an Arduino/chipKIT pin (A5) then connect this jumper.

Voltage Select Jjumper:

This jumper needs to be connected. The left two pins should be shorted together if a 3.3V Arduino/chipKIT board is used, and the right to pins should be shorted if a 5V board is used. This simply sets the high-side voltage level of the level converters for TX, RX, P1_5 and P0_4.

I/O Enable Jumpers:

This is a block of 6 pairs of pins. Each of the 6 pins on the left (8, SDA, SCL, 7, 4, 13) can be shorted across to the pins on the right (WKUP, P1_3, P1_2, P0_4, P1_5 and SW_BTN) if so desired. The left hand column are Arduino/chipKIT pin names, and the right hand column are BLE module pin names. This jumper block allows any of the available BLE module pins to be connected to Arduino/chipKIT pins. None of these jumpers need to be connected by default - they are all optional.

RX Jumpers/TX Jumpers:

Each of these is a block of 4 sets of pins. On the left of each block are four different Arduino/chipKIT digital I/O pins, and the right hand column is all connected together, and goes to either the RX or TX level shifters and then on to the BLE module. These blocks are where you select which UART (or set of pins on the Arduino/chipKIT interface) the BLE modules connects to. For example, if you want the BLE module to connect to the standard Arduino hardware serial on pins 0 and 1, then you would put shorting jumpers across the bottom two pins of each of the blocks. You can move the jumpers up or down the blocks to select different TX or RX connections from the BLE module to the Arduino/chipKIT board. This allows for maximum flexibility when using the BLE Blaster shield, as you can avoid using UARTs that are already used for other purposes on your project.