# Inclusive Design Cheatsheet

### Always add a Doctype.
```html
<!DOCTYPE html>
```

### Define a language
```html
<html lang="en">
```

### Responsive design
Define content breakpoints -> one design for all.

### Allow pinch-to-zoom
```html
<meta name="viewport" content="width=device-with, initial-scale=1.0">

### Use relative font-size
```css
html {
  font-size: 100%
}
```
Use rem (relative to root font-size) or em (relative to parent font-size)
2rem means two times larger then the default font size.

### Use viewport units
This snippet ensures a minimum font-size height for the page.
```css
html {
  font-size: calc(1em + 1vw);
}
```
### Insert scripts at body
```html
  <script>// logic</script>
</body>
```
### Load css fonts even if there is no JavaScript
```html
<link rel="stylesheet" href="fonts.css" media="none" onload="if(media!='all')media='all'">
<noscript>
  <link rel="stylesheet" href="fonts.css">
</noscript
```
The font has to be base64-encoded.
Or use font loader [like here](https://github.com/bramstein/fontfaceobserver)

### Load only the characters of a font you need.
[Webfont generator](http://www.fontsquirrel.com/tools/webfont-generator)

### Use main
Mark main content! Good for printing and hiding unnecessary content.
```html
<main id="main">
</main>
```

### Skip links
Shown only to keyboard users to directly go to the main content!
```css
[href=”#main”] {
  position: absolute;
  top: 0;
  right: 100%; /* moves off screen */ }
[href=”#main”]:focus {
  right: auto;
}
```

### Putting the page together
```html
<!DOCTYPE html> <!-- the main language of the page declared --> 
<html lang="en">
  <head>
    <meta charset="utf-8">
    <!-- a viewport declaration which does not disable zooming -->  
    <meta name="viewport" content="width=device-width, initialscale=1.0">
    <!-- a non-blocking base64-encoded font resource -->  
    <link rel="stylesheet" href="fonts.css" media="none"   onload="if(media!='all')media='all'">
    <noscript>
      <link rel="stylesheet" href="fonts.css">
    </noscript>
    <!-- a non-blocking stylesheet -->  
    <link rel="stylesheet" href="main.css" media="none"   onload="if(media!='all')media='all'">
    <noscript>
      <link rel="stylesheet" href="main.css">
    </noscript>
    <!-- a descriptive label for the page -->  
    <title>Inclusive Design Template | Heydon's Site</title>
  </head>
  <body>
    <!-- a handy skip link for keyboard users -->  <a href="#main">skip to main content</a>
    <!-- logo / page navigation etc. goes here -->
    <main id="main">
      <!-- unique content of page goes here -->  
    </main>
    <!-- a non-blocking javascript resource -->  <script src="scripts.js"></script> 
  </body>
</html>
```

## Paragraph
### Set max width for reading comfortability
```css
main {
  max-width: 60rem;
}

@media (min-width: 120rem) {
  html {
    font-size: 150%; /* default is 100% */
  }
}
```
### Relative line height
```css
p {
  font-size: 1rem; /* the default */
  line-height: 1.5;
}
```
### Add contrast
```css
main {
  background: #EEE;
}
p {
  color: #222;
}
```
### Improve link underlines
```css
p a {
  text-decoration: none;
  text-shadow: 0.05em 0 0 #fff, -0.05em 0 0 #fff,
    0 0.05em 0 #fff, 0 -0.05em 0 #fff,
    0.1em 0 0 #fff, -0.1em 0 0 #fff,
    0 0.1em 0 #fff, 0 -0.1em 0 #fff;
  background-image: linear-gradient(to right, currentColor 0%, currentColor 100%);
  background-repeat: repeat-x;
  background-position: bottom 0.05em center;
  background-size: 100% 0.05em;
}
```
And fallback for older browsers
```css
.ie-lte-9 a {
  text-decoration: underline;
}
```
### Change links focus rendering
```css
p a:focus {
  outline: none;
  background-color: #cef;
  text-shadow: 0.05em 0 0 #cef, -0.05em 0 0 #cef,
    0 0.05em 0 #cef, 0 -0.05em 0 #cef,
    0.1em 0 0 #cef, -0.1em 0 0 #cef,
    0 0.1em 0 #cef, 0 -0.1em 0 #cef;
```
### Mark external links with icon
```css
[href^="http"]:not([href*="domain.com"])::after {
  display: inline-block;
  width: 1em;
  height: 1em;
  background-image: url('path/to/external-icon.svg');
  background-repeat: no-repeat;
  background-position: center;
  background-size: 75% auto;
  /* alternative text rules */
  content: '(external link)';
  overflow: hidden;
  white-space: nowrap;
  text-indent: 1em; /* width of icon */
}
```
