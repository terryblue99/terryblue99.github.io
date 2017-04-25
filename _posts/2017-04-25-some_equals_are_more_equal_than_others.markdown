---
layout: post
title:  "Some Equals Are More Equal Than Others"
date:   2017-04-25 20:41:14 +0000
---

I have come to realise that a part of coding can sometimes mean having to unlearn what I've learned.

Case in point; I was testing some code I'd written, part of which contained the seemingly innocent statement, 'if a = b'. My code was failing by going into a loop so I didn't even have an error message to look at for guidance. I put breakpoints in the code to have it stop so I could see what it was doing at a given point, to no avail.
 
I tried everything I could think of to figure out what was causing the code to fail, but nothing worked. It kept looping and I was rapidly becoming loopy. Then after walking through the code what seemed an endless amount of times, I saw a piece of it that literally jumped out as the cause of my misery; 'if a = b'.
 
The equal in this statement did not equal the equal I had intended it to be; it should have been 'if a == b'. Why hadn't I noticed that before? I made the correction and my code finally passed it's test.
 
I wonder what I'll have to unlearn next :)
