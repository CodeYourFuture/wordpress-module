# WordPress Lesson 1

** What we will learn today?**
- [One](#one)
- [Two](#two)
- [The Template Hierarchy](#the-template-hierarchy)
- [Child Themes](#child-themes)
- [The WordPress Loop and WP Query](#the-wordpress-loop-and-wp-query)
- [Homework](#homework)
---

**Before we begin...**

* You should have finished a pre-class lesson that showed you how to set up a local installation of WordPress on your machine using Docker? Let the mentors know if you have not completed this yet.
* WordPress uses the PHP programming language. This module is not designed to teach you PHP. However, although the syntax is a little different, you will be able to use what you have learned so far in JavaScript (such as variables, functions, arrays, conditional statements and so on) to help you. See [PHP Quick Start](#appendix-1-php-quick-start) in the appendix for a short overview of what is different.

## One

Para

## Two

Para

## The Template Hierarchy

Whether you are building your own theme, or modifying someone else’s with a child theme (explained later), you will have to understand the WordPress Template Hierarchy. This is the name given to the way WordPress chooses what template file in the current theme to use for each URI (or path) your user visits on your site — what one to use on the home page, the about page, search results page, 404 page and so on.

  > Do you remember when working with node.js you had to deal with routing in your code? WordPress is slightly different — it maps the URI to a template file(s) in your theme based on the rules of the Template Hierarchy.

The choice of template file that WordPress makes can be visualised with the following image representing the Template Hierarchy:

![Visualisation of the Template Hierarchy](./assets/lesson1/wp-hierarchy.png)

[View a larger version](https://developer.wordpress.org/files/2014/10/wp-hierarchy.png)

This shows you all the different possible template files you could have in your theme related to the Hierarchy. It may look a little complicated… but the good news is that they are all optional apart from one — the `‘index.php’` file. If you only had this file in your theme ALL pages would use this to output the content on that page. 

> ...you do need one more file in your theme called style.css but this is not related to the Template Hierarchy, it only outputs your styles

So, think of every template file you add after `‘index.php’` as simply allowing you to be more specific about what content outputs to a specific page. Let’s take a look at an example…
 
You should have the WordPress theme called ‘twentyseventeen’ installed and selected — if not, select it now in your WordPress admin under 'Themes'. Then, find the theme files in your local WordPress installation under `/wp-content/themes/twentyseventeen`. As well as the shared template files such as `‘header.php’, ‘footer.php’, ‘functions.php’` and so on there are the following files:
	
* `‘index.php’` — the default layout template file
* `‘front-page.php’` — the template file used for your homepage
* `‘page.php’` — …for pages
* `‘archive.php’` — …for post category archives
* `‘404.php’` — …for the 404 error page

We can see here that the twentyseventeen theme has the default `‘index.php’` but also four other template files that will be used as you browse different parts of your site.

Let’s take your site’s front page (i.e. home page) as an example — what twentyseventeen template file will be used for this…? Will it be `‘index.php’`? Hold on… it is a page, so it will be `‘page.php’` right…? Well, look at the Template Hierarchy image above again and look from left (more specific) to right (less specific). You will hopefully see that the answer is that it will use ‘front-page.php’ as this is more specific and overrides all the others.

Behind the scenes WordPress is doing a similar thing to what we are asking above — it asks itself, ‘What page am I on?’ and then it finds the most specific template file in the current theme available and uses that. This means that, as a theme developer, you have the flexibility to be as specific or as non-specific as you like when deciding what your site looks like.

So, now a quick quiz… (Use the Template Hierarchy image above to help you, the answers are in the Appendix.)

**Exercise 1: Quiz** 

* Q1. Our user is still on the site home page but we have deleted the `‘front-page.php’` file from our theme. What template file will be used for the home page now? 
* Q2. We want to change what outputs on all pages. What template file from above will we need to alter? 
* Q3. We want all pages to be the same apart from an About page that we have created. What do we need to do to have a template file specific to the this page only? (Note: the page URL will be ‘http:///mysite.com/about’)

Now that you have the knowledge to modify theme files, you may be tempted to start changing the your favourite theme’s template files to do what you want. But before you do, consider this — what happens if the theme updates at a later date with new features or bug-fixes? Then there is a good chance you will lose your changes! It is always better to create a child theme.

## Child Themes

Para

## The WordPress Loop and WP Query

### The WordPress Loop

> "The Loop" is the main process of WordPress. You use The Loop in your template files to show posts to visitors. You could make templates without The Loop, but you could only display data from one post.

Simply put, the Loop checks if there are posts or pages to be displayed and then displays them. It looks a bit like this:

```
<?php
    if ( have_posts() ) :
        while ( have_posts() ) :
            the_post();
            // Post Content here
        endwhile;
    endif;
?>
```

This is a PHP code block starting with an `if` statement. This has a `have_posts()` condition, which is a built-in WordPress boolean function (i.e. it will return `TRUE` or `FALSE`) that checks the database for content — if `TRUE` the content will be returned and the `while` statement will loop through each result. So, what content will be displayed? Here are some typical examples:

* **The user is viewing a page** — The loop will fetch and display the content of that page
* **The user is viewing a post** — The loop will fetch and display the content of that post
* **The user is browsing a category** — The loop will fetch and display the latest posts in that specific category

You'll find the loop used throughout WordPress themes and is the main way that content is pulled from your database and output onto your site. 

#### The Loop in action

Let's take a look at `index.php` in our twentyseventeen theme — find it and open it up in your code editor. Can you find where the `while` loop begins and ends?

```
<?php 
/* Start the Loop */
while ( have_posts() ) : the_post();
  get_template_part( 'template-parts/post/content', get_post_format() );
endwhile;
?>
```

The `get_template_part()` line is WordPress function that, as you can guess, gets a template part from elsewhere in our theme — the first parameter is the file location and the second parameter `get_post_format()` is another built-in WordPress function that returns the type of content being fetched (e.g. post, page, etc).

> This is an example of breaking up code into modular, resuable parts — this is good programming, right? Remember using partials in Handlebars? It's the same idea here.

Let's open the content template part for a page. Find the following file in the twentyseventeen folder and open it:

> `/template-parts/post/content-page.php`

And you will see the following:

```
<article id="post-<?php the_ID(); ?>" <?php post_class(); ?>>
	<header class="entry-header">
		<?php the_title( '<h1 class="entry-title">', '</h1>' ); ?>
		<?php twentyseventeen_edit_link( get_the_ID() ); ?>
	</header><!-- .entry-header -->
	<div class="entry-content">
		<?php
			the_content();
			wp_link_pages( array(
				'before' => '<div class="page-links">' . __( 'Pages:', 'twentyseventeen' ),
				'after'  => '</div>',
			) );
		?>
	</div><!-- .entry-content -->
</article><!-- #post-## -->
```

You can see a mixture of HTML (`<article>`, `<header>`, `<h1>` etc) and PHP code. This is the content that will output for each iteration of our `while` loop. Try and edit the code to see what effect it has on the page output.

**Exercise** 

* Can you output the current date after the `<header>` element using HTML?
* Can you make the date dynamic using PHP? Can you add the current time as well? HINT: Google 'PHP date' and remember, any PHP code needs to be in PHP blocks.

## WP_Query

So by now you may be thinking, that's okay but what if I wan't to fetch my own content and display it? Can we use the loop wherever we want? Can we have multiple loops on a page? For this we use WP_Query, a powerful and flexible WordPress class that allows us to use the Loop with our own options (arguments).

**Exercise** 

* Can you think of reasons why you may want to use WP_Query in your theme? Here a couple of examples, try and think of some more...
  - To fetch and display related posts to the post currently being viewed
  - To display posts from two categories at once

A typical WP_Query code block looks like this:

```
<?php 
// WP_Query arguments
$args = array(
	'post_type' => array( 'post' ), // Set the content type to 'post'
  'category_name' => 'news', // fetch posts in the news category'
	'posts_per_page' => '5', // fetch 5 posts at a time'
	'orderby' => 'rand', // order the posts randomly'
);

// The Query
$queryLatestNews = new WP_Query( $args );

// The Loop
if ( $queryLatestNews->have_posts() ) {
	while ( $queryLatestNews->have_posts() ) {
		$queryLatestNews->the_post();
		// Post Content here
	}
} else {
	echo '<p>Sorry, no posts found</p>';
}

// Restore original Post Data
wp_reset_postdata();
?>
```

First we set our arguments — in the above example we want to fetch five (`'posts_per_page'`), random (`'orderby'`) posts (`'post_type'`) in the news category (`'category_name'`). We then pass this to a new WP_Query instance and use a WordPress Loop to output the results of our query.

> Our loop also has an else statement to handle the output for when there are no results.

> The last line `wp_reset_postdata();` is important — it terminates this WP Query instance and allows to add further instances.

There are lots of available arguments you can pass to WP Query. Have a look at this code snippet and think to yourself how you could use some of these arguments in your theme:

[Arguments list for WP Query](https://gist.github.com/luetkemj/2023628)

## Resources

1.  [The Loop in Action](https://codex.wordpress.org/The_Loop_in_Action)
2.  [WP Query Codex Docs](https://codex.wordpress.org/Class_Reference/WP_Query)
3.  [Interactive WP Query code generator](https://generatewp.com/wp_query/)

## Homework

1.  **Excercise** 
2.  **Excercise** 
3.  **Excercise** 
    
## Appendix 1 PHP Quick Start

* PHP (Hypertext Preprocessor) is a widely-used, open-source server-side scripting language that is well suited to web development.
* PHP files can contain text, HTML, CSS, JavaScript, and PHP code and have a file extension ".php".
* PHP is commonly used as part of a LAMP server stack (Linux, Apache, MySQL, and PHP). MySQL is a relational database system.
* A PHP syntax block begins and ends like so:
```
<?php
// Your code here
?>
```
* Variable are declared with a dollar sign, e.g. a variable called ‘a’ with a value of 1 looks like so:
```
<?php
  $a = 1;
?>
```
* Comments in PHP look like so:
```
<?php
// This is a single-line comment

# This is also a single-line comment

/*
This is a multiple-lines comment block
that spans over multiple
lines
*/
?>
```

## Appendix 2 Quiz Answers

* A1. ‘page.php’
* A2. ‘page.php’
* A3. We need to create a ‘page-about.php’ template file
