AhoyDTU Dokumentation
===================================

**AhoyDTU** ist ein Projekt um Wechselrichter der Marke Hoymiles mit eigener Hardware auszulesen. Es basiert im wesentlichen aus einem ESP und einem Funkmodul. Die Hardware kann für weniger als 20€ zusammengebaut werden und macht damit den Wechselrichter per MqTT erreichbar. Es wird neben den aktuellen Produktionsdaten auch die Möglichkeit der Ansteuerung des Wechselrichters bereitgestellt. Damit lässt sich der Wechselrichter zum Beispiel in seiner Leistung begrenzen.

Das Projekt ist Open Source und wird unter einer CC-BY-NC-SA 4.0 Lizenz auf `Github <https://github.com/lumapu/ahoy>`_ veröffentlicht. Das Projekt hat auch eine `Website <https://ahoydtu.de>`_, die einen Online-Installer enthält. Die `aktuelle Firmware <https://fw.ahoydtu.de>`_ ist ohne Login jederzeit in verschiedenen Verisonen verfügbar.

.. note::

   Dieses Projekt ist noch im Entwicklungsstadium

**Warning: HMS-XXXXW-2T WiFi inverters are not supported. They have a 'W' in their name and a DTU serial number on its sticker

Achtung Vorsicht: HMS-XXXXW-2T WiFi Wechselrichter werden nicht unterstützt. Sie haben ein 'W' im Modellnamen und eine DTU-Seriennummer auf dem Aufkleber.**

Inhalte
--------

.. toctree::

   usage
   mqtt
   api
   faq
   protocol
   zeroExport
