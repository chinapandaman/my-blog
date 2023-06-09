---
title: Vim as Primary IDE - Intro
date: 2023-04-28 14:31:10
tags:
	- Coding
	- IDE
	- Vim
---
Throughout the years I have been coding, different IDEs/editors have attracted me and improved my workflow in different ways. Back in college, the very first editor I was taught to use a lot for CS classes was the good old Vim that comes with most Linux distributions. At the time I did not spend much time hacking it and simply learned a lot of the basic ways of using it. But it did serve its purposes for a college student with general syntax highlighting for most main stream languages and allowed me completing most of my projects.

<!-- more -->

When I first started my career, I came to realization that I finally need something more beefy than just an editor. And this is around the time where I was introduced to the JetBrains IDEs, in particular PyCharm. The rich features bundled in even just the community edition of this IDE such as GUI debugging, refactoring, searches and static analysis are amazing. Not to mention with the professional edition (which most companies would be more than happy to purchase for their software engineers), you can have supports on some of the most popular frameworks such as Django and Flask, and it has an awesome GUI database tool which makes day-to-day DB workload just that much simpler. To me, PyCharm is truly, like what JetBrains suggests, the essential tool for software developers. Throughout these years, I have tried different editors such as Atom, Sublime, vscode, etc. However none of these, even with a rich set of plugins, can compete with the kind of developing experience PyCharm brought to me.

After being spoiled for a long time by JetBrains IDEs, things finally started changing a little bit. I have recently acquired a new job and there are certain things with the new role that makes me shift away from an IDE with lots of out-of-the-box features. First of all the system admin restricts a lot of accesses on the laptops given to the employees, making installing any software quite a process. These restrictions however revolves mostly around the GUIs and does not stop you from doing a lot of things using the terminal. On top of that the kind of work I'm doing with this role is more and more based on terminal than GUIs. Finally unlike a lot of my previous roles where the tech stacks are usually monolithic, this time I have to use a wide variety of languages and frameworks. Ultimately this means I have to look for something that's more general purpose than a monolithic IDE.

All and all I have decided that instead of something like PyCharm I need another tool that can boost my development experience with the new role. But I also said I didn't really like a lot of the editors I tried like say vscode. And this is the moment I put my eyes back on my good old friend from college, Vim. I have used Vim heavily back in the days and know how strong it is when it comes to editing. And despite the fact that I have been a bandwagon on the IDE side, I'm also aware how configurable Vim can be and there have been projects like SpaceVim I know of which turns Vim into an IDE. And obviously Vim, even though it can be run as a GUI, is primarily terminal based.

So finally I made the decision of switching back to Vim. And my goal is ultimately making developing using Vim a similar if not the same experience as an IDE like PyCharm, but also more general purpose and terminal based. In this series of blogs I will do my best to present how I progressively made Vim better and in the end my primary tool of coding for both work and personal projects today.
