# WordPress 0

**What we will learn today?**
- [What is Open Source?](#what-is-open-source)
- [What is WordPress? WordPress.com versus WordPress.org](#user-content-what-is-wordpress-wordpresscom-versus-wordpressorg)
- [What do WordPress developers do?](#what-do-wordpress-developers-do)
- [The WordPress working environment](#the-wordpress-working-environment) <!-- TODO Choose proper title -->
- [Homework](#homework)
---

## What is Open Source?

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

The movement has continued growing since then and nowadays there are many examples of popular Open Source software such as, for example, WordPress, Firefox, React, Python, the Apache web server and the MySQL database.

> **Exercise:** Find out more examples of Open Source software.
>
> **Exercise:** Can you think of any software that is "free" (as in you pay £0.00 for it) but would not qualify as Open Source?

If you wish to find out more on this topic, please watch the excellent documentary ["Revolution OS"](https://www.youtube.com/watch?v=4vW62KqKJ5A) on YouTube.


This section has sourced information from:
* [GNU - Free Software Definition](https://www.gnu.org/philosophy/free-sw.html)
* [Make WordPress Training - What is Open Source](https://make.wordpress.org/training/handbook/user-lessons/what-is-open-source/)
* [Opensource.com - What's the difference between open source software and free software?](https://opensource.com/article/17/11/open-source-or-free-software)


## What is WordPress? WordPress.com versus WordPress.org

WordPress is an Open Source Content Management System (CMS), released in 2003 by Matt Mullenweg and Mike Little. As of 2017, it has 59% of the CMS marketshare and 28% of all websites, worldwide.

Although WordPress started as a blogging platform, it can also be used for building websites (large and small), e-commerce sites (with the WooCommerce plugin), private community platforms (with the BuddyPress plugin), forums (with the bbPress plugin), etc.

Some examples of these could be: [Kinning Park Complex](http://www.kinningparkcomplex.org/), [Sony Music](https://www.sonymusic.com/), [Duracell Lighting](http://www.duracelllighting.com/), and [The Rolling Stones](http://www.rollingstones.com/)

The introduction of the Rest API into WordPress core a couple of years ago, has also made it possible to write web or mobile apps that links into WordPress.

> **Exercise:** Find out what a Content Management System (CMS) is. Can you find another example of a popular CMS?
>
> **Exercise:** Find more examples of WordPress sites, by type: a blog, a local business website, an e-commerce website, a news site, etc. Which is your favourite? What do you like about it?


### WordPress.com versus WordPress.org

In certain situations, there is a slight confusion about why sometimes we talk about WordPress.com and other times we say WordPress.org. Aren't they both the same?

Unfortunately, the short answer is "Yes and No"... which does not help!

So, just to set the record straight, when we talk about WordPress, we mean **WordPress.org**. The Open Source software that you can download for free from the website with the same domain name.

On the other hand, **WordPress.com** is a massive multisite installation of WordPress owned by **Automattic**, which is in turn owned by Matt Mullenweg, one of the two original WordPress developers.

So basically, WordPress.com runs WordPress and, therefore, the main concepts are the same for both. They both have Pages and Posts, Categories and Tags, a Media Gallery, a Customizer and Settings pages, etc.

Even so, their Dashboards (the main screen the user sees after login) look quite different:

![screengrab of the wordpress.com dashboard](assets/lesson0/wp.com-dashboard.png)
_A screengrab of the wordpress.com dashboard._

![screengrab of the wordpress.org dashboard](assets/lesson0/wp.org-dashboard.png)
_A screengrab of the wordpress.org dashboard._

Remember the 4 freedoms? You are free to modify the software and free to distribute the modification!

But the Dashboard is not the only difference between the two. Although WordPress.com can be free if you have a Free Plan, you are restricted from doing a lot of things unless you upgrade to a paid plan, such as, for example, linking the site to your own domain or installing any plugins to extend functionality.  

Whereas with WordPress.org there are no restrictions whatsoever, but you need to install it on your own host, with your own domain and either do the site maintenance yourself or hire someone to do it for you.

And here is where WordPress developers come in...

## What do WordPress developers do?

As an IT professional, there's several different ways of working with WordPress:

*   You can build and maintain websites for clients using, and adapting, existing WordPress **Themes** ( = collection of templates for the frontend ) and **Plugins** ( = extensions to the default WordPress functionality ).
*   You can create WordPress Themes for clients or to sell them on platforms such as the [Theme Directory](https://en-gb.wordpress.org/themes/) or the [Theme Forest](https://themeforest.net).
*   You can create WordPress Plugins for clients or to sell on the [Plugin Directory](https://en-gb.wordpress.org/plugins/).

Of course, you can also earn a living as a content editor, a blogger or a business owner with a WordPress website. But that topic is outside the scope of this course ;-)

We will cover Themes and Plugins extensively during the course but, in the meantime, if you want to find out more, please refer to the following links in the WordPress Codex:

* [WordPress Developers Handbook - What is a Theme](https://developer.wordpress.org/themes/getting-started/what-is-a-theme/)
* [WordPress Developers Handbook - What is a Plugin](https://developer.wordpress.org/plugins/intro/what-is-a-plugin/)


## The WordPress working environment

Content by Peter.

## Resources

1.  ["The Cathedral and the Bazaar" by Eric S. Raymond](http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/index.html)
2.  [WordPress Codex](https://codex.wordpress.org)
3.  [WordPress TV](https://wordpress.tv)
4.  [Resource 4 for Topic 4](https://google.com)
5.  [Resource 5 for Topic 4](https://google.com)

## Homework

1.  **Create a blog with WordPress.com** \- The objective of this exercise is to help you become familiar with the key WordPress concepts.

    1.  Create a free account on wordpress.com and choose a name for the blog.
    2.  Choose a Theme.
    3.  Add an About page and type some content. A couple of lines will be enough.
    4.  Create a new Post and type some content.
    5.  Set the site language to English UK.
    6.  Choose to show only 3 posts per page and allow comments on posts, but comments should be approved by an administrator before being displayed.
    7.  Find a Copyright-free image with an appropriate size and use it as the site's header.
    8.  Add a menu with the following items: Home, About and Contact. "Home" should link to the main blog page and "Contact" should link to an email address.

    Do as many of the tasks below as you can but don't worry if you get stuck with any of the steps. There is a lot of information in the [WordPress.com support site](https://en.support.wordpress.com/) or, if you can't find a solution there, please don't hesitate to ask us on Slack.

2.  **Setup your localhost with Docker** -
3.  **\[Bonus/Optional\]** Third part/optional - Hardest
4.  **Research:**

Prepare for the next class
--------------------------

1.  Read this [Some Tutorial or Video etc...](https://google.com)
