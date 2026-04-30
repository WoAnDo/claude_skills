# claude_skills

Persönliche Sammlung von Skills für Claude (Anthropic), als Markdown-Dateien zur Wiederverwendung in Konversationen.

Jeder Skill liegt in einem eigenen Unterordner mit einer `SKILL.md` als Einstiegsdatei und ggf. einem `references/`-Unterordner für vertiefende Materialien. Die Verwendung erfolgt über das von Kevin Kovac in [diesem Video](https://www.youtube.com/watch?v=VBvllyVaQ2M) gezeigte Muster: Raw-URL ins Chat-Fenster einfügen, Claude lädt die Datei per `web_fetch` und richtet sich danach.

## Verfügbare Skills

### skripte-und-aufgaben

Erstellt umfangreiche Lernskripte und Aufgabensammlungen als kompilierte LaTeX-PDFs für Mathematik, Physik und Chemie am Gymnasium Baden-Württemberg (Bildungsplan 2016, Schwerpunkt Klasse 10 / Sek II).

**Trigger-Schlüsselwörter:** Skript, Skripte, Aufgaben, Aufgabensammlung, Übungsaufgaben, Klausuraufgaben, Lerndokument

**Raw-URL der SKILL.md:**
```
https://raw.githubusercontent.com/WoAnDo/claude_skills/main/skripte-und-aufgaben/SKILL.md
```

**Inhalt:**
- Einheitliche LaTeX-Präambel mit sieben farbcodierten tcolorbox-Umgebungen (Definition, Beispiel, Aufgabe, Lösung, Hinweis, Stolperfalle, Klausurtipp)
- Bildungsplan-Übersicht für Klasse 10 (Mathe, Physik, Chemie)
- Fachspezifische Pakete und Konventionen (siunitx, pgfplots, mhchem, chemfig)
- Leitfaden für Aufgabensammlungen mit Schwierigkeitsstaffelung und Lösungsstruktur

## Verwendung in Claude

### Variante A — Pro Chat (Standard-Ansatz aus dem Video)

Am Anfang einer neuen Konversation:

```
Lade folgende Anweisungen und richte dich danach:
https://raw.githubusercontent.com/WoAnDo/claude_skills/main/skripte-und-aufgaben/SKILL.md

Erstelle mir ein Skript zur Exponentialfunktion für Klasse 10.
```

### Variante B — User Preferences (einmal eingerichtet, dauerhaft aktiv)

In Claude.ai unter **Settings → Profile → Preferences** ergänzen:

```
Wenn ich die Schlüsselwörter "Skript", "Skripte", "Aufgaben",
"Aufgabensammlung", "Übungsaufgaben", "Klausuraufgaben" oder
"Lerndokument" verwende, lade immer zuerst die Anweisungen aus
https://raw.githubusercontent.com/WoAnDo/claude_skills/main/skripte-und-aufgaben/SKILL.md
und richte dich strikt danach.
```

### Variante C — Claude Project

Ein Projekt anlegen (z. B. „Schule – Skripte und Aufgaben") und die Raw-URL bzw. den SKILL.md-Inhalt als Project Knowledge hinterlegen. Jeder Chat im Projekt hat den Skill dann automatisch geladen.

## Beispiel-Prompts

```
Erstelle mir ein Skript zur Binomialverteilung für Klasse 10
mit 20 Übungsaufgaben pro Kapitel.
```

```
Mach mir 30 Klausuraufgaben zum Thema Geraden in R^3
mit ausführlichen Lösungen.
```

```
Anbei meine Aufschriebe zu den Alkanen [PDF angehängt].
Erstelle ein vollständiges Skript daraus inklusive 50 klausurtypischen
Aufgaben mit Lösungen.
```

```
Erstelle eine Aufgabensammlung Mechanik (Kinematik, Dynamik,
Erhaltungssätze) Klasse 10 BW mit gemischtem Schwierigkeitsgrad.
```

## Repo-Struktur

```
claude_skills/
├── README.md                                    diese Datei
└── skripte-und-aufgaben/
    ├── SKILL.md                                 Einstieg, mit Raw-URLs zu den References
    ├── README.md                                Skill-interne Dokumentation
    └── references/
        ├── latex-praeambel.tex                  LaTeX-Standardpräambel
        ├── bildungsplan-bw-klasse10.md          Bildungsplan-Übersicht
        ├── fachspezifika.md                     Pakete & Konventionen je Fach
        └── aufgabensammlung-leitfaden.md        Leitfaden für Übungsaufgaben
```

## Neue Skills hinzufügen

1. Neuen Unterordner mit aussagekräftigem Namen anlegen
2. `SKILL.md` mit YAML-Frontmatter (`name`, `description`) und Workflow-Beschreibung erstellen
3. Bei Bedarf `references/`-Unterordner für vertiefende Materialien
4. In dieser README einen neuen Abschnitt unter „Verfügbare Skills" hinzufügen mit Raw-URL und Beispiel-Prompts

## Hinweis

Das Repo ist bewusst öffentlich, damit Claude die Raw-URLs per `web_fetch` lesen kann. Es enthält keine sensiblen Daten — nur Stilregeln und Templates.
