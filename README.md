# Verkehrsnetz

## Was wir brauchen

Einen "simplifizierten", aufdatierten Graphen für die gesamte Mobilität mit Nodes und Edges (inkl. Kilometrierung) und Transport Modi. Idealerweise werden daraus auch Dinge ersichtlich wie einzelne Bus- oder Tramlinien etc.       

Für die **GeoUnconference** könnte man das vorerst auf den öffentlichen Verkehr und auf die Schweiz mit Grenzregionen einschränken.      
Grundsätzlich brauchen wir das aber für alle Transport Modi und weltweit, da wir unsere GPS-Datenpunkte von [Posmo One](https://datamap.io/) auf einem Graphen abbilden wollen.
                 
Wichtig dabei ist, dass dieser Graph historisch und immer auch für die aktuelle Gegenwart funktioniert.              
Denn unsere Daten wurden gestern und werden heute und morgen erhoben. Und unser Map Matching ist nur so gut wie der Graph.

PS:       
Bei den Gemeindegrenzen haben wir bereits gesehen, was für Probleme entstehen, wenn der Bund diese nur periodisch (1 x pro Jahr) aufdatiert. Um z.B. eine Abstimmung als Karte darzustellen, mussten wir die über 10 Gemeinden von Bellinzona nach der Fusion zu einem grossen Ganzen zusammenführen.   
      

## Woran wir arbeiten

Diesen Graphen ertellen wir zurzeit für Züge. Dabei sind uns die grossen Unterschiede zwischen verschiedenen Datenquellen (BAV, GTFS, Shapefiles) aufgefallen. 
Leider funktioniert ein einfaches Mapping nicht und viel Handarbeit ist nötig.      
Auch der zur Verfügung gestellte Graph hat seine Tücken.         

2 Beispiele:        
1. Bei BAV/Didok gibt es für den HB Zürich, HB Museumsstrasse und HB Löwenstrasse 3 verschiedene UIC-Refs.       
In GTFS sind HB Löwenstrasse und HB Museumsstrasse Teil des HB (850300) und werden über ihre Gleise ausgewiesen.     
Beim Node-Edge-Graphen gibts dann hingegen 3 einzelne Nodes.         
Bei der HB SZU, die sich zwar im HB befindet, gibts dann wieder einen einzelnen Node (in BAV, GTFS und im Graphen).      
      
2. Gewisse Edges sind nicht mit Nodes connected. So geht z.B. das letzte Edge der Metro von Lausanne nach Renens bis in den Bahnhof von Renens anstatt zur Metrostation Renens.  


## Wie man das ausbauen könnte

Wir selbst arbeiten viel mit Webinterfaces, damit Nodes oder Edges auf einer Karte überprüfbar sind. 
Wir könnten uns vorstellen eine solche webbasierte Karte zugänglich zu machen, damit man die Karte 
a) laufend aufdatieren kann und b) verschiedene Datensets herunterladen kann.               

Man könnte dann Anfragen/Download machen wie z.B.: 
- Gibt mir das gesamte Zug-Schienennetz im Kanton Zürich, Stand Mai 2021. 
- Gib mir alle neuen Tramlinien seit 2020 in der ganzen Schweiz. 


## Offene Fragen
- Kontinuierliche Updates
- Finanzierung





Siehe:
https://twitter.com/datamapio/status/1388849007607357442?s=20
https://www.swisstopo.admin.ch/de/swisstopo/veranstaltungen/colloque.detail.event.html/swisstopo-internet/events2021/colloquium-20-21/20210326.html
