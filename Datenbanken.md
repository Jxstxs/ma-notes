



# Datenbanken

## Datenbanksystem: **DB und DBMS ergeben Informationssystem**

### Datenbankmanagementsystem

- Gesamtheit der Programme zur Verwaltung der Datenbank (zentrale Funktion der Manipulation, ..)

### Datenbank

- integrierter Persistenter Datenbestand einschließlich aller relevanten Informationen über dargestellte Daten
    - Datendefinitionen, Zugriffsrechte, Primärdaten

### Datenbanksystem

- elektronische Datenverwaltung, welche große Mengen an Daten effizient, widerspruchsfrei und dauerhaft speichert
- benötigte Teilmengen in bedarfsgerechten Darstellungsformen für Benutzer bereitstellt

## Datenverarbeitung

### Dateiorientiert

- Mehrfachspeicherung gleicher Daten
- Aufwendige Datenpflege
- Gefahr inkonsistenter Datenbestände
- logische Abhängigkeit => Programm und Daten
- Datenschutzprobleme

### Datenbankorientiert

- nicht Redundante Speicherung
- keine Speicherinkonsistenz
- Programm unabhängig
- leichtere Rechte Vergabe

## ANSI-SPARC

### internes Schema/Datensicht

- physische Speicherung der Daten
- Speicher Verteilung
- Speicher Typen (passende Datentypen)

### konzeptionelles Schema/Datensicht

- logische Struktur aller Daten
- unabhängig von Problemen der internen

### externes Schema/Datensicht

- Benutzersicht
- durch unterschiedliche Anwender unterschiedliche Daten

## Entwurf von Datenbanken

Modellierung auf konzeptioneller Ebene und Optimierung der Datenstruktur

- Realitätsausschnitt: externes Schema (Abstraktion)
- Datenmodell: konzeptionelle Schema (Spezifikation)
- Implementation: internes Schema (=> Datenbasis)

## Modellierung

### Entity-Relationship-Modell

- Ziel: Darstellung von Daten und Beziehungen => konzeptionelle Ebene
- Besteht aus:
    - Entität(Rechteck): realer Gegenstand => Kunde, Artikel, ...
    - Beziehung(Raute): Form der Beziehung => Kunde **kauft** Artikel, ...
    - Attribute(Ellipse): Eigenschaften => Name, Adresse, Preis, Stückzahl, ...

#### Kardinalitäten

- 1:1 => Mann(1)~~verheiratet~~Frau
- 1:c => Kunde(1)bekommt(c)Rabatt
    - ein Kunde bekommt keinen/einen Rabatt
- 1:n => Kunde(1)erteilt(n)Auftrag
- m:n => Mitarbeit(m)fährt(n)Firmenauto
    - Beziehung wird selbst zur Relation mit jeweiligen Primärschlüsseln

### Relationen-Modell

- Tabelle bestehend aus einer Spalte => Entität (Tabellenkopf)
- Attribute in den Zeilen

## Normalisierung

### Ziele

- Flexible, Stabile Datenbank => leichte Pflege
- Verhindern von Anomalien
    - Ändern: unterschiedliche Werte durch mehrere Attribute mit selben "Sinn"
    - Löschen: Überreste Gelöschter Daten durch Redundanz
    - Einfügen: nicht alle Attribute mit selben "Sinn" werden gleich Beschrieben(Daten eingefügt)
- geringe Redundanz => geringer Speicherbedarf
- leichte Erweiterungen

## ACID

Voraussetzung für Verlässliche Systeme

### Atomrarität (Abgeschlossenheit)

- entweder volle Ausführung oder gar keine => Transaktionen
    - DBMS sieht Transaktion als elementar Operation => ununterbrochen
    - erst "gültig" wenn fehlerfrei und komplett abgeschlossen
        - wenn Fehler => Rollback zur letzten fehlerfreien Aktion

### Konsistenz Erhaltung

- Sequenz von Operationen hinterlassen konsistenten Datenbestand
- Konsistenz wird erreicht durch
    - Normalisierung
    - Integritätsbedingungen
        - besonders: inhaltliche und referentielle
        - Bereichsintegrität: jeder Wert muss in einem Wertebereich liegen
        - Entitäts Integrität: Primkey muss eindeutig und nicht null sein
        - Referentielle Integrität: Fremdschlüssel muss entweder null oder ein existierender sein
    - Schlüssel

### Isolation (Abgrenzung)

- parallel laufende Operationen dürfen sich nicht gegenseitig beeinflussen

### Dauerhaftigkeit

- garantiert das Daten nach Operation dauerhaft im Datenbestand bestehen
- Transaktionlog: speichert alle schreib Transaktionen um diese zu reproduzieren

## Datenmodelle

legt die Struktur der zu speichernden Daten und deren Operatoren fest (löschen, ändern, ...)

### hierarchisches

- Baumstruktur
- leicht nachvollziehbarer Pfad zum Wurzelobjekt
- weist meist Redundanz auf

### netzwerk

- ohne Redundanz
- keine klare "Struktur"

### relationales

- ???
- Bsp: Oracle, DB2, ADABAS, MS Access

#### Grundlagen

- Relationen schema: gesamtheit aller Attribute
- Relation: gesamter Tabelleninhalt
- Attribut: "Spalte" in der Tabelle
- Attributwert
- Tupel: gesamte Zeile => ein Datensatz

#### Merkmale

- Datenverwaltung in 2D Tabellen
- Datensätze mit Primkey Identifiziert
    - ebenfalls zur Verknüpfung von Tabellen => logischer Aufbau
- Datenfelder haben Datentyp (Domäne) und können indiziert werden

#### Schlüssel

- infrage kommende Attribute => Schlüsselkandidaten
- Primärschlüssel: Identifiziert Datensatz eindeutig
- Sekundärschlüssel: alle Schlüsselkandidaten die keine Schlüssel sind
- Fremdschlüssel: Primärschlüssel einer anderen Relation
- kombinierter Schlüssel: Schlüssel bestehend aus mehreren Attributen

### objektorientiertes

- ???

# SQL

- Projektion: Auswahl bestimmter Attribute

```sql
SELECT Name, Alter FROM Personen;
```

- Selektion: Projektion mit Bedingung

```sql
SELECT Name, Alter FROM Personen WHERE Alter > 18;
```

- Verbunde: Verbindet 2 Relationen zu einer (Rechenintensiv)
    - Mengenvereinigung: Einfügen eines Tupels in eine Relation
        - INNER, LEFT, RIGHT Join)

```sql
SELECT p.Name, a.Abteilung FROM Personen as p INNER JOIN Abteilungen as a ON p.Abteil_Nummer = a.Abteil_Nummer;
```

    - Mengendifferenz: zum Entfernen aus einer Relation

```sql
SELECT * FROM Personen WHERE Personen.ID NOT IN (SELECT ID FROM Kunde);
```

    - Kartesisches Produkt (Durchschnittsmenge): Enthält Spalten beider Relationen

```sql
SELECT * FROM Personen, Abteilung WHERE Personen.ID = Abteilung.ID;
```
