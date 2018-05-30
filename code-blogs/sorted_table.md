
# Displaying Google Sheet Data in a paginated, sortable and searchable HTML table


![Image of Yaktocat](http://abirqasem.github.io/pics_for_apps/prettytable_small.png)

>### [Running demo](https://script.google.com/macros/s/AKfycbwRWKoSqdj8rqeaR9F6DPIEIJpr7aEqPNQwh8r-REeAM8T0cH0/exec)



We will use [Google Apps Script](https://developers.google.com/apps-script/), to fetch data from a Google sheet and DataTables (a JQuery plug-in) to display them. While in this blog we are showing a  basic implementation of the DataTables, it is a powerful tool with tons of features. If you are interested here's a nice [guide](https://datatables.net/manual/installation).



# Steps

## Add the libraries

>#### Make sure you have JQuery installed. It is after all a  **JQuery** plug-in.

```html
<script src="https://code.jquery.com/jquery-3.1.1.slim.min.js" integrity="sha384-A7FZj7v+d/sdmMqp/nOQwliLvUsJfDHW+k9Omg/a/EheAdgtzNs3hpfag6Ed950n" crossorigin="anonymous"></script>
<link rel="stylesheet" href="//code.jquery.com/ui/1.11.3/themes/smoothness/jquery-ui.css"> <!--check-->
<script src="//code.jquery.com/ui/1.11.4/jquery-ui.js"></script> <!--changed from lucoaong's version 1.11.3-->
```


>#### Add the DataTables CSS and the library

```html
<-- There may be a later version available -->
<link rel="stylesheet" href="//cdn.datatables.net/1.10.10/css/jquery.dataTables.min.css">
<script src="//cdn.datatables.net/1.10.10/js/jquery.dataTables.min.js"></script>
```

## The Table HTML

>#### The table's HTML is quite straight forward with only a few requirements. Your table must have a `table id` and one of the css class must be `display`. You will also need a header row.

>Here's a skeleton of a table that will work with DataTables

```html
<table id="my_table_id" class="display">
<thead>
	<tr>
   <th>Column Header 1</th>
    <th>Column Header 2</th>
   </tr>
</thead>
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

>#### And the JS code to render the table
```javascript
$(document).ready(function(){
  $('#my_table_id').DataTable();
}
```

>#### Hand coding table HTML is a pain. So here's a utility to make simple data table
>Make sure this code is on the client side JS and not server side JS.

```javascript

/*
	Utility to make DataTables compliant HTML table  
	data is a 2d array (first row assumed to be header) and table_id is the id for the table	Note: data will mutate. So please keep a copy
*/  


function make_table_html (data, table_id) {
  var header_row = data[0]
  var cols = header_row.length;

  data.shift(); // data mutates
  var data_rows = data
  var t_html = "<table id="+"'" + table_id+"'"+ "class='table table-striped table-hover cell-border'>"

  var header_html = "<thead><tr>"
  for (var c in header_row) {
        header_html+= "<th>"+ header_row[c] +"</th>"
  }
  header_html += "</tr></thead>";


  var row_html = "<tbody>";

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
```


# (Almost) Complete Google AppsScript example

## Code.gs

```javascript
// GAS web server
function doGet(e) {
  var ui = HtmlService.createTemplateFromFile('UI')
  return ui.evaluate()
     .setTitle("Datatable Demo").setSandboxMode(HtmlService.SandboxMode.IFRAME);
}

// getting some data
function get_data () {
  var data = SpreadsheetApp.openById('add your sid').getSheetByName('sheet name').getRange("give range").getValues();
  return data;
```
## UI.HTML
```html
<!DOCTYPE html>
<html>
  <head>
  <base target="_top">
  <!-- add your libraries JQuery and JQuery UI and their CSS, DataTables CSS and JS, I have also used Bootstrap, but that is not a requirement-->
  </head>

  <body>
  <div class="container" id="mainsec">
     <div class="row"><button type='button' class='btn btn-primary' id='view_data'>View Data</button>
     </div>
     <div id='view_data_area' class="row"></div>
   </div>

  <script>

   var view_data = document.getElementById('view_data');
   view_data.onclick = function (event) {
    google.script.run.withSuccessHandler (function (data) {
      $('#view_data_area').html (make_table_html (data, 'senators'));
      $('#senators').DataTable();

    }).withFailureHandler(function (e){console.log(e)}).get_data();      
  }


  </script>
  </body>
</html>

```
