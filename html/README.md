# Mastering Html

As I mentioned in main README.md, we will split a html page into useful parts. Then we will memorize them.

I will use a few famous websites as examples.

* [Github](https://github.com/) (collaboration)
* [Amazon](https://www.amazon.com) (ecommerce)
* [NY Times](https://www.nytimes.com/) (news)
* [Twitter](https://twitter.com/) (Social)
* [Bitbucket](https://bitbucket.org/) (I just want to use their frontpage as Splash page)

Here is my approach to web application design. 

1. Less is better. Any addition on your page adds more weight to it.
2. Do not hide things. Try to avoid dropdown menu if you can. Show only the things the user needs.
3. Contents trump Styles. Be fast. Be simple. Be elegant.
4. Every line needs to have purpose.


##### Table of Contents  

0. [Layouts](#layouts)
1. [Navbar](#navbar)
2. [Sidbar](#sidebar)
3. [Menu](#menu)
4. [Footer](#footer)
5. [Tutorials](#tutorials)
   1. [How to set up](#howtosetup) 
   2. [Add Placeholders](#addplaceholder)
   3. [Add Layouts](#addlayouts)

<a name="layouts" />

## Layouts

First, this is a generic placeholder in any html. This is what I got from typing `!` in Visual Studio Code. It's called [Emmet snippets](http://docs.emmet.io/cheat-sheet/)
But I added one more line to it: ``
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Document</title>
  <meta charset="UTF-8">
  <!-- the line below makes the page mobile friendly -->
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
<body>
    
</body>
</html>
```

<a name="navbar" />

## Navbar

Navar is where you store things that you want your user to be able to see all the time. But you have to be careful on how big you want it to be.

Let's look at how Github does it. Github's navbar does not stick to the top whereas Bitbucket's homepage has navbar that sticks to the top.

Here is Github nav tags

```html
<div class="header header-dark header-logged-in true" role="banner">
  <div class="container clearfix">

    <a class="header-logo-invertocat">
    </a>

    <div class="header-search" role="search">
    </div>

    <ul class="header-nav float-left" role="navigation">
      <li class="header-nav-item">
      </li>
      <li class="header-nav-item">
      </li>
      <li class="header-nav-item">
      </li>
    </ul>

    <ul class="header-nav user-nav float-right" id="user-links">
      <li class="header-nav-item">
      </li>
      <li class="header-nav-item dropdown js-menu-container">
      </li>
      <li class="header-nav-item dropdown js-menu-container">
      </li>
    </ul>

  </div>
</div>
```

Let's compare that with Bitbucket's splash page

```html
<div style="height: 95px;">
  <header class="header__branded-domains header__branded-domains--bitbucket">
    <div class="grid">
      <a href="https://bitbucket.org/" class="header__logo-link" title="Atlassian Bitbucket">

      </a>
      <a href="#" class="aui-icon aui-icon-large aui-iconfont-appswitcher menu-toggle"></a>
      <nav class="header__branded-domains__nav-links">
        <ul>
          <li> <a href="/product/features" title="Features" class="features cms-link--navLink">Features</a> </li>
        </ul>
      </nav>
    </div>
    <nav class="header__branded-domains__nav-links--mobile" style="max-height: 0px; position: static;">
      <ul>
        <li> <a href="/product/features" title="Features" class="features cms-link--navLink">Features</a> </li>
      </ul>
    </nav>
  </header>
</div>
```

Now we start seeing patterns. All the lists on a webpage seem to be using `<ul>` tag. But I also see additional tags in Bitbucket html tag.

Can you see them?

1. Bitbucket's html is more semantic. There are html tags that exist just for semantic purpose; they have no built-in styles. They are just for logical separation of documents.
2. Bitbucket follows [BEM syntax](https://en.bem.info/methodology/naming-convention/)

There are a lot of ways to style your website. And there are a lot of methodologies out there. Use whatever fits your need. We will cover them in CSS section.

Here are what we've learned so far.

1. `<div></div>` is heavily used in html to group things.
2. `<ul></ul>` for any type of list.
3. We need some sort of naming convention for CSS. (e.g. BEM)
4. You do have an option of adding additonal semantic tags `<nav>` or `<header>` as in Bitbucket's home page. I personally prefer to have them since they make it easier to find things.
5. And on Bitbucket page, you see `<div style="height: 95px;">` which contains inline styling and some people consider as **bad**. I will talk about it more when I get to CSS.

<a name="sidebar" />

## Sidebar

Sidebar contains page specific info. Application specific info should go to navbar. So sidebar should contain related info based on what page the user is on. Again, if you can get away with 
not having sidebar, do that. The less is better.

Let's see what kind of information some websites contain on sidebars.

In Bitbucket, the right sidebar contains recent commits. That's pretty useful.

```html
<div class="aui-item sidebar">

  <section class="activity">
    <h2>
      Recent activity

      <a href="/duklee/rss/feed?token=502c623b37f9f3c8ec08f39876e7717f" title="Subscribe to this newsfeed" class="rss"><span class="aui-icon aui-icon-small aui-iconfont-rss rss-icon">Subscribe to this newsfeed</span></a>
    </h2>

    <div class="newsfeed">

      <article class="news-item pushed" data-author="duklee">

        <a href="/duklee/">
          <div class="aui-avatar aui-avatar-small">
            <div class="aui-avatar-inner">
              <img alt="Duk Lee" src="https://bitbucket.org/account/duklee/avatar/48/?ts=1486826581" class="" data-src-url="https://bitbucket.org/account/duklee/avatar/48/?ts=1486826581"
                data-src-url-2x="https://bitbucket.org/account/duklee/avatar/96/?ts=1486826581">
            </div>
          </div>
        </a>

        <div class="news-item-title">

          <a href="/duklee/jekyllblog/commits/8c75fd08b5deb7262419ac290bbb151b1f14cb27">1 commit</a>

        </div>
        <div class="news-item-description">

          Pushed to

          <a href="/duklee/jekyllblog" title="duklee/jekyllblog">duklee/jekyllblog</a>
        </div>

        <div class="changesets">
          <div class="changeset">
            <a href="/duklee/jekyllblog/commits/8c75fd08b5deb7262419ac290bbb151b1f14cb27" class="changeset-hash">8c75fd0</a>photo
            section added
          </div>
        </div>

        <div class="news-item-info">

          <a href="/duklee/">Duk Lee</a> ·
          <time datetime="2017-01-22T07:38:46-08:00" title="22 January 2017 07:38">2017-01-22</time>
        </div>
      </article>

    </div>

  </section>
</div>
```

Again we notice Bitbucket is using semantic tags such as `<article>` and `<section>`. 
On [this great document](https://developer.mozilla.org/en-US/docs/Web/HTML/Element), Firefox groups them into "Content Sectioning".

And sidebar seems be nested into `<main>` tag; it is and should be logically tied to the page content. 

<a name="menu" /> 

## Menu

I personally believe that web app shouldn't be exactly like desktop app. Even for a desktop app, I don't hardly go through menu and submenus. And I usually get
frustrated by too much information.

A good web developer understands how to eliminate things. Any additional elimination is a bandwidth gain. It's like borrowing your friend's car for grocery shoppping 
when you were living in a dorm. Don't use up gas driving everywhere. Just do grocery shopping. Bandwidth is not free. Be mindful.

Here are some snippets from various websites.

From Mozilla Developer Network

```html
<div class="submenu submenu-cols-2 js-submenu" id="nav-platform-submenu" aria-hidden="true" style="z-index: 99998; display: none;">
  <div class="submenu-column">
    <div class="title">Technologies</div>
    <ul>
      <li><a href="/en-US/docs/Web/HTML">HTML</a></li>

    </ul>
  </div>
  <div class="submenu-column last">
    <div class="title">References &amp; Guides</div>
    <ul>
      <li><a href="/en-US/docs/Learn">Learning web development</a></li>

    </ul>
  </div>
  <button type="button" class="submenu-close transparent"><span class="offscreen">Close submenu</span><i aria-hidden="true" class="icon-remove-sign"></i></button></div>
```

From Bitbucket

```html
<div class="aui-dropdown2-section">
  <strong>Recently viewed</strong>
  <ul class="aui-list-truncate">
    <li>
      <a>
        <span class="aui-avatar aui-avatar-xsmall aui-avatar-project">
              <span class="aui-avatar-inner">
                <img />
              </span>
        </span>
        tipjar
      </a>
    </li>
    <li>
      <a>
        <span class="aui-avatar aui-avatar-xsmall aui-avatar-project">
              <span class="aui-avatar-inner">
                <img />
              </span>
        </span>
        workopenly
      </a>
    </li>
    <li>
      <a>
        <span class="aui-avatar aui-avatar-xsmall aui-avatar-project">
              <span class="aui-avatar-inner">
                <img />
              </span>
        </span>
        DipperUI
      </a>
    </li>
  </ul>
</div>
```

<a name="footer" />

## Footer

Footer contains boring corporate fine print stuff. Also some useful links can go there as well. 

1. Footer is rarely sticky. Do not make both navbar and footer sticky. 
2. Footer should contain info that is useful only when the user needs them.

[Github](https://github.com/)

```html
<div class="container site-footer-container">
  <div class="site-footer" role="contentinfo">
    <ul class="site-footer-links float-right">
      <li><a>Contact GitHub</a></li>
    </ul>

    <ul class="site-footer-links">
      <li>© 2017 <span>GitHub</span>, Inc.</li>
    </ul>
  </div>
</div>
```

[React Doc](https://facebook.github.io/react/)

```html
<footer class="nav-footer">
  <section class="sitemap">
    <a class="nav-home">
    </a>
    <div>
      <h5><a>Docs</a></h5>
      <a>Quick Start</a>
      <a>Thinking in React</a>
      <a>Tutorial</a>
      <a>Advanced Guides</a>
    </div>
    <div>
      <h5><a>Community</a></h5>
      <a>Stack Overflow</a>
      <a>Discussion Forum</a>
      <a>Reactiflux Chat</a>
      <a>Facebook</a>
      <a>Twitter</a>
    </div>
    <div>
      <h5><a>Resources</a></h5>
      <a>Conferences</a>
      <a>Videos</a>
      <a>Examples</a>
      <a>Complementary Tools</a>
    </div>
    <div>
      <h5>More</h5>
      <a>Blog</a>
      <a>GitHub</a>
      <a>React Native</a>
      <a>Acknowledgements</a>
    </div>
  </section>
  <a class="fbOpenSource">
    <img />
  </a>
  <section class="copyright">
    Copyright © 2017 Facebook Inc.
  </section>
</footer>
```

<a name="tutorials" />

## Tutorials

<a name="howtosetup" />

### How to set up

1. Make sure you have git installed on your machine. If you are using a Mac or any Unix machine, type `git` in terminal. Follow this [instruction](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. Clone this git repo. `git clone https://github.com/duk/FrontendLessons.git`
3. Make sure you have node installed on your machine as well. type `node` in termanl to check. Get nodejs from [here](https://nodejs.org/en/download/)
4. Go to the cloned directory by `cd FrontendLessons` or wherever your cloned directory is.
5. Run `npm install`
6. Run `live-server` Your browser should start with index.html

<a name="addplaceholder" />

### Add Placeholder

1. Go to [`http://127.0.0.1:8080/html/index.html`](http://127.0.0.1:8080/html/index.html) on your browser
2. As you can see you do not see anything.
3. Now from your favorite editor, open `index.html`
4. We will add three html tags; `<header>`, `<main>`, `<footer>` ([`http://127.0.0.1:8080/html/placeholder.html`](http://127.0.0.1:8080/html/placeholder.html))

Let's open up a developer tool and see what's going on. By the way, make sure you familarize yourself with the developer tool. If you are
a web developer, you will be using that a lot.

Go to [`http://127.0.0.1:8080/html/placeholder.html`](http://127.0.0.1:8080/html/placeholder.html) and open up a developer tool. Then select `<header>`. All three tags have the
same built-in style. `display: block;` is like a line with return carriage at the end; the entire row is occupied by the element. And


```css
article, aside, footer, header, hgroup, main, nav, section {
    display: block;
}
```

<a name="addlayouts" />

### Add Layouts

To visiualize what's happening, let's add borders to `<header>`,`<main>` and `<footer>`

```html
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        header,
        main,
        footer {
            border: 1px solid black;
        }
    </style>
</head>
```

Let's work on `<header>` section more. I would like to add a logo, search box and a navigation bar inside the `<header>`
Open [`http://127.0.0.1:8080/html/layouts.html`](http://127.0.0.1:8080/html/layouts.html)

```html
<header>
    <a href="#">super awesome logo</a>
    <div>
        <form action="">
            <input type="text">
            <button>Search</button>
        </form>
    </div>
    <nav>
        <ul>
            <li>item 1</li>
            <li>item 2</li>
            <li>item 3</li>
        </ul>
    </nav>

</header>
```

Now what do you see? Things look stacked up against one another. But we want it to line up horizontally not vertically. If you investigate the tags,
you will notice `<div>` and `<form>` are `block` elements.

Let's head over to Mozilla Developer Network CSS doc and read about `display` options. When I made these change below, I was able to display the log, 
search and menu items horizontally. Open [`http://127.0.0.1:8080/html/layouts00.html`](http://127.0.0.1:8080/html/layouts00.html) to see the change.

```css
header,
main,
footer,
div,
form {
    border: 1px solid black;
}
        
div {
    display: inline-block;
}
/*form {
    display: inline-block;
}*/
        
nav,
li {
    display: inline-block;
}
```

We will worry about making things pretty in CSS tutorials. I will try to keep CSS stuff to the minium so that we can focus on html.
    