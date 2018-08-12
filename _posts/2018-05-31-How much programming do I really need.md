---
layout: post
title:  "How much programming do I need?"
categories: blog
---

# How does a Mechanical Engineer get taught about Software Topics?
In my case, not at all. When I was in school, we had one programming class which taught basics on C and FORTRAN. Some classes assumed you had some MATLAB familiarity, others some LabVIEW concepts, but that was pretty much it. This is problematic, because many of these classes depended on creating some models or small control systems. It should be of no surprise that most of my code ended up looking like a mess until I took an internship that was mostly programming. Then my code ended up looking like a terrible mess.
"<!--more-->"
# So what should you learn?
I spent a few years after I graduated asking myself the wrong question - "What languages should I learn?".

This is the wrong question for multiple reasons. First, learning a programming language alone will only make you able to write terrible code in one language. And learning another language will simply help you to torture another compiler. Second, it does not tell you when you are done, or whether it is a good usage of your time. The right question to ask, at least at the beggining, is "How much Software Engineering/Computer Science do I need to know to do my job?". Then, the follow up becomes "How much of this stuff do I need to learn to make my life better?"

Having asked that question, let us explore the topic a bit.

# Say you are a test engineer
And that you have been tasked with instrumenting a part of a manufacturing line. This can take many forms, but for simplicity's sake, we can assume that we are only going to be reading some temperatures.

Chances are, you may be able to get away with using canned software. But if you are not able to find what you need, what should you learn?

If you are absolutely sure that your code will be throw-away and not to be reused (which almost never happens), then it may be safe to learn the basics of a programming language and do a few excercises. From there, you can build a simple piece of software that uses some kind of API to read a few temperatures and saves them to a file. The code will have its functionality statically defined - namely, it will run and do one simple thing. It will not necessarily be the most performant, but the majority of the heavy lifting will be done by the driver that you are using.

This is very different than if you are a test engineer tasked with creating a framework for testing parts across a full manufacturing line.

This sounds a bit obvious, but it is an extremely important point. If you are only tasked with writing ad-hoc tools, then you may only need to learn some basics through the process of learning a programming language. However, if you are tasked with writing software that you believe may need to be reused, or expanded, then you may need to learn do things the "right way".

And the right way, well, there's a lot of articles written for this. For example, you may want to [teach yourself CS](https://teachyourselfcs.com/). But if I was to summarize making software the "right way", I would say to not forget to treat it scientifically. Plan, execute, measure - these things are often forgotten in the rush of trying out code until it happens to work.

# What should everyone learn though?

No matter whether you will be writing code for a single test or for an entire line, there are a few things everyone should do. First, try to understand what your code is doing instead of writing lines by trial and error until things happen to work.

Second, please use Source Code Control. There are a gazillion articles on the web on this. Yes, even if you are the only person working on the project. No, it does not even have to cost you money.

Furthermore, please learn to not like your software. A problem I have seen a lot is that people get attached to the software they write and it creates a blind spot. It makes realizing what can be done better quite difficult. Look at a lot of stuff written by others, and [refactor](https://en.wikipedia.org/wiki/Code_refactoring).


-SRPSM
