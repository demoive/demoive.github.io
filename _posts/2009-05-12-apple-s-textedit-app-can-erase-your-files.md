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
When editing a document in TextEdit, a copy of your work is automatically saved every 30 seconds to the hard drive*. This behavior is common in software as it provides a convenient means to recover some of your work should the application unexpectedly quit or crash.

Unfortunately, the means by which TextEdit saves a copy of your work is awfully rudimentary. It simply writes your data to a regular file and gives it the same name as your TextEdit document but with ` (Autosaved)` appended as a suffix (without an extension). And since no verification is performed to see if a file with that particular name already exists, it will overwrite anything that gets in its way with no confirmation or warning!
