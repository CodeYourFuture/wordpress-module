# WordPress - Appendix

**Further Reading**
- [Child Themes](#child-themes)
- [PHP Quick Start](##php-quick-start)
- [What is Open Source? GPL and MIT Licenses](#what-is-open-source-gpl-and-mit-licenses)
---

## Child Themes

A **Child Theme** is a theme that inherits layout, styling and functionality from another Theme, called the **parent theme**. You would create a Child Theme when you wish to make permanent changes to the parent theme's template files or stylesheet.

Let's demonstrate this with an exercise:

> Before the exercise: For the sake of demonstrating what happens when we make changes to a parent theme, we will swap our current version of the `twentyseventeen` theme for an older one.
> 1. Download version 1.0 from its [github repository](https://github.com/WordPress/twentyseventeen)
> 2. Move it to your local site's `wp-content/themes` folder, overriding the existing folder with the same name.
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

This is the reason why we don't make changes directly to a Theme, but create a Child Theme instead. A Child Theme inherits everything from its parent theme and overrides what it wishes to change.

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

4. Now that you have a Child Theme, go to your website's Dashboard > Appearance > Themes. Can you see it listed with the others? Hover the mouse over the Child Theme box and click the `Description` button. Can you find the text you typed earlier?

5. Activate the Child Theme and have a look at the website. What changes can you see?

> Exercise: Now it's time to change the main header title's font to "Limelight" again, but this time from the Child Theme as it should be. Try to work out how to do it by yourself and only ask for help from the mentors if you haven't found the solution elsewhere.
>
> Exercise:  Have a look at Q3 at the bottom of the [Template Hierarchy](#the-template-hierarchy) section. We now want to make sure that our new Child Theme has a super special `About` page.
> 1. Before you start, make sure you have a page called `About`. Add a photo and a couple of paragraphs of text in its content.
> 2. We want the page title to be all caps and a nice bright colour. We also want the photo to float to the left and have a right padding of 1em. We don't want any styling changes inline! In which file should you make them instead?
> 3. Now we want to add a special section just below the page content. This section will have a pale yellow background, a padding of 3em and some centered text saying "Get in touch!". This text should link to your email. In which file should you make the changes?



## PHP Quick Start

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


According to the [PHP Manual](http://php.net/manual/en/intro-whatis.php):

> PHP (recursive acronym for PHP: Hypertext Preprocessor) is a widely-used open source general-purpose scripting language that is especially suited for web development and can be embedded into HTML.

The WordPress core is written in PHP and so are the WordPress Themes and Plugins, at least partly. You can see how PHP interacts with HTML in the `twentyseventeen/page.php` Theme template:

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

Even though the bulk of WordPress core is in PHP, the newest additions to WordPress have been written in Backbone (the new Customizer) and React (the Gutenberg editor) as it slowly starts to move towards Javascript.


## What is Open Source? GPL and MIT Licenses

In 1984, Richard Stallman launched the **GNU Project** and created the **General Public License** (GPL) as a response to his increasing unhappiness with proprietary software, vendor lock-in practices and the resulting loss of personal freedom, as he saw it.

> "When users don't control the program, we call it 'nonfree' or 'proprietary' software. The nonfree program controls the users, and the developer controls the program; this makes the program an instrument of unjust power."
> - Richard Stallman, [The Free Software Definition](https://www.gnu.org/philosophy/free-sw.html)

This marked the birth of **Free Software**, by which software is considered free if it respects the 4 fundamental freedoms:

1. Anyone has the freedom to run the software as they wish, for any purpose
2. Anyone has the freedom to study how the program works, and change it as they wish
3. Anyone has the freedom to redistribute the software
4. Anyone has the freedom to distribute copies of their own modified version of the Software

As a consequence, access to the code must be open and all 3rd party software needed to run it must also comply with the 4 fundamental freedoms.

A few years later, in 1997, Eric Raymond wrote an essay called **"The Cathedral and the Bazaar"**, in which he described how the Linux operating system and the Free Software philosophy had created a surprisingly effective and collaborative way of writing software.

This set the stage for the appearance, one year later, of the term **Open Source** software. Open Source software is a close relative of Free Software but with a stronger focus on the methodology rather than the philosophy.

The movement has continued growing since then and nowadays there are many examples of popular Open Source software such as, for example, WordPress, Firefox, React, Python, Node, the Apache and NGINX web servers, just to mention a few.

For example, Node Package Manager is a system for distributing open source code. When someone writes `npm install XXX` they are taking advantage of a vast ecosystem of open source code.

### Copyleft, GPL and MIT

**Copyleft** is a method for making a program compliant with the 4 freedoms of Free Software, and requiring that all modified and extended versions of the program also be compliant.

According to the GNU Project:

> Certain kinds of rules about the manner of distributing free software are acceptable, when they don't conflict with the central freedoms. For example, copyleft (very simply stated) is the rule that when redistributing the program, you cannot add restrictions to deny other people the central freedoms.
>
> Copyleft also provides an incentive for other programmers to add to free software [...] and helps programmers who want to contribute improvements to Free Software get permission to do so.

This Copyleft rule translates into the **General Public License (GPL) Licence** for distribution with the Open Source software in question.

The **MIT License** is another popular Open Source software license that was originally developed at the Massachusetts Institute of Technology. Unlike the GPL, the only requirement an MIT license places on its recipients is that they keep the original copyright notice intact when they repurpose, redistribute, or otherwise reuse the code.

> "Copyright <YEAR> <COPYRIGHT HOLDER>
>
> Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
>
> The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE."
>
> The MIT License, from [The Open Source Initiative website](https://opensource.org/licenses/MIT)

In practical terms, the main difference is that GPL says that if you use my GPL code in your released code, you must also release your code under the GPL or something similar. MIT is very similar to GPL except that if you use my GPL code in your released code, you're allowed to license your part of the code in other non-Open Source ways.

So GPL "coerces" Open Source on anything that uses it whereas MIT is more flexible. There are good reasons for using both and many amongst the WordPress core developers are very committed to the coercive nature of GPL. But many big companies are suspicious of it.

If you wish to find out more about Free Software, Open Source and licensing, please watch the excellent documentary ["Revolution OS"](https://www.youtube.com/watch?v=4vW62KqKJ5A) on YouTube.

These sections have been sourced from:
* [GNU - Free Software Definition](https://www.gnu.org/philosophy/free-sw.html)
* [GNU - What is Copyleft?](https://www.gnu.org/copyleft/copyleft.html)
* [Make WordPress Training - What is Open Source](https://make.wordpress.org/training/handbook/user-lessons/what-is-open-source/)
* [Opensource.com - What's the difference between open source software and free software?](https://opensource.com/article/17/11/open-source-or-free-software)
