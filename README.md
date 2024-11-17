# Datenbankprojekt in SQL für eine online Büchertausch-App
## Projektbeschreibung

Die Buchtausch-App ist eine Plattform, die es Benutzer ermöglicht, Bücher in ihrer lokalen Gemeinschaft auszutauschen. Ziel ist es, eine benutzerfreundliche Datenbank zu erstellen, die es den Benutzern ermöglicht, ihre nicht mehr benötigten Bücher anzubieten und Bücher, die sie gerne lesen würden, auszuleihen. Die Benutzer können über die App ihre Bücher verwalten, Ausleihvorgänge koordinieren und sehen, welche Bücher in ihrer Nähe verfügbar sind.

## Features

- Buchverwaltung: Benutzer können ihre Bücher zum Verleih anbieten und die Bücher anderer ausleihen.
- Standortbasierte Suche: Eine Kartenansicht zeigt verfügbare Bücher in der Nähe an.
- Benutzerdatenverwaltung: Speicherung von Informationen über die Benutzer, die Bücher einstellen und ausleihen.
- Ausleihmanagement: Koordination von Ausleih- und Rückgabeprozessen
- Bewertungsmanagement: Benutzer können die Bücher und Ausleihvorgänge bewerten

## ERM-Modell
![grafik](https://github.com/user-attachments/assets/16929df5-4373-486c-b72f-2253516eaa83)


## Datenbankstruktur
Die Datenbank besteht aus 23 Tabellen, die wie folgt strukturiert sind:

**`adresse`**: Dies ist eine Beziehungstabelle, die die Tabellen `land`, `ort` und `benutzende` miteinander verknüpft.

**`ausleihdauer`**: Diese Tabelle speichert die Ausleihdauer in Tagen.

**`ausleihe`**: Dies ist eine Beziehungstabelle, die der Verwaltung von Ausleihen und Rückgaben von Büchern dient. Sie verknüpft die Tabellen `benutzende` und `buchexemplar` miteinander.

**`autor`**: In dieser Tabelle werden die Autoren gespeichert.

**`autoren_schreiben_bücher`**: Dies ist eine Beziehungstabelle, in der die Tabelle `autor` und `buchtitel` miteinander verknüft werden.

**`benutzende`**: In dieser Tabelle werden benutzerspezifische Daten wie Name, Emailadresse und Passwort gespeichert.

**`benutzende_haben_benutzerrollen`**: Dies ist eine Beziehungstabelle, in der die Tabelle `benutzende` und `benutzerrolle` miteinander verknüft werden.

**`benutzer_versandoptione`**: Dies ist eine Beziehungstabelle, in der die Tabelle `benutzende` und `versandoptionen` miteinander verknüft werden.

**`benutzer_zeitslots`**: Dies ist eine Beziehungstabelle, in der die Tabelle `benutzende` und `zeitslots` miteinander verknüft werden.

**`benutzerrolle`**: Diese Tabelle speichert die möglichen Benutzerrollen.

**`bewertung`**: Dies ist eine Beziehungstabelle, in der die Tabelle `buchtitel` und `benutzende` miteinander verknüft werden.

**`buchexemplar`**: Dies ist eine Beziehungstabelle, in der die Tabelle `buchtitel`, `benutzende` und `zustand`  miteinander verknüft werden.

**`buchtitel`**: Dies ist eine Beziehungstabelle, in der die Tabelle `buchtitel` und `verlag`  miteinander verknüft werden.

**`bücher_gehörenzu_genre`**: Dies ist eine Beziehungstabelle, in der die Tabelle `buchtitel` und `genre`  miteinander verknüft werden.

**`genre`**: Diese Tabelle verwaltet die Genres, die Bücher zugeordnet werden können.

**`land`**: In dieser Tabelle werden die Länder gespeichert.

**`ort`**: In dieser Tabelle werden die Wohnorte der Benutzenden gespeichert.

**`verlag`**: Diese Tabelle speichert die Verlagshäuser.

**`versandoptionen`**: Diese Tabelle speichert die möglichen Versandoptionen.

**`zeitslots`**: Diese Tabelle speichert die möglichen Zeitslots, in denen Bücher bei Usern abgeholt werden können.

**`zustand`**: Diese Tabelle speichert die möglichen Zuständer der Bücher inkl. Beschreibung.

**`View - bewertung_user`**: Diese Ansicht zeigt, welcher Nutzer, welchen Buchtitel wie bewertet hat. So kann sich schnell ein Überblick verschafft werden, welche Bücher beliebt und welche unbeliebt sind. Letzteres kann zum Anlass genommen werden, diese Bücher nicht mehr anzubieten.

**`View - wer_hat_was_ausgeliehen`**: Diese Ansicht zeigt, welcher Nutzer welchen Buchtitel von wann bis wann ausgeliehen hat. Hieraus kann abgeleitet werden, wer ein eher "langsamer" Leser ist.

Hinweis: Folgende Ausrücke werden Synonym für `benutzende` im Bereich der Fremdschlüsselverknüpfung verwendet:
![grafik](https://github.com/user-attachments/assets/bfcb35b9-1845-4419-be05-9fcf9c4ba1af)

Hinweis: Folgende Ausrücke werden Synonym für `buchtitel` im Bereich der Fremdschlüsselverknüpfung verwendet:
![grafik](https://github.com/user-attachments/assets/5a69430a-df03-4fd5-a23a-256c9b7adea3)

## Installation 

1. **Voraussetzungen**:
   - Stelle sicher, dass mySQL Workbench installiert ist.
  
3. **Schritt-für-Schritt-Anleitung**
   - Klone das Repository:
  ```bash
     git clone https://github.com/Morgaine007/Projekt-Data-Mart-Erstellung-in-SQL.git
```
   - Lade die Datei 'code.sql' herunter.
   - Dann in mySQL Workbench auf File > Open SQL Script klicken und Datei 'code.sql' importieren und ausführen.
   ![grafik](https://github.com/user-attachments/assets/48f6e01a-3a35-4c72-927d-596243009550)
   - Erstelle die Datenbank und führe die SQL-Skripte in folgender Reihenfolge aus:
     1. `tests_positiv.sql` – Führt positive Tests zur Überprüfung der Funktionalität der Datenbank durch.
     2. `tests_negativ.sql` – Führt negative Tests zur Simulation ungültiger Eingaben und Fehler durch.
    
## Verwendung

1. **Erstellen und Initialisieren der Datenbank**:
   - Führe das `code.sql`-Skript aus, um die Datenbank zu erstellen und die Tabellen zu initialisieren.

2. **Durchführen von Abfragen**:
   - Du kannst Abfragen wie folgt ausführen:
     ```sql
     SELECT * FROM büchertausch.app.buchexemplar WHERE BuchID = 1;
     ```
   - Weitere Abfragen findest du in der Datei `tests_positiv.sql`.

3. **Hinzufügen und Bearbeiten von Daten**:
   - Füge Daten über SQL-INSERT-Befehle hinzu oder aktualisiere bestehende Datensätze mit SQL-UPDATE-Befehlen.

## Tests

Das Projekt enthält zwei Arten von Tests:

1. **Positive Tests**:
   - Überprüfung, ob die grundlegenden Datenbankoperationen wie Einfügen, Aktualisieren, Löschen sowie die Fremdschlüsselbeziehungen ordnungsgemäß funktionieren.
   - Diese Tests findest du in der Datei `tests_positiv.sql`.

2. **Negative Tests**:
   - Überprüfung, ob die Datenbank korrekt auf ungültige Eingaben reagiert (z.B. ungültige Datenformate oder das fehlen von Pflichtfeldern).
   - Diese Tests findest du in der Datei `tests_negativ.sql`.
