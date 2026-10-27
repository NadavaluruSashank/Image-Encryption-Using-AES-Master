# Image Encryption using AES — source

See the [main README](../README.md) for the full project overview.

## Requirements

- Python 3.8+
- `pip install pycryptodome pillow pyqt5`

## Run

```bash
python main.py
```

Encrypting an image with a key writes `cipher.txt`. Decrypting that file with the same key writes `decryptedImage.png`.
