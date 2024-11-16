# Datenbankprojekt in SQL für eine online Büchertausch-App
## Projektbeschreibung

Die Buchtausch-App ist eine Plattform, die es Benutzer ermöglicht, Bücher in ihrer lokalen Gemeinschaft auszutauschen. Ziel ist es, eine benutzerfreundliche Datenbank zu erstellen, die es den Benutzern ermöglicht, ihre nicht mehr benötigten Bücher anzubieten und Bücher, die sie gerne lesen würden, auszuleihen. Die Benutzer können über die App ihre Bücher verwalten, Ausleihvorgänge koordinieren und sehen, welche Bücher in ihrer Nähe verfügbar sind.

## Features

- Buchverwaltung: Benutzer können ihre Bücher zum Verleih anbieten und die Bücher anderer ausleihen.
- Standortbasierte Suche: Eine Kartenansicht zeigt verfügbare Bücher in der Nähe an.
- Benutzerdatenverwaltung: Speicherung von Informationen über die Benutzer, die Bücher einstellen und ausleihen.
- Ausleihmanagement: Koordination von Ausleih- und Rückgabeprozessen
- Bewertungsmanagement: Benutzer können die Bücher und Ausleihvorgänge bewerten

## Datenbankstruktur
Die Datenbank besteht aus 21 Tabellen, die wie folgt strukturiert sind:

**`adresse`**: Dies ist eine Beziehungstabelle, die die Tabellen `land`, `ort` und `benutzende` miteinander verknüpft.

**`ausleihdauer`**: Diese Tabelle speichert die Ausleihdauer in Tagen.

**`ausleihe`**: Dies ist eine Beziehungstabelle, die der Verwaltung von Ausleihen und Rückgaben von Büchern dient. Sie verknüpft die Tabellen `benutzende` und `buchexemplar` miteinander.

**`autor`**: In dieser Tabelle werden die Autoren gespeichert.

**`autoren_schreiben_bücher`**: Dies ist eine Beziehungstabelle, in der die Tabelle `autor` und `buchtitel` miteinander verknüft werden.

**`benutzende`**: In dieser Tabelle werden benutzerspezifische Daten wie Name, Emailadresse und Passwort gespeichert.

**`benutzende_haben_benutzerrollen`**: Dies ist eine Beziehungstabelle, in der die Tabelle `benutzende` und `benutzerrolle` miteinander verknüft werden.

**`benutzer_versandoptionen`**: Dies ist eine Beziehungstabelle, in der die Tabelle `benutzende` und `versandoptionen` miteinander verknüft werden.

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

Hinweis: Folgende Ausrücke werden Synonym für `benutzende` im Bereich der Fremdschlüsselverknüpfung verwendet:
![grafik](https://github.com/user-attachments/assets/bfcb35b9-1845-4419-be05-9fcf9c4ba1af)

Hinweis: Folgende Ausrücke werden Synonym für `buchtitel` im Bereich der Fremdschlüsselverknüpfung verwendet:
![grafik](https://github.com/user-attachments/assets/5a69430a-df03-4fd5-a23a-256c9b7adea3)

## Installation 

1. **Voraussetzungen**:
   - MariaDB, mySQL oder eine ähnliche relationale Datenbank
