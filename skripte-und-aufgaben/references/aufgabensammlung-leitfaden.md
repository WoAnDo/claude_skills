# Leitfaden für Aufgabensammlungen

## Aufbau

Eine Aufgabensammlung hat zwei klar getrennte Teile:

1. **Aufgabenteil** — alle Aufgaben hintereinander, ohne Lösungen
2. **Lösungsteil** (Anhang) — alle Lösungen, jeweils mit Verweis auf die Aufgabennummer

Die Trennung ist wichtig, damit der Schüler erst eigenständig versucht, bevor er nachschaut.

## Anzahl Aufgaben

Standardvorgaben (anpassbar):
- **Klein:** 10–15 Aufgaben (eine Klausurvorbereitung)
- **Mittel:** 20–30 Aufgaben (ein Themengebiet)
- **Groß:** 50–80+ Aufgaben (komplette Themenabdeckung mit allen Fallunterscheidungen)

## Schwierigkeitsstaffelung

Aufgaben in **drei Stufen** ordnen (nicht streng linear, aber tendenziell):

### Stufe 1 — Reproduktion / Grundlagen (40 %)
Direkte Anwendung einer Definition oder Formel.
- "Berechne …"
- "Gib an …"
- "Zeichne …"

### Stufe 2 — Anwendung / Reorganisation (40 %)
Mehrere Schritte, Kombination von Konzepten.
- "Untersuche, ob …"
- "Bestimme …"
- "Begründe …"

### Stufe 3 — Transfer / Sachaufgabe (20 %)
Übertragung auf neuen Kontext, mehrschrittige Sachaufgaben, Beweise.
- "Modelliere folgenden Sachverhalt …"
- "Beweise …"
- "Diskutiere …"

## Skizzen

**Standard:** Jede Aufgabe, deren Sachverhalt visuell ist, bekommt eine TikZ-Skizze in der Aufgabe.
- Vektorgeometrie → Vektoren mit Pfeilen
- Mechanik → Kraftpfeile, Skizze des physikalischen Aufbaus
- Funktionen → Koordinatensystem mit Graphen
- Stochastik → Baumdiagramm, Histogramm
- Chemie → Strukturformel oder Versuchsaufbau

Skizzen in der Aufgabe sind **schematisch** und führen nicht zur Lösung. Skizzen in der Lösung sind **vollständig** mit allen Beschriftungen.

## Lösungsstruktur

Jede Lösung folgt diesem Schema:

```
Aufgabe N — Lösung

1. Gegeben / Gesucht / Ansatz (kurz)
2. Schritt 1 mit Erläuterung
3. Schritt 2 mit Erläuterung
   ...
4. Endergebnis eingerahmt: \ergebnis{x = 3{,}45}
5. Antwortsatz im Sachzusammenhang (bei Sachaufgaben)
```

### Was zu vermeiden ist
- ❌ Nur Endergebnis ohne Rechenweg
- ❌ Sprünge über mehrere Umformungen ("dann ergibt sich offensichtlich …")
- ❌ Unkommentierte Formelanwendung
- ❌ Endergebnis ohne Einheit
- ❌ Antwortsatz vergessen bei Sachaufgaben

### Was Standard ist
- ✅ Jede Umformung kommentiert ("durch Quadrieren", "wegen Symmetrie", "mit der dritten binomischen Formel")
- ✅ Zwischenergebnisse hervorgehoben oder explizit benannt
- ✅ Bei Fallunterscheidungen: Fälle nummerieren
- ✅ Bei Einsetzungen: Variable, dann eingesetzte Werte
- ✅ Endergebnis mit `\ergebnis{...}` einrahmen, Einheit nicht vergessen

## Mischung der Aufgabentypen

Wenn eine Aufgabensammlung mehrere Fälle/Untertypen abdeckt (z. B. Urnenmodell mit 4 Fällen):
- **Nicht** alle Aufgaben zum gleichen Fall hintereinander
- **Stattdessen:** Aufgaben **gemischt** anordnen, damit der Schüler erkennen muss, welcher Fall vorliegt
- Mischung deterministisch (mit Seed) generieren, damit Reproduzierbarkeit gegeben ist
- In der Lösung: explizit benennen, welcher Fall vorliegt und warum

## Querverweise

Aufgaben mit `\label{aufg:N}` markieren, in Lösungen mit `\ref{aufg:N}` referenzieren. Im Lösungsteil zusätzlich Seitenzahl der Aufgabe einblenden:
```latex
\section*{Lösung zu Aufgabe \ref{aufg:5} (S.~\pageref{aufg:5})}
```

## Klausurtypische Aufgaben

Wenn der Auftrag "klausurtypisch" lautet, gelten zusätzliche Regeln:
- **Punkteverteilung** angeben (z. B. "(4 P.)") an jeder Aufgabe
- **Bearbeitungszeit** schätzen und vermerken
- **Hilfsmittel** angeben ("ohne Hilfsmittel" / "mit Taschenrechner" / "mit Formelsammlung")
- **Aufgabenformat** an typische Klausuren anlehnen: in Teilaufgaben (a), (b), (c) gegliedert
- Lösung enthält **Punkteverteilung** auf die Teilschritte

## Beispiel-Layout einer Aufgabe

```latex
\begin{aufgabe}[Aufgabe 7 \hfill (5 P.)]
\label{aufg:7}
Gegeben sei die Gerade $g \colon \vec{x} = \begin{pmatrix} 1 \\ 0 \\ 2 \end{pmatrix}
+ t \cdot \begin{pmatrix} 1 \\ 1 \\ 0 \end{pmatrix}$
und der Punkt $P(3 \mid 2 \mid 5)$.

\begin{enumerate}[label=(\alph*)]
  \item Bestimme den Lotfußpunkt von $P$ auf $g$. \hfill (3 P.)
  \item Berechne den Abstand von $P$ zu $g$. \hfill (2 P.)
\end{enumerate}

\begin{center}
\begin{tikzpicture}[scale=0.8]
  % schematische Skizze
\end{tikzpicture}
\end{center}
\end{aufgabe}
```

Und die zugehörige Lösung:

```latex
\begin{loesung}[Lösung zu Aufgabe \ref{aufg:7}]
\textbf{(a)} Lotfußpunkt: ...

Setze den Verbindungsvektor $\vec{PQ}$ mit $Q \in g$ orthogonal zum Richtungsvektor:
\[
  \vec{PQ} \cdot \begin{pmatrix} 1 \\ 1 \\ 0 \end{pmatrix} = 0
\]
... [Schritt-für-Schritt] ...

\ergebnis{F = (2 \mid 1 \mid 2)}

\textbf{(b)} Abstand:
\[
  d = \lvert \vec{PF} \rvert = \sqrt{1 + 1 + 9} = \sqrt{11}
\]

\ergebnis{d \approx \SI{3{,}32}{LE}}
\end{loesung}
```
