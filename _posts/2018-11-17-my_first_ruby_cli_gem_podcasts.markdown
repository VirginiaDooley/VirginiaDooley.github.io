---
layout: post
title:      "My first Ruby CLI gem: Podcasts!"
date:       2018-11-17 08:08:06 +0000
permalink:  my_first_ruby_cli_gem_podcasts
---


![Vulture](https://pixel.nymag.com/imgs/daily/vulture/2018/05/03/podcasts-so-far/03-best-so-far-podcasts-2.w700.h467.jpg)

I devour podcasts like it’s my job. Living abroad, I soak up every U.S. political podcast I can stand. And when I feel like I need a break in the action from this increasingly unhealthy habit, I switch to something more light hearted and inspiring. With all this podcasting, I am always on the hunt for the next best thing. I stumbled on a [convincing shortlist by Vulture](https://www.vulture.com/) and knew I had found my site to scrape for my Command Line Interface Data Gem Project. 

On the Vulture webpage, I found: 

* A title with a url link and producer name 
* A summary 

After an inspection with developer tools, it was clear that I would need to do some splitting since title and url were bundled together in the same id. 

I named my Ruby CLI Gem: **Podcastme**

My Ruby Gem provides: 

* A CLI interface that user’s can interact with
* A data scraping class directed at the Vulture webpage
* Four levels of data including title, producer, summary and url to find the podcast and download or subscribe

When run, the user is presented with an indexed list of 16 podcasts including the title and producer. The user is prompted to choose a number to view more information about that podcast including summary and url at which they can sample or subscribe. 

I split my code into three files to handle: 

**CLI.rb**
code handling CLI display logic and user input

**Scraper.rb**
code scraping two levels of data, displaying two more for user selection

**Podcast.rb**
adds properties and find methods by index

There was a ton of initial set up but after that, the project was pretty straight forward. I watched Avi’s videos to get started and learned an incredible quick start for building gems: 

```bundle gem podcastme```

This command set me up with the directory and some basic files needed to build out my gem. 

Next, I created a new executable file and updated it with shabang and required files to load my ruby files. 

```#!/usr/bin/env ruby```

In this file, I added the require_relative files rather than required gems (which I put in my environment.rb file) . What’s the difference? 

*requirerelative complements the builtin method require by allowing you to load a file that is relative to the file containing the requirerelative statement.

I added the colorize gem to give the user interface a little zing and make the user input actions clear. From there it was time to scrape with open-uri and nokogiri gems and select the right css attributes to build out other methods to run, find, and select my list of podcasts. Although the focus for this project was on data scraping, it was a good chance to reaffirm my knowledge of object oriented Ruby and practice a variety of Ruby methods and enumerators. 

Overall, it was really exciting to build something that would not only have a functioning interface, but would also be useful to others as a published ruby gem. For my next steps, I’m going to consider building it out further by scraping the individual urls (which are mostly on different websites) to display a list of episodes for the user to choose from. 

You can find my podcastme gem here: https://github.com/VirginiaDooley/podcastme
