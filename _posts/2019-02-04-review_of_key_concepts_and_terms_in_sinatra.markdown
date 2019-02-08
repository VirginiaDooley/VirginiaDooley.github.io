---
layout: post
title:      "Review of key concepts and terms in Sinatra"
date:       2019-02-04 08:32:57 -0500
permalink:  review_of_key_concepts_and_terms_in_sinatra
---


Despite labs, meetups and pair programming, a major drawback of an online coding course is that I spend most of my learning time alone and not actually discussing concepts out loud. To prepare for the technical review of my Sinatra project and moving onto Rails, I went back to my labs to confirm my understanding of the key concepts related to Sinatra. 

**Which gems are essential in a Sinatra app and what do they do?**
* [ActiveRecord](https://rubygems.org/gems/activerecord/versions/5.0.0.1) gives us access to magical database mapping and association powers.
* [Rake](https://github.com/ruby/rake), short for "ruby make", is a package that lets us quickly create files and folders, and automate tasks such as database creation, 
* [Sinatra-activerecord](https://github.com/janko/sinatra-activerecord) gives us access to some awesome Rake tasks. In other words, this gem extends Sinatra with ActiveRecord helper methods and Rake tasks.

**What is the purpose of the config.ru and what is included in the file?**
The purpose of config.ru is to detail to Rack (a gem for Ruby that will help us create a web server at its simplest) the environment requirements of the application and start the application. When you start your server with ```shotgun```, config.ru is the first file that is checked. In that file, the Sinatra library is called, our app files are  required and the application is run. 

``` require 'sinatra' ```

``` require_relative ‘./app.rb’ ```

``` run Application ```

**What is middleware?**
Middleware is software that acts as a bridge between an operating system or database and applications, especially on a network. For the purposes of this project, I used Rack::MethodOverride to enable the ability to add PATCH, PUT, DELETE routes in my controllers. 

**What is the 'schema'?**
"The term "schema" refers to the organization of data as a blueprint of how the database is constructed (divided into database tables in the case of relational databases).

**What are 'routes' and how do they work?**
Routes are the part of an application that connect HTTP requests to a specific method in your application code built to handle responding to such a request (that part of code is called a Controller Action).

In other words, when a request is made to https://learn.co/blog, the router matches the request to the route and the matching controller action renders the HTML response (aka 'the view' or the V in MVC)

**What Is A RESTful Route?**
The client/server relationship is a prerequisite of a set of principles known as REST( representational state transfer). When something follows this principle, it's known as 'RESTful". 

A RESTful route provides a mapping between HTTP verbs (POST, GET, PUT, PATCH, DELETE), controller actions, and (implicitly) CRUD (Create, Read, Update/Replace, Update/Modify, Delete) operations in a database. A single entry in the routing file creates seven different routes in your application. Review the map [here](https://www.restapitutorial.com/lessons/httpmethods.html).

**What are DOM views?**
The Document Object Model (DOM) is an application programming interface (API) for HTML and XML documents (among others). It defines the logical structure of documents and the way a document is accessed and manipulated.

**What is a session and what happens when a session begins/ends?**
*Who:* 
You (the user), your browser and your app server. All these actors interact using sessions and cookies to move a stateless HTTP exchange to persist a simple state. 

*What: *
A session (aka transient or session cookie) is an object hash that stores data describing a client's interactions with a website at a given point in time. It stores key => value pairs of things like URL, date, time of use, username, email, etc as requested by the server.

A (persistent) cookie is a hash that gets stored in the browser and sent back to the server along with every subsequent request.

 Cookies are the client-side counterpart to sessions.

*When:*
When a user visits a webpage, (persistent) cookies are stored.
When the user logs into the site, the session begins.

At this point, cookies and sessions start working together:

"The web application on the server reads the cookie, associates it with an existing session (if such a session exists), and decides how to respond. For example, if there is no cookie received, the application might show the login page. If a cookie is received that doesn't match the data stored in the server-side session hash, the app might show the login page with the username filled out –– having retrieved that data from the cookie –– but request that the user reauthenticate. If a cookie is received that does match the data in the server-side session hash, the app would respond with that user's data."

*Where:*
Sessions are stored in the app server until the user logs out of the app or the session times out. 
Cookies are stored in the browser until they are cleared or deleted. 

*Why:*
Improved user experience!
Cookies make it easier for a user to visit, leave and return to websites without having to login repeatedly. Sessions simply allow you to navigate through a site without repeatedly having to authenticate yourself on every new page you visit **within** the web application domain - which would be SUPER annoying. 


**What is the flow of the MVC?**
MVC stands for Model — View — Controller. It's a paradigm. It allows a coder to separate the logic of the application and more easily update each part. And likewise, MVC allows a user on the client side to create and update objects in the database. 

If you're a visual learner like me, this may be better understood visually: 

![](https://i.imgur.com/4o3Qtrv.png)

Feel free to comment with additional concepts you feel are essential to my review!


