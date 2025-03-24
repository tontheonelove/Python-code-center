`````
import random
import string

def generate_username(length=8):
    # รวมตัวอักษรพิมพ์เล็ก พิมพ์ใหญ่ และตัวเลข
    characters = string.ascii_lowercase + string.ascii_uppercase + string.digits
    # สร้าง username โดยการสุ่มตัวอักษรจาก characters
    username = ''.join(random.choice(characters) for _ in range(length))
    return username

# ใช้ set เพื่อป้องกันการซ้ำ
usernames = set()
while len(usernames) < 10:
    usernames.add(generate_username())

# แสดงผลลัพธ์
for i, username in enumerate(usernames, 1):
    print(f"Username {i}: {username}")

`````
