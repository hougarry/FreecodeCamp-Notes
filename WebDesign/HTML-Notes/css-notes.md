1.Create a body selector and give it a font-family set to Open Sans with a fallback of sans-serif.? 
```
body {
  font-family: "Open Sans", sans-serif;
}
```

 fallback means  a secondary or backup option that is used when the primary choice is not available or supported.

 2. structure of css:  margin/border/padding, height/content/width/. mbp,hcw(mackbookpro, hey, can't wait)

**3.what's the difference between id and class?**
In HTML, if an element has the `class` attribute set to "logo," you would target it in CSS using the class selector `.logo`:

```css
/* CSS for elements with class="logo" in HTML */
.logo {
  /* Your styles here */
}
```

If an element has the `id` attribute set to "logo," you would target it in CSS using the ID selector `#logo`:

```css
/* CSS for an element with id="logo" in HTML */
#logo {
  /* Your styles here */
}
```

The class selector (`.classname`) is used to target multiple elements with the same class, while the ID selector (`#idname`) is used to target a single unique element with a specific ID.

**4.how to create navigation by enable navigation on the page, add an unordered list with the following three list items?**
INFO
HTML
CSS
The list items text should be wrapped in anchor tags.
To create a navigation menu with an unordered list where each list item is a link, you can use HTML like this:

```html
<ul>
  <li><a href="#info">INFO</a></li>
  <li><a href="#html">HTML</a></li>
  <li><a href="#css">CSS</a></li>
</ul>
```

In this `code`:

- `<ul>` represents an unordered list.
- `<li>` represents each list item within the list.
- `<a>` represents anchor tags that will create the links.

Each `<a>` tag has an `href` attribute that specifies the destination or anchor within the same page. For example, `#info` will scroll to an element with `id="info"` when clicked.

Make sure to place this list within your HTML document's `<body>` element where you want the navigation menu to appear. Also, ensure that you have corresponding elements in your page with the `id` attributes "info," "html," and "css" so that the links will scroll to the appropriate sections when clicked.

