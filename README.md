= Little Ghost
Rick Wysocki <rlwysockijr@gmail.com>
1, {docdate}
:description: This document provides instructions for installing Little Ghost, a simple but flexible Hugo theme.
:keywords: hugo
:imagesdir: images
:toc: left
:icons: image
:iconsdir: icons

{description}

image::ghost-post-image.png[]

Little Ghost is a simple but flexible https://gohugo.io[Hugo] theme built with https://tailwindcss.com[Tailwind CSS]. It offers an easy and aesthetically pleasing kick-start to blogs and portfolio websites. is primarily designed for blogs and portfolio websites.

== Installing littleGhost

=== Prerequisites

==== Knowledge Prerequisites

These instructions assume a working familiarity with the following practices:

* Using Hugo's capabilities as a content management system.
* Navigating command-line interfaces.
* Employing a text-editor, such as Virtual Studio Code, to edit a flat file structure.

The instructions will explain features and/or uses of each of these concepts, but if you are truly new to any of them you should research them before moving forward here.

==== Software Prequisites

You will need to install Node.JS, Node Package Manager, and Hugo installed on your machine to use Little Ghost. The following links provide installation instructions for each of these programs:

- https://nodejs.org/en[Node.js]
- https://docs.npmjs.com/downloading-and-installing-node-js-and-npm[NPM]
- https://gohugo.io/installation/[Hugo]

[TIP]
.Checking Your Machine
====
If you are unsure whether any or all of these prerequisite programs are installed on your machine, you can easily check each of them using your command-line interface using the following commands.

* ```node -v```
* ```npm -v```
* ```hugo version```

If the software is installed, each command will return a version number.
====

=== Create Your Hugo Site and Add the Theme Files

After you've installed Node.js, NPM, and Hugo, you're ready to create your Hugo site. In your command-line interface, navigate to the folder where you want to place your site. Then, run the following command, replacing "mysite" with the name of your site:

NOTE: These instructions will continue as though the name of the site is "mysite". 

```
  hugo new site mysite
```

Next, navigate to your site directory.

```
cd mysite
```

Now, you'll add Little Ghost to your themes directory. First, initiate a .git file:

```
git init
```

Then, install the theme using the following command:

```
git submodule add https://github.com/rickwysocki/littleGhost.git themes/littleGhost
```

=== Initiate Tailwind

Little Ghost's Tailwind CSS requires a couple extra steps. Navigate to the theme folder:

```
cd themes/littleGhost
```

Then, run the following:

```
npm init -y
```

Finally, run a Node script to build your site from the Tailwind files. 

```
npm run build-tw
```

[NOTE]
.Editing Tailwind Files
====
If you like to tinker below the hood, you'll need to run ```npm run build-tw``` to update your site any time you change Tailwind-related content. If you want to do extensive editing of this content, I recommend the following:

1. Navigate to your theme folder in a separate command-line window.
2. Run ```npx tailwindcss -i ./assets/main.css -o ./assets/style.css --watch```

This will rebuild your CSS automatically any time you make changes.
====

== Configuring Your Site

You need to add some content to your ```config.toml``` file before your site will run.

```
baseURL = ""
languageCode = 'en-us'
title = ''
theme = ["littleGhost"]
enableInlineShortcodes = true

[params]

# Site info
author = 'Author'
author_bio = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
long_bio = "Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."

# SEO
description = 'Site description.'

# Images
site_image = 'images/ghost.png' # Add site-wide featured image here.
author_image = 'images/ghost.png' # Used for main author bio card.
nav_logo = 'images/ghost.png' # Icon included in nav-bar.
post_image = 'images/ghost-post-image.png'
post_image_alt = 'Little Ghost logo.'


# Links / Socials
email = '#'
github = '#'
mastodon = '#'
twitter = '#'
# instagram = ''
# facebook = ''

pluralizeListTitles = false

[menu]
  [[menu.main]]
    name = "Home"
    url = "/"
    weight = 1
  [[menu.main]]
    name = "Posts"
    url = "/posts/"
    weight = 2
  [[menu.main]]
      name = "Portfolio"
      url = "/portfolio/"
      weight = 3


[taxonomies]
  tag = "tags"
  course = 'courses'
  category = 'categories'


[permalinks]
  posts = '/posts/:year/:month/:title/'
  categories = '/:title/'
```

IMPORTANT: Add this code to the ```config.toml``` in the root directory of your project, **not** the configuration file in the Little Ghost theme folder. 

=== Create Your First Page

You're ready to create your first page. Follow these steps:

1. Open your site folder in your text editor of choice. 
2. Create a file titled _index.md **in your content directory**.
3. Add the following front matter:

```
---
title: Home
layout: single
site_header: true
---
```

Feel free to add any text below the front matter before you move on. This text will display on your homepage. 

=== View Your Site

If you are still in the theme folder in your command-line interface, navigate back to your root site folder. Then, run:

```
hugo serve
```

The local server returned by the command-line interface can now be used in a browser to view your site.

== Page Layout and Front Matter Options

There are two page layouts in Little Ghost: 

* single.
* project-page.

They are *extremely* similar, but portfolio pages offer an additional feature, discussed below.

=== Single Layout

Single layouts are simple. Because Hugo is agnostic to the difference between posts and pages, you can use the single layout for essentially any content you create.

There are a number of different front matter variables you can use for pages in Little Ghost. Here's an example of front matter for a blog post:

```
---
layout: single
title:  "What is New About New Media?"
date:   2021-11-16 11:34:22 -0500
tags:
  - Media Studies
summary: New media are better defined as media that challenge our existing conceptions of technology... even if the new media in question might be old.
published: true
featured_image: featured.jpg
featured_alt: A roll of camera film.
---
```

Note that these parameters usually depend you configuring them in the front matter for a page. They are not always required in every context. A date, for example, is not necessary--you can safely remove that for undated pages.

=== Project-page Layout

Project-page layouts are almost identical to single page layouts. The only difference is that project-page layouts allow you to include an optional "Project Info" aside that details information about a project and skills you demonstrate in it. This is meant to be useful on pages where the main column might be used to display work, such as a gallery.

Here is an example of front matter for a project-page.

```
---
title: "Making Future Matters"
layout: project-page
summary: I co-edited and designed an experimental, born-digital edited collection of writing studies scholarship.
project_info: true
featured_image: featured.png
featured_alt: Making Future Matters logo.
skills:
  - Web Design
  - Adobe InDesign
  - HTML5 / CSS
  - Javascript
  - Project Management
  - Editorial Work
  - Adobe Premiere
---
```

=== Site Header

On any page, you have the option to include a site header that will display your main image, tagline, and links that you've set up in the config file. You can include this on a page by adding the following to your front matter:

```
site_header: true
```

I recommend using this, at least, on your home page.

=== Working with Images

You can call a `featured_image:` parameter on any content page you create, as well as a `featured_alt:` parameter describing the image for accessibility. You've seen an example of this above:

```
featured_image: featured.png
featured_alt: Making Future Matters logo.
```

I recommend including images using [Hugo page bundles](https://gohugo.io/content-management/page-bundles/) for the most seamless experience. A `featured_image` assigned in the front matter will display at the top of the page as well as on list pages. For additional images, I recommend using the standard [Hugo figure shortcode](https://gohugo.io/content-management/shortcodes/).

=== Navigation

Little Ghost comes out of the box with three pages in the navigation:

- A Home page. This will display the _index.md file in the content directory that you created above.
- A Posts page. This is your blog. To use it, create a posts/ folder in your content directory and place content there.
- A Portfolio page. This page will usefully display any page that has `category: portfolio` included in the front matter, giving you an easy way to offer a sample of your work to visitors.

You can add any other pages to the site navigation in your config file. For example:

```
[menu]
  [[menu.main]]
    name = "Home"
    url = "/"
    weight = 1
  [[menu.main]]
    name = "Posts"
    url = "/posts/"
    weight = 2
  [[menu.main]]
      name = "Portfolio"
      url = "/portfolio/"
      weight = 3
  [[menu.main]] # This page has been added to the navigation.
      name = "Research"
      url = "/research/"
      weight = 4
```

=== Featured

Besides "portfolio," there is one other category that allows you to create featured content, which can be displayed on any page. This takes two steps.

==== Add Featured Content Categories to Front Matter

First, add `featured_post: true` to any content you want to feature. Note that this will apply to _any_ page, not just posts, despite the name.

==== Add Featured Content to Pages

You can decide which pages will display featured content. For example, you could just include it on the home page for new visitors. To display featured content, simply add the following to a page's front matter:

```
featured_grid: true
```

Note that the grid will always display a maximum of two pages per row, so I recommend keeping your featured content to multiples of two for aesthetic purposes.

== Front Matter Options

[cols="1,1"]
|===
|Cell in column 1, header row |Cell in column 2, header row 

|layout
|```layout: single```, ```layout: portfolio-page```

|title
|Cell in column 2, row 2

|date
|Cell in column 2, row 3 

|tags
|Cell in column 2, row 3 

|summary
|Cell in column 2, row 3 

|published
|Cell in column 2, row 3 

|featured_image
|Cell in column 2, row 3 

|project_info
|Cell in column 2, row 3 

|skills
|Cell in column 2, row 3 

|site_header
|Cell in column 2, row 3 

|featured_grid
|Cell in column 2, row 3 

|featured_post
|Cell in column 2, row 3 

|featured_alt
|Cell in column 2, row 3 
|=== 
