---
layout: post
title:  "atom-maven"
date:   2017-09-28 23:45
categories: projects
permalink: /blog/:year/:month/:day/:title/
excerpt: "Maven integration for Atom!"
image:
  feature: atom-mark.png
tags: [atom, apache, maven, javascript, js, node, nodejs, projects]
link: https://atom.io/packages/atom-maven
---

Maven integration for atom!

Generates module specific .classpath files based on the Maven pom files in your Atom workspace.

## Features

| Feature | Status |
| :------ | :-----: |
| Configures the classpath for every Maven module in your workspace. | Complete |
| Automatically update the classpath when you update your pom files. | Complete |
| Build the Maven projects in the workspace on save. | Complete |
| Build the Maven project via user interaction with the UI. | Complete |
| Notification when your classpath has been configured. | Complete |
| Notification when a duplicate dependency definition has been identified. | TODO |
| Notification when a dependency does not exist. | Complete |
| Link to the location of erroneous dependencies. | In Progress |
| Identify when a new pom file is added into the workspace and bind the change event to it. | TODO |


![310516](https://cloud.githubusercontent.com/assets/12021575/15692408/12018824-2786-11e6-8cac-289fd0af4076.JPG)

### Using the UI Features
There are two method of using atom-maven from the UI; from the Packages menu, and from the command palette.

#### Packages menu

![packages-menu](https://cloud.githubusercontent.com/assets/12021575/25781403/bba6e132-3331-11e7-9596-b6bd74812bd9.PNG)

#### Command Palette

![command-palette](https://cloud.githubusercontent.com/assets/12021575/25781396/ab10a45c-3331-11e7-8131-06fcd1f0c132.PNG)

## Known Issues

The notification which informs you that a dependency doesn't exist always points to line 0.

## Configuration  

It is required that Apache Maven is correctly installed on your computer and is ready to use on the command line.

Please see the Maven website for [installation instructions](http://maven.apache.org/install.html).

| Configuration Key | Required / Optional | Description |
| :------ | :----- | :----- |
| Classpath File Name | Optional | The name of the file to write your classpath to in your Maven module. |
| Generate Classpaths On Startup | Optional | Build all maven pom files on Atom start up and create classpaths for each. |
| Generate Classpaths On Save | Optional | Watch maven pom files for save events and create classpath when the pom changes. |


## What's new?
Checkout the [changelog](https://github.com/concon121/atom-maven/blob/master/CHANGELOG.md) for the full list of recently implemented features and bug fixes.

## Backlog and Issues
The complete list of features which needs to be implemented, future enhancements, known issues and bugs can be found on the atom-maven GitHub repository [issues page](https://github.com/concon121/atom-maven/issues).

## Contributing
Contributions are always welcome, there is still a lot of work to be done!  Feel free to pick up an issue in the backlog and open a pull request to get the conversation going.  I am more than happy to provide help and direction, and very welcoming of advice and suggestions.

## Raising Issues

If atom-maven is not resolving your classpath correctly, it is really useful for debugging purposes if you could provide sample pom files which I can use to reproduce your issue.

## What can I use atom-maven for?

I started developing atom-maven as I wanted to be able to write my Java code in Atom.  There are a couple of packages I found which make this easier, but they depend on a .classpath file being configured.  As a user of Maven, Maven configures your classpath and makes sure all your dependencies are available when you need them to be.  The atom-maven package replicates this functionality and generates the .classpath file other Atom Java packages need, based on your Maven pom files!   

### Useful Java Packages

The below atom packages work well with atom-maven:

*   [autocomplete-java](https://atom.io/packages/autocomplete-java)
*   [linter-javac](https://atom.io/packages/linter-javac)

#### autocomplete-java
Capable of reading the generated .classpath file, this package provides functionlity to organise imports, complete packages and classes, examine methods etc...

Note. git ignored .classpath files are not discovered.

#### linter-javac
Capable of reading the generated .classpath file, this package will attempt to compile your .java files and show you all the compile time problems with your code.

## Kudos
Kudos to the following, for making my life easier!

* [node-maven-api](https://www.npmjs.com/package/node-maven-api)
* [atom-message-panel](https://github.com/tcarlsen/atom-message-panel)
* [xml2js](https://github.com/Leonidas-from-XIV/node-xml2js)
