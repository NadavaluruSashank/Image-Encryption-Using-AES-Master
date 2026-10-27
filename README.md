# Image Encryption & Decryption using AES

A Python desktop application that encrypts an image with **AES-256** and restores it exactly on decryption. Built with a PyQt5 GUI so a user can pick an image, enter a key, and get back an encrypted cipher file (or the original image from one).

## How it works

1. The selected image is read and Base64-encoded.
2. The user's key is hashed with **SHA-256** to produce a 256-bit AES key.
3. The data is padded and encrypted in **CBC mode** with a fresh random IV, which is prepended to the ciphertext.
4. The result is written to `cipher.txt`.
5. Decryption reads the IV back, decrypts with the same key, removes the padding and writes the original image back out as `decryptedImage.png`, with no loss.

## Project structure

```
Image-Encryption-using-AES-master/
├── main.py         # PyQt5 GUI: choose file, enter key, encrypt / decrypt
├── AESCipher.py    # AES-256-CBC wrapper (SHA-256 key derivation, padding, IV)
├── Encrypter.py    # Image -> encrypted cipher text
├── Decrypter.py    # Cipher text -> original image
├── ui.ui, ui_2.ui  # Qt Designer layouts for the two windows
└── IMAGE_ENCRYPTION_AND_DECRYPTION_USING_AE.pdf   # Project report
```

## Tech stack

Python 3 · PyCryptodome · Pillow · PyQt5

## Run it

```bash
git clone https://github.com/NadavaluruSashank/Image-Encryption-Using-AES-Master.git
cd Image-Encryption-Using-AES-Master/Image-Encryption-using-AES-master
pip install pycryptodome pillow pyqt5
python main.py
```

## Possible improvements

- Switch from CBC to an authenticated mode (AES-GCM) so tampered files are detected.
- Use a proper key-derivation function (PBKDF2 / scrypt with a salt) instead of a single SHA-256 hash of the password.
- Let the user choose where to save the cipher file instead of always writing `cipher.txt`.

## Report

The full write-up, including background on AES and results, is in [`IMAGE_ENCRYPTION_AND_DECRYPTION_USING_AE.pdf`](Image-Encryption-using-AES-master/IMAGE_ENCRYPTION_AND_DECRYPTION_USING_AE.pdf).
