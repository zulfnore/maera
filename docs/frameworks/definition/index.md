---
layout: default
title:  "Defining a framework"
category: development
tags: development
---

Maera makes it easy to create new frameworks.

To create a new framework you can create a new plugin:

```php

<?php
/*
Plugin Name:         Example Framework
Description:         This is just an example of hw to build a framework plugin for the Maera theme
Version:             0.1
Author:              me
Author URI:          http://example.com
*/

define( 'MAERA_EXAMPLE_FRAMEWORK_URL', plugins_url( '', __FILE__ ) );
define( 'MAERA_EXAMPLE_FRAMEWORK_PATH', dirname( __FILE__ ) );

// Include our framework class.
require_once MAERA_EXAMPLE_FRAMEWORK_PATH . '/class-Maera_Example.php';

/**
 * Include the framework
 */
function maera_framework_example_include( $frameworks ) {

	// Add our framework to the array of available frameworks
	$frameworks[] = array(

		// Alphanumeric (lowercase name of our framework)
		'value' => 'example',

		// The full name of our framework.
		// This will be used in the framework selection option in the dashboard
		'label' => 'Example',

		// The name of our Framework Class.
		// We're going to include everything concerning our framework there.
		'class' => 'Maera_Example_Framework',

	);

	return $frameworks;

}
// Add our framework to the list of available frameworks
add_filter( 'maera/frameworks/available', 'maera_framework_bootstrap_include' );
?>
```

Next step: [adding our framework macros](/docs/frameworks/framework-macros)