# TODO — LSTM Stock Prediction

## Current state (verified from main.py)
- 2-layer LSTM (64 units each) → Dense(128, relu) → Dropout(0.5) → Dense(1), trained for 20 epochs, batch_size 32.
- 60-day sliding window, `StandardScaler`-scaled, 95/5 train/test split.
- Evaluation is **visual only** — the script plots predictions vs. actual close price, but never prints a number. There's no RMSE/MAE anywhere, and no validation split during `fit()` (so no loss curve to check for overfitting during training either).
- Only one stock (`MicrosoftStock.csv`) is used.

## Improvements, roughly in priority order
1. **Add a real evaluation number.** A plot that "looks close" isn't a result. Compute RMSE and MAE (and ideally directional accuracy — did it get the up/down move right, which matters more than the exact price for most real uses) and print/log them.
2. **Add a validation split to `model.fit()`** (`validation_data=(X_test, y_test)` or a slice of train) and plot the train/val loss curve. Right now there's no way to tell if 20 epochs is under/over-fitting — it's a number picked without evidence.
3. **Generalize beyond one stock.** Turn the script into a function that takes a ticker/CSV path, and run it on at least one more stock. Right now there's no way to tell if this works in general or happens to look okay on Microsoft specifically.
4. **Reconsider the scaler.** `StandardScaler` works, but `MinMaxScaler` (0-1) is the far more common choice for LSTM price data in practice — worth trying both and noting which performs better, or explaining why `StandardScaler` was chosen.
5. **Turn this into a notebook (or add real comments/markdown)** so the stages — load data, build windows, build model, train, evaluate — are legible to someone skimming it, not just someone willing to read 140 lines of script top to bottom.
6. **Pin the TensorFlow/Keras version in requirements.txt** if not already — LSTM/Keras APIs drift between versions and this is the kind of script that silently breaks on a fresh install otherwise.
