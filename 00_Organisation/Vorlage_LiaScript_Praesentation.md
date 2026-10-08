<!--
author:    Vorname Nachname; Vorname Nachname
email:     vorname.nachname@st.ovgu.de
version:   0.1.0
language:  de
narrator:  Deutsch Female
mode:      Presentation
classroom: enable

title:     «Titel der Präsentation»
comment:   «Ein Satz: Welcher Ausbildungsberuf, welcher Betrieb, welches Handlungsfeld?»
-->

<!--
================================================================================
ANLEITUNG FÜR DAS KI-MODELL (z. B. in HAWKI) – dieser Block bleibt im Ergebnis stehen
================================================================================
Du füllst diese Vorlage zu einer LiaScript-Präsentation aus. Regeln:
1. Struktur, Überschriften-Ebenen und Reihenfolge der Folien beibehalten. Folien dürfen
   ergänzt werden (je eine `##`-Überschrift), aber keine Pflichtfolie entfällt.
2. Alles in «Winkelklammern» ersetzen. Kommentare `<!-- KI: … -->` nach dem Ausfüllen löschen.
3. Jede Folie bekommt eine Sprechernotiz: Zeile `                --{{0}}--`, darunter 1–3 Sätze.
4. Text NIE mit 4 oder mehr Leerzeichen einrücken (sonst erscheint er als Codeblock).
   Quiz- und Umfrageoptionen beginnen am Zeilenanfang mit `- [( )]`, `- [(X)]`, `- [[ ]]`, `- [[X]]`.
5. `{{1}}`, `{{2}}` … steht in einer eigenen Zeile direkt vor dem Block, der nacheinander erscheinen soll.
   Soll mehr als ein Absatz zusammen erscheinen: in `<section>` … `</section>` einschließen.
6. Nichts erfinden: keine Ausbildungsordnungen, Lernfeldnummern, Vertrags- oder Abbruchzahlen,
   Betriebsdaten oder Literatur, die nicht im mitgelieferten Material stehen.
   Unsichere Angaben mit `<!-- PRÜFEN: … -->` markieren.
7. Keine personenbezogenen Daten oder Betriebsinterna aus der Exkursion übernehmen.
8. Sprache: Deutsch, Fachbegriffe korrekt, Sie-Form gegenüber dem Plenum.
================================================================================
-->

# «Titel der Präsentation»

**«Gruppe N»** · 14.12.2026 · Prozesse, Systeme und Organisation betrieblicher Facharbeit, OVGU

                --{{0}}--
«Begrüßung in einem Satz und worum es heute geht.»

## Der Betrieb

<!-- KI: Branche, Größe, Tätigkeitsfelder – anonymisiert, keine Interna. -->

                --{{0}}--
«Betrieb kurz vorstellen und erklären, warum er zum Ausbildungsberuf passt.»

| Merkmal | Angabe |
| --- | --- |
| Branche | «…» |
| Betriebsgröße | «z. B. 50–250 Beschäftigte» |
| Tätigkeitsfelder | «…» |
| Ausbildung im Betrieb | «Berufe, Zahl der Auszubildenden» |

## Der Ausbildungsberuf

                --{{0}}--
«Ausbildungsberuf mit den wichtigsten Strukturdaten vorstellen.»

{{1}}
| Merkmal | Angabe |
| --- | --- |
| Ausbildungsberuf | «Bezeichnung laut Ausbildungsordnung» <!-- PRÜFEN: BIBB --> |
| Dauer und Gliederung | «…» |
| Abschlussprüfung | «z. B. gestreckte Abschlussprüfung Teil 1/Teil 2» |
| Genealogie | «Vorgängerberufe, Neuordnung» |
| Vertrags- und Abbruchzahlen | «Zahl, Jahr, Quelle» |

## Analysierter Arbeitsprozess

<!-- KI: Einen typischen Arbeitsprozess aus der Erkundung beschreiben: Auftrag, Schritte, Werkzeuge, Anforderungen. -->

                --{{0}}--
«Den Arbeitsprozess an einem konkreten Auftrag erklären.»

> **Typischer Auftrag:** «Auftrag in 2–3 Sätzen»

{{1}}
``` ascii
 Auftrag ──► Planung ──► Durchführung ──► Kontrolle ──► Übergabe
  «…»         «…»          «…»              «…»          «…»
```

{{2}}
| Prozessschritt | Gegenstand | Werkzeuge & Methoden | Anforderungen |
| --- | --- | --- | --- |
| «…» | «…» | «…» | «…» |
| «…» | «…» | «…» | «…» |

## Abgeleitetes Handlungsfeld

                --{{0}}--
«Vom Arbeitsprozess zum beruflichen Handlungsfeld und zum Lernfeld.»

{{1}}
**Berufliches Handlungsfeld:** «Titel und kurze Beschreibung»

{{2}}
**Bezug zum Lernfeld:** «Nummer und Titel laut Rahmenlehrplan» <!-- PRÜFEN: Rahmenlehrplan -->

{{3}}
``` ascii
 Arbeitsprozess ──► Handlungsfeld ──► Lernfeld ──► Lernsituation
```

## Aktivierung: Quiz

                --{{0}}--
«Quiz ankündigen.»

**«Frage 1 – eine richtige Antwort»**

- [( )] «falsch»
- [(X)] «richtig»
- [( )] «falsch»
[[?]] «Hinweis, falls die Antwort falsch war»

**«Frage 2 – mehrere richtige Antworten»**

- [[X]] «richtig»
- [[ ]] «falsch»
- [[X]] «richtig»

## Offene Fragen

                --{{0}}--
«Offene Fragen für die Diskussion mit dem Plenum.»

{{1}}
1. «Frage»
2. «Frage»

**«Umfrage an das Plenum»**

- [(1)] «Option»
- [(2)] «Option»
- [(3)] «Option»

## Quellen

                --{{0}}--
Hier finden Sie alle Quellen und Bildnachweise.

- «Autor:in» («Jahr»). *«Titel»*. «Verlag/URL»  <!-- APA 7 -->
- «Ausbildungsordnung / Rahmenlehrplan mit Jahr»
- Bildnachweise: «Datei – Urheber – Lizenz»

## KI-Nutzung

                --{{0}}--
Für diese Präsentation haben wir KI-Werkzeuge so genutzt, wie in der Tabelle angegeben.

| Werkzeug (Modell) | Zweck | Prompt (Kurzform) | Was wir geprüft/geändert haben |
| --- | --- | --- | --- |
| «Werkzeug» | «z. B. Gliederung der Folien» | «…» | «z. B. Strukturdaten mit BIBB-Datenbank geprüft» |

<small>Zitierbeispiel (APA 7): «Anbieter» («Jahr»). *«Modellname»* [Large language model]. «URL», abgerufen am «Datum».</small>
