# Datastream-Project

This project has been realized by Jean Pachebat, Tom Reppelin and Paul Fayard. 

The goal is to test some online learning models to try to predict the future value of several cryptocurrencies (BTC, ETH, ...).

## ⚡️ Quickstart

First run

```sh
pip install -r requirements.txt
```

To get our features and the true value of the crypto in real-time, we use Kafka.
The producer will realize requests on the Binance API (see https://binance-docs.github.io/apidocs/spot/en/#change-log) and will write the obtained json file in a topic called binance-topic. You must create this topic before running the code. 
Then run 

```sh
python producer.py
```

The script consumer.py do several things. First, the Kafka consumer read the json wrote in the binance-topic, then it creates some features, and eventually, a HoeffdingTreeRegressor try to predict the value of the crypto.
The predicted value is then compared to the true value. The results are saved in a csv file : csv_name.csv
Just run 

```sh
python consumer.py csv_name
```

You can plot an animation with your predictions and the true values by running 

```sh
python animation.py csv_name coin_name
```

Last, the notebook present other experiments : online model tunning, comparison batch-online learning, time-series forecasting with SNARIMAX, ...
