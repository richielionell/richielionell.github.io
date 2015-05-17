---
layout: post
title: Handling Ampersands While on Jekyll
---

If you had clicked on my RSS feed until sometime ago you would have been welcomed with an ugly page with this error;


    error on line 464 at column 16: xmlParseEntityRef: no name

The trouble was the ampersand in a few of my posts. Learnt from these posts that you had to do a `&amp;` to prevent stand-alone-ampersand accidents.

- [GitHub Pages, Jekyll, Ampersands and Apostrophes](http://dwdii.github.io/2013/08/28/GitHub-Pages-Jekyll-Ampersands.html)
- [http://stackoverflow.com/a/14318580/1948860](http://stackoverflow.com/a/14318580/1948860)

