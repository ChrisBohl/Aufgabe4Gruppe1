# Aufgabe4Gruppe1
//Beschreibung Aufgabenstellung 4: Matrix Hochregallager: Fischertechnik Simulationsfabrik
//Sehr geehrte Damen und Herren, zunächst möchten wir uns bei Ihnen für die Übernahme des Auftrags zur Erstellung eines Micro-Services des Dashboards für den Demonstrator PID4CPS nach Industrie 4.0-Standards bedanken! Gerne informiere wir Sie auf diesem Weg, welchen Funktionsumfang das von Ihnen zu erstellende Programm aufweisen soll. Bei diesen Funktionalitäten handelt es sich um die Minimalanforderungen. Sie sind dazu eingeladen, weitere Funktionen, basierend auf den zur Verfügung gestellten Daten, zu entwerfen und diese mit uns zu diskutieren. Auch können weitere Daten auf dem Server zur Verfügung gestellt werden, wenn Sie diese für bestimmte Funktionalitäten benötigen.
//Die Funktionalitäten des Programms müssen umfassen: • Eingabemöglichkeit, welche Fächer mit welchen Produktionsmaterialien belegt sind o Schematische Visualisierung des Hochregallagers mit der Möglichkeit, fachindividuell die jeweilige Belegung festzulegen. Zu berücksichtigende Variablen sind: Belegt/nicht belegt. Wenn belegt: Farbe, numerische ID und RFID-Adresse. Wenn aus Informationen ableitbar, selbstergänzend • Fortlaufendes Tracking und Ausgabe der aktuellen Belegung des Hochregallagers o Visualisierung von Belegungsveränderungen jeglicher Fächer o Geeignete Visualisierung, die auf Belegungsänderungen aufmerksam macht
//Hier sind die gefilterten Daten im JSON-Format zu finden: https://it2wi1.if-lab.de/rest/ft_fach/Parameter/H-vertikal/Parameter/H-horizontal/Parameter/Referenztaster%20vertikal/Parameter/Referenztaster%20Ausleger%20vorne/Parameter/Referenztaster%20Ausleger%20hinten
//Was ist zu tun?   
//1.  Erstellen Sie eine HTML-Seite, die die gefilterten Daten im JSON-Format anzeigt.
//2.  Erstellen Sie eine HTML-Seite, die die gefilterten Daten im JSON-Format anzeigt und die Möglichkeit bietet, die Daten zu filtern.
//3.  Erstellen Sie eine HTML-Seite, die die gefilterten Daten im JSON-Format anzeigt und die Möglichkeit bietet, die Daten zu filtern und zu sortieren.
//4.  Erstellen Sie eine HTML-Seite, die die gefilterten Daten im JSON-Format anzeigt und die Möglichkeit bietet, die Daten zu filtern und zu sortieren. Die Daten sollen in einer Tabelle angezeigt werden. Die Tabelle soll mit Hilfe von JavaScript erstellt werden.
// Wie gehe ich vor?
//1.  Erstellen Sie ein neues GitHub-Repository mit dem Namen „PID4CPS-WI1920-Aufgabe4-<IhrName>“.
//2.  Erstellen Sie einen neuen Branch mit dem Namen „develop“.
// Wie erstelle ich jetzt eine HTML Seite?
//1.  Erstellen Sie eine neue Datei mit dem Namen „index.html“.
//2.  Fügen Sie den folgenden Code in die Datei ein:
//<!DOCTYPE html>
//<html>
//<head>
//Wie füge ich die Möglichkeit hinzu, die Möglichkeit bietet, die Daten zu filtern und zu sortieren. Die Daten sollen in einer Tabelle angezeigt werden. Die Tabelle soll mit Hilfe von JavaScript erstellt werden. Die Daten sind unter folgenden Link abrufbar: https://it2wi1.if-lab.de/rest/ft_fach/Parameter/H-vertikal/Parameter/H-horizontal/Parameter/Referenztaster%20vertikal/Parameter/Referenztaster%20Ausleger%20vorne/Parameter/Referenztaster%20Ausleger%20hinten
//Wie kann ich die HTML Seite anzeigen?
//1.  Öffnen Sie die Datei „index.html“ mit einem Browser Ihrer Wahl.
//2.  Sie sollten nun die HTML Seite sehen.
//Was ist jetzt zu tun? Ich habe bereits eine HTML Seite erstellt, die die Daten anzeigt. die Möglichkeit bietet, die Daten zu filtern und zu sortieren. Die Daten werden in einer Tabelle angezeigt . Die Tabelle ist mit Hilfe von JavaScript erstellt. Ich habe bereits einen GitHub-Repository erstellt. Ich habe bereits einen Branch erstellt.
//1.  Erstellen Sie einen Pull-Request mit dem Namen „Aufgabe 4: <IhrName>“.
//2.  Fügen Sie mich als Reviewer hinzu.
//3.  Warten Sie auf das Feedback.
//4.  Überarbeiten Sie Ihren Code, wenn nötig.
//5.  Wiederholen Sie die Schritte 1-4, bis der Pull-Request akzeptiert wird.
//6.  Mergen Sie den Pull-Request in den Branch „master“.
//7.  Erstellen Sie einen neuen Branch mit dem Namen „release“.
//8.  Mergen Sie den Branch „master“ in den Branch „release“.
//9.  Erstellen Sie einen neuen Release mit dem Namen „v1.0“.
//10.  Erstellen Sie einen neuen Branch mit dem Namen „hotfix“.
//Ich kann keinen Pull-Request erstellen. Was kann ich tun?
//1.  Überprüfen Sie, ob Sie alle Schritte befolgt haben.
//2.  Überprüfen Sie, ob Sie mich als Reviewer hinzugefügt haben.
//3.  Überprüfen Sie, ob Sie den Branch „develop“ als Basis für den Pull-Request ausgewählt haben.
//4.  Überprüfen Sie, ob Sie den Pull-Request erstellt haben.


<!DOCTYPE html>
<html>
<head>
  <title>JSON-Daten anzeigen</title>
  <style>
    table {
      border-collapse: collapse;
    }
    th, td {
      border: 1px solid black;
      padding: 8px;
    }
  </style>
</head>
<body>
  <h1>JSON-Daten anzeigen</h1>
  
  <label for="filterInput">Filter:</label>
  <input type="text" id="filterInput">
  
  <table id="dataTable">
    <thead>
      <tr>
        <th>Datum</th>
        <th>H-vertikal</th>
        <th>H-horizontal</th>
        <th>Referenztaster vertikal</th>
        <th>Referenztaster Ausleger vorne</th>
        <th>Referenztaster Ausleger hinten</th>
      </tr>
    </thead>
    <tbody id="dataBody">
      <!-- Der Inhalt der Tabelle wird mit JavaScript generiert -->
    </tbody>
  </table>
  
  <script>
    // JSON-Daten abrufen und die Tabelle erstellen
    fetch('https://it2wi1.if-lab.de/rest/ft_fach')
      .then(response => response.json())
      .then(data => {
        const tableBody = document.getElementById('dataBody');
        
        // Funktion zum Filtern der Daten
        const filterData = () => {
          const filterInput = document.getElementById('filterInput');
          const filterValue = filterInput.value.toLowerCase();
          
          const filteredData = data.filter(item => {
            const values = Object.values(item.werte).join(' ').toLowerCase();
            return values.includes(filterValue);
          });
          
          createTable(filteredData);
        };
        
        // Funktion zum Sortieren der Daten
        const sortData = (key, order) => {
          const sortedData = [...data].sort((a, b) => {
            if (a.werte[key] < b.werte[key]) return -1;
            if (a.werte[key] > b.werte[key]) return 1;
            return 0;
          });
          
          if (order === 'desc') {
            sortedData.reverse();
          }
          
          createTable(sortedData);
        };
        
        // Funktion zur Erstellung der Tabelle
        const createTable = (dataArray) => {
          tableBody.innerHTML = '';
          
          dataArray.forEach(item => {
            const row = document.createElement('tr');
            
            const datumCell = document.createElement('td');
            datumCell.textContent = item.datum;
            row.appendChild(datumCell);
            
            Object.values(item.werte).forEach(value => {
              const dataCell = document.createElement('td');
              dataCell.textContent = value;
              row.appendChild(dataCell);
            });
            
            tableBody.appendChild(row);
          });
        };
        
        createTable(data);
        
        // Event Listener für Filterung
        const filterInput = document.getElementById('filterInput');
        filterInput.addEventListener('input', filterData);
        
        // Event Listener für Sortierung
        const sortableHeaders = document.querySelectorAll('th');
        sortableHeaders.forEach(header => {
          header.addEventListener('click', () => {
            const key = header.textContent.toLowerCase();
            const order = header.classList.contains('desc') ? 'asc' : 'desc';
            
            sortableHeaders.forEach(header => {
              header.classList.remove('asc', 'desc');
            });
            
            header.classList.add(order);
            
            sortData(key, order);
          });
        });
      })
      .catch(error => {
        console.error('Fehler beim Abrufen der Daten:', error);
      });
  </script>
</body>
</html>
