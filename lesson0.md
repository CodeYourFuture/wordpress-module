# WordPress 0
** What we will learn today?**
- [What is Open Source?](#what-is-open-source)
- [What is WordPress? WordPress.com versus WordPress.org](#what-is-wordPress-wordpress.com-versus-wordpress.org)
- [What do WordPress developers do?](#what-do-wordpress-developers-do)
- [The WordPress working environment](#the-wordpress-working-environment) <!-- TODO Choose proper title -->
- [Homework](#homework)
---

## What is Open Source?

A brief summary of the philosophy behind Open Source. Probably with a link to the video recommended by ? in Slack.

## What is WordPress? WordPress.com versus WordPress.org

### What is WordPress

Include the following points:

*   It's an Open Source Content Management System (CMS)
*   How it started and by whom.
*   Market share
*   Its uses (blog, simple website, large website, multisite, e-commerce, , etc) with examples.

> **Exercise 1:** Find out what a Content Management System is.
> 
> **Exercise 2:** Find more examples of WordPress sites, by type: a blog, a local business website, an e-commerce website, a news site, etc. Which is your favourite? What do you like about it?

### WordPress.com versus WordPress.org

Include the following points:

*   When we say WordPress, we mean WordPress.org
*   WordPress.com = hosted multisite install, run by Automattic, owned by Matt Mullenberg
*   Interaction/relationship between the two

Although the Dashboards look quite different, the key concepts (pages, posts, themes, customizer, settings, media gallery, etc.) are the same.

![screengrab of the wordpress.com dashboard](assets/lesson0/wp.com-dashboard.png)

_A screengrab of the wordpress.com dashboard._

![screengrab of the wordpress.org dashboard](assets/lesson0/wp.org-dashboard.png)

_A screengrab of the wordpress.org dashboard._

## What do WordPress developers do?

As an IT professional, there's different ways of working with WordPress:

*   You can build websites for clients using, and adapting, existing WordPress Themes (=templates) and Plugins (=extensions to the default WordPress functionality).
*   You can create WordPress Themes for clients or to sell on platforms such as the Theme Repository or the Theme Forest.
*   You can create WordPress Plugins for clients or to sell on the Plugin Repository.

We will cover Themes and Plugins extensively during the course but, in the meantime, if you want to find out more, you can read these two articles:

Of course, you can also earn a living as a content editor, a blogger or a business owner with a WordPress website. But that'd be outside the scope of this course ;-)

## The WordPress working environment

_This tutorial is based on my [original blog post](https://wptavern.com/composing-a-wordpress-development-environment-with-docker) on The WordPress Tavern._

**If you don't care about what Docker is for now, feel free to jump to the part where we actually [spin up a WordPress Docker container](https://gist.github.com/petersuhm/086753a461a37bae7b33185eebecbaaf#hello-wordpress).**

In the last few years, a wave of virtualization technologies have swept through our WordPress development environments. The one that has sounded the most promising to me has been Docker: lightweight and flexible. Yet, until recently, getting Docker up and running was an overwhelming task – especially on a non-Linux machine. Getting Docker to work required running it inside of a virtual Linux machine and configuring stuff like port forwarding and other parts of the network yourself.

Let's take a quick break and explain what a virtual machine is: Different kinds of software requires different operating systems to run. If you want to run a Windows program on a Mac computer, you can install a virtual Windows machine on your Mac. When we do web development, most of our software will be running on servers using the Linux operating system. Therefore, it is beneficial for us to utilise virtual machines to run Linux on our development machines as well. The more we can replicate the environment where our code will eventually be running, the less uncomfortable errors we will probably encounter. Historically, using virtual machines have had 2 main obstacles: 1. they are really slow and resource intensive - especially if you run a few of them at the same time. If you run 3 virtual machines with Linux, your computer's hardware is actually running 4 computers worth of operating systems all at once. 2. configuring the network is not very easy. If you go to `localhost` in your browser, is it _your_ `localhost` or the virtual machine's `localhost`? The answer is "it depends"!

Btw. if your computer is already running Linux, using Docker is still preferable, but we will get to that later.

Now it’s different.

With (a stable) Docker for Mac and Windows and Docker Compose at hand, getting Docker up and running is easy and pain-free. With Docker Compose you can tell Docker exactly what you want your WordPress development environment to look like and it will take care of it.

### What goes into a WordPress development environment?

In order to run a basic WordPress installation, we need a few things:

- A web server, such as Apache or Nginx
- A PHP executable to run PHP code (WordPress is written in the PHP language)
- The actual WordPress source code
- A SQL database for WordPress to store our content

Thankfully, most of this has been taken care of for us when we use Docker.

### What is Docker?

Docker is a technology that makes it really simple to create isolated containers for your applications and websites to run in. These containers can be combined and modified to fit the needs of your applications. Docker is utilizing the Linux Containers technology (LXC) where multiple isolated environments can share the same Linux kernel. Think of a Docker container as a very lightweight virtual machine. This basically means that you can have separate "virtual machines" for all your different projects, but sharing the same operating system behind the scenes.

The Docker ecosystem is built around these containers. In the [Docker Hub](https://hub.docker.com/), you can find an endless number of containers that other people have built, including containers with WordPress already installed, or you can build your own using a Dockerfile.

### What is Docker Compose?

Docker Compose is what makes Docker available to mortals like you and me. As the name implies, Docker Compose is a tool for composing Docker containers. That means defining your services (containers), setting up the network between them, sharing local directories with them, and a few more things.

With Docker Compose you create a simple file in the root of your project that describes the setup required by your application/website. For a WordPress theme that might mean a container to run WordPress, a container to run MySQL and a container to run NPM.

### Hello WordPress!

Okay, it's time to get the ball rolling. First of all, you need Docker installed on your computer. So please go ahead and install Docker CE (community edition):

* [Mac](https://www.docker.com/docker-mac)
* [Ubuntu](https://www.docker.com/docker-ubuntu)
* [Windows](https://www.docker.com/docker-windows)

The process should be fairly straightforward.

Next thing, create a folder somewhere on your machine and name it something "my-wordpress-site". In Terminal:

```bash
$ mkdir my-wordpress-site
```

Next, we are ready to create our `docker-compose.yml` config file. This is actually all we need to spin up a WordPress site inside of a Docker container. Here's how a very basic `docker-compose.yml` file could look:

```yaml
version: '2'

services:
  db:
    image: mysql:5.7
    ports:
      - "3306:3306"
    volumes:
      - my_wp_site_db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: wordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: secret

  wordpress:
    depends_on:
      - db
    image: wordpress:php5.6-apache
    ports:
      - "80:80"
    volumes:
      - my_wp_site_wp_content:/var/www/html/wp-content
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_PASSWORD: wordpress

volumes:
  my_wp_site_db_data:
    driver: "local"
  my_wp_site_wp_content:
    driver: "local"
```

You can copy and paste the file content into a file called `docker-compose.yml` inside of the "my-wordpress-site" folder.

Try to run `docker-compose up -d` in your Terminal to spin up the WordPress environment. If all goes well, you should see something like this:

```bash
Creating network "wordpressdockerexample_default" with the default driver
Creating volume "wordpressdockerexample_my_wp_site_wp_content" with local driver
Creating wordpressdockerexample_db_1 ...
Creating wordpressdockerexample_db_1 ... done
Creating wordpressdockerexample_wordpress_1 ...
Creating wordpressdockerexample_wordpress_1 ... done
```

Go visit http://localhost in your browser and you will be presented with the famous 5-minute installation of WordPress. That should be fairly self-explaining and after doing that your WordPress site is up and running.

If you want to see which Docker containers are running, you can always run `docker ps`:

```bash
$ docker ps

CONTAINER ID        IMAGE                     PORTS
457c48ca8328        wordpress:php5.6-apache   0.0.0.0:80->80/tcp       ...
e77876ff7ac2        mysql:5.7                 0.0.0.0:3306->3306/tcp   ...
```

And finally if you want to stop your containers, you can simply run `docker-compose down`.

If you want to understand what's in the `docker-compose.yml` file, feel free to have a look at Appendix 2 - however, this is by no means required reading.

------

_**Troubleshooting:** The part that usually goes wrong here is the port forwarding. Going to http://localhost in your browser is the same thing as going to http://localhost:80 AKA port 80 on your local host. If something else is already running on port 80 (ie. you have another web server installed locally) you will need to change the file to use another port:_

```yml
ports:
  - "80:8888"
```

_The same goes with the database if you already have MySQL running on port 3306 locally._

### Working with plugins and themes in our container

If you want to develop your own WordPress plugin or theme you can bundle this WordPress environment with your project. Let's say you want to work on a WordPress plugin called "My Awesome WP Plugin", first create a folder for your plugin:

```bash
$ mkdir my-awesome-wp-plugin
```

Next, copy and paste the `docker-compose.yml` into the project folder. You then need to add an extra line to the `volumes` section of the `wordpress` service:

```yml
volumes:
  - my_wp_site_wp_content:/var/www/html/wp-content
  - .:/var/www/html/wp-content/plugins/my-awesome-wp-plugin/ # add this line
```

Can you guess what that line does? It maps the current directory on your local machine (represented by a ".") to a folder named "my-awesome-wp-plugin" inside of the Docker container. The "my-awesome-wp-plugin" folder will be located inside of the "/wp-content/plugins" folder, which is where WordPress looks for plugin files.

If you are working on a WordPress theme instead, the process will be exactly the same, only the folder will be inside of "/wp-content/themes" instead.

## Resources

1.  [Easy WP Guide WordPress Manual](https://easywpguide.com/)
2.  [WordPress Codex](https://codex.wordpress.org)
3.  [WordPress TV](https://wordpress.tv)
4.  ["The Cathedral and the Bazaar" by Eric S. Raymond](http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/index.html)

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
    
    Do as many of the tasks below as you can but don't worry if you get stuck with any of the steps. There is a lot of information in the [WordPress.com support site](https://en.support.wordpress.com/) or, if you can't find a solution there, please ask on Slack.
    
2.  **Setup your localhost with Docker**
    1.  Follow the Docker tutorial above and make sure you have a local WordPress development environment ready for class.
    2.  Once you have succesfully set it up post an update on Slack, or ask for help if you are struggling to complete
    3.  Login to the admin interface of your Docker WordPress install and look around. Try replicating some of the steps you completed above for your WordPress.com account in your Docker install — do you notice many differences with the WordPress.com admin interface?
3.  **Explore and install a plugin**
    1. Find the plugins section (under Plugins > Add New). Search for a 'contact form' plugin (use the Search field in the top right).

        - **Don’t just install the first one in the search results** - read reviews, look at screenshots, read the installation instructions and consider what one to choose. 

    2. Install and Activate your chosen plugin.
    
## Appendix 1: Why Docker?

There are a few reasons why Docker is an attractive technology for me. Here are the most important requirements I have for my development environment and how Docker solves them:

* **Clean machine:** In an ideal world, I prefer not to install anything related to my development environment directly on my own computer. I work on so many different projects that this gets unmanageable. When one thing works, another doesn’t. I also travel a lot and should something happen to my computer, I want to be able to set up a new machine in minutes.
* **Shareable:** I often work in teams, so sharing my development environment with teammates is crucial.
* **Lightweight:** This is important, especially when on the road. Try running a few Vagrant boxes compared to a few Docker containers and see what I mean.
* **Extendable:** Extending Docker is very easy. For example, I could extend the official WordPress container and build it with a specific plugin or theme.
* **Mirror production:** My development environment needs to be as close to production as possible. With Docker this is easy, since Docker can be used in production as well.

## Appendix 2: What's in our Docker Compose file?

Let's quickly walk through what's in our `docker-compose.yml` file:

First of all, we define 2 _services_ - a `wordpress` service and a `db` service. The `db` service is using the official `mysql` Docker container image and it is is using the one that is tagged `5.7`. The `wordpress` service is using the official `wordpress` image, which comes pre-packaged with WordPress, PHP and a web server. Specifically, we are using the one that is tagged `php5.6-apache` because we are using PHP 5.6 and the Apache web server. There are a ton of different versions of the official `wordpress` image [on the Docker Hub](https://hub.docker.com/_/wordpress/).

Next we use the `ports` section to tell Docker Compose how to forward the ports of the Docker containers to our local machine. By forwarding port 3306 of the database container to our local port 3306, we can easily connect to the database locally from our own machine. By forwarding port 80 of the WordPress container to our local port 80, we can access the WordPress install directly via our browser.

Each service also has a `volumes` section. Each of these volumes map a folder inside of the container to our local machine. This is important because our Docker containers are completely wiped every time we turn them off. So if we want our data to persist across sessions, we need Docker to store the data on our local machine and not only inside of the container. For WordPress, we mount the `wp-content` folder to our local machine because this folder is where WordPress stores plugins, themes and uploads as we add these to our WordPress site.

Finally, each service has an `environment` section where we can specify values for variables that our Docker container uses to configure the environment. If you want the WordPress database to have another name or use another password, this is where you can configure it.
