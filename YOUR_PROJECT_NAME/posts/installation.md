# Installation
Simpler blog example from [https://github.com/nuejs/nue/tree/master/packages/examples/simple-blog/%40global](https://github.com/nuejs/nue/tree/master/packages/examples/simple-blog/%40global)

## Install Nue
bun i nuekit

## Build your project
Create a folder YOUR_PROJECT_NAME, enter it and add index.md with a markdown title
```
mkdir YOUR_PROJECT_NAME
cd YOUR_PROJECT_NAME
echo '# Hello everyone' > index.md
```

## Run project
nue

## Editing
edit YOUR_PROJECT_NAME/index.md markdown content using your favorite editor to add basic SEO
```
---
title: Welcome to the blog
description: Create a simple blog using Nue.
---
```

## Add img folder
Create YOUR_PROJECT_NAME/img and add images of social icons in svg (for example github.svg, linkedin.svg, ...)

## Add layout
Create YOUR_PROJECT_NAME/layout.html
```
<header>
  <a href="/">Back to home</a>
  <nav>
    <a :for="el in social" :href="el.url">
        <img class="icon" src="/img/{el.icon}.svg">
    </a>
  </nav>
</header>

<footer>
    <p>{fullname} - { new Date().getFullYear()}</p>
    <q>{slogan}</q>
</footer>
```

## Add data
Create YOUR_PROJECT_NAME/site.yaml with this content
```
fullname: YOUR_PROJECT_NAME_GOES_HERE
slogan: Simpler blog example by the_shorekeeper using Nue.
credits: shouanren ~ the_shorekeeper
social:
  - icon: github
    url: https://www.github.com/shouanren/
  - icon: linkedin
    url: https://x.com/the_shorekeeper
```

## Update the layout
Edit YOUR_PROJECT_NAME/layout.html to have this:
```
<header>
  <a href="/">Back to home</a>
    <nav>
      <a :for="el in social" :href="el.url">
      <img class="icon" src="/img/{el.icon}.svg">
    </a>
  </nav>
</header>
<main>
  <h1>{title}</h1>
  <p>
    <pretty-date :date/>Article author: <a href="https:x.com/the_shorekeeper">{credits}</a>
  </p>
  <article>
    <slot for="content"/>
  </article>
</main>
<footer>
  <p>{fullname} - { new Date().getFullYear()}</p>
  <q>{slogan}</q>
</footer>
```

## Edit the Homepage to display posts
Edit YOUR_PROJECT_NAME/index.md with content_collection: posts
```
---
title: Welcome to the blog
description: Simpler blog by the_shorekeeper using Nue.
content_collection: posts
---
# Hello everyone
```

## Add posts with some content
Create YOUR_PROJECT_NAME/posts/scaleable-design-system.md and add valid markdown to it
Create YOUR_PROJECT_NAME/posts/installation.md and add valid markdown to it

## Edit the Layout to render the collection of posts
Edit YOUR_PROJECT_NAME/layout.html to have this:
```
<header>
  <a href="/">Back to home</a>
  <nav>
    <a :for="el in social" :href="el.url">
        <img class="icon" src="/img/{el.icon}.svg">
    </a>
  </nav>
</header>
<main>
  <h1>{title}</h1>
  <p>
    <pretty-date :date/>Article author: <a href="https:x.com/the_shorekeeper">{credits}</a>
  </p>
  <article>
    <slot for="content"/>
  </article>
  <aside>
    <a :for="post in posts" :href="post.url">
      <h2>{post.title}</h2>
      <p>{post.date}</p>
      <p>{post.pubDate}</p>
    </a>
  </aside>
</main>
<footer>
  <p>{fullname} - { new Date().getFullYear()}</p>
  <q>{slogan}</q>
</footer>
```

## Add styles
### THIS IS TO VERIFY BECAUSE IT DOESN'T SEEM TO WORK PROPERLY (also have added a YOUR_PROJECT_NAME/style.css with all styles merged)
Create YOUR_PROJECT_NAME/@global/style.css with the required CSS (feel free to copy from this repo)

## Deploy
nue --production
