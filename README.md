# SCT_PJCT_1
def caesar_cipher(text, shift, mode="encrypt"):
    result = ""
    
    if mode == "decrypt":
        shift = -shift 

    for char in text:
        if char.isalpha(): 
            ascii_offset = 65 if char.isupper() else 97
            new_char = chr((ord(char) - ascii_offset + shift) % 26 + ascii_offset)
            result += new_char
        else:
            result += char 

    return result


# User input section
def main():
    print("Caesar Cipher - Encrypt & Decrypt Text")
    message = input("Enter your message: ")
    shift = int(input("Enter shift value (integer): "))
    choice = input("Type 'encrypt' to encode or 'decrypt' to decode: ").strip().lower()

    if choice in ["encrypt", "decrypt"]:
        output = caesar_cipher(message, shift, mode=choice)
        print(f"\nResult ({choice}ed message): {output}\n")
    else:
        print("Invalid choice! Please enter 'encrypt' or 'decrypt'.")

if __name__ == "__main__":
    main() 
