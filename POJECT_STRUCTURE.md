# Project Structure

A consistent structure makes your work reproducible and shareable. This document aims to define a standard approach to published projects.

---

## Standard Layout

```
project-name/
├── README.md
├── requirements.txt
├── .gitignore
├── .env                  # Credentials such as API keys (never commit)
├── data/
│   ├── raw/              # Original, immutable
│   └── processed/        # Cleaned, transformed
├── notebooks/
│   ├── 01-exploration.ipynb
│   ├── 02-analysis.ipynb
│   └── 03-modeling.ipynb
├── src/
│   ├── __init__.py
│   ├── data.py
│   ├── features.py
│   └── models.py
└── results/
    ├── figures/
    └── tables/
```

---

## Key Files

### README.md

Every project needs one:

```markdown
# Project Title

Brief description of what this project does.

## Data

Source, time period, size.

## Methods

Your approach in 2-3 sentences.

## Results

Key findings.

## Reproduction

python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python src/main.py

## Author

Your Name (@github-handle)
```

### requirements.txt

Pin versions for reproducibility:

```
pandas==2.2.0
numpy==1.26.3
scikit-learn==1.4.0
matplotlib==3.8.2
statsmodels==0.14.1
python-dotenv==1.0.0
```

Generate from your environment:
```bash
pip freeze > requirements.txt
```

### .gitignore

```gitignore
# Python
__pycache__/
*.py[cod]
.venv/
.env

# Jupyter
.ipynb_checkpoints/

# Data (too large for Git)
data/raw/*
data/processed/*
!data/*/.gitkeep

# Results (regenerate from code)
results/*/*
!results/*/.gitkeep

# IDE
.vscode/
.idea/

# OS
.DS_Store
```

---

## Conventions

### Data

Never modify raw data. Your pipeline:

```
data/raw/ (immutable) > script > data/processed/
```

For large datasets, don't commit them. Add instructions in README for how to obtain them, or reference PQE databases.

### Notebooks

Number them to show workflow order:

```
01-exploration.ipynb
02-feature-engineering.ipynb
03-modeling.ipynb
04-results.ipynb
```

Clear outputs before committing. Move reusable code to `src/` (the source code folder).

### src/

Production code lives here. Example `src/data.py`:

```python
"""Data loading and processing."""

import pandas as pd
from pathlib import Path

DATA_DIR = Path(__file__).parent.parent / "data"


def load_raw(filename: str) -> pd.DataFrame:
    """Load from data/raw/."""
    return pd.read_csv(DATA_DIR / "raw" / filename, parse_dates=["date"])


def process(df: pd.DataFrame) -> pd.DataFrame:
    """Clean and transform."""
    df = df.copy()
    df = df.dropna(subset=["price"])
    df["returns"] = df["price"].pct_change()
    return df
```

---

## Quick Setup

```bash
mkdir my-project && cd my-project
mkdir -p data/{raw,processed} notebooks src results/{figures,tables}
touch README.md requirements.txt .gitignore .env
touch data/raw/.gitkeep data/processed/.gitkeep
touch results/figures/.gitkeep results/tables/.gitkeep
touch src/__init__.py
git init
git add .
git commit -m "Initial structure"
```

The `.gitkeep` files preserve empty directories in Git.
