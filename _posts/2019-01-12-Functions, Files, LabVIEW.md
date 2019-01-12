---
layout: post
title:  "Functions, Files and LabVIEW"
categories: blog
description: Some musings on contrasting file hierarchies between LabVIEW and other languages.
---
(in work)

## How is code divided?

In **Clean Code**, the author, Robert Martin, quotes Ron Jeffries' thoughts on what makes clean code. One of the comments that Ron makes is that clean code **contains no duplication**. Later on, he goes to describe that code should effectively be tiny, but using different words. This got me thinking about how code is often organized within LabVIEW and other languages.

## LabVIEW and code organization

In LabVIEW, a subroutine or function must effectively be its own file. This is pretty dramatically different than many other languages where it is common to put multiple functions within the same file insofar as they belong to the same package.

For example, let's look at the [this Java code](https://github.com/clojure/clojure/blob/master/src/jvm/clojure/lang/Cons.java) that wraps Clojure calls.

That code imports clojure.lang and provides a series of methods to do Clojure "stuff". Namely, the quintessential *Cons* which allows you to couple two pieces of data together. It also contains a lot of methods that make sense to do to things that you have *Cons*'d together.

What would it look if we were to do this in LabVIEW?

Well, there would likely be a main library (.lvlib file) and a series of files - one file per method. We would have thus a clojureLang.lvlib or clojureLangCons.lvlib, with a file for the *next* method (next.vi within the lvlib) , one for count, etc.

## Why does this matter?

I think this matters because it seems like the code gets tiny-er by definition. It's now in multiple files.

However, we have to do the same amount of work to ensure that each individual function is not dependent on things it does not depend on, does not continue to duplicate lower-level logic, etc. There is a great opportunity because the language itself pushes you towards that division of responsibility - but you still got to do the work and notice if you are starting to replicate logic across multiple files.

\- Simon Perez Santa Maria
