---
name: skripte-und-aufgaben
description: Erstellt umfangreiche Lernskripte und Aufgabensammlungen als kompilierte LaTeX-PDFs für Mathematik, Physik und Chemie am Gymnasium Baden-Württemberg (Bildungsplan 2016, Schwerpunkt Klasse 10/Sek II). Diesen Skill IMMER verwenden, wenn der Nutzer die Schlüsselwörter "Skript", "Skripte", "Aufgaben", "Aufgabensammlung", "Übungsaufgaben", "Klausuraufgaben" oder "Lernunterlagen" verwendet — auch dann, wenn nicht explizit "PDF" oder "LaTeX" gesagt wird. Ebenso bei Anfragen wie "erstelle ein Lerndokument zu X", "mach mir Übungen zu Y", "Klassenarbeitstraining zu Z" oder beim Hochladen von Aufschrieben/Notizen mit der Bitte um Aufbereitung. Deckt fachliche Inhalte (Mathematik mit TikZ/pgfplots, Physik mit Mechanik-/E-Lehre-Skizzen, Chemie mit chemfig/mhchem) sowie Stilregeln (farbcodierte tcolorbox-Boxen, ausführliche Schrittlösungen, Stolperfallen-Hinweise) ab.
---

# Skripte und Aufgabensammlungen — Gymnasium BW

> **Hinweis an Claude:** Wenn dieser Skill aus GitHub geladen wurde, sind die unten erwähnten Referenzdateien unter folgenden Raw-URLs abrufbar (per `web_fetch`):
>
> - LaTeX-Standardpräambel: <https://raw.githubusercontent.com/WoAnDo/claude_skills/main/skripte-und-aufgaben/references/latex-praeambel.tex>
> - Bildungsplan-Übersicht: <https://raw.githubusercontent.com/WoAnDo/claude_skills/main/skripte-und-aufgaben/references/bildungsplan-bw-klasse10.md>
> - Fachspezifische Pakete und Konventionen: <https://raw.githubusercontent.com/WoAnDo/claude_skills/main/skripte-und-aufgaben/references/fachspezifika.md>
> - Leitfaden für Aufgabensammlungen: <https://raw.githubusercontent.com/WoAnDo/claude_skills/main/skripte-und-aufgaben/references/aufgabensammlung-leitfaden.md>
>
> Diese Referenzen erst dann nachladen, wenn sie für die konkrete Aufgabe gebraucht werden — nicht alle auf Vorrat.

Dieser Skill bündelt die Konventionen für Lernskripte und Aufgabensammlungen, wie Wolfgang sie für seinen Kontext (Klasse 10 Gymnasium Baden-Württemberg) nutzt.

## Zwei Hauptproduktarten

### 1. Skript (Lehrdokument)
Ausführliches Lehrwerk zu einem Themenfeld. Aufbau:
- **Titel & Inhaltsverzeichnis** (mit `\tableofcontents`)
- **Konzepterklärung** mit Definitionen, Herleitungen, Skizzen
- **Beispielaufgaben mit Musterlösungen** als didaktische Brücke
- **Klausurtipps und typische Stolperfallen** (eigene Box-Klasse)
- **Übungsaufgaben** (10–20 pro Kapitel) mit ausführlichen Lösungen im Anhang
- **Optional: Anhang mit Formeln, Tabellen, Glossar**

Typische Länge: 15–60 Seiten.

### 2. Aufgabensammlung
Fokus auf Übungsmaterial. Aufbau:
- **Kurzes Konzept-Recap** (1–2 Seiten, optional)
- **Aufgabenteil** (15–80 Aufgaben) mit Skizzen, gestaffeltem Schwierigkeitsgrad
- **Lösungsteil** mit Schritt-für-Schritt-Rechnungen, eingerahmten Endergebnissen

Typische Länge: 20–50 Seiten.

## Workflow

### Schritt 1: Anforderung präzisieren
Wenn Wolfgang nur "erstell mir ein Skript zu X" sagt, kurz klären (oder begründet annehmen):
- **Fach und Klassenstufe** (Default: Klasse 10 Gymnasium BW)
- **Skript oder Aufgabensammlung?** (manchmal beides)
- **Anzahl Übungsaufgaben** (Default: 10–20 pro Kapitel)
- **Liegen Aufschriebe/Notizen vor?** Wenn ja: zuerst Inhalte daraus extrahieren

Wenn Wolfgang Aufschriebe als PDF hochlädt: **immer zuerst lesen** (mit dem `pdf-reading`-Skill), bevor das Skript geschrieben wird. Niemals "drüber-schreiben" mit allgemeinem Lehrbuchwissen.

### Schritt 2: Bildungsplan-Abgleich
Bei Themenwahl oder Lerninhalt-Fragen ggf. den **Bildungsplan 2016** unter `https://www.bildungsplaene-bw.de/` konsultieren (per `web_fetch`). Die aufschlüsselten Standardthemen stehen in `bildungsplan-bw-klasse10.md` (siehe Raw-URL oben).

### Schritt 3: LaTeX-Präambel verwenden
Die Standard-Präambel mit allen Boxen und Farben liegt in `latex-praeambel.tex` (siehe Raw-URL oben). **Diese Präambel ist die Referenz für alle Skripte** — keine Box-Stile neu erfinden, keine Farben improvisieren. Konsistenz über alle Dokumente hinweg ist gewünscht.

Die Präambel enthält fertige tcolorbox-Umgebungen für:
- `definition` (blau) — für Definitionen, Sätze, Merksätze
- `beispiel` (grün) — für durchgerechnete Beispielaufgaben
- `aufgabe` (orange) — für Übungsaufgaben
- `loesung` (grau) — für Lösungen
- `hinweis` (gelb) — für allgemeine Hinweise
- `stolperfalle` (rot) — für typische Klausurfehler
- `klausurtipp` (lila) — für strategische Tipps

### Schritt 4: Fachspezifische Pakete & Konventionen
Siehe `fachspezifika.md` (Raw-URL oben) für die je nach Fach benötigten Pakete (chemfig, mhchem, siunitx, pgfplots) und übliche Skizzen (Wurfparabel, Reaktionsgleichungen, Vektorzeichnungen).

### Schritt 5: Aufgaben-Design
Siehe `aufgabensammlung-leitfaden.md` (Raw-URL oben):
- Schwierigkeitsstaffelung (Grundlagen → Anwendung → Transfer/Sachaufgabe)
- Skizzen so oft wie möglich (TikZ inline)
- Lösungen *immer* mit Zwischenschritten, nicht nur Endergebnis
- Endergebnisse mit `\boxed{}` einrahmen (Mathe/Physik) bzw. visuell hervorheben

### Schritt 6: Kompilieren und prüfen
- pdflatex zwei Durchläufe (für Inhaltsverzeichnis und Querverweise)
- Bei chemfig/mhchem-Problemen ggf. `texlive-plain-generic` (für simplekv) und `texlive-lang-german` nachinstallieren
- XeLaTeX nur einsetzen, wenn explizit `fontspec` oder Spezialschriften gebraucht werden
- Bei Fehlern: kurzen Auszug aus dem `.log` zeigen und gezielt fixen, nicht das ganze Dokument neu generieren

### Schritt 7: Ausgabe
Das fertige PDF nach `/mnt/user-data/outputs/` kopieren und mit `present_files` zum Download anbieten. Der Dateiname soll Fach + Thema + Klasse enthalten, z. B. `mathematik_klasse10_binomialverteilung.pdf`.

## Stilregeln (wichtig)

- **Sprache:** Durchgehend Deutsch, formelle Ansprache an Schüler ("man berechnet ...", nicht "wir berechnen ...")
- **Mathematik-Notation:** Konsequent `\vec{a}`, `\mathbb{R}`, `\cdot` für Multiplikation, kein `*`
- **Einheiten:** Immer `siunitx` mit `\SI{9{,}81}{\metre\per\second\squared}` (deutsche Dezimalkomma-Konvention)
- **Vektoren in 3D:** Spaltenform mit `\begin{pmatrix} x \\ y \\ z \end{pmatrix}`
- **Reaktionsgleichungen:** `\ce{}` aus mhchem
- **Strukturformeln:** chemfig
- **Diagramme:** pgfplots bevorzugen vor selbstgemalten TikZ-Achsen
- **Komma als Dezimaltrennzeichen** in allen Zahlen (deutsche Konvention), `0{,}5` in Mathe-Modus
- **Bildungsplan-Bezug:** wenn relevant, Themen mit Bildungsplan-Codes (z. B. "3.3.5.1 Kinematik") referenzieren

## Anti-Muster (vermeiden)

- ❌ Generisches Lehrbuch-Material ohne BW-Bezug
- ❌ Englische Begriffe wenn deutsche Standard sind ("Bernoulli-Experiment" statt "Bernoulli trial")
- ❌ Lösungen ohne Zwischenschritte
- ❌ Übungsaufgaben ohne Skizzen (wenn der Stoff visuell ist)
- ❌ Unkommentierte Formeln ohne Herleitung im Skript-Teil
- ❌ Ad-hoc-Boxen statt der Standard-tcolorbox-Umgebungen aus der Präambel

## Beispiele aus früheren Skripten

| Fach | Thema | Umfang |
|------|-------|--------|
| Mathematik | Binomialverteilung | 38 S., 7 Kapitel, 140 Übungen |
| Mathematik | Geometrische Beweise mit Vektoren | 20 Aufgaben mit Skizzen + Lösungen |
| Mathematik | Urnenmodell (Kombinatorik) | 80 Aufgaben, 4 Fälle gemischt |
| Physik | Mechanik (Kinematik, Dynamik, Erhaltungssätze) | 15 S. + 17 S. Herleitungsband |
| Chemie | Alkohole | 30 S., 70 klausurtypische Aufgaben |
| Chemie | Alkane | Komplettes Skript mit Strukturformeln |

Wenn ein neues Thema "in der Familie" eines bisherigen ist, Stil und Boxen-Verwendung konsistent halten.
