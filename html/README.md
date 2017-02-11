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

<a name="sidebar" />

## Sidebar

<a name="menu" />

## Menu

<a name="footer" />

## Footer