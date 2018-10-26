# Lesson 3 - Plugin development

## What are WordPress plugins?
Plugins are a great way to add extra functionality to our WordPress sites. There are thousands of WordPress plugins avaialble in the [plugin directory](https://wordpress.org/plugins/), but sometimes we need something that is so specific to our exact use case that we need to write our own plugins.

In its purest form, a plugin is simply a PHP file with a comment header containing _at least_ a `Plugin Name`. It looks something like this:

```php
<?php

/*
Plugin Name: My First WordPress Plugin
*/

// Your code goes here
```
_This is an example of the most basic WordPress plugin you can create._

If we put this file in the `wp-content/plugins` directory directly, or in a subdirectory, we have a plugin.

#### Exercise
_Create your own WordPress plugin and see if you can activate it from the WP dashboard. Explore [other headers](https://developer.wordpress.org/plugins/the-basics/header-requirements/) to add to your plugin, such as a version number or a link to your own website._

### Actions and filters

The way we typically add functionality in WordPress is by using [actions](https://developer.wordpress.org/plugins/hooks/actions/) and [filters](https://developer.wordpress.org/plugins/hooks/filters/).

Actions allow us to execute a function at a specific point in the execution of the WordPress code. As an example if we want to do something after WordPress has been initialised we can hook into the `init` action with a function. Filters are similar to actions, with the main difference being that we can modify (or filter) data relevant to that action. In this tutorial we will only focus on actions.

> **Dive deeper**  
> The best place to learn about WordPress plugin development is the "[Plugin Developer Handbook](https://developer.wordpress.org/plugins/)". It's "the official" guide to plugin development from the WordPress developer team.

Here is an example on how we can provide an anonymous function to an action:

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

#### Exercise
_Add an alert, like in the example above, to your WordPress plugin. What happens if you de-activate your plugin?_

## Custom post types

Lorem ipsum.

## Shortcodes

Lorem ipsum.
