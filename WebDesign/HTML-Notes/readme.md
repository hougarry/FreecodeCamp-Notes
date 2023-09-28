this is for html notes

### Table
In HTML, you can create a table structure that includes a `<thead>`, `<tr>`, `<th>`, and `<td>` elements to define a table with a header row. Here's an example structure:

```html
<table>
  <thead>
    <tr>
      <th>Header Cell 1</th>
      <th>Header Cell 2</th>
      <th>Header Cell 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Data Cell 1</td>
      <td>Data Cell 2</td>
      <td>Data Cell 3</td>
    </tr>
    <!-- Additional rows of data -->
  </tbody>
</table>
```

Explanation of the elements:

- `<table>`: Defines the table container.
- `<thead>`: Defines the table header section.
- `<tr>`: Defines a table row within the `<thead>`.
- `<th>`: Defines table header cells. These cells typically contain header information.
- `<td>`: Defines table data cells. These cells contain the actual data.

In this example, the `<thead>` section contains one row (`<tr>`) with three header cells (`<th>`). You can adjust the number of header cells and their content to match your table's requirements.

The `<tbody>` section is used for the table's body, where you would typically place the data rows (`<tr>`) and data cells (`<td>`).

Remember that this is just a basic structure, and you can customize it further by adding more rows and cells or applying CSS styles to improve the table's appearance and functionality.


## html-css
html{
    box-sizing: border-box;
}
*, *:before, *:after{
    box-sizing: inherit;
}

*, *:before, *:after { box-sizing: inherit; }: This CSS rule is a bit more complex. It uses the universal selector * to select all elements in the HTML document, along with *::before and *::after to select pseudo-elements that are before and after each element, respectively. It then sets the box-sizing property to inherit.

box-sizing: inherit; means that these elements (including pseudo-elements) will inherit the box-sizing property value from their parent elements. So, if a specific element or its parent has box-sizing: border-box, then all of its children and pseudo-elements will also have box-sizing: border-box.