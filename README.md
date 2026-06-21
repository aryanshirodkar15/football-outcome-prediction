# Football Match Outcome Prediction

An exploratory machine-learning project that turns historical football match results into rolling form features and trains a random forest classifier to predict home wins, draws, and away wins.

## Project overview

The notebook walks through the full early-stage modeling workflow:

- Load and combine season-level match data
- Clean dates, results, and duplicate rows
- Build team-level rolling form features
- Compare home and away attacking and defensive form
- Train a `RandomForestClassifier`
- Evaluate predictions with accuracy and a confusion matrix

## Features

The model uses recent form without leaking the current match result:

- Average goals scored over the previous five matches
- Average goals conceded over the previous five matches
- Wins in the previous five matches
- Home-versus-away differences for each form metric

## Repository structure

```text
.
├── data/
│   ├── raw/                         # Season-level source files
│   └── combined_ucl_matches.csv     # Combined modeling dataset
├── notebooks/
│   └── 01_data_exploration.ipynb    # Cleaning, features, training, evaluation
└── requirements.txt
```

## Run locally

```bash
git clone https://github.com/aryanshirodkar15/football-outcome-prediction.git
cd football-outcome-prediction
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Open `notebooks/01_data_exploration.ipynb` and run the cells from top to bottom.

## Modeling note

The notebook uses a chronological split for its final evaluation, which better reflects real prediction conditions than randomly shuffling future matches into the training set.

## Roadmap

- Add tournament and season validation
- Compare random forest performance with logistic regression and gradient boosting
- Add probability calibration and richer evaluation metrics
- Package feature engineering into reusable Python modules
- Create an interactive prediction dashboard

## License

This project is available under the MIT License.
