---
layout: page
title: Source Code Control for things that are not Source Code
description: What other uses exist for Source Code Control beyond putting your source code in it?
---

## Calling your documents Report_v3_final_forrealthistime.doc
I often start a report or paper with the best intentions. I intend to ensure that I keep one file updated, but that there are backups. Every once in a while I will come up with a different idea. Maybe it would be best if I remove one section, but I like the content in it. It's ok, I tell myself, I will remove that part and save it as another file. Then I will think about it for a bit and get rid of one of the versions.

So I end up with Report.doc and Report_Abridged.doc. While my cloud backup tools can take care of reverting a version or two, I do not know when the last snapshot was taken, hence why I opted to just change the file name until I figure out which one is better. After creating the second file I forget about the first until maybe a few years later when I am cleaning up that computer.

After deciding the work to be complete, I want to get some feedback. Rename the file (Report_Abridged_Final.doc) and send it to someone. They add their comments and send it back, but we do not use the inbuilt tools for reviewing because we forget.

I save the file as Report_Abridged_Final_v2. And so on.

## What does this have to do with Source Code Control?
One of the interesting side-effects of software is that it is often starts as text files. Tools created to save, compare or analyze source code can often be used for completely different things. This blog is a great example.

The blog is hosted in Github, a Source Code Control provider. Ignoring, for now, the sections of this that are "code", many files are just pure text files with some formatting in them saved in a format called "Markdown".

## Working in Markdown
Markdown is a simple markup language that can be converted and rendered as HTML, PDF or many other formats. There are a lot of guides on Markdown, so I will not quite go onto how to use it. What is important, is that Markdown can be written in a simple text editor and saved.

## Taking advantage of Github when writing text
Source Code Control tools have two main uses that are relevant to this discussion. The first is that they allow you to not worry about losing your data by keeping it somewhere that is not your computer and thus safe from coffee spills. The second, and more important, is that they can keep track of your changes without needing to continue to append \_final to your files manually.

This means that you can create a report of some kind, and, instead of saving it to your documents folder, save it into a repository in something like Github. As you work on it, you can save it to your desktop, but push it to that repository routinely. This will allow you to not worry much about keeping it safe, but if this stopped there it would not have much over saving things into OneDrive or Dropbox.

An important difference is that you have much more granularity on what versions are "frozen" and can be reverted to.

## Writing a report
Every day you make a few changes and push them to a repository without needing to change the file name ,even if you are not sure the changes will stick. If you ever need to look at a previous version of the file, just Revert to it. If you forgot what changed, just use a Diff tool to automatically compare.

Should you need to stick to a more standard document type that does not allow directly loading it up onto a text editor for a Diff, you can simply ignore the Diff part and have it track changes for you. At every "save" you can pretty easily add comments to keep track of what's different.

Try it out, and stop appending \_final and \_finalForReal to all your documents.
