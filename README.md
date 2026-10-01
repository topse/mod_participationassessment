# Moodle Plugin zur Selbstbewertung der Mitarbeit
Grundsätzlich ist Benutzerfreundlichkeit das oberste Ziel. Für den laufenden Betrieb sollte möglichst keine Tastatur benötigt werden, für
Konfiguration darf eine Tastatur benötigt werden. Die UI sollte mobile und Desktop Geräte im Blick haben.
```
Trainer erstellt Aktivität
        │
        ▼
Notenskala konfigurieren
        │
        ▼
Trainer gibt Bewertungsvorgang frei
        │
        ├── Gruppe / Gruppierung
        ├── Datum
        └── Ablaufzeit
        │
        ▼
Schüler sehen Eingabemaske
        │
        ▼
Selbsteinschätzung + optionaler Kommentar
        │
        ▼
Trainer beurteilt
        │
        ├── ✓ Übernehmen
        └── eigene Bewertung + Kommentar
        │
        ▼
Übernahme in Moodle-Bewertung
```

## Funktionen aus Administratorsicht
Im Administrationsbereich des Plugins kann der Administrator verschiedene Notenskalen anbieten, diese hier sollen per Default angeboten werden:

### Berufliches Gymnasium Niedersachsen 11. Klasse
 | Ab Prozent | Notenstufe |
| --- | --- |
| 0 | 6 |
| 20 | 5- |
| 27 | 5 |
| 33 | 5+ |
| 40 | 4- |
| 45 | 4 |
| 50 | 4+ |
| 55 | 3- |
| 60 | 3 |
| 65 | 3+ |
| 70 | 2- |
| 75 | 2 |
| 80 | 2+ |
| 85 | 1- |
| 90 | 1 |
| 95 | 1+ |

### Berufliches Gymnasium Niedersachsen 12. und 13. Klasse

 | Ab Prozent | Notenpunkte |
| --- | --- |
| 0 | 0 |
| 20 | 1 |
| 27 | 2 |
| 33 | 3 |
| 40 | 4 |
| 45 | 5 |
| 50 | 6 |
| 55 | 7 |
| 60 | 8 |
| 65 | 9 |
| 70 | 10 |
| 75 | 11 |
| 80 | 12 |
| 85 | 13 |
| 90 | 14 |
| 95 | 15 |

### IHK Notenstufen Niedersachsen

 | Ab Prozent | Notenstufe |
| --- | --- |
| 0 | 6 |
| 30 | 5- |
| 32 | 5 |
| 48 | 5+ |
| 50 | 4- |
| 52 | 4 |
| 65 | 4+ |
| 67 | 3- |
| 69 | 3 |
| 79 | 3+ |
| 81 | 2- |
| 83 | 2 |
| 90 | 2+ |
| 92 | 1- |
| 94 | 1 |
| 100 | 1+ |



## Funktionen aus Trainersicht

### Normal-Ansicht
Hier wird ein QR-Code angezeigt. Dieser wird benötigt, falls die Schüler gerade nicht am Rechner arbeiten, dass Sie den
von der elektronischen Tafel oder Beamer direkt einscannen und sofort auf die Aktivität kommen, damit sie schnell und unkompliziert mit einem mobilen Endgerät eine Selbsteinschätzung
vornehmen können.

Außerdem ist hier für den Trainer ein Button "Bewertungsrunde starten" mit Datum daneben (das per default heute ist) und einer Ablaufzeit, default 5min. Sobald der aktiviert wird, können
Schüler überhaupt erst eine Selbstbewertung vornehmen (das passiert nämlich nur nach Anfrage durch den Trainer - nicht wenn der Schüler es will). Bitte prüfen unter welchen Umständen hier
eingestellt werden muss, für welche Gruppe oder Gruppierung die Bewertungsrunde gilt unter Annahme, dass eine Gruppe oder Gruppierung dafür verwendet wird, die Schüler von Kursen und Klassen
zusammenzufassen, Stichwort "Getrennte Gruppen" oder nicht. Das ist spannend, wenn man einen Kurs mit mehreren Klassen gleichzeitig macht, deren Schüler in Moodle durch Gruppen oder Gruppierungen getrennt werden.



### Einstellungs-Ansicht
Der Trainer legt eine Aktivität vom Type Selbstbewertung an, oder auch mehrere das ist egal. Er stellt ein
welche Notenskala (siehe Admin Bereich) verwendet werden soll, oder ob eine eigene definiert werden soll,
oder ob die aktuelle Skala aus dem Kurs übernommen werden soll. In jedem Fall gibt es einen weiteren Button "Notenskala in Bewertungssystem dieses Kurses übernehmen".
Dieser übernimmt die hier aktuell eingestellte Notenskala in die Bewertungseinstellung des Kurses.

Wenn die hier eingestellte Notenskala nicht der Notenskala im Kurs entspricht, soll hier immer eine Warnung stehen mit einer Ansicht, die die aktuelle
Kurseinstellung zeigt, die dann per Buttonclick übernommen werden kann.

### Bewertungsrunden
Hier kann man nach Datum und Uhrzeit der Bewertungsrunde auswählen und dann noch nach üblichen Filtereinstellungen
(Gruppen, suchen, Sortieren nach Vor- und Nachname usw.) Selbstbewertungen anzeigen lassen.
Hier muss die Lehrkraft jede Selbstbewertung "beurteilen", also entweder zustimmen (einfach Checkbox "OK"), oder eine eigene Bewertung abgeben, und außerdem ein Kommentar.
In den Einstellungen kann ein Standardkommentar für "OK" voreingestellt werden, der wenn vorhanden automatisch immer dann in die Maske eingetragen wird (aber geändert werden kann),
wenn OK aktiviert wird.

Dies wird alles innerhalb des Plugins gespeichert. Unten auf der Maske gibt es einen Button "In die Kursbewertung übernehmen". Der sorgt dafür, dass der
aktuelle Bewertungsvorgang (also alle Daten der gewählten Bewertungsrunde) in das Bewertungssystem des Kurses übertragen bzw. aktualisiert werden. Falls nicht vorhanden wird eine
Bewertungskategorie "Selbstbewertung" automatisch angelegt (Durschnittsbewertung) und mit einem manuellen Bewertungsaspekt, dass als Namen das Datum trägt und wenn vorhanden den Namen
der Gruppe oder Gruppierung. Hierbei zählt wenn vorhanden natürlich die Neubewertung der Lehrkraft.

Übernommen wird immer ein Prozentwert, das heißt der Bewertungsaspekt reicht immer von 0...100, und wird anhand der im Bewertungssystems eingestellten Notenskala in Note umgerechnet.

Die Anzeige sowohl des eingerichteten Bewertungsaspekts als auch der Kategorie soll Note (Prozent) anzeigen.

Nur Selbstbewertungen, die durch die Lehrkraft Freigegeben wurden, werden in das Bewertungssystem des Kurses übertragen.

## Funktionen aus Teilnehmersicht

Der Teilnehmer sieht falls eine Freigabe erteilt wurde, eine UI zur Eingabe einer eigenen Note (am besten nur Buttons, damit Mobile eingabe möglichst einfach ist),
mit der Möglichkeit einen Kommentar dazuzuschreiben. Wenn keine Freigabe aktiv ist, sieht er seine Historie an Selbstbewertungen inkl. seiner
Kommentare, die mögliche Neubewertung und die Kommentare der Lehrkraft. Auch nach Abgabe einer Selbstbewertung kommt er auf diese Übersichtsdarstellung. Die Zeilen, die die Lehrkraft bestätigt hat,
sind mit Haken markiert und die Eingaben der Lehrkraft werden gezeigt, bei den anderen gibt es eine Uhr und die Eingaben der Lehrkraft sind halt offen.
