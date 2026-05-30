# 📊 Trump Tweets & Oil Price Analysis

This project analyzes the relationship between Donald Trump’s tweets and oil price movements using Python for data processing and R for statistical analysis and visualization.

---

# 🧭 Project Structure


oil-trump-tweets/
│
├── data/
│ ├── raw/ # original datasets (unchanged)
│ ├── processed/ # cleaned and merged datasets
│
├── python/
│ ├── src/ # Python scripts (data collection & preprocessing)
│ └── notebooks/ # Jupyter notebooks for exploration
│
├── r/
│ ├── scripts/ # R analysis scripts
│ ├── renv/ # R environment (auto-generated)
│ ├── renv.lock # locked R package versions
│
├── results/
│ ├── figures/ # plots for presentation
│ ├── tables/ # regression outputs / summaries
│
├── requirements.txt # Python dependencies
├── .venv/ # Python virtual environment (not tracked)
├── README.md


---

# ⚙️ Setup Instructions

## 🐍 Python Setup

### 1. Create virtual environment

```bash
python -m venv .venv
2. Activate environment

Mac/Linux:

source .venv/bin/activate

Windows:

.venv\Scripts\activate
3. Install dependencies
pip install -r requirements.txt
📊 R Setup (VSCode Terminal)
1. Start R
R
2. Set CRAN mirror (if prompted)

Choose:

0-Cloud
or
Germany (Munich)

Or manually:

options(repos = c(CRAN = "https://cloud.r-project.org"))
3. Install renv (first time only)
install.packages("renv")
4. Restore R environment
renv::restore()

This installs all required R packages from renv.lock.

🔁 Reproducibility Workflow
Python (when adding new packages)
pip install <package>
pip freeze > requirements.txt

(only when changes are finalized)

R (when adding new packages)
install.packages("<package>")
renv::snapshot()
📌 Data Pipeline Overview
Python – Data Collection
Collect Trump tweets
Download oil price data (e.g. Brent / WTI via Yahoo Finance)
Python – Preprocessing
Cleaning data
Timestamp alignment
Feature engineering
R – Analysis
Time series analysis
Correlation analysis
Lag analysis
Regression models
Outputs
Figures → results/figures/
Tables → results/tables/
🧪 Requirements
Python 3.10+
R 4.2+
VSCode recommended
Git
👥 Team Workflow
Use feature branches:
feature/data-collection
feature/preprocessing
feature/analysis
feature/visualization
main branch = stable version only
🚀 Quick Start
git clone <repo-url>
cd oil-trump-tweets

# Python setup
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt

# R setup
R
renv::restore()
📊 Goal

To investigate whether Donald Trump’s tweet activity has a measurable impact on oil price movements using statistical and time series methods.

| Sprache | Dependency-System      |
| ------- | ---------------------- |
| Python  | pip + requirements.txt |
| R       | renv + renv.lock       |


-------------------------------------


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


-----------------------------

Best Practice für dein Projekt

Da du beides verwendest:

project/
│
├── .venv/
├── requirements.txt
├── renv.lock
├── renv/
├── src/
└── ...
Neue Python-Abhängigkeit → pip freeze > requirements.txt
Neue R-Abhängigkeit → renv::snapshot()
Beides anschließend committen

Dann können Kollegen exakt dieselben Python- und R-Versionen der Pakete wiederherstellen:

pip install -r requirements.txt

und in R:

renv::restore()

Ein kleiner Hinweis: Den Ordner .venv/ committet man normalerweise nicht nach GitHub (er gehört in .gitignore). Bei renv ist es etwas anders: Die Datei renv.lock wird committet, der eigentliche Paket-Cache meist nicht. Daher lohnt es sich zu prüfen, welche renv-Dateien dein Git aktuell verfolgt.