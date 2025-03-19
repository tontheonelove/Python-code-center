# Check Bitcoin prices from 3 different exchanges: Binance, Coinbase, and Kraken.

- 1. Install required libraries: You need to install the requests library first. If it is not installed, you can install it with the command:
```
pip install requests
```
- 2. Code to check Bitcoin price from 3 exchanges: This code uses the API of Binance, Coinbase, and Kraken to compare Bitcoin price data
 
## python Code
```
import requests

# ฟังก์ชันเพื่อดึงข้อมูลราคาจาก Binance
def get_binance_price():
    url = "https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT"
    response = requests.get(url)
    data = response.json()
    return float(data['price'])

# ฟังก์ชันเพื่อดึงข้อมูลราคาจาก Coinbase
def get_coinbase_price():
    url = "https://api.coinbase.com/v2/prices/spot?currency=USD"
    response = requests.get(url)
    data = response.json()
    return float(data['data']['amount'])

# ฟังก์ชันเพื่อดึงข้อมูลราคาจาก Kraken
def get_kraken_price():
    url = "https://api.kraken.com/0/public/Ticker?pair=BTCUSD"
    response = requests.get(url)
    data = response.json()
    return float(data['result']['XXBTZUSD']['c'][0])

# ฟังก์ชันหลักในการเปรียบเทียบราคา
def compare_prices():
    binance_price = get_binance_price()
    coinbase_price = get_coinbase_price()
    kraken_price = get_kraken_price()

    print(f"Binance Price: ${binance_price}")
    print(f"Coinbase Price: ${coinbase_price}")
    print(f"Kraken Price: ${kraken_price}")

    # เปรียบเทียบราคาที่ได้
    prices = {
        "Binance": binance_price,
        "Coinbase": coinbase_price,
        "Kraken": kraken_price
    }

    # หา exchange ที่มีราคาสูงที่สุด
    highest = max(prices, key=prices.get)
    print(f"The highest price is from {highest}.")

    # หา exchange ที่มีราคาต่ำที่สุด
    lowest = min(prices, key=prices.get)
    print(f"The lowest price is from {lowest}.")

# เรียกใช้งานฟังก์ชัน
compare_prices()
```

### Description:
- Binance API: Use https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT to fetch the price of Bitcoin (BTC) against USDT (Tether), a digital dollar.
- Coinbase API: Use https://api.coinbase.com/v2/prices/spot?currency=USD to fetch the current price of Bitcoin.
- Kraken API: Use https://api.kraken.com/0/public/Ticker?pair=BTCUSD to fetch the price of Bitcoin from Kraken.
### Usage:
- This code will fetch the price of Bitcoin from all three exchanges (Binance, Coinbase, Kraken).
- It will show the price of each exchange and show which exchange has the highest and lowest price.
