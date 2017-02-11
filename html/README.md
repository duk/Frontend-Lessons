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
      <li><a href="/en-US/docs/Web/CSS">CSS</a></li>
      <li><a href="/en-US/docs/Web/JavaScript">JavaScript</a></li>
      <li><a href="/en-US/docs/Web/Guide/Graphics">Graphics</a></li>
      <li><a href="/en-US/docs/Web/HTTP">HTTP</a></li>
      <li><a href="/en-US/docs/Web/API">APIs / DOM</a></li>
      <li><a href="/en-US/docs/Mozilla/Add-ons/WebExtensions">WebExtensions</a></li>
      <li><a href="/en-US/docs/Web/MathML">MathML</a></li>
    </ul>
  </div>
  <div class="submenu-column last">
    <div class="title">References &amp; Guides</div>
    <ul>
      <li><a href="/en-US/docs/Learn">Learning web development</a></li>
      <li><a href="/en-US/docs/Web/Tutorials">Tutorials</a></li>
      <li><a href="/en-US/docs/Web/Reference">References</a></li>
      <li><a href="/en-US/docs/Web/Guide">Developer Guides</a></li>
      <li><a href="/en-US/docs/Web/Accessibility">Accessibility</a></li>
      <li><a href="/en-US/docs/Games">Game development</a></li>
      <li><a href="/en-US/docs/Web">...more docs</a></li>
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
      <a href="/account/user/workopenly/projects/TIP" class="aui-icon-container project-link" tabindex="-1">
        <span class="aui-avatar aui-avatar-xsmall aui-avatar-project">
              <span class="aui-avatar-inner">
                <img src="https://bitbucket.org/account/user/workopenly/projects/TIP/avatar/32">
              </span>
        </span>
        tipjar
      </a>
    </li>
    <li>
      <a href="/account/user/workopenly/projects/WOR" class="aui-icon-container project-link" tabindex="-1">
        <span class="aui-avatar aui-avatar-xsmall aui-avatar-project">
              <span class="aui-avatar-inner">
                <img src="https://bitbucket.org/account/user/workopenly/projects/WOR/avatar/32">
              </span>
        </span>
        workopenly
      </a>
    </li>
    <li>
      <a href="/account/user/bhndipper/projects/DIP" class="aui-icon-container project-link" tabindex="-1">
        <span class="aui-avatar aui-avatar-xsmall aui-avatar-project">
              <span class="aui-avatar-inner">
                <img src="https://bitbucket.org/account/user/bhndipper/projects/DIP/avatar/32">
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
      <li><a href="https://github.com/contact" data-ga-click="Footer, go to contact, text:contact">Contact GitHub</a></li>
      <li><a href="https://developer.github.com" data-ga-click="Footer, go to api, text:api">API</a></li>
      <li><a href="https://training.github.com" data-ga-click="Footer, go to training, text:training">Training</a></li>
      <li><a href="https://shop.github.com" data-ga-click="Footer, go to shop, text:shop">Shop</a></li>
      <li><a href="https://github.com/blog" data-ga-click="Footer, go to blog, text:blog">Blog</a></li>
      <li><a href="https://github.com/about" data-ga-click="Footer, go to about, text:about">About</a></li>

    </ul>

    <a href="https://github.com" aria-label="Homepage" class="site-footer-mark" title="GitHub">
      <svg aria-hidden="true" class="octicon octicon-mark-github" height="24" version="1.1" viewBox="0 0 16 16" width="24">
        <path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0 0 16 8c0-4.42-3.58-8-8-8z"></path>
      </svg>
    </a>
    <ul class="site-footer-links">
      <li>© 2017 <span title="0.95590s from github-fe134-cp1-prd.iad.github.net">GitHub</span>, Inc.</li>
      <li><a href="https://github.com/site/terms" data-ga-click="Footer, go to terms, text:terms">Terms</a></li>
      <li><a href="https://github.com/site/privacy" data-ga-click="Footer, go to privacy, text:privacy">Privacy</a></li>
      <li><a href="https://github.com/security" data-ga-click="Footer, go to security, text:security">Security</a></li>
      <li><a href="https://status.github.com/" data-ga-click="Footer, go to status, text:status">Status</a></li>
      <li><a href="https://help.github.com" data-ga-click="Footer, go to help, text:help">Help</a></li>
    </ul>
  </div>
</div>
```

[React Doc](https://facebook.github.io/react/)

```html
<footer class="nav-footer">
  <section class="sitemap">
    <a href="/react/" class="nav-home">
    </a>
    <div>
      <h5><a href="/react/docs/">Docs</a></h5>
      <a href="/react/docs/hello-world.html">Quick Start</a>
      <a href="/react/docs/thinking-in-react.html">Thinking in React</a>
      <a href="/react/tutorial/tutorial.html">Tutorial</a>
      <a href="/react/docs/jsx-in-depth.html">Advanced Guides</a>
    </div>
    <div>
      <h5><a href="/react/community/support.html">Community</a></h5>
      <a href="http://stackoverflow.com/questions/tagged/reactjs" target="_blank">Stack Overflow</a>
      <a href="https://discuss.reactjs.org/" target="_blank">Discussion Forum</a>
      <a href="https://discord.gg/0ZcbPKXt5bZjGY5n" target="_blank">Reactiflux Chat</a>
      <a href="https://www.facebook.com/react" target="_blank">Facebook</a>
      <a href="https://twitter.com/reactjs" target="_blank">Twitter</a>
    </div>
    <div>
      <h5><a href="/react/community/support.html">Resources</a></h5>
      <a href="/react/community/conferences.html">Conferences</a>
      <a href="/react/community/videos.html">Videos</a>
      <a href="https://github.com/facebook/react/wiki/Examples" target="_blank">Examples</a>
      <a href="https://github.com/facebook/react/wiki/Complementary-Tools" target="_blank">Complementary Tools</a>
    </div>
    <div>
      <h5>More</h5>
      <a href="/react/blog/">Blog</a>
      <a href="https://github.com/facebook/react" target="_blank">GitHub</a>
      <a href="http://facebook.github.io/react-native/" target="_blank">React Native</a>
      <a href="/react/acknowledgements.html">Acknowledgements</a>
    </div>
  </section>
  <a href="https://code.facebook.com/projects/" target="_blank" class="fbOpenSource">
    <img src="/react/img/oss_logo.png" alt="Facebook Open Source" width="170" height="45">
  </a>
  <section class="copyright">
    Copyright © 2017 Facebook Inc.
  </section>
</footer>
```