``````
import random
import string

# รายการตัวอักษรและส่วนประกอบที่ใช้สร้างอีเมล
letters = string.ascii_lowercase
domains = ['gmail.com', 'hotmail.com', 'yahoo.com', 'outlook.com', 'example.com']

# ฟังก์ชันสร้างอีเมลแบบสุ่ม
def generate_random_email():
    username_length = random.randint(5, 10)  # ความยาวชื่อผู้ใช้ 5-10 ตัวอักษร
    username = ''.join(random.choice(letters) for _ in range(username_length))
    domain = random.choice(domains)
    return f"{username}@{domain}"

# สร้าง 10 อีเมล
print("10 อีเมลปลอมที่สร้างแบบสุ่ม:")
for i in range(10):
    email = generate_random_email()
    print(f"{i+1}. {email}")

``````
