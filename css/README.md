# Mastering CSS

First, go through some of awesome websites on your own. The biggest hurdle in CSS for me is to grok `positionining`. I found 
[Learn CSS Positioning in Ten Steps](http://www.barelyfitz.com/screencast/html-training/css/positioning/) very helpful.

And I also find this [w3schools.com How TO](http://www.w3schools.com/howto/default.asp) great for breaking a site into modules.

First, I will go through one of the simplest CSS framework called "[skeleton](https://github.com/dhg/Skeleton/blob/master/css/skeleton.css)" and try to understand each line. Then we will learn how to 
group things and memorize them. Also we will go over some popualr CSS processing techniques and BEM.

##### Table of Contents  

0. [Color](#color)
1. [Learn from Skeleton](#skeleton)
2. [Learn from Bulma](#bulma)
3. [Learn from Pure CSS](#purecss)
4. [CSS Flashcards](#flashcards)
5. [Good CSS Websites](#links)

<a name="color" />

## 0. Color

Most bad looking websites are because of misuse of colors. To really understand web design, you have to understand color. So we will learn about color here.

Here are some helpful links that I found

* [Web design 101: color theory](https://webflow.com/blog/web-design-101-color-theory)
* [A Simple Way to Understand Hue, Saturation and Luminosity](https://www.labnol.org/home/hue-saturation-luminosity/20104/)


<a name="skeleton" />

## 1. Learn from Skeleton

First thing you would notice in any type of CSS framework is that it comes with some sort of `normalizing` css library. Browsers do have built-in
styles for html tags. So in order to be consistent across all the browsers we need to `remove` predefined styles. Think of it as erasing the
blackboard before writing your stuff.

```css
.container {
  position: relative;
  width: 100%;
  max-width: 960px;
  margin: 0 auto;
  padding: 0 20px;
  box-sizing: border-box; }
```
`position: relative;` gives the framework flexibility to handle position if needed.
`width: 100%` stretches the width to 100%, but `max-width` limits it only up to 960px. `margin: 0 auto;` is a good one to memorize since it's
the way we can make sure things are centered.

Open [`http://127.0.0.1:8080/css/skeleton00.html`](http://127.0.0.1:8080/css/skeleton00.html)

```css
.column,
.columns {
  width: 100%;
  float: left;
  box-sizing: border-box; }
```

[Interesting article](https://www.paulirish.com/2012/box-sizing-border-box-ftw/) on `box-sizing: border-box;`. Also read [this article](https://css-tricks.com/box-sizing/) as well.

Open [`http://127.0.0.1:8080/css/skeleton01.html`](http://127.0.0.1:8080/css/skeleton01.html)

```css
@media (min-width: 400px) {
  .container {
    width: 85%;
    padding: 0; }
}
```
Go read [Using media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries). So what this part is saying is that
'if the browser size is bigger than 400px, we can add some more padding by reducing the width to 85%. But when it shrink below 400px, we are now
contrained with space. So stretch width to full 100%.

Open [`http://127.0.0.1:8080/css/skeleton02.html`](http://127.0.0.1:8080/css/skeleton02.html)

```css
@media (min-width: 550px) {
  .container {
    width: 80%; }
  .column,
  .columns {
    margin-left: 4%; }
  .column:first-child,
  .columns:first-child {
    margin-left: 0; }

  .one.column,
  .one.columns                    { width: 4.66666666667%; }
  .two.columns                    { width: 13.3333333333%; }
  .three.columns                  { width: 22%;            }
  .four.columns                   { width: 30.6666666667%; }
  .five.columns                   { width: 39.3333333333%; }
  .six.columns                    { width: 48%;            }
  .seven.columns                  { width: 56.6666666667%; }
  .eight.columns                  { width: 65.3333333333%; }
  .nine.columns                   { width: 74.0%;          }
  .ten.columns                    { width: 82.6666666667%; }
  .eleven.columns                 { width: 91.3333333333%; }
  .twelve.columns                 { width: 100%; margin-left: 0; }

  .one-third.column               { width: 30.6666666667%; }
  .two-thirds.column              { width: 65.3333333333%; }

  .one-half.column                { width: 48%; }

  /* Offsets */
  .offset-by-one.column,
  .offset-by-one.columns          { margin-left: 8.66666666667%; }
  .offset-by-two.column,
  .offset-by-two.columns          { margin-left: 17.3333333333%; }
  .offset-by-three.column,
  .offset-by-three.columns        { margin-left: 26%;            }
  .offset-by-four.column,
  .offset-by-four.columns         { margin-left: 34.6666666667%; }
  .offset-by-five.column,
  .offset-by-five.columns         { margin-left: 43.3333333333%; }
  .offset-by-six.column,
  .offset-by-six.columns          { margin-left: 52%;            }
  .offset-by-seven.column,
  .offset-by-seven.columns        { margin-left: 60.6666666667%; }
  .offset-by-eight.column,
  .offset-by-eight.columns        { margin-left: 69.3333333333%; }
  .offset-by-nine.column,
  .offset-by-nine.columns         { margin-left: 78.0%;          }
  .offset-by-ten.column,
  .offset-by-ten.columns          { margin-left: 86.6666666667%; }
  .offset-by-eleven.column,
  .offset-by-eleven.columns       { margin-left: 95.3333333333%; }

  .offset-by-one-third.column,
  .offset-by-one-third.columns    { margin-left: 34.6666666667%; }
  .offset-by-two-thirds.column,
  .offset-by-two-thirds.columns   { margin-left: 69.3333333333%; }

  .offset-by-one-half.column,
  .offset-by-one-half.columns     { margin-left: 52%; }

}
```

Now we are getting into Skeleton's Grid system. First thing we notice is that all the measurement is in percentage so that the layout
stays responsive regardless what devices that the user is on.

Open [`http://127.0.0.1:8080/css/skeleton03.html`](http://127.0.0.1:8080/css/skeleton03.html)

```css
/* NOTE
html is set to 62.5% so that all the REM measurements throughout Skeleton
are based on 10px sizing. So basically 1.5rem = 15px :) */
html {
  font-size: 62.5%; }
```
Typography is a huge part of web design. Picking a right font family can make your website look so much better. This is a good time to look into what type of measurement units are used.

1. px: static value that we need to avoid as much as we can
2. em: dynamic respect to the parent element. em values compound.
3. rem: just like em but its values are relative to the root html element. no compounding.

To me, `rem` unit seems to be a good choice for handling font size.

Open [`http://127.0.0.1:8080/css/skeleton04.html`](http://127.0.0.1:8080/css/skeleton04.html)

```css
body {
  font-size: 1.5em; /* currently ems cause chrome bug misinterpreting rems on body element */
  line-height: 1.6;
  font-weight: 400;
  font-family: "Raleway", "HelveticaNeue", "Helvetica Neue", Helvetica, Arial, sans-serif;
  color: #222; }
```

After the author sets the base font-size in `<html>` tag, he sets other font attributes in `<body>` tag.


Open [`http://127.0.0.1:8080/css/skeleton05.html`](http://127.0.0.1:8080/css/skeleton05.html)

```css
h1, h2, h3, h4, h5, h6 {
  margin-top: 0;
  margin-bottom: 2rem;
  font-weight: 300; }
h1 { font-size: 4.0rem; line-height: 1.2;  letter-spacing: -.1rem;}
h2 { font-size: 3.6rem; line-height: 1.25; letter-spacing: -.1rem; }
h3 { font-size: 3.0rem; line-height: 1.3;  letter-spacing: -.1rem; }
h4 { font-size: 2.4rem; line-height: 1.35; letter-spacing: -.08rem; }
h5 { font-size: 1.8rem; line-height: 1.5;  letter-spacing: -.05rem; }
h6 { font-size: 1.5rem; line-height: 1.6;  letter-spacing: 0; }
```

First, the author is setting styles for header tags.


```css
@media (min-width: 550px) {
  h1 { font-size: 5.0rem; }
  h2 { font-size: 4.2rem; }
  h3 { font-size: 3.6rem; }
  h4 { font-size: 3.0rem; }
  h5 { font-size: 2.4rem; }
  h6 { font-size: 1.5rem; }
}
```

But on bigger screen, these header tags are bigger.

```css
p {
  margin-top: 0; }

a {
  color: #1EAEDB; }
a:hover {
  color: #0FA0CE; }

.button,
button,
input[type="submit"],
input[type="reset"],
input[type="button"] {
  display: inline-block;
  height: 38px;
  padding: 0 30px;
  color: #555;
  text-align: center;
  font-size: 11px;
  font-weight: 600;
  line-height: 38px;
  letter-spacing: .1rem;
  text-transform: uppercase;
  text-decoration: none;
  white-space: nowrap;
  background-color: transparent;
  border-radius: 4px;
  border: 1px solid #bbb;
  cursor: pointer;
  box-sizing: border-box; }

.button:hover,
button:hover,
input[type="submit"]:hover,
input[type="reset"]:hover,
input[type="button"]:hover,
.button:focus,
button:focus,
input[type="submit"]:focus,
input[type="reset"]:focus,
input[type="button"]:focus {
  color: #333;
  border-color: #888;
  outline: 0; }

.button.button-primary,
button.button-primary,
input[type="submit"].button-primary,
input[type="reset"].button-primary,
input[type="button"].button-primary {
  color: #FFF;
  background-color: #33C3F0;
  border-color: #33C3F0; }
.button.button-primary:hover,
button.button-primary:hover,
input[type="submit"].button-primary:hover,
input[type="reset"].button-primary:hover,
input[type="button"].button-primary:hover,
.button.button-primary:focus,
button.button-primary:focus,
input[type="submit"].button-primary:focus,
input[type="reset"].button-primary:focus,
input[type="button"].button-primary:focus {
  color: #FFF;
  background-color: #1EAEDB;
  border-color: #1EAEDB; }

input[type="email"],
input[type="number"],
input[type="search"],
input[type="text"],
input[type="tel"],
input[type="url"],
input[type="password"],
textarea,
select {
  height: 38px;
  padding: 6px 10px; /* The 6px vertically centers text on FF, ignored by Webkit */
  background-color: #fff;
  border: 1px solid #D1D1D1;
  border-radius: 4px;
  box-shadow: none;
  box-sizing: border-box; }
/* Removes awkward default styles on some inputs for iOS */
input[type="email"],
input[type="number"],
input[type="search"],
input[type="text"],
input[type="tel"],
input[type="url"],
input[type="password"],
textarea {
  -webkit-appearance: none;
     -moz-appearance: none;
          appearance: none; }

textarea {
  min-height: 65px;
  padding-top: 6px;
  padding-bottom: 6px; }
input[type="email"]:focus,
input[type="number"]:focus,
input[type="search"]:focus,
input[type="text"]:focus,
input[type="tel"]:focus,
input[type="url"]:focus,
input[type="password"]:focus,
textarea:focus,
select:focus {
  border: 1px solid #33C3F0;
  outline: 0; }

label,
legend {
  display: block;
  margin-bottom: .5rem;
  font-weight: 600; }

fieldset {
  padding: 0;
  border-width: 0; }

input[type="checkbox"],
input[type="radio"] {
  display: inline; }

label > .label-body {
  display: inline-block;
  margin-left: .5rem;
  font-weight: normal; }

ul {
  list-style: circle inside; }
ol {
  list-style: decimal inside; }
ol, ul {
  padding-left: 0;
  margin-top: 0; }
ul ul,
ul ol,
ol ol,
ol ul {
  margin: 1.5rem 0 1.5rem 3rem;
  font-size: 90%; }
li {
  margin-bottom: 1rem; }

code {
  padding: .2rem .5rem;
  margin: 0 .2rem;
  font-size: 90%;
  white-space: nowrap;
  background: #F1F1F1;
  border: 1px solid #E1E1E1;
  border-radius: 4px; }
pre > code {
  display: block;
  padding: 1rem 1.5rem;
  white-space: pre; }

th,
td {
  padding: 12px 15px;
  text-align: left;
  border-bottom: 1px solid #E1E1E1; }
th:first-child,
td:first-child {
  padding-left: 0; }
th:last-child,
td:last-child {
  padding-right: 0; }

button,
.button {
  margin-bottom: 1rem; }
input,
textarea,
select,
fieldset {
  margin-bottom: 1.5rem; }
pre,
blockquote,
dl,
figure,
table,
p,
ul,
ol,
form {
  margin-bottom: 2.5rem; }

.u-full-width {
  width: 100%;
  box-sizing: border-box; }
.u-max-full-width {
  max-width: 100%;
  box-sizing: border-box; }
.u-pull-right {
  float: right; }
.u-pull-left {
  float: left; }

hr {
  margin-top: 3rem;
  margin-bottom: 3.5rem;
  border-width: 0;
  border-top: 1px solid #E1E1E1; }
```
One thing to notice here is [Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)

> A CSS pseudo-class is a keyword added to selectors that specifies a special state of the element to be selected. For example :hover will apply a style when the user hovers over the element specified by the selector.


```css
.container:after,
.row:after,
.u-cf {
  content: "";
  display: table;
  clear: both; }
```

`:after` is [Pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)

>Just like pseudo-classes, pseudo-elements are added to selectors but instead of describing a special state, they allow you to style certain parts of a element. For example, the ::first-line pseudo-element targets only  the first line of an element specified by the selector.

Also you will see [`clear: both;`](https://developer.mozilla.org/en-US/docs/Web/CSS/clear) a lot in any CSS files on the Web.

>The clear CSS property specifies whether an element can be next to floating elements that precede it or must be moved down (cleared) below them. The clear property applies to both floating and non-floating elements.
>
>When applied to non-floating blocks, it moves the border edge of the element down until it is below the margin edge of all relevant floats. This movement (when it happens) causes margin collapsing not to occur.
>
>When applied to floating elements, it moves the margin edge of the element below the margin edge of all relevant floats. This affects the position of later floats, since later floats cannot be positioned higher than earlier ones.
>
>The floats that are relevant to be cleared are the earlier floats within the same block formatting context.

```css
/* Larger than mobile */
@media (min-width: 400px) {}

/* Larger than phablet (also point when grid becomes active) */
@media (min-width: 550px) {}

/* Larger than tablet */
@media (min-width: 750px) {}

/* Larger than desktop */
@media (min-width: 1000px) {}

/* Larger than Desktop HD */
@media (min-width: 1200px) {}
```

This is where you would put your stuff based on screen size you need to support. Always use `min-width`. When you design a website, you design for the smallest possible device first, then start adding media queries for bigger devies. You **never** design for a desktop then adding media queries for small devices.



<a name="bulma" />

## 2. Learn from Bulma

Let's look at [Bulma](https://github.com/jgthms/bulma). If you go there, first thing you notice is bulma.sass file. So what is "Sass"? Sass stands for "Syntactically Awesome Style Sheets" and there are currently two dialects. One is `.sass` and the other is `scss`. 

>Sass makes CSS fun again. Sass is an extension of CSS, adding nested rules, variables, mixins, selector inheritance, and more. It's translated to well-formatted, standard CSS using the command line tool or a web-framework plugin.
>
>Sass has two syntaxes. The new main syntax (as of Sass 3) is known as "SCSS" (for "Sassy CSS"), and is a superset of CSS's syntax. This means that every valid CSS stylesheet is valid SCSS as well. SCSS files use the extension .scss.
>
>The second, older syntax is known as the indented syntax (or just "Sass"). Inspired by Haml's terseness, it's intended for people who prefer conciseness over similarity to CSS. Instead of brackets and semicolons, it uses the indentation of lines to specify blocks. Although no longer the primary syntax, the indented syntax will continue to be supported. Files in the indented syntax use the extension .sass.


```sass
/*! bulma.io v0.3.1 | MIT License | github.com/jgthms/bulma */
@charset "utf-8"

@import "sass/utilities/_all"
@import "sass/base/_all"
@import "sass/elements/_all"
@import "sass/components/_all"
@import "sass/grid/_all"
@import "sass/layout/_all"
```
As you can see, sass/scss is great for organizing your project neatly.

You should go read [Sass Documentation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html) first.

sass/utilities/_all
```sass
@charset "utf-8"

@import "functions.sass"
@import "variables.sass"
@import "mixins.sass"
@import "controls.sass"
```

functions.sass

```sass
@function powerNumber($number, $exp)
  $value: 1
  @if $exp > 0
    @for $i from 1 through $exp
      $value: $value * $number
  @else if $exp < 0
    @for $i from 1 through -$exp
      $value: $value / $number
  @return $value

@function colorLuminance($color)
  $color-rgb: ('red': red($color),'green': green($color),'blue': blue($color))
  @each $name, $value in $color-rgb
    $adjusted: 0
    $value: $value / 255
    @if $value < 0.03928
      $value: $value / 12.92
    @else
      $value: ($value + .055) / 1.055
      $value: powerNumber($value, 2)
    $color-rgb: map-merge($color-rgb, ($name: $value))
  @return (map-get($color-rgb, 'red') * .2126) + (map-get($color-rgb, 'green') * .7152) + (map-get($color-rgb, 'blue') * .0722)

@function findColorInvert($color)
  @if (colorLuminance($color) > 0.55)
    @return rgba(#000, 0.7)
  @else
    @return #fff

@function removeUnit($number)
  @if type-of($number) == 'number' and not unitless($number)
    @return $number / ($number * 0 + 1)
  @return $number

@function roundToEvenNumber($number)
  @return floor($number / 2) * 2
```

variable.sass

```sass
////////////////////////////////////////////////
////////////////////////////////////////////////
// 1. Initial variables

// Colors
$black:        hsl(0, 0%, 4%) !default
$black-bis:    hsl(0, 0%, 7%) !default
$black-ter:    hsl(0, 0%, 14%) !default

$grey-darker:  hsl(0, 0%, 21%) !default
$grey-dark:    hsl(0, 0%, 29%) !default
$grey:         hsl(0, 0%, 48%) !default
$grey-light:   hsl(0, 0%, 71%) !default
$grey-lighter: hsl(0, 0%, 86%) !default

$white-ter:    hsl(0, 0%, 96%) !default
$white-bis:    hsl(0, 0%, 98%) !default
$white:        hsl(0, 0%, 100%) !default

$orange:       hsl(14,  100%, 53%) !default
$yellow:       hsl(48,  100%, 67%) !default
$green:        hsl(141, 71%,  48%) !default
$turquoise:    hsl(171, 100%, 41%) !default
$blue:         hsl(217, 71%,  53%) !default
$purple:       hsl(271, 100%, 71%) !default
$red:          hsl(348, 100%, 61%) !default

// Typography
$family-sans-serif: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", "Helvetica", "Arial", sans-serif !default
$family-monospace: "Inconsolata", "Consolas", "Monaco", monospace !default

$size-1: 3.5rem !default
$size-2: 2.75rem !default
$size-3: 2rem !default
$size-4: 1.5rem !default
$size-5: 1.25rem !default
$size-6: 14px !default
$size-7: 0.75rem !default

$weight-light: 300 !default
$weight-normal: 400 !default
$weight-semibold: 500 !default
$weight-bold: 700 !default

// Miscellaneous
$easing: ease-out !default
$radius-small: 2px !default
$radius: 3px !default
$radius-large: 5px !default
$speed: 86ms !default

////////////////////////////////////////////////
////////////////////////////////////////////////
// 2. Primary colors

$primary: $turquoise !default

$info: $blue !default
$success: $green !default
$warning: $yellow !default
$danger: $red !default

$light: $white-ter !default
$dark: $grey-darker !default

////////////////////////////////////////////////
////////////////////////////////////////////////
// 3. Applied variables

// Invert colors
$orange-invert: findColorInvert($orange) !default
$yellow-invert: findColorInvert($yellow) !default
$green-invert: findColorInvert($green) !default
$turquoise-invert: findColorInvert($turquoise) !default
$blue-invert: findColorInvert($blue) !default
$purple-invert: findColorInvert($purple) !default
$red-invert: findColorInvert($red) !default

$primary-invert: $turquoise-invert !default
$info-invert: $blue-invert !default
$success-invert: $green-invert !default
$warning-invert: $yellow-invert !default
$danger-invert: $red-invert !default
$light-invert: $dark !default
$dark-invert: $light !default

// General colors
$background: $white-ter !default

$border: $grey-lighter !default
$border-hover: $grey-light !default

// Text colors
$text: $grey-dark !default
$text-invert: findColorInvert($text) !default
$text-light: $grey !default
$text-strong: $grey-darker !default

// Code colors
$code: $red !default
$code-background: $background !default

$pre: $text !default
$pre-background: $background !default

// Link colors
$link: $primary !default
$link-invert: $primary-invert !default
$link-visited: $purple !default

$link-hover: $grey-darker !default
$link-hover-border: $grey-light !default

$link-focus: $grey-darker !default
$link-focus-border: $primary !default

$link-active: $grey-darker !default
$link-active-border: $grey-dark !default

// Typography
$family-primary: $family-sans-serif !default
$family-code: $family-monospace !default

$size-small: $size-7 !default
$size-normal: 1rem !default
$size-medium: $size-5 !default
$size-large: $size-4 !default

////////////////////////////////////////////////
////////////////////////////////////////////////
// 4. Lists and maps

$colors: (white: ($white, $black), black: ($black, $white), light: ($light, $light-invert), dark: ($dark, $dark-invert), primary: ($primary, $primary-invert), info: ($info, $info-invert), success: ($success, $success-invert), warning: ($warning, $warning-invert), danger: ($danger, $danger-invert)) !default

$sizes: $size-1 $size-2 $size-3 $size-4 $size-5 $size-6 !default
```
mixins.sass

```sass
=arrow($color)
  border: 1px solid $color
  border-right: 0
  border-top: 0
  content: " "
  display: block
  height: 0.5em
  pointer-events: none
  position: absolute
  transform: rotate(-45deg)
  width: 0.5em

=block
  &:not(:last-child)
    margin-bottom: 1.5rem

=clearfix
  &:after
    clear: both
    content: " "
    display: table

=center($size)
  left: 50%
  margin-left: -($size / 2)
  margin-top: -($size / 2)
  position: absolute
  top: 50%

=delete
  // We need even pixel dimensions to ensure the delete cross can be perfectly centered
  $dimension-small: roundToEvenNumber(1.5 * removeUnit($size-6) * removeUnit($size-small)) * 1px
  $dimension-normal: roundToEvenNumber(1.5 * removeUnit($size-6) * removeUnit($size-normal)) * 1px
  $dimension-medium: roundToEvenNumber(1.5 * removeUnit($size-6) * removeUnit($size-medium)) * 1px
  $dimension-large: roundToEvenNumber(1.5 * removeUnit($size-6) * removeUnit($size-large)) * 1px
  +unselectable
  -moz-appearance: none
  -webkit-appearance: none
  background-color: rgba($black, 0.2)
  border: none
  border-radius: 290486px
  cursor: pointer
  display: inline-block
  font-size: $size-normal
  height: $dimension-normal
  outline: none
  position: relative
  transform: rotate(45deg)
  transform-origin: center center
  vertical-align: top
  width: $dimension-normal
  &:before,
  &:after
    background-color: $white
    content: ""
    display: block
    left: 50%
    position: absolute
    top: 50%
    transform: translateX(-50%) translateY(-50%)
  &:before
    height: 2px
    width: 50%
  &:after
    height: 50%
    width: 2px
  &:hover,
  &:focus
    background-color: rgba($black, 0.3)
  &:active
    background-color: rgba($black, 0.4)
  // Sizes
  &.is-small
    height: $dimension-small
    width: $dimension-small
  &.is-medium
    height: $dimension-medium
    width: $dimension-medium
  &.is-large
    height: $dimension-large
    width: $dimension-large

=fa($size, $dimensions)
  display: inline-block
  font-size: $size
  height: $dimensions
  line-height: $dimensions
  text-align: center
  vertical-align: top
  width: $dimensions

=hamburger($dimensions)
  cursor: pointer
  display: block
  height: $dimensions
  position: relative
  width: $dimensions
  span
    background-color: $text
    display: block
    height: 1px
    left: 50%
    margin-left: -7px
    position: absolute
    top: 50%
    transition: none $speed $easing
    transition-property: background, left, opacity, transform
    width: 15px
    &:nth-child(1)
      margin-top: -6px
    &:nth-child(2)
      margin-top: -1px
    &:nth-child(3)
      margin-top: 4px
  &:hover
    background-color: $background
  // Modifers
  &.is-active
    span
      background-color: $link
      &:nth-child(1)
        margin-left: -5px
        transform: rotate(45deg)
        transform-origin: left top
      &:nth-child(2)
        opacity: 0
      &:nth-child(3)
        margin-left: -5px
        transform: rotate(-45deg)
        transform-origin: left bottom

@keyframes spinAround
  from
    transform: rotate(0deg)
  to
    transform: rotate(359deg)

=loader
  animation: spinAround 500ms infinite linear
  border: 2px solid $border
  border-radius: 290486px
  border-right-color: transparent
  border-top-color: transparent
  content: ""
  display: block
  height: 1rem
  position: relative
  width: 1rem

=overflow-touch
  -webkit-overflow-scrolling: touch

=overlay($offset: 0)
  bottom: $offset
  left: $offset
  position: absolute
  right: $offset
  top: $offset

=placeholder
  $placeholders: ':-moz' ':-webkit-input' '-moz' '-ms-input'
  @each $placeholder in $placeholders
    &:#{$placeholder}-placeholder
      @content

=unselectable
  -webkit-touch-callout: none
  -webkit-user-select: none
  -moz-user-select: none
  -ms-user-select: none
  user-select: none

// Responsiveness

$tablet: 769px !default
// 960px container + 40px
$desktop: 1000px !default
// 1152px container + 40
$widescreen: 1192px !default
// 960 and 1152 have been chosen because
// they are divisible by both 12 and 16

=from($device)
  @media screen and (min-width: $device)
    @content

=until($device)
  @media screen and (max-width: $device - 1px)
    @content

=mobile
  @media screen and (max-width: $tablet - 1px)
    @content

=tablet
  @media screen and (min-width: $tablet)
    @content

=tablet-only
  @media screen and (min-width: $tablet) and (max-width: $desktop - 1px)
    @content

=touch
  @media screen and (max-width: $desktop - 1px)
    @content

=desktop
  @media screen and (min-width: $desktop)
    @content

=desktop-only
  @media screen and (min-width: $desktop) and (max-width: $widescreen - 1px)
    @content

=widescreen
  @media screen and (min-width: $widescreen)
    @content
```

controls.sass

```sass
$control-radius: $radius !default
$control-radius-small: $radius-small !default

=control
  -moz-appearance: none
  -webkit-appearance: none
  align-items: center
  border: none
  border-radius: $control-radius
  box-shadow: none
  display: inline-flex
  font-size: $size-normal
  height: 2.285em
  justify-content: flex-start
  line-height: 1.5
  padding-left: 0.75em
  padding-right: 0.75em
  position: relative
  vertical-align: top
  // States
  &:focus,
  &.is-focused,
  &:active,
  &.is-active
    outline: none
  &[disabled],
  &.is-disabled
    pointer-events: none

// The controls sizes use mixins so they can be used at different breakpoints
=control-small
  border-radius: $control-radius-small
  font-size: $size-small
=control-medium
  font-size: $size-medium
=control-large
  font-size: $size-large
```

<a name="purecss" />

## 3. Learn from Pure CSS

<a name="flashcards" />

## 4. CSS Flashcards

This is where I will collect all the things I want you to memorize.

Card 01
```css
html {
  font-size: 62.5%; /* font-size 1em = 10px on default browser settings */
}
```

<a name="links" />

## 5. Good CSS Websites

* [cssreference.io](http://cssreference.io/)
* [MDN CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)