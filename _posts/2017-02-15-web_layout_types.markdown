---
layout: post
title:  "Web Layout Types"
date:   2017-02-15 21:06:49 +0000
---



Scaling  Elements
	
•	Fixed (px)
•	Elastic (em); 1em = 16px
•	Fluid (%)
•	Using Min/Max Sizing


Fixed (px)

A fixed website layout has a wrapper that is a fixed width, and the components inside it have either percentage widths or fixed widths. The important thing is that the container (wrapper) element is set to not move. No matter what screen resolution the visitor has, he or she will see the same width as other visitors.

A 960-pixel width has become the standard in modern Web design because most website users are assumed to browse in 1024×768 resolution or higher.

PROS: 
Widths are the same for all screens large and small.  

CONS: 
A fixed-width layout may create excessive white space for users with larger screen resolutions.

Smaller screen resolutions may require a horizontal scroll bar, depending on the fixed layout’s  width.


Elastic (em)

In Elastic layouts the size of the columns or sections is in proportion to the font size being used.
The widths are specified in em(s) and because font sizes vary, the em is a relative unit that responds to 
the user’s text-size preferences.

PROS: 
In responsive design up-scaling / down-scaling the text will keep the containers in
 	            	Proportion with their text content.

CONS: 
It takes a lot of savvy and testing to get the layout right for all users. Parent elements
	            	may begin to bump into each other as the type expands in size.  


Fluid (%)

In a fluid website layout, also referred to as a liquid layout, the majority of the components inside have percentage widths, and thus adjust to the user’s screen resolution.

While some designers may give set widths to certain elements in fluid layouts, such as margins, the layout in general uses percentage widths so that the view is adjusted for each user.

PROS:
Makes full use of the screen and can eliminate horizontal scroll bars in smaller screen resolutions

CONS:
The designer has less control over what the user sees with regards to container sizes and where type and media wraps


Min/Max Sizing

Four CSS properties, min-width, max-width, min-height and max-height, can be used to create a fixed width/height if the user’s screen is too small or too big for the layout to be usable; In this case, the layout gets a scroll bar and functions essentially as a fixed-width/height layout:


Unfortunately, most versions of Internet Explorer don’t support min-width, max-width, min-height and max-height. This is solved with an IE-specific expression (use the following web address for details on this):

http://perishablepress.com/press/2007/01/16/maximum-and-minimum-height-and-width-in-internet-explorer/


Example Code

HTML

<div class="fixed-size">
    Fixed (px)
</div>

<div class="elastic-size">
    Elastic (em)
</div>

<div class="fluid-size">
    Fluid (%)
</div

<div class="threshold-size">
    Threshold (min/max)
</div>

CSS

body {
    font-size: 1
        100%;
}

div {
    background: aqua;
    padding: 20px;
    margin: 10px;
    font-size: 1em;
}

.fixed-size { 
    width: 200px;
}

.elastic-size { 
    width: 12.5em; /* 200px/16px */
}

.fluid-size { 
    width: 70%; 
}

.threshold-size { 
    min-width: 500px;
    max-width: 900px;
}


