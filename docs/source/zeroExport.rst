Bedarfsoptimierte Leistungsregelung
#####################################

Das Modul "Bedarfsoptimierte Leistungsregelung" ergänzt Ahoy um die Möglichkeit nur so viel Leistung(Strom) zu erzeugen wie im Haus benötigt wird.

Um das zu ermöglichen, wird die Leistung am Übergabepunkt (Zähler) gemessen und die Wechselrichter entsprechend geregelt.

Konfiguration
***************

Die Einstellungen von Ahoy beinhalten eine Sektion ``Bedarfsoptimierte Leistungsregelung`` (hier zu sehen sind die Standardeintellungen):

.. image:: ../images/zeroExport/zeroExportSettings.png
  :width: 600
  :alt: zeroExport Einstellungen - Default

Um die Bedarfsoptimierte Leistungsregelung zu aktivieren, ...

.. image:: ../images/zeroExport/zeroExportSettingsGroupGeneral.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Allegemein - Default

.. image:: ../images/zeroExport/zeroExportSettingsGroupPowermeter.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Zähler - Default

.. image:: ../images/zeroExport/zeroExportSettingsGroupInverter.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Inverter - Default

.. image:: ../images/zeroExport/zeroExportSettingsGroupBattery.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Batterie - Default

.. image:: ../images/zeroExport/zeroExportSettingsGroupAdvanced.png
  :width: 600
  :alt: zeroExport Einstellungen Gruppe Erweiterte Einstellungen - Default


Log
*****

Die Bedarfsoptimierte Leistungsregelung hat zwei verschiedene Debugmöglichkeiten, die in der Konfiguration aktiviert werden können.
- Log over Webserial
- Log over MQTT

Dabei werden je nach Modul der Regelung unterschiedliche JsonDatensätze ausgegeben.
