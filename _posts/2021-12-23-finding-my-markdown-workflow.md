---
layout: post
title: "Finding my Markdown Workflow"
date: 2021-12-23 21:00
description: I spend a day trying different markdown editors in an effort to find a workflow I enjoy.
categories: Productivity   
---

# Finding my Markdown Workflow

Recently I took three weeks off for some end of year vacation time. For the first time there wasn't one thing I wanted to focus on. A typical vacation for me is either spending some time on side projects like [Lazy Gardener](https://lazygardener.app) or doing math. But this time around the drive wasn't there to put time into either, so where to put it? When faced with endless possibilities I took to making a list. While listing all the things around the house that needed to be done I wanted to go over my notes to see if there was something that hadn't made it to my todo.txt file. There was a problem; my notes were all over the place. 

My documents folder had random notes of various sizes in just about every folder, most out of context of the folder. Over time I'd become rather sloppy relying on search over structure. The laziness came from the fact that I never thought about *how* I was taking notes. When creating a new note I would first have to think about the context of the note. Home vs personal development? Should I make a folder for this topic? It's like sitting down to write some code without first thinking of the problem you're trying to solve. That's fine when you're starting to rough things out, but not a great long term plan. The result for me was to create a new file, type some thoughts down, then hit save. Location be damned, thus creating my dependence on Spotlight / [Alfred](https://www.alfredapp.com). Similar to writing code, the best code is the one not written. The best searching is one I didn't have to do. Having a well-defined (not rigid) structure means I wouldn't have to search, I could just go to where the note was. 

Another I was having with my note taking workflow was just how I was taking notes. I do all my note taking in Markdown as I've found plain text files work best for me. During the day I may jot some notes down on pen and paper, but eventually they find their way to a text file. Markdown is great. Simple syntax that supports things like links, list, and images. Plus, renders easily to html (I use [Pandoc](https://pandoc.org) for this). Though not a part of Markdown, I use YAML metadata to specify title, date, and tags for my notes. What I was looking for was an IDE of sorts for how I take notes. 

## What I want

In an ideal world[^1] there would exist some application that would support the following features:

* Easy to use
* Structured views (folders and content outline)
* Plain text editing
* Spell check
* Live preview of rendered output
* Ability to run cli actions[^2]
* **Bonus**: Visualization of tag connectedness

## Editors 

### Sublime and VS Code 

Over the years I've relied heavily (and enjoy using) both [Sublime Text](https://www.sublimetext.com) and [VS Code](https://code.visualstudio.com). With Sublime and VS Code had roughly the same problem in that I didn't want to invest time into setting up were the last two bullet points above. Mainly the ability to run cli commands easily was what kept me looking for a better solution. Both allow you to specify a build target via json files, but it would be something I would need to learn how to do. For whatever reason, VS Code didn't feel "comfortable" to use as my note taking app. This might be a mental context issue. At work I'm on a PC in VS Code for most the day. It's a natural for me when I need to make a note to pop open an empty file and just start typing. In fact, for work I might setup a notes workspace and use VS Code or Sublime. But for home with the additional desire to build notes and upload posts to my site, both were close, but not quite there. If I couldn't find a better workflow I would finish getting Sublime setup. 

[![Sublime](/assets/images/finding-my-markdown-workflow/sublime-article.jpg)](/assets/images/finding-my-markdown-workflow/sublime.png)
[![VS Code](/assets/images/finding-my-markdown-workflow/vscode-article.jpg)](/assets/images/finding-my-markdown-workflow/vscode.png)

It was at this point I decided that I wanted to try some apps that made for editing Markdown. 

### Bear 

First up, [Bear](https://bear.app). From their website:

> Bear is a beautiful, flexible writing app for crafting notes and prose.

It is. For a group of people that I realized were not me. Its ability to cross link notes and workflow based around tagging make it a great choice for people looking to just write. But without the ability to edit arbitrary text files on my computer and no way to view and edit in plain text Bear wasn't going to work. If you don't care about plain text editing, they have new Markdown editor [Panda](https://bear.app/panda/) that will be integrated into Bear in the future. Though it's easier to edit the Markdown in Panda, it's still not full plain text editing. I would love to see Bear support a form of "Source Code Mode" similar to [Typora](https://typora.io)[^3], and allow for local file access^[4]. Bear also didn't have a way from me to run cli commands. It would require me to completely change how I took notes. And if wanted to ever not use Bear I would have to export all most notes, just like I had to do with [Evernote](https://evernote.com) awhile back. 
  
### Obsidian 

Tried a few others, but all were less feature rich than Bear. Except one, [Obsidian](https://obsidian.md). Obsidian looks great and its graph visualizer for tags is just plain cool. Except the ability to run cli commands easily, Obsidian did it all. But there was something about it, similar to VS Code, that made is somewhat uncomfortable to use. Long term I know that if I didn't *want* to open the app to write, I would write. Overall Obsidian is great and when I'm interested in the connectedness of my notes it's what I'll use. Though not my primary note taking app, it's going to stay installed.

[![Obsidian](/assets/images/finding-my-markdown-workflow/obsidian-article.jpg)](/assets/images/finding-my-markdown-workflow/obsidian.png)

### Nova 

After more searching I came across [Nova](https://nova.app) by Panic. I've been using Panic software since 2005 and actually had Nova installed from when I signed up for the beta. At the time I was using it to build some sites and overall was pleasant to use. It never occurred to me to try it as my Markdown editor of choice until one of those random [Best X for Y](https://www.sitepoint.com/the-best-markdown-editors-for-mac/) search hits mentioned it. Nova is nice to use. The more I used it the more I wondered if my issue with VS Code and Obsidian is that they're not native.  Whatever it is, Nova didn't have that issue and ticked all the boxes except seeing a tag node graph. For my site I setup a quick Task to build and another to do the upload (Nova supports the upload and syncing, just haven't set that up). For my notes, I can "build" a note which exports it using Pandoc to html. After a week of use and a bit of organization of folders I'm happily using it as my default note taking app. It's setup in a way that works for me. I'm pretty sure most people would have stopped at VS Code, and I probably should have too. Workflows are like pens[^5]; your opinion of the perfect one changes over time. And it takes patience to find the one that works for you. There's a lot of great editors out there for everyone, Nova just fits my needs right now.  

[![Nova](/assets/images/finding-my-markdown-workflow/nova-article.jpg)](/assets/images/finding-my-markdown-workflow/nova.png)

[^1]: A truly ideal world I wouldn't need notes. I could remember everything and recall it instantly. 
[^2]: My current website is build with [Publish by Sundell](https://github.com/johnsundell/publish)
[^3]: Typora was good, but the sliding animation when toggling Source Code Mode on and off was too distracting
[^4]: Importing doesn't count
[^5]: I recently purchased 10 different technical pens from [Jet Pens](https://www.jetpens.com) looking to change up from my Pilot Hi-Tec C