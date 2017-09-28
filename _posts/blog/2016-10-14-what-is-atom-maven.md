---
layout: post
title:  "What is atom-maven?"
date:   2016-10-14 21:39
categories: blog
permalink: /blog/:year/:month/:day/:title/
excerpt: "atom-maven is a plugin for the popular text editor atom.io which attempts to add support for Apache Maven."
image:
  feature: apache_maven.jpg
tags: [sample]
---

So it seemed appropriate for my first attempt at my first blog post to write about my first ever so slightly semi not unsuccessful open source project - [atom-maven][atom-maven].

Earlier this year, I fell in love with [atom][atom.io], the new (ish) text editor developed by GitHub.  Its marketed as a "hackable text editor for the 21st century", and it really lives up to that claim allowing you to customise it to your hearts content and extends its functionality via custom plugins (if you want to be proper about it, they're called packages).

Atom's community is pretty huge and growing.  At the time of writing there are 5074 plugins available to download, and even more custom themes so that you can modify how the UI looks.  Atom is built using [electron][electron] which uses the Google Chrome V8 engine. Buzz words aside, this means that atom is a desktop Node JS app, with a HTML and JavaScript UI with all the developer tools of the Chrome web browser.  Pressing `ctrl + alt + i` to open the developer console, you can immediately start throwing down the jQuery and playing with the UI.  As atom is a Node JS app, you also have access to all the Node API's right there in the developer console, as well as the API's which atom its self exposes.

Once I quit screwing with atom and trying to break it, I got down to business and started looking into how I could really optimise my work stream using the flexibility and customisability that atom affords me.  At the time when I started using atom, I was doing a lot of front end UI HTML and JavaScript work, so of course I hunted down every and all plugins which would make my life easier in that respect.  There are code formatters ([atom-beautify][atom-beautify]) and linters ([linter-eslint][linter-eslint]) galore, there's even a sexy little plugin called [vim-mode][vim-mode] (and [ex-mode][ex-mode]) which give you vim short cuts in your text editor!  I was literally in developer Nirvana!

Unfortunately the day came when I had to switch back from JavaScript to good old Java, and switch back to my slow, clunky, memory sucking Eclipse IDE.  Don't get me wrong, I like Eclipse.  It's got a lot of really cool features that I couldn't do without.  Some days though, I just want to throw it through a window.  If you've ever used Eclipse, you've probably had one of those moments where you're sat there thinking, "Why are you spending 10 minutes building the ENTIRE workspace, when all I asked you to do was open this poxy little file...".  It was one of these moments which ultimately sparked my quest to turn my simple atom text editor into a fully fledged Java IDE.  

First things first, what plugins had other people already created which would aid me in my noble quest?

- [linter-javac][linter-javac] - Even the best developers make mistakes.  Eclipse, as well as pretty much every other IDE has the functionality to point out things that will result in compilation errors.  linter-javac does just this.  It basically uses the javac installed on your system which comes with your JDK to compile your code in the background when you save your work.  If it detects a problem, it will display a red error mark on the screen to notify you.  Lovely.
- [autocomplete-java][autocomplete-java] - Another feature that every good IDE has, I know it as the more colloquial term "intellesence", which I believe was coined by Microsoft for their Visual Studio product.  But don't quote me on that.  It simply shows you a little drop down as you're typing, suggesting completions for the things you could be typing.  This may include completing the name of a variable, displaying the list of available methods in a class, displaying classes on the classpath with a name similar to what you've started typing etc... I find this one really useful for exploring API's I'm fairly unfamiliar with.

For me, these two plugins covered the basics, the features I felt were missing that atom did not already provide out of the box, and the features that I really wanted in an IDE.  I'm a bit of a command line geek, so there's a lot of stuff IDE's do, for example git integration (which atom does a whole lot better by the way) or building my code, which I just prefer to just do on the command line or write scripts to do.

Conceptually the two plugins I found are great, they provide exactly the functionality that I wanted.  There's just one catch.  Both of these plugins require a .classpath file to have been configured in the root folder of your project to tell them what third party dependencies that your project uses and can compile against.  The .classpath file is simply a semi-colon separated list of file paths to jar files that your project needs.  At first glance, it seems pretty easy to throw one of these file together manually and maintain it manually, but the further down the rabbit hole you go you begin to remember that your dependencies have dependencies, and their dependencies have dependencies, and so on... As an avid Apache Maven user I'm quite used to M2E bridging the gap between Eclipse and Maven, sorting out my classpath woes for me automatically.  It occurred to me that I needed an M2E for atom, and thus lacking any pre-existing atom packages for Apache Maven, [atom-maven][atom-maven] was born.

The aim of [atom-maven][atom-maven] is to do for atom what M2E does for eclipse.  Shamelessly stolen from the [M2E website][M2E], the features it provides are:

- Launching Maven builds from within Eclipse
- Dependency management for Eclipse build path based on Maven's pom.xml
- Resolving Maven dependencies from the Eclipse workspace without installing to local Maven repository
- Automatic downloading of the required dependencies from the remote Maven repositories
- Wizards for creating new Maven projects, pom.xml and to enable Maven support on plain Java project
- Quick search for dependencies in Maven remote repositories

A good amount of work has been put into atom-mavens dependency resolution and mediation mechanisms so that a .classpath file can be created efficiently and with a high degree of accuracy.  This aspect of atom-maven works very well, however there are certain features missing so you don't quite get the complete Maven experience just yet.  I really want to nail down the dependency resolution features before I move on to the more "nice to haves" and UI oriented features, like kicking off a build.  Like I said, I'm a command line geek, these are fairly low priority for me.

In the coming weeks, I will endeavour to write posts explaining some of the things I learnt creating atom-maven, some of the challenges that I faced and hopefully knock out a few more features while I'm at it.

Happy Coding and Good Night!

[atom-maven]:  https://atom.io/packages/atom-maven
[atom.io]:     https://atom.io
[atom-beautify]:            https://atom.io/packages/atom-beautify
[linter-eslint]: https://atom.io/packages/linter-eslint
[vim-mode]: https://atom.io/packages/vim-mode
[ex-mode]: https://atom.io/packages/ex-mode
[linter-javac]: https://atom.io/packages/linter-javac
[autocomplete-java]: https://atom.io/packages/autocomplete-java
[M2E]: http://www.eclipse.org/m2e/
