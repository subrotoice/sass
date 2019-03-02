## SASS by Subroto
Official Website (https://sass-lang.com/guide)
Sass in this Free Crash Course (https://www.youtube.com/watch?v=roywYSEPSvc)
For background effect (https://bennettfeely.com/clippy)
- SASS just programm version of css which convert in to normall css. like main.scss compile to main.css and index.html page link with main.css not main.scss
- every valid CSS3 stylesheet is valid SCSS as well. (https://responsivedesign.is/articles/difference-between-sass-and-scss)
- You should always use SCSS, Because noraml css3 + Program CSS, For crating theme

**Variables: to store colors, font stacks, or any CSS value you think you'll want to reuse. Sass uses the $ symbol.**
-- In SCSS
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
- In CSS
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}

Other variable fetch
$colors : (
    primary: #005dff,
    primary-lite: lighten(#005dff, 40%),
    primary-dark: darken(#005dff, 40%),
    accent: #fff6bb
);

#bg {
    background-color: map-get($colors, accent); // background-color: #fff6bb; (css)
}
