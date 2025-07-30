from PIL import Image
import numpy as np
import os

# Load image
def load_image(path):
    image = Image.open(path)
    return np.array(image), image.mode

# Save image
def save_image(data, mode, path):
    img = Image.fromarray(data.astype('uint8'), mode)
    img.save(path)

# Encrypt image
def encrypt_image(data, key):
    data = data.astype('int16')
    encrypted = (255 - data + key) % 256
    return encrypted.astype('uint8')

# Decrypt image
def decrypt_image(data, key):
    data = data.astype('int16')
    decrypted = (255 - (data - key)) % 256
    return decrypted.astype('uint8')

# Get base name of file
def get_base_name(filename):
    return os.path.splitext(filename)[0]

# Main program
def main():
    print("🔐 Image Encryption Tool - SkillCraft Internship")

    filename = input("Enter the image file name (with extension): ")

    if not os.path.isfile(filename):
        print("❌ File not found. Please check the name and try again.")
        return

    try:
        data, mode = load_image(filename)
    except Exception as e:
        print(f"❌ Failed to load image: {e}")
        return

    encryption_key = None
    encrypted_data = None

    while True:
        print("\nWhat do you want to do?")
        print("1. Encrypt the image")
        print("2. Decrypt the image")
        print("3. Exit")

        choice = input("Enter your choice (1/2/3): ").strip()

        if choice == "1":
            encryption_key = int(input("Enter encryption key (e.g. 42): "))
            encrypted_data = encrypt_image(data, encryption_key)
            encrypted_file = f"encrypted_{get_base_name(filename)}.png"
            save_image(encrypted_data, mode, encrypted_file)
            print(f"✅ Encrypted image saved as: {encrypted_file}")

        elif choice == "2":
            if encrypted_data is None or encryption_key is None:
                print("⚠️ You need to encrypt the image first before decrypting.")
                continue

            user_key = int(input("Enter decryption key (must match encryption key): "))
            if user_key != encryption_key:
                print("❌ Wrong key! Cannot decrypt the image.")
                continue

            decrypted_data = decrypt_image(encrypted_data, user_key)
            decrypted_file = f"decrypted_{get_base_name(filename)}.png"
            save_image(decrypted_data, mode, decrypted_file)
            print(f"✅ Decrypted image saved as: {decrypted_file}")

        elif choice == "3":
            print("👋 Exiting program. Thank you!")
            break

        else:
            print("❌ Invalid choice. Please enter 1, 2, or 3.")

if __name__ == "__main__":
    main()
