# WordPress Module Group Project

## Outline

For the CYF WordPress module we want you to create a working website using WordPress. You will work together in groups to create a WordPress theme and accompanying plugin.

### Goals
* Use your new WordPress skills as well as your existing HTML, CSS and JavaScript knowledge
* Learn the advantages of using a CMS like WordPress
* Follow a project brief, ensuring you meet the requirements given to you
* Show creativity in coming up with solutions to problems and demonstrate design flair
* Use collaboration, communication and project management skills

## The Project Brief

For this project we will imagine that you are working with a client called Glasgow Bike Store. They have chosen you to help them build a website, congratulations! They have outlined the following:

> "We are the Glasgow Bike Store, a social enterprise that provides bike products and repair services. We require a new website to allow our clients to discover who we are, contact us if they need help and to use a tool to browse our product database. We want to be able to manage and edit content on the site, including adding to and editing our products database. We are looking for a simple design that follows our existing brand.

### The Project Requirements

You are required to:

* Set up a WordPress installation for the website
* Add the following Pages and content:
  1. 'Home' page, featuring:
      * Short welcome text
      * Large image
      * Testimonial(s)
  2. 'About' page, featuring:
      * Text and accompanying images
  3. 'Products' page, featuring:
        * A table displaying all company products, with appropriate headings for 'Product Name', 'Colour', 'Price' and 'SKU Code'
        * A form for Administrators (i.e. logged in users) only, that allows new products to be added to the database. It should have text input fields for 'Product Name', 'Colour', 'Price' and 'SKU Code' as well as a textarea input field for 'Description'
        * The table and form data display and functionality should be managed by a custom WordPress plugin (see below for details)
  4. 'Contact' page, featuring:
      * Company address and telephone number
      * A contact form (via a third-party plugin of your choice)
* The site should have the following shared elements across all pages:
  * A header with: 
    * Company logo
    * Navigation menu to link to the pages listed above
    * A contact telephone number
  * A footer with: 
    * Company logo at half the size of the header
    * A contact telephone number
    * A link to the company Twitter and Facebook accounts. These links should open in a new window

### Custom Plugin

To manage and display products a custom WordPress plugin is required. This plugin should:

* Create a 'Product' custom post type
  * The custom post type should have text fields for: 'Product Name', 'Colour', 'Price' and 'SKU Code' as well as a textarea field for 'Description'
* Create a custom archive template that outputs the products on a page in a table
* Create a form that allows logged on users to add new products to the database, preferably via the WordPress REST API

### Design Guidelines

* The client has provided a rough layout (see project assests below) that you should follow
* The text and images can be laid out however you like. Text and images are provided but you can add your own if prefer
* Colours should follow the company brand guidelines (see project assests below)
* The theme should be responsive so that it works across smaller screens (e.g. mobiles) as well as larger screens

### Project Assets

* The client has provided you with the following assets:

- [Brand guidelines](./project-assets/brand-guidelines.md) — Logo and colours
- [Layout](./project-assets/layout.png) — A rough layout for you to follow
- [Site Content](./project-assets/site-content.md) — content required for each page
- [Images](./project-assets/images/) — images for you to use

### Getting Started

* Install a new instance of WordPress on you machine, or use an existing installation and delete all content 
* Download the [Minimalist theme](https://github.com/carmemias/minimalist-theme), install and activate it in your local WordPress install
* Make sure you know where theme and plugin folders are stored in the WordPress installation structure — you will need to edit these files
* Read the Project Requirements again. Is there anything you don't understand?
* Split up tasks amongst your group. Here are some ideas for responsibilities:
  * Project Manager — understands the brief, ensures everyone knows what they are to do, communicates with the team and the client regularly
  * Front End Developer(s) — Makes sure the theme matches the required look and feel, applies brand styling and outputs the product database via the API
  * Back End Developer(s) — Creates and/or sources plugins to meet requirements, creates the product database and provides the API
  * Tester(s) — makes sure the website works, meets the requirements and has no bugs, provides feedback to developers
* Plan together what you are going to do during the week, set up a Slack channel for the project and arrange a time to discuss and/or meet together
* Use GIT to work collaboratively on your theme and plugin code. Create branches for each feature you build and create pull requests to merge in finished code. Review each others code before approving pull requests
* If you are stuck post a question on the `#scotland-wp` channel in Slack

### Stretch Goals

You will get bonus points if you can also complete the following:

* Include complete [theme stylesheet header metadata](https://codex.wordpress.org/Theme_Development#Theme_Stylesheet).
  * Do you know what all these items mean? What is the 'License', the 'Text Domain' and so on?
* Try sharing your theme with a fellow student and ask them if they can install it via the WordPress admin.
  * Does it install okay? You will need to make sure you [provide a `.zip` file](https://www.competethemes.com/blog/manually-install-wordpress-theme/) to your fellow student.
* Make the site available for the client by uploading to a hosting service
  * Set the client up with their own login account so that they can edit content. Provide some basic documentation so that they know where and how to login. _(Pretend a mentor is the client and send them details via Slack)_
* Imagine you are charging the client for the work you are doing
  * How do you work out how much to charge the client?
  * Estimate how long the project will take (in days) and compare this to how long it actually took — how accurate where you?
  * Do you ask for all the money upfront, or wait until you have finished?

## Further Reading

* [Creating A WordPress Plugin Is Easier Than You Think](https://www.wpbeaverbuilder.com/creating-wordpress-plugin-easier-think/)
* [How to Create Custom Post Types In WordPress](https://www.hostinger.co.uk/tutorials/wordpress-custom-post-types)
* [A Quick Start Guide To The WordPress REST API](https://www.wpsuperstars.net/wordpress-rest-api/)
