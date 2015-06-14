---
layout: post
title: WebStorm Babel plugin
---

# How-To Set Up the Babel Plugin in WebStorm

I've been enjoying programming in ECMAScript 6 recently.  I use the Babel plugin for WebStorm to compile ES6 code down
to ES5 code that can be run in the browser.

Babel has several advantages over Traceur.  Babel and Traceur both support all (or nearly all) of the ECMAScript 6 features
but Babel already has plans to begin support for proposed ECMAScript 7 features.  When I last looked at Traceur, 
it required a run time JavaScript library to support some of the ECMAScript 6 features.  Reportedly, Babel also produces 
more readable code.

But I always have trouble remembering how to set up the plugin and I haven't tried setting up Babel on a permanent basis
because I wasn't sure if I'd continue using it (versus Traceur).

For my reference (and yours, if you choose), here's how to set up Babel in WebStorm:  
1. Create a Scope  
![alt text](https://raw.githubusercontent.com/gwmccull/gwmccull.github.io/master/images/2015-06-11-webstorm-add-scope.png "Add New Scope")
  a. Name the Scope  
  ![alt text](https://raw.githubusercontent.com/gwmccull/gwmccull.github.io/master/images/2015-06-11-webstorm-add-scope-name.png "Name the New Scope")
  b. Add files to the Scope  
  ![alt text](https://raw.githubusercontent.com/gwmccull/gwmccull.github.io/master/images/2015-06-11-webstorm-scope-add-files.png "Add file to the Scope")
2. Set JavaScript version to ECMAScript 6  
![alt text](https://raw.githubusercontent.com/gwmccull/gwmccull.github.io/master/images/2015-06-11-webstorm-javascript-version.png "Set the JavaScript Version")
3. Add the Babel file watcher  
![alt text](https://raw.githubusercontent.com/gwmccull/gwmccull.github.io/master/images/2015-06-03_babel_preferences.png "WebStorm Preferences")
  a. Set the arguments  
  `$FilePathRelativeToProjectRoot$ --source-maps --out-dir out`  
  b. Set the Working Directory  
  `$ProjectFileDir$`  
  c. Set the Output Path to Refresh  
  `out`  
  d. Set the file scope to the scope you created earlier  
4. Files will now be transpiled to ECMAScript 5 in the `out` directory  