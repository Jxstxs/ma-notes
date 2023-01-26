



# Netzwerke

## Klassifikation

### Ausdehnung

#### Local Area Network (LAN)

- nur wenige Quadrat Kilometer groß => privat Gebäude, ...
- nur ein Betreiber/Nutzer => Familie, ...
- meist Kupferkabel und Funknetze

#### Metropolitan Area Network (MAN)

- Ausdehnung von Stadt => ca 100 km²
- lokal verteilte Firmenbereiche, ...
- Kupferkabel und Glasfasernetz

#### Wide Area Network (WAN)

- Ausdehnung von Land
- kann zur Verbindung von [LANS](#local-area-network-lan) genutzt werden
- Kupferkabel und Glasfasernetz

#### Global Area Network (GAN)

- Ausdehnung von der Welt
- kann zur Verbindung von [WANS](#wide-area-network-wan) genutzt werden
- Kupferkabel und Glasfasernetz
    - gering Vernetzte Gebiete => Satellitennetz

## Übertragungsmedien

### Kupferkabel

#### Koaxialkabel (BNC-Kabel)

- Geschwindigkeit: 10MBit/s

##### Aufbau

- Außenmantel
- Masse: Metallnetz
- Isolation
- Kupferleitung

#### Twisted Pair Kabel

- Kupferkabel mit Adern, welche verdreht sind

### Glasfaser

#### Aufbau

- Hülle
- Lackierung
- Mantel
- Kern
- Vollader
- Kompaktader
- Hohlader
- Bündelader
- Mehradriges Kabel

#### Übertragungsart

L(E)D erzeugt Licht, welches durch Totalreflexion das Signal im Kern transportiert

#### Probleme

- Dämpfung: Minderung der Signalamplitude bei Transport
    - Prevention
        - Laserdioden
        - Minimierung des Leit Durchmessers
    - Provokation
        - Beugung statt Reflexion

### Funknetz

#### Aufbau

- Sender/Empfänger
- Netzwerkkarten
- Access Point

#### Probleme

- Dämpfung: Verringerung der Feldstärke durch Absorption und Reflexion
    - Stahlbeton, Gelände, Wetter

### Berechnung


## Topologien

physische und logische Verbindung der Geräte
      physisch: Aufbau Hardware
      logisch: Nutzung der Netze

### Bus

Alle an einem Kabel angeschlossen

#### Vorteile

- keine Zusatzgeräte, geringe Kabelmenge
- einfacher Aufbau
- leicht erweiterbar

#### Nachteile

- Trennung zur Hauptader => Netzausfall
- aufwendige Fehlersuche

### Stern

Jeder Rechner mit Hub/Layer 2 Switch mit P2P verbunden

#### Vorteile

- leichte Fehlersuche
- hohe Übertragungsraten möglich
- leicht erweiterbar

#### Nachteile

- zusatzkosten => Geräte
- hoher Kabelaufwand

#### Möglichkeiten

- physisch: Stern
- logisch:
    - Bus Hub Unit: Packet wird an jeden Rechner gesendet
    - Layer 2 Switch: Packet wird nur an Zielrechner gesendet
    - Ring: ?

### Ring

Jeder Rechner hat Vor und Nachgänger
      IRL: meist Doppelring

#### Vorteile

- Durch Aufbau optimierbare Packet Wege
- geringer Kabelaufwand
- leicht erweiterbar

#### Nachteile

- lange Reaktionszeit bei großen Ringen
- hohe Abhängigkeit des Gesamtsystems von der Einzelleistung

## Zugriffsverfahren

regelt wie auf das Netzwerk an sich und dessen Ressourcen zugegriffen darf

### Carrier Sense Multiple Access / Collision Detection (CSMA/CD)

