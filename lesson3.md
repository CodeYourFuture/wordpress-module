# Lesson 3 - Plugin development

* What is a WordPress plugin
  * The most basic plugin
  * Plugin handbook and reference
* Custom post types
* Shortcodes


## What is a WordPress plugin?


```php
<?php

/*
Plugin Name: My First WordPress Plugin
*/

// Your code goes here
```
_This is an example of the most basic WordPress plugin you can create._

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

> **Dive deeper**  
> The best place to learn about WordPress plugin development is the "[Plugin Developer Handbook](https://developer.wordpress.org/plugins/)". It's "the official" guide to plugin development, from the WordPress developer team.
