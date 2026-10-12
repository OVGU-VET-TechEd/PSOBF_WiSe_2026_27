<!--
author:    Hannes Tegelbeckers
email:     hannes.tegelbeckers@ovgu.de
version:   0.1.0
language:  de
narrator:  Deutsch Female
mode:      Presentation
classroom: enable

title:     PSOBF – KI-Einführung I: Large Language Models & Prompting
comment:   Sitzung 1 (12.10.2026) des Seminars „Prozesse, Systeme und Organisation betrieblicher Facharbeit": Wie funktioniert ein Large Language Model (Token, Wahrscheinlichkeiten, Trainingsdaten, Kontextfenster) – und wie prompte ich gut (Rolle · Aufgabe · Kontext · Format · Beispiele; iteratives Nachschärfen mit dem CLEAR-Framework)?
tags:      PSOBF, Künstliche Intelligenz, Large Language Model, Token, Kontextfenster, Prompting, CLEAR, Berufsbildung
-->

# KI-Einführung I: Large Language Models & Prompting

**Prozesse, Systeme und Organisation betrieblicher Facharbeit** · Sitzung 1 · 12.10.2026

<!-- didaktik="KI-Teil der Auftaktsitzung · ca. 60 min · alle Aufgaben in Einzelarbeit mit Classroom-Auswertung" -->

> **Leitfrage:** Was passiert eigentlich, wenn ein Sprachmodell antwortet – und wie bringe ich es dazu, mir bei der Analyse von Arbeitsprozessen wirklich zu helfen?

{{1}}
<section>

**Nach dieser Sitzung können Sie …**

1. die Begriffe **Token, Wahrscheinlichkeit, Trainingsdaten und Kontextfenster** erklären,
2. daraus typische **Stärken und Schwächen** von Sprachmodellen ableiten,
3. einen Prompt aus **Rolle · Aufgabe · Kontext · Format · Beispielen** aufbauen,
4. einen Prompt mit dem **CLEAR-Framework** iterativ nachschärfen.

</section>

                --{{0}}--
Im zweiten Teil der heutigen Sitzung geht es um Künstliche Intelligenz. Wir schauen zuerst unter die Motorhaube eines Sprachmodells und üben dann, gute Prompts zu schreiben.

## Einstieg: Was glauben Sie?

<!-- didaktik="Lehrschritt provozieren · 3 min · Umfrage, Ergebnis zeigen, nicht auflösen – Auflösung auf Folie Trainingsdaten" -->

**Allein (1 min):** Stimmen Sie der Aussage zu?

> **„Ein Sprachmodell wie ChatGPT schlägt die Antwort in einer Datenbank nach."**

- [(ja)] Stimmt
- [(eher ja)] Stimmt eher
- [(eher nein)] Stimmt eher nicht
- [(nein)] Stimmt nicht

                --{{0}}--
Stimmen Sie bitte ab. Wir lösen die Frage im Laufe der Sitzung auf.

## Was ist ein Large Language Model?

Ein **Large Language Model (LLM)** ist ein großes neuronales Netz, das darauf trainiert wurde, **das nächste Textstück vorherzusagen**.

{{1}}
``` ascii
  Eingabe (Prompt)          Sprachmodell                 Ausgabe
 +-----------------+     +-----------------+     +---------------------+
 | "Die Ausbildung | --> |  Milliarden von | --> | wahrscheinlichstes  |
 |  dauert ..."    |     |  Parametern     |     | nächstes Token      |
 +-----------------+     +-----------------+     +---------------------+
                                  ^                         |
                                  +---- wird angehängt -----+
                                     und erneut eingelesen
```

{{2}}
<section>

Vier Begriffe erklären fast alles, was Sie im Alltag mit LLMs beobachten:

| Begriff | Kurz gesagt |
| --- | --- |
| **Token** | Die Einheiten, in die Text zerlegt wird |
| **Wahrscheinlichkeiten** | Das Modell wählt das nächste Token nach Wahrscheinlichkeit |
| **Trainingsdaten** | Woher das Modell seine Muster hat |
| **Kontextfenster** | Wie viel Text das Modell auf einmal „sieht" |

</section>

                --{{0}}--
Ein Sprachmodell erzeugt Text Stück für Stück. Jedes neue Stück wird an den bisherigen Text angehängt, und dann wird wieder das nächste Stück vorhergesagt. Technisch steckt meist die sogenannte Transformer-Architektur dahinter.

## 1 · Token

Sprachmodelle lesen keine Buchstaben und keine ganzen Wörter, sondern **Token**: häufige Wörter, Wortteile, Satzzeichen.

{{1}}
``` ascii
 vereinfachtes Beispiel (die echte Zerlegung hängt vom Modell ab):

 "Ausbildungsordnung"  -->  [Aus] [bildungs] [ordnung]
 "Mechatroniker"       -->  [Mech] [atron] [iker]
 "Die"                 -->  [Die]
```

{{2}}
<section>

**Warum ist das wichtig?**

- Kosten, Geschwindigkeit und Grenzen werden **in Token gemessen**, nicht in Wörtern.
- Faustregel für Englisch: 1 Token ≈ 4 Zeichen ≈ ¾ Wort. **Deutsche Texte brauchen meist mehr Token** – lange Komposita werden zerlegt.
- Aufgaben auf Buchstabenebene (Zählen, Silben, Reime) fallen Modellen schwer, weil sie die Buchstaben gar nicht direkt sehen.

Ausprobieren: [OpenAI Tokenizer](https://platform.openai.com/tokenizer)

</section>

                --{{0}}--
Für das Modell ist Text eine Folge von Zahlen. Jedes Token hat eine Nummer im Vokabular. Deshalb kann ein Modell einen ganzen Absatz souverän zusammenfassen, aber beim Zählen der Buchstaben in einem Wort danebenliegen.

### Kurzcheck Token

**Allein (1 min):** Ein Modell soll zählen, wie oft der Buchstabe „r" in „Erdbeere" vorkommt, und liegt falsch. Warum?

- [( )] Das Modell kennt das Wort „Erdbeere" nicht.
- [(X)] Das Modell verarbeitet Token, nicht einzelne Buchstaben.
- [( )] Das Kontextfenster ist zu klein.
- [( )] Die Trainingsdaten enthalten keine deutschen Wörter.
[[?]] Denken Sie an die Einheit, in der das Modell Text „sieht".

                --{{0}}--
Richtig ist: Das Modell sieht Token. Ob ein Buchstabe darin vorkommt, muss es indirekt erschließen.

## 2 · Wahrscheinlichkeiten

Für jedes nächste Token berechnet das Modell eine **Wahrscheinlichkeitsverteilung** über sein ganzes Vokabular.

{{1}}
``` ascii
 "Die Ausbildung zum Mechatroniker dauert ..."

  dreieinhalb  ████████████████████████  62 %
  drei         ███████                   18 %
  in           ███                        7 %
  zwei         ██                         5 %
  ...          ███                        8 %

  (ausgedachte Beispielwerte zur Veranschaulichung)
```

{{2}}
<section>

**Folgen für Sie:**

- Das Modell wählt nicht immer das wahrscheinlichste Token, sondern **zieht zufällig** aus der Verteilung (gesteuert z. B. über die *Temperatur*). → **Gleicher Prompt, andere Antwort.**
- Ziel ist **plausibler** Text, nicht **wahrer** Text. Wo Wissen fehlt, entsteht trotzdem flüssiger Text → **Halluzination**.
- Je seltener ein Thema in den Trainingsdaten ist (z. B. eine bestimmte Ausbildungsordnung), desto unsicherer die Verteilung.

</section>

                --{{0}}--
Das Modell hat kein eingebautes Wissen darüber, ob etwas stimmt. Es kennt nur, welche Fortsetzung in ähnlichen Texten häufig war. Deshalb klingt eine falsche Antwort genauso überzeugend wie eine richtige.

### Kurzcheck Wahrscheinlichkeiten

**Allein (1 min):** Sie stellen dieselbe Frage zweimal in einem neuen Chat. Was erwarten Sie?

- [( )] Immer exakt dieselbe Antwort, weil das Modell deterministisch rechnet.
- [(X)] Meist ähnliche, aber unterschiedlich formulierte Antworten – manchmal auch inhaltlich abweichende.
- [( )] Eine Fehlermeldung, weil die Frage schon gestellt wurde.
[[?]] Das Modell zieht aus einer Wahrscheinlichkeitsverteilung.

                --{{0}}--
Genau deshalb lohnt es sich, wichtige Fragen mehrfach zu stellen oder Antworten gegenzuprüfen. Weichen die Antworten stark voneinander ab, ist das ein Warnsignal.

## 3 · Trainingsdaten

{{1}}
``` ascii
  1. Vortraining                 2. Feinabstimmung              3. Nutzung
 +----------------------+      +------------------------+      +----------------+
 | riesige Textmengen:  | ---> | Beispiele für gute     | ---> | Ihr Prompt     |
 | Webseiten, Bücher,   |      | Antworten + Bewertung  |      | im Chat        |
 | Code, Foren ...      |      | durch Menschen         |      |                |
 | Ziel: nächstes Token |      | Ziel: hilfreich, sicher|      | Wissen fest    |
 +----------------------+      +------------------------+      +----------------+
        Wissensstichtag ──┘
```

{{2}}
<section>

**Was folgt daraus?**

| Eigenschaft der Trainingsdaten | Folge im Seminar |
| --- | --- |
| Endet an einem **Stichtag** | Neuordnungen von Ausbildungsberufen fehlen eventuell |
| Viel Englisch, viel Allgemeines | Deutsches Berufsbildungssystem, Lernfelder, Rahmenlehrpläne oft ungenau |
| Enthält Meinungen und **Verzerrungen (Bias)** | Stereotype Bilder von Berufen und Beschäftigten |
| Kein Zugriff auf Ihren Betrieb | Das Modell kennt Ihre Exkursion nicht – Sie müssen den Kontext liefern |

</section>

{{3}}
<section>

**Auflösung des Einstiegs:** Ein LLM schlägt **nicht** in einer Datenbank nach. Wissen steckt als Muster in den Parametern. Manche Werkzeuge kombinieren das Modell zusätzlich mit einer **Websuche** – dann sollten Quellen angezeigt werden, die Sie prüfen können.

</section>

                --{{0}}--
Das Modell lernt in zwei Phasen: Zuerst sagt es auf riesigen Textmengen das nächste Token vorher, danach wird es mit menschlichem Feedback auf hilfreiche Antworten abgestimmt. Was nach dem Stichtag passiert ist oder selten im Netz steht, kennt es schlecht.

## 4 · Kontextfenster

Das **Kontextfenster** ist alles, was das Modell bei einer Antwort gleichzeitig berücksichtigen kann – gemessen in Token.

{{1}}
``` ascii
 +---------------------------------------------------------------+
 |                        Kontextfenster                         |
 |  [Systemanweisung] [bisheriger Chat] [hochgeladene Datei]     |
 |  [Ihr aktueller Prompt] [die Antwort, die gerade entsteht]    |
 +---------------------------------------------------------------+
   ^ was nicht hineinpasst, wird abgeschnitten oder zusammengefasst
```

{{2}}
<section>

**Was folgt daraus?**

- **Kein Gedächtnis zwischen Chats** (außer das Werkzeug hat eine eigene Speicherfunktion). Ein neuer Chat beginnt bei null.
- **Sehr lange Chats:** Frühe Anweisungen können verloren gehen; Informationen in der Mitte langer Texte werden schlechter genutzt („lost in the middle").
- **Ihre Chance:** Was im Kontext steht, kann das Modell nutzen. Geben Sie relevantes Material mit – z. B. Auszüge aus der Ausbildungsordnung oder Ihre Beobachtungsnotizen (anonymisiert!).

</section>

                --{{0}}--
Das Kontextfenster ist das Arbeitsgedächtnis des Modells. Alles, was Sie dort hineingeben, kann das Modell verwenden. Darum ist guter Kontext oft wichtiger als eine geschickte Formulierung.

## Zwischenquiz: Funktionsweise

<!-- didaktik="Sicherung Teil 1 · 4 min · Einzelarbeit · Ergebnisse im Classroom zeigen und kurz besprechen" -->

**Allein (3 min):**

**1. Sie laden in einem neuen Chat die Ausbildungsordnung Ihres Berufs hoch. Wo befindet sich der Text jetzt für das Modell?**

- [( )] In den Trainingsdaten
- [(X)] Im Kontextfenster
- [( )] In den Parametern des Modells
[[?]] Hochgeladene Dateien verändern das Modell nicht.

**2. Welche Aussagen stimmen? (mehrere richtig)**

- [[X]] Ein LLM kann flüssig formulierte, aber falsche Angaben machen.
- [[ ]] Ein LLM prüft jede Aussage vor der Ausgabe an einer Quelle.
- [[X]] Lange deutsche Fachbegriffe werden in mehrere Token zerlegt.
- [[X]] Ein neuer Chat kennt den Inhalt eines alten Chats normalerweise nicht.

                --{{0}}--
Kurze Sicherung, bevor wir zum Prompting kommen.

## Prompting: Die fünf Bausteine

Ein guter Prompt gibt dem Modell, was es **nicht wissen kann**.

{{1}}
| Baustein | Leitfrage | Beispiel aus PSOBF |
| --- | --- | --- |
| **Rolle** | Aus welcher Perspektive soll das Modell antworten? | „Du bist Ausbilder:in im Kfz-Handwerk mit Erfahrung in der Arbeitsprozessanalyse." |
| **Aufgabe** | Was genau soll herauskommen? Mit welchem Verb? | „Gliedere den Arbeitsprozess *Bremsanlage instand setzen* in Prozessschritte." |
| **Kontext** | Was muss das Modell über Situation, Zielgruppe, Material wissen? | „Es geht um das 2. Ausbildungsjahr Kfz-Mechatroniker:in. Grundlage sind meine Notizen unten." |
| **Format** | Wie soll das Ergebnis aussehen? | „Tabelle mit Spalten: Schritt · Werkzeuge · Anforderungen. Höchstens 8 Zeilen." |
| **Beispiele** | Wie sieht ein gutes Ergebnis aus? | „Beispielzeile: Fahrzeug annehmen · Auftragsblatt · Kundengespräch führen" |

{{2}}
> **Merksatz:** Nicht jeder Prompt braucht alle fünf Bausteine – aber wenn das Ergebnis nicht passt, fehlt meist einer davon.

                --{{0}}--
Rolle, Aufgabe, Kontext, Format und Beispiele. Am wichtigsten sind meist Aufgabe und Kontext. Beispiele helfen besonders dann, wenn Sie ein ganz bestimmtes Format oder einen Stil erwarten.

### Vorher – nachher

{{1}}
<section>

**❌ Vorher**

```text
Schreib was über Arbeitsprozesse beim Kfz-Mechatroniker.
```

</section>

{{2}}
<section>

**✅ Nachher**

```text
[Rolle]    Du bist Ausbilder:in im Kfz-Handwerk und kennst die
           Arbeitsprozessanalyse.
[Aufgabe]  Gliedere den Arbeitsprozess "Bremsanlage instand setzen"
           in 5–8 Prozessschritte.
[Kontext]  Ich studiere Berufspädagogik und bereite eine Betriebs-
           erkundung in einer Kfz-Werkstatt vor. Ich will wissen,
           worauf ich bei der Beobachtung achten soll.
[Format]   Tabelle: Schritt | Werkzeuge & Methoden | Anforderungen
           an die Fachkraft. Danach 3 Beobachtungsfragen.
[Beispiel] Fahrzeug annehmen | Auftragsblatt, Probefahrt |
           Kundenwunsch erfassen, Fehler eingrenzen
Wenn dir Informationen fehlen, frag nach, bevor du antwortest.
```

</section>

                --{{0}}--
Der zweite Prompt ist länger, aber das Ergebnis ist sofort brauchbar. Achten Sie auf den letzten Satz: Sie dürfen das Modell ausdrücklich auffordern, Rückfragen zu stellen.

### Beispiele im Prompt: Zero-Shot und Few-Shot

{{1}}
| | Zero-Shot | Few-Shot |
| --- | --- | --- |
| Was? | Nur Anweisung, kein Beispiel | Anweisung + ein bis wenige Beispiele |
| Wann? | Einfache, eindeutige Aufgaben | Bestimmtes Format, Stil, Fachsprache, Einordnung |
| Risiko | Ergebnis weicht von Ihrer Vorstellung ab | Modell kopiert das Beispiel zu eng |

{{2}}
<section>

**Tipp:** Verwenden Sie **zwei unterschiedliche** Beispiele, damit das Modell das Muster erkennt und nicht nur ein Beispiel nachahmt.

</section>

                --{{0}}--
Sprachmodelle können aus wenigen Beispielen im Prompt lernen, was Sie erwarten. Das nennt man Few-Shot-Prompting.

## Iteratives Nachschärfen

Der erste Prompt ist selten der beste. Prompting ist ein **Dialog**:

{{1}}
``` ascii
   +-----------+      +-----------+      +-----------+      +-------------+
   | Prompt    | ---> | Antwort   | ---> | prüfen &  | ---> | nachschärfen|
   | schreiben |      | lesen     |      | bewerten  |      |             |
   +-----------+      +-----------+      +-----------+      +------+------+
         ^                                                         |
         +---------------------------------------------------------+
```

{{2}}
<section>

**Typische Nachschärf-Prompts:**

- „Kürze auf die Hälfte und lass Allgemeinplätze weg."
- „Das ist zu allgemein. Beziehe dich auf das 2. Ausbildungsjahr."
- „Welche deiner Angaben sind unsicher? Markiere sie."
- „Formuliere die Prozessschritte als Handlungen (Verb am Ende)."

</section>

                --{{0}}--
Behandeln Sie die erste Antwort als Entwurf. Lesen Sie kritisch, sagen Sie dem Modell genau, was fehlt, und fordern Sie es auf, unsichere Angaben selbst zu kennzeichnen.

## Das CLEAR-Framework

Leo S. Lo (2023) schlägt fünf Prinzipien vor, um Prompts zu prüfen und zu verbessern:

{{1}}
| | Prinzip | Prüffrage an meinen Prompt |
| --- | --- | --- |
| **C** | **Concise** – knapp | Steht nur drin, was das Modell wirklich braucht? |
| **L** | **Logical** – logisch | Ist die Reihenfolge nachvollziehbar (Kontext → Aufgabe → Format)? |
| **E** | **Explicit** – explizit | Habe ich Umfang, Format und Zielgruppe ausdrücklich genannt? |
| **A** | **Adaptive** – anpassungsfähig | Passe ich den Prompt an, wenn die Antwort nicht stimmt? |
| **R** | **Reflective** – reflektiert | Prüfe ich die Antwort auf Richtigkeit, Quellen und Bias? |

{{2}}
<section>

**C, L, E** helfen beim **Schreiben**, **A** und **R** beim **Nachschärfen**.

</section>

                --{{0}}--
Das CLEAR-Framework stammt aus der Bibliothekswissenschaft und verbindet Prompting mit Informationskompetenz. Die ersten drei Buchstaben betreffen den Prompt selbst, die letzten beiden den Umgang mit der Antwort.

### Kurzcheck CLEAR

**Allein (1 min):** Sie bitten das Modell um Literatur zur Arbeitsprozessanalyse. Es nennt fünf Titel. Sie suchen jeden Titel im Bibliothekskatalog. Welches Prinzip wenden Sie an?

- [( )] Concise
- [( )] Logical
- [( )] Explicit
- [(X)] Reflective
[[?]] Es geht um das Prüfen der Antwort.

                --{{0}}--
Genau – Reflective. Sprachmodelle erfinden besonders gern Literaturangaben, die echt aussehen. Jede Quelle wird geprüft.

## Übung: Ihr erster Prompt

<!-- didaktik="Anwendung · 15 min · Einzelarbeit am eigenen Gerät · Prompts im Classroom sammeln, 2–3 Beispiele freiwillig im Plenum besprechen" -->

**Allein (8 min):** Bereiten Sie den **Rechercheauftrag zur nächsten Sitzung** vor. Schreiben Sie einen Prompt, mit dem ein Sprachmodell Ihnen einen ersten Überblick über **typische Arbeitsprozesse in Ihrem Berufsfeld** gibt. Nutzen Sie alle fünf Bausteine.

{{1}}
<section>

> ⚠️ **Datenschutz:** Keine Namen, keine Betriebsinterna, keine personenbezogenen Daten in den Prompt. Nutzen Sie ein von der Hochschule bereitgestelltes Werkzeug (z. B. HAWKI), wenn möglich.

Fügen Sie Ihren Prompt hier ein:

[[___ ___ ___ ___]]

</section>

{{2}}
<section>

**Allein (5 min):** Schicken Sie den Prompt ab, lesen Sie die Antwort und schärfen Sie **einmal** nach. Welches CLEAR-Prinzip hat Ihnen beim Nachschärfen am meisten geholfen?

- [(C)] Concise
- [(L)] Logical
- [(E)] Explicit
- [(A)] Adaptive
- [(R)] Reflective

</section>

                --{{0}}--
Jetzt sind Sie dran. Schreiben Sie Ihren Prompt allein und teilen Sie ihn über das Textfeld. Wer möchte, stellt seinen Prompt gleich im Plenum vor.

## Reflexion

<!-- didaktik="Sicherung · 3 min · Umfrage zeigen, Lücken benennen" -->

**Allein (1 min):** Welche Bausteine haben in Ihrem **ersten** Prompt gefehlt? (mehrere möglich)

- [[Rolle]] Rolle
- [[Aufgabe]] Aufgabe (klar genug)
- [[Kontext]] Kontext
- [[Format]] Format
- [[Beispiele]] Beispiele
- [[nichts]] Es hat nichts gefehlt

{{1}}
<section>

**Allein (1 min):** Wie sicher fühlen Sie sich jetzt beim Prompten?

- [(1)] Unsicher
- [(2)] Eher unsicher
- [(3)] Eher sicher
- [(4)] Sicher

</section>

                --{{0}}--
Die Auswertung zeigt uns, welche Bausteine am häufigsten fehlen. Erfahrungsgemäß sind das Kontext und Format.

## Zusammenfassung

{{1}}
| Funktionsweise | … und was ich daraus für meinen Prompt mache |
| --- | --- |
| **Token** | Länge und Kosten in Token denken; keine Buchstaben-Aufgaben erwarten |
| **Wahrscheinlichkeiten** | Antwort ist plausibel, nicht geprüft → **Faktencheck** |
| **Trainingsdaten** | Stichtag und Bias beachten → **Primärquellen** (BIBB, Ausbildungsordnung, Rahmenlehrplan) |
| **Kontextfenster** | Relevantes Material mitgeben, neue Chats für neue Themen |

{{2}}
<section>

**Prompting:** Rolle · Aufgabe · Kontext · Format · Beispiele → **nachschärfen mit CLEAR**.

**PSOBF-Regel:** KI-Nutzung kennzeichnen (Werkzeug, Zweck, Prompt; APA 7) und jede Aussage über Ausbildungsberufe mit Primärquellen prüfen.

</section>

                --{{0}}--
Wenn Sie wissen, wie ein Sprachmodell funktioniert, verstehen Sie auch seine Fehler. Und Sie wissen, was Ihr Prompt leisten muss.

## Ausblick: Sitzung 2 (Selbstlernen)

**Montag, 19.10.2026 · 🔵 Selbstlernsitzung – KI-Einführung II: Werkzeuge, Grenzen, Ethik**

- LiaScript-Modul [S02 – KI-Einführung II](https://liascript.github.io/course/?https://raw.githubusercontent.com/OVGU-VET-TechEd/PSOBF_WiSe_2026_27/main/Selflearn/S02_KI_Einfuehrung_II.md) bearbeiten
- **Rechercheauftrag:** Ihr Berufsfeld mit KI erkunden – mit dem heute entwickelten Prompt – und die Ergebnisse mit Primärquellen prüfen
- **Abgabe** im Moodle-Kurs bis **25.10.2026, 23:59 Uhr**: Prompt(s), Antwort, Faktencheck

Vertiefung: [KI-Campus Prompt-Labor](https://ki-campus.org/courses/prompt-labor)

                --{{0}}--
Nächste Woche arbeiten Sie selbstständig weiter. Nehmen Sie Ihren Prompt von heute als Startpunkt für den Rechercheauftrag.

## Quellen

- Brown, T. B., Mann, B., Ryder, N., Subbiah, M., Kaplan, J., Dhariwal, P., … Amodei, D. (2020). Language models are few-shot learners. *Advances in Neural Information Processing Systems, 33*, 1877–1901.
- Liu, N. F., Lin, K., Hewitt, J., Paranjape, A., Bevilacqua, M., Petroni, F., & Liang, P. (2024). Lost in the middle: How language models use long contexts. *Transactions of the Association for Computational Linguistics, 12*, 157–173. https://doi.org/10.1162/tacl_a_00638
- Lo, L. S. (2023). The CLEAR path: A framework for enhancing information literacy through prompt engineering. *The Journal of Academic Librarianship, 49*(4), 102720. https://doi.org/10.1016/j.acalib.2023.102720
- Ouyang, L., Wu, J., Jiang, X., Almeida, D., Wainwright, C. L., Mishkin, P., … Lowe, R. (2022). Training language models to follow instructions with human feedback. *Advances in Neural Information Processing Systems, 35*, 27730–27744.
- Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., & Polosukhin, I. (2017). Attention is all you need. *Advances in Neural Information Processing Systems, 30*.
- OpenAI. (o. J.). *Tokenizer*. https://platform.openai.com/tokenizer
- KI-Campus. (o. J.). *Prompt-Labor*. https://ki-campus.org/courses/prompt-labor

                --{{0}}--
Hier finden Sie die Quellen zu dieser Sitzung.
