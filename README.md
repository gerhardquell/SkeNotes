# SkeNotes - Zettelkasten-Datenbank

## Einführung
Das Programm wurde gerade neu überarbeitet und wird demnächst hochgeladen. Haben Sie bitte etwas Geduld.

## Handbuch

### Einführung

SkeNotes ist eine Zettelkasten-Datenbank, die Ihnen ermöglicht, Notizen zu organisieren und mit bibliographischen Quellen zu verknüpfen. Das Programm basiert auf dem Zettelkasten-Prinzip, bei dem Wissensinhalte auf einzelnen "Zetteln" festgehalten werden, die miteinander verknüpft werden können.

### Systemvoraussetzungen

- Python 3.8 oder höher
- PySide6 (Qt-Bibliothek für Python)
- PostgreSQL 12 oder höher
- psycopg2 (PostgreSQL-Treiber für Python)

### Installation

1. Stellen Sie sicher, dass PostgreSQL installiert ist und läuft (Port: 5437).
2. Führen Sie das SQL-Skript `cr_skenotes.sql` aus, um die Datenbank zu erstellen:
   ```
   psql -p 5437 -f cr_skenotes.sql
   ```
3. Installieren Sie die benötigten Python-Abhängigkeiten:
   ```
   pip install PySide6 psycopg2-binary
   ```
4. Starten Sie das Programm:
   ```
   python skenotes.py
   ```

### Programmstruktur

SkeNotes besteht aus folgenden Komponenten:

- **Hauptfenster**: Ein Fenster mit zwei Tabellen und einem Eingabebereich dazwischen.
- **Zettel-Tabelle** (links): Zeigt die vorhandenen Notizen mit Code und Titel.
- **Biblio-Tabelle** (rechts): Zeigt die bibliographischen Quellen mit Ident und Titel.
- **Eingabebereich** (Mitte): Besteht aus zwei Tabs für Zettel und Quellen.

### Erste Schritte

1. Starten Sie das Programm.
2. Verbinden Sie sich mit der Datenbank über das Menü "Datenbank" > "Verbinden".
3. Nach erfolgreicher Verbindung werden die vorhandenen Notizen und Quellen in den Tabellen angezeigt.

### Arbeiten mit Notizen

#### Neue Notiz erstellen
- Klicken Sie mit der rechten Maustaste in die Zettel-Tabelle und wählen Sie "Neu".
- Geben Sie einen Titel und den Text der Notiz ein.
- Fügen Sie Tags hinzu, um die Notiz zu kategorisieren (durch Kommas getrennt).
- Klicken Sie auf "Speichern", um die Notiz zu speichern.

#### Notiz bearbeiten
- Wählen Sie eine Notiz in der Tabelle aus.
- Klicken Sie mit der rechten Maustaste und wählen Sie "Ändern".
- Bearbeiten Sie die Notiz und klicken Sie auf "Speichern".

#### Notiz löschen
- Wählen Sie eine Notiz in der Tabelle aus.
- Klicken Sie mit der rechten Maustaste und wählen Sie "Löschen".
- Bestätigen Sie den Löschvorgang.

#### Folgezettel erstellen
- Bearbeiten Sie eine Notiz oder erstellen Sie eine neue.
- Klicken Sie auf "Speichern + Folgezettel".
- Ein neuer Zettel wird erstellt, der automatisch mit dem vorherigen verknüpft ist.

### Arbeiten mit Quellen

#### Neue Quelle erstellen
- Klicken Sie mit der rechten Maustaste in die Biblio-Tabelle und wählen Sie "Neu".
- Füllen Sie die Felder aus (Kurztitel, Kurzautor, KurzIdent, etc.).
- Wählen Sie den Typ der Quelle (Buch, Artikel, Zeitschrift, etc.).
- Klicken Sie auf "Speichern", um die Quelle zu speichern.

#### Quelle bearbeiten
- Wählen Sie eine Quelle in der Tabelle aus.
- Klicken Sie mit der rechten Maustaste und wählen Sie "Ändern".
- Bearbeiten Sie die Quelle und klicken Sie auf "Speichern".

#### Quelle löschen
- Wählen Sie eine Quelle in der Tabelle aus.
- Klicken Sie mit der rechten Maustaste und wählen Sie "Löschen".
- Bestätigen Sie den Löschvorgang.
- Hinweis: Eine Quelle kann nur gelöscht werden, wenn sie nicht von Notizen referenziert wird.

### Rahmen

Die Anwendung lädt Rahmen-Informationen aus der Datei `nodes_rahmen.csv`. Diese Rahmen werden verwendet, um Notizen nach Themen zu organisieren. Der Rahmen wird anhand des Präfixes des Notizschlüssels (z.B. "A000") bestimmt.

### Tipps

- Verwenden Sie Tags, um Ihre Notizen zu kategorisieren und leichter wiederzufinden.
- Erstellen Sie Folgezettel, um zusammenhängende Gedanken zu verknüpfen.
- Verknüpfen Sie Notizen mit bibliographischen Quellen, um den Ursprung von Informationen zu dokumentieren.
- Die Tags "folgt:" und "siehe:" können verwendet werden, um Notizen miteinander zu verknüpfen.

### Fehlerbehebung

- **Verbindungsfehler**: Stellen Sie sicher, dass PostgreSQL läuft und die Datenbank `skenotes` existiert.
- **Zugangsdaten**: Standardmäßig wird der Benutzer "notes" mit dem Passwort "ske00zettel" verwendet.
- **Port**: Der Standardport ist 5437. Wenn Ihre PostgreSQL-Installation einen anderen Port verwendet, müssen Sie die Konfiguration anpassen.
