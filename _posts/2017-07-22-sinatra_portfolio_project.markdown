---
layout: post
title:  "Sinatra Portfolio Project"
date:   2017-07-22 16:39:36 -0400
---


REQUIREMENTS

1.	Build an MVC Sinatra Application
2.	Use ActiveRecord with Sinatra
3.	Use Multiple Models
4.	Use at least one has_many relationship
5.	Must have user accounts. The user that created a given piece of content should be the only person who can modify that content
6.	You should validate user input to ensure that bad data isn't created

Being an avid watch collector I decided to write an app that would allow a collector like myself to document their watch collection.  I decided to have just two models, a user and a watch model, as I am a staunch believer in utilizing the KISS (Keep It Simple, Stupid) principle.

My first task was to use the [Corneal](https://github.com/thebrianemory/corneal) Sinatra app generator to generate a MVC template structure. I then used the commands provided in Corneal to generate my user and watch controllers, models, and tables.

I also wanted to create my app by using the TDD method as I had never done so before.  I didn’t want to reinvent another wheel so I took an existing Rspec file that was similar to what I needed, and modified it for my purposes. I did have to tweak it a few times as I progressed through creating my app but I was glad I decided to go that route.

I have to say I was a little nervous about attempting this project but I was surprisingly amazed at how relatively smoothly the whole process went by using [Corneal](https://github.com/thebrianemory/corneal) and TDD, and I believe that I have met all of the project requirements.

My app doesn’t have any bells and whistles in terms of amazing colorful graphics, but it does the job it was created to do.  However, I am looking forward to the time when I will be creating apps like that.

My app can be viewed in Github, [here.](https://github.com/terryblue99/watch_collection)
