---
layout: post
title:      "What I Got Out Of Having A Professional Review My Code"
date:       2019-03-14 17:09:14 -0400
permalink:  what_i_got_out_of_having_a_professional_review_my_code
---



After writing the initial code for my Rails-JS project, I was pretty happy with myself. I’d incorporated fetch, async-await and the application wasn’t breaking. It wasn’t until I had a friend  that has been working professionally with Javascript for five years review my code brought me down a peg or two.

**Here are some of the takeaways:**

Developers spend much time reviewing code they did not write or have not looked at in a while.  They are not especially fond of doing so.  Anything that helps them do this more quickly is appreciated, and anything that should be simple but is unnecessarily complicated will piss them off.  Additionally, being sloppy will not serve you well.   Your style should be consistent so that the reader can make some basic assumptions about what they are looking at and is not being distracted by your different spacing or indenting.  Beautify, is an excellent tool for helping out with the last bit.  And linters (ESLint, JSHint) are great for helping out with this issue as well. 

**function() {} or () => {}**
Pick one and try to stick to it.  The time when your choice here makes a difference is when you are working with the 'this' value.  Often, you can avoid the problem entirely.  For example, using JQuery's .each().

**Semicolons - Use them or lose them**
If someone is reviewing your code, they are judging you whether you want them to or not.  Being haphazard with semicolon insertion makes you look sloppy.  Some people subscribe to not using them at all.  If you're going to be one of those people, don't use them. 


**Extract Strings as separate variables when possible:**
When making API calls, you should extract strings as separate variables. 

For example:
```
$.get(`units/${unitId}/something/${somethingId}`)
```
becomes:
```
const somethingUrl = `units/${unitId}/something/${somethingId}`
$.get(somethingUrl)
```
Try not to mix promises and Callbacks:
This goes back to having a consistent style. Either you rely on callback functions, or you use Promises. Both allow you to sequentially execute actions so don’t drive someone crazy by having them figure out which approach you are using.  One area where I ignore this advice is when using a promise would introduce complexity.  For example, using .click().
Just use the callback. 
