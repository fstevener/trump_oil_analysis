# Trump Tweets vs Oil Price Analysis

## Goal
Investigate whether Donald Trump’s tweets influence oil prices.

## Methods
- Time series analysis
- Sentiment analysis
- Regression models

## Setup
conda env create -f environment.yml
Rscript -e "renv::restore()"

## Pipeline
1. Data collection (Python)
2. Preprocessing (Python)
3. Analysis (R/Python)
4. Visualization (R)

## Authors

| Sprache | Dependency-System      |
| ------- | ---------------------- |
| Python  | pip + requirements.txt |
| R       | renv + renv.lock       |


wie gehe ich jetzt im laufe des projeketes vor wenn ich neue pakete benötige

Sehr gute Frage – genau das ist der Punkt, an dem viele Projekte chaotisch werden, wenn man es nicht sauber regelt.

Ich gebe dir jetzt den klaren Workflow für euren gesamten Projektverlauf mit renv + Python venv, damit ihr später keinen Dependency-Stress bekommt.

🧠 Grundprinzip (wichtig verstehen)

In R mit renv gilt:
👉 Installieren + Snapshot sind zwei getrennte Schritte

🟢 STANDARD WORKFLOW (immer gleich im Projekt)
📌 Fall: Du brauchst ein neues R-Paket
1. IM R TERMINAL installieren
install.packages("neues_paket")

oder mehrere:

install.packages(c("paket1", "paket2"))
2. Danach IMMER snapshotten
renv::snapshot()

👉 Das schreibt die Versionen in renv.lock

3. fertig
🧠 Was passiert dabei?
install.packages() → installiert lokal im Projekt
renv::snapshot() → “speichert Zustand für Team”
👥 Was passiert bei euren Teamkollegen?

Wenn jemand den Code zieht:

renv::restore()

👉 und alles ist exakt identisch

⚠️ WICHTIGE REGELN (sehr wichtig für euer Projekt)
❌ NICHT tun:
Pakete in Scripts installieren
install.packages("ggplot2")  # ❌ falsch im Script
❌ NICHT vergessen:
snapshot nach Installation
❌ NICHT global installieren:
alles gehört ins Projekt
🧭 GUTER PROJEKT-ABLAUF (REAL LIFE)
Phase 1: Exploration
du installierst öfter neue Pakete
oft snapshot()
Phase 2: Stabilisierung
kaum neue Pakete
nur noch restore() bei neuen Leuten
Phase 3: Abgabe
lockfile ist fix
keine Änderungen mehr
🐍 UND WIE PASST PYTHON DA REIN?

Python läuft parallel:

Python Workflow:
pip install neue_lib

Dann:

pip freeze > requirements.txt

👉 oder (besser bei euch):

einmal sauber requirements.txt pflegen
nicht ständig freeze überschreiben
🔁 KOMPLETTE MERKREGEL FÜR EUCH
R (renv)
install.packages() → renv::snapshot()
Python (venv)
pip install → requirements.txt aktualisieren (manuell)


Python (raw data)
   ↓
data/processed/merged.csv
   ↓
R scripts lesen CSV
   ↓
results/figures + tables


oil-trump-tweets/
│
├── README.md
├── .gitignore
├── requirements.txt          # Python dependencies
│
├── data/
│   ├── raw/                  # unveränderte Daten (Tweets, Oil)
│   ├── processed/            # zusammengeführte / bereinigte Daten
│
├── python/
│   ├── src/
│   │   ├── data_collection.py
│   │   ├── preprocessing.py
│   │   ├── analysis.py
│   │
│   └── notebooks/
│       └── exploration.ipynb
│
├── r/
│   ├── scripts/
│   │   ├── analysis.R
│   │   ├── plots.R
│   │
│   ├── renv/                 # renv environment (automatisch erstellt)
│   ├── renv.lock
│   ├── .Rprofile
│
├── results/
│   ├── figures/              # Plots für Präsentation
│   ├── tables/              # Tabellen / Regression outputs
│
├── docs/
│   └── project_plan.md
│
└── .venv/                    # Python environment (NICHT committen)