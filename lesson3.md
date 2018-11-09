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

Out of the box WordPress comes with a few different "post types" and as a WordPress developer you can add your own programmatically. You already know two of them: (Blog) _posts_ and _pages_. For your group project you will have to create your own custom post type to represent bikes for sale. Post types can be used to store and group information about different kinds of content. A few examples of custom post types one could add could be _videos_, _employees_ or _recipes_.

#### Exercise
_Come up with at least 3 different kinds of custom post types._

In order to add post types WordPress has a function called `register_post_type()` which you can call from within an action, such as the `init` action which is run after WordPress has been initialised. It has a few different options that you can use to tweak your post type. For example you can decide if your post type is supposed to be public or only visible from the WordPress admin. Registering a custom post type for _people_ looks like this:

```php
add_action('init', function () {
    register_post_type('people', [
        'labels' => [
            'name' => __('People'),
            'singular_name' => __('Person'),
        ],
        'public' => true,
        'has_archive' => true,
    ]);
});
```

The function takes an array of options, such as `has_archive` or `labels`, which itself takes an array of options.

#### Exercise
_Register your own custom post type from your plugin. Google around and see if you can find a way to change the default icon in the sidebar in the WordPress admin._

The best place to go to find out what you can do with post types is the WordPress Codex: https://codex.wordpress.org/Post_Types.

### Listing custom post types

In the previous lesson on theme development you were introduced to the [template hierachy](https://github.com/CodeYourFuture/wordpress-module/blob/master/lesson2.md#the-template-hierarchy). Like posts and pages you can also create custom templates for listing your custom post types. In WordPress such a list is referred to as an "archive". **You will need this for your group project** to list bikes for sale.

#### Exercise
_Using the template hierarcy, figure out how to build a custom archive template for your custom post type._
