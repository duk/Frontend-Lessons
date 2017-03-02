# Mastering CSS

First, go through some of awesome websites on your own. The biggest hurdle in CSS for me is to grok `positionining`. I found 
[Learn CSS Positioning in Ten Steps](http://www.barelyfitz.com/screencast/html-training/css/positioning/) very helpful.

And I also find this [w3schools.com How TO](http://www.w3schools.com/howto/default.asp) great for breaking a site into modules.

First, I will go through one of the simplest CSS framework called "[skeleton](https://github.com/dhg/Skeleton/blob/master/css/skeleton.css)" and try to understand each line. Then we will learn how to 
group things and memorize them. Also we will go over some popualr CSS processing techniques and BEM.

##### Table of Contents  

1. [Color](#color)
2. [Learn from Skeleton](#skeleton)
3. [Learn from Bulma](#bulma)
4. [Learn from Pure CSS](#purecss)
5. [CSS Flashcards](#flashcards)
6. [Good CSS Websites](#links)

<a name="color" />

## 1. Color

Most bad looking websites are because of misuse of colors. To really understand web design, you have to understand color. So we will learn about color here.

Here are some helpful links that I found

* [Web design 101: color theory](https://webflow.com/blog/web-design-101-color-theory)
* [A Simple Way to Understand Hue, Saturation and Luminosity](https://www.labnol.org/home/hue-saturation-luminosity/20104/) (Watch the embeded Youtube Video)
* [Google Material Design Color](https://material.io/guidelines/style/color.html)


<a name="skeleton" />

## 2. Learn from Skeleton

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

## 3. Learn from Bulma

Let's look at [Bulma](https://github.com/jgthms/bulma). If you go there, first thing you notice is bulma.sass file. So what is "Sass"? Sass stands for "Syntactically Awesome Style Sheets" and there are currently two dialects. One is `.sass` and the other is `scss`. 

>Sass makes CSS fun again. Sass is an extension of CSS, adding nested rules, variables, mixins, selector inheritance, and more. It's translated to well-formatted, standard CSS using the command line tool or a web-framework plugin.
>
>Sass has two syntaxes. The new main syntax (as of Sass 3) is known as "SCSS" (for "Sassy CSS"), and is a superset of CSS's syntax. This means that every valid CSS stylesheet is valid SCSS as well. SCSS files use the extension .scss.
>
>The second, older syntax is known as the indented syntax (or just "Sass"). Inspired by Haml's terseness, it's intended for people who prefer conciseness over similarity to CSS. Instead of brackets and semicolons, it uses the indentation of lines to specify blocks. Although no longer the primary syntax, the indented syntax will continue to be supported. Files in the indented syntax use the extension .sass.


```sass
/*! bulma.io v0.3.1 | MIT License | github.com/jgthms/bulma */
@charset "utf-8"
```

>To explicitly specify the encoding of your stylesheet, use a @charset declaration just like in CSS. Add @charset "encoding-name"; at the beginning of the stylesheet (before any whitespace or comments) and Sass will interpret it as the given encoding. Note that whatever encoding you use, it must be convertible to Unicode.

[`http://127.0.0.1:8080/css/bulma00.html`](http://127.0.0.1:8080/css/bulma00.html)

```sass
@import "sass/utilities/_all"
@import "sass/base/_all"
@import "sass/elements/_all"
@import "sass/components/_all"
@import "sass/grid/_all"
@import "sass/layout/_all"
```

`@import` is just like regular CSS import, but the significant difference is that Sass `@import` is just a syntatic sugar. It just tells SCSS parser to append that file into a main file.


As you can see, sass/scss is great for organizing your project neatly.

You should go read [Sass Documentation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html) first.

Okay. Let's go through every sass file from top to bottom starting with the files under utilities folder 

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

```
`powerNumber($number, $exp): calculates the value of a number exposed to another one. Returns a number.` Best way to undesrstand a function to see how it is used. The only place this function is used in another function, `colorLuminance`

`$` is how to make something variable in Sass.

```sass
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
```
`colorLuminance($color): defines if a color is dark or light. Return a decimal number between 0 and 1 where <= 0.5 is dark and > 0.5 is light.`
```sass
@function findColorInvert($color)
  @if (colorLuminance($color) > 0.55)
    @return rgba(#000, 0.7)
  @else
    @return #fff
```

`findColorInvert($color): returns either 70% transparent black or 100% opaque white depending on the luminance of the color.`

```sass
@function removeUnit($number)
  @if type-of($number) == 'number' and not unitless($number)
    @return $number / ($number * 0 + 1)
  @return $number
```

`removeUnit($number): removes the unit of a Sass number. So "10px" becomes "10" and "3.5rem" returns "3.5". Used for string concatenation.`

```sass
@function roundToEvenNumber($number)
  @return floor($number / 2) * 2
```

`roundToEvenNumber($number): rounds a number to the closest but lower even one. So 23 becomes 22, and 7.5 returns 6.`

The purpose of this function is to have `the delete cross` perfectly centered

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

```

`!default` at the end of every line allows user to override the variable. Aa we learned from color section, `lumenosity(brightness)` can manage three colors; white, black and different shades of grey.

[A Sass `!default` use case](https://robots.thoughtbot.com/sass-default)

```sass
$orange:       hsl(14,  100%, 53%) !default
$yellow:       hsl(48,  100%, 67%) !default

$green:        hsl(141, 71%,  48%) !default
$turquoise:    hsl(171, 100%, 41%) !default

$blue:         hsl(217, 71%,  53%) !default
$purple:       hsl(271, 100%, 71%) !default
$red:          hsl(348, 100%, 61%) !default
```
For different colors, different hue numbers are used. Notice the nubmers amonst similar colors. I suggest you to play with various numbers to get the colors.

```sass
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
```

```sass
// Miscellaneous
$easing: ease-out !default
$radius-small: 2px !default
$radius: 3px !default
$radius-large: 5px !default
$speed: 86ms !default
```

```sass
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

```

```sass
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

>Some things in CSS are a bit tedious to write, especially with CSS3 and the many vendor prefixes that exist. A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. 

```sass
=border-radius($radius)
  -webkit-border-radius: $radius
  -moz-border-radius:    $radius
  -ms-border-radius:     $radius
  border-radius:         $radius

.box
  +border-radius(10px)
```



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

<a name="bulma-base" />

### bulma / sass / base

minireset.sass

```sass
/*! minireset.css v0.0.2 | MIT License | github.com/jgthms/minireset.css */
// Blocks
html,
body,
p,
ol,
ul,
li,
dl,
dt,
dd,
blockquote,
figure,
fieldset,
legend,
textarea,
pre,
iframe,
hr,
h1,
h2,
h3,
h4,
h5,
h6
  margin: 0
  padding: 0

// Headings
h1,
h2,
h3,
h4,
h5,
h6
  font-size: 100%
  font-weight: normal

// List
ul
  list-style: none

// Form
button,
input,
select,
textarea
  margin: 0

// Box sizing
html
  box-sizing: border-box

*
  box-sizing: inherit
  &:before,
  &:after
    box-sizing: inherit

// Media
img,
embed,
object,
audio,
video
  height: auto
  max-width: 100%

// Iframe
iframe
  border: 0

// Table
table
  border-collapse: collapse
  border-spacing: 0

td,
th
  padding: 0
  text-align: left
```

generic.sass

```sass
$body-background: $white !default
$body-size: $size-6 !default

html
  background-color: $body-background
  font-size: $body-size
  -moz-osx-font-smoothing: grayscale
  -webkit-font-smoothing: antialiased
  min-width: 300px
  overflow-x: hidden
  overflow-y: scroll
  text-rendering: optimizeLegibility

article,
aside,
figure,
footer,
header,
hgroup,
section
  display: block

body,
button,
input,
select,
textarea
  font-family: $family-primary

code,
pre
  -moz-osx-font-smoothing: auto
  -webkit-font-smoothing: auto
  font-family: $family-code

body
  color: $text
  font-size: 1rem
  font-weight: $weight-normal
  line-height: 1.5

// Inline

a
  color: $link
  cursor: pointer
  text-decoration: none
  transition: none $speed $easing
  &:hover
    color: $link-hover

code
  background-color: $code-background
  color: $code
  font-size: 0.8em
  font-weight: normal
  padding: 0.25em 0.5em 0.25em

hr
  background-color: $border
  border: none
  display: block
  height: 1px
  margin: 1.5rem 0

img
  max-width: 100%

input[type="checkbox"],
input[type="radio"]
  vertical-align: baseline

small
  font-size: 0.8em

span
  font-style: inherit
  font-weight: inherit

strong
  color: $text-strong
  font-weight: $weight-bold

// Block

pre
  background-color: $pre-background
  color: $pre
  font-size: 0.8em
  white-space: pre
  word-wrap: normal
  code
    background: none
    color: inherit
    display: block
    font-size: 1em
    overflow-x: auto
    padding: 1.25rem 1.5rem

table
  width: 100%
  td,
  th
    text-align: left
    vertical-align: top
  th
    color: $text-strong
```

helpers.sass

```sass
// Display

$displays: 'block' 'flex' 'inline' 'inline-block' 'inline-flex'

@each $display in $displays
  .is-#{$display}
    display: #{$display}
  .is-#{$display}-mobile
    +mobile
      display: #{$display} !important
  .is-#{$display}-tablet
    +tablet
      display: #{$display} !important
  .is-#{$display}-tablet-only
    +tablet-only
      display: #{$display} !important
  .is-#{$display}-touch
    +touch
      display: #{$display} !important
  .is-#{$display}-desktop
    +desktop
      display: #{$display} !important
  .is-#{$display}-desktop-only
    +desktop-only
      display: #{$display} !important
  .is-#{$display}-widescreen
    +widescreen
      display: #{$display} !important

// Float

.is-clearfix
  +clearfix

.is-pulled-left
  float: left

.is-pulled-right
  float: right

// Overflow

.is-clipped
  overflow: hidden !important

// Overlay

.is-overlay
  +overlay

// Text

.has-text-centered
  text-align: center

.has-text-left
  text-align: left

.has-text-right
  text-align: right

// Visibility

.is-hidden
  display: none !important

.is-hidden-mobile
  +mobile
    display: none !important

.is-hidden-tablet
  +tablet
    display: none !important

.is-hidden-tablet-only
  +tablet-only
    display: none !important

.is-hidden-touch
  +touch
    display: none !important

.is-hidden-desktop
  +desktop
    display: none !important

.is-hidden-desktop-only
  +desktop-only
    display: none !important

.is-hidden-widescreen
  +widescreen
    display: none !important

// Other

.is-disabled
  pointer-events: none

.is-marginless
  margin: 0 !important

.is-paddingless
  padding: 0 !important

.is-unselectable
  +unselectable
```

<a name="bulma-elements" />

### bulma / sass / elements

box.sass

```sass
.box
  +block
  background-color: $white
  border-radius: $radius-large
  box-shadow: 0 2px 3px rgba($black, 0.1), 0 0 0 1px rgba($black, 0.1)
  display: block
  padding: 1.25rem

a.box
  &:hover,
  &:focus
    box-shadow: 0 2px 3px rgba($black, 0.1), 0 0 0 1px $link
  &:active
    box-shadow: inset 0 1px 2px rgba($black, 0.2), 0 0 0 1px $link
```

button.sass

```sass
$button: $grey-darker !default
$button-background: $white !default
$button-border: $grey-lighter !default

$button-hover: $link-hover !default
$button-hover-border: $link-hover-border !default

$button-focus: $link-focus !default
$button-focus-border: $link-focus-border !default

$button-active: $link-active !default
$button-active-border: $link-active-border !default

$button-shadow-inset: inset 0 1px 2px rgba($black, 0.2) !default

@function buttonIconSpacing($button-font-size, $icon-width)
  // The button font-size value with no unit
  $button-value: removeUnit($button-font-size)
  // The rem height of the button
  // based on a height of 2.5em
  $button-height: 2.5rem * $button-value // rem
  // The rem total horizontal padding of the button
  $button-horizontal-padding: 2 * 0.75rem * $button-value // rem
  // For the icon center to align with the button center
  // the horizontal padding + the icon width must equal the button height
  // $button-height = $button-horizontal-padding + $icon-width + $difference
  $difference: $button-height - $button-horizontal-padding - $icon-width
  @return $difference / 2

=button-icon($button-font-size)
  $small-offset: buttonIconSpacing($button-font-size, 1rem)
  $normal-offset: buttonIconSpacing($button-font-size, 1.5rem)
  $medium-offset: buttonIconSpacing($button-font-size, 2rem)
  $large-offset: buttonIconSpacing($button-font-size, 3rem)
  .icon
    &:first-child:not(:last-child)
      margin-left: $normal-offset
      margin-right: $button-font-size / 2
    &:last-child:not(:first-child)
      margin-left: $button-font-size / 2
      margin-right: $normal-offset
    &:first-child:last-child
      // The -1px is to account for the button 1px border
      margin-left: calc(-1px + #{$normal-offset})
      margin-right: calc(-1px + #{$normal-offset})
    &.is-small
      &:first-child:not(:last-child)
        margin-left: $small-offset
      &:last-child:not(:first-child)
        margin-right: $small-offset
      &:first-child:last-child
        margin-left: calc(-1px + #{$small-offset})
        margin-right: calc(-1px + #{$small-offset})
    &.is-medium
      &:first-child:not(:last-child)
        margin-left: $medium-offset
      &:last-child:not(:first-child)
        margin-right: $medium-offset
      &:first-child:last-child
        margin-left: calc(-1px + #{$medium-offset})
        margin-right: calc(-1px + #{$medium-offset})
    &.is-large
      &:first-child:not(:last-child)
        margin-left: $large-offset
      &:last-child:not(:first-child)
        margin-right: $large-offset
      &:first-child:last-child
        margin-left: calc(-1px + #{$large-offset})
        margin-right: calc(-1px + #{$large-offset})

// The button sizes use mixins so they can be used at different breakpoints
=button-small
  border-radius: $radius-small
  font-size: $size-small
  +button-icon($size-small)
=button-medium
  font-size: $size-medium
  +button-icon($size-medium)
=button-large
  font-size: $size-large
  +button-icon($size-large)

.button
  +control
  +unselectable
  background-color: $button-background
  border: 1px solid $button-border
  color: $button
  cursor: pointer
  justify-content: center
  padding-left: 0.75em
  padding-right: 0.75em
  text-align: center
  white-space: nowrap
  strong
    color: inherit
  +button-icon($size-normal)
  // States
  &:hover,
  &.is-hovered
    border-color: $button-hover-border
    color: $button-hover
  &:focus,
  &.is-focused
    border-color: $button-focus-border
    box-shadow: 0 0 0.5em rgba($button-focus-border, 0.25)
    color: $button-focus
  &:active,
  &.is-active
    border-color: $button-active-border
    box-shadow: $button-shadow-inset
    color: $button-active
  // Colors
  &.is-link
    background-color: transparent
    border-color: transparent
    color: $text
    text-decoration: underline
    &:hover,
    &.is-hovered,
    &:focus,
    &.is-focused,
    &:active,
    &.is-active
      background-color: $background
      color: $text-strong
  @each $name, $pair in $colors
    $color: nth($pair, 1)
    $color-invert: nth($pair, 2)
    &.is-#{$name}
      background-color: $color
      border-color: transparent
      color: $color-invert
      &:hover,
      &.is-hovered
        background-color: darken($color, 2.5%)
        border-color: transparent
        color: $color-invert
      &:focus,
      &.is-focused
        border-color: transparent
        box-shadow: 0 0 0.5em rgba($color, 0.25)
        color: $color-invert
      &:active,
      &.is-active
        background-color: darken($color, 5%)
        border-color: transparent
        box-shadow: $button-shadow-inset
        color: $color-invert
      &.is-inverted
        background-color: $color-invert
        color: $color
        &:hover
          background-color: darken($color-invert, 5%)
      &.is-loading
        &:after
          border-color: transparent transparent $color-invert $color-invert !important
      &.is-outlined
        background-color: transparent
        border-color: $color
        color: $color
        &:hover,
        &:focus
          background-color: $color
          border-color: $color
          color: $color-invert
        &.is-loading
          &:after
            border-color: transparent transparent $color $color !important
      &.is-inverted.is-outlined
        background-color: transparent
        border-color: $color-invert
        color: $color-invert
        &:hover,
        &:focus
          background-color: $color-invert
          color: $color
  // Sizes
  &.is-small
    +button-small
  &.is-medium
    +button-medium
  &.is-large
    +button-large
  // Modifiers
  &[disabled],
  &.is-disabled
    opacity: 0.5
  &.is-fullwidth
    display: flex
    width: 100%
  &.is-loading
    color: transparent !important
    pointer-events: none
    &:after
      +loader
      +center(16px)
      position: absolute !important
```
content.sass

```sass
.content
  +block
  color: $text
  // Inline
  li + li
    margin-top: 0.25em
  // Block
  p,
  ol,
  ul,
  blockquote,
  table
    &:not(:last-child)
      margin-bottom: 1em
  h1,
  h2,
  h3,
  h4,
  h5,
  h6
    color: $text-strong
    font-weight: $weight-normal
    line-height: 1.125
  h1
    font-size: 2em
    margin-bottom: 0.5em
    &:not(:first-child)
      margin-top: 1em
  h2
    font-size: 1.75em
    margin-bottom: 0.5714em
    &:not(:first-child)
      margin-top: 1.1428em
  h3
    font-size: 1.5em
    margin-bottom: 0.6666em
    &:not(:first-child)
      margin-top: 1.3333em
  h4
    font-size: 1.25em
    margin-bottom: 0.8em
  h5
    font-size: 1.125em
    margin-bottom: 0.8888em
  h6
    font-size: 1em
    margin-bottom: 1em
  blockquote
    background-color: $background
    border-left: 5px solid $border
    padding: 1.25em 1.5em
  ol
    list-style: decimal outside
    margin-left: 2em
    margin-right: 2em
    margin-top: 1em
  ul
    list-style: disc outside
    margin-left: 2em
    margin-right: 2em
    margin-top: 1em
    ul
      list-style-type: circle
      margin-top: 0.5em
      ul
        list-style-type: square
  table
    width: 100%
    td,
    th
      border: 1px solid $border
      border-width: 0 0 1px
      padding: 0.5em 0.75em
      vertical-align: top
    th
      color: $text-strong
      text-align: left
    tr
      &:hover
        background-color: $background
    thead
      td,
      th
        border-width: 0 0 2px
        color: $text-strong
    tfoot
      td,
      th
        border-width: 2px 0 0
        color: $text-strong
    tbody
      tr
        &:last-child
          td,
          th
            border-bottom-width: 0
  // Sizes
  &.is-small
    font-size: $size-small
  &.is-medium
    font-size: $size-medium
  &.is-large
    font-size: $size-large
```

form.sass
```sass
$input:                     $grey-darker !default
$input-background:          $white !default
$input-border:              $grey-lighter !default

$input-hover:               $grey-darker !default
$input-hover-border:        $grey-light !default

$input-focus:               $grey-darker !default
$input-focus-border:        $link !default

$input-disabled:            $text-light !default
$input-disabled-background: $background !default
$input-disabled-border:     $background !default

$input-arrow:               $link !default

$input-icon:                $grey-lighter !default
$input-icon-active:         $grey !default

$input-radius:              $radius !default

=input
  +control
  background-color: $input-background
  border: 1px solid $input-border
  color: $input
  &:hover,
  &.is-hovered
    border-color: $input-hover-border
  &:focus,
  &.is-focused,
  &:active,
  &.is-active
    border-color: $input-focus-border
  &[disabled],
  &.is-disabled
    background-color: $input-disabled-background
    border-color: $input-disabled-border
    box-shadow: none
    color: $input-disabled
    +placeholder
      color: rgba($input, 0.3)

.input,
.textarea
  +input
  box-shadow: inset 0 1px 2px rgba($black, 0.1)
  max-width: 100%
  width: 100%
  &[type="search"]
    border-radius: 290486px
  // Colors
  @each $name, $pair in $colors
    $color: nth($pair, 1)
    &.is-#{$name}
      border-color: $color
  // Sizes
  &.is-small
    +control-small
  &.is-medium
    +control-medium
  &.is-large
    +control-large
  // Modifiers
  &.is-fullwidth
    display: block
    width: 100%
  &.is-inline
    display: inline
    width: auto

.textarea
  display: block
  line-height: 1.25
  max-height: 600px
  max-width: 100%
  min-height: 120px
  min-width: 100%
  padding: 10px
  resize: vertical

.checkbox,
.radio
  align-items: center
  cursor: pointer
  display: inline-flex
  flex-wrap: wrap
  justify-content: flex-start
  position: relative
  vertical-align: top
  input
    cursor: pointer
    margin-right: 0.5em
  &:hover
    color: $input-hover
  &.is-disabled
    color: $input-disabled
    pointer-events: none
    input
      pointer-events: none

.radio
  & + .radio
    margin-left: 0.5em

.select
  display: inline-block
  height: 2.5em
  position: relative
  vertical-align: top
  &:after
    +arrow($input-arrow)
    margin-top: -0.375em
    right: 1.125em
    top: 50%
    z-index: 4
  select
    +input
    cursor: pointer
    display: block
    font-size: 1em
    outline: none
    padding-right: 2.5em
    &:hover
      border-color: $input-hover-border
    &::ms-expand
      display: none
  // States
  &:hover
    &:after
      border-color: $input-hover
  // Sizes
  &.is-small
    +control-small
  &.is-medium
    +control-medium
  &.is-large
    +control-large
  // Modifiers
  &.is-fullwidth
    width: 100%
    select
      width: 100%

.label
  color: $input
  display: block
  font-weight: bold
  &:not(:last-child)
    margin-bottom: 0.5em

.help
  display: block
  font-size: $size-small
  margin-top: 5px
  @each $name, $pair in $colors
    $color: nth($pair, 1)
    &.is-#{$name}
      color: $color

// Containers

.control-label
  +mobile
    margin-bottom: 0.5em
  +tablet
    flex-basis: 0
    flex-grow: 1
    flex-shrink: 0
    margin-right: 1.5em
    padding-top: 0.5em
    text-align: right

.control
  position: relative
  text-align: left
  &:not(:last-child)
    margin-bottom: 0.75rem
  // Modifiers
  &.has-addons
    display: flex
    justify-content: flex-start
    .button,
    .input,
    .select
      border-radius: 0
      margin-right: -1px
      width: auto
      &:hover
        z-index: 2
      &:focus,
      &:active
        z-index: 3
      &:first-child
        border-radius: $input-radius 0 0 $input-radius
        select
          border-radius: $input-radius 0 0 $input-radius
      &:last-child
        border-radius: 0 $input-radius $input-radius 0
        select
          border-radius: 0 $input-radius $input-radius 0
      &.is-expanded
        flex-grow: 1
        flex-shrink: 0
    .select select
      &:hover
        z-index: 2
      &:focus,
      &:active
        z-index: 3
    &.has-addons-centered
      justify-content: center
    &.has-addons-right
      justify-content: flex-end
    &.has-addons-fullwidth
      .button,
      .input,
      .select
        flex-grow: 1
        flex-shrink: 0
  &.has-icon
    .icon
      color: $input-icon
      pointer-events: none
      position: absolute
      top: ($size-normal * 2.5) / 2
      z-index: 4
    .input
      &:focus
        & + .icon
          color: $input-icon-active
      &.is-small
        & + .icon
          top: ($size-small * 2.5) / 2
      &.is-medium
        & + .icon
          top: ($size-medium * 2.5) / 2
      &.is-large
        & + .icon
          top: ($size-large * 2.5) / 2
    &:not(.has-icon-right)
      .icon
        left: ($size-normal * 2.5) / 2
        transform: translateX(-50%) translateY(-50%)
      .input
        padding-left: 2.5em
        &.is-small
          & + .icon
            left: ($size-small * 2.5) / 2
        &.is-medium
          & + .icon
            left: ($size-medium * 2.5) / 2
        &.is-large
          & + .icon
            left: ($size-large * 2.5) / 2
    &.has-icon-right
      .icon
        right: ($size-normal * 2.5) / 2
        transform: translateX(50%) translateY(-50%)
      .input
        padding-right: 2.5em
        &.is-small
          & + .icon
            right: ($size-small * 2.5) / 2
        &.is-medium
          & + .icon
            right: ($size-medium * 2.5) / 2
        &.is-large
          & + .icon
            right: ($size-large * 2.5) / 2
  &.is-grouped
    display: flex
    justify-content: flex-start
    & > .control
      flex-basis: 0
      flex-shrink: 0
      &:not(:last-child)
        margin-bottom: 0
        margin-right: 0.75rem
      &.is-expanded
        flex-grow: 1
        flex-shrink: 1
    &.is-grouped-centered
      justify-content: center
    &.is-grouped-right
      justify-content: flex-end
  &.is-horizontal
    +tablet
      display: flex
      & > .control
        display: flex
        flex-basis: 0
        flex-grow: 5
        flex-shrink: 1
  &.is-loading
    &:after
      +loader
      position: absolute !important
      right: 0.75em
      top: 0.75em
```

icon.sass

```sass
.icon
  +fa(21px, 1.5rem)
  .fa
    font-size: inherit
    line-height: inherit
  // Sizes
  &.is-small
    +fa(14px, 1rem)
  &.is-medium
    +fa(28px, 2rem)
  &.is-large
    +fa(42px, 3rem)
```
image.sass

```sass
$dimensions: 16 24 32 48 64 96 128

.image
  display: block
  position: relative
  img
    display: block
    height: auto
    width: 100%
  // Ratio
  &.is-square,
  &.is-1by1,
  &.is-4by3,
  &.is-3by2,
  &.is-16by9,
  &.is-2by1
    img
      +overlay
      height: 100%
      width: 100%
  &.is-square,
  &.is-1by1
    padding-top: 100%
  &.is-4by3
    padding-top: 75%
  &.is-3by2
    padding-top: 66.6666%
  &.is-16by9
    padding-top: 56.25%
  &.is-2by1
    padding-top: 50%
  // Sizes
  @each $dimension in $dimensions
    &.is-#{$dimension}x#{$dimension}
      height: $dimension * 1px
      width: $dimension * 1px
```

notification.sass

```sass
.notification
  +block
  background-color: $background
  border-radius: $radius
  padding: 1.25rem 2.5rem 1.25rem 1.5rem
  position: relative
  code,
  pre
    background: $white
  pre code
    background: transparent
  .delete
    position: absolute
    right: 0.5em
    top: 0.5em
  .title,
  .subtitle,
  .content
    color: inherit
  // Colors
  @each $name, $pair in $colors
    $color: nth($pair, 1)
    $color-invert: nth($pair, 2)
    &.is-#{$name}
      background-color: $color
      color: $color-invert
```

other.sass

```sass
.block
  +block

.container
  position: relative
  +desktop
    margin: 0 auto
    max-width: $desktop - 40px // 960px
    // Modifiers
    &.is-fluid
      margin: 0 20px
      max-width: none
  +widescreen
    max-width: $widescreen - 40px // 1152px

.delete
  +delete

.fa
  font-size: 21px
  text-align: center
  vertical-align: top

.heading
  display: block
  font-size: 11px
  letter-spacing: 1px
  margin-bottom: 5px
  text-transform: uppercase

.highlight
  +block
  font-weight: $weight-normal
  max-width: 100%
  overflow: hidden
  padding: 0
  pre
    overflow: auto
    max-width: 100%

.loader
  +loader

.number
  align-items: center
  background-color: $background
  border-radius: 290486px
  display: inline-flex
  font-size: $size-medium
  height: 2em
  justify-content: center
  margin-right: 1.5rem
  min-width: 2.5em
  padding: 0.25rem 0.5rem
  text-align: center
  vertical-align: top
```

progress.sass

```sass
.progress
  +block
  -moz-appearance: none
  -webkit-appearance: none
  border: none
  border-radius: 290486px
  display: block
  height: $size-normal
  overflow: hidden
  padding: 0
  width: 100%
  &::-webkit-progress-bar
    background-color: $border
  &::-webkit-progress-value
    background-color: $text
  &::-moz-progress-bar
    background-color: $text
  // Colors
  @each $name, $pair in $colors
    $color: nth($pair, 1)
    &.is-#{$name}
      &::-webkit-progress-value
        background-color: $color
      &::-moz-progress-bar
        background-color: $color
  // Sizes
  &.is-small
    height: $size-small
  &.is-medium
    height: $size-medium
  &.is-large
    height: $size-large
```

table.sass

```sass
$table:                           $grey-darker !default
$table-background:                $white !default
$table-border:                    $grey-lighter !default

$table-head:                      $grey !default

$table-row-hover-background:      $white-bis !default
$table-row-even-background:       $white-bis !default
$table-row-even-hover-background: $white-ter !default

.table
  background-color: $table-background
  color: $table
  margin-bottom: 1.5rem
  width: 100%
  td,
  th
    border: 1px solid $table-border
    border-width: 0 0 1px
    padding: 0.5em 0.75em
    vertical-align: top
    // Modifiers
    &.is-narrow
      white-space: nowrap
      width: 1%
  th
    color: $text-strong
    text-align: left
  tr
    &:hover
      background-color: $table-row-hover-background
  thead
    td,
    th
      border-width: 0 0 2px
      color: $table-head
  tfoot
    td,
    th
      border-width: 2px 0 0
      color: $table-head
  tbody
    tr
      &:last-child
        td,
        th
          border-bottom-width: 0
  // Modifiers
  &.is-bordered
    td,
    th
      border-width: 1px
    tr
      &:last-child
        td,
        th
          border-bottom-width: 1px
  &.is-narrow
    td,
    th
      padding: 0.25em 0.5em
  &.is-striped
    tbody
      tr
        &:nth-child(even)
          background-color: $table-row-even-background
          &:hover
            background-color: $table-row-even-hover-background
```

tag.sass

```sass
.tag
  align-items: center
  background-color: $background
  border-radius: 290486px
  color: $text
  display: inline-flex
  font-size: $size-small
  height: 2em
  justify-content: center
  line-height: 1.5
  padding-left: 0.875em
  padding-right: 0.875em
  vertical-align: top
  white-space: nowrap
  .delete
    margin-left: 0.25em
    margin-right: -0.5em
  // Colors
  @each $name, $pair in $colors
    $color: nth($pair, 1)
    $color-invert: nth($pair, 2)
    &.is-#{$name}
      background-color: $color
      color: $color-invert
  // Sizes
  &.is-medium
    font-size: $size-normal
  &.is-large
    font-size: $size-medium
```

title.sass

```sass
$title:             $grey-darker !default
$title-size:        $size-3 !default
$title-weight:      $weight-light !default
$title-weight-bold: $weight-semibold !default

$subtitle:          $grey-dark !default
$subtitle-size:     $size-5 !default
$subtitle-strong:   $grey-darker !default
$subtitle-weight:   $weight-light !default

.title,
.subtitle
  +block
  word-break: break-word
  em,
  span
    font-weight: $title-weight
  strong
    font-weight: $title-weight-bold
  .tag
    vertical-align: middle

.title
  color: $title
  font-size: $title-size
  font-weight: $title-weight
  line-height: 1.125
  strong
    color: inherit
  & + .highlight
    margin-top: -0.75rem
  & + .subtitle
    margin-top: -1.25rem
  // Colors
  @each $size in $sizes
    $i: index($sizes, $size)
    &.is-#{$i}
      font-size: $size

.subtitle
  color: $subtitle
  font-size: $subtitle-size
  font-weight: $subtitle-weight
  line-height: 1.25
  strong
    color: $subtitle-strong
  & + .title
    margin-top: -1.5rem
  // Colors
  @each $size in $sizes
    $i: index($sizes, $size)
    &.is-#{$i}
      font-size: $size
```
<a name="bulma-components" />

### bulma / sass / components

```sass
.card-header
  align-items: stretch
  box-shadow: 0 1px 2px rgba($black, 0.1)
  display: flex

.card-header-title
  align-items: center
  color: $text-strong
  display: flex
  flex-grow: 1
  font-weight: $weight-bold
  padding: 0.75rem

.card-header-icon
  align-items: center
  cursor: pointer
  display: flex
  justify-content: center
  padding: 0.75rem

.card-image
  display: block
  position: relative

.card-content
  padding: 1.5rem
  .title + .subtitle
    margin-top: -1.5rem

.card-footer
  border-top: 1px solid $border
  align-items: stretch
  display: flex

.card-footer-item
  align-items: center
  display: flex
  flex-basis: 0
  flex-grow: 1
  flex-shrink: 0
  justify-content: center
  padding: 0.75rem
  &:not(:last-child)
    border-right: 1px solid $border

.card
  background-color: $white
  box-shadow: 0 2px 3px rgba($black, 0.1), 0 0 0 1px rgba($black, 0.1)
  color: $text
  max-width: 100%
  position: relative
  .media:not(:last-child)
    margin-bottom: 0.75rem
```

level.sass

```sass
.level-item
  align-items: center
  display: flex
  flex-basis: auto
  flex-grow: 0
  flex-shrink: 0
  justify-content: center
  .title,
  .subtitle
    margin-bottom: 0
  // Responsiveness
  +mobile
    &:not(:last-child)
      margin-bottom: 0.75rem

.level-left,
.level-right
  flex-basis: auto
  flex-grow: 0
  flex-shrink: 0
  .level-item
    &:not(:last-child)
      margin-right: 0.75rem
    // Modifiers
    &.is-flexible
      flex-grow: 1

.level-left
  align-items: center
  justify-content: flex-start
  // Responsiveness
  +mobile
    & + .level-right
      margin-top: 1.5rem
  +tablet
    display: flex

.level-right
  align-items: center
  justify-content: flex-end
  // Responsiveness
  +tablet
    display: flex

.level
  +block
  align-items: center
  justify-content: space-between
  code
    border-radius: $radius
  img
    display: inline-block
    vertical-align: top
  // Modifiers
  &.is-mobile
    display: flex
    & > .level-item
      &:not(:last-child)
        margin-bottom: 0
      &:not(.is-narrow)
        flex-grow: 1
  // Responsiveness
  +tablet
    display: flex
    & > .level-item
      &:not(.is-narrow)
        flex-grow: 1
```

media.sass

```sass
.media-left,
.media-right
  flex-basis: auto
  flex-grow: 0
  flex-shrink: 0

.media-left
  margin-right: 1rem

.media-right
  margin-left: 1rem

.media-content
  flex-basis: auto
  flex-grow: 1
  flex-shrink: 1
  text-align: left

.media
  align-items: flex-start
  display: flex
  text-align: left
  .content:not(:last-child)
    margin-bottom: 0.75rem
  .media
    border-top: 1px solid rgba($border, 0.5)
    display: flex
    padding-top: 0.75rem
    .content:not(:last-child),
    .control:not(:last-child)
      margin-bottom: 0.5rem
    .media
      padding-top: 0.5rem
      & + .media
        margin-top: 0.5rem
  & + .media
    border-top: 1px solid rgba($border, 0.5)
    margin-top: 1rem
    padding-top: 1rem
  // Sizes
  &.is-large
    & + .media
      margin-top: 1.5rem
      padding-top: 1.5rem
```

menu.sass

```sass
.menu
  font-size: $size-normal

.menu-list
  line-height: 1.25
  a
    border-radius: $radius-small
    color: $text
    display: block
    padding: 0.5em 0.75em
    &:hover
      background-color: $background
      color: $link
    // Modifiers
    &.is-active
      background-color: $link
      color: $link-invert
  li
    ul
      border-left: 1px solid $border
      margin: 0.75em
      padding-left: 0.75em

.menu-label
  color: $text-light
  font-size: 0.8em
  letter-spacing: 0.1em
  text-transform: uppercase
  &:not(:first-child)
    margin-top: 1em
  &:not(:last-child)
    margin-bottom: 1em
```

message.sass

```sass
.message
  +block
  background-color: $background
  border-radius: $radius
  font-size: $size-normal
  // Colors
  @each $name, $pair in $colors
    $color: nth($pair, 1)
    $color-invert: nth($pair, 2)
    $color-lightning: max((100% - lightness($color)) - 2%, 0%)
    $color-luminance: colorLuminance($color)
    $darken-percentage: $color-luminance * 70%
    $desaturate-percentage: $color-luminance * 30%
    &.is-#{$name}
      background-color: lighten($color, $color-lightning)
      .message-header
        background-color: $color
        color: $color-invert
      .message-body
        border-color: $color
        color: desaturate(darken($color, $darken-percentage), $desaturate-percentage)

.message-header
  align-items: center
  background-color: $text
  border-radius: $radius $radius 0 0
  color: $text-invert
  display: flex
  justify-content: space-between
  line-height: 1.25
  padding: 0.5em 0.75em
  position: relative
  a,
  strong
    color: inherit
  a
    text-decoration: underline
  .delete
    flex-grow: 0
    flex-shrink: 0
    margin-left: 0.75em
  & + .message-body
    border-top-left-radius: 0
    border-top-right-radius: 0
    border-top: none

.message-body
  border: 1px solid $border
  border-radius: $radius
  color: $text
  padding: 1em 1.25em
  a,
  strong
    color: inherit
  a
    text-decoration: underline
  code,
  pre
    background: $white
  pre code
    background: transparent
```

modal.sass

```sass
.modal-background
  +overlay
  background-color: rgba($black, 0.86)

.modal-content,
.modal-card
  margin: 0 20px
  max-height: calc(100vh - 160px)
  overflow: auto
  position: relative
  width: 100%
  // Responsiveness
  +tablet
    margin: 0 auto
    max-height: calc(100vh - 40px)
    width: 640px

.modal-close
  +delete
  background: none
  height: 40px
  position: fixed
  right: 20px
  top: 20px
  width: 40px

.modal-card
  display: flex
  flex-direction: column
  max-height: calc(100vh - 40px)
  overflow: hidden

.modal-card-head,
.modal-card-foot
  align-items: center
  background-color: $background
  display: flex
  flex-shrink: 0
  justify-content: flex-start
  padding: 20px
  position: relative

.modal-card-head
  border-bottom: 1px solid $border
  border-top-left-radius: $radius-large
  border-top-right-radius: $radius-large

.modal-card-title
  color: $text-strong
  flex-grow: 1
  flex-shrink: 0
  font-size: $size-4
  line-height: 1

.modal-card-foot
  border-bottom-left-radius: $radius-large
  border-bottom-right-radius: $radius-large
  border-top: 1px solid $border
  .button
    &:not(:last-child)
      margin-right: 10px

.modal-card-body
  +overflow-touch
  background-color: $white
  flex-grow: 1
  flex-shrink: 1
  overflow: auto
  padding: 20px

.modal
  +overlay
  align-items: center
  display: none
  justify-content: center
  overflow: hidden
  position: fixed
  z-index: 1986
  // Modifiers
  &.is-active
    display: flex
```

nav.sass

```sass
$nav-height: 3.5rem !default

// Components

.nav-toggle
  +hamburger($nav-height)
  // Responsiveness
  +tablet
    display: none

.nav-item
  align-items: center
  display: flex
  flex-grow: 0
  flex-shrink: 0
  font-size: $size-normal
  justify-content: center
  padding: 0.5rem 0.75rem
  a
    flex-grow: 1
    flex-shrink: 0
  img
    max-height: 1.75rem
  .button + .button
    margin-left: 0.75rem
  .tag
    &:first-child:not(:last-child)
      margin-right: 0.5rem
    &:last-child:not(:first-child)
      margin-left: 0.5rem
  // Responsiveness
  +mobile
    justify-content: flex-start

.nav-item a,
a.nav-item
  color: $text-light
  &:hover
    color: $link-hover
  // Modifiers
  &.is-active
    color: $link-active
  &.is-tab
    border-bottom: 1px solid transparent
    border-top: 1px solid transparent
    padding-bottom: calc(0.5rem - 1px)
    padding-left: 1rem
    padding-right: 1rem
    padding-top: calc(0.5rem - 1px)
    &:hover
      border-bottom-color: $primary
      border-top-color: transparent
    &.is-active
      border-bottom: 3px solid $primary
      color: $primary
      padding-bottom: calc(0.5rem - 3px)
  // Responsiveness
  +desktop
    &.is-brand
      padding-left: 0

// Containers

.nav-menu
  // Responsiveness
  +mobile
    background-color: $white
    box-shadow: 0 4px 7px rgba($black, 0.1)
    left: 0
    display: none
    right: 0
    top: 100%
    position: absolute
    .nav-item
      border-top: 1px solid rgba($border, 0.5)
      padding: 0.75rem
    &.is-active
      display: block
  +tablet-only
    padding-right: 1.5rem


.nav-left,
.nav-right
  align-items: stretch
  flex-basis: 0
  flex-grow: 1
  flex-shrink: 0

.nav-left
  display: flex
  justify-content: flex-start
  overflow: hidden
  overflow-x: auto
  white-space: nowrap

.nav-center
  align-items: stretch
  display: flex
  flex-grow: 0
  flex-shrink: 0
  justify-content: center
  margin-left: auto
  margin-right: auto

.nav-right
  justify-content: flex-end
  // Responsiveness
  +tablet
    display: flex

// Main container

.nav
  align-items: stretch
  background-color: $white
  display: flex
  min-height: $nav-height
  position: relative
  text-align: center
  z-index: 2
  & > .container
    align-items: stretch
    display: flex
    min-height: $nav-height
    width: 100%
  // Modifiers
  &.has-shadow
    box-shadow: 0 2px 3px rgba($black, 0.1)
```

pagination.sass

```sass
$pagination: $grey-darker !default
$pagination-background: $white !default
$pagination-border: $grey-lighter !default

$pagination-hover: $link-hover !default
$pagination-hover-border: $link-hover-border !default

$pagination-focus: $link-focus !default
$pagination-focus-border: $link-focus-border !default

$pagination-active: $link-active !default
$pagination-active-border: $link-active-border !default

$pagination-disabled: $grey !default
$pagination-disabled-background: $grey-lighter !default
$pagination-disabled-border: $grey-lighter !default

$pagination-current: $link-invert !default
$pagination-current-background: $link !default
$pagination-current-border: $link !default

$pagination-ellipsis: $grey-light !default

$pagination-shadow-inset: inset 0 1px 2px rgba($black, 0.2)

.pagination,
.pagination-list
  align-items: center
  display: flex
  justify-content: center
  text-align: center

.pagination-previous,
.pagination-next,
.pagination-link,
.pagination-ellipsis
  +control
  +unselectable
  font-size: 0.875rem
  padding-left: 0.5em
  padding-right: 0.5em
  justify-content: center
  text-align: center

.pagination-previous,
.pagination-next,
.pagination-link
  border: 1px solid $pagination-border
  min-width: 2.5em
  &:hover
    border-color: $pagination-hover-border
    color: $pagination-hover
  &:focus
    border-color: $pagination-focus-border
  &:active
    box-shadow: $pagination-shadow-inset
  &[disabled],
  &.is-disabled
    background: $pagination-disabled-background
    color: $pagination-disabled
    opacity: 0.5
    pointer-events: none

.pagination-previous,
.pagination-next
  padding-left: 0.75em
  padding-right: 0.75em

.pagination-link
  &.is-current
    background-color: $pagination-current-background
    border-color: $pagination-current-border
    color: $pagination-current

.pagination-ellipsis
  color: $pagination-ellipsis
  pointer-events: none

.pagination-list
  li
    &:not(:first-child)
      margin-left: 0.375rem

+mobile
  .pagination
    flex-wrap: wrap
  .pagination-previous,
  .pagination-next
    flex-grow: 1
    flex-shrink: 1
    width: calc(50% - 0.375rem)
  .pagination-next
    margin-left: 0.75rem
  .pagination-list
    margin-top: 0.75rem
    li
      flex-grow: 1
      flex-shrink: 1

+tablet
  .pagination-list
    flex-grow: 1
    flex-shrink: 1
    justify-content: flex-start
    order: 1
  .pagination-previous,
  .pagination-next
    margin-left: 0.75rem
  .pagination-previous
    order: 2
  .pagination-next
    order: 3
  .pagination
    justify-content: space-between
    &.is-centered
      .pagination-previous
        margin-left: 0
        order: 1
      .pagination-list
        justify-content: center
        order: 2
      .pagination-next
        order: 3
    &.is-right
      .pagination-previous
        margin-left: 0
        order: 1
      .pagination-next
        order: 2
        margin-right: 0.75rem
      .pagination-list
        justify-content: flex-end
        order: 3
```

panel.sass

```sass
.panel
  font-size: $size-normal
  &:not(:last-child)
    margin-bottom: 1.5rem

.panel-heading,
.panel-tabs,
.panel-block
  border-bottom: 1px solid $border
  border-left: 1px solid $border
  border-right: 1px solid $border
  &:first-child
    border-top: 1px solid $border

.panel-heading
  background-color: $background
  border-radius: $radius $radius 0 0
  color: $text-strong
  font-size: 1.25em
  font-weight: $weight-light
  line-height: 1.25
  padding: 0.5em 0.75em

.panel-tabs
  align-items: flex-end
  display: flex
  font-size: 0.875em
  justify-content: center
  a
    border-bottom: 1px solid $border
    margin-bottom: -1px
    padding: 0.5em
    // Modifiers
    &.is-active
      border-bottom-color: $link-active-border
      color: $link-active

.panel-list
  a
    color: $text
    &:hover
      color: $link

.panel-block
  align-items: center
  color: $text-strong
  display: flex
  justify-content: flex-start
  padding: 0.5em 0.75em
  input[type="checkbox"]
    margin-right: 0.75em
  & > .control
    flex-grow: 1
    flex-shrink: 1
    width: 100%
  &.is-active
    border-left-color: $link
    color: $link-active
    .panel-icon
      color: $link

a.panel-block,
label.panel-block
  cursor: pointer
  &:hover
    background-color: $background

.panel-icon
  +fa(14px, 1em)
  color: $text-light
  margin-right: 0.75em
  .fa
    font-size: inherit
    line-height: inherit
```

tab.sass

```sass
.tabs
  +block
  +unselectable
  align-items: stretch
  display: flex
  font-size: $size-normal
  justify-content: space-between
  overflow: hidden
  overflow-x: auto
  white-space: nowrap
  a
    align-items: center
    border-bottom: 1px solid $border
    color: $text
    display: flex
    justify-content: center
    margin-bottom: -1px
    padding: 0.5em 1em
    vertical-align: top
    &:hover
      border-bottom-color: $text-strong
      color: $text-strong
  li
    display: block
    &.is-active
      a
        border-bottom-color: $primary
        color: $primary
  ul
    align-items: center
    border-bottom: 1px solid $border
    display: flex
    flex-grow: 1
    flex-shrink: 0
    justify-content: flex-start
    &.is-left
      padding-right: 0.75em
    &.is-center
      flex: none
      justify-content: center
      padding-left: 0.75em
      padding-right: 0.75em
    &.is-right
      justify-content: flex-end
      padding-left: 0.75em
  .icon
    &:first-child
      margin-right: 0.5em
    &:last-child
      margin-left: 0.5em
  // Alignment
  &.is-centered
    ul
      justify-content: center
  &.is-right
    ul
      justify-content: flex-end
  // Styles
  &.is-boxed
    a
      border: 1px solid transparent
      border-radius: $radius $radius 0 0
      &:hover
        background-color: $background
        border-bottom-color: $border
    li
      &.is-active
        a
          background-color: $white
          border-color: $border
          border-bottom-color: transparent !important
  &.is-fullwidth
    li
      flex-grow: 1
      flex-shrink: 0
  &.is-toggle
    a
      border: 1px solid $border
      margin-bottom: 0
      position: relative
      &:hover
        background-color: $background
        border-color: $border-hover
        z-index: 2
    li
      & + li
        margin-left: -1px
      &:first-child a
        border-radius: $radius 0 0 $radius
      &:last-child a
        border-radius: 0 $radius $radius 0
      &.is-active
        a
          background-color: $primary
          border-color: $primary
          color: $primary-invert
          z-index: 1
    ul
      border-bottom: none
  // Sizes
  &.is-small
    font-size: $size-small
  &.is-medium
    font-size: $size-medium
  &.is-large
    font-size: $size-large
```

<a name="bulma-grid" />

### bulma / sass / grid

columns.sass

```sass
.column
  display: block
  flex-basis: 0
  flex-grow: 1
  flex-shrink: 1
  padding: 0.75rem
  .columns.is-mobile > &.is-narrow
    flex: none
  .columns.is-mobile > &.is-full
    flex: none
    width: 100%
  .columns.is-mobile > &.is-three-quarters
    flex: none
    width: 75%
  .columns.is-mobile > &.is-two-thirds
    flex: none
    width: 66.6666%
  .columns.is-mobile > &.is-half
    flex: none
    width: 50%
  .columns.is-mobile > &.is-one-third
    flex: none
    width: 33.3333%
  .columns.is-mobile > &.is-one-quarter
    flex: none
    width: 25%
  .columns.is-mobile > &.is-offset-three-quarters
    margin-left: 75%
  .columns.is-mobile > &.is-offset-two-thirds
    margin-left: 66.6666%
  .columns.is-mobile > &.is-offset-half
    margin-left: 50%
  .columns.is-mobile > &.is-offset-one-third
    margin-left: 33.3333%
  .columns.is-mobile > &.is-offset-one-quarter
    margin-left: 25%
  @for $i from 1 through 12
    .columns.is-mobile > &.is-#{$i}
      flex: none
      width: ($i / 12) * 100%
    .columns.is-mobile > &.is-offset-#{$i}
      margin-left: ($i / 12) * 100%
  +mobile
    &.is-narrow-mobile
      flex: none
    &.is-full-mobile
      flex: none
      width: 100%
    &.is-three-quarters-mobile
      flex: none
      width: 75%
    &.is-two-thirds-mobile
      flex: none
      width: 66.6666%
    &.is-half-mobile
      flex: none
      width: 50%
    &.is-one-third-mobile
      flex: none
      width: 33.3333%
    &.is-one-quarter-mobile
      flex: none
      width: 25%
    &.is-offset-three-quarters-mobile
      margin-left: 75%
    &.is-offset-two-thirds-mobile
      margin-left: 66.6666%
    &.is-offset-half-mobile
      margin-left: 50%
    &.is-offset-one-third-mobile
      margin-left: 33.3333%
    &.is-offset-one-quarter-mobile
      margin-left: 25%
    @for $i from 1 through 12
      &.is-#{$i}-mobile
        flex: none
        width: ($i / 12) * 100%
      &.is-offset-#{$i}-mobile
        margin-left: ($i / 12) * 100%
  +tablet
    &.is-narrow,
    &.is-narrow-tablet
      flex: none
    &.is-full,
    &.is-full-tablet
      flex: none
      width: 100%
    &.is-three-quarters,
    &.is-three-quarters-tablet
      flex: none
      width: 75%
    &.is-two-thirds,
    &.is-two-thirds-tablet
      flex: none
      width: 66.6666%
    &.is-half,
    &.is-half-tablet
      flex: none
      width: 50%
    &.is-one-third,
    &.is-one-third-tablet
      flex: none
      width: 33.3333%
    &.is-one-quarter,
    &.is-one-quarter-tablet
      flex: none
      width: 25%
    &.is-offset-three-quarters,
    &.is-offset-three-quarters-tablet
      margin-left: 75%
    &.is-offset-two-thirds,
    &.is-offset-two-thirds-tablet
      margin-left: 66.6666%
    &.is-offset-half,
    &.is-offset-half-tablet
      margin-left: 50%
    &.is-offset-one-third,
    &.is-offset-one-third-tablet
      margin-left: 33.3333%
    &.is-offset-one-quarter,
    &.is-offset-one-quarter-tablet
      margin-left: 25%
    @for $i from 1 through 12
      &.is-#{$i},
      &.is-#{$i}-tablet
        flex: none
        width: ($i / 12) * 100%
      &.is-offset-#{$i},
      &.is-offset-#{$i}-tablet
        margin-left: ($i / 12) * 100%
  +desktop
    &.is-narrow-desktop
      flex: none
    &.is-full-desktop
      flex: none
      width: 100%
    &.is-three-quarters-desktop
      flex: none
      width: 75%
    &.is-two-thirds-desktop
      flex: none
      width: 66.6666%
    &.is-half-desktop
      flex: none
      width: 50%
    &.is-one-third-desktop
      flex: none
      width: 33.3333%
    &.is-one-quarter-desktop
      flex: none
      width: 25%
    &.is-offset-three-quarters-desktop
      margin-left: 75%
    &.is-offset-two-thirds-desktop
      margin-left: 66.6666%
    &.is-offset-half-desktop
      margin-left: 50%
    &.is-offset-one-third-desktop
      margin-left: 33.3333%
    &.is-offset-one-quarter-desktop
      margin-left: 25%
    @for $i from 1 through 12
      &.is-#{$i}-desktop
        flex: none
        width: ($i / 12) * 100%
      &.is-offset-#{$i}-desktop
        margin-left: ($i / 12) * 100%
  +widescreen
    &.is-narrow-widescreen
      flex: none
    &.is-full-widescreen
      flex: none
      width: 100%
    &.is-three-quarters-widescreen
      flex: none
      width: 75%
    &.is-two-thirds-widescreen
      flex: none
      width: 66.6666%
    &.is-half-widescreen
      flex: none
      width: 50%
    &.is-one-third-widescreen
      flex: none
      width: 33.3333%
    &.is-one-quarter-widescreen
      flex: none
      width: 25%
    &.is-offset-three-quarters-widescreen
      margin-left: 75%
    &.is-offset-two-thirds-widescreen
      margin-left: 66.6666%
    &.is-offset-half-widescreen
      margin-left: 50%
    &.is-offset-one-third-widescreen
      margin-left: 33.3333%
    &.is-offset-one-quarter-widescreen
      margin-left: 25%
    @for $i from 1 through 12
      &.is-#{$i}-widescreen
        flex: none
        width: ($i / 12) * 100%
      &.is-offset-#{$i}-widescreen
        margin-left: ($i / 12) * 100%

.columns
  margin-left: -0.75rem
  margin-right: -0.75rem
  margin-top: -0.75rem
  &:last-child
    margin-bottom: -0.75rem
  &:not(:last-child)
    margin-bottom: 0.75rem
  // Modifiers
  &.is-centered
    justify-content: center
  &.is-gapless
    margin-left: 0
    margin-right: 0
    margin-top: 0
    &:last-child
      margin-bottom: 0
    &:not(:last-child)
      margin-bottom: 1.5rem
    & > .column
      margin: 0
      padding: 0
  &.is-grid
    // Responsiveness
    +tablet
      flex-wrap: wrap
      & > .column
        max-width: 33.3333%
        padding: 0.75rem
        width: 33.3333%
        & + .column
          margin-left: 0
  &.is-mobile
    display: flex
  &.is-multiline
    flex-wrap: wrap
  &.is-vcentered
    align-items: center
  // Responsiveness
  +tablet
    &:not(.is-desktop)
      display: flex
  +desktop
    // Modifiers
    &.is-desktop
      display: flex
```

tiles.sass

```sass
.tile
  align-items: stretch
  display: block
  flex-basis: 0
  flex-grow: 1
  flex-shrink: 1
  min-height: min-content
  // Modifiers
  &.is-ancestor
    margin-left: -0.75rem
    margin-right: -0.75rem
    margin-top: -0.75rem
    &:last-child
      margin-bottom: -0.75rem
    &:not(:last-child)
      margin-bottom: 0.75rem
  &.is-child
    margin: 0 !important
  &.is-parent
    padding: 0.75rem
  &.is-vertical
    flex-direction: column
    & > .tile.is-child:not(:last-child)
      margin-bottom: 1.5rem !important
  // Responsiveness
  +tablet
    &:not(.is-child)
      display: flex
    @for $i from 1 through 12
      &.is-#{$i}
        flex: none
        width: ($i / 12) * 100%

```
<a name="bulma-layout" />

### bulma / sass / layout

hero.sass

```sass
// Components

.hero-video
  +overlay
  overflow: hidden
  video
    left: 50%
    min-height: 100%
    min-width: 100%
    position: absolute
    top: 50%
    transform: translate3d(-50%, -50%, 0)
  // Modifiers
  &.is-transparent
    opacity: 0.3
  // Responsiveness
  +mobile
    display: none

.hero-buttons
  margin-top: 1.5rem
  // Responsiveness
  +mobile
    .button
      display: flex
      &:not(:last-child)
        margin-bottom: 0.75rem
  +tablet
    display: flex
    justify-content: center
    .button:not(:last-child)
      margin-right: 1.5rem

// Containers

.hero-head,
.hero-foot
  flex-grow: 0
  flex-shrink: 0

.hero-body
  flex-grow: 1
  flex-shrink: 0
  padding: 3rem 1.5rem
  // Responsiveness
  +from($widescreen)
    padding-left: 0
    padding-right: 0

// Main container

.hero
  align-items: stretch
  background-color: $white
  display: flex
  flex-direction: column
  justify-content: space-between
  .nav
    background: none
    box-shadow: 0 1px 0 rgba($border, 0.3)
  .tabs
    ul
      border-bottom: none
  // Colors
  @each $name, $pair in $colors
    $color: nth($pair, 1)
    $color-invert: nth($pair, 2)
    &.is-#{$name}
      background-color: $color
      color: $color-invert
      a,
      strong
        color: inherit
      .title
        color: $color-invert
      .subtitle
        color: rgba($color-invert, 0.9)
        a,
        strong
          color: $color-invert
      .nav
        box-shadow: 0 1px 0 rgba($color-invert, 0.2)
      .nav-menu
        +mobile
          background-color: $color
      a.nav-item,
      .nav-item a:not(.button)
        color: rgba($color-invert, 0.7)
        &:hover,
        &.is-active
          color: $color-invert
      .tabs
        a
          color: $color-invert
          opacity: 0.9
          &:hover
            opacity: 1
        li
          &.is-active a
            opacity: 1
        &.is-boxed,
        &.is-toggle
          a
            color: $color-invert
            &:hover
              background-color: rgba($black, 0.1)
          li.is-active a
            &,
            &:hover
              background-color: $color-invert
              border-color: $color-invert
              color: $color
      // Modifiers
      &.is-bold
        $gradient-top-left: darken(saturate(adjust-hue($color, -10deg), 10%), 10%)
        $gradient-bottom-right: lighten(saturate(adjust-hue($color, 10deg), 5%), 5%)
        background-image: linear-gradient(141deg, $gradient-top-left 0%, $color 71%, $gradient-bottom-right 100%)
      // Responsiveness
      +mobile
        .nav-toggle
          span
            background-color: $color-invert
          &:hover
            background-color: rgba($black, 0.1)
          &.is-active
            span
              background-color: $color-invert
        .nav-menu
          .nav-item
            border-top-color: rgba($color-invert, 0.2)
  // Sizes
  &.is-medium
    +tablet
      .hero-body
        padding-bottom: 9rem
        padding-top: 9rem
  &.is-large
    +tablet
      .hero-body
        padding-bottom: 18rem
        padding-top: 18rem
  &.is-fullheight
    min-height: 100vh
    .hero-body
      align-items: center
      display: flex
      & > .container
        flex-grow: 1
        flex-shrink: 1
```

section.sass

```sass
.section
  background-color: $white
  padding: 3rem 1.5rem
  // Responsiveness
  +desktop
    // Sizes
    &.is-medium
      padding: 9rem 1.5rem
    &.is-large
      padding: 18rem 1.5rem
```

footer.sass

```sass
.footer
  background-color: $background
  padding: 3rem 1.5rem 6rem
```

<a name="purecss" />

## 4. Learn from Pure CSS

<a name="flashcards" />

## 5. CSS Flashcards

This is where I will collect all the things I want you to memorize.

Card 01
```css
html {
  font-size: 62.5%; /* font-size 1em = 10px on default browser settings */
}
```

Card 02
```
The clear CSS property specifies whether an element can be next to floating elements that precede it or must be moved down (cleared) below them. The clear property applies to both floating and non-floating elements.
When applied to non-floating blocks, it moves the border edge of the element down until it is below the margin edge of all relevant floats. This movement (when it happens) causes margin collapsing not to occur.
When applied to floating elements, it moves the margin edge of the element below the margin edge of all relevant floats. This affects the position of later floats, since later floats cannot be positioned higher than earlier ones.
```

<a name="links" />

## 6. Good CSS Websites

* [cssreference.io](http://cssreference.io/)
* [MDN CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)