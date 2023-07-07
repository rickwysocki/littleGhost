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

## Configuring Your Site

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

## Page Layout and Front Matter Options

There are two types of page layouts you can call on in front matter: single and project-page.

### Single Layout

Single layouts are simple. Because Hugo generally is agnostic to the difference between posts and pages, you can use the single layout for essentially any content you create.

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

Note that the of the display of most of these parameters on the site depends on them being configured in the front matter for a page. A date, for example, is not necessary--you can safely remove that for undated pages.

### Project-page Layout

Project-page layouts are almost identical to single page layouts. The only difference is that project-page layouts allow you to include an optional "Project Info" aside that details information about a project and skills you demonstrate in it. This is meant to be useful on pages where the main column might be used to display work, such as a gallery.

Here is an example of front matter for a project-page.

```
---
title: "Making Future Matters"
layout: portfolio-page
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

### Site Header

On any page, you have the option to include a site header that will display your main image, tagline, and links that you've set up in the config file. You can include this on a page by adding the following to your front matter:

```
site_header: true
```

I recommend using this, at least, on your home page.

### Working with Images

You can call a `featured_image:` parameter on any content page you create, as well as a `featured_alt:` parameter describing the image for accessibility. You've seen an example of this above:

```
featured_image: featured.png
featured_alt: Making Future Matters logo.
```

I recommend including images for any page in a Hugo page bundle for the most seamless experience. Any image called as the `featured_image` in the front matter will show up on top of the page and on any list pages including your page. For any other images, I recommend using the standard Hugo figure shortcode.

### Standard Navigation

Little Ghost comes out of the box with three pages in the navigation:

- A Home page. This will display the _index.md file in your content directory that you created above.
- A Posts page. This is your blog. To use it, create a posts/ folder in your content directory and place content there.
- A portfolio page. This page will usefully display any page that has `category: portfolio` included in the front matter, giving you an easy way to offer a sample of your work to site visitors.

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

### Featured

Besides "portfolio," there is one other category that you can easily make use of in Little Ghost that allows you to create featured content that you would like viewers to pay particular attention to. This takes two steps.

#### Add Featured Content Categories to Front Matter

The first thing you'll want to do is add `featured_post: true` to any content you want to feature. Note that this will apply to _any_ page, not just posts, despite the name.

#### Add Featured Content to Pages

You can decide which pages you want to add a featured content box to. For example, you could just include it on the home page for new visitors. To display featured content, simply add the following to your front matter:

```
featured_grid: true
```

Note that the grid will always display two posts in a row when the screen is wide enough, so I recommend keeping your featured content to multiples of two for aesthetic purposes.
