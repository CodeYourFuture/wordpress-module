# WordPress — Pre-class introduction

The WordPress module is four weeks of classes designed to get you up and running with WordPress and learn it's various features so that you can work with your fellow students to build a WordPress site. You will use use your existing HTML, CSS and JavaScript knowledge to create a WordPress theme and plugin and we will explore the WordPress REST API to write a small React web app. 

In preperation for the first class please read the following and try and complete the exercises. If you have any problems please post a message on Slack.

**What we will learn today?**
- [What is WordPress?](#what-is-wordpress)
- [WordPress.com versus WordPress.org](#wordpresscom-versus-wordpressorg)
- [Set up your WordPress development environment](#set-up-your-wordpress-development-environment)
- [Homework](#homework)
- [Resources](#resources)

---

## What is WordPress?

WordPress is an Open Source Content Management System (CMS), released in 2003 by Matt Mullenweg and Mike Little. It was released in 2003 by Matt Mullenweg and Mike Little. As of 2018, it has 60% of the CMS marketshare and 31% of all websites, worldwide ([source](https://kinsta.com/wordpress-market-share/)). It is:

* The most popular CMS, by far
* Free to use and modify
* Easy to use
* Extendable with a wide variety of plugins and themes

Some examples of WordPress are: [Kinning Park Complex](http://www.kinningparkcomplex.org/), [Sony Music](https://www.sonymusic.com/), [Duracell Lighting](http://www.duracelllighting.com/), and [The Rolling Stones](http://www.rollingstones.com/)

> **Exercise:** Find out what a Content Management System (CMS) is. Can you find another example of a popular CMS? Can you find more examples of WordPress sites?

### WordPress.com versus WordPress.org

There are two ways you can use WordPress:

* Via [wordpress.com](https://wordpress.com/) — a massive multisite installation of WordPress owned by **Automattic**, where your site is hosted for you. It is free to use, however you are restricted from doing a lot of things (such as linking the site to your own domain or installing any plugins to extend functionality) unless you upgrade to a paid plan. 

* Via [wordpress.org](https://wordpress.org/) — where you can download WordPress to install on your own server, either via a hosting company or on your own computer. There are no restrictions whatsoever, but you are responsible for installing and setting it up.

The main concepts are the same for both. They both have Pages and Posts, Categories and Tags, a Media Gallery, a Customizer and Settings pages, etc. Even so, their Dashboards (the main screen the user sees after login) look quite different:

![screengrab of the wordpress.com dashboard](assets/lesson0/wp.com-dashboard.png)
_A screengrab of the wordpress.com dashboard._

![screengrab of the wordpress.org dashboard](assets/lesson0/wp.org-dashboard.png)
_A screengrab of the wordpress.org dashboard._

> **Exercise:** Create a blog with WordPress.com and become familiar with the key WordPress concepts. If you get stuck with any of the steps, don't worry, check the [WordPress.com support site](https://en.support.wordpress.com/) or post a question on Slack.
> 1.  Create a free account on [wordpress.com](https://wordpress.com/) and choose a name for the blog.
> 2.  Choose a Theme.
> 3.  Have a look around and try add some content — a Page, some news-style Posts. Try upload image(s) and add to your pages/posts.
> 4.  Try change some Options such as setting the site language to English UK.
> 5.  Add a menu with the following items: Home, About and Contact. "Home" should link to the main blog page and "Contact" should link to an email address.

## Set up your WordPress development environment

In order to run a basic WordPress installation, we need a few things:

- A web server, such as Apache or Nginx
- A PHP executable to run PHP code (WordPress is written in the PHP language)
- The actual WordPress source code
- A SQL database for WordPress to store our content

If you are using Windows or OSX we are going to use a local development tool calle [Flywheel](https://getflywheel.com/), a tool that makes setting up a local WordPress install really easy.

1. Watch this short intorductory video: [WordPress Development with Local by Flywheel Part 1: Getting Started](https://www.youtube.com/watch?time_continue=5&v=reOE5btJ4L0)
2. [Download and install Flywheel](https://local.getflywheel.com/) (click the 'Fee Download' button). It's quite big at around 500MB, so it may take a while.
3. Watch this video and folow the installation instructions: [WordPress Development with Local by Flywheel Part 1: Getting Started](https://www.youtube.com/watch?v=No8AGfNvUII)

---

## Homework

1. Follow the 'Set up your WordPress development environment' tutorial above and make sure you have a local WordPress development environment ready for class.
2. Login to the admin interface of your WordPress install and look around. Try replicating some of the steps you completed above for your WordPress.com account in your local install — do you notice many differences with the WordPress.com admin interface?
3. Explore and install a plugin — find the plugins section (under Plugins > Add New). Search for a 'contact form' plugin (use the Search field in the top right).
> **Don’t just install the first one in the search results** - read reviews, look at screenshots, read the installation instructions and consider what one to choose.

---

## Resources

1. [WordPress Developers Handbook - What is a Theme](https://developer.wordpress.org/themes/getting-started/what-is-a-theme/)
2. [WordPress Developers Handbook - What is a Plugin](https://developer.wordpress.org/plugins/intro/what-is-a-plugin/)
3. [Easy WP Guide WordPress Manual](https://easywpguide.com/)
4. [WordPress Codex](https://codex.wordpress.org)
5. [WordPress TV](https://wordpress.tv)
