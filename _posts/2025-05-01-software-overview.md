---
title: Software Overview
subtitle: A custom lighting controller
layout: post
---

# Software Overview

---

## Abstraction Layer

We need a way to abstract the physical layer from the software layer. This entails fixture personality (profiles, basically a list of all the features of the fixture and their DMX addresses), patching (mapping the fixture to a DMX address), and actually sending the DMX data to the fixture.

This is relatively simple, and shouldn't be literal hell to implement. Just need to have a way to send data from a 'Light' object to a 'Fixture' object, with light being the abstracted version of the fixture, e.g, light has color and intensity, and fixture has DMX addressing and fixture type, etc. 

## The software (Modular Synth)

- Most basic object is a Light. This is the actual representation of the fixture.

- Lights have a number of properties, such as color, intensity, position, etc. These properties are mapped to the actual DMX addresses of the fixture.

- Each light also has a *Patch* (being the node graph, not the dmx patch). 

- A *Patch* is a collection of linked *Nodes*, which represent the actual signal chain.

- Each *Node* has a number of inputs and outputs, which can be connected to other nodes.

- There are 4 high level data types:
    - Number 
    - Color 
    - Boolean 
    - Vector (2d, 3d, 4d, etc. probs 2d or 3d for now)

- Each type tries to automatically convert whenever possible, e.g, color to number, number to color, etc.

- Inputs can be: 
    - ### **--HARDWARE--**
    - Fader (number)
    - Button (boolean)
    - Encoder (number)
    - XY Pad (vector)
    - Ultrasonic Sensor (number)
    - ### **--SOFTWARE--**
    - LFO (number)
    - MIDI (number)
    - Audio (number)
    - DMX (number)
    - BPM (boolean)

- Outputs can be:
    - Intensity (number)
    - Color (color)
    - Position (vector)
    - Strobe (number)
    - Shutter (number)
    - Gobo (number)
    - Color Wheel (number)
    - Zoom (number)
    - Focus (number)
    - Iris (number)
    - Frost (number)
    - Prism (number)
    - Etc. etc. other utils

- Values should show with inferred units when possible, e.g, color should show as a color, and strobe rate should show as hz

- Software should instantly update when a *Patch* is changed

- There should be a way to get properties of the *Light* the *Patch* is attached to

- Nodes should display a compact visual preview of their current output — e.g., a number as a dial, color as a swatch, vector as X/Y graph — to aid debugging and patch understanding.

- Subsections of *Patches* can be saved as *Nodes*

- *Patches* should be serializable to be saved and loaded

- *Nodes* with state (like timers, counters, or sequencers) must handle graph re-evaluation, rewiring, and reloads without glitching or resetting unexpectedly.

- Cycles and excessive recursion should be detected and clamped to prevent infinite loops, above all else, not interrupting the show.

- A main *Patch* should exist, which by default passes all inputs to all outputs, and also allows for the setting of *Uniforms*.

- *Uniforms* are a way to pass information from the main *Patch* to all other *Patches*

- *Uniforms* can also contain arrays of data // Potential problem, what if user wants to manipulate array and then use it in a *Patch*?

- *Uniforms* can not be changed in any *Patch* other than the main *Patch*

- Non critical errors should be logged to console, and logical errors in a *Patch* should be shown in the ui, but not stop execution.

- Critical errors should prevent compilation of the *Patch* and show an error message in the ui, and revert to the last working state.

- *Nodes* should be defined via a json file, which contains the inputs and outputs, other metadata, and the actual code for the *Node*.

- *Nodes* should be able to be user defined

- *Fixtures* should be able to use GDTF files

- Above all else, light output should not be interrupted.

## UI 
- Should be able to have multiple *Patches* open at once

