-- Wovmoh --
Wovmoh is a custom lighting controller designed for live performance, focusing on modularity, hackability, and ease of use. The project aims to create a system akin to a modular synthesizer: where users connect various inputs (like faders and buttons) to outputs (like light intensity and color) through a series of nodes. This approach allows for a system which not only emphasizes real time performative lighting over cue based lighting consoles, but also provides a more intuitive and flexible way to control lighting fixtures.

-- The Basics --
In a typical Wovmoh project, a user starts by setting up a number of fixtures (lights), and their respective DMX addresses. The user then creates a patch.
A patch is a collection of nodes, which represent the actual signal chain, from input to output. 
Patches are built in a graphical interface, similar to blender's node editor, and are compiled from C++ to a mix of CPU- and GPU-side code, depending on the type of node.
Each node has a number of inputs and outputs, which can be connected to other nodes. 
Example Patch Flow:
Fader (input) -> Math (node) -> Color Gradient (node) -> Color (output)

Another advantage of the node based system, is its extensibility. Anyone can easily create new nodes, and these can be shared with other users.

-- The Hardware --
The console itself is designed to be run standalone, with a Raspberry Pi 5 as the brain, and a touchscreen as the main interface. 

Various inputs and outputs are included with the console:
- Faders
- Buttons
- Rotary encoders
- X-Y Pad
- Ultrasonic distance sensor

All of these inputs can be used as an input in any patch, and this allows for a far more performative way to control lights, as opposed to the constant diving into software on regular consoles.

The console will also support MIDI, DMX, MTC and audio input, which allows for even more flexibility in control.

In terms of outputs, the console will likely just support DMX and Art-Net, but this can easily be expanded in the future to include other protocols, such as sACN.

-- Rough Cost Breakdown --
ELECTRONICS
- 1x Raspberry Pi 5 16GB: $120
- 1x NVME SSD: $50
- 1x 7.5" Touchscreen: $250
- 20x Faders: $80
- 30x Buttons: $50
- 3x Rotary Encoders: $30
- 2x X-Y Pads: $100
- 1x Ultrasonic Sensor: $10
- 1x Keypad: $20
- 2x RP2040: $10
- DMX Interface (Transceiver, Connectors): $40
- Ports + Connectors: $50
- PSU: $40
- PCB Fabrication / Prototyping: $400
Subtotal: $1250
- 3D Printed Case: $100
- Corner Guards: $15
- Aluminum back panel: $80
- Aluminum front panel: $120
Subtotal: $315 * 1.5 (prototyping + margin) 
= $472.5
Total: $1722.5

Only smt, pcba, cnc, and 3dp are covered, so remaining costs:
- Pi 5: $120
- SSD: $50
- Touchscreen: $250
- X-Y Pads: $100
- Ports + Connectors: $50
- PSU: $40
- Corner Guards: $15
Subtotal: $625
Stuff I already have:
- Pi 5
- SSD
- PSU
- Corner Guards
Actual Subtotal: $625 - $120 - $50 - $40 - $15 = $400

To nzd:
- $400 * 1.5 = $600