---
layout: post
title:  "Scope Creep : A worked Example"
categories: intro
---
(In work)

# Say you are still the same test engineer
On a previous post I brought up the idea of learning what you need to do your job. I also then proceeded to mention that if you only make throw-away code you can be pretty safe from needing to figure out some of the future intricacies of software design. Let us chat about why code is never as throw-away as we would initially imagine.

On the same example as before, let's imagine that you need to use some tools to measure temperatures in your manufacturing line. You buy some kind of USB Data Acquisition (DAQ) device and get to work. Then you write some code to do the following - let's work under the assumption that you can't use some kind of canned software to do this for now:

A. Begin communicating with the USB DAQ device.
B. Tell the DAQ device what kind of thing you want it to do - Acquire temperatures at a rate of 1 Hz.
C. Do this for a minute, then stop.
D. Put your temperatures in a file that some spreadsheet software can open.

Everything works great,  you get your data and go home.

Issues can crop up when you need to do a similar task again, but that is not quite the same.

Say, instead of needing to acquire temperatures with a USB DAQ device you now need to use an Ethernet based device. Everything is almost the same, assuming they use the same driver, you keep points B-D but need to change point A to being:

A. Begin communicating with the DAQ Device at some IP set up in a file

You noticed that you needed to use an IP adress and those change, so you figured out that you could put the IP on a file to spare you from needing to rewrite your code if the IP changes.

Awesome, you get your data.

Then a month later you need to figure out whether the line is vibrating. As luck would have it, that manufacturer also sells an Ethernet based device to acquire vibration data. This time you change part B of your code to acquire vibrations:

B. Tell the DAQ device what kind of thing you want it to do - Acquire vibration data at a rate of 50000 Hz

Awesome, you get your data again - but the information that you get seems wonky. The values that you see in your spreadsheets and graphs seem incorrect. This prompts you to decide to acquire data faster, and so you turn back to getting another piece of hardare. You are still quite lucky and that company makes some USB based hardware that can acquire even faster, at 100000 Hz.

So now you need to change lines A and B.

# This is a silly example

But it is one that I have seen a lot of times. You begin to work on writing some software for a quick test but only think about the current test at hand.

Where things get interesting is trying to make sure that your code can do what you need it to do today, but that it will be able to do what you need it to do tomorrow *for the same project* because that project's scope will inevitably change.

Even if you are willing to disregard all code made previously for each single project, the project's needs may change forcing you to need to change your software to accomplish whatever it is you are trying to do.

# So what should we do for this?

First, let's think about what needs to happen to get data on an abstract level - without discussing the implementation details.

A. Find and start communicating with a device.
B. Configure the device.
C. Get data from the device.
D. Do something with that data.

Then, your software can figure out what it needs to do - for example, from a configuration document. Let's work our way down one of these point.

A. Find and start communicating with a device.
 1. Call Driver X.
   1. Use the functions for USB
   2. Use the functions for Ethernet
     1. Find the device on the network
     2. Tell the device that it needs to ignore commands from other computers for a bit
 2. Call Driver Y.
   1. Use functions for USB

At a very simplified level, this could be kept within a configuration document in some form. It could be as simple as: A121

This is not necessarily a good starting point for an application, but a thought excercise on what vectors of your application can change. This is also an excercise to understand the importance of software requirements which everyone agrees are important, but often are ignored.

-SRPSM
