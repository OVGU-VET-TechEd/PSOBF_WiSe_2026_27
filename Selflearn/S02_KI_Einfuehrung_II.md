<!--
author:    Hannes Tegelbeckers
email:     hannes.tegelbeckers@ovgu.de
version:   0.1.0
language:  de
narrator:  Deutsch Female
mode:      Textbook

title:     S02 – KI-Einführung II: Werkzeuge, Grenzen, Ethik (Selbstlerneinheit)
comment:   PSOBF – Prozesse, Systeme und Organisation betrieblicher Facharbeit – Selbstlerneinheit zu Sitzung 2 (Selbstlerntermin 19.10.2026). KI-Werkzeuge nach Zweck auswählen, Grenzen erkennen, Aussagen über Ausbildungsberufe mit Primärquellen prüfen, KI-Nutzung datenschutzgerecht und transparent dokumentieren; Rechercheauftrag eigenes Berufsfeld.
tags:      PSOBF, Künstliche Intelligenz, Prompting, Halluzination, Faktencheck, Datenschutz, KI-Kennzeichnung, Selbstlernen
-->

# S02 – KI-Einführung II: Werkzeuge, Grenzen, Ethik

<!-- didaktik="Selbstlerneinheit S02 · Selbstlerntermin 19.10.2026 (Dozent nicht vor Ort) · ca. 75 min + Rechercheauftrag · baut auf KI-Einführung I (12.10.2026) auf" -->

> [!IMPORTANT] 🧭 Leitfrage
> Welches KI-Werkzeug nutze ich wofür – und wie stelle ich sicher, dass das, was die KI über meinen Ausbildungsberuf sagt, auch stimmt?

> [!WARNING] 📅 Selbstlerntermin am 19.10.2026
> An diesem Termin gibt es keine Präsenzveranstaltung. Bearbeiten Sie diese Einheit und danach den **Rechercheauftrag** (Abschnitt 4). Grundlage ist die Sitzung [KI-Einführung I](https://liascript.github.io/course/?https://raw.githubusercontent.com/OVGU-VET-TechEd/PSOBF_WiSe_2026_27/main/Sitzungen/01_KI_Einfuehrung_I_LLM_Prompting.md) – nehmen Sie Ihren Prompt vom 12.10. als Startpunkt. Offene Fragen besprechen wir am 26.10.

> [!TIP] ✍️ Übung in Moodle
> Bearbeiten Sie die Übung im Moodle-Kurs bis **25.10.2026, 23:59 Uhr**: [Übung in Moodle öffnen](https://elearning.ovgu.de/course/view.php?id=22043)

**Ablauf (ca. 75 min + Rechercheauftrag)**

<!-- data-type="none" -->
| Schritt | Inhalt | Zeit |
| --- | --- | --- |
| 0 | Wo stehen Sie? | 3 min |
| 1 | Werkzeuge nach Zweck auswählen | 12 min |
| 2 | Grenzen erkennen: eine KI-Antwort prüfen | 25 min |
| 3 | Ethik und Recht | 15 min |
| 4 | Rechercheauftrag eigenes Berufsfeld | 15 min Planung + Bearbeitung |
| 5 | Abschluss | 5 min |

**Lernziele – nach dieser Einheit können Sie …**

1. für eine Aufgabe ein passendes KI-Werkzeug **auswählen** und die Wahl **begründen**,
2. typische Fehler von Sprachmodellen (Halluzination, erfundene Quellen, veraltetes Wissen, Bias) in einer Antwort **erkennen**,
3. Aussagen über einen Ausbildungsberuf mit **Primärquellen prüfen** (Ausbildungsordnung, Rahmenlehrplan, BIBB),
4. entscheiden, welche Daten Sie einem KI-Werkzeug **nicht** geben dürfen,
5. Ihre KI-Nutzung **transparent kennzeichnen** (Werkzeug, Zweck, Prompt; APA 7).

## 0 · Wo stehen Sie?

**Wie sicher fühlen Sie sich?** (1 = gar nicht, 4 = sehr sicher)

Ich erkenne, ob eine KI-Antwort über einen Ausbildungsberuf stimmt.

- [(1)] 1
- [(2)] 2
- [(3)] 3
- [(4)] 4

Ich weiß, welche Daten ich nicht in ein KI-Werkzeug eingeben darf.

- [(1)] 1
- [(2)] 2
- [(3)] 3
- [(4)] 4

> [!TIP] 🔁 Kurz erinnert (KI-Einführung I)
> Ein Sprachmodell sagt das **nächste Token** nach **Wahrscheinlichkeit** voraus. Sein Wissen stammt aus **Trainingsdaten** mit Stichtag, und es sieht nur, was im **Kontextfenster** steht. Ein guter Prompt hat **Rolle · Aufgabe · Kontext · Format · Beispiele** und wird mit **CLEAR** nachgeschärft.

## 1 · Werkzeuge nach Zweck auswählen

<!-- didaktik="ca. 12 min" -->

Es gibt nicht „die KI“. Werkzeuge unterscheiden sich darin, **ob sie im Netz suchen**, **ob sie Quellen anzeigen** und **wofür sie gebaut sind**.

| Zweck | Werkzeugtyp | Beispiele | Worauf Sie achten |
| --- | --- | --- | --- |
| Diskutieren, strukturieren, Texte überarbeiten | Chat-Assistent | HAWKI (OVGU-Zugang), ChatGPT, Claude | Antwort ohne Quellen – Fakten immer prüfen |
| Aktuelle Informationen recherchieren | Such-Assistent mit Quellenangaben | Perplexity | Quellen anklicken: Steht das wirklich dort? |
| Wissenschaftliche Literatur finden | Literatur-Assistent | Consensus | Titel im Bibliothekskatalog bzw. per DOI prüfen |
| Verbindliche Fakten zum Ausbildungsberuf | **keine KI** – Primärquelle | Ausbildungsordnung, Rahmenlehrplan, BIBB, BERUFENET | Diese Quellen sind der Maßstab |

<small>Werkzeugauswahl nach der Kurswebseite PSOBF. HAWKI ist über Ihren OVGU-Account nutzbar und wird von der Hochschule bereitgestellt.</small>

**Welches Werkzeug passt am besten?**

[[Chat-Assistent] [Such-Assistent] [Literatur-Assistent] [Primärquelle]]
[       (X)               ( )                ( )                ( )      ] Sie wollen Ihre Beobachtungsnotizen aus dem Betrieb (anonymisiert) in eine Tabelle bringen.
[       ( )               ( )                ( )                (X)      ] Sie brauchen die verbindliche Ausbildungsdauer und die Prüfungsstruktur Ihres Berufs.
[       ( )               ( )                (X)                ( )      ] Sie suchen Studien zur Arbeitsprozessanalyse in der Berufsbildung.
[       ( )               (X)                ( )                ( )      ] Sie wollen wissen, welche Neuordnungen in Ihrem Berufsfeld gerade diskutiert werden.
***
Chat-Assistenten sind stark beim Strukturieren von Material, das **Sie** mitgeben. Such-Assistenten finden Aktuelles und zeigen Quellen – die Sie trotzdem öffnen müssen. Für verbindliche Angaben (Dauer, Prüfung, Lernfelder) ist die **Primärquelle** der Maßstab, nicht die KI.
***

## 2 · Grenzen erkennen: eine KI-Antwort prüfen

<!-- didaktik="ca. 25 min · Kernübung der Einheit" -->

| Grenze | Was passiert | Woher es kommt (vgl. KI-Einführung I) |
| --- | --- | --- |
| **Halluzination** | flüssige, plausible, aber falsche Aussagen | Ziel ist plausibler, nicht wahrer Text |
| **Erfundene Quellen** | echt aussehende Literaturangaben, die es nicht gibt | dieselbe Ursache – Quellenangaben sind auch nur Text |
| **Veraltetes Wissen** | Neuordnungen und aktuelle Zahlen fehlen | Trainingsdaten enden an einem Stichtag |
| **Bias** | stereotype Bilder von Berufen und Beschäftigten | Verzerrungen in den Trainingsdaten |
| **Fehlender Betriebskontext** | allgemeine statt betriebsspezifische Prozesse | das Modell kennt Ihren Betrieb nicht |

<small>Erfundene Literaturangaben sind gut belegt: In einer Untersuchung waren 55 % der von GPT-3.5 und 18 % der von GPT-4 erzeugten Literaturangaben frei erfunden (Walters & Wilder, 2023).</small>

### Übung 2a: Fehler finden

Eine Studentin fragt ein Sprachmodell nach ihrem Ausbildungsberuf. So lautet die Antwort:

> *„Die Ausbildung zum Kfz-Mechatroniker / zur Kfz-Mechatronikerin dauert **drei Jahre**. Die Inhalte für den Berufsschulunterricht sind in **Lernfeldern in der Ausbildungsordnung** festgelegt, die das BIBB erlässt. Typische Arbeitsprozesse sind Diagnose, Wartung und Instandsetzung von Fahrzeugsystemen. Eine aktuelle Studie (Müller & Schmidt, 2024, *Arbeitsprozesse im Kfz-Handwerk*, BIBB-Report 12, S. 34) zeigt, dass 80 % der Arbeitszeit auf Diagnose entfallen. Der Beruf wird überwiegend von Männern ausgeübt, weil er körperliche Kraft erfordert.“*

Welche Aussagen müssen Sie beanstanden oder prüfen?

- [[X]] die Ausbildungsdauer
- [[X]] wo die Lernfelder festgelegt sind
- [[ ]] „Diagnose, Wartung und Instandsetzung“ als typische Arbeitsprozesse
- [[X]] die Studie mit der 80-%-Angabe
- [[X]] die Begründung für den geringen Frauenanteil
***
- **Dauer:** Die Ausbildung dauert **dreieinhalb Jahre** – prüfbar in der Ausbildungsordnung bzw. beim BIBB.
- **Lernfelder:** Sie stehen im **Rahmenlehrplan der KMK** (Berufsschule), nicht in der Ausbildungsordnung (Betrieb). Die Verwechslung ist typisch – und für PSOBF zentral.
- **Studie:** Autoren, Titel und Reihe klingen plausibel. Ohne Fund im Katalog oder auf der BIBB-Seite gilt sie als **nicht belegt** – sehr wahrscheinlich erfunden.
- **Begründung:** Der niedrige Frauenanteil ist eine Tatsache, die Begründung ist ein **Stereotyp** (Bias). Ursachen müsste man mit Forschung belegen.
- **Arbeitsprozesse:** grundsätzlich plausibel – aber allgemein. Was in *Ihrem* Betrieb geschieht, klärt erst die Erkundung.
***

### Übung 2b: Wo prüfe ich was?

[[Ausbildungsordnung] [Rahmenlehrplan (KMK)] [BIBB-Daten]]
[         (X)                  ( )                  ( )     ] Ausbildungsdauer und Gliederung der Abschlussprüfung
[         ( )                  (X)                  ( )     ] Lernfelder und Zeitrichtwerte in der Berufsschule
[         ( )                  ( )                  (X)     ] Zahl der neu abgeschlossenen Ausbildungsverträge und Vertragslösungen
[         (X)                  ( )                  ( )     ] Ausbildungsrahmenplan für den Betrieb
***
Ausbildungsordnung und Rahmenlehrplan finden Sie beim BIBB bzw. bei der KMK; Strukturdaten (Verträge, Vertragslösungen, Vorbildung, Alter) z. B. im **BIBB-Datenreport** und in der Datenbank **DAZUBI**. Diese Quellen brauchen Sie auch für den Rechercheauftrag am 16.11.
***

> [!TIP] 💡 Faustregel
> **Jede Zahl, jedes Datum, jede Quelle** aus einer KI-Antwort wird geprüft. Eine Antwort ist ein Entwurf – keine Quelle.

## 3 · Ethik und Recht

<!-- didaktik="ca. 15 min" -->

| Thema | Regel für PSOBF |
| --- | --- |
| **Datenschutz** | Keine personenbezogenen Daten (Namen, Fotos, Gesprächsmitschnitte) und keine Betriebsinterna in KI-Werkzeuge. Notizen vorher anonymisieren. Nutzen Sie möglichst HAWKI. |
| **Urheberrecht** | Fremde Texte und Bilder nicht ungeprüft hochladen und nicht als eigene ausgeben. |
| **Transparenz** | KI-Nutzung in Präsentation und Hausarbeit kennzeichnen: Werkzeug, Zweck, Prompt (APA 7). |
| **Eigenverantwortung** | Sie verantworten jede Aussage – auch die, die eine KI formuliert hat. |

**Darf das in den Prompt?**

[[ok] [nicht ok]]
[ (X)    ( )    ] „Ich erkunde eine Kfz-Werkstatt mit ca. 20 Beschäftigten in Sachsen-Anhalt.“
[ ( )    (X)    ] „Meister Peter K. aus der Werkstatt XY GmbH hat mir erzählt, dass …“
[ ( )    (X)    ] ein Foto des Auftragsbuchs mit Kundennamen und Kennzeichen
[ (X)    ( )    ] ein öffentlich zugänglicher Auszug aus der Ausbildungsordnung
[ ( )    (X)    ] interne Kalkulationen und Stundensätze des Betriebs
***
Allgemeine, nicht identifizierende Angaben und öffentliche Dokumente sind unproblematisch. Namen, Kundendaten, Kennzeichen und Betriebsinterna gehören nicht in ein KI-Werkzeug – auch nicht „nur kurz“.
***

**So kennzeichnen Sie die KI-Nutzung (APA 7):**

```text
Im Text:        (OpenAI, 2026)
Literatur:      OpenAI. (2026). ChatGPT (Version vom 19.10.2026) [Large language model].
                https://chatgpt.com
Anhang:         Prompt im Wortlaut, Datum, Zweck, was Sie übernommen bzw. geändert haben
```

<small>Nach McAdoo (2023). Für HAWKI geben Sie das in HAWKI gewählte Modell und dessen Anbieter an.</small>

## 4 · Rechercheauftrag eigenes Berufsfeld

<!-- didaktik="Planung ca. 15 min, Bearbeitung bis 25.10.2026" -->

> [!IMPORTANT] 📝 Auftrag
> Erkunden Sie mit einem KI-Werkzeug **typische Arbeitsprozesse in Ihrem Berufsfeld** und prüfen Sie die Antwort mit Primärquellen.

1. **Prompt:** Verbessern Sie Ihren Prompt vom 12.10. (Rolle · Aufgabe · Kontext · Format · Beispiele). Bitten Sie das Modell, unsichere Angaben zu markieren.
2. **Antwort:** Speichern Sie die Antwort **unverändert**.
3. **Nachschärfen:** Schärfen Sie mindestens einmal nach (CLEAR). Notieren Sie, was Sie geändert haben und warum.
4. **Faktencheck:** Prüfen Sie **mindestens fünf** Aussagen in einer Tabelle:

<!-- data-type="none" -->
| Aussage der KI | Primärquelle | Ergebnis | Korrektur |
| --- | --- | --- | --- |
| „Die Ausbildung dauert 3 Jahre.“ | Ausbildungsordnung, § 2 | ❌ falsch | 3,5 Jahre |
| … | … | ✅ / ⚠️ / ❌ | … |

5. **Kennzeichnung:** Werkzeug, Modell, Datum (APA 7).

**Ihr Prompt (Entwurf):**

[[___ ___ ___ ___]]

> [!TIP] ✍️ Abgabe als Übung in Moodle
> Laden Sie **Prompt(s) · Originalantwort · Nachschärfung · Faktencheck-Tabelle · Kennzeichnung** als ein PDF in der Moodle-Übung hoch – bis **25.10.2026, 23:59 Uhr**: [Übung in Moodle öffnen](https://elearning.ovgu.de/course/view.php?id=22043)

## 5 · Abschluss

**Noch einmal: Wie sicher fühlen Sie sich jetzt?**

Ich erkenne, ob eine KI-Antwort über einen Ausbildungsberuf stimmt.

- [(1)] 1
- [(2)] 2
- [(3)] 3
- [(4)] 4

**Was nehmen Sie mit?** Welche Grenze hat Sie am meisten überrascht – und was tun Sie dagegen?

[[___ ___]]

> [!TIP] 🔗 Vertiefung
> [KI-Campus Prompt-Labor](https://ki-campus.org/courses/prompt-labor) · UNESCO-Leitfaden zu generativer KI in Bildung und Forschung (UNESCO, 2023)

## Quellen

- Lo, L. S. (2023). The CLEAR path: A framework for enhancing information literacy through prompt engineering. *The Journal of Academic Librarianship, 49*(4), 102720. https://doi.org/10.1016/j.acalib.2023.102720
- McAdoo, T. (2023, 7. April). *How to cite ChatGPT*. APA Style. https://apastyle.apa.org/blog/how-to-cite-chatgpt
- UNESCO. (2023). *Guidance for generative AI in education and research*. UNESCO. https://doi.org/10.54675/EWZM9535
- Walters, W. H., & Wilder, E. I. (2023). Fabrication and errors in the bibliographic citations generated by ChatGPT. *Scientific Reports, 13*, 14045. https://doi.org/10.1038/s41598-023-41032-5
