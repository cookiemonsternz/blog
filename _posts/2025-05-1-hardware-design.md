---
title: Hardware Design
subtitle: A custom lighting controller
layout: post
---

# Hardware Design
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

## Hardware
I'd like to start by looking at some other consoles, and seeing what they do with their hardware.

---

![grandMA3 Light](https://xom.malighting.com/xom-rest/assets/22ea1a65-8443-46b1-87a1-e075ba751ce0/preview?mimeType=image%2Fpng&width=1170&height=700)

---

![Full Boar 4](http://www.hog4.de/wp-content/themes/wholehog4/images/fullboar4consolefoto.jpg)

---

![Onyx nx4](https://obsidiancontrol.com/media/catalog/product/cache/c12c4bb72a9f8e06484754c446869e58/n/x/nx4-lt-43887.png)

---

![Chamsys MQ80](https://th.bing.com/th/id/OIP.qSnLBREtCPJN4lUM4m5cGgHaE8?rs=1&pid=ImgDetMain)

---

![Chamsys QuickQ 30](https://chamsyslighting.com/wp-content/uploads/2024/03/QuickQ-20-RIGHT.png)

---

Notice anything similar?
Every single console has:
- Faders
- Buttons
- Rotary encoders
- A Keypad (excluding the quick q 30, which has a touchscreen keypad)
- At least one touchscreen

Honestly, these are all incredible sensible design choices, and mostly, I'd like to stick to them.

---

### My Console

---

#### Faders

Faders are just one of the most amazing things ever. They're incredibly intuitive, especially for intensity, speeds, and mixing between things. They're also easy to use as an input method, and tactile, which is great for live performance.

#### Buttons

I'm torn on buttons. On one hand, they're great for one shots and triggering things, but they can also become a bit overwhelming. For example, the grandMA3 has a total of 106 assignable buttons (I think), which is an absolute crapton. Remembering what button does what is a pain, especially when you have multiple pages of buttons. 
I think the best solution is to have a few buttons, but not too many. A good way to do it is probably a bank of around ten buttons, and a button under each fader.

#### Rotary Encoders

To be honest, I only really ever use rotary encoders for pan and tilt, but they are a great way to do that, far better than faders or (unfortunately) x-y pads. They can be good for color, but a color picker is far better. 
Overall, I think maybe 3 rotary encoders is a good number, which would likely be used for tweaking pan, tilt, and something else (maybe intensity?).

Unlike other consoles, where encoders are used in programming to set values, they would again be used more for live performance, but this is something I need to think about more, for example, what happens when you want to move an individual fixture to focus on something / someone? How does this work in my software?

#### Keypad

This is again influenced by how much I want the editing of a show to be done on the console vs a computer. If the console is just for performance, then a keypad is almost irrelevant, but if it's also used for programming, then its a must. 

I think the main time when you're programming live is when you're setting up a show, and need to just adjust values, like position presets, etc. This is another flaw in my modular synth idea, as it doesn't really allow for this (or position presets in general actually :/).

#### Touchscreen

Yep, definitely. Useful for live performance, and great for programming. Can be used for a lot of things, including a color picker, and a visual representation of the fixtures. Also can be available for some live programming, but needs to be very responsive, and not laggy at all.

#### X-Y Pad

I absolutely want some x-y pads. They're amazing for just mucking around on, and especially with the modular synth idea, they could be used for a lot of things. You could interpolate between four different position presets, etc.

#### Weird Stuff

- Ultrasonic distance sensor (think theremin)
- Velocity sensitive buttons / pads
- Laser beam (see laser harp)
- Capacitive touch pad, but for vibrato (roli seaboard vibrato-esque) - would need like 200hz tho

---

## Next Steps

Next time, I want to look more of the technical software side, and then look at the hardware in more detail as well. Following that, I'll submit the project to OSHW Stars, and then start working on the hardware.