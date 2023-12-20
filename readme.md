# AGI.EXPERT API

## Finance Prediction Models

> The Predict Simple API allows you to initiate predictions for specific stock and crypto assets. This API is designed to be simple to use, requiring only a few parameters to generate predictions. Below, you'll find information on how to use the API, its endpoint, and sample function calls in Python.

### API Endpoint (POST)

```
http://api.agi.expert/predict_simple
```

### Parameters

 - **asset (string, required)**: The asset symbol for which you want to generate predictions.
 - **exchange (string, required)**: The exchange where the asset is traded (Stocks/Crypto). 
 - **country (string, required)**: The country associated with the asset. For crypto, put 'USA'.
 - **model (string, optional)**: The predictive model to use for generating predictions. Default is "deepQLearning". Check back for the latest models, as they are updated regularly.
 - **List of models**:
   - deepQLearning
   - XGBoost (Future)
   - CatBoost (Future)
   - doubleDeepQLearning (Future)
   - newsPDoubleDeepQLearning (Future)

### Response

The API response will include the prediction results in JSON format.
```
status: success
result: -11.951863923488109%
asset: NVDA
starttime: 2023-08-28 22:13:51.630321
```

### Usage

**Python Code Snippet**
```
import requests
import json

def request_prediction(url, payload, headers):
    response = requests.post(url, headers=headers, data=json.dumps(payload))
    task_id = response.text 
    verify(url, task_id, headers)

def verify(url, task_id, headers):
    _url = f"{url}/{task_id}"
    response = requests.get(_url, headers=headers) 
    print("Prediction Results: ", response.text)
```

### Sample Stock Payload

```
url = "http://api.agi.expert/predict_simple"

payload = {
    "exchange": "Stock",
    "asset": "AAPL",
    "country": "USA",
    "model": "deepQLearning" # optional
}

headers = {
    'api-key': 'YOUR_API_KEY',
    'Content-Type': 'application/json'
}
request_prediction(url, payload, headers)
```

### Sample Crypto Payload

```
url = "http://api.agi.expert/predict_simple"

payload = {
    "exchange": "Crypto",
    "asset": "BTC",
    "country": "USA"
}

headers = {
    'api-key': 'YOUR_API_KEY',
    'Content-Type': 'application/json'
}
request_prediction(url, payload, headers)
```

### Notes

 - Make sure to replace 'YOUR_API_KEY' with your actual API key.
 - The model parameter is optional. If not provided, the default model used will be "deepQLearning".
 - The verify function is used to check the prediction status and results after initiating a prediction.



# Training endpoints

### Convert files to Q&A

```
url = "http://api.agi.expert/convert_simple"

payload = {
    "file": "file-390303f",
    "description": "This is for python code knowledge",
    "name": "TensorFlow",
    "type": "Code", #check docs for list of types
}

headers = {
    'api-key': 'YOUR_API_KEY',
    'Content-Type': 'application/json'
}
request_prediction(url, payload, headers)
```

### Tokenize

```
url = "http://api.agi.expert/tokenize_simple"

payload = {
    "type": "word", #subword, character
    "file": "file-343093"
}

headers = {
    'api-key': 'YOUR_API_KEY',
    'Content-Type': 'application/json'
}
request_prediction(url, payload, headers)
```


### Train

```
url = "http://api.agi.expert/train_simple"

payload = {
    "trainingfile": "file-232e38",
    "validationfile": "file-383e9",
    "epochs": "5",
    "model": "WizardLM-70B-V1.0"
}

headers = {
    'api-key': 'YOUR_API_KEY',
    'Content-Type': 'application/json'
}
request_prediction(url, payload, headers)
```


# search models

```
import requests
import json

url = "http://api.agi.expert/api/search?keyword=Finance"

payload = json.dumps({})
headers = {
  'api-key': '123456789',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```



# make predictions


Finance/Prediction Models:
```
import requests
import json

url = "http://api.agi.expert/predict_simple"

payload = json.dumps({
  "exchange": "Stock",
  "timeFrame": "1hr",
  "asset": "AAPL",
  "country": "USA",
  "model": "deepQLearning"
})
headers = {
  'api-key': '123456789',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
task_id = response.text

```

get prediction results

```sh
import requests

url = f"https://api.agi.expert/predict_simple/{task_id}"

payload = {}
headers = {
  'api-key': 'bv86OrBwLQuBbReg7LAltw'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```

Art/Drawer:

RealEstate/HousePricing:

Lifestyle/Recommendations/Movies:

Psychology/Twitter-to-personality:  

# use binance to get real-time prices

```
#Defining Binance API URL
key = "https://api.binance.com/api/v3/ticker/price?symbol="
keyus = "https://api.binance.us/api/v3/ticker/price?symbol="
  
#load json
assets = json.loads('''
{
    "wbtc": {
        "binance": "BTCUSDT",
        "decimal": 8,
        "address": "0x1BFD67037B42Cf73acF2047067bd4F2C47D9BfD6"
    },
    "matic": {
        "binance": "MATICUSDT",
        "decimal": 18,
        "address": "0x2791bca1f2de4661ed88a30c99a7a9449aa84174"
    }
}
''')


asset1='wbtc'

#Access the variables for WBTC
assetbinance = assets[asset1]['binance']




#gather price
url = key+assetbinance  
data = requests.get(url)
data = data.json()
assetprice = data['price']
print(assetprice)
```
