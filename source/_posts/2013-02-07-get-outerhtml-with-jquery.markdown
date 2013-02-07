---
layout: post
title: "Get outerHTML with jQuery"
date: 2013-02-07 14:25
comments: true
categories: [jquery, javascript, html]
---
While working on a bigger issue, I realized I needed a way to get the outer HTML of an element using jQuery, but since there's no native jQuery functionality to do that I searched around for various people's suggestions. The two main ones are basically:

####Use the native outerHTML property
`$([selector])[0].outerHTML` or `$([selector]).get(0).outerHTML`. This property is supported by all browsers at this point (Firefox was the last to catch up with FF11 last year)

####Create a temporary Parent
`$('<div>').append($([selector]).clone()).html`. This one is mainly used as a fallback for older browsers with no support for the outerHTML property (more or less just FF11 and under)

I decided to incorporate both techniques into a neat little jQuery plugin. Here's a gist of it...

{% gist 4728750 %}

