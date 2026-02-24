---
title: Software First Steps
subtitle: A custom lighting controller
layout: post
---

# Software First Steps
I have been working on the very base software of the lighting controller, and have made some decent progress!

## Framework
After much deliberation, I eventually settled on using Qt for the software development. I'm using a mix of c++ and Qt Quick (qml) for the UI and backend respectively.
I originally planned on using Kivy, but I was worried about performance and rigidity of data types in python. I spent three or four days struggling with Qt, and ultimately got nowhere, but today, I decided to ignore Qt for now, and just focus on the backend. I've implemented the basics of the node graph, including:
- Input and output pins
- Nodes
- Connections
- Evaluation (only in order of creation for now, later will be in order of connections)
- Node types (number, color, boolean, vector)

I've even made a minimal example, consisting of a two value nodes into an add node. 

## The Code


- ### DataValue
Starting from the top, the first thing I implemented was the basic data types. I decided to go with Number, Bool, Color, and Vector (3d only, but can be used as 2d).
These are all pretty simple, only a few operator overloads. All types are stored as a variant, so they are utilized through the DataValue class, which has some other shared functions.

- ### Pin
The base pin class only stores the pin id, name, and data type, as well as a pointer to the parent node. The base pin class is not used directly, but inherited by the InputPin and OutputPin classes.
Input pins only expose a few more members, such as a couple functions regarding connections (isConnected, getConnectedPin, getConnectedPinValue, connect, disconnect), and also stores the currently connected output pin.
Output pins are the same but also store a value, and provide methods for setting and getting that value. Alongside this, they can be connected to multiple input pins, which adds a bit more complexity.
- ### Node
