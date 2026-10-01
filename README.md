 # Moodle Plugin zur Selbstbewertung der Mitarbeit

 Grundsätzlich ist Benutzerfreundlichkeit das oberste Ziel. Für den laufenden Betrieb sollte möglichst keine Tastatur benötigt werden, für die Konfiguration darf eine Tastatur benötigt werden. Die UI sollte sowohl mobile Geräte als auch Desktop-Geräte berücksichtigen.

 Der typische Ablauf ist:

```
Trainer erstellt Aktivität
        │
        ▼
Notenskala konfigurieren
        │
        ▼
Trainer startet Bewertungsrunde
        │
        ├── Gruppe / Gruppierung
        ├── Startzeit
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
        ├── ✓ Bestätigen
        │     → Selbstbewertung wird übernommen
        │
        └── Eigene Bewertung + Kommentar
              → Lehrerbewertung wird übernommen
        │
        ▼
Endzustand der Bewertungsrunde
        │
        ▼
Übernahme in Moodle-Bewertung
```

 ## Funktionen aus Administratorsicht

 Im Administrationsbereich des Plugins kann der Administrator verschiedene Notenskalen als **Vorlagen** verwalten.

 Die folgenden Notenskalen werden standardmäßig mit dem Plugin ausgeliefert:

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

### Verwaltung der Notenskalen

 Die ausgelieferten Standardskalen dienen ausschließlich als **Vorlagen** und sind nicht direkt veränderbar.

 Der Administrator kann:

 - eigene Notenskalen erstellen,
- eigene Notenskalen bearbeiten,
- eigene Notenskalen löschen.

 Eine Aktivität arbeitet **niemals direkt mit einer administrativen Vorlage**.

 Wenn ein Trainer in einer Aktivität eine Vorlage auswählt, wird daraus immer eine **eigene interne Kopie der Notenskala für diese Aktivität** erzeugt. Die Aktivität verwendet anschließend ausschließlich diese Kopie.

 Wird eine solche kopierte Notenskala verändert, betrifft die Änderung ausschließlich diese Aktivität. Die ursprüngliche Vorlage und andere Aktivitäten bleiben unverändert.

 Damit sind die Standardskalen unveränderliche Vorlagen und die tatsächlich verwendeten Notenskalen immer **aktivitätseigene Kopien**.

---

 # Funktionen aus Trainersicht

 ## Übersicht

 Die Startseite der Aktivität dient als Übersicht und ermöglicht das schnelle Starten einer Bewertungsrunde.

 ### QR-Code

 Auf der Übersicht wird ein QR-Code angezeigt.

 Der QR-Code führt dauerhaft direkt zur Aktivität. Er muss nicht für jede Bewertungsrunde neu erzeugt werden.

 Die Teilnehmer können den QR-Code beispielsweise von einer elektronischen Tafel oder einem Beamer mit ihrem mobilen Endgerät scannen.

 Ist keine Bewertungsrunde aktiv, zeigt die Aktivität dem Teilnehmer entsprechend an, dass momentan keine Selbstbewertung freigegeben ist.

 Ist eine Bewertungsrunde aktiv, gelangt der Teilnehmer direkt zur Eingabemaske.

 ### Bewertungsrunde starten

 Der Trainer kann eine neue Bewertungsrunde starten.

 Die Runde enthält mindestens:

 - Startzeit
- Ablaufzeit
- Gruppe oder Gruppierung bzw. den gesamten Kurs

 Standardmäßig:

 - Startzeit: jetzt
- Dauer: 5 Minuten

 Beispiel:

 > **Bewertungsrunde starten**\
>  Gruppe: BGYM11A\
>  Start: 01.10.2026, 08:15 Uhr\
>  Dauer: 5 Minuten
>
>  **\[ Bewertungsrunde starten \]**

 Nach dem Start wird deutlich angezeigt:

 > 🟢 **Bewertungsrunde aktiv – noch 03:42 Minuten**

 Eine Bewertungsrunde ist ein eigenständiger Vorgang. Jede gestartete Runde bleibt anschließend in der Historie erhalten.

 ### Gruppen und Gruppierungen

 Die Bewertungsrunde kann gelten für:

 - den gesamten Kurs,
- eine Moodle-Gruppe,
- eine Moodle-Gruppierung.

 Dabei soll möglichst die vorhandene Moodle-Gruppenlogik verwendet werden.

 Insbesondere bei Kursen mit mehreren Klassen soll es möglich sein, beispielsweise eine Bewertungsrunde nur für die Gruppe bzw. Gruppierung einer bestimmten Klasse freizugeben.

 Die Berechtigung muss serverseitig geprüft werden. Ein Teilnehmer darf eine Bewertungsrunde nicht allein durch Kenntnis der URL aufrufen können.

 Die Sichtbarkeit einer Bewertungsrunde ergibt sich insbesondere aus:

 - Kursmitgliedschaft,
- Gruppenzugehörigkeit,
- Gruppierung,
- aktivem Zeitraum,
- Moodle-Capabilities und weiteren erforderlichen Berechtigungen.

 Nach Ablauf der Runde können keine neuen Selbstbewertungen mehr abgegeben werden. Bereits abgegebene Selbstbewertungen bleiben erhalten und können vom Trainer weiterhin beurteilt werden.

---

 # Einstellungs-Ansicht

 Der Trainer legt eine Aktivität vom Typ **Selbstbewertung** an. Es können mehrere solcher Aktivitäten in einem Kurs angelegt werden.

 Für jede Aktivität wird eine **eigene interne Notenskala** verwendet.

 ## Notenskala auswählen

 Beim Einrichten der Aktivität kann der Trainer:

 - eine vom Administrator bereitgestellte Notenskala als **Vorlage übernehmen**,
- eine eigene Notenskala definieren,
- eine vorhandene Notenskala aus dem Kurs als Grundlage übernehmen.

 In allen Fällen gilt:

 > **Die Aktivität arbeitet anschließend immer mit einer eigenen internen Kopie der Notenskala.**

 Es gibt keine direkte Referenz der Aktivität auf eine Admin-Vorlage oder auf die ursprüngliche Kursnotenskala.

 Beispiel:

 > **Notenskala**
>
>  \[ BGYM Niedersachsen – Klasse 11 ▼ \]
>
>  **\[ Vorlage übernehmen \]**

 Nach dem Übernehmen wird eine Kopie erzeugt:

 > **Eigene Notenskala**\
>  BGYM Niedersachsen – Klasse 11 (Kopie)
>
>  Diese Notenskala gehört zu dieser Aktivität und kann unabhängig von der Vorlage bearbeitet werden.

 Wird die ursprüngliche Admin-Vorlage später verändert oder gelöscht, bleibt die bereits in der Aktivität gespeicherte Kopie unverändert.

 Ebenso bleibt die Aktivität unverändert, wenn sich später die Notenskala des Kurses ändert.

 ### Kursnotenskala übernehmen

 Wenn die Notenskala des Kurses als Grundlage verwendet werden soll, wird ebenfalls zunächst eine **eigene Kopie innerhalb der Aktivität** erzeugt.

 Die Aktivität arbeitet auch in diesem Fall nicht direkt mit der Kursnotenskala.

 Die Funktion kann beispielsweise heißen:

 > **\[ Kursnotenskala als Vorlage übernehmen \]**

 Danach kann die kopierte Notenskala innerhalb der Aktivität unabhängig bearbeitet werden.

---

 # Notenskala in das Kurs-Bewertungssystem übernehmen

 Zusätzlich gibt es die Funktion:

 > **\[ Notenskala für diesen Kurs übernehmen \]**

 Damit kann die aktuell in der Aktivität vorhandene **eigene interne Notenskala** in das Bewertungssystem des Kurses übernommen bzw. dort eingerichtet werden.

 Wichtig ist:

 > Für diese Funktion wird immer die **aktuelle Kopie der Notenskala aus der Aktivität** verwendet. Die ursprüngliche Admin-Vorlage wird niemals direkt verwendet.

 Wenn die für die Aktivität konfigurierte Notenskala nicht der aktuell für den Kurs relevanten Notenskala entspricht, wird eine Warnung angezeigt.

 Beispiel:

 > ⚠️ **Die Notenskala dieser Aktivität unterscheidet sich von der aktuellen Notenskala des Kurses.**
>
>  **Notenskala dieser Aktivität**
>
>  | Ab Prozent | Note |
> | --- | --- |
> | 0 | 6 |
> | 20 | 5- |
> | ... | ... |
>
> **Aktuelle Kursnotenskala**
>
>  | Ab Prozent | Note |
> | --- | --- |
> | 0 | 6 |
> | 30 | 5 |
> | ... | ... |
>
> **\[ Notenskala für diesen Kurs übernehmen \]**

 Die konkrete technische Umsetzung soll die vorhandenen Moodle-Mechanismen für Bewertungsskalen und das Gradebook verwenden.

---

 # Bewertungsrunden

 In diesem Bereich werden alle bisher gestarteten Bewertungsrunden angezeigt.

 Eine Bewertungsrunde enthält mindestens:

 - Datum
- Uhrzeit
- Gruppe bzw. Gruppierung
- Startzeit
- Ablaufzeit
- Anzahl der Teilnehmer
- Anzahl abgegebener Selbstbewertungen
- Anzahl noch nicht beurteilter Selbstbewertungen

 Beispiel:

 | Datum | Gruppe | Dauer | Abgegeben | Beurteilt |
| --- | --- | --- | --- | --- |
| 01.10.2026 08:15 | BGYM11A | 5 min | 22 / 24 | 18 / 22 |
| 24.09.2026 10:05 | BGYM11A | 5 min | 23 / 24 | 23 / 23 |

Nach Auswahl einer Bewertungsrunde können die Teilnehmer gefiltert und sortiert werden.

 Mögliche Filter:

 - Gruppe / Gruppierung
- Vorname
- Nachname
- Status
- Selbstbewertung vorhanden / nicht vorhanden
- bestätigt / bewertet / offen

---

 # Beurteilung durch die Lehrkraft

 Die Lehrkraft sieht pro Teilnehmer mindestens:

 | Teilnehmer | Selbstbewertung | Lehrerbewertung | Status |
| --- | --- | --- | --- |
| Anna Müller | 2 | 2 | ✓ Bestätigt |
| Max Mustermann | 2- | 2 | ✓ Bewertet |
| Lisa Schmidt | 1- | – | ⏳ Offen |

Die Lehrkraft kann eine abgegebene Selbstbewertung auf zwei Arten abschließen.

 ## 1\. Selbstbewertung bestätigen

 Die Lehrkraft kann **OK** auswählen.

 Damit übernimmt sie die Selbstbewertung des Schülers unverändert.

 Beispiel:

 > Selbstbewertung: **2**
>
>  ☑ **OK**

 Der Vorgang erhält anschließend den Status:

 > ✓ **Bestätigt**

 Die Lehrerbewertung entspricht der Selbstbewertung.

 ## 2\. Eigene Bewertung vergeben

 Alternativ kann die Lehrkraft eine eigene Bewertung abgeben.

 Beispiel:

 > Selbstbewertung: **2-**
>
>  Lehrerbewertung: **2**
>
>  Kommentar:\
>  „Gute und regelmäßige Beteiligung.“

 Der Vorgang erhält anschließend den Status:

 > ✓ **Bewertet**

 ### Bestätigt und Bewertet sind alternative Endzustände

 **Bestätigt** und **Bewertet** sind zwei alternative Endzustände einer Selbstbewertung.

```
                    ┌── ✓ Bestätigt
                    │   Lehrer übernimmt Selbstbewertung
                    │
Abgegeben ──────────┤
                    │
                    └── ✓ Bewertet
                        Lehrer vergibt eigene Bewertung
```

 Beide Zustände gelten als **abschließend beurteilt**.

 Eine später vorgenommene Änderung der Lehrerbewertung ist keine neue Statusstufe, sondern eine **Änderung bzw. Neubewertung eines bereits abgeschlossenen Vorgangs**.

---

 # Kommentare

 Die Lehrkraft kann bei der Beurteilung einen Kommentar hinterlegen.

 In den Einstellungen kann ein Standardkommentar für die Bestätigung definiert werden.

 Beispiel:

 > **Standardkommentar bei „OK“:**\
>  `Danke für deine Einschätzung.`

 Wird bei einer Beurteilung **OK** ausgewählt, wird dieser Text automatisch als Kommentar vorgeschlagen.

 Der Text kann vor dem Speichern verändert oder gelöscht werden.

---

 # Speicherung

 Die Selbstbewertung, die Lehrerbewertung und die Kommentare werden innerhalb des Plugins gespeichert.

 Dabei werden mindestens getrennt gespeichert:

 - Selbstbewertung des Teilnehmers
- Kommentar des Teilnehmers
- Lehrerbewertung
- Kommentar der Lehrkraft
- Status
- Bewertungsrunde
- Zeitpunkt der Abgabe
- Zeitpunkt der Lehrerbewertung

 Die Selbstbewertung wird nicht durch eine spätere Lehrerbewertung überschrieben.

 Damit kann beispielsweise dauerhaft dargestellt werden:

 |  | Bewertung |
| --- | --- |
| Schüler | 2- |
| Lehrer | 2 |

---

 # Übernahme in die Kursbewertung

 Am Ende einer Bewertungsrunde kann die Lehrkraft die Daten in das Moodle-Bewertungssystem übertragen:

 > **\[ In Kursbewertung übernehmen \]**

 Dabei wird immer der aktuelle Stand der ausgewählten Bewertungsrunde übertragen bzw. aktualisiert.

 ## Idempotente Übertragung

 Die Übertragung muss **idempotent** sein.

 Das bedeutet:

 > Wird dieselbe Bewertungsrunde mehrfach in die Kursbewertung übernommen, entstehen **keine doppelten Bewertungsaspekte und keine doppelten Bewertungen**.

 Für jede Bewertungsrunde gibt es im Gradebook genau einen zugehörigen Bewertungsaspekt.

 Bei einer erneuten Übertragung wird dieser bestehende Bewertungsaspekt **aktualisiert**.

 Beispiel:

```
1. Übertragung
01.10.2026 – BGYM11A
        ↓
Gradebook-Bewertungsaspekt wird angelegt

2. Übertragung
01.10.2026 – BGYM11A
        ↓
derselbe Bewertungsaspekt wird aktualisiert

3. Übertragung
01.10.2026 – BGYM11A
        ↓
wieder derselbe Bewertungsaspekt wird aktualisiert
```

 Es darf dadurch nicht entstehen:

```
01.10.2026 – BGYM11A
01.10.2026 – BGYM11A
01.10.2026 – BGYM11A
```

 Die Zuordnung zwischen Bewertungsrunde und Gradebook-Bewertungsaspekt muss daher technisch eindeutig sein.

 Nur Selbstbewertungen, die zu einer vom Trainer gestarteten Bewertungsrunde gehören und durch die Lehrkraft abschließend beurteilt wurden, werden als fertige Bewertung in das Bewertungssystem übertragen.

 Noch offene Selbstbewertungen werden nicht als fertige Bewertung übertragen.

---

 # Bewertungswert

 Intern wird immer ein numerischer Wert zwischen **0 und 100 Prozent** verwendet.

 Beispiel:

```
Selbstbewertung
       │
       ▼
      85 %
       │
       ▼
Moodle-Bewertungssystem
       │
       ▼
Notenskala
       │
       ▼
      1-
```

 Die Notenskala bestimmt die Darstellung des Prozentwertes als Note bzw. Notenpunkte.

 Dadurch bleibt die eigentliche Bewertung unabhängig von einer konkreten Notenskala.

---

 # Gradebook-Kategorie

 Falls noch nicht vorhanden, wird automatisch eine Bewertungskategorie **„Selbstbewertung“** angelegt.

 Die Kategorie verwendet eine Durchschnittsbewertung.

 Für jede Bewertungsrunde wird darunter ein eigener manueller Bewertungsaspekt angelegt.

 Der Name des Bewertungsaspekts enthält mindestens das Datum der Bewertungsrunde und, sofern vorhanden, die Gruppe oder Gruppierung.

 Beispiel:

 > **Selbstbewertung**
>
>  └── 01.10.2026 – BGYM11A

 Der Bewertungsaspekt hat intern einen Wertebereich von **0 bis 100**.

 Die Darstellung im Moodle-Bewertungssystem soll sowohl den Prozentwert als auch die entsprechende Note anzeigen.

 Bei wiederholter Übertragung derselben Bewertungsrunde wird der bereits vorhandene Bewertungsaspekt aktualisiert und nicht erneut angelegt.

---

 # Teilnehmeransicht

 ## Aktive Bewertungsrunde

 Wenn für den Teilnehmer eine Bewertungsrunde aktiv ist, sieht er unmittelbar die Eingabemaske.

 Die Eingabe soll möglichst ohne Tastatur funktionieren.

 Beispiel:

 > ### Wie schätzt du deine Mitarbeit ein?
>
>  **6**\
>  **5-**\
>  **5**\
>  **5+**\
>  **4-**\
>  **4**\
>  **4+**\
>  **3-**\
>  **3**\
>  **3+**\
>  **2-**\
>  **2**\
>  **2+**\
>  **1-**\
>  **1**\
>  **1+**
>
>  Optional:
>
>  **Kommentar**
>
>  `[________________________________]`
>
>  **\[ Selbstbewertung abgeben \]**

 Die Darstellung der Bewertungsbuttons richtet sich nach der für die Aktivität konfigurierten **internen Notenskala**.

 Bei einer Notenpunktskala werden entsprechend die Werte 0–15 angezeigt.

 Die Buttons sollen für Touch-Geräte ausreichend groß sein.

---

 # Eine Selbstbewertung pro Bewertungsrunde

 Pro Teilnehmer und Bewertungsrunde kann genau **eine** Selbstbewertung abgegeben werden.

 Nach der Abgabe kann keine zweite Selbstbewertung für dieselbe Runde erstellt werden.

 Der Teilnehmer wird anschließend direkt zu seiner Historie weitergeleitet.

---

 # Teilnehmerhistorie

 Wenn keine Bewertungsrunde aktiv ist, sieht der Teilnehmer seine bisherigen Selbstbewertungen.

 Auch nach der Abgabe einer Selbstbewertung wird diese Historie angezeigt.

 Beispiel:

 | Datum | Eigene Bewertung | Lehrer | Status |
| --- | --- | --- | --- |
| 01.10.2026 | 2 | 2 | ✓ |
| 24.09.2026 | 2+ | 2 | ✓ |
| 17.09.2026 | 3 | – | ⏳ |

Auf mobilen Geräten kann dieselbe Information als Karten dargestellt werden.

 ### Status

 **✓ Bestätigt**

 Die Lehrkraft hat die Selbstbewertung übernommen.

 **✓ Bewertet**

 Die Lehrkraft hat eine eigene Bewertung vergeben.

 **⏳ Offen**

 Die Selbstbewertung wurde abgegeben, aber noch nicht durch die Lehrkraft beurteilt.

 Bei offenen Bewertungen werden die Eingaben der Lehrkraft noch nicht angezeigt.

 Bei abgeschlossenen Bewertungen werden angezeigt:

 - eigene Bewertung des Schülers,
- Bewertung der Lehrkraft,
- Kommentar des Schülers,
- Kommentar der Lehrkraft,
- Status.

---

 # Bewertungsrunden und Statusmodell

 Eine Bewertungsrunde selbst kann unterschiedliche Zustände haben:

```
Geplant / aktiv
      │
      ▼
  Ablauf erreicht
      │
      ▼
   Abgeschlossen
```

 Die einzelnen Teilnehmerbewertungen innerhalb einer Runde haben dagegen einen eigenen Status:

```
Noch nicht abgegeben
        │
        ▼
     Abgegeben
        │
        ├───────────────┐
        ▼               ▼
   ✓ Bestätigt      ✓ Bewertet
      END               END
```

 **Bestätigt** und **Bewertet** sind dabei gleichwertige Endzustände.

 Die Bewertungsrunde kann abgelaufen sein, obwohl einzelne Teilnehmerbewertungen noch offen sind. Die Lehrkraft kann diese anschließend weiterhin beurteilen.

 Eine nachträgliche Änderung einer bereits abgeschlossenen Lehrerbewertung wird als Änderung/Neubewertung des bestehenden Vorgangs behandelt und erzeugt keinen neuen Status.

---

 # Anforderungen an die Notenskalenhistorie

 Die interne Notenskala einer Aktivität muss die **konkreten Schwellenwerte und Bezeichnungen zum Zeitpunkt der Übernahme** enthalten.

 Eine Aktivität darf nicht von späteren Änderungen an einer Admin-Vorlage oder der ursprünglichen Kursnotenskala abhängig sein.

 Beispiel:

```
Admin-Vorlage
      │
      │ Vorlage übernehmen
      ▼
┌─────────────────────────────┐
│ Aktivität                   │
│                             │
│ Eigene Notenskala-Kopie     │
│                             │
│ 0  → 6                      │
│ 20 → 5-                     │
│ 27 → 5                      │
│ ...                         │
└─────────────────────────────┘
```

 Die Aktivität verwendet ausschließlich diese eigene Kopie.

 Wird die Vorlage später geändert, bleibt die Aktivität unverändert.

 Wird die Notenskala der Aktivität geändert, wird ausschließlich die interne Kopie dieser Aktivität geändert.

 Dadurch bleiben historische Bewertungsrunden und ihre Interpretation dauerhaft nachvollziehbar.
