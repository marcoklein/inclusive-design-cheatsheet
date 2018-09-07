# inlusive-design-cheatsheet

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
