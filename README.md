import re
import random
import string
import hashlib

common_passwords = ["123456", "password", "admin", "hello123", "qwerty"]
password = input("Enter Your Password: ")

score = 0

print("\n----- Password Analysis -----")
if len(password) >= 8:
    score += 1
else:
    print("❌ Password should contain at least 8 characters")
if re.search("[A-Z]", password):
    score += 1
else:
    print("❌ Add uppercase letters")
if re.search("[a-z]", password):
    score += 1
else:
    print("❌ Add lowercase letters")
if re.search("[0-9]", password):
    score += 1
else:
    print("❌ Add numbers")
if re.search("[@#$%^&*!]", password):
    score += 1
else:
    print("❌ Add special characters")
if password in common_passwords:
    print("❌ This is a commonly used password")
else:
    score += 1
print("\n----- Password Strength -----")

if score <= 2:
    print("🔴 Weak Password")
elif score <= 4:
    print("🟠 Medium Password")
else:
    print("🟢 Strong Password")
print("\n----- Suggested Strong Password -----")

characters = string.ascii_letters + string.digits + "@#$%^&*"

suggested_password = ''.join(random.choice(characters) for i in range(12))

print("Suggested Password:", suggested_password)
print("\n----- Encrypted Password (SHA-256 Hash) -----")

hashed_password = hashlib.sha256(password.encode()).hexdigest()

print(hashed_password)
