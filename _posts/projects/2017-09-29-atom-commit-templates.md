---
layout: post
title:  "atom-commit-templates"
date:   2017-09-29 00:46
categories: projects
permalink: /blog/:year/:month/:day/:title/
excerpt: "Easily set custom commit templates from the Atom UI"
image:
  feature: atom-mark.png
tags: [sample]
link: https://atom.io/packages/atom-commit-templates
---

Easily set custom commit templates from the Atom UI

## Setting a Git Commit Template

To enable your git commit template to take effect, this package writes to a ```.gitcommit``` file in your home directory, and updates your git configuration to use this file as a commit template e.g.

```
git config --global commit.template ~/.gitcommit
```

#### Keyboard Shortcuts

- ```ctrl-shift-alt-t``` on Windows and Linux
- ```cmd-shift-alt-t``` on OSX
- ```Atom Commit Templates: Set Commit Template``` from the command palette

#### Input Dialog
![atom-commit-template](https://user-images.githubusercontent.com/12021575/30941905-a8f31262-a3df-11e7-86e5-772338acb340.jpg)

#### Commit Message Automatically Populated
![commit-message](https://user-images.githubusercontent.com/12021575/30941982-10b29774-a3e0-11e7-89eb-e0f36498a4f7.png)

## Goes well with

- [Git Plus](https://atom.io/packages/git-plus) - Git commands without the terminal!
- [Git Control](https://atom.io/packages/git-control) - A git GUI directly in Atom

## Kudos

Kudos to the following, for making my life easier!

- [atom-input-dialog](https://github.com/aki77/atom-input-dialog)
