# Fachspezifika — Pakete und Konventionen

## Mathematik

### Pakete (zusätzlich zur Standardpräambel)
```latex
\usepackage{amsmath, amssymb, amsthm, mathtools}
\usepackage{cancel}                  % \cancel für Kürzen
\usepackage{tikz}
\usepackage{pgfplots}
\pgfplotsset{compat=1.18}
\usetikzlibrary{calc, intersections, angles, quotes, 3d, arrows.meta}
```

### Notation
- Vektoren: `\vec{a}` (in Präambel auf Fettdruck umgestellt: `\boldsymbol{a}`)
- Spaltenvektoren: `\begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix}`
- Skalarprodukt: `\vec{a} \cdot \vec{b}`
- Beträge: `\lvert \vec{a} \rvert` oder `\|\vec{a}\|`
- Mengen: `\R, \N, \Z, \Q` (in Präambel als Makros)
- Funktionen: `f \colon D \to W`, `x \mapsto f(x)`
- Logarithmen: `\ln, \log`, in Basis: `\log_{10}`

### Standardskizzen mit TikZ
- **Kartesisches Koordinatensystem 2D:** mit `pgfplots` als `axis` mit `axis lines=middle`
- **Vektorzeichnung:** `\draw[->,thick] (0,0) -- (3,2) node[midway,above]{$\vec{v}$};`
- **3D-Achsen:** `\begin{tikzpicture}[x={(1cm,0cm)}, y={(0.5cm,0.5cm)}, z={(0cm,1cm)}]`
- **Funktionsgraphen:** `pgfplots` mit `\addplot[...]{x^2 - 2*x + 1};`
- **Wahrscheinlichkeitsbäume:** TikZ mit Tree-Layout

### Typische Inhalte mit Beispiel-Setup
- **Binomialverteilung:** Histogramme mit `\addplot+[ybar interval]`
- **Geraden in ℝ³:** Kreuzungspunktrechnung, Lotfußpunkt
- **Beweise mit Vektoren:** Mittelpunktsatz, Strahlensätze, Dreiecksungleichung

## Physik

### Pakete
```latex
\usepackage{siunitx}                 % \SI{9{,}81}{\metre\per\second\squared}
\usepackage{tikz}
\usepackage{pgfplots}
\usetikzlibrary{patterns, decorations.pathreplacing, arrows.meta}
% Optional für Schaltungen:
% \usepackage{circuitikz}
```

### Konventionen
- **Einheiten:** Immer mit `siunitx`: `\SI{9{,}81}{\metre\per\second\squared}`
- **Dezimalkomma:** Konsequent Komma (`g = \SI{9{,}81}{...}`)
- **Vektoren:** Fettdruck (Geschwindigkeit `\vec{v}`, Kraft `\vec{F}`)
- **Indizes:** physikalisch sinnvoll (`E_\text{kin}`, `E_\text{pot}`, `F_\text{N}` für Normalkraft)
- **Konstanten:** mit Unsicherheit, wenn relevant (`g = \SI{9{,}81}{\metre\per\second\squared}`)

### Standardskizzen mit TikZ
- **Schiefe Ebene:** Dreieck mit Winkel α, Klotz darauf, Kraftpfeile (Hangabtriebs-, Normalkraft, Reibung)
- **Wurfparabel:** `pgfplots` mit `domain=0:tmax`, Komponenten v_x, v_y einzeichnen
- **Federpendel:** Schraubenlinie mit `decorations.pathreplacing` oder Pattern
- **Stromkreise:** `circuitikz` (separat zu installieren, aber standardmäßig in TeXLive)
- **s-t-, v-t-, a-t-Diagramme:** Drei nebeneinander mit `pgfplots`

### Standard-Herleitungen (sollten im Skript-Teil stehen)
- Weg-Zeit-Gesetz aus a = const (drei Methoden: Integration, Diagrammfläche, kinematische Mittelung)
- Energieerhaltung beim freien Fall (E_pot → E_kin)
- Zentripetalkraft über ähnliche Dreiecke
- Elastischer Stoß: 5-Schritt-algebraische Herleitung mit dritter binomischer Formel
- Kräftezerlegung an der schiefen Ebene mit Stufenwinkelsatz

## Chemie

### Pakete
```latex
\usepackage[version=4]{mhchem}       % Reaktionsgleichungen: \ce{H2O}, \ce{CH3-CH2-OH}
\usepackage{chemfig}                 % Strukturformeln
\setatomsep{1.8em}
\setbondoffset{1pt}
\setdoublesep{0.45ex}
% Optional:
% \usepackage{chemmacros}
```

### Konventionen
- **Reaktionsgleichungen:** Immer mit `\ce{}`: `\ce{2 H2 + O2 -> 2 H2O}`
- **Reaktionspfeile:** `<=>` für Gleichgewicht, `->[<text>]` mit Bedingungen
- **Aggregatzustände:** als Index, z. B. `\ce{H2O_{(l)}}`
- **Energiebeträge:** in kJ/mol mit siunitx: `\SI{-285{,}8}{\kilo\joule\per\mole}`
- **Strukturformeln:** chemfig, Skelett-Schreibweise bei Organik bevorzugt
- **Funktionelle Gruppen:** farblich oder fett hervorheben

### Standardskizzen mit chemfig
- **Ethanol:** `\chemfig{H_3C-CH_2-OH}` oder ausführlich
- **Verzweigte Alkane:** `\chemfig{H_3C-CH(-CH_3)-CH_2-CH_3}`
- **Cyclohexan:** `\chemfig{*6(------)}`
- **Ester:** `\chemfig{R-C(=[::-60]O)(-[::60]O-R')}`
- **Zwischenmolekulare Wechselwirkungen:** punktierte Linien zwischen Molekülen mit TikZ-Overlay

### Didaktische Anker (immer einbauen)
- **Struktur-Eigenschafts-Konzept** als roter Faden
- **Donator-Akzeptor-Konzept** bei Säure/Base und Redox
- **Unterscheidung Atom/Molekül/Stoff** explizit ansprechen
- **Klausurfehler** explizit als `stolperfalle`-Box einbauen, z. B.:
  - "Wasserstoffbrücken sind keine chemischen Bindungen"
  - "Siedepunktdifferenz nicht allein durch Molekülmasse, sondern durch Art der Wechselwirkung"
  - "Sauerstoff in der OH-Gruppe nicht vergessen beim Bilanzieren der Verbrennung"

## Allgemein

### pgfplots-Standard für Funktionsgraphen
```latex
\begin{tikzpicture}
\begin{axis}[
  axis lines = middle,
  xlabel = {$x$}, ylabel = {$y$},
  xmin = -3, xmax = 3, ymin = -1, ymax = 5,
  grid = both,
  grid style = {gray!25},
  width = 10cm, height = 7cm,
]
\addplot[domain=-3:3, thick, mainblue, samples=100]{x^2};
\end{axis}
\end{tikzpicture}
```

### TikZ-Standard für geometrische Skizzen
```latex
\begin{tikzpicture}[scale=1]
\draw[->] (-1,0) -- (5,0) node[right]{$x$};
\draw[->] (0,-1) -- (0,4) node[above]{$y$};
\draw[thick, mainblue] (0,0) -- (3,2) node[midway, above left]{$\vec{a}$};
\draw[thick, exgreen] (3,2) -- (4,3) node[midway, right]{$\vec{b}$};
\end{tikzpicture}
```
