# WordPress Lesson 1

**What we will learn today?**
- [Basic Concepts](#basic-concepts)
- [WordPress Backend and Folder Structure](#wordpress-backend-and-folder-structure)
- [The Template Hierarchy](#the-template-hierarchy)
- [Child Themes](#child-themes)
- [The WordPress Loop](#the-Wordpress-loop)
- [Homework](#homework)
---

**Before we begin...**

* You should have finished a pre-class lesson that showed you how to set up a local installation of WordPress on your machine using Docker? Let the mentors know if you have not completed this yet.
* WordPress uses the PHP programming language. This module is not designed to teach you PHP. However, although the syntax is a little different, you will be able to use what you have learned so far in JavaScript (such as variables, functions, arrays, conditional statements and so on) to help you. See [PHP Quick Start](#appendix-1-php-quick-start) in the appendix for a short overview of what is different.

## Basic Concepts

**Before we start, we would like to point out that, from now on, when we talk about WordPress we mean WordPress.org**.

This section will be 100% hands on and we will learn the key WordPress terms and concepts by using them. To achieve this, we will work with the local WordPress installation from [Lesson0](https://github.com/CodeYourFuture/wordpress-module/blob/master/lesson0.md)'s exercises.

Concept | What is it? | When or where do we use it?
--------|-------------|----------------------------
Page | |
Post | |
Category | |
Tag | |
Comment | |
Widget | |
Plugin | |
Theme | |

> Exercise: Using your own words, fill the gaps in the table above. Give examples if necessary.

### Media

WordPress allows you to upload the following Media types onto your site:

Media | Formats allowed
------|-----------------
Images | .jpg .jpeg .png .gif .ico
Video | .mp4 .m4v (MPEG-4) .mov (QuickTime) .wmv (Windows Media Video) .avi .mpg .ogv (Ogg) .3gp (3GPP) .3g2 (3GPP2)
Audio | .mp3 .m4a .ogg .wav
Other | .pdf

The maximum file size allowed will vary depending on the website hosting provider. It is important, though, to keep in mind that big image file sizes are often the key factor in slowing down a website.

> Exercise: Open Google's [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) page and run the test for these two websites: [Iceland](http://iceland.co.uk/) and [Argos](http://www.argos.co.uk/)
> How do they compare? Have a look at Google's **Optimisation Recommendations** for both. What type of improvements do they highlight?

Video and Audio can also be embedded major platforms, such as YouTube and Vimeo, simply by copying and pasting the URL onto the page or post content. This can be useful if the file sizes are large.

Some widgets facilitate the inclusion of Media in other parts of the website, such as the sidebar or the footer. Also, some themes allow Media in other parts of the website, such as the header.

All media files uploaded onto the site can be viewed (and their settings edited) from the **Media Gallery**.

> Exercise: Upload or embed different types of Media inside one of your posts of pages: Images, Video and Audio.
> What is the difference between image Title, Caption, Alt Text and Description? Are they always needed? Why?
>
> Exercise: Use 4 or 5 images to create an image gallery. Try out the different options that come with WordPress by default, for example different image sizes, alignments and links.
> Is there anything you'd like to do with the Gallery but can't?

### Settings, Customizer, and Tools

> Exercise: Log into your local WordPress website and have a look at the various options in the **Settings menu**. If you haven't done so yet, do tasks v and vi from Lesson 0's first [Homework](https://github.com/CodeYourFuture/wordpress-module/blob/carmemias-lesson1/lesson0.md#homework) exercise.
> Now have a look at the Settings > Permalinks section. What do you think it does?
>
> Exercise: Now go open the **Customizer**. If your theme allows it, add a video to the Home page header and change the background colour and title font.
> Are the widgets here the same as the widgets we looked at earlier? How about the menus? Make changes to either of them here and see if they show in the other Widgets/Menu page.
>
> Exercise: Look at the **Tools menu** > **Import** and **Export** options. In which situations do you think they would be useful?
> Export the content of your exercise website onto a file. Swap files with the person sitting next to you. Import each other's content. Why do you think we are made to choose a user name? Would you always want to import the images? Why?

### Users and Roles

Read what the **WordPress Codex** says about [User Roles](https://codex.wordpress.org/Roles_and_Capabilities)

> Exercise: Have a look at the [New Yorker](https://www.newyorker.com/)'s WordPress website. Which user roles do you think they use? Why?

## WordPress Backend and Folder Structure

To run a WordPress website, we need a web hosting package with PHP and one [MySQL](https://dev.mysql.com/) database.

### Brief introduction to the MySQL database

**MySQL** is an Open Source **relational** database. In a relational database, data is grouped in tables according to what they represent. Each table has at least two columns, the first of which is always a unique id number. Each row represents a data entry.

For example, in WordPress, there a table for posts (normally called `wp_posts`) with columns such as: ID, post_author, post_date, post_content, post_title, post_status, etc.

Example `wp_posts`:

ID | post_author | post_date | post_content | post_title | post_status
---|-------------|-----------|--------------|------------|------------
1 | 1 | 2017-06-07 10:05:32 | Welcome to WordPress. This is your... | Hello world! | publish
2 | 1 | 2017-06-08 17:47:50 | Repository-hosted Themes are re... | My opinion on Themes | publish

And another table for users (normally called `wp_users`) with columns such as ID, user_login, user_email, user_pass (it's content is encrypted), display_name, etc.

Example `wp_users`:

ID | user_login | user_email | user_pass | display_name
---|------------|------------|-----------|-------------
1 | lance | lance@gmail.com | $P$BSpbh5H3XbtH | Lance Smith

Notice that the `post_author` column in the `wp_posts` table contains an integer instead of a name. This corresponds to the value in the `wp_users` `ID` column corresponding to the post author. The tables `wp_posts` and `wp_users` "relate" (or are connected) to each other via that unique user ID.

### PHP

According to the [PHP Manual](http://php.net/manual/en/intro-whatis.php):

> PHP (recursive acronym for PHP: Hypertext Preprocessor) is a widely-used open source general-purpose scripting language that is especially suited for web development and can be embedded into HTML.

The WordPress core is written in PHP and so are WordPress Themes and Plugins, at least partly. You can see how PHP interacts with HTML in the `twentyseventeen/page.php` Theme template:

```php
<?php
/**
 * The template for displaying all pages
 */

get_header(); ?>

<div class="wrap">
	<div id="primary" class="content-area">
		<main id="main" class="site-main" role="main">

			<?php
			while ( have_posts() ) : the_post();

				get_template_part( 'template-parts/page/content', 'page' );

				// If comments are open or we have at least one comment, load up the comment template.
				if ( comments_open() || get_comments_number() ) :
					comments_template();
				endif;

			endwhile; // End of the loop.
			?>

		</main><!-- #main -->
	</div><!-- #primary -->
</div><!-- .wrap -->

<?php get_footer(); ?>
```

All code between the `<?php ... ?>` tags is PHP, the rest is HTML.

> Exercise: Have a look at the example code above and compare it with the source code of one of your own WordPress site pages. Try to work out what the WordPress PHP code does.

Even though the bulk of WordPress core is in PHP, the newest additions to WordPress have been written in Backbone (the new Customizer) and React (the Gutenberg editor) as it slowly starts to move towards Javascript.

We will look in more detail at Themes and template files later on today.

### WordPress Folder Structure

We will have a look at the WordPress folder structure together in class and explain what goes where.

> Exercise: If you haven't done so yet, [download WordPress](https://wordpress.org) and unzip the file.

## The Template Hierarchy

Whether you are building your own theme, or modifying someone else’s with a child theme (explained later), you will have to understand the WordPress Template Hierarchy. This is the name given to the way WordPress chooses what template file in the current theme to use for each URI (or path) your user visits on your site — what one to use on the home page, the about page, search results page, 404 page and so on.

  > Do you remember when working with node.js you had to deal with routing in your code? WordPress is slightly different — it maps the URI to a template file(s) in your theme based on the rules of the Template Hierarchy.

The choice of template file that WordPress makes can be visualised with the following image representing the Template Hierarchy:

![Visualisation of the Template Hierarchy](assets/lesson1/wp-hierarchy.png)

**<a href="https://developer.wordpress.org/files/2014/10/wp-hierarchy.png" target="_blank">View a larger version**</a>

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

A **Child Theme** is a theme that inherits layout, styling and functionality from another Theme, called the **parent theme**. You would create a Child Theme when you wish to make permanent changes to the parent theme's template files or stylesheet.

Let's demonstrate this with an exercise:

> Before the exercise: For the sake of demonstrating what happens when we make changes to a parent theme, we will swap our current version of the `twentyseventeen` theme for an older one.
> 1. Download version 1.0 from its [github repository](https://github.com/WordPress/twentyseventeen)
> 2. move it to your local site's `wp-content/themes` folder, overriding the existing folder with the same name.
> 3. Double check that `twentyseventeen` is the active Theme on your site.
>
> Exercise: We will now change the main header title's font to "Limelight", which you can find in [Google Fonts](https://fonts.google.com). These are the steps to follow:
> 1. Read the Google Fonts instructions on how to set the font to "Limelight". Notice that you will need to make changes in two different places.
> 2. Use the browser's developer tools to find out the class and/or id of the title html element.
> 2. Find out the css rule that sets the title's font family.
> 3. Identify which theme files you will need to make the changes indicated in Google Fonts.  
> 4. Make the changes directly in the theme files and open the page in the browser. The title should now show in the new font!
>
> 5. Now, notice the Dashboard notice telling you there is an update for your theme. Run the update so that your Theme now has the latest version.
> 6. Have a look at the website again. What happened to the header font? Yes, that's right, because the Theme has been updated, **all our changes have been overriden and are now lost**.

This is the reason why don't make changes directly to a Theme, but create a Child Theme instead. A Child Theme inherits everything from its parent theme and overrides what it wishes to change.

Let's do it with our example exercise. First of all, follow these steps to create a Child Theme:
1. Open your website's `wp-content/themes` folder and create a new folder. In this example we will call the folder `twentyseventeen-child` but you call it anything you like, just make sure there are no spaces or special characters in the name.
2. Add a new file called `style.css` and paste the following text in it:
```css
/*
 Theme Name:   My First Child Theme
 Theme URI:    http://mywebsite.com/my-first-child-theme/
 Description:  A Description for your Theme. This is the text that shows in Dashboard > Appearance > Themes
 Author:       Your Name
 Author URI:   http://mywebsite.com
 Template:     twentyseventeen
 Version:      1.0.0
 License:      GNU General Public License v2 or later
 License URI:  http://www.gnu.org/licenses/gpl-2.0.html
 Tags:         light, dark, two-columns, right-sidebar, responsive-layout, accessibility-ready
 Text Domain:  twentyseventeen-child
*/
```
   We type the parent theme's folder name by the `Template` attribute and the Child Theme's folder name by `Text Domain`.
3. Add a new file called `functions.php` to the child theme folder and paste the following text in it:
```PHP
<?php
function my_child_theme_enqueue_styles() {

    wp_enqueue_style( 'parent-style', get_template_directory_uri() . '/style.css' );
    wp_enqueue_style( 'child-style',
        get_stylesheet_directory_uri() . '/style.css',
        array( 'parent-style' ),
        wp_get_theme()->get('Version')
    );
}
add_action( 'wp_enqueue_scripts', 'my_child_theme_enqueue_styles' );
?>
```
   The code above first loads the parent theme's stylesheet, and then loads the Child Theme's stylesheet. Thus, the Child Theme's CSS rules override those of the parent theme when applied to the same element, class or id.

4. Now that you have a Child Theme, go to your website's Dashboard > Appearance > Themes. Can you see it listed with the others? Hover the mouse over the Child Theme box and click the `Description` button. can you find the text you typed earlier?

> Exercise: Now it's time to change the main header title's font to "Limelight" again. You should be able to work out how to do it by yourself.
>
> Exercise:  Have a look at Q3 at the bottom of the [Template Hierarchy](#the-template-hierarchy) section. We now want to make sure that our new Child Theme makes the `About` page look different from the other pages.
> 1. Before you start, make sure you have a page called `About` ;-) and that it has a photo and a couple of paragraphs of text in it.
> 2. We want the page title to be all caps and a nice bright colour. We also want the photo to float to the left and have a right padding of 1em. Do not make the styling changes inline! In which file should you make them instead?
> 3. Now we want to add a special section just below the page content. This section will have a pale yellow background, a padding of 3em and some centered text saying "Get in touch!". This text should link to your email. In which file should you make the changes?

To find out more about the Child Themes or the WordPress functions used in the code above, please refer to the [WordPress Codex](https://codex.wordpress.org).

## The WordPress Loop

Para

## Resources

1.  [One](https://example.com/)
2.  [Two](https://example.com/)
3.  [Three](https://example.com/)

## Homework

1.  **Exercise**: Change your site's theme to `Simppeli`. Are all website settings kept? and how about the customisations? Do you have as much choice as with the `twentyseventeen` theme?
2.  **Exercise**
3.  **Exercise**

## Appendix 1 PHP Quick Start

## Appendix 2 Quiz Answers

* A1. ‘page.php’
* A2. ‘page.php’
* A3. We need to create a ‘page-about.php’ template file
