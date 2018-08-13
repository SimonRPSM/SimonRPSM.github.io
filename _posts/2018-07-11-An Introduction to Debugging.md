---
layout: post
title:  "An Introduction to Debugging"
categories: intro
description: Everything is broken.
---

(in work)

# Debugging is often taught incidentally
When most people learn to program or to work with software, it is pretty common that they learn a few tips and tricks on how to Debug. You will write some software, it will not work, and then you start looking for what is wrong until it works - rinse, wash, repeat. Through introductory programming courses, you often learn about intricacies of the language or IDE that you are using, but rarely is there much time given to how to Debug.

I learnt a lot about the topic when I started doing Applications Engineering and directly supported our customers, mostly through trial and error. Being mentored by some more senior engineers helped quite a bit, but it was always a bit puzzling when they could pinpoint problems just a few questions. It was not necessarily that they had run into the same thing, but simply that, like anything else, debugging is something you get good at.

# When do you need to Debug?
"Well, when things don't work" is not a correct answer. Before beggining to debug your software or system, you really need to think about what the system is supposed to do. And write it down. No exceptions. This is because if you cannot state in words what your system is supposed to do, you probably have a very hazy definition of what "it works" means. Pinpointing what your system should do by describing its requirements is paramount to figuring out what is broken, regardless of whether your code is acting weird, or your machine is constantly running into its mechanical limit switches.

# How do you start?
Once you have defined what your system needs to do, then you can start trying to figure out whether or not it is doing that very thing. I will leave aside comments of design for this discussion to focus on the troubleshooting itself. However, software that is well designed and tested is much easier to debug.

# What kind of bug is it?
There are two main types of problems. Repeatable problems, and non-repeatable problems. We will focus on the first group first.

First, figure out what the trigger is for the problem you are seeing.

Second, treat it as a searching algorithm. Once you know what the input to your system is, and what the output should be, then you can follow the path of that input all the way through the different glue-layers until the output.

A good analogy to this is dye testing for plumbing. In dye testing, a specific bright-green die is injected into a plumbing system somewhere - then you look for anywhere that you can see this dye. In software, you can do something similar by taking the time to trace the input to your system through every unit until it's output. This can be done by elegant IDEs or debuggers, but do not discount the humble text file or writing to Syslog. Have each module or unit log to a text file what data it is receiving and its output. Then you may trace the file or Syslog, which often gives you insight onto what is going on within your system, even if you cannot directly peak into it's execution.

While it seems pretty painful to do, it is not dissimilar from instrumenting a physical system. Taking the time to do this slowly and thoughtfully when problems arise (if you could not do it before for reasons xyz) will generally save time in the long run - I have almost never come up ahead when I just tried to wing it.

![Diagram](https://raw.githubusercontent.com/SimonRPSM/SimonRPSM.github.io/master/_posts/Diagrams/DebuggingSampleSystem.png)

Using the above system as an example, you may realize that you are getting garbage data in a User Interface at some point. Most of the time the first reaction is to check out the logs - but what, exactly does that tell us?

If the logs are good, then we can look at the path the data took until the Log and where it branches off towards the user interface. We can pretty safely assume that there is no problem before the Analysis Process, and that the error happens in the communication between the Analysis and the SCADA system, the SCADA Process itself, the communication between the SCADA Process and the User Interface Process, or in multiple of these.

It the logs show us the incorrect data we expect, then we can assume that the problem happens before the analysis. If you have no other way to peak into the system, you could start by checking the physical connections or checking with handheld instruments whether the sensors give the expected data. Then, as possible, continue splitting the problem in half until you hare a pretty good idea as to where you think there will be a problem.

Then write it down. Write what you think the problem is, what you will change, and how you expect it to react. If at all possible, note it down on top of a system diagram. Otherwise, as you continuously change things within your system you may forget the exact changes done and troubleshoot things unecessarily.
