---
layout: post
title:  "Regex - Love it *and* Hate it"
date:   2017-04-06 20:04:36 -0400
---

"I hate Regex because frankly I really don’t understand it"
"You can think of regular expressions as wildcards on steroids"
"Regex makes me want to weep"
"I love it and I hate it"

Can you relate to one of the above quotes? I actually came accross them while researching how to use regex, and I have to admit, I'm one of the weirdos who actually love it.  At first glance it may seem like the brainchild of someone who had completely lost their mind but, love it or hate it (or both), its results can sometimes appear as nothing but miraculous. 

And on that note, I wanted to share the following.  It's just a small sample of what regex can do and which have helped me solve some of my coding problems.  


```
**Regex quick reference**

[abc]
A single character of: a, b, or c
[^abc]
Any single character except: a, b, or c
[a-z]
Any single character in the range a-z
[a-zA-Z]
Any single character in the range a-z or A-Z
^
Start of line
$
End of line
\A
Start of string
\z
End of string
.
Any single character
\s
Any whitespace character
\S
Any non-whitespace character
\d
Any digit
\D
Any non-digit
\w
Any word character (letter, number, underscore)
\W
Any non-word character
\b
Any word boundary
(...)
Capture everything enclosed
(a|b)
a or b
a?
Zero or one of a
a*
Zero or more of a
a+
One or more of a
a{3}
Exactly 3 of a
a{3,}
3 or more of a
a{3,6}
Between 3 and 6 of a

**Match beginning and end**

 /^wp.*php$/ ==> Starts with wp and ends with php

Matches
wp-comments-post.php
wp.something.php
wp.php

/(/\b[A-Z].*[[:punct:]]$/)/ ==> Starts with a capital and ends with a punctuation

Matches
	Flake!

**Phone Number verification**

Example:

^\s*(?:\+?(\d{1,3}))?[-. (]*(\d{3})[-. )]*(\d{3})[-. ]*(\d{4})(?: *x(\d+))?\s*$

if phone.match(/^\s*(?:\+?(\d{1,3}))?[-. (]*(\d{3})[-. )]*(\d{3})[-. ]*(\d{4})(?: *x(\d+))?\s*$/)	
  return true
else
  return false	
end

It would match the following examples and much more:

18005551234
1 800 555 1234
+1 800 555-1234
+86 800 555 1234
1-800-555-1234
1 (800) 555-1234
(800)555-1234
(800) 555-1234
(800)5551234
800-555-1234
800.555.1234
800 555 1234x5678
8005551234 x5678
1    800    555-1234
1----800----555-1234

**Split a string by commas and/or spaces**

"john@doe.com, person@somewhere.org terry@blue.com".split(/[\s,]+/)
# => ["john@doe.com", "person@somewhere.org", "terry@blue.com"]

```
