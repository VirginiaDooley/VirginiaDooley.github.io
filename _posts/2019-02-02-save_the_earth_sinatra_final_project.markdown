---
layout: post
title:      "Save the Earth! Sinatra Final Project"
date:       2019-02-02 11:10:57 -0500
permalink:  save_the_earth_sinatra_final_project
---


Since my final Sinatra project was introduced in January - aka the month of better intentions - I thought it was appropriate to build an app that would help me achieve my 2019 resolutions. I'm also trying to teach my kids about my coding journey so building an eco-action do list seemed like a good way to address both goals. 

Here is what I learned in the process: 

1. Helpers are your friends! Between my ```logged_in?``` and ```current_user``` helpers, I was able to refactor a significant amount of code. 

In addition to validating access to certain ```get``` requests, I had always wondered how nav bars display different content once logged in. It turns out it's super simple once you have those helpers defined:

```<% if logged_in? %>

#if a user is logged in, they will see these options:

<a class="btn btn-primary" href="/">Home</a>					
<a class="btn btn-primary" href="/ideas">Eco-Ideas</a>							
<a class="btn btn-primary" href="/actions/new">Create an Action</a>							
<a class="btn btn-primary" href="/actions/show">View my Actions</a>							
<a class="btn btn-primary" href="/logout">Log Out</a>

<% else %>

#otherwise, they will see these options:

<a class="btn btn-primary" href="/users/login">Log In</a>
<a class="btn btn-primary" href="/users/signup">Sign Up</a>
<a class="btn btn-primary" href="/ideas">Eco-Ideas</a>
<% end %>```
							

2. I love learning about new gems. For this project, I used some gems that helped save loads of time, protect against bad data and improve the user experience.
* [Corneal](https://github.com/thebrianemory/corneal) helped me set up the initial scaffolding in seconds. For someone who is prone to spelling mistakes and broken code as a result, Corneal **set up my environment as well as basic MVC files**. It did generate views in .html.erb and added styling which I ultimately (mostly) stripped out in favor of bootstrap. 
* [Bcrypt](https://github.com/codahale/bcrypt-ruby) **authenticated my user input** and prevented users from persisting instances of an objects with empty params with just a few lines of code in my models.
* [Rack Flash](https://rubygems.org/gems/rack-flash3/versions/1.0.5) **eliminated the need for a failure view** and instead let the user know when their input was successful or not. 
* My pair programmer partner for this week told me she used [validations built into ActiveRecord](https://guides.rubyonrails.org/v2.3.11/activerecord_validations_callbacks.html) which I definitely want to try out next time.

3. Planning your routes in the beginning will really help you gain a better understanding of how your app functions and how your code interacts. Doing so, will only prepare you better for your technical review.

All in all, I really enjoyed this project and look forward to user testing with my kids! 




							
							
