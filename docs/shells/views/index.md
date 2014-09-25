---
layout: default
title:  "Adding custom templates (views) to our shell"
category: development
tags: development
---

Since Maera uses [twig](http://twig.sensiolabs.org/) we were able to do some fancy stuff, allowing you to include your own templates in plugins. The templates reside in the `views` folder.

Directory structure:

```
views
├── parts
|   ├── pagination.twig
|   ├── searchform.twig
|   ├── single-title.twig
|   └── tease-title
├── 404.twig
├── author.twig
├── base.twig
├── comment.twig
├── comments.twig
├── footer.twig
├── header.twig
├── html-header.twig
├── index.twig
├── page.twig
├── single.twig
└── tease.twig
```

Oc course you can customize that and build a different structure for your own shell, but this is the default structure that will be used if you only choose to customize a couple of these files.

Maera will automatically look for a `/views` folder first in the folder of your shell and if it doesn't find one of the required files in there, it will automatically fallback to the default template views from the theme's views folder.

You can see more details on the default files included on [Maera's githug repository](https://github.com/wpmu/maera/tree/master/views).