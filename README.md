# 📈 BTC-USD Trading Bot — XGBoost

Pipeline ML complet de prédiction de la direction du Bitcoin (BTC-USD)
avec backtesting réaliste incluant les frais de transaction.

---

## 🎯 Objectif

Prédire si le prix du BTC-USD sera **haussier ou baissier** le lendemain,
à partir de données historiques et d'indicateurs techniques.

---

## 🏗️ Architecture du projet

```
btc_trading_bot/
│
├── notebooks/
│   ├── 01_exploration.ipynb          # Analyse exploratoire des données
│   ├── 02_feature_engineering.ipynb  # Construction des features
│   ├── 03_model_xgboost.ipynb        # Entraînement et évaluation
│   └── 04_backtesting.ipynb          # Simulation de trading
│
├── data/
│   ├── btc_raw.csv                   # Données brutes OHLCV
│   ├── btc_features.csv              # Features engineered
│   ├── btc_final.csv                 # Données finales du backtest
│   ├── btc_overview.png              # Visualisation prix + volume
│   └── backtest_results.png          # ML vs Buy & Hold
│
├── requirements.txt
└── README.md
```

---

## 🔬 Stack Technique

| Outil | Usage |
|---|---|
| `Python 3.11` | Langage principal |
| `yfinance` | Collecte des données Yahoo Finance |
| `pandas / numpy` | Manipulation et calculs |
| `ta` | Indicateurs techniques (RSI) |
| `XGBoost` | Modèle de classification supervisée |
| `scikit-learn` | TimeSeriesSplit, métriques |
| `matplotlib` | Visualisations |

---

## ⚙️ Feature Engineering

| Feature | Description |
|---|---|
| `returns` | Rendement journalier en % |
| `rsi` | Relative Strength Index (14j) |
| `volatility_7` | Écart-type des rendements sur 7j |
| `volatility_30` | Écart-type des rendements sur 30j |
| `return_yesterday` | Rendement J-1 |
| `return_two_days_ago` | Rendement J-2 |
| `return_last_week` | Rendement J-5 |
| `price_vs_ma7` | Prix / Moyenne mobile 7j |
| `price_vs_ma30` | Prix / Moyenne mobile 30j |

---

## 🤖 Modélisation

- **Algorithme** : XGBoost Classifier
- **Validation** : TimeSeriesSplit (5 folds) — élimine tout look-ahead bias
- **Cible** : Classification binaire (1 = hausse demain, 0 = baisse)
- **Baseline** : 51.1% (majorité de classe)
- **Score moyen** : ~49% — résultat honnête sur un marché quasi-efficient

---

## 📊 Résultats du Backtesting

Simulation sur 1415 jours (2021-2024) avec frais de 0.1% par transaction.

| Métrique | Stratégie ML | Buy & Hold |
|---|---|---|
| Rendement total | -25.6% | +90.2% |
| Sharpe Ratio | 0.12 | 0.49 |
| Max Drawdown | -79.3% | -76.6% |
| Nb trades | 79 | 1 |

![Backtest Results](data/backtest_results.png)

---

## 💡 Conclusions & Enseignements

> Le modèle XGBoost ne parvient pas à battre la stratégie Buy & Hold
> sur le BTC-USD — ce qui est cohérent avec la théorie des marchés efficients.

**Ce que ce projet démontre :**
- ✅ Construction d'un pipeline ML complet de bout en bout
- ✅ Feature engineering sur séries temporelles financières
- ✅ Validation croisée sans look-ahead bias (TimeSeriesSplit)
- ✅ Backtesting réaliste avec frais de transaction
- ✅ Analyse honnête et critique des résultats

---

## 🚀 Lancement

```bash
git clone https://github.com/ton-username/btc-trading-bot
cd btc-trading-bot
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

---

## 📚 Références

- [XGBoost Documentation](https://xgboost.readthedocs.io/)
- [Technical Analysis Library](https://technical-analysis-library-in-python.readthedocs.io/)
- [Yahoo Finance API](https://pypi.org/project/yfinance/)