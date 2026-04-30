# Skripte und Aufgabensammlungen — Skill-Paket

Dieses Skill-Paket bündelt die Konventionen und Templates für Lehrskripte und Aufgabensammlungen für das Gymnasium Baden-Württemberg (Klasse 10).

## Inhalt

```
skripte-und-aufgaben/
├── SKILL.md                                    Hauptdokument mit Triggern und Workflow
├── README.md                                   diese Datei
└── references/
    ├── latex-praeambel.tex                     Standard-LaTeX-Präambel mit allen Boxen
    ├── bildungsplan-bw-klasse10.md             Bildungsplan-Übersicht
    ├── fachspezifika.md                        Pakete & Konventionen je Fach
    └── aufgabensammlung-leitfaden.md           Leitfaden für Übungsaufgaben
```

## Trigger-Schlüsselwörter

Der Skill wird (sobald installiert) automatisch geladen bei:
- "Skript", "Skripte"
- "Aufgaben", "Aufgabensammlung", "Übungsaufgaben", "Klausuraufgaben"
- "Lerndokument", "Lernunterlagen"
- Anfragen wie "erstelle ein PDF zu …" mit Klassen-/Fachbezug
- Hochladen von Aufschrieben/Notizen mit Aufbereitungswunsch

## Aktueller Status

Das Skill-Verzeichnis in Claude.ai ist derzeit schreibgeschützt. Die Optionen:

1. **Als Projekt-Wissen anhängen:** Die SKILL.md und references-Dateien einem Claude-Projekt hinzufügen — dann sind sie in jedem Chat innerhalb dieses Projekts verfügbar.
2. **Auf zukünftiges Skill-Upload-Feature warten:** Wenn Anthropic das ermöglicht, ist das `.skill`-Paket sofort einsatzbereit.
3. **Als Memory-Eintrag:** Ich (Claude) merke mir die wichtigsten Stilregeln in der Memory, sodass sie auch ohne formales Skill-System greifen.

## Verwendung der LaTeX-Präambel

Die Datei `references/latex-praeambel.tex` kann direkt als Vorlage genutzt werden. Sie enthält bereits alle Box-Umgebungen (`definition`, `beispiel`, `aufgabe`, `loesung`, `hinweis`, `stolperfalle`, `klausurtipp`) im einheitlichen Farbschema.
