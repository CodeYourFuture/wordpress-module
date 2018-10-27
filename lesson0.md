# WordPress — Pre-class introduction

The WordPress module is four weeks of classes designed to get you up and running with WordPress and learn its various features so that you can work with your fellow students to build a WordPress site. You will use use your existing HTML, CSS and JavaScript knowledge to create a WordPress theme and plugin and we will explore the WordPress REST API to write a small React web app.

=======

In preparation for the first class please read the following and try and complete the exercises. If you have any problems please post a message on Slack.

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

If you are using Windows or OSX we are going to use a local development tool called [Flywheel](https://getflywheel.com/), a tool that makes setting up a local WordPress install really easy.

1. Watch this short introductory video: [WordPress Development with Local by Flywheel Part 1: Getting Started](https://www.youtube.com/watch?time_continue=5&v=reOE5btJ4L0)
2. [Download and install Flywheel](https://local.getflywheel.com/) (click the 'Free Download' button). It's quite big at around 500MB, so it may take a while.
3. Watch this video and follow the installation instructions: [WordPress Development with Local by Flywheel Part 2: Installing a Local WordPress Site](https://www.youtube.com/watch?v=No8AGfNvUII)

> Make a note of the 'Local site path' location, this is where WordPress is installed and you will be editing some of these files later.
> Make a note of your username and password, you will use these to login to your WordPress installation.

### On Ubuntu
_NB. If you are using Windows or OSX please skip this._

If you are using Ubuntu there aren't many out-of-the-box development environments for WordPress. This means that getting up and running requires a few extra manual steps.

#### 3. Create a MySQL database
Installing a MySQL server on Ubuntu requires a little bit of extra work, which is why we recommend that you instead sign up for a free MySQL database on https://db4free.net/. The service is free but the database you get is very slow. If you like tinkering around and want a faster database feel free to [try installing MySQL on your own machine](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04) - ask for help if you get stuck.

#### 2. Install PHP
Installing PHP on Ubuntu can be done using the `apt-get` tool. Fire up the Terminal app and type in:
```bash
sudo apt-get install php-cli php-mysql
```

This will install PHP and the PHP / MySQL driver.

#### 3. Install WordPress
In order to install WordPress you need the WordPress PHP files. You can download them directly from the Terminal with this command:

```bash
wget http://wordpress.org/latest.tar.gz
```

Once WordPress has been downloaded, you can unzip the files with the following command:

```bash
tar -xzvf latest.tar.gz
```

This will create a folder named "wordpress" on your machine. Feel free to rename this folder to the name of your website.

#### 4. Run WordPress
In order to run your WordPress website with PHP, you can use the built-in PHP server. Navigate in to your WordPress folder (from step 3) and run the following command in Terminal:

```bash
cd [FOLDER NAME HERE]
php -S localhost:8080
```

This will start the PHP server on port 8080. You can now navigate to http://localhost:8080 to access your WordPress site.

During the installation wizard you are asked to provide the database settings from DB4Free (step 1). Use whatever you selected back in step 1 and use `db4free.net` for the "host". After completing the installation wizard, you WordPress site is ready to go.

---

## Homework

1. Follow the 'Set up your WordPress development environment' tutorial above and make sure you have a local WordPress development environment ready for class.
2. Login to the admin interface of your WordPress install and look around. Try replicating some of the steps you completed above for your WordPress.com account in your local install — do you notice many differences with the WordPress.com admin interface?
3. Explore and install a plugin — find the plugins section (under Plugins > Add New). Search for a 'contact form' plugin (use the Search field in the top right).
> **Don’t just install the first one in the search results** - read reviews, look at screenshots, read the installation instructions and consider which one to choose.

---

## Resources

1. [WordPress Developers Handbook - What is a Theme](https://developer.wordpress.org/themes/getting-started/what-is-a-theme/)
2. [WordPress Developers Handbook - What is a Plugin](https://developer.wordpress.org/plugins/intro/what-is-a-plugin/)
3. [Easy WP Guide WordPress Manual](https://easywpguide.com/)
4. [WordPress Codex](https://codex.wordpress.org)
5. [WordPress TV](https://wordpress.tv)
