---
layout: post
title:      "Moving from Ruby on Rails to Javascript"
date:       2019-06-05 15:45:59 +0000
permalink:  moving_from_ruby_on_rails_to_javascript
---


When I started Javascript six weeks ago, I couldn’t even begin to process how Javascript might fit into my Rails app. I was aware of basic features like alerts but was nervous about the the significant change in syntax and the sometimes too flexible nature of JS. Everyone seems to either rave or complain about Javascript but regardless, it's ubiquitous in modern web apps. 

> Everyone: You’re doing the same things in new ways. 

> Me: But why do I need to do anything in a new way if my app is fully functional? 

![](https://images.ecosia.org/2IzCt0rivf8T31qujTPbpA3_OdE=/0x390/smart/http%3A%2F%2Fwww.memecreator.org%2Fstatic%2Fimages%2Fmemes%2F4025305.jpg)

It wasn't until I completed my JS Final Project that I finally understood the how and why I would continue to adopt new languages, libraries and frameworks into my coding arsenal. 

When moving from Rails to Javascript, you begin integrating new libraries like jQuery (which make it possible to *write less, do more* with Javascript - sounds appealing, right?) to make your app more user friendly. It's the old stuff you learned in Ruby done in different ways that increase speed, structure and potential for scalability. 

By integrating jQuery and serializers, I can render related data on the same page without needing to reload the page. By adding serializers to your Rails app, you can expose your model relationships to Javascript and make it possible to render in JSON format and 'paint' your DOM with your data. As aptly put by [a fellow Flatiron student:](https://brentbauman86.github.io/weaving_with_javascript) 

> serializers act as the glue that binds your rails attributes for a specific object and allows you to access those attributes via js.
> 

For example, pre-jQuery, users had to reload my Rails CRM app approximately 4 times to dig out the a list of Clients for a specific Programme. With jQuery, it can all be viewed on the same page by defining a click event, JSON data call and ID selector in which to render the Client names. 

```
$(() => {
  console.log("programmes.js is loaded");
  getProgrammeClients()
});

function getProgrammeClients(){
  $("a.programme-link").on('click', function() {
    let programme_id = $(this).data("id");
    let programme_url = "/programmes/" + programme_id + "/clients" + ".json"

    $.get(programme_url, (data) => {
      data.forEach(obj => console.log(obj))
      showProgrammeClients(programme_id, data)
    });
  });
}

function showProgrammeClients(programme_id, clientArr){
  let text = "<ul>";
  clientArr.forEach(obj => {
    let link = `<a href="/clients/${obj.id}">`
    text += "<li>" + link + obj.full_name + "</a>" + "</li>"
  });
  $('.programme-' + programme_id + '-clients').append(text)
}
```

I think if I had grasped the purpose of Javascript and fit with RoR years ago, my coding journey might have been slightly less bumpy. Feel free to comment on other compelling reasons to make the jump into Javascript and beyond! 






