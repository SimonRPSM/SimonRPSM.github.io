---
layout: page
title: A Primer on Machine Vision
description: The basic terminology and an introductory methodology
tags: primer
---
## [First Draft - needs a ton of work]

## A brief introduction
I put a computer together recently. One of the many steps of the process is to put the Motherboard in the case and screw it to a number of standoffs that often come mounted on the case.

If the standoffs are mounted on the case, either a person put them there, or a machine screwed them in. For both options, the case is quite likely checked before being shipped to ensure the right number of standoffs have been applied.

Similarly to how a person can add the standoffs, a machine could also check that the standoffs are there.

How could this be done? Some approaches would be to use the fact that a standoff, well, stands off the case. Therefore, a probe could be used to check for object presence by lightly bumping onto all the standoffs. Another option would be to train a machine to do the same thing a person would do - look at it.

This requires taking a camera ( or something like a camera ), acquiring images, analyzing those images, and telling some kind of other manufacturing system (or a person) the result.

Notice that this approach is slightly different than setting up a probe to bump onto the device under test (DUT). This is because we are just taking an image - not directly measuring the DUT, but trying to infer some information from another property. There are a lot of different complexities than on a more "direct" method of measurement, but we'll cross those in time.

Instead of using the camera to check for whether the standoffs are there (checking for presence) you could use it to check whether they have been correctly screwed in. You could also use images to check whether the case has been correctly machined, if it is important that it is the right size, or to check for the quality of the surface finish. Each one of these has lightly different approaches and requirements, sometimes at odds with each other.

## I can totally see it in that picture, what's the problem?
When setting up a system to acquire images for a machine to inspect, we will need to understand three main things.
1. Images that are aesthetically pleasing do not necessarily make for good images to process.
2. Your brain does a whole lot of work to understand an image that we just take for granted.
3. The information needs to be in the image in the first place. There's a limit to how much software you can throw at an image to get further information out of it.

## A basic methodology
Great, you still want to set up a machine vision system. Where do you start?

I tend to work from the object to be measured and towards the machine, so let's start at the DUT with a different example. Let's say you are manufacturing cups (because its the closest object to me right now).

### 1. Understand what you actually are trying to measure
Similar to software testing, it is not enough to just say that "the cup needs to be good/ fine/ pretty/ etc". You need to have specific things that you want to measure, such as the width of the base and what is acceptable. Some things can be slightly harder to quantify such as ensuring that the base is circular, but for those there are specific geometric measurements such as the Heywood Circularity Factor.

### 2. Understand how accurately and precisely you need to measure it
If you are measuring an electric signal then this would depend on values such as the resolution of the Data Acquisition System and its accuracy. Here it will correlate to the resolution of the sensor (amongst other specifications) as well as the physical layout.

For example, if you are trying to measure the width of the base, you may want to measure it +/- some number of mms.

### 3. Set up the physical layout
Understanding the layout will give you two main important pieces of information: the working distance and the ambient light.

The working distance is generally defined as the distance between the vision system and the DUT. It is with knowledge of the working distance (and smallest detail you want to find) that you can calculate the necessary lens (resolution and focal length) and camera sensor.

The necessity of being able to control the ambient light cannot be overestimated. I like to describe ambient light as analogous to noise on an electrical cable. In the same way that you would not put your thermocouple wiring, unshielded, on top of a motor drive, trying to set up any optical measurement without controlling (or at least understanding ambient light) will yield unpredictable results at best. You can try to filter it out if it does not directly clash with your measurement (the same way that you can filter out 60hz noise from something connected to the wall), but that is not always the case. Checking if an LED is on or off in direct sunlight can be difficult.

### 4. Get to calculating
This is where a lot of the work goes. First, calculate the necessary resolution of the sensor making an assumption about your area of interest (the area that will be in the image and that contains your DUT). Second, look at lenses that would give you the right area of interest to get the resolution you need. This may include looking at MTF charts to figure out the maximum resolution a lens can resolve. Three, look at what cameras contain the specifications of the sensor you need (in resolution, framerate and accuracy). Fourth, ensure that the lens you picked will work with your sensor. For example, some sensors are particularly large and the lens itself needs to be large enough not to *window* out pieces of the image.

### 5. Now you can actually set up the rest of the system
This is where you start considering the bus of the camera, as well as latency, triggering capabilities, control options, etc.

### 6. Ok, no you can start thinking about the software
That's not quite right - you want to be considering this throughout the process, but a lot of things will start to crystalize as you go through the decision on the system components.

### 7. Having fun with integration
And then you can start putting it all together.

## All of this sounds pretty painful and generic
There are a lot of resources on each step, as well as pieces of software that you can leverage.

I will be trying to compile a series of tools and articles on each piece to help out.

\- Simon Perez Santa Maria
