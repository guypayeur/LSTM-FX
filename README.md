# Pragmatic Deep Learning Model for Forex Forecasting
This is the companion code to [Pragmatic Deep Learning Model for Forex Forecasting](https://medium.com/@AdamTibi/pragmatic-deep-learning-model-for-forex-forecasting-569aae6d4a1a). So, if you want to understand the intention of the code, I highly recommend reading the article series first.

You can also see the content of this page [visually explained on YouTube](https://youtu.be/bMKVVXgxmI4).

Below are the instructions to setting up the environment and running the Jupyter Notebook files.

## Setting Up The Environment
The model training and prediction have been tested on both Ubuntu Linux 20.04 and Windows 10 and both work as expected.
To prepare your machine to run the code, follow these steps:
- Install Conda or update your Conda installation to the latest
- Make sure you have the latest Nvidia driver if you are planning to use the GPU. On Windows, the latest version of Nvidia driver was failing on some machines and the solution was to revert back to version 431.86, so keep this in mind. The details of installing TensorFlow can be found here: [Official TensorFlow GPU support for Nvidia](https://www.tensorflow.org/install/gpu)
- Execute the next lines on your console:
```bash
conda create --name tf python==3.8.* ipython jupyter pandas numpy scikit-learn matplotlib flask
conda activate tf
```
I chose to install TensorFlow 2.3 as it has some solved bugs that hit me with earlier versions. Unfortunately, this version was not available from Conda which had TensorFlow 2.1, so I had to use pip:
```bash
pip install tensorflow-gpu==2.3
```
N.B. Keras became part of TensorFlow from v2, no need to install it separately.
## Files Structure
```
│ LICENSE                       # The code licence 
│ README.md                     # This Readme file
|
├─LSTM-FX-Train-Test            # Directory of the Training and Testing of Model
| │   common_variables.py       # Configures your model before training and testing
| │   multi_pred_model.ipynb    # Multiple predictions of more than one unit
| │   prep_and_split.ipynb      # Prepares your data and splits it into multiple CSVs
| │   README.md                 # Read me for the training and testing
| │   test_model.ipynb          # Tests your trained model
| │   time_series.py            # Utility reusable functions 
| │   train_model.ipynb         # Trains your model
| │
| ├───data                      # storage direcotry for the CSV
| │
| ├───models                    # Contains the trained models
| │   └───gbpusd-32-256-14      # Sample trained model
| │
| └───scalers                   # Contains the scalers used in the model training
|         gbpusd-32-256-14.bin  # Sample scaler associated with the model
|
├─LSTM-FX-CTrader-Client        # Directory of the client code
│     MLBot.cs                  # Sample bot C# code
│     README.md                 # Read me for the CTrader Client
|
└─LSTM-FX-Prediction-Server     # Directory of the Web Server
  │   main.py                   # The web server loading file
  │   README.md                 # Read me for the Prediction server
  │
  └───Models                    # Directory of the ML Models 
      │   gbpusd-32-256-14.bin  # Sample MinMax Scaler
      │
      └───gbpusd-32-256-14      # Directory of Sample LSTM Model 
```
## Tools
I used Juypter Notebook from within Visual Studio Code for Windows. And I have also tried with Linux (Ubuntu 20.04) and both worked in the same way.
## Training and Testing Your Model
[LSTM-FX-Train-Test](LSTM-FX-Train-Test/README.md)
## Backtesting Your Trading Strategy
[LSTM-FX-Prediction-Server](LSTM-FX-Prediction-Server/README.md)
## Disclaimer
These stories are meant as a research on the capabilities of deep learning and are not meant to provide any financial or trading advice. Do not use this research and/or code with real money.
## Licence
This repository and the code are licenced under the MIT licence, please check the licence before attempting to use the code.