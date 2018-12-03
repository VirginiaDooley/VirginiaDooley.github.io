---
layout: post
title:      "OO Ruby Review"
date:       2018-12-03 18:34:23 +0000
permalink:  oo_ruby_review
---


In this post, I review scopes of class as well as instance and local methods and variables. I’m a visual learner so this graphic and these quick reference points really helped me ground me when these concepts were first introduced. 

![](https://www.natashatherobot.com/wp-content/uploads/variable-scope-ruby.jpg)  

 * Class variable (@@a_variable): Available from the class definition and any sub-classes. Not available from anywhere outside.
 * Instance variable (@a_variable): Available only within a specific object, across all methods in a class instance. Not available directly from class definitions.
 * Global variable ($a_variable): Available everywhere within your Ruby script. Seldom used. 
 * Local variable (a_variable): It depends on the scope. You’ll be working with these most and thus encounter the most problems, because their scope depends on various things.

### Class Scope

But what do we mean by “available”? Availability of methods and variables (and constants) in Ruby is understood by scope. In other words, scope determines which methods and variables are available at a given time. Let’s discuss the above reference points in more detail. 

### Class & Instance Methods

From our lessons, we know that:

> Classes act as a factory for our objects, capable of instantiating new instances (or 'life') of those objects. 

We call the methods defined within the object's class** instance methods** because they are methods that belong to any instance of the class.

For example, by defining #swim within a Student class, swim becomes a method of all instances of Student. If we instantiate more Students, they can all swim. Remember, an object can do anything, but it has to be taught how to do it.

A **class method** is a method that is called on the class itself (using the **self** keyword), not on the instances of that class. **Self** is a special keyword that points to the object that "owns" the currently instance of an object and can be used inside of a class and/or instance method. In an instance method, self points to the object whereas within a class method, the class itself owns the method.

### Local vs. Instance vs. Class Variables

A  **local variable** that is defined inside one method, for example, cannot be accessed by another method. In order to make variables available outside of a particular method, we can use **instance variables** inside our classes.

An** instance variable** is a variable that is accessible in any instance method in a particular instance of a class. 

A **class variable** is accessible to the entire class––it has *class scope*. 


```
class Podcast
  attr_accessor :title, :producer, :url, :summary

 #class variable set to an empty array
 @@all = [] 

 #class method using the self keyword
 def self.find(index)
    self.all[index.to_i-1]
  end

  def initialize(title, producer, url, summary)
    #setting properties - these are instance variables
    @title = title
    @producer = producer
    @url = url
    @summary = summary
    #all instances of the Podcast object will be stored in a class variable. self.class.all refers to the class of Podcast rather than a Podcast object
    self.class.all << self
  end

  def self.all
    #all Podcasts will be called in the @@all class variable
    @@all
  end

end
```







