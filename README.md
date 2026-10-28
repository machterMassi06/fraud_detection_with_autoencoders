# Credit Card Fraud Detection with an Autoencoder

This project explores fraudulent transaction detection as a semi-supervised
anomaly detection problem. The autoencoder is trained on legitimate (genuine/normal)
transactions; a high reconstruction error indicates a potentially fraudulent
transaction.

## Contents

- [`anomaly_detection_with_autoencoders.ipynb`](./anomaly_detection_with_autoencoders.ipynb): data exploration, preprocessing, model training, and evaluation.
- [`inference_simulation.ipynb`](./inference_simulation.ipynb): loads the trained weights and scores an example transaction.

## Dataset

The notebook downloads the `card-transdata` dataset with KaggleHub
(`elakiyasekar/card-transdata`). It contains transaction features and the
`fraud` target. An internet connection is required to download it.

## Installation and usage

Install the dependencies in a Python environment:

```bash
python -m pip install -r requirements.txt
```

Then open the notebook in Jupyter or VS Code and run its cells in order. The
notebook uses the `card_transdata.csv` file downloaded by KaggleHub.

To run the inference simulation, first run the training notebook and ensure
`ae_anomaly.weights.h5` is in the inference notebook's working directory. The
inference input must follow the training feature order and preprocessing
(standardized numeric features and binary features kept as 0/1). The training
notebook does not persist the fitted scaler or a production-calibrated
threshold; the inference notebook therefore reports a reconstruction score
unless a suitable threshold is supplied.