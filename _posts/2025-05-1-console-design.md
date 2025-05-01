---
title: Console Design
subtitle: A custom lighting controller
layout: post
---

# Console Design
---
## Recap Design Goals
In order of importance:
- Price (under 800 USD)
- Can utilise lights fully (e.g, all the features of the fixture, including effects, gobos, etc.)
- Abstracted (Don't have to think fixture level while performing)
- Easy to use (1. Performing, 2. Connection (e.g, plug and play w/ dmx and art-net, etc.), 3. Programming)
- Good looking (software and hardware)
- Hackable (open source, easy to modify)
- Expandable (fader wing, etc.)

## Software 
I've come up with a few ideas for the software, and I'll go over them here. 

### Modular Synth
Modular synths get a bit of a bad rap, for example, the first image that comes up on google is this abomination:
![Modular Synth](https://img.redbull.com/images/c_crop,x_0,y_0,h_1749,w_2624/c_fill,w_1500,h_1000/q_70,f_auto/redbullcom/2019/01/04/b3fce7b3-a7a5-44a4-bc2f-e616b187f70b/richard-devine-modular-synth)
Which is, safe to say, **not** what I want to go for.

For this system, I'm imagining a modular workspace, based on the raw concept of *Input -> Output*.
In short, you have a number of inputs (faders, buttons, sounds, etc.), and a number of outputs (light properties, e.g intensity, color, etc.). 

In between the inputs and outputs, there are a large number of modules, which can be connected together to create a signal chain. For example, you could have a fader, which is connected to a *Math* module, which is connected to the position x output of a fixture. In addition to inputs such as faders, you can also have *LFO* or *MIDI* inputs, and define constant inputs or information about the fixture (e.g, ordered id, fixture type, location, etc.).

Not only would this allow for a far more abstract way of programming, it also allows for a very hackable system, which could easily support custom modules, and could be expanded to support a number of different input and output types. 

Pros:
- Highly Modular / Reusable
- Good for live performance
- Allows for good visual feedback
- Easy to add new modules

Cons:
- Can be overwhelming for new users
- Visual mess (e.g, cables everywhere)
- Performance issues (say someone makes an infinite loop mid performance :/)
- Mapping to physical outputs (difference between lights, etc.)
- User debugging (How do you debug a signal chain?)
- Representing data types (e.g, number vs color vs fixture, etc. - maybe just only have numbers?)

Another source of inspiration for this is Blender's node editors, which are a great example of a modular system which is easy to use and understand (although maybe not for a beginner).
![Blender Node Editor](https://docs.blender.org/manual/en/latest/_images/interface_controls_nodes_introduction_example.jpg)