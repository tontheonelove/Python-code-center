# Library Installation Steps
- First, you need to install the librouteros library using the command

```
pip install librouteros
```

# ตัวอย่างโค้ด Python สำหรับเชื่อมต่อ MikroTik API:

```
from librouteros import connect

## กำหนดข้อมูลการเชื่อมต่อ
HOST = '0.0.0.0'  # IP ของ MikroTik Router
USER = 'admin'          # ชื่อผู้ใช้
PASSWORD = 'password'  # รหัสผ่าน

## เชื่อมต่อกับ MikroTik Router
api = connect(username=USER, password=PASSWORD, host=HOST)

## ตรวจสอบข้อมูลจาก Router
def get_system_interface():
    interface = api('/interface/print')
    return interface

## เรียกดูข้อมูลจาก MikroTik
interface = get_system_interface()
for interface in interface:
    print(interface)
```
