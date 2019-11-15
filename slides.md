---
title: Introduction to Drupal - slides
---

<section>

# Introduction to Drupal
— with [mparker17][mparker17-drupalorg]

Follow along at [mparker17.github.io/talk--drupal-intro](index.md)

[mparker17-drupalorg]: https://www.drupal.org/u/mparker17

</section>

<section>
<section>

## Who am I?

[mparker17][mparker17-drupalorg] on Drupal.org, [Github][mparker17-github], and [Gitlab][mparker17-gitlab]

I work for [Digital Echidna][echidna], [Brady's Meat & Deli][bradysmeats]

<small>(previously [Environment Canada][wsc], [Versabanq][versabanq], [UWaterloo][uwaterloo], [PeaceWorks][peaceworks], [Myplanet][myplanet], [OpenConcept][openconcept])</small>

I am an [Acquia Certified Drupal Developer][acquia-cert]

<small><abbr title="Computer Science">CS</abbr> degree not completed at UWaterloo</small>

[mparker17-github]: https://github.com/mparker17
[mparker17-gitlab]: https://gitlab.com/mparker17
[echidna]: https://echidna.ca
[bradysmeats]: https://bradysmeats.com
[wsc]: https://www.canada.ca/en/environment-climate-change/services/water-overview/quantity/monitoring/survey.html
[versabanq]: https://www.versabank.com
[uwaterloo]: https://uwaterloo.ca
[peaceworks]: https://peaceworks.ca
[myplanet]: https://www.myplanet.com
[openconcept]: https://openconcept.ca
[acquia-cert]: https://certification.acquia.com/user/843258

</section>
</section>

<section>
<section>

# Goal and Objectives

This session will provide you with the knowledge you need to build a Drupal website using pre-built components and work on a Drupal website with others.

At the end of the session, you will:

* Be able to list the software on a web server and explain what that software does;
* Know what a CMS is, why using one is a good idea, and why Drupal is the best;
* Be able to install Drupal;
* Know the basic Drupal building blocks are and how they're used; and,
* Be familiar with the collaboration tools used on a typical Drupal project.

</section>
</section>
<section>
<section>

# How the web works

(In two minutes)

</section>
<section>

## Getting the message

* (Almost) every computer on the Internet has a unique address.
* Any two computers can send messages to each-other if:

    1. they know each-other's address,
    2. they have agreed on a medium to talk,
    3. they use a language they both understand.

* On the web…

    1. the addressing system is Domain Names (kinda),
    2. the medium is called HTTP
    3. the languages used are HTML, CSS and Javascript.

</section>
<section>

## Server-s you right!

* A web server is a normal computer running a special program (an HTTP server).
* An HTTP server listens for messages from browsers, requesting files. Most files it sends back verbatim.
* The HTTP server sends certain types of files through a separate program, sending the output from the program to the browser.

</section>
<section>

## Questions?

(don't sweat the details)

</section>
</section>
<section>
<section>

# Content management systems

</section>
<section>

## Content-ing yourself with the basics

* HTML is not a programming language, it's just another document format.
* Most web pages have a lot of non-content things on a page, like menus, supplementary information, headers and footers, ads, etc.
* Due to all this extra stuff, it's a pain to maintain even a small set of HTML files.
* CMSs are programs designed to write HTML for you that run on the web server.

</section>
<section>

## Dru-pal's your pal!

I use a CMS called Drupal because:

* it's general enough to be used for many things,
* it's really modular: there are TONS of plugins to do common tasks,
* I get extensive control over the look of my pages without a lot of work on my part,
* it has a powerful developer library, and
* the community is vibrant and helpful.

</section>
<section>

Drupal is awesome, but it's not perfect. Some common complaints are:

* It's not polished enough to "accidentally" create the content you want, like in Wordpress…
    * … but a study proved that Wordpress was actually harder to use than Drupal *if you tried to use it for things other than blogging*!
* Drupal has it's own theming engine, which can be challenging for designers familiar with HTML/CSS but not Drupal…
    * … but the theming engine affords control over the HTML in ways that CMSs without theming engines cannot!
* It was originally written before PHP was object-oriented, so it does things differently than developers expect…
    * … but Drupal 8 is be a complete, object-oriented rewrite of the system built on the [Symfony framework](https://symfony.com/).

</section>
<section>

## Questions?

We'll be installing Drupal so you can play around with it next.

</section>
</section>
<section>
<section>

# Running Drupal

Get out your computers!

</section>
<section>

## How a server stacks up

You can run Drupal on any computer running these programs:

1. Apache HTTP server — A program that listens for web browsers and responds to them by sending either:
    * a file from the server's hard drive, or
    * the output from a program.
2. PHP — A programming language designed for generating HTML on the fly.
    * The PHP program echos everything it's sent, except the sections of a file between `&lt;?php` and `?&gt;`, which it treats as instructions.
3. MySQL — A program to quickly and easily store and retrieve data.

</section>
<section>

## AMPed up

It's actually pretty easy to set up because there are tools that bundle these programs together:

* Macintosh: MAMP — [`mamp.info`](https://www.mamp.info/en/)
* Windows: Acquia Dev Desktop — [`dev.acquia.com/downloads`](https://dev.acquia.com/downloads)
* Linux (ubuntu): `sudo apt install tasksel && sudo tasksel install lamp-server`

Once your AMP stack is installed and running, test it out going to `http://localhost:8080/` (MAMP), `http://localhost:8082/` (Acquia Dev Desktop) or `http://localhost/` (Linux) in a web browser.

</section>
<section>

## Quick review

1. Apache, MySQL and PHP were just installed on your computer.
2. Windows and Mac users got a nice control panel to turn them on and off.
3. When turned on, Apache will serve the contents of a folder on your hard drive…
    * Macintosh: `/Applications/MAMP/htdocs`
    * Windows: `%HOMEPATH%\Sites\acquia-drupal`
    * Linux: `/var/www`

The folder that Apache serves is called your *webroot*.

## Questions before we move on?

</section>
<section>

## (Data) Base camp

Drupal stores content and settings in a database. We'll need to set one up before we set up Drupal.

1. Start phpMyAdmin:
    * Windows: In the Acquia Dev Desktop control panel, click the `Manage my database` button. A browser will launch with phpMyAdmin in it.
    * Macintosh: In the MAMP control panel, click the `Open start page` button. A browser will launch with the MAMP start page. Click `phpMyAdmin` in the header.
    * Linux: `sudo apt-get install phpmyadmin`. In a web browser, go to `http://localhost/phpmyadmin`.
2. Click `Users` at the top of the screen.
3. Click `Add user`.
4. Under *Login Information*, enter a short alphanumeric username, set Host to `localhost`, enter and retype a password. Take note of these credentials! Since they're on your local machine, they don't have to be secure.
5. Under *Database for user*, click `Create database with same name and grant all privileges`.*
6. Click the `Add user` button at the bottom.

This sets up a database with the same name as the username.

</section>
<section>

## Installing Drupal

1. Download the latest version of Drupal 7 from [`drupal.org/project/drupal`](https://www.drupal.org/project/drupal),
2. unpack the ZIP-file / tarball,
3. put the extracted files at your webroot (don't forget the `.htaccess` file!),
4. go to `http://localhost/install.php`:
    1. On the *Choose profile* page, choose `Standard`.
    2. On the *Choose language* page, choose `English` (unless you prefer another language - in that case, follow the directions).
    3. Hopefully you'll skip the *Verify requirements* stage. If not, ask for help from our trained technicians!
    4. On the *Set up database* step, enter the database name, username and password you entered when setting up the database. Leave the *Advanced options* alone.
    5. Drupal will take a few seconds to *Install [the] profile* you selected in the first step.
    6. On the *Configure site* step, enter a site name and e-mail address. Set up a Maintenence account with the username `admin` and the password `admin` (change these for your real site!). Enter other information as appropriate.
    7. On the *Finished* step, follow the link to your new site!

</section>
<section>

## Questions?

Next, we'll create our own movie-raiting website, similar to IMDB.

</section>
</section>
<section>
<section>

# Drupal building blocks

Modules, themes, users, content types, menus, taxonomy, blocks and views.

</section>
<section>

## Modular Bells

* A Drupal module is a plugin / add-on / extension that adds or changes functionality.
* There are over 20,000 modules maintained by the Drupal Community at [`drupal.org/project/modules`](https://www.drupal.org/project/project_module).
* Put modules in `sites/all/modules`.
* You can enable, disable, install and update modules from *Administration → Modules*.
    * After updating a module's files, run database updates with `update.php` as soon as possible.

</section>
<section>

* Look at the *Downloads* and *Project information* sections: ![Downloads and Project Information sections at drupal.org/project/metatag](/assets/modules-metatag.png)
    * Is there a recommended release?
    * Is the *maintenance status* "Actively maintained"?
    * Are *automated tests* enabled?
    * Are the number of installs > 1000?
    * Was the *last modified* date recent?
    * Developers: look at the code — does it conform to the [Drupal coding standards](https://www.drupal.org/docs/develop/standards) and is easy to follow?

</section>
<section>

## Theme songs

* A Drupal theme is a visual style / skin.
* There are over 1500 themes maintained by the Drupal Community at [`drupal.org/project/themes`](https://www.drupal.org/project/project_theme).
    * Some themes, like Zen, Omega, AdaptiveTheme and Fusion are *base themes* — designed as something for themers to build off of, not to be used on their own.
* Put themes in `sites/all/themes`.
* Theme settings are at *Administration → Appearance*.

</section>
<section>

## User your time wisely

* Drupal is designed to be a multi-user system.
* The Maintenance user created during the install process is special: all permission checks automatically succeed for it.
    * It's also called the super-user.
    * Many developers use it when developing locally.
    * Be careful who you give the super-user credentials to!
    * Avoid using it on production!
* Create, edit and delete users at *Administration → People*.

</section>
<section>

## Role playing

* Access control is done through roles:
    1. Create a role and assign a set of permissions to it.
    2. Assign one or more roles to one or more users.

* During a permission check, the current user's roles are checked. If any of the current user's roles has permission, they are granted access.
* You can set a special administrator role which is given all new permissions (i.e.: when a module is added).
* Manage roles at *Administration → People → Permissions → Roles*

</section>
<section>

## Permission to come aboard?

* As a general rule, Drupal doesn't disclose functionality that the user doesn't have access to.
    * If a user happens to find a link to a page they don't have access to, they'll get an access denied error.
* Assign permissions to roles at *Administration → People → Permissions*.

</section>
<section>

![The documentation page on Drupal.org, showing that the header, sidebars, footers, tabs and menus are not content.](/assets/drupal-page-content.png)

</section>
<section>

## Learning to type

* Drupal calls the data in the content area of the page a node.
* Drupal developers often create content types (node types) to model big chunks of data.
    * Developers, think of structs or objects.
* Some example content types are:
    * Movies
    * Actors
    * Reviews
* There's a handy Google Doc of content-type blueprints at [`atendesigngroup.com/node/2029`](https://atendesigngroup.com/node/2029)
* Create, edit and delete content types at *Administration → Structure → Content types*.

</section>
<section>

## Field trip!

* A field is a smaller chunk of data belonging to a node or user.
* All content types come with a required title field (which you can generate and/or hide, but not delete).
* Some fields for Movie nodes are:
    * Title (plain text)
    * Synopsis (rich text)
    * MPAA rating (string chosen from a list)
    * Genre (tag)
    * Release date (date)
    * User rating (integer)
    * List of actors (node reference)
* You can make fields of fields using the [Field collection module](https://www.drupal.org/project/field_collection).
* You can make fields that link to other nodes using the [Entity reference module](https://www.drupal.org/project/entityreference).
* When the core *Field UI* module is enabled, you can manage fields while editing content types.
* You can actually attach fields to nodes, users, comments, and taxonomy terms.

</section>
<section>

## The path of least resistance

* Drupal modules that create visitable pages on the site must register an "internal path" for each page.
* For content, the module *node* generates an internal path like `node/1`.
* But, humans and search engines like to see the name of the page in the path.
    * Drupal's core `Path` module allows you to create aliases, which Drupal resolves to an internal path before it can display the page.
    * Administer aliases at *Administration → Configuration → Search and Metadata → URL aliases*.
* We use modules like [Pathauto](https://www.drupal.org/project/pathauto) to automatically generate aliases.
    * Manage pathauto patterns at *Administration → Configuration → Search and Metadata → URL aliases → Patterns*.

</section>
<section>

## Aside: Alias security risks

Be careful what aliases you set up in the root of the site!

* Setting an alias like `node` will break Drupal's internal routing system!
* Many search engines validate your control of a domain by determining whether or not you can put files at the root of the domain (e.g.: Google Analytics).
    * A user could potentially gain access to your analytics data by creating an alias like `google-site-verification-$uuid.html`!
* It's good practice to let Pathauto create new pages with the pattern `content/[node:title]` to avoid these pitfalls.

</section>
<section>

## It's raining menus!

* A menu is a list of links, usually used for navigation.
* Create, edit and delete menus and menu items at *Administration → Structure → Menus*.
* Drupalism: both the internal routing system and (this) page-listing system share the same name
    * References to `menu_router` and `hook_menu()` have to do with the internal routing system.
    * References to `menu_custom`, `menu_links` and the Menu module have to do with this page-listing system.

</section>
<section>

## A higher taxonomy bracket

* Most CMSs allow you to tag content, including Drupal.
* But Drupal takes it one step further by allowing multiple tagging systems.
* In Drupal, tagging systems are called "vocabularies" (or taxonomies). Tags are called "terms".
    * Terms can have synonyms, related terms and a hierarchy.
* Administer taxonomy and terms at *Administration → Structure → Taxonomy*.
* Example: classifying recipes:
    * Terms in the "Season" vocabulary:
        * Spring
            * Lunar new year
            * Easter
        * Summer
        * Fall
            * Thanksgiving
        * Winter
            * Festive
    * Terms in the "Meat" vocabulary:
        * Beef
        * Pork
        * Lamb
* Some people use node references instead of taxonomy terms; use whatever seems easiest given your use-case.

</section>
<section>

![A screenshot of a page on the Drupal website highlighting regions and blocks](/assets/drupal-page-blocks.png)

</section>
<section>

## Block party

* Most non-content stuff on a page are blocks.
    * The *placement* of the content in a theme is done with a block, but the content itself is managed by other modules.
    * Blocks must be placed in regions.
    * Regions are defined by the theme.
    * You have a lot of control over when blocks are shown — whitelist, blacklist, custom PHP code and to certain roles.
    * Custom blocks have an optional title, a body, and an administrative title, but are not entities.
* Blocks can be configured in *Administration → Structure → Blocks*.
* You can make blocks of blocks with the *Mini panels* module (a sub-module of [Panels](https://www.drupal.org/project/panels)).

</section>
<section>

## A View-tiful Mind

Views lets you make lists of things.

* Views can be displayed on their own pages, in blocks, in RSS feeds, or as attachments to other views (called *Displays*).
* You display views in HTML lists, tables, jump menus or leave them unformatted (called *Formats*), as well as add headers, footers and content when the list is empty.
* You can display pages in their entirety, or only a limited set of fields. You can add relationships to get related fields (i.e.: a node's author's interests).
* You can narrow the list with hidden filters, let the user set the filters themselves by exposing them, or get contextual filters from the environment where the view is being displayed (i.e.: the page a block is displayed on).
* You can control how the list is sorted.

</section>

<section>

## Questions?

Next, we'll talk about working on your shiny new site with your friends.

</section>
</section>
<section>
<section>

# Collaborating

Database dumps, git and features

</section>

<section>

## Storage lockers

* Settings, configuration, content, blocks, etc. are stored in the database for quicker access.
* PHP files, styles, downloadable files and images are stored on the server's filesystem.
* The database and filesystem together make up a single Drupal site.
* We recommend setting up or agreeing upon a "canonical" site that everyone can make their changes when you're ready.

</section>
<section>

## Down in the dumps

Writing the contents of a database to a file is called making a database dump.

To do this:

1. Go to phpMyAdmin.
2. Click the name of the Drupal database in the column at the left.
3. Click the `Export` tab at the top.
4. Set *Export method* to `Quick` and *Format* to `SQL`, and click `Go`.
5. The database will download to your computer.
    * Remember: your username and password are stored in the database, so be very careful how you distribute database dumps!

</section>
<section>

## Import-ant notes

If you want to use a database dump, you must put it back into your database.

To do this:

1. Go to phpMyAdmin.
2. Click the name of the Drupal database in the column at the left.
3. Click the `Import` tab at the top.
4. Under *File to import*, choose the database dump you want to import, and click `Go`.

If you run into failed imports, try deleting (`drop`ping) everything in your database before importing.

</section>
<section>

## Git outta here

* Git is a tool to keep record changes to files.
    * Developers, there are several tutorials at [`try.github.com`](https://try.github.io/) which you can use to learn it.
    * Designers, you really only need to know how to get the latest changes. I recommend [GitHub Desktop](https://desktop.github.com/).
* GitHub is a free service that allows everyone working on a project to store their files the same place.
* Many Drupal shops (and some hosting providers) use it to store all the files that make up a Drupal site, except...
    * the file at `sites/default/settings.php` because it contains sensitive information unique to the computer it's on
    * any files under `sites/default/files/` because it tends to be extremely large and often has temporary files
    * any other files containing passwords, keys, etc.
* By adding paths and filenames to a file named `.gitignore`, you can tell Git to never store them. Make sure to set this up first!

</section>
<section>

## Bonus features

* The *Features* module transfers settings in the database to files on the filesystem.
* This is useful for keeping track of changes to your settings and site structure over time.
* It's good practice to store features for your content types and any structures related to them.
* You can generate features from *Administration → Structure → Features*.
* Extract the files it generates into your site's modules folder, then enable them from the Features admin page or the Modules admin page.

</section>
<section>

## Questions?

Only one more thing before you can get back to working on your projects...

</section>
</section>
<section>
<section>

# Drush

The DRUpal SHell.

</section>
<section>

## Drush hour

* A number of frequently-used Drupal tasks have been automated with [Drush](https://github.com/drush-ops/drush).
* Drush allows you to perform tasks like downloading files to the right place, clearing caches or running updates on the command-line, which is often faster doing them manually.
* Windows users already have it installed. Macintosh and Linux users need to install it as follows:
    * Macintosh: `/Applications/MAMP/bin/php/php5.4.4/bin/pear channel-discover pear.drush.org && /Applications/MAMP/bin/php/php5.4.4/bin/pear install drush/drush`
    * Linux: `pear channel-discover pear.drush.org && pear install drush/drush`

</section>
</section>
<section>

## Questions and discussion

This session should have provided you with the knowledge you need to build a Drupal website using pre-built components and work on a Drupal website with others.

You should now:

* Be able to list the software on a web server and explain what that software does;
* Know what a CMS is, why using one is a good idea, and why Drupal is the best;
* Be able to install Drupal;
* Know the basic Drupal building blocks are and how they're used; and
* Be familiar with the collaboration tools used on a typical Drupal project.

Find me at [drupal.org/u/mparker17](https://www.drupal.org/u/mparker17) — [mparker17 on GitHub](https://github.com/mparker17) — [mparker17 on GitLab](https://gitlab.com/mparker17).

</section>
