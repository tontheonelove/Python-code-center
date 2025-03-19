## Create Random Password 10 Digit

`````
import random
import string

# ฟังก์ชันเพื่อสร้างรหัส 16 หลักที่ไม่ซ้ำกัน
def generate_code():
    characters = string.ascii_letters + string.digits + string.punctuation
    return ''.join(random.choice(characters) for _ in range(16))

# สร้างรหัส 10 ชุดที่ไม่ซ้ำกัน
def generate_unique_codes(num_codes):
    codes = set()
    while len(codes) < num_codes:
        code = generate_code()
        codes.add(code)
    return list(codes)

# สร้างรหัส 10 ชุด
unique_codes = generate_unique_codes(10)

# แสดงผล
for code in unique_codes:
    print(code)
`````
