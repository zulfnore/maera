---
layout: default
title:  "Defining a shell"
category: development
tags: development
---

Maera makes it easy to create new shells.

The recommended method to create a new shell is by writing a custom WordPress plugin.

File structure of a shell plugin:

```
├── assets
|   └── Stylesheets and scripts
├── views
|   └── shell-specific templates
├── class-Maera_Example.php
├── shell.html.twig
└── shell.php
```

The first step will be to create our main plugin file. In this case we will call this file shell.php  
It would be best if you could keep the same file structure in your own shells to ensure better consistency.


```php

<?php
/*
Plugin Name:         Example Shell
Description:         This is just an example of hw to build a shell plugin for the Maera theme
Version:             0.1
Author:              me
Author URI:          http://example.com
*/

define( 'MAERA_EXAMPLE_SHELL_URL', plugins_url( '', __FILE__ ) );
define( 'MAERA_EXAMPLE_SHELL_PATH', dirname( __FILE__ ) );

// Include our shell class.
require_once MAERA_EXAMPLE_SHELL_PATH . '/class-Maera_Example.php';

/**
 * Include the shell
 */
function maera_shell_example_include( $shells ) {

	// Add our shell to the array of available shells
	$shells[] = array(

		// Alphanumeric (lowercase name of our shell)
		'value' => 'example',

		// The full name of our shell.
		// This will be used in the shell selection option in the dashboard
		'label' => 'Example',

		// The name of our Shell Class.
		// We're going to include everything concerning our shell there.
		'class' => 'Maera_Example_Shell',

	);

	return $shells;

}
// Add our shell to the list of available shells
add_filter( 'maera/shells/available', 'maera_shell_bootstrap_include' );
?>
```

Next step: [adding our shell macros](/docs/shells/macros).
