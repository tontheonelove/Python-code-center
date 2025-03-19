## Check top 10 crypto price 


- 1.Install the requests library if it is not already installed
```
pip install requests
```


- 2. โค้ด Python สำหรับดึงข้อมูล
```
import requests

# URL ของ API จาก CoinGecko
url = "https://api.coingecko.com/api/v3/coins/markets"

# ตั้งค่าพารามิเตอร์การดึงข้อมูล
params = {
    'vs_currency': 'usd',  # ใช้ USD เป็นสกุลเงิน
    'order': 'market_cap_desc',  # เรียงตาม market cap
    'per_page': 10,  # จำกัดแค่ 10 เหรียญ
    'page': 1  # หน้าแรก
}

# ส่งคำขอ GET ไปยัง API
response = requests.get(url, params=params)

# ตรวจสอบสถานะการตอบกลับ
if response.status_code == 200:
    coins = response.json()  # แปลงข้อมูล JSON
    print("10 เหรียญ Crypto ที่มาใหม่:")
    for idx, coin in enumerate(coins, 1):
        print(f"{idx}. {coin['name']} ({coin['symbol']}) - ราคา: ${coin['current_price']}")
else:
    print("ไม่สามารถดึงข้อมูลจาก CoinGecko ได้")

```

### Description:
- vs_currency='usd': Set the currency to be displayed as USD
- order='market_cap_desc': Sort by market cap
- per_page=10: Display the first 10 coins
- page=1: The first page we want to fetch data
- This code will fetch data from the CoinGecko API and display the coin name, symbol, and current price of the first 10 coins that have arrived on the market.
