import random
import string

def generate_password(length=12, use_digits=True, use_symbols=True):
    characters = string.ascii_letters  # a-zA-Z
    if use_digits:
        characters += string.digits  # 0-9
    if use_symbols:
        characters += string.punctuation  # !@#$%^&*()...

    if not characters:
        raise ValueError("No characters selected for password generation.")

    password = ''.join(random.choice(characters) for _ in range(length))
    return password

# === CLI Interface ===
if __name__ == "__main__":
    print("Password Generator 🛡️")
    try:
        length = int(input("Enter password length (e.g., 12): "))
        use_digits = input("Include digits? (y/n): ").lower() == 'y'
        use_symbols = input("Include symbols? (y/n): ").lower() == 'y'

        password = generate_password(length, use_digits, use_symbols)
        print(f"\nGenerated Password: {password}")
    except Exception as e:
        print(f"Error: {e}")
