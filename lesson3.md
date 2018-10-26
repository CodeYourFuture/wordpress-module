# Lesson 3 - Plugin development

* What is a WordPress plugin
  * The most basic plugin
  * Plugin handbook and reference
* Custom post types
* Shortcodes


## What is a WordPress plugin?
Plugins are a great way to add extra functionality to our WordPress sites. There are thousands of WordPress plugins avaialble in the [plugin directory](https://wordpress.org/plugins/), but sometimes you need something that is very specific to your exact use case that you need to write a plugin yourself.

In its purest form, a plugin is simply a PHP file with a comment header container _at least_ a `Plugin Name`. It looks like this:

```php
<?php

/*
Plugin Name: My First WordPress Plugin
*/

// Your code goes here
```
_This is an example of the most basic WordPress plugin you can create._

If you put this file in the `wp-content/plugins` directory directly, or in a subdirectory, you have a plugin.

**Exercise**  
_Create your own WordPress plugin and see if you can activate it from the WP dashboard. Explore [other headers](https://developer.wordpress.org/plugins/the-basics/header-requirements/) to add to your plugin, such as a version number or a link to your own website._

> **Dive deeper**  
> The best place to learn about WordPress plugin development is the "[Plugin Developer Handbook](https://developer.wordpress.org/plugins/)". It's "the official" guide to plugin development, from the WordPress developer team.

The way we typically add functionality in WordPress is by using [actions](https://developer.wordpress.org/plugins/hooks/actions/) and [filters](https://developer.wordpress.org/plugins/hooks/filters/).

```php
<?php

/*
 * Plugin Name: My First WordPress Plugin
 */

 add_action('wp_head', function () {
    echo '<script>alert("Welcome to my site!")</script>';
 });
```
_A very simple WordPress plugin that uses the `wp_head` action to inject JavaScript code into the `<head></head>` part of the WordPress site._

