
## The Problem

We want sortable and searchable html table

![Image of Yaktocat](pics_for_apps/prettytable.png)


## Solution

We need to add some libs to the HTML
Build the table in a certain way
Then get the data


## Steps

We are using datatable JQuery plug in. They have a nice [guide](https://datatables.net/manual/installation) too.

0. Make sure you have JQuery installed. It is a *JQuery* plug in.
1. Add the following css and javascript to your HTML

    ```html
    <-- There may be later version please check -->
    <link rel="stylesheet" href="//cdn.datatables.net/1.10.10/css/jquery.dataTables.min.css">
    <script src="//cdn.datatables.net/1.10.10/js/jquery.dataTables.min.js"></script>
    ```
2. Your table must have a `table id` and the class should be `display` (the table can be and should be programmatically built in most cases).

```html
<table id="my_table_id" class="display">
```		

3. You will also need a header row.
  ```
    <thead>
        <tr>
            <th>Column Header 1</th>
            <th>Column Header 2</th>
        </tr>
    </thead>
  ```
4. And the body
  ```
<tbody>
  <tr>
    <td>Row 1 Data 1</td>
    <td>Row 1 Data 2</td>
  </tr>
  <tr>
    <td>Row 2 Data 1</td>
    <td>Row 2 Data 2</td>
  </tr>
</tbody>
```

3. Finally to render the table
```javascript
$(document).ready(function(){
  $('#my_table_id').DataTable();
}
```
## An utility to make simple data table

```javascript

/* An utility to make simple data table
  pass in the data from a spreadsheet and a table id

*/  


function make_table_html (data, table_id) {
  var header_row = data[0]
  var cols = header_row.length;

  data.shift();
  var data_rows = data



  var t_html = "<table id="+"'" + table_id+"'"+ "class='table table-striped table-hover cell-border'>"


  var header_html = "<thead><tr>"
  for (var c in header_row) {
        header_html+= "<th>"+ header_row[c] +"</th>"
  }
  header_html += "</tr></thead>";


  var row_html = "<tbody>"

  for (var r in data_rows) {
    row_html += "<tr>"
    for (var c=0; c<cols; c++) {
      row_html += "<td>"+ data_rows[r][c] + "</td>"
    }
    row_html += "</tr>"
  }
  row_html += "</tbody>"

  t_html+= header_html+row_html + "</table>"

  return t_html

}




$(document).ready(function(){
  $('#art_table').DataTable()

}









```
