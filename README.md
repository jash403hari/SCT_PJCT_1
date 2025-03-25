# SCT_CS_1
# === CAESAR CIPHER PROGRAM ===
# This program encrypts and decrypts messages using the Caesar cipher technique.

def caesar_cipher(text, shift, mode="encrypt"):
    """
    Function to perform Caesar Cipher encryption or decryption.
    
    Parameters:
    - text (str): The input message.
    - shift (int): The number of positions to shift the letters.
    - mode (str): 'encrypt' for encoding, 'decrypt' for decoding.
    
    Returns:
    - str: The transformed message (encrypted or decrypted).
    """
    result = ""

 # Reverse shift for decryption mode
    if mode == "decrypt":
        shift = -shift  

 # Process each character in the input text
    for char in text:
        if char.isalpha():  # Check if the character is a letter
            ascii_offset = 65 if char.isupper() else 97  # Determine ASCII offset for uppercase/lowercase
            new_char = chr((ord(char) - ascii_offset + shift) % 26 + ascii_offset)  # Shift within alphabet range
            result += new_char
        else:
            result += char  # Keep non-alphabetic characters unchanged

    return result  # Return the modified text


# === USER INPUT SECTION ===
def main():
    """
    Handles user input, calls the Caesar Cipher function, and displays results.
    """
    print("\n=== Caesar Cipher - Encrypt & Decrypt Text ===")

# Get user input for message
    message = input("Enter your message: ")

# Validate shift input (must be an integer)
    while True:
        try:
            shift = int(input("Enter shift value (integer): "))  # Convert input to integer
            break  # Exit loop if input is valid
        except ValueError:
            print("Invalid input! Please enter a valid integer.")  # Error message for invalid input

 # Get encryption or decryption mode
    choice = input("Type 'encrypt' to encode or 'decrypt' to decode: ").strip().lower()

# Validate user choice and process text
    if choice in ["encrypt", "decrypt"]:
        output = caesar_cipher(message, shift, mode=choice)  # Call function
        print(f"\nResult ({choice}ed message): {output}\n")  # Display result
    else:
        print("Invalid choice! Please enter 'encrypt' or 'decrypt'.")  # Error message


# === PROGRAM EXECUTION ===
if __name__ == "__main__":
    main()  # Run the main function
