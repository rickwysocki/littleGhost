# Little Ghost - Hugo Theme

Little Ghost is a simple but extensible Hugo theme built with Tailwind.css. It is primarily designed for blogs and portfolio websites. I designed it to give folks an easy and aesthetically pleasing kick-start to their Hugo sites.

## Installing littleGhost

### Prequisites

To use Little Ghost, you'll need to have Node.js, Node Package Manager, and Hugo installed on your machine. Here are links to the relevant documentation:
- [Node.js](https://nodejs.org/en)
- [NPM](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
- [Hugo](https://gohugo.io/installation/)

### Create Your Hugo Site and Add the Theme Files

After you've installed Node.js, NPM, and Hugo, you're ready to create your Hugo site. In your command-line interface navigate to the folder where you want to place your site. Then, run the following command, replacing "name" with the name of your site:

```
  hugo new site name
```

Then, navigate to your site directory. (Note that these instructions will continue to assume that your site is titled "name.")

```
cd name
```

Now, you'll add Little Ghost to your themes directory. First, initiate a .git file":

```
git init
```

Then, install the theme using the following command:

```
git submodule add https://github.com/rickwysocki/littleGhost.git themes/littleGhost
```

### Initiate Tailwind

You'll need to take a few extra steps to get Tailwind.css working. Navigate to the theme folder:

```
cd themes/littleGhost
```

Then, run the following:

```
npm init -y
```

Finally, you'll run a Node script that will build your site from the Tailwind files. You'll need to run this script to update your site any time you change Tailwind-related content in layout files.

```
Run npm-build-tw.
```

I recommend the following if you want to do more extensive editing of theme layouts:

1. Navigate to your theme folder in a separate command-line window.
2. Run npx tailwindcss -i ./assets/main.css -o ./assets/style.css --watch`

This will automatically rebuild your site any time you make changes.

### Configuring Your Site

Your site won't work quite yet. First, you'll need to add some information to your config.toml file. Note that you should add this to _your_ config file in the root directory of your Hugo site, not to the theme.toml file included in the Little Ghost Theme files.

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

### Create Your First Page.

At this point, you're ready to create your first page. Create a file titled _index.md in your content directory and add the following front matter:

```
title: Home
layout: single
site_header: true
```


### View Your Site

You're now ready to view your site. If you are still in the theme folder in your command-line interface, navigate back to your root site folder. Then, run:

```
hugo serve
```

You should see your site using the server link given to you.
