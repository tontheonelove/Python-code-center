# Check Ip Address

## Install the library: First
```
pip install requests
```

## Python Code Here 

```
import requests

def get_ip_info(ip):
    url = f"https://ipinfo.io/{ip}/json"
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        return data
    else:
        return None

# ตัวอย่างการใช้งาน
ip_address = "202.44.53.254"  # ใส่ IP ที่ต้องการตรวจสอบ
info = get_ip_info(ip_address)

if info:
    print(f"IP Address: {info.get('ip')}")
    print(f"Hostname: {info.get('hostname')}")
    print(f"Location: {info.get('city')}, {info.get('region')}, {info.get('country')}")
    print(f"Organization: {info.get('org')}")
else:
    print("ไม่สามารถดึงข้อมูลของ IP ได้")

```


## How it works:
- This code will make a request to the ipinfo.io API to retrieve information about the specified IP. It will provide information such as location (city, region, country), hostname, and organization name.
- If you are using an IP other than 8.8.8.8, you can put it in the ip_address variable instead.
- If you want to use other APIs, such as ip-api.com, just change the URL and response accordingly.
