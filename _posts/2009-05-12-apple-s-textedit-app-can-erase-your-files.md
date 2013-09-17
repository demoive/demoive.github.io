---
layout: post
title: Apple’s TextEdit App Can Erase Your Files
permalink: apple-s-textedit-app-can-erase-your-files
excerpt: Apple’s TextEdit application has a massive design flaw that could potentially erase other files on your computer. Weird, right? Ironically, it’s TextEdit’s safeguard against loss of data that is the culprit of the defect. And the corruption of files isn’t a randomly occurring glitch either — it is caused by a shortcoming of the algorithm used in the Autosave feature.
---

Test page content

![Icon of the TextEdit Application](/assets/img/posts/TextEdit-Icon.png)

Apple’s TextEdit application has a massive design flaw that could potentially erase other files on your computer. Weird, right? Ironically, it’s TextEdit’s safeguard against loss of data that is the culprit of the defect. And the corruption of files isn’t a randomly occurring glitch either — it is caused by a shortcoming of the algorithm used in the Autosave feature.

## The Autosave Flaw
When editing a document in TextEdit, a copy of your work is automatically saved every 30 seconds to the hard drive†. This behavior is common in software as it provides a convenient means to recover some of your work should the application unexpectedly quit or crash.

Unfortunately, the means by which TextEdit saves a copy of your work is awfully rudimentary. It simply writes your data to a regular file and gives it the same name as your TextEdit document but with ` (Autosaved)` appended as a suffix (without an extension). And since no verification is performed to see if a file with that particular name already exists, it will overwrite anything that gets in its way with no confirmation or warning!

## Example
To better illustrate this flaw, take the following scenario. Suppose, for whatever reason, that I have a file named `Craziness (Autosaved)` and I create a text document called `Craziness.txt` in the same directory. In the screenshot below `Craziness (Autosaved)` is an image file (with the extension removed in order to illustrate my point):

![Screenshot of my 2 original files](/assets/img/posts/TextEdit-Autosave_1.png)

When I start editing my `Craziness.txt` file in TextEdit, the application autosaves my work (as it should), but since my image document has the same name as what TextEdit would call its autosaved file, my image file is overwritten:

![Screenshot of TextEdit's autosaved file](/assets/img/posts/TextEdit-Autosave_2.png)

When I’m done editing my `Craziness.txt` document, TextEdit removes the autosaved copy (as one would expect). However, now my original image file is gone with no real way to recover it (since it’s not moved to the Trash but actually overwritten):

![Screenshot showing loss of data caused by TextEdit](/assets/img/posts/TextEdit-Autosave_3.png)

## Solutions
Accounting for this file naming issue is so programmatically simple that it’s astounding the defect even exists. The simplest improvement would be to prefix the filename with a period (as in `.Craziness (Autosaved)`) in order to hide it from the Finder since the chances of having a naming conflict with a hidden file are greatly reduced.

But hiding the file from the user still allows for potential name collisions and as Mac OS X’s default text editor, TextEdit’s naming convention should be even more robust. To start, TextEdit could include either a timestamp or a sequence of random numbers to help make its autosaved filename unique. Most importantly, however, should be to verify if a file would be overwritten and if so, generate a different random number or append an incremental counter. Heck, even my [Page Capture widget](https://github.com/demoive/Page-Capture) won’t overwrite files since it uses the same naming convention as Apple’s screencapturing application (`File 1`, `File 2`, `File 3`, etc.)

## The Rant
One might argue that the possibility of having a file end with ` (Autosaved)` _and_ not have an extension is pretty slim. So what? My argument is that the possibility of an application **deleting other files blindly** is a completely unacceptable use case scenario, no matter how rarely it may occur. I think it is more reasonable to expect that a corporation as large as Apple Inc. would produce software that doesn’t delete unrelated files from my hard drive without my knowledge. Especially since OS X is — as Apple claims — the “most advanced operating system in the world.”

<span style="color:gray">†30 seconds is the default. The time interval is configurable and the user is allowed to disable the Autosave feature entirely.</span>