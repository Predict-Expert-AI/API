
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

url = "http://agi.expert/predict_simple"

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
