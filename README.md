# 🔥 Sequence-to-Sequence Event Prediction

## Project Summary

Imagine watching a series of events and trying to guess what might happen next. Earlier events can give clues about later ones. This project uses a deep learning model to learn from event sequences and predict future events. The challenge is learning how the order of events changes what may happen.

I prepared event sequences, trained the model, and compared different settings to test its predictions. For example, a simulator can produce a chain of events, and the model can estimate what may follow. I learned how to work with time-based data, tune models, and evaluate them carefully instead of trusting training results alone.

---

## Technical Documentation


🚀 **An advanced deep learning-based sequence-to-sequence (Seq2Seq) model for event prediction with cross-validation, hyperparameter tuning, and robust evaluation.**

🔗 **GitHub Repository:** [Sequence-to-Sequence Event Prediction](https://github.com/ShalinVachheta017/seq2seq-event-prediction/tree/main)

---

## 🎯 Objective / Goal
The primary goal of this project is to build a reliable **sequence-to-sequence (Seq2Seq)** framework that can predict future event sequences from historical event data.

This work focuses on:
- Learning temporal patterns in sequential data using an encoder-decoder architecture.
- Improving generalization through cross-validation and configuration search.
- Selecting and validating the best-performing model on unseen test data.

---

## 🧠 Methodology / Approach
The project follows a structured training-and-evaluation workflow:

1. **Data Loading & Preprocessing**
   - Reads event sequence data from `Events.csv`.
   - Prepares data for sequence modeling and K-fold splitting.

2. **Model Architecture**
   - Uses a **Bidirectional LSTM Encoder-Decoder** architecture.
   - Includes teacher forcing during training (configured ratio).

3. **K-Fold Cross-Validation**
   - Trains across multiple folds to reduce overfitting and increase robustness.

4. **Hyperparameter Tuning**
   - Searches over configurable settings (hidden sizes, layers, epochs, learning rates, etc.) from `config.yaml`.

5. **Post-Training Analysis**
   - Compares trained configurations and identifies the best model using validation metrics.

6. **Retraining & Final Evaluation**
   - Retrains the selected best configuration.
   - Evaluates final performance on test data and stores results.

---

## 📌 Key Findings
Based on the repository’s workflow and outputs:

- The **multi-stage pipeline** (train → analyze → retrain) improves model selection reliability.
- **Cross-validation + hyperparameter tuning** provides better confidence in model robustness versus single-run training.
- The project records both intermediate and final results in structured files:
  - `all_jobs_results.csv` for training-stage outcomes.
  - `final_test_results.csv` for final test performance.
- The architecture is well-suited for sequence forecasting tasks where event order and temporal context matter.

> Note: Numerical results depend on dataset version and chosen configuration in `config.yaml`.

---

## ✅ Summary
This repository presents a complete and reproducible Seq2Seq event prediction pipeline using LSTM-based encoder-decoder networks.

In summary, it delivers:
- A configurable deep learning training framework.
- Robust model selection through K-fold validation and post-analysis.
- Final retraining and performance reporting for unbiased test evaluation.

The project can serve as a strong baseline for future extensions such as attention mechanisms, transformer-based sequence models, or richer event feature engineering.

---

## 🗂 Project Structure
```text
📂 Sequence-to-Sequence-Event-Prediction
├── main.py               # Runs the full training pipeline
├── train.py              # Training & validation functions
├── post_analysis.py      # Selects the best model after training
├── retrain.py            # Retrains the best model and evaluates on test set
├── model_definition.py   # LSTM-based encoder-decoder model
├── data_loader.py        # Data preprocessing & k-fold dataset preparation
├── metrics.py            # Custom loss & evaluation metrics
├── utils.py              # Utility functions (logging, config handling, plotting)
├── config.yaml           # Configuration settings for training jobs
├── Events.csv            # Dataset file (input)
└── README.md             # Project documentation
```

---

## ⚙️ Installation & Setup

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/ShalinVachheta017/seq2seq-event-prediction.git
cd seq2seq-event-prediction
```

### 2️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

### 3️⃣ Ensure Correct Folder Structure
Ensure that `Events.csv` (dataset file) is present in the root directory.

---

## 🚀 How to Train the Model

Run the full training pipeline:
```bash
python main.py
```

This script:
1. Loads data from `Events.csv`
2. Trains the model with multiple hyperparameter combinations (from `config.yaml`)
3. Saves logs and outputs into `./logs` and `./outputs`

---

## 📊 Post-Training Analysis
Select the best-performing model after training:
```bash
python post_analysis.py
```

---

## 🔄 Retraining and Final Evaluation
Retrain the selected best model and evaluate on test data:
```bash
python retrain.py
```

Outputs are saved to `final_test_results.csv`.

---

## 🧩 Customization
To modify hyperparameters (batch size, epochs, learning rate, etc.), edit `config.yaml`.

Example:
```yaml
general:
  batch_size: 8
  epochs_list: [40, 80, 100, 120]
  learning_rates: [0.001]
  hidden_sizes: [64, 128, 256]
  num_layers_options: [1, 2, 3]
  bidirectional_options: [true, false]
```

---

## 📈 Performance Metrics
The model is evaluated using:
- Cross-Entropy Loss (training and validation)
- Accuracy and Coverage (post-training and final evaluation)

Stored result files:
- `all_jobs_results.csv` (training phase)
- `final_test_results.csv` (final evaluation)

---

## 🏗 Model Architecture
```text
Encoder (BiLSTM) → Decoder (LSTM) → Fully Connected Layer
```

Teacher forcing is used during training.

---

## 🤝 Contributing
Feel free to **fork**, open issues, and submit pull requests.

---

## 📜 License
This project is open-source under the **MIT License**.
