# Verkehrsnetz

## Update 2. Geounconference, 9. September 2021
Gruppe Mobilität und Verkehr
- Corinne Frey (am Verkehrsnetz beteiligt), 
- Christine Meixner von derpunkt, 
- Patrick Müller von Outdoor Active        
- Roger Fischer   
                            
Siehe auch: [Diskussion Mobilität und Verkehr](https://github.com/GeoUnconference/discussions/discussions/10)         

Aus meiner Sicht wäre es sinnvoll rasch einen Prototypen zu bauen, der die konkreten Anforderungen an einen gemeinsamen Datenpool in die Tat umsetzt.     

### Erster und einfachster Usecase: Aktuelle Gemeindegrenzen
Da CH-Gemeinden auch während dem Jahr fusionieren (z.B. Gemeindefusion Bellinzona), aber Gemeindegrenzen nur 1 x pro Jahr zur Verfügung stehen, könnte man so ein ganz einfaches Beispiel schaffen, an dem man exemplarisch der Mehrnutzen für alle sichtbar würde. Bei jeder Abstimmung oder Wahl braucht es Gemeindegrenzen und diese sind auch historisch relevant.

URL: gemeindegrenzen.ch         
Nutzer:innen: Alle Journalist:innen, alle Planer:innen, Behörden, d.h. eine sehr breite Nutzerbasis             

Karte zeigt aktuellsten Stand der Gemeindegrenzen.             
Auf einem Zeitstrahl kann man in die Vergangenheit oder in die Zukunft (geplante Fusionen)           

Download:        
- LV95 und WGS84             
- GeoJSON, Shapefile          

### 2. Use Case, den wir vorgestellt haben
Aktuelles ÖV-Netz (auch mit Busstrecken)           
Siehe: https://github.com/datamapio/verkehrsnetz#woran-wir-arbeiten



## Update, 25. Juni 2021
An der gestrigen #GeoUnconference gabs eine Gruppe zum Thema Verkehrsnetz und Mobilität. Die Wichtigkeit des Verkehrsnetzes war unbestritten in unserer Gruppe. 
Wichtig sind Qualität und Aktualität dieses Verkehrsnetzes. Bei Swisstopo wird das Verkehrsnetz in den Kategorien Schiene, Strasse, Wasser und Luft unterteilt. Was mir daran gefällt, ist dass neben dem Graphen auch Flächen (z.B. ein Bahnhof) eine Rolle spielen, wie auch Gewässer. Dies ist auch für uns wichtig. 
Auf der Strasse ist aber für uns ein zusätzlicher Bus-Netz-Layer (bzw. beim ÖV-Netz interessieren uns die Strassen nur insofern, als sich darauf öffentlicher Verkehr fortbewegt) unabdingbar und ich hoffe, nicht nur für uns.   
       
Die Lösung für Updates z.B. kurz-, mittel- und langfristige Unterbrechungen von Tram- oder Bus-Linien, saisonale Schifffahrt usw. könnte man über das Einspielen von Fahrplänen (GTFS) oder über manuelle Updates lösen. Dabei hätte gewisse Nutzer der Plattform auf ihre Gebiete, Regionen, Gemeinden usw. Zugriff und könnten dort Aenderungen vornehmen. Z.B. Ausfall der Strecke 6 vom Knoten Hardturm bis Knoten Endstation von Juni bis November 2021.        
      
Eine weitere Art von Änderungen wären Probleme des Graphen sichtbar zu machen, z.B. eine Kante/Edge, die im falschen Node endet. Diese Dinge würden an GIS-Büros übergeben, dies könnte regional oder national geschehen.     

Ich hoffe, dass wir bereits bei der nächsten #GeoUnconference konkret an einem Prototypen arbeiten können.




## Was wir brauchen

Einen "simplifizierten", aufdatierten Graphen (am ehesten Fachnetz TU des BAV?) für die gesamte Mobilität mit Nodes/Knoten und Edges/Kanten (inkl. Kilometrierung und Höhenmeter) und Transport Modi. Idealerweise werden daraus auch Dinge ersichtlich wie einzelne Bus- oder Tramlinien etc.       

Für die **GeoUnconference** könnte man das vorerst auf den öffentlichen Verkehr und auf die Schweiz mit Grenzregionen einschränken.      
Grundsätzlich brauchen wir das aber für alle Transport Modi und weltweit, da wir unsere GPS-Datenpunkte von [Posmo One](https://datamap.io/) auf einem Graphen abbilden wollen.
                 
Wichtig dabei ist, dass dieser Graph historisch und immer auch für die aktuelle Gegenwart funktioniert.              
Denn unsere Daten wurden gestern und werden heute und morgen erhoben. Und unser Map Matching ist nur so gut wie der Graph.

PS:       
Bei den Gemeindegrenzen haben wir bereits gesehen, was für Probleme entstehen, wenn der Bund diese nur periodisch (1 x pro Jahr) aufdatiert. Um z.B. eine Abstimmung als Karte darzustellen, mussten wir die über 10 Gemeinden von Bellinzona nach der Fusion zu einem grossen Ganzen zusammenführen.   
      

## Woran wir arbeiten

<img src="https://github.com/datamapio/verkehrsnetz/blob/main/h3_nodes_edges.png" width="1200" />

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
a) von aussen laufend aufdatieren kann und b) man jederzeit verschiedene Datensubsets herunterladen kann.               

Man könnte dann Anfragen/Download machen wie z.B.: 
- Gibt mir das gesamte Zug-Schienennetz im Kanton Zürich, Stand Mai 2021. 
- Gib mir alle neuen Tramlinien seit 2020 in der ganzen Schweiz. 


## Offene Fragen
- Zusammenarbeit
- Kontinuierliche Updates
- Finanzierung







Siehe:
- [unser Tweet](https://twitter.com/datamapio/status/1388849007607357442?s=20) vom 2021-05-02
- [swisstopo-Kolloquium "Verkehrsnetz CH"](https://www.swisstopo.admin.ch/de/swisstopo/veranstaltungen/colloque.detail.event.html/swisstopo-internet/events2021/colloquium-20-21/20210326.html) vom 2021-03-26
