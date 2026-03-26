# LSTM Stock Prediction

A machine learning project using Long Short-Term Memory (LSTM) networks to predict stock price movements.

## Project Structure

- `main.py`: Core script for data preprocessing, model training, and evaluation.
- `MicrosoftStock.csv`: Historical stock price data used for training.
- `requirements.txt`: Necessary libraries (TensorFlow/Keras, Pandas, NumPy, etc.).

## Methodology
- **Data Preprocessing**: Scaling and windowing historical price data.
- **Model**: Sequential LSTM neural network built with Keras.
- **Evaluation**: Visualizing predictions against actual historical trends.

## Getting Started

1.  **Install Dependencies**:
    ```bash
    pip install -r requirements.txt
    ```
2.  **Run the Prediction**:
    ```bash
    python main.py
    ```
