# lampomittari
---
''
<html>
    <head>
      <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
      <script type="text/javascript">
        google.charts.load('current', {'packages':['corechart']});
        google.charts.setOnLoadCallback(drawChart);
      

        async function drawChart() {

         let url='https://api.thingspeak.com/channels/1527799/feeds.json?results=20';
         
         const fetchResults = await fetch(url);
         const jsonResults = await fetchResults.json();
         const feedsResults = jsonResults.feeds;

         let editRows = [['Pvm','lämpötila']];

                  
         //let editRows='';
         for (const i in feedsResults) {
             editRows.push([feedsResults[i].created_at, parseInt(feedsResults[i].field2.split('.')[0])]);
           //  editRows +=" "+ feedsResults[i].field1.split('.')[0];
         }
         document.getElementById("resultTable").innerHTML = editRows;

        var data = google.visualization.arrayToDataTable( editRows);

        
        let editRows2 = [['Pvm', 'ilmankosteus']];
        for (const i in feedsResults) {
             editRows2.push([feedsResults[i].created_at, parseInt(feedsResults[i].field1.split('.')[0])]);
        }
        var data2 = google.visualization.arrayToDataTable( editRows2);
        document.getElementById("resultTable").innerHTML = editRows2;
        

        let editRows3 = [['Pvm', 'Dew_point']];
        for (const i in feedsResults) {
             editRows3.push([feedsResults[i].created_at, parseInt(feedsResults[i].field3.split('.')[0])]);
        }
        var data3 = google.visualization.arrayToDataTable( editRows3);
       document.getElementById("resultTable").innerHTML = editRows3;
        
        let editRows4 = [['Pvm', 'Heat_index']];
        for (const i in feedsResults) {
             editRows4.push([feedsResults[i].created_at, parseInt(feedsResults[i].field4.split('.')[0])]);
        }
        var data4 = google.visualization.arrayToDataTable( editRows4);
        document.getElementById("resultTable").innerHTML = editRows4;
        
    
      //  var data = google.visualization.arrayToDataTable([
        //  ['Pvm','lämpötila'],
       //   ['1.10', +11],
       //   ['2.10', +7],
       //   ['3.10', +12],
       //   ['4.10',  +4]
       // ]);
     // var data2 = google.visualization.arrayToDataTable([
        //  ['Pvm', 'ilmankosteus'],
        //  ['1.10',  54],
        //  ['2.10',  42],
        //  ['3.10',  60],
        //  ['4.10',  52]
       //]);
      
          var options = {
            title: 'Lämpötila',
            curveType: 'function',
            legend: { position: 'bottom' }
          };
          var options2 = {
            title: 'Ilmankosteus',
            curveType: 'function',
            legend: { position: 'bottom' }
          };
          var options3 = {
           title: 'Dew_point',
           curveType: 'function',
           legend: { position: 'bottom' }
          };
          var options4 = {
            title: 'Heat_index',
            curveType: 'function',
            legend: { position: 'bottom' }
          };
          var chart = new google.visualization.LineChart(document.getElementById('lampotila'));
          chart.draw(data, options);
          var chart2 = new google.visualization.AreaChart(document.getElementById('ilmankosteus'));
          chart2.draw(data2, options2);
          var chart3 = new google.visualization.LineChart(document.getElementById('Dew_point'));
          chart3.draw(data3, options3);
          var chart4 = new google.visualization.AreaChart(document.getElementById('Heat_index'));
          chart4.draw(data4, options4);
          //setTimeout w3Scool 
          setTimeout(drawChart,3000)
        }
      </script>
    </head>
    <body>
        <div id="resultTable"></div>
        <div id="lampotila" style="width: 900px; height: 500px"></div>
        <div id="ilmankosteus" style="width: 900px; height: 500px"></div>
        <div id="Dew_point" style="width: 900px; height: 500px"></div>
        <div id="Heat_index" style="width: 900px; height: 500px"></div>
    </body>
    </body>
  </html>
''
||

! [Kaavio] (main/lampomittarin%20kaaviokuvat.jpg)

||
