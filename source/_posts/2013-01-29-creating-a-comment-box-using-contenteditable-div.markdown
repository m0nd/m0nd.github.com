---
layout: post
title: "Comment Box using ContentEditable Div"
date: 2013-01-29 11:46
comments: true
categories: [jquery, css, html5, contenteditable]
published: false
---
As part of some functionality on an upcoming website/service I am currently working on, one of the things I needed was a way to comment on "posts". At first I figured I would just use a regular ol' textarea, and be done with that buuuut then I started doing a little digging around to see how the "big boys" (Twitter, Facebook, Google, et al) handle this and found something quite interesting.

Most of the "biggest" sites that have some sort of commenting functionality are using the **HTML5** `contenteditable` attribute on an element (mostly `<div>`) to provide a box for users to type their comment in.

I found this to be preeeetty interesting and delved into it a bit more to find the pros and cons of using a contenteditable over a plain ol' textarea.

###Pros

####Rich formatting of text
This one is kinda neat and allows, for instance, twitter posts to have the username formatted differently to other text, or you could even use bold, italics, etc in your comments if you so desire. Textareas can only work with plain text and you would have to use [clever tricks](http://stackoverflow.com/a/8438534/758529) like facebook does, to try styling/formatting the text inside.

####Any element can be editable
This is another cool aspect, and can be used for instance to allow users to modify any or every single page on your site, including images. This point is definitely a big plus for CMS developers.

###Cons

####Browser support isn't fully standardized (yet)
Unless you just want straight up editing of your content without any concern about how the edits to your elements will be formatted/saved then this might not be that big of a deal. The main problem is that browsers implement a lot of the behaviour of contenteditable elements fairly differently e.g. when you press `Enter` some browsers insert `<div>`, others insert `<p>`, and yet others insert `<br>`. Things will probably get better as things get more standardized though, but it's still something to watch out for. One big plus is that browser *support* is great and goes even as far back as IE 5 (Microsoft were the first ones to introduce it).

Ok enough background info, now onto how I actually went about creating my very own comment box...

##Getting Started
``` html The basic Markup
<div class="commentbox" contenteditable="true">
	<span class="placeholder">Write a comment</span>
</div>
```

##Issues
Almost all issues I encountered were various browser quirks, like the very different ways each browser deals with a user pressing Enter or Backspace, and what elements get created after.