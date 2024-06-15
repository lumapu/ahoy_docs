Einleitung
======================

Zusammenbau
--------------------------------

Installation
--------------------------------
Am einfachsten kann die aktuelle Firmware (Release) auf den ESP mit unserem `Webinstaller <https://ahoydtu.de/web_install>`_ installiert werden. Hierzu wird ein 'Chromium-Browser' benötigt, d.h. Google Chrome oder Microsoft Edge.

Weboberfläche
--------------------------------
Was bedeutet was?

Live
*******************
Das Dashboard bietet eine klare und detaillierte Übersicht über die Leistung Ihrer Solaranlagen.

   Obere Übersicht: 
      Im oberen Kasten sehen Sie eine allgemeine Übersicht der aktuellen Solaranlage. Hier werden die wichtigsten Leistungsdaten wie die aktuelle Erzeugung und der Gesamtstatus der Anlage angezeigt.

   Detaillierte Moduldaten: 
      Im unteren Bereich sind die einzelnen Solarmodule in vier blauen Blöcken dargestellt. Jede dieser Blöcke enthält spezifische Eigenschaften und Leistungsdaten der jeweiligen Module, sodass Sie den Zustand und die Effizienz jedes Moduls individuell überwachen können.

   Gesamtübersicht bei mehreren Anlagen: 
      Wenn mehr als eine Solaranlage vorhanden ist, erscheint ganz oben ein Kasten in orange/brauner Farbe. Dieser Bereich zeigt die summierte aktuelle Leistung aller Anlagen an, wodurch Sie einen schnellen Überblick über die gesamte erzeugte Energie erhalten.

.. note::

  Die Daten werden live abgefragt, was bedeutet, dass sie stets aktuell sind und Ihnen jederzeit eine präzise Übersicht über den aktuellen Zustand und die Leistung Ihrer Solaranlagen bieten._.

History
*******************
In der 2D-Diagramm-Anzeige sehen Sie den Verlauf der Solaranlage in den letzten Stunden. Die x-Achse stellt die Zeit dar, während die y-Achse die Leistung in Watt anzeigt. Durch die Diagrammverläufe können Sie den Energieertrag und mögliche Schwankungen über den Tag hinweg nachvollziehen.

Webserial
*******************
Die Konsole zeigt allgemeine Debug-Daten an, die Entwicklern helfen, Fehler genauer nachzuvollziehen und zu beheben.

Settings
*******************
Hier können Einstellungen vorgenommen werden, auf der Sie verschiedene Parameter für Ihre Solaranlage konfigurieren können.

System Config
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
kleine Allgemeine Einstellungen

Netzwerk
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Alles rund um Thema Netzwerk

Protection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Wenn Thema Sicherheit mal ganz groß geschrieben werden soll.

Inverter
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Hier können die Invertert erfasst und Eingestellt werden. 
Zusätzlich auch das Verhalten von Ahoy unter bestimmten Bedingungen.

NTP Server
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Der Zeit-Server.

Sonnen Auf/-Untergang
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Auf und Sonnenuntergang berchnung findet hier statt.

MQTT
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Nur für Nerds.

Pinout Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Wichtig für die jenigen die selbst ein Board gebaut haben und die Portion mit dem gewissen etwas heraus holen wollen.

Display Config
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
OLED, ePaper, LCD,... alles was das Herz begehrt.

Bedarfsoptimierte Leistungsregelung
------------------------
Von nöten für Akku und Zero-Export Enthusiast.

System
*******************
Aktuelle System Infos.
