---
layout: post
title:      "Tech for Good: Rails Final Project"
date:       2019-04-07 09:24:05 +0000
permalink:  tech_for_good_rails_final_project
---


When a [local community organisation](https://novanew.org.uk/) decided it was time to go 100% digital, I used my rails final project as an opportunity to explore how I might help. I’ve used Salesforce and other CRMs in the past and had always hoped to learn how to build my own one day. Past experience with CRMs gave me some idea on how I wanted to map out my models and associations, but I did run into trouble along the way that I will detail here in hopes of saving others some time going forward. 

**Hiccup 1 **

I first ran into trouble when my controllers weren’t referencing the corresponding ids for their nested routes. If you're not calling the right :id in your controllers, your routes will quickly get tangled in your console and in your mind!

```
#routes.rb

resources :organisations do
    resources :programmes
end
```

```
rake routes

organisation_programme_path 

GET      /organisations/:organisation_id/programmes/:id(.:format)    
```   

```
#programmes_controller.rb

def show
    @programme = Programme.find(params[:id])
    @client = Client.new
  end
```

**The :id in your controller must match the one in the nested route**, specifically the one that is being nested. Otherwise, you will be using a foreign key, such as :organisation_id as shown in the example above. 

**Hiccup 2 **

Despite the fact that the ```has_and_belongs_to_many association```, this project required that I include the ability to add a writable attribute. 

> 4.4.1.1 Additional Column Methods
> 
> If the join table for a has_and_belongs_to_many association has additional columns beyond the two foreign keys, these columns will be added as attributes to records retrieved via that association. Records returned with additional attributes will always be read-only, because Rails cannot save changes to those attributes.
> 
> **The use of extra attributes on the join table in a has_and_belongs_to_many association is deprecated. If you require this sort of complex behavior on the table that joins two models in a many-to-many relationship, you should use a has_many :through association instead of has_and_belongs_to_many.**

Unfortunately I realised this a bit late and thereforce had to do a bit of backtracking to change my associations and create a join table. 

**Hiccup 3**

In theory, scope methods are simple to understand. However, I found rendering data less straightforward and the documentation a little thin. After reading the documention repeatedly, here are the two videos that finally helped me. 

[Active Record Scope Methods](https://www.youtube.com/watch?v=akwUv3KzRcc)

[Custom scopes in model files in a Rails application](https://www.youtube.com/watch?v=OHS4OXPMRfc)
		
Although my project is complete, I look forward to developing this further over the coming weeks with the hopes of Nova CRM becoming a useful open source and completely customisable tool for the non-profit community. Please check it out, comments and contributions welcome! https://github.com/VirginiaDooley/nova-new



 
