# 🔐 Image Encryption Tool
A simple image encryption and decryption program built using Python and NumPy, developed as part of an internship project under **SkillCraft Technology**.

This tool allows users to securely encrypt and decrypt image files using a basic pixel-level encryption algorithm.

---

## 📌 Features

- Menu-driven interface
- Encrypt any image using a numeric key
- Decrypt only if the correct key is provided
- Automatically saves encrypted and decrypted images
- Runs in a continuous loop until the user exits

---

## 💡 How It Works

The program uses the following transformation for encryption:

Encrypted Pixel = (255 - Original Pixel + Key) % 256


And for decryption:

Original Pixel = (255 - (Encrypted Pixel - Key)) % 256



This ensures the operation is reversible only with the correct key.

---

## 🚀 Getting Started

### ✅ Prerequisites

Make sure you have Python installed along with the required libraries:

```bash
pip install pillow numpy



📂 File Structure

Image Encryptor/
│
├── image_tool.py         # Main Python script
├── README.md             # Project documentation
├── your_image.png        # Your original image
├── encrypted_your_image.png
├── decrypted_your_image.png


⚠️ Important Notes
The same key must be used for encryption and decryption.

If you enter the wrong key during decryption, the image will not be decrypted.

Currently works with images in .png, .jpg, or similar formats supported by PIL.


📚 Technologies Used
Python 3.x

Pillow (PIL)

NumPy

