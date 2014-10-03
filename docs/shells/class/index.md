---
layout: default
title:  "Building the shell Class"
category: development
tags: development
---

Our main shell class will contain all the functionality of our shell. We will be loading our stylesheets, sripts and anything else required by our shell here.

{% highlight php linenos=table %}
<?php

/**
* The Shell
*/
class Maera_Framework_Core {

	private static $instance;

	private function __construct() {

		do_action( 'maera/shell/include_modules' );

		// CAUTION: DO NOT DELETE THIS.
		if ( ! defined( 'MAERA_SHELL_PATH' ) ) {
			define( 'MAERA_SHELL_PATH', dirname( __FILE__ ) );
		}

		// Define our compiler.
		$compiler = null;

		// Enqueue the scripts
		add_action( 'wp_enqueue_scripts', array( $this, 'scripts' ), 110 );

		// Add the shell Timber modifications
		add_filter( 'timber_context', array( $this, 'timber_extras' ) );

	}

	/**
	 * This is required to instantianate our shell
	 */
	public static function get_instance() {
		if ( null == self::$instance ) {
			self::$instance = new self;
		}

		return self::$instance;
	}

	/**
	 * Register all scripts and additional stylesheets (if necessary)
	 */
	function scripts() {

		wp_register_style( 'example-css', MAERA_EXAMPLE_SHELL_URL . '/assets/css/style.css' );
		wp_enqueue_style( 'example-css' );

		wp_register_script( 'example-js', MAERA_EXAMPLE_SHELL_URL . '/assets/js/main.js', false, null, false );
		wp_enqueue_script( 'example-js' );

	}

	/**
	 * Timber extras.
	 */
	function timber_extras( $data ) {

		$data['singular']['image']['switch'] = true;
		$data['singular']['image']['width']  = 550;
		$data['singular']['image']['height'] = 300;

		$data['archives']['image']['switch'] = true;
		$data['archives']['image']['width']  = 550;
		$data['archives']['image']['height'] = 300;

		return $data;
	}

}
?>
{% endhighlight %}

The above contains the basics of a shell and is just an example.

**Lines 10-28:** Add any actions & filters we may be using. This is where you'll probably be executing any custom functions that you add to this class. These are executed as soon as the class is intantianatied.  
**Lines 33-39:** We use the singleton pattern to instantianate our classes, so this is necessary. Also requires line 8: `private static $instance;`  
**Lines 44-52:** Enqueue our stylesheets and scripts.  
**Lines 57-68:** Include any customizations that our shell requires to handle our twig template files.  

Next step: [adding our custom templates](/docs/shells/views).