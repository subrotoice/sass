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
**Import: like PHP include**
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

**Mixins: Some thing like function. When same variable needs to use many times then it use.**
```
// SCSS
@mixin transform($property) {
  -webkit-transform: $property;
  -ms-transform: $property;
  transform: $property;
}

.box { @include transform(rotate(30deg)); }

// CSS Output
.box {
  -webkit-transform: rotate(30deg);
  -ms-transform: rotate(30deg);
  transform: rotate(30deg);
}

// Another SCSS
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
**Operators: Doing math in your CSS is very helpful with math operators like +, -, *, /, and %. **
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
