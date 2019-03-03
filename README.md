## SASS by Subroto
Official Website (https://sass-lang.com/guide)

Sass in this Free Crash Course (https://www.youtube.com/watch?v=roywYSEPSvc)

For background effect (https://bennettfeely.com/clippy)
- SASS just programm version of css which convert in to normall css. like main.scss compile to main.css and index.html page link with main.css not main.scss
- Every valid CSS3 stylesheet is valid SCSS as well. (https://responsivedesign.is/articles/difference-between-sass-and-scss), SCSS and SASS are same except ( ';', '{}' )
- You should always use SCSS, Because noraml css3 + Program CSS, For crating theme

**Variables: to store colors, font stacks, or any CSS value you think you'll want to reuse. Sass uses the $ symbol.**

- In SCSS
```
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```
- In CSS
```
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}
```
Other variable fetch
```
$colors : (
    primary: #005dff,
    primary-lite: lighten(#005dff, 40%),
    primary-dark: darken(#005dff, 40%),
    accent: #fff6bb
);

#bg {
    background-color: map-get($colors, accent); // background-color: #fff6bb; (css)
}
```
```
//Using Functions
@function color($color-name){
    @return map-get($colors, $color-name);
}

#bg{
     background-color: color(primary);
}
```

**Nesting: Very powerful tool in my perception**
```
// SCSS
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```
```
// Compile CSS
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```
**Import: like PHP include. It import scass file where mixins include script** 
```
// reset.scss
html,
body,
ul,
ol {
  margin:  0;
  padding: 0;
}

// main.scss
@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}


// CSS Output
html,
body,
ul,
ol {
  margin:  0;
  padding: 0;
}

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```
**Mixin: is a way to bind some code (with/without class name + CSS Property) that will going repeatedly be used. Like PHP include, but only style not total file like import. Mixins are included by @include directive which takes Name  and Optionally arguments**

```
@mixin large-text {  //Only properties - Without Class name
  font: {
    family: Arial;
    size: 20px;
    weight: bold;
  }
  color: #ff0000;
}

.page-title {
  @include large-text;
  padding: 4px;
  margin-top: 10px;}

// CSS Output
.page-title {
  font-family: Arial;
  font-size: 20px;
  font-weight: bold;
  color: #ff0000;
  padding: 4px;
  margin-top: 10px; }

// Mixins may also be included outside of any rule
@mixin silly-links {  //Class name and Properties
  a {
    color: blue;
    background-color: red;
  }
}
@include silly-links;

// CSS Output
a {
  color: blue;
  background-color: red; }

// Arguments Passing
@mixin sexy-border($color, $width) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}

p { @include sexy-border(blue, 1in); }

// CSS Output
p {
  border-color: blue;
  border-width: 1in;
  border-style: dashed; }


// We normally pass arguments, But it is possible to pass a block of styles to mixin as argument, Here receiving parameter is @content directive

@mixin apply-to-ie6-only { //Content/Block of code passing
  * html {
    @content;
  }
}
@include apply-to-ie6-only {
  #logo {
    background-image: url(/logo.gif);
  }
}

// CSS Output
* html #logo {
  background-image: url(/logo.gif);
}

$color: white;
@mixin colors($color: blue) {
  background-color: $color;
  @content;
  border-color: $color;
}
.colors {
  @include colors { color: $color; }
}

// CSS Output
.colors {
  background-color: blue;
  color: white;
  border-color: blue;
}

// Another Handy Maxin use for responsive design
$desktop: 840px;
@mixin desktop {
    @media (min-width: #{$desktop}){
        @content;
    }
}

// CSS Output
@media (min-width: 840px) {
  body #bg {
    -webkit-clip-path: polygon(0 0, 66% 0, 37% 100%, 0% 100%);
            clip-path: polygon(0 0, 66% 0, 37% 100%, 0% 100%);
  }
}
```

**Operators: Doing math in your CSS is very helpful with math operators. **
```
// SCSS
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}

// CSS Output
.container {
  width: 100%;
}

article[role="main"] { 
  float: left;
  width: 62.5%;
}

aside[role="complementary"] {
  float: right;
  width: 31.25%;
}

//Another SCSS
span {
    width: 500/2*4+90px;
}
// CSS Output
span {
  width: 1090px;
}
```
