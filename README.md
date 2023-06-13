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
hugo new site mysite
```

## Install the Theme

Navigate to your site's root directory in the terminal and use the following command to install the theme:

```
git submodule add https://github.com/rickwysocki/littleGhost.git themes/littleGhost
```

## Configuration

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
  author_image = 'images/ghost.png' # Used for main author bio card.
  nav_logo = 'images/ghost.png' # Icon included in nav-bar.
  # canonical_url = 'https://url.com'

  # Links / Socials
  email = '#'
  github = '#'
  # mastodon = 'https://mas.to/@rickwysocki'
  # twitter = '' fix user name
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
