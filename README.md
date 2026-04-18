 
# 📈 BTC-USD Trading Bot — XGBoost

Prédiction du prix du Bitcoin via un pipeline ML complet.

## Stack technique
- Python, XGBoost, Scikit-learn
- Feature Engineering : RSI, Volatilité, Lags
- Validation : TimeSeriesSplit (pas de look-ahead bias)
- Backtesting avec frais de transaction

## Structure
btc_trading_bot/
├── notebooks/   # Exploration & visualisation
├── src/         # Code de production
├── data/        # Données (non versionnées)
└── main.py      # Pipeline complet

## Lancement
```bash
pip install -r requirements.txt
python main.py
```