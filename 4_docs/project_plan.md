
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