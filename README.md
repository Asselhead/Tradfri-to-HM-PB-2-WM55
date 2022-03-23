# Tradfri-to-HM-PB-2-WM55
Leiterplatte zum Umbau eines Ikea Tradfri Taster/Dimmer auf Homematic/AskSin++ HM-PB-2-WM55

Beim letzten Ikea Besuch bin ich mal wieder an den Tradfri Smart Home Komponenten hängen geblieben.
Aufgefallen ist mir dabei besonders ein kleiner formschöner AN/AUS Taster für schlappe ~~6€~~ 7€ (teurer geworden).

Es handelt sich um die Ikea Artikelnummer 704.085.95

![Tradfri01.jpg](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Tradfri01.jpg)

Da ich kein großer Freund von Betrieb und Wartung mehrerer Systeme (ioBroker/FHEM usw.) oder auch mehrerer Funkstandards (868MHz & Zigbee) bin,
habe ich mir den Tradfri Taster per Hardware Upgrade auf Homematic/ASKSIN umgebaut. Er ist damit ein direkter Ersatz für einen HM-PB-2-WM55.

Die Demontage des Tasters ist relativ einfach. Einfach mal nach IKEA TRÅDFRI On/Off Switch Teardown googlen.

Die Leiterplatte ist 1mm dick und hat 4 Lagen:

![TOP_ISO.png](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Top.png)
![BOT.png](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Bot.png)

Auf der Leiterplatte wird ein CC1101 Modul, der ATMEGA328P-AU, ein 8MHz Resonator, zwei Taster auf der Top und einer (Config) auf der Bot Seite bestückt:

![Top_Best.jpg](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Top_Best.jpg)
![Bot_Best.jpg](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Bot_Best.jpg)

Es wäre optional möglich einen Reset Baustein zu bestücken, ebenso wie eine Batterie Last Schaltung.
Dafür bitte in die Schaltung schauen und die Widerstandswerte den eigenen Vorstellungen anpassen.

# Schaltung

Die [Schaltung](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Docs/TradfritoHM-PB-2-WM55.pdf) besteht im wesentlichen aus der AskSin++ Beispielschaltung ergänzt durch zwei Taster. In Schaltung gibt es die Möglichkeit bei allen drei Tastern externe Pull-Up Widerstände zu bestücken. Das ist nur eine experimentelle Option und ist im Normalfall überflüssíg, da die internen Pull-Up Widerstände des Atmega im Sketch aktiviert sind.

# Bestückungszeichnung und BOM

Die Bestückungszeichnung kann [hier](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Docs/TradfritoHM-PB-2-WM55_Assy.pdf) heruntergeladen werden.
Eine spezielle Reichelt BOM habe ich nicht erstellt. Bitte die Bauteilwerte aus der BOM entnehmen. Es handelt sich ausschließlich um 0603 Kondensatoren/Widerstände.

Es ist zwar eigentlich genügend Platz auf der Leiterplatte, jedoch habe ich versucht zu vermeiden Bauteile innerhalb der Kreise an den vier Leiterplattenecken zu platzieren, da hier die Silikon-Abdichtungsmatte auf der Leiterplatte aufliegt und auch dafür sorgt, dass der Taster nach Betätigung immer wieder in die Ruheposition zurück geht.
Zwei der vier Silikon "Stößel" habe ich von hinten etwas mit einer Rasierklinge abgeschnitten, damit die Kante des CC1101 Modul nicht stört. Wäre aber ggf. gar nicht nötig gewesen. Muss man ausprobieren.

Für die Bestückung der Leiterplatte müssen auf jeden Fall die Batteriekontakte der original Tradfri Leiterplatte abgelötet und wieder verwendet werden. Das stellt kein großes Problem dar.
Etwas Lötzinn auf die Kontakte und dann mit einer großen Lötspitzen erhitzen.

Wer möchte kann die Taster von der Ikea Leiterplatte ablöten und weiter verwenden. Wer lieber neue auflöten möchte, wird bei LCSC fündig:

[S1 und S2](https://lcsc.com/product-detail/Tactile-Switches_XKB-Connectivity-TS-1187A-B-A-B_C318884.html)

[SW1](https://lcsc.com/product-detail/Tactile-Switches_XUNPU-TS-1088-AR02016_C720477.html)

# Gerberdaten

Die [Gerberdaten](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Gerber/Tradfri_to_HM.zip) können so direkt nach z.B. JLCPCB hochgeladen werden. Bitte Leiterplattendicke 1mm wählen. Es handelt sich um eine 4 Lagen Leiterplatte.

Wer Spaß mit den Leiterplatten hat, darf mir gerne nen Kaffee spendieren:

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/L3L52JYN0)

# Sketch

Als Sketch kommt der HM-PB-2-WM55 Sketch zum Einsatz. Dieser wurde von Jêróme erstellt und befindet sich auch schon in der Arduino Beispiel_AskSinPP

[Sketch](https://github.com/jp112sdl/Beispiel_AskSinPP/blob/master/examples/HM-PB-2-WM55/HM-PB-2-WM55.ino)

Der Sketch kann 1:1 übernommen werden.

# Programmierung

Für die Programmierung muss zunächst der Ardiuno Pro Mini Bootloader (8MHz/3,3V) aufgespielt werden. Dazu kann man temporär einen 2x3 Pin ISP Stecker auflöten, oder diesen mit ein paar Drähten verbinden. Das gleiche gilt für den 1x6 Pin Stecker/Buchse für das Aufspielen des Sketch per USB/Seriell Adapter. Da ich mehrere dieser Ikea Taster auf Homematic umrüsten möchte, habe ich mir aus Federkontakten (Pogo-Pins) einen Adapter gebaut mit dem ich die Leiterplatten ohne löten programmieren kann. Dazu habe ich einfach die Pogopins in eine Lochraster Leiterplatte gelötet und anschließend einen Rahmen darum gelegt um die Position der Leiterplatte über den Pogo Pins zu fixieren.

![ProgAdapter](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/ProgAdapter.jpg)

Die [STL](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Docs/Tradfri_Frame_Final.stl) habe ich mal angehängt, falls sich jemand den Rahmen ausdrucken und auf die Programmier-Lochrasterplatte (Epoxy) kleben möchte.

# Spannungsversorgung

Es empfiehlt sich eine Marken Knopfzelle vom Typ CR2032 zu verwenden. Knopfzellen haben einen sehr hohen Innenwiderstand. Dies führt dazu, dass bei größerer Belastung die Spannung sehr schnell einbricht. Größere Belastung bedeutet hier bereits >5mA. Üblicherweise dürfen Marken Knopfzellen für wenige Sekunden bis Max. 15-30mA belastet werden.
Wenn die HM-PB-2-WM55 Leiterplatte z.B. Konfigurationsdaten sendet, kann die Stromaufnahme auch für mehr als ein paar Sekunden 30mA überschreiten. Eine kleine Hilfe bringt es, wenn man die Stützkondensatoren für das CC1101 Modul möglichst groß (2x10µF) wählt. Wenn man den Taster nach der Programmierung noch am USB-Seriell Wandler testet und anlernt und ggf. eine Direktverknüpfung herstellt, sollte die Knopfzelle im normalen Betrieb keine Probleme haben.
Ein normaler Sendevorgang (Einschalten eine Aktors) dauert dann nur noch ca. 663ms, was die Knopfzelle problemlos wegsteckt. 

![Sendeimpuls](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Power_662ms.png)

Auch das Dimmen geht, weil hier mehrfach kurze Pakete gesendet werden.

Eine andere Option ist die Sendeleistung des CC1101 zu reduzieren. Dazu bitte im Forum nachschauen:
[Forumseintrag](https://homematic-forum.de/forum/viewtopic.php?f=76&t=70114)

# Antenne

Zur Verlegung der Antenne ist es ratsam einen Gehäusesteg, auf dem die Lpl. aufliegt, mit einer kleinen Kerbe zu versehen (Messer/Dremel). Die Antenne kann dann einfach einmal an der Leiterplattenkontour entlang ins Gehäuse gelegt werden. Man sieht genau, welcher Gehäusesteg gemeint ist. Zum Einbau kann es helfen die Antenne mit einem kleinen Stück Tesa zu fixieren.

# Fotos
![Eingebaut](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Eingebaut.jpg)
![Mit_Silikonmatte](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Mit_Silikonmatte.jpg)
![Batt_Comp](https://github.com/Asselhead/Tradfri-to-HM-PB-2-WM55/blob/main/Images/Batt_Comp.jpg)



# Lizenz

Creative Commons BY-NC-SA
Give Credit, NonCommercial, ShareAlike

![by-nc-sa.eu.png](https://github.com/Asselhead/Arduino-Pro-Mini-RF/blob/master/Images/by-nc-sa.eu.png)

Creative Commons License

This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.


