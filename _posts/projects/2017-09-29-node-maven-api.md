---
layout: post
title:  "node-maven-api"
date:   2017-09-29 00:26
categories: projects
permalink: /blog/:year/:month/:day/:title/
excerpt: "Run Maven commands via a Node JS API!"
image:
  feature: nodejs.jpg
tags: [npm, javascript, js, node, nodejs, projects]
link: https://www.npmjs.com/package/node-maven-api
---

Run maven commands via a Node JS API!

## Usage

To create the maven handler, you need to call the create method providing the path to the POM file to be handled.

```
var mvn = require('node-maven-api').create('/workspace/project/pom.xml');

mvn.clean();
mvn.install();
```

### Clean

Invoke a maven clean on your project.

```
mvn.clean();
```

### Install

Invoke a maven install on your project.

```
mvn.install();
```

### Test

Invoke a maven test on your project.

```
mvn.test();
```

### Effective POM

Get the effective pom for your project.  A promise will be returned which will be resolved to a javascript object which represents the xml effective pom.

```
var promise = mvn.effectivePom();

promise.then((result) => {
    console.log('Effective POM is: ', result);
});
```

### Custom Commands

The API provided by this module can not possibly cover every maven goal, there is far too many!  You can run any command you need with the execCommand function.

Function Parameters:

1.  The event name for your command.
2.  The command to execute.

```
// mvn clean install -f /path/to/my/pom.xml
mvn.execCommand('my-custom-event', 'clean install');
```

### Events

Sometimes you might want to perform some action after you have executed a maven command.  Upon completion of a process, the api will trigger an event via the Node JS EventEmitter.

For the methods which this api exposes, the event names are as you may expect:

*   clean
*   clean-failed
*   install
*   install-failed
*   test
*   test-failed
*   effective-pom
*   effective-pom-failed

For custom commands you may provide your own event name, with the assumption that '-failed' will be automatically added in the event of a failure.

You may use the ```registerEvent``` function to bind a callback to an event.

Function Parameters:

1.  The event name to bind a callback to.
2.  The callback to bind to the event.

Example:

```
mvn.registerEvent('my-custom-event', () => {
  console.log('My Custom Maven command was successful! :)')
});

mvn.registerEvent('my-custom-event-failed', () => {
  console.error('My Custom Maven command Failed... :(')
});

mvn.execCommand('my-custom-event', 'clean install');
```
