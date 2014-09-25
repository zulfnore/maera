---
layout: default
title:  "Theme Supports"
category: development
tags: development
---

When building your own shell, you can activate parts of the Maera framework using theme supports.  
Theme supports provide functionality and classes that you can use in your shells without requiring you to write your own code, thus taking advantage of Maera's structure.  

Theme supports are usually loaded using the `after_setup_theme` action.  
In addition to the default [theme features](http://codex.wordpress.org/Theme_Features) Kirki includes the following extra features:

```php
<?php

function my_theme_supports() {

	// Add Kirki
	add_theme_support( 'kirki' );

	// Add retina support
	add_theme_support( 'retina' );

	// Add color calculations support
	// Please note that this uses the 'jetpack_color' class.
	// More info on that class here: https://github.com/Automattic/jetpack/blob/master/_inc/lib/class.color.php
	add_theme_support( 'maera_color' );

	// Add the tonesque library
	add_theme_support( 'tonesque' );

	// Add site-logo support
	add_theme_support( 'site-logo' );

}
add_action( 'after_setup_theme', 'my_theme_supports' );

?>
```

You can find the list of theme_supports provided by Maera below:

## Kirki

[Kirki](http://kirki.org) is a wrapper for the WordPress customizer, making it easier for you to write your own customizer options and extend the default functionality.  
To enable kirki support and include the kirki framework you can use  
`add_theme_support( 'kirki' );`  
If the [kirki plugin](https://wordpress.org/plugins/kirki/) plugin is not installed on the user's site, then we include this from inside the theme to reduce dependencies. 

## Retina

When you add theme support for retina images, the image resizing script will create some additional images with the suffix **@2x** and also enqueue the [retina.js script](http://imulus.github.io/retinajs/) script.
To enable retina support you can use  
`add_theme_support( 'retina' );`

## Color calculations

If you need to do some color calculations performed, you can use Jetpack's color calculations class. If [Jetpack](https://wordpress.org/plugins/jetpack/) is not installed, then we include this class on the theme core to reduce dependencies.  
To include this feature you can use  
`add_theme_support( 'maera_color' );`

## Tonesque

If you need to retrieve the main color of an image and perform calculations based on that color, you can use Jetpack's [Tonesque library](https://github.com/Automattic/jetpack/blob/master/_inc/lib/tonesque.php). If [Jetpack](https://wordpress.org/plugins/jetpack/) is not installed, then we include this class on the theme core to reduce dependencies. Please note that when this is used, the color calculations class is also included.  
To include this feature you can use  
`add_theme_support( 'tonesque' );`


## Site Logo

Maera includes [Automattic's site-logo plugin](https://github.com/Automattic/site-logo). This way we're trying to standardize site logos usage across all shells. More documentation on this can be found on the [plugin's repository](https://github.com/Automattic/site-logo).
To include this feature you can use  
`add_theme_support( 'site-logo' );`