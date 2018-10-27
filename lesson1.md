# WordPress Lesson 1

**What we will learn today?**
- [Basic Concepts](#basic-concepts)
  - [Media](#media)
  - [Settings, Customiser and Tools](#settings-customiser-and-tools)
  - [Users and Roles](#users-and-roles)
- [The Course Project](#the-course-project)
- [Homework](#homework)
---

**Before we begin...**

* You should have finished a pre-class lesson that showed you how to set up a local installation of WordPress on your machine. Let the mentors if there have been any problems completing this.

* WordPress uses the PHP programming language. This module is not designed to teach you PHP. However, although the syntax is a little different, you will be able to use what you have learned so far in JavaScript (such as variables, functions, arrays, conditional statements and so on) to help you. 

## Basic Concepts

**Before we start, we would like to point out that, from now on, when we talk about WordPress we mean WordPress.org**.

To log into your local WordPress install. Use the username and password you typed in during the 5-minute installation process.

In this section we will learn the key WordPress terms and concepts by using them, in a 100% hands-on way, with the local WordPress installation from [Lesson0](https://github.com/CodeYourFuture/wordpress-module/blob/master/lesson0.md)'s exercises.

> Exercise: Using your own words, fill the gaps in the table below. Give examples if necessary.
>
> Key Concept | What is it? | When or where do we use it?
> --------|-------------|----------------------------
> Page | |
> Post | |
> Category | |
> Tag | |
> Comment | |
> Widget | |
> Plugin | |
> Theme | |

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

Video and Audio can also be embedded from major platforms such as YouTube and Vimeo. Simply copy and paste the URL onto the page or post content. This can be useful if the file sizes are large.

Some widgets facilitate the inclusion of Media in other parts of the website, such as the sidebar or the footer. Also, some themes allow Media in other parts of the website, such as the header.

All media files uploaded onto the site can be viewed (and their settings edited) from the **Media Gallery**.

> Exercise: Upload or embed different types of Media inside one of your posts of pages: Images, Video and Audio.
> What is the difference between image Title, Caption, Alt Text and Description? Are they always needed? Why?
>
> Exercise: Use 4 or 5 images to create an image gallery. Try out the different options that come with WordPress by default, for example different image sizes, alignments and links.
> Is there anything you'd like to do with the Gallery but can't?

### Settings, Customizer, and Tools

> Exercise: Log into your local WordPress website and have a look at the various options in the **Settings menu**. 
> Now have a look at the Settings > Permalinks section. What do you think it does?
>
> Exercise: Now open the **Customizer**. If your theme allows it, add a video to the Home page header and change the background colour and title font.
> What else can you change?
> Are the widgets here the same as the widgets in Dashboard > Appearance > Widgets? How about the menus? Make changes to either of them here and see if they show in the other Widgets/Menu page.
>
> Exercise: Look at the **Tools menu** > **Import** and **Export** options. In which situations do you think they would be useful?
> Export the content of your exercise website onto a file. Swap files with the person sitting next to you. Import each other's content. Why do you think we are made to choose a user name? Would you always want to import the images? Why?

### Users and Roles

Read what the **WordPress Codex** says about [User Roles](https://codex.wordpress.org/Roles_and_Capabilities).

> Exercise: Have a look at the [New Yorker](https://www.newyorker.com/)'s WordPress website. Which user roles do you think they use? Why?

## The Course Project

Throughout this WordPress module, we will use the exercises to build a website. We will start with a very basic theme and improve it as we go along.

To start with, please read the [project description](/group-project.md) and then come back here to do the exercises:

> Exercise: Download the [Minimalist theme](https://github.com/carmemias/minimalist-theme), install and activate it in your local WordPress install.

> Exercise: If the WordPress core version is less than 5.0.0., install the Gutenberg plugin.

> Exercise: Create the pages (`Home`, `About Us`, `Contact Us` and also a `Blog` page), 2 posts for the blog and a menu. Add useful widgets to the sidebar.

> Exercise: Add a form to the `Contact Us` page. find several plugins to choose from and decide which one you should use. Be prepared to discuss your choice with the class. We want to hear what you looked for and all pros and cons of your choice.

> Exercise: Which other plugins do you think we **should** have and why?
