Bedarfsoptimierte Leistungsregelung
#####################################

Allgemein
-----------

Das Modul 'Bedarfsoptimierte Leistungsregelung' (auch bekannt unter Zero-Export) erweitert Ahoy um die Möglichkeit, die WR nur so viel Strom zu erzeugen, wie im Haus benötigt wird.
Dazu wird die Leistung am Übergabepunkt (Zähler) gemessen und die Wechselrichter entsprechend geregelt.
Wir zeigen euch, wie Ihr es umsetzen könnt und was bei solch ein Projekt darauf zu beachten ist.

Wichtig zu wissen: Diese erweiterte Funktion ist derzeit nur für Modelreihen der ESP32-S3 verfügbar.

Aber was ist denn genau 'Zero-Export'? Dafür ein kleiner Exkurs.

Zero-Export
***********
Unser Ahoy managed den 0%-Einspeise-Modus (Zero Export).
Es werden die Inverter abgefragt und erzeugte PV-Leistung abgefragt. Die Messwerte an einer Messstelle (z.B. Zähler, Strommessgeräte) werden parallel erfasst und miteinander verrechnet. Um schlussendlich den Wert der überschüssigen Leistung zu erhalten.

Dieser Wert wird an den Wechselrichter zurückgeliefert, damit dieser sich an den aktuellen Haushaltsverbrauch anpassen kann. 

Was wird denn benötigt um so eine Regelung umzusetzen?
******************************************************

+ DTU (Ahoy)

+ den passenden Wechselrichter

+ Smart Meter

+ und um den Smart-Meter auszulesen (z.B. Tibber, Hichi, Volkszähler, oder andere).


Konfiguration
-------------

Hier gibt es die Möglichkeit bis zu 6 Gruppen zu hinterlegen. Diese haben hier den Sinn mehrere Quellen der Verbraucher zu hinterlegen.
Die Werte werden summiert und dann für die Regelung mit einbezogen. 

**Hinweis:** Wenn Hichi/Tibber oder Volkszähler genutzt werden soll, ist es ratsam diesen alleine zu nutzen. 
Da hier die Daten direkt vom Stromzähler abgefragt werden, reicht es alleine die Gesamtleistung auszulesen.

Die Einstellungen von Ahoy beinhalten eine Sektion ``Bedarfsoptimierte Leistungsregelung`` (hier zu sehen sind die Standardeintellungen):

.. image:: ../images/zeroExport/zeroExportSettings.png
  :width: 600
  :alt: zeroExport Einstellungen - Default

Konfiguration einer Gruppe
**************************

Um die Gruppe einzustellen, kann man auf der rechten Seite das Zahnrad drücken.

Es sollte sich ein Formular öffnen.
Siehe wie auf dem Bild.

.. image:: ../images/zeroExport/zeroExportSettingsGroupGeneral.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Allegemein - Default

``Gruppe`` wird vom System vergeben und ist gleichzeitig auch die ID der Gruppe.

``Enabled`` gibt die Gruppe zur Regelung gemäß den eingestellten Parametern frei. 

``Name`` kann frei vergeben werden. Dieses Feld wird vom System nicht benutzt und dient der Identifizierung der Gruppe.

**ACHTUNG:** Die Gruppe muss vor der Aktivierung vollständig konfiguriert sein.

PowerMeter
***************

Um den aktuellen Verbrauch auch zu messen, müssen hier jetzt die PowerMeter eingerichtet werden.

Um von einem SMART-Meter die Daten abzufragen muss man sich an die Schnittstelle hängen.

Mögliche Schnittstellen:

+ [Volkszähler](https://www.volkszaehler.org/), 

+ Hichi, 

+ Tibber (https://tibber.com/) (macht nur Sinn wenn ihr schon bei Tibber seid), 

+ etc..

.. image:: ../images/zeroExport/zeroExportSettingsGroupPowermeter.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Zähler - Default

``Type`` Shelly, Tasmota, Mqtt, Hichi, Tibber

``IP:`` IP-Adresse des Endgeräts

``JSON Path:`` data.json?node_id=1 (Tibber)

``Username:`` admin (Tibber)

``Password:`` Passwort des Gerätes

Note

Je nach wahl des Gerätes aus dem die Daten bezogen werden, ändert sich das Formular passend.
Sollte hier etwas vermisst werden. Erstellt ein Issue auf Github.



Inverter
***************

Im Reiter Rubrik befinden sich die Einstellungen für die der Gruppe angehörigen Wechselrichter.

.. image:: ../images/zeroExport/zeroExportSettingsGroupInverter.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Inverter - Default

``erste Spalte`` wird vom System vergeben und ist eine Nummerierung der verfügbaren Wechselrichter in dieser Gruppe.

``Enabled`` entscheidet, ob der Wechselrichter geregelt wird oder nicht. ACHTUNG: Einen Wechselrichter erst aktivieren, wenn er vollständig konfiguriert ist.

``Name`` ist der zu regelnde Wechselrichter. Er wird aus der Liste der in Ahoy konfigurierten Wechselricher ausgewählt.

``Regelziel`` ist entweder ``Sum`` oder der Aussenleiter ``L1, L2, L3`` an dem der Wechselrichter einspeist.

``Power (min)`` ist die minimale Leistung des Wechselrichters. Wird vom Wechselrichter eine kleinere Leistung gefordert, so wird der Wechselrichter ausgeschaltet. **ACHTUNG**: Bei Hoymiles wird bei weniger als 2% der Leistung abgeschaltet.

``Power (max)`` ist die maximale Leistung des Wechselrichters. **INFO**: Mehr Leistung als der WR kann ist nicht möglich.

Batterie
***************

Hier befinden sich die Einstellungen für den Batterieschutz. Wenn dieser aktiviert ist, wird die Spannung der Batterie  über jeden PV-Eingang 1 aller der Gruppe angehörenden Wechselrichter gemessen und mit den eingestellten Werten verglichen. Unterschreitet eine gemessene Spannung den Abschaltwert, werden alle der Gruppe angehörenden Wechselrichter ausgeschaltet. Sobald alle gemessenen Spannungen den Einschaltwert wieder überschreiten werden alle der Gruppe angehörenden Wechselrichter wieder eingeschaltet.

.. image:: ../images/zeroExport/zeroExportSettingsGroupBattery.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Batterie - Default

Erweiterte Einstellungen
************************

Hier befinden sich die Einstellungen für die Regelung.

.. image:: ../images/zeroExport/zeroExportSettingsGroupAdvanced.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Erweiterte Einstellungen - Default

``SetPoint (Watt)`` Setzt die Leistung auf die geregelt werden soll (Standard 0 Watt). 100 regelt auf einen Bezug von 100 W, -600 auf eine Einspeisung von 600W.


``Refresh rate (sec)`` Aktualisierungsrate wie oft geregelt werden soll (Standard 10 sec.)


``Power tolerances (Watt)`` Toleranz im dem nicht aktiv geregelt werden soll (Standard 10 Watt).


``Group Power max (Watt)`` Maximalleistung die für die Gruppe gesetzt werden soll.


``Kp:`` P-Regler https://de.wikipedia.org/wiki/Regler#P-Regler_(P-Anteil)

``Ki:`` I-Regler https://de.wikipedia.org/wiki/Regler#I-Regler_(I-Anteil)

``Kd:`` D-Regler https://de.wikipedia.org/wiki/Regler#D-Glied_(D-Anteil)



Log / Debug-Modus
-----------------

Es existieren zwei Debugmöglichkeiten, die in der Konfiguration aktiviert werden können.
- Log over Webserial

- Log over MQTT

Dabei werden je nach Modul der Regelung unterschiedliche Json-Datensätze ausgegeben.

*Änderungen und Irrtümer vorbehalten*

.. code-block:: bash

    ze: {"group":0,"type":"groupWaitRefresh","B":45930169,"next":"GETINVERTERACKS","E":45930169,"D":0}

.. code-block:: bash

    ze: {"group":0,"type":"groupGetInverterAcks","B":45930171,"iv":[{"id":0},{"id":1},{"id":2}],"wait":false,"E":45930172,"D":1}

.. code-block:: bash

    ze: {"group":0,"type":"groupGetInverterData","B":45930185,"iv":[{"id":0},{"id":1},{"id":2}],"E":45930186,"D":1}

.. code-block:: bash

    ze: {"group":0,"type":"groupBatteryprotection","B":45930199,"en":true,"inv":3,"U":52.29999924,"action":"On","err":"battSwitch 1 == isProducing()1","sw":true,"E":45930200,"D":1}

.. code-block:: bash

    ze: {"group":0,"type":"groupGetPowermeter","B":45930213,"mod":"getPowermeterWattsShelly","HTTP_URL":"http://172.16.16.31/status","P":-440.6900024,"P1":-589.0300293,"P2":60.77000046,"P3":87.56999969,"E":45930275,"D":62}

.. code-block:: bash

    ze: {"group":0,"type":"groupController","B":45930288,"w":30,"x":-440.6900024,"x1":-589.0300293,"x2":60.77000046,"x3":87.56999969,"e":470.6900024,"e1":619.0300293,"e2":-30.77000046,"e3":-57.56999969,"Kp":-0.477999985,"Ki":0,"Kd":0,"Ta":5120,"yP":-224.9898071,"yP1":-295.8963318,"yP2":14.70805931,"yP3":27.51845932,"esum":-402851.5625,"esum1":115841.5703,"esum2":-331159.2813,"esum3":-10893.54199,"yI":0,"yI1":0,"yI2":0,"yI3":0,"ealt":1404.369995,"ealt1":1230.380005,"ealt2":270.3099976,"ealt3":-36.31999969,"yD":0,"yD1":0,"yD2":0,"yD3":0,"yPID":-224.9898071,"yPID1":-295.8963318,"yPID2":14.70805931,"yPID3":27.51845932,"E":45930289,"D":1}

.. code-block:: bash

    ze: {"group":0,"type":"groupPrognose","B":45930344,"E":45930344,"D":0}

.. code-block:: bash

    ze: {"group":0,"type":"groupAufteilen","B":46662266,"y":-628.1015625,"y1":-629.8510742,"y2":-48.92329788,"y3":21.99278069,"0":"0 grpTarget: 0: ivPmin: 65535: ivPmax: 0: ivId_Pmin: 0: ivId_Pmax: 0","1":"1 grpTarget: 0: ivPmin: 65535: ivPmax: 0: ivId_Pmin: 0: ivId_Pmax: 0","2":"2 grpTarget: 1: ivPmin: 50: ivPmax: 50: ivId_Pmin: 1: ivId_Pmax: 1","3":"3 grpTarget: 1: ivPmin: 70: ivPmax: 70: ivId_Pmin: 2: ivId_Pmax: 2","4":"4 grpTarget: 0: ivPmin: 65535: ivPmax: 0: ivId_Pmin: 0: ivId_Pmax: 0","5":"5 grpTarget: 0: ivPmin: 65535: ivPmax: 0: ivId_Pmin: 0: ivId_Pmax: 0","6":"6 grpTarget: 0: ivPmin: 65535: ivPmax: 0: ivId_Pmin: 0: ivId_Pmax: 0","103":"3","+deltaP":21.99278069,"102":"2","-deltaP":-48.92329788,"E":46662267,"D":1}

.. code-block:: bash

    ze: {"group":0,"type":"groupSetLimit","B":45930422,"inv":2,"limit":116,"wait":60,"data":{"val":116,"id":3,"path":"ctrl","cmd":"limit_nonpersistent_absolute"},"E":45930423,"D":1}

.. code-block:: bash

    ze: {"group":0,"type":"resetWaitLimitAck","B":45931128,"id":2,"inv":1,"wait":0,"E":45931128,"D":0}

.. code-block:: bash

    ze: {"group":0,"type":"newDataAvailable","B":45930845,"avail":true,"id":3,"inv":2,"zeL":116,"ivL":88,"ivPm":400,"ivL%":22,"E":45930846,"D":1}
