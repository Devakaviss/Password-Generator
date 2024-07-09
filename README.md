# Password-Generator
import random
import string
import pyperclip

def generate_password(length, use_uppercase, use_lowercase, use_digits, use_special):
    character_set = ''
    if use_uppercase:
        character_set += string.ascii_uppercase
    if use_lowercase:
        character_set += string.ascii_lowercase
    if use_digits:
        character_set += string.digits
    if use_special:
        character_set += string.punctuation

    if not character_set:
        raise ValueError("No character types selected")

    password = ''.join(random.choice(character_set) for _ in range(length))
    return password

def main():
    print("Welcome to the Password Generator!")

    length = int(input("Enter the desired password length: "))
    use_uppercase = input("Include uppercase letters? (yes/no): ").strip().lower() == 'yes'
    use_lowercase = input("Include lowercase letters? (yes/no): ").strip().lower() == 'yes'
    use_digits = input("Include digits? (yes/no): ").strip().lower() == 'yes'
    use_special = input("Include special characters? (yes/no): ").strip().lower() == 'yes'

    try:
        password = generate_password(length, use_uppercase, use_lowercase, use_digits, use_special)
        print(f"Generated password: {password}")
        pyperclip.copy(password)
        print("Password has been copied to clipboard.")
    except ValueError as e:
        print(e)

if __name__ == "__main__":
    main()
