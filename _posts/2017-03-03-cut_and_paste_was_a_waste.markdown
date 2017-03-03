---
layout: post
title:  "Cut and Paste was a Waste"
date:   2017-03-03 00:13:02 +0000
---


I was working on a Ruby looping lab, Countdown to Midnight Lab, where the instructions were:

Write a method that takes in an integer argument and uses a while loop to countdown from that integer to 0, outputting "
#{number} SECOND(S)!" in each iteration of the loop. The method should return "HAPPY NEW YEAR!" after the loop finishes.  

I also had to make the loop pause for one second each trip around.


I thought this would be relatively straightforward as I had already covered the basics in the initial Ruby group of lessons, so I was reasonably confident…. **WRONG!**

Here is the code I came up with:

```
def countdown(number, seconds)
  while number > 0
  	countdown_with_sleep(seconds)
  	puts "#{number} SECOND(s)!"
    number -= 1
  end
  puts "HAPPY NEW YEAR!"
end

def countdown_with_sleep(seconds)
  sleep seconds
end

countdown(10, 1) 
```

I typed everything except for the values of the two puts strings which I cut and pasted directly from the instructions. It all looked good to me at this point so I ran it, and horror of horrors got the following error! 

syntax error, unexpected tIDENTIFIER, expecting keyword_end

I looked at that piece of code every which way but I just couldn’t see what could be causing the error; after all, there was no missing keyword_end as the error was indicating. And what was the unexpected tIDENTIFIER it was referring to? If I had any hair, I’m sure I would have been pulling them out at that point. 
 
Then out of the blue (pun intended as my last name is Blue) I recalled a famous saying of Sherlock Holmes; “when you have eliminated the impossible, whatever remains, however improbable, must be the truth”. Could the fact that I had copied and pasted some of the code have anything to do with the problem?

Yep! That was exactly the cause of the problem, because when I deleted those parts of the code and typed them in myself, lo and behold…. **SUCCESS!**

On investigation, apparently what had happened was that in highlighting the strings to be copied, the highlighted area had included the following space and that was what was causing the error. 
 
I’m not giving up on cutting and pasting though; I just have to be more careful in future :)

