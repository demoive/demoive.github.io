---
layout: post
title: Filename Conflicts On Download
permalink: filename-conflicts-on-download
excerpt: I was very satisfied when Apple revisited how the Finder handled some of its file-naming architecture. Some behaviors were bugs and absolutely had to be fixed. For example, prior to Leopard there existed a mixed behavior when renaming files under different view modes (Column View, Icon View, Detail View, etc.).
---

<!--
categories: [technology]
tags: [os, mac, functionality, interaction
tags:
  - os
  - mac
  - functionality
  - interaction
-->

I was _very_ satisfied when Apple revisited how the Finder handled some of its file-naming architecture. Some behaviors were bugs and _absolutely had_ to be fixed. For example, prior to Leopard there existed a mixed behavior when renaming files under different view modes (Column View, Icon View, Detail View, etc.).

![Finder's toolbar buttons for the different View Modes](/assets/img/posts/finder-view-modes.png)

Normally if you start changing the name of a file and change your mind you could hit the Escape key, and the name would be restored to what you started with. However, under the Column View, hitting Escape was equivalent to hitting Return, and whatever text you currently had would be accepted. Very annoying! Obviously the first behavior is more intuitive, and it is inarguable that the renaming file behavior should be consistent throughout all View Modes.

## The Good
![Finder's intelligent filename selection which excludes the extension when renaming](/assets/img/posts/finder-name-selecting-on-rename.png)

The feature I most liked, however, was that if the extension of the file is visible and you started renaming it, the entire filename except for the extension was selected. This change made renaming much quicker and easier because not only did you no longer have to remember the extension, but less typing was required (on average four characters: period + three letter extension). At first these four extra characters might not seem like too much work, but if you rename a list of files, you would drastically notice the difference.

## The Bad
There is at least one more thing that I see that needs to be changed. When Safari downloads a file and another file already exists with the same name, it begins appending sequential numbers (preceded by a dash) to the end of the filename in order to distinguish them (“-1”, “-2”, “-3”, etc.).

![Two icons showing the intended behavior of Safari's renaming algorithm when downloading files with the same name](/assets/img/posts/finder-name-conflict-suffix.png)

But is the added suffix really appended to the end of the filename? Turns out it isn’t and I consider it a major bug. Say what you will, but I don’t see it as simply a behavior that isn’t necessarily right or wrong. I think it’s obvious what the intention is (refer to the screenshot above) and the screenshot below shows an example when the intention doesn’t carry through. From my observations, the Finder inserts the “suffix” immediately before the first period it encounters while searching from beginning to end of the filename. It should be inserted before the _last_ period.

![Two icons showing the malfunction in Safari's renaming algorithm](/assets/img/posts/finder-name-conflict-problem.png)

## The Solution
It would be very easy to iterate from back to front of the filename (my [Page Capture widget](https://github.com/demoive/Page-Capture) does). And it happens to be more efficient since extensions are typically shorter than the actual filename. Hopefully someone over at Apple reads this post and fixes the problem. While they’re on it, they might as well fix the other [problem I’ve mentioned with the TextEdit Autosave algorithm]({% post_url 2009-05-12-apple-s-textedit-app-can-erase-your-files %}).