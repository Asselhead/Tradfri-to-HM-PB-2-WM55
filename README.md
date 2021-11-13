# Tradfri-to-HM-PB-2-WM55
Leiterplatte zum Umbau eines Ikea Tradfri Taster/Dimmer auf Homematic/AskSin++ HM-PB-2-WM55

Beim letzten Ikea Besuch bin ich mal wieder an den Tradfri Smart Home Komponenten hängen geblieben.
Aufgefallen ist mir dabei besonders ein kleiner formschöner AN/AUS Taster für schlappe 6€.

Es handelt sich um die Ikea Artikelnummer 704.085.95

![Tradfri01.jpg](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Tradfri01.jpg)

Da ich kein großer Freund von Betrieb und Wartung mehrerer Systeme (ioBroker/FHEM usw.) oder auch mehrerer Funkstandards (868MHz & Zigbee) bin,
habe ich mir den Tradfri Taster per Hardware Upgrade auf Homematic/ASKSIN umgebaut. Er ist damit ein direkter Ersatz für einen HM-PB-2-WM55.

Die Demontage des Tasters ist relativ einfach. Einfach mal nach IKEA TRÅDFRI On/Off Switch Teardown googlen.

Die Leiterplatte ist 1mm dick und hat 4 Lagen:

![TOP_ISO.png](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Top.png)
![BOT.png](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Bot.png)

Auf der Leiterplatte wird ein CC1101 Modul, der ATMEGA328P-AU, ein 8MHz Resonator, zwei Taster auf der Top und einer (Config) auf der Bot Seite:

![Top_Best.jpg](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Top_Best.jpg)
![Bot_Best.jpg](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Bot_Best.jpg)

Es wäre optional möglich einen Reset Baustein zu bestücken, ebenso wie eine Batterie Last Schaltung.
Dafür bitte in die Schaltung schauen und die Widerstandswerte den eigenen Vorstellungen anpassen.

# Schaltung

Die [Schaltung](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Docs/TradfritoHM-PB-2-WM55.pdf) besteht im wesentlichen aus der AskSin++ Beispielschaltung ergänzt durch zwei Taster.

# Bestückungszeichnung und BOM

Die Bestückungszeichnung kann [hier](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Docs/TradfritoHM-PB-2-WM55_Assy.pdf) heruntergeladen werden.
Eine spezielle Reichelt BOM habe ich nicht erstellt. Bitte die Bauteilwerte aus der BOM entnehmen. Es handelt sich ausschließlich um 0603 Kondensatoren/Widerstände.

Es ist zwar eigentlich genügend Platz auf der Leiterplatte, jedoch habe ich versucht zu vermeiden Bauteile innerhalb der Kreise an den vier Leiterplattenecken zu platzieren, da hier die Silikon-Abdichtungsmatte auf der Leiterplatte aufliegt und auch dafür sorgt, dass der Taster nach Betätigung immer wieder in die Ruheposition zurück geht.
Zwei der vier Silikon "Stößel" habe ich von hinten etwas mit einer Rasierklinge abgeschnitten, damit die Kante des CC1101 Modul nicht stört. Wäre aber ggf. gar nicht nötig gewesen. Muss man ausprobieren.

Für die Bestückung der Leiterplatte müssen auf jeden Fall die Batteriekontakte der original Tradfri Leiterplatte abgelötet und wieder verwendet werden. Das stellt kein großes Problem dar.
Etwas Lötzinn auf die Kontakte und dann mit einer großen Lötspitzen erhitzen.

# Gerberdaten

Die Gerberdaten können so direkt nach z.B. JLCPCB hochgeladen werden. Bitte Leiterplattendicke 1mm wählen.







