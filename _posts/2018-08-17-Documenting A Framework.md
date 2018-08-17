---
layout: page
title: Documenting a Framework
description: Lessons learnt from documenting a large Open Source project
image: DCAF.png
---
# A Starting point
Writing good documentation is pretty hard, and not something I necessarily look forward to. But unless you want to be constantly answering questions about your code it is worthwhile doing.

When I started looking into the documentation that existed for DCAF, I came to the conclusion that there was a fair bit of good material, but it was mostly in a series of presentations within a Documentation repo. The presentations were sorted by when they were presented more than by topic, which meant that you had to have knowledge of when a topic was discussed to get information about it.

There was also some help contained within the sample projects, but you had to know that there were sample projects to get there. Finally, there was also some documentation on the DCAF forum - but any documentation update required being an admin to that forum. And finding any help also requires searching through a forum, which is not ideal.

# What makes good framework documentation?
There are a lot of tools and books written on documenting code.

Many of these cover things such as making the code itself self-documenting (Pragmatic Programmer), or on how to make code have a certain "look" so that a reader can easily understand what something is (style guides like the Python PEP). There are also books on software requirements and project requirements and their documentation, but I wanted to talk about how to document a framework.

In this case, there are 3 types of things that a user could want to do with DCAF:

1. Use the Framework without programming anything. Only use the Configuration Editor and have custom code (if any) exist outside the framework.
2. Use the Framework and create application specific behaviour within it. Use the examples to load it or add extra behaviour.
3. Build re-usable plug-ins for the framework, or modify the framework itself.

For simplicity, let us ignore the configuration aspect. Otherwise the list gets too long to keep copying.

# What does each one need?

Let's start by discussing the first use-case. This case needs to have an understanding of:

* Nomenclature
  * External components
* API
  * External API - how to call the framework
* List of available sample projects
* List of currently available modules

And that's pretty much it.

The second use-case requires those things, as well as a few extra ones:

* Nomenclature
  * External components
  * Plugin components
* API
  * External API - how to call the framework
  * Integration APIs - how to load up a module into the framework
* List of available sample projects
* List of currently available modules

The third use-case takes those things and adds quite a few more:

* Nomenclature
  * External components
  * Plugin components
  * Engine components
* API
  * External API - how to call the framework
  * Integration APIs - how to load up a module into the framework
  * Engine APIs
* List of available sample projects
* List of currently available modules
  * Where to look at the available modules source code
  * How the available modules work, to use as examples
* Best practices
* Niche topics

# So do we just create three documents?

We could have 3 separate repositories, one for each user type. However, maintaining this would be pretty difficult. They would quickly get desynchronized.

Instead, let's compartmentalize the different types of content so that we only write about each thing once - and whoever does not need a specific piece can just skip it.

So I created a Developer's Guide that has all of the necessary information on using the DCAF Framework to make applications. Well, tried to - there is still a lot of stuff that is missing. But it's a good starting point.

Then we created some classroom training material as well as some exercises.

Wait a minute, we already had exercises - we did the same thing again. There were already some exercises in the hands-on folders.

Also, there were still a bunch of documents on the forum that are orphaned

# So what are we aiming for

Currently I am working on trying to simplify the available materials even further. Ideally, we would have the following organization:

### Presentations

Series of 1 hour, reusable presentations. The idea is that someone that has to give a quick talk on DCAF can use these, or slides from these and cater to a specific audience

### Training

Holistic training that contains content from the Dev Guide and other presentations, but is catered towards the classroom. Does not contain exercises but instead points to the ...

### Hands on

Currently we have a couple of Hands-On presentations and exercises. Ideally the training will point to these, and there will be two types. The first type can be given as a stand-alone session, and the second can be an addendum. Both are made to be used as exercises in the training.

1. Full exercises with step-by-step instructions on creating a configuration, creating a simple module, creating a more complex module
2. Challenge exercises with description and solutions, but without step-by-step instructions

### DevGuide

Finally, this is a longform document that tries to encompass the entirety of the knowledge that a developer needs to know if they want to work with, or modify, DCAF.

# So why is the current state of the documentation still so fragmented?

It's often easier to create a new document for a specific purpose than to arrange reusable things.

Funny how whether we are writing code or writing documents, we have to force ourselves to think about longterm reusability instead of "just making the thing I need right now".

-SRPSM
