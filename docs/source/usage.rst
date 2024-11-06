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
Das Dashboard bietet eine klare und detaillierte Übersicht über die Leistung Ihrer Photovoltaikanlagen.

   Obere Übersicht: 
      Im oberen Kasten sehen Sie eine allgemeine Übersicht der aktuellen PV-Anlage. Hier werden die wichtigsten Leistungsdaten wie die aktuelle Erzeugung und der Gesamtstatus der Anlage angezeigt.

   Detaillierte Moduldaten: 
      Im unteren Bereich sind die einzelnen Photovoltaikmodule in vier blauen Blöcken dargestellt. Jede dieser Blöcke enthält spezifische Eigenschaften und Leistungsdaten der jeweiligen Module, sodass Sie den Zustand und die Effizienz jedes Moduls individuell überwachen können.

   Gesamtübersicht bei mehreren Anlagen: 
      Wenn mehr als eine PV-Anlage vorhanden ist, erscheint ganz oben ein Kasten in oranger/brauner Farbe. Dieser Bereich zeigt die summierte aktuelle Leistung aller Anlagen an, wodurch Sie einen schnellen Überblick über die gesamte erzeugte Energie erhalten.

.. note::

  Die Daten werden live abgefragt, was bedeutet, dass sie stets aktuell sind und Ihnen jederzeit eine präzise Übersicht über den aktuellen Zustand und die Leistung Ihrer PV-Anlagen bieten._.

History
*******************
In der 2D-Diagramm-Anzeige sehen Sie den Verlauf der PV-Anlage in den letzten Stunden. Die x-Achse stellt die Zeit dar, während die y-Achse die Leistung in Watt anzeigt. Durch die Diagrammverläufe können Sie den Energieertrag und mögliche Schwankungen über den Tag hinweg nachvollziehen. Die Tagesgrafik funktioniert nur wenn in den Einstellungen auch die Daten für Sunrise & Sunset eingetragen sind, ansonsten bleibt die Anzeige leer.

Webserial
*******************
Die Konsole zeigt allgemeine Debug-Daten an, die Entwicklern helfen, Fehler genauer nachzuvollziehen und zu beheben.

Settings
*******************
Hier können Einstellungen vorgenommen werden, auf der Sie verschiedene Parameter für Ihre PV-Anlage konfigurieren können.

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


Activate all new tags
~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ 

- Match: ``Any version``
- Version type: ``Tag``
- Action: ``Activate version``

Activate only new branches that belong to the ``1.x`` release
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Custom match: ``^1\.\d+$``
- Version type: ``Branch``
- Action: ``Activate version``

Delete an active version when a branch is deleted
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Match: ``Any version``
- Version type: ``Branch``
- Action: ``Delete version``

Diverse Werte und den Tageserzeugszähler am Mitternacht zurücksetzen.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Die Werte werden um 0:00 Uhr zurück gesetzt.

.. note::

   You can also create two rules:
   one to match ``-stable`` and other to match ``-release``.





NTP Server
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Der Zeitserver.

Sonnen Auf/-Untergang
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Auf- und Sonnenuntergangs-Berechnung findet hier statt.

MQTT
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Nur für Nerds.

Pinout Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Wichtig für Diejenigen die selbst ein Board gebaut haben und die Portion mit dem gewissen Etwas heraus holen wollen.

Display Config
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
OLED, ePaper, LCD,... alles was das Herz begehrt.

Bedarfsoptimierte Leistungsregelung
------------------------
Vonnöten für Akku und Zero-Export Enthusiasten.

System
*******************
Aktuelle System-Infos.
