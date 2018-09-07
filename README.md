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
