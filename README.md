# littleGhost
A super-simple (but extensible) Hugo template.

## Introduction

Little Ghost is just a really dead-simple Hugo Theme born out of my adventures in learning Hugo. I'll be continuing to update it, but it's currently designed for a personal website / portfolio.

## Prequisites

In order for the theme to work, you'll need to have both Hugo and Node.JS installed. You can refer to each of their respective websites for details, but here are the basic terminal commands you'll use to install them using Homebrew.

For Hugo:
```
brew install hugo
```

For Node.JS
```
brew install node
```

## Create a Hugo Site

Once you've got Hugo and Node installed, you can go ahead and create your site.

```
hugo new site site_name
```

After you've done this, go ahead and add a home page. First, create a file titled _index.md in the content folder. Then, add the following front matter at the top of the page.

```
---
title: "Home"
layout: single
---
```

## Install the Theme

Now, you can go ahead and install Little Ghost. Navigate to your site's root directory in the terminal and initiate a .git file:

```
git init

```

Then, you can add the theme using the following command:

```
git submodule add https://github.com/rickwysocki/littleGhost.git themes/littleGhost
```

## Configuration

Once you've got the theme installed, add the following to your config file.

```

# baseURL =
languageCode = 'en-us'
title = 'Site Title'
theme = "littleGhost"


[params]

  # Site info
  author = 'Your Name'
  author_bio = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. "
  long_bio = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."

  # SEO
  description = ''
  site_image = 'images/ghost.png' # Add site-wide featured image here.
  author_image = 'images/author.jpeg' # Used for main author bio card.
  nav_logo = 'images/ghost.png' # Icon included in nav-bar.

  # Links / Socials
  email = '#'
  github = '#'
  # mastodon = ''
  # twitter = ''
  # instagram = ''
  # facebook = ''


[menu]
  [[menu.main]]
    name = "Home"
    pre = "fa fa-home"
    url = "/"
    weight = 1
  [[menu.main]]
    name = "Posts"
    pre = "fa fa-keyboard"
    url = "/posts/"
    weight = 2

[taxonomies]
  tag = "tags"

```

You can go ahead and update the params under "Site info," "SEO," and "Links / Socials."

At this point, things should be up and running. To see your site, go the terminal and input:

```
hugo serve
```

Navigate to your web server in the browser and you should see your new Hugo site.

## Configuring the Blog

You've likely noticed that the "Posts" item in the header isn't working. It's a simple fix. Create a folder in the Content directory titled posts. You can then go ahead and add posts there. I recommend using Hugo's page bundles, but you can also add files directly there as well.

==Note: you may need to quit and restart the server in the terminal after adding the Posts folder.==

The following front matter can be added to blog posts.

```
---
title:  "Title"
date:   2023-03-10 16:08:22 -0500
summary: # A description of the post that will show up when the posts are listed.
description: # Used for SEO. If left blank, the description in your config file is pulled in.
featured_image: featured.png # This works as a featured image for the post. Note that the title must be featured before the file type.
featured_alt: # Include alt text and include more readers.
layout: post
---
```

## Customizing the Styles

At the top of themes/littleGhost/assets/custom.scss, there are some variables you can tweak to change the color scheme. All of my custom styles are in that same file, so go ahead and tweak at your leisure.
