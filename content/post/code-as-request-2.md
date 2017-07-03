---
title: "Code as request 2"
description: "Another application by request"
date: "2017-07-03T13:34:00+07:00"
tags: ["problem", "react", "app"]
---
# Code as request 2
Every lunch time, my team will struggle finding place to have lunch. Everyone will ask each other "Where will we have lunch today?", and most of us would say "anywhere". We waste time here up to minutes a day. We have tried 3 approaches.

## Line vote
In [Line](http://line.me) application, there is a feature to create poll and let everyone in group vote the result. Sound great. But the pain is we have to create new poll + choices everyday we can't reuse it and most of us also have no idea where should we have lunch. In the end poll was not successful.

![line-poll-image](http://)

## Google form
We have tried [Google form](https://form.google.com). Created form and send the link to everyone in team. With this approach we can reuse the poll just reopen it again next day. But it stil require everyone to participate in. The result is not successful

![google-form](http://)

## Luuchdomizer
### Design
So I created an application to random place to have lunch. My requirement is
- No internet needed
- One person must be enough (no vote system)
- Can add more places later
- Less chance to get same place as yesterday

### Implementation
I decided to use React as progressive web app because I want it to be available both on mobile and web. Since this app is very small so I don't use 3rd party css library css file as well. I use in-line style only. I choose copy theme [AYU](http://github.com/ayutheme) color as I use it in text editor since sublime to vscode. I feel comfortable with it. When it comes to an app responsive design is one important thing. I've learnen how to use `display:flex`. To store user data I decided to parse json data to string and save it into `localStorage` in browser. With this I don't have to setup firebase database for each user, easier right? And to reduce the odd for yesterday random place, I have to create submit button to tell the app that we have choosed this one. The app will calculate new odd using this formular 

**Selected:** odd value - 1
**Others:** odd value + 1
Every place started odd value is 10. Then it will random between 0 and sum odd value. Finally it will check which range the randomed value is.

And again, to beautifully add this web app to home screen we need cool icon. Thanks to [Flaticon](http://flaticon.com) for providing me cool free icon as always. 

### Hosting
At first time, I tried to host this application on github pages in company's github enterprise but no luck. The server response 500 as a result. When I think again this app don't related to company at all. I make it public [here](http://github.com/serm-tape/lunchdomizer). And hosting it on [Netlify](http://netlify.com) [here](http://lunchdomizer.netlify.com).

# Conclusion
This is how I solve the problem. I don't know there are other lunch randoming application around here. I have created one. How do you solve this kind of problem please share with me.