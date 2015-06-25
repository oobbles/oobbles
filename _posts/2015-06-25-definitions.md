---
layout: post
title:  "Definitions"
date:   2015-06-25 11:10:43
categories: code essay
---
##Definitions

###What is a class?
A class is a blueprint we use to make objects.  The blueprint can indicate attributes (like id, or name) and also spell out its methods- (what it can do).

###What is a model?
I think of the model as the class, but specifically geared towards use with databases.  It is a more general version, the M in MVC. I kind of consider it the bottom layer, because the views and the controllers are more front facing, where the model interacts with the database and provides things to the views.

###What is a method?
Methods (called functions in most other programming languages) are things an object can do.  We use them to save time, bundling together smaller statements in to one tidy package.  The start with `def` and end with `end` and must be defined before calling them.

###What is a variable?
Variables give a name to the things we store in Ruby's memory.  Ruby has five kinds: Global, Local, Constant, Class and Instance.

###What is a request?
When you ask for something.  In light of our recent project, when a user does some action that uses a route, they are requesting the controller find that route and do what is contained therein.

###What is a route?
A specific path leading to an action.  Often times serving up a page, which leads us to...

###In the context of a web application, what is a "response"?
When the page gets a request, it follows the route and sends a response.  I think of it as the completed action of whatever the route led to.