FAQ
######

.. contents::
   :local:

Generell
***********

Die 10 Gebote der AhoyDTU
===========================

1. Du sollst nicht senden ohne Elko
2. Du sollst den Elko huldigen
3. Ein Elko ist durch nichts zu ersetzen außer durch noch mehr Elkos
4. Ohne Elko am NFR-Modul kein Support
5. Du sollst die Boot-Taste beim ESP32 während des Flashens drücken
6. Du sollst einen DNS in den Network Setting eintragen wenn Du statische IPs verwendest
7. Du sollst ein gutes Netzteil und ein „dickes“ USB-Kabel verwenden
8. Du sollst keine Adapterplatinen anschließen (Psalm 3, beim Heiligen Stefant)
9. Du sollst lesen die Changelogs bevor Du Fragen stellst und Issues aufmachst
10. Du sollst keine anderen DTUs neben Dir haben

Wo finde ich die aktuelle Firmware
====================================

Die aktuelle Firmware (Release) ist immer unter `Github Releases <https://github.com/lumapu/ahoy/releases>`_ zu finden. Zudem haben wir für euch noch einen Webservice eingerichtet, der auch ohne Login `jede Firmwareversion <https://fw.ahoydtu.de>`_ verfügbar macht - auch `Entwicklerversionen <https://fw.ahoydtu.de/fw/dev>`_.


Wie lautet das Standardpasswort für den WLAN AP (Access Point)
================================================================

Das Passwort lautet: ``esp_8266``, der WLAN AP ``AHOY-DTU``.


Ich habe mein Passwort vergessen, wie komme ich wieder in Ahoy?
================================================================

Ohne Passwort kein Zugriff. Es hilft nur den ESP komplett zurückzusetzen und eine anschließende Neueinrichtung. Am einfachsten geschieht das mit dem  `Online Installer <https://ahoydtu.de/web_install>`_


Kann ich Wechselrichter verschiedener Serien auslesen?
========================================================

Ja! Das geht durch den Anschluss mehrerer Funkmodule an einen ESP. Beachte, dass nur der ESP32 das CMT2300A Funkmodul unterstützt.


Wie viele Wechselrichter kann ich mit einer AhoyDTU auslesen?
===============================================================

Je nach ESP kann man 4 (ESP8266) oder bis zu 32 (ESP32) Wechselrichter auslesen. Dabei gilt zu beachten, dass die Wechselrichter sequenziell abgefragt werden, auch wenn zwei (verschiedene) Funkmodule verbaut sind.


Was bedeutet DTU?
===================

DTU bedeutet Data-Transfer-Unit. Das ist auch die Grundidee hinter Ahoy. AhoyDTU soll eine Brücke zwischen dem Wechselrichter und der Hausautomatisierung sein. Durch verschiedene Erweiterungen wurde dieses Konzept teilweise gebrochen, Beispiele: Display, History-Graph
Im Groben und Ganzen ist die AhoyDTU aber weiterhin als Brücke (Connector) zu sehen.


Kann Ahoy auch als Batteriewechselrichter eingesetzt werden?
==============================================================

Mit gewissen Voraussetzungen geht das. Hierfür muss der Wechselrichter so an den Akku angeschlossen werden dass die Kondensatoren am Eingang des Wechselrichters nicht zu schnell geladen werden (Strombegrenzung). Dies hier ist keine Anleitung wie man einen Wechselrichter in diesem Szenario einsetzt, soll aber grundsätzlich die Frage "ob das geht" beantworten.


Ahoy betreiben
*****************

Kann man den Wechselrichter in der Leistung begrenzen?
========================================================

Ja der Wechselrichter ist begrenzbar. Man kann den Wechselrichter entweder prozentual oder in Watt begrenzen. Die Begrenzung kann über drei Wege von statten gehen:

- über die Weboberfläche
- per MqTT
- per API Request

Durch die ``MqtTT`` und ``API`` Schnittstellen können die Wechselrichter auch automatisiiert im (kleinen) Sekundenbereich limitiert werden, d.h. eine Nulleinspeisung über ein externes Skript ist möglich.


Kann man den Wechselrichter auch dauerhaft auf 600W / 800W begrenzen?
=======================================================================

Ja die Wechselrichter bieten zwei Arten von Begrenzung: Eine temporäre Begrenzung (non persistent) und eine dauerhafte (persistent) Begrenzung. Es können auch beide gleichzeitig verwendet werden. Folgendes Szenario soll besser verständlich machen was gemeint ist:

Es wird ein HM-1500 eingesetzt, also ein 1500W Wechselrichter. Dieser soll um einem Balkonkraftwerk zu entsprechen auf 800W begrenzt sein. Diese 800W Begrenzung kann dauerhaft im Wechselrichter hinterlegt werden. Startet der Wechselrichter nach einer Nacht (er schaltet ab, sobald an seinen Eingängen kein Strom mehr anliegt) wieder ein, so startet er mit maximal 800W. Hat man jetzt zusätzlich einen Bezugszähler im Zugriff könnte man bei viel Verbrauch diesen statischen Wert temporär z.B. mit 1000W überschreiben.

.. note::

   Der absolute Wert sollte nicht zu oft verändert werden, schon garnicht über ein Skript. Da der Wert fest im Wechselrichter gespeichert wird, könnte die Speicherzelle Schaden von zu häufigem Speichern nehmen. Bisher ist noch kein solcher Fall bekannt geworden, aber wir warnen seit Beginn. Alles was unter 10000 Schreibzyklen bleib sollte unkritisch sein (auf die Lebenszeit des Wechselrichters gesehen).


Was sagen mir die Funkstatistiken (Radio Statisiken)?
========================================================

Klickt man in der Live-Ansicht unten auf den Balken, der sagt wann das letzte Paket empfangen wurde öffnet sich folgendes Popup:

   .. image:: ../images/faq/radioStatistics.png
      :width: 400
      :alt: Screenshot der Funktstatistiken (Radio Statistik)

   Im Allgemeinen hat Ahoy an verschiedenen Stellen Zähler, die insgesamt ein Aussage treffen wie gut das Funkmodul performt, bzw. wie gut die Verbindung ist. Grundsätzlich ist die Kommunikation bei den neueren Wechselrichtern (HMS- und HMT-Serie) stabiler, da sie auf 868Mhz funken. Die älteren Generationen funken auf 2.4Ghz.

   ===================  =====
   Feld                 Beschreibung
   ===================  =====
   TX count             Anzahl der gesendeten Pakete
   RX success           Anzahl der erfolgreich empfangenen Pakete (100% ist das Optimum)
   RX fail              Anzahl fehlgeschlagener Sendeversuche (sollte nahe 0 sein)
   RX no answer         Anzahl fehlgeschlagener Sendeversuche ohne eine Antwort vom Wechselrichter (sollte nahe 0 sein)
   RX fragments         Anzahl der Fragmente, die empfangen wurden. Ein Paket besteht oft aus mehreren Fragmenten daher ist die Zahl wesentlich größer als die anderen.
   TX retransmits       Anzahl der erneuten Sendeversuche (auf Fragmentbasis, daher auch hier eine höhere Anzahl)
   Inverter loss rate   Anzahl der verlorenen Pakete detektiert durch den Wechselrichter
   DTU loss rate        Anzahl der verlorenen Pakete detektiert durch die DTU
   ===================  =====

   Sind die ``RX no answer`` hoch kann es auch daran liegen, dass die DTU nachts versucht den / die Wechselrichter abzufragen. Das kann über eine Einstellung ``Pausieren in der Nacht`` abgestellt / reduziert werden.


Fehlersuche
*************


Mein Wechselrichter wird nicht erkannt
========================================

1. Zuerst sollte der Status der AhoyDTU geprüft werden unter ``System``. Hier sind vor allem der Zustand ``connected`` und der Status des Interrupt Pins wichtig. Der Interrupt Status darf nur während einer möglichen Kommunikation mit dem Wechselrichter bewertet werden.

   .. image:: ../images/faq/systemNrfStatus.png
      :width: 400
      :alt: Screenshot des NRF24 Status in ``System``

2. Die Anschlusseinstellungen für das NRF24 Modul prüfen. Im Bild der ESP8266 mit seinen NRF24 Einstellungen.

   .. image:: ../images/faq/configPinNrf.png
      :width: 400
      :alt: Screenshot der NRF24 Anschlusseinstellungen für den ESP8266

3. Ist es Tag oder Nacht? Der Wechselrichter antwortet nur solange er Strom von den Modulen bekommt, also nur tagsüber.
4. Prüfen, ob die grüne / rote LED des Wechelrichters blinkt, nur dann ist eine Kommunikation möglich.
5. Prüfen, ob das richtige Funkmodul im Einsatz ist:

   +------------------+-------------------+
   | Wechselrichter   | Funkmodul         |
   +==================+===================+
   | HM-xxxx          | NRF24             |
   +------------------+-------------------+
   | MI-xxxx          | NRF24             |
   +------------------+-------------------+
   | HMS-xxxx         | CMT2300A          |
   +------------------+-------------------+
   | HMT-xxxx         | CMT2300A          |
   +------------------+-------------------+
   | HMS-xxxxW        | nicht unterstützt |
   +------------------+----++++++++-------+


In der Live Ansicht sind die Wechelrichter grau dargestellt und die Daten aktualisieren sich nicht
====================================================================================================

Eine graue Darstellung bedeutet, dass Ahoy gerade keine erfolgreiche Funkverbindung mit dem Wechselrichter herstellen kann. Das sollte prinzipiell nur nachts so sein.


Auf dem Display wird der Graph nicht angezeigt, obwohl er aktiviert wurde
===========================================================================

Wichtig bei dieser Funktion ist die Einstellung der Koordinaten unter "Sonnenauf- und -untergang". Die Position ist notwendig, um die Grenzen des Graphen berechnen zu können.
