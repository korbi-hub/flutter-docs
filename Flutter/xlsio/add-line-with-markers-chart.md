---
layout: post
title: Excel Line with Markers Chart of Syncfusion Flutter XlsIO.
description: Learn how to create, add and manipulate the line with markers chart in Excel worksheet using Syncfusion Flutter XlsIO. 
platform: flutter
control: Excel
documentation: ug
---

# Adding Stacked line Chart to Excel worksheet

Line marker is a line that is drawn on chart plot and bound to some value on an axis. It may be used to show a trend or mark an important value.

The following code snippet illustrate how to add Line with Markers chart to Excel worksheet using Flutter XlsIO.

{% highlight dart %}
// Create a new Excel document.
final Workbook workbook = Workbook();

// Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Setting value in the cell.
sheet.getRangeByName('A1').setText('City Name');
sheet.getRangeByName('A2').setText('Chennai');
sheet.getRangeByName('A3').setText('Mumbai');
sheet.getRangeByName('A4').setText('Delhi');
sheet.getRangeByName('A5').setText('Hyderabad');
sheet.getRangeByName('A6').setText('Kolkata');
sheet.getRangeByName('B1').setText('Temp in C');
sheet.getRangeByName('B2').setNumber(34);
sheet.getRangeByName('B3').setNumber(40);
sheet.getRangeByName('B4').setNumber(47);
sheet.getRangeByName('B5').setNumber(20);
sheet.getRangeByName('B6').setNumber(66);
sheet.getRangeByName('C1').setText('Temp in F');
sheet.getRangeByName('C2').setNumber(93);
sheet.getRangeByName('C3').setNumber(104);
sheet.getRangeByName('C4').setNumber(120);
sheet.getRangeByName('C5').setNumber(80);
sheet.getRangeByName('C6').setNumber(140);

//Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add the chart.
final Chart chart1 = charts.add();

// Set Chart Type.
chart1.chartType = ExcelChartType.lineMarkers;

// Set data range in the worksheet.
chart1.dataRange = sheet.getRangeByName('A1:C6');
chart1.isSeriesInRows = false;

// set charts to worksheet.
sheet.charts = charts;

//save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
workbook.dispose();
File('LineWithMarkersChart.xlsx').writeAsBytes(bytes);
{% endhighlight %}

