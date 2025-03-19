## Sample code:

```
import socket

# ฟังก์ชันในการสแกนพอร์ต
def scan_ports(target_ip):
    # พอร์ตที่จะทำการสแกน (ตั้งแต่พอร์ต 1-65535)
    open_ports = []

    for port in range(1, 65536):
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)  # กำหนดเวลาเชื่อมต่อ
        result = sock.connect_ex((target_ip, port))  # ลองเชื่อมต่อไปยังพอร์ต
        if result == 0:
            open_ports.append(port)  # ถ้าเชื่อมต่อสำเร็จ
        sock.close()

    return open_ports

# กำหนด IP เป้าหมาย
target_ip = "118.175.28.187"  # ใส่ IP เป้าหมายที่ต้องการสแกน

# เรียกใช้ฟังก์ชัน
open_ports = scan_ports(target_ip)

# แสดงผลลัพธ์
if open_ports:
    print(f"พอร์ตที่เปิดอยู่บน IP {target_ip}: {open_ports}")
else:
    print(f"ไม่พบพอร์ตที่เปิดบน IP {target_ip}")

```
## Code Description:

- The scan_ports function gets the target IP and tests the ports from 1 to 65535 using the TCP protocol.
- Uses socket.socket to establish a TCP connection and uses connect_ex to test the connection to the port.
- If the connection is successful (result is 0), the port is added to the list of open ports.
- Displays the result of which ports are open.
- You can change the target_ip value to the IP you want to scan.
