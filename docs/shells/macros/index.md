---
layout: default
title:  "Skin Macros"
category: development
tags: development
---

Maera uses twig to handle a lot of its templating.
You can learn more about the twig syntax here: by taking a look at [twig's templating documentation](http://twig.sensiolabs.org/doc/templates.html)  
An essential part of a shell is the [macros](http://twig.sensiolabs.org/doc/templates.html#macros) we use throughout the other templates.  
You will have to create a new file called `shell.html.twig` and Maera will automatically use it for its macro definitions.  
Below you can see the definitions that we have for the Bootstrap shell.

You'll notice at some points that we include apply_filters and other WordPress-specific functions that don't normally exist on twig.  
We are able to do that because we use the [Timber Library](http://upstatement.com/timber/) to implement twig.

<script src="https://gist.github.com/aristath/463cd8f8bf7568707155.js"></script>

You can simply copy-paste these to your own shell plugin and tweak them to suit your own needs.

Please note that even if you leave some of these empty, you will have to include them or specify fallbacks.